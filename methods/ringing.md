# Method: ringing
## Table of Contents
* [Overview](#overview)
* [HTTP request](#http-request)
* [Path parameters](#path-parameters)
* [Query parameters](#query-parameters)
* [Request body](#request-body)
* [Response header](response-header)

## Overview
This indicates to the dispatch system that a call is ringing at one or more agent phones.

In a multi-tenancy dispatch system, a reference to the taxi company (your customer) can be made via the `hostname` or a `companyId` specified as a path / query parameter or in the request body.

## HTTP request
`POST https://{domain}/telephony/ringing`

or

`POST https://{hostname}/{companyId}/telephony/ringing`

## Path parameters

| parameter | description | example |
| :---: | --- | :---: |
| hostname | **string**<br><br>The FQDN where we can connect to your API server | api.example.com |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |

## Query parameters

| parameter | description | example |
| :---: | --- | :---: |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |

## Request body

### JSON representation
```json
{
  "companyId": string,
  "phoneNumber": string,
  "queueId: string,
  "queueType": string,
  "agentId": string,
  "callId": string
}
```

### Fields
| fields | description | example |
| :---: | --- | :---: |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |
| phoneNumber | **string**<br><br>The e.164 formatted telephone number of the caller. | +441234567890 |
| queueId | **string**<br><br>The ID of the queue.  This can be used to identify multiple sites / brands within a company | main@exampletaxis.com or executive@london.exampletaxis.com |
| queueType | **string**<br><br>Is this a driver or a customer queue.  This can be used to determine whether to show a booking screen or driver record.  If the driver calls and currently has a *Passenger on Board*, then this could show the booking.<br><br>Possible values:<br><br>`customer` or `driver` | customer |
| callId | **string**<br><br>The unique ID for the call<br><br>Optional. | 1VeYj4B1udKz7vldrNmJ |


## Response header
if successful, the API should return a `200 OK`.  If the call should be handled by a different agent / queue, you can send a `307 Temporary redirect`, along with the redirect details in a `Location` field.

### Example
```http
HTTP/1.1 307 Temporary redirect
Location: john.smith@example.com
```
