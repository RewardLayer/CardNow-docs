***

## Catalog Models
***
###Product
Describes a Product that can be ordered 

The Product is an individual product that can be ordered as a part of a order. The product is configured for each partner and determines the type of packaging type included as part of the order

|Name|	Type|	Notes|
|---|---|---|
|Packaging Type|`enum`|	A specific type of package that the card will be packaged in The values are ```Box```, ```Starter``` or ```Refill```|
|Brand|	`string`|	The name of the Brand for the card that can be ordered|
|SKU|	`string`|	The SKU that is used to order the product. Based on the Packaging type and brand this will be unique and will determine both the brand and the packaging type|
***

**Sample**

```json
{
"PackagingType": "Box",
"Brand": "Amazon",
"SKU": "AmazonKIT"
}
```

## Ordering Models
***
###Order
Describes an Order

The order are the details of what will or what was sent to an individual customer. 



| Name              | Type          | Notes                                                        |
| ----------------- | ------------- | :----------------------------------------------------------- |
| InvoiceNumber     | `string`      | A invoice number that is used by the customer to track the order. |
| OrderId           | Int           | A unique identifier use by the API to track the order        |
| PartnerOrderId    | string        | An identifer sent by the partner when creating an order      |
| CreatedUTC        | DateTime      | Date/Time that the order is created                          |
| UpdatedUTC        | DateTime      | Date/Time the order was last updated                         |
| Status            | String        | The status of the order                                      |
| FulfillmentStatus | String        | The status of fulfillment                                    |
| OrderTotal        | decimal       | Total cost of the order                                      |
| Discounts         | decimal       | Discounts on the order                                       |
| Customer          | Customer      | Customer Information for the order                           |
| Payment           | Payment       | Payment for the address                                      |
| ShippingAddress   | Address       | Address the Order is shipped                                 |
| BillingAddress    | Address       | Billing Address for the Order                                |
| LineItems         | LineItem[]    | List of line items for the Order                             |
| Fulfillments      | Fulfillment[] | Fulfillment details for the order                            |

**Sample**

```json
{
  "InvoiceNumber" : "ABC123455",
  "OrderId" : 123,
  "PartnerOrderId" : "ABCSFFFFGFF",
  "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
  "UpdatedUTC" : "2019-07-26T16:59:57-05:00.",
  
}
```

###LineItem

###Fulfillment

###Customer

###Address

###Payment

## Activating Models

***
## Error Models
***
###Error
Describes the Error return for a set of 400 or 500 error returns


The error​ model is a set of error code and messages that describe the error that happened in the system.

|Name|	Type|	Notes|
|---|---|---|
|ErrorCode|`string`|	A fixed string error message that can be used|
|Message|	`string`|	A short human readable message|
|MoreInfoURL|	`string`|	A link to the document website that goes into more detail about this error and how to fix it.|
|UserMessage|	`string`|	A longer form human readable message on how to solve the problem or give details about the nature of the error|
***

**Sample**
```json
{
"ErrorCode": "exchange.invalid.productLine",
"Message": "The product line is not recognized",
"MoreInfoUrl": "docs.cardpool.com/reference/exchange.invalid.productLine",
"UserMessage": "There is a misconfiguration of the product line. Please check the id that was sent into the api call to make sure it matches a product line id that was sent from the supportedProductLine API call"
}
```