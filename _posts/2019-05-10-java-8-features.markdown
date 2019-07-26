---
layout: post
title:  "Java 8 Features"
date:   2019-05-10 16:55:23 +0530
categories: Java
---

# Some cool features of Java 8  

Java 8 has brought in a few cool interesting features which has made Java folks fall in love with Java yet once again. In this short blog, I am going to walk through some of the most widely used features of Java 8. So lets get started...

* **Default and static methods in Interfaces** - While purists might sniff, this is one elegant way in which new functionalities can be applied later to all implementing classes of an interrface. So essentially you can introduce some default (and yes you read it correct **implemented**) method implementations in the interface itself so that all classes can inherit (and if required also override) the base implementation. Well - then what is the difference with Abstract classes ? Abstract classes can also additionally define constructors and have state defining variables and the purpose is completely different. Abstract class methods define some base behaviour whereas default methods of Java 8 interfaces help in backward compatibility of adding new functionalities without changing at too many places.     

Static methods of an interface are a perfect way to create some utility stateless methods which really do not require to be present in the class (having a state). 

* **Java Lambdas/ Functional interfaces** - Arguably this is the biggest feature introduced in Java 8 and its the right step towards making Java a functional language as well. So Java 8 has added the concept of Functional interfaces which are special interfaces that can be annotated with *@FunctionalInterface* annotation and have a single method defined. **A lambda expression is essentially the implementation of that single method in the functional interface.** So with this lambdas - we have the following quick wins : we can completely replace the anonymous inner classes (which would have implemented this functional interfaces) and like a true functional language, we can pass the lambdas as method arguments. 

Of course lambdas have also made Java code look cool!

* **Stream API** - This is a more expressive and elegeant way of iteraing over a collection when compared to the traditional approach. As an example let us take a 
Traditional way:
{% highlight ruby %}
    List<Employees> origEmployeeList = new ArrayList<>();
    List<Employees> filteredEmployeeList = new ArrayList<>();
     for(Employee emp : employeeList) {
         if(emp.getSalary() > 50000) {
             filteredEmployeeList.add(emp);
         }
     }
     return filteredEmployeeList;
{% endhighlight %}


Stream way:
{% highlight ruby %}
return origEmployeeList
     .filter( emp -> emp.getSalary() > 50000)
     .collect(toList());
{% endhighlight %}

Also stream helps in parallel processing!

* **Optional** - This is another smart technique which Java has introduced to help programmers get rid of Null Pointer Exception. Essentially, the idea is that return type of any method be wrapped with an Optional wrapper so that even if the method returns a null object, we will not encounter a NPE at runtime.
