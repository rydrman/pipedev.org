---
title: "Forum - June 2019"
date: 2019-06-27
author: Ryan Bottriell
draft: true
---

A big thank you again to all those who made it out to this month's forum! We had an amazing turnout, made some new friends, and had some wonderful discussions.

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

---

TODO: the other side
TODO: the universal thoughts
TODO: conclusion

How do we maintain large codebases
Coding standards team, or body to help direct things. Not just linting but the whole development process, development best practices
Properly scoped tasks, regular integration, often a lot of issues arise from one person in isolation writing and making a lot of changes and presenting a huge merge
Don’t try to reinvent process to much:
Example: gitflow: master as dev branch with branches for each release, but that caused a huge spaghetti of branches and merges
Be proud of your work
Take the time to not just make it work but to really be proud of it
Teams responsible for their own standards
This can largely be dependent on the people who are there, and the size of the studio
Still involves core tools and core pipelines

## Migrating Code from an Individual to a Team

How does something scale form one developer to like 4 or 5
Communication!!
Depends on the people at some level
Consistent standards are great, being in sync
Feeling included, feeling empowered is a huge thing
There’s something to be said about trust here, and a big thing
Idea: open conference room
Regularly scheduled, open time for face-to-face feedback and communication

## Deploying Python in a Pipeline Environment

Deployment Strategies
A few different strategies for different teams and levels, but everyone responsible in large part for their own code, standards and deployments
Does this create a lot a lot or reproduction
Do we care about things that won’t live long
When do things not live longer than they should?
Properly integrated dev environments that support standards
How do you quantify the gains from standards enforcement?
What are the best prices of information to ask of contributors
Maybe just documentation about what you did

Local, shared drive
What is the goal of either
Pip-env
Resolving things can be slow
Virtualenv
Deterministic environments, is this the goal, is this the
Being able to go back to days past, reproduceability
But not everything is part of that (farm, services)

Code Insight

Code Ownership
The balance between ownership, collaboration, dictator

## Things you Need At Scale

Project managers, architects
Long term and short term planners
Requirements gathering, tracking, roadmapping
Are these really scale problems

# Managing Documentation

Maybe even release notes
Developers don’t necessarily need that
How do you measure the imapact of good documentation on users?
Firefox (good example of documentation done well)
IF we are honest, developers are really bad at writing docs that are accessible to a large set of users
Answer good questions
What are you looking at
Cookbook type stuff
Reference to go much farther
Generate docs from code:
Still needs to be searchable and accessible
Easy feedback to find and mark documentation as out of date
Someone on the other side of that
Sometimes documentation can be collaborative
accessible

Culture
Very common theme in almost every discussion


## Type Hinting

It’s great! and worth the time. This is especially true in Python 3, where it doesn't need to be hidden in ugly comments. A few members expressed concern that type hints remove some of the simplicity and elegance of the language itself, but it seems that could be argued both ways.

## Technical Issues At Scale

What is python at scale?
NFS problems?
Servers?
Env Vars - max character limits
NFS - Rez
Myths? (mention previous forum)
Once or twice rez not being able to resolve
NFS and stat-ing in rez can be a problem
Importing processes can have issues because of pythonpaths
Maybe they were really problems a long time ago
At what point is hardware cheaper than the dev time to fix these things
Multithreading - Multiprocessing
Difficult for web servers
Async in python 3
Something over python that manages subprocesses
Py 3.8 (interpreters) spawn new interpreter sessions withing the same runtime…
Analyzing Dependencies
Monkeypatch importing to track the call graph
Pump that into something else and generate dependency graphs
Pydeps, not alwas the best
The hardest part is analysis of this information
Runtime dependencies
Getting rid of these can help, but can also be hard
Reload statements
Necessary evil?
Consensus is largely do not use them
Not understanding the impact of the reload statement
PYC files
Precompile, disable, neither?
Seems to run the gamut
Probably making a choice and comitting is fine


## Further Reading and Links

The [Clean Code/Coder/Architecture Series](https://www.pearson.com/us/higher-education/series/Robert-C-Martin-Series/348084.html) of books are a must read for those who want to go beyond just writing code that works. These books are a great knowledge base to help with writing code that functions well in large teams and at larger scales.

[Sonar Cloud](https://sonarcloud.io), along with its open source and self-hosted [counterparts](https://www.sonarqube.org/), provide code quality analysis that looks at many different aspects of cleanliness and maintainability. This kind of thing can provide useful insight and feedback to developers looking to improve the code that they write.
"Pep8-ish" is a recommended YouTube video on the Python pep8 standard (link still needed)
"Don’t Pep8 Me" is another such video (link still needed)

[Black](https://github.com/python/black) is an "uncompromising" code formatter for Python, which means that you can stop talking about how it should be done and just standardize

[How Google Works](https://www.amazon.ca/How-Google-Works-Eric-Schmidt/dp/1455582344) is a recommended read if you are interested in learning about how one of the largest software companies in the world works

[Powerful](https://www.amazon.ca/Powerful-Building-Culture-Freedom-Responsibility/dp/1939714095) is another recommended read on the culture and process of Netflix, and how they manage their teams and scale

[The Pipeline Conference](https://thepipelineconference.com) is having it's inaugural event alongside Siggraph this year if you want to attend
