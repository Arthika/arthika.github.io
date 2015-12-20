## General Information:  

* Order/trading services allow a trading strategy to send buy or sell orders, modify (replace) or cancel them or check the status of any order.
* Any order can be accepted (before generating a 'trade') or refused by many reasons (not enough margin, invalid trading interface or security, ...) After an order is accepted, it will remain in a 'pending order' state, till it will be executed.
* Once an order is accepted, it can be modified or cancelled by the trading strategy.
* The result of executing an order is a 'trade'. Any trade object has much more properties than the original order sent by the strategy.
* A startegy can try to execute several order on a single request to improve lantecy.
 
## Examples  

*  Sending a 100,000 EUR-USD 'Buy' order of type market, using a given trading interface (TI):  

```javascript
$ curl -i --data '{"setOrder":{"user":"demo","token":"927814C103AAF349D435659059BCCEAD9A91C8E9","order":[{"security":"EUR_USD","tinterface":"Baxter_CNX","quantity":100000,"side":"buy","type":"market"}]}}' http://demo.arthikatrading.com:81/fcgi-bin/IHFTRestAPI/setOrder --header 'Content-Type: application/json'

HTTP/1.1 200 OK
Date: Thu, 02 Jul 2015 00:00:00 GMT
Server: Apache/2.4.7 (Ubuntu)
Transfer-Encoding: chunked
Content-Type: application/json;charset=iso-8859-1

{ "setOrderResponse": { 
   "order": [ 
      { "security": "EUR_USD", 
        "tinterface": "Baxter_CNX", 
        "quantity": 100000, 
        "side": "buy", 
        "type": "market",
        "timeinforce": "fill or kill", 
        "tempid": 233, 
        "result": "order requested" } ], 
   "timestamp": "1445961592.763712" } 
}
```

*  Sending a 100,000 EUR-USD 'Sell' order of type market, using a given trading interface (TI):

```javascript
$ curl -i --data '{"setOrder":{"user":"demo","token":"927814C103AAF349D435659059BCCEAD9A91C8E9","order":[{"security":"EUR_USD","tinterface":"Baxter_CNX","quantity":100000,"side":"sell","type":"market"}]}}' http://demo.arthikatrading.com:81/fcgi-bin/IHFTRestAPI/setOrder --header 'Content-Type: application/json'

HTTP/1.1 200 OK
Date: Thu, 02 Jul 2015 00:00:00 GMT
Server: Apache/2.4.7 (Ubuntu)
Transfer-Encoding: chunked
Content-Type: application/json;charset=iso-8859-1

{ "setOrderResponse": { 
   "order": [ 
      { "security": "EUR_USD", 
        "tinterface": "Baxter_CNX", 
        "quantity": 100000, 
        "side": "sell", 
        "type": "market", 
        "timeinforce": "fill or kill", 
        "tempid": 234, 
        "result": "order requested" } ], 
   "timestamp": "1445961770.890986" } 
}
```

## setOrder()

###Request: setOrder

* **user**: 		*Required*.	Strategy login assigned by the backend administrator.
* **token**: 		*Required*.	Token obtained during the [authentication procedure](https://github.com/Arthika/API-REST/wiki/Authentication).
* **order**:            *Required*.	List of orders to be created (one or more orders). Each order will have following fields:
    * **security**: 	Required.	Security/instrument to be applied for this order.
    * **tinterface**: 	Optional.	Trading interface where order will be routed through. Default value: 	Trading interface with the best top-of-book price (best price).
    * **quantity**: 	Required.	Number of security items to be bought/sell.
    * **side**: 	Required.	"buy" or "sell".
    * **type**: 	Required.	"market" or "limit".
    * **timeinforce**:	Optional.	"day", "good till cancel", "inmediate or cancel" or "fill or kill". Default value: "fill or kill".
    * **price**: 	Optional.	Can be set only with "limit" orders. Defines the price to be reached before executing the order. If price is not reached, order will remain "pending" till expiration time will be reached. Default value: Trading interface with the top-of-book price (best price).
    * **expiration**: 	Optional.	Can be set only with "limit" orders. Defines the maximum time in seconds that order can exist as 'pending'. When expiration time is reached, order is self-destroyed. Default value: 	Trading interface with the top-of-book price (best price).
    * **param**: 	Optional.	Private parameter defined by the user for custom usage (must be an integer).

### Response: setOrderResponse

  * **result**: 	Error code.
  * **message**: 	String with the result message in case of error.
  * **order**: 		List of created orders with following fields:
      * **security**: 	Security/instrument applied for the order.
      * **tinterface**: 	Trading interface where order will be routed through.
      * **quantity**: 	Number of security items to be bought/sell.
      * **side**: 		"buy" or "sell".
      * **type**: 		"market" or "limit".
      * **timeinforce**:	"day", "good till cancel", "inmediate or cancel" or "fill or kill".
      * **price**: 		Only present on "limit" orders.
	Defines the price to be reached before executing the order.
	If price is not reached, order will remain "pending" till expiration time will be reached.
      * **expiration**: 	Only present on "limit" orders. Defines the maximum time that order can exist as 'pending'. It is defined in seconds. When expiration time is reached, order is self-destructed.
      * **userparam**: 	Private parameter defined by the user for custom usage (an integer).
      * **tempid**: 	Temporary order ID assigned by Arthika system.
      * **result**: 	"order requested" when order was received by Arthika system to be processed, or an error.

## cancelOrder()

###Request: cancelOrder

* **user**: 		*Required*.	Strategy login assigned by the backend administrator.
* **token**: 		*Required*.	Token obtained during the [authentication procedure](https://github.com/Arthika/API-REST/wiki/Authentication).
* **fixid**:            *Required*. 	List of orders to be cancelled (one or more orders). Each order will be defined by the Fix ID field returned by getOrder web service (streaming or polling)

### Response: cancelOrderResponse
  * **result**: 	Error code.
  * **message**: 	String with the result message in case of error.
  * **order**: 		List of cancelled orders with following fields:
      * **fixid**: 		Fix ID identifiying the order to be cancelled.
      * **result**: 		String indicating the result of this operation, that can be an error or "cancel requested" if cancelation is in progress.

## modifyOrder()

###Request: modifyOrder

* **user**: 		*Required*.	Strategy login assigned by the backend administrator.
* **token**: 		*Required*.	Token obtained during the [authentication procedure](https://github.com/Arthika/API-REST/wiki/Authentication).
* **order**:            *Required*. 	List of pending orders to be modified (one or more orders). Each order will have following fields:
      * **fixid**:            *Required*. 	Fix ID field returned by getOrder web service (streaming or polling) after order was launched by 'setOrder' web service.
      * **price**:            *Required*. 	New price to be applied in the order.
      * **quantity**:         *Required*. 	New quantity to be applied in the order.

### Response: modifyOrderResponse

  * **result**: 	Error code.
  * **message**: 	String with the result message in case of error.
  * **order**: 		List of modified orders with following fields:
      * **fixid**: 		Fix ID identifiying the order to be modified.
      * **result**: 		String indicating the result of this operation, that can be an error or "modify requested" if modification is in progress.
