<h1 style="text-align:center; font-weight: bold">Strategy 1: Buy and Hold, Single Contract</h1>

Equity Market Risk — $`\beta`$

You could buy every stock in the S&P 500 with weighting but costs time and money OR you could buy a futures contract that exposes you to the same assets and therefore gives you $`\beta`$.

<h2 style="font-weight: bold">Strategy 1:</h2>
<h3>Buy and Hold, Single Contract.</h3>

<hr>

Initially focus on S&P 500 as a way to get exposure to — and be rewarded for — equity market risk.

<h3 style="text-align:center; font-weight: bold">Multipliers, Tick Size, and Tick Value</h3>

For example, on the Chicago Mercantile Exchange there are two sizes of S&P 500 Futures:
- e-mini future (ES), with a contract unit of $50, and a minimum price fluctuation of 0.25 index points = $12.50
- e-micro future (MES), with a contract unit of $5, and a minimum price fluctuation of 0.25 index points = $1.25

Contract Unit — the relationship between the price and value of different futures contracts. \
e.g. if we hold an e-mini future, a 45 index point increase in the S&P 500 would result in a profitof $`45 \times \$50 = 2250`$.

This multiplicative nature means contract unit can be referred to as the  ___multiplier___

The notional exposure per contract is equal to its price times its multiplier.

$`\text{Notional Exposure per Contract(\$)} \; = \; \text{Multiplier(\$)} \times \text{Price}`$

OR if converting between currencies

$`\text{Notional Exposure per Contract(Base Currency)} \; = \; \text{Multiplier} \times \text{Price} \times \text{FX rate}`$

Minimum Price Fluctuation — smallest unit the price can be traded/quoted in. Referred to hereon as ___tick size___ 

$`\text{Tick Value} \; = \; \text{Multiplier} \times \text{Tick Size}`$

<h3 style="text-align:center; font-weight: bold">Futures expiries and rolling</h3>

Front Month — contract with the nearest expiry

<hr>

<h3 style="text-align:center; font-weight: bold">Trading Costs</h3>

Commission and Spread are both applicable for futures

Mid Price — center between Bid and Ask (assuming no spread)

$`\text{Spread Cost} \; = \; \text{Price Paid(Received)} - \text{Mid Price}`$

<hr>

Let's say that we currently hold the S&P 500 e-mini December 2023 future. It expires December 15th (3rd friday of the month). If we wish to maintain our position, we must roll into the next expiration (March 2024).

Rolling involves the simultaneous selling and buying a nearer further out contract, respectively. 

In our example we could sell the December contract on December 11th and then buy the March future that same day. We incurred spread costs and commissions for buying and selling each contract. 

Carver mentions a calendar spread but we will ignore that for now.

Profit (loss):
- Costs (commission & spread) on intial trade and any other trade unrelated to rolling
- Costs (commission & spread) on rolling trades
- Profit/Loss from holding contracts between rolls (using mid prices)

<h3 style="text-align:center; font-weight: bold">Back-Adjusting Futures Prices</h3>

Back-adjustment — creating a price series that reflects the profit/loss from constantly holding & rolling a single contract but ignores trading costs.

Back-adjusted price should remain constant over the roll. See Appendix B for a better understanding of the process.

If we were to hold the S&P 500 (at appropriate weighting) our total return would look like this:

$`\text{Total Return} \; = \; \text{Spot Returns} + \text{Dividends}`$

We know for futures that through a no-arbitrage argument, the futures price at any time is equal to the spot price of the index, plus any expected dividends we will get before the future expires, minus any interest we would pay to borrow the money for buying stocks. This is known as __excess return__:

$`\text{Excess Return} \; = \; \text{Total Return} - \text{Interest} = \text{Spot Return} + \text{Dividends} - \text{Interests}`$

This extra component to excess return is also referred to as ___Carry___ (discussed in greater depth in Strategy 10). 

<h3 style="text-align:center; font-weight: bold">Measuring Profits from a Trading Strategy</h3>

Given a series of positions in contracts, $`N_t`$ (where a positive number means we're long, and negative, short) and a series of back-adjusted prices, $`P_t`$, the return in price points for time $`t`$ is: 

$`\text{Return(Price Points)}, R^{points}_t, R_{p,t} \; = \; N_{t-1} \times (P_t - P_{t-1})`$

For this strategy, buy and hold a single contract, our cumulative return equals the change in price over the full period ($`t = 0, t = T`$):

$`\text{Cumulated Return(Price Points)}_{t=0,T} \; = \; (P_T - P_0)`$

The return in currency of the future is:

$`\text{Return(Currency of Future)}, R^{instr}_t, R_{i,t} \; = \; R^{points}_t \times \text{Multiplier}`$

It follows that the return in base currency is:

$`\text{Return(Base Currency)}, R^{base}_t \; = \; R^{instr}_t \times \text{FX rate}`$

Account Curve — cumulative return series

<hr>

<h3 style="text-align:center; font-weight: bold">Backtesting</h3>

Overfitting — choosing a strategy and ignoring other strategies because of an overtrust in the historical performance of some combination of actions (e.g. x cryptocurrency did well and we should only invest in said cryptocurrency and not diversify)

Data mining — a strategy proven in a backtest but lacks any reasonable explanation, and therefore must be reduced to pure luck and should be ignored (unless a reasonable explanation can be determined)

<hr>

<h3 style="text-align:center; font-weight: bold">Capital</h3>

For Strategy One, Carver assumes you hold the entire notional value of a future as cash reserves.

$`\text{Returns(\%)}, \; R^{\%}_t \; = \; \Large{\frac{100 \times R^{base}_t}{Capital_{t-1}}}`$

Note: since it is assumed that you maintain the entire notional value in reserves, the effective investment cost — the starting value in our return — is the capital set aside for this investment. Should less capital be held, as discussed in subsequent strategies, the denominator will decrease (with subsequent gains increasing).

<h3 style="text-align:center; font-weight: bold">Assessing Performance Characteristics</h3>

<h3 style="text-align:center">Annual Returns</h3>

Carver makes the assumption that a business year is comprised of 256 days so it follows that an Annualized Daily Return (Annualized Return) for any unit is equal to 256 times the average of daily returns:

$`\text{Annualized Return} \; = \; 256 \times \overline{\text{Daily Returns}}`$

<h3 style="text-align:center">Risk and Standard Deviation</h3>

Carver takes the symmetric view of risk — treating all returns as equally risky, whether they positive or negative — as opposed to the asymmetric view of risk — concerned only for negative returns. He justifies this decision with:

1. If we include all available returns, our risk statistic is far more robust and less vulnerable to outliers
2. When using daily returns, it is very likely that there will be many positive and negative returns
3. Futures allow us to be both long and short, asymmetric risk leads to different values of risk depending on being short or long a position.

Carver's preferred measure of risk is the standard deviation of returns. We could use max drawdowns — max cumulative loss experienced during backtest — and the Calmar Ratio in addition. 

$`\text{Calmar Ratio} \; = \Large{\frac{\text{Average Annual Return}}{\text{Maximum Drawdown}}}`$

The drawbacks to this measurement is that:
- There is only one max drawdown per backtest therefore we are incredibly reliant on a single data point
- It is dependent on data set length
- It provides a false sense of security that the most we could lose is X dollars

$`\text{Mean Return(returns} \;  r_1 \; ... \; r_T), \; r^* = \LARGE{\frac{r_t}{T} \;  + \frac{r_{t-1}}{T} \; + \; ... \; + \; \frac{r_1}{T}}`$

$`\text{Standard Deviation of Returns}, \; \sigma \; = \; \LARGE{\sqrt{\frac{(r_T \; - \; r^*)^2}{T} \; + \; \frac{(r_{T-1} \; - \; r^*)^2}{T} \; + \; ... \; + \; \frac{(r_{1} \; - \; r^*)^2}{T}}}`$

The mean return can be annualized by multiplying it by 256 and the standard deviation can be annualized by multiplying it by $`\sqrt{256}`$ which just so happens to be 16 (one of the reasons why Carver chose 256 business days).

Values of annual and annualized standard deviation can vary as a result of certain assumptions not being met:

1. When annualzing there was zero auto-correlation — yesterday's return had no impact on today's — which is rarely true for the markets (up days are followed by up days and down days are followed by down days).
2. Daily returns have a symmetric, well-behaved distribution

Despite this, annualized standard deviation is generally pretty close to annual standard deviation and any loss in accuracy is made up in the additional data points included in its estimate.

<h3 style="text-align:center">Risk adjusted returns: Sharpe Ratio</h3>

The Sharpe Ratio is our returns adjusted for risk, in other words high average returns are penalized for high risk (standard deviations) which means from a Sharpe Ratio perspective, you can't take excessive risk in order to get high returns.

$`\text{Sharpe Ratio(SR)} \; = \; \Large{\frac{\text{Mean Return} - \text{Risk-Free Interest Rate}}{\text{Standard Deviation of Returns}}}`$

The difference of Mean Return and Risk-Free Interest Rate is the Excess Returns. Recall to earlier in this strategy that through the no-arbitrage argument for futures, we only deal with Excess Returns as Dividends and Interest Rates are already factored into the price of futures; therefore:

$`\text{SR(for futures)} \; = \; \Large{\frac{\text{Mean Excess Return}}{\text{Standard Deviation}}}`$

$`\text{Annualized SR}, \; SR^* \; = \; SR \times \sqrt{256}`$

<h3 style="text-align:center">Measuring Asymmetry: Skew</h3>

Many are critical of the assumption of symmetrical returns that underpins standard deviation and by extension the Sharpe Ratio. The alternative to this would be the Sortino Ratio which uses the standard deviation of negative returns.

$`\text{Sortino Ratio} \; = \; \Large{\frac{\text{Mean Return} \; - \; \text{Risk-Free Rate}}{\text{Standard Deviation of Negative Returns}}}`$

Carver prefers to use the Sharpe Ratio and measure the symmetry of returns(skew) separately.

Positive skew — more losing days than winning days but the losing days will be relatively small in magnitude \
e.g. Holding an insurance policy: many small losses — paying premiums — and large gains — filing claims.

Negative skew — more winning days than losing days but the winning days will be relatively small in magnitude \
e.g. The insurance company offer insurance policies: many small gains — receiving premiums — and large losses — when claims are filed.

Holding a negatively skewed asset could be a good way of taking on risk that others may shy away from.

Monthly skew is a good balance between having enough data points and not being excessively variable.

<h3 style="text-align:center">Measuring Fat Tails</h3>

Equities typically have fat-tailed distributions where are extreme returns are more likely than in a Normal (Gaussian) Distribution.

One way of measuring the tailedness of a distribution but Carver dislikes due to:
1. It's hard to interpret
2. Doesn't tell you if you have fat left or right tails
3. Not a robust statistical measure so a few days could have significant impact

Carver's preferred alternative is to compare returns to Normal Distribution. 

1. Demean the series (subtract the daily mean return from every data point)
2. Measure percentile of the demeaned results at various points
3. Get 1st, 30th, 70th, 99th percentile returns

The percentile ratios are as follows:

$`\text{Lower Percentile Ratio (of \% returns)} \; = \; \Large{\frac{\text{1st Percentile}}{\text{30th Percentile}}}`$

$`\text{Upper Percentile Ratio (of \% returns)} \; = \; \Large{\frac{\text{99th Percentile}}{\text{70th Percentile}}}`$

For a Normal Distribution the ratio (our reference ratio) comes from the Inverse CDF function for each percentile: 

$`\text{Reference Ratio} \; = \; \Large{\frac{\text{Inverse CDF(0.99)}}{\text{Inverse CDF(0.70)}}} \; \normalsize{=} \; \Large{\frac{\text{Inverse CDF(0.01)}}{\text{Inverse CDF(0.30)}}} \;\normalsize{\approx \; \Large{4.4395}}`$

Compare the reference ratio to each percentile ratio:

$`\text{Relative Lower Fat Tail Ratio, Lower Tail} \; = \; \Large{\frac{\text{Lower Percentile Ratio}}{\text{Reference Ratio}}}`$

$`\text{Relative Upper Fat Tail Ratio, Upper Tail} \; = \; \Large{\frac{\text{Upper Percentile Ratio}}{\text{Reference Ratio}}}`$

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 2: Buy and Hold with Risk Scaling</h1>

Given a quantity of capital, decide how many contracts to buy.

<h2 style="font-weight: bold">Strategy 2:</h2>
<h3>Buy and hold, with positions scaled for risk.</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Measuring Risk of a Single Contract</h3>

$`\text{Riskiness} \; = \; \text{Annualized Standard Deviation of Returns}`$

Translate risk into dollar values:

$`\text{Current Annualized Standard Deviation(\$)} \; = \; \text{Notional Value} \times \text{Standard Deviation(\% returns)}`$

If: $`SR \; = \; \Large{\frac{\text{Annualized Mean Returns}}{\text{Standard Deviation}}}`$

Then: 
$`\text{Annualized Mean Returns} \; = \; SR \times \text{Standard Deviation}`$

Presuming Normal Distribution of returns, 68% of the time our range of returns will be [Mean - $`\sigma`$, Mean + $`\sigma`$]

<h3 style="text-align:center; font-weight: bold">Basic Position Scaling</h3>

Suppose we have \$22,500 in capital and are comfortable with 16\% risk per year, measured in annualized standard deviation terms — target risk $`\tau`$. How many S&P 500 would we want to own? In this example, we're looking at S&P 500 e-micro's at a price of 4500 which has a notional exposure of \$22,500 with a annualized standard deviation of 16\% (how convenient!). So we'd look for \$3600 worth of risk which a single contract of the S&P 500 e-micro would provide ($`\$22,500 \times 16\%`$).

Risk of a single contract, measured as an annualized standard deviation:

$`\sigma(\text{Contract, Base Currency}) \; = \; \text{Notional Exposure(Base Currency)} \times \sigma_\%`$

Risk for an entire position given N contracts:

$`\sigma(\text{Position, Base Currency}) \; = \; \sigma(\text{Contract, Base Currency}) \times N`$

Predetermined target risk — $`\tau`$ (annualized \% standard deviation)

$`\sigma\text{(Target, Base Currency)} \; = \; \text{Capital(Base Currency)} \times \tau`$

We now set our required position risk to be equal to the risk target in currency terms:

$`\sigma\text{(Target, Base)} \; = \; \sigma\text{(Position, Base)}`$

After rearranging our required number of contracts _N_ is:

$`N \; = \; \Large{\frac{\text{Capital} \; \times \; \tau}{\text{Multiplier} \; \times \; \text{Price} \; \times \; FX \; \times \; \sigma_\%}}`$

Alternatively, using daily risk in price points, $`\sigma_p \; = \; \Large{\frac{\text{Current Price} \; \times \; \sigma_\%}{16}}`$

We can also calculate $`\sigma_p`$ by taking the standard deviation of a series of differences in daily back adjusted prices.

The advantage of using price points is that it works even if the futures price is negative, giving us this formula:

$`N \; = \; \Large{\frac{\text{Capital} \; \times \; \tau}{\text{Multiplier} \; \times \; FX \; \times \; \sigma_\% \; \times \; 16}}`$

<h3 style="text-align:center">Some useful ratios:</h3>

$`\text{Contract Leverage} \; = \; \Large{\frac{\text{Notional Exposure per Contract}}{\text{Capital}}}`$

$`\text{Volatility Ratio} \; = \; \Large{\frac{\tau}{\sigma_\%}}`$

$`N \; = \; \Large{\frac{\text{Volatility Ratio}}{\text{Contract Leverage}}}`$

$`\text{Leverage Ratio} \; = \; \Large{\frac{\text{Total Notional Exposure}}{\text{Capital}}}`$

$`\text{Leverage Ratio} \; = \; \Large{\frac{N \; \times \; \text{Notional Exposure per Contract}}{\text{Capital}}}`$

$`\text{Leverage Ratio} \; = \; N \times \text{Contract Leverage Ratio}`$

$`\text{Leverage Ratio} \; = \; \text{Volatility Ratio}`$

It follows that the required amount of leverage is equal to volatility ratio: target volatility divided by price volatility of the instrument.

<h3 style="text-align:center; font-weight: bold">Setting Target Risk</h3>

Factors:
- Risk possible given margin levels (from exchange or broker)
- Risk possible given prudent leverage (ability to cope with losses)
- Personal risk appetite
- Optimal risk given expected performance (from return profile of strategy)

<h3 style="text-align:center">Prudent Leverage</h3>

Recall leverage ratio formula:

$`\text{Volatility Ratio} \; = \; \Large{\frac{\tau}{\sigma_\%}}`$

Say you are willing to accept daily loss of 30\% & lose 50\% of the position with the annualized standard deviation of 16\%, then:

$`\text{Max} \; \tau \; = \; \sigma_\% \; \times \; \text{Maximum Leverage Ratio}`$

$`\text{Max} \; \tau \; = \; \sigma_\% \; \times \; \Large{\frac{\text{Maximum Capital Loss}}{\text{Worst Return}}}`$

$`\text{Max} \; \tau \; = \; 0.16 \; \times \Large{\frac{0.50}{0.30}} \normalsize \; = \; 26.5\%`$

<h3 style="text-align:center">Optimal Risk Given Performance</h3>

$`\text{Half Kelly Optimal Risk} \; \approx \; \Large{\frac{SR}{2}} \normalsize \times 100`$

<hr>

<h3 style="text-align:center; font-weight: bold">A note on compounding...</h3>

Don't compound returns during backtests as this give a better picture of what the strategy would do in the average year agnostic of the previous year's results. Ensure that you always use current account value of your trading account as notional capital when running the strategy live. This results in positions being scaled backed when losses are incurred. 

<hr>

<h3 style="text-align:center; font-weight: bold">Minimum Capital</h3>

$`\text{Minimum Capital for 1 Contract} \; = \; \Large \frac{\text{Capital} \; \times \; \tau}{\text{Multiplier} \; \times \; \text{Price} \; \times \; FX \; \times \; \sigma_\%}`$

Set minimum capital so that you can own at least 4 contracts which allows you to properly scale position without having to close it.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 3: Buy & Hold with Variable Risk Scaling</h1>

One estimate is simply the most recent risk estimate seen over the last month or so

<h2 style="font-weight: bold">Strategy 3:</h2>
<h3>Buy and Hold, with Positions Scaled for Variable Risk</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Forecasting Future Volatility</h3>

Volatility tends to cluster. Using an estimate of standard deviation derived from the last month or so of returns does a good job of forecasting what standard deviation will be in the near term.

To calculate a standard deviation on recent returns we need a moving average of returns. For N returns:

$`r^*_t \; = \; \Large \frac{r_t}{N} \; + \; \frac{r_{t-1}}{N} \; + \; ... \; + \; \frac{r_{t-N+1}}{N}`$

$`\sigma(N)_t \; = \; \Large \sqrt{\frac{(r_t \; - \; r^*_t)^2}{N} \; + \; \frac{(r_{t-1} \; - \; r^*_t)^2}{N} \; + \; ... + \; \frac{(r_{t-N+1} \; - \; r^*_t)^2}{N}}`$\
If we're calculating $`\sigma_\%`$, annualized \% risk we'd used \% returns for $`r_t`$ & multiply by 16.

This method can be too noisy so it's better to use exponentially weighted moving average (EWMA):

$`\text{EWMA Standard Deviation}, \; \sigma(\alpha)_{t} \; = \; \sqrt{\alpha(r_t-r^*_t)^2 \; + \; \alpha(1 - \alpha)(r_{t-1} - r^*_t)^2 \; + \; \alpha(1-\alpha)^2(r_{t-2} - r^*_t)^2 \; + \; ...}`$

Half-life:\
Simple Moving Average(SMA) is 1/2 the window. For EWMA: $`\alpha \; = \; \Large{\frac{2}{N+1}}`$. $`\alpha`$ is the emphasis placed on recent data (i.e. 1 means full weight on most recent data point, 0 means no emphasis placed on most recent data point). Carver recommends a value of 0.06.

Unfortunately, although standard deviation tends to cluster in the short term, it also mean reverts in the long term. As a result we want to blend our short and long term standard deviation:

$`\sigma_{blend,t} \; = \; 0.3(\text{Ten year average of} \; \sigma_t) + 0.7\sigma_t`$

<h3 style="text-align:center; font-weight: bold">Risk Adjusted Costs</h3>

$`\Large \frac{\text{The Reduction in Expected Return Due to Costs}}{\text{Estimate of Risk}}`$

$`\text{Costs in SR Terms} \; = \; \Large \frac{\text{Annual Costs}}{\text{Annualized Standard Deviation}}`$

$`\text{Spread Cost, Price Points} \; = \; \Large \frac{\text{Bid} \; - \; \text{Offer}}{2}`$

$`\text{Spread Cost, Currency} \; = \; \text{Multiplier} \; \times \; \text{Spread Cost Price Points}`$

$`\text{Spread Cost, Currency} \; = \; \Large \frac{\text{Tick Value} \; \times \; \text{Spread in ticks}}{2}`$

$`\text{Total Cost per Trade, Currency} \; = \; \text{Spread Cost, Currency} \; + \; \text{Commission per Contract}`$

$`\text{Total Cost per Trade, \%} \; = \; \Large \frac{\text{Total Cost per Trade, Currency}}{\text{Price} \; \times \; \text{Multiplier}}`$

To get this Total Cost per Trade in risk-adjusted terms (SR) we divide by the % standard deviation

$`\text{Risk Adjusted Cost per Trade} \; = \; \Large \frac{\text{Total Cost per Trade, \%}}{\text{Price} \; \times \; \text{Multiplier}}`$

$`\text{Risk Adjusted Holding Cost} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2`$

$`\text{Risk Adjusted Transaction Cost} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Turnover}`$

$`\text{Annual Risk Adjusted Cost} \; = \; \text{Risk Adjusted Holding Cost} \; + \; \text{Risk Adjusted Transaction Cost}`$

Turnover — the number of times we turnover our average position

__Risk adjusted cost allows us to compare instruments__

<h3 style="text-align:center; font-weight: bold">Which Instruments to Trade</h3>

<h3 style="text-align:center">Minimum capital, performance and costs</h3>

$`\text{Minimum Capital for 4 Contracts} \; = \; \Large \frac{4 \; \times \; \text{Multiplier} \; \times \; \text{Price} \; \times \; FX \; \times \; \sigma_\%}{\tau}`$

Best instrument maximizes SR, and minimizes costs. Don't want to spend more than 1/3 of pre-cost SR on costs.

$`\Large \frac{1}{3} \normalsize \; \text{Pre-Cost SR} \; > \; \text{Rolls per Year} \; \times \; 2 \; + \; \text{Turnover} \; \times \; \text{Risk Adjusted Cost per Trade}`$

<h3 style="text-align:center">Liquidity</h3>

Avoid small markets in general. 

$`\text{Average Daily Volume in USD Risk} \; = \; FX \; \times \; \text{Average Daily Volume} \; \times \; \sigma_\% \; \times \; \text{Price} \; \times \; \text{Multiplier}`$

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 4: Buy & Hold Portfolio with Variable Risk Position Sizing</h1>

Use Strategy 3 for different instruments, based on how Strategy 3, our capital allocation equals risk allocation. 

<h2 style="font-weight: bold">Strategy 4:</h2>
<h3>Buy and hold a portfolio of instruments, each with positions scaled for a variable risk estimate.</h3>

<hr>

Strategy Variations: Risk Parity and All-Weather

<h3 style="text-align:center; font-weight: bold">Strategy Variation: Risk Parity</h3>

$`\text{Position Size,} \; N_t \; = \; \Large \frac{\text{Capital} \; \times \; \tau}{\text{Multiplier} \; \times \; \text{Price}_t \; \times \; FX_t \; \times \; \sigma_{\%t}}`$

The optimal number of contracts for instrument _i_ given proportion of capital (weight) allocated to it is:

$`N_{i,t} \; = \; \Large \frac{\text{Capital} \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;}`$

Carver typically weights instruments equally, in the strategy he splits 50\% into S&P 500 and 50\% into bonds.

<h3 style="text-align:center">Correcting for Diversification</h3>

Diversification:

- Enjoy reduced risk for a similar return
- Can apply more leverage to meet risk target

Instrument Diversification Multiplier (IDM) which allows us to hit our expected risk target (greater than 1). It can be approximated by:

$`\approx \Large \frac{\text{Target Risk}}{\text{Realized Aggregate Risk}}`$

So...

$`N_{i,t} \; = \; \Large \frac{\text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;}`$

The leverage required by this strategy make futures a necessity. Most other assets would be impossible to get the desired leverage. 

<h3 style="text-align:center; font-weight: bold">Strategy Variation: All Weather</h3>

Risk Parity had stellar performance for 2 Reasons:
- Bonds & equities benefitted from related repricing effects, lower interest rates, and higher PEs
- Low Correlation between US bonds & equities

Bonds & Equities have high correlation in an inflationary environment.

Carver's recommended all-weather allocation:
- 25\% US Stocks: S&P 500 micro
- 25\% Bonds
  - 12.5\% Long Term: US 10-year bond futures
  - 12.5\% Intermediate: US 5-year bond futures
- 25\% Commodities
  - 12.5\% WTI Crude Oil mini futures
  - 12.5\% Corn futures
- 25\% Gold: Gold micro futures

Gold & Commodities benefit from inflationary environments

<h3 style="text-align:center; font-weight: bold">Strategy Variation: Generalized Risk Premia Portfolio</h3>

$`\text{Minimum Capital (4 contracts)} \; = \; \Large \frac{4 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;}{\times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}`$

<h3 style="text-align:center">How to set instrument weights</h3>

We want a correlation matrix - set of estimates for all pairwise correlations between sub-strategy returns, trading each instrument. Since each strategy should have approximate risk, we don't need a covariance matrix which incorporates standard deviation (risk).

<h3 style="text-align:center">An algorithm for automatically selecting instruments</h3>

1. Decide on set of possible instruments
    - meet cost, liquidity, & legal requirements
2. Choose the first investment
    - Using general IDMs, go through each instrument & calculate minimum capital for each instrument, discarding any that exceed capital availabe
    - Choose the 1 with the lowest risk adjusted cost
3. Measure the expected SR of the portfolio
    - Assuming all instruments have same pre-cost SR,\
    $`\text{Instrument Annual SR}_i \; = \; SR^* - (T \times c_i)`$\
    $`\text{Instrument Annual Mean}_i \; = \; \tau \times (SR^* - (T \times c_i))`$\
    $`\text{Instrument Annual Mean in Portfolio}_i \; = \; \text{Weight}_i \times IDM \times \tau \times (SR^* - (T \times c_i))`$\
    $`\text{Portfolio Mean(for N instruments)} \; = \; \sum_{i=1}^{N}(\text{Weight}_i \times IDM \times \tau \times (SR^* - (T \times c_i)))`$\
    $`\text{Portfolio} \; \sigma \; = \; IDM \times \tau \times \sqrt{w \; \Sigma \; w'}`$ where _w_ is the vector of instrument weights, _w'_ is vector _w_ transposed, $`\Sigma`$ is the correlation matrix of sub-strategy returns, and perform matrix multiplication inside.\
    $`\text{Portfolio SR (for N instruments)} \; = \; \Large \frac{\sum^{N}_{i=1}(\text{Weight}_i \times (SR^* - (T \times c_i)))}{\sqrt{w \; \Sigma \; w'}}`$
4. Iterate over all instruments not in portfolio
5. Choose instrument with high-expected SR for its trial portfolio
6. Check to see if expected SR for current portfolio has decreased by +10\%, if so, don't include instrument

<h4>Carver's recommended risk targets:</h4>

$\begin{equation}
\nonumber
\begin{align*}
\text{1 instrument} &: 10\% \\
\text{2-6 instruments} &: [10\%, 20\%] \\
\text{1+ instrument from each of the 7 asset classes} &: 20\% \\
\text{2+ instruments from each class} &: 25\%
\end{align*}
\end{equation}$

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 5: Slow Trend Following</h1>

<h2 style="font-weight: bold">Strategy 5:</h2>
<h3>Buy & hold 1+ instruments when they're in long up trend, scaled for variable risk estimates.</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Testing for Market Uptrend</h3>

Can use SMA(256), if $`SMA < P_t \rightarrow \text{uptrend}`$. SMA(256) can be a bit rocky since it's slow to react. Add a shorter term SMA to smooth this out. $`SMA(64) > SMA(256) \rightarrow \text{uptrend}`$.

This Moving Average Crossover(MAC) is a decent way of identifying long-term trends but fails to recognize faster trends with several short-lived reversals. 

Alternative is to use EWMA(_α_). Can create an $`EWMAC \; = \; EWMA(N=64) - EWMA(N=256)`$. 

Use this trend filter as an on/off switch for strategy 4's equation:

$`N_{i,t} \; = \; \Large \frac{\text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;} \times \normalsize(EWMAC > 0)`$

<h3 style="text-align:center; font-weight: bold">Trend Filter on S&P 500 Micro Futures</h3>

<ol>
  <li>slightly lower risk</li>
  <li>better average drawdown</li>
  <li>lower returns</li>
  <li>higher turnover</li>
  <li>≈ annual costs</li>
</ol>

Alternative method to managing positions is a static method where you don't adjust your position once established in an uptrend.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 6: Slow Trend Following, Long & Short</h1>

<h2 style="font-weight: bold">Strategy 6:</h2>
<h3>Trade 1+ instruments, each with positions scaled for variable risk estimate. Hold a long position when they have been in a long uptrend, and a short position in a downtrend.</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Adjusting the trend filter to go both long and short</h3>

$`
\begin{equation}
\nonumber
\begin{align*}
\text{EWMAC > 0} &: \text{Go Long}\\
\text{EWMAC < 0} &: \text{Go Short}
\end{align*}
\end{equation}
`$

$`N_{i,t} \; = \; \Large \frac{\text{Sign(trend)}_t \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;} \times \normalsize(EWMAC > 0)`$

<h3 style="text-align:center; font-weight: bold">Results</h3>

Worse average return, worse average drawdown, worse average SR; however, these same statistics are better in aggregate.

To compare & negate secular trends we can compare using linaer regression:\
$`y_t \; = \; \alpha + \beta x_t + \epsilon_t`$ where $`y_t`$ is the monthly average returns, $`\alpha`$ is the difference between strategies, $`\beta`$ is how much the two strategies comove, $`x_t`$ is the base strategy like strategy 4, $`\epsilon`$ is the estimate of error.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 7: Slow trend following with trend strength</h1>

<h2 style="font-weight: bold">Strategy 7:</h2>
<h3>Strategy 6 scaled according to strength of the trend</h3>

<hr>

Looking at crossover over time, volatility and market value has changed so this crossover needs to be risk-adjusted

Forecast — value that is proportional to an expected risk adjusted return (SR)

$`\text{Raw Forecast} \; = \; \Large \frac{\text{Fast EWMA} \; - \; \text{Slow EWMA}}{\sigma_p}`$\
where $`\sigma_p \; = \; \Large \frac{\text{Price} \; \times \; \sigma_\%}{16}`$

We scale the forecast to average absolute value of 10:

$`\text{Scaled Forecast} \; = \; \Large \frac{\text{Raw Forecast} \; \times \; 10}{\text{Average Absolute Value of Raw Forecast}}`$

$`\text{Forecast Scalar} \; = \; \Large \frac{10}{\text{Average Absolute Value of Raw Forecast}}`$

$`\text{Scaled Forecast} \; = \; \Large \frac{\text{EWMA(64)} - \text{EWMA(16)}}{\sigma_p} \normalsize \times \text{Forecast Scalar} `$

$`N_{i,t} \; = \; \Large \frac{\text{Scaled Forecast}_{i,t} \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{10 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t} \;} \times \normalsize(EWMAC > 0)`$

Good idea to set max forecast value (Carver uses 20).

$`\text{Capped Forecast}_{i,t} \; = \; \text{max(min(Scaled Forecast}_{i,t}, \; -20), \; +20)`$

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 8: Fast trend following, long & short with trend strength</h1>

<h2 style="font-weight: bold">Strategy 8:</h2>
<h3>Strategy 7 with shorter trend duration</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Constructing a faster trend filter</h3>

Should use windows of 1:4 ratios:\
e.g 16:64, 32:128, 64:256

Same equation as Strategy 7 to calculate N number of positions for a particular trend filter.

<h3 style="text-align:center; font-weight: bold">Buffering to reduce trading costs</h3>

Buffer _B_ set as a fraction _F_ of the average long position:

$`B_{i,t} \; = \; \Large \frac{F \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_{i} \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}`$

Per Carver: _F_ can easily be 0.10. 

Create upper & lower buffers and trade if current position is outside of these buffers:

$`\text{Lower Bound}, \; B^L_{i,t} \; = round(N_{i,t} \; - \; B_{i,t})`$

$`\text{Upper Bound}, \; B^U_{i,t} \; = round(N_{i,t} \; + \; B_{i,t})`$

$`\text{Current Position}, \; C_{i,t}`$

$`Decision = \begin{cases}
 & B^U_{i,t} \; \leq \; C_{i,t} \; \leq \; B^L_{i,t} \; : \; \text{No Trading Required} \\ 
 & C_{i,t} \; < \; B^L_{i,t} \; : \; \text{Buy} \; (B^L_{i,t} \; - \; C_{i,t}) \;  \text {Contracts} \\ 
 & C_{i,t} \; > \; B^U_{i,t} \; : \; \text{Sell} \; (C_{i,t} \; - \; B^U_{i,t}) \;  \text {Contracts} 
\end{cases}`$


<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 9: Multiple Trend Following Rules</h1>

We want to trade as many instruments as possible as they give us access to many different kinds of risk premia. This is seen in many instruments when their returns are relatively uncorrelated. We don't have to just diversify across instruments but we can diversify across strategies.

<h2 style="font-weight: bold">Strategy 9:</h2>
<h3>Trade a portfolio of one or more instruments, each with positions scaled for a variable risk estimate. Calculate a number of forecasts for different speeds of trend filter. Place a position based on the combined forecast.</h3>

<hr>

<h3 style="text-align:center">Selecting a series of trend following filters</h3>
Anything shorter than EWMAC(4,16) would be too expensive for most instruments. Anything longer than EWMAC(64,256) becomes too correlated with a long only strategy.

- $`\text{EWMAC}_n \; = \; \text{EWMAC}(n, \; 4n)`$

For each variation, ues the same position sizing and management rules as strategy eight:
- Calculate the raw crossover value for each trading rule variation
- Divide by the standard deviation to find the risk normalized forecast
- Scale the forecast so it has an expected absolute average value of 10
- Cap the forecast
- Calculate an optimal risk adjusted unrounded position, _N_ contracts, using the capped forecast, risk target, current risk of the instrument, current price, FX rate, plus the capital, instrument weights and instrument diversification multiplier (IDM)
- Calculate a buffer zone around the optimal position
- Compare the current position to the buffer zone to decide whether to trade

Need forecast scalars which Carver already calculated:
| EWMAC   | Forecast Scalars |
|:--------|:----------------:|
| EWMAC2  | 12.1             |
| EWMAC4  | 8.53             |
| EWMAC8  | 5.95             |
| EWMAC16 | 4.10             |
| EWMAC32 | 2.79             |
| EWMAC64 | 1.91             |

<hr>

<h3 style="text-align:center">Should we use a different measure of volatility for different trend speeds?</h3>

Whilst we may be using incredibly short or long EWMA's for our forecasts, EWMA's from 10-50, 30-35 in particular, are best at predicting future volatility.

<hr>

<h3 style="text-align:center">The performance of different trend filters</h3>

Historically EWMAC(16, 64) has been the most profitable. $`\beta`$ to the long strategy increases as the speed decreases. 

<h3 style="text-align:center">Combining different forecasts</h3>
How do we combine these strategies, several options each at a different stage of the trade generation process:
1. Averaging the raw forecasts before any capping takes place
2. Averaging the capped forecasts
3. Averaging calculated positions, either before or after buffering
4. Trading each trend filter as a completely different system, netting off the trades generated
5. Compeltely separate systems, with no netting

Option 5 is a non-starter since it lacks the benefit of netting whilst also increasing trading costs. Carver believes averaging as soon as possible offers the greatest benefit (reduces calculations and simplifies the trading strategy); however, it is best to do averaging on capped rather than uncapped forecasts as it ensures we won't end up with a combined forecast that is temporarily dominated by a single trend filter just because it happens to have a very large forecast on a given day. 

It follows that the preferred method is to take a weighted average of capped forecasts from different trading rules (option 2). The weights used when calculating this average are forecast weights. Forecast weights will sum to 1 and none will be negative. Remember that all forecasts are consistently scaled to achieve an average absolute forecast value of 10.

For each trend filter _j_ traded, calculate a capped forecast at time _t_ using the equation below for a given instrument _i_:

$`\text{Raw Forecast}_{i,j,t} \; = \; \Large{\frac{\text{Fast EWMA}_{i,j,t} - \text{Slow EWMA}_{i,j,t}}{\sigma_{p,i,t}}}`$

Apply filter specific forecast scalar (from table above), and a cap of 20 on the absolute value of the scaled forecast:

$`\text{Scaled Forecast}_{i,j,t} \; = \; \text{Raw Forecast}_{i,j,t} \; \times \; \text{Forecast Scalar}_j`$

$`\text{Capped Forecast}, \; f_{i,j,t} \; = \; \text{max(min(Scaled Forecast}_{i,j,t},\; +20), \; -20)`$

Take a weighted average of capped forecasts, using forecast weights $`w_{i,j}`$ which sum to 1 for a given instrument:

$`\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{\# filters}}_{j=1} (w_{i,j} \; \times \; f_{i,j,t})}`$

<h3 style="font-weight: bold; text-align:center"> Factors to consider in choosing forecast weights</h3>

- Expected pre-cost SR: better performing trading rules should get a higher weight
- Costs of trading a given filter: cheaper and slower trading rules will get a higher weight since post-cost SR will be higher
- Correlation between forecasts: higher weights for rules that are more diversifying

<h3 style="text-align: center;">Costs</h3>
Most straightforward factor. Each filter will likely have the same turnover across instruments; therefore the costs will be dependent on the individual cost per trade for each instrument. 

<h3 style="text-align: center;">Correlation and Diversification</h3>
Diversification pattern for trend filters don't vary much for different instruments, so we can use aggregated results. Here we would want to create a correlation matrix of aggregate returns for each trend filter. Typically further apart filters will have less correlation. Since filters on the extremes (very fast and very slow) have the lowest average correlation with other filters, it follows that if accounting for diversification alone, filter weights would have a 'U' shape with greater weighting placed on the fastest and slowest filters.

<h3 style="text-align: center;">Pre-Cost Performance</h3>
Carver makes the case that whilst there are considerable differences in performance between filters for each instrument, these differences are not statistically significant and therefore do not warrant a different filter for each instrument based on its performance; instead, he uses aggregate results for performance by trading rule to influence weighting.

<h3 style="text-align: center; font-weight: bold;">Putting it together: a method for allocating forecast weights</h3>
Principles for allocating forecast weights:

- Forecast weights should be the same across instruments, except where trading costs dictate otherwise
- Forecast weights should be lower on rules that trade faster where instruments have a higher cost per trade
- Avoid overfitting forecast weights: placing too much weight on a single trading rule variation
- Forecast weights should ideally be higher on more diversifying rule variations: the slowest and the fastest

Bearing that in mind

1. On an instrument by instrument basis, remove trading rules that are too expensive
2. Allocate forecast weights using a top down methodology (for strategy nine, this implies all remaining trend filters get the same forecast weight)

<h3 style="text-align: center">Removing expensive trading rules</h3>
Recall from Strategy 3 the trading speed limit where instruments which use up more than 1/3 of their expected pre-cost return in costs are excluded. Carver uses a notional value of 0.10 SR units for instrument trading costs.

$`\text{Annual Risk Adjusted Costs} \; = \; \text{Transaction Costs} \; + \; \text{Holding Costs}`$

This can be broken down further:

$`\text{Risk Adjusted Transaction Costs} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Annual Turnover}`$

$`\text{Risk Adjusted Holding Costs} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2`$

We can have a higher max trading cost for trading rules since:

1. If our most expensive trading rule incurs exactly 0.10 SR units in costs for a given instrument, then on average the combined forecast will always be well under 0.10 SR units
2. The effect of buffering our positions will slow down trading and allow us to trade a set of forecasts that is a little quicker. 

Because of these two effects, Carver uses a higher limit of 0.15 SR units for trading rules.

For a given instrument if the max annual risk adjusted costs is 15, the maximum allowable turnover can be derived for a given trading rule variation:

$`\text{Annual Risk Adjusted Costs} \; < \; 0.15`$

$`\text{(Cost per Trade} \; \times \; \text{Turnover}) \; + \; \text{(Cost per Trade} \; \times \; \text{Rolles per Year} \; \times \; 2) \; < \; 0.15`$

$`\text{Turnover} \; < \; \Large{\frac{0.15 \; - \; (\text{Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2)}{\text{Cost per Trade}}}`$


<h3 style="text-align: center">Top down method for choosing forecast weights</h3>

1. Split the list of trading rules by style. Allocate between styles according to your preferences
2. Within a given style, allocate equally across trading rules
3. Within a given trading rule, allocate equally across variations of each given trading rule

Trading styles can be categorized as divergent or convergent: 
- Divergent strategies make money when markets diverge away from equilibrium: trend following is a classic divergent strategy. 
- Convergent strategies make money when markets move towards their equilibrium. 

For our current strategy, the application of it is very easy:
- We only have one style: divergent. Allocate 100% of forecast weights to this
- We only have one trading rule: trend following with EWMAC. Allocate 100% of our forecast weights to that rule
- We have between one and six variations of our trading rule, depending on the instrument we're trading. Equally divide 100% of our forecast weight between these rules

Carver believes that it is best to equally allocate to avoid overfitting by choosing certain variations that we believe to be better.

<h3 style="text-align: center; font-weight: bold">Accounting for forecast diversification</h3>

Similar to the Instrument Diversification Multiplier, we need to use a Forecast Diversification Multiplier to better allocate for diversification of returns (see appendix B). Calculated using pooled info across instruments (can also be estimated theoretically under certain assumptions which have the advantage of no in-sample fitting). 

Since most trend filters are fairly correlated the FDM's won't ever be too high. After applying the FDM, the combined forecast can exceed +/- 20 so a cap is necessary.

$`\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{Trading Variations}}_{j = 1}\;(W_{i,j} \; \times \; F_{i,j,t})}`$

$`\text{Scaled Combined Forecast}_{i,t} \; = \; \text{Raw Combined Forecast}_{i,t} \; \times \; FDM_j`$

$`\text{Capped Combined Forecast}_{i,t} \; = \; \text{max(min(Scaled Combined Forecast}_{i,t}, \; +20), \; -20)`$

$`N_{i,t} \; = \; \LARGE{\frac{\text{Capped Combined Forecast}_{i,t} \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{10 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}`$

<h3 style="text-align: center; font-weight: bold">Performance Evaluation</h3>

Does better than any other strategy so far but equities still lag behind with an SR close to 0. Volatility however has done well with an SR close 0.50.

<hr>

<h3 style="text-align: center; font-weight: bold">Is trend following dead?</h3>

While trend following has lost money in 2009, 2015, 2016, and 2018, strategies do have losing years. Even still, the positively-skewed nature of this strategy means that losses in losing years are much smaller than the gains in winning years. It does seem, however, that trend following's returns have diminished over time with total non-compounded returns in the 1970s of 500% compared, over 200% in each of the next 3 decades, but only 100% since 2010. Research has shown that over the centuries, decades of relative underperformance for trend following isn't uncommon. 

Another factor is that the psychological biases which seem to underpin trend following are unlikely to go away any time soon unless human traders are completely replaced by computers.

<hr>

<h3 style="text-align: center; font-weight: bold">Conclusion</h3>

While trend following has been profitable, we should focus on other strategies to add to our repetoire to further diversify.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 10: Basic Carry</h1>

$`\text{Excess Return} \; = \; \text{Spot Return} \; + \; \text{Carry}`$

For example, the S&P 500 carry is equal to the dividends we'd earn less the interest required to fund a loan used for buying all the stocks in the S&P 500 index. 

In fact, __all futures have carry__, although the source of this return differs depending on the asset class.

The back-adjusted price is effectively the cumulated history of past excess returns, so it incorporates the effects of both spot returns and carry; however, carry can be predicted independently, and very successfully.

Carry is a well-known risk premium that is quite different from the trend premium. Carry is also potentially hazardous without the nice positive skew we've grown accustomed to. Should be used with care, or better yet combined with trend following.

<h2 style="font-weight: bold">Strategy 10:</h2>
<h3>Trade a portfolio of one or more instruments, each with positions scaled for a variable risk estimate. Scale positions according to the strength of their forecasted carry</h3>

<hr>

<h3 style="text-align:center">The causes of carry</h3>

These carry returns come from different sources, depending on the asset class of the instrument you trade. We can decompose these returns by thinking about an arbitrage trade that will replicate a long position in the future. For the equities, the arbitrage trade is to borrow funds to buy the shares that make up the index, giving us this excess return:

$`\text{Excess Return(Equities) = Spot Return + Dividends - Interest}`$

$`\text{Carry(Equities) = Dividends - Interest}`$

Hence, carry for equities can be positive or negative depending on the relative size of dividend yields and interest rates.

Consider bonds:

$`\text{Excess Return(Bonds) = Spot Return + Yield - Repo Rate}`$

$`\text{Carry(Bonds) = Yield - Repo Rate}`$

Since the repo rate is often lower than the yield, carry in bonds is normally positive. An exception being when the central bank sets short-term interest rates at a high level which is expected to fall in the future, resulting in an inverted yield curve.

Consider in foreign exchange (FX) markets where there are two different interest rates:

$`\text{Excess Return(FX) = Spot Return + Deposit Rate - Borrowing Rate}`$

$`\text{Carry(FX) = Deposit Rate - Borrowing Rate}`$

Consider for example a long GBPUSD trade, which is equivalent to borrowing USD, converting them into pounds, and then depositing the pounds. The deposit rate would be the appropriate interest rate in the UK, and the borrowing rate would be the US interest rate. G10 FX markets typically have similar interest rates so their carry is negligible whereas emerging market currencies normally have significant positive carry against the dollar. 

Short Term Interest Rates and Volatility cary is more complex and worth reading later but the formula is:

$`\text{Excess Return(STIR, Vol) = Spot Return + Current Spot Price - Futures Price}`$

$`\text{Carry(STIR, Vol) = Current Spot Price - Futures Price}`$

Consider metals which have no carry and are almost certainly negative:

$`\text{Excess Return(Metals) = Spot Return - Borrowing Cost - Storage Costs}`$

$`\text{Carry(FX) = -(Borrowing Cost + Storage Costs)}`$

Consider Energy and Agricultural Products:

$`\text{Excess Return(Energy, Agricultural) = Spot Return - Borrowing Cost - Storage Costs + Convenience Yield}`$

$`\text{Carry(FX) = Convenience Yield - (Borrowing Cost + Storage Costs)}`$

This convenience yield reflects the current market expectations about future supply and demand for the commodit which could be positive or negative. Commodities typically have a negative carry although positive carries possible for extended periods of time.

<h3 style="text-align:center">Carry: What can go wrong</h3>

Be wary of thinking carry is just free money. If you buy a future with an expected carry, the price may move against you, effectively cancelling out your return. _Spot Drag_ is when the price decreases more than the value of the carry becoming a loss whereas a price rise will add to the carry gains.

Carvers backtests find that a $1 carry will typically return $1.15. Assets which offer positive carry are only doing so because there are risks from holding them. Said asset might have a negative skew for example. Holding an emerging market FX future would have a positive carry due to the risk of sudden and drastic depreciation events. 

<h3 style="text-align:center">Measuring expected carry</h3>

Our expected carry can be measured by comparing the current price of the future and the spot. It's difficult to get spot prices for many assets, especially commodities. Spot and futures prices need to be synchronized in time to get an accurate estimate, which isn't always easy. Even if we can get spot prices, it's a hassle and potentially expensive to add another source of data.

However, this isn't a problem if we're holding futures that are further out on the curve. Theoretically the next previous expiration contract serves as the spot price of the further out contract. For example for the S&P 500 e-mini, expiring in December, March, June, and September, if December is the front month its price can be used to estimate the spot price for the March contract.

$`\text{Raw Carry = Price of nearer futures contract - Price of Currently Held Contract}`$

An advantage of this approach is both contracts are trading on the same exchange so if daily closing prices are used, the values will be synchronized.

This isn't much help for most financial futures, where we are typically limited to holding the front contract and there isn't a nearer contract we can use for comparison. We can get around this if we assume that the gradient of the futures curve is constant, then the expected carry on the contract we are holding will be equal to:

$`\text{Raw Carry = Price of Currently Held Contract - Price of Further Out Contract}`$

There will always need to be another future further out because without it, rolling would be impossible; however, the further out contract might not appear until a few days before expiry. Worst case scenario we have an accurate reading for carry a few times a year when each roll happens which is normally sufficient.

A couple of examples, its November 2021 and you're trading the S&P 500 December 2021 contract. Since this is the front contract, you don't have the option of calculating carry using a nearer delivery month and you're not collecting spot S&P 500 index prices. So you go to the further out March 2022 contract. The prices were 4578.50 and 4572.00 for December and March, respectively. Making the raw carry:

$`\text{Raw Carry = Price of Currently Held Contract - Price of Further Out Contract}`$

$`\text{Raw Carry = 4578.50 - 4572.00 = 6.50}`$

Now consider WTI Crude Oil future. Carver only trades the December delivery. Imagine you had already begun holding the December 2022 contract which is priced at 62.09. Obviously this isn't the front month — so you can use a nearer month in your calculation. Crude has monthly deliveries so the previous contract is November 2022, trading at 62.61:

$`\text{Raw Carry = Price of nearer futures contract - Price of Currently Held Contract}`$

$`\text{Raw Carry = 62.61 - 62.09 = 0.52}`$

<h3 style="text-align:center; font-style:italic">Annualization</h3>

This value of carry reflects what we can expect to earn between expiries. Some contracts trade quarterly, others monthly; and even some that roll usually two but sometimes three months apart. We must annualize to get a consistent estimate of carry.

$`\text{Expiry Difference in Years} \; = \; \Large{\frac{|\text{Months between Contracts}|}{12}}`$

$`\text{Annualized Raw Carry} \; = \; \Large{\frac{\text{Raw Carry}}{\text{Expiry Difference in Years}}}`$

<h3 style="text-align:center; font-style:italic">Risk Adjustment</h3>

Although the S&P 500 is expected to earn 26.0 price units of carry to the 6.24 for Crude Oil, so what? Since our annualized carry is in units of price, it makes sense to divide it by the annualized standard deviation of returns for the relevant instrument also in price units.

$`\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}`$

We may also use annualized standard deviation of returns in percentage terms with:

$`\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_\% \; \times \; \text{Current Contract Price}}}`$

After risk adjusting, the carry for Crude Oil, 0.358, is 10 times higher than the S&P 500, 0.035.

<h3 style="text-align:center">Carry as a Trading Strategy</h3>

This is where forecasting comes in. In strategy 7, Carver formally defined a forecast as a __value that is proportional to an expected risk adjusted return__ which implies forecasts are proportional to expected SRs. 

Since carry is defined as an expected annual return divided by an annualized standard deviation both in the same price units, __expected carry is equal to expected SR__. Hence, the carry calculation above naturally produces a forecast:

$`\text{Carry Forecast} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}`$

Carver uses this in reference to a truly robust trading strategy that can deal with less than perfect data:

<p style="font-style:italic">Loose pants fit everyone — Perry Kaufman</p>

If you look at the carry for natural gas, it is incredibly seasonal, consistently going negative for certain months of the year because of seasonal changes to supply and demand and it's very difficult and expensive to store, amplifying seasonal effects. This seasonality is the main reason Carver only trades the December contract for Crude. Using a fixed month for seasonal commodities helps lessen this.

After plotting the carry for the Bund, it shows its incredibly seasonal, switching every quarter. The method of comparing carry for the first two contracts is rather imprecise which means the carry estimate will always have the wrong sign. The reason for Bund seasonality is the German government issues a new batch of bunds every six months which then become the "cheapest to deliver" (CTD).

If we hold the Eurostoxx, the carry will be unusually positive for the March contract and the price of the June Eurostoxx is usually lower than that of March. Most firms in the Eurostoxx pay their largest dividend in April. As a result our carry forecast will be systematically wrong. When holding March it will be biased upwards and for June it will be far too low.

In theory this problem affects almost all equity futures except for the German DAX30 which is a total return index. This is more noticeable outside of the USA where dividends tend to be paid annually or semi-annually as opposed to quarterly in the USA. US dividends tend to be lower than in Europe, further dampening the effect.

<h3 style="text-align:center">Reducing costs when carry trading</h3>

From the above it's clear we have:
<ol type="a">
  <li>a general problem</li>
  <li>instrument specific problems</li>
</ol>

The _general_ problem is that carry estimates are unusually noisy, as the price difference between adjacent futures contracts can move around from day to day.

We then have _specific_ problems with seasonal instruments where carry varies persistently depending on which month we are currently trading. These fall into two categories:
1. Those where we are accurately estimating the seasonality because we trade the second contract, such as Natural Gas
2. Instruments where we are getting it wrong because we can only trade the front contract, but are imprecisely measuring carry using the difference between the first and second contracts. Includes a few bond markets and most non-US equity markets.

First, let's consider the problem of noise. Noise will lead to unnecessary trading, thus increasing trading costs without realizing additional profits. We can either buffer or smooth the forecast in some way. Smoothing isn't appropriate for trend filters since they are constructed from moving averages but they can be used for carry:

$`\text{Smoothed Carry Forecast(Span) = EWMA}_{span}\text{(Carry Forecast)}`$

Different spans may be appropriate for different instruments. Natural Gas and other instruments with correctly estimated seasonality would require quite a short span to adjust quickly to changes after each roll whereas a longer span would make sense for most other instruments.

Carver uses four different spans as his carry trading rule variations:

- 5 business days ~1 week
- 20 business days ~1 month
- 60 business days ~3 months
- 120 business days ~6 months

$`\text{Scaled Carry Forecast(Span)} \; = \; \text{Smoothed Carry Forecast(Span)} \; \times \; \text{Forecast Scalar}`$

Carver finds a forecast scalar of 30 is appropriate. Would need to measure the average absolute value across all of our different futures instruments with all available data history which in Carver's case came in around 0.33 so x30 would get an average value of 10.

$`\text{Capped Carry Forecast(Span)} \; = \; \text{max(min(Scaled Forecast(Span)}, \; +20 \;), \; -20)`$

If we were only trading one speed of carry, then we'd calculate these forecasts every day, using closing prices. We'd then recalculate the optimal position using the standard position scaling equations. However it's better to trade multiple carry trading rule variations to get some diversification benefit.

<h3 style="text-align:center">Trading multiple carry trading rules</h3>

Same deal as combining multiple trading rule variations in the previous chapter. We must:

1. Determine which trading rule variations are cheap enough to trade. Identical max turnover formula
2. Select a set of forecast weights, Carver found that equal weights for trend filters that meet the turnover requirement seen below (maybe worth calculating ourselves)

| Carry    | Turnover        |
|:---------|:---------------:|
| Carry5   | 5.75            |
| Carry20  | 3.12            |
| Carry60  | 1.82            |
| Carry120 | 1.22            |

(Remember Carry5 means the EWMA(5))

Bunds, Bobl, Bono all do well in retrospect despite the wrong estimate of carry. As Carver says _even a strategy that gets the carry wrong consistently can be profitable_

Same formula for calculating raw combined forecast and Scaled combined forecast

FDM suggested forecast weights (provided by Carver):

| Carry                 | Forecast Weight | FDM             |
|:----------------------|:---------------:|:---------------:|
| Carry5, 20, 60, 120   | 0.25            | 1.04            |
| Carry20, 60, 120      | 0.333           | 1.03            |
| Carry60, 120          | 0.50            | 1.02            |
| Carry120              | 1.00            | 1.00            |


<h3 style="text-align:center">Reviewing Carry Performance</h3>

Median Absolute Carry (MAC) = Average Scaled Forecast divided by the Forecast Scalar (30) and taking the median absolute value. MAC will be larger for asset classes with instruments that have stronger carry forecasts on average. When MAC is higher, annualized standard deviation will also be higher.

$`\text{Median Absolute Carry, MAC} = \text{Median}(\Large{\frac{\text{Average Scaled Forecast}}{\text{Forecast Scalar}}})`$

The difference in standard deviation also implies that SRs may not be the most sensible metric to evaluate performance across asset classes. An alternative measure is adjusted mean return (AMR) which is also a Sharpe ratio but it's the annual return divided by the risk target of 20%, not the realized standard deviation we use for a standard SR calculation. Unlike the actual SR it will be smaller when forecasts are lower, and vice versa.

You can directly compare AMR to MAC since both are Sharpe Ratios (this is because the forecasts produced by this strategy are equal to their expected SRs, other strategies only produce forecasts proportional to their expected SRs). MAC is the Sharpe Ratio promised by carry and the AMR is the Sharpe Ratio delivered by carry. 

$`\% \text{Carry Realized} = AMR / MAC`$. 

%Carry Realized > 100% means more carry delivered than promised, and vice versa.

Carry under promises and over delivers in all but two asset classes: agricultural and energy markets which are also where there are many seasonal instruments.

Carver believes we don't have enough evidence to exclude certain instruments or adjust weights.

Carry is cheaper to trade than trend but its SR isn't as good. However, it does have a significantly lower beta, unlike trend it usually has a more mixed set of longs and shorts. This results in a higher alpha.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 11: Combined carry and trend</h1>


<h2 style="font-weight: bold">Strategy 11:</h2>
<h3>Trade a portfolio of one or more instruments, each with positions scaled for a variable risk estimate. Scale positions according to the strength of a combined foreast which is a weighted average of carry and trend forecast.</h3>

<h3 style="text-align:center; font-weight: bold">Building Blocks</h3>

Values designed in this book are able to fit neatly together for any combination.

<h3 style="text-align:center; font-weight: bold">Forecast weights for a combined strategy</h3>

First, for any given instrument we will slect the subset of forecasting rules which don't exceed Carver's speed limit of 0.15 Sharpe Ratio units in costs, using the turnover figures previously mentioned, and the risk adjusted cost per trade for the relevant instrument.

Remembering the top down method:

- Allocate between styles to your preference. Our two styles are convergent and divergent. Trend is divergent and carry is convergent.
- We only have one trading rule within each style: EWMAC trend in divergent and carry in convergent
- Up to 6 variations of EWMAC and up to 4 variations of carry.

Carver uses a 60/40 split (trend / carry) as it maximizes SR, minimizes drawdown, and has a pretty decent alpha.

Forecast Weights for a given set of EWMAC and Carry trading rule variations

| EWMAC/Carry Combination                       | Forecast Weight each EWMAC | Forecast Weight each Carry |
|:----------------------------------------------|:--------------------------:|:---------------:|
| Carry5, 20, 60, 120, EWMAC2, 4, 8, 16, 32, 64 | 0.10                       | 0.10            |
| Carry5, 20, 60, 120, EWMAC4, 8, 16, 32, 64    | 0.12                       | 0.10            |
| Carry5, 20, 60, 120, EWMAC8, 16, 32, 64       | 0.15                       | 0.10            |
| Carry5, 20, 60, 120, EWMAC16, 32, 64          | 0.20                       | 0.10            |
| Carry5, 20, 60, 120, EWMAC32, 64              | 0.30                       | 0.10            |
| Carry20, 60, 120, EWMAC32, 64                 | 0.30                       | 0.1333          |
| Carry20, 60, 120, EWMAC64                     | 0.60                       | 0.1333          |
| Carry20, 60, 120                              | 0.00                       | 0.3333          |
| Carry60, 120                                  | 0.00                       | 0.50            |
| Carry120                                      | 0.00                       | 1.00            |

| Number of Trading Rules |  FDM  | Number of Trading Rules |  FDM  |
|:-----------------------:|:-----:|:-----------------------:|:-----:|
| 13                      | 1.39  | 40 or more              | 2.00  |
| 12                      | 1.38  | 35                      | 1.93  |
| 11                      | 1.36  | 30                      | 1.81  |
| 10                      | 1.35  | 25                      | 1.69  |
| 9                       | 1.34  | 22                      | 1.55  |
| 8                       | 1.32  | 21                      | 1.54  |
| 7                       | 1.29  | 20                      | 1.53  |
| 6                       | 1.27  | 19                      | 1.50  |
| 5                       | 1.25  | 18                      | 1.48  |
| 4                       | 1.23  | 17                      | 1.46  |
| 3                       | 1.03  | 16                      | 1.44  |
| 2                       | 1.02  | 15                      | 1.42  |
| 1                       | 1.00  | 14                      | 1.41  |

<h3 style="text-align:center; font-weight: bold">Evaluating trend and carry</h3>
Now that we have a combined forecast with the correct scale, it's just a matter of applying the usual procedure for capping, position sizing calculation and buffering.

Carver notes, it is a little weird that the SR for an individual instrument is lower for trend than for a long only benchmark, yet the aggregate SR is much higher. Another way of looking at this is to consider the ratio between these two SRs, individual and aggregate, a Sharpe Ratio ratio (SRR). The SRR reflects the realized diversification benefits in risk adjusted returns from diversifying across multiple instruments. The combined strategy has a median SR a fraction below carry but an aggregate SR that is better than trend. If you were trading a single instrument, you face a stark choice between a better SR (carry) or a nicer skew (trend).

<h1 style="text-align:center; font-weight: bold">Strategy 12: Adjusted trend</h1>

Adjust the size of a forecast to reflect the likely probability of a sudden reversal.

<h2 style="font-weight: bold">Strategy 12:</h2>
<h3>A variation on any strategy that uses EWMAC trend filters. Adjust the trend forecast according to the probability of a reversal.</h3>

<hr>

<h3 style="text-align:center; font-weight: bold">Forecasted and Actual Risk Adjusted Returns</h3>

Remember from Part One that a forecast is an expected risk adjusted return. We know that these forecasts are broadly correct since they result in profitable strategies but there is a great deal we don't know. Carver noted that evidence in favor of using trend strength in a forecast to size positions was weeak, at least for the EWMAC64 and introduced forecast capping as a fait accompli.

Forecasting and capping imply that there is a linear relationship between trend strength and expected risk adjusted return but only up until the forecast cap kicks in.

The fastest two EWMAC rules we see a strong bounce back after a strong negative trend, without a similar effect for positive trends (the dead cat bounce). The opposite effect can be seen in volatility markets (after a strong positive trend in VIX, which would be associated with falling equity prices, vol tends to fall sharply).

But this only really applies to equities so we should be careful about applying asset class specific rules. They need to be broad and robust with lots of data to test.

<hr>

<h3 style="text-align:center; font-weight: bold">The role of volatility</h3>

The issue with particularly large forecasts is that they're generally less effective at predicting than small forecasts.

Why is this? Remember a trend forecast is:

_the difference between two smoothed prices divided by the standard deviation of price changes_

There are two possible causes for this outsized forecast:
1. Prices have changed a lot: a strong trend
2. Recent volatility has been especially low

<hr>

<h3 style="text-align:center; font-weight: bold">Adjusting trend forecasts for trend strength</h3>

As a general rule, avoid making adjustments too complex or you risk overfitting. We also want to avoid using asset class specific effects as there isn't enough statisticcal significance to get robust estimates for the required adjustments. Because different instruments have different behavior in selloffs and rallies, any adjustment that is applied globally to all instruments ought to be symmetrical.

Carver suggests this approach:
- For EWMAC2, use a "double V" forecast mapping
- For EWMAC4, "scale and cap" the forecast at +15 instead of +20
- For EWMAC64, "scale and cap" the forecast at +15 instead of +20
- For all other filters, keep the forecast unchanged

The "double V" mapping works as follows, and replaces the normal forecast capping stage. Taking the original scaled forecast for the EWMAC2 trend filter, F:

$`F < -20: \text{Capped forecast} = 0 `$ \
$`-20 < F < -10: \text{Capped forecast} = -40 - (2 \times F)`$ \
$`-10 < F < +10: \text{Capped forecast} = 2 \times F`$ \
$`+10 < F < +20: \text{Capped forecast} = +40 - (2 \times F)`$ \
$`F > +20: \text{Capped forecast} = 0`$

Extreme forecasts are reduced. The downside of doubling these modest forecasts is that it increases trading costs in order to meet the average absolute forecast value of 10.

The "scaled and cap" mapping also replaces the normal forecast capping stage and prevents us from increasing our froecast once it reaches an absolute value of +15. The correct multiplier here is 1.25. Taking the original scaled forecast for the EWMAC4 or EWMAC64 trend filter, F:

$`F < -15: \text{Capped forecast} = -15 \times 1.25 = -18.75 `$ \
$`-15 < F < +15: \text{Capped forecast} = 1.25 \times F`$ \
$`F > +15: \text{Capped forecast} = +18.75`$

<h3 style="text-align:center; font-weight: bold">Evaluating the adjusted forecasts</h3>
Very small impact, Carver, himself, wouldn't trade it but hard to justify the increased complexity.

<hr>

<h1 style="text-align:center; font-weight: bold">Strategy 13: Trend followign and carry in different risk regimes</h1>

Different levels of volatility affect trading strategies in different ways. We try to scale our positions according to our current estimate of risk. Beyond that, you would expect that trend following strategies would like markets to move, whilst carry strategies should prefer stability. 

But there is a big difference between a steadily rising market, such as the 2017 S&P 500, and a market that is veering sharply from one extreme to another. The latter will usually be highly unprofitable for trend style trading, whilst the former is a dream come true.

<h2 style="font-weight: bold">Strategy 13:</h2>
<h3>A variation on any strategy that trades EWMAC and carry where we adjust the strength of the forecast according to the volatility regime</h3>

<h3 style="text-align:center; font-weight: bold">Defining the level of volatility</h3>

We must find some way of defining the current level of volatility for a given instrument and it must be backward looking measure or we won't be able to use it to improve our trading. And it must be a different measure for each instrument, as crisis can be idiosyncratic as well as global. Carver uses a relatively simple measure, which calculates relative volatility of an instrument compared to its long run average. Let $\sigma_{\%i,t}$ be the current estimated level of percentage standard deviation of returns for a given market $i$, measured using the method developed in strategy three. Then the relative level of volatility $V_{i,t}$ is the current estimate divided by the ten-year rolling average. Assuming 256 business days in a year that would be:

$`V_{i,t} \; = \; \LARGE{\frac{\sigma_{\%i,t}}{mean(\sigma_{\%i,t - 2560}, \; \sigma_{\%i,t - 2559}, \; ..., \; \sigma_{\%i,t})}}`$ 

Carver takes the distribution of relative volatility. He uses anything below 25 percentile as low volatility, above 75 percentile as high, anything in between is medium.

For him:

- Low Vol: V less than 0.77
- Medium Vol: V between 0.77 and 1.12
- High Vol: V more than 1.12

<h3 style="text-align:center; font-weight: bold">Defining the level of volatility</h3>

Performance is bad when moving from low volatility to high volatility. EWMAC rules are sure fire losers when volatility increases.

<h3 style="text-align:center; font-weight: bold">Adjusting forecasts for volatility regimes</h3>
We could stop trading when volatility hits the highest regimes but selling everything and buying again causes high trading costs.

We could just scale our position. This is the quantile point based on historical data for a given instrument:

$`Q_{i,t} \; = \; \text{Quantile of} \; V_{i,t} \; \text{in Distribution}(V_{i,0} \; ... \; V_{i,t})`$

This will vary between 0 (lowest value we've seen so far) and 1 (for the highest). 0.5 would indicate this is the median point in the historical distribution. We then calculate a vol multiplier, M:

$`M_{i,t} \; = \; EWMA_{span=10}(2 \; - \; 1.5 \; \times \; Q_{i,t})`$

If our volatility is especially low, with Q = 0.0 then we'd multiply our forecast by two, taking double the normal position. Conversely, if volatility is at historical highs, with Q = 1.0, we would halve our forecast. To reduce trading costs, apply a EWMA with a ten-day smooth.

$`\text{Raw EWMA(N) forecast}_{i,t} \; = \; \Large{\frac{(EWMA\_N_{i,t} \; - \; EWMA\_4N_{i,t})}{\sigma_{p,i,t}}}`$

$`\text{Adjusted raw EWMA(N) forecast}_{i,t} \; = \; \text{Raw forecast}_{N,i,t} \; \times \; M_{i,t}`$

Whereas for carry:

$`\text{Smoothed Carry(Span) Forecast}_{i,t} \; = \; EWMA_{span}(\text{Carry Forecast}_{i,t})`$

$`\text{Adjusted Smoothed Carry(span) forecast}_{i,t} \; = \; \text{Smoothed carry(span) forecast}_{i,t} \; \times \; M_{i,t}`$

# Formulas

## Legend
- $`^* \; — \; \text{annualized values} `$
- $`\% \; — \; \text{percent values}`$

## Definitions
### Assumptions:
- $`\text{Business days in a year} = 256 `$


### General:
- $`\text{Multiplier (Contract Unit) — dollar value of each point of price movement}`$

- $`\text{Tick Size (Minimum Price Fluctuation) — smallest unit price is quoted in}`$

- $`\text{Front Month — contract with soonest expiration}`$
<hr>

- $`\text{Notional Exposure per Contract (\$)} = \text{Multiplier (\$)} \; \times \; \text{Price}`$

- $`\text{Tick Value} = \text{Multiplier} \; \times \; \text{Tick Size}`$

### Costs:
- $`\text{Commission Cost — as determined by the exchange and broker}`$
<hr>

- $`\text{Spread Cost (Price Points)} = \text{Price Paid(Received)} \; - \; \text{Mid Price}`$

- $`\text{Spread Cost (Currency)} = \text{Multiplier} \times \text{Spread Cost (Price Points)}`$

- $`\text{Costs (in SR Terms)} = \Large{\frac{\text{Annual Cost}}{\text{Annualized Standard Deviation}}}`$

- $`\text{Total Cost per Trade (Currency)} = \text{Spread Cost (Currency) + Commission per Contract}`$

- $`\text{Total Cost per Trade (\%)} = \Large{\frac{\text{Total Cost per Trade (Currency)}}{\text{Price} \; \times \; \text{Multiplier}}}`$

- $`\text{Total Cost per Trade (\%)} \; = \; \text{Total Cost per Trade (\%)}`$

- $`\text{Risk Adjusted Cost per Trade}_\% = \Large{\frac{\text{Total Cost per Trade (\%)}}{\sigma_\%}}`$

- $`\text{Risk Adjusted Transaction Cost}, \; c_{i, \%} = \text{Risk Adjusted Cost per Trade} \; \times \; N; \; where \; N \; = \; \text{positions traded}`$

- $`\text{Risk Adjusted Transaction Cost (Annualized)}, \; c_{i, \%}^* \; = \; c_i \; \times \; \text{Turnover}`$

- $`\text{Risk Adjusted Holding Costs} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2`$

- $`\text{Annual Risk Adjusted Cost} \; = \; \text{Transaction Costs} \; + \; \text{Holding Costs}`$

- $`\text{Annual Risk Adjusted Cost} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; (\text{Rolls per Year} \; \times \; 2 \; + \; \text{Turnover})`$

### Returns:
<hr>

- $`\text{Total Return} = \text{Spot Return} \; + \; \text{Dividends}`$

- $`\text{Excess Returns} = \text{Total Return} \; + \; \text{Dividends} \; - \; \text{Interest}`$

- $`\text{Carry} = \text{Dividends} \; - \; \text{Interest}`$

- $`N_t \; \text{— number of contracts held at time} \; t`$

- $`\text{Return(in price points)}, \; R^{Points}_t \; = \; N_{t-1} \; \times \; (P_t - P_{t-1})`$

- $`\text{Return(in currency of future)}, \; R^{Instr}_t \; = \; R^{Points}_t \; \times \; \text{Multiplier}`$

- $`\text{Return(in base currency)}, \; R^{Base}_t \; = \; R^{Instr}_t \; \times \; \text{FX Rate}`$

- $`\text{Return(in \%)}, \; R^\%_t \; = \; \Large{\frac{100 \; \times \; R^{Base}_t}{\text{Capital}_{t-1}}}`$

- $`\text{Annualized Daily Returns} \; = \; 256 (\text{Business Days}) \; \times \; \overline{\text{Daily Return}}`$

- $`\text{Mean Return(returns} \;  r^\%_1 \; ... \; r^\%_T), \; r^* = \LARGE{\frac{r^\%_t}{T} \;  + \frac{r^\%_{t-1}}{T} \; + \; ... \; + \; \frac{r^\%_1}{T}}`$

- $`\text{Standard Deviation of \% Returns}, \; \LARGE{\sigma \; = \; \sqrt{\frac{(r^\%_T \; - \; r^*)^2}{T} \; + \; \frac{(r^\%_{T-1} \; - \; r^*)^2}{T} \; + \; ... \; + \; \frac{(r^\%_{1} \; - \; r^*)^2}{T}}}`$

- $`\text{Annualized Standard Deviation}, \; \sigma_{annual} \; = \; \sigma \; \times \sqrt{256}`$

### Risk Adjusted:
<hr>

- $`\text{Sharpe Ratio (Risk Adjusted Returns)}, \; SR \; = \; \LARGE{\frac{R^\%_t}{\sigma}}`$

- $`\text{Annualized Pre-Cost} \; SR, \; SR^* \; = \; SR \; \times \; \sqrt{256}`$

- $`\text{Instrument Annual SR}_i \; = \; SR^* - (T \times c_i); \; where \; T = \text{Turnover}, \; \; i`$

- $`\text{Instrument Annual Mean}_i \; = \; \tau \; \times \; [SR^* \; - \; (T \; \times \; c_i)]`$

- $`\text{Instrument}, \; i, \; \text{ Mean in Portfolio} \; = \; \text{Weight}_i \; \times \; IDM \; \times \; \tau \; \times \; [SR^* \; - \; (T \; \times \; c_i)]`$

- $`\text{Annual Portfolio Expected Return} \; = \; \sum_{i=1}^{n}(\text{Weight}_i \; \times \; IDM \; \tau \; \times \; [SR^* \; - \; (T \; \times \; c_i)]); \; where \; n \; = \; \text{instruments in portfolio}`$

- $`\text{Portfolio} \; \sigma \; = \; IDM \; \times \; \tau \; \times \; \sqrt{w \; \Sigma \; w'}; \; where \; w \; \text{is the vector of instrument weights}, \; \Sigma \; \text{is the correlation matrix of sub-strategy returns}`$

- $`\text{Portfolio SR} \; = \; \LARGE{\frac{\sum_{i=1}^{N}(\text{Weight}_i \; \times \; [SR^* - (T \; \times \; c_i)])}{\sqrt{w \; \Sigma \; w' \;}}}`$

### Tails:
<hr>

To compare returns to a Normal (Gaussian) Distribution

- $`\text{Lower Percentile Ratio (of \% returns)} \; = \; \Large{\frac{\text{1st Percentile}}{\text{30th Percentile}}}`$

- $`\text{Upper Percentile Ratio (of \% returns)} \; = \; \Large{\frac{\text{99th Percentile}}{\text{70th Percentile}}}`$

- $`\text{Reference Ratio} \; = \; \Large{\frac{\text{Inverse CDF(0.99)}}{\text{Inverse CDF(0.70)}}} \; \normalsize{=} \; \Large{\frac{\text{Inverse CDF(0.01)}}{\text{Inverse CDF(0.30)}}} \;\normalsize{\approx \; \Large{4.4395}}`$

- $`\text{Relative Lower Fat Tail Ratio} \; = \; \Large{\frac{\text{Lower Percentile Ratio}}{\text{Reference Ratio}}}`$

- $`\text{Relative Upper Fat Tail Ratio} \; = \; \Large{\frac{\text{Upper Percentile Ratio}}{\text{Reference Ratio}}}`$


### Exposure:
<hr>

- $`\text{Notional Exposure (Base Currency)} \; = \; \text{Multiplier} \; \times \; \text{Price} \; \times \; \text{FX Rate}`$

- $`\text{Risk of a Single Contract}, \; \sigma \; \text{(Contract, Base Currency)}\; = \; \text{Notional Exposure (Base Currency)} \; \times \; \sigma_\%`$

- $`\text{Position Risk for N Contracts}, \; \sigma\text{(Position, Base Currency)} \; = \; \sigma\text{(Contract, Base Currency)} \; \times \; N`$

### Risk:
<hr>

- $`\tau \; \text{— risk target (as standardized annual deviation)}`$

- $`\text{Risk Target in Currency}, \; \sigma \; \text{(Target, Base Currency)} \; = \; \text{Capital(Base)} \; \times \; \tau`$

- $`N = \Large{\frac{\text{Capital} \; \times \; \tau}{\text{Multiplier} \; \times \; \text{FX Rate} \; \times \; \sigma_\%}}`$

- $`\text{Optimal Risk Given Performance} \; = \; \Large{\frac{100 \; \times \; SR}{2}}`$


### Ratios:
<hr>

- $`\text{Contract Leverage} = \Large{\frac{\text{Notional Exposure per Contract}}{Capital}}`$

- $`\text{Volatility} \; = \; \Large{\frac{\tau}{\sigma_\%}}`$

- $`N = \Large{\frac{\text{Volatility Ratio}}{\text{Contract Leverage}}}`$

- $`\text{Leverage Ratio} \; = \; \Large{\frac{\text{Total Notional Exposure}}{\text{Capital}}} \; \normalsize{=} \; \Large{\frac{N \; \times \; \text{Notional Exposure per Contract}}{\text{Capital}}} \; \normalsize{=} \; N \; \times \; \text{Contract Leverage Ratio} \; = \; \text{Volatility Ratio}`$

### Rolling Averages:
<hr>

- $`\text{Moving Average of Returns (Window = N)}, \; r^*_t \; = \LARGE{\frac{r_t}{N} \; + \; \frac{r_{t-1}}{N} \; + \; ... \; + \; \frac{r_{t-N+1}}{N}}`$

- $`\sigma(N)_t \; = \; \Large{\sqrt{\frac{(r_t \; - \; r^*_t)^2}{N} \; + \; \frac{(r_{t-1} \; - \; r^*_t)^2}{N} \; + \; ... \; + \; \frac{(r_{t-N+1} \; - \; r^*_t)^2}{N}}}`$

#### NOTE: if calculating $`\sigma_\%`$, annualized % risk, use % returns for $`r_t`$ and multiply by 16
<hr>

- $`\text{EWMA Returns (of N returns)}, \; r^*(\alpha)_t = \alpha r_t \; + \; \alpha(1 - \alpha)r_{t-1} \; + \; \alpha(1 - \alpha)^2r_{t-2} \; + \; ...`$

- $`\text{EWMA Standard Deviation}, \; \sigma(\alpha)_t = \; \sqrt{\alpha(r_t \; - \; r^*_t)^2 + \alpha(1-\alpha)(r_{t-1} - r^*_t)^2 + \alpha(1-\alpha)^2(r_{t-2} - r^*_t)^2 \; + \; ...}`$

- $`\alpha = \Large{\frac{2}{N+1}}`$

### Trends:
<hr>

- $`\text{Moving Average Crossover}, \; MAC(n_1, n_2)\; = \; MA(n_2) \; - \; MA(n_1)`$ \
e.g. $`EWMAC(64, 256) \; = \; EWMA(64) \; - \; EWMA(256)`$

- $`\text{EWMAC}_n \; = \; \text{EWMAC}(n, \; 4n)`$

- $`=> N_i = \LARGE{\frac{\text{Capital} \; \times \; IDM \; \times \; \text{Weight}_{i,t} \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}(EWMAC \; > \; 0)`$

- $`\text{Trend} = \begin{cases}
 & \text{Long(+1) if } EWMAC > 0\\ 
 & \text{Short(-1) if } EWMAC < 0
\end{cases}`$

- $`=> N_{i,t} \; = \; \LARGE{\frac{\text{Trend}_t \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}`$

### Comparing Strategies:
To compare strategies and negate secular trends, take linear regression between two strategies
<hr>

- $`y_t \; = \; \alpha \; + \; \beta x_t \; + \; \epsilon_t; \; where \; \alpha \; \text{is the difference in strategies}, \; \beta \; \text{is the comovement of both strategies}, \; \epsilon \; \text{is the error}`$

### Forecasts:
<hr>

- $`\text{Raw Forecast} \; = \; \LARGE{\frac{\text{Fast EWMA} \; - \; \text{Slow EWMA}}{\sigma^*_p}} \; \normalsize where \; \sigma^*_p \; = \; \LARGE{\frac{\text{Price} \; \times \; \sigma^*_\%}{16}}`$

- $`\text{Scaled Forecast (Average Absolute Value of 10)} \; = \; \Large{\frac{\text{Raw Forecast} \; \times \; 10}{\text{Average Absolute Value of Raw Forecast}}}`$

- $`\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{\# filters}}_{j=1} (w_{i,j} \; \times \; f_{i,j,t})}`$

- $`\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{Trading Variations}}_{j = 1}\;(W_{i,j} \; \times \; F_{i,j,t})}`$

- $`\text{Scaled Combined Forecast}_{i,t} \; = \; \text{Raw Combined Forecast}_{i,t} \; \times \; FDM_j`$

- $`\text{Capped Combined Forecast}_{i,t} \; = \; \text{max(min(Scaled Combined Forecast}_{i,t}, \; +20), \; -20)`$

- $`N_{i,t} \; = \; \LARGE{\frac{\text{Capped Combined Forecast}_{i,t} \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{10 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}`$

- $`\text{Forecast Scalar} \; = \; \Large{\frac{10}{\text{Average Absolute Value of Raw Forecast}}}`$ \
$`\text{Carver approximates this to} \approx 1.9 \; \text{for EWMAC(16, 64)}`$

- $`N_i \; = \; \LARGE{\frac{\text{Scaled Forecast}_{i,t} \; \times \; \text{Capital} \; \times \; IDM \; \text{Weight}_i \; times \; \tau}{10 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}`$ \
Note: Since average value of Scaled Forecast = 10, we have to divide by 10 

- $`\text{Capped Forecast}_{i,t} \; = \; \max(\min(\text{Scaled Forecast}_{i,t}, \; +20), \; -20)`$ \
$`\text{range} \; = \; [-20, 20]`$

### Weighted Positions:
<hr>

- $`\text{Number of Positions in Instrument} \; i, \; N_{i,t} \; = \; \LARGE{\frac{\text{Capital} \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; \text{FX}_{i,t} \; \times \; \sigma_{\%,i,t}}}`$

- $`IDM = \Large{\frac{\text{Target Risk}}{\text{Realized Aggregate Risk}}} \normalsize{\; \text{where IDM is} \; [1, \; \infty)}`$

- $`N_i \; = \; \LARGE{\frac{\text{Capital} \; \times \; \text{IDM} \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Futures Multiplier}_i \; \times \; \text{Price}_i \; \times \; \text{FX}_i \; \times \; \sigma_{\%,i}}}`$

### Buffering:
- $`F \; — \; \text{fraction of average long position as a buffer (e.g. 0.10)}`$
<hr>

- $`B_{i,t} \; = \; \LARGE{\frac{F \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{\text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{i,t}}}`$

- $`\text{Lower Bound}, \; B^L_{i,t} \; = round(N_{i,t} \; - \; B_{i,t})`$

- $`\text{Upper Bound}, \; B^U_{i,t} \; = round(N_{i,t} \; + \; B_{i,t})`$

- $`\text{Current Position}, \; C_{i,t}`$

- $`Decision = \begin{cases}
 & B^U_{i,t} \; \leq \; C_{i,t} \; \leq \; B^L_{i,t} \; : \; \text{No Trading Required} \\ 
 & C_{i,t} \; < \; B^L_{i,t} \; : \; \text{Buy} \; (B^L_{i,t} \; - \; C_{i,t}) \;  \text {Contracts} \\ 
 & C_{i,t} \; > \; B^U_{i,t} \; : \; \text{Sell} \; (C_{i,t} \; - \; B^U_{i,t}) \;  \text {Contracts} 
\end{cases}`$


### Multipliers:
<hr>

- $`\text{Portfolio} \; \sigma \; = \; \sqrt{w \; \Sigma \; w' \;};`$ \
$`where \; w \; \text{is the vector of position weights}, \; \Sigma \; \text{is the covariance matrix of percent returns}`$

- $`w_{i,t} \; = \; \LARGE{\frac{N_{i,t} \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t}}{\text{Capital}}}`$

- $`99^{th} \; \text{percentile of portfolio} \; \sigma`$

- $`\text{Estimated Portfolio Risk Multiplier}, \; M_t(\text{Portfolio Risk}) \; = \; \Large{\text{min}(1, \; \frac{99^{th} \; \text{percentile of portfolio} \; \sigma}{\text{Portfolio} \; \sigma_t})}`$


#### Jump Portfolio:
1. Get annualized standard deviation for each instrument from percentage returns
2. $`\text{Calculate} \;  99^{th} \; \text{percentile from the distribution of standard deviations for each instrument.}`$

- $`\Sigma^{jump} \; — \; \text{covariance matrix of annualized standard deviations and correlation of percent returns}`$

- $`\text{Jump Portfolio} \; \sigma \; = \; \sqrt{w \; \Sigma^{jump} \; w' \;}`$

- $`\text{Jump Portfolio Risk Multiplier}, \; M_t(\text{Jump Portfolio}) \; = \; \Large{\text{min}(1, \; \frac{99^{th} \; \text{percentile of portfolio} \; \sigma}{\text{Jump Portfolio} \; \sigma_t})}`$

### Excess Return by Future Type:
- STIR — Short Term Interest Rates
<hr>

- $`\text{Excess Return} \; = \; \text{Spot Return} + \text{Carry}`$  

- $`\text{Excess Return(Equities) = Spot Return + Dividends - Interest}`$

- $`\text{Excess Return(Bonds) = Spot Return + Yield - Repo Rate}`$

- $`\text{Excess Return(FX) = Spot Return + Deposit Rate - Borrowing Rate}`$

- $`\text{Excess Return(STIR, Vol) = Spot Return + Current Spot Price - Futures Price}`$

- $`\text{Excess Return(Metals) = Spot Return - Borrowing Cost - Storage Costs}`$

- $`\text{Excess Return(Energy, Agricultural) = Spot Return - Borrowing Cost - Storage Costs + Convenience Yield}`$

#### Carry:

- $`\text{Raw Carry = Price of nearer futures contract - Price of Currently Held Contract}`$

- $`\text{Raw Carry = Price of Currently Held Contract - Price of Further Out Contract}`$

- $`\text{Expiry Difference in Years} \; = \; \Large{\frac{|\text{Months between Contracts}|}{12}}`$

- $`\text{Annualized Raw Carry} \; = \; \Large{\frac{\text{Raw Carry}}{\text{Expiry Difference in Years}}}`$

- $`\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}`$

- $`\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_\% \; \times \; \text{Current Contract Price}}}`$

#### Carry Forecasting:

- AMR — Adjusted Mean Return 

<hr>

- $`\text{Carry Forecast} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}`$

- $`\text{Smoothed Carry Forecast(Span) = EWMA}_{span}\text{(Carry Forecast)}`$

- $`\text{Scaled Carry Forecast(Span)} \; = \; \text{Smoothed Carry Forecast(Span)} \; \times \; \text{Forecast Scalar}`$

- $`AMR \; = \; \Large \frac{\text{Annual Return}}{\text{Target Risk}}`$
- $`\text{Capped Carry Forecast(Span)} \; = \; \text{max(min(Scaled Forecast(Span)}, \; +20 \;), \; -20)`$
- $`\text{Median Absolute Carry, MAC} = \text{Median}(\Large{\frac{\text{Average Scaled Forecast}}{\text{Forecast Scalar}}})`$

- $`\% \text{Carry Realized} = AMR / MAC`$. 

### Volatility:
- $`\text{Instrument Volatility}, \; V_{i,t} \; = \; \LARGE{\frac{\sigma_{\%i,t}}{mean(\sigma_{\%i,t - 2560}, \; \sigma_{\%i,t - 2559}, \; ..., \; \sigma_{\%i,t})}}`$ 

- $`\text{Quantile Point for Instrument} \; i, \; Q_{i,t} \; = \; \text{Quantile of} \; V_{i,t} \; \text{in Distribution}(V_{i,0} \; ... \; V_{i,t})`$

- $`\text{Volatility Multiplier}, \; M_{i,t} \; = \; EWMA_{span=10}(2 \; - \; 1.5 \; \times \; Q_{i,t})`$

#### Smoothed Volatility Forecast:
- $`\text{Raw EWMA(N) forecast}_{i,t} \; = \; \Large{\frac{(EWMA\_N_{i,t} \; - \; EWMA\_4N_{i,t})}{\sigma_{p,i,t}}}`$

- $`\text{Adjusted raw EWMA(N) forecast}_{i,t} \; = \; \text{Raw forecast}_{N,i,t} \; \times \; M_{i,t}`$

#### Whereas for carry:

- $`\text{Smoothed Carry(Span) Forecast}_{i,t} \; = \; EWMA_{span}(\text{Carry Forecast}_{i,t})`$

- $`\text{Adjusted Smoothed Carry(span) forecast}_{i,t} \; = \; \text{Smoothed carry(span) forecast}_{i,t} \; \times \; M_{i,t}`$
