---
layout: post
title: "In memory datastores - Memcache and Redis"
date: 2017-10-10 16:55:23 +0530
categories: NoSQL
---

# In memory data stores
Often in low latency web and mobile applications, we need the existence of a caching layer to temporarily store some frequently sought entities provided they don't change frequently over time. Examples would be country list, state list, language list, currency list etc. In the past, these caching systems were mostly implemented using some custom data structures (like Ehcache is very still very popular among Java developers) but recently, we have seen that these caching engines are best implemented by a seperate process which runs a key-value pair database (like Memcache , Redis).
Both memcache and redis are key value type databases which can be very easily and effectively used as a caching system.

# What is Memcache ?
It's probably one of the simplest key value NoSQL database. It's basically a distributed in memory object caching system which means that it is not a persistent data store and all data is lost after restart. It's very simple which means that it is unaware of any other nodes an hence not fault tolerant. Its eviction policy is LRU.

It uses the *libevent* library for network communications. 

Use the below command to start it : ** memcached – d -u <UserName> -p <TCP/IP Port> - U <UDP Port> **

Most important commands for setting data in the cache are (all of them accept the parameters : command flag expirationTime sizeInBytes) :
* set
* add
* append
* prepend
* cas (check and set) – it only sets the data if it has not modified by any other clients since last fetched. 

Hence it accepts a token (which can be retrieved by the gets command)
Most important commands for retrieving data from the cache :
* get
* gets (used to retrieve the token used in cas command)

Command used to retrieve the statistics - STATS
In Java – **SpyMemcached** Client is most popularly used to get / set data with memcached (It returns a Future object post the get / set operation)

### Memcached vs Redis
Redis is in fact a abetter solution because of the following 3 features:
* a) Conditional persistence in the database
* b) Multilpe data types (it is rather a data structure mechanism) which are Strings, Hashes, Lists, Sets and Ordered Sets
* c) 6 different cache eviction policies
* d) In Memcached – key is 215 B and value is 1 MB, in Redis – Key & value can be as big as 512 MB
* e) Redis offers replication

However following are the cases where memcached is suitable:
* a) Relatively less amounts of data
* b) Slightly more efficient as it consumes lesser memory
