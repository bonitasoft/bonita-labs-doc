# Getting started

Bonita Intelligent Continuous Improvement (BICI) installation and configuration instructions. 

## Download

Download BICI from the [Bonitasoft Customer Portal](https://customer.bonitasoft.com/).

## Install

Follow the instructions described in the [installation guide](installation_guide.md).

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

