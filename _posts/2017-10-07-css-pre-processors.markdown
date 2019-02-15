---
layout: post
title:  "CSS Preprocessors - LESS and SASS"
date:  2017-10-07 16:55:23 +0530
categories:  "Frontend"
---
# CSS Preprocessors - why ?
All of us know that we require CSS To make a webpage look beautiful.However CSS has some limitations (and it does not support normal programming like syntax) and this is exactly where CSS pre-processors add value. The 2 most popular CSS pre-procesors are LESS and SASS

## LESS 

LESS has 4 distinct advantages over normal CSS :
* Allows variable declarations with @ tag
* Allows mixins declarations (which are groups of properties) to be potentially re-used
* Allows functions to be defined in CSS
* Allows arithmetic operators to be used

Following are code snippets in LESS:

{% highlight ruby %}
// variable declaration 
@background-color: #ffffff;
@text-color: #1A237E;

p{
  // usage of the variable
  background-color: @background-color;
  color: @text-color;
  padding: 15px;
}

// arithmetic operation
#right{
  width: @div-width * 2;
  background-color: @color;
}

{% endhighlight %}

LESS provides a native command line interface (CLI), lessc, which handles several tasks beyond just compiling the LESS syntax. So basically following is a command which you can use to convert LESS code to CSS code (this process of converting one type of source to another type of source is known as transpiling):

*lessc style.less style.css*

## SASS 
