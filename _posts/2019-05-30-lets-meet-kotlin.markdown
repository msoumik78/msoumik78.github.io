---
layout: post
title:  "Why use Kotlin ?"
date:   2019-05-30 13:55:23 +0530
categories: Kotlin
---

# Why use Kotlin ? 

In this blogpost, I am going to take a dive into some of the most widely used features of **Kotlin** and see if they are attractive 
enough for us to make the switch. First let us start with some background/ history. Kotlin was started sometime back by the same guys (Jetbtrains inc.) who created the wonderful Java IDE and had this same motivation to create a completely new JVM based language. The biggest advantage of using Kotlin is that it helps in writing much more **concise ,clean and also safe code**.

Let us browse through some of the key features of the Kotling language (please also refer to my Github project [KotlinExperiments](https://github.com/msoumik78/KotlinExperiments/blob/master/src/app.kt):
* Variables are declared using the *var* keyword and constants are declared using *val* keyword. Further variables do not need to be declared with their types always, that is auto inferred in case types are not specified

{% highlight ruby %}
  var firstName = "Soumik"
  var lastName = "Mukherjee"
  const val age = 40
{% endhighlight %}

* **Safe code and eliminating NullPointerException completely** - Another big thing which Kotlin has introduced is null safe. So with good coding in Kotlin you can get rid of the dreaded NullPointerException. Actually Kotling distinguishes between non-nullable and nullable types. So for example - there can be a non nullable String and a nullable one (denoted by _String?_). Please refer to the below code snippet:
{% highlight ruby %}
    var name : String = "Soumik"
    //below line generates a compile time error
    //name = null

    var surname: String? = "Mukherjee"
    // below line does NOT generate a compile type error as we have used a nullable type
    surname= null
    
    // Also the ?. operator ensures that the name will not be invoked in case empObject is null
     println(empObject?.name)
{% endhighlight %}

* One of the biggest things in Kotlin is that you do not need to encapsulate all the code within a class
* **Clean and readable code** Another good thing is that functions can be declared with default parameters as below:
{% highlight ruby %}
  fun calculateSalaryBasedOnAgeAndDepartment(department: String, age: Int = 40) : Double
{% endhighlight %}
So in the above function declarataion, the caller can optionally specify the second parameter (age) and in case the caller does not specify that parameter - it will take the default value 40.

* Another related aspect is that the function can be called with named parameter as below:
{% highlight ruby %}
  calculateSalaryBasedOnAgeAndDepartment(age=30, department = "IT");
{% endhighlight %}

The above two aspects (default parameters in function declaration and ability to call a function with named parameter)- have made method overloading and builder methods completely redundant and in my opinion - this is one of the smartest enhancements in Kotlin.

* **Clean and concise code** - In order to instantiate a class in Kotlin we do NOT require the **new** operator, so classes are just instantiated as shown below:
{% highlight ruby %}
  // class instantiated with zero argument constructor
  var studentObject= Student()
  
  // class instantiated with one argument constructor
  var empObject = Employee ("Soumik") 
{% endhighlight %}
Also the data class concept (which represents/symbolises value objects) reduces boilerplate code to a great extent. Please refer to the below example:
{% highlight ruby %}
  data class Employee (val name: String, val age: Int, val designation: String, val Salary: Long) 
{% endhighlight %}
The above line of the code is equivalent to some 20 lines of Java code with all getters and setter methods and also with equals() and hashcode() methods. However with usage of Lombok with java - the boilerplate in java code can also be reduced. 

* Also another aspect of Kotlin is that we do not need to do null checks thanks to the ? operator
