# Module 02 — Crude Oil

---

## The Crude Quality Spectrum

Crude oil is not one product — it is a spectrum of hydrocarbons that vary dramatically in quality. Two properties define a crude grade and determine its value:

**API Gravity** measures density. Higher API = lighter = more valuable (yields more gasoline and diesel, less heavy residual). The scale is inverse to specific gravity: water = 10° API.

- Light crude: > 31° API
- Medium crude: 22-31° API
- Heavy crude: < 22° API

**Sulfur Content** determines processing cost. Sweet crude (< 0.5% sulfur) can be refined with simpler equipment. Sour crude (> 0.5% sulfur) requires hydrotreating/hydrocracking units that cost hundreds of millions to build — this is why sour crude trades at a discount.

### Major Crude Grades

| Grade | API Gravity | Sulfur % | Classification | Region | Notes |
|-------|------------|----------|----------------|--------|-------|
| WTI (West Texas Intermediate) | 39.6° | 0.24% | Light sweet | US (Permian/Midland) | US domestic benchmark |
| Brent (BFOET basket) | 38.3° | 0.37% | Light sweet | North Sea | International benchmark, ~80% of global crude priced off Brent |
| LLS (Louisiana Light Sweet) | 36.1° | 0.39% | Light sweet | US Gulf Coast | Gulf Coast physical benchmark |
| Mars | 28.9° | 1.93% | Medium sour | US Gulf of Mexico | Key GOM offshore grade, US sour benchmark |
| Arab Light | 33.0° | 1.77% | Medium sour | Saudi Arabia | Largest single exported grade in the world |
| Arab Heavy | 27.4° | 2.83% | Medium sour | Saudi Arabia | Feeds complex refineries in Asia |
| Dubai/Oman | 31.0° | 2.04% | Medium sour | Middle East | Asian crude benchmark (DME) |
| Urals | 31.7° | 1.35% | Medium sour | Russia | Historically priced off Brent minus a differential |
| WCS (Western Canadian Select) | 20.5° | 3.47% | Heavy sour | Canada (oil sands) | Trades at steep discount — requires diluent for pipeline transport |
| Maya | 21.5° | 3.30% | Heavy sour | Mexico | Key Latin American heavy grade |
| Bonny Light | 35.4° | 0.14% | Light sweet | Nigeria | Premium sweet crude, popular in European refineries |

**Why this matters for trading**: Quality differentials are tradeable spreads. A simple refinery (atmospheric distillation only) needs light sweet crude. A complex refinery (with cokers, hydrocrackers, FCC units) can process cheap heavy sour crude and crack it into high-value products at wider margins. When light-heavy differentials widen (light sweet premium increases), complex refiners profit more. When differentials narrow, simple refiners benefit. Tracking these differentials tells you about refinery economics and marginal barrel economics globally.

## WTI vs. Brent — The Two Benchmarks

| | WTI | Brent |
|---|-----|-------|
| Full name | West Texas Intermediate | Brent-Forties-Oseberg-Ekofisk-Troll (BFOET) |
| Quality | 39.6° API, 0.24% S | 38.3° API, 0.37% S |
| Delivery | Physical at Cushing, OK | Cash-settled against ICE Brent Index (based on physical BFOET cargoes) |
| Exchange | NYMEX/CME (ticker: CL) | ICE (ticker: B) |
| Contract size | 1,000 barrels | 1,000 barrels |
| Settlement | Physical delivery | Cash settled |
| Tick size | $0.01/bbl ($10 per contract) | $0.01/bbl ($10 per contract) |
| Daily volume | ~1M contracts | ~500K contracts |
| Global role | US domestic benchmark | International benchmark — ~80% of global crude priced off Brent |
| Pricing scope | Primarily landlocked US midcontinent | Waterborne (seaborne), globally accessible |

### The WTI-Brent Spread

The WTI-Brent spread (WTI minus Brent) is one of the most important spreads in energy. Its historical range is roughly **-$27 to +$5**, though it typically trades between **-$5 and +$3**.

**What drives it**:

- **US production growth**: When shale production surges and midcontinent logistics cannot move oil to export terminals fast enough, WTI weakens vs. Brent (spread goes more negative). This drove the blow-out to -$27 in 2011.
- **US export capacity**: After the 2015 repeal of the US crude export ban, US Gulf Coast export infrastructure expanded dramatically. Better export capacity tightens the spread (WTI strengthens toward Brent) because excess US crude can be sold internationally.
- **Cushing inventory levels**: High Cushing inventories weaken WTI specifically (since Cushing is the delivery point). When Cushing approaches operational capacity, the front spread collapses.
- **Global supply disruptions**: Middle East tensions, Libya outages, North Sea maintenance — these tighten global supply and push Brent higher relative to WTI.
- **Atlantic Basin arbitrage**: When the WTI-Brent spread exceeds the shipping cost from the US Gulf to Europe (~$1.50-3.00/bbl), US crude exports flow to Europe, which narrows the spread. When it contracts below shipping cost, flows slow and the spread widens again. This creates a natural floor/ceiling.

**How to trade it**: Long WTI / short Brent (or vice versa). On CME, you can trade this directly as the WTI-Brent spread futures contract. Most crude oil relative-value traders have an opinion on this spread.

## OPEC and OPEC+

### Members

**OPEC (13 members)**: Saudi Arabia, Iraq, Iran, UAE, Kuwait, Venezuela, Libya, Nigeria, Algeria, Angola, Congo, Gabon, Equatorial Guinea. Combined production: ~27 million bbl/d. Saudi Arabia alone: ~9-10 million bbl/d (can surge to ~12 million).

**OPEC+ allies (10 key non-OPEC partners)**: Russia (~9-10 million bbl/d), Kazakhstan, Mexico, Oman, Azerbaijan, Malaysia, Bahrain, Brunei, Sudan, South Sudan. Russia is by far the most important ally.

**OPEC+ combined**: ~40+ million bbl/d, roughly 40% of global crude production. This is enough market share to meaningfully influence prices.

### How Quotas Work

OPEC+ sets production quotas at ministerial meetings (every 1-2 months, or ad hoc). Each member gets a ceiling. The total OPEC+ cut is allocated across members based on baseline production levels.

**Compliance dynamics**: Compliance is uneven. Saudi Arabia and UAE tend to over-comply (cut more than their quota). Iraq, Nigeria, and Russia tend to under-comply (cheat and produce above quotas by 200-500K bbl/d). The market watches actual production data (secondary sources like Platts, Argus, IEA) vs. stated quotas to assess real compliance. Weak compliance undermines cuts and is bearish.

**Saudi spare capacity**: Saudi Arabia holds ~2-3 million bbl/d of spare capacity — production it could bring online within 90 days but chooses not to. This is the world's strategic supply buffer. No other country has spare capacity on this scale. When spare capacity is high, the market has a cushion against disruptions. When spare capacity drops below ~1.5 million bbl/d, the risk premium in crude rises sharply.

### How to Read OPEC Meetings

**The price move = decision minus expectation**. If the market expects a 500K bbl/d cut and OPEC delivers 1 million, crude rallies. If the market expects a cut and OPEC does nothing, crude sells off. Always know the consensus expectation before the meeting.

Watch for:
- Rumors 24-48 hours before the meeting (delegations leak)
- Saudi-Russia alignment (when they agree, the decision is usually decisive)
- Internal fractures (UAE and Iraq have pushed back on quotas repeatedly)
- Timing of the next meeting (short intervals = monitoring mode, signals instability)
- The communique language: "monitor the market" = no action; "adjust output" = cut or hike

### Historical OPEC Price Wars

**1985-1986**: Saudi Arabia abandoned its swing producer role and opened the taps to punish quota cheaters. Crude crashed from $30+ to under $10. Devastated non-OPEC producers (North Sea, US stripper wells). Saudi revenue collapsed but they regained market share. Lesson: Saudi Arabia has the lowest production costs and can outlast anyone in a price war.

**2014-2016**: Saudi Arabia refused to cut production in the face of the US shale revolution, seeking to test shale breakevens and drive out high-cost producers. Brent dropped from $115 to $28 (Jan 2016). Shale producers went bankrupt in waves, but survivors cut costs and got more efficient — breakevens fell from $70-90 to $40-55. Led to the OPEC+ alliance with Russia in late 2016 as Saudi realized it could not kill shale.

**March 2020**: Saudi Arabia and Russia failed to agree on COVID-era production cuts. Saudi launched a price war, slashing official selling prices by $6-8/bbl and pledging to increase output to 12+ million bbl/d. Coming on top of COVID demand destruction (~20 million bbl/d lost in weeks), this pushed WTI to -$37.63 on April 20, 2020. OPEC+ agreed to the largest cut in history (9.7 million bbl/d) days later.

**Key lesson**: OPEC price wars destroy value for everyone but eventually end. The recovery trades (going long crude, long calendar spreads into backwardation) after capitulation have historically been some of the best risk/reward trades in energy.

## US Shale — The Marginal Barrel

### Basin-by-Basin Production

| Basin | Location | Production (bbl/d) | Primary Product | Key Feature |
|-------|----------|-------------------|-----------------|-------------|
| Permian | West Texas / SE New Mexico | ~6.0 million | Light sweet crude + associated gas | Largest and most prolific. Multiple stacked pay zones (Spraberry, Wolfcamp, Bone Spring). Still growing. |
| Eagle Ford | South Texas | ~1.1 million | Light sweet crude + condensate + gas | More mature. High initial rates but steep declines. Significant condensate production. |
| Bakken | North Dakota / Montana | ~1.1 million | Light sweet crude | Logistics-constrained (limited pipeline capacity, rail to Gulf Coast). Harsh winters affect operations. |
| DJ-Niobrara | Colorado | ~450K | Light crude + gas | Regulatory risk (Colorado state rules). Suburban encroachment limits drilling locations. |
| Anadarko | Oklahoma | ~400K | Oil + gas + NGLs | SCOOP/STACK plays. More gas-weighted. |

**Total US crude production**: ~13.6 million bbl/d (world's largest producer). Of this, shale/tight oil is ~9+ million bbl/d.

### Shale Economics

**Breakeven costs**: The WTI price needed for a new shale well to earn its cost of capital.
- Permian Tier 1 acreage: $35-45/bbl
- Permian Tier 2/3 acreage: $50-60/bbl
- Eagle Ford core: $45-50/bbl
- Bakken core: $50-55/bbl

These breakevens have fallen dramatically since 2014 (from $70-90 to current levels) due to efficiency gains: longer laterals (now 10,000-15,000+ feet vs. 5,000 in 2014), more proppant per stage, faster drilling times, and pad drilling (multiple wells from one location).

**Typical well economics**: Cost $5-8M to drill and complete. Initial production (IP) rate of 500-1,500 bbl/d. Estimated ultimate recovery (EUR) of 500K-1.5M barrels over the well's life.

**Decline rates**: Shale wells decline extremely fast compared to conventional wells.
- Year 1 decline: 60-75% (a well producing 1,000 bbl/d at peak might produce 250-400 bbl/d after 12 months)
- Year 2 decline: 30-40%
- Year 3+: 10-15% per year

This means shale production requires **constant drilling** just to stay flat. If rigs stop drilling for 6 months, production falls significantly. This is fundamentally different from conventional production (which declines 3-8% per year).

**DUC wells (Drilled but Uncompleted)**: Wells that have been drilled but not yet hydraulically fractured. These are essentially latent supply that can be brought online in 2-4 weeks (vs. 4-6 months for a new well from scratch). The DUC count is a leading indicator of near-term supply. When DUCs are drawn down aggressively, it signals operators are accelerating production without adding rigs. When DUCs build, operators are banking wells for later.

**Rig count-to-production lag**: ~6 months total (price signal to rig count ~2-3 months, rig count to production ~3-6 months). When rig counts rise, production growth follows with a lag. When rig counts fall (e.g., price crash), production declines follow. The Baker Hughes rig count (Friday 1:00 ET) is the leading indicator. The EIA Drilling Productivity Report (monthly) converts rig count into production estimates by basin.

**How shale acts as a price ceiling**: When WTI rises above $70-80, shale drilling accelerates, production grows, and within 6-12 months the additional supply caps prices. This is why crude has struggled to sustain prices above $90-100 for long periods in the shale era — shale supply is the structural price ceiling. Conversely, shale breakevens provide a soft price floor (~$40-50) because production declines fast once prices fall below breakeven.

## Cushing, Oklahoma — The Delivery Point

Cushing is the physical delivery point for WTI futures. It is the most important storage hub in the world for understanding WTI pricing mechanics.

**Key statistics**:
- Total shell capacity: ~90 million barrels
- Operational minimum (tank bottoms, working minimum): ~20-22 million barrels — below this level, oil physically cannot be pumped out
- Comfortable operating range: 25-60 million barrels
- Pipeline connectivity: Major hub connecting pipelines from the Permian, Midcontinent, Canada (Keystone/Marketlink), and running south to the Gulf Coast (Seaway, MarketLink reverse)

**How Cushing levels drive WTI**:
- **Rising inventories** (builds): Increase storage competition, push WTI front month lower relative to deferred months (contango widens)
- **Falling inventories** (draws): Reduce available supply for delivery, tighten the front month, can push WTI into backwardation
- **Near tank tops** (>75 million): Severe contango, potential for front-month collapse as deliverable supply exceeds demand
- **Near operational minimum** (<25 million): Sharp backwardation as barrels become scarce for delivery

### The April 2020 Event: WTI Goes Negative

On April 20, 2020, the May WTI futures contract settled at **-$37.63/bbl** — the first time a major crude benchmark traded below zero. Here is exactly what happened:

1. **COVID demand destruction**: Global oil demand fell by ~20-25 million bbl/d in April 2020 (from ~100 to ~75-80 million). The demand decline was unprecedented in speed and scale.
2. **OPEC+ price war**: Saudi Arabia and Russia flooded the market with extra barrels in March-April before agreeing to cut.
3. **Cushing filled up**: Inventories surged to ~65 million barrels approaching the ~76 million barrel operational limit. Physical traders could not find storage anywhere.
4. **Futures expiry mechanics**: The May WTI contract expired on April 21. Holders of long positions at expiry must take physical delivery at Cushing. If you cannot take delivery (no storage), you must sell at any price.
5. **Cascading liquidation**: Financial longs (ETFs like USO, retail traders, specs) who had no intention or ability to take physical delivery were forced to sell at any price on the last trading day. Buyers disappeared. The price went negative — meaning sellers were paying buyers to take oil off their hands.

**Trading lessons from April 2020**:
- Understand the delivery mechanism of any futures contract you trade
- Financial investors in physically-delivered contracts face real delivery risk at expiry
- Cushing capacity is a hard physical constraint on WTI pricing
- The spread between the first and second month (the prompt spread) is the key signal — when it blows out in contango, it signals physical market stress
- After the event, CME modified its systems to handle negative prices, and USO restructured its roll strategy

## Global Crude Flows and Chokepoints

### Major Trade Routes

| Route | Volume (million bbl/d) | Key Feature |
|-------|----------------------|-------------|
| Middle East to Asia | ~21 | Largest single crude flow. Saudi, Iraq, UAE, Kuwait to China, India, Japan, South Korea. Via Strait of Hormuz. |
| Russia to China / India | ~5-6 | Grown dramatically post-2022 sanctions. Pipe (ESPO) + seaborne (Urals via shadow fleet tankers). |
| West Africa to Asia / Europe | ~3-4 | Nigerian, Angolan crude. Competes with US shale for European market share. |
| US Gulf to Europe / Asia | ~4-5 | Post-export ban repeal (2015). Primarily light sweet crude (WTI Midland, Eagle Ford). Growing every year. |
| Canada to US | ~4 | Overwhelmingly heavy sour (WCS). Via Keystone, Enbridge mainline, now Trans Mountain to Pacific Coast. |
| North Sea to Europe | ~2-3 | Declining production. Brent basket underpins the benchmark but volumes are shrinking. |
| Latin America to US Gulf | ~1-2 | Heavy crudes (Maya, Castilla) feed Gulf Coast complex refiners. Declining as Venezuela output fell from 3M to <1M bbl/d. |

### Critical Chokepoints

| Chokepoint | Throughput (million bbl/d) | Risk | Historical Disruptions |
|------------|--------------------------|------|----------------------|
| Strait of Hormuz | ~21 | Iran could theoretically mine or blockade. 21% of global supply at risk. | Tanker wars (1980s), Iran tensions (2019 tanker attacks). Brent could spike $20-50 on closure. |
| Strait of Malacca | ~16 | Piracy risk, single route for China/Japan/Korea oil imports. | Rare disruption, but a military conflict scenario would be catastrophic for Asian energy security. |
| Suez Canal / SUMED Pipeline | ~7-9 | Disruption adds 10-15 days to Europe-Asia routes via Cape of Good Hope. | 2021 Ever Given blockage, 2023-24 Houthi attacks forced mass rerouting. |
| Bab el-Mandeb | ~7-8 | Gateway to Suez from the south. Yemen (Houthi) conflict zone. | 2023-24 Houthi missile/drone attacks on commercial tankers. |
| Turkish Straits (Bosphorus) | ~3-4 | Kazakh and some Russian crude exits Black Sea. Physical width constraint, ice risk. | Regular congestion, insurance cost spikes. |
| Panama Canal | ~1 | Smaller crude volumes, but LPG and LNG transits are significant. | 2023-24 drought reduced daily transits from 36 to ~22. |

**Trading implications**: Chokepoint disruptions create immediate risk premiums. Hormuz risk adds $2-10/bbl to Brent depending on severity. Suez rerouting widens the WTI-Brent spread (increases tanker demand and shipping costs) and pushes up freight rates. Track tanker rates (Baltic Dirty Tanker Index) and shipping route data for early signals.

## The Crude Oil Forward Curve

The forward curve is the set of all futures prices from the front month out to the longest-dated contract (7+ years for crude). Its shape tells you about the physical market balance.

### Contango (Front Month < Deferred Months)

Signals oversupply or weak near-term demand. Storage is available and economically attractive.

**The storage trade (cash-and-carry arbitrage)**:

1. Buy physical crude at spot price
2. Store it (in tanks at Cushing, on tankers as floating storage, or in pipelines)
3. Simultaneously sell a deferred futures contract to lock in the higher future price
4. Deliver the physical crude against the futures contract at expiry

**Profit = Forward spread - Cost of carry**

Cost of carry = storage cost + financing cost + insurance + quality/loss allowance

**Example**:
- Spot WTI: $70.00/bbl
- 6-month forward WTI: $73.50/bbl
- Spread: $3.50/bbl
- Storage cost (Cushing): $0.40/bbl/month x 6 = $2.40
- Financing (5% annual on $70): $1.75
- Insurance/other: $0.15
- Total cost of carry: $4.30/bbl
- Profit: $3.50 - $4.30 = **-$0.80 (trade does NOT work — contango is too narrow)**

Now change the 6-month forward to $75.50:
- Spread: $5.50/bbl
- Same cost of carry: $4.30/bbl
- Profit: $5.50 - $4.30 = **+$1.20/bbl (trade works — lock in risk-free profit)**

When contango exceeds cost of carry, storage fills up. When it narrows below, storage draws down. This arbitrage mechanism links the physical and paper markets.

**Supercontango**: Rare extreme contango (>$10-15 spread to 6-month). Occurred in April 2020 ($15-20 1-month contango) and 2008-09. During supercontango, traders charter VLCCs (Very Large Crude Carriers, 2M barrels each) as floating storage at $30,000-80,000/day because land storage is full. If you can source storage during supercontango, the returns are exceptional.

### Backwardation (Front Month > Deferred Months)

Signals tight supply or strong near-term demand. Inventory is being drawn. The market is paying a premium for immediate delivery.

**Convenience yield**: The implicit benefit of holding physical inventory — the ability to meet immediate demand, avoid stockouts, or capitalize on spot market tightness. In backwardation, the convenience yield exceeds the cost of storage. Refineries pay a premium for prompt barrels because they need to keep running.

**Backwardation characteristics**:
- Discourages storage (why store when the front is worth more than deferred?)
- Incentivizes inventory drawdowns
- Producers benefit (they sell at higher prompt prices)
- Typically bullish for sentiment — associated with tight markets and higher absolute prices
- No theoretical limit — during crises, front month can be $10-15+ above deferred months

**Reading the curve**: Steep contango ($2+/month) = very oversupplied. Mild contango ($0.30-0.80/month) = balanced-to-loose. Flat = equilibrium. Mild backwardation ($0.50-1.50) = tight. Steep backwardation ($2+) = crisis or supply disruption.

**Key insight**: The shape of the curve often matters more for trading than the absolute price level. A market at $80 in backwardation is fundamentally tighter than a market at $80 in contango. Calendar spreads trade the curve shape directly.

## Key Crude Oil Trades

### 1. Flat Price (Directional)
Long or short outright WTI or Brent. Highest risk, highest reward. Margin requirement: ~$5,000-8,000 per contract ($1/bbl move = $1,000 P&L on 1 contract of 1,000 barrels). Daily ranges of $1-3/bbl are normal, $5+ on event days (OPEC decisions, geopolitical events, inventory surprises). Driven by macro, OPEC, geopolitics.

### 2. Calendar Spreads
Long one expiry, short another. These trade the curve shape (contango/backwardation), not the absolute price. Lower margin (~$1-2K vs ~$6K outright).

- **Prompt spread** (Month 1 vs. Month 2): Most liquid, most volatile calendar spread. Directly reflects near-term supply/demand tightness. Typical range: -$2.00 to +$2.00. Driven by Cushing levels, weekly EIA data, refinery demand.
- **Seasonal spread** (e.g., Dec vs. Jun): Captures summer driving season demand vs. winter. Longer-dated, smoother, mean-reverting.
- **Butterfly** (e.g., long Mar, short 2x Jun, long Sep): Trades the curvature of the forward curve. Lower risk, mean-reverting. Used to isolate kinks in the curve.

**Example**: You believe Cushing draws will tighten the front end over the next month. Buy the prompt spread (long Month 1, short Month 2). If backwardation increases from $0.50 to $1.50, you make $1.00/bbl = $1,000 per spread.

### 3. WTI-Brent Spread
Trade directly via CME's WTI-Brent spread futures contract or by going long CL / short B (or vice versa). A core macro crude oil trade reflecting US vs. international relative value. Driven by Cushing inventory, US export capacity utilization, and global disruptions.

### 4. Grade Differentials
Relative value between crude grades:
- **WTI vs. Mars (sour differential)**: Widens when light sweet is in high demand or sour supply is plentiful. Narrows when complex refinery demand is strong and they bid up sour crude.
- **LLS vs. WTI**: Gulf Coast vs. Cushing. Reflects pipeline logistics and export economics. When Gulf Coast exports are strong, LLS trades at a premium.
- **WCS vs. WTI**: Heavy-light differential. Driven by Canadian pipeline capacity (TMX, Keystone, Enbridge), diluent costs, and Gulf Coast complex refinery demand. Range: -$12 to -$25 normally, blew out to -$45 in late 2018 during pipeline constraints.
- **Brent vs. Dubai (EFS)**: Light sweet vs. medium sour international. Reflects Asian refinery demand for sour crude and Middle East supply.

### 5. Time Spreads with Physical Context
Experienced traders combine calendar spreads with physical knowledge. If you know a pipeline expansion will add 500K bbl/d of Permian takeaway capacity in Q3, you can trade the Midland-Cushing basis tightening and the impact on WTI calendar spreads. If you know a major refinery turnaround will reduce crude demand in March, you can position for the front spread to weaken. This is where physical understanding creates financial edge.

## Reading

- <a class="source-link" data-source="oil101">Oil 101</a> — chapters 6-8. Covers crude grades, the shale revolution, transportation, Cushing storage, and global crude flows.
- <a class="source-link" data-source="eia">EIA Today in Energy</a> — the recent articles on US crude production records, Middle East import dependency, and tanker rate spikes are directly relevant.
- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 3 (The Forward Curve). Covers contango, backwardation, and calendar spread mechanics for crude oil.

Also recommended: **The Prize** by Daniel Yergin. A Pulitzer Prize-winning history of the global oil industry. 900+ pages but reads like a thriller.`
  },
  {
    id: '03',
    name: 'Natural Gas',
    desc: 'Henry Hub, TTF, LNG, seasonality, storage',
    lesson: 
