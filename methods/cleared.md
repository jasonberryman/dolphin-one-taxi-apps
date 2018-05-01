# Method: cleared
## Table of Contents
* [Overview](#overview)
* [HTTP request](#http-request)
* [Path parameters](#path-parameters)
* [Query parameters](#query-parameters)
* [Request body](#request-body)
* [Response header](response-header)
* [Response body](response-body)

## Overview
This indicates to the dispatch system that a call has ended.

In a multi-tenancy dispatch system, a reference to the taxi company (your customer) can be made via the `hostname` or a `companyId` specified as a path / query parameter or in the request body.

## HTTP request
`POST https://{domain}/telephony/cleared`

or

`POST https://{hostname}/{companyId}/telephony/cleared`

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
  "queueId": string,
  "queueType": string,
  "agentId": string,
  "callId": string,
  "callUrl": string,
  "recordingUrl": string,
  "times": {
    "received": string,
    "totalWait": string,
    "connected": string,
    "duration": string,
    "cleared": string
  }
}
```

### Fields

| fields | description | example |
| :---: | --- | :---: |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |
| phoneNumber | **string**<br><br>The e.164 formatted telephone number of the caller. | +441234567890 |
| queueId | **string**<br><br>The ID of the queue.  This can be used to identify multiple sites / brands within a company | main@exampletaxis.com or executive@london.exampletaxis.com |
| queueType | **string**<br><br>Is this a driver or a customer queue.  This can be used to determine whether to show a booking screen or driver record.  If the driver calls and currently has a *Passenger on Board*, then this could show the booking.<br><br>Possible values:<br><br>`customer` or `driver` | customer |
| agentId | **string**<br><br>The unique ID of the agent who answered the call | john.smith@exampla.com |
| callId | **string**<br><br>The unique ID for the call<br><br>Optional. | 1VeYj4B1udKz7vldrNmJ |
| callUrl | **string**<br><br>The URL for the call detail record |   |
| recordingUrl | **string**<br><br>The URL to listen to the recording |  |
| times.{} | **object**<br><br>An object containing the times for this call. |  |
| times.received | **string**<br><br>The time that the call was received, in [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format. | 2018-04-30T15:32:46.243+01:00 |
| times.totalWait | **string**<br><br>The time that the call was queueing, in [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format. | PT10S |
| times.connected | **string**<br><br>The time that the call was connected, in [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format. | 2018-04-30T15:32:56.457+01:00 |
| times.duration | **string**<br><br>The duration of the call, in [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format. | PT4M23S |
| times.cleared | **string**<br><br>The time that the call was cleared, in [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) format. | 2018-04-30T15:37:19.243+01:00 |

## Response header
if successful, the API should return a `200 OK`.

## Response body
If successful, the API can return an optional [bookingSnapshot](../resources/bookingsnapshot.md) to allow greater reporting within the Calll reports.
