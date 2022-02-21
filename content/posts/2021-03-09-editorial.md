---
title: "Editorial and Review"
date: 2021-03-09
author: Ryan Bottriell
summary: "A discussion of playback, review, and editorial pipelines lead by Ahead.io"
---

In this session, Ahead.io presented their product Cezanne Studio to kick off a larger discussion about editorial and review pipelines.

### Cezanne Studio

The first minutes of our forum this month was an introduction to [Cezanne Studio](http://cezanne.ahead.io/cezanne-studio/). Cezanne is a review tool and media player first introduced in 2011 and recently updated with a 2.0 release. Alex presented the many features that it has as well as some of the design goals and potential next steps for the product.

Getting a walkthrough of this application gave our conversation a great starting point, and Alex did a great job of showing us around without turning it into a sales pitch.

### Q&A

Having been through the overview, there were a few questions that came up about Cezanne and its features:

- What are the main differences between Cezanne and RV?

  _There is a lot of overlap, but Cezanne is a Qt-based application with a much more modular and extensible construction when compared to RV. Cezanne also has a bigger focus on editorial workflows than RV._

- What are the python API and integration like?

  _Similar to other applications that we use in this industry, you can simply run scripts against the API, but there is also a structure plugin system for deeper integrations, responding to events etc._

  _The GUI and Gl pipeline are also exposed to plugins for doing lower-level plugin development._

- How stable is the USD plugin? How far can it be pushed?

  Currently, the plugin is in alpha. It allows for loading one 3d/USD clip directly into the timeline only (for now). You can select what to show from a USD scene, switch cameras, etc.

- Is Cezanne using the latest python version of otio?

  _yes_

### Open Discussion

To kick off the discussion, Alex wanted to know what we thought about using otio as a method to share and sync timelines between different pieces of software in a live, collaborative way.

This idea is intriguing, and reminds us a lot of NVidia's Omniverse project - which aims to do the same live collaboration via USD as an interchange format.

The larger question here is around how studios are embracing or not embracing these non-linear pipeline ideas that come in with real-time, and other collaborative technologies.

In general, we talked about how there's excitement here but by-and-large this is still an upcoming idea and not something that most studios are jumping into head-first just yet. As pipeline developers, our primary concerns are often along the lines of stability and simplicity. So as much as there's excitement, introducing live collaboration tools doesn't help with that so will need to be driven by a clear desire on the artist side rather than from the pipeline side.

That being said, we also talked about some more contained use cases that we identified. Especially in the era of COVID, having a shared session allows people to continue collaborating as they would otherwise in a shared office space. Realistically, as long as this kind of session is contained to one department it has the potential to enable great opportunities without really affecting the stability of the pipeline as a whole.

The other interesting scenario that we talked about was for previs. If you could connect Cezanne to Maya, and be able to have the two applications linked together, the timeline and transition functionality of Cezanne could prove much easier to use than trying to set everything up directly in Maya. You would need to be able to push out playblasts from Maya semi-automatically or something but it's an interesting idea nonetheless.

### Wrapping Up

There were also a number of one-off ideas and questions that we talked through in this session, but they either don't fit the theme or my notes were not entirely coherent. If you want to get all the juicy details, be sure to come out to our next event!
