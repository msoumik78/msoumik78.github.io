---
layout: post
title:  "Modern day HTML5 quickstart"
date:   2017-09-11 16:55:23 +0530
categories: "Frontend"
---

# HTML5 Fundamentals

We all know that HTML5 has added some cool features over the previous versions and here a bunch of very useful and very east to use features :
* Addition of semantic keywords (like header, footer, article, section)  which makes it easy for search engine bots to read the page
* Addition of the audio and video tags 
* Addition of the canvas and svg tags
* Addition of the folllowing new HTML input types (datetime, email, number, URL etc)e) Addition of output as an output type.


Some other important concepts introduced in HTML5 include the following :
* Geolocation API  - This feature is extensively used by all location aware web applications of today's world
{% highlight ruby %}
          If ((navigatior.geoloction() != undefined ) {
                    lat= navigator.pos.coords.latitude, 
                    long = navigator.pos.coords.longitude
                   } 
{% endhighlight %}

* LocalStorage and SessionStorage - This feature is used by web applications which wnts to store some data in browser memory. Representative code snippets for the same: 
{% highlight ruby %} - 
          if(typeof(Storage) !== "undefined") {
                    localStorage.setItem(“foo”, “bar”);
                  }
{% endhighlight %}

Localstorage stays even after the browser is closed but SessionStorage is only applicable for the current browser session.

### Localstorage vs Cookies vs indexedDB
Cookies are a security risk as the data is exchanged evertime with the server. Cookies can store only 4KB of data. If your server
needs data, store it in cookies. 

Localstorage / SessionStorage can  store only Strings as key / value pairs, so one has to use JSON.stringify() and JSON.parseString() to set / get non string data. Also it is essentially a DOM storage with a synchronous API. IF your client needs data, store it in localstorage / sessionstorage. Localstorage can store 5MB of data per domain with no expiration date.

**IndexedDB** can store much more data and can store data apart from String.Main advantage of IndexedDB is that it is a asynchronous API and hence do not block the UI. 

### Webworkers
This helps to execute a javascript task in the background without blocking UI or user actions, sample code snippets below:
{% highlight ruby %}
var w;
function startWorker() {
    if(typeof(Worker) !== "undefined") {
          if(typeof(w) == "undefined") {            
              w = new Worker("demo_workers.js");        
           }        
         w.onmessage = function(event) {
              document.getElementById("result").innerHTML = event.data;
           };    
         } else {        
              document.getElementById("result").innerHTML = "Sorry! No Web Worker support.";
        }
}


function stopWorker() {     
    w.terminate();    
    w = undefined;
  }
{% highlight ruby %}