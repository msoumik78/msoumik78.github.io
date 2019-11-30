---
layout: post
title:  "Why use HATEOAS as the application architecture ?"
date:   2019-06-05 13:55:23 +0530
categories: Java
---

# Why use HATEOAS ? 

In this blogpost, I am going to briefly discuss the background and the motivation for ther HATEOAS architectural style for REST services. Well before we proceed, let me tell you that HATEOAS expands to Hypermedia As The Engine of APplication State. Now that is quite something, so gently read on to understand it better.

Well I think all of us understand REST services and how they differ from normal web pages. Basically REST services were originally designed to only return data while webpages are meant for displaying data as well as some hyperlinks which can help one to take some more actions by navigating to the links. The purpose of the **HATEOAS** architecture is essentially to add the flavour of the web page to the "data only" REST reponses. So to put it very simply, a HATEOAS styled REST service will return data along with links to the caller.

An example of a HATEOAS web service response looks like something below:
{% highlight ruby %}
[{"studentName":"Soumik1","courseName":"Advanced Java","courseDurationInMonths":6,"links":[{"rel":"self","href":"http://localhost:8080/Soumik1"}]},
{"studentName":"Soumik2","courseName":"REST","courseDurationInMonths":6,"links":[{"rel":"self","href":"http://localhost:8080/Soumik2"}]},{"studentName":"Soumik3","courseName":"Clean Code","courseDurationInMonths":6,"links":[{"rel":"self","href":"http://localhost:8080/Soumik3"}]},
{"studentName":"Soumik4","courseName":"Graal VM","courseDurationInMonths":6,"links":[{"rel":"self","href":"http://localhost:8080/Soumik4"}]},
{"studentName":"Soumik5","courseName":"Spring Boot","courseDurationInMonths":6,"links":[{"rel":"self","href":"http://localhost:8080/Soumik5"}]}]
{% endhighlight %} 

So if you refer to the above Json response, you will see that a link has been appeneded to each of the return items. One disticnt advantage of this architecture is that it clearly helps in loose coupling between the client and the server code.

There is a special MIME type for HATEOAS architecture and it is "application/hal+json".
You can use Spring boot as the framework for building HATEOAS styled REST services, the required dependency is:
{% highlight ruby %}
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-hateoas</artifactId>
        </dependency>
{% endhighlight %}

please also refer to my Github project [HATEOAS](https://github.com/msoumik78/springboowithHATEOAS)
