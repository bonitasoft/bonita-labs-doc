# Download, Install, and Configure ICI add-on

Bonita Intelligent Continuous Improvement installation and configuration instruction. this chapter cover quick start mode
which is a docker container deployment and manual installation, including provided Living application setup.

## Download

Download ICI from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/). The downloaded file is a zip file containing
a detailed `installation-guide.md`, the ICI application, two living application and an installer.

## Installation

Installation can be done in a *Quick start* or *Production* mode. 
 
* Quick start mode will launch two docker container
* Production mode is an on premise ICI installation and requires to have and elastic platform up and running.

:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

To ensure you have java installed, using command `java -version`

If Bonita engine database vendor is oracle, get JDBC driver jar from Oracle (not included in distribution).

### Quick start mode

1. Ensure you have java installed, using command `docker --version`
1. Docker requires an active internet connection to pull elastic search docker image
1. Follow installation guide Quick start instructions.

### Production mode

1. Follow installation guide ICI standalone application instructions.

## Configuration

Main configuration is done by the installer. 

Once installed, you need to setup in Bonita portal profile mapping for 
profiles `Configuration` and `Operations Manager`.
 


