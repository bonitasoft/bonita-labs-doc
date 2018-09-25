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

#### Responses
* default
default response
  * application/json
  string



## `/ici-process-api`
### `GET`
Get processes
#### Query parameters
No parameters

#### Responses
* default
default response
  * application/json
  string
