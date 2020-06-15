# Payment API
This is a generic API for supporting online payment.
The scope of this API is limitted (for the moment to Mobile payment).
The operation supported by the API:
- [Verify](https://github.com/wutsi/wutsi.github.io/blob/master/design/payment-api/README.md#verify)
- [Transfer](https://github.com/wutsi/wutsi.github.io/blob/master/design/payment-api/README.md#transfer)
- [Transfer Status](https://github.com/wutsi/wutsi.github.io/blob/master/design/payment-api/README.md#transfer-status)

---------------
## Verify
Verify a customer's phone number
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

##### Response Status Code
| Status Code | Error Code | Description |
|-------------|------------|-------------|
| 200         |            | The customer is valid |
| 404         | customer_not_found | Customer not found |


---------------
## Transfer
Sends a request to transfer funds to a given customer.

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
     "transactionId": "1234",
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

##### Response Status Code
| Status Code | Error Code  | Description |
|-------------|-------------|-------------|
| 202         |             | Accepted. The Transaction is been processed |
| 400         | bad_request | |
| 409         | duplicate_transaction | There is already a transaction with that ID |
| 409         | invalid_currency | The currency is not valid |
| 500         |                  | Server error |


---------------
## Transfer Status
Request the status of a transfer

```
GET /v1/payment/transfer/<transaction-id>
```

##### Response Status Code
| Status Code | Error Code  | Description |
|-------------|-------------|-------------|
| 202         |             | Accepted. The Transaction is been processed |
| 404         | transaction_not_found | `transaction-id` is not valid |
| 500         |                       | Server error |

##### Response Status Body
| Name                 | Description |
|----------------------|-------------|
| transactionId        | ID of the transaction |
| carrierTransactionId | Carrier Transaction ID |
| amount.value         | Amount transfered |
| amount.currency      | Amount ISO currency code |
| customer.phone       | Mobile number in international format |
| customer.carrier     | Mobile Phone carrier |
| status               | Status of the transaction: `successful` or `failed` |
| errorCode            | Error code |

##### Transfer Error Codes
- `insufisant_funds`: Not enough fund to complete the transactions.
- `limit_reached`: Limit of transaction reached.
- `customer_not_found`: Invalid mobile number.

---------------
## Misc.
### Mobile Carriers
The carrier supported are:
- `mtn`: MTN Mobile Money
