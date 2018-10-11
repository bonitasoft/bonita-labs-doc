# Process-mining

Process mining is a set of analysis made on any enterprise data log or events, in order to discover processes and 
compute some statistics or business analytic queries. Applied to Bonita platform, we use BPM event logs stored in 
Bonita engine database to compute a predictive model.


## General

As an introduction, you can see some of our [webinars](https://www.bonitasoft.com/videos?category=Webinars) for
more information about process mining.

## What is used in BICI v1: Predict chances to finish on time

Analysis done in BICI will replay each process instance using its history and compute the remaining time on each state it went through.

Then percentiles of the remaining time for each of these state will be stored in a *prediction model*.

The *prediction model* allows to predict the percentage of chance to be within a target duration.

Then the state of the case is deducted from this percentage and target duration, possible states are _on time_, _late_, or _predicted late_. 

