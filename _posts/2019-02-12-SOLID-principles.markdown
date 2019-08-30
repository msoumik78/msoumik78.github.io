---
layout: post
title: "SOLID Design Principles"
date: 2019-02-12 16:55:23 +0530
categories: Design
---

# SOLID principles
One of the fundamental aspects of any good object oriented design (and which makes a quality software) is its degree of compliance to SOLID principles. In a nutshell, SOLID means the following:
* S - Single Responsibility Principle
* O - Open Close Principle
* L - Liskov Substitution Principle
* I - Interface Segregation Principle
* D - Dependency Inversion Principle

## Single Responsibility Principle
This means that a class/method should have only one purpose and in general, it should be changed for only one reason. 
A common violaton of this principle is the case when we are performing business logic in the DAO/ Persistence layer. Ideally business logic should be coded in the Service layer and only database interactions should be done in the DAO layer. So if the DB changes in future from RDBMS to NoSQL - only DAO layer should be impacted and service layer should not be impacted. Similarly if there is a core change in the business logic, only service layer should be impacted and not the DAO layer. **Any class/method should have only one reason to change and that is why classes and methods should be smaller.**   

## Open Closed Principle
This is another fundamental principle of good software design and it means that **classes should be open for extension and closed for modification**. What this means is that - we should design classes in a way that in future due to enhancements (or even changes) in requirements - they should not be modified. May beb they can be extended to provide additional behaviour. The danger of modifying existing class is that it can introduce regression bugs in already well tested code.
There are various ways in which thius principle can be followed and below are some tips:
* You should never ever write any logic in the superclass which involves the sub class
* Try to use strategy design principle as much as possible - please also refer to my blog on "Clean Code" where I have given an example of how this can be achieved 

## Liskov Substitution Principle
This is another principle which ensures good software design and it basically states that if your program expects a base class at some places and during runtime, it receives a subclass of that base class - there should not be any change of behaviour in your program. Which essentially means that the base class and the subclasses can be used interchangeably.
A thumb rule to ensure that this principle is not broken is to keep the base class as simple as possible without bloating it up and the child classes should all call base parent methods to the maximum extent possible to ensure any inconsistent behaviours between the base class and the child classes.

## Interface Segregation Principle
This principle basically states that interfaces should not be big and should not contain many method definitions. In fact - smaller the interfaces more is the chance that they need to change in future. Ideally interfaces should be smaller and specific to the clients/callers which refer them and not generic in nature. This makles software design more cohesive. 

## Dependency Inversion Principle
This is another very important principle which ensures loosely coupled software design if followed religiously. Basically we need to keep in mind the following:
* High level modules hould not directly depend on low level modules - there should be a layer of abstraction in between
* And this abstraction layer should not depend on details
One thumb rule that I always follow and recommend is that never use the new operator in the high level class to instantiate the low level class. Rather inject the interface (corresponding to the low level class) in the high level class by way of constructors and that's how - the high level class and low level class can stay loosely coupled.

