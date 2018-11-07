# Release notes

## New features in BICI v1.1.0 
* For the Operations Managers, new _Analytics_ page added to their Living Application:
    - Statistical indicators on case durations by case
    - Number of cases open per month and case status (Late or On time) at the time they were archived
    - Dispersion of case durations 10% by 10%
* For the developer, new _Polling_ page to manage data polling from Bonita database to BICI storage
* New REST API extensions available for the developer to get the results of the algorithm (percentage of chances to finish on time) and use it in existing business applications.
* Security:
    - https mechanism added
    - JWT mechanism with of auto-generated token if needed
    - Input validation implemented to protect against malicious JavaScript
* Translation in French and Spanish
* Health check page for the platform administration, making sure the back-end is up and running

## Improvements
* Graphical rework of the Monitoring page: data got more readable, desktop display got more efficient
* New _Search_ field on case ID (even partial) and case initiator
* Case overview page shows the current tasks and their assignees
* Better access right management of process versions and cases
* The installation procedure does not start the scheduled polling automatically
* Full support of IE11
* Better error management on both Living Applications


## Limitations and known issues

* The process mining algorithm does not yet take into account your business data. It will be relevant only on processes which their duration are correlated to the path that is taken in the process.
* No security mechanism implemented in the BICI backend. It is up to you to secure the access to the BICI backend REST APIs.

## Bug fixes

### Fixes in Bonita Intelligent Continuous Improvement 1.1.0
ICI-1045 On configuration page, unable to update "Confidence threshold" if "Target duration" is empty
ICI-923	Process version are not filtered regarding access right
ICI-922	Process version should be listed from bonita and not from elastic
ICI-921	[doc] architecture image is a bit too wide. Scrolling is needed which is not that great
ICI-920	Cases with 50% chances are in the On-time tab but are orange. They should be green.
ICI-898	[EDGE] error pop up has a big icon
ICI-856	Navigation in Omar's LA looses current tab when returning back from overview
