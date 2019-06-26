# Pre-requisites

Bonita Intelligent Continuous Improvement prerequisites lists all required environments to operate BICI Add-on.

## Hardware

We recommend to use a dedicated server for BICI, and for the BICI storage. 

### BICI server


Hardware required for BICI server:

| Type | Minimum | Recommended |
|:-|:-|:-|
| Processors | 4 CPU cores | 8 CPU cores or more |
| Memory (RAM) | 4 GB | 12 GB or more, depending on usage|
| Disk space | 10 GB | 10 GB |

   
:::info    
When predictive model is computed, nearly all computing is done in JVM memory. Most of computation is done in memory,
while hard disk is only used for logging.    
:::

### Elastic search

If you deploy elastic on premise, we recommend to follow official [elastic support matrix](https://www.elastic.co/support/matrix)
 and [installation guide](https://www.elastic.co/guide/en/elasticsearch/reference/6.2/setup.html) 

## Software


Software required for BICI Add-on:

| | Version
|:-|-
| **Operating system** |
| Microsoft Windows Server | 2016 64 bits and higher |
| Red Hat Enterprise Linux |  6.5 64 bits and higher |
| Ubuntu | 16.04 LTS 64 bits and higher |
| **Java Virtual Machine** |
| Oracle Java SE Runtime Environment | 8u112 (see note 1) |
| OpenJDK | 8u112 (see note 1) |
| **Bonita platform** | 
| Bonita | 7.5.4 and higher (see note 2, 3 and 4) |
| **Storage** | 
| Elasticsearch | 6.5.3 and higher (unless using the docker version launched by the installer)|
| **Docker** | 
| Docker | 18.03 and higher|
| **Browser** |
| Mozilla Firefox | latest version |
| Google Chrome | latest version |
| Microsoft Edge | latest version |
| Microsoft Internet Explorer | 11 |
| **Mobile** |
| Mozilla Firefox | latest version |
| Google Chrome | latest version |
| Apple Safari | latest version |

Notes:
1. BICI can be executed on Java 8. Java 9 and above are not yet supported. 
2. All Subscription editions are supported.
3. Archive must be activated
4. BICI has its own connection pool to connect to Bonita engine database. Ensure database has available connections 
in addition to Bonita connections

:::info    
When installing BICI, an active Internet connexion is required to download Docker images.    
:::

## Skills

BICI is not a Data Scientist tooling, so no particular skills are required to use the add-on

## Data

Data polled from Bonita engine database use archive table to read BPM history, thus Archive mode be activated.
