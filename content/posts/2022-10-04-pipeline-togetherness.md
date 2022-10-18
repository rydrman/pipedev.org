---
title: "Pipeline Togetherness"
date: 2022-10-04
author: Ryan Bottriell
summary: "On the global pipeline community and how we get connected"
---

I actually started this meetup with a few housekeeping items that ended up being very much on point for the topic! As we started talking about the possibility of replacing the pipedev slack with something else things kind of just rolled into the main discussion...

## Pipeline Togetherness

The pipedev.org [slack channel](https://join.slack.com/t/pipe-dev/shared_invite/enQtOTQzNDE3MTkzNzMzLTA4ODRmMzFkMmUwODJkYzVkY2NmODhmZjAxZTI3MmI1NzVlNTYwNGI5MTYxYjgyNTFhZGVhMDgxOTNmOWEzN2M) is rather quiet these days. There's no harm in keeping it around, but I wanted to open a discussion about switching to an alternative which might be more active or provide a format that's more useful to everyone.

In general, we've seen a shift from slack to discord recently, but there are definitely still very active slack communities such as the ASWF one. Someone also brought up mailing lists as a nice alternative, but there is already the [global vfx pipelines](https://groups.google.com/g/global-vfx-pipelines) mailing list that is also very quiet these days.

### The Trouble with Real-Time Q&A

One of the driving goals of this community is to connect members of our community, and then also to make a record that might be useful to others (ie. these posts). The format of mailing lists is more in-line with that goal because it's a persistent record that can usually be browsed and searched.

Much of the existing discussion (if any), takes place in chat groups. Although any community is great, we discussed how chat is not a great place for all of these items because it's pretty time-dependent, and makes it both easy to lose and hard to discover the information.

As a global community, we are connecting more and more across time zones. It's often easy to entirely miss conversations overnight, and even if you do see them, participating in an old conversation can be fruitless.

When a question is answered in a chat stream, it quickly gets buried under new messages. If you need to come back to the answer later you might be able to find it, but often it gets harder as time passes. The information is also lost to anyone else that didn't see it happen, which is especially true in the public space since you cannot get google results for slack messages.

### Persistence and Discoverability

Keeping again with the themes of this pipedev group, it seemed to make sense that a more persistent, forum-like resource would be a better solution. Something like the Q&A design of the StackExchange sites (eg: StackOverflow).

_After the meeting, I went on a search for a potential stack overflow clone and ended up discovering that you can propose new stack exchange sites. This seemed like the ideal solution because I don't need to host it, the platform is well-proven, and the content would be the easiest to find. As of writing, the proposal is still active and needs both support and participation to become a real thing, please [contribute](https://area51.stackexchange.com/proposals/127325/vfx-pipelines?referrer=OTQ1OTI5MWVhY2Q5NjBjNTA3ZjhlZWM4NWJjNTQ0MWUwYzM0ZjhhNTg0MzYzYTZhNzUyMzhjNTE5MDg1ZjUyOF1Y9p3iOxI-FQsfROCcjEN_Upjtls4MpUfGdY32juug0)_

## Documentation

Our discussion on Q&A brought up the idea of documentation, and so we spent most of the rest of the meeting following this tangent.

> Do folks try to enforce documentation, somehow? Or push people to write it in some other way?

_This is actually a topic that we covered more in-depth [a couple of years ago](https://pipedev.org/posts/2020-01-29-docs/)_

Certainly, with code and API documentation, the group was largely in favour of setting up automation to enforce some level of existence and consistency. The harder part is user and workflow documentation as well as how-tos and post-mortems.

One strategy that was proposed was to keep a brain trust of users close throughout the implementation of a system. Their regular feedback is not only valuable to help guide development but, if you keep good notes, can also be a great starting point for compiling the most valuable bits of information for other users.

This was mirrored in the idea of both a buddy system that pairs developers with artists, and the appointment of product owners (PO). With product owners, one or two people are selected at the beginning of a project to represent the end users. They will communicate as needed with other users to gather ideas and opinions, but are ultimately responsible for guiding the priorities and deliverables of the project.

Once available, product owners then also become an invaluable resource for identifying the types of documentation to write, and for providing feedback on the efficacy and completeness of that documentation. You should already be making regular deliveries of features to these POs, so the explanatory user docs become more of a requirement for them to fully explore and make use of them.

### Documentation Systems

In terms of tooling, we were all only lukewarm on sphynx, and groaned a little at the mention of doxygen. Both are great tools, but the experience with either can be very hit-and-miss depending on the language and ecosystem that you are working with.

The one thing that we did generally agree on was that setting up a system where all published documentation can live inside the codebase as markdown can make life a lot easier. It not only allows the documentation to follow the same review and approval process as the code, but also encourages making documentation changes at the same time as code changes. This is not only convenient, but is a great place to start developing healthier documentation habits overall.

### Conclusion

_At this point in the evening, we actually moved into a super interesting (but rather off-topic) discussion around different experiences and techniques for teaching programming. For the sake of having a reasonably consistent article, I have not included those notes here._

If there's one thing that came out of our discussion, it's that this great community of pipeline devs is made up of busy people. We enjoy connecting with each other and helping each other out, but also all have busy work and personal lives that (not surprisingly) keep us from participating consistently all year round.

Overall, the format of these sessions seems to be well received, and the notes that come out of our meetings continue to be a nice resource for at least some of us.

I am optimistic about the stack exchange proposal (please [participate](https://area51.stackexchange.com/proposals/127325/vfx-pipelines?referrer=OTQ1OTI5MWVhY2Q5NjBjNTA3ZjhlZWM4NWJjNTQ0MWUwYzM0ZjhhNTg0MzYzYTZhNzUyMzhjNTE5MDg1ZjUyOF1Y9p3iOxI-FQsfROCcjEN_Upjtls4MpUfGdY32juug0)!), but even if it doesn't get enough participation to become its own site the idea of a more accessible knowledge base seems like the right next thing to build out.

Thanks for reading!

### Existing Community Links and Resources

1. Slack Instances
   - [ASWF](https://academysoftwarefdn.slack.com) (specifically the pipeline channel)
   - [studiosysadmins](https://studiosysadmins.slack.com)
   - [pipedev](https://pipe-dev.slack.com)
1. Google Groups
   - [USD](https://groups.google.com/g/usd-interest)
1. Discord
   - [Coding for CGI & VFX](https://discord.gg/KepWvn8)
   - [Cloud Native Studios](https://discord.gg/XPAS9rysnr)
   - [StudioSysAdminsFr (France)](https://discord.gg/ZBrXHevRT)
   - [Open Pype](https://discord.gg/sFNPWXG)
   - [CG Wire](https://discord.gg/VbCxtKN)
