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
