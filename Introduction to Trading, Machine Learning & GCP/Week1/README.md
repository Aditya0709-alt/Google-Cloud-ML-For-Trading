The way the BigQuery magic function works is you basically enter your query and then it saves the output of the query to a Pandas DataFrame, which we call df. So this here is relatively long complicated query that will give us all of the features we need for our Machine Learning model. Our model will be really simple and that it only has two features as input. The first feature will be the previous day's closing price. Makes sense to me. The second feature, it will be something we call a three-day trend. A three-day trend variable for any given row looks at the previous four days of closing costs. If the closing price on a day is greater than the closing price on the previous day, and we assign a day plus one, otherwise we assign a day minus one. 

If the majority in the past three days consists of positive ones and the three-day trend is set to positive one, otherwise, is at negative one. So we get the data we need by making heavy use of this lag function in SQL. We go into more depth behind this lag function in the BigQuery Machine Learning Lab. For now, let's take this query as is. Let's go ahead and execute it.

The output of our query should be stored in this Pandas DataFrame that we call df. Let's go ahead and use the head command to see the first five rows of the DataFrame.

Next, let's try to get some intuition for this trend underscore three underscored day variable by embedding in the time series above. This series of commands looks at a subset of a full closing price time series from June to July of 2018. So the first plot command contains the closing price as a dotted line. The second plot command shows positive three-day trends as blue dots while the third plot command shows negative three-day trend as red dots. Let's go ahead and execute this cell.

So as expected, when the close values are visually trending downwards, we expect to see a lot of red dots. When the trend is upwards we expect to see more blue dots. In this next cell, we check the size for our dataset.

Next, we go ahead and fit the model on our training data. Since we don't have a lot of data, the training will be pretty fast. This our mix predictions on the testing data, we're going to use this output to gauge how good our model is.

To gauge how good our model is, we'll use two metrics; the Root Mean Squared Error and the variance score. The Root Mean Squared Error attempts to engage on average how far off your prediction is when the truth; the lower the better. The variance score is how correlated your prediction are to the truth; the closer to one the better. Now, getting good values for these metrics doesn't necessarily mean your model is useful. It all depends on the context. In this case, would you be okay with being off by around three points for your closing value prediction? As a sanity check, whenever you build a regression model, I'd like to plot the predictions against the truth like we do in this cell here.


### Data Trends

<img width="1180" alt="Screenshot 2023-09-22 at 3 36 52 PM" src="https://github.com/Aditya0709-alt/ds-algo/assets/77115883/7ced448f-d90b-46e2-8e8a-eda3b231fe40">

### Best Fit Line

<img width="1240" alt="Screenshot 2023-09-22 at 3 36 14 PM" src="https://github.com/Aditya0709-alt/ds-algo/assets/77115883/c61767ee-2212-4bad-aaab-8ece08b2c940">


## Trading Fundamentals

The financial markets have evolved to become faster and more efficient, with trading strategies aiming to exploit fleeting opportunities. This discussion will cover the differences between trading and investing, the main strategy categories in quantitative trading, and their strengths and weaknesses.

1. **Trading vs. Investing**
   - Buy-side firms primarily invest and advise, including asset managers like private equity, mutual funds, and quantitative hedge funds.
   - Sell-side firms, such as banks and broker dealers, sell investments and provide market-making services.

2. **Investment Strategies**
   - Portfolio managers on the buy side make long-term strategic asset allocation decisions and shorter-term tactical decisions.
   - The most common strategy is buying and holding undervalued assets based on fundamental analysis.

3. **Hedge Fund Strategies**
   - Hedge funds employ traders, developers, and researchers to implement quantitative strategies.
   - Their goal is to generate Alpha, a positive return independent of market movements, often achieved by minimizing risks.

4. **Alpha in Portfolio Management**
   - Portfolio manager Alpha comes from long asset holdings exposed to market, sector, and company risk.
   - Hedge fund Alpha comes from risk-mitigating strategies, distinct from market exposure.

5. **Rebalancing**
   - Portfolio managers use fundamental analysis to rebalance portfolios, adjusting asset allocations.
   - Trading firms have shorter time frames and rarely rely on fundamentals; they seek market inefficiencies.

6. **Quantitative Methods**
   - Buy-side quant methods include regression, prediction models, statistical arbitrage, and machine learning.
   - Sell-side quant methods focus on execution strategies, reducing market impact and providing liquidity.

Both buy-side and sell-side firms may employ execution strategies when executing trading orders.

In summary, the financial world distinguishes between trading and investing, with different strategies and goals. While portfolio managers use fundamental analysis and rebalancing for long-term gains, hedge funds and trading firms pursue Alpha by exploiting market inefficiencies with shorter time frames and quantitative methods. Sell-side firms contribute by facilitating large order execution and market making.

### Quant Strategies

Quant strategies are rule-based approaches used to generate orders and manage risk based on historical price data analysis.
They can range from low-frequency to high-frequency trading, with high-frequency strategies requiring sub-millisecond capabilities.

1. **Forecasting Methods**:
   - Quantitative strategies attempt to forecast future asset values or price spreads between assets based on statistically significant factors.
   - Mean reversion strategies rely on the stability of an asset's price or spread relative to another asset, reverting to its long-term mean when too high or low.

2. **Correlation vs. Co-integration**:
   - Correlation measures how two variables move together over time, ranging from -1 (perfect negative correlation) to 1 (perfect positive correlation).
   - Co-integration assesses whether the difference between means of variables remains constant over time and is distinct from correlation.

3. **Momentum and Trend-Following**:
   - Momentum strategies involve buying past winners and selling past losers, opposite to mean reversion strategies.
   - Momentum strategies have outperformed the S&P 500 in recent years, partly due to underreaction and overreaction to market information.

4. **Market Micro-Structure**:
   - Market micro-structure encompasses trading infrastructure, rules, behaviors, and patterns.
   - High-frequency traders exploit infrastructure anomalies and competitor behavior using game theory models.
   - They also aim to detect and profit from large orders broken up and hidden using execution strategies.

5. **Spoofing**:
   - Spoofing involves misleading other traders by submitting non-intentional orders to the market to manipulate prices.
   - Traders may use this tactic to encourage better prices for their trades.

In summary, quantitative trading strategies are rule-based methods that leverage historical price data analysis to generate orders and manage risk. These strategies encompass various approaches, including mean reversion, momentum, and exploiting market micro-structure, such as detecting large hidden orders and spoofing tactics.


