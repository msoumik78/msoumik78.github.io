---
layout: post
title:  "How to write clean code"
date:   2019-05-24 13:55:23 +0530
categories: Java
---

# How to write clean Java code

One of the fundamental aspects that I have learnt progressively over time as a software engineer is the value of clean code. Honestly I never realized the value when I was
only a junior programmer. But now looking back I realize - how critically important for a tech savvy company to have clean code to minimize the technical debt over time.

So in this blog, I am going to present some very basic but really helpful tips to write clean code. So here you go:

* **Tip 1 - Use intention revealing names of classes, methods and objects** - However trivial it might seem, I have always realized how important is is to be able to infer purpose from the names of classes, methods and variables. Examples of some bad names:
AccNo, CurrBal, getAdvPay, 

And below is how the above stuff should have been named properly:
AccountNumber, CurrentBalance, getAdvancePayment()

If a code is written with such intention revealing names, it is always very easy to find out bug from existing code and also easier to maintain such code by a new team and hence the technical debt and overall cost of ownership goes down. 

* **Tip 2 - Use smaller methods and classes** -  This is also another very important aspect that I have learnt over time and it boils down to a few important / salient points:
* Never have a method exceeding 4 ~5 lines
* Never have a class exceeding 5 ~ 6 methods
* Always believe in the fact that every class and method should follow the **Single responsibility pattern** which means it should do exactly one thing and the moment you use longer names - it breaks that principle which is the recipe of future issues (bad design essentially).

* **Tip 3 - Use comments very sparingly** - This is another aspect which I have also learnt 

* **Tip 4 - Use strategy design pattern and avoid if/else statement as much as possible**



