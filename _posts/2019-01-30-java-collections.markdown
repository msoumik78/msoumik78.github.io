---
layout: post
title: "Java Collection Synopsis"
date: 2019-01-30 16:55:23 +0530
categories: Java
---

### Collections 

This post tries to deal with some frequently useful features of Java collection API. As we all know, the main types of Java Collections include the following:
* List (You will use this when you want to maintain the order of elements)
* Set (You will use this when you don't want to keep duplicates. To check for equality, set objects need to override hashCode() & equals() methods) 
* Map (You will use this when you want to maintain a key value pair)

With that said, let us explore the different types of List : 
* Vector (threadsafe/sychoronized and hence slow. Also this is a legacy class and hence I will not recommend using it in new codebase.)
* ArrayList (not threadsafe & hence fast) 
* CopyOnWriteArrayList (synchronized but its thread safety mechanism is different from vector. While Vector implements a LOCK, this one does not.)
* Collections.synchronizedList() - This is another way to create a synchronized list 
* LinkedList - This is Doubly linked list implementation

CopyOnWriteArrayList(COWAL) will perform better when collection size is small and there are more frequent reads and less write operations. 

Now let us explore the different types of Sets : 
* HashSet - This is the basic one
* TreeSet - This is the one where the stored objects are sorted. Hence the stored objects must implement the Comparable interface. 

Now let us explore the different types of Maps : 
* HashTable (threadsafe/sychoronized and hence slow), 
* HashMap (fast and not threadsafe) 
* TreeMap (sorted keys) 
* ConcurrentHashmap (fast & threadsafe)

Some other important concepts in the Java Collection API:
* **Unmodifiable collection**:  Make a list unmodifiable by using `Collection.unmodifiable(list)` and similarly make a map unmodifiable by using `Collection.unmodifiable(m)`

* **Generics & Type erasure**:  Declaring a collection of a specific type (like ArrayList<String>) is the generics way. 
Type erasure means the runtime erases the type to make the binary compatible with old versions.Generic Wildcard: <? extends T>  means upper bound by T and <? super T> means lower bound by TFailfast & Fail Safe IteratorComparator & Comparable: Comparable interface is implemented by the actual object (say Song) which needs to be compared. The method that needs to be implemented is "compareTo"Comparator interface is implemented by any class. The method that needs to be implemented is "compare" and this method takes 2 arguments corresponding to the objects to be compared. 

* **Comparator vs Comparable**: Using Comparator is a more flexible way of comparing as the comparing criteria can be easily changed by writing a different comparator.
* **HashCode and Equals** : The rule to implement hashcode and equals is that - 
  * If hashcodes of 2 objects are not same, they are not equal. 
  * If hashcodes are same - the 2 objects may or may not be equal. 
  * If 2 objects are equal (which means using equals operator return true against 2 objects) their hashcodes must be same.
