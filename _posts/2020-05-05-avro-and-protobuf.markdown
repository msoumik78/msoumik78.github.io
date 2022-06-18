---
layout: post
title:  "Avro and Protocol Buffer"
date:   2020-05-05 13:55:23 +0530
categories: Event-Driven-Architecture
---

# Protocol Buffer 

While there are several serialisation formats, the one which has really become popular in recent times is Protocol Buffers (from Google).
It is alternate to another popular serialisation framework - which is Avro.
Here is very short quick intro on protocol buffers :

1. Schema is defined in .proto files and then corresponding java files can be created using Proto compiler or maven plugin
2. Example of a proto file :

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

3. Each of the fields can be required/optional or repeated
4. The identifier at the end of the field is the tag for the corresponding field, normally tags from 1-15 occupy lesser byte.
5. Some very popular usage of protobuf in industry :
    1. Used as an alternate to json as response format for Spring boot based REST endpoints - for lesser size and lesser response time
    2. Also used in gRPC - it is faster than spring boot
    3. Also used as an alternate to Avro in Kafka
6. Very simple java code to show serialisation using protobuf :

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


7. Protobuf is more aligned to multiple languages than Avro
8. Also making a change to the existing schema in Protobuf is easier

