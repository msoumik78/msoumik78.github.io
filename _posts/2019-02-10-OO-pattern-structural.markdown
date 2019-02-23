---
layout: post
title: "Structural OO Design Patterns"
date: 2019-02-10 16:55:23 +0530
categories: Design
---

# Structural Pattern

Decorator - In this pattern, additional responsibilities are attached to a class dynamically at runtime. Ideally a decorator implementation should have the decorator interface as an object instance variable. Java I/O contains ample examples of decorators. Below is the code snippet:

{% highlight ruby %}
 public class DecoratorI {    
    public String description();    
    public float cost(); 
  }
 
 public class ConcreteDecorator1 implements Decorator1 {    
      private DecoratorI decI;    
      public void ConcereteDcorator1(DecoratorI dec){        
          decI = dec;    
       }  
    public String description() {        
      return "Concere Decorator1" + decI.description();        
    }    
    
    public float cost(); {         
      return x + decI.cost();        
   } }

{% endhighlight %}

Adapter - This pattern is used to implement a specific interface (which the client calls) and in turn delegates call to a different method. Following are the types:a) Object Adapter - b) Class Adapter - 
Facade - Provides a single unified interface instead of making a lot of calls to all granular level methods.
Proxy- Essentially a layer between the client and the server and can be of the following types:a) Remote - Java RMI / EJB's stubs / skeletons are classic examplesb) Virtual - If the actual object is heavy (like an image) a virtual proxy can be usedc) Protection proxy - Typically corporate firewalls are examples
