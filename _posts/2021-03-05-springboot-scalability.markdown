---
layout: post
title:  "Scaling Microservices"
date:   2021-03-05 13:55:23 +0530
categories: MicroServices
---

# How to scale your Springboot based microservice

In this blogpost, I would discuss some fundamentals principles to be followed in scaling out (horizontal scaling) of miicroservices.
In a cloud native containerized environment - scaling out is a cost effective way to ensure that the microservice is able to serve the increasing load and at the most optimum cost possible.

So here are some of the fundamental principles to achieve maximum scalability at least possible cost:
- Ensure that you do not store any state (like storing anything in in-memory caches like ConcurrentHashmap etc.) in your application. If a caching requirement exists, ensure that you store in an external distributed caching service like Redis or Hazelcast.
- Ensure that you deploy your service in containers like docker.
- Ensure that you use a container management platform like kubernetes or cloudfoundry to auto manage the cluster
- Best would be if you can go in an end-to-end asyc stack. And it would be very easy to implement the same using ** Kotlin Co-routines ** which can help you to achieve extreme scalability. Co-routines are like very light-weight threads and they are not blocked but are just suspended. They are a much easier alternative to reactive architecture.
- Last but not the least, consider from a functional perspective if you can migrate out from Springboot and 

