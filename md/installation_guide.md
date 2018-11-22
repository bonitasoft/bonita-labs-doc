# Installation guide

Bonita ICI installation guide. It covers evaluation and production modes installation, as well as detailed available parameters values.  
Installation can be done using *evaluation* or *production* modes. Evaluation mode will start two Docker containers and deploy Living Applications. Production mode is an on-premise BICI server deployment.

## Hardware and software requirements

Check all requirements detailed in [Bonitasoft offical documentation](https://documentation.bonitasoft.com)

### Bonita platform
First of all, you need an up and running **Bonita platform 7.5.4 or greater**.  
BICI server will connect directly to Bonita database, in a read-only manner.


## Using the installer

This mode is designed to get a fully functional BICI stack including BICI server, BICI storage and Living Applications 
for configuration and operations management.

### Pre-requisite

Elasticsearch, even in a Docker container, requires a specific configuration of virtual memory. For more information, see [elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html)

```
# configure runtime environnement
sudo sysctl -w vm.max_map_count=262144
```
or edit file `/etc/sysctl.conf` file

### Installation

Run the Add-on using `bonita-ici` (`bonita-ici.bat` on Windows platform) script that is located inside the `bin` folder

This installer will do the following operations:
* `stopApp`: stop and remove any existing BICI back-end running
* `stopStorage`: stop and remove any BICI storage (elasticsearch) docker container
* `startStorage`: deploy an Elasticsearch server in a Docker container
* `startApp`: configure and deploy the BICI server in a Docker container
* `deploy`: deploy the two Living Applications configured to run on top of this installation.

All required parameters are asked in the command line.

### Installation with a manually installed Elasticsearch

If you want to use a your own manually installed elasticsearch, change the following properties from the `configuration.properties` File:
```
elasticsearch.port=<port of the elasticsearch>
elasticsearch.host=<host of the elasticsearch>
```

Then run the installer like this:
```
bonita-ici startApp deploy
```

It will not try to start the bonita-storage (Elasticsearch) docker container and it will use the elasticsearch specified in the `configuration.properties` File.


### SSL configuration

HTTPS is activated by default on the module. 

There are two ways to configure it:

#### Self-signed certificate

If you don't already have a valid certificate for you platform or does not know what it is, choose this option.
A certificate will be generated for you based on some informations asked by the installer.

:::info
This is not recommended for a Production use of BICI. It is recommended to get your own certificate.
:::

#### Provide your own certificate

If you already have a certificate and the associated private key of your domain, it can be given to the installer to be used in the backend to enable the https.

This certiface and the private key must be passed to the installer in a format compatible with the Java KeyStore. 

Common supported formats are JKS and PKCS12.

##### Example using LetsEncrypt's certbot:

Generate a certificate for your local machine using the certbot of Lets encrypt using the following command line
```
certbot certonly
```
(For more information, go to [Let's Encrypt documentation](https://letsencrypt.org/getting-started/))

Convert the certificate given by LetsEncrypt into a PKCS12 format
```
openssl pkcs12 -export -in /etc/letsencrypt/live/{domain}/fullchain.pem -inkey /etc/letsencrypt/live/{domain}/privkey.pem -out mykey.p12 -name myAlias
```

Then when using the installer provide this generated file as a keystore, the same password for the keystore and the key, and the same alias.

### Stop the module 

It can be stopped using `bonita-ici stopStorage stopApp`

:::info
use `./bonita-ici --help` to display all options
:::

### Pass parameters using configuration file

All parameters asked by the installer can be passed using a configuration file.

Example:

```
./bonita-ici --file configuration.properties
```

The sample configuration file named `configuration.properties` contains all properties that can be configured


## Manual installation

The deliverable is composed of one standalone application, two Bonita Living Applications, and an installer that will
help you install the backend and deploy the two Living Applications in your current instance of the Bonita platform.

```
bonita-bici-<VERSION>.zip
    |---- bici-application-<VERSION>.zip           // Standalone application for A.I.
    |---- la-configuration-<VERSION>.zip          // Bonita L.A. for BICI. configuration
    |---- la-operations-management-<VERSION>.zip  // Bonita L.A. for Operations Management
    |---- la.properties                           // properties used by L.A. deployer utility
    |---- installation-guide.md                   // this file
    |---- configuration.properties                // sample configuration file
    |---- bin/bonita-ici                          // an utility that start the dockers and deploy L.A.s
    |---- bin/bonita-ici.bat                      // an utility that start the dockers and deploy L.A.s (Windows)
    |---- jdbc_drivers/                           // the folder where to put the jdbc driver of the Bonita platform database
```


### Elasticsearch

The BICI server requires and Elasticsearch. Supported versions are 6.2.3 or above, in cluster or single node mode. 

For more information, please refer to the [official installation guide](https://www.elastic.co/downloads/elasticsearch)


### BICI server

1. Copy `bici-application-<VERSION>.zip` to the host. 
2. Unzip it in the directory of your choice. 

We will refer to the extracted directory as `BICI_APPLICATION_HOME`.

#### Configuration

Edit `$BICI_APPLICATION_HOME/application.properties` to configure the application.
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

Oracle only: copy Jdbc driver in `$BICI_APPLICATION_HOME/lib` (drivers for PostgreSQL, MySQL and MS SqlServer are already provided).

#### Advanced configuration

Other parameters are available in `$BICI_APPLICATION_HOME/application.properties`.  
We recommend you to read this file and change other parameters if needed.

#### Advanced polling profile mode (Oracle only)

This mode requires that the database user is allowed to create materialized views. To grant this, use 
`GRANT CREATE MATERIALIZED VIEW TO <USER>` using a SYS connection prior to start the application.  

To activate this mode, uncomment this property in `$BICI_APPLICATION_HOME/application.properties`

```
#bonita.ici.polling.profile=advanced
```

### Launch

To launch the application, simply run `$BICI_APPLICATION_HOME/bin/bonita-bici` on Linux 
or `$BICI_APPLICATION_HOME/bin/bonita-bici.bat` on Windows.

This will start a web server on port 8082 by default (if not changed in `$BICI_APPLICATION_HOME/application.properties`)

### Installation of BICI Living Applications

#### Using the deployer

This method is the recommended way. Use the command below, you will be prompted for required parameters

```shell
./bonita-bici deploy
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
