---
layout: post
title: "Java Collection Synopsis"
date: 2019-01-30 16:55:23 +0530
categories: Java
---

### Collections 

Main types of Collections are-- List (ordered), Set (No duplicates) & Maps (Key Value pairs)
Types of List : 
* Vector (threadsafe/sychoronized and hence slow)
* ArrayList (not threadsafe & hence fast) 
* CopyOnWriteArrayList (synchronized & fast) 
* LinkedList 

Types of Set : 
* HashSet 
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
* If hashcodes of 2 objects are not same, they are not equal. 
* If hashcodes are same - the 2 objects may or may not be equal. 
* If 2 objects are equal (which means using equals operator return true against 2 objects) their hashcodes must be same.
