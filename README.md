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
* As far as possible no component should require root rights.
* The UI provided in the web interface should be simple and focus on the core purpose of the framework.

# Basic components

The following components are provided:
* **metric collector**: Collects hetrics on the compute nodes, performs preprocessing and acumulation, and injects the data into the **metric transport** component. Can be triggered by a cron job or run as a daemon.
* **metric transport**: A infrastructure that allows to collect and distribute metric data within a cluster.
* **metric store**: A persistent storage for timeseries metric data that is optimised for fast writing of raw node metric data. Can convert the timeseries data into a format optimised for a job specific data presentation.
* **job archive**: A json schema together with directory layout specification to archive job data to disk.
* **control**: Offers central monitoring and configuration for the **metric transport** agents. Archives jobs once they are finished. Performs continous query operations on metric data.
* **web backend**: A data provider for the web frontend.
* **web frontend**: The web user interface. May be served by **web backend**.

![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98929802-00d07a80-24dc-11eb-8fda-f6d6f22bac70.png)
