# Open Platform for AI (OpenPAI) ![alt text][logo]

[logo]: ./pailogo.jpg "OpenPAI"

[![Build Status](https://travis-ci.org/Microsoft/pai.svg?branch=master)](https://travis-ci.org/Microsoft/pai)
[![Coverage Status](https://coveralls.io/repos/github/Microsoft/pai/badge.svg?branch=master)](https://coveralls.io/github/Microsoft/pai?branch=master)

# Table of Contents
1. [What's OpenPAI](#what's-openpai)
2. [Why choose OpenPAI](#why-choose-openpai)
3. [Setup](#setup)
4. [Model Training](#model-training)
5. [Learn More](#learn-more)
6. [Contributing](#contributing)

## What's OpenPAI
OpenPAI is a complete open source deep learning platform software. The platform incorporates the mature design that has a proven track record in Microsoft's large scale production environment.

OpenPAI supports AI jobs (e.g., deep learning jobs) running in a GPU cluster. The platform provides OpenPAI runtime environment support, with which existing deep learning frameworks, e.g., CNTK and TensorFlow, can onboard OpenPAI without any code changes. The runtime environment support provides great extensibility: new workload can leverage the environment support to run on OpenPAI with just a few extra lines of script and/or Python code.

## Why choose OpenPAI
### Support on-premises and easy to deploy

- OpenPAI giving user the freedom to take advantage of on-premises, hybrid, or public 
Cloud infrastructure. 
- Comprehensive documents to guide user to deployment.
- Supports single-box deployment for trial users.

### Design for Deep Learning and heterogeneous hardware 

- Pre-built docker for popular AI frameworks, including new hardware.
- Support Distributed training.
- Locality aware GPU scheduling. Heterogeneous hardware as first level concept for scheduler design. 

### Most complete solution for deep learning 

- User, data and job management via Virtual Cluster concept.
- Support all mainstream deep learning frameworks. Support complete training pipeline at one cluster: deep learning training combined with big data and jobs.
- Support HDFS/Hadoop, K8s, Yarn eco-system.

### Easy to extend 

- One key purpose of OpenPAI is to support the highly diversified requirements from academia and industry. OpenPAI is completely open: it is under the MIT license. 
- OpenPAI is architected in a modular way: different module can be plugged in as appropriate. This makes OpenPAI particularly attractive to evaluate various research ideas, which include but not limited to the following [components](./docs/reasearch.md).

## Setup
#### 1 Prerequisite
We assume that the whole cluster has already been configured by the system maintainer to meet the following requirements:
- Recommend Ubuntu 16.04 LTS. (CentOS and other linux system is not support at this time).
- Assign each server static IP address.
- Server can access the external network. Have access to a Docker registry service (e.g., Docker hub) to store the Docker images for the services to be deployed.
- All machines' SSH service is enabled, share the same username / password and have sudo privilege. 
- Need NTP service for clock synchronization. Recommend use default.
- Recommend no Docker installed or a Docker with api version >= 1.26.
- Network reachable between servers.

#### 2 Setup
##### 2.1 For beginner to setup cluster: [Quickstart deployment process](./docs/quick_deployment.md)
##### 2.2 For advanced user and developer to setup cluster: [Deployment Guides](https://github.com/Microsoft/pai/blob/master/pai-management/doc/cluster-bootup.md)

## Model Training

- [Use Visual studio submit jobs](https://github.com/Microsoft/vs-tools-for-ai/blob/master/docs/pai.md) 
- [Use Visual studio code submit jobs](https://github.com/Microsoft/vscode-tools-for-ai/blob/master/docs/quickstart-05-pai.md)
- [Using PAI webportal submit jobs](https://github.com/Microsoft/pai/blob/yanjga/doc/job-tutorial/README.md#job-submission)
- [Job samples](https://github.com/Microsoft/pai/tree/yanjga/doc/examples)


## Learn More
The OpenPAI user [Learn More Documentation](./docs/documentation.md) provides in-depth instructions for using OpenPAI.

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
