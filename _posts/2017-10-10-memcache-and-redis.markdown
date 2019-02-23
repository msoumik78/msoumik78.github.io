---
layout: post
title: "In memory datastores - Memcache and Redis"
date: 2017-10-10 16:55:23 +0530
categories: NoSQL
---

# In memory data stores
Often in low latency web and mobile applications, we need the existence of a caching layer to temporarily store some frequently sought entities provided they don't change frequently over time. Examples would be country list, state list, language list, currency list etc. **In the past, these caching systems were mostly implemented using some custom data structures (like Ehcache is still very popular among Java developers) but recently, we have seen that these caching engines are best implemented by a seperate process which runs a key-value pair database (like Memcache , Redis).**

Both memcache and redis are key value type databases which can be very easily and effectively used as a caching system.

### Memcache
It's probably one of the simplest key value NoSQL database. It's basically a distributed in memory object caching system which means that it is not a persistent data store and all data is lost after restart. It's very simple which means that it is unaware of any other nodes an hence not fault tolerant. Its eviction policy is LRU.
It uses the *libevent* library for network communications. 
if you want to give it a try, download it locally and use the below command to start it : memcached – d -u <UserName> -p <TCP/IP Port> - U <UDP Port>

Most frequently used commands for setting a value in the cache (all of them accept the parameters : command flag expirationTime sizeInBytes) :
* set
* add
* append
* prepend
* cas (check and set) – it only sets the data if it has not modified by any other clients since last fetched. Hence it accepts a token (which can be retrieved by the gets command)

Most frequently used commands for retrieving data from the cache :
* get
* gets (used to retrieve the token used in cas command)

The command that can be used to retrieve the statistics is  *STATS*

Following is some code snippets to connect to memcache server and then set and retrieve values from memcache:
{% highlight ruby %}

//Normally we have to use telnet protocol to connect to memcache
$telnet 127.0.0.1 11211
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

// Below command sets the value 'Soumik' against the key 'name'. Also expiration time of the cache is set to 900 secs. The 
// command returns STORED indicating that the value was indeed stored successfully. 
set name 0 900 9
Soumik
STORED

// Below command retrieves the value set against the key 'name'
get name
VALUE name 0 9
Soumik
{% endhighlight %}

In Java – **SpyMemcached** Client is most popularly used to get / set data with memcached (It returns a Future object post the get / set operation). Following is some representative Java code snippet to connect to memcache from java:

{% highlight ruby %}
   MemcachedClient mcc = new MemcachedClient(new InetSocketAddress("127.0.0.1", 11211));
      System.out.println("Connection to server sucessfully");
      
      //not set data into memcached server
      System.out.println("set status:"+mcc.set("tutorialspoint", 900, "memcached").done);
      
      //Get value from cache
      System.out.println("Get from Cache:"+mcc.get("tutorialspoint"));
{% endhighlight %}

### Redis
Redis is another very popular and extremely powerful key-value NoSql datbase. It is much more versatile than memcache.
Some very important differences with memcache:
* Conditional persistence in the database - so unlike memcache, redis can also be used as the persistence layer
* Supports multilpe data types which are Strings, Hashes, Lists, Sets and Ordered Sets
* Supports 6 different cache eviction policies
* In Memcache – key is only 215 Bytes and value is 1 MB, in Redis – both Key & value can be as big as 512 MB
* Redis offers replication
* Another very powerful feature of redis is that it can also double as a messaging solution 

However following are the cases where memcached is suitable:
* Relatively less amounts of data
* Slightly more efficient as it consumes lesser memory


Below are some code snippets for some standard operations in Redis from the redis-cli console:
{% highlight ruby %}
// Sets a key named 'name' to 'Soumik' and then retrieves the value against the key
SET name Soumik
GET name
Soumik

// Below is an example of redis hash which is like a java hashmap. So a has named 'employee' is set
HMSET employee name Soumik age 40 designation architect
HGET employee name
Soumik
HGET employee age
40

// Below code snippets creates a set named 'friends' and add 3 entries in the set
SADD friends Sanjay
SADD friends Bumba
SADD friends Manoj

{% endhighlight %}


### Ehcache vs Memcache vs Redis

EhCache is probably the most favourite and widely used caching system for Java developers. **If your requirement is that, the caching system will only be accessible from java based systems, EhCache is probably the way to go.**

**However if you want to setup a standalone but simple caching engine which can be leveraged by various applications (Java and non Java apps like NodeJs/ PHP/Python) within the enterprise landscape, you can go for Memcache.**
Redis scenario is similar to memcache but even more flexible. So probably **redis usage is recommended when you can possibly want to persist the cache from time to time (or even leverage redis as the primary data store) or you have a messaging requirement (will cover the messaging aspect of redis in a seperate post) as well.** Like memcache, Redis is also a distributed system which can be leveraged by various Java & Non Java based applications in the enterprise landscape. 

*Will try to cover redis based messaging in a different blog and compare it with Apache ActiveMQ / RabitMQ*
