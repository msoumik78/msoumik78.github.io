---
layout: post
title:  "Jenkins and its role in the CI/CD"
date:   2019-03-05 13:55:23 +0530
categories: DevOps
---

## Jenkins and its role in Continuous Integration / Continuous Deployment lifecycle

I think all of us are aware of the need of the DevOps/CI-CD in this world when we are working in Agile based projects ans strive for quick builds and deployments. Undoubtedly Jenkins is one of the primary touls that is used to setup a build and deployment pipeline which helps in building software and pushing/deploying the updated/latest version of the software to the target environments.

Some other tools which execute similar tasks as Jenkins include Bamboo(from Atlassian) , Teamcity, Hudson, Spinnaker etc. 

# What is Continuous Integration ?
This is a practice where the latest codebase (as soon as it is checked in a specific branch) is built (but not deployed) to ensure that there is no compilation issues when the latest code is pushed to the version control.  
So Continuous Integration jobs are normally triggered by developer commits in the target branch. 

# What is Continuous Deployment ?
Omn the other hand, continuous deployment jobs run at specific times of the day (may be twice a day) and builds the binary from the latest source and then deploys it to a common testing server.Often post deployment, some regression test harness is also triggered which verifies that basic product functionalities are intact/broken in the latest builds. 

# Some best practices
