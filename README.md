# Introduction

ClusterCockpit is a monitoring platform that is tailormade for job-specific performance monitoring in HPC cluster environments.
This repository has the purpose to provide a platform for discussions about the architecture and interfaces of the ClusterCockpit HPC monitoring framework.

[In the Wiki](https://github.com/ClusterCockpit/cc-architecture/wiki/Learning-from-experience) you find the experiences with the current implementation that inspired below requirements and structure.

# Non-functional requirements

This leads to the following non-functional requirements:
* The overall monitoring framework shall be made up of components.
* Every component consists a self-contained binary
* It is preferred to implement tailor-made solutions vs. using external libraries or frameworks if it is feasible and promises a significant performance advantage or overall complexity reduction.
* Components are connected via stable, standardized interfaces that allow to integrate each component standalone.
* The overall framework should be plug and play to deploy, setup, and use.
* No external servers are required to use the overall framework.
* The UI provided in the web interface should be simple and focus on the core purpose of the framework.

# Basic components


![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98929802-00d07a80-24dc-11eb-8fda-f6d6f22bac70.png)
