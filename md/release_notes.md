# Release notes

## New features in BICI v1.2.0 
### Follow process activities in an efficient manner
New "Status" section in BICI case execution details
In BICI case list, when the Operations Manager clicks on a case, the case details page displays a useful timeline with graphical indication of case start, elapsed time, and target duration.
This helps Omar to graphically understand the remaining time before the case becomes late, or the duration of the overdue when the case is late.

### New Analytics reporting: Access to statistics on tasks in a process
The Operations Manager now gets two tabs for Analytics: the existing analytics graphs on cases becomes the _Case indicators_ tab, and a new tab has been added: _Task indicators_. It displays statistical information on task execution, giving for all tasks and gateways in the case: 
    - number of occurrences
    - average execution duration
    - number of cases where the task has been found
    - the _loop ratio_: if greater than one, it means that the event has been executed more than once in the case: the case contains one or several loops. This requires some attention, as loops may decrease efficiency and predictability in case execution.
    
### Efficient data gathering from Bonita to BICI database
Implement a boost mode for polling on PostgreSQL. The goal of boost modes is to optimize the first polling time to reduce the impact on the database during production time
This mode as well as the existing boost mode on Oracle are made available in the installer.

### Miscellaneous
- Security : Document how to input a renewed https certificate in BICI
- Graphical page structure : Make sure "BICI LA" accurately inherit from any CSS theme

## Limitations and known issues
## Bug fixes

### Fixes in BICI 1.2.2 (2019-09-05)
* [ICI-1147] - Apply input validation for all BICI Application API
* [ICI-1215] - Impossible to know how to make the process visible to Omar
* [ICI-1289] - BICI 1.2.1 inconsistent usage of the BICI backend/server term in the BICI status/healthcheck page

### Fixes in BICI 1.2.1 (2019-08-01)
* [ICI-1265] - Improve the configuration file

### Fixes in BICI 1.2.0 (2019-06-13)
* [ICI-1148] Initial polling fails with large database when polling mode is set to advanced
* [ICI-1122] Avoid scrollbar on case list on tablet on monitoring page
* [ICI-1002] Elapsed time is wrong on polling status page
