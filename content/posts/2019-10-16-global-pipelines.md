---
title: "Global VFX Pipelines"
date: 2019-10-16
author: Ryan Bottriell
summary: "In this session, we really tried to focus on the _global_ aspect of this topic. Looking specifically at studios and scenarios where there are multiple sites across many time zones."
---

In this session, we really tried to focus on the _global_ aspect of this topic. Looking specifically at studios and scenarios where there are multiple sites across many time zones.

We started off by simply trying to identify why studios choose to expand globally - as opposed to expanding teams in a single location. Generally, we see only a few:

- **Tax Breaks**: This seems to be the biggest one, and may be one of the only reasons that Vancouver has developed such a large VFX and animation sector over the last while. Recently Sydney, Australia has made itself very attractive and it seems to be working.
- **Talent Pool**: We all know how much the VFX workforce ebbs and flows within and among studios. You need a large base of good talent to keep the whole process moving - and sometimes that means having a studio where the talent is or wants to be.
- **Clients/Markets**: L.A. seems a good example of this - Hollywood is still very much a hub for North American film development and so it can be very beneficial to have at least a small workforce locally to that. In the same way, other film markets around the world become much more accessible when there is a team able and active in the local community.
- **Reduce Timelines**: This one is more than a little debatable, but with locations set up in the right time-zones, you can create a 24 hour pipeline where hand-offs are done during the crossover - enabling constant progress at all hours.

We recognized that the last point hints at one of the biggest challenges in creating and operating a global pipeline: which is simply that a globally distributed workforce creates cultural and communication issues that you just don't battle with in a centralized facility.

All of this talk lead us into another question: _will we ever really get to a world of cloud pipelines_?

The Nimble Collective was an interesting kick at the bucket, and worked out pretty well for them seemingly having joined the Amazon family. Certainly with companies like Amazon, and Netflix getting into the production game we will see some interesting versions of the pipeline in the cloud. The biggest issue that we usually see in going into the cloud is really the data cycle and charges of ingress/egress on the public cloud.

If you have talked to any of the cloud vendors at Siggraph or other events they certainly are good at making the whole transition sound inevitable - and it's hard to argue when the whole world seems to be doing it! Our strict security requirements are not cloud-friendly, but could come around.

### Aspects of a Global Pipeline

#### Storage / Media Transfer

Making sure data is available to the right artists in the right locations at the right time is a real struggle - as any global studio will tell you. We didn't spent too much time on this one, because it's pretty easy to understand and didn't actually seem to be a real driver of issues.

#### Services, Tooling, Software

Same as above. It's important for us to remember that our software is not immune from the issues of globalization. If anything it forces us to have a robust delivery and runtime mechanism for ensuring a robust environment.

#### Security

Where is your content being displayed? When is it in transition and where is it at rest - is it encrypted? These are the main questions that seem to come up when thinking about the security of a global pipeline. This is in addition to the regular issues of identity and account management that you would find in any business expanding across multiple sites.

We also know that there are some contracts related to the advertising of unreleased technology products etc. which have isolation requirements that simply cannot scale (ie require an entirely separated network and armed guards).

#### Quality Control / Environment

For VFX studios, color accuracy and high fidelity viewing are paramount in ensuring that the images being produced meet the quality bar that is expected. This problem may be more related to size rather than distribution, but in either case ensuring the right hardware, software and working conditions exist becomes more and more of a challenge.

#### Communication / Culture

This was our biggest discussion point, and we seemed to all agree that fundamentally the challenges of communication and culture pose the greatest challenge. In many ways, a multi-site studio is just many studios working together. In that scenario it's very easy, if not predestined that you'll end up with entirely distinct cultures and mentalities in each location. This, of course, it not automatically a bad thing, but what we often see is that the personal aspect disappears, and people start to say things like: "oh London hates this" or "Vancouver never does that right" - which can easily become a bad landscape for effective collaboration. **Empathy** was a key word in this discussion: specifically how it's so key to effective teams and collaboration but so much harder to generate and maintain across the multi-site boundaries.

This got us talking about remote workers - like properly remote and "alone". There's something to be said - and probably some studies here and there - about whether a remote worker is more productive. It certainly seems like less distraction and less meetings could make that so. This idea seems dependant on the work being done, and the fact that the work is solitary, well defined and manageable.

So what about the githubs of the world - the companies which are and have always been entirely remote? Maybe there is a point to be made about a company that starts remote, and develops a remote-friendly culture from day one out of necessity. We recognized that for someone working remote to a company with a central office, it's easy to miss out on in-person conversations, impromptu meetings and other information. This is another point to the idea of communication, and makes us think that maybe the hardest thing to do it take a centralized team/company and try to distribute it or make it remote. This would be because it requires significant and difficult changes to fundamental cultures and communication strategies that may be well established. One way that we've seen and heard of this being managed is having strict practices of having one true channel for communication - such as tickets/issues/chat - which everyone is diligent about writing down the outcomes of conversations that take place offline.

We also discussed the team and organization structure of the globalized studio. Do you create teams that span across sites or try to keep them together? Are employees' managers in the same city as them or not? We generally agreed that it is up to the work being done and the management involved, but that the manager and team culture are most relevant. A decentralized team might be more accessible for direct and personal collaboration with others in their respective sites, but be challenged on collaborating within the team. The same probably goes the other way around for teams centralized to one site.

This also brought up many other questions about remote workers that we didn't really have good answers to:

- how to you effectively on-board a remote worker?
- what opportunities are there for a remote worker to get good mentorship and training? - is there a reasonable career growth path for remote workers?
- in any of these cases do they get forgotten? can we really expect equal opportunities when they are remote to a central studio or location?

Back to communication a little - what about phone systems? Some companies have them and some don't, but essentially every employee having a phone on their desk and being able to reach any other employee. Calling is definitely a really quick way to shorten a conversation that you cannot have in person, or that you would otherwise have over chat. We also discussed the difference between a phone and video chat. Maybe it's generational or personal thing but we felt that the phone was somehow more personal than a video chat or at least that it was generally faster and less painless for getting answers. Regardless, I think we all know that it's better than text chatting for fostering empathy and communicating tone.

### Software Package Management

At this point it's starting to seem inevitable that in every forum we find some way to tangent into talking about software packaging and environment management. I am going to leave some of the details out of this forum post as they were not entirely on topic, but if you are dying for more check out some of the other previous posts.

Many existing studios are heavily NFS based, using a shared network drive to release and load software packages and scripts. This is an easy and accessible method - but does it scale globally? and does it scale to large development teams and complex software environments? We know from the experience of our members that it certainly _can_, but we also know that in other scenarios it can cause a lot of pain. So what is the perfect architecture at scale? In short - we don't have a consensus yet. It appears largely related to the culture of the studio, and it's a give and take between the simplicity of chaos and red tape of process. In the end we're not even sure how you measure the benefits of either.

And on that note - we ran out of time! Perhaps that is a topic for deeper discussion at the next forum, or maybe not. If you'd like to have a say be sure to sign up for the mailing list below.

Thanks for reading!

### Further Reading and Links

- We've mentioned this one before, but [How Google Works](https://www.howgoogleworks.net/) came up again as an interesting read. Specifically, it talks about a business that was forced to grow through many similar pains as it scaled, migrated and in a lot of ways created the cloud as we know it today.
