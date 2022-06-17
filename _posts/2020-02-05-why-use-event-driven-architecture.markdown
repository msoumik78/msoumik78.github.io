---
layout: post
title:  "Why use Event Driven architecture ?"
date:   2020-02-05 13:55:23 +0530
categories: "Event Driven Architecture"
---

# Why use Event Driven ARchitecture ? 

Why use Event Driven Microservices:
— For better scalability by being asynchronous, say for example in your system during user creation/registration - you will have to send an email.
It does not make sense to make that process synchronous as the SMTP server can be down

— One producer multiple consumer 
	= Example - some change made by the customer in the frontend to his billing address.
	 This needs to be propagated to multiple backend Microservices like credit , debit , loans etc.


Why use Spring Kafka :
 lets us write both producer and consumer side without any bootstrapping, we can just write our business logic
Basically 3 types
