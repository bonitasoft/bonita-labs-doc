# Getting started

Bonita Intelligent Continuous Improvement Add-on (ICI Add-on) installation and configuration instructions. 

This chapter covers *Evaluation* and *Production*, two different installation modes.

## Download

Download ICI Add-on from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

The archive contains:
* An installation guide: `installation-guide.md`
* The ICI application: `ici-application-<version>.zip`
* Two Living Applications: Case Monitoring with predictions, and Configuration of the first application
* An installer: `bin/bonita-ici`

## Installation

Installation can be done in a *Evaluation* or *Production* mode. The major difference between those modes is that in the evaluation mode, Elasticsearch and ICI servers are provided in a Docker container, with basic settings.  
This evaluation mode is very easy to install, to get immediate value from the ICI add-on.  

However, to ensure the best performance of a system using Elasticsearch, advanced settings are needed. This means that the ICI Add-on installed in *Evaluation* mode may not handle a large volume of data efficiently.   

So, for production, we recommand to switch to a clusterized and configured Elasticsearch instance, and install ICI on *Production* mode.
 
:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

### Evaluation mode

1. Ensure you have java installed, using command `java -version`
2. Ensure you have Docker installed, using command `docker --version`
3. Docker requires an active Internet connection to pull the Elasticsearch Docker image and to build the ICI application image
4. Follow the installation guide "evaluation mode" instructions from the archive.

### Production mode

1. Ensure you have Java installed, using the command `java -version`
2. Follow the installation guide "production mode" instructions.

## Configuration

Most of the configuration is done by the installer. 

Once installed, you need to setup the Bonita Portal profile mapping for profiles `Configuration` and `Process Manager`.

`Process Manager mapping` must also be configured for each process in order to display them in the `Operations Management` 
living application.
