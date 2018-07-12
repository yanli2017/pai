# Open Platform for AI (PAI)

[![Build Status](https://travis-ci.org/Microsoft/pai.svg?branch=master)](https://travis-ci.org/Microsoft/pai)

# Table of Contents
1. [What’s OpenPAI?](#what’s-openpai)
2. [Why choose OpenPAI](#why-choose-openpai)
3. [Setup](#setup)
4. [Quick Start](#quick-start)
5. [Contributing](#contributing)
6. [Where to Go from Here](#where-to-go-from-here)

## What’s OpenPAI?
Platform for AI (PAI) is a platform for cluster management and resource scheduling. The platform incorporates the mature design that has a proven track record in Microsoft's large scale production environment.

PAI supports AI jobs (e.g., deep learning jobs) running in a GPU cluster. The platform provides PAI runtime environment support, with which existing deep learning frameworks, e.g., CNTK and TensorFlow, can onboard PAI without any code changes. The runtime environment support provides great extensibility: new workload can leverage the environment support to run on PAI with just a few extra lines of script and/or Python code.

<p style="text-align: left;">
  <img src="./sysarch.png" title="System Architecture" alt="System Architecture" />
</p>

The [system architecture](./docs/system_architecture.md) is illustrated above.

## Why choose OpenPAI?
### Microservices Architecture
PAI embraces a microservices architecture: every component runs in a container. The system leverages Kubernetes to deploy and manage static components in the system. The more dynamic deep learning jobs are scheduled and managed by Hadoop YARN with our GPU enhancement. The training data and training results are stored in Hadoop HDFS.
### Deep learning workload and GPU scheduling
PAI supports GPU scheduling, a key requirement of deep learning jobs. For better performance, PAI supports fine-grained topology-aware job placement that can request for the GPU with a specific location (e.g., under the same PCI-E switch).
### Run Anywhere
OpenPAI is open source giving you the freedom to take advantage of on-premises, hybrid, or public cloud infrastructure.
### Open and Pluggable
One key purpose of PAI is to support the highly diversified requirements from academia and industry. PAI is completely open: it is under the MIT license. PAI is architected in a modular way: different module can be plugged in as appropriate. This makes PAI particularly attractive to evaluate various research ideas, which include but not limited to the following [components](./docs/reasearch.md).

## Setup
### &ensp;&ensp;&ensp;Prerequisite
We assume that the whole cluster has already been configured by the system maintainer to meet the following requirements:

- A [dev-box](./how-to-setup-dev-box.md) has been set up and can access the cluster.
- SSH service is enabled on each of the machines.
- All machines share the same username / password for the SSH service on each of them.
- The username that can be used to login to each machine should have sudo privilege.
- All machines to be set up as masters should be in the same network segment.
- A load balancer is prepared if there are multiple masters to be set up

### &ensp;&ensp;&ensp;[Quickstart deployment process](./docs/quick_deployment.md)
#### &ensp;&ensp;&ensp;&ensp;Step 0. Prepare the dev-box
#### &ensp;&ensp;&ensp;&ensp;Step 1. Prepare the quick-start.yaml file
#### &ensp;&ensp;&ensp;&ensp;Step 2. Generate PAI configuration files
#### &ensp;&ensp;&ensp;&ensp;Step 3. Boot up Kubernetes
#### &ensp;&ensp;&ensp;&ensp;Step 4. Start all PAI services

## Quick Start
#### &ensp;&ensp;&ensp;&ensp;1. Upload data and code
Use HDFS tools to upload your code and data to HDFS on the system. We upload a [Docker image](https://hub.docker.com/r/paiexample/pai.example.hdfs/) to DockerHub with built-in HDFS support.
Please refer to the [HDFS commands guide](https://hadoop.apache.org/docs/r2.7.2/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html) for details. 
#### &ensp;&ensp;&ensp;&ensp;2. Submit job
- Prepare a job config file
Prepare the [config file](#json-config-file-for-job-submission) for your job.
- Submit the job through web portal
Open web portal in a browser, click "Submit Job" and upload your config file.

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

## Where to Go from Here
#### &ensp;&ensp;&ensp;&ensp;[System architecture](./docs/system_architecture.md)
#### &ensp;&ensp;&ensp;&ensp;[OpenPAI Programming Guides](https://github.com/Microsoft/pai/blob/master/examples/README.md)
#### &ensp;&ensp;&ensp;&ensp;[Restful API Docs](https://github.com/Microsoft/pai/blob/master/rest-server/README.md)
#### &ensp;&ensp;&ensp;&ensp;[Deployment Guides](https://github.com/Microsoft/pai/blob/master/pai-management/doc/cluster-bootup.md)
#### &ensp;&ensp;&ensp;&ensp;[Cluster Maintenance Guides](https://github.com/Microsoft/pai/wiki/Cluster-Maintenance)
#### &ensp;&ensp;&ensp;&ensp;Other Documents:
##### &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;[Configuration: customize OpenPAI via its configuration](https://github.com/Microsoft/pai/blob/master/pai-management/doc/how-to-write-pai-configuration.md#cluster_configuration)
##### &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;[Monitoring: track the behavior of your jobs]()
##### &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;[Job Scheduling: scheduling resources across OpenPAI jobs](https://github.com/Microsoft/pai/blob/master/hadoop-ai/README.md)
##### &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;[FrameworkLauncher: launching customize Framework by Launcher Service](https://github.com/Microsoft/pai/blob/master/frameworklauncher/README.md)
##### &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;[Third Party Projects: related third party OpenPAI projects]()

#### &ensp;&ensp;&ensp;External Resources:
##### &ensp;&ensp;&ensp;&ensp;&ensp;StackOverflow: [tag openpai](https://stackoverflow.com/questions/tagged/openpai)
##### &ensp;&ensp;&ensp;&ensp;&ensp;Mailing Lists: ask questions about OpenPAI here
