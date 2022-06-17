---
layout: post
title:  "Best Practices of REST API Design"
date:   2020-03-05 13:55:23 +0530
categories: MicroServices
---

# Why use Microservices ?

In this blog, I am going to discuss about microservices. Well lets accept the fact that microservices architecture is the order of the day. Everybody is de-composing their old fashioned monolithic application into small chunks of manageable microservices.
That way the application consists of almost independent multiple projects which can be independently worked on by different persons. It takes de-coupling to the next level.

So I have created 2 sample microservices for a pseudo banking application:
* authentication microservice
* core banking microservice

The first one which is the authentication microservice exposes a REST endpoint like : /retailBanking/authenticate and is a POST one. If the credentials are correct, only then it returns a valid JwT, else an exception is thrown for invalid credentials. 
