Welcome to Arthika's ACT (Algorithmic Currency Trader) user manual.

### ACT Platform Concepts

Arthika's algorithm currency trading platform (called ACTP) allows any user operate in different trading markets  by using automated trading algorithms (trading strategies).

Before trading in these markets, all users should undertand following main concepts used by the Arthika's trading platform (ACTP):

[1. Prime broker account (PB Account)](https://github.com/Arthika/User-Manual/wiki/1.--Prime-Broker-Account) : Account provided by a licensed brokerage where the trader deposits his funds (used for trading).    
[2. Venue](https://github.com/Arthika/User-Manual/wiki/2.--Venue) : Trading system where orders from traders are matched (executed) and, therefore, traders obtain their profits or their loses.    
[3. Trading interface (TI)](https://github.com/Arthika/User-Manual/wiki/TI) : Communication channel (often called a FIX connection) between the venue and ACTP. Over these channels prices are sent from the venue to ACTP and orders are sent back from ACTP to the venue.    
[4. Strategy (AU or Accounting Unit)](https://github.com/Arthika/User-Manual/wiki/AU) : Algorithm or program developed by a trader which receives prices from ACTP and send orders to the ACPT (ACPT will route these prices and orders between the venues to/from the strategy).    
[5. Equity pool (EP)](https://github.com/Arthika/User-Manual/wiki/EP) : Set of strategies who shares equity and margin in order to operate in different markets.    
### Forex Trading Concepts
[Trading concepts](https://github.com/Arthika/User-Manual/wiki/Trading-Concepts)   
[Assets](https://github.com/Arthika/User-Manual/wiki/Asset)    
[securities](https://github.com/Arthika/User-Manual/wiki/Security)    
[trades](https://github.com/Arthika/User-Manual/wiki/Trade)    
[orders](https://github.com/Arthika/User-Manual/wiki/Trade)    
[positions](https://github.com/Arthika/User-Manual/wiki/Positions)       
    
### Data Model

Once previous trading concepts has been understood, the Arthika's data model is shown the following figure:
    
[[Images/data_model_1.png]]    