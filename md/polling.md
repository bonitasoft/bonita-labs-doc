# Poll data from Bonita platform to ICI Module

In order to learn from the history of all executed processes in Bonita platform, ICI backend need to access and poll data from Bonita platform database.

The first time ICI backend is launched, all data regarding case and task execution is retrieved from the Bonita platform database. Then, every 15 minutes (default configuration), a job updates the module with data of newly executed tasks and cases.

## Configuration

All these configuration can be set in the `application.properties` of the ICI backend.

Bonita platform database connection informations
```
bonita.datasource.url=jdbc url
bonita.datasource.username=username
bonita.datasource.password=password
```

If you use oracle you need to add your driver `lib` folder of the ICI backend ( or in the `jdbc_driver` folder of the  installer if you use it).

Polling rate interval, i.e. at each rate the data in ICI backend will be updated
```
bonita.ici.polling.rate_minute=15
```

The connection pool of this polling can be configured to limit or increase the polling velocity.
It can be useful to decrease it when you want to limit the impact of the ICI modules on Bonita platform's performances.
```
spring.datasource.hikari.maximum-pool-size=20
```

## Manage polling executions

The polling can be handled on a page served directly on the ICI backend, By default it can be accessed on [http://localhost:8082/](http://localhost:8082/)

This page allows to:
* activate/deactivate the polling.
* run it immediately.
* cancel any running polling.
* see previous polling executions.

## Troubleshooting

### Polling errors

When a polling execution fails, it can be seen in error in the polling page [http://localhost:8082/](http://localhost:8082/).

More information would be available in output logs on the backend, either in the Standard output or in the log file `logs/bonita-ici.log`
 
### Deleted cases

When a started case is already polled in ICI storage and then deleted in Bonita platform, this case is still present 
in ICI storage and will still be displayed in Operation Management Living app, but this overview can't be displayed 
anymore since data is deleted from Bonita database .   
