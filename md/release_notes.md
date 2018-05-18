# Release notes

## What's in ICI v1.0.0 

* A mechanism to incrementally retrieve Data from Bonita platform database.
* A process mining algorithm that predict what are the chances that a case will finish in time and how much time it will take.
* A living application that allows to define the target for each of these processes.
* A living application that allows to view cases along with their prediction.

## Limitations and known issues

* The process mining algorithm does not yet take into account your business data. It will be relevant only on processes which their duration are correlated to the path that is taken in the process.
* No security mechanism implemented in the ICI backend. It is up to you to secure the access to the ICI backend REST APIs.