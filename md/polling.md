# Poll data from Bonita to BICI

In order to learn from the history of all executed processes in Bonita platform, BICI need to access and poll data from Bonita Database.

The first time BICI is launched, all data regarding case and task execution is retrieved from the Bonita Database. Then, every 15 minutes (default configuration), a job updates the module with data of newly executed tasks and cases.

## Configuration

All these configuration items can be set in the `application.properties` of the BICI.

Bonita Database connection informations
```
bonita.datasource.url=jdbc url
bonita.datasource.username=username
bonita.datasource.password=password
```

If you use Oracle, you need to add your driver `lib` folder of the BICI (or in the `jdbc_driver` folder of the installer).

Polling rate interval, i.e. at each rate the data in BICI will be updated
```
bonita.bici.polling.rate_minute=15
```

The connection pool of this polling can be configured to limit or increase the polling velocity.
It can be useful to decrease it when you want to limit the impact of BICI on Bonita performances.
```
spring.datasource.hikari.maximum-pool-size=20
```

## Manage polling executions

The polling can be handled in BICI Configuration Living Application.

This page allows to:
* activate/deactivate the polling
* run it immediately
* cancel any running polling
* see previous polling executions

## Troubleshooting

### Polling errors

When a polling execution fails, it can be seen in error in BICI Configuration Living Application.

More information is available in the output logs on the BICI, either in the Standard output or in the log file `logs/bonita-ici.log`
