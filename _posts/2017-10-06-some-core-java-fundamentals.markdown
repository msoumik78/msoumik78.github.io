---
layout: post
title:  "Some Core Java basics"
date:   2017-08-22 16:55:23 +0530
categories: jekyll update
---


# Core Java Fundamentals
This will be a topic 

### Serialization

One can mark an object to be serializable just by implementing the marker Serializable interface.
Serialization technique can be used to read and write data if that data will be read by Java programs only.

Serialization (Converting an in-memory object to serialized state) -  

ObjectOutputStream os = new ObjectOutputStream (new FileOutputStream("x.ser")); 
os.writeObject();

De-Serialization (Converting a serialized state to in-memory object) -   
ObjectInputStream os = new ObjectInputStream (new FileInputStream("x.ser")); 
os.readObject();

Static & Transient variables are not serialized. One can mark a variable transient if that variable does not contain any original value (derived from other fields)
When an object gets serialized - the entire object graph gets serialized which means that all objects referenced by the object gets serialized. 
If any object in the graph is not serializable - the entire chain breaks and serialization fails. Hence Serialization is a whole or none proposition. 
During the process of de-serialization, constructors are not called (and hence the objects are not default initialized). If any object in the hierarchy is not serializable - constructor chaining starts from that point. Once constructor chaining starts, it can't be stopped.
A long field by the name "serialVersionUID" can be used to prevent any issues during de-serialization process if there is a change in the class after serialization happened. (private long serialVersionUID). But using this field means that the programmer is taking risk of any bad changes.
Acceptable changes for Serialization - 
* Field addition
* Fields changed from transient to non transientUn-acceptable changes for Serialization - 
* Field deletion 
* Fields changed from non transient to transient

An alternative to implementing the Serializable interface is implementing the Externalizable interface. This can be used in the following cases:

* One can overide the default serialization (by overriding the readObject() and writeObject() method in the class which implements Serialization). In fact this is also a technique to ensure that you can override these methods and throw a NotSerializableException - 
this is to make a subclass no serializable (when its parent is serializable)
* One can implement the Externalizable interface and override the readExternal() and writeExternal() methods and implement the custom serialization logic. This can improve the performance.


### Collections 

Main types of Collections are-- List (ordered), Set (No duplicates) & Maps (Key Value pairs)
Types of List : 
* Vector (threadsafe/sychoronized and hence slow), 
* ArrayList (not threadsafe & hence fast), 
* CopyOnWriteArrayList (synchronized & fast), 
* LinkedList, 

Types of Set : 
* HashSet, 
* TreeSet (sorted)

Types of Maps : 
* HashTable (threadsafe/sychoronized and hence slow), 
* HashMap (fast and not threadsafe), 
* TreeMap (sorted keys), 
* ConcurrentHashmap (fast & threadsafe)

Unmodifiable collection:  Make a list unmodifiable by using `Collection.unmodifiable(list)` and similarly make a map unmodifiable by using `Collection.unmodifiable(m)`
Generics & Type erasure:  Declaring a collection of a specific type (like ArrayList<String>) is the generics way. 
Type erasure means the runtime erases the type to make the binary compatible with old versions.Generic Wildcard: <? extends T>  means upper bound by T and <? super T> means lower bound by TFailfast & Fail Safe IteratorComparator & Comparable: Comparable interface is implemented by the actual object (say Song) which needs to be compared. The method that needs to be implemented is "compareTo"Comparator interface is implemented by any class. The method that needs to be implemented is "compare" and this method takes 2 arguments corresponding to the objects to be compared. 

Using Comparator is a more flexible way of comparing as the comparing criteria can be easily changed by writing a different comparator.
HashCode and Equals : The rule to implement hashcode and equals is that - 
If hashcodes of 2 objects are not same, they are not equal. If hashcodes are same - the 2 objects may or may not be equal. If 2 objects are equal (which means using equals operator return true against 2 objects) their hashcodes must be same.
