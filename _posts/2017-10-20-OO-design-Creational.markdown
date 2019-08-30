---
layout: post
title: "Creational OO Design Patterns"
date: 2017-10-20 16:55:23 +0530
categories: Design
---


## Creational Paterns
These patterns describe the best practices related to object creation - how they should be created, where they should be created in order to build a loosely couple well designed software.

# Singleton - 
This pattern ensures that only 1 object of a class gets created (per JVM) and hence it is about **how to create only one object of a class**. So below are how you can create singletons:
* Having a private constructor and a pulic static getInstance() method which creates an object and returns the object to the caller.Following is a code snippet of a double checked locking for creating singleton objects and it is also performant and perfect for a multi threaded environment (like web applications):
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

* Another option is to do an early loading of the _instance variable in a static initializer before any client calls_. Still another option is to use _Enum_ to implement Singletons.

# Factory - 
This design pattern deals with how objects should be created to ensure encapsulation. It is very important to seperate the object creation from object usage so that both of them can vary independently.Below are the variants of the factory pattern (In fact Spring framework is one of the most popular implementations of the Factory design pattern):
* Normal Factory - This is just a method which encapsulates object creation and hides all object creation details from the client. 
Spring IoC is a classic example.
* Factory Method - Defines an abstract method in the superclass and lets the subclass to implement the method (inheritance way)
* Abstract factory - Defines an abstract factory to create concrete factories which in turn can create products (essentially there are 2 inheritance trees - one of the factory and the other of the product). This is more of an aggregation way.

# Builder -
This pattern is used to avoid telescoping (multiple) constructors and help to create the big object in steps. Gof Defines it as "Seperate the construction process of objects
from its representation so that the same construction process can create multiple representations." Components are : 
* Builder interface - exposes the various methods 
* ConcreteBuilder implementation - implements the methods 
* Product - this is built in steps 
* Director - this builds the product in steps using the builder interface methods

**One interesting observation is that if you are using Kotlin as the programming language and leverage the featurees of default values in functions and named parameters in function calls, these features probably make method overloading and builder pattern redundant!** 

# Prototype -
This pattern is used to create an exact clone if creation of an object is an expensive operation. Following types are available:
* Shallow copy - this is available in Java out of box. The object class contains the clone() method but one should also implement the marker Cloneable interface. It copies only primitive fields and not object references.
* Deep copy - this means that the entire object tree has to be cloned. This does not come out of box but Java serialization and deserialization can be used to implement this.
