# Introduction

ClusterCockpit is a monitoring platform that is tailormade for job-specific performance monitoring in HPC cluster environments.
This repository has the purpose to provide a platform for discussions about the architecture and interfaces of the ClusterCockpit HPC monitoring framework.

Up to now ClusterCockpit was a pilot implemententation of a web frontend for job-specific performance monitoring. It is implemented in PHP building on the [Symfony web framework](https://symfony.com/) and supports [InfluxDB](https://www.influxdata.com/products/influxdb/) as a timeseries metric store. Job meta data and user data have to be inserted in a SQL database by other means, e.g. using a cron job script.

The usage of ClusterCockpit by us and the feedback we got from external users lead to a number of insights and experiences we want to take into account for our first production implementation:

* The Symfony web framework is a great piece of software and provides solutions
 for everything you may need in a web application. It has a large community and
 the documentation is much better than what I saw in other packages (it is
 still not great, but that is probably not the fault of Symfony). The code
 quality and software design is awesome as far as I can judge. While similar
 opinionated MVC web frameworks are available in most other scripting languages
 (Ruby, Python, Perl, and others) I gave PHP a shot, as it seemed a common
 choice in this application area. But what, in the case of opinionated web
 frameworks, can be seen as an advantage may turn out as a disadvantage. You
 may end up with a solution that is way more complicated then necessary. One
 example is the required MySQL server you need to setup beforehand. Another
 common issue with PHP, and what I know this is similar with all other
 scripting languages, is that the package manager and update process is
 complex, fragile and requires constant maintenance by the developer. Even
 worse this complexity is exposed to the user of your software, and it is
 very likely that many issue tickets are related to problems with the
 package manager, software environment, and broken dependencies between
 external packages. Is there an alternative? Especially for web based
 applications Golang offers (builtin) support for web applications. It is
 a compiled language with self contained binaries, which means that the
 complexity of software dependencies through package managers and the
 shared library nightmare as in C/C++ does not apply. Updating boils down
 to throw in a new binary for your OS and CPU architecture. Also you do
 not need a separate web server in production use, getting rid of another show stopper for
 an average user. There is a reason that a lot of new applications are
 implemented in Golang nowadays.
* Any required external server creates complexity and prevents people from
 using your software. This applies to the web server mentioned above, but
 also to database and caching servers (MySQL, InfluxDB, and Redis). Every
 server is a universe on its own and requires effort to setup and maintain
 it. Especially for smaller Open Source projects it is not feasible to
 integrate those external server dependencies and provide an all included
 support.
* A distributed HPC cluster is an inherently complex environment for
system software. On one hand you want to provide an easy installation and
setup process, so that users can try your software. On the other hand you
need to integrate in a complex and volatile environment, where every
computing center has its specific issues and requirements. Also you must
proof to admins that your software does not influence or endanger the
operation of the cluster. This is especially true for components that run
on the compute nodes, as ,e.g., the metric collector. Ideally you provide
an integrated solution for vanilla Linux HPC Clusters that is plug and
play to install, setup, and use. But you also need to provide modular
components with documented standardized interfaces that also can be
integrated standalone in complex HPC environments of larger computing
centers.
*  Initially the plan was to provide a full-fledged UI with options to configure
 the monitoring framework via the web interface. As it turned out
 a conventional graphical user interface is not the best option for all
 use-cases. Especially lists are entered much more efficiently in a text format.
 For our targeted user audience we can safely assume that people know how to use a text editor.
 As a consequence the UI should focus on the core purpose of the framework to allow to search, filter, and show job performance monitoring data.


# Basic requirements

This leads to the following high-level requirements:
* The overall monitoring framework shall be decomposed in components.
* Every components is a self-contained binary.
* Components are connected via stable, standardized interfaces that allow to integrate each component standalone.
* The overall framework should be plug and play to deploy, setup, and use.
* No external servers are required to use the overall framework.
* The UI provided in the web interface should be simple and focus on the core purpose of the framework.

# Basic components


![ClusterCockpit components](https://user-images.githubusercontent.com/11572749/98777167-8d057380-23f0-11eb-9568-1f4e83002dab.png)
