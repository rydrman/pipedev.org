---
title: "October 2021"
topic: "Getting Started in Pipeline"
date: 2021-10-19
author: Ryan Bottriell
summary: "Thoughts and advice on getting started as a pipeline developer"
---

In this session, we wanted to uncover some thoughts and advice on getting started as a pipline developer. I have also been looking for a bit more of a structured format for our meetings for a while now, and so decided to run this session based off of the ideas of [lean coffee](https://www.scrum.org/resources/blog/lean-coffee-5-minutes). Overall, I think that this worked really well, and you will find that because of this the notes below are structured more like a Q&A than the usual stream of conciousnes that I am trying to organize.

# Getting Started in Pipeline

We spent a little bit of time saying hello, writing down some topics, and voting at first. Then, once a question surfaced at the top of the list, we jumped in.

## On-Boarding Processes

The first question was a poll of on-boarding processes. What have you experienced and what kind of on-boarding does your company currently run through for pipeline folks?

Our answers spanned the full gamut, I would say. From being handed a computer that doesn't work and having to run with it, to dedicated training material and a dedicated mentor to help answer any of your questions and be a guide.

We also talked about the idea of a 15 minute pipeline, and being able to run through the pipeline on your own in the first week. This, along with any hands on training in the pipeline space, can be a valuable part of getting people up to speed.

## What type of projects do you work on in pipeline?

In a lot of ways, pipeline {{% tooltip TD "Technical Director" %}}s are responsible for almost everything. They are the caretakers of the entire pipeline and often the first set of eyes on any problem that arises. This is because the pipeline TD's primary goal is usually to keep production moving, and provide solutions to both new and old problems that facilitate a more efficient pipeline.

Nowadays, senior pipeline TD's often also take up development tasks in the pipeline that are important to the show, but are not able to be completed in the core development group because of limited resources or other priorities. In many ways, as you gain experience in pipeline, you get the ability to specialize based on your passion. Because there's always so much work to do you can find different pipeline people working on vastly different areas of interest.

As a follow up, here's a random selection of things that people had been working on in the last couple of days:

- learned to make pdfs with python
- built a crowd placement system (anim cache -> build crowd -> go through pipeline properly)
- fixing compatibility issues for python 3 migration
- rv support, rv plugins, configuring view rooms
- exploring DCC software and learning how to render movies from each one

## What barriers do you feel you face in trying to get into the industry?

> It's easy to show up to an interview and get asked questions about software and processes that you know nothing about

The general advice here is to try to show what you do know, and ask about what you don’t. Recognizing that you don't know something, but offering an alternative can help to shift the converstation towards a topic that let's you exemplify your skills and personality. There may be specific topics that they are hoping you know, but most of the time the interviewer is just trying to get you talking so that they can get a sense of who you are, what your experience is, and how you work.

Asking questions also shows great qualities. Curiosity and an eagerness to learn are important traits for good pipeline developer, since the industry is constantly growing and reinventing things. Showing an ability to recognize and be honest about what you don't know also shows great character. Someone who pretends to know everything won't get too far before being found out.

This advice won't always work, but when you have the choice, you always want to find a studio that asks about what you know, is genuinely interested in your aspirations, and is responsive to feedback and questions from your side. At the end of the day, try to remember that running a good interview is no easy task, and not everyone that you meet with is going to be great at it.

> There's a huge gap between what students are taught and what the industry wants you to know.

The term "pipeline" is notoriously hard to define, and will be a little different depending on who you talk to. Even more so, positions in pipeline vary wildly between studios and even inside of a single studio (as we discussed earlier). The "pipeline" also more often than not represents everything that is unique to a studio and it's specific problems. So often you won't see pipelines in academia because the same scale and problem set is just not there, or sometimes there is a small, simple pipeline that you might not even think about (a few scripts setup by a past student or professor to help setup renders, for example).

> I interviewed for a pipeline intern and was asked really specific computer-science questions.

It's probably safe to say that studios have been burned in the past by hiring people with limited computer science knowledge.

That being said, our industry is filled with pipeline TD's from a wide variety of background, many of which without any formal computer science training. Problem solving is a much more important fundamental skill, but also harder to interview for so sometimes hard skills come into questions instead.

The general advice here is to find projects and experiences that can help to showcase problem solving skills - your ability to observe the interconnectedness of a workflow and create automation. _This is something that we touched on in more depth later on_.

## How can you move into pipeline from a nen-technical position?

For those not inside of the VFX industry, it might come as a surprise to learn that many pipeline developers and TD's started out on the artistic side of the fence. One of our own members told his story of starting out in animation and experimenting with python to ease some repetative tasks. Over time they were automating away their job, and sharing tools with the rest of the team. The pipeline team took notice and the rest is history!

This story is not an uncommon one, and there are many studios that are always on the lookout for folks who are interested in making the transition. Some will even provide mentorship and other training resources to help you make the transition if it's something you are interested in.

It's less common, but there are also stories of production folks moving into pipeline. In any case, the story is always the same. Learn a little Python, and find some painful parts of your job to automate. As you get a sense for what is possible you start to see more and more opportunities to create cool pipeline-y solutions.

## Any advice for your former self?

There was a lot of good advice in here, and for the sake of this article I am going to join a few together and rephrase others to try and create an ordered list (starting with the most common).

1. Open yourself up. People want to know what you think, and also have interesting things to say.
2. Assume that you know nothing. There's always more to learn, and the best solution is one that comes from more than one mind.
3. Ask questions. Getting help is encouraged, and copying other people's code is one of the best ways to learn.
4. Don't forget to keep a good work-life balance. There's an endless list of things to do in pipeline, and you won't be able to do it all.
5. It's normal to complain about old code, but choosing to rewrite everything is a bad idea.
6. The 15 minute rule. If you don't know something, give yourself 15 minutes to figure it out, then ask for help.

---

## How do you build problem solving skills?

The easiest thing to do is to find some of your own repetative tasks and just try to write a script which automates it. It can be hard to motivate yourself with fake scenarios, so looking for opportunities in the work that you are already doing can help make things more real.

If you really have a hard time, you can always sit down to code a personal website for your CV. You will need more than just python skills for this one, but working through each piece of the puzzle exposes you to a lot of new problems to solve.

A big part of pipeline is working with others, as we've mentioned. There's a ton of great open source projects that you can get involved with in both the VFX industry and outside of it (openpype, ASWF, etc...). Lots of these projects have lists of problems that need solving, and usually label issues that are easy for first-time contributors.

Outside of open source there are also indy projects that welcome all kinds of help. These usually are volunteer experiences that expose you to the whole production process and have plenty of their own pipeline challenges to be solved.

## Final Notes

As we wrapped up the night, someone asked if some of the pipeline folks that are currently in the industry would be willing to throw out some problems for others to solve and get a feel for the work. We all agreed that this is a great idea! It will require a few people to take the time and come up with some scenarios, so if that could be you, please reach out to me on slack and I will make sure that we get them up on the website or something for everyone to benefit from!

Thanks for reading!
