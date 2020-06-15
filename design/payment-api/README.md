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
| customer          | N        | Full name of the customer |
| mobileNumber      | Y        | Mobile number in international format |
| carrier           | Y        | Mobile Phone carrier |


##### Response Status Code
| Status Code | Error Code | Description |
|-------------|------------|-------------|
| 200         |            | The customer is valid |
| 404         | customer_not_found | Customer not found |
| 404         | invalid_carrier    | Carrier not supported |


---------------
## Transfer
Sends a request to transfer funds to a given customer.

```
POST /v1/payment/transfer
```

##### Request
| Name              | Required | Description |
|-------------------|----------|-------------|
| transactionId     | Y        | Globally unique ID of the transaction. Use GUID for this |
| customer          | Y        | Full name of the customer |
| mobileNumber      | Y        | Mobile number in international format |
| carrier           | Y        | Mobile Phone carrier |
| amount            | Y        | Amount to transfer |
| currency          | Y        | ISO currency code |
| description       | N        | Description of the transaction |


##### Response Status Code
| Status Code | Error Code  | Description |
|-------------|-------------|-------------|
| 202         |             | Accepted. The Transaction is been processed |
| 400         | bad_request |   |
| 409         | duplicate_transaction | There is already a transaction with that ID |
| 409         | invalid_currency      | The currency is not valid |
| 409         | invalid_carrier       | Carrier not supported |


---------------
## Transfer Status
Request the status of a transfer

```
POST /v1/payment/transfer/status
```

##### Request
| Name              | Required | Description |
|-------------------|----------|-------------|
| transactionId     | Y        | ID of the transaction |
| carrier           | Y        | Phone carrier |


##### Response Status Code
| Status Code | Error Code  | Description |
|-------------|-------------|-------------|
| 200         |             | Success |
| 404         | transaction_not_found | transactionId is not valid |
| 404         | invalid_carrier       | Carrier not supported |

##### Response Status Body
| Name                 | Description |
|----------------------|-------------|
| transactionId        | Globally unique ID of the transaction. Use GUID for this |
| carrierTransactionId | Carrier reference ID |
| customer             | Full name of the customer |
| mobileNumber         | Mobile number in international format |
| carrier              | Mobile Phone carrier |
| amount               | Amount to transfer |
| currency             | ISO currency code |
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
