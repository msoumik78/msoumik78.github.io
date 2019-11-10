---
layout: post
title:  "Modern day HTML5 quickstart"
date:   2017-09-11 16:55:23 +0530
categories: "Frontend"
---

# HTML5 Fundamentals

We all know that HTML5 has added some really cool features in version 5 and here are a few of the most used ones :
* Semantic keywords (like header, footer, article, section)  which makes it easy for search engine bots to read the page
* **Audio** and **video** tags 
* **Canvas** and **svg** tags
* Addition of the folllowing new HTML input types (datetime, email, number, URL etc)e) Addition of output as an output type.

Some other important concepts introduced in HTML5 include the following :
* **Geolocation API**  - This feature is extensively used by all location aware web applications of today's world
{% highlight ruby %}
//below code sets the lat and long variables to current latitude and longitude respectively if browser supports this Geolocation feature
If ((navigatior.geoloction() != undefined ) {
          lat= navigator.pos.coords.latitude, 
          long = navigator.pos.coords.longitude
         } 
{% endhighlight %}

* **LocalStorage** and **SessionStorage** - This feature is used by web applications which wnts to store some data in browser memory. Representative code snippets for the same: 
{% highlight ruby %} 
//below code sets value 'soumik' against the key named 'name' in localstorage if this feature is supported by the browser
        if(typeof(Storage) !== "undefined") {
                    localStorage.setItem("name","soumik");
                  }
{% endhighlight %}

Localstorage stays even after the browser is closed but SessionStorage is immediately destroyed after the current session ends.

### Localstorage vs Cookies vs indexedDB
**Cookies are a security risk as the data is exchanged evertime with the server. Cookies can store only 4KB of data. If your server
needs data, you have to store it in cookies.** 

**Localstorage / SessionStorage can  store only Strings as key / value pairs, so one has to use JSON.stringify() and JSON.parseString() to set / get non string data. Also it is essentially a DOM storage with a synchronous API. IF your client only needs the data, store it in localstorage / sessionstorage. Localstorage can store 5MB of data per domain with no expiration date.**

**IndexedDB** can store much **more data and can store data apart from String.** Also IndexedDB has a asynchronous API and hence does not block the UI. 

*This block will be enhanced later with examples of websockets and webworkers.*
