# Module 07 — Exercises

## Exercise 1: Environment and Data Pipeline Setup
- [ ] Set up a Python environment with the libraries listed in the lesson
- [ ] Get a free EIA API key from eia.gov
- [ ] Write a script that pulls daily WTI and Henry Hub prices from the EIA API
- [ ] Store the data in a pandas DataFrame and save it to a CSV
- [ ] Automate the script to update daily (cron job or scheduled task)

## Exercise 2: Seasonal Analysis
- [ ] Pull 10 years of Henry Hub front-month prices
- [ ] Create a seasonal overlay chart (each year in a different color on a Jan-Dec axis)
- [ ] Calculate the average monthly return for each calendar month
- [ ] Which month has the highest average return? The lowest? Is this statistically significant?

## Exercise 3: Storage Model
- [ ] Pull weekly EIA natural gas storage data (5+ years)
- [ ] Calculate the 5-year average storage level for each week of the year
- [ ] Plot current storage vs. 5-year average vs. 5-year range
- [ ] Build a simple linear regression: gas price ~ f(storage surplus/deficit, HDD forecast, production)
- [ ] What is the R-squared? Which variable has the most explanatory power?

## Exercise 4: Mean Reversion Strategy
- [ ] Calculate the WTI 1st-2nd month calendar spread daily for 5 years
- [ ] Compute a rolling z-score (60-day window)
- [ ] Build a simple strategy: go long when z-score < -2, short when z-score > +2, exit at z-score = 0
- [ ] Backtest this strategy. Calculate: total return, Sharpe ratio, max drawdown, win rate
- [ ] Does the strategy work? What are its weaknesses?

## Exercise 5: Crack Spread Analysis
- [ ] Pull WTI, RBOB, ULSD prices and calculate the 3:2:1 crack spread daily
- [ ] Plot the crack spread over time with a 20-day and 60-day moving average
- [ ] Calculate the correlation between the crack spread and refinery utilization
- [ ] Build a seasonal model of the crack spread — does it predict well out of sample?

## Exercise 6: EIA Report Surprise Model
- [ ] Collect the last 52 weeks of EIA crude inventory data: actual vs. consensus estimate
- [ ] Calculate the "surprise" (actual minus consensus) each week
- [ ] Track the 30-minute price move after each report
- [ ] Plot surprise vs. price move — is the relationship linear?
- [ ] Build a simple model: expected price move = f(surprise magnitude and direction)

## Exercise 7: Data Dashboard
- [ ] Build a Jupyter notebook or simple dashboard that displays:
  - Current prices: WTI, Brent, Henry Hub, RBOB, ULSD
  - Key spreads: WTI-Brent, 3:2:1 crack, gas calendar spread
  - Storage charts: crude and gas inventories vs. 5-year avg
  - Forward curves: WTI and Henry Hub
- [ ] Update it weekly as your go-to market overview tool
