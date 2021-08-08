---
title: "July 2021"
topic: "Filesystems and Data Management"
date: 2021-07-20
author: Ryan Bottriell
summary: "How do we organize and deal with all of the data that's produced in a pipeline?"
---

It's been quite some time since we had a topic-based discussion forum. Our virtual meetups have been smaller since the pandemic started and the online space just doesn't have quite the same energy for collaborative discussions. Nonetheless, in this session I wanted to try something a little bit different in order to make sure that everyone had a voice and we got a chance to talk about the biggest questions and ideas from the room.

## Filesystems and Data Management

This topic is intentionally a little vague. Depending on who showed up we could talk about anything from file naming conventions to database management or even the inner working of filesystems themselves.

Given that the group was quite small, we did actually talk about a number of things before going through the discussion and taking notes - unfortunatley those are not captured here, but what we did capture is still a very interesting set of questions and thoughts about where we are as an industry.

### What is the future of filesystems in the VFX industry?

If we ever were to move to some other filesystem format or interface, it would likely need to start with a common standard. Like the unix filesystem standard that we use on linux. This is unlikely to be created or driven from within the industry, however, given that we are not crazy enough to think that designing and developing our own filesystem is worthwhile (right?!).

That being said, there are some existing standards that are arising for new technologies, the most notable being s3 as a defacto standard for object storage. This brought up questions about how object storage works, and whether it breaks files down to be more efficient.

The answer is largely different depending on the implementation that you use, but certainly, some do. That being said, as far as those that were in attendance knew, file chunking to reduce duplication is actually a very difficult problem to solve and you get more gains more easily through compression instead. [Hammerspace](https://hammerspace.com) came up as a technology that implements deduplication and compression. It does this in conjunction with object storage to make cross-site data movement and storage quicker and more efficient.

### Will we ever get away from NFS?

Something about our industry's reliance on NFS makes developers nervous, but as far as we know this has been true for decades. NFS is an extremely well-established technology that is battle-hardened by many industries around the world, this makes it an easy choice and one that is really hard to give up.

NFS is also still actively being developed. Although we don't talk about it much, the latest NFS v4.1 (2010) is still largely not in use but provides some awesome functionality around clustering and scalability.

All this to say, NFS makes a lot of things really simple and is such a widely used technology that it's unlikely to get replaced anytime soon. Though it does continue to evolve!

### How to best optimize file storage for projects?
> _for example: using hardlinks, symlinks, filesystem level compression etc._

The first scenario here is with files that are controlled by the pipeline. These are files and directories that are created, organized and managed by pipeline code. Users don't usually look at or navigate these files manually.

In this case, you can leverage the code that's already in place to add efficiencies within the filesystem. For example, as something is versioned, you can create symlinks or hard links to avoid creating copies of files that are the same across versions. Assuming, of course, that the files are read-only since you don't want the act of changing one version to change others!

On the other side are files that are not pipeline-controlled. These are file sets that users create manually, version manually and organize manually. You can create tools for users to run on these files, but without more knowledge about the files and structure, they can be very hard to clean up programmatically.

Generally, our strategy for data like this is to use monitoring and quotas. Aka be able to report back to the user how much disk space they are using and enforce quotas for how much they are allowed to use.

Another useful way to handle this is to set up a billing or chargeback system for productions - where they pay for the cumulative space that is being used. Charging the user themselves can be counterproductive if they spend too much energy worrying about size and therefore becoming less productive, but having productions pay for space overall incentivizes the team as a whole to not go overboard. At the same time, if they have the budget to go overboard then they can, and that money can simply be turned around into additional infrastructure.

Another idea that we talked about is that some filesystems (mac, butrfs) also support the idea of copy on write (aka reflinks) which allows a file to be references like a hardlink, but then not affect the original file when the reference is written to. This would only work in very specific setups but could be really valuable in the right place ([reflink vs symlink](https://dev.to/robogeek/reflinks-vs-symlinks-vs-hard-links-and-how-they-can-help-machine-learning-projects-1cj4)).

### File Versioning

In a VFX house, there's a couple of ways that we version files: version control (`git`, `perforce`, etc), or simply the idea of keeping versioned files (`scene_1.ma`, `scene_2.ma`, ...). Version control systems require that you interact with them regularly - check in and out files, adding comments etc. Versioned files is more likely to be seen in a pipeline that deals with binary and scene data - where multiple versions might be needed at the same time (by different scenes) and there is no significant branching and merging workflows that are required by something like a source control system.

There's also a larger topic of discussion here around how we deal with asset versioning and references. When everything is versioned up over time do you create a pipeline that updates your scene references automatically to the latest version or do you require an explicit upgrade action to take place?

As usual, good tooling is very helpful here to help people: know when to update; manage the update processes; and possibly automate the bulk update of scenes. With that in mind, our overall wisdom is to avoid automatically updating as much as possible. An out-of-date character in a scene can be updated, but a process that can break scenes autonomously and without warning is much worse.

## Undiscussed Questions & Topics

These are questions and topics that came up in the room and were voted for, but that we didn't have time to talk about or answer:

- distributed filesystems - global/always-on data
- how to handle NFS data in Kubernetes and cloud deployment?
- Is putting an index before the filesystem always going to be beneficial? (db, webservice, etc..)
- Use of SQL vs No-SQL for production data
- does everyone deploy software and run it from nfs? even on windows?

## Final Thoughts

I'm not sure if this discussion system helped make these notes any more useful. It certainly did make it much easier for me to organize and write out this article and I believe that it did provide a better space for everyone to get a voice in our discussion (though we will need to try again with more people to know for sure).

Thanks for reading!
