- **Risk management** goes beyond the the usual topics of position sizing, stop loss and leverage. 
- **Trading Psychology** is the reflection of your actions in the markets. It helps you introspect and find answers to why and how you made a profit or a loss in a particular trade or investment. 
- Risk management techniques vary based on how you are positioned in the market (single position, multiple positions, or complete portfolio).
- Risk management can be --- from a single trading position, multiple trading positions or for a portfolio.

- **Topics: Risk Management**
	- Risk & its many forms
	- Position Sizing 
	- Single Position Risk
	- Multiple Position Risk & Hedging
	- Hedging with Options
	- Portfolio attributes and risk estimation
	- Value at Risk
	- Asset Allocation and its impact on risk (and returns)
	- Insights from the portfolio equity curve
- **Topics: Trading Psychology**
	- Anchoring Bias
	- Regency Bias
	- Confirmation Bias
	- Bandwagon Effect
	- Loss Aversion
	- Illusion of Control
	- Hindsight Bias

## Risk
- For a trader with a rupee of profit, there is a loss to another trader for same rupee. For a group of traders consistently making money, there must be another group of traders consistently loosing money. 
- Successful trading is 80% money management and 20% strategy. 
- Money management and associated topics largely involve assessment of risk. 
- Risk in stock market laymen terms is the 'probability of loosing money'. You are exposed to risk when you transact in the markets. 
- Risk can be broken down into -- Systematic Risk & Unsystematic Risk. When you own a stock you are automatically exposed to both these categories of risks. 
- There are multiple reasons why you can loose money -- deteriorating business prospects, declining business margins, management misconduct, competition eating margins, and so on. 
- All these are **risks related to the company.**
- For example, you decided to invest Rs. 1L in HCL technologies. A few months later company declares its revenues has declined, hence you will loose money on your investment. However, this news will not impact its competitors (TCS, Wipro, Mindtree)'s stock price.
- The risk of losing money due to company specific (internal) reasons is often termed as **Unsystematic Risk**
- Unsystematic risk can be diversified by investing money in different companies (preferably from different sectors).
			![[Pasted image 20241009025939.png]]

- Unsystematic risk drastically reduces when more stocks are added. However, after 20 stocks, the risk is not really diversifiable.
- Systematic risk is common to all stocks in the markers. It arises from common market factors -- macroeconomic landscape, political situation, geographical stability, monetary framework, etc. 
- Few systematic risks that can drag the market down are  -- de-growth in GDP, Interest Rate Tightening, Inflation, Fiscal Deficit, Geopolitical risk.
- Systematic risk is inherent in the system and cannot be diversified. However, it can be 'hedged'. 
- Hedging is a technique that can be used to get rid of systematic risk.
- Hedging and Diversification are two different things. Diversification is used to minimize unsystematic (company's) risk. Hedging is used to minimize systematic (market) risk.
- No market trade / investment should be ever considered safe. 

## Expected Return
- Everyone expects a return on their investment they make. 
- Expecting a realistic return plays a pivotal role in investment management. 
- The expected return of the portfolio can be calculated with the formula -- 
	$$E(R_p) = W_1R_1 + W_2R_2 + .... + W_nR_n$$
	where, 
		$E(R_p)$ - Expected Return of the portfolio
		$W$ - Weight of Investment
		$R$ - Expected Return of Individual Asset

- Expected Return is not a guaranteed return, rather it is a probabilistic expectation of a return on investment.

## Variance
- **Variance** of a **stock returns** is a measure of how much a stock's return varies with respect to its average daily returns. 
- **Portfolio Variance** helps us understand risk at the portfolio level.
- We can calculate the risk of a single stock by calculating its Standard Deviation. 
	    $$Variance, \sigma^2 = \sum \dfrac{(X - \mu)^2}{N}$$
	    where,
		    $\sigma^2$ - Variance
		    $X$ - daily return
		    $\mu$ - Average of Daily Return
		    $N$ - Total number of observations

Example, The daily return of a stock for 5 consecutive days --
- The average return is (0.75 + 1.25 - 0.55 - 0.75 + 0.8) / 5 = 0.3 

| Day | Daily Return | Average | Dispersion From Average | Dispersion Squared        |
| --- | ------------ | ------- | ----------------------- | ------------------------- |
| 1   | 0.75%        | 0.3     | 0.75 - 0.3 = 0.45       | $(0.45\%)^2$ = 0.002025%  |
| 2   | 1.25%        | 0.3     | 1.25 - 0.3 = 0.95       | $(0.95\%)^2$ = 0.009025%  |
| 3   | -0.55%       | 0.3     | -0.55 - 0.3 = -0.85     | $(-0.85\%)^2$ = 0.007225% |
| 4   | -0.75%       | 0.3     | -0.75 - 0.3 = -1.05     | $(-1.05\%)^2$ = 0.011025% |
| 5   | 0.8%         | 0.3     | 0.8 - 0.3 = 0.5         | $(0.50 \%)^2$ = 0.002500% |
Sum of Dispersion Squared = 0.0318 
Variance, $\sigma^2$ = $\dfrac{0.0318}{5}$ = 0.00636%

**The variance gives a sense of how the daily returns are spread out from average expected returns.**
- A large variance indicates that a stock would be quite risky.
- A smaller variance indicates lesser risk. 
- The variance in above example, can be considered high, since we are just looking at 5 days of data. 
- The volatility of the stock (standard deviation) during last five days is given by $\sqrt{\sigma^2}$  =  ~ 0.8%

## Covariance & Correlation
**Covariance** indicates how two (or more) variables move together. 
- Positive Covariance - two variables moves together
- Negative Covariance - two variables moves in opposite direction

Covariance in context of stock markets measure how the prices of two stocks (or more) move together. 
Covariance and Correlation may sound same, but are two different things. 

$$Covariance = \sum \dfrac{(R_{t1} - Avg. R_{t1}) \times (R_{t2} - Avg. R_{t2})}{n-1}$$
where,
	$R_{t1}$ - Daily return of Stock 1
	$Avg. R_{t2}$ - Average Return of Stock 1 over n period
	n - total number of days

Example, Two Stocks, Cipla Ltd. & Idea Cellular Ltd. 
Basic Idea: Both are two large corporations in completely different sectors.

Calculating Covariance: 
1. Calculate daily returns for both the stocks. (Today's price / Yesterday's price - 1) 
2. Calculate the average of daily returns
3. Subtract the daily return by its average
4. Multiply the series calculated in previous step. 
5. Sum up the calculations in step 4
6. Divide the sum by count  - 1. Count is total data points in step 4.

We should only look at whether the two stocks share a positive or negative covariance. The difference does not matter. Since, Covariance is only used to check if two stock move in same or opposite direction. 

Covariance does not tell us the degree to which two stocks move. The degree or magnitude is captured by **Correlation**.

$$Correlation = \dfrac{Cov(x, y)}{\sigma_{x} \times \sigma_{y}}$$

where, 
$Cov(x, y)$ - Covariance b/w two stocks
$\sigma_x$ - standard deviation of stock x
$\sigma_y$ - standard deviation of stock y

The covariance between Idea and Cipla is 0.106, which indicates that the two stocks are not tightly correlated. 

The portfolio managers strive to select stocks which share a negative covariance. They want stocks in portfolio which can hold up, i.e., if one goes down they want the other to hold up. This reduces the overall risk.
# Cointegration
Correlated instruments tend to move in a similar way but, over time, the price ratio (spread) between two instruments might diverge considerably. 
[Cointegrated instruments](https://en.wikipedia.org/wiki/Cointegration) on the other hand don't necessarily move in the same direction: the spread between them can on some days increase but the prices usually find themselves being "pulled back together" to the mean, which provides optimal conditions for pairs arbitrage trading. 

The two workhorses of finding the cointegration are Engle-Granger test and, Johansen Test. 
We'll go with the former since its augmented version is implemented in [`statsmodels`](https://www.statsmodels.org/). The idea of Engle-Granger test is simple. We perform a linear regression between the two asset prices and check if the residual is stationary using the [Augmented Dick-Fuller (ADF) test](https://en.wikipedia.org/wiki/Augmented_Dickey%E2%80%93Fuller_test). If the residual is stationary, then the two asset prices are cointegrated.
## Variance & Covariance Matrix
- Variance is the deviation of stock's return with its own average return.
- Covariance is the variance of the stock's return with respect to another stock's return.
- An equity portfolio typically contains multiple stocks. In order to estimate the variance, covariance, and correlation of a multi-stock portfolio we need matrix algebra.
- 'Variance-Covariance' Matrix does not convey much information, so we need to develop Correlation Matrix on top of it, which is then used to calculate Portfolio Variance.
- Portfolio Variance tells us the amount of risk one is exposed to when he or she holds a set of stocks in the portfolio. 

