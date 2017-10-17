---
layout: post
title:  "Scala concepts"
date:   2017-08-22 16:55:23 +0530
categories: jekyll update
---

# Scala Concepts

### How to run a Scala Program

Some important concepts:
* There is no hard and fast rule that scala source file should contain a class name which is the same as the name of the source file.
* Normally in scala – the program is first compiled using  -scalac X.scalaand then run usingscala X
* However since this interpreter takes a while, there is another faster interpreter in scala termed as fsc. This one runs a server daemon process, hence the first time invocation can take a while but subsequent invocations are much faster.
* Scala has a command line REPL utility which can be used to run any command. Some commands can be put in a scala script file and then the file can be run using the command (however the script needs to have expression and not just class declaration):scala X.scala
* Semicolons at the end of each line of source code is not required.
* Multiline strings can be formed using triple quotes. 

Remember : This internally first compiles and then runs the bytecode
