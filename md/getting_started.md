# Getting started

Bonita Intelligent Continuous Improvement installation and configuration instruction. 

This chapter cover *Evaluation* and *Production* installation.

## Download

Download ICI from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

The archive contains:
* The installation guide: `installation-guide.md`
* The ICI application: `ici-application-<version>.zip`
* The Living applications
* An installer: `bin/bonita-ici`

## Installation

Installation can be done in a *Evaluation* or *Production* mode. 

:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

* *Evaluation mode* mode is designed to try out the ICI module on an existing Bonita platform.
* *Production* mode should be used when using ICI module for production.

### Evaluation mode

1. Ensure you have java installed, using command `java -version`
2. Ensure you have Docker installed, using command `docker --version`
3. Docker requires an active internet connection to pull Elasticsearch docker image and to build ICI application image
4. Follow installation guide Quick start instructions from the archive.

### Production mode

1. Ensure you have java installed, using command `java -version`
2. Follow installation guide ICI standalone application instructions.

## Configuration

Main configuration is done by the installer. 

Once installed, you need to setup in Bonita portal profile mapping for 
profiles `Configuration` and `Operations Manager`.

`Process Manager mapping` must also be configured for each process in order to display them in Operation Management 
living application.
