# Introduction

ClusterCockpit is a monitoring platform that is tailormade for job-specific performance monitoring in HPC cluster environments.
This repository has the purpose to provide a platform for discussions about the architecture and interfaces of the ClusterCockpit HPC monitoring platform.

Up to now ClusterCockpit was a pilot implemententation of a web frontend for job-specific performance monitoring. It is implemented in PHP building on the [Symfony web framework](https://symfony.com/) and supports [InfluxDB](https://www.influxdata.com/products/influxdb/) as a timeseries metric store. Job meta data and user informations must be inserted in a SQL database by other means, e.g. using a cron job script.

# Basic components


![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98777167-8d057380-23f0-11eb-9568-1f4e83002dab.png)
