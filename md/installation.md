# Download, Install, and Configure ICI add-on

Bonita Intelligent Continuous Improvement installation and configuration instruction. 

This chapter cover *Quick start* and *Production* installation.

## Download

Download ICI from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).
The archive contains:
* The installation guide: `installation-guide.md`
* The ICI application: `ici-application-<version>.zip`
* The Living applications
* An installer: `bin/bonita-ici`

## Installation

Installation can be done in a *Quick start* or *Production* mode. 
 
* *Quick start* mode is designed to try out the ICI module on an existing bonita application.
* *Production* mode should be used when using ICI module for production.

## Pre-requisites

* A bonita platform
* Java
* Docker (for *Quick start*)

:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

If Bonita engine database vendor is oracle, get JDBC driver jar from Oracle (not included in distribution).

### Quick start mode

1. Ensure you have java installed, using command `java -version`
2. Ensure you have java installed, using command `docker --version`
3. Docker requires an active internet connection to pull Elasticsearch docker image and to build ICI application image
4. Follow installation guide Quick start instructions from the archive.

### Production mode

1. Ensure you have java installed, using command `java -version`
2. Follow installation guide ICI standalone application instructions.

## Configuration

Main configuration is done by the installer. 

Once installed, you need to setup in Bonita portal profile mapping for 
profiles `Configuration` and `Operations Manager`.
 


