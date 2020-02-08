---
layout: post
title:  "Why use Microservices ?"
date:   2020-01-05 13:55:23 +0530
categories: Java
---

# Why use Microservices ?

In this blog, I am going to discuss about microservices. Well lets accept the fact that microservices architecture is the order of the day. Everybody is de-composing their old fashioned monolithic application into small chunks of manageable microservices.
That way the application consists of almost independent multiple projects which can be independently worked on by different persons. It takes de-coupling to the next level.

So I have created 2 sample microservices for a pseudo banking application:
* authentication microservice
* core banking microservice

The first one which is the authentication microservice exposes a REST endpoint like : /retailBanking/authenticate and is a POST one. If the credentials are correct, only then it returns a valid JwT, else an exception is thrown for invalid credentials. 

The second one is a sample core banking web service exposes a REST endpoint like : /retailBanking/getAccountBalance and is a GET one. Some more aspects:
* It accepts the JWT in the Authorixzation header and also the userName as a request parameter
* If the request does not contain the JWT - it will not be accepted
* If the request contains an invalid JWT - even then it will not be accepted 

## Json Web Token

This is one of the most widely used ways of securing a web service. Well a json web token contains 3 parts : header, payload and signature. 
All microservices post authentication - normally accept a Json web token. If the token is valid - only then 

Your confusion can be that anyone can generate a JWT and present to the server - but that will be rejected as the JWT will not match as the signature is different as that person does not have the secret key for signing.
Hence stealing json token will not help, if the json token is valid - then the server understands that it has indeed been issued by the authentication service.

