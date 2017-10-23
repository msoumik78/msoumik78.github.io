|layout|title|date|categories|
|---|---|---|---|
|post|"Sprk Concepts"|2017-10-18 10:30:00 +0530|jekyll update| 


# Spark Core

First copy the Spark binary distribution and untar it.
Then login as 'hduser' and set JAVA_HOME as : export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64/
Then go to the folder - /home/soumik/apache/spark/spark-1.6.2-bin-hadoop2.6 and execute the command : 
bin/spark-shell

This will return a command prompt
scala >

Some common commands which can be executed from this prompt are as follows:

sc.version
sc.appName
:load spark-core-commands.scala
:quit

The wordcount program in spark using scala:

import org.apache.spark.SparkContext
import org.apache.spark.SparkContext._
val txtFile = "README.md"
val txtData = sc.textFile(txtFile)txtData.cache()
val wcData = txtData.flatMap(l => l.split(" ")).map(word => (word, 1)).reduceByKey(_ + _)
wcData.collect().foreach(println)




