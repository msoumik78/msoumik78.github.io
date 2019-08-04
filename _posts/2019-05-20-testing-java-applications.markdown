---
layout: post
title:  "Testing Java applications"
date:   2019-05-20 13:55:23 +0530
categories: Java
---

There are several levels of testing that are progressively executed on a production ready java applications. These several roiunds of testing test different aspects 
of the application and this blog discusses about these various levels of testing and their purposes.

* **Unit testing** - This is the first and basic testing where every single java method is tested. This testing is actually a "white box testing"
and is done using mocking frameworks (Mockito, PowerMock etc.)

* **Integration testing** - This is the second level of testing where several layers of the application are tested in one shot which means a request is 

* **Functional testing** - This is the last and final level of testing where the application is tested end-to-end (usuually from the UI perspective) and 
using some UI testing automation tool (like Selenium)

