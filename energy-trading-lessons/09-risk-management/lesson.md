# Module 09 — Risk Management

---

## Why Energy Risk Is Different

Risk management in energy is not an afterthought — it is the difference between a career and a blowup. Energy markets have characteristics that make them more dangerous than equities or rates:

**Fat tails**: Energy returns have kurtosis of 5-15 (vs. ~3 for a normal distribution). A 5-sigma event in equities is once-in-a-lifetime. In energy, 5-sigma events happen every 2-3 years: negative WTI (2020), $200 TTF gas (2022), $9,000/MWh ERCOT (2021), WTI $147 to $32 (2008). Your risk framework must assume that the worst thing you can imagine will eventually happen.

**Gap risk**: Prices can gap overnight on OPEC decisions, geopolitical events, or weather shifts. A stop loss at $78 is meaningless if WTI opens at $72 after an OPEC surprise. Gaps are more frequent in energy than in deeply liquid equity index futures.

**Correlation instability**: WTI and Brent are 95% correlated in normal markets. During the April 2020 WTI negative event, the correlation dropped to <50% because the stress was specific to WTI's delivery mechanism. A "hedged" WTI-Brent book could have lost on both legs simultaneously. Spread traders live and die by correlation stability.

**Structural leverage**: Futures require only 5-10% margin, creating 10-20x implicit leverage. A $6,000 margin on one WTI contract controls $80,000 of crude. A 7.5% adverse move wipes the margin entirely.

**Blowup history**:
| Entity | Loss | Year | What Happened |
|--------|------|------|---------------|
| Amaranth Advisors | $6.6 billion | 2006 | Concentrated natural gas calendar spreads |
| MF Global | $1.6 billion (client funds) | 2011 | European sovereign debt bets on repo, misuse of client segregated funds |
| China Aviation Oil | $550 million | 2004 | Short call options on jet fuel, margin calls, CEO jailed |
| Metallgesellschaft | $1.3 billion | 1993 | Stack-and-roll hedge on long-term oil contracts, cash flow mismatch |
| MotherRock Energy | $300 million | 2006 | Natural gas options, short vol into a volatile market |
| Texas power traders | Billions (aggregate) | 2021 (Uri) | Short power exposure during Winter Storm Uri, $9,000/MWh for days |

## Position Sizing

### Volatility-Based Sizing

The most common approach at professional shops. Size the position so that a normal day's adverse move costs a tolerable amount.

```
Position size = Target daily risk ($) / (Daily $ vol per contract)

Daily $ vol per contract = Daily price volatility x Contract multiplier

Example — WTI:
Target daily risk: $100,000
WTI 20-day realized vol: 2.0% annualized → daily vol = 2.0% x $80 / √252 = $1.01/bbl
But more practically: WTI daily range averages ~$1.50/bbl (1 std dev of daily changes)
Daily $ vol per contract = $1.50 x 1,000 = $1,500
Position size = $100,000 / $1,500 = 67 contracts

Example — Henry Hub gas:
Target daily risk: $50,000
Gas daily vol: ~$0.08/MMBtu (1 std dev)
Daily $ vol per contract = $0.08 x 10,000 = $800
Position size = $50,000 / $800 = 62 contracts

Example — Calendar spread (WTI M1-M2):
Target daily risk: $30,000
Prompt spread daily vol: ~$0.15/bbl
Daily $ vol per spread = $0.15 x 1,000 = $150
Position size = $30,000 / $150 = 200 spreads
```

**Critical principle**: Size to the volatility, not to the conviction. A high-conviction trade with 2x normal size will blow you up when you are wrong at the worst time. The market does not care about your conviction.

### Adjusting for Volatility Regime

Vol regimes change. WTI daily vol in a quiet period might be $1.00/bbl. After an OPEC surprise, it could be $3.00/bbl for weeks. If you sized for $1.00 vol and the regime shifts to $3.00, your position is 3x too large.

```
Approach: Use a 20-day rolling volatility measure. Recalculate position sizes weekly.

Low vol (daily vol < $1.00/bbl): Size up. Take advantage of cheap risk.
Normal vol ($1.00-2.00): Standard sizing.
High vol ($2.00-3.50): Cut size 30-50%.
Crisis vol (>$3.50): Cut to half or less. Capital preservation mode.
```

### Correlation-Adjusted Sizing

If you are long the WTI-Brent spread AND long the WTI prompt spread, these positions are correlated (both benefit from WTI front-month strength). Your combined risk is higher than the sum of individual risks.

```
Portfolio VaR = √(VaR₁² + VaR₂² + 2 × ρ × VaR₁ × VaR₂)

Example:
Position A: WTI-Brent spread, daily VaR = $50K
Position B: WTI prompt spread, daily VaR = $30K
Correlation between A and B: ρ = 0.6

Portfolio VaR = √($50K² + $30K² + 2 × 0.6 × $50K × $30K)
            = √($2,500M + $900M + $1,800M)
            = √$5,200M = $72.1K

Without correlation adjustment: $50K + $30K = $80K (overstates if ρ < 1)
With full correlation (ρ = 1): $80K (worst case)
With zero correlation (ρ = 0): $58.3K (diversified)
```

Size each position knowing the combined portfolio risk. If the portfolio VaR exceeds your limit, cut the more marginal position.

## Value at Risk (VaR)

### Three Approaches

**Parametric VaR** (simplest):
```
VaR = Portfolio value × z-score × σ_daily × √(holding period)

Example: $10M WTI position, 95% confidence, 1-day, daily vol 2%
VaR = $10M × 1.65 × 0.02 × √1 = $330,000

"There is a 5% chance of losing more than $330K tomorrow."
```

**Problem**: Assumes returns are normally distributed. They are not. Energy returns have fat tails. Parametric VaR underestimates tail risk by 30-50%.

**Historical VaR** (better for energy):
```
1. Collect the last 500 daily P&L changes for the position
2. Sort from worst to best
3. 95% VaR = the 25th worst day (5% × 500)
4. 99% VaR = the 5th worst day

This captures the actual distribution including fat tails.
```

**Monte Carlo VaR** (most flexible):
```
1. Estimate the return distribution (mean, vol, skew, kurtosis) for each risk factor
2. Simulate 10,000+ scenarios using correlated random draws
3. Calculate portfolio P&L for each scenario
4. VaR = the 5th percentile of the P&L distribution
```

Monte Carlo can incorporate non-linear payoffs (options), time-varying volatility, and complex correlations. This is what most fund risk teams run.

### Expected Shortfall (CVaR) — Beyond VaR

VaR tells you the threshold. It does NOT tell you how bad it gets beyond the threshold. Expected Shortfall (also called CVaR or Conditional VaR) answers: **"Given that we are in the 5% tail, what is the average loss?"**

```
Example:
95% VaR = $500K
95% Expected Shortfall = $850K

Interpretation: On a normal bad day (one in 20), you lose $500K.
On a truly bad day (average of the worst 5%), you lose $850K.
```

Expected Shortfall is a better risk metric for energy because it captures the fat tails that VaR ignores. A portfolio with the same VaR but higher ES has more tail risk — which is exactly where energy blowups happen.

## Stress Testing

VaR works in normal markets. Stress tests are for crises — the events that actually kill firms.

### Historical Scenario Analysis

Run your current portfolio through each of these past events. Calculate the P&L and margin impact.

| Scenario | Duration | Crude | Gas | Products | Power | Key Dynamic |
|----------|----------|-------|-----|----------|-------|-------------|
| 2008 Financial Crisis | Jul-Dec 08 | WTI $147→$32 (-78%) | $13→$3 (-77%) | Cracks collapsed then spiked | Demand destruction | Correlated sell-off across all energy |
| 2014-16 OPEC Price War | Jun 14-Jan 16 | WTI $107→$26 (-76%) | Flat ($2-4) | Cracks held ($15-20) | Unaffected | Crude-specific stress, products decoupled |
| April 2020 COVID/Negative WTI | Mar-Apr 20 | WTI -$37.63 | HH $1.50 | Cracks collapsed | Demand destruction | Storage filled, delivery mechanism failed |
| Feb 2021 Winter Storm Uri | 5 days | WTI +$5 | HH $2.50→$23.50 | Flat | ERCOT $9,000/MWh | Gas-power nexus, regional not global |
| Mar 2022 Russia-Ukraine | 2 weeks | Brent $90→$130 | TTF €100→€220 | Diesel $60+ crack | EU power €300+ | Geopolitical supply shock |

**For each scenario, calculate**:
1. **P&L impact**: Reprice every position using the historical stress moves
2. **Margin calls**: Would your margin call exceed available cash? If yes, you'd be forced to liquidate at the worst time
3. **Correlation breakdown**: Which positions that were "hedged" would fail to hedge? (WTI-Brent during the WTI negative event, gas-power during Uri)
4. **Liquidity**: Could you actually exit? During April 2020, WTI front-month liquidity dried up. During Uri, gas basis points were untradeable. If you can't exit, your mark-to-market loss could be the actual loss.

### Hypothetical Stress Scenarios

Build forward-looking scenarios that haven't happened yet:

- **Strait of Hormuz closure**: Brent +$30-50, gas +$5-10, products +$20-30, tanker rates 5x. Duration: weeks to months.
- **US strategic petroleum reserve release (500M bbl)**: WTI -$15-20 over months. Front-end contango.
- **ERCOT summer blackout**: ERCOT power to $5,000+, gas basis spikes, rolling blackouts. Duration: days.
- **Global recession**: Crude -40%, gas -30%, cracks -50% initially then recovery. Duration: 6-12 months.

## The Greeks in Energy Context

### Delta Management

Net portfolio delta = your total directional crude exposure, expressed in barrels-equivalent. Sum the deltas from all positions: outright futures + spread legs + option deltas.

```
Portfolio:
Long 50 WTI = +50,000 bbl delta
Short 30 Brent = -30,000 bbl delta
Long 20 gasoline cracks (= short 20 CL) = -20,000 bbl crude delta
Long 10 WTI $85 calls (delta = 0.35) = +3,500 bbl delta

Net crude delta = +50,000 - 30,000 - 20,000 + 3,500 = +3,500 bbl
→ Roughly flat. A $1/bbl move in crude costs ~$3,500.
```

**Risk**: If you think you're hedged but your deltas are wrong, you have hidden directional exposure. Recalculate daily.

### Gamma Risk — Where Blowups Happen

Gamma is the rate of change of delta. It is highest for near-expiry, at-the-money options. Short gamma positions lose money on large moves in either direction and are the mechanism behind many energy blowups.

```
You sold 100 WTI $80 puts expiring in 3 days. WTI at $80.50.
Delta: ~-0.45 per contract → position delta: +45,000 bbl (you're long from the short puts)
Gamma: 0.08 per $1 move

WTI drops $2 to $78.50:
New delta: -0.45 - (0.08 × 2 × 100) = now you're short ~61,000 bbl equivalent
The puts are now ITM and you owe $2.00 × 100 × 1,000 = $200,000 in intrinsic value
Plus you need to adjust your hedge → buying 16,000 bbl of delta at worse prices

Short gamma near expiry in energy is a widow-maker. The speed of energy price moves
near binary events (EIA report, OPEC) can make gamma hedging impossible.
```

### Vega — Seasonal Opportunities

Energy implied volatility has strong seasonal patterns:
- **Winter gas IV**: 50-70% (high uncertainty about heating demand)
- **Summer gas IV**: 25-40% (more predictable demand)
- **Hurricane season crude IV**: Elevated June-November
- **OPEC meeting windows**: IV spikes 1-2 weeks ahead, crushes after

**Vega trade**: In April, buy Jan gas straddles (high vega) when winter IV is at its seasonal low. As October approaches and winter uncertainty increases, winter IV rises. Sell the straddle. You profited from the seasonal IV increase without needing the price to move.

## Correlation Risk — The #1 Killer of Spread Traders

### Why Correlations Break

Spread trading assumes that the two legs of the spread move together (high correlation). The spread P&L comes from the small divergence between them. But in crises, correlations break down:

**WTI vs. Brent (normal ρ ≈ 0.95)**:
- April 2020: WTI went negative while Brent stayed at $20+. The stress was specific to WTI's Cushing delivery point. A long WTI/short Brent spread lost $55+/bbl.
- A trader who sized the WTI-Brent spread assuming ρ = 0.95 (low spread vol) would have been ruined.

**Gas vs. Power (normal ρ ≈ 0.80-0.90)**:
- Winter Storm Uri: Gas spiked to $23 but power spiked to $9,000. A short power/long gas spark spread that was "hedged" lost $8,970/MWh because power moved 400x more than gas.

**Adjacent month futures (normal ρ ≈ 0.99)**:
- Calendar spread between March and April gas: normally moves $0.05-0.20/day. The Widowmaker can move $1.00+/day during winter weather shifts. ρ drops from 0.99 to 0.85.

### Managing Correlation Risk

1. **Use recent correlation, not long-term**: A 5-year correlation of 0.95 is meaningless if the last 3 months show 0.80. Use 60-day rolling correlations.
2. **Stress-test with low correlation**: Ask "what happens if ρ drops to 0.50?" Size so that a correlation breakdown doesn't exceed your max loss tolerance.
3. **Diversify correlation exposure**: Don't have all your risk in one correlation assumption. If you are long WTI-Brent AND long LLS-WTI AND long WTI M1-M2, all three depend on WTI front-month stability.
4. **Use options for tail protection**: Buy cheap OTM puts or calls as insurance against correlation breakdown. The cost of protection is small relative to the tail loss.

## Liquidity Risk

### How to Measure It

| Metric | What It Tells You | Where to Find It |
|--------|-------------------|-----------------|
| Bid-ask spread | Cost to enter/exit | Exchange data, broker screens |
| Average daily volume (ADV) | How much trades daily | CME, ICE data |
| Open interest | Total outstanding positions | Exchange data |
| Your position / ADV | Days to exit at normal volumes | Calculate yourself |
| Market depth (Level 2) | Orders sitting in the book | Exchange data feeds |

**Rules of thumb**:
- **Position / ADV < 5%**: Comfortable. Can exit in 1 day with minimal impact.
- **Position / ADV = 5-20%**: You are a significant participant. Exit will move the market. Plan 2-5 days.
- **Position / ADV > 20%**: You ARE the market. Amaranth territory. Don't get here.

### Liquidity Across the Energy Curve

| Product | Front Month ADV | 6-Month Out | 12-Month Out | 24-Month Out |
|---------|----------------|-------------|--------------|--------------|
| WTI (CL) | ~900K contracts | ~100K | ~30K | ~5K |
| Henry Hub (NG) | ~350K | ~80K | ~20K | ~3K |
| RBOB (RB) | ~100K | ~20K | ~5K | <1K |
| ULSD (HO) | ~100K | ~20K | ~5K | <1K |

Back-month liquidity drops 90-99% from front-month. This means:
- Wider bid-ask spreads (cost more to trade)
- More market impact (your order moves the price)
- Harder to exit in a crisis (no one to buy from you)

**Size back-month positions based on back-month liquidity, not front-month.**

## Risk Limits — The Professional Framework

| Limit Type | Typical Level | Purpose | Who Enforces |
|------------|--------------|---------|--------------|
| Daily P&L stop | -$X (e.g., -$1M) | Stop trading after a bad day | Auto-enforced by risk system |
| Weekly P&L stop | -$X (e.g., -$2M) | Prevent compounding daily losses | Risk team |
| Drawdown limit | -5% triggers review, -10% shutdown | Protect capital | CRO/Management |
| Position limit per product | Max lots per contract month | Prevent concentration | Risk team |
| VaR limit | Max daily VaR (e.g., $5M at 95%) | Portfolio-level risk cap | Risk team |
| Concentration limit | No single trade > 20-25% of VaR | Diversification mandate | Risk team/PM |
| Gross notional limit | Max total long + short notional | Prevent excess leverage | Risk team |
| Delta limit | Max net directional exposure | Control flat-price risk | PM + risk team |

### The Drawdown Trigger Mechanism

At multi-strategy funds, the drawdown trigger is the most consequential risk limit:

```
Peak NAV: $500M
-3% ($485M): PM gets a call from risk team. "What's going on? Do you need to reduce?"
-5% ($475M): Risk budget cut 25-50%. PM must reduce positions. On formal watch.
-7% ($465M): Risk budget cut 50-75%. Only defensive trades allowed.
-10% ($450M): Pod SHUT DOWN. All positions liquidated. PM may be terminated.
```

The survival game at a multi-strat is: **never hit -10%**. This means:
- Size so that a 3-sigma day costs <2% of capital
- Diversify across 15-30 uncorrelated positions
- Have exit plans for every position before entry
- Cut losers at predefined stops, don't "hope"

## The Amaranth Case Study — In Full

### The Setup

Amaranth Advisors was a $9.2 billion multi-strategy hedge fund. Trader Brian Hunter, age 32, ran the natural gas book from Calgary. In 2005, Hunter made $1 billion for the fund (mainly from Hurricane Katrina-related gas trades), earning a personal payout of ~$75 million.

### The Trade

Hunter was massively long winter natural gas calendar spreads:
- Long March 2007 and March 2008 gas futures
- Short April and summer 2007/2008 gas futures
- The trade: winter gas will be expensive relative to summer (curve will steepen)

The position was enormous: ~100,000 NYMEX contracts (~1 Tcf notional). This was **30-40% of total Henry Hub open interest for some months**. The market knew the position existed and who held it.

### The Collapse

In September 2006, three things went wrong simultaneously:

1. **Weather forecasts turned warm**: Mild winter forecasts reduced the winter premium → winter/summer spreads narrowed
2. **Natural gas production was rising**: Shale gas (early Haynesville/Barnett) was adding supply → long-term bearish for winter scarcity
3. **Amaranth tried to exit but couldn't**: Their position was so large relative to market liquidity that every attempt to sell pushed prices further against them. The market moved to extract maximum pain.

### The Numbers

- **September 1-6**: Lost ~$560 million as spreads narrowed
- **September 7-14**: Lost another ~$2 billion trying to exit
- **September 15-21**: Transferred remaining positions to JP Morgan and Citadel at fire-sale prices. Additional ~$3 billion loss.
- **Total loss**: ~$6.6 billion in 3 weeks
- **Fund's remaining NAV**: ~$3 billion (from $9.2B). Fund shut down within weeks.

### The Lessons (Burned Into Every Energy Risk Manager's Memory)

1. **Position size relative to market liquidity, not portfolio size**: Amaranth's position was 30-40% of open interest. If you need 5+ days to exit at full size, you are too big. Rule: your position should be <5% of ADV for comfortable exit.

2. **Calendar spreads are NOT low risk**: Low exchange margin tempted Amaranth into massive notional. Margin of ~$1,000 per spread × 100,000 spreads = $100M margin, but the spread moved $2-5/MMBtu × 100,000 × 10,000 = $2-5 BILLION loss.

3. **Concentrated positions create existential risk**: All of Amaranth's gas risk was in one trade structure (winter/summer calendar spreads). A diversified book of 20+ uncorrelated spread positions across crude, gas, products, and power would have limited the damage.

4. **Risk limits must be enforced**: Amaranth's risk team reportedly flagged the concentration but was overruled by the PM's profitability. When a trader is making $1 billion, it is hard to tell them to cut size. Risk teams must have authority to force reductions, independent of PM objections.

5. **Past success is the most dangerous input**: Hunter made $1B in 2005 from a similar trade (Katrina-driven gas spike). This confirmed his bias that winter gas always pays. He sized 2006 based on 2005's success. The market doesn't repeat.

## The Metallgesellschaft Case — Hedging Gone Wrong

In 1993, Metallgesellschaft AG's US subsidiary (MG Refining & Marketing) lost $1.3 billion on oil hedging:

**The trade**: MGRM sold long-term fixed-price oil contracts to customers (5-10 year delivery). To hedge, they bought rolling front-month futures (a "stack-and-roll" hedge). The idea: roll the long front-month position each month, maintaining the hedge.

**What went wrong**: Oil prices fell in 1993. The long futures hedge lost money immediately (mark-to-market losses). But the long-term fixed-price customer contracts gained in value — the customers were locked in at above-market prices. The problem: the gains were unrealized (delivered over 5-10 years), while the losses were immediate cash margin calls.

**The liquidity mismatch**: MGRM faced $900M+ in margin calls from exchange-traded futures losses. The parent company panicked and liquidated the entire position — crystallizing losses. Had they held and continued rolling, the hedge would have worked over the full contract life.

**Lesson**: Cash flow mismatch kills. A hedge can be economically correct but operationally fatal if you cannot fund the margin calls. Treasury and liquidity management are as important as the hedge itself.

## Practical Daily Risk Workflow

### Before Market Open (7:00 AM ET)
1. Review overnight moves in Brent, TTF, Asia session
2. Check any OPEC/geopolitical headlines
3. Calculate current portfolio VaR with updated prices
4. Verify all positions vs. yesterday's end-of-day report
5. Identify any position limits approaching breach

### During Market Hours
1. Monitor P&L real-time
2. On high-vol days, recalculate VaR mid-day
3. If daily P&L stop is approaching, prepare to cut positions
4. Log any trades and update position sheets

### End of Day (3:00-5:00 PM ET)
1. Reconcile all positions with exchange/prime broker
2. Calculate final daily P&L and attribution
3. Run end-of-day VaR and stress tests
4. Flag any limit breaches or near-breaches
5. Report to PM and risk team

### Weekly
1. Recalculate 60-day rolling correlations
2. Update position sizing based on current vol regime
3. Re-run full stress test suite with updated portfolio
4. Review any new risk factors (new OPEC dynamics, weather regime shift, etc.)

## Reading

- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 6 (Risk Management and Regulation). Covers position limits, CFTC regulation, and the COT report as a positioning indicator.
- <a class="source-link" data-source="oil101">Oil 101</a> — chapter 14 (OPEC and Geopolitics) for understanding the geopolitical tail risks that stress tests must account for.

Also recommended: **Against the Gods** by Peter Bernstein — a history of risk that changes how you think about tail events. **Amaranth case study papers** (Google Scholar: "Amaranth natural gas") — required reading on liquidity risk. **Energy Risk magazine** (energyrisk.com) for how professional risk teams operate.
