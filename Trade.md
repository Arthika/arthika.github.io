## Orders and Trades

Orders and trades are similar concepts to identify a buy/sell operation that a trader performs in a market.    

An **order** is what a trader (or trading strategy) wants to do.
A **trade** is the result of executing an order in the market (a completed transaction)

An order can be identified by the following parameters:

 * **Security**: 	Security/instrument to be applied in the transaction.
 * **Trading interface**: 	Trading interface where order will be routed through.
 * **Quantity**: 	Number of security items to be bought/sell.
 * **Side**: 	"buy" or "sell".
 * **Type**: 	"market" or "limit". A market order will be sent to the market instantly (instantly executed). A limit order might be executed instantly or could remain as a 'pending order' till some condition would match.
 * **Time-in-force**:	When an order is received by the venue, its execution might take some time. This parameter defines some conditions to control the execution of an order. Tipical time-in-force type are: "day", "good till cancel", "inmediate or cancel" or "fill or kill".
 * **price**: 	Defines the target price desired by the trader in the final transaction.
 * **expiration**: 	With some special time-in-force 'limit' orders, this field defines the maximum time in seconds that order can exist as 'pending'. When expiration time is reached, order is usually self-destroyed.

When an order is executed, the resulting **trade** will have the following parameters:

* **Temporary ID**:	When an order is sent, Arthika's platform will assign a temporary ID till the order will be executed. This temporary ID is tipically a number.
* **Trade ID**:	ID assigned by Arthika's system to identify this trade. This ID is always the same after an order cancelation or modification ('cancelOrder' and 'modifyOrder' web services), so user can always identify uniquely.
* **FIX ID**:	ID assined by the venue to this trade. This ID must be used to do a cancellation or replacement. The result of replacing a trade is another trade with a different 'FIX ID' but the same 'Trade ID'.
* **Account**:	Name of the account where settlement whill be done after order execution.
* **Trading interface**:	Name of the [trading intarface](https://github.com/Arthika/API-REST/wiki/TI) used to route the order.
* **Security**:	Instrument name (EUR/USD, GBP/USD, ...)
* **Pips**:		Number of decimals that defines the "pips" of the price.
* **Quantity**:	Amount of the order (of the security).
* **Side**:		"buy" or "sell".
* **Type**:		"market" or "limit". A market order will be sent to the market instantly (instantly executed). A limit order might be executed instantly or could remain as a 'pending order' till some condition would match.
* **Limit price**:	Limit price assigned to a 'limit' order.
* **Time-in-force**:	When an order is received by the venue, its execution might take some time. This parameter defines some conditions to control the execution of an order. Tipical time-in-force type are: "day", "good till cancel", "inmediate or cancel" or "fill or kill".
* **Finished price**:	Final negotiated price when the order was executed.
* **Finished quantity**:	Final negotiated quantity when an order was executed. The finished quantity can differ from the requested amount in the original order depending on the time-in-force applied.
* **Commission currency**:	Asset to be used to apply the commission ("EUR", "USD", ...)
* **Commission**:	Commission amount to be applied to an executed order (at defined 'commcurrency' asset/currency).
* **Status**:	Status of the order or trade: "invalid", "in flux", "pending", "indetermined", "executed", "canceled", "rejected", "error while sending", "replaced to a new order", "replaced to cancel status" or "cancelled by user".
* **Reason**:	Descriptive message indicating why the order reached defined 'status'.


#### Example

A trader sent the following order:   
    

The resulting trade (extracted from the blotter) was:    
