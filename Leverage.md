## Leverage and Available Margin

Leverage is a platform-parameter associated with a [PB account](https://github.com/Arthika/API-REST/wiki/PB-Account) that determines the maximum total-risk that a trader can reach.    

The maximum leverage parameter is agreed between the trader and the prime broker.    
Leverage allows a trader to open positions with a higher [total-risk](https://github.com/Arthika/API-REST/wiki/Total-Risk) than the equity deposited in the [account](https://github.com/Arthika/API-REST/wiki/PB-Account).    

Leverage can be easily configured at Arthika's Trading Platform backoffice GUI:

[[Images/gui_account_leverage.png]]

#### Example

1. Suppose a defined leverage of 40    
2. Suppose that current cash in the account is 100K EUR    
3. Suppose current EUR_USD market price is 1.13200    
4. Suppose there is a USD cash open position (spot market) of 500K USD    
    
If platform denomination currency is EUR, following calculations can be done:    
    
**Maximum total-risk** that trader can reach in USD = 100K x 1.13200 x 40 = 4,528K USD (about 4.5M USD)   
**Available margin** (in USD) =  4,528K - 500K = 4,028K USD    

This means that trader (the trading strategy) can send an order to buy USD with a maximum quantity of 4,028K.
