---
type: post
title:  "Hadoop fundamentals"
date:   2017-10-09 16:55:23 +0530
categories: jekyll update
---


Hadoop standalone mode :
By default, Hadoop is configured to run in a non-distributed or standalone mode, as a single Java process. There are no daemons running and everything runs in a single JVM instance. HDFS is not used.

Hadoop pseudo distributed mode :The Hadoop daemons run on a local machine, thus simulating a cluster on a small scale. Different Hadoop daemons run in different JVM instances, but on a single machine. HDFS is used instead of local FS.

Steps for hadoop installation in pseudo distributed mode in Ubuntu
* 1) Create a hadoop user and hadoop group$ sudo addgroup hadoop$ sudo adduser --ingroup hadoop hduser
* 2) Install jdk (if not already installed)$ sudo apt-get install sun-java6-jdk
* 3) Install ssh (if not already installed)
* 4) Ensure passwordless ssh access :hduser@ubuntu:~$ ssh-keygen -t rsa -P ""hduser@ubuntu:~$ cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys
* 5) Disable IPV6:Add the following lines to the end of the file /etc/sysctl.conf
net.ipv6.conf.all.disable_ipv6 = 1net.ipv6.conf.default.disable_ipv6 = 1net.ipv6.conf.lo.disable_ipv6 = 1


Change the following configuration files :
* a) core-site.xml : Following are the properties to be changed:fs.default.name  - hdfs://localhost:9000Hadoop.tmp.dir
* b) hdfs-site.xml : Following are the properties to be changed dfs.replication
* c) mapred-site.xml : mapred.job.tracker  - localhost:9010

Steps to start the hadoop cluster:
* 1) Formatting the namenode : bin/hadoop namenode -format
* 2) Start the hadoop cluster :sbin/start-dfs.shsbin/start-yarn.sh
