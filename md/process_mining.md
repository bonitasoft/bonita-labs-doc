# Process-mining

Process mining is a set of analysis made on any enterprise data log or events, in order to discover processes and 
compute some statistics or business analytic queries. Applied to Bonita platform, we use BPM event logs stored in 
Bonita engine database to compute a predictive model


## General

As an introduction, you can see some of ours [webinars](https://www.bonitasoft.com/videos?category=Webinars) for
more information about process mining.

## What is used in ICI v1: Predict chances to finish on time

Analysis done in ICI will observe each path used by process instance, and compute the remaining time to completion. In
addition, the current state of the case is used know which task is active at this time. 

The predictive model allows to predict case duration, based on similar completed instances split in percentiles. 
Prediction consist on defining which percentile belong to each open case, and according to process configuration predict
if case is _on time_, _late_, or _predicted late_. 

