---
layout: post
title:  "Why use NoSQL"
date:   2017-08-22 16:55:23 +0530
categories: jekyll update
---

# Why use NoSQL solution

We are living in the age of data and it grows exponentially
in today’s world. Forget data intensive apps / companies like Youtube /
Facebook – even small to medium sized enterprises in today’s world are facing a
never seen before kind of data boom. I read somewhere that Facebook CEO Mark
Zuckerberg had famously said that there are more people on Facebook today that
the number of people living in the planet 100 years back. Isn’t it simply
incredible!! ?

So the question that we are facing now is how do
we manage this huge amount of data and also economically manage the same. One
thing is for sure – this huge volume of data can’t be efficiently and
economically managed using standard RDBMS solutions. This has given rise to a
completely different genre of databases which are commonly referred as *NoSQL databases*. At the moment, there
are 150+ types of NoSQL databases. Although each one of them tends to vary from
the other in some way or the other – following are some common properties that
can be attributed to all types of NoSQL databases:
* They don’t support standard ANSI SQL syntax
* They don't support ACID properties and tranactions

Interestingly the different NoSQL databases are broadly divided into the following main types:
* Key Value Store - -This is the simples type of NoSQL database which stores data in the form of a
key value pair where the key can be an atomic value and the value (depending on
the specific variants of the database) can be an atomic value or an array of
values or a data structure. Popular examples of this type of database include
Memcached, Redis, Riak etc. These key value pairs are very popularly used as
caching solutions to cache frequently referred data in mobile / web application
to increase the performance of desktop / mobile application
* Document Oriented Databases
* Bigtables / Column oriented database
* Graph databases

## CAP theorem
