# Installation guide

This installation guide covers ways to install BICI with the provided installer, as well as detailed available parameters
values.
The installation process allows to deploy BICI resources on Bonita and relies on Docker to deploy BICI components. 


## BICI deliverable content

The deliverable is composed of one standalone application, two Bonita Living Applications, and an installer that will
help you install the backend and deploy the two Living Applications in your current instance of the Bonita platform.

```
bonita-ici-<VERSION>.zip
    |---- bici-application-<VERSION>.zip          // Standalone application for A.I.
    |---- la-configuration-<VERSION>.zip          // Bonita L.A. for BICI. configuration
    |---- la-operations-management-<VERSION>.zip  // Bonita L.A. for Operations Management
    |---- la.properties                           // properties used by L.A. deployer utility
    |---- installation-guide.md                   // this file
    |---- configuration.properties                // sample configuration file
    |---- bin/bonita-ici                          // an utility that start the docker containers and deploy L.A.s
    |---- bin/bonita-ici.bat                      // an utility that start the docker containers and deploy L.A.s (Windows)
    |---- jdbc_drivers/                           // the folder where to put the jdbc driver of the Bonita platform database
```


## General Prerequisites

For a detailed list of supported environment and tools, see the [prerequisites](prerequisites.md).


### Bonita

You need an up and running Bonita Stack, the BICI application will connect directly to Bonita database.


### Elasticsearch

Elasticsearch, even in a Docker container, requires a specific configuration of virtual memory on the machine that will
host it. For more information, see [elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html)

On a Linux host
```
# configure runtime environnement
sudo sysctl -w vm.max_map_count=262144
```
or edit file `/etc/sysctl.conf` file



## Using the installer

Extract the BICI deliverable on the host machine

In the following, we will use `$BICI_INSTALLER_HOME` when noticing the directory where the installer has been extracted
on the host machine.

### Docker

The installer relies on Docker to deploy all BICI components and is intended to be run on the Docker host directly

* Ensure you have Docker installed, using command `docker --version`
* Docker requires an active Internet connection to pull the Elasticsearch Docker image and to build the BICI application image

#### Windows OS

Due to a current limitation of the installer, you must set the `DOCKER_HOST` environment variable to let the installer
access to the Docker daemon

For instance
```
set DOCKER_HOST=tcp://localhost:2375
```


### Bonita Storage access

Jdbc drivers for PostgreSQL, MySQL and MS SqlServer are already provided with the installer.

For Oracle only: copy Jdbc driver in `$BICI_INSTALLER_HOME/jdbc_drivers`.


## Full installation using the installer

This mode is designed to get a fully functional BICI stack including BICI server, BICI storage and Living Applications 
for configuration and operations management.


### Full installation overview

![Full installation using the installer](images/bici_installation_installer_full.svg)


### Installation

Run the Add-on using `bonita-ici` (`bonita-ici.bat` on Windows platform) script that is located inside the `bin` folder

:::info
use `./bonita-ici --help` to display all options
:::

By default, this installer performs the following operations:
* `stopApp`: stop and remove any existing BICI application running (Docker container)
* `stopStorage`: stop and remove any BICI storage (elasticsearch) Docker container
* `startStorage`: start an Elasticsearch Docker container
* `startApp`: configure and deploy the BICI application as a Docker container
* `deploy`: deploy the two Living Applications configured to run on top of this installation.


### BICI Configuration

All required parameters are asked in the command line.


### Pass parameters using configuration file

All parameters asked by the installer can be passed using a configuration file.

Example:

```
./bonita-ici --file configuration.properties
```

The sample configuration file named `configuration.properties` contains all properties that can be configured


### Https configuration

`https` is activated by default on the BICI application. 

There are two ways to configure it

#### Self-signed certificate

If you don't already have a valid certificate for you platform or does not know what it is, choose this option.
A certificate will be generated for you based on configuration settings provided to the installer.

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


#### Update the certificate

When the certificate expires, it can replaced by a new certificate generated by the installer or one that you provide.

Replace it by reinstalling the backend:
* stop the BICI application using `bonita-ici stopApp`
* start the BICI applicaiton and redeploy BICI Living Applications using either the new certificate or newly generated one using `bonita-ici startApp deploy`

If the certificate is autogenerated, the Bonita JVM needs to be restarted.


### Stop the BICI Application

It can be stopped using `bonita-ici stopStorage stopApp`





### Advanced polling profile mode

:::info
This mode is only available when Bonita is using an Oracle Database
:::


This mode requires that the database user is allowed to create materialized views. To grant this, use 
`GRANT CREATE MATERIALIZED VIEW TO <USER>` using a SYS connection prior to start the application.  

TODO entry in the configuration file + cli available???
To activate this mode, uncomment this property in `$BICI_APPLICATION_HOME/application.properties`

```
#bonita.ici.polling.profile=advanced
```






### Installation with a manually installed Elasticsearch


TODO: can provide this using the cli??
several host???


#### Overview


![Full installation using the installer](images/bici_installation_installer_no_elasticsearch.svg.svg)


#### Configuration

Same as 


If you want to use a your own manually installed elasticsearch, change the following properties in the `configuration.properties` file:
```
elasticsearch.port=<port of the elasticsearch>
elasticsearch.host=<host of the elasticsearch>
```

#### Installation

Then run the installer like this:

TODO : pass the file
```
bonita-ici startApp deploy
```

It will not try to start the BICI Storage (Elasticsearch) docker container and it will use the elasticsearch specified in
the `configuration.properties` File.



