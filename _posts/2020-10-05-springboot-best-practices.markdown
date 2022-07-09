---
layout: post
title:  "Best practices while using Spring Boot"
date:   2020-10-05 13:55:23 +0530
categories: MicroServices
---

# Best practices while using Spring Boot

There is no doubt that Spring Boot is the most commonly used framework when it comes to develop micro services using Java. Main reason for the popularity of Spring Boot is its very quick way of bootstrapping (thanks to its "convention over configuration" philosophy) and its very well supported community.
In this blog, I am not going to the basics of Spring Boot but discuss some of the best practices that I have learnt over time:

* **Usage of profiles and usage of config server** : Some of my recommendations are below : 
    - Never use properties file , always use yaml format simply because yaml is much user friendly as it clearly shows the hierarchy. 
    - Use spring profiles prudently in properties file and in configuration server and here are some more details:
        -  Generic (or environment independent properties) should be declared at the top of yml. 
        -  Then some properties which are environment specific should be declared under specific profiles. 
        -  Any property which you can often change a lot (like some connection timeout, read timeout etc.) and for which normally no code change is required - should go in config server. Because if these properties change, you can just restart config server - no need to restart or deploy application. 

* **Usage of Kotlin as the programming language** - There are several advantages of using Kotln as the programming language and now spring boot has first class support for Kotlin. The main advantages that I see in using Kotlin are :
   - Very concise and readable code - see how multiple model objects can be declared in a small file - we can declare all model or data classes in a single file and don’t need even Lombok
   - Ability to use Kotlin co-routines and obtain much better scalability. With co-routines (which are similar to threads but very very lightweight) - we can make the stack completely asynchronous and hence much more scalable with increasing load. So basically all the methods in the call stack are suspend functions - which means - controller, service and DAP layers are all suspend functions.

* **Usage of  async ability** - For long running tasks, you can use the async ability of Kotlin so that you can process long running backend tasks with a separate dedicated thread pool. This is often used in the below circumstances:
    - When you want to submit long running jobs to backend but don’t want the caller thread to wait for long
    - When for a single incoming request - you my need to make parallel calls to multiple backends and then collect (and collate) the response
* **Usage of Micrometer prudently** -  Using micrometer and the associated metrics and a dimensional metrics system (like SignalFX) can already give you a lot of information about the performance. Like you can simply annotate the controllers as below which will give you very useful info about the average latency of the requests in production

* **Resilience** -In today’s world - resilience is very important and we should build some degree of resilience within our application. So here are some of the common stuff that should be leveraged:
    - If you are connecting to an external cache system like Hazelcast or Redis - you should build some custom resilience so that the client can recover and reconnect in case the cache system goes down intermittently
    - Usage of Retry module of Resilience4j (or even custom retrial with an interval) when calling any external API. This might help as the service often responds during retrial. 
