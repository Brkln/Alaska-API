# Create payment
Endpoint: `/createPayment`

Body:
```json
{
  "additional_info":"here you can put any infos, will be used in the webhook, so you can put the id for example of your customer", *
  "address":"mmFzJnZ5RjVfAFPjbJfnu2djZ2iRrSR3Vg", *
  "webhook_url":"https://brooklyn.is/payment", *
  "minimum_confirmations":4,
  "price":0.003, *
  "satoshi-per-byte":6,
  "testnet":true, 
  "crypto":"bitcoin" *
}
```

Response:
```json
{
  "expire":1645134736212,
  "payment_info":{
    "payment_id":"sMoDboa7MVlOW561miXKtm34xMsS2a6Y",
    "price":0.003,
    "address":"myRdLgqkvvT3MR7sHVGyTNG2kBZanHYViX",
    "send_to":"mmFzJnZ5RjVfAFPjbJfnu2djZ2iRrSR3Vg" 
  }
  "settings":{
    "satoshi-per-byte":6,
    "testnet":true,
    "crypto":"bitcoin",
    "webhook_url":"https://brooklyn.is/payment",
    "minimum_confirmations":4
  }
}
```

Webhook Content:
```json
{
  "payment_id":"sMoDboa7MVlOW561miXKtm34xMsS2a6Y",
  "additional_info":"here you can put any infos, will be used in the webhook, so you can put the id for example of your customer"  
}
```
