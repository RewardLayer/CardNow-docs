***

Allows for retrieving a single Order

### ```GET``` v1/orders/{id}

A heart resource that allows for the monitoring and testing of the API

***

Request

```sh
GET https://api-cardnow.com/v1/orders/1234
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
| 200         | [Order](https://docs.cardnow.com/api-reference/models/#order) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Status Returns

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |

***

Retrieve a list of orders

### ```GET``` v1/orders

the list of orders

***

Request

```sh
GET https://api-cardnow.com/v1/orders
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
{  "Orders": [
{
  "InvoiceNumber" : "ABC123455",
  "OrderId" : 123,
  "PartnerOrderId" : "ABCSFFFFGFF",
  "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
  "UpdatedUTC" : "2019-07-26T16:59:57-05:00."
  
},
{
  "InvoiceNumber" : "ABC123455",
  "OrderId" : 123,
  "PartnerOrderId" : "ABCSFFFFGFF",
  "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
  "UpdatedUTC" : "2019-07-26T16:59:57-05:00."
  
}
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
| 200         | Array of [Orders](https://docs.cardnow.com/api-reference/models/#product) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Status Returns

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |

***

Create a new Order

### ```POST``` v1/orders

Creates a single order

***

Request

```sh
POST https://api-cardnow.com/v1/orders
Accept-Encoding: gzip,deflate
correlationid: 7e79f263-57a7-4d59-bd0a-69e03806488f
Host: api.cardnow.com
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.1.1 (java 1.5)
```

***

Responses

=== "200 OK"

    {
      "InvoiceNumber" : "ABC123455",
      "OrderId" : 123,
      "PartnerOrderId" : "ABCSFFFFGFF",
      "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
      "UpdatedUTC" : "2019-07-26T16:59:57-05:00."
      
    }

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
| 200         | [Order](https://docs.cardnow.com/api-reference/models/#order) |              |
| 400         | [Error](https://docs.cardnow.com/api-reference/models/#error) |              |
| 429         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Status Returns

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |