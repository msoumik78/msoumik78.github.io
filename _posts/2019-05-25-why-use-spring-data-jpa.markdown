---
layout: post
title:  "Why use Spring data JPA ?"
date:   2019-05-25 13:55:23 +0530
categories: Java
---

# Why use Spring data JPA ?

In this blog, I am going to discuss about one of the newest and finest additions in the Spring group of projects which is Spring data jpa. For the uninitiated, the main advantage that it brings to the table is that it helps in reducing boiler plate JDBC code to a great extent and thereby it keeps codebase clean.

So what really is Spring data JPA ? Do we still need a JPA implementation like Hibernate / EclipseLink when we are using Spring data jpa.
The answer to the last question is yes - we indeed still need a JPA implementation (like Hibernate) when we are using Spring data JPA. 

Spring data JPA is **NOT an alternate** to Hibernate - we still need a JPA implementation like Hibernate. But our basic boiler plate code for a CRUD functionality is drastically reduced if we spring data JPA.

Let us see with a small example:
