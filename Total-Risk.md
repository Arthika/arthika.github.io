## Total risk

The total-risk is the sum of all [open positions](https://github.com/Arthika/API-REST/wiki/Open-Position) which includes a particular asset. Open positions in Forex can be of different types depending on the instruments configured in the [prime-broker account](https://github.com/Arthika/REST-API/wiki/PB-Account):

 * **Cash positions** : When the instruments used in the market are simple cash transfers ([SPOT market](https://github.com/Arthika/REST-API/wiki/Spot)). These positions are also referred as ['asset positions'](https://github.com/Arthika/REST-API/wiki/Spot).
 * **Swap positions** : When the instruments used in the market are swaps ([SINGLE-SWAP market](https://github.com/Arthika/REST-API/wiki/Single-Swap)). These positions are also referred as ['security positions'](https://github.com/Arthika/REST-API/wiki/Single-Swap).

Positions are opened per [prime-broker account](https://github.com/Arthika/REST-API/wiki/PB-Account) and a final aggregated position (at a specific asset) can be obtained by the sum of all open positions from all accounts at same asset.

Total-risk is not usually considered for the denomination currency which, by default, is not a risky asset.
All total-risks (per asset and account and aggregated per asset) can be found in the GUI:

[[Images/gui_au_total_risk.png]]

#### Example

1. Suppose that opened [asset positions](https://github.com/Arthika/REST-API/wiki/Spot) (cash positions) are:
    * 100K EUR at Cantor's account
    * 200K USD at Cantor's account
    * 500K USD at Baxter's account
    * 50K GBP at Baxter's account    

2. Suppose that opened [security positions](https://github.com/Arthika/REST-API/wiki/Single-Swap) (swap positions) are:
    * 500K @ 1.10300 -SELL- EUR/USD at Cantor's account
    * 250K @ 1.52100 -BUY- GBP/USD at Baxter's account    
    
Total-risk for different assets can be calculated on this way:    

**Total-risk** in EUR will be not considered because EUR is the denomination currency.    
**Total-risk** in USD and GBP per account can be obtained:    
 * At Cantor's account = 200K + ( 200K x 1.52100 ) = 200K + 304.2K = 504.2K USD    
 * At Baxter's account = 500K - ( 250K x 1.52100 ) = 500K - 304.2K = 195.8K USD    
 * At Baxter's account = 50K + 250K = 300K GBP    
    
Aggregated **total-risk** for different assets will be:    
 * USD total-risk = 700K USD    
 * GBP total-risk = 300K USD
