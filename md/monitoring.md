# Operations Management

The Operations Management Living Application contains pages that allow Operations Managers to monitor cases with more information than they could normally get by looking at cases execution.

## Monitoring page

The view is filtered by process and optionally process version.
The artificial intelligence algorithm applies a prediction to each case: its likelihood to finish within the target duration, given two parameters: its execution flow so far and the time remaining before the target duration.

Based on this information, the page shows a pie chart with the proportion of cases *Late* (already behind the deadline), *Predicted late* (likelihood is below 50%), and *On time* (likelihood is 50% or above).

It also contains a tabbed list of cases that identifies each case by its ID as well as the name of the initiator. 
For each case *On time* and *Predicted late*, the likelihood to finish on time and the remaining time are also displayed.
For *Late* cases, the amount of time the case has been late as well as the initial due date are displayed.

A click on a particular case displays its overview: current business data values as well as a timeline that shows all human tasks already done as well as the current task and its assignee.

This helps Operations Managers make the best short-term decision to put operations back on track if needed, and organize the team's activity.
