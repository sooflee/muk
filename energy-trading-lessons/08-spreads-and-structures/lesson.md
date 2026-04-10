# Module 08 — Spreads & Structures

---

## Why Spreads Dominate Energy Trading

Most professional energy P&L comes from spread trading, not directional bets. At Citadel, Millennium, or Balyasny energy pods, the PM runs a book of 20-50 spread positions across crude, gas, products, and power. Flat price directional trades are rare and typically small relative to the relative value book.

**Why spreads are superior for professional trading**:

| | Outright (Flat Price) | Spread |
|---|---|---|
| Margin | WTI: ~$6,000/contract | WTI calendar: ~$1,000-2,000 |
| Daily P&L vol | $1,500/contract (WTI at $1.50/bbl daily vol) | $200-500/contract (spread daily vol $0.20-0.50) |
| Drivers | Macro, OPEC, geopolitics, sentiment, flows | Specific fundamentals: storage, refinery, weather, logistics |
| Edge source | Extremely hard to predict | Quantifiable with S/D models, seasonal patterns, physical knowledge |
| Sharpe ratio (typical) | 0.3-0.8 | 1.0-3.0 |
| Drawdown risk | Can lose 30%+ in weeks | Typically <10% unless concentrated |

The key insight: spreads **isolate** specific fundamental drivers by removing common factors. A crack spread doesn't care if crude rallies $5 on OPEC — it only moves if products rally more or less than crude. This makes the trade analyzable and modelable.

## Calendar Spreads (Time Spreads)

Buy one delivery month, sell another in the same commodity. You are trading the **shape of the forward curve**, not the price level.

### Prompt Spread (M1 - M2)

The most liquid and most important calendar spread. It directly reflects near-term supply/demand tightness.

**WTI prompt spread**:
- Typical range: -$2.00 (deep contango) to +$3.00 (strong backwardation)
- Driven by: Cushing inventory levels, EIA weekly report surprises, refinery demand, pipeline flow changes
- Deep contango (-$2+): Cushing >65M bbl, storage filling up, oversupply
- Strong backwardation (+$2+): Cushing <25M bbl, barrels scarce, drawdowns accelerating

**Henry Hub prompt spread**:
- Typical range: -$0.50 to +$1.00
- Driven by: weather (HDD/CDD), storage vs. 5-year average, production changes
- Tends to be in contango during injection season (surplus going into storage)
- Flips to backwardation during cold winter withdrawals

### Seasonal Spreads

**Winter/Summer gas** (e.g., Jan-Jul or the "Winter Strip - Summer Strip"):
- Winter premium typically $0.50-2.00/MMBtu
- Driven by: end-of-injection storage level, winter weather expectations, LNG export demand
- When October storage is projected low (<3.2 Tcf), winter premium expands
- When storage is abundant (>3.9 Tcf), winter premium compresses

```
Worked example — Winter/Summer gas spread:
Jan 2027 Henry Hub: $4.20/MMBtu
Jul 2027 Henry Hub: $3.30/MMBtu
Spread (Jan - Jul): $0.90

Historical range for this time of year: $0.50 - $1.80
Current storage: 3.1 Tcf (200 Bcf below 5yr avg)
Thesis: storage deficit will widen → winter premium should expand to $1.30+
Trade: Buy Jan / Sell Jul (long the winter/summer spread)
```

### The Widowmaker — Mar/Apr Gas

The most famous (and dangerous) calendar spread in energy. March is the last month of winter withdrawal season. April is the first month of injection season. The spread between them captures the transition from winter scarcity to spring surplus.

**Why "widowmaker"**:
- Range: historically -$0.20 to +$3.00, but can spike to $5.00+ in extreme cold
- The spread can move $0.50-1.00 in a single day on weather model shifts
- Amaranth ($6B loss in 2006) was killed by positions in winter gas calendar spreads including this one
- Low margin (~$500-1,000/spread) tempts traders to put on massive size, amplifying losses

**What drives it**:
- Late-winter weather: a February/March cold blast extends withdrawals → March prices spike → spread widens
- End-of-winter storage: if storage exits winter below 1.5 Tcf, March can trade at extreme premiums
- Injection season outlook: strong spring production growth narrows the spread as the market expects easy refill

### Butterfly (Fly)

Long Month A + Short 2x Month B + Long Month C. Trades the **curvature** of the forward curve between three adjacent months.

```
Butterfly example (WTI Jun-Jul-Aug):
Entry: Jun $80.00, Jul $79.50, Aug $79.20
Fly = (Jun - Jul) - (Jul - Aug) = $0.50 - $0.30 = $0.20

If Jun tightens relative to Jul more than Jul tightens vs. Aug:
Exit: Jun $80.80, Jul $79.80, Aug $79.40
Fly = ($80.80 - $79.80) - ($79.80 - $79.40) = $1.00 - $0.40 = $0.60
Profit = $0.60 - $0.20 = $0.40/bbl = $400 per 1-lot fly

Margin: ~$500-800 per fly (very capital efficient)
```

Butterflies are lower risk than outright calendar spreads because they cancel most directional and curve-level risk. They isolate very specific kinks in the curve — often caused by refinery turnarounds, seasonal transitions, or contract expiry dynamics.

## Crack Spreads (Refining Margins)

Crack spreads represent the refinery's gross margin: the difference between the value of refined products and the cost of crude oil input.

### Structure Deep Dive

**3:2:1 Crack** (industry standard):
- Buy 3 barrels crude → Sell 2 barrels gasoline + 1 barrel diesel
- Formula: (2 x RBOB $/bbl + 1 x ULSD $/bbl) / 3 - WTI $/bbl
- This approximates a simple US Gulf Coast refinery's product slate

**Execution on exchange**:
```
To put on a 3:2:1 crack (10 lots):
Buy 30 CL contracts (30,000 barrels crude)
Sell 20 RB contracts (20 x 42,000 gal = 840,000 gal = 20,000 bbl)
Sell 10 HO contracts (10 x 42,000 gal = 420,000 gal = 10,000 bbl)

Margin: ~$2,500-4,000 per "crack" (3 CL + 2 RB + 1 HO)
Compare: 3 outright CL would require ~$18,000 margin
```

### What Drives Crack Spreads

**Refinery utilization**: The single most important driver. US Gulf Coast refinery utilization typically runs 88-96%. During spring/fall turnarounds, utilization drops to 85-90%, reducing product supply and widening cracks. Unplanned outages widen cracks immediately.

**Seasonal patterns**:
- **Q1 (Jan-Mar)**: Turnaround season. Utilization drops. Cracks moderate. Heating oil demand supports ULSD crack.
- **Q2 (Apr-Jun)**: Post-turnaround restarts. Utilization rises to 93-96%. Driving season demand ramps. Gasoline cracks widen sharply. This is typically the strongest period for 3:2:1 cracks.
- **Q3 (Jul-Sep)**: Peak driving season. Gasoline demand peaks (9.5M+ bbl/d). 3:2:1 cracks at seasonal highs ($25-40/bbl). Hurricane risk can widen cracks further (refinery shutdowns on Gulf Coast).
- **Q4 (Oct-Dec)**: Driving season ends. Gasoline cracks narrow. Diesel/heating oil cracks strengthen (winter heating demand, export demand for European distillate).

**Inventory levels**: Gasoline inventories below the 5-year average = bullish gasoline cracks. Distillate inventories below average = bullish diesel cracks. The deficit relative to seasonal norms is the key metric, not the absolute level.

**Historical crack spread ranges (3:2:1, $/bbl)**:
| Environment | Range | Conditions |
|-------------|-------|------------|
| Depressed | $5-15 | Recession, high utilization, oversupply (2019-2020) |
| Normal | $15-25 | Balanced market, seasonal utilization patterns |
| Elevated | $25-40 | Low product inventories, turnarounds, strong demand |
| Extreme | $40-60+ | Post-COVID restocking (2022), severe refinery outages |

**The 2022 crack spike**: After Russia invaded Ukraine, the loss of ~1M bbl/d of Russian refined product exports (especially diesel to Europe) pushed the 3:2:1 above $50/bbl for weeks. ULSD cracks alone hit $70-80/bbl. Traders who were long cracks made generational returns. This was a structural supply shock, not a seasonal pattern.

### Gasoline vs. Diesel (RB-HO Spread)

The spread between gasoline and diesel cracks is itself a tradeable spread — it isolates which product is tighter.

```
RBOB-ULSD spread (in $/bbl):
RBOB at $2.50/gal = $105.00/bbl
ULSD at $2.80/gal = $117.60/bbl
Spread = $105.00 - $117.60 = -$12.60 (diesel at premium)

Seasonal pattern:
Spring/Summer: Gasoline cracks > Diesel cracks → spread narrows or flips positive
Fall/Winter: Diesel cracks > Gasoline cracks → spread widens negative
```

Trading this spread isolates the seasonal gasoline/diesel demand balance without crude price exposure.

## Spark Spreads (Power Generation Margin)

**Spark spread = Power price - (Gas price x Heat rate)**

The spark spread is the power generator's gross margin, analogous to the crack spread for refiners.

### Detailed Mechanics

```
PJM Western Hub on-peak power: $65/MWh
Henry Hub gas: $3.80/MMBtu
Heat rate of efficient CCGT: 7.0 MMBtu/MWh
Heat rate of peaker CT: 10.5 MMBtu/MWh

CCGT spark = $65 - ($3.80 x 7.0) = $65 - $26.60 = $38.40/MWh (profitable)
Peaker spark = $65 - ($3.80 x 10.5) = $65 - $39.90 = $25.10/MWh (profitable — scarcity)

Implied heat rate = $65 / $3.80 = 17.1 MMBtu/MWh
→ Even a plant with a 17 heat rate is marginal. Market is very tight.
```

**What the implied heat rate tells you**: If the implied heat rate is 7-8, only efficient CCGTs are running — ample supply. If 10-12, peakers are needed — moderate tightness. If 15+, extreme scarcity — even the worst plants are being called. During Winter Storm Uri, ERCOT implied heat rates hit 100+.

### Spark Spread Variants

- **7x24**: All hours, blended. Used for long-dated financial hedging.
- **On-peak** (HE8-HE23, weekdays): Higher value. Demand is strongest during business hours and evening.
- **Off-peak** (HE1-HE7, weekends): Lower prices, sometimes negative in high-renewables markets.
- **Clean spark**: Spark spread minus carbon cost per MWh. Relevant in carbon-priced markets (EU ETS, RGGI).

```
Clean spark = Power - (Gas x HR) - (Carbon price x Emission factor)
EU example:
Power: €85/MWh, Gas: €35/MWh(th), HR: 2.0 MWh(th)/MWh(e)
Carbon: €60/tCO2, Gas emission factor: 0.37 tCO2/MWh(th)
Clean spark = €85 - (€35 x 2.0) - (€60 x 0.37 x 2.0) = €85 - €70 - €44.40 = -€29.40
→ Gas plant is uneconomic. Coal-to-gas switching at this carbon price.
```

## Locational Spreads (Basis)

Same commodity, different delivery location. Every basis spread is a transportation economics question.

### Natural Gas Basis — Where the Alpha Is

Gas basis is one of the most active and profitable areas of energy spread trading because the US gas pipeline system has chronic bottlenecks.

**Key gas basis spreads**:

| Spread | Description | Typical Range | Driver |
|--------|-------------|---------------|--------|
| Waha - Henry Hub | Permian gas to Gulf Coast | -$2.00 to +$0.50 | Permian associated gas production vs. pipeline capacity. Often deeply negative. |
| Algonquin - Henry Hub | New England delivery | $0.00 to +$30.00 | Winter pipeline constraints into New England. Can spike violently during cold. |
| SoCal Border - Henry Hub | California delivery | -$1.00 to +$5.00 | Western pipeline congestion, CA gas demand, renewable displacement. |
| Chicago - Henry Hub | Midwest delivery | -$0.30 to +$1.50 | Moderate; well-connected pipeline system. |
| Dominion South - Henry Hub | Appalachian (Marcellus) | -$1.50 to +$0.20 | Marcellus production exceeding takeaway capacity. Persistently discounted. |

**Waha basis** is the most dramatic example. The Permian Basin produces ~25 Bcf/d of associated gas (produced alongside oil — operators drill for oil and gas comes out whether they want it or not). Pipeline capacity out of the Permian is ~23-24 Bcf/d. When production exceeds capacity, Waha gas prices collapse — sometimes going **negative** (producers pay to dispose of gas rather than shut in oil wells). This is a structural trade that persists until new pipeline capacity is built.

**Algonquin basis** is the most volatile. New England has limited pipeline capacity and virtually no LNG import capacity since the Everett LNG terminal's role diminished. During cold snaps, gas for heating and power generation competes for limited pipeline space. Algonquin basis has spiked to $20-30/MMBtu above Henry Hub during polar vortex events — a 10x+ premium over normal.

### Crude Oil Basis

| Spread | Description | Typical Range | Driver |
|--------|-------------|---------------|--------|
| WTI Midland - WTI Cushing | Permian to pipeline hub | -$5.00 to +$0.50 | Permian pipeline capacity. Blew out to -$15 in 2018 before new pipes. |
| WTI - Brent | US vs. international | -$8.00 to +$3.00 | US export capacity, Cushing inventory, global disruptions. |
| LLS - WTI | Gulf Coast vs. Cushing | -$1.00 to +$5.00 | Gulf Coast refinery demand, export economics. |
| WCS - WTI | Canadian heavy vs. US light | -$25.00 to -$10.00 | Pipeline capacity from Alberta, diluent costs, heavy demand. |

## Inter-Commodity Spreads

### Frac Spread (NGL vs. Gas)

```
Frac spread = NGL price ($/gal) x 42 - Gas price ($/MMBtu) x ~6.0 shrink factor

Example (ethane):
Ethane: $0.25/gal = $10.50/bbl
Gas equivalent of ethane recovered: ~0.06 MMBtu/gal processing input
Gas: $3.50/MMBtu
Frac spread drives the economics of gas processing plants:
→ Wide frac spread = profitable to process wet gas into NGLs
→ Narrow frac spread = ethane rejection (leave NGLs in the gas stream)
```

The frac spread determines how much wet gas processing occurs. When the frac spread widens (NGL prices rise relative to gas), processors run at capacity and gas production effectively increases. When it narrows, ethane is rejected — reducing gas liquids supply and increasing effective gas pipeline volumes.

### LNG Arbitrage

```
JKM (Japan Korea Marker): $14.00/MMBtu
Henry Hub: $3.50/MMBtu
Gross arbitrage: $10.50/MMBtu

Less:
Liquefaction fee: $2.50/MMBtu (tolling charge at Sabine Pass, Cameron, etc.)
Shipping (USGC to Asia): $1.50-3.00/MMBtu (varies with charter rates)
Regas fee: $0.50/MMBtu
Insurance/loss: $0.30/MMBtu
Total cost: $4.80-6.30/MMBtu

Net arbitrage: $10.50 - $5.55 (mid) = ~$4.95/MMBtu → trade is OPEN
When JKM-HH < ~$5.00 → arbitrage closes → LNG flows to Asia slow
```

LNG arbitrage is the mechanism that links US gas (Henry Hub) to European gas (TTF) and Asian gas (JKM). When the arb is open, US LNG exports run at max capacity (~14 Bcf/d). When it closes, cargoes get diverted or deferred. Tracking this arb tells you about global gas supply rebalancing.

### Gas-Coal Switching

In power markets, the relative price of gas vs. coal determines which fuel generators burn. When gas is cheap relative to coal (adjusted for heat rate and carbon cost), gas plants displace coal → gas demand increases, coal demand decreases. When gas is expensive, coal plants run more.

```
Gas plant cost: Gas price x Gas HR = $3.50 x 7.0 = $24.50/MWh
Coal plant cost: Coal price x Coal HR + Carbon = ($2.50/MMBtu x 10.0) + ($5 x 0.95) = $29.75/MWh
→ Gas is cheaper → gas displaces coal → more gas demand

If gas rises to $5.00: Gas cost = $5.00 x 7.0 = $35.00/MWh > Coal $29.75
→ Coal is cheaper → coal runs more → gas demand falls
Switching price: ~$4.25/MMBtu at these coal/carbon levels
```

The switching price is a soft floor/ceiling on gas demand — it provides natural mean-reversion for gas prices.

## Option Structures in Energy

### Collar — The Most Common Producer Hedge

A producer sells a call (gives up upside above strike) and buys a put (protects downside below strike). The call premium finances the put → zero-cost or low-cost protection.

```
Producer hedge example:
WTI at $80. Producer sells $90 call and buys $70 put. Zero-cost collar.
- WTI falls to $60: Put pays $10/bbl protection. Producer receives $70 effective.
- WTI stays at $80: Both options expire worthless. Producer sells at $80.
- WTI rallies to $100: Call is exercised. Producer capped at $90 effective.

The collar is essentially: "I'm willing to give up prices above $90 in exchange for guaranteed floor at $70."
```

When many producers put on collars at similar levels, the collective options market flow suppresses volatility. The hedging flow creates resistance at the call strike (price ceiling) and support at the put strike (price floor). Track producer hedging activity (reported in 10-Qs) for options market intelligence.

### Straddle / Strangle — Volatility Trades

```
WTI at $80. Buy $80 straddle (long $80 call + long $80 put).
Premium: $3.50/bbl (call) + $3.20/bbl (put) = $6.70/bbl total cost.
Breakeven: Below $73.30 or above $86.70 (need a $6.70 move in either direction).

This trade profits from a large move in EITHER direction.
Use before binary events: OPEC meetings, EIA reports, geopolitical escalation.
The risk: if nothing happens and vol crushes, you lose the full premium.
```

**Energy-specific dynamics**: Straddles before OPEC meetings are priced expensively because the market knows the event is coming. The key is whether the actual move exceeds what the straddle prices in. If the straddle costs $6.70 and WTI moves $10, you profit. If it moves only $4, you lose even though "something happened."

### Calendar Option Spreads — Trading Vol Term Structure

Buy an option in one month, sell an option in another month at the same strike. This trades the **term structure of implied volatility**.

```
Winter gas vol is typically 50-60%. Summer gas vol is 30-40%.
Buy Jan $4.00 call (high IV) for $0.50
Sell Jul $4.00 call (low IV) for $0.20
Net cost: $0.30/MMBtu

You're long winter vol and short summer vol. If winter vol increases or summer vol decreases, you profit.
```

## Thinking About Spread Trades — The Framework

Every spread trade should answer these six questions:

**1. What is my fundamental view?**
"Gasoline demand will exceed expectations this summer because VMT data is trending 3% above prior year, and Gulf Coast turnarounds are heavier than normal, constraining supply."

**2. What does the spread currently price in?**
"The Q3 3:2:1 crack is at $28/bbl, which is the 35th percentile of the 5-year range for this week of year. The market is pricing normal demand and normal utilization."

**3. What is the historical range?**
"This spread has ranged from $15 to $55 over 5 years, with a seasonal average of $32 for this period."

**4. What would make me wrong?**
"A recession, which would reduce driving demand. Or a crude supply disruption that pushes crude up faster than products."

**5. What is my stop?**
"I am wrong if the crack breaks below $22, which would imply demand is weaker than even bearish scenarios. Max loss: $6/bbl."

**6. How does the spread behave near expiry?**
"Crack spreads converge to actual refinery economics as physical delivery approaches. If physical margins are strong, the spread should hold or widen."

## Reading

- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 4 (Spread Trading) is the core reference. Covers crack spreads, spark spreads, basis spreads, and calendar spreads with worked examples.
- <a class="source-link" data-source="oil101">Oil 101</a> — chapters 9-10 (refining) provide the physical context behind crack spreads. Chapter 7 (transportation) explains why basis exists.
- <a class="source-link" data-source="eia">EIA Today in Energy</a> — the Middle East tanker rate article shows how physical supply disruptions drive basis and inter-regional spread opportunities in real time.

Also recommended: **Energy Trading & Investing** by Davis Edwards. The most practical book on energy trading. Covers every spread type with real P&L examples — essential for fund interview prep.
