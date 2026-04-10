# Module 05 — Exercises

## Exercise 1: Real-Time Price Monitoring
- [ ] Go to an ISO website (PJM, ERCOT, or CAISO) and find their real-time LMP map
- [ ] Monitor prices at different nodes for one day — note the range between cheapest and most expensive nodes
- [ ] What causes the price difference? (hint: look at congestion)

## Exercise 2: Spark Spread Calculation
- [ ] Pull daily PJM Western Hub day-ahead power prices and Henry Hub gas prices for the past year
- [ ] Calculate the implied heat rate (power price / gas price) for each day
- [ ] What is the average implied heat rate? What does that tell you about the marginal generator?
- [ ] On what days was the implied heat rate extremely high or low? What happened?

## Exercise 3: The Duck Curve
- [ ] Pull hourly CAISO prices for a sunny week and a cloudy week
- [ ] Plot the 24-hour price profile for each
- [ ] Identify the "duck curve" shape. How negative do midday prices get?
- [ ] If you owned a battery, what would your charge/discharge strategy be?

## Exercise 4: ERCOT Winter Storm Uri Case Study
- [ ] Research the February 2021 Texas power crisis
- [ ] What were the key causes (supply failures, demand surge, gas supply)?
- [ ] How high did prices go? For how long?
- [ ] What was the total financial impact? Who won and who lost?
- [ ] Write a 1-page analysis with trading lessons learned

## Exercise 5: Peak vs. Off-Peak Spread
- [ ] Pull hourly power prices for any ISO for the past year
- [ ] Define peak (7am-11pm weekdays) vs. off-peak
- [ ] Calculate the average peak-offpeak spread by month
- [ ] Is this spread seasonal? What drives the seasonality?

## Exercise 6: Congestion Analysis
- [ ] Pick two nodes in the same ISO that are geographically separated
- [ ] Pull daily LMPs for both nodes for 6 months
- [ ] Calculate the basis (Node A - Node B) daily
- [ ] When is congestion worst? Can you identify the constrained transmission path?
