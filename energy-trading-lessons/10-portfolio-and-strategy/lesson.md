# Module 10 — Portfolio & Strategy (+ Breaking Into the Industry)

---

## How Energy Hedge Funds Operate

### Fund Types

**Macro/Directional** (e.g., Andurand Capital, Westbeck Capital):
Large directional bets on commodity prices. Pierre Andurand made hundreds of millions in 2022 being long crude ahead of Russia-Ukraine. Annual return volatility: 30-60%. Can be up 100%+ or down 50%+ in a year. Sharpe: 0.5-1.5. These funds live and die by the PM's conviction and timing. Team: typically small (PM + 2-5 analysts). AUM: $500M-5B.

**Relative Value / Spread** (e.g., Citadel commodities, Millennium pods, Balyasny):
Trade mispricings between related instruments — crack spreads, calendar spreads, basis, inter-commodity. Steadier returns, higher Sharpe (1.5-3.0+), smaller drawdowns. This is where most institutional energy capital sits and where most of the jobs are. The bread-and-butter: 20-50 concurrent spread positions, actively managed. Team: PM + 1-3 analysts per pod.

**Systematic/Quant** (e.g., Millennium quant pods, AHL/Man Group, Two Sigma):
Algorithmic strategies using statistical models, trend-following, mean-reversion, or ML. Edge is speed, data processing, and discipline. Lower per-trade conviction but higher trade frequency. Sharpe: 1.0-2.5. Growing demand for quant talent in energy. Team: PM + quant researchers + engineers.

**Physical/Commercial** (e.g., Freepoint, Castleton, Hartree, Gunvor):
Trade physical cargoes and optimize logistics using financial derivatives to hedge. Owning or leasing storage, pipeline capacity, or terminal access creates real options — the right (but not obligation) to move, store, or blend physical commodities. These real options have measurable value. Historical Sharpe: 2.0+. Edge is physical infrastructure and operational knowledge.

**Multi-Strategy Pod Model** (e.g., Citadel, Millennium, Balyasny, Point72):
The dominant institutional model. Fund is organized into semi-independent "pods," each run by a PM with a dedicated analyst team and risk budget. Energy is one vertical among many (alongside equities, rates, credit, macro). PMs are compensated 15-20% of their net P&L above a hurdle. The fund provides capital, risk management, technology, and operational infrastructure. Fund-level Sharpe: 2.0-4.0+ (through diversification across pods).

### The Pod Structure In Detail

**Portfolio Manager (PM)**: The decision-maker. Runs the book, sizes positions, approves all trades. Typically 5-15 years of experience. Started as an analyst, progressed to junior trader, then PM. Compensation: 15-20% of net P&L (pass-through). A PM making $30M in a year takes home $4.5-6M. A PM losing money takes home base salary (~$200-400K) and is at risk of pod shutdown.

**Analysts (1-3 per pod)**: Build and maintain S/D balance models, monitor inventory data, maintain spread models, produce trade memos, run quant screens. **This is the most common entry point for new hires.** An analyst who demonstrates good trade ideas and risk awareness can progress to co-PM or launch their own pod in 3-5 years. Compensation (junior): $150-250K total (base + bonus). Senior analyst: $300-600K.

**Risk budget**: Expressed as a VaR limit (e.g., $50M in 95% daily VaR) or gross notional limit. PM deploys this budget across any energy trades they choose. The risk team monitors utilization in real-time.

**Independent risk team**: Reports to the CRO, NOT the PM. Monitors positions real-time, enforces limits, runs stress tests. Can force position reductions — PM cannot override. This independence is critical: the risk team's job is to protect the fund from individual PMs, including the most profitable ones.

**Drawdown triggers**: The ruthlessly Darwinian mechanism:
- **-3% from peak**: Informal discussion. "What's going on?"
- **-5% from peak**: On formal watch. Risk budget may be cut 25-50%.
- **-7% from peak**: Risk budget cut 50-75%. Only defensive/reducing trades.
- **-10% from peak**: Pod is SHUT DOWN. All positions liquidated. PM may be terminated.

The -10% hard stop means: if you start with $500M in capital, losing $50M ends your pod. Given that a normal position might have a daily VaR of $2-5M, a bad 2-week stretch can put you in danger. This is why diversification and stop discipline are existential — not just good practice.

### Pod Economics Example

```
PM starts year with $500M capital allocation, $50M VaR limit.

Good year:
Net P&L: +$30M (6% return)
PM payout (18%): $5.4M
Analyst bonus pool: $1.5M
Fund keeps: $23.1M

Bad year:
Net P&L: -$25M (hit -5% trigger, risk cut)
PM payout: $0 (below hurdle). Still earns ~$300K base salary.
If PM hits -10%: pod shut down. PM may be terminated.

Breakeven calculation:
Fixed costs (salaries, data, technology): ~$3-5M/year
PM needs to generate >$5M just to earn above base salary
→ 1% return on $500M capital is the minimum viable result
```

## Idea Generation — The 4 Pillars

### Pillar 1: Fundamental Analysis

Every trade should be grounded in a supply/demand thesis. The goal is to build a more accurate S/D balance than the market consensus.

**Crude oil S/D balance framework**:
```
Supply:
  OPEC crude production        ~27.0 M bbl/d
  OPEC+ allies (Russia, etc.)  ~13.5 M bbl/d
  US crude                     ~13.6 M bbl/d
  Other non-OPEC               ~17.5 M bbl/d
  Processing gains              ~2.5 M bbl/d
  TOTAL SUPPLY                 ~74.1 M bbl/d (crude only)

Demand:
  OECD (US, Europe, Japan, etc.)  ~46.0 M bbl/d
  China                           ~16.5 M bbl/d
  India                            ~5.5 M bbl/d
  Other non-OECD                  ~35.0 M bbl/d
  TOTAL DEMAND                   ~103.0 M bbl/d (total liquids)

Note: Supply includes NGLs, biofuels, and other liquids to get to ~103 M bbl/d total.

Implied stock change = Supply - Demand
If supply > demand → inventory builds → bearish
If demand > supply → inventory draws → bullish

Your edge: a better estimate of any one of these components than the market.
```

**Key data sources for fundamental analysis**:
- **EIA Weekly Petroleum Status** (Wed 10:30 ET): US crude, gasoline, distillate inventories, refinery utilization, imports, exports. The single most market-moving energy report.
- **EIA Thursday Gas Storage** (Thu 10:30 ET): Weekly gas storage change. Build your own model to estimate ahead of the report.
- **Baker Hughes Rig Count** (Fri 1:00 ET): Leading indicator of US shale production (6-month lag).
- **IEA Monthly Oil Market Report** (~15th): Most respected independent global S/D analysis.
- **OPEC Monthly Report** (~12th): OPEC's own view. Tends to be more optimistic on demand.
- **Kpler/Vortexa** (real-time): Satellite-tracked tanker and cargo flows. See physical trade as it happens.
- **IIR Energy** (subscription): Refinery turnaround schedules. Know exactly which units are offline.

### Pillar 2: Quantitative Screens

Systematic screening identifies where spreads are statistically anomalous relative to history.

**Z-score screen**:
```
For each spread in your universe (50-100 spreads across crude, gas, products, power):
1. Calculate the 60-day rolling mean and standard deviation
2. Compute z-score = (current - mean) / std
3. Flag any spread with |z| > 1.5

Result: a daily list of "extreme" spreads that warrant fundamental investigation.
Warning: a spread at z = +2.5 may be extreme for a REASON (structural change).
Always check fundamentals before trading a quant signal.
```

**Seasonal deviation screen**:
```
For each spread:
1. Calculate the 10-year average level for this week of year
2. Calculate the 10-year standard deviation for this week of year
3. Compute: current level vs. seasonal average
4. Flag spreads 1.5+ std devs from seasonal average

Example:
3:2:1 crack, Week 15 (mid-April):
10yr average: $30/bbl
10yr std dev: $8/bbl
Current: $22/bbl
Deviation: -1.0 std devs (mildly cheap but not extreme)
→ Watch list, not an immediate trade
```

**Regression residual screen**:
```
Run regression: Crack = f(utilization, gasoline deficit, VIX)
Model says fair value: $28
Actual: $22
Residual: -$6 (crack is $6 cheap vs. model)
→ If the model is correctly specified, this is a buy signal
→ Check: has a structural change (new refinery capacity, demand shift) invalidated the model?
```

### Pillar 3: Event-Driven Catalysts

**OPEC+ meetings**: The most important scheduled event for crude. Pre-meeting, develop 3 scenarios:
1. Base case (what consensus expects) → no trade
2. Hawkish surprise (deeper cut or extended timeline) → long crude, long backwardation
3. Dovish surprise (smaller cut, compliance slippage, price war) → short crude, long contango

The trade = decision minus expectation. Position for the scenario you think is underpriced.

**EIA report trading**: Build your own estimate. If your model says -4M bbl crude draw and consensus says -1.5M, you have a directional signal going into the report.

**Weather model shifts**: GFS and ECMWF run 4x daily (00Z, 06Z, 12Z, 18Z). A cold-to-warm shift in the 8-14 day forecast kills gas and power prices. A warm-to-cold shift rallies them. The key: be early to the model shift. The first run showing a new pattern moves gas $0.10-0.20. By the third confirming run, the move is priced.

### Pillar 4: Market Microstructure

**Options market signals**:
- **Skew**: If WTI call skew (OTM calls expensive relative to puts) is at 1-year highs, the market is pricing upside tail risk. Ask why.
- **Put/call ratio**: Extreme put buying (ratio > 1.5) = hedging/fear. Can signal a local bottom if fundamentals are neutral.
- **Implied vol term structure**: If 1-month IV is higher than 3-month IV (inverted term structure), the market expects a near-term event.

**Positioning (COT data)**:
- **Managed money net long at 90th+ percentile**: Market is crowded long. Vulnerable to liquidation cascade on bearish news. Not a timing tool — but if you have a bearish view, the crowded positioning amplifies the potential move.
- **Managed money net short at 10th percentile**: Crowded short. Vulnerable to short squeeze. A bullish catalyst will move prices further than usual.

**Open interest by month**: A sudden surge in OI in a specific back month signals that a large player is building a position. Track daily changes.

## The Trade Memo — Your Professional Currency

At a fund, you present trade ideas in a structured memo format. In an interview, you present them verbally in the same structure. Have 2-3 ready at all times.

### Memo Template

```
TRADE: [Precise description — e.g., "Long Q3 2027 3:2:1 Gulf Coast Crack Spread"]
DIRECTION: Long / Short
CURRENT LEVEL: [Specific number — e.g., "$28.50/bbl"]
TARGET: [Specific number — e.g., "$38/bbl"]
STOP: [Specific number — e.g., "$22/bbl"]
TIMEFRAME: [e.g., "6-8 weeks, through peak driving season"]
RISK/REWARD: [e.g., "1.6:1 ($9.50 upside vs. $6.50 downside)"]

THESIS (2-3 sentences):
Gasoline inventories are 18M bbl below the 5yr average with driving season
starting in 3 weeks. Gulf Coast utilization at 88% vs. 93% seasonal norm
due to extended turnarounds — product supply deficit will widen cracks.

FUNDAMENTAL CASE:
- Gasoline stocks: 215M bbl vs. 5yr avg 233M (-18M, 8th percentile)
- Distillate stocks: 110M bbl vs. 5yr avg 125M (-15M, 12th percentile)
- Refinery utilization: 88% vs. seasonal normal 93%
- VMT (vehicle miles traveled): tracking +2.4% YoY
- Cushing crude: 38M bbl (comfortable → limited risk on short crude leg)

QUANTITATIVE SUPPORT:
- 3:2:1 at $28.50 = 35th percentile of 5-year range for this week of year
- Seasonal pattern: cracks typically rally $8-12 from mid-April through mid-June
- Regression model (crack vs. utilization + gasoline deficit): fair value $34
- Z-score vs. 60-day mean: -0.8 (not extreme, but trending toward cheap)

CATALYSTS:
- Major Gulf Coast turnarounds end mid-April → utilization ramp to 93%+
- First strong summer gasoline demand data (EIA May reports)
- Memorial Day weekend demand surge (late May)

RISKS:
- Recession indicators worsen → driving demand disappoints (mitigant: stop at $22)
- Crude supply disruption pushes crude up faster than products (mitigant: rolling crude
  hedge if Brent risk premium exceeds $5 from current)
- Early hurricane forces Gulf Coast refinery shutdowns (actually bullish for cracks
  if offshore production stays online — products get tighter)

SIZING:
- Pod risk budget: $5M daily VaR. Allocation to this trade: 15% = $750K/day
- 3:2:1 daily vol: ~$0.80/bbl → $800 per 1-lot crack per day
- Position: $750K / $800 = ~940 barrels of crack ≈ 300 lots of 3:2:1
- Check vs. liquidity: 300 lots = 900 CL + 600 RB + 300 HO
  CL ADV ~900K (0.1%), RB ADV ~100K (0.6%), HO ADV ~100K (0.3%) → comfortable
```

## Portfolio Construction

### Diversification Principles

**Across time horizons**:
- **Tactical** (days to weeks): EIA report trades, weather model shifts, OPEC positioning. High turnover, lower conviction per trade, many small bets.
- **Fundamental** (weeks to months): Crack spread seasonals, storage trajectory trades, basis infrastructure plays. Core book. Higher conviction, larger size.
- **Structural** (months to quarters): Energy transition themes, long-term S/D imbalances, regulatory regime changes. Smaller positions, long time to thesis realization.

**Across spread types**:
- Calendar spreads (5-10 positions): WTI prompt, gas winter/summer, seasonal rolls
- Crack spreads (3-5 positions): 3:2:1, gasoline vs. diesel, seasonal cracks
- Basis spreads (5-10 positions): WTI-Brent, Waha-HH, regional gas, crude differentials
- Inter-commodity (2-3 positions): Frac spread, LNG arb, gas-coal switching
- Directional (0-2 positions): Only with high conviction AND catalyst. Small relative to spread book.
- Options (2-5 positions): Vol trades, tail hedges, event-driven

**Correlation-aware sizing**: Two gasoline crack trades (Q2 and Q3) are highly correlated (~0.85). Treat them as one combined position for risk purposes. The portfolio VaR is NOT the sum of individual position VaRs — it is the correlation-weighted sum.

### The Carry vs. Convexity Balance

**Carry trades** provide steady positive P&L:
- Selling options premium (collect theta)
- Harvesting backwardation roll yield (long in backwardated markets)
- Calendar spreads that converge predictably

**Convex trades** provide asymmetric payoffs:
- Buying cheap OTM options before binary events
- Tail hedges (deep OTM puts on crash scenarios)
- Event-driven trades with large potential move and limited downside

**The right mix**: Carry trades fund the portfolio's day-to-day operations. Convex trades protect against tail events and generate outsized returns when the market surprises. A portfolio of only carry trades will be profitable 11 months and blow up in the 12th. A portfolio of only convex trades will bleed premium while waiting for the event. The ideal: 60-70% carry, 30-40% convex.

## Performance Measurement

| Metric | Target (RV/Spread) | Target (Directional) | Notes |
|--------|--------------------|--------------------|-------|
| Annual Return | 10-25% | 15-40%+ | Directional more volatile |
| Sharpe Ratio | 1.5-3.0 | 0.5-1.5 | Sharpe >2.0 = institutional quality |
| Max Drawdown | <8% | <20% | Pod hard stop at -10% |
| Win Rate | 52-60% | 45-55% | Higher for RV due to mean-reversion |
| Avg Win / Avg Loss | 1.2-1.8x | 1.5-3.0x | Directional needs bigger winners |
| Calmar Ratio | >2.0 | >1.0 | Return / max drawdown |
| Monthly Hit Rate | 70-80% positive months | 55-65% | Consistency matters for capital retention |

**P&L attribution**: Decompose returns into:
- **Alpha** (from spread selection and timing): the PM's skill
- **Beta** (from directional energy exposure): not skill — any index can do this
- **Carry** (from roll yield and time decay): structural, not timing-dependent
- **Volatility** (from options positions): vega and gamma P&L

Institutional allocators want alpha, not beta. A PM who returns 20% with 15% from directional crude exposure and 5% from alpha is less valuable than a PM who returns 12% with 10% from alpha.

## Breaking Into Energy Trading

### Entry Points (Ranked by Frequency)

**1. Analyst at energy trading fund** (most common):
- Role: Research, model building, trade idea generation
- Requires: Energy fundamentals knowledge, Python, Excel, ability to write trade memos
- Firms: Citadel, Millennium, Balyasny, Point72 (pod shops); Freepoint, Castleton, Hartree (physical/commercial); Andurand, Westbeck (directional)
- Comp (Y1): $150-250K total. Y3-5: $300-600K with good performance.
- Path: Analyst → Senior Analyst → Co-PM → PM (5-8 years)

**2. Physical trading trainee** (highest ceiling):
- Role: Learn to trade physical cargoes. Rotational programs through different desks.
- Firms: Vitol, Trafigura, Glencore, Gunvor, Mercuria, bp, Shell trading
- Requires: Strong academics, language skills (Mandarin, Spanish, Arabic are valued), personality fit (high energy, relationship-builder)
- Comp (Y1): $100-150K. Y5-7 with track record: $1-5M+. Top physical traders: $10M+.
- Path: Trainee → Junior Trader → Trader → Senior Trader/Partner (5-10 years)

**3. Quant/developer at commodities fund**:
- Role: Build models, data infrastructure, signals, execution algorithms
- Requires: Python, C++, SQL, statistics, time series analysis, ML
- Firms: Citadel, Millennium, Two Sigma, AHL/Man Group, systematic energy shops
- Comp: Competitive with tech ($200-500K+). Lower ceiling than PM track but more stable.

**4. Sell-side energy research** (good training ground):
- Role: Publish research, build models, support institutional clients
- Firms: Goldman Sachs, Morgan Stanley, JP Morgan, Citi commodity research
- Comp (Y1): $150-200K. Director-level: $400-800K.
- Path: Analyst → Associate → VP → Director, then transition to buy-side PM

**5. Commercial/corporate energy**:
- Role: Hedge corporate energy exposure (airline fuel, utility gas, E&P production)
- Firms: Airlines (Southwest, Delta), utilities, E&P companies (ConocoPhillips, EOG)
- Comp: Lower than hedge fund but better work-life balance. Analyst: $100-150K. Manager: $200-350K.

### What They Look For

**1. Fundamentals knowledge** — Can you discuss the crude S/D balance with specificity?
Bad answer: "I think oil is going up because of tensions in the Middle East."
Good answer: "Global demand is ~103M bbl/d. OPEC+ is producing ~34M including Russia at ~9M with weak compliance from Iraq and Kazakhstan. The call on OPEC crude for Q3 is ~28.5M bbl/d at current demand, implying ~1M bbl/d of draws if OPEC holds quotas. Cushing is at 32M bbl, below the 5-year average. I think Q3 backwardation should widen."

**2. Quantitative skills** — Python (pandas, matplotlib, statsmodels), Excel (can you build a quick S/D model in 30 minutes?), SQL (if quant-oriented), statistics (regression, time series, hypothesis testing).

**3. Trade idea articulation** — Present in memo format, from memory, under pressure. You should be able to give current prices, the fundamental setup, your directional view, the spread you'd trade, entry/target/stop, and sizing. Vague answers are disqualifying.

**4. Intellectual curiosity** — Do you read energy news daily? Can you discuss what moved this week? Do you follow the EIA reports? If your interviewer asks "What did the EIA report show this morning?" and you say "I didn't check," the interview is over.

**5. Risk awareness** — Every trade idea must include "what could go wrong" and how you'd manage it. Funds hire traders who will survive, not just traders who will make money for two years then blow up.

### Interview Preparation

**"Give me a trade idea."**
Have 2-3 ready. Present in memo format: Trade, direction, current level, target, stop, thesis, fundamental support, quant support, risks, sizing. Specific numbers throughout. Not "I like oil long-term" — that's not a trade.

**"Walk me through the crude oil S/D balance."**
Global demand by region. Supply by source (OPEC, US, non-OPEC). Net implied stock change. Compare EIA, IEA, OPEC forecasts. Where do you think consensus is wrong?

**"Why is gas in contango/backwardation right now?"**
Storage economics framework. Current inventories vs. 5-year average. Cost of carry vs. calendar spread. Injection/withdrawal rate vs. norms. LNG export levels. Production trends.

**"How would you size a position in [spread X]?"**
Vol-based sizing formula. Risk budget → daily vol → contract multiplier → position. Then check: "Is this position <5% of the contract month's ADV? Can I exit in 1-2 days?"

**"What happened in energy this week?"**
You must know: EIA inventory report results and surprises, any OPEC news, notable price moves (WTI, Brent, gas, cracks), the narrative driving the market. Prepare daily.

**"Explain the 3:2:1 crack spread."**
Formula. Physical logic (why 3:2:1 approximates a refinery). Calculate with current prices. What drives it (utilization, inventories, seasonality). Is the crack currently rich or cheap vs. seasonal norms?

**"Tell me about a time you were wrong."**
Describe a specific trade or analytical error. Focus on what you learned about your process, not the outcome. "I was short gas going into a polar vortex because my weather model weighted GFS more than ECMWF. I learned to weight the models equally and keep stops tighter around weather-sensitive positions." Never blame luck.

**Brainteaser: "$10M, 100:1 leverage on WTI — what's your strategy?"**
The correct answer: "I would NOT use 100:1 leverage. At 100:1, a 1% WTI move ($0.80) wipes out the entire $10M. WTI routinely moves 2-3% daily. The correct approach: 5-10x leverage, deployed across 10-15 uncorrelated spread positions, each sized so a 3-sigma day costs no more than 1-2% of capital. Target Sharpe: 1.5+, Max DD: <10%."

### How to Stand Out

**1. Paper trade track record**: Document 6-12 months of trades in memo format. Track results honestly. Include losers with post-mortems. This is the single most differentiating thing a candidate can bring to an interview. Attach a summary: total return, Sharpe, max drawdown, win rate.

**2. Original analysis**: Download EIA data via API. Build a Permian production model. Create a seasonal crack spread visualization. Write up a non-obvious view on an energy spread with data. Post on LinkedIn or send directly to people at target firms.

**3. Know the market cold**: On any given day, you should know: WTI, Brent, Henry Hub, RBOB, ULSD, TTF spot prices (± 5%). Last week's EIA report numbers. OPEC+ policy and next meeting date. Forward curve shape and why. 2-3 live trade ideas.

**4. Network**: Energy trading is small and relationship-driven. Conferences: CERAWeek (Houston, March), APPEC (Singapore, October), IP Week (London, February), FT Commodities Summit. Industry events: local commodity meetups, university energy clubs. LinkedIn: follow and engage with energy analysts and traders.

**5. Physical trading experience**: If you can get a physical rotation at Vitol, Trafigura, Glencore, bp trading, or Shell trading — take it. Physical knowledge is a durable edge that financial-only traders never acquire. Understanding how cargoes are priced, loaded, shipped, and delivered gives you pattern recognition that no model replicates.

## Reading

- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — the entire text. By this point in the curriculum, you should have read it cover to cover. Revisit the spread trading and risk management sections now that you have the context to absorb them deeply.
- <a class="source-link" data-source="oil101">Oil 101</a> — the complete book. It is the physical-market bible. When an interviewer asks about crude grades, pipeline logistics, or refinery yields, this book is where the answers live.
- <a class="source-link" data-source="eia">EIA Today in Energy</a> — make this a daily habit. Read 2-3 articles per week. Over 6 months, you will build an intuitive understanding of what drives energy markets.

Also recommended: **The World for Sale** by Javier Blas and Jack Farchy — the story of the physical commodity trading houses (Vitol, Glencore, Marc Rich). **The Asylum** by Leah McGrath Goodman — the wild history of NYMEX. **Superforecasting** by Philip Tetlock — how to be a better forecaster (directly applicable to energy). Follow on X/Twitter: @JavierBlas, @ed_morse_citi, and energy traders who post publicly.
