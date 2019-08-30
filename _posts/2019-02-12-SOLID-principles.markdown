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

## Interface Segregation Principle

## Dependency Inversion Principle
