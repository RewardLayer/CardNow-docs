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
|MinAmount|	`double`|	The min amount that can be loaded|
|MaxAmount|	`double`|	The max amount that can be loaded|

***

**Sample**

```json
{
"PackagingType": "Box",
"Brand": "Amazon",
"SKU": "AmazonKIT",
  "MinAmount": "5.00",
  "MaxAmount": "100.00"
}
```

## Ordering Models
***
###Order
Describes an Order

The order are the details of what will or what was sent to an individual customer. 



| Name               | Type                                                         | Notes                                                        |
| ------------------ | ------------------------------------------------------------ | :----------------------------------------------------------- |
| OrderId            | Int                                                          | A unique identifier use by the API to track the order        |
| InvoiceNumber      | `string`                                                     | A invoice number that is used by the customer to track the order. |
| PartnerOrderId     | string                                                       | An identifier sent by the partner when creating an order      |
| CreatedUTC         | DateTime                                                     | Date/Time that the order is created                          |
| UpdatedUTC         | DateTime                                                     | Date/Time the order was last updated                         |
| Status             | String                                                       | The status of the order                                      |
| FulfillmentStatus  | String                                                       | The status of fulfillment                                    |
| OrderTotal         | decimal                                                      | Total cost of the order                                      |
| Discounts          | decimal                                                      | Discounts on the order                                       |
| SubTotal           | decimal                                                      | Sub-total before discounts are applied to the order          |
| Customer           | [Customer](https://docs.cardnow.com/api-reference/models/#customer) | Customer Information for the order                           |
| PaymentTransaction | [PaymentTransaction[]](https://docs.cardnow.com/api-reference/models/#payment) | Payment for the Order                                        |
| ShippingAddress    | [Address](https://docs.cardnow.com/api-reference/models/#address) | Address the Order is shipped                                 |
| BillingAddress     | [Address](https://docs.cardnow.com/api-reference/models/#address) | Billing Address for the Order                                |
| LineItems          | [LineItem[]](https://docs.cardnow.com/api-reference/models/#lineitem) | List of line items for the Order                             |
| Fulfillment       | [Fulfillment](https://docs.cardnow.com/api-reference/models/#fulfillment)[] | Fulfillment details for the order                            |
| Refunds            | [Refund](https://docs.cardnow.com/api-reference/models/#refund))[] | Refunds performed on the order                               |

**Sample**

```json
{
  "InvoiceNumber" : "ABC123455",
  "OrderId" : 123,
  "PartnerOrderId" : "ABCSFFFFGFF",
  "CreatedUTC" : "2019-07-26T16:59:57-05:00.",
  "UpdatedUTC" : "2019-07-26T16:59:57-05:00."
  
}
```

###LineItem

The LineItem represents the details of Product that needs to be fulfilled

| Name          | Type     | Notes                                                  |
| ------------- | -------- | :----------------------------------------------------- |
| LineItemId    | int      | The identifier for the line item                       |
| CreatedUTC    | DateTime | Date/Time that the line item is created                |
| UpdatedUTC    | DateTime | Date/Time the line item was last updated               |
| Sku           | String   | The identifier of the product that should be fulfilled |
| Quantity      | int      | Quantity of the product that should be ordered         |
| Price         | decimal  | Price of the Product                                   |
| Discount      | decimal  | Discount applied to the line item                      |
| SubTotal      | decimal  | Sub-total for the line item                            |
| LineItemTotal | decimal  | Total for the line item                                |

**Sample**

```json
{
"lineItemId" : 1233
}
```

###Fulfillment

Details of line items that have been fulfilled

| Name            | Type                                                         | Notes                                       |
| --------------- | ------------------------------------------------------------ | :------------------------------------------ |
| FulfillmentId   | int                                                          | The identifier for the fulfillment          |
| CreatedUTC      | DateTime                                                     | Date/Time that the line item is created     |
| UpdatedUTC      | DateTime                                                     | Date/Time the line item was last updated    |
| LineItems       | [LineItem[]](https://docs.cardnow.com/api-reference/models/#lineitem) | List of line items that have been fulfilled |
| TrackingCompany | string                                                       | Tracking Company used to ship the product   |
| TrackingNumber  | String[]                                                     | Tracking Numbers                            |
| ShipDate        | DateTime                                                     | The Datetime the products shipped           |

###Customer

Information on the customer that the order was placed on behalf

| Name         | Type     | Notes                                   |
| ------------ | -------- | :-------------------------------------- |
| CustomerId   | string      | The identifier for the Customer         |
| CreatedUTC   | DateTime | Date/Time that the customer is created  |
| UpdatedUTC   | DateTime | Date/Time the customer was last updated |
| EmailAddress | string   | Email Address of the customer           |
| PhoneNumber  | string   | Phone number of the customer            |

###Address

Describes an Address

| Name         | Type     | Notes                                  |
| ------------ | -------- | :------------------------------------- |
| AddressId    | int      | The identifier for the Address         |
| CreatedUTC   | DateTime | Date/Time that the address is created  |
| UpdatedUTC   | DateTime | Date/Time the address was last updated |
| FirstName    | String   | First name of the recipient            |
| LastName     | String   | Last name of the recipient             |
| Company Name | string   | Name of the company (Optional)         |
| AddressLine1 | String   | Address line 1                         |
| AddressLin2  | String   | Address line 2(Optional)               |
| City         | String   | City                                   |
| Region       | String   | Region/State                           |
| PostalCode   | String   | Postal Code/Zip Code (Zip plus 4)      |



###PaymentTransaction

Payment for the Order

| Name              | Type   | Notes                                                        |
| ----------------- | ------ | :----------------------------------------------------------- |
| PaymentId         | int    | The identifier for the Payment                               |
| TransactionStatus | string | Status of the Transaction                                    |
| OrderId           | int    | OrderId associated with the Transaction                      |
| Type              | string | Type of transaction: authorization: Money that the customer has agreed to pay. The authorization period can be between 7 and 30 days (depending on your payment service) while a store waits for a payment to be captured.<br/>capture: A transfer of money that was reserved during the authorization<br/>sale: The authorization and capture of a payment performed in one single step.<br/>void: The cancellation of a pending authorization or capture.<br/>refund: The partial or full return of captured money to the customer. |
| Source            | String | Credit Card, Credit, Invoice                                 |
| Status            | string | Status of the payment                                        |

###Refund

Refund on the Order

| Name     | Type       | Notes                         |
| -------- | ---------- | :---------------------------- |
| RefundId | `int`        | The identifier for the Refund |
| Amount   | `decimal`    | Refund Amount                 |
| LineItem | `LineItem[]` | Line Items Affected           |
| Status   | `string`     | Status of the refund          |


## Activation Models
***


###Activation
The Activation allows for activation of a single card. 

Using an App or having the customer enter the card numbers

|Name|	Type|	Notes|
|---|---|---|
|ActivationId|`string`| The id of the activation	|
| CreatedUTC   | `DateTime` | Date/Time that the address is created  |
| UpdatedUTC   | `DateTime` | Date/Time the address was last updated |
|CustomerId|	`string`|	The id of the customer|
|Sku|	`string`|	The SKU of the Product|
|BarCode|	`string`|	The barcode that was scanned  or entered from the customer |
|Amount|	`double`|	The amount to load|
|Status|	`Enum`|	The values are ```Success```, ```Pending``` or ```Failed```|
|FailedUserMessage|	`string`|	The message for a failure|
***

**Sample**

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


***
## Error Models
***
###Error
Describes the Error return for a set of 400 or 500 error returns


The error model is a set of error code and messages that describe the error that happened in the system.

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
