---
layout: post
title:  "Scaling Microservices"
comments: true
date:   2021-03-05 13:55:23 +0530
categories: MicroServices
---

# How to scale your Springboot based microservice

In this blogpost, I would discuss some fundamentals principles to be followed in scaling out (horizontal scaling) of miicroservices.
In a cloud native containerized environment - scaling out is a cost effective way to ensure that the microservice is able to serve the increasing load and at the most optimum cost possible.

So here are some of the fundamental principles to achieve maximum scalability at least possible cost:
- Ensure that you do not store any state (like storing anything in in-memory caches like ConcurrentHashmap etc.) in your application. If a caching requirement exists, ensure that you store in an external distributed caching service like Redis or Hazelcast.
- Ensure that you deploy your service in containers like docker.
- Ensure that you use a container management platform like kubernetes or cloudfoundry to auto manage the cluster
- Best would be if you can go in an end-to-end asyc stack. And it would be very easy to implement the same using ** Kotlin Co-routines ** which can help you to achieve extreme scalability. Co-routines are like very light-weight threads and they are not blocked but are just suspended. They are a much easier alternative to reactive architecture.
- Last but not the least, consider from a functional perspective if you can migrate out from Springboot and 

{% if page.comments %} 
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    /*
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://https-msoumik78-github-io.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
