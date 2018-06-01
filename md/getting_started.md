# Getting started

Bonita Intelligent Continuous Improvement Add-on installation and configuration instruction. 

This chapter covers *Evaluation* and *Production*, two different installation modes.

## Download

Download ICI Add-on from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

The archive contains:
* An installation guide: `installation-guide.md`
* The ICI application: `ici-application-<version>.zip`
* Two Living Applications: Case Monitoring with predictions, and Configuration of the first application
* An installer: `bin/bonita-ici`

## Installation

Installation can be done in a *Evaluation* or *Production* mode. The major difference between those mode is that 
Elasticsearch and ICI server are provided in Docker container for evaluation mode and don't allow to connect 
to an existing Elasticsearch cluster.

:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

* *Evaluation mode* mode is designed to try out the ICI add-on on an existing Bonita platform.
* *Production* mode should be used when using ICI add-on for production.

### Evaluation mode

1. Ensure you have java installed, using command `java -version`
2. Ensure you have Docker installed, using command `docker --version`
3. Docker requires an active Internet connection to pull Elasticsearch Docker image and to build ICI application image
4. Follow the installation guide "Quick start" instructions from the archive.

### Production mode

1. Ensure you have Java installed, using the command `java -version`
2. Follow the installation guide "ICI standalone application" instructions.

## Configuration

Most of the configuration is done by the installer. 

Once installed, you need to setup in Bonita portal profile mapping for 
profiles `Configuration` and `Operations Manager`.

`Process Manager mapping` must also be configured for each process in order to display them in Operation Management 
living application.
