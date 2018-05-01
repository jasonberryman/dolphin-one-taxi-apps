# Method: invite
## Table of Contents
* [Overview](#overview)
* [HTTP request](#http-request)
* [Path parameters](#path-parameters)
* [Query parameters](#query-parameters)
* [Response body](response-body)

## Overview
When a new call is received, an invite request is sent to the dispatch system to verify if the caller is eligible for any automated services or elevated queue priority.  The dispatch API should return one or more of the following objects:

* Array of addresses which meet the pre-requisites for automated booking
* Array of existing / active bookings
* Queue priority

In a multi-tenancy dispatch system, a reference to the taxi company (your customer) can be made via the `hostname` or a `companyId` specified as a path or query parameter.

## HTTP request
`GET https://{domain}/telephony/invite`

or

`GET https://{hostname}/{companyId}/telephony/invite`

## Path parameters

| parameter | description | example |
| :---: | --- | :---: |
| hostname | **string**<br><br>The FQDN where we can connect to your API server | api.example.com |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |

## Query parameters

| parameter | description | example |
| :---: | --- | :---: |
| companyId | **string**<br><br>Where the domain does not point to a specific company, this can be specified here (name or reference)<br><br>Optional. | ABC Taxis or 1645780 |
| phoneNumber | **string**<br><br>The e.164 formatted telephone number of the caller. | +441234567890 |
| queueId | **string**<br><br>The ID of the queue.  This can be used to identify multiple sites / brands within a company | main@exampletaxis.com or executive@london.exampletaxis.com |
| queueType | **string**<br><br>Is this a driver or a customer queue.  This can be used to determine what time of response to send.<br><br>* customer<br>* driver | customer |
| callId | **string**<br><br>The unique ID for the call<br><br>Optional. | 1VeYj4B1udKz7vldrNmJ |


## Response body
if successful, the response body contains an instance of [inviteSnapshot](../resources/inviteSnapshot.md)