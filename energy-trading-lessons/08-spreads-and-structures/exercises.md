# Module 08 — Exercises

## Exercise 1: Calendar Spread Deep Dive
- [ ] Pull 5 years of WTI 1st-2nd month spreads
- [ ] Create a seasonal overlay chart of the spread
- [ ] Is there a reliable seasonal pattern in the prompt spread?
- [ ] Calculate the correlation between the prompt spread and Cushing inventories

## Exercise 2: Build a Crack Spread Monitor
- [ ] Pull daily WTI, RBOB, ULSD prices and compute: 1:1 gas crack, 1:1 diesel crack, 3:2:1 crack
- [ ] Plot all three over 3 years
- [ ] Which crack is currently most expensive relative to its historical range?
- [ ] Add refinery utilization as an overlay — does it predict crack spread direction?

## Exercise 3: Spark Spread Calculation
- [ ] Get daily PJM Western Hub power prices and Henry Hub gas prices
- [ ] Calculate the spark spread assuming heat rates of 7, 8, 10 MMBtu/MWh
- [ ] Which heat rate generator was "in the money" most often?
- [ ] Plot the 10 HR spark spread — when is it positive and what drives it?

## Exercise 4: Nat Gas Basis Analysis
- [ ] Pull Henry Hub and 3 regional gas prices (SoCal Citygate, Chicago, Algonquin)
- [ ] Calculate and plot each basis differential for the past 2 years
- [ ] Identify the most volatile basis. Research the pipeline infrastructure that drives it
- [ ] For each hub, what is the seasonal pattern? Why does it exist?

## Exercise 5: Trade Idea Framework
- [ ] Pick any spread from this module
- [ ] Write a 1-page trade recommendation covering:
  - The spread and current level
  - Your fundamental thesis (why it should move)
  - Historical context (where is it vs. 5-year range?)
  - Catalysts (upcoming data, events, or seasonal factors)
  - Risk factors (what could go wrong?)
  - Entry, target, and stop-loss levels
- [ ] This is the format you'd use to pitch a trade idea at a fund

## Exercise 6: Butterfly/Fly Construction
- [ ] Pull WTI calendar spread data for Jun/Jul/Aug for 3 years
- [ ] Construct the butterfly: (Jun - Jul) - (Jul - Aug) = Jun - 2*Jul + Aug
- [ ] Plot the fly over time. What drives it?
- [ ] Is the fly mean-reverting? Calculate the half-life of mean reversion.
