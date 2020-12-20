# V1 API Reference

### Overview

### Base URL

## Monitoring
***
### ```GET``` v1/heartbeat
#### Heartbeat Message

A heart resource that allows for the monitoring and testing of the API
***
Request 
```sh
GET https://api-cardnow.com/v1/heartbeat
Accept-Encoding: gzip,deflate
correlationid: 7e79f263-57a7-4d59-bd0a-69e03806488f
Host: api.cardnow.com
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.1.1 (java 1.5)
```
***
=== "Response - 200 OK"


```json
{
  "heartbeat": "ok"
}
```
=== "Response - 500 "

```json
{
  "ErrorCode": "cardnow.error.heartbeat",
  "Message": "The is something wrong with the heartbeat message",
  "MoreInfoUrl": "docs.cardnow.com/api-reference/exchange.invalid.heartbeat",
  "UserMessage": "There was an error when calling the heartbeat message. Please contact support@cardnow.com to address the issue. "
}
```
=== "Response - 503"
```json

```
***
##### Headers

|Name|Type|Description|
|---|---|---|
|correlationid|`guid`|The correlation Id is used to track the API request|
|x-api-key|`guid`|The API key from your developer account used to identify the limits on your account|

***
##### Status Returns
|Http Status|Response Model|Notes|
|---|---|---|
|200|None||
|400|`Error`||
|400| |Rate Limited|
|500| ||
|503| ||

***
##### Status Returns


***
## Catalog

***
## Ordering
***
## Activating
***
## Models
***
### Error Models

####Error
Describes the Error return for a set of 400 or 500 error returns


The error​ model is a set of error code and messages that describe the error that happened in the system.

|Name|	Type|	Notes|
|---|---|---|
|ErrorCode|`string`|	A fixed string error message that can be used|
|Message|	`string`|	A short human readable message|
|MoreInfoURL|	`string`|	A link to the document website that goes into more detail about this error and how to fix it.|
|UserMessage|	`string`|	A longer form human readable message on how to solve the problem or give details about the nature of the error|
***

sample
```json
{
"ErrorCode": "exchange.invalid.productLine",
"Message": "The product line is not recognized",
"MoreInfoUrl": "docs.cardpool.com/reference/exchange.invalid.productLine",
"UserMessage": "There is a misconfiguration of the product line. Please check the id that was sent into the api call to make sure it matches a product line id that was sent from the supportedProductLine API call"
}
```
