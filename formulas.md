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