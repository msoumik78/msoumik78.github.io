---
layout: post
title:  "Why use Kotlin ?"
date:   2019-05-30 13:55:23 +0530
categories: Java
---

# Why use Kotlin ? 

In this blogpost, I am going to take a dive into some of the most widely used features of **Kotlin** and see if they are attractive 
enough for us to make the switch. First let us start with some background/ history. Kotlin was started sometime back by the same guys (Jetbtrains inc.) who had this same motivation to create a completely new JVM based language. The biggest advantage of using Kotlin is that it helps in writing much more concise and clean code.

Let us browse through some of the key features of the Kotling language (please also refer to my Github project (KotlinExperiments) [https://github.com/msoumik78/KotlinExperiments]):
* Variables are declared using the *var* keyword and constants are declared using *val* keyword
* Variables do not need to be declared with their types always, that is auto inferred in case types are not specified

{% highlight ruby %}
var firstName = "Soumik"
var lastName = "Mukherjee"
const val age = 40
{% endhighlight %}

* One of the biggest things in Kotlin is that you do not need to encapsulate all the code within a class
* Another good thing is that functions can be declared with default parameters as below:
{% highlight ruby %}
fun calculateSalaryBasedOnAgeAndDepartment(department: String, age: Int = 40) : Double
{% endhighlight %}
So in the above function declarataion, the caller can optionally specify the second parameter (age) and in case the caller does not specify that parameter - it will take the default value 40.

* Another related aspect is that the function can be called with named parameter as below:
{% highlight ruby %}
calculateSalaryBasedOnAgeAndDepartment(age=30, department = "IT");
{% endhighlight %}

The above two aspects (default parameters in function declaration and ability to call a function with named parameter)- have made method overloading and builder methods completely redundant and in my opinion - this is one of the smartest enhancements in Kotlin.

* One can also declare class in Kotlin but the instantiation does not require **new** operator
* Also another aspect of Kotlin is that we do not need to do null checks thanks to the ? operator





