# Open Platform for AI (OpenPAI) ![alt text][logo]

[logo]: ./pailogo.jpg "OpenPAI"

[![Build Status](https://travis-ci.org/Microsoft/pai.svg?branch=master)](https://travis-ci.org/Microsoft/pai)
[![Coverage Status](https://coveralls.io/repos/github/Microsoft/pai/badge.svg?branch=master)](https://coveralls.io/github/Microsoft/pai?branch=master)

OpenPAI is an open source platform that provides complete AI model training and resource management capabilities, it is easy to extend and supports on-premise, cloud and hybrid environments in various scale. 

# Table of Contents
1. [When to consider OpenPAI](#when-to-consider-openpai)
2. [Why choose OpenPAI](#why-choose-openpai)
3. [How to deploy](#how-to-deploy)
4. [How to use](#how-to-use)
5. [Resources](#resources)
6. [Get Involved](#get-involved)
7. [Contributing](#contributing)

## When to consider OpenPAI
1. When your organization need a better utilization of AI computing resources (GPU/CPU etc.). On demand allocates resources. 
2. When your organization need an easy IT ops platform for AI.
3. When your organization need to share and reuse common AI assets like Model, Data, Environment, etc.
4. When you want to run complete training pipeline in one place. 


## Why choose OpenPAI
The platform incorporates the mature design that has a proven track record in Microsoft's large-scale production environment.

### Support on-premises and easy to deploy

OpenPAI is a full stack solution. OpenPAI not only supports on-premises, hybrid, or public Cloud deployment, but also supports single-box deployment for trial users.

### Support popular AI frameworks and heterogeneous hardware

Pre-built docker for popular AI frameworks. Easy to include heterogeneous hardware. Support Distributed training, such as distributed TensorFlow.

### Most complete solution and easy to extend

OpenPAI is a most complete solution for deep learning, support virtual cluster, compatible Hadoop / kubernetes eco-system, complete training pipeline at one cluster etc. OpenPAI is architected in a modular way: different module can be plugged in as appropriate. 


## How to deploy
#### 1 Prerequisites
Before start, you need to meet the following requirements:

- Ubuntu 16.04
- Assign each server static IP address. Network reachable between servers.
- Server can access the external network. Have access to a Docker registry service (e.g., Docker hub) to store the Docker images for the services to be deployed.
- All machines' SSH service is enabled, share the same username / password and have sudo privilege.
- Need to enable NTP service.
- Recommend no Docker installed or a Docker with api version >= 1.26.

#### 2 Deploy OpenPAI
##### 2.1 [Quick deploy with default settings](./docs/quick_deployment.md)
##### 2.2 [Customized deploy](https://github.com/Microsoft/pai/blob/master/pai-management/doc/cluster-bootup.md)

## How to use
- Training  
You can queue a training job, and wait it complete. Also you can request a dedicated resource on-demand, to work with an interactive environment like Jupyter notebook. In both scenarios, you need to submit a job with different configurations
    - [Submit a job in Visual Studio](https://github.com/Microsoft/vs-tools-for-ai/blob/master/docs/pai.md) 
    - [Submit a job in Visual Studio Code](https://github.com/Microsoft/vscode-tools-for-ai/blob/master/docs/quickstart-05-pai.md)
    - [Submit a job in web portal](https://github.com/Microsoft/pai/blob/yanjga/doc/job-tutorial/README.md#job-submission)
    - [Job templates](https://github.com/Microsoft/pai/tree/yanjga/doc/examples)
    - [How to request on-demand resource with job submitting]()
- Cluster administration    
    - [Deployment infrastructure](https://github.com/Microsoft/pai/blob/master/pai-management/doc/cluster-bootup.md)
    - [Cluster maintenance](https://github.com/Microsoft/pai/wiki/Maintenance-(Service-&-Machine))
    - Monitoring
- Share model, data, environments
- TO BE align with When you want to run complete training pipeline in one place 

## Resources
The OpenPAI user [documentations](./docs/documentation.md) provides in-depth instructions for using OpenPAI

## Get Involved
- [StackOverflow:](./stackoverflow.md) If you have questions about OpenPAI, please submit question at stackoverflow under tag: openpai
- [Report an issues:](https://github.com/Microsoft/pai/wiki/Issue-tracking) If you have issues/ bugs/ new features, please submit it at Github 
## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

#### Who should consider contributing to OpenPAI?
- Folks who want to add support for other ML and DL frameworks
- Folks who want to make OpenPAI a richer AI platform (e.g. support for more ML pipelines, hyperparameter tuning)
- Folks who want to write tutorials/blog posts showing how to use OpenPAI to solve AI problems


When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.