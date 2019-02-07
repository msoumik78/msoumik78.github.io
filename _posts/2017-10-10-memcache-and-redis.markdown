---
layout: post
title: "In memory datastores - Memcache and Redis"
date: 2017-10-10 16:55:23 +0530
categories: NoSQL
---

# In memory data stores
Often in low latency web and mobile applications, we need the existence of a caching layer to temporarily store some frequently sought entities provided they don't change frequently over time. Examples would be country list, state list, language list, currency list etc. In the past, these caching systems were mostly implemented using some custom data structures (like Ehcache is still very popular among Java developers) but recently, we have seen that these caching engines are best implemented by a seperate process which runs a key-value pair database (like Memcache , Redis).
Both memcache and redis are key value type databases which can be very easily and effectively used as a caching system.

### Memcache
It's probably one of the simplest key value NoSQL database. It's basically a distributed in memory object caching system which means that it is not a persistent data store and all data is lost after restart. It's very simple which means that it is unaware of any other nodes an hence not fault tolerant. Its eviction policy is LRU.
It uses the *libevent* library for network communications. 
if you want to give it a try, download it locally and use the below command to start it : **memcached – d -u <UserName> -p <TCP/IP Port> - U <UDP Port>**

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

Following is some code snippets to set and retrieve values from memcache:
{% highlight ruby %}
set w3big 0 900 9
memcached
STORED

get w3big
VALUE w3big 0 9
memcached
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
