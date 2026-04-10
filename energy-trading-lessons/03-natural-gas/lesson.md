# Module 03 — Natural Gas

---

## What Is Natural Gas

Natural gas is primarily methane (CH4, ~95%), with small amounts of ethane, propane, butane (collectively "natural gas liquids" or NGLs), and trace CO2 and nitrogen. It is the cleanest-burning fossil fuel (~50% less CO2 than coal per unit of energy) and plays a growing role in power generation globally.

**Sources**: Conventional gas wells, shale formations (Marcellus, Haynesville), and "associated gas" produced alongside oil (Permian). The distinction between dry gas (methane only) and wet gas (methane + NGLs) matters — wet gas basins produce valuable liquids that can subsidize drilling even when gas prices are low.

**Key units**:
- **MMBtu** (million British Thermal Units) — the standard pricing unit for US gas. One MMBtu is approximately the energy in 1,000 cubic feet of gas.
- **Mcf** (thousand cubic feet) — volume measure. 1 Mcf ≈ 1.037 MMBtu.
- **Bcf** (billion cubic feet) — used for daily production and weekly storage changes. US produces ~105 Bcf/d.
- **Tcf** (trillion cubic feet) — used for annual production, reserves, and storage capacity. US annual consumption: ~32 Tcf.

## Henry Hub — The US Benchmark

Henry Hub is a physical pipeline interconnection point in Erath, Louisiana, where 13 interstate and intrastate pipelines converge. Its central location in the US pipeline grid and proximity to the Gulf Coast LNG export terminals makes it the natural pricing point for US gas.

**NYMEX Natural Gas Futures (NG)**:
- Contract size: 10,000 MMBtu
- Tick size: $0.001/MMBtu = $10 per tick
- At $3.50/MMBtu, one contract = $35,000 notional
- Delivery: Physical at Henry Hub
- Contract months: 12 consecutive months listed, plus longer-dated contracts out to ~12 years
- Most liquid natural gas futures contract in the world

## The Seasonal Cycle

Natural gas has the strongest seasonality of any major commodity, driven by the fundamental mismatch between when gas is consumed (winter heating) and when it can be most efficiently produced (year-round).

```
April - October:  INJECTION SEASON — gas goes into underground storage, building a buffer for winter
November - March: WITHDRAWAL SEASON — gas comes out of storage to meet heating demand
```

**Typical storage trajectory**:
- End of withdrawal (late March): ~1.5-2.0 Tcf remaining in storage
- Summer injection builds ~70-90 Bcf/week in shoulder months, ~30-50 Bcf/week during summer peak (AC demand competes)
- End of injection (October 31): ~3.5-3.8 Tcf — this is the winter cushion
- Winter withdrawals of 100-200+ Bcf/week during cold snaps

**The November 1 storage target**: The market obsessively focuses on projected end-of-October storage levels. This is the number that determines whether winter supply is comfortable or tight. Below 3.2 Tcf entering winter signals risk. Above 3.9 Tcf signals oversupply. The forward curve reflects this: winter months (Dec-Feb) trade at a premium to summer months (Jun-Aug), typically $0.50-2.00/MMBtu higher. This seasonal spread is the most predictable pattern in energy.

## Storage — The Most Important Variable

US working gas storage capacity: ~4.7 Tcf across ~400 underground storage facilities. Three facility types:
- **Depleted reservoirs** (~80% of capacity): Former gas fields. Large volume but slow injection/withdrawal rates.
- **Salt caverns** (~5% of capacity, mainly Gulf Coast): Fast cycling. Can inject/withdraw quickly. Used for short-term balancing.
- **Aquifers** (~15%, mainly Midwest): Moderate speed. Geological limitations on withdrawal rates.

### Key Storage Levels

| Level | Range | Market Implication |
|-------|-------|-------------------|
| Comfortable end-of-injection (Oct 31) | 3.5-3.8 Tcf | Well-supplied for winter. Prices stable. |
| Low end-of-injection | < 3.2 Tcf | Tight winter ahead. Prices rise, winter spreads widen. |
| High end-of-injection | > 3.9 Tcf | Oversupplied. Prices fall, contango deepens. Risk of hitting capacity (~4.7 Tcf). |
| Comfortable end-of-withdrawal (Mar 31) | 1.5-2.0 Tcf | Normal. Market relaxed about supply. |
| Danger zone end-of-withdrawal | < 1.2 Tcf | Acute shortage risk. Prices can spike dramatically. |

### The EIA Thursday Report

Published every Thursday at 10:30 ET. Reports the weekly change in US working gas in storage (net injection or withdrawal, in Bcf). Regional breakdown: East, Midwest, Mountain, Pacific, South Central (salt + non-salt).

**How to trade it**: Consensus estimates circulate beforehand (Bloomberg survey, analyst models). **The price move is driven by the surprise** — actual minus consensus.

- A 5-10 Bcf miss from consensus: $0.05-0.15/MMBtu move
- A 15-20 Bcf miss: $0.15-0.30 move
- A 25+ Bcf miss: $0.30+ move, sometimes $0.50+ on extreme surprises

Build your own storage model (tracking degree days, production, LNG feedgas, power burn) to estimate the weekly number independently. When your estimate diverges from consensus, that is a trading signal.

**Storage vs. 5-year average**: THE key metric. Storage 200+ Bcf above the 5-year average = very bearish. Storage 200+ Bcf below = very bullish. The surplus/deficit trajectory (whether you are moving toward or away from the 5-year average) matters as much as the absolute level.

**Storage economics**: When the summer-winter spread (e.g., Oct-Jan) exceeds the cost of injection + storage + withdrawal (typically $0.20-0.40/MMBtu total), it is profitable to inject gas in summer and withdraw in winter. This is the gas equivalent of the crude contango storage trade. The spread effectively prices in the market's view of winter scarcity.

## Weather — The Dominant Short-Term Driver

### Degree Day Definitions

**Heating Degree Days (HDD)**: For each day, HDD = max(0, 65°F - average daily temperature). A day with an average temperature of 30°F contributes 35 HDDs. More HDDs = more furnaces/boilers running = more gas burned for heating. Cumulative weekly HDDs drive storage withdrawals in winter.

**Cooling Degree Days (CDD)**: For each day, CDD = max(0, average daily temperature - 65°F). A day with an average of 90°F contributes 25 CDDs. More CDDs = more air conditioning = more gas-fired power generation.

**Gas-weighted degree days (GWDD)**: Population-weighted to reflect actual demand centers. A cold snap over the densely populated Northeast and Midwest matters far more than the same cold over rural Montana. Major gas demand centers: Northeast corridor (Boston to DC), Great Lakes/Midwest (Chicago, Detroit), Texas (both heating and cooling), and California.

### Weather Models

- **GFS (Global Forecast System)**: American model run by NOAA. Runs 4x daily (00z, 06z, 12z, 18z UTC). Free and publicly available. Provides forecasts out to 16 days. Traders watch every model run for changes.
- **ECMWF (European Centre for Medium-Range Weather Forecasts)**: European model. Generally considered more accurate for 6-10 day forecasts. Runs 2x daily (00z, 12z). Requires paid subscription. The "Euro model" is the gold standard.

**How traders use models**: The market reacts to **model shifts** — when a forecast changes from warm to cold (or vice versa), gas moves immediately. A significant cold shift in the 6-10 day forecast (e.g., going from 5 HDDs above normal to 15 HDDs above normal) can move Henry Hub $0.10-0.30 in hours. Traders compare the latest model run to the previous run and to the competing model.

**Impact timeline**:
- Same-day/next-day: Spot and cash market prices respond to real-time weather
- 1-5 day forecast: Drives prompt month volatility
- 6-14 day forecast: Primary driver of front-month futures. This is where most weather-based trading happens.
- Beyond 14 days: Forecasts lose skill rapidly. Market relies on seasonal norms and analogs (comparing current patterns to historical years).

## Supply

US dry gas production: ~105 Bcf/d — the world's largest. Key supply basins:

| Basin | Production | Type | Key Characteristic |
|-------|-----------|------|-------------------|
| Appalachia (Marcellus/Utica) | ~35 Bcf/d | Dry gas + some NGLs | Largest US gas basin by far. Low-cost, prolific wells. Pipeline-constrained heading eastward and southward. Dominion South basis often negative. |
| Permian (TX/NM) | ~15 Bcf/d | Associated gas | Produced alongside oil. Output tied to oil drilling, not gas price. When oil is $80+, associated gas floods the market regardless of gas price. Key bearish structural factor. |
| Haynesville (LA/TX) | ~14 Bcf/d | Dry gas | Most price-responsive basin — drilling ramps quickly when gas prices rise above $3.00-3.50. Near Gulf Coast LNG terminals, so minimal transportation discount. |
| Eagle Ford (TX) | ~7 Bcf/d | Associated gas + dry gas | Mix of oil and gas wells. Associated gas component tied to oil economics. |
| Other (DJ Basin, Bakken, conventional, Gulf of Mexico) | ~34 Bcf/d | Various | Conventional declining, GOM steady, DJ Basin regulatory risk. |

**Associated gas**: Gas produced as a byproduct of oil drilling (primarily Permian). When oil prices are high, oil drilling increases, and associated gas production rises regardless of gas prices — it is essentially free gas that must go somewhere. This can suppress Henry Hub even when gas demand is strong. The "call on associated gas" is a structural bearish factor for Henry Hub whenever oil prices are high and Permian drilling is active.

**Pipeline constraints**: Production can be stranded if pipeline takeaway capacity is insufficient. Appalachian gas has historically been constrained heading east and south due to regulatory opposition to new pipeline construction. Permian gas competes with oil for limited pipeline space out of West Texas. When constraints bind, local basis collapses (Waha has traded as low as -$10/MMBtu) while destination hubs like Henry Hub hold firm.

## Demand

US natural gas demand by sector (~105 Bcf/d total consumption + exports):

| Sector | Share | Volume | Characteristics |
|--------|-------|--------|----------------|
| Power generation | ~35% | ~37 Bcf/d | Largest and growing. Gas competes with coal and renewables in the dispatch stack. Weather-sensitive (summer cooling load). |
| Residential/commercial | ~25% | ~26 Bcf/d | Heating. Highly seasonal — winter demand is 3-4x summer. Driven by HDDs. |
| Industrial | ~22% | ~23 Bcf/d | Fertilizer (ammonia/urea), petrochemicals (ethylene), glass, cement. Relatively stable but price-sensitive at the margin. |
| LNG exports | ~13% | ~14 Bcf/d | Rapidly growing. The new structural demand source linking US gas to global prices. |
| Mexican pipeline exports | ~5% | ~5 Bcf/d | Steady growth as Mexico builds gas-fired power plants near the US border. |

### Gas-Coal Switching

The most important demand-side mechanism for gas prices. In the power generation sector, gas and coal compete for dispatch.

- **When Henry Hub falls below ~$2.00-2.50/MMBtu**: Gas plants are cheaper to run than most coal plants. Gas displaces coal from the generation stack. Gas demand for power rises.
- **When Henry Hub rises above ~$3.50-4.00/MMBtu**: Coal becomes competitive again. Coal displaces gas. Gas demand for power falls.

This switching dynamic creates a soft floor (~$2.00) and soft ceiling (~$4.00-4.50) for Henry Hub during periods of stable coal prices. It is a natural mean-reverting mechanism. The exact switching price depends on regional coal costs, heat rates of specific plants, and carbon/emissions regulations.

## LNG — The Globalizer

LNG (Liquefied Natural Gas): gas cooled to -260°F (-162°C), reducing its volume 600x for transport by specialized tankers. The liquefaction process is energy-intensive (uses ~10% of the gas as fuel).

### US LNG Export Capacity (~14 Bcf/d)

| Terminal | Location | Capacity (Bcf/d) | Operator | Notes |
|----------|----------|-------------------|---------|-------|
| Sabine Pass | Cameron Parish, LA | ~5.0 | Cheniere | First US LNG export terminal (2016). 6 trains. |
| Corpus Christi | TX | ~2.5 | Cheniere | 3 trains + Stage 3 expansion underway. |
| Cameron | Hackberry, LA | ~2.1 | Sempra | 3 trains. |
| Freeport | Freeport, TX | ~2.1 | Freeport LNG | 3 trains. Was offline Jun 2022 - Mar 2023 after an explosion. |
| Calcasieu Pass | Cameron Parish, LA | ~1.5 | Venture Global | Newer facility. |
| Additional under construction | Various | ~5-8 (by 2027-28) | Various | Golden Pass (ExxonMobil/QatarEnergy), Plaquemines (Venture Global), others. |

### Global Gas Benchmarks

- **JKM (Japan-Korea Marker)**: Asian LNG spot benchmark. Published by Platts. Quoted in $/MMBtu.
- **TTF (Title Transfer Facility)**: European gas benchmark. Traded on ICE. Dutch virtual hub. Replaced UK NBP as the European reference. Quoted in EUR/MWh (convert to $/MMBtu: divide by ~3.412 and adjust for EUR/USD).

### LNG Export Margin Calculation

```
LNG Export Margin = Destination Price - Henry Hub - Shipping Cost - Liquefaction Fee

Example (US to Asia):
JKM:                $14.00/MMBtu
Henry Hub:          -$3.50/MMBtu
Shipping:           -$1.25/MMBtu (Gulf Coast to NE Asia, ~25 days)
Liquefaction:       -$2.50/MMBtu (tolling fee, varies by contract)
----------------------------------------------
Net margin:          $6.75/MMBtu  → PROFITABLE, terminal runs at full capacity

Example (margin collapse):
JKM:                $8.00/MMBtu
Henry Hub:          -$3.50/MMBtu
Shipping:           -$1.25/MMBtu
Liquefaction:       -$2.50/MMBtu
----------------------------------------------
Net margin:          $0.75/MMBtu  → Marginal. Some cargoes may be cancelled.
```

**Impact on Henry Hub**: LNG exports have structurally lifted Henry Hub by ~$0.50-1.00/MMBtu compared to the pre-LNG era (pre-2016). When a major terminal goes offline — as when Freeport LNG was shut down June 2022 to March 2023 after an explosion — ~2 Bcf/d of demand disappears overnight, and Henry Hub drops. Conversely, when a new terminal comes online, it adds structural demand. Track daily LNG feedgas data (available from Marine Traffic/Kpler/Bloomberg) as a real-time demand signal.

## Basis Trading

Basis = Price at Location - Henry Hub. Basis differentials are driven by pipeline infrastructure, local supply/demand balances, and seasonal patterns. Basis trading is where deep physical knowledge creates the most trading edge.

### Key Regional Hubs

| Hub | Typical Basis to HH | Extreme Range | Primary Driver |
|-----|---------------------|---------------|----------------|
| Waha (Permian, TX) | -$0.50 to -$2.00 | Down to -$10+ (has gone negative outright) | Massive associated gas production from Permian oil drilling vs. limited pipeline takeaway to Gulf Coast. New pipelines narrow basis; pipeline delays widen it. |
| Algonquin Citygate (New England) | +$0.50 to +$2.00 | Up to +$20-50 in winter cold snaps | Very limited pipeline capacity into New England. No new pipelines built in decades (local opposition). Cold snaps cause acute gas shortage — LNG imports by tanker to Everett, MA fill the gap at extreme cost. |
| SoCal Citygate (California) | +$1.00 to +$3.00 | Up to +$10-20 during heat waves or pipeline outages | Limited pipeline into Southern California. Aliso Canyon storage facility restricted since 2015 leak. Heat waves spike power demand (AC) and gas burns. |
| Chicago Citygate | +$0.10 to +$0.50 | +$1-3 in polar vortex cold | Midwest heating demand center. Well-connected to multiple supply sources (Appalachia, Gulf Coast, Rockies), so normally tight basis. Blows out only in extreme cold. |
| Dominion South (Appalachia) | -$0.30 to -$1.00 | Down to -$2+ | Marcellus production exceeds pipeline takeaway heading east and south. New pipeline capacity narrows this basis; production growth widens it. |
| AECO (Alberta, Canada) | -$0.50 to -$2.00 | Down to -$5+ | Canadian gas supply exceeds regional demand and export pipeline capacity. LNG Canada terminal (under construction) could structurally shift this. |

**Basis is physical**: If you know the pipeline map — where the bottlenecks are, what new capacity is coming online (and when), what happens to flows in extreme cold or heat — you can form high-conviction basis views that the broader market may not have. This is where fundamental research on infrastructure creates the most edge.

## Key Natural Gas Trades

### 1. Flat Price (Directional)
Long/short Henry Hub. Driven by weather, storage trajectory, production trends, LNG demand. At $3.50/MMBtu, one NG contract = $35,000 notional. A $0.10 move = $1,000 per contract. Gas can move $0.20-0.50 in a single session on weather shifts or storage surprises.

### 2. Calendar Spreads
The heart of gas trading. The seasonal cycle creates predictable spread structures:
- **Summer/Winter** (e.g., Oct/Jan or Apr strip vs. Jan strip): The core seasonal trade. Buy the spread when you expect a tight winter; sell when you expect comfortable storage.
- **Winter/Winter** (e.g., Jan 2027 vs. Jan 2028): Trades the year-over-year fundamental outlook. Driven by production growth, LNG capacity additions, power demand trends.
- **March/April (Widowmaker)**: See below. The most dangerous and volatile calendar spread in energy.

### 3. Basis Spreads
Henry Hub vs. regional pricing points. Requires deep physical and infrastructure knowledge. Examples: Waha-Henry Hub (Permian takeaway), Algonquin-Henry Hub (New England winter), SoCal-Henry Hub (California heat).

### 4. Weather Trades
Positioning ahead of cold/warm model shifts. Traders monitor every GFS and ECMWF run and trade the prompt month (and sometimes the prompt week in physical markets) based on forecast changes. Short duration, high frequency. Requires real-time weather data subscriptions and fast execution.

### 5. Storage Report Trades
Building a proprietary storage estimate and positioning for the EIA Thursday release when your number diverges from consensus. If you estimate a 90 Bcf injection and consensus is 80 Bcf, you sell ahead of the report expecting a bearish surprise. Requires a storage model incorporating: degree days, production, LNG feedgas, power burn (from generation data), industrial demand, and imports/exports.

## The Widowmaker — March/April Spread

The March/April natural gas spread is called the "widowmaker" because it has destroyed traders and entire funds.

**Why it is so volatile**: March is the last month of winter (withdrawal season). April is the first month of summer (injection season). The price difference between them reflects the market's assessment of how tight supply will be at the very end of winter.

- **Mild winter**: Storage ends winter at comfortable levels (1.7-2.0+ Tcf). March premium to April is small ($0.20-0.50). Smooth transition.
- **Cold winter**: Storage draws deeply. March gas is scarce and expensive relative to April. Spread can blow out to $2-5+.
- **Catastrophic winter**: If storage approaches danger zone (<1.2 Tcf), the March premium can reach $5-10+ as the market prices in the possibility of physical shortage.

**The Amaranth Advisors disaster (2006)**: Amaranth, a multi-strategy hedge fund, accumulated a massive position in winter/summer natural gas calendar spreads — effectively betting that winter gas would be expensive relative to summer. Their position was enormous — reportedly ~100,000 contracts, representing a significant portion of open interest. When the market moved against them (a warm early fall reduced winter risk premium), they could not exit their position without moving the market further against themselves. They lost **$6 billion** in approximately two weeks — one of the largest trading losses in history. The fund collapsed entirely.

**Key lessons from Amaranth**: Position size relative to market liquidity is everything. Even a correct directional view is worthless if your position is too large to exit. The March/April spread can move $1-2+ in a single day during volatile periods. Respect the name.

## Reading

- <a class="source-link" data-source="eia">EIA Today in Energy</a> — the recent articles on natural gas production growth projections and NGPL export records are directly relevant. Read gas-focused articles weekly.
- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 4 (Spread Trading), specifically the basis spread discussion. Covers Henry Hub vs. regional pricing and pipeline-driven basis.

Also recommended: **RBN Energy blog** (rbnenergy.com). The best free resource for North American gas fundamentals. Daily posts on storage, LNG, basis, and NGLs. Also: **The Handbook of Energy Trading** by Stefano Fiorenzani for storage valuation and seasonal spread modeling.`
  },
  {
    id: '04',
    name: 'Refined Products',
    desc: 'Gasoline, diesel, jet fuel, refining economics',
    lesson: 
