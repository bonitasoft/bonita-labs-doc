# Release notes

## New values
### Task assignment decision support 

When a case seems stuck or gets pretty late, view all candidates for the pending task and maybe reassign the task to someone else: choose the candidate with the smallest workload or someone you expect to be able to get the case back on track.


### Rich case execution timeline

For every case, learn about durations of all task execution: pending, last assignment, and execution date and time, durations between the states, and average durations for these durations. All such data help understanding the detailed history of tasks execution along the case lifecycle.

### Monitoring 'Unknown' status

In BICI Monitoring page, when a case's prefix has been encountered by less than 100 archived cases, it is not displayed with the 'On time' status anymore, but with the new 'Unknown' status, because the predicted ratio is not robust enough under 100 cases.
For those cases, we cannot predict whether they will finish on time or be late.

### Status bar on case execution details

For each case, the case execution details page gives a full status bar that recalls case start time, deadline, elapsed time and remaining time to deadline, so you get all you need to anticipate and react along the case lifecycle.


## Rest API version changes

The version of the Rest API has been updated from 1.0 to 2.0.
The Rest API '/bici-case-api' does not return the same result for the cases with the status 'onTime'. And in order to keep consistency, the status 'onTime' has been renamed in 'predictedOnTime'.


## Bug fixes

### Fixes in BICI 1.3.1 (2020-02-06)
* [ICI-1403] - Display name for page 'case details' is wrong. It should be "BICI Case Details page"
* [ICI-1380] - Task analytics table headers not aligned on some screen sizes
* [ICI-1399] - The period over which the average duration of tasks has been computed is missing
* [ICI-851] - Nothing explains that the BICI application is not reachable by BICI LA
* [ICI-1425] - Update frontend dependencies
* [ICI-1381] - Architecture picture in the doc: API to REST API ext. arrow should only be one way
### Fixes in BICI 1.3.0 (2019-12-05)
* [ICI-1386] - [LA Configuration] Not possible to configure and create prediction model for more than 10 process
* [ICI-1268] - As Omar when I come back to the monitoring page, I need the same loader than at first display