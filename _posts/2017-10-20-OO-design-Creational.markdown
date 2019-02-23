---
layout: post
title: "Creational OO Design Patterns"
date: 2017-10-20 16:55:23 +0530
categories: Design
---


# Creational Patern

Singleton - Ensures that only 1 instance of a class gets created. Ways of creating a singleton:
* Having a private constructor and a pulic static getInstance() method which creates an object and returns the object to the caller.
* The above option can potentially create multiple objects in a multithreaded environment and hence getInstance() method should be synchronized. 
This will ensure that only 1 instance gets created even in a multi threaded environment. 
However synchronizing all access to the getInstance() method can degrade performance.

* To avoid the performance degrade , a double checked locking (and also making the _instance variable marked as volatile) can be used as descibed
  below:
   
   {% highlight ruby %}
   public Object getInstance() {        
      if (_instance == null) {              
          synchronized (){               
              if (_instance == null) {                             
                    _instance = new SingletonInstance()                                               
                    }                                      
                 }                                
             }                     
             return _instance           
       }           
   {% endhighlight %}    
       
* Another option is to do an early loading of the _instance variable in a static initializer before any client calls.
* Another option is to use Enum to implement Singleton

Factory - This design pattern encapsulates object creation. It is very important to seperate the object creation from object usage so that both of them can vary independently.Below are the variants of the factory pattern (In fact Spring framework is one of the most popular implementations of the Factory design pattern):
* Normal Factory - This is just a method which encapsulates object creation and hides all object creation details from the client. 
Spring IoC is a classic example.
* Factory Method - Defines an abstract method in the superclass and lets the subclass to implement the method (inheritance way)
* Abstract factory - Defines an abstract factory to create concrete factories which in turn can create products (essentially there are 2 inheritance trees - one of the factory and the other of the product). This is more of an aggregation way.

Builder - This pattern is used to avoid telescoping (multiple) constructors and help to create the big object in steps. Gof Defines it as "Seperate the construction process of objects
from its representation so that the same construction process can create multiple representations." Components are : 
* Builder interface - exposes the various methods 
* ConcreteBuilder implementation - implements the methods 
* Product - this is built in steps 
* Director - this builds the product in steps using the builder interface methods

Prototype - This pattern is used to create an exact clone if creation of an object is an expensive operation. Following types are available:a) Shallow copy - this is available in Java out of box.
The object class contains the clone() method but one should also implement the marker Cloneable interface. It copies only primitive fields and not object references.b) Deep copy - this means that the entire object tree has to be cloned. This does not come out of box but Java serialization and deserialization can be used to implement this.

