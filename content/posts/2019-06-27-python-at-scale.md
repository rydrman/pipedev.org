---
title: "June 2019"
topic: "Python at Scale"
date: 2019-06-27
author: Ryan Bottriell
summary: "Just to be absolutely clear, we are talking about The Python Programming Language. Due to its integration in many of the digital content creation (DCC) applications, and other reasons I'm sure, it has become extremely prevalent in the visual effects and animation industries. 'At Scale', however, it a little bit more ambiguous. We discussed many different aspects of the language itself, but also a good amount about the people who use it..."
---

A big thank you again to all those who made it out to this month's forum! We had an amazing turnout, made some new friends, and had some wonderful discussions.

Also, before I jump in: [The Pipeline Conference](https://thepipelineconference.com) is having it's inaugural event alongside Siggraph this year so check that out!

## Python At Scale

Just to be absolutely clear, we are talking about [The Python Programming Language](https://python.org). Due to its integration in many of the digital content creation (DCC) applications, and other reasons I'm sure, it has become extremely prevalent in the visual effects and animation industries. "At Scale", however, it a little bit more ambiguous. We discussed many different aspects of the language itself, but also a good amount about the people who use it. I've given as much structure to these discussions as possible without taking things too far out of order or misrepresenting how organized we actually were. Enjoy!

## Encouraging Contribution

In the studio environment, the line between artist and developer are often all too blurry. This can be a powerful thing, because we work in a world where our _clients_ might have enough skill and determination to actually jump in and write code to solve their own problems! The real challenge then becomes: how do you properly empower them to do so? and how do you balance the enforcement of quality and standards against the barrier to entry?

There are some lessons we can learn from the open-source community here. Tagging issues that are more accessible for first-time contributors, for example. Although, some of the prerequisites for that are not always achievable (well organized backlogs, issue curators, long-term deadlines - to name a few). This also relies on a strong, well-documented or self-service CI setup to help people understand the processes involved.

Along similar lines is also the buddy system. This might look like pair programming, or just sitting down together to work through the source control/review/merge workflows that exist. Of course, here you are looking at having spare developer cycles available for this, and a communication structure that supports easy access to such help. At the end of the day, if a would-be-contributor is not aware of all of the help available - or what the first step is that they need to take - it all might be for naught, which is important to understand.

This conversation brought up a few interesting thought experiments as well. For example: what if we looked at getting into Python itself and removing some of the language features (think classes or the like)? Technical aspects aside, the proposal here is about reducing the complexity and creating an area that is more accessible: with less to learn initially, and less ways to shoot yourself in the foot.

One thing that we have collectively seen to work is sandboxing. Having an accessible and self-serve space for people to write, run, test and experiment with code is a must-have. Additionally, one of the key attributes of this space must be _safety_. Safety for me to make mistakes and not accidentally impact production or bring harm to the hard work of others. This idea, however, is more about the environment of development rather than the language itself.

> The right environment gives developers the confidence to make mistakes, learn from them, and iterate without fear of causing problems for others

In all of this discussion, we also have to remember that everyone learns differently. Some things we do may work well for some while other struggle, but there are definitely some agreed upon points that can help encourage both new and repeat contributors:

- establish and document clear and concise steps for new contributors
- make ourselves (as developers) accessible and open to providing help
- provide consistency in development processes; so that everyone learns and teaches the same workflows
- establish and advocate for a constructive and proactive culture in code reviews; to encourage growth, collaboration, and discussion
- ensure that the right people are available to spend the necessary time on review

Some additional notes/ideas:

- standards and requirements can do more harm then good when they are not justified and properly explained (teach not preach)
- set up a regular walk-in session for Q&A with members of the development team - this can help with the accessibility aspect

## Managing a Large Codebase

As the number of contributors grows the sheer volume of tools, scripts, applications and raw source code can become a problem of their own. This discussion, interestingly enough, split itself into two opposing streams of thought: one being that of standards, process and control; and the other leaning more towards organic growth and self-organizing teams. That being said, there are also many universally agreed upon ways to make some of these things easier no matter what your situation is.

Introducing and enforcing a set of standards and practices is definitely an effective way to maintain some level of consistency over a vast sea of source code. We are not just talking about code formatting or linting here either - to be truly effective, we need to define a set of development processes and best practices to cover all aspects of the code and it's organization. One recommendation for achieving this is to establish a working group; One with an open membership which can establish and maintain these standards. As previously discussed, all of this comes with the additional burden of properly communicating the requirements. Ideally, the working group also maintains a set of editor plugins or other tooling to support their decisions. This allows developers to easily meet, and for CI systems to easily validate the established requirements.

On the other hand, there are many successful instances to be seen of large software companies relying on smaller teams to develop their own best practices and ways of working. There is definitely an element of trust here: trusting each of the teams to act professionally and do what is necessary to produce reliable software and tools. One of the main discussion points that drive this side of the conversation was just in playing the devils advocate to the above scenario: How do you measure the busine$$ value of standards enforcement? What if you don't centralize and standardize? You can provide a set of resources to be taken advantage of, but allow teams and developers to find what works best for them.

In our forum group, there were cases of studios following both of these scenarios, and succeeding. We pondered the difference, and ultimately settled on studio culture being at the heart of most difference. Where these difference cultures come from is a discussion on its own, and discussions on affecting a change in culture is way beyond our expertise.

## Best Practices For Teams and At Scale

An interesting question came up about how we can promote projects with a single developer into one owned and maintained by a team. What this sparked, really, was an expose on best practices for software development in general. What that tells us is that projects of any size which are built with care will be the easiest to scale and maintain over time.

- Merge early and merge often - do not build in a bubble and present a huge changeset to your colleagues
- Be proud of your code - not just what your code does, but the code itself
- Communicate - discuss your work as often as possible and gather feedback

## Things you Need At Scale

A small list of additional resources required as projects and codebases scale out. After jotting down this list, though, we couldn't help but wonder: Are these really scale problems, though? Or do the jobs just get bigger at scale?

- Project management
- Software architects
- Short, medium and long term planning - project road maps
- Requirement gathering, tracking
- Release management
- A healthy balance between ownership and collaboration

## Deploying Python in a Pipeline Environment

As an [interpreted language](https://en.wikipedia.org/wiki/Interpreted_language), Python distribution is largely just making the source files available for people to execute. Because of that, one of the consistent solutions that we see is just a large shared network drive in which all code is placed and executed from. What you often end up with is either a repository of versioned packages or a singular view of what is currently _the pipeline_. In the former, you additionally require methods to specify, resolve and build up environments with the versions of the code that you want, whereas the former introduces challenges with isolating environments and reduce the impact of bugs or breaking changes.

### Python Byte Code

Do we enable the generation of `.pyc` files in production? Do we pre-generate `.pyc` files and deploy them exclusively? The answers here seem to run the gamut, and probably anything is a good solution as long as you stick to it.

### Some Notable Tools

- [Rez](https://github.com/nerdvegas/rez) - packaging, environment definition and dependency resolution
- [virtualenv](https://virtualenv.pypa.io/en/latest/) - environment isolation
- [pipenv](https://github.com/pypa/pipenv) - python packaging, environment isolation, dependency resolution, deterministic builds

## Managing Documentation

Do we include release notes under the umbrella of documentation? And how do you even measure the impact of good documentation?

If we're honest with ourselves, developers are not usually the best at writing docs that are accessible to our users. Even when we do write decent documentation it is always at risk of becoming out of date, which can be detrimental to the usability of the system as a whole.

Realistically, it feels like in a studio environment the documentation must be collaborative. A well build system with the right culture creates a workflow where all documentation can be fixed, and improved by anyone at any time. Dedicated technical writers or other people responsible for initial documentation can still provide a lot of value in this kind of system, but we admit that realistically we cannot expect to see the investment of resources required to professionally maintain all of a studios documentation over time.

## Type Hinting

It’s great! and worth the time. This is especially true in Python 3, where it doesn't need to be hidden in ugly comments. A few members expressed concern that type hints remove some of the simplicity and elegance of the language itself, but it seems that could be argued both ways.

## Technical Issues At Scale

This turned into a very interesting topic. It feels like there are a lot of myths surrounding possible Python technical issues, but as we dove into them no one could actually recount any real cases when they were encountered - only heresay and rumours. Maybe some of these things were more reasonable considerations in the past, but as hardware and systems have improved, it's hard to say that they are even worth the hourly rate of a developer to think about.

### Myths?

- Importing Python code over NFS (Network File System) can be too chatty and cause problems

> Python looks for a lot of different files and file extensions, not to mention checking and (re-)compiling pyc code (if enabled)

- Rez adds one `PYTHONPATH` entry for each package, which gets long and slow - adding to the file system chatter

### Things You May Not Know / Tips

- There are character limits to environment variables ([Linux](https://unix.stackexchange.com/a/521377), [Windows](https://devblogs.microsoft.com/oldnewthing/20100203-00/?p=15083))
- Do not deploy code with the reload statement - it does [a lot more](https://docs.python.org/2.7/library/functions.html#reload) than you may know. It's also not as accessible in Python3.X


## Further Reading and Links

The [Clean Code/Coder/Architecture Series](https://www.pearson.com/us/higher-education/series/Robert-C-Martin-Series/348084.html) of books are a must read for those who want to go beyond just writing code that works. These books are a great knowledge base to help with writing code that functions well in large teams and at larger scales.

[Sonar Cloud](https://sonarcloud.io), along with its open source and self-hosted [counterparts](https://www.sonarqube.org/), provide code quality analysis that looks at many different aspects of cleanliness and maintainability. This kind of thing can provide useful insight and feedback to developers looking to improve the code that they write.
"Pep8-ish" is a recommended YouTube video on the Python pep8 standard (link still needed)
"Don’t Pep8 Me" is another such video (link still needed)

[Black](https://github.com/python/black) is an "uncompromising" code formatter for Python, which means that you can stop talking about how it should be done and just standardize

[How Google Works](https://www.amazon.ca/How-Google-Works-Eric-Schmidt/dp/1455582344) is a recommended read if you are interested in learning about how one of the largest software companies in the world works

[Powerful](https://www.amazon.ca/Powerful-Building-Culture-Freedom-Responsibility/dp/1939714095) is another recommended read on the culture and process of Netflix, and how they manage their teams and scale
