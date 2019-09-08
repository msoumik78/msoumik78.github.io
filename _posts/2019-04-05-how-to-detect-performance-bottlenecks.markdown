---
layout: post
title:  "How to detect performance bottlenecks in Java applications"
date:   2019-04-05 13:55:23 +0530
categories: Performance
---

## Java application's performance tuning
I guess all of us will agree that while writing a clean code for Java application is one thing, making it performant is another skill.
In this blog, I will try to highlight some of the key facts which a Java developer/architect/performance engineer needs to be aware for detecting possible reasonsn for performance issues in Java application.

# Some basic high level facts of Java memory and garbage collection 
In the next few lines, I would just touch upon some of the basic facts for JVM memory management and Java Garbage Collection basics which every Java developer should be aware of. Esssentially, the JVM heap memory is divided into the following components:
* __Young generation__ - This is the place where all objects which are created initially reside here. This place is further sub-divided into the following components:
  * 1 Eden space - All new objects initially reside here.
  * 2 Survivor spaces - All new objects which survive a minor garbage collection end up staying here.
* __Old generation__ - This is where all new objects which stay for even longer time end up here.
* __Permanent Generation/Metaspace__ - This is the space where all methods , interned strings and class definitions reside. From Java 8 onwards, this has been renamed to metaspace. 

There are 2 types of garbage collection (GC):
* __Minor GC__ - This happens frequently and it is absolutely normal and the JVM attempts to reclaim the young generation as much as possible.
* __Full GC__ - This should NOT attempt frequently and if it does happen frequently, it definitely needs to be rectified. This GC attempts to reclaim the space of Old generation. 

Also following are the main types of GC threads available in JVM:
* __Serial GC__
* __Parallel GC__
* __ConcurrentmarkSweepGC__
* __G1GC__

Following are some of the most important types of OutOfmemory(OOM) error:
* Exception in thread “main” java.lang.OutOfMemoryError: Java heap space - Too less heap space available and this can happen say for example if you add to a list in an infinite loop.
* Exception in thread “main” java.lang.OutOfMemoryError: PermGen space - Too less space available in permanent generation.
* Exception in thread “main” java.lang.OutOfMemoryError: GC overhead limit exceeded - This is a tricky one and it indicates that 

# What are some common steps to rectify Java performance issues ?
Now that you have a got a brief idea about JVM memory/ heap space sub divisions and GC and OOM errors, let me quickly suggest a few most common steps to address java performance issues:
* OOM error solution - In case of OOM due to heap space issue, try to increase the heap space using JVM parameters : -Xms1024m -Xmx1024m . It is always advisable to start JVM with same values of Xms (minimum heap space) & Xmx (maximum heap space). It should be either 512MB or at max 1024 MB. In case of OOM issue due to Permgen space issue, try to increase the permgen space using JVM parameters: XX:MaxPermSize=256m   
* GC problem solution - If there are too many Full GCs being performed by the JVM, it definitely indicates that there are issues with memory. In order to dig it deeper, normally it is advised to restart JVM with parameters like -Xloggc:/gc.log (logging gc logs in a seperate file), -XX:+PrintGCTimeStamps  &  -XX:+PrintGCDateStamps. 

