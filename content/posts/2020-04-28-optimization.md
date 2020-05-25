---
title: "Forum - April 2020"
topic: "Code Optimization, Speed, and Efficiency"
date: 2020-04-28
author: Ryan Bottriell
summary: "What does it mean to optimize code in a pipeline context, and how do we approach it?"
---

# Code Optimization, Speed, and Efficiency

You need code before you can optimize it.

Right off the bat we're talking about not optimizing code at all, but it's an important point to remember as a developer. Optimizing too early can make your code unnecessarily complex and sometimes run less efficiently.

Once you have a nice functioning code base that isn't running as fast as needed, then you jump back in for optimizations. We all recognized that profiling the code and really understanding the bottlenecks are important whenever you plan to implement optimizations. What we have also found to be true is that clean, well structured code is infinitely easier to profile and therefore optimize than a pile of spaghetti, which it important to remember during the initial implementation.

The CProfile and profile packages that come with the python standard library came up as go-to tools for profiling python code. Those with experience did admit that it's not exactly plug-and-play. This is true for profiling in most languages, where the profiler collects a huge amount of information while your code is running, and they you are expected to find useful ways to look at the data and start to figure out where time is being spent and optimizations can be made. The standard library profiler gives you all the tools for the job, including a command line to view and filter your data, but it takes time to learn the intricacies or build up a collection of useful recipes that help you explore the results.

As we discussed our experiences and methodologies, it also came out that many of us opt to not use profilers per se, but rather simpler timers and print statements around suspect areas of our code. This can be a very simple way to find slow parts of a pipeline or set or processes, and also reduces the amount of data that you are sifting through. That being said, it makes some assumptions that you know where to start looking. From the experience in the room, we discussed that often what you think is the slow part of your program isn't, or at least isn't for the reason that you thought it was.

## Optimizing Pipeline Code

While sharing stories of different code bases and programs we had optimized, it started to become clear that most of what we had optimized was not really pipeline code as you might imagine. We asked ourselves why this might be the case. Why don't we optimize pipeline code?

We talked about how pipeline code really is the glue that holds many different pieces together, but because of that it's also not often the bottleneck. The process of saving a scene file or setting up a folder structure is more limited by interactions with the filesystem than the code itself.

To put this more concisely, pipeline code is most often I/O bound (rather than cpu bound, memory bound, etc). There are definitely many ways to optimize I/O bound code, but when the vast majority of your execution time is spent writing a scene file to disk (for example) there's often not much to be done or worthy gain to be made. The same is true for situations like a render, where pipeline code may be operating before and after the render, but the render process will take such a huge amount of time in comparison, any slow portions of the pipeline code won't be noticeable. This example also identifies the final point - which is that there's usually a decent amount of pipeline code which is executed remotely, where there is no human waiting around and able to complain about it taking a few extra minutes.

## "_General Slowness_" and the Filesystem

This discussion got us on the topic of general slowness. The ever-present struggle of all studios and pipelines. The general catch-all issue for help desk reports and complaints from artists.

More often than not, slowness gets blamed on the network: especially since most studios use large network filers. Those of us that have dealt with this problem on a technical level, or even just chatted with a systems engineer, know that the network is often not the problem. There are so many intricate pieces and moving parts that can play a role in slowness that one slow server, a bad cache or even an overloaded workstation can create problems.

_We were diverging a little far from the code optimization discussion a this point, but I'll try to bring the context back here along the way._ We talked about how network storage can be very slow compared to local disk, and that metadata operations make up a large part of that slowness (checking if a file exists, reading a file's timestamp, permissions, ownership etc.). In python, we can optimize with this information by changing the way that we access files:

```py
# this requires an additional metadata call to the
# filesystem, which is slower. Not to mention that
# the file could still disappear in between the
# is_file and open calls.
if os.path.is_file("data.csv"):
  with open("data.csv") as data_file:
    return data_file.read()
else:
    return None

# always opt for the pythonic way of working with
# a file: ask for forgiveness, not permission
try:
  with open("data.csv") as data_file:
    return data_file.read()
except FileNotFoundError:
    return None
```

From our experience, you also get the best performance out of a network filesystem when reading large amounts of data sequentially. To optimize for this in python, we can opt to read more data into memory rather than processing it piecemeal.

```py
# because of the python iterator, this first
# implementation reads one line, processes it,
# and then goes back to read another line.
# Each read operation is separated by the time
# it takes to process
with open("data.csv") as data_file:
  for line in data_file:
    process_line()

# instead, we can read the whole file all at once,
# and then stop interacting with the network filer
# completely
with open("data.csv") as data_file:
  data = data_file.read()

for line in data.splitlines():
  process_line()
```

## The Games Perspective

Recently we've had the pleasure of including perspectives from the video games industry at the forum, which is always very interesting to hear about - as they are similar to the VFX and animation industry in many ways but also so different.

The big difference that we talked about in this session, is the practice of using a giant shared perforce server for game data. This means that all of the data is localized onto a huge local disk, and kept in sync with a central repository of data. Local data is faster for sure, but the inclusion of a perforce server means that when you do need to go back to the network, it can be much slower with the additional overhead (checking files in/out, looking at history, querying for locks, etc).

## Parallel Python

After some time, our conversation made it's way back to python, specifically and the types of optimizations that one can make.

Python3's asyncio seems particularly relevant to our conversation on I/O bound applications, since on paper it allows your application to do other things while waiting for I/O to return. This includes making http requests, loading file data, and listening for incoming requests. In practice, however, there is a significant cost to this new idea. It makes your application significantly more complex, and therefore more difficult to maintain. In plugin or even callback scenarios like a lot of pipeline code that we deal with, one can also argue that introducing the async event loop can be more struggle than it's worth.

The other main option for python code is to use the multiprocessing module. This essentially starts a whole new python instance, copies the necessary data over and runs a function over there. This works really well for heavy tasks that don't need to share a lot of information, like CPU bound data processing applications since the cost of setting up each process is relatively high, and you have to deal with data and errors much more carefully.

Some of us have used these technologies in our code before - and they can definitely help when properly applied. Asyncio is really more aimed at webserver-type applications, and multiprocessing for crunching big data sets. If you need to copy a large number of files, something like multiprocessing might help, but that depends on the specific bandwidth of your disk/connection and whether or not you need multiple processes to fully saturate it (aka: always profile and analyze).

## Python Alternatives

At this point we asked ourselves about alternatives to python. Go, Rust and C++ seem to come up at least once in each forum, and are undeniably more performant and more parallelizeable than python.

> Use the right language for the job * <- _with an asterisk_

This was our general consensus on the matter. Basically, we see great benefits in being able to use alternative languages for things that they are more suited to. Go for web servers, rust for systems programming, C++ for high performance plugins etc, but there's a catch (As always). These languages all have their learning curves, especially newer languages that are not already prevalent in our industry. There's also a different maintenance, and deployment cost to them. Python is notoriously forgiving, which makes developing and deploying it very fast and easy under a lot of circumstances.

What is clear, though is that many of those present had already used Go or rust in a pipeline context, or were seriously considering it for the future.

## Python Compilers

The last thoughts that we had were about python compilers. Cython, nuitka, and other tools exist which compile python code into native python modules with the goal of producing faster, and more optimized modules.

Overall, from the experience in the room, it seemed like these tools can have worthy benefits in applications which are CPU bound. The work to set up, use and maintain a toolchain like this for a project however is not really worth it for I/O bound applications or smaller scripts.

## Conclusion

And that's about where we ended off. Overall it was a very interesting topic, since many of us have dealt with or dabbled around this idea in our own work but for the most part it feels like pipeline code is not often the primary target of optimization efforts. Got your own thoughts for this discussion? [Join the discussion on slack!](https://join.slack.com/t/pipe-dev/shared_invite/enQtOTQzNDE3MTkzNzMzLTA4ODRmMzFkMmUwODJkYzVkY2NmODhmZjAxZTI3MmI1NzVlNTYwNGI5MTYxYjgyNTFhZGVhMDgxOTNmOWEzN2M)

Thanks for reading!

## Further Reading & Interesting Links

- Application performance monitoring from elastic [https://www.elastic.co/apm](https://www.elastic.co/apm)
- Keynote on Python3 Concurrency [YouTube](https://www.youtube.com/watch?v=9zinZmE3Ogk)
- Comes recommended as a fun book to go through: [https://natureofcode.com](https://natureofcode.com/)
- A great project to try if you've never done it, or to learn a new language/tool: [ray tracer in a weekend](https://github.com/RayTracing/raytracing.github.io)
- [ripgrep (github)](https://github.com/BurntSushi/ripgrep) is a useful recursive, code friendly search tool to add to your toolbox
- A specification for application metrics and tracing [https://opentelemetry.io/](https://opentelemetry.io/)
- Demo of Blender's new realtime viewport [YouTube](https://www.youtube.com/watch?v=gy2Sa-DMZEk)
- Article on Unity's real time and cinematic tools [The Verge](https://www.theverge.com/2017/10/4/16409734/unity-neill-blomkamp-oats-studios-mirror-cinemachine-short-film)
