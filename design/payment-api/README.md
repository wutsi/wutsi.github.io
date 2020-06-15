# Payment API
This is a generic API for supporting online payment.
The scope of this API is limitted (for the moment to Mobile payment).
The operation supported by the API:
- Verify: Verify the identify of a customer
- Transfer: Transfer payment to a customer
- Transfer Status: Return the status of a transaction


## Verify
This command verify the status of a customer, ensure that its phone number is valid.
```
POST /v1/payment/verify
```


##### Request
| Name              | Required | Description |
|-------------------|----------|-------------|
| customer.name     | N        | Full name of the customer |
| customer.phone    | Y        | Mobile number in international format |
| customer.carrier  | Y        | Mobile Phone carrier |

```json
{
   "customer": {
     "name": "Roger Milla",
     "phone": "+2379999999",
     "carrier": "mtn"
   }
}
```

##### Response
| Status Code | Error Code | Description |
|-------------|------------|-------------|
| 200         |            | The customer is valid |
| 404         | customer_not_found | Customer not found |


## Transfer
This is the command for transfering fund to a given customer.

```
POST /v1/payment/transfer
```

##### Request Body
| Name              | Required | Description |
|-------------------|----------|-------------|
| customer.name     | N        | Full name of the customer |
| customer.phone    | Y        | Mobile number in international format |
| customer.carrier  | Y        | Mobile Phone carrier |
| amount.value      | Y        | Amount value |
| amount.currency   | Y        | Amount ISO currency code |
| meta.description  | N        | Description of the transaction |
| meta.transactionId| Y        | Globally unique ID of the transaction. Use GUID for this |


```json
{
   "meta": {
     "invoiceId": "1234",
     "description": "..."
   },
   "customer": {
     "name": "Roger Milla",
     "number": "+2379999999",
     "carrier": "mtn"
   },
   "amount":{
     "value": 130000,
     "currency": "XAF"
   }
}
```

##### Response
| Status Code | Error Code  | Description |
|-------------|-------------|-------------|
| 202         |             | Accepted. The Transaction is been processed |
| 400         | bad_request | |
| 409         | duplicate_transaction | There is already a transaction with that ID |
| 409         | invalid_currency | The currency is not valid |


## Transfer Status
Return the status of a transfer

```
GET /v1/payment/transfer/<transaction-id>
```

##### Response Body
```
{
   "transactionId": "1234",
   "status": "approved"
}
```

## Misc.
### Mobile Carriers
The carrier supported are:
- `mtn`: MTN Mobile Money
