---
layout: post
title:  "Best practices for designing Microservices"
date:   2020-04-05 13:55:23 +0530
categories: MicroServices
---

# Best practices for designing Microservices

Some of the sesign patterns that should be followed to make a maintainable microservices :

* Use single responsibility principle - every single Microservice should have a single purpose, this will help in better maintenance in future - each Microservice can change / evolve regardless of other Microservice
* Use complete separate datastore
* Use a container management platform like kubernetes
* Use monitoring and alerting with micrometer and prometheus/SignalFX 
* Use JWT for authentication/authorization of each Microservices
* Have separate Githib repo and corresponding maven / gradle build for each set of Microservices
* Assume that the server is stateless - there is no concept of session n the context pf Microservices
* Do not design for a distributed monolith - what I mean to say here is that don’t develop a shared common library - say in one Microservice you need one version and in other other version. Better not to use a shared common version.
