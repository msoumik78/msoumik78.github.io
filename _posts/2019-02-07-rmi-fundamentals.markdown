---
layout: post
title: "Java RMI"
date: 2019-02-07 16:55:23 +0530
categories: Java
---

# Java RMI (Remote Method Invocation)
I think some of you are surprised at this post - is Java RMI still relevant in today's world od de-coupled microservices styled architecture ? Well I will share my take on this once towards the end of the post but beofre that, please read on to recap your RMI fundamentals.

At its core - RMI is a simplified version of method to method communication between 2 different JVMs and it is technically a simplified version of the CORBA protocol. If you only have Java in your landscape, it makes sense to use RMI over CORBA.

Well, below are the steps to create and deploy a simple RMI program:
 * Create a Remote interface (by extending the marker Remote interface) and declare a couple of remote methods.
 * Now create a class (say MyRemoteImpl) which extends the UnicastRemoteObject and implement the remote interface that you have created in the previous step. This class needs to implement the methods declared in the above remote interface. Also you can optionally have a main method in the same class. Representative code snippets:
 
 {% highlight ruby %}
 // Create the remote interface
 public interface SimpleRemoteService extends Remote {
    String sendMessage(String clientMessage) throws RemoteException;
}
 
// Create a class which implements the above remote interface
public class SimpleRemoteServiceImpl implements SimpleRemoteService { 
    public String sendMessage(String clientMessage) { 
        return "Client Message".equals(clientMessage) ? "Server Message" : null;
    }
 
// instantiate the remote class within the main method 
SimpleRemoteService remoteService = new SimpleRemoteServiceImpl();

//Now expose this remote object for clients outside the current JVM by giving it a name 'RemoteX'
Naming.rebind("RemoteX",remoteService);
 {% endhighlight %}
 
* Compile the classes and generate stubs & skeletons using the rmic compiler (on the remote class created in the previous step)
* Start the rmi server using the command - rmiregistry
* Open a different window and start the class created in step 2 using - java MyRemoteImpl. This steps registers the class in the RMI server and makes it available for remote calls.
* Now write a client with the following code:

{% highlight ruby %}
// Below code looks up for the remote object deployed in the other JVM a while back
Object o = Naming.lookup("rmi://localhost/RemoteX");
{% endhighlight %}


# RMI vs REST styled web services

Well my take is that for internal communication within a Java based enterprise - one should use RMI as you can stay completely within the Java world. A couple of disadvantages would be strong coupling and monolithic application. However if you want to have a client facing application for clients over internet - you should go for REST styled micro services architecture.
