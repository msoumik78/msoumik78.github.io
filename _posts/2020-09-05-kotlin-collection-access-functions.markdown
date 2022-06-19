---
layout: post
title:  "Collection access functions in Kotlin"
date:   2020-09-05 13:55:23 +0530
categories: Kotlin
---

# Collection access functions in Kotlin

Kotlin provides a wide set of functions to access collections and here is a short summary of some very useful ones:
Some of the functions accept a lambda expression which specifies the condition under which the operator is applied. 

* For collection creation, following are used extensively
	- emptyMap() , emptySet(), emptyList()
	- listOf(), mapOf(), setOf()
	- mutableListOf() , mutableMapOf(), mutableSetOf()
	- linkedSetOf(), linkedMapOf()
	- hashSetOf() , hashMapOf()
	- sortedSetOf(), sortedMapOf()

* For changing the content of collection: 
 	- add() , addAll() , put() , putAll() , plus(), plusElement()
	- remove(), removeAll(), minus(), minusElement(),
	- drop() , dropLast(), removeFirst(), removeLast()
	- take(), takeLast(), takeWhile()
	- map() , mapNotNullTo() , mapValues(), mapKeys()
	- filter(), filterNot() , filterKeys(), filterValues()
	- sorted(), sortedAscending(), sortedDescending()

* For retrieving parts of collection: 
 	- get(), getOrNull() , getOrElse(), getOrDefault()
	- elementAt() , elementAtOrElse() , elementAtOrNull()
	- find(), first() , findLast()

