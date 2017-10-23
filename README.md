# node-nestpay

A NodeJS module to interface with Nestpay Payment Gateway.

## Installation
```
npm install gulp-grab
```
## Methods
- Purchase
- Authorize
- Capture
- Void
- Refund
## Endpoints
- İş Bankası
- Akbank
- Finansbank
- Denizbank
- Kuveytturk
- Halkbank
- Anadolubank
- ING Bank
- Citibank
- Cardplus
- Ziraat Bankası
## Example
```
var nodeNestpay=require('./index.js');
var config = {
    name: 'ISBANK',
    password: 'ISBANK07',
    clientId: 700100000
}
nestpay = new nodeNestpay(config);
var pay = {
    number: '5456165456165454',
    year: '12',
    month: '12',
    cvv: '000',
    amount: '10',
    currency: 'TRY'
} 
nestpay.authorize(pay).then(function(doc) {
    console.log(doc);
    nestpay.capture({ orderId: doc.OrderId }).then(function(docx) {
        console.log(docx);
        nestpay.void({ orderId: doc.OrderId }).then(function(docy) {
            console.log(docy);
        }).catch(function(docy) {
            console.log(docy);
        });
    }).catch(function(docx) {
        console.log(docx);
    });
}).catch(function(doc) {
    console.log(doc);
});
```