---
layout: post
title: Introducing WebTalk
date: 2017-10-18 04:00
comments: true
categories: Computing
---

> WebTalk is a [repository][1]{:target="_blank"} of boilerplate code for building web applications using [Logtalk][2]{:target="_blank"} and [SWI-Prolog][3]{:target="_blank"}. It features bootstrap based templates for responsiveness, scaffolding for creating HTML pages and scaffolding for creating RESTful API endpoints. It is a useful starting point for Logtalk projects that require user interaction via a web browser.

There are many ideas in artificial intelligence that I would like to explore using Prolog, both to improve my competence with the language and to take advantage of its declarative nature. The language becomes a bit cumbersome, however, as the amount of code increases in a project. In exploring ways of modularising Prolog code, I came across Logtalk.

Logtalk is an extension of Prolog that provides modern object oriented programming features. This makes for writing clean, reusable, code in a manner similar to that which we have come to expect from modern programming languages. The code can be compiled using many of the popular Prolog implementations such as SWI-Prolog. All this makes Logtalk well suited to everyday programming experiments and I decided to run with it to work on my ideas.

Many of the systems that I want to build and experiment with require some amount of user interaction, and, being a web developer for the past eight years or so, I have become used to providing browser-based interfaces for such interaction. Knowing this, my first experiment was to check how easy it would be to build a web application using Logtalk and SWI-Prolog's HTTP libraries.

The basic requirements for the test application included a templating system to allow HTML reuse, centralised configuration management, a standard way of creating HTML pages and a standard way of creating RESTful API endpoints. Having built an application that satisfies these requirements, I realised that it could be used as a starting point for future projects, not just for me, but for other developers as well. Because of this, I decided to make the code available on Github. The WebTalk project was born!

I will continue to develop this boilerplate code as I think of more common features of web applications that could be included. Hopefully, with time, it will evolve into a versatile system suitable for a diverse range of applications.


[1]: https://github.com/sandogeorge/webtalk
[2]: http://logtalk.org/
[3]: http://www.swi-prolog.org/