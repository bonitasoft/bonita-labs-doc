# Getting started

Bonita Intelligent Continuous Improvement Add-on (BICI Add-on) installation and configuration instructions. 

This chapter covers *Evaluation* and *Production*, two different installation modes.

## Download

Download BICI Add-on from [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

The archive contains:
* An installation guide: `installation-guide.md`
* The BICI application: `bici-application-<version>.zip`
* Two Living Applications: *BICI Case Monitoring* with predictions, and *BICI Configuration*, to configure the first application
* An installer: `bin/bonita-ici` (`bin/bonita-ici.bat` on Windows platform)

## Install

:::info
Check all [pre-requisites](./prerequisites.md) prior to install.
:::

The installer rely on docker to deploy all components of BICI.

1. Ensure you have java installed, using command `java -version`
2. Ensure you have Docker installed, using command `docker --version`
3. Docker requires an active Internet connection to pull the Elasticsearch Docker image and to build the BICI application image
4. Unzip the application  `bici-application-<version>.zip`
5. Run `bin/bonita-ici` (`bin/bonita-ici.bat` on Windows platform)
6. Follow the instructions

For more detailed informations of that, see the [installation guide](installation_guide.md).

## Configure

### Configure Profiles
Once installed, you need to setup the Bonita Portal profile mapping for the profile `Configuration` and make sure Operations Managers are mapped to the provided profile `Process Manager`. 
Moreover, for each process supervised by Operation Managers, the `Process Manager mapping` must also include the Operations Managers in order to display data of the processes in the `Operations Management` Living Application.

### Synchronize data

In the [Configure Living application](configure.md)'s `Polling Status` tab, activate the synchronization to push your data into the BICI storage.

### Configure processes

In the [Configure Living application](configure.md)'s `Configuration` tab, set target durations and create models for your processes. 

## Explore

### Monitor executing cases

Check out the [Operation manager Living application](monitoring.md)'s `Monitoring` tab, it contains live monitoring of executing cases.

### Analyse performance of completed cases

Check out the [Operation manager Living application](monitoring.md)'s `Analytics` tab, it contains analytics of completed cases.

