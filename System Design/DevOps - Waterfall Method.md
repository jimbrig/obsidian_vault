---
creation date: 2021-05-06 17:53
modification date: Thursday 6th May 2021 17:53:14
tags: ["#note"]
author: Jimmy Briggs
---

# DevOps - Waterfall Method

For a long time, software development projects used the waterfall model for their software development lifecycle (SDLC). The waterfall approach looked like this:

![diagram showing the waterfall model of system development](https://miro.medium.com/max/60/0*pL2-XY8eOsplMMRQ.png?q=20)

![diagram showing the waterfall model of system development](https://miro.medium.com/max/1280/0*pL2-XY8eOsplMMRQ.png)

(Peter Kemp / Paul Smith — [Wikimedia Commons](https://en.wikipedia.org/wiki/Waterfall_model#/media/File:Waterfall_model.svg))

The stages of the waterfall model were as follows:

-   **Requirements** — Clearly define the requirements of the application. In this phase, it’s important to capture all of the possible requirements for the system.
-   **Design** — Use the requirements determined in the previous step to work out a system design. This is the part where we would normally also define what hardware and software we need for our software to work.
-   **Implementation** — Using the design document (which defines the architecture for our app) we implement the expected functionality in small programs. Every unit that we create is developed and tested against its functionality.
-   **Integration and testing** — The units that have been developed are integrated into a system after being tested individually. After the system has been integrated, the entire system is then tested for any outstanding bugs or issues.
-   **Deployment of system** — Our hard work is coming to an end! The testing is completed, and now we can deploy our app to the stores.
-   **Maintenance** — After the deployment has been completed, it’s possible that issues can crop up in the future. Over time, patches are released to resolve problems that were not encountered during the initial development or implementation.

Of course, there is nothing wrong with this approach. Development teams used it for years, and nobody suffered because of it. When the method was adhered to, the result was high-quality software. One reason for this was that the steps only progressed in a linear motion from left to right — for example, the design phase could only begin once the requirements phase was complete, implementation could only be started when the design was finished, and so on and so forth.

On the surface, this approach seems ubiquitous. In systems where the requirements were well defined, it worked quite well. But more recently, we’ve seen fewer software projects adopt this methodology, and instead, we’ve seen the rise of DevOps as a more modern, flexible development framework. But why is that?

## What’s wrong with the waterfall?

In a perfect world, the waterfall model would probably always work fine. Unfortunately, as developers, we know that we don’t live in a perfect world. And this can introduce some difficulties. For example, people’s requirements can change, and this change can occur at an inopportune time.

To illustrate, imagine that your customer has requested an app that can let users book a car to rideshare. You’re at the implementation stage, and suddenly, a new competitor comes to the market with a product that lets people get food delivered to their house from nearby fast-food stores.

If this is an area you’d also like your app to compete in, you can’t break out of the implementation stage and suddenly revert back to the design phase to put your function in. If we went against this and reverted back to the design phase anyway and then tried to resume from there, then we wouldn’t technically be following the waterfall model anyway, and the benefits yielded from following a software development lifecycle would be largely lost. Software lifecycles are supposed to ensure a certain level of quality, so if you just disregard them and do your own thing, you do so at your own risk.

![two rows of people sitting in cubicles working at computers](https://miro.medium.com/max/60/0*LCN7rmJbT7y7F8rB.jpeg?q=20)

![two rows of people sitting in cubicles working at computers](https://miro.medium.com/max/1125/0*LCN7rmJbT7y7F8rB.jpeg)

Photo by [Tima Miroshnichenko](https://www.pexels.com/@tima-miroshnichenko?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from [Pexels](https://www.pexels.com/photo/people-working-in-a-call-center-5453837/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)

## Everyone’s in their own silo

In a pre-DevOps world, the people involved in the deployment and support of applications were largely siloed. Your developers would work in one space, your quality assurance (QA) team in another, and the support staff for your app in yet another. That’s not including the people who are required to actually host your app, plus everyone else who is involved in the reliable hosting of your app.

This can lead to some communication problems, as developers produce new releases, give them to the QA team, deploy them to a test environment, and then repeat this until a release is finalized. For example, because the hosting team is so far removed from the development side of things, it is possible (and has happened) that the developers could make something only for the hosting team to rebuff their work because it won’t work in the hosting environment.

***
Links: [[System Design]]
Source: [What Is Mobile DevOps, and Why Should You Care? | by Lew C | May, 2021 | Better Programming](https://betterprogramming.pub/what-is-mobile-devops-and-why-should-you-care-7e9094c8b034)

