---
layout: post
title:  "Let's quickly learn MongoDB"
date:   2017-08-24 16:55:23 +0530
categories: jekyll update
---

# MongoDB

MongoDB
is one of the most popular document oriented databases which is a major type of
NoSQL database.  The document oriented databases closely resemble RDBMS in the sense
that the data is stored in form of documents (which are similar to rows in RDBMS) and the 
documents are stored in collections (which are similar to tables in RDBMS).  
The biggest difference with RDBMS is that the documents are indeed meant for storing semi 
structured data and also the documents are completely schema free. This means that in MongoDB
you can go ahead and store documents in collections without even creating the collection
in the first place. This also means that MongoDb insert operations are much
faster than corresponding insert operations of RDBMS.



## Typical CRUD syntax in MongoDB

Following are the useful CRUD commands: 
* a) db.collectionName.find () : Uses the operator $eq, $ne, $gt, $gte, $lt, $lte, $or
Example : db.employees.name (title : “Gupta” $or designation : SA)
Find command also takes an optional second argument which is used to specify the projection :Example : db.collectionName.find ( , {title:1, Name :0})It means only title will be displayed.
Also number of rows returned can be limited by using the command : db.collectionName.find(). Limit (5)
Also the result can be sorted by using the command : db.collectionName.find().sort (“title:1” , “Name : -1”)This means the resultset will be sorted by title in ascending order and name in descending order.
* b) db.collectionName.insert ()
* c)db.collectioName.update (, $set )First argument is used to identify the document and second argument after $set to set the data.
* d) db.collectionName.remove()


## MongoDB Text & geospatial Index

## MongoDB Replication & Sharding

How to create a sharded cluster in MongoDB
* a) First start mongod process in 3 machines (using the command : mongod -host <> - port 27017 – replySet <> 
* b) Then connect a mongo process to any one instance and issue the commands (rs.initialize() and 
  then rs.add <Second Server> and rs.add <Third Server>
  * c) After that start the 3 config servers with the command (mongod – configServr -replySet <>
  * d) After that start the mongos instance using the command (mongos -cnfigdb ConfigDb1:ConfigDB2:ConfigDB3)
  * e) After that , start a mongo process and connect to the mongos instance and issue the command 
    (sh.addShard  (rs1/ReplicaInatance1:ReplicaInstance2:ReplicaInatance3)
