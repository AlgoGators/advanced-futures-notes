<h1 style="text-align:center; font-weight: bold">Strategy 9: Multiple Trend Following Rules</h1>

We want to trade as many instruments as possible as they give us access to many different kinds of risk premia. This is seen in many instruments when their returns are relatively uncorrelated. We don't have to just diversify across instruments but we can diversify across strategies.

## __Strategy 9:__
### Trade a portfolio of one or more instruments, each with positions scaled for a variable risk estimate. Calculate a number of forecasts for different speeds of trend filter. Place a position based on the combined forecast.

<hr>

### Selecting a series of trend following filters
Anything shorter than EWMAC(4,16) would be too expensive for most instruments. Anything longer than EWMAC(64,256) becomes too correlated with a long only strategy.

- $\text{EWMAC}_n \; = \; \text{EWMAC}(n, \; 4n)$

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

### __Should we use a different measure of volatility for different trend speeds?__

Whilst we may be using incredibly short or long EWMA's for our forecasts, EWMA's from 10-50, 30-35 in particular, are best at predicting future volatility.

<hr>

### The performance of different trend filters
Historically EWMAC(16, 64) has been the most profitable. $\beta$ to the long strategy increases as the speed decreases. 

### Combining different forecasts
How do we combine these strategies, several options each at a different stage of the trade generation process:
1. Averaging the raw forecasts before any capping takes place
2. Averaging the capped forecasts
3. Averaging calculated positions, either before or after buffering
4. Trading each trend filter as a completely different system, netting off the trades generated
5. Compeltely separate systems, with no netting

Option 5 is a non-starter since it lacks the benefit of netting whilst also increasing trading costs. Carver believes averaging as soon as possible offers the greatest benefit (reduces calculations and simplifies the trading strategy); however, it is best to do averaging on capped rather than uncapped forecasts as it ensures we won't end up with a combined forecast that is temporarily dominated by a single trend filter just because it happens to have a very large forecast on a given day. 

It follows that the preferred method is to take a weighted average of capped forecasts from different trading rules (option 2). The weights used when calculating this average are forecast weights. Forecast weights will sum to 1 and none will be negative. Remember that all forecasts are consistently scaled to achieve an average absolute forecast value of 10.

For each trend filter _j_ traded, calculate a capped forecast at time _t_ using the equation below for a given instrument _i_:

$\text{Raw Forecast}_{i,j,t} \; = \; \Large{\frac{\text{Fast EWMA}_{i,j,t} - \text{Slow EWMA}_{i,j,t}}{\sigma_{p,i,t}}}$

Apply filter specific forecast scalar (from table above), and a cap of 20 on the absolute value of the scaled forecast:

$\text{Scaled Forecast}_{i,j,t} \; = \; \text{Raw Forecast}_{i,j,t} \; \times \; \text{Forecast Scalar}_j$

$\text{Capped Forecast}, \; f_{i,j,t} \; = \; \text{max(min(Scaled Forecast}_{i,j,t},\; +20), \; -20)$

Take a weighted average of capped forecasts, using forecast weights $w_{i,j}$ which sum to 1 for a given instrument:

$\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{\# filters}}_{j=1} (w_{i,j} \; \times \; f_{i,j,t})}$

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

$\text{Annual Risk Adjusted Costs} \; = \; \text{Transaction Costs} \; + \; \text{Holding Costs}$

This can be broken down further:

$\text{Risk Adjusted Transaction Costs} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Annual Turnover}$

$\text{Risk Adjusted Holding Costs} \; = \; \text{Risk Adjusted Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2$

We can have a higher max trading cost for trading rules since:

1. If our most expensive trading rule incurs exactly 0.10 SR units in costs for a given instrument, then on average the combined forecast will always be well under 0.10 SR units
2. The effect of buffering our positions will slow down trading and allow us to trade a set of forecasts that is a little quicker. 

Because of these two effects, Carver uses a higher limit of 0.15 SR units for trading rules.

For a given instrument if the max annual risk adjusted costs is 15, the maximum allowable turnover can be derived for a given trading rule variation:

$\text{Annual Risk Adjusted Costs} \; < \; 0.15$

$\text{(Cost per Trade} \; \times \; \text{Turnover}) \; + \; \text{(Cost per Trade} \; \times \; \text{Rolles per Year} \; \times \; 2) \; < \; 0.15$

$\text{Turnover} \; < \; \Large{\frac{0.15 \; - \; (\text{Cost per Trade} \; \times \; \text{Rolls per Year} \; \times \; 2)}{\text{Cost per Trade}}} $


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

$\text{Raw Combined Forecast}_{i,t} \; = \; \Large{\sum^{\text{Trading Variations}}_{j = 1}\;(W_{i,j} \; \times \; F_{i,j,t})}$

$\text{Scaled Combined Forecast}_{i,t} \; = \; \text{Raw Combined Forecast}_{i,t} \; \times \; FDM_j$

$\text{Capped Combined Forecast}_{i,t} \; = \; \text{max(min(Scaled Combined Forecast}_{i,t}, \; +20), \; -20)$

$N_{i,t} \; = \; \LARGE{\frac{\text{Capped Combined Forecast}_{i,t} \; \times \; \text{Capital} \; \times \; IDM \; \times \; \text{Weight}_i \; \times \; \tau}{10 \; \times \; \text{Multiplier}_i \; \times \; \text{Price}_{i,t} \; \times \; FX_{i,t} \; \times \; \sigma_{\%i,t}}}$

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

$\text{Excess Return} \; = \; \text{Spot Return} \; + \; \text{Carry}$

For example, the S&P 500 carry is equal to the dividends we'd earn less the interest required to fund a loan used for buying all the stocks in the S&P 500 index. 

In fact, __all futures have carry__, although the source of this return differs depending on the asset class.

The back-adjusted price is effectively the cumulated history of past excess returns, so it incorporates the effects of both spot returns and carry; however, carry can be predicted independently, and very successfully.

Carry is a well-known risk premium that is quite different from the trend premium. Carry is also potentially hazardous without the nice positive skew we've grown accustomed to. Should be used with care, or better yet combined with trend following.

<h2 style="font-weight: bold">Strategy 10:</h2>
<h3>Trade a portfolio of one or more instruments, each with positions scaled for a variable risk estimate. Scale positions according to the strength of their forecasted carry</h3>

<hr>

<h3 style="text-align:center">The causes of carry</h3>

These carry returns come from different sources, depending on the asset class of the instrument you trade. We can decompose these returns by thinking about an arbitrage trade that will replicate a long position in the future. For the equities, the arbitrage trade is to borrow funds to buy the shares that make up the index, giving us this excess return:

$\text{Excess Return(Equities) = Spot Return + Dividends - Interest}$

$\text{Carry(Equities) = Dividends - Interest}$

Hence, carry for equities can be positive or negative depending on the relative size of dividend yields and interest rates.

Consider bonds:

$\text{Excess Return(Bonds) = Spot Return + Yield - Repo Rate}$

$\text{Carry(Bonds) = Yield - Repo Rate}$

Since the repo rate is often lower than the yield, carry in bonds is normally positive. An exception being when the central bank sets short-term interest rates at a high level which is expected to fall in the future, resulting in an inverted yield curve.

Consider in foreign exchange (FX) markets where there are two different interest rates:

$\text{Excess Return(FX) = Spot Return + Deposit Rate - Borrowing Rate}$

$\text{Carry(FX) = Deposit Rate - Borrowing Rate}$

Consider for example a long GBPUSD trade, which is equivalent to borrowing USD, converting them into pounds, and then depositing the pounds. The deposit rate would be the appropriate interest rate in the UK, and the borrowing rate would be the US interest rate. G10 FX markets typically have similar interest rates so their carry is negligible whereas emerging market currencies normally have significant positive carry against the dollar. 

Short Term Interest Rates and Volatility cary is more complex and worth reading later but the formula is:

$\text{Excess Return(STIR, Vol) = Spot Return + Current Spot Price - Futures Price}$

$\text{Carry(STIR, Vol) = Current Spot Price - Futures Price}$

Consider metals which have no carry and are almost certainly negative:

$\text{Excess Return(Metals) = Spot Return - Borrowing Cost - Storage Costs}$

$\text{Carry(FX) = -(Borrowing Cost + Storage Costs)}$

Consider Energy and Agricultural Products:

$\text{Excess Return(Energy, Agricultural) = Spot Return - Borrowing Cost - Storage Costs + Convenience Yield}$

$\text{Carry(FX) = Convenience Yield - (Borrowing Cost + Storage Costs)}$

This convenience yield reflects the current market expectations about future supply and demand for the commodit which could be positive or negative. Commodities typically have a negative carry although positive carries possible for extended periods of time.

<h3 style="text-align:center">Carry: What can go wrong</h3>

Be wary of thinking carry is just free money. If you buy a future with an expected carry, the price may move against you, effectively cancelling out your return. _Spot Drag_ is when the price decreases more than the value of the carry becoming a loss whereas a price rise will add to the carry gains.

Carvers backtests find that a $1 carry will typically return $1.15. Assets which offer positive carry are only doing so because there are risks from holding them. Said asset might have a negative skew for example. Holding an emerging market FX future would have a positive carry due to the risk of sudden and drastic depreciation events. 

<h3 style="text-align:center">Measuring expected carry</h3>

Our expected carry can be measured by comparing the current price of the future and the spot. It's difficult to get spot prices for many assets, especially commodities. Spot and futures prices need to be synchronized in time to get an accurate estimate, which isn't always easy. Even if we can get spot prices, it's a hassle and potentially expensive to add another source of data.

However, this isn't a problem if we're holding futures that are further out on the curve. Theoretically the next previous expiration contract serves as the spot price of the further out contract. For example for the S&P 500 e-mini, expiring in December, March, June, and September, if December is the front month its price can be used to estimate the spot price for the March contract.

$\text{Raw Carry = Price of nearer futures contract - Price of Currently Held Contract}$

An advantage of this approach is both contracts are trading on the same exchange so if daily closing prices are used, the values will be synchronized.

This isn't much help for most financial futures, where we are typically limited to holding the front contract and there isn't a nearer contract we can use for comparison. We can get around this if we assume that the gradient of the futures curve is constant, then the expected carry on the contract we are holding will be equal to:

$\text{Raw Carry = Price of Currently Held Contract - Price of Further Out Contract}$

There will always need to be another future further out because without it, rolling would be impossible; however, the further out contract might not appear until a few days before expiry. Worst case scenario we have an accurate reading for carry a few times a year when each roll happens which is normally sufficient.

A couple of examples, its November 2021 and you're trading the S&P 500 December 2021 contract. Since this is the front contract, you don't have the option of calculating carry using a nearer delivery month and you're not collecting spot S&P 500 index prices. So you go to the further out March 2022 contract. The prices were 4578.50 and 4572.00 for December and March, respectively. Making the raw carry:

$\text{Raw Carry = Price of Currently Held Contract - Price of Further Out Contract}$

$\text{Raw Carry = 4578.50 - 4572.00 = 6.50}$

Now consider WTI Crude Oil future. Carver only trades the December delivery. Imagine you had already begun holding the December 2022 contract which is priced at 62.09. Obviously this isn't the front month — so you can use a nearer month in your calculation. Crude has monthly deliveries so the previous contract is November 2022, trading at 62.61:

$\text{Raw Carry = Price of nearer futures contract - Price of Currently Held Contract}$

$\text{Raw Carry = 62.61 - 62.09 = 0.52}$

<h3 style="text-align:center; font-style:italic">Annualization</h3>

This value of carry reflects what we can expect to earn between expiries. Some contracts trade quarterly, others monthly; and even some that roll usually two but sometimes three months apart. We must annualize to get a consistent estimate of carry.

$\text{Expiry Difference in Years} \; = \; \Large{\frac{|\text{Months between Contracts}|}{12}}$

$\text{Annualized Raw Carry} \; = \; \Large{\frac{\text{Raw Carry}}{\text{Expiry Difference in Years}}}$

<h3 style="text-align:center; font-style:italic">Risk Adjustment</h3>

Although the S&P 500 is expected to earn 26.0 price units of carry to the 6.24 for Crude Oil, so what? Since our annualized carry is in units of price, it makes sense to divide it by the annualized standard deviation of returns for the relevant instrument also in price units.

$\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}$

We may also use annualized standard deviation of returns in percentage terms with:

$\text{Carry} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_\% \; \times \; \text{Current Contract Price}}}$

After risk adjusting, the carry for Crude Oil, 0.358, is 10 times higher than the S&P 500, 0.035.

<h3 style="text-align:center">Carry as a Trading Strategy</h3>

This is where forecasting comes in. In strategy 7, Carver formally defined a forecast as a __value that is proportional to an expected risk adjusted return__ which implies forecasts are proportional to expected SRs. 

Since carry is defined as an expected annual return divided by an annualized standard deviation both in the same price units, __expected carry is equal to expected SR__. Hence, the carry calculation above naturally produces a forecast:

$\text{Carry Forecast} \; = \; \Large{\frac{\text{Annualized Raw Carry}}{\sigma_p \; \times \; 16}}$

Carver uses this in reference to a trading strategy that can deal with less than perfect data:

<p style="font-style:italic">Loose pants fit everyone — Perry Kaufman</p>. 

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

$\text{Smoothed Carry Forecast(Span) = EWMA}_{span}\text{(Carry Forecast)}$

Different spans may be appropriate for different instruments. Natural Gas and other instruments with correctly estimated seasonality would require quite a short span to adjust quickly to changes after each roll whereas a longer span would make sense for most other instruments.

Carver uses four different spans as his carry trading rule variations:

- 5 business days ~1 week
- 20 business days ~1 month
- 60 business days ~3 months
- 120 business days ~6 months

$\text{Scaled Carry Forecast(Span)} \; = \; \text{Smoothed Carry Forecast(Span)} \; \times \; \text{Forecast Scalar}$

Carver finds a forecast scalar of 30 is appropriate. Would need to measure the average absolute value across all of our different futures instruments with all available data history which in Carver's case came in around 0.33 so x30 would get an average value of 10.

$\text{Capped Carry Forecast(Span)} \; = \; \text{max(min(Scaled Forecast(Span)}, \; +20 \;), \; -20)$

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

The difference in standard deviation also implies that SRs may not be the most sensible metric to evaluate performance across asset classes. An alternative measure is adjusted mean return (AMR) which is also a Sharpe ratio but it's the annual return divided by the risk target of 20%, not the realized standard deviation we use for a standard SR calculation. Unlike the actual SR it will be smaller when forecasts are lower, and vice versa.

You can directly compare AMR to MAC since both are Sharpe Ratios (this is because the forecasts produced by this strategy are equal to their expected SRs, other strategies only produce forecasts proportional to their expected SRs). MAC is the Sharpe Ratio promised by carry and the AMR is the Sharpe Ratio delivered by carry. $\% Carry Realized = AMR / MAC$. %Carry Realized > 100% means more carry delivered than promised, and vice versa.

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

