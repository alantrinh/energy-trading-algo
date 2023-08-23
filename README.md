# Energy Trading Algorithm

* Electricity grids are operated with a certain frequency. This frequency is sustained when supply and demand of electricity are exactly matched. With oversupply the frequency rises, with demand exceeding supply it drops. As long as the frequency is kept in a tolerable range the grid is stable, otherwise it is endangered of power failures. To keep the balance between supply and demand in that tolerable range wholesale electricity markets are structured in a multi-market setting for trading bundles of electricity.  
* The day-ahead market seeks to arrange most of the short-term supply and demand the day prior to delivery times due to technical considerations and risk mitigation. Day-ahead markets usually consist of sealed-bid pay-as-cleared auctions where market participants submit price-volume bids to buy or sell electricity for the 24 hours of the next operating day. Meaning that every auction participant submits a bid of how much energy to buy or sell at a certain price without knowing the other bids. Within pay-as-cleared a uniform price for both buyers and sellers is determined by the market clearing price based on the so-called merit-order-model. All sell orders below this clearing price and all buy orders above this clearing price will be accepted and priced at the clearance price.  
* To cope with the increasing volatility and uncertainty in power production that come with rising shares of renewable energies in the electricity grid, grid-scale energy storage systems can provide additional flexibility. Because of their high efficiency and their ability to store or deliver power almost instantaneously battery energy storage systems are an optimal fit for the short-term nature of the electricity markets.  
* In the Great Britain market, you can also trade without an asset such as a power plant, renewables or in our case batteries. Therefore, we differentiate between physical trades – backed by an asset – and solely financial trades on the markets without actually providing or receiving energy. For this task we will focus on financial trades to neglect all the technical complexities that come with asset-backed trading.

# Task

* Develop a little trading algorithm that maximizes profits from financial trades between two day- ahead auctions in Great Britain. The two auctions:
    * function as mentioned with sealed bids and based on the pay-as-cleared mechanism.
    * market hourly bundles of electricity, so auction participants submit bids to buy or sell electricity for every
hour of the next operating day.
    * are sequential, meaning that you first must submit your bids for the first auction, wait for its results and
afterwards submit your bids for the second auction (a bid consists of a volume you want to buy or sell and
the price you want to pay or receive).
* For the first auction we provide you with a price forecast. Depending on your strategy, it can make a lot of sense to
also produce a price forecast for the second auction. You can use the input variables that we provide you with to create your own forecast. You can also choose a different approach or use any data you can find that would be available at the respective time of your forecast.
* As you act as a non-physical trader, your net position resulting from the trades on the two auctions should be zero for all timesteps, as you cannot provide this net position to the grid on the next day. The difference between your net market position after both auctions and the energy you can provide (which is zero as you trade without an asset) will be settled with the so-called system prices.
    * With a net deficit you must pay the system price to buy the difference in energy back.
    * For a net surplus of energy, the system price is paid to you for the difference in energy.
    * So, it’s also possible to earn money with system prices from either providing less energy than planned to
the system (if system prices are negative) or from taking demand out of the market (if system prices are
positive).
    * At the time of the auctions, you do not know exactly what the system price will be, you only have a forecast
of its price range available to you.
    * You can assume that every trade results in 5 GBP/MWh of costs for taxes and fees which you must account for in
your strategy.
  
* For every timestep you compare the planned to the actual profits of your strategy and include error metrics for the forecasting.
    * Display which profits/losses came from the auctions and which from system prices. Other kpis showing how your strategy performed, can also add value.
* Please follow the convention of negative values for energy translating to buying and vice versa positive values translating to selling of energy to the market.
* You can assume that your bids would not have changed the auction prices. Of course, you must account for the cases where you did not get accepted if your sell bid is above or the buy bid is below the clearing price.
* Minimum price and volume increments:
    * Price tick: 0.1GBP/MWh
    * Volume tick: 0.1MW
* Use the data until the end of February 2022 for training and the rest for testing
