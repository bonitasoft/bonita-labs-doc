# Release notes

::: info
**Note:** The 1.3 is currently work in progress (WIP).
:::


# Rest API version changes

The version of the Rest API has been updated from 1.0 to 2.0.
The Rest API '/bici-case-api' does not return the same result for the cases with the status 'onTime'. And in order to keep consistency, the status 'onTime' has been renamed in 'predictedOnTime'.

# New Monitoring 'Unknown' status

In BICI Monitoring page, a case who have a path with less than 100 cases passed doesn't have the 'On time' status anymore, but the new 'Unknown' status, in order to differentiate among the cases that are in time those who have a prediction and those who do not have one.

