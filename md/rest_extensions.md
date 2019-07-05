# BICI Operations Management API

*version 1.0*

API used by Operations Management Living Application

## `/bici-case-api`
#### Http method
`GET`

#### Description
This list of cases can be filtered by status (late, predictedLate, onTime) or using a search term

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, starts at 0|
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process|
|status|string|false|Status of the cases: late, predictedLate, onTime|
|search|string|false|Search keyword, will search in case id and name of the initiator|

## `/bici-process-api`
#### Http method
`GET`

#### Description
Get processes that the user is manager of

#### Query parameters
No parameters

## `/bici-query-api`
#### Http method
`GET`

#### Description
This allows to execute an analytics query.

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, starts at 0|
|queryName|string|true|Name of the analytics query|
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process. If empty, use all allowed versions|
|parameters|object|false|Parameters required by the query|

