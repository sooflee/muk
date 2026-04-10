# Module 04 — Refined Products

---

## What Comes Out of a Barrel

Crude oil is not consumed directly — it must be refined into usable products. A typical barrel of US crude (42 gallons) processed through a complex Gulf Coast refinery running light sweet crude yields approximately:

| Product | Yield % | Gallons per Barrel | Price Benchmark | Exchange Contract |
|---------|---------|-------------------|----------------|-------------------|
| Gasoline | ~45% | ~19 gal | RBOB | RB (NYMEX) — 42,000 gal, $/gal |
| Diesel / Heating Oil | ~27% | ~11 gal | ULSD | HO (NYMEX) — 42,000 gal, $/gal |
| Jet Fuel | ~10% | ~4 gal | Platts Jet (OTC) | No liquid exchange contract |
| Heavy Fuel Oil | ~4% | ~1.7 gal | HSFO / VLSFO | ICE — $/metric ton |
| LPG (propane, butane) | ~4% | ~1.7 gal | Mont Belvieu propane | Various |
| Petroleum Coke | ~5% | ~2.1 gal equivalent | Pet coke | OTC |
| Other (asphalt, lubricants, petrochemicals) | ~5% | ~2.1 gal | Various | OTC |

**Note**: Total yield actually exceeds 100% of input volume due to "processing gain" — cracking heavy molecules into lighter ones increases total volume by ~5-6%. A refinery inputs 1 barrel of crude but outputs ~1.05-1.06 barrels equivalent of products.

Yields vary significantly with crude quality and refinery configuration. Heavy sour crude yields more fuel oil and coke, less gasoline and diesel. Complex refineries with FCC units, hydrocrackers, and cokers can upgrade heavy fractions into lighter, higher-value products — which is why complex refineries earn higher margins on cheap heavy crude.

## Key Product Benchmarks

| Product | Contract Name | Ticker | Exchange | Contract Size | Unit | Conversion to $/bbl |
|---------|--------------|--------|----------|--------------|------|---------------------|
| Gasoline | RBOB (Reformulated Blendstock for Oxygenate Blending) | RB | NYMEX | 42,000 gallons | $/gallon | Multiply by 42 |
| Diesel / Heating Oil | NY Harbor ULSD (Ultra-Low Sulfur Diesel) | HO | NYMEX | 42,000 gallons | $/gallon | Multiply by 42 |
| Jet Fuel | Platts Jet (physical price assessment) | N/A | OTC | Cargo basis | $/gallon | Multiply by 42 |
| High Sulfur Fuel Oil | 3.5% Fuel Oil | FO | ICE | 1,000 MT | $/metric ton | Divide by ~6.35 (bbl/MT for fuel oil) |
| Low Sulfur Fuel Oil | 0.5% VLSFO | N/A | ICE | 1,000 MT | $/metric ton | Divide by ~6.35 |

**The critical conversion**: RBOB and ULSD are quoted in **$/gallon**. Crude oil is quoted in **$/barrel**. To compare them directly: **$/gallon x 42 = $/barrel**.

Example: RBOB at $2.50/gallon = $2.50 x 42 = **$105.00/barrel**. This is the number you use in crack spread calculations.

## Crack Spreads — The Core Trade

A **crack spread** is the difference between the value of refined products and the cost of crude oil input. It represents the refiner's gross margin (before operating costs, which run ~$4-8/bbl for a US Gulf Coast refinery).

The name comes from the catalytic cracking process that "cracks" heavy hydrocarbon molecules into lighter ones.

### Crack Spread Structures with Worked Examples

Assume: **RBOB = $2.50/gal ($105.00/bbl), ULSD = $2.80/gal ($117.60/bbl), WTI = $78.00/bbl**

**1:1 Gasoline Crack** (simplest):
- Buy 1 barrel crude, sell 1 barrel gasoline
- = RBOB in $/bbl - WTI = $105.00 - $78.00 = **$27.00/bbl**
- On exchange: Buy 1 CL, Sell 1 RB

**1:1 Diesel Crack**:
- Buy 1 barrel crude, sell 1 barrel diesel
- = ULSD in $/bbl - WTI = $117.60 - $78.00 = **$39.60/bbl**
- On exchange: Buy 1 CL, Sell 1 HO

**3:2:1 Crack Spread** (industry standard — approximates typical refinery output):
- Buy 3 barrels crude, sell 2 barrels gasoline + 1 barrel diesel
- = (2 x RBOB $/bbl + 1 x ULSD $/bbl) / 3 - WTI $/bbl
- = (2 x $105.00 + 1 x $117.60) / 3 - $78.00
- = ($210.00 + $117.60) / 3 - $78.00
- = $327.60 / 3 - $78.00
- = $109.20 - $78.00 = **$31.20/bbl**
- On exchange: Buy 3 CL, Sell 2 RB + 1 HO

**2:1:1 Crack Spread**:
- Buy 2 barrels crude, sell 1 barrel gasoline + 1 barrel diesel
- = (1 x RBOB $/bbl + 1 x ULSD $/bbl) / 2 - WTI $/bbl
- = ($105.00 + $117.60) / 2 - $78.00
- = $111.30 - $78.00 = **$33.30/bbl**
- On exchange: Buy 2 CL, Sell 1 RB + 1 HO

**5:3:2 Crack Spread** (more realistic refinery yield):
- Buy 5 barrels crude, sell 3 barrels gasoline + 2 barrels diesel
- = (3 x RBOB $/bbl + 2 x ULSD $/bbl) / 5 - WTI $/bbl
- = (3 x $105.00 + 2 x $117.60) / 5 - $78.00
- = ($315.00 + $235.20) / 5 - $78.00
- = $550.20 / 5 - $78.00
- = $110.04 - $78.00 = **$32.04/bbl**
- On exchange: Buy 5 CL, Sell 3 RB + 2 HO

### Historical Crack Spread Ranges (3:2:1)

| Environment | 3:2:1 Crack ($/bbl) | Context |
|-------------|---------------------|---------|
| Depressed | < $10 | Demand destruction, oversupplied products. Refineries consider shutdowns at this level. |
| Normal/low | $10-15 | Below-average but sustainable for efficient refineries. |
| Normal | $15-25 | Typical operating range. Refineries profitable. |
| Strong | $25-35 | Tight product markets. High refinery margins. Incentivizes max utilization. |
| Extreme | > $35 | Supply crisis. Usually driven by low inventories + high demand + refinery outages. |
| 2022 peak | > $60 | Historic. Post-COVID demand recovery + Russian refining loss + low global inventories + COVID-era refinery closures. |

### What Drives Crack Spreads

- **Refinery utilization**: Lower utilization = less product supply = wider cracks. EIA reports weekly utilization data.
- **Turnaround season**: Spring (Feb-Apr) and fall (Sept-Nov) maintenance reduces throughput, supports cracks.
- **Product inventories vs. seasonal norms**: Low gasoline or distillate stocks relative to the 5-year average = wider cracks.
- **Seasonal demand**: Driving season (May-Sep) supports gasoline cracks. Winter supports diesel/heating oil cracks.
- **Crude quality mix**: If heavy/sour crude supply tightens, complex refineries lose their cheap feedstock advantage. If light sweet supply surges (Permian), simple refinery economics improve.
- **Refinery closures/additions**: COVID era saw ~1.5M bbl/d of global refinery closures. This structural capacity reduction supported cracks well into 2022-23.

## Gasoline Seasonality

### RVP (Reid Vapor Pressure) Specifications

Gasoline volatility is regulated to reduce evaporative emissions (smog). The allowable volatility changes seasonally:

- **Summer blend** (June 1 - September 15): RVP must not exceed **7.8 psi** (some reformulated gasoline areas require 7.0 psi). Lower volatility = harder to produce. Requires more alkylate, reformate, and removal of cheap high-RVP components like butane.
- **Winter blend** (September 16 - May 31): RVP allowed up to **15.0 psi**. Higher volatility = easier and cheaper to produce. Butane (cheap, ~4.5 psi contribution) can be blended in, effectively stretching the gasoline pool.

### The Seasonal Transition

- **February-March**: Refineries begin switching from winter to summer-grade production. Turnarounds are scheduled to coincide with the blend transition.
- **April-May**: Distribution system transitions to summer blend. Gas stations must sell summer-grade by June 1 in most markets.
- **During transition**: Supply of compliant summer gasoline can tighten before driving season begins. This is the period of highest seasonal crack premiums.

### The Seasonal Crack Pattern

Gasoline cracks typically begin rising in February as:
1. Refineries enter spring turnaround (reducing product output)
2. The market anticipates the costly summer-grade blend switch
3. Pre-season inventory building begins for driving season

Cracks peak in **April-May** (tightest supply of summer-grade gasoline ahead of driving season). They begin declining after the July 4th holiday as:
1. Refineries are at maximum summer utilization (90-95%)
2. Driving demand plateaus
3. The September RVP transition approaches (back to easier winter blend)

**Driving season**: Memorial Day (late May) through Labor Day (early September). US gasoline demand rises from ~8.5 million bbl/d in winter to ~9.5+ million bbl/d at the summer peak.

## Diesel / Heating Oil (ULSD)

### Specifications

**Ultra-Low Sulfur Diesel (ULSD)**: Maximum 15 ppm sulfur content (regulation since 2006, down from 500 ppm). This specification was a major regulatory shift that required billions in refinery hydrotreater upgrades.

**Cetane number**: Measures ignition quality (analogous to octane for gasoline, but higher = better for diesel). Minimum standard: 40. Premium diesel: 45-50. Higher cetane = smoother combustion, less noise, better cold-start performance.

### Demand Drivers

- **Trucking and freight**: ~75% of US diesel demand. On-highway diesel consumption is directly tied to economic activity. Key indicators: trucking tonnage index, rail carloads, PMI manufacturing data. When the economy is strong, diesel demand is strong — and vice versa.
- **Construction and mining**: Heavy equipment (excavators, dump trucks, generators) runs on diesel. Tied to infrastructure spending and housing starts.
- **Agriculture**: Tractors, combines, irrigation pumps. Seasonal peaks during planting (spring) and harvest (fall).
- **Heating oil**: Chemically identical to diesel but taxed differently. Concentrated in the **Northeast US (PADD 1)** — about 5.5 million households still use heating oil. Demand is sharply seasonal (November-March) and weather-dependent. Cold snaps in the Northeast can cause rapid inventory draws and price spikes.

### The 2022 Diesel Crisis

In 2022, US distillate inventories fell to their lowest levels since 1951. Contributing factors:
- Post-COVID demand recovery as the economy reopened
- Loss of ~1 million bbl/d of Russian diesel exports to Europe (sanctions)
- COVID-era refinery closures (~1.5M bbl/d global capacity permanently shut)
- Strong trucking demand during the post-COVID logistics boom

ULSD crack spread exceeded **$70/bbl** — unprecedented. Diesel was the tightest product globally and the primary driver of overall refining margins.

## Jet Fuel

**Jet A-1**: The standard commercial aviation fuel. Key specifications:
- Freeze point: below -47°C (must remain liquid at altitude)
- Flash point: above 38°C (safety — resistance to ignition)
- Energy density: ~18,400 BTU/pound (high energy per unit weight is critical for aircraft)
- Sulfur: maximum 0.3%

**Not exchange-tradeable** with liquid futures. Airlines hedge jet fuel exposure using crude oil futures, heating oil/ULSD futures (closest proxy), or OTC jet fuel swaps. The jet-ULSD basis risk is typically small ($0.05-0.15/gal) but can widen during supply dislocations.

**Demand tracks air travel**: COVID reduced jet fuel demand by ~70% in 2020. Recovery has been gradual, reaching ~95% of pre-COVID levels by 2024-25. Business travel recovery has been slower than leisure. Long-term, sustainable aviation fuel (SAF) mandates will reshape jet fuel markets.

## Fuel Oil and IMO 2020

### The IMO 2020 Regulation

The International Maritime Organization (IMO) mandated that ships use fuel with sulfur content **not exceeding 0.5%** (down from the prior 3.5% limit), effective January 1, 2020. Ships must comply by one of three methods:

1. **Burn VLSFO (Very Low Sulfur Fuel Oil)**: 0.5% sulfur. Most common choice. More expensive than HSFO.
2. **Burn MGO (Marine Gasoil)**: Distillate-quality fuel. Most expensive option but always compliant.
3. **Install scrubbers**: Exhaust gas cleaning systems that strip sulfur from stack emissions. Allows continued use of cheap HSFO (3.5% sulfur). Capex of $2-10M per vessel depending on size. Payback depends on the HSFO-VLSFO spread.

### The HSFO-VLSFO Spread as a Trade

HSFO demand dropped ~30% after IMO 2020. VLSFO and MGO demand surged. The **HSFO-VLSFO spread** widened dramatically in late 2019 (peaking at ~$300/MT) and has remained structurally wider since (typically $100-200/MT).

**Scrubber economics**: Ships with scrubbers can still burn cheap HSFO and pocket the HSFO-VLSFO differential. If the spread is $150/MT and a VLCC burns ~60 MT/day, the daily savings = $9,000/day. Over a year, that is ~$3.3 million — making the $5-8M scrubber investment a 2-year payback. When the spread narrows, scrubber economics weaken and fewer newbuilds install scrubbers.

## Refinery Operations

### US Refinery Capacity by PADD

US total: ~18 million bbl/d across ~130 operating refineries.

| PADD | Region | Refining Capacity | Key Characteristics |
|------|--------|-------------------|-------------------|
| PADD 1 | East Coast | ~1.3M bbl/d | Consumer region. Imports products from PADD 3 (Gulf Coast) and Europe. Philadelphia Energy Solutions closure (2019, ~335K bbl/d) was a major loss. |
| PADD 2 | Midwest | ~4.0M bbl/d | Processes Canadian heavy crude (WCS) via Enbridge/Keystone pipelines. Also runs Bakken light. Serves regional demand. Key refineries: Whiting (BP, ~440K bbl/d), Wood River (Phillips 66). |
| PADD 3 | Gulf Coast | ~10.0M bbl/d | **The US refining hub — ~55% of national capacity.** Largest, most complex refineries in the world. Processes everything from WTI light to imported heavy sour. Exports products globally. Hurricane-exposed. |
| PADD 4 | Rockies | ~0.7M bbl/d | Small, isolated market. Few refineries, local supply/demand. Higher product prices due to limited competition. |
| PADD 5 | West Coast | ~2.0M bbl/d | Isolated from other PADDs (no product pipelines connecting to PADD 3). California has strict fuel specifications (CARB gasoline). Higher product prices. Relies on Alaskan crude, California production, and waterborne imports. |

### Utilization and Turnarounds

**Normal utilization**: 90-95% during peak demand periods. US refineries are highly utilized compared to global average (~82%) because they are large, efficient, and well-positioned for export.

**Turnaround season**: Planned maintenance shutdowns ("turnarounds") cluster in two periods:
- **Spring (February-April)**: After winter heating oil demand subsides, before summer driving season. Refineries overhaul FCC units, cokers, and hydrotreaters.
- **Fall (September-November)**: After summer driving season, before winter heating demand. Switch crude slates and reconfigure for maximum distillate production.

Turnarounds typically take 3-6 weeks per unit and are planned 12-18 months in advance. Analyst firms (Turner Mason, IIR Energy) track and publish turnaround schedules. During heavy turnaround periods, national utilization drops to 85-88%, reducing product supply and supporting crack spreads.

**Unplanned outages**: Fires, equipment failures, and hurricanes. Gulf Coast refineries (PADD 3) are highly exposed to Atlantic hurricanes (June-November). An unplanned outage at a large refinery (200K+ bbl/d) can spike local product cracks by $2-5/bbl within hours. The 2017 Hurricane Harvey shut ~4.5M bbl/d of Gulf Coast refining for weeks — gasoline cracks spiked over $30/bbl.

## The Gasoline-Diesel Spread

The **gas-diesel spread** = RBOB ($/bbl) minus ULSD ($/bbl). This relative value spread reflects the tug-of-war between gasoline and diesel demand:

- **Diesel outperforms (spread narrows or goes negative)** when: economic activity is strong (trucking, construction drive diesel demand), winter heating demand surges (Northeast heating oil), distillate inventories are abnormally low, or diesel export demand is strong.
- **Gasoline outperforms (spread widens/goes more positive)** when: driving season demand is strong, gasoline inventories are tight (especially ahead of summer-grade RVP transition), economic slowdown reduces diesel demand while consumer driving holds up.

**Seasonal pattern**: Gasoline tends to outperform in spring/early summer (driving season anticipation + RVP transition). Diesel tends to outperform in fall/winter (heating oil demand + harvest diesel + holiday freight).

The spread also tracks macro cycles — making it a useful relative value trade and economic indicator. A sharp narrowing of the spread (diesel surging) often signals strong economic activity.

## PADDs — Petroleum Administration for Defense Districts

The US is divided into 5 PADDs for energy data reporting and analysis. Understanding PADDs is essential because product pricing, inventory levels, and trade flows are all reported by PADD.

- **PADD 1 (East Coast)**: Largest consumer region. 120M+ people. Depends on product imports from PADD 3 (via Colonial Pipeline, the largest product pipeline in the US at ~2.5M bbl/d) and overseas. Any disruption to Colonial Pipeline (like the 2021 Colonial Pipeline ransomware attack) causes immediate gasoline shortages on the East Coast.
- **PADD 2 (Midwest)**: Both refining and consumption center. Receives Canadian crude, produces and consumes products regionally. Chicago and Group 3 (Tulsa) are key pricing hubs.
- **PADD 3 (Gulf Coast)**: The engine room of US refining. ~10M bbl/d capacity. Exports refined products to PADD 1, Latin America, Europe, and West Africa. Sets the marginal product price for the Atlantic Basin. Hurricane risk is the primary supply concern.
- **PADD 4 (Rockies)**: Small, isolated. Higher local product prices. Supplied by a handful of small refineries processing local crude.
- **PADD 5 (West Coast)**: Isolated from the rest of the US (mountains, no product pipelines to PADD 3). California's CARB gasoline specification is the strictest in the US, making West Coast gasoline the most expensive. Refinery outages cause immediate local price spikes because there is no easy way to bring in replacement product.

## Key Refined Products Trades

- **Crack spreads**: 3:2:1, 2:1:1, 5:3:2, or individual 1:1 product cracks. The bread and butter of products trading. Express a view on refinery margins and product tightness.
- **Gasoline calendar spreads**: Especially around the RVP transition (February-April). The March/April RBOB spread captures the winter-to-summer blend shift and turnaround impact. Summer months trade at a premium to winter.
- **Gas-diesel spread**: RBOB vs. ULSD relative value. Captures macro cycles and seasonal demand shifts.
- **RBOB vs. Brent crack**: International refining margin perspective. European gasoline pricing vs. international crude.
- **Fuel oil spreads**: HSFO vs. VLSFO (the IMO 2020 scrubber economics trade). HSFO vs. crude (the "fuel oil discount" or coking margin).
- **Product calendar spreads**: ULSD summer/winter (heating oil seasonality), RBOB driving season vs. shoulder months.

## Reading

- <a class="source-link" data-source="oil101">Oil 101</a> — chapters 9-11. Covers the refining process, refinery economics, and product specifications. Essential for understanding crack spread dynamics.
- <a class="source-link" data-source="eia">EIA Today in Energy</a> — the Q1 2026 petroleum price review covers product price dynamics alongside crude.
- <a class="source-link" data-source="primer">A Primer on Energy Trading</a> — Section 4 (Spread Trading), specifically crack spreads. Covers the 3:2:1 structure and what drives refining margins.

Also recommended: EIA "Refinery Yield" data (free dataset of US refinery product yields by PADD) and the EIA Weekly Petroleum Status Report — the most market-moving energy report in the world, released every Wednesday at 10:30 ET.`
  },
  {
    id: '05',
    name: 'Power Markets',
    desc: 'Electricity pricing, ISOs, renewables impact',
    lesson: 
