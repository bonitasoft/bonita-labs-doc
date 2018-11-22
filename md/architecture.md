# Architecture

Bonita Intelligent Continuous Improvement Add-on (BICI) extracts data of the Bonita Engine database, transforms it, and stores documents in an Elasticsearch storage engine. A set of REST APIs allow to query this storage. Those APIs are used in two Living Applications deployed on Bonita Platform to configure processes and render predictions.   

![Bonita Intelligent Continuous Improvement Add-on Architecture](images/bici_architecture.png)

## Overview

BICI connects to the Bonita Engine database, using its own connection pool to read events from the archives. 
Events are stored in Elasticsearch.

When configuring processes using the "Configuration" Living Application, a REST API extension calls the BICI REST API to store the configuration.

Data is polled from Bonita on a configurable time interval.  

Once configured, the developer can configure the relevant processes using [BICI Configuration living application](configure.md) 
and start the creation of the prediction model based on completed cases and then applied on open cases. 

The "Operations Management" Living Application is a mobile first -usable on a desktop- UI which displays predictions.   

## Components

### BICI server
 
The backend server polls data, creates process mining models, and serves protected REST apis.

:::info
BICI Server is secured by https and a security token to only allow requests from Bonita server.
Calls with other origins are rejected with a 403 (Forbidden) response code.
:::

### BICI storage

It stores BICI data and predictive models, and it relies on Elasticsearch engine.

### _BICI Configuration_ Living Application

This Living Application is used to configure the processes and verify that data are up to date in the BICI storage.

### _BICI Operation Management_ Living Application

This Living Application is used to:
* Display case execution information and predictions to the Operation Managers.
* Provide analytics on executed cases.
  
