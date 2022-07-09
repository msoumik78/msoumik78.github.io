---
layout: post
title:  "Kotlin Functions - Extension functions, Infix functions and Higher Order functions"
date:   2020-12-05 13:55:23 +0530
categories: Kotlin
---

# Kotlin Functions : Extension Functions, Infix functions and Higher Order functions

## Extension Functions
This is a popular feature among Kotlin developers to keep the code base small. In fact, as the name suggests, proper usage can actually help to write very concise and idiomatic code.
As the name suggests, with this feature, one can actually so called "extend" 3rd party libraries thereby also honour one of the important tenets of object oriented programming which is "Open Closed Principle".
Recommendation is to use extension functions instead of writing utility classes and static functions. Now let's see some extension fiunctions in action :

{% highlight ruby %}
// On String class - as if an extension of String itself. Can be invoked as : "amusement".removeFirstAndLastCharacter()
fun String.removeFirstAndLastCharacter() = this.substring(1, this/length -1)

//On Int class 
fun Int.triple() = this*3

// On List<> class : 
fun List<T>.midElement() = this[this.size/2]
{% endhighlight %}

One important aspect of extension functions is that they are resolved statically which means that if you pass a child type of the receiver type, it will still be resolved by the declared type as it is resolved statically only.

## Infix Functions  
Actually this is a syntactic sugger in Kotlin by which it allows us to call one-argument functions quickly. 
In order to create an infix function, two arguments are required:
  - The first argument is the target object
  - The second argument is the actual argument passed to the function.

{% highlight Ruby %}
 // below is a declaration of infix function 
 infix fun Int.addCustom(b : Int) : Int = this + b
// actual call
val y = 10 addCustom 20        
{% endhighlight %}

  
## Higher Order Functions
This is the technique of pure functional programming. Essentially - higher order functions are those which accept functions as arguments and return functions.
Higher order functions are most useful when writing some generic code like : writing API invocation
So we can write a higher order function to invoke a REST endpoint and one of the arguments of the HOF can be the actual method.  
{% highlight ruby %}  
// Example when accepting function as an argument :

fun calculate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {  
    return operation(x, y)                                          
}
fun sum(x: Int, y: Int) = x + y                                     
fun main() {
    val sumResult = calculate(4, 5, ::sum)                          
    val mulResult = calculate(4, 5) { a, b -> a * b }               
    println("sumResult $sumResult, mulResult $mulResult")
}
 
//Example when a function is stored in a variable :
val addOffset = {x : Int -> x + 10}
println(addOffset(2)
println(addOffset.invoke(2))  
{% endhighlight %}  
  
