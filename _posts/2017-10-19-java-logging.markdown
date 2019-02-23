---
layout: post
title: "Java logging"
date: 2017-10-19 16:55:23 +0530
categories: Java
---

# Logging in a Java application
Logging is a fundamental aspect of any enterprise class software development as when it is designed well, it is able to provide just sufficient information without cluttering the output files. There are various ways of logging in Java and includes the following:
* Using a Logging facade like SL4J
* Using an implementation (like Log4J / Logback) directly  

Log levels are generally of the following types (although it varies from one implementation to another) - from top to bottom, the severity increases which means the one at the top is least severe while the one at the bottom is most severe:
* TRACE / FINER
* DEBUG
* INFO
* WARN
* ERROR
* SEVERE
* FATAL


# SL4J vs LogBack
SL4J is one of the most commonly used logging frameworks/façades and it needs to be backed up by a logging implementation which can be Log4j, Java Logging or Logback. Using SL4J is always a better design choice because of the following reasons :
* It is just a facade and any logging implementation can be tied to it
* It is better performing. Example - logger.debug("There is an issue for user named {}", user) --> The string concatenation (which is very costly) does not happen if debug is disabled.Also Logback contains a native implementation (which has almost zero memory footprint) of SL4J and hence **SL4J-Logback combination is best**.

# Logging best practices
Some of the commonly used best practices for java logging would be:
* In production, log only ERR and above (meaning more severe) so that production logs are not unnecessarily cluttered
* In Dev, log DEBUG (and more severe) to understand exactly what's going on
* Log precisely with all the contextual information
* Preferably use a combination of SL4J and Logback.

# Log collection and analysis
Apart from logging correctly, another aspect is collecting the log files and analyzing them properly. In today's world, this has become even more significant as logs are being accumulated in various servers and they need to be brought to some common place for analysis.
Hence below are the tools which are used in today's world for log analysis: 
* ELK stack (ElasticSearch-LogStash-Kibana) - Logstash helps to collect the log files and store them in the indexing engine 'ElasticSearch' and Kibana is the Web UI for visualization and analysis
* Splunk - This is another common tool, particularly in the big data world, which is used for storing, searching and analyzing log files. 

