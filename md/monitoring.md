# Monitor cases

The Operation managment living application contains pages to monitor cases given their time prediction.

## The UI

The view is filtered by process and optionally its version.
It is composed by a pie chart that shows the ratio between cases late, predicted late and on time.
It also has a list of cases that display the success rate percentage and the time remaining before the target duration.
You can click on a particular case to display its overview.

## How to create your own UI

The ICI module provide a set of [REST APIs](./rest_api.md) to list processes and cases along their predictions. Thanks to these, you can create your own UI in any front end technology you want. If you want to create Bonita custom pages and add it in your own living application, it is recommanded to create Bonita REST API extensions that calls the ICI module REST APIs.
