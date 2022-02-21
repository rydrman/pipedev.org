---
title: "Leveraging Containers in a Pipeline"
date: 2020-06-17
author: Ryan Bottriell
summary: "How can we or how do we use container technologies in a pipeline context?"
---

To kick off this session, we started talking about what a container is. Everyone got a chance to put the idea into their own words and speak a little bit about their experiences with it. If you don't know what a container is, I recommend doing some introduction tutorials for docker, or ask a colleague for a demo! We also spoke about the underlying technologies of a container to make sure that we all had a reasonable base for the discussions to come. I can't really share the that we went over here, but if you want to do your own digging lookup Linux namespaces, cgroups, the chroot command, and overlayfs. These four pieces of tech are the foundation of what a container is.

Outside of our industry, containers have really taken off. They are primarily a web technology - isolated and predictable like a virtual machine but lighter and faster. Putting your server or other application in a container gives you complete control over the runtime environment, ensuring the ultimate consistency between development and production.

Containers are also generally designed to be much more ephemeral. A stateless application running in a container can be really easily scaled out or back in and distributed across many physical hosts as needed. This promise does not come without conscience design, though, which is something we will touch on later.

### Who is Currently Using Containers?

There are a few use cases that we have seen or heard of in our industry. The most obvious one is the use of containers for running the web services that make up our pipelines. Some are building new services into containers, converting old ones, or designing entirely new microservice-based pipelines that leverage containers from day one. Here we're all leveraging containers to do what containers do best, but are there other use cases that are more unique to our industry?

Some of our render farms do use Linux cgroups to help carve out resources on farm machines, which is a container technology. We also talked about exploring the use of Nvidia GPU containers for rendering or other workloads, but it doesn't seem like anyone has looked at that in any serious capacity.

Some of us have also had good success using containers to standardize their build environments. The [Academy Software Foundation (ASWF)](https://www.aswf.io) also has started providing container images that represent the [VFX reference platform](https//vfxplatform.com), making it easier to build against the recommended software versions.

### The Problem with VMs

In many ways containers are a sort of natural successor to the VM. Collectively we've found that VMs are too easy to bolt additional things into. Especially if it's slow or difficult to request or provision a new VM in your studio, there's a temptation to add new applications to existing VMs instead, having them do many things. This can cause a number of issues like overloading the VM, linking the stability of two unrelated applications, and making it harder to understand what any given VM actually does, to name a few.

Similarly, we often use the term 'snowflake' when we talk about VMs. This is because the usual way to set up a VM is by first creating it from a base image, and then manually going into the VM and installing the required software and components for the app that it will run. This makes every VM unique, just like a snowflake. If something happens to it, it may be impossible to rebuild just the right way and get things running. Of course, a diligent team using tools like [Ansible](https://www.ansible.com/overview/how-ansible-works) can greatly if not entirely remove this issue.

With containers, many of these problems are removed simply because of the way the tools and infrastructure are set up. The `Dockerfile` acts as a repeatable recipe for building the container, and is often able to be fairly simple because it starts from a predictable base and does not need to be concerned with any competing applications or software existing in the same container. Creating and running new containers is generally much more self-service and repeatable as well, and since the image is created before running the container, there's generally less start-up time compared to VM infrastructure where the configuration/provisioning stage is only run after the VM is created.

Of course, there are complexities and edge-cases to all of the statements being made here, but were talking more generally about the promises and personal experiences with both pieces of tech.

### What We Are and Are Not Running

A quick poll of those present showed that most of us are running some containers in production. Usually these are newer services or workflows that had the luxury of starting fresh. That leaves the largest percentage of applications not running in containers, and largely without the bandwidth or will to convert them. _Don't fix what 'aint broke_, as they say.

So aside from scheduling, are there other inhibitors to the use of containers in out pipelines. For one, we recognize that the dynamic nature of our software environments is not particularly container-friendly. Unlike an isolated web service, on the desktop side we have many contributors all writing code and plugins that are selected and loaded at runtime. The isolated and self-sufficient nature of containers makes this kind of environment at least require updates very often not to mention the crazy matrix of combinations you might need to bake out images for. This is not only true for containers, but other self-contained environments like those created by Conda or pip.

The other thing that we'd all love to be able to do is run DCC workloads or testing in containers. Often the lack of GPU and display access makes this difficult, not to mention the licensing and other technical challenges of trying to get a DCC application to run in a container. The ASWF and its CI efforts might prove to be very helpful in this area and we're all watching that in anticipation.

### Conclusion

Overall, we are excited to see what the future of containers might bring for us, but are not really seeing any extremely novel uses of containers in a pipeline context that you wouldn't already see in the web and other industries. If you have something of your own we'd love to hear about it, maybe a show-and-tell session?

Thanks for reading!

### Further Reading & Interesting Links

- [ACM Paper](https://dl.acm.org/doi/pdf/10.1145/3105692.3105702) on building a microservices pipeline
- [NVIDIAs GPU Containers](https://github.com/NVIDIA/nvidia-docker) for interacting with the host GPU from a docker container
