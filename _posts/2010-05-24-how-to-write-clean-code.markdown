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
AccNo, CurrBal, getAdvPay
And below is how the above stuff should have been named properly:
AccountNumber, CurrentBalance, getAdvancePayment()

If a code is written with such intention revealing names, it is always very easy to find out bug from existing code and also easier to maintain such code by a new team and hence the technical debt and overall cost of ownership goes down. 

* **Tip 2 - Use smaller methods and classes** -  This is also another very important aspect that I have learnt over time and it boils down to a few important / salient points:
* Never have a method exceeding 4 ~5 lines
* Never have a class exceeding 5 ~ 6 methods
* Always believe in the fact that every class and method should follow the **Single responsibility pattern** which means it should do exactly one thing and the moment you use longer names - it breaks that principle which is the recipe of future issues (bad design essentially).

* **Tip 3 - Use comments very sparingly** - This is another aspect which I have also learnt that we should use comments only to explain in some very specific cases why we have written that piece of code. Actually a well written code is like poetry or a well written prose and it should / does not need much explanation. Also we should never have commented code which is a very bad practice I must say.If you ever need to refer to old code - you can always refer to old versions from your Git / SVN.

* **Tip 4 - Use strategy design pattern and avoid if/else statement as much as possible** - This is another very important principle which I have learnt over time and this is also very closely related to "Open Close Principle". In general we should not use if/else to determine some sub class related behaviour - we should use strategy pattern instead which makes the code still work later when a new condition / subclass is introduced.

Let me try to explain this to you with some example:
{% highlight ruby %}
	public class OCPTester {
	
	private Vehicle vehicle;
	public void Vehicle(Vehicle vehicle) {
		this.vehicle= vehicle;
	}
		move() {
			if ((vehicle) instanceOf  (Train)) {
				....
			} else if ((vehicle) instanceOf (Tram)) {
				....
			}  else if ((vehicle) instanceOf (Bus)) {
				....
			}
		}
	}

	public subclass Train extends Vehicle {
	}
	public subclass Tram extends Vehicle {
	}
		public subclass Bus extends Vehicle {
	}	
{% endhighlight %}

Main problem of the above code is that the superclass Vehicle knows about the subclasses and it contains logic (within the *move* method) about the subclass behaviour. This is very bad because if new subclasses (new vehcle types like plane) are added in future, the superclass needs to change. So the above logic should be re-factored as below:

{% highlight ruby %}
public class OCPTester {
	private Vehicle vehicle;
	public void Vehicle(Vehicle vehicle) {
		this.vehicle= vehicle;
	}
	move() {
		vehicle.run();
	}
}

	public subclass Train extends Vehicle {
		run (){
		}
	}

	public subclass Tram extends Vehicle {
		run (){
		}
	}
	
	public subclass Bus extends Vehicle {
		run (){
		}
	}	

{% endhighlight %}

So essentially what we have done is that we have moved out the logic to the corresponding sub classes where it should ideally reside.
