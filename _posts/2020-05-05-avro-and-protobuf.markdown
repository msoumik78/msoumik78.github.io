---
layout: post
title:  "Avro and Protocol Buffer"
date:   2020-05-05 13:55:23 +0530
categories: Event-Driven-Architecture
---

# Serialisation formats

While all of us understand the need of serialisation to transfer data across network devices - it often becomes difficult to make the right choice of the serialisation framework for the project. Out of many such serialisation formats - 2 which are m0st frequently used are Protocol Buffers and Avro. In this blog, I'll summarise both of them and also provide my personal prefernce / opinion based on experience.


# Protocol Buffers (often called Protobuf)
This one is from Google and has really become popular in recent times. Here is very short quickstart guide or summary  :

* Schema is defined in .proto files and then corresponding java files can be created using Proto compiler or maven plugin. Below is an example of a proto file which is the schema definition:

{% highlight ruby %}

syntax = "proto3";
package model;

option java_package = "com.experiment.protobuf.model";
option java_outer_classname = "StudentProto";

message Student {
  int32 student_id = 1;
  string student_name = 2;
}
{% endhighlight %}

* Each of the fields in the above schema can be required/optional or repeated
* The identifier at the end of the field is the tag for the corresponding field, normally tags from 1-15 occupy lesser byte.
* Some very popular uses of protobuf in industry :
    - Used as an alternate to json as response format for Spring boot based REST endpoints - for lesser size and lesser response time
    - Also used in gRPC - it is faster than spring boot
    - Also used as an alternate to Avro in Kafka

  Below is a sample java code to show serialisation using protobuf :

{% highlight ruby %}

StudentProto.Student student1
    =  StudentProto.Student.newBuilder()
        .setStudentId(1)
        .setStudentName("Soumik")
        .build() ;
FileOutputStream output = new FileOutputStream("test.txt");
student1.writeTo(output);

byte[] bytes = Files.readAllBytes(Paths.get("test.txt"));
StudentProto.Student student2 = StudentProto.Student.parseFrom(bytes);
{% endhighlight %}

* Protobuf is more aligned to multiple languages than Avro
* Also making a change to the existing schema in Protobuf is easier


# Avro 
Avro was originally created in context of Hadoop (which is the Big data framework from DOg Cutting). Again here is a short summary:

* The schema is usually a json file named .avsc
* Usually a maven plugin is used to generate the model objects from the schema.
* Below is an example of json schema :       

{% highlight ruby %}
{"namespace": "example.avro",
 "type": "record",
 "name": "User",
 "fields": [
     {"name": "name", "type": "string"},
     {"name": "favorite_number",  "type": ["int", "null"]},
     {"name": "favorite_color", "type": ["string", "null"]}
 ]
}
{% endhighlight %}

* Avro is the default serialisation format which was used in Kafka. Nowadays Kafka has also come up with support for protobuf.
  Below is a sample java code to achieve serialisation :

{% highlight ruby %}
User user1 = new User();
    user1.setName("Alyssa");
    user1.setFavoriteNumber(256);

DatumWriter<User> userDatumWriter = new SpecificDatumWriter<User>(User.class);
DataFileWriter<User> dataFileWriter = new DataFileWriter<User>(userDatumWriter);
dataFileWriter.create(user1.getSchema(), new File(fileNameToStoreSerializedData));
dataFileWriter.append(user1);
dataFileWriter.close();
{% endhighlight %}

