|layout|title|date|categories|
|---|---|---|---|
|post|"Some OO Design patterns"|2017-10-20 16:55:23 +0530|Design Patterns| 


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

Factory - This design pattern encapsulates object creation and below are the variants:
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
