# Release notes

## What's in ICI v1.0.0 

* A mechanism to incrementally retrieve Data from Bonita platform database.
* A process mining algorithm that predict what are the chances that a case will finish in time and how much time it will take.
* A living application that allows to define the target for each of these processes.
* A living application that allows to view cases along with their prediction.

## Limitations and known issues

* The process mining algorithm does not yet take into account your business data. It will be relevant only on processes which their duration are correlated to the path that is taken in the process.
* No security mechanism implemented in the ICI backend. It is up to you to secure the access to the ICI backend REST APIs.

## Bug fixes

### Fixes in Bonita Intelligent Continuous Improvement 1.0.2
ICI-854  As Omar, I don't want to see deleted cases (either automatic or manual delete) in my case list
ICI-901  Installer should not display password in debug mode
ICI-900  Typo in interactive installer 
ICI-899  Start command in evaluation mode should not ask host name from bonita

### Fixes in Bonita Intelligent Continuous Improvement 1.0.1

#### Fixes in Documentation
* ICI-848 Document why deleted cases are displayed in Operations Management Living Application	

#### Fixes in the Add-On
* ICI-826 Some logs are printed when connection to database is not UP	
* ICI-837 Polling status displays "finishing" status before "running"	
* ICI-847 No percentage displayed when case is late since less than 1 hour
* ICI-853 Connection errors to ici storage are not displayed properly in polling status page
* ICI-855 Polling fails when a case is deleted in Bonita database
