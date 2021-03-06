---
layout: post
title:  "Why Docker and its role in the CI/CD"
date:   2019-03-10 13:55:23 +0530
categories: DevOps
---

## Docker - What and why ?
Unless you are living in a cave, you must have heard the name of Docker although some of you might not have had the opportunity to work with Docker. 
That is perfectly ok! But I must admit without any iota of doubt - that there are very few softwares apart from Docker which had been able to create the kind of buzz which Docker had created in the last decade. 
Docker has literally taken the development and devops community by storm and have completely revolutionized the way in which we used to build and ship software.

# What problem does Docker solve ?
In very simple terms - Docker represents containers for your softwares just like actual containers which are used in the ports for transporting.
The very fact that we can use the same docker image to deploy our software in DEV / TEST/ ACC / PRD environments itself ensures that it irons out any environment spefiic issues.
So it just ensures that the exact same envionment is available for your software all the way. 
Say for example - you have built a Spring MVC based web application and it requires a certain version of JDK, Tomcat and MySQL to run. So you will build your container image with specific versions of these softwares pre-installed.  

# Docker's most common commands
Following are some major steps while you get started with Docker:
* Create a docker file
* Build the docker file to create an image for the container (docker build -t X)
* Build a container from the previously created image (docker run -d -p 80:8080 Y)
* Start the container
* Stop the container once your job is over (docker stop <container_id>)
* Destroy / remove the container - when you are sure that you no longer need it (docker rm <container_id>)
* Destroy / remove the image (docker images rm <image_id>)
* How to list all containers (docker ps -a)


# Docker's role in a modern CI / CD pipeline
In previous time - in a typical CD pipeline, we used to deploy the product binaries (which means JAR / WAR / EAR files for a Java EE application) but now we deploy the docker containers (which contain JDK, Tomcat and your binary deployed in Tomcat). The pipeline essentially stops the old container and removes it and then install the new container and start the same. 
