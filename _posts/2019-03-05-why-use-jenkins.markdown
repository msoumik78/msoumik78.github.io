---
layout: post
title:  "Jenkins and its role in the CI/CD"
date:   2019-03-05 13:55:23 +0530
categories: DevOps
---

## Jenkins and its role in Continuous Integration / Continuous Deployment lifecycle

I think all of us are aware of the need of the DevOps/CI-CD in this world when we are working in Agile based projects ans strive for quick builds and deployments. Undoubtedly Jenkins is one of the primary touls that is used to setup a build and deployment pipeline which helps in building software and pushing/deploying the updated/latest version of the software to the target environments.

Some other tools which execute similar tasks as Jenkins include Bamboo(from Atlassian) , Teamcity, Hudson, Spinnaker etc. 

# What is Continuous Integration (CI) ?
This is a practice where the latest codebase (as soon as it is checked in a specific branch) is built (but not deployed) to ensure that there is no compilation issues when the latest code is pushed to the version control.  
So Continuous Integration jobs are normally triggered by developer commits in the target branch. 

# What is Continuous Deployment (CD) ?
On the other hand, continuous deployment jobs run at specific times of the day (may be twice a day) and builds the binary from the latest source and then deploys it to a common testing server.Often post deployment, some regression test harness is also triggered which verifies that basic product functionalities are intact/broken in the latest builds. 
So the continuous deployment job does the following:
* Builds the latest binary
* Uploads the latest binary to Nexus/ Artifactory (whatever binary version control system is available)
* Deploys the latest binary to the server using Ansible / Nolio / Bladelogic or other deployment tools

I'll try to create seperate blogs on Docker containers and also on Ansible based deployments

# Some best practices with regards to version control system (Github/ Gitlab) and the branching strategies
Normally every DevOps team follows their own practices but below contains some recommendations:
* Latest code is always contained in a branch named "_integration_"
* When a developer wants to develop a new feature/ fix a bug, he clones the _integration_ and creates a feature branch named _feature/X_ and carries out his task locally within that branch and when done he merges it back to _integration_. All the Continuous integration and continuous deployment jobs are run on the _integration_ branch normally.  
* When the softwarer is ready to be tested (and eventually released) - latest code is pushed from _integration_ to another branch named _release_. Now all bug fixes for the current releases are merged to _release_ and also ported manually to _integration_ 
* When its time to do production release, _release_ branch is merged to _master_ branch and it is deployed to production from _master_. So _master_ branch always contains the latest production code.


# Some best practices for setting up Jenkins for CI / CD jobs
In jenkins, you will have to configure/ enter details essentially for the following sections:
* Source code management - In this section, you will have to specify the Git repo and the branch to be used for building  
* Build Triggers - You will have to specify the trigger for the job which can be a polling Github at specific intervals.
* Build Environment and Build - Which means spefying whether maven or graddle or ANT will be used to do the build
* Post build actions - This is only applicable for the CD jobs where the 

