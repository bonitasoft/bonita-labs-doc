# Release notes

::: info
**Note:** The 1.3 is currently work in progress (WIP).
:::


## Rest API version changes

The version of the Rest API has been updated from 1.0 to 2.0.
The Rest API '/bici-case-api' does not return the same result for the cases with the status 'onTime'. And in order to keep consistency, the status 'onTime' has been renamed in 'predictedOnTime'.

## New Monitoring 'Unknown' status

In BICI Monitoring page, when a case's prefix has been encountered by less than 100 archived cases, it is not displayed with the 'On time' status anymore, but with the new 'Unknown' status, because the predicted ratio is not robust enough under 100 cases.
For those cases, we cannot predict whether they will finish on time or be late.

