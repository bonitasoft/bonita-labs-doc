# Security

## REST APIs

REST APIs are not yet secured. In production only Bonita platform and the plaftorm administrator should be able to access BICI backend by e.g. configuring your network this way.

## Elasticsearch

Elasticsearch access should be restricted to the BICI backend. Alternativly you can use Elasticsearch editions that contains security features [see Elasticsearch documentation](https://www.elastic.co/guide/en/x-pack/current/xpack-security.html).

## REST API extensions

REST API extensions should be secured using Bonita REST API authorization mechanism [see Bonita platform documentation](https://documentation.bonitasoft.com/bonita/7.6/rest-api-authorization).

