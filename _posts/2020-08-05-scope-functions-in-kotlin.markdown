---
layout: post
title:  "Scope functions in Kotlin"
date:   2020-08-05 13:55:23 +0530
categories: Kotlin
---

# Scope functions in Kotlin

Kotlin scope functions are a special syntax to help us write more concise and idiomatic code which is also the one of the main motivation for using Kotlin programming language. It is important to understand that the scope functions are called so as they are always invoked in context of a scoped object - hence the name.

Following are the types of scope functions (remember these scope functions do not provide any additional functionality but provide smarter syntax to write compact code) :

* Below are the 2 scope functions which are used to decorate (put additional info/ property) on the context object and also return the context object.

	apply - This one is mainly used to set some properties of the context object. Context object is referred with ‘this’
 	also - This one is mainly used to write some log statements. Context object is referred with ‘it’


	class Computer(var cpuType : String = "", var ramSize : Int=0)
var computer2 = Computer().apply {
    this.cpuType = "i9"
    this.ramSize = 32
}.also {
    println("Configuration of computer : Cpu =  ${it.cpuType} , Ram = ${it.ramSize}")
}



* Below are the 3 other scope functions which are normally used to do some work but don’t return the context object rather returns the result of the lambda expression.
	let - Context object is referred with it.
	run - Context object is referred with this.
	with - Context object is referred with this.
