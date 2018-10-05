# BICI Operations Management API

*version 1.0*

API used by Operations Management Living Application

## `/bici-case-api`
#### Http method
`GET`

#### Description
Get list of running cases

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, start at 0|
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process|
|status|string|false|Status of the cases: late, predictedLate. onTime|
|search|string|false|Search keyword, will search in case id and name of the initiator|

## `/bici-process-api`
#### Http method
`GET`

#### Description
Get processes

#### Query parameters
No parameters

## `/bici-query-api`
#### Http method
`GET`

#### Description
Execute a query

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, start at 0|
|queryName|string|false|Name of the analytic query |
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process. If empy, use all allowed versions|
|parameters|object|false|Parameters required by the query|

