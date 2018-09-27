# ICI Operations Management API

*version 1.0*

API used by Operations Management Living Application


## `/ici-case-api`
### `GET`
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

## `/ici-process-api`
### `GET`
Get processes
#### Query parameters
No parameters

## `/ici-query-api`
### `GET`
Execute a query
#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, start at 0|
|parameters|object|false|Parameters required by the query|

