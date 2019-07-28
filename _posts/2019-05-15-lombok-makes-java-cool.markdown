---
layout: post
title:  "Project Lombok"
date:   2019-05-15 13:55:23 +0530
categories: Java
---

# Project Lombok makes Java cool again  

For all of us who have witnessed from inside (whcih means we worked as Java developers/architects) the progress of mainstream Java development over the years, needles to mention that we are all fascinated by the power and cleanness brought in by lombok annotations. Please also refer top the official lombok project [here](https://projectlombok.org/ "Project Lombok").

For the uninitiated - Project lombok has introduced some really **cool annotations** which relieve you from writing a lot of routine boiler plate code and hence *keeps your source Java file smaller and hence cleaner*. Below are some most popular examples of the lombok annotations:

* **@Getter** - This when annotated on top of the class generates all the getter accessor methods corresponding to all the class variables and following the Java bean naming convention. 

* **@Setter**  - Similar as above but it generates the setter methods of all class variables.

* **@ToString** - It generates the toString() implementation as per standard conventions. 

* **@EqualsAndHashcode** - It generates the equals() and hashcode() implementation as per standard conventions.

* **@NoArgsConstructor, @RequiredArgsConstructor and @AllArgsConstructor** - It generates all the necessary constructors as per standard conventions.

There are in fact a couple of alternatives to Lombok and they are [Autovalue](https://github.com/google/auto/tree/master/value) and [Immutables](http://immutables.github.io/) and they also operate by the way of annotating source classes. But the biggest difference between Lombok and Autovalue/Immutables is the fact that Lombok annotation parser directly generates the class file from the source while Autovalue/Immutables's annotation parsers generate the enhanced classes (with the additional boiler plate code and with a different class name) and then you can compile the sources. **This is why I like Lombok's approach as it does not generate another cluttered source file and hence its actually a better way (in my opinion) to write cleaner code which is free of all boiler plate.**

Below is a basic example of a lombok annotated class:

{% highlight ruby %}

@Getter
@Setter
@ToString
@EqualsAndHashcode
@@AllArgsConstructor
public class Employee {
 private String empId;
 private String empFirstName;
 private String empLstName;
 private String empDesignation;
 private String empDepartment;
 private double empMonthlyGross;
 private double empAge;
 }

{% endhighlight %}

