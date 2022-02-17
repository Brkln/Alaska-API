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

# Examples

## In your API

```js
const express = require('express');
const app = express();
app.use(express.json();
app.post('/payment', (req, res) => {
  console.log(JSON.parse(req.body.additional_info).username + ' has bought the product, his payment id is ' + req.body.payment_id);
  return res.status(200).send('=)');
});
app.listen(80, () => {
  console.log('listening on port 80');
}); 
```

## And in your app

```js
var url = "https://xxxxxxxxxx.brooklyn.is/createPayment";
var xhr = new XMLHttpRequest();
xhr.open("POST", url);
xhr.setRequestHeader("Content-Type", "application/json");
xhr.onreadystatechange = function () {
   if (xhr.readyState === 4) {
      console.log(xhr.status);
      console.log(xhr.responseText);
   }};
var data = `{
  "additional_info":"{\"username\":\"brooklyn\"}", 
  "address":"mmFzJnZ5RjVfAFPjbJfnu2djZ2iRrSR3Vg", 
  "webhook_url":"https://brooklyn.is/payment", 
  "minimum_confirmations":4,
  "price":0.003, 
  "satoshi-per-byte":6,
  "testnet":true, 
  "crypto":"bitcoin" 
}
`;
xhr.send(data)
```
###### Credit to [Reqbin](https://reqbin.com) for the request code.
