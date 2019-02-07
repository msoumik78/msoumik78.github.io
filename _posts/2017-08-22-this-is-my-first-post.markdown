---
layout: post
title:  "Why use NoSQL"
date:   2017-08-22 16:55:23 +0530
categories: NoSQL
---

# Why use NoSQL solution

We are living in the age of data and it grows exponentially
in today’s world. Forget data intensive apps or companies like Youtube /
Facebook – nowadays even small to medium sized enterprises are facing a
never seen before kind of "data boom". I read somewhere that Facebook CEO Mark
Zuckerberg had famously said that there are more people on Facebook today than
the number of people living in the planet some 80 years back !!!

So the question that we are facing now is how do we manage this huge amount of data and also economically store/ retrieve the same. One
thing is for sure – this huge volume of data can’t be efficiently and economically managed using standard RDBMS solutions. This has given rise to a completely different genre of databases which are commonly referred as *NoSQL databases*. At the moment, there
are 150+ types of NoSQL databases. Although each one of them tends to vary from the other in some way or the other – following are some common properties that can be attributed to all types of NoSQL databases:
* They don’t support standard ANSI SQL syntax
* They don't support ACID properties and tranactions

Interestingly the different NoSQL databases are broadly divided into the following main types:
* Key Value Store - This is the simplest type of NoSQL database which stores data in the form of a key value pair where the key can be an atomic value and the value (depending on the specific variants of the database) can be an atomic value or an array of
values or a data structure. Popular examples of this type of database include Memcached, Redis, Riak etc. These key value pairs are very popularly used as caching solutions to cache frequently referred data in mobile / web application to increase the performance of desktop / mobile application
* Document Oriented Databases - These are probably closest to RDBMS but they have a dynamic schema. Put differently, you do not need to create the table before storing data there. Most popular example of this type of NoSQL is MongoDB. 
* Bigtables / Column oriented database - These are the databases which are used in modern day datawarehousing scenarios. COlumn oriented basically means that all values of a specific column are stired together.
* Graph databases - These are very niche and can ideally be used to design social networking data models. Example is Neo4J.

# Let’s understand CAP Theorem and the debate between Consistency & Availability

Interestingly there is a very good theorem which clearly explains the challenges of a distributed architecture. It is known as CAP
theorem. Essentially it states that out of the following 3 properties/characteristics, any database system in the world can honor at most 2 and can never satisfactorily honor all 3. Well, below are the 3 properties/characteristics
that we were talking about:
* Consistency (C) – This indicates, whether in a distributed database architecture (where the data is sharded and stored in many
machines), the database can provide correct (latest) results to all the clients
querying for results. 
* Availability (A) – This indicates, whether in a
distributed database architecture, the database can provide response to all the
clients querying for results. Although some of the responses can still not be
latest, a database with a higher availability will still strive to provide some
response to all of its clients. 
* Partition Tolerance (P) – This indicates,
whether in a distributed database architecture, the database system, as a
whole, can still respond if there are outages / network failures of some of the
nodes.

As you might have probably guessed, the first 2 characteristics (Consistency & Availability) are often a tradeoff. So
basically it means that if you want higher consistency, you will have to forego a bit of availability. This means that if you want to show correct response to your clients, it means that may be some clients will not receive response at all but whoever will receive response – they will always get the latest response. Imagine the case of a messaging platform – where consistency is of paramount
importance – you can’t afford to show a stale message to any client but it is probably okay if you can’t respond to all clients. 

On the other hand – if you want more availability you will have to let go a bit of consistency. Which means that if you want to show
response to all clients – it might mean some clients will indeed see the latest response while some others might be seeing a bit of stale response at the moment. As an example imagine an ecommerce platform – where all users are displayed an array of huge number of products. It is very important that all users are shown the list of products while it might be okay if some users might still not see the latest product while some others will see all the latest products. 

So in the world of distributed databases –
Consistency and availability are always a tradeoff. However if you go for less consistency (and more availability) – the clients which are receiving (at the moment) a stale response – they will also eventually see the latest response. This is known as the concept of eventual consistency. So in the world of NoSQL – we say that they follow a model of **BASE** (contrary to the ACID characteristics of RDBMS) – which means they are Basically Available, they are in a Soft state and will be Eventually Consistent.
