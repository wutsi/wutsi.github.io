# Payment API
This is a generic API for supporting online payment.
The scope of this API is limitted (for the moment to Mobile payment).
The operation supported by the API:
- Pay: Receive payment from customer
- Transfert: Transfer payment to a customer
- Cancel: Cancel a transaction
- Status: Return the status of a transaction
- Verify: Verify the identify of a customer

## API Operations
## Pay


## Transfer
##### Request
```json
{
   "meta": {
     "orderId": "40490943",
     "description": "This is the description"
   },
   "customer": {
     "name": "Roger Milla",
     "number": "+2379999999"
   },
   "amount":{
     "amount": 130000,
     "currency": "XAF"
   }
}
```

##### Response
```
{
   "transactionId": "4309430943",
   "status": "approved"
}
```

## Cancel

## Status

## Verify

## API Errors
