# BICI Operations Management API

*version 2.0*

API used by Operations Management Living Application

## `/bici-case-by-id-api`
#### Http method
`GET`

#### Description
Return the open case related to the provided case id

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|caseId|integer|true|id of the case|

#### Response examples
* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-case-by-id-api?caseId=101
```json
{
    "caseId": 101,
    "startDate": "2019-06-17T15:27:29.044Z",
    "startedBy": {
        "id": 4,
        "username": "walter.bates",
        "firstName": "Walter",
        "lastName": "Bates"
    },
    "process": {
        "definitionId": "8662860246251890111",
        "name": "Vacation",
        "version": "4.0",
        "versionSpecified": true
    },
    "status": "LATE",
    "predictedEndDate": "2019-06-17T15:28:10.220Z",
    "predictedDurationInMillis": 41153,
    "minInMillis": null,
    "maxInMillis": null,
    "withinTargetRatio": 0
}
```

## `/bici-case-api`
#### Http method
`GET`

#### Description
This list of cases can be filtered by status (late, predictedLate, predictedOnTime, unknown) or using a search term

#### Query parameters
|Parameter|Type|Required|Description|
|---------|----|--------|-----------|
|c|integer|false|Number of elements to return|
|p|integer|false|Page to return, starts at 0|
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process|
|status|string|false|Status of the cases: late, predictedLate, predictedOnTime, unknown|
|search|string|false|Search keyword, will search in case id and name of the initiator|

#### Response examples
* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-case-api?processName=Vacation
```json
{
    "cases": [
        {
            "caseId": 101,
            "startDate": "2019-06-17T15:27:29.044Z",
            "startedBy": {
                "id": 4,
                "username": "walter.bates",
                "firstName": "Walter",
                "lastName": "Bates"
            },
            "process": {
                "definitionId": "8662860246251890111",
                "name": "Vacation",
                "version": "4.0",
                "versionSpecified": true
            },
            "status": "LATE",
            "predictedEndDate": "2019-06-17T15:28:10.220Z",
            "predictedDurationInMillis": 41153,
            "minInMillis": null,
            "maxInMillis": null,
            "withinTargetRatio": 0
        }
    ],
    "counts": {
        "predictedLate": 0,
        "late": 1,
        "predictedOnTime": 0,
        "unknown": 0
    },
    "lastPollingDate": "2019-06-25T15:54:40.298Z"
}
```

## `/bici-process-api`
#### Http method
`GET`

#### Description
Get processes that the user is manager of

#### Query parameters
No parameters

#### Response examples
* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-process-api
```json
[
    {
        "name": "Vacation",
        "versions": [
            "4.0"
        ],
        "targetDurationInMillis": 259200000,
        "successRateThreshold": 0.5
    }
]
```

* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-process-api
```json
{
    "code": 404,
    "message": "Unexpected error: no_supervised_process"
}
```

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
|queryName|string|true|Name of the analytics query: case-time-distribution, case-statistics, case-late-per-month, task-statistics|
|processName|string|true|Name of the process|
|processVersion|string|false|Version of the process. If empty, use all allowed versions|
|parameters|object|false|Parameters required by the query: durationOfAnalysis, for case-time-distribution, case-statistics, case-late-per-month, task-statistics; durationInMillis, for case-late-per-month|

#### Response examples
* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-query-api?queryName=case-time-distribution&processName=Vacation&durationOfAnalysis=2m
```json
{
    "percentiles": [
        "10",
        "20",
        "30",
        "40",
        "50",
        "60",
        "70",
        "80",
        "90",
        "100"
    ],
    "durationMillis": [
        0,
        0,
        0,
        0,
        0,
        0,
        0,
        0,
        0,
        0
    ]
}
```

* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-query-api?queryName=case-statistics&processName=Vacation&durationOfAnalysis=2y
```json
{
    "median": 38345,
    "count": 100,
    "min": 34520,
    "max": 50736,
    "avg": 41545,
    "std_deviation": 5584
}
```

* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-query-api?queryName=case-late-per-month&processName=Vacation&durationOfAnalysis=2m&durationInMillis=300
```json
{
    "month": [
        6
    ],
    "year": [
        2019
    ],
    "predictedOnTime": [
        0
    ],
    "late": [
        0
    ]
}
```

* http://localhost:8080/bonita/apps/bici-operations-management/API/extension/bici-query-api?queryName=task-statistics&processName=Vacation&durationOfAnalysis=2y
```json
[
    {
        "taskName": "Merge",
        "type": "gate",
        "averageDuration": 0,
        "count": 100,
        "numberOfCases": 100,
        "loopRatio": 1,
        "percentOccurrences": 100
    },
    {
        "taskName": "Notify employee request approved",
        "type": "auto",
        "averageDuration": 879,
        "count": 100,
        "numberOfCases": 100,
        "loopRatio": 1,
        "percentOccurrences": 100
    },
    {
        "taskName": "Request approved ?",
        "type": "gate",
        "averageDuration": 0,
        "count": 100,
        "numberOfCases": 100,
        "loopRatio": 1,
        "percentOccurrences": 100
    },
    {
        "taskName": "Review request",
        "type": "user",
        "averageDuration": 27682,
        "count": 100,
        "numberOfCases": 100,
        "loopRatio": 1,
        "percentOccurrences": 100
    }
]
```

