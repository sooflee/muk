# Module 07 — Quantitative Skills

---

## Why Quant Skills Matter in Energy

Energy trading has moved decisively toward quantitative approaches. Every major energy hedge fund — Citadel, Millennium, Balyasny, Freepoint — requires analysts who can pull data, build models, and backtest trade ideas programmatically. The edge in energy is not just knowing fundamentals; it is knowing fundamentals *faster and more precisely* than the market by systematically processing data that others read manually.

Python is the standard. R, MATLAB, and Excel have niche uses, but Python dominates because it combines data manipulation (pandas), statistical modeling (statsmodels, scipy), machine learning (scikit-learn), and visualization (matplotlib, seaborn) in one ecosystem. Every code example in this module is Python.

## Data Sources — Your Raw Material

### Free Sources

| Source | Data Available | Access Method | Update Frequency | Trading Use |
|--------|---------------|---------------|-----------------|-------------|
| EIA API (v2) | US crude/gas/product production, inventories, imports/exports, refinery utilization, prices | REST API (free key at eia.gov/opendata) | Weekly (petroleum Wed, gas Thu), monthly (production, STEO) | Build S/D balances, estimate weekly reports, track production trends |
| FRED (St. Louis Fed) | WTI, Brent, Henry Hub spot/futures, crack spreads, economic indicators (GDP, PMI, CPI) | `fredapi` Python library | Daily (prices), monthly/quarterly (macro) | Macro overlay, demand proxies, long-run price history |
| Yahoo Finance | Futures prices (CL, NG, RB, HO), ETFs (USO, UNG), equities | `yfinance` library | Daily (15-min delayed) | Quick backtests, correlation analysis, screening |
| CME Group | Settlement prices, volume, open interest by contract month | CSV downloads at cmegroup.com | Daily | Open interest analysis, roll tracking, volume profiles |
| CFTC | Commitments of Traders (COT) — positions by category | Weekly CSV at cftc.gov | Tuesdays (published Friday) | Positioning extremes, crowded trade detection |
| NOAA | Weather data, HDD/CDD (heating/cooling degree days), forecasts | REST API, CSV downloads | Daily | Gas/power demand modeling, weather-to-price regressions |
| Baker Hughes | US rig count by basin, target (oil/gas), trajectory (horizontal/vertical/directional) | CSV at bakerhughes.com | Weekly (Friday 1pm ET) | Shale production forecasting, rig-to-production models |

### Professional Sources (Paid — Used at Funds)

| Source | Data | Cost Range | Why It Matters |
|--------|------|-----------|----------------|
| Bloomberg Terminal | Real-time prices, curves, news, analytics | $25K+/year | Industry standard. If your fund has one, learn BPIPE and BQL. |
| Refinitiv Eikon | Prices, shipping, fundamentals | $15K+/year | Strong on shipping data (vessel tracking). |
| Platts / Argus | Physical price assessments (cargoes, differentials, basis) | $5K-50K/year | The definitive physical market prices. Platts and Argus assess prices daily — these set physical settlement. |
| Kpler / Vortexa | Satellite-based cargo tracking, vessel movements, storage | $20K+/year | See exactly how much crude is on the water, where LNG cargoes go, floating storage. Near real-time physical flow data. |
| IIR Energy | Refinery turnaround schedules, unit outages | $10K+/year | Know when specific refinery units are offline. Essential for crack spread trading. |
| Genscape / Wood Mac | Pipeline flow monitors, storage tank readings (via infrared/satellite) | $10K-50K/year | Near real-time pipeline throughput and inventory data. Information edge for basis traders. |

### EIA API — Your First Data Pipeline

The EIA API v2 is the single most important free data source. Key series to pull:

```python
import requests
import pandas as pd

API_KEY = 'your_key_here'
BASE = 'https://api.eia.gov/v2'

def get_eia_series(series_id, start='2015-01-01'):
    """Pull a single EIA data series."""
    url = f'{BASE}/seriesid/{series_id}'
    params = {'api_key': API_KEY, 'start': start, 'frequency': 'weekly'}
    r = requests.get(url, params=params)
    data = r.json()['response']['data']
    df = pd.DataFrame(data)
    df['period'] = pd.to_datetime(df['period'])
    df = df.sort_values('period').set_index('period')
    df['value'] = pd.to_numeric(df['value'])
    return df['value']

# Key weekly petroleum series
crude_inventory = get_eia_series('PET.WCESTUS1.W')      # US commercial crude stocks
gasoline_inventory = get_eia_series('PET.WGTSTUS1.W')    # US gasoline stocks
distillate_inventory = get_eia_series('PET.WDISTUS1.W')  # US distillate stocks
crude_production = get_eia_series('PET.WCRFPUS2.W')      # US crude production
refinery_util = get_eia_series('PET.WPULEUS3.W')         # Refinery utilization %
cushing_inventory = get_eia_series('PET.WCRSTOK1.W')     # Cushing, OK stocks
```

**Critical EIA series for gas trading**:
```python
gas_storage = get_eia_series('NG.NW2_EPG0_SWO_R48_BCF.W')  # Lower 48 working gas
gas_production = get_eia_series('NG.N9010US2.M')             # Dry gas production (monthly)
lng_exports = get_eia_series('NG.N9133US2.M')                # LNG exports (monthly)
```

## Time Series Analysis for Energy

### Stationarity and Why It Matters

Most energy prices are **non-stationary** — they wander without a fixed mean. You cannot reliably apply mean-reversion strategies to raw prices. But **returns**, **spreads**, and **deviations from seasonal norms** are often stationary. This is why spread trading dominates energy: spreads mean-revert, flat prices do not.

**Testing stationarity**:
```python
from statsmodels.tsa.stattools import adfuller

# Raw price: likely non-stationary
result = adfuller(df['wti_price'].dropna())
print(f'WTI price ADF p-value: {result[1]:.4f}')  # Typically p > 0.05 → non-stationary

# Spread: likely stationary
result = adfuller(df['wti_brent_spread'].dropna())
print(f'WTI-Brent spread ADF p-value: {result[1]:.4f}')  # Often p < 0.05 → stationary
```

### Cointegration — The Foundation of Spread Trading

Two price series are **cointegrated** if their linear combination is stationary — they may wander individually, but they move together in the long run. This is the formal justification for pairs/spread trading.

```python
from statsmodels.tsa.stattools import coint

# Test if WTI and Brent are cointegrated
score, pvalue, _ = coint(df['wti'], df['brent'])
print(f'Cointegration p-value: {pvalue:.4f}')  # p < 0.05 → cointegrated

# Find the hedge ratio (how much Brent per unit of WTI)
import statsmodels.api as sm
model = sm.OLS(df['wti'], sm.add_constant(df['brent'])).fit()
hedge_ratio = model.params[1]
spread = df['wti'] - hedge_ratio * df['brent']  # This spread should be stationary
```

**Energy pairs that are typically cointegrated**: WTI-Brent, RBOB-ULSD, Henry Hub-regional basis hubs, adjacent month futures (same commodity). When cointegration breaks down temporarily, it may be a trading signal — or it may signal a structural regime change. Always check the fundamentals.

### Seasonality — The Strongest Edge in Energy

Energy has more predictable seasonality than any other asset class. Gas prices are higher in winter. Gasoline cracks widen in summer. Crude demand follows economic cycles but also has seasonal patterns (refinery maintenance in spring and fall).

**Seasonal decomposition**:
```python
from statsmodels.tsa.seasonal import STL

# Decompose gas price into trend + seasonal + residual
stl = STL(df['gas_price'], period=52)  # 52 weeks = annual cycle
result = stl.fit()
trend = result.trend
seasonal = result.seasonal
residual = result.resid

# The residual is what's left after removing trend and seasonality
# Large residuals = potential mispricing
```

**Seasonal overlay chart** — the most useful visual in energy analytics:
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(12, 6))
for year in range(2018, 2026):
    subset = df[df.index.year == year]
    ax.plot(subset.index.dayofyear, subset['gas_storage'],
            label=str(year), alpha=0.7)

# 5-year average
five_yr = df.groupby(df.index.dayofyear)['gas_storage'].mean()
ax.plot(five_yr.index, five_yr.values, 'k--', linewidth=2, label='5yr avg')
ax.set_xlabel('Day of Year')
ax.set_ylabel('Working Gas Storage (Bcf)')
ax.legend()
```

**Seasonal spread analysis** — where most energy fund alpha comes from:
```python
# Calculate summer/winter gas spread by year
# Summer strip: Apr-Oct avg, Winter strip: Nov-Mar avg
for year in range(2018, 2026):
    summer = df[(df.index.year == year) & (df.index.month.isin([4,5,6,7,8,9,10]))]['gas'].mean()
    winter = df[(df.index.year == year if m <= 3 else year+1) & 
                (df.index.month.isin([11,12,1,2,3]))]['gas'].mean()
    print(f'{year}: Summer ${summer:.2f}, Winter ${winter:.2f}, Spread ${winter-summer:.2f}')
```

### Volatility Analysis

**Realized volatility** — what actually happened:
```python
# Annualized realized vol from daily returns
df['log_return'] = np.log(df['wti'] / df['wti'].shift(1))
df['realized_vol_20d'] = df['log_return'].rolling(20).std() * np.sqrt(252)
# WTI typical range: 20-40% annualized. Above 40% = crisis. Below 20% = complacent.
```

**GARCH models** — volatility clustering is real in energy:
```python
from arch import arch_model

# Fit GARCH(1,1) to WTI returns
am = arch_model(df['log_return'].dropna() * 100, vol='Garch', p=1, q=1)
res = am.fit(disp='off')
df['garch_vol'] = res.conditional_volatility / 100 * np.sqrt(252)
```

Energy volatility clusters intensely around events (OPEC decisions, hurricanes, geopolitical crises) and seasonally (winter gas vol > summer gas vol, hurricane season crude vol).

## Building a Storage Model

A gas storage model is one of the first practical tools an energy analyst builds. The goal: estimate the EIA Thursday gas storage number before it is released, and profit from the difference between your estimate and consensus.

**Inputs**:
- **Weather** (HDD/CDD): heating and cooling degree days drive residential and power sector gas demand
- **Gas production**: EIA weekly proxy, supplemented by daily pipeline flow estimates
- **LNG feedgas**: how much gas is flowing to LNG export terminals (trackable via pipeline nominations)
- **Power burn**: gas consumed for electricity generation (function of power demand and gas price vs. coal)
- **Industrial demand**: relatively stable, estimated from seasonal patterns

```python
# Simplified weekly gas balance
def estimate_storage_change(week_data):
    """Estimate weekly gas storage injection/withdrawal in Bcf."""
    supply = (
        week_data['dry_production_bcfd'] * 7 +  # ~105 Bcf/d x 7
        week_data['lng_imports_bcfd'] * 7 +      # ~0 (negligible)
        week_data['canada_imports_bcfd'] * 7      # ~5-8 Bcf/d
    )
    demand = (
        week_data['residential_commercial_bcfd'] * 7 +  # HDD-driven
        week_data['power_burn_bcfd'] * 7 +               # CDD + price-driven
        week_data['industrial_bcfd'] * 7 +                # ~22 Bcf/d
        week_data['lng_exports_bcfd'] * 7 +               # ~12-14 Bcf/d
        week_data['mexico_exports_bcfd'] * 7              # ~6 Bcf/d
    )
    implied_storage_change = supply - demand  # Positive = injection, negative = withdrawal
    return implied_storage_change

# Compare your estimate to Bloomberg consensus
# If your model says +52 Bcf and consensus is +68 Bcf → you expect a bearish miss
# Position: short gas ahead of the report (or if you can't time it, build a track record first)
```

**The payoff**: A consistent 5-10 Bcf edge over consensus translates directly into a tradeable signal. At $0.03-0.05/MMBtu per 5 Bcf miss, on 100 contracts (1M MMBtu), that is $30,000-50,000 per correct call.

## Forward Curve Analysis

The forward curve is the most information-rich object in energy. Professional energy desks maintain real-time forward curve analytics.

```python
# Build a forward curve snapshot
# Assume you have settlement prices for each contract month
months = ['CLF27', 'CLG27', 'CLH27', 'CLJ27', 'CLK27', 'CLM27',
          'CLN27', 'CLQ27', 'CLU27', 'CLV27', 'CLX27', 'CLZ27']
prices = [78.50, 78.20, 77.85, 77.50, 77.10, 76.80,
          76.55, 76.30, 76.10, 75.90, 75.70, 75.50]

# Calendar spread = M1 - M2
prompt_spread = prices[0] - prices[1]  # $0.30 backwardation
print(f'Prompt spread: ${prompt_spread:.2f}')

# Cal strip = average of 12 months
cal_strip = np.mean(prices)
print(f'Cal27 strip: ${cal_strip:.2f}')

# Curve slope = M1 - M12
slope = prices[0] - prices[-1]
print(f'Curve slope (M1-M12): ${slope:.2f}')

# Track curve evolution over time — how the entire curve has shifted
# Plot today's curve vs. 1 week ago, 1 month ago, 3 months ago
```

**Curve shape metrics**:
```python
# Contango/backwardation z-score
df['prompt_spread'] = df['cl_m1'] - df['cl_m2']
df['ps_zscore'] = (
    (df['prompt_spread'] - df['prompt_spread'].rolling(120).mean()) /
    df['prompt_spread'].rolling(120).std()
)
# Z > +2: unusually strong backwardation — check for supply disruption or inventory tightness
# Z < -2: unusually deep contango — check for oversupply, Cushing builds, demand collapse
```

## Regression Modeling for Energy

Regression is the workhorse of energy analytics. The goal is to identify the fair value of a spread given observable fundamentals, and trade the residual when it diverges.

### Crack Spread Regression

```python
import statsmodels.api as sm

# Model: 3:2:1 crack = f(refinery utilization, gasoline deficit, distillate deficit, VIX)
X = df[['refinery_util', 'gasoline_deficit', 'distillate_deficit', 'vix']].dropna()
y = df['crack_321'].loc[X.index]
X = sm.add_constant(X)

model = sm.OLS(y, X).fit()
print(model.summary())

# Fair value vs. actual
df['crack_fair_value'] = model.predict(X)
df['crack_residual'] = y - df['crack_fair_value']

# Trade signal: residual > 1.5 std → crack is rich → sell crack
# Trade signal: residual < -1.5 std → crack is cheap → buy crack
df['crack_zscore'] = df['crack_residual'] / df['crack_residual'].std()
```

### Gas Price Regression

```python
# Henry Hub gas = f(storage deficit, HDD forecast, LNG feedgas, production)
X = df[['storage_deficit_bcf', 'hdd_forecast', 'lng_feedgas_bcfd', 'dry_production_bcfd']]
y = df['henry_hub']
X = sm.add_constant(X.dropna())
y = y.loc[X.index]

model = sm.OLS(y, X).fit()

# Key output: R² tells you how much of gas price variation fundamentals explain
# Typical R² for monthly gas: 0.50-0.70
# The unexplained 30-50% is sentiment, positioning, and short-term noise — that's where alpha hides
```

### Regression Pitfalls in Energy

- **Multicollinearity**: storage deficit and production are correlated → coefficients become unstable. Check VIF (variance inflation factor). Drop redundant variables.
- **Non-stationarity**: regressing one non-stationary series on another produces spurious results. Use spreads, changes, or cointegrated pairs.
- **Structural breaks**: the shale revolution, LNG export boom, and COVID each created regime changes. A model trained on 2010-2014 data may be useless for 2020+ data. Use rolling windows (2-3 year lookback).
- **Overfitting**: 5 explanatory variables for 60 monthly observations = overfit. Keep the ratio of observations to variables above 10:1. Prefer 2-4 variables max.

## Backtesting Energy Strategies

### Framework

```python
class EnergyBacktest:
    def __init__(self, data, lookback=60, transaction_cost=0.02):
        self.data = data
        self.lookback = lookback
        self.tc = transaction_cost  # $/bbl or $/MMBtu per round trip

    def generate_signals(self):
        """Z-score mean reversion on a spread."""
        spread = self.data['spread']
        signals = pd.Series(0, index=spread.index)

        for i in range(self.lookback, len(spread)):
            window = spread.iloc[i-self.lookback:i]
            z = (spread.iloc[i] - window.mean()) / window.std()

            if z < -1.5:
                signals.iloc[i] = 1    # Spread cheap → buy
            elif z > 1.5:
                signals.iloc[i] = -1   # Spread rich → sell
            else:
                signals.iloc[i] = signals.iloc[i-1]  # Hold

        return signals

    def run(self):
        signals = self.generate_signals()
        daily_returns = self.data['spread'].diff()

        # P&L = signal * next day's spread change - transaction cost on trades
        trades = signals.diff().abs()  # 1 when signal changes
        pnl = signals.shift(1) * daily_returns - trades * self.tc

        return {
            'total_pnl': pnl.sum(),
            'sharpe': pnl.mean() / pnl.std() * np.sqrt(252),
            'max_dd': (pnl.cumsum() - pnl.cumsum().cummax()).min(),
            'win_rate': (pnl[pnl != 0] > 0).mean(),
            'n_trades': int(trades.sum() / 2),
        }
```

### Avoiding Common Pitfalls

**Lookahead bias**: The deadliest mistake. If your signal uses today's close to trade today's close, your backtest is wrong. Always: `signal[t]` → `return[t+1]`.

**Survivorship bias**: Energy markets have structural breaks (negative WTI, $200+ TTF). If your data excludes these, your model looks better than reality.

**Transaction costs**: WTI front month bid-ask: ~$0.01/bbl (negligible). Back month: $0.05-0.20/bbl. OTC products: $0.10-0.50. Gas: $0.002-0.01/MMBtu. Cracks: $0.05-0.15 per leg. Include realistic costs per product.

**Overfitting**: If your backtest has a 4.0 Sharpe with 15 parameters, it is overfit. The best energy strategies use 2-4 parameters. A 1.2 Sharpe that is robust out-of-sample is worth 100x a 4.0 Sharpe that falls apart.

**Out-of-sample discipline**: Split data 60/20/20 (train/validate/test). Develop on training set, tune on validation set, run ONCE on test set. If your test-set Sharpe drops below 0.5x your training-set Sharpe, you are overfit.

## Statistical Measures for Evaluating Trades

| Metric | Formula | Good | Great | Notes |
|--------|---------|------|-------|-------|
| Sharpe Ratio | Ann. return / Ann. vol | >1.0 | >2.0 | The primary metric. Below 0.5 = not worth the risk. |
| Max Drawdown | Peak-to-trough loss | <15% | <8% | How much pain you endure. Determines if you survive to recover. |
| Calmar Ratio | Ann. return / Max DD | >1.0 | >2.0 | Return per unit of worst-case pain. Better than Sharpe for risk-adjusted evaluation. |
| Win Rate | % of trades profitable | >50% | >55% | High win rate + small avg win is worse than 45% win rate + large avg win. |
| Profit Factor | Gross profit / Gross loss | >1.3 | >2.0 | Below 1.0 = losing money. Simple sanity check. |
| Avg Win / Avg Loss | Mean win / Mean loss | >1.2 | >2.0 | Measures asymmetry. Cut losers fast, let winners run. |
| Sortino Ratio | Return / Downside vol | >1.5 | >3.0 | Only penalizes downside volatility. Better than Sharpe for skewed strategies. |

## Machine Learning in Energy Trading

### Where ML Works

**Weather post-processing**: Numerical weather prediction (NWP) models (GFS, ECMWF) have systematic biases. ML models (random forests, gradient boosting) trained on historical model-vs-actual errors can improve 7-14 day temperature forecasts by 0.5-1.5°F. In gas/power trading, a 1°F forecast improvement is worth millions annually.

**Load forecasting**: Predicting power demand 24-48 hours ahead using temperature forecasts, day-of-week, holidays, and economic variables. XGBoost and neural networks achieve <2% MAPE on day-ahead load. Critical for power trading desks.

**Anomaly detection**: Detecting unusual patterns in EIA data (e.g., a refinery outage implied by unexpected inventory build), pipeline flow data, or vessel tracking data. Isolation forests and autoencoders work well.

**NLP on news and reports**: Parsing EIA reports, OPEC communiques, earnings call transcripts for sentiment. BERT-based models can classify bullish/bearish signals from text faster than manual reading.

### Where ML Fails

**Flat price prediction**: Predicting whether WTI goes up or down tomorrow. The signal-to-noise ratio is too low. Random forests, LSTMs, and transformers all fail to consistently beat a coin flip on energy flat price direction. Academic papers claiming otherwise are overfit.

**Regime changes**: ML models trained on 2015-2019 data catastrophically fail during COVID, Uri, or Russia-Ukraine. Energy markets have genuine structural breaks that violate the stationarity assumption underlying all ML.

**Small sample sizes**: You get ~250 trading days per year, ~52 EIA reports. With 10 features, you have maybe 5:1 observation-to-feature ratio. This is statistically insufficient for complex models. Use simple models (linear, logistic) with 2-4 features.

**Start simple**: Linear regression → seasonal models → z-score mean reversion → gradient boosting → only then consider deep learning. Most profitable energy strategies at hedge funds are surprisingly simple quantitatively. The edge is in the data and the fundamental insight, not the algorithm.

## Visualization for Energy

### Essential Chart Types

**Forward curve evolution** — track how the entire curve shifts over time:
```python
fig, ax = plt.subplots(figsize=(12, 6))
for date in ['2026-01-15', '2026-02-15', '2026-03-15']:
    curve = get_curve(date)  # Your function to get curve by date
    ax.plot(curve.index, curve.values, label=date)
ax.set_xlabel('Contract Month')
ax.set_ylabel('Price ($/bbl)')
ax.legend()
```

**Storage trajectory with 5-year band** — the most important gas chart:
```python
# Plot current year storage vs. 5-year min/max band
ax.fill_between(doy, five_yr_min, five_yr_max, alpha=0.2, color='gray', label='5yr range')
ax.plot(doy, five_yr_avg, 'k--', label='5yr avg')
ax.plot(current_doy, current_storage, 'r-', linewidth=2, label='Current')
```

**Heatmap** — hourly power prices by month (essential for power trading):
```python
import seaborn as sns
pivot = df.pivot_table(values='price', index='hour', columns='month', aggfunc='mean')
sns.heatmap(pivot, cmap='YlOrRd', annot=True, fmt='.0f')
```

**Spread vs. fundamental driver scatter** — visual regression:
```python
ax.scatter(df['gasoline_deficit'], df['crack_321'], alpha=0.5)
ax.plot(x_fit, y_fit, 'r-', linewidth=2)  # Regression line
ax.set_xlabel('Gasoline Deficit vs. 5yr Avg (M bbl)')
ax.set_ylabel('3:2:1 Crack ($/bbl)')
```

## Putting It Together — Daily Workflow

A quantitative energy analyst's daily routine:

**Pre-market (6:00-7:30 AM ET)**:
1. Pull overnight price changes (Asia and European session)
2. Check weather model updates (GFS 00Z and 06Z runs)
3. Update storage and production trackers
4. Scan for news (OPEC, geopolitics, outages)

**Market hours (8:00 AM-2:30 PM ET)**:
1. On report days (Wed/Thu): run your storage/inventory model, compare to consensus, position
2. Monitor spread z-scores for new signals
3. Track real-time Cushing and pipeline flow data (if available)
4. Log trade ideas and market observations

**Post-market (3:00-5:00 PM ET)**:
1. Update all models with today's settlement prices
2. Refresh forward curve database
3. Calculate daily P&L attribution (which positions made/lost money and why)
4. Prepare overnight risk summary for PM

## Reading

- <a class="source-link" data-source="eia">EIA Today in Energy</a> — this is the data you will be pulling and analyzing programmatically. Familiarize yourself with what the EIA publishes so you know what to query via their API (eia.gov/opendata — free API key required).
- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 6 (Risk Management and Regulation), specifically the COT report discussion. The COT data is one of the first datasets you should learn to pull and analyze.

Also recommended: **Python for Data Analysis** by Wes McKinney (the creator of pandas). The one Python book you need. **Advances in Financial Machine Learning** by Marcos Lopez de Prado — covers backtesting pitfalls and strategy evaluation.
