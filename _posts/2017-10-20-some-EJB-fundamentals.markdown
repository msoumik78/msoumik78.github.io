---
layout: post
title: "EJB fundamentals"
date: 2017-10-20 14:55:23 +0530
categories: Java
---


# Session beans

Interfaces for SB-  3 types of interfaces - Local, Remote and WebService. Only the methods exposed by the specific interface can be accessed via the corresponding interface.
Lifecycle listeners for Stateless SB: PostConstruct, Pre-Destroy
Lifecycle listeners for Stateful Session Beans: PostConstruct, PostActivate, PrePassivate, PreDestroy (Generally the same resource opening method is annotated with PostConstruct/PostActivate and the same resource closing method is annotated with PrePassivate/PreDestroy)
Tips for Stateful Session Beans: Always annotate a method (usually the last method) with a Remove annotation. This destroys the instance of the bean which was associated with the client and thereby eases performance issues.


# Message Driven Beans

Messagging are of 3 types - P2P (Queues), Pub Sub (Topics) & Request Reply (using JMSCorelationId & ReplyTo)
MDBs are annotated with @MessageDriven and they must implement the "MessageListener" interface and hence implement the "onMessage" method. @MessageDriven annotation is supported with ActivationConfig property names and values - usually property names are like destinationType, destinationName, acknowledgeMode, subscriptionDurability, MessageSelector
Advantages of using MDB over POJO JMSListeners - Inbuilt Multithreading built in MDBs (as they are pooled by container), Not required to establish ConnectionFactory, create Session etc in an MDB.
For better functional design - the business logic of a MDB should not be written entirely in the onMessage method. The onMessage method should call a business method (may be in a seperate unit testable POJO) which should contain the business logic.

# DI, Listeners & Timers

DI is heavily used in EJB3 as these annotations - @Resource, @EJB, @PeristentContext, @PersistenceUnitUsage of @Resource annotation : DataSources, Topics, Queues, ConnectionFactories, Environment variables, EJB Context (Session / MessageDriven context)
Listeners - Can be present at 3 levels - DefaultListener, Class Listener, Method Listener and the order of execution is DefaultListener-->ClassListener-->MethodListener. Default and Class level listeners can be excluded using @ExcludeDefaultListener & @ExcludeClassListeners.
The listener class is usually a seperate class and contains a method annotated with @AroundInvoke.
Timers - Some basic scheduling mechanisms are available. The metod to be called usually annotated with @TimeOut annotation. Also the timer is created using timer.createTimer()

# Transaction & Security

Transactions- ACID (Atomic - All or none will happen), Consistent (State can go inconsistent during transaction but will return to consistence once transaction is complete), Isolation (Levels are Read Uncomitted, Read Comitted, Repeatable & Serializable Read), Durability (changes are durable)
Transaction attributes are - Required (Most frequent), RequiresNew, Mandatory, Never (SIgnifies the non transactional nature to the client like writing to a file system), Supports (Generally used for read operations), Not Supported (Generally used for MDBs)

