---
layout: post
title:  "Basics of Kotlin with examples"
date:   2020-06-05 13:55:23 +0530
categories: Kotlin
---

# Basics of Kotlin with examples

Kotlin is a JVM language which has not only become the de-facto programming language for developing Android applications but also is increasingly becoming very popular on the server side as well. So server side folks are also taking Kotlin very seriously because of so many cool features. Here I’ll summarise some of the basic features which have become really popular (remember Kotlin aims to make the code as compact and minimal as possible). If you look at each of the features below, they seem to be very logical way to make the Java syntax more concise but still readable and understandable.

* We do not need to end sentences with semicolons
* Variables are declared with keyword var and constants with keyword val
  Also in Kotlin, the variable name is declared/written first followed by a colon and then the variable type. Variable type is optional in Kotlin and it is able to auto infer.

{% highlight ruby %}
	var data1 : String = “text”
	val data2:  String = “text”
{% endhighlight  %}


* String has 2 significant additions:
    * Multiline strings - this feature has now been introduced in Java as well
    * String templates which contain some dynamic parts

{% highlight ruby %}
	var letterBody: String = """
	    Dear ${letterRecipeint ?: "Recipent" }
	    This is to inform you that we have.....
	    You are receiving this letter on ${Date()}
	""".trimIndent()
{% endhighlight %}


* Functions have 2 main enhancements which have made function overloading redundant:
    * You can specify default value of some parameters and hence those parameters may not be supplied 
    * You can also invoke function with named arguments

{% highlight ruby %}
	fun buildComputer(cpuTypeProvided: String = "i5",
			  ramSizeInGBProvided: Int = 8)
	    = Computer(cpuType = cpuTypeProvided,ramSize = ramSizeInGBProvided )

	buildComputer()
	buildComputer(cpuTypeProvided = "i9")
	buildComputer(cpuTypeProvided = "i9", ramSizeInGBProvided = 16)
{% endhighlight  %}

In the above example, the function buildComputer is declared with default values for both the arguments. So as shown above, you can even invoke the same function without any argument and then it will take the default values of those arguments which were not specified. You can of course supply specific values in which case the default values will not be used.


* Kotlin has a different way to deal or completely remove the null pointer exception from runtime to compile time. For every data type, Kotlin essentially has 2 types (one type can’t contain null value and the other one can contain null), say for example :
{% highlight ruby %}		
		var text1 : String 
		var text2 : String?	
{% endhighlight %}
	     
So text1 can’t contain null values. If you try to assign null values in it, the compiler will flag it as a compile time exception.
However text2 can contain null values
