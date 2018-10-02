# Getting started

Bonita Intelligent Continuous Improvement Add-on (BICI Add-on) installation and configuration instructions. 

This chapter covers *Evaluation* and *Production*, two different installation modes.

## Download

Download BICI Add-on from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

The archive contains:
* An installation guide: `installation-guide.md`
* The BICI application: `ici-application-<version>.zip`
* Two Living Applications: *BICI Case Monitoring* with predictions, and *BICI Configuration*, to configure the first application
* An installer: `bin/bonita-bici`

## Installation

Installation can be done in an *Evaluation* or *Production* mode. The major difference between those modes is that in the *Evaluation* mode, Elasticsearch and BICI servers are provided in Docker containers, with basic settings.  
This mode is very easy to install, to get immediate value from the BICI Add-on.  

However, to ensure the best performance of a system using Elasticsearch, advanced settings are needed. This means that the BICI Add-on installed in *Evaluation* mode may not handle a large volume of data efficiently.   

So, for production, we recommand to switch to a clusterized and configured Elasticsearch instance, and install BICI in *Production* mode.
 
:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

### Evaluation mode

1. Ensure you have java installed, using command `java -version`
2. Ensure you have Docker installed, using command `docker --version`
3. Docker requires an active Internet connection to pull the Elasticsearch Docker image and to build the BICI application image
4. Follow the installation guide "evaluation mode" instructions from the archive.

### Production mode

1. Ensure you have Java installed, using the command `java -version`
2. Follow the installation guide "production mode" instructions.

## Configuration

Most of the configuration is done by the installer. 

Once installed, you need to setup the Bonita Portal profile mapping for the profile `Configuration` and make sure Operations Managers are mapped to the provided profile `Process Manager`. 
Moreover, for each process supervised by Operation Managers, the `Process Manager mapping` must also include the Operations Managers in order to display data of the processes in the `Operations Management` Living Application.
