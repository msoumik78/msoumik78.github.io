---
layout: post
title:  "How to write performant Java applications"
date:   2019-04-10 13:55:23 +0530
categories: Performance
---

## Writing Performant Java applications
In this blog, I am going to describe some basic tips which will help us to write more performant Java applications.
So below are the list of tips:
* Don't use Sring concatenation, use StringBuffer / StringBuilder instead - I think all of us would agree that String concatenation creates to omany strings in the meory which is very bad and we should always use the alternative.
* Ensure that all resources are closed - better use a try-with-resources block. This is also another most common area which causes memory leak. 
* Do profiling of the applications to ensure that there are no specific performance issues of the application - It is always advisable to do a profiling of the application  and understand the bottlenecks very well.
* Use primitive types as much as possible - This consumes much less memory. 
* Try to avoid BigInteger/ BigDecimal as much as possible - Same here, unless you need very high degree of accuracy, please avoid them. 
* Check current log level first before printing - Logging is IO intensive and hence reduces performance. So only log error / fatal in production. And for all debug logging, please use "if log.isDebugEnabled()"
* Resort to caching of at expensive stuff like database operations - Caching of DB connections is must at the server start time, this should improve the application latency.
* Avoid recursion, iterator as much as possible - These are some general suggestions to ensure that the most efficient algorithms are used in your code. 
