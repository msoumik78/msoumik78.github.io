---
layout: post
title: "Structural OO Design Patterns"
date: 2019-02-15 16:55:23 +0530
categories: Design
---

## Behavioural Patterns
These patterns refer to the best practices of how classes/objects should be designed to interact with each other to have a loosely coupled and well designed software.

# Strategy pattern
This pattern advocates how best to write loosely coupled code and one definite way is to use aggregation over encapsulation. So basically this pattern suggests 
that parts of the program which are susceptible to change in future should be encapsulated so that they are replacable.
So ideally when we are using aggregation - during runtime we can pass on the actual behaviour.
As an example - if we are designing a client which leverages encapsulation and since there can be different encapsulation strategies, it would be best
if the encapsulation strategy is defined in an interface and the corresponding chosen implementation is passed at runtime using object aggregation.


# Template method pattern
This pattern is typically for building some framework when we implement some behaviour(which we know at the framework level) and some other behaviour is 
left to be implemented at a lower level (which means outside the framework). 

# Command pattern
This encapsulates method invocation.

# Chain of Responsibility pattern
This is the pattern where a series of components / objects take turns sequentially to fulfill certain responsibilities. One very good example of this pattern is the 
servlet filter.

# Observer pattern
This is the pattrern typically used to build asynchronous communication betwene objects and is the essence of reactive systems in todays world.
In the traditional case - this requires a publisher which emits events at fixed intervals and an observer which consumes the events (and reacts) accordingly to events.
