---
title: "Managing Migrations and Upgrades"
date: 2022-05-31
author: Ryan Bottriell
summary: "Replacing old things with new things, or making old things new again"
---

Replacing old things with new things, or making old things new again
Some of us might be lucky (or unlucky) and find ourselves in the situation of building a brand new pipeline from the ground up, but for most of us this is not the case. Working in pipeline often means inheriting and maintaining old systems and software that have been around for quite some time.

Eventually, old software needs to be updated or replaced. Maybe it's managing the upgrade of a database; moving from one database to another; updating dependency versions to access new features; changing OS versions; or any other similar activities. The goal of this session was to share our experiences, successes, and failures when approaching and tackling these migrations and updates.

## Managing Migrations and Upgrades

As with other recent sessions, this was run more or less like a lean coffee session: where we moved from one question/topic to the next based on Q&A submissions and some voting.

### Python 2 to 3 Migrations

For those who are not aware, python 2 reached the end of support on January 1st, 2020 but most of our studios are still running it quite widely. The reasons are numerous, but I won't go into detail here as this is something that we've talked about before. Needless to say, we've all been thinking about and participating in python migration efforts over the last several years, with more still to do for many of us.

In general, there are two common approaches to migrating python code:

1. Fork the code into a python3-only version and backport fixes as needed
2. Update and continue writing the code in a python2/3 compatible way

From a really casual survey, it was clear that both of these methods were being used quite heavily by those in attendance. In general, we agreed that the choice was based on the specific situation, but most studios are opting to make their code compatible rather than forking. 

One of the benefits of writing compatible code is that you can test in both python 2 and python 3. If and when you learn of bugs or regressions, you can check if they exist in both versions of the language or just one. This can help in debugging, but also gives you a fallback in case you get stuck on a bad issue and are unable to run the application in python 3.

We also talked about tooling and CI integrations. For example, your CI process can be updated to reject code that is not python3-compatible. More broadly, there's a lesson to be learned about tooling. Namely: never underestimate the value of good migration tooling. The python community built a great number of awesome tools for this process, and most studios have used, wrapped, and extended these tools for their own internal setups.

The other lesson that came out in this discussion is that of a group effort. Often in programming tasks, we are quick to say that you can't just throw more bodies at the problem and build something faster, but in the case of a mass migration like python 2 to 3 that might be less true. In this case, there's a nice opportunity to learn and work as a team, rather than creating one python conversion expert you can keep everyone learning together. This knowledge is then helpful for all members of the team as they continue to maintain and write compatible code moving forward.

### Pitching New Projects or Overhaul Projects

If it ain't broke, don't fix it, right? As developers, we are often the ones spending time in old codebases reporting back issues and asking for time to revamp or replace them, but sometimes it can be hard to ask for and justify. We discussed why this is, as well as some strategies for approaching the conversation.

One of the challenges with replacing something outright is that it presents a lot of risk to your company. You're asking your company to invest a significant amount of time and energy into you and your idea with the hope that in the end, it will be significantly better than what exists. Additionally, you are either asking them to have reduced support on the old system or constantly playing catch-up by porting new features to the new system.

Application/system replacement should always be paired with a strong business or production reason for doing it. You should be prepared to quantifiably demonstrate the flaws of the current system as well as the improvements that you expect to see in the new system. These can be stability, performance, reduced maintenance time, or anything else that is important to the business.

Having a strong business reason and expected improvements is also applicable to update and upgrade projects as well. The key difference is that you can make incremental improvements to an old system while requesting a much smaller amount of risk to the business. Incremental improvements are also a really powerful way to build trust in your ideas and ability to deliver on them, and should always be your first choice when possible.

A few additional tips that came from our discussion:

- respect old code for what it has been able to accomplish
- remember that old code is often messy because it's filled  with  bug fixes
- focus all of your planning on delivering a positive impact to users as quickly and as regularly as possible
- never forget that all projects need training and marketing time, too

### End-of-Life and Deprecation

There's a classic tale in pipeline: production asks for something to be built really fast for a very specific purpose on one project, but 10 years later you're still supporting it.

Given how ubiquitous of a story that is, it seems that none of us have much success at pre-determining the life of any piece of software. All that we can do is to remember our future selves as much as possible and keep our code clean.

But even if we can't set an end-of-life date at the start of a project, the day still comes eventually for many applications. So what can we do to help with this process?

By and large, the biggest piece of advice that came from our discussion on this topic was to use telemetry. Even something as simple as logging into a file each time an application is started can give you a huge amount of important information when approaching a deprecation. For example: is anyone still using this application?

Additional information like usernames can help you to identify who your main users are, and provide you with a short list of people to talk to about why they are using something or why they haven't moved on to whatever was supposed to replace it.

Of course, you can always just turn something off or disable access and see who comes complaining, but that's a hard thing to recommend. Introducing telemetry early and in abundance can answer all of the otherwise difficult questions and ease your mind through a deprecation.

Along with this telemetry is the idea of redirection. Old functions and libraries can be rewritten to simply call the new thing. Old websites and URLs can be redirected to new pages. Old binaries can be turned into wrappers that call other programs. This is a great way to replace and move users to a new system without causing disruption.

### Who is responsible for relaying deprecation information, and how attentive are people to this information?

Of course, in some cases, you can get away with upgrading or replacing components of a system without needing to tell anyone, but when an application or service is being removed that users or artists interact with directly, how does the memo get out?

Beyond the idea of redirection, which was mentioned earlier, most of what we discussed here was how you can leverage all the existing communication methods. Email, in-person, in chat, etc depending on how many users need to be reached. Maybe there's a notification in the user interface itself, or a regular email to anyone that has used the application in the last week. Eventually, you'd hope that the list of users is small enough that you can reach out directly, or accept the small impact and move forward with the change.

### When is a change/upgrade ready to go out?

It's tempting to say "when it works", but really the answer is more along the lines of when it's working, tested, the code is clean, and the upgrade or migration path is clear to all stakeholders. That's a mouthful, but it does highlight the importance of all of the organizational and housekeeping work that must be involved in order to manage these processes successfully. Someone also added "when the documentation is updated" as a similarly important factor.

In many cases, the easy thing to do is release the new version so that it's optionally available first. This is a low-risk approach that gives people time to test and report issues while still being able to fall back on a known working version.

We also talked about readiness meaning when the code can be properly supported by your team both in understanding and availability. It would be irresponsible, for example, to release a change that only you have seen on a Friday afternoon before your week-long vacation to Timbuktu.

### Conclusion

Most of us have been through these upgrade and replacement projects before and we will no doubt continue to face them in the future. Common themes in all of our success stories were data and timing.

Having the right information available to answer your questions about who is using something and how is invaluable when introducing change. It can also help to identify what any  replacement solution needs to provide. Similar data gathered in tandem from the replacement solution can also help you monitor the progress and success of a project while it's happening.

However, all of this data is only helpful if you have a big enough sample - so planning ahead and introducing the telemetry early is important. Similarly, approaching all of these upgrade and update projects methodically, and one piece at a time helps to keep everyone sane and build confidence in you and your team's ability to deliver.

I hope that we all learned a little something from one another in this session and that maybe our thoughts and advice could prove useful to you as a reader.

Thanks for reading!

### Book Recommendations 

- [Working Effectively With Legacy Code](https://medium.com/r/?url=https%3A%2F%2Fwww.oreilly.com%2Flibrary%2Fview%2Fworking-effectively-with%2F0131177052%2F)
- [Refactoring: Improving the Design of Existing Code](https://medium.com/r/?url=https%3A%2F%2Fwww.oreilly.com%2Flibrary%2Fview%2Frefactoring-improving-the%2F9780134757681%2F)
- [Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://medium.com/r/?url=https%3A%2F%2Fwww.oreilly.com%2Flibrary%2Fview%2Fclean-architecture-a%2F9780134494272%2F)
- [Clean Code: A Handbook of Agile Software Craftsmanship](https://medium.com/r/?url=https%3A%2F%2Fwww.oreilly.com%2Flibrary%2Fview%2Fclean-code-a%2F9780136083238%2F)
- [The Design Of Everyday Things](https://medium.com/r/?url=https%3A%2F%2Fwww.amazon.ca%2FDesign-Everyday-Things-Revised-Expanded%2Fdp%2F0465050654)
