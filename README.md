# Introduction

ClusterCockpit is a monitoring platform that is tailormade for job-specific performance monitoring in HPC cluster environments.
This repository has the purpose to provide a platform for discussions about the architecture and interfaces of the ClusterCockpit HPC monitoring platform.

Up to now ClusterCockpit was a pilot implemententation of a web frontend for job-specific performance monitoring. It is implemented in PHP building on the [Symfony web framework](https://symfony.com/) and supports [InfluxDB](https://www.influxdata.com/products/influxdb/) as a timeseries metric store. Job meta data and user data have to be inserted in a SQL database by other means, e.g. using a cron job script.

The usage of ClusterCockpit by us and the feedback we got from external users lead to a number of insights and experiences we want to take into account for our first production implementation:

* The Symfony web framework is a great piece of software and provides solutions for everything you may need in a web application. It has a large community and the documentation is much better than what I saw in other packages (it is still not great, but that is probably not the fault of Symfony). The code quality and software design is awesome as far as I can judge.  

# Basic components


![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98777167-8d057380-23f0-11eb-9568-1f4e83002dab.png)
