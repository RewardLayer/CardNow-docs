***

Allows for retrieving a single activation

### ```GET``` v1/activations/{id}

An activation of a card

***

Request

```sh
GET https://api-cardnow.com/v1/activation/8a6e1b99a51e4d6f8832698423a19b70
Accept-Encoding: gzip,deflate
correlationid: 7e79f263-57a7-4d59-bd0a-69e03806488f
Host: api.cardnow.com
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.1.1 (java 1.5)
```

***

Responses

=== "200 OK"

```json
{
  "InvoiceNumber" : "ABC123455",
  "OrderId" : 123,
  "PartnerOrderId" : "ABCSFFFFGFF",
  "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
  "UpdatedUTC" : "2019-07-26T16:59:57-05:00."
  
}
```

=== "400 "

```json

{
  "ErrorCode": "cardnow.error.catalog",
  "Message": "The is something wrong with the catalog",
  "MoreInfoUrl": "docs.cardnow.com/api-reference/cardnow.invalid.catalog",
  "UserMessage": "There was an error when calling the catalog message. Please contact support@cardnow.com to address the issue. "
}

```

=== "429"

```json

```



=== "503"


```json

```

***

##### Headers

| Name          | Type   | Description                                                  |
| ------------- | ------ | ------------------------------------------------------------ |
| correlationid | `guid` | The correlation Id is used to track the API request          |
| x-api-key     | `guid` | The API key from your developer account used to identify the limits on your account |

***

##### Status Returns

| Http Status | Response Model                                               | Notes        |
| ----------- | ------------------------------------------------------------ | ------------ |
| 200         | [Acrivation](https://docs.cardnow.com/api-reference/models/#activation) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Return Codes

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |

***

Retrieve a list of Activations

### ```GET``` v1/activations

the list of activations

***

Request

```sh
GET https://api-cardnow.com/v1/activations
Accept-Encoding: gzip,deflate
correlationid: 7e79f263-57a7-4d59-bd0a-69e03806488f
Host: api.cardnow.com
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.1.1 (java 1.5)
```

***

Responses

=== "200 OK"

```json
{  "Activations": [
  {
    "ActivationId": "18df3ed5040647c3a2c08a460c3e73a0",
    "CreatedUTC": "2020-04-23T18:25:43.511Z",
    "UpdatedUTC": "2020-04-23T18:25:43.511Z",
    "CustomerId": "921a745a516046749f074b260e340a41",
    "SKU": "FREBZRD",
    "Amount" : "50.00",
    "Status" : "Pending"

  },
  {
    "ActivationId": "18df3ed5040647c3a2c08a460c3e73a0",
    "CreatedUTC": "2020-04-23T18:25:43.511Z",
    "UpdatedUTC": "2020-04-23T18:25:43.511Z",
    "CustomerId": "921a745a516046749f074b260e340a41",
    "SKU": "FREBZRD",
    "Amount" : "50.00",
    "Status" : "Pending"

  } ]
}
```

=== "429"

```json

```



=== "500 "

    ```json
    {
      "ErrorCode": "cardnow.error.catalog",
      "Message": "The is something wrong with the catalog",
      "MoreInfoUrl": "docs.cardnow.com/api-reference/cardnow.invalid.catalog",
      "UserMessage": "There was an error when calling the catalog message. Please contact support@cardnow.com to address the issue. "
    }
    ```

=== "503"




***

##### Headers

| Name          | Type   | Description                                                  |
| ------------- | ------ | ------------------------------------------------------------ |
| correlationid | `guid` | The correlation Id is used to track the API request          |
| x-api-key     | `guid` | The API key from your developer account used to identify the limits on your account |

***

##### Status Returns

| Http Status | Response Model                                               | Notes        |
| ----------- | ------------------------------------------------------------ | ------------ |
| 200         | Array of [Activations](https://docs.cardnow.com/api-reference/models/#activation) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Return Codes

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |

***

Create a new Activation of a card

### ```POST``` v1/activations

Creates a single activation

***

Request

```sh
POST https://api-cardnow.com/v1/activations
Accept-Encoding: gzip,deflate
correlationid: 7e79f263-57a7-4d59-bd0a-69e03806488f
Host: api.cardnow.com
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.1.1 (java 1.5)
```

***

Responses

=== "200 OK"
```json
    {
"ActivationId": "18df3ed5040647c3a2c08a460c3e73a0",
"CreatedUTC": "2020-04-23T18:25:43.511Z",
"UpdatedUTC": "2020-04-23T18:25:43.511Z",
"CustomerId": "921a745a516046749f074b260e340a41",
"SKU": "FREBZRD",
"Amount" : "50.00",
"Status" : "Pending"

}
```
=== "500 "

    ```json
    {
      "ErrorCode": "cardnow.error.catalog",
      "Message": "The is something wrong with the catalog",
      "MoreInfoUrl": "docs.cardnow.com/api-reference/cardnow.invalid.catalog",
      "UserMessage": "There was an error when calling the catalog message. Please contact support@cardnow.com to address the issue. "
    }
    ```

=== "503"


    ```json
    
    ```

***

##### Headers

| Name          | Type   | Description                                                  |
| ------------- | ------ | ------------------------------------------------------------ |
| correlationid | `guid` | The correlation Id is used to track the API request          |
| x-api-key     | `guid` | The API key from your developer account used to identify the limits on your account |

***

##### Status Returns

| Http Status | Response Model                                               | Notes        |
| ----------- | ------------------------------------------------------------ | ------------ |
| 200         | [Activation](https://docs.cardnow.com/api-reference/models/#activation) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Return Codes

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |

