---
layout: post
title: "Structural OO Design Patterns"
date: 2019-02-10 16:55:23 +0530
categories: Design
---

## Structural Patterns
These patterns refer to the best practices of how classes/objects should be composed to create good software. 

# Decorator -
In this pattern, additional responsibilities/capabilities are attached to a class dynamically at runtime. Ideally a decorator implementation should have the decorator interface as an object instance variable. Java I/O contains ample examples of decorators. Below is the code snippet:

{% highlight ruby %}
 public interface IDecorator {    
    public String description();    
    public float cost(); 
  }
 
 public class ConcreteDecorator1 implements IDecorator {    
      private IDecorator Idec;    
      public void ConcereteDcorator1(IDecorator dec){        
          Idec = dec;    
       }  
    public String description() {        
      return "Concere Decorator1" + Idec.description() +"description specific to ConcreteDecorator1....";        
    }    
     public float cost(); {         
       return Idec.cost() + (cost of ConcereteDecorator1);        
   } }
{% endhighlight %}

# Adapter -
This pattern is used to implement a specific interface (which the client calls) and in turn delegates call to a different method. Following are the types:
* Object Adapter
* Class Adapter 
So basically an adapter is the middleman in between which is responsible for receiving your client call and converting to the target call. Without the adapter - the client and the target are normally unable to speak to each other.

# Facade - 
Provides a single unified interface instead of making a lot of calls to all granular level methods.
A typical example in a classic Java EE layer is the existence of session facade whose job is to make a coarse grained method call which internally makes calls to many fine grained methods and then collates and returns the response to the client. This saves network bandwidth that the client would had to make otherwise in directly calling multiple fine grained methods. 

# Proxy- 
Essentially this strategy is about building a layer between the client and the server and this layer can be of the following types:
* Remote - Java RMI / EJB's stubs / skeletons are classic examples
* Virtual - If the actual object is heavy (like an image) a virtual proxy can be used
* Protection proxy - Typically corporate firewalls are examples
