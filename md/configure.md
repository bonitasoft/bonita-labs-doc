# Configure Operations Management Living Application

A living application is provided with the ICI module to configure processes and compute prediction models.

## Target duration

The target duration is a mandatory configuration to set. It allows ICI module to know what is a normal time execution for a given process. With this information compute a percentage of chances for the process to finish within this time.

In the page the target duration is configurable in days.

## Success rate threshold

If the success rate percentage of a case is below this success rate threshold, a case will be considered *predicted late*.

e.g. if the success rate threshold is 80%, all cases having a success rate percentage below 80% will be displayed as predicted late the monitoring view.

## Create the model

A button is present to run the computation of the prediction model for a particular case.

The model is then computed using all current history is present in the ICI storage. You can at any time compute again the prediction model to take in account newly finished cases.