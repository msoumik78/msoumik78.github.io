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
-----------------------------------------------------------------------  
Time taken(in ms) to create 10000 objects using new operator : 69  
Time taken(in ms) to create 10000 objects using cloning : 5  
Time taken(in ms) to create 10000 objects using reflection : 44  
-----------------------------------------------------------------------  

It clearly indicates that new operator is costliest while cloning operation is fastest and the reflection is actually faster than new operator!



# Deep copy in Serialization

Another interesting aspect of Java cloning is that by default - the clone() method does shallow copy only whioch means the object references are not replicated but instead - both the original and cloned objects internal object references pointt to the same reference. So in order to overcome this, there are various ways in which we can **properly clone** nested objects also, this approiach is known as **deep copy**. Below are some ways in which the same can be achieved:

* Normal serialization which means writing the object to a disc and then reading it from the disc - This is the basic serialization where we serialize the object bytecode into local filesystem and then de-serialise it from file system to in-memory object. However the biggest drawback is that it needs to have write privilege on local filesyetem which can be a potential security issue.  

* In memory serialization - This is an advanced technique of the above where instead of writing to the disc, we can do the serialization and de-serialization from an in-memory location from within the heap memory of the JVM. I have written this [example](https://github.com/msoumik78/ObjectCreationAndCloning/blob/master/src/main/java/deepCopy/DeepCopyUsingInMemorySerialization.java) to demosntrate this.  

* Using Apache's SerializationUtils class - This is still another technique where we use Apache library Serializationutil to accomplish this.  I have written this [example](https://github.com/msoumik78/ObjectCreationAndCloning/blob/master/src/main/java/deepCopy/DeepCopyUsingSerializationUtils.java) to demosntrate this.  

