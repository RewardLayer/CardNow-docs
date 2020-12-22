***

Allows for retrieving the list of Products

### ```GET``` v1/catalog

A heart resource that allows for the monitoring and testing of the API

***

Request

```sh
GET https://api-cardnow.com/v1/catalog
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
    {  "Catalog": [
    {
    "PackagingType": "Box",
    "Brand": "Amazon",
    "SKU": "AmazonKIT"
    },
    {
    "PackagingType": "Box",
    "Brand": "Best Buy",
    "SKU": "BestBuyKIT"
    }
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
| 200         | Array of [Products](https://docs.cardnow.com/api-reference/models/#product) |              |
| 400         | `Error`                                                      |              |
| 400         |                                                              | Rate Limited |
| 500         |                                                              |              |
| 503         |                                                              |              |

***

##### Status Returns

| Https Status | Error                        | Message                                     |
| ------------ | ---------------------------- | ------------------------------------------- |
| 400          | `exchange.invalid.x-api-key` | The x-api-key HTTP header value is invalid. |
| 500          | `cardnow.error.heartbeat`    | There was a problem with the heartbeat      |