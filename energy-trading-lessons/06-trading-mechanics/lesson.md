# Module 06 — Trading Mechanics

## Overview

Before you can trade, you need to understand the instruments and market microstructure. This module covers futures, options, swaps, and how energy markets actually function.

## Key Concepts

### 1. Futures Contracts

A futures contract is a standardized agreement to buy or sell a commodity at a set price on a future date.

**Key terms**:
- **Contract size**: WTI = 1,000 barrels, Henry Hub = 10,000 MMBtu
- **Tick size**: WTI = $0.01/bbl = $10 per contract per tick
- **Front month**: The nearest expiring contract (most liquid)
- **Expiry/Delivery**: Physical delivery (WTI) vs. cash settlement (Brent, gas)
- **Roll**: Closing a position in the expiring month and opening in the next

**Margin**:
- **Initial margin**: Deposit required to open a position (~5-10% of notional)
- **Maintenance margin**: Minimum balance. If your account falls below, you get a margin call.
- **Mark-to-market**: Positions are settled daily. Gains/losses flow through daily.

### 2. Forward Curve Terminology

```
Front month (prompt) → 2nd month → 3rd month → ... → back months (deferred)
```

- **Cal strip**: Average price of all 12 months in a calendar year (e.g., Cal26 WTI)
- **Prompt spread**: Front month minus 2nd month
- **Time spread / Calendar spread**: Any two different months
- **Fly (butterfly)**: Spread of spreads (e.g., long Jun, short 2x Jul, long Aug)

### 3. Options on Futures

Energy options are primarily American-style, exercisable into the underlying futures contract.

**Key concepts**:
- **Call**: Right to buy the future at the strike price
- **Put**: Right to sell the future at the strike price
- **Premium**: Price paid for the option
- **Implied volatility**: The market's expectation of future price movement
- **The Greeks**: Delta (directional exposure), gamma (rate of delta change), theta (time decay), vega (vol sensitivity)

**Energy-specific option features**:
- Skew: Energy tends to have positive skew (calls are more expensive than puts) because supply disruptions cause upside spikes
- Extreme tail risk: Energy options can have very fat tails
- Seasonal vol: Implied vol is higher for winter gas options than summer

### 4. Swaps (OTC)

- Bilateral agreements between two parties
- **Fixed-for-floating swap**: One party pays a fixed price, the other pays the floating (spot/index) price
- Very common in energy for hedging and speculation
- Cleared through ICE Clear or CME ClearPort
- Basis swaps, calendar swaps, crack spread swaps all trade OTC

### 5. Exchange vs. OTC Markets

| Feature | Exchange (Futures) | OTC (Swaps, Forwards) |
|---------|-------------------|----------------------|
| Standardized | Yes | Customizable |
| Transparency | Full price transparency | Bilateral, less transparent |
| Counterparty risk | Clearinghouse guarantees | Bilateral (unless cleared) |
| Liquidity | Deep in benchmarks | Can be thin in exotic points |
| Regulation | CFTC (US) | Dodd-Frank clearing mandates |

### 6. Order Types and Execution

- **Limit order**: Buy/sell at a specific price or better
- **Market order**: Execute immediately at best available price
- **Stop order**: Triggered when price reaches a level — used for risk management
- **ICE / CME Globex**: Electronic matching engines
- **Voice brokered**: Many OTC products still trade via brokers (phone/chat)
- **Algo/systematic execution**: Increasingly common at funds

### 7. Position Limits and Regulation

- **CFTC position limits**: Maximum positions in energy futures (spot month and all months)
- **Speculative position limits**: Different from hedger limits
- **Reportable positions**: Above a threshold, positions are reported to the CFTC
- **COT report**: Weekly aggregation of positions by category (commercial, non-commercial, etc.)

### 8. The Roll and Expiration

- Energy futures expire monthly (some have weekly options)
- WTI expiry: 3 business days before the 25th of the month prior to delivery
- At expiry, you must either close or take/make physical delivery
- **Roll yield**: Gain or loss from rolling a position. In contango, rolling longs costs money (sell low, buy high). In backwardation, rolling longs earns (sell high, buy low).

### 9. Contract Specifications to Memorize

| Contract | Size | Tick | Tick Value | Exchange |
|----------|------|------|------------|----------|
| WTI Crude | 1,000 bbl | $0.01 | $10 | NYMEX |
| Brent Crude | 1,000 bbl | $0.01 | $10 | ICE |
| Henry Hub Gas | 10,000 MMBtu | $0.001 | $10 | NYMEX |
| RBOB Gasoline | 42,000 gal | $0.0001 | $4.20 | NYMEX |
| ULSD | 42,000 gal | $0.0001 | $4.20 | NYMEX |

### 10. Practical Considerations

- **Liquidity**: Front months are liquid, back months can be illiquid. Bid-ask spreads widen as you go out the curve.
- **Slippage**: The cost of executing at a worse price than expected, especially in size.
- **Contract month codes**: F=Jan, G=Feb, H=Mar, J=Apr, K=May, M=Jun, N=Jul, Q=Aug, U=Sep, V=Oct, X=Nov, Z=Dec

## Reading List

1. CME Group contract specification pages (bookmark them)
2. "Options, Futures, and Other Derivatives" by John Hull — chapters on futures and energy
3. CME Group: "Introduction to Energy Futures and Options"
