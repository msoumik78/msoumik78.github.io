---
layout: post
title:  "CSS Preprocessors - LESS and SASS"
date:  2017-10-07 16:55:23 +0530
categories:  "Frontend"
---
# CSS Preprocessors - why ?
All of us know that we require CSS To make a webpage look beautiful. **However CSS has some limitations (and it does not support normal programming like syntax) and this is exactly where CSS pre-processors add value.** The 2 most popular CSS pre-procesors are LESS and SASS

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
@div-width: 10

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

**lessc style.less style.css**

## SASS 
SASS is another popular CSS pre-processor (and it is in fact very similar to CSS) and below are some commands:
{% highlight ruby %}

$title-font: normal 24px/1.5 'Open Sans', sans-serif;
$cool-red: #F44336;
$box-shadow-bottom-only: 0 2px 1px 0 rgba(0, 0, 0, 0.2);

h1.title {
  font: $title-font;
  color: $cool-red;
}

div.container {
  color: $cool-red;
  background: #fff;
  width: 100%;
  box-shadow: $box-shadow-bottom-only;
}

{% endhighlight %}

A SASS file can also be compiled using a node based CLI command as below:
**node-sass input.scss output.css**

## Conclusion
I think using CSS pre-processors definitely brings in a lot of advantages to the frontend developers who can use variables, mixins or even do some simple maths. However note that, in modern day CSS, you can define and use a variable using plain / vanilla CSS without using any pre-processors as below:
{% highlight ruby %}
//declares a variable named 'bg-color', this is a custom property and should always start with -- 
:root {
  --bg-color: coral; 
}

//Now the CSS variable/custom property can be accessed using the var() function
#div1 {
  background-color: var(--bg-color); 
}
{% endhighlight %}

However I still think using a simple CSS pre-processor (LESS / SASS) gives much more power and flexibility to the frontend developer. Now once you have decided thatr you will indeed use a CSS pre-processor and then if the next question is which one - it is entirely a personal choice as both are very siumilar. While market share of SASS is much more than LESS and SASS is written in Ruby while LESS in Javascript, I still believe that using one is entirely a personal discretion. So go ahead and try both and decide yourself! 
