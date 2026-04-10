# Module 05 — Power Markets (Electricity)

## Overview

Electricity is fundamentally different from other energy commodities: it cannot be economically stored at scale (yet). This creates unique pricing dynamics, extreme volatility, and some of the most complex trading in energy.

## Key Concepts

### 1. Why Power Is Different

- **No storage**: Electricity must be produced and consumed simultaneously (grid must balance in real-time)
- **Locational pricing**: Price varies by node/zone — transmission congestion creates price differences
- **Real-time markets**: Day-ahead and real-time markets clear every hour (or 5 minutes)
- **Extreme optionality**: Prices can spike from $30/MWh to $10,000/MWh in minutes during scarcity

### 2. US Power Market Structure (ISOs/RTOs)

The US grid is managed by Independent System Operators / Regional Transmission Organizations:

| ISO/RTO | Region | Key Features |
|---------|--------|--------------|
| PJM | Mid-Atlantic, Midwest | Largest US power market |
| ERCOT | Texas | Isolated grid, no capacity market, extreme volatility |
| CAISO | California | High renewables penetration, duck curve |
| MISO | Midwest, South | Large wind penetration |
| SPP | Central US | Wind-heavy |
| NYISO | New York | Congested, high prices |
| ISO-NE | New England | Gas-dependent, winter price spikes |

### 3. Locational Marginal Pricing (LMP)

LMP = the cost of serving one additional MWh of demand at a specific node. Composed of:

```
LMP = Energy Component + Congestion Component + Loss Component
```

- **Energy**: The marginal cost of generation (set by the most expensive unit needed to meet demand)
- **Congestion**: Price premium when transmission lines are at capacity
- **Losses**: Cost of energy lost during transmission

Nodal prices can vary dramatically across the grid at the same moment.

### 4. The Generation Stack (Merit Order)

Generators are dispatched in order of marginal cost:

```
Cheapest → Most Expensive:
1. Renewables (wind, solar) — ~$0 marginal cost
2. Nuclear — very low marginal cost, must-run
3. Coal — variable, depends on coal price
4. Natural Gas Combined Cycle (CCGT) — often the marginal unit
5. Natural Gas Peakers (combustion turbines) — high cost, run only during peaks
6. Oil — rarely used, emergency/peak only
```

The **marginal unit** (usually gas) sets the price for ALL generators. This is why gas prices drive power prices.

### 5. The Spark Spread

**Spark spread** = Power price - (Gas price × Heat rate)

- Heat rate: efficiency of converting gas to electricity (MMBtu/MWh). Typical: 7-10 MMBtu/MWh
- A gas plant's heat rate determines its breakeven: if the spark spread > 0 at its heat rate, it's profitable to run
- **Implied heat rate**: Power price / Gas price. Tells you the efficiency of the marginal generator.

### 6. The Dark Spread

**Dark spread** = Power price - (Coal price × Coal heat rate) - Carbon cost

Similar to spark spread but for coal plants. Increasingly irrelevant in the US but still matters globally.

### 7. Renewables and the Duck Curve

In high-renewables markets (especially CAISO):
- Solar floods the grid midday → prices collapse (can go negative)
- As the sun sets, demand ramps up and solar drops off → sharp evening ramp
- The load profile looks like a duck (belly at midday, neck in evening)
- This creates **ramping risk** and makes gas peakers more valuable for the evening hours

### 8. Capacity Markets vs. Energy-Only Markets

- **Capacity markets** (PJM, ISO-NE, NYISO): Pay generators to be available, even if not running. Ensures reliability.
- **Energy-only markets** (ERCOT): No capacity payments. Generators earn money only when producing. Prices can spike to $5,000-$9,000/MWh to incentivize investment. ERCOT is the "Wild West."

### 9. Key Power Trades

- **Spark spread trades**: Long power / short gas (or vice versa)
- **Congestion trades (FTRs/ARRs)**: Bet on transmission congestion between nodes
- **Peak vs. off-peak**: Buy cheap off-peak power, sell expensive on-peak
- **Calendar spreads**: Summer vs. winter, month-to-month
- **Basis trades**: One hub vs. another (e.g., PJM West Hub vs. NYISO Zone J)
- **Renewable capture rate**: What price do wind/solar actually receive vs. the average?
- **Virtual bidding**: Bid into day-ahead market, settle against real-time price

### 10. ERCOT — The Trader's Market

- Energy-only, no capacity market
- Extremely weather-sensitive (Texas heat + Texas cold)
- February 2021 Winter Storm Uri: prices hit $9,000/MWh for days
- Summer 2023: Extreme heat stress
- Battery storage is growing rapidly, changing peak pricing dynamics

## Reading List

1. "Fundamentals of Electricity Markets" — any ISO's introductory guide (PJM Learning Center is excellent)
2. EIA Electricity Data Browser
3. Monitor Analytics — PJM State of the Market reports
4. Potomac Economics — ERCOT and MISO market monitor reports
5. Follow @gridstatus on Twitter/X for real-time grid data
