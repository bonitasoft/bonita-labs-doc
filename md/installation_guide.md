# Installation guide

Bonita ICI installation guide. It covers evaluation and production modes installation, 
and detailed available parameters values.  

Installation can be done using *evaluation* or *production* modes. Evaluation mode will start two Docker containers 
and deploy Living Applications. Production mode is an on-premise ICI server deployment.

## Hardware and software requirements

Check all requirements detailed in [Bonitasoft offical documentation](https://documentation.bonitasoft.com)

### Bonita platform
First of all, you need an up and running **Bonita platform 7.5.4 or greater**.  
ICI server will connect directly to Bonita database, in a read-only manner.


## Evaluation mode

This mode is designed to get a fully functional ICI stack including ICI server, ICI storage and Living Applications 
for configuration and operations management.

:::warning
Due to the usage of Docker containers for ICI server and storage, this mode is not recommended for a production platform.
:::


### Linux / OSX

Elasticsearch, even in a Docker container, requires a specific configuration of virtual memory. For more information, see [elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html)

```
# configure runtime environnement
sudo sysctl -w vm.max_map_count=262144
```
or edit file `/etc/sysctl.conf` file


### Interactive installer 

Run the Add-on using `bonita-ici` (`bonita-ici.bat` on Windows platform) script that is located inside the `bin` folder

This installer will do the following operations:
 
* prompt for parameters if they are not provided in the command line
* deploy an Elasticsearch server in a Docker container
* configure and deploy the ICI server in a Docker container
* deploy the two Living Applications configured to run on top of this installation.

Example:

```
./bonita-ici -d jdbc:postgresql://192.23.1.25:5432/bonita\
            -u bonita \
            -p bpm \ 
            -b https://192.23.1.24:8080/bonita \
            -U install \
            -P install \
            -H 192.23.1.23
```

Parameters are:

* d: the jdbc url of the bonita datasource to use
* u: the username for the datasource
* p: the username for the datasource
* b: the url of bonita platform
* U: the username to use when deploying LAs on bonita (default 'install')
* P: the password to use when deploying LAs on bonita (default 'install')
* H: the host on which this current host is accessible from bonita (i.e. the external ip),  (default 'localhost')

The ports on which Elasticsearch and ICI standalone application will be deployed can be customized
* i: the port of the deployed ICI application (default '8082') 
* e: the port of the deployed elasticsearch (default '9200')    

:::info
use `./bonita-ici --help` to display all options
:::

It can be stopped using `bonita-ici stop`

## Production mode 
The deliverable is composed of one standalone application, two Bonita Living Applications, and an installer that will
help you install the backend and deploy the two Living Applications in your current instance of the Bonita platform.

```
bonita-ici-<VERSION>.zip
    |---- ici-application-<VERSION>.zip           // Standalone application for A.I.
    |---- la-configuration-<VERSION>.zip          // Bonita L.A. for I.C.I. configuration
    |---- la-operations-management-<VERSION>.zip  // Bonita L.A. for Operations Management
    |---- la.properties                           // properties used by L.A. deployer utility
    |---- installation-guide.md                   // this file
    |---- bin/bonita-ici                          // an utility that start the dockers and deploy L.A.s
    |---- bin/bonita-ici.bat                      // an utility that start the dockers and deploy L.A.s (Windows)
    |---- jdbc_drivers/                           // the folder where to put the jdbc driver of the Bonita platform database
```


### Elasticsearch

The ICI server requires and Elasticsearch. Supported versions are 6.2.3 or above, in cluster or single node mode. 

For more information, please refer to the [official installation guide](https://www.elastic.co/downloads/elasticsearch)


### ICI server

1. Copy `ici-application-<VERSION>.zip` to the host. 
2. Unzip it in the directory of your choice. 

We will refer to the extracted directory as `ICI_APPLICATION_HOME`.

#### Configuration

Edit `$ICI_APPLICATION_HOME/application.properties` to configure the application.
Mandatory parameters are:

In Elasticsearch configuration
```
bonita.elasticsearch.hosts              // http url(s) of the installed Elasticsearch 

# when Elasticsearch endpoints are protected by authentication,
# rest client basic authentication can be enabled by adding properties as follow
#bonita.elasticsearch.username=admin
#bonita.elasticsearch.password=changeme
```

In Bonita database configuration
```
bonita.datasource.url                   // url of Bonita Platform database
bonita.datasource.username              // username used to connect to the Bonita database (can be a read-only user)
bonita.datasource.password              // password associated to the user used to connect to Bonita database
```

Oracle only: copy Jdbc driver in `$ICI_APPLICATION_HOME/lib` (drivers for PostgreSQL, MySQL and MS SqlServer are already provided).

#### Advanced configuration

Other parameters are available in `$ICI_APPLICATION_HOME/application.properties`.  
We recommend you to read this file and change other parameters if needed.

#### Advanced polling profile mode (Oracle only)

This mode requires that the database user is allowed to create materialized views. To grant this, use 
`GRANT CREATE MATERIALIZED VIEW TO <USER>` using a SYS connection prior to start the application.  

To activate this mode, uncomment this property in `$ICI_APPLICATION_HOME/application.properties`

```
#bonita.ici.polling.profile=advanced
```

### Launch

To launch the application, simply run `$ICI_APPLICATION_HOME/bin/bonita-ici` on Linux 
or `$ICI_APPLICATION_HOME/bin/bonita-ici.bat` on Windows.

This will start a web server on port 8082 by default (if not changed in `$ICI_APPLICATION_HOME/application.properties`)

### Installation of ICI Living Applications

#### Using the deployer

This method is the recommended way. Use the command below, you will be prompted for required parameters

```shell
./bonita-ici deploy
```

#### Manually

This method is the not recommended way, but can be used if you want fine control of deployed Living Applications.

#### Living Application "Configuration"

1. Unzip `la-configuration-<VERSION>.zip` :

```
├── api-configuration-<VERSION>.zip
├── application.xml
├── deploy.json
├── page-configuration-<VERSION>.zip
└── profile.xml
```

2. In the extracted folder, unzip the REST API extension named `api-configuration-<VERSION>.zip` 

```
├── api-configuration-<VERSION>
│   ├── com
│   ├── configuration.properties
│   ├── lib
│   └── page.properties
```

3. Edit the file `configuration.properties` to configure `bonita.ici.application.url`

4. Rezip `api-configuration-<VERSION>.zip`

5. Login to Bonita Portal with credentials that belong to the _Administrator_ profile.

    * In Organization > Profiles, install profile `profile.xml` located in `la-configuration-<VERSION>.zip`  
        * To edit the mapping of _Configuration_ profile, click on "More" in the third panel.
        * Add all needed organization entities that will be able to access this Living Application.
    * In Resources, install the REST API extension `api-configuration.zip` located in `la-configuration-<VERSION>.zip`
    * In Resources, install the page `page-configuration.zip` located in `la-configuration-<VERSION>.zip`
    * In Applications, install the Living Application `application.xml` located in `la-configuration-<VERSION>.zip`

#### Living Application "Monitoring"

1. Unzip `la-operations-management-<VERSION>.zip` :

```
├── api-monitoring-<VERSION>.zip
├── application.xml
├── deploy.json
├── page-operations-management-<VERSION>.zip
└── profile.xml
```

2. In the extracted folder, unzip the REST API extension named `api-monitoring-<VERSION>.zip` 

```
├── api-monitoring-<VERSION>
│   ├── com
│   ├── configuration.properties
│   ├── lib
│   └── page.properties
```

3. Edit the file `configuration.properties` to configure `bonita.ici.application.url`

4. Rezip `api-monitoring-<VERSION>.zip`

5. Login to Bonita Portal with credentials that belong to the _Administrator_ profile.

    * In Organization > Profiles, install profile `profile.xml` located in `la-operations-management-<VERSION>.zip`
        * To edit the mapping of _Monitoring_ profile, click on "More" in the third panel.
        * Add all needed organization entities that will be able to access this Living Application.
    * In Resources, install the REST API extension `api-monitoring.zip` located in `la-operations-management-<VERSION>.zip`
    * In Resources, install the page `page-operations-management.zip` located in `la-operations-management-<VERSION>.zip`
    * In Applications, install the Living Application `application.xml` located in `la-operations-management-<VERSION>.zip`
