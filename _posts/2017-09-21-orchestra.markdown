---
layout: post
title: Orchestra - A Platform for Mobile Crowdsensing
date: 2017-09-21 13:35
comments: true
external-url: 
categories: Computing
project: Orchestra
---

>Orchestra is a platform for [mobile crowdsensing][1]{:target="_blank"} that aims to be **generic**, allowing arbitrary crowdsensing scenarios, and **online adaptive**, allowing sensing task specifications to be adjusted without taking the system down. This post provides an overview of my motivation for starting the project and the work that has been done thus far.

In the spring of 2016, during my master's studies, I completed a course in [agent][2]{:target="_blank"} systems and their applications. This was my first encounter with (multi) agent systems and I quickly became intrigued by the idea of autonomous software entities capable of collaborating to solve problems. I imagined creating colonies of such agents that would trivialise most of my day to day tasks, including making money, allowing me more free time to do the things I love---play basketball and read books---and ride off into the sunset of early retirement. Ambitious much? :)
 
I soon realized that the gap between my imagination and reality was a significant one, and I would need to spend years tinkering with multiagent systems to achieve anything close to what I had envisioned. It would require a significant amount of work in various sub-fields of artificial intelligence, such as [constraint satisfaction][4]{:target="_blank"} and [unsupervised learning][5]{:target="_blank"}. But first, I would need an easy way of spawning these agents.

Since I had hands-on experience, from the lab work of the course I did, using the [JADE][3]{:target="_blank"} platform to create agents, I decided to use it as the base of my investigations. JADE is easy to program and is said to be [FIPA][6]{:target="_blank"} compliant, so I thought it would be as good a starting point as any. I decided to make it my semester project, for the agent systems course, to build a cloud platform that would allow me, or any other interested party, to launch JADE-based multiagent systems with just a few clicks. The outcome of this project was [PhaseMetrics.io][7]{:target="_blank"}.

While developing PhaseMetrics.io, I came across [a journal article][8]{:target="_blank"} describing the field of mobile crowdsensing, its applications and existing challenges in adopting / commercializing such systems. Many of the problems outlined in the article struck me as potential applications for multiagent systems. Because of this, and knowing that I needed something to focus on for my master's thesis, I decided to start working on Orchestra, which would exist at the intersection of multiagent systems and mobile crowdsensing. This was a diversion from my initial plans of glorious, multi-purpose, agent colonies, but, nevertheless, interesting testing grounds for the kinds of algorithms I would need to develop in order to achieve my initial goals.

The plan of action was simple. Develop a system that is generic enough to handle the creation of arbitrary crowdsensing campaigns, and facilitates online adjustment of sensing task specifications. Once this phase is completed, I would be able to start injecting elements of AI to give the agents perception and reasoning abilities, based on crowdsensed data, allowing them to solve complex optimization problems. Easier said than done!

I faced many challenges while coding the system but I persevered and ended up with a [management interface][9]{:target="_blank"} to create sensing campaigns and sensing task specifications, and an [Android application][10]{:target="_blank"} (currently in beta) that allows (Android) device owners to contribute sensor data to the campaigns. There is a possibility to extend the platform to any device that supports running a Java Virtual Machine, and this will be the focus of some future iterations of the project.

I am now at the point where I will start applying to the platform to real world problems. Some of the intended applications include behavioural analysis and asset tracking, an could involve recreating the work of different researchers. Recreating projects done by various mobile crowdsensing researchers will serve to validate the genericity of the platform, thereby building trust in it and improving the chances of uptake within the broader crowdsensing community.


[1]: https://en.wikipedia.org/wiki/Crowdsensing
[2]: https://en.wikipedia.org/wiki/Software_agent
[3]: https://en.wikipedia.org/wiki/Java_Agent_Development_Framework
[4]: https://en.wikipedia.org/wiki/Constraint_satisfaction
[5]: https://en.wikipedia.org/wiki/Unsupervised_learning
[6]: https://en.wikipedia.org/wiki/FIPA
[7]: http://phasemetrics.io
[8]: http://doi.acm.org/10.1145/2794400
[9]: http://orchestra.phasemetrics.io
[10]: https://play.google.com/store/apps/details?id=io.phasemetrics.orchestra
