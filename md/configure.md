# Configure _BICI Operations Management_ Living Application

A living application is provided with the BICI Add-on to configure processes and compute prediction models.

## Target duration

The target duration is a mandatory configuration to set. It allows the BICI Add-on to know what is a normal time execution for a given process. With this information, it computes a percentage of chances for the process instance to finish within this time.

In the page, the target duration is configurable in calendar days.

## Success rate threshold

If the success rate percentage of a case is below this success rate threshold, a case will be considered as *Predicted late*.

e.g. if the success rate threshold is 80%, all cases having a success rate percentage below 80% will be displayed as *Predicted late* in the monitoring view.

## Create the model

A button is present to run the computation of the prediction model and apply it to every open case.

The model is then computed using all current history available in the BICI storage. You can at any time compute again the prediction model to take in account newly finished cases.
