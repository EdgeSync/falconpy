# Quick Scan

![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png) [![Twitter URL](https://img.shields.io/twitter/url?label=Follow%20%40CrowdStrike&style=social&url=https%3A%2F%2Ftwitter.com%2FCrowdStrike)](https://twitter.com/CrowdStrike)

## Using the Quick Scan service collection

![Uber class support](https://img.shields.io/badge/Uber%20class%20support-%E2%9C%93%20Yes-green.svg) ![Uber class support](https://img.shields.io/badge/Service%20class%20support-%E2%9C%93%20Yes-green.svg)

### Table of Contents

| API Function | Description |
| :--- | :--- |
| [GetScansAggregates](quick-scan.md#getscansaggregates) | Get scans aggregations as specified via json in request body. |
| [GetScans](quick-scan.md#getscans) | Check the status of a volume scan. Time required for analysis increases with the number of samples in a volume but usually it should take less than 1 minute |
| [ScanSamples](quick-scan.md#scansamples) | Submit a volume of files for ml scanning. Time required for analysis increases with the number of samples in a volume but usually it should take less than 1 minute |
| [QuerySubmissionsMixin0](quick-scan.md#querysubmissionsmixin0) | Find IDs for submitted scans by providing an FQL filter and paging details. Returns a set of volume IDs that match your criteria. |

### GetScansAggregates

Get scans aggregations as specified via json in request body.

**Content-Type**

* Consumes: _application/json_
* Produces: _application/json_

**Parameters**

| Required | Name | Type | Datatype | Description |
| :---: | :--- | :--- | :--- | :--- |
| ✅ | **body** | body | _string_ |  |

**Usage**

**Service class example**

```python
from falconpy import quick_scan as FalconScan

falcon = FalconScan.Quick_Scan(creds={
     'client_id': falcon_client_id,
     'client_secret': falcon_client_secret
})

BODY = {
    'Body Payload': 'See body description above'
}

response = falcon.GetScansAggregates(body=BODY)
print(response)
```

**Uber class example**

```python
from falconpy import api_complete as FalconSDK

falcon = FalconSDK.APIHarness(creds={
      'client_id': falcon_client_id,
      'client_secret': falcon_client_secret
   }
)

BODY = {
    'Body Payload': 'See body description above'
}

response = falcon.command('GetScansAggregates', body=BODY)
print(response)
falcon.deauthenticate()
```

### GetScans

Check the status of a volume scan. Time required for analysis increases with the number of samples in a volume but usually it should take less than 1 minute

**Content-Type**

* Produces: _application/json_

**Parameters**

| Required | Name | Type | Datatype | Description |
| :---: | :--- | :--- | :--- | :--- |
| ✅ | **ids** | query | array \(_string_\) | ID of a submitted scan |

**Usage**

**Service class example**

```python
from falconpy import quick_scan as FalconScan

falcon = FalconScan.Quick_Scan(creds={
     'client_id': falcon_client_id,
     'client_secret': falcon_client_secret
})

IDS = 'ID1,ID2,ID3'

response = falcon.GetScans(ids=IDS)
print(response)
```

**Uber class example**

```python
from falconpy import api_complete as FalconSDK

falcon = FalconSDK.APIHarness(creds={
      'client_id': falcon_client_id,
      'client_secret': falcon_client_secret
   }
)

IDS = 'ID1,ID2,ID3'

response = falcon.command('GetScans', ids=IDS)
print(response)
falcon.deauthenticate()
```

### ScanSamples

Submit a volume of files for ml scanning. Time required for analysis increases with the number of samples in a volume but usually it should take less than 1 minute

**Content-Type**

* Produces: _application/json_

**Parameters**

| Required | Name | Type | Datatype | Description |
| :---: | :--- | :--- | :--- | :--- |
| ✅ | **body** | body | _string_ | Submit a batch of SHA256s for ml scanning. The samples must have been previously uploaded through `/samples/entities/samples/v3` |

**Usage**

**Service class example**

```python
from falconpy import quick_scan as FalconScan

falcon = FalconScan.Quick_Scan(creds={
     'client_id': falcon_client_id,
     'client_secret': falcon_client_secret
})

BODY = {
    'Body Payload': 'See body description above'
}

response = falcon.ScanSamples(body=BODY)
print(response)
```

**Uber class example**

```python
from falconpy import api_complete as FalconSDK

falcon = FalconSDK.APIHarness(creds={
      'client_id': falcon_client_id,
      'client_secret': falcon_client_secret
   }
)

BODY = {
    'Body Payload': 'See body description above'
}

response = falcon.command('ScanSamples', body=BODY)
print(response)
falcon.deauthenticate()
```

### QuerySubmissionsMixin0

Find IDs for submitted scans by providing an FQL filter and paging details. Returns a set of volume IDs that match your criteria.

**Content-Type**

* Produces: _application/json_

**Parameters**

| Required | Name | Type | Datatype | Description |
| :---: | :--- | :--- | :--- | :--- |
|  | **filter** | query | _string_ | Optional filter and sort criteria in the form of an FQL query. For more information about FQL queries, see [our FQL documentation in Falcon](https://falcon.crowdstrike.com/support/documentation/45/falcon-query-language-feature-guide). |
|  | **offset** | query | _string_ | The offset to start retrieving submissions from. |
|  | **limit** | query | _integer_ | Maximum number of volume IDs to return. Max: 5000. |
|  | **sort** | query | _string_ | Sort order: `asc` or `desc`. |

**Usage**

**Service class example**

```python
from falconpy import quick_scan as FalconScan

falcon = FalconScan.Quick_Scan(creds={
     'client_id': falcon_client_id,
     'client_secret': falcon_client_secret
})

PARAMS = {
    'filter': 'string',
    'offset': 'string',
    'limit': integer,
    'sort': 'string'
}

response = falcon.QuerySubmissionsMixin0(parameters=PARAMS)
print(response)
```

**Uber class example**

```python
from falconpy import api_complete as FalconSDK

falcon = FalconSDK.APIHarness(creds={
      'client_id': falcon_client_id,
      'client_secret': falcon_client_secret
   }
)

PARAMS = {
    'filter': 'string',
    'offset': 'string',
    'limit': integer,
    'sort': 'string'
}

response = falcon.command('QuerySubmissionsMixin0', parameters=PARAMS)
print(response)
falcon.deauthenticate()
```

