# Module 09 — Exercises

## Exercise 1: Position Sizing
- [ ] Calculate the 30-day rolling daily volatility for WTI, Henry Hub, RBOB, and ULSD
- [ ] If your risk budget is $25,000/day, how many contracts of each can you trade?
- [ ] How does the position size change when vol doubles (e.g., during a crisis)?
- [ ] Build a position-sizing calculator in Python

## Exercise 2: VaR Calculation
- [ ] Pull 2 years of daily returns for a simple portfolio: long 10 WTI + short 5 Brent
- [ ] Calculate 95% and 99% 1-day VaR using: parametric, historical, and Monte Carlo methods
- [ ] How different are the three estimates? Which do you trust most for energy?
- [ ] Calculate Expected Shortfall (CVaR) at the 99% level

## Exercise 3: Stress Test Your Portfolio
- [ ] Create a hypothetical portfolio of 3-5 energy positions (e.g., long WTI/Brent, short gas calendar, long crack spread)
- [ ] Replay the following scenarios through your portfolio:
  - April 2020 (COVID oil collapse)
  - Feb 2021 (Winter Storm Uri)
  - Feb-Mar 2022 (Russia-Ukraine)
- [ ] What is the worst-case P&L? Would you survive each scenario?

## Exercise 4: Correlation Analysis
- [ ] Build a correlation matrix of daily returns for: WTI, Brent, Henry Hub, RBOB, ULSD, PJM power
- [ ] Calculate rolling 60-day correlations for WTI-Brent and WTI-RBOB
- [ ] Identify periods where correlations broke down — what was happening in the market?
- [ ] How should correlation instability affect your spread sizing?

## Exercise 5: Amaranth Deep Dive
- [ ] Research and write a 2-page case study on Amaranth Advisors' collapse
- [ ] Cover: the strategy, the position sizes, what went wrong, the timeline of losses
- [ ] What risk management rules were violated?
- [ ] Design a set of risk limits that would have prevented the blowup

## Exercise 6: Build a Risk Dashboard
- [ ] Using your portfolio from Exercise 3, build a risk dashboard that shows:
  - Portfolio VaR (daily, 10-day)
  - Net delta by commodity
  - Correlation matrix
  - P&L under 3 stress scenarios
  - Current position size vs. max allowed
- [ ] Update it as you add trade ideas from other modules
