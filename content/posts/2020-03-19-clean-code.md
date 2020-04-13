---
title: "Forum - March 2020"
topic: "Clean Code vs Production Deadlines"
date: 2020-03-19
author: Ryan Bottriell
summary: "This forum started off, as many do, with a simple question: What is clean code?"
---

Thank you to everyone who logged on for our first **virtual** forum! It's a crazy time right now with everyone transitioning to or already working from home, but I'm so happy that we could still come together and talk shop. Given how things went, I think that enabling remote participation should be a goal for every forum!

# Clean Code vs Production Deadlines

This forum started off, as many do, with a simple question:

> What is clean code?

Given that we were jumping into this topic, it seemed reasonable to first make sure that we were all on the same page. _"Production Deadlines"_ is more or less defined as the delivery schedules imposed on our work by those that need to use it to create the content that our studios are paid to create.

_"Clean Code"_, however, is an arguably much less concrete topic and one that we could not as easily summarize. For at least a few of us, _Clean Code_ by Robert Martin is our de-facto standard definition, and is a recommended read. As a book, though, it's not a very succinct definition for the phrase.

Trying to boil it down, we came up with a few vaguely descriptive phrases. Clean code to us is...

- not necessarily simple, but easy to understand
- easy to navigate, read and follow
- both easy to test, and well tested
- easily extended
- not fragile (aka you are confident that touching it will not cause it to break in unexpected ways)
- in the right domain and at the right abstraction level
- well cared for by a development team

Additionally, we started to talk about API boundaries. Although the shape of the API does not necessarily correlate to clean code, it does get you a long way towards making the code base maintainable. A well defined and stable API boundary gives you the freedom to refactor and clean a codebase without affecting the way it's consumed.

The other topic that came up in the discussion of clean code was tooling around style guides, formatting and linting. Generally, we agreed that using a style guide or linter is not necessary for clean code, nor does it automatically create clean code. Nonetheless, we believe that they can provide valuable insight into your codebase; ease with legibility; and reduce the need for stylistic discussions in code reviews.

## Production Deadlines

Having worked our way through the idea of clean code, we decided to fold back in the idea of production deadlines, and how the two relate.

Technical debt was the first term to come up. The push and pull between doing it fast and doing it right can been seen as the management of technical debt. When we build things quickly and cut a few corners to meet a tight deadline, we accrue this debt. It's not necessarily bad, but must be paid down regularly to keep it at a manageable level.

A really good example of this, is when you need to add a feature to a system or codebase that isn't really set up to do so. Do you take the time to understand the original design, and refactor the system as need to extend nicely to the new feature? Or do you hack the feature on top of what's there to get it done? And most importantly, if you do hack it in, do you schedule time to circle back and do the refactoring properly?

This brings us to the next question: How do you sell clean code to managers and production? And how do you justify and get approval for that refactoring and redesign time?

## Business Value

Ultimately it seems like you would have to collect metrics on lost productivity due to maintaining messy code, or perhaps the impact to production when things become unstable and break unexpectedly. This can still be a hard thing to do, and we didn't have a whole lot of advice in the room for how to approach this. [SonarCloud](https://sonarcloud.io) did come up briefly as a something that measures technical debt and can assign real numbers to the cost of fixing it, but it seems far from a complete solution.

The deeper question we then asked was whether or not it should be on production/management to sign off on clean code, or paying back technical debt. If we agree that we as professional software engineers we have a duty to produce clean and maintainable code, then it would mean that we must take responsibility for such choices.

So how does one take such responsibility? One way is to include time for design, refactoring, and cleaning into all of your development tasks and time estimates. In this case we are opting not to deliver unclean code, or at least ensuring that a rapid delivery requires additional time to be spent afterwards - not just moving on to the next feature.

The hard truth about what we do, is that the frames we deliver are what make the business money. Our software helps with that, but is still a {{% tooltip "cost center" "A cost center is a department or function within an organization that does not directly add to profit but still costs the organization money to operate. ([source](https://www.investopedia.com/terms/c/cost-center.asp))" %}} to the business. No matter what we do, we should believe that our actions add value to the business.

## Day-to-Day & Best Practices

At this point in the evening, our discussions became a bit more focused on practical implications of the topic.

### Testing

Testing your code properly is one excellent way to make it cleaner and more maintainable. With a suite of automated tests that can be run, any developer can much more easily make changes and be confident that they haven't broken anything.

Tests also naturally document the behaviour of your code - which can give others a lot of understanding about what it does, and how it's used.

Some of us have found that tests can also become their own technical debt. In some cases, tests that are far too specific or intricate become outdated or need to be updated with every little code change. These tests are not inherently bad, but in larger numbers they just start to make changing a codebase very cumbersome.

Some of the best tests to write in the context of this discussion are ones that test your code at the API level, or human interface level. These could also be considered black box tests - where the test has no access to, or knowledge of, the internal workings of the codebase.

We also talked about property testing, which many of us were not aware of. This is a technique in which you describe inputs and outputs by their properties, and the framework generates a large set of permutations for inputs and outputs to test the properties.

### Deployment

We recognized that software deployment is a part of this picture, as well. Taking the time to establish robust rollout and rollback processes is often one of the first items on the list to be bumped by a tight delivery.

Fortunately, this is also something that is easier to sell. An automated deployment process can save developers a lot of time and stress that would otherwise be spent navigating a manual release process. Additionally, a quick and accessible rollback button can reduce downtime significantly for production.

### Build A Toolchain

We asked ourselves the question: why aren't people already doing all of these things? Even many of those in the room could not say that they tested regularly or followed these practices with the majority of their work.

One of the answers to this question is that the barriers to entry are either too great or too many. For some, they have never written a unit test or seen an automated test suite first hand - and jumping in on your own is a big task.

For others, it's often the DCC environments that we use. Running code to execute within Maya, for example, has two very important implications. For one, it means that the code often relies upon Maya itself, requiring the application and licensing to be available on machines that execute the tests, and that whatever test framework you are using is appropriately installed to run `mayapy` or set up python in the proper way so that it can load the maya libraries.

Above those technical challenges, is the very nature of a DCC application. These applications generally expose some kind of 'scene' data to be queried and manipulated. This often acts as one giant and complex global state for the application, meaning that the number of {{% tooltip "pure functions" " a function where the return value is only determined by its input values, without observable side effects ([source](https://www.sitepoint.com/functional-programming-pure-functions/))" %}} in a maya tool is likely to be quite low. More directly, it makes writing testable code very hard. Usually, the global state going into a procedure is very specific, requires a lot of set up, or the sheer number of possible global states is so great that it makes testing for all possible error cases very hard.

All this to say, that there are a number of hurdles in the way of setting up automated testing and supporting good workflows for developers. Solving some of these problems one, and providing the solutions in a toolchain or even training for developers to leverage might go a long way in getting these practices going.

### Evangelize for Clean Code

This example of privacy came up: the general population use to know next to nothing about online privacy and information security. Over the last few years, technologists, researchers and the media have been preaching the need for us to get smart with our data, and to be aware of who is collecting it and for what. This has lead to some great new legislation and created a population that demands security and privacy from the companies and services that they interact with.

Perhaps we need to be doing the same for what we believe in. If we believe that our technology needs to be built out of clean code and that every deployment should be tested and automated, then we must preach it. We should find ways to teach our users to understand and even demand high quality software that is delivered in a reliable way.

And let's not forget about our fellow team members. We must also not succumb to the status quo. It may not happen over night, but we can work these best practices into our planning meetings, design sessions and code reviews. Over time we can support our team through the learning and discovery process as they begin to follow these practices.

### Know Your Users

As we discussed the ideas of communication between engineering and production, it came through that not every studio is the same position. This seems like an obvious point to make, but a few interesting ideas came out of this.

In a small studio, or on a smaller project developers can often find themselves working directly with users. Sitting within earshot of the artists that are running your code changes the delivery and feedback loops entirely. In this scenario, it might entirely be the case that you and your desk mate are running code off of a shared drive, running, testing and making changes in a really tight loop.

One could argue that stopping to write unit tests in this kind of workflow is counter-productive, especially given the testing challenges that we talked about before. The ideals of {{% tooltip TDD "Test Driven Development" %}} might disagree, but when the cost of a bug or breakage is a tap on the shoulder and an impromptu coffee break, the risk is pretty low.

Finding this workflow in a larger studio is not impossible as well. The beta user seemed to us like a rare and valuable resource for the clean coder. These are the artists that want to get the latest before anyone else, and are happy to test it all out, knowing full well that they may hit a few issues along the way.

Depending on the size and proximity of this group, you are likely still going to want to set up reliable deployment practices, and internal automated testing. Just make sure that these users have an easy way to switch back and forth from the stable release - so that their early testing is not rewarded with lost productivity and waiting around.

At the far end of this spectrum is the status page. A single place for people to quickly understand the state and status of your software and services. In large organizations, this kind of information needs to be made readily available, since the regular channels of communication are often long and cumbersome compared to the whole studio in a single room.

## Conclusion

This was quite an interesting one for sure. If anything, I think we learned that clean coding is very much something that everyone wants to be doing, but that more often than we are proud of does not happen.

Is this really an effect of deadlines in production, though? Based on our discussion, it seems like the answer is probably yes, but only some of the time. More likely, it seems like a problem of culture, training, tooling and support. So I shall leave you to ponder that thought until next time.

Thanks for reading!

## Further Reading & Links

- [Dropbox Tech: Rewriting the heart of our sync engine](https://dropbox.tech/infrastructure/rewriting-the-heart-of-our-sync-engine) - Not just for the article, but contains a wonderful check list to follow when you are considering a rewrite
- [Hypothesis](https://hypothesis.works/) - a property-based testing framework for python
- [Black](https://github.com/python/black)  - an "uncompromising" code formatter for Python
- [Dockerfile linter](https://github.com/hadolint/hadolint)
- [Bash linter](https://www.shellcheck.net/)
- [PowerShell linter](https://github.com/PowerShell/PSScriptAnalyzer)
- [Statuspage](https://www.atlassian.com/software/statuspage) and [Cachet](http://cachethq.io/) are status page products which can help report the state of your operations
