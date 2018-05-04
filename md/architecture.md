# Architecture

Bonita Intelligent Continuous Improvement use data Bonita engine database and store them in an Elasticsearch storage
engine. A set of [REST API](./rest_api.md) allow to query this storage. Those API are used in two Living Application
deployed on Bonita platform to configure processes and render predictions.   

## Overview

ICI connects to Bonita engine database, using it owns connection pool to read events from archives. 
Events are stored in elastic search

When configuring processes using Configuration Living Application, a REST API extension calls ICI REST API to store configuration.

Data is polled from Bonita on a configurable interval. Once configured, a prediction model is build, 
based on completed cases and then applied on open cases 
  
Operation Management Living Application is a mobile first UI which displays predictions.   
