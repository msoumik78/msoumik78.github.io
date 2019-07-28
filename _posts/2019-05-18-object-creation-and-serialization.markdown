---
layout: post
title:  "Object creation and Serialization"
date:   2019-05-18 13:55:23 +0530
categories: Java
---

# Object creation

We java folks have ever wondered how many ways can we create objects in Java and what are the benefits and pitfalls of each method ?
In this short blog, I am going to discuss the pros and cons of some of the most popular ways of object creation in Java. Please refer 
to my Github project [ObjectCreationAndCloning](https://github.com/msoumik78/ObjectCreationAndCloning) for this.

So let us see the most popular ways of object creation in Java:
* **Using new operator**- This is by far the most well known and most widely used way of creating an object statically from a class. What I mean statically is that the classname is hardcoded and known at compiletime.

* **Using cloning** - This is a very easy and quick way to copy the content of one object exactly as-is into another object of the same class type.

* **Using Reflection** - This is a dynamic way of object creation where the class name is loaded dynamically at runtime. So unlike the new operator of the first case, the class name is NOT known at compile time. 

Now I have done some experimentation to study and compare the performance differences across all these three methods of object creation. Please refer to the class [ObjectCreationTester](https://github.com/msoumik78/ObjectCreationAndCloning/blob/master/src/main/java/objectCreation/ObjectCreationTester.java) of the same repo. Below is a statistic for your reference:
***********************************************************************
Time taken(in ms) to create 10000 objects using new operator : 69
Time taken(in ms) to create 10000 objects using cloning : 5
Time taken(in ms) to create 10000 objects using reflection : 44
***********************************************************************

It clearly indicates that new operator is costliest while cloning operation is fastest and the reflection is actually faster than new operator!



# Deep copy in Serialization
