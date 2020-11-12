# Introduction

ClusterCockpit is a monitoring platform that is tailormade for job-specific performance monitoring in HPC cluster environments.
This repository has the purpose to provide a platform for discussions about the architecture and interfaces of the ClusterCockpit HPC monitoring framework.

[In the Wiki](https://github.com/ClusterCockpit/cc-architecture/wiki/Learning-from-experience) you find the experiences with the current implementation that inspired below requirements and structure.

# High-level requirements

This leads to the following high-level requirements:
* The overall monitoring framework shall be decomposed in components.
* Every components is a self-contained binary.
* Components are connected via stable, standardized interfaces that allow to integrate each component standalone.
* The overall framework should be plug and play to deploy, setup, and use.
* No external servers are required to use the overall framework.
* The UI provided in the web interface should be simple and focus on the core purpose of the framework.

# Basic components


![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98777167-8d057380-23f0-11eb-9568-1f4e83002dab.png)
