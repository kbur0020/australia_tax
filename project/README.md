# The Australian Tax Paradox

A data investigation into how much Australians pay in tax, where it goes, and the $269 billion the government chooses not to collect through tax concessions.

**Live site:** https://kbur0020.github.io/australia_tax/
**Sketch (PDF):** australia_tax_sketch.pdf

## About this project

Built for **FIT2179 Data Visualisation, Monash University, Semester 1 2026**.

Ten Vega-Lite visualisations tell a three-act story drawn from three independent Australian government data sources, plus an ABS geographic boundary file:

1. **Act 1 — Where the money lives.** Income distribution by Victorian postcode and occupation.
2. **Act 2 — Where it goes.** Federal expenditure breakdown and budget vs outcome.
3. **Act 3 — The hidden cost.** Tax concessions, who benefits, and what $269bn could fund.

## Repository structure

```
.
├── index.html                        # Entry point — embeds all 10 charts
├── css/
│   └── styles.css                    # Editorial design system
├── charts/                           # 10 Vega-Lite specifications (.vg.json)
│   ├── 01_choropleth_victoria_income.vg.json
│   ├── 02_diverging_bars_postcodes.vg.json
│   ├── 03_lollipop_occupations.vg.json
│   ├── 04_donut_federal_expenditure.vg.json
│   ├── 05_slope_budget_variance.vg.json
│   ├── 06_bubbles_tax_expenditures.vg.json
│   ├── 07_heatmap_decile_concession.vg.json
│   ├── 08_dumbbell_gender.vg.json
│   ├── 09_lines_timeseries.vg.json
│   └── 10_waffle_perspective.vg.json
└── data/                             # Cleaned source data (CSV + TopoJSON)
    ├── ato_postcode_australia.csv
    ├── ato_postcode_victoria.csv
    ├── ato_top_bottom_10_australia.csv
    ├── ato_top_bottom_10.csv
    ├── ato_top10_occupations_australia.csv
    ├── ato_top30_occupations.csv
    ├── ato_occupations_by_state.csv
    ├── ato_gifts_by_state.csv
    ├── fbo_2024_25_expenses_by_function.csv
    ├── fbo_2024_25_by_function_summary.csv
    ├── teis_large_tax_expenditures.csv
    ├── teis_distribution_by_decile.csv
    ├── teis_gender_distribution.csv
    ├── teis_big3_timeseries.csv
    ├── derived_what_could_be_funded.csv
    ├── derived_waffle.csv
    ├── victoria_postcodes_topo.json
    └── melbourne_postcodes_topo.json
```

## The 10 chart idioms

Every chart uses a distinct combination of marks, channels, and arrangement under Munzner's framework.

| # | Idiom | Marks | Primary channels | Story act |
|---|---|---|---|---|
| 1 | Choropleth map | geoshape (area) | colour, geographic position | Act 1 |
| 2 | Diverging horizontal bar | bar (area) | position, length, diverging hue | Act 1 |
| 3 | Lollipop (ranked) | rule + circle | position, length, sequential colour | Act 1 |
| 4 | Donut / arc chart | arc | angle, colour | Act 2 |
| 5 | Slope (paired-line) chart | line + circle | paired position, diverging hue | Act 2 |
| 6 | Packed bubble chart | circle | size, colour, categorical position | Act 3 |
| 7 | Heatmap | rect | colour intensity, two ordinal axes | Act 3 |
| 8 | Dumbbell / paired-dot | rule + circle (×2) | paired position, hue | Act 3 |
| 9 | Multi-series time line | line + circle | position over time, hue, dashed projection marker | Act 3 |
| 10 | Waffle / unit chart (custom-built derived) | rect grid | count, colour, faceted by row | Act 3 |

Chart 10 is the rubric's required "custom-built derived chart" — it combines data from Treasury TEIS 2025-26 and the Final Budget Outcome 2024-25 to produce a comparison that exists in neither source on its own.

## Data sources

All sources are official Australian government publications, used in their most recent available editions.

| Source | Year | Licence |
|---|---|---|
| ATO Taxation Statistics, Snapshot Table 7 | 2022–23 | CC BY 3.0 AU |
| Treasury Tax Expenditures and Insights Statement | 2025–26 | CC BY 4.0 |
| Final Budget Outcome, Appendix A | 2024–25 | CC BY 4.0 |
| ABS Postcode Areas (POA), ASGS Edition 3 | 2021 | CC BY 4.0 |

Full citations and verification details are in the colophon at the bottom of `index.html` and in the project's data bundle README.

## Running locally

Open `index.html` in any modern browser served from a local web server (charts will not load via `file://` due to browser CORS rules on `fetch`).

```bash
# from the project root
python3 -m http.server 8000
# then open http://localhost:8000
```

## Acknowledgement of AI use

Anthropic's Claude AI was used during development for data cleaning automation,
Vega-Lite specification scaffolding, and grammar review of narrative text.
The investigation, narrative angle, chart selection, design system, and final
editorial decisions are the author's.

## Licence

© Kai Burke 2026. The visualisation, narrative text, and original code in this
repository are released under [Creative Commons Attribution 4.0
International](https://creativecommons.org/licenses/by/4.0/).

The underlying datasets retain their original licences as listed above.
