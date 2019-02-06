---
layout: post
title: "RMI fundamentals"
date: 2019-02-07 16:55:23 +0530
categories: Java
---



# Java RMI (Remote Method Invocation)

Steps to create and deploy a RMI program
 Create a Remote interface (by extending the marker Remote interface) and declare a couple of methods.
 * Create a class (say MyRemoteImpl) which extends the UnicastRemoteObject and implement the Remote interface. This class needs to implement the methods declared in the remote interface. Also have a main method in the same class which should have the below code:
 
 {% highlight ruby %}
 MyRemoteImpl x = new MyRemoteImpl();
 Naming.rebind("RemoteX",x);
 
 {% endhighlight %}
 
* Compile the classes and generate stubs & skeletons using the rmic compiler (on the remote class created in the previous step)
* Start the rmi server using the command - rmiregistry
* Open a different window and start the class created in step 2 using - java MyRemoteImpl. This steps registers the class in the RMI server and makes it available for remote calls.
* Now write a client with the following code:

{% highlight ruby %}
Object o = Naming.lookup("rmi://localhost/RemoteX");

{% endhighlight %}
