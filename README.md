# Cameroon Trade Partner Analysis: Bilateral Trade, Trade Balance and Partner Dynamics, 2015-2023

An end-to-end trade-data analytics project on Cameroon's bilateral merchandise trade, built from
UN Comtrade annual trade-value data.

> **Note:** The source data covers **2015-2023** (9 years). 2024-2025 were not yet published by
> UN Comtrade at the time this dataset was pulled, so the study period was adjusted accordingly.
> This is documented in the notebook's Limitations section.

## Objective

Identify Cameroon's most important trading partners, understand how those relationships have
evolved between 2015 and 2023, and measure how concentrated Cameroon's trade is among a small
number of countries with a closer look at seven countries of interest: **China, Nigeria,
France, Netherlands, Vietnam, India, and the United States**.

## Headline results (2015-2023, current US$)

| | |
|---|---|
| Cameroon's #1 trading partner | **China** — 16.7% of total trade, running a large bilateral deficit |
| Largest bilateral trade surplus | **Netherlands** (+$4.16B cumulative) |
| Largest bilateral trade deficit (priority countries) | **China** (-$5.10B cumulative) |
| Fastest-growing priority partner | **Netherlands** (+72% total trade, 2015→2023) |
| Declining priority partner | **Nigeria** (-83% total trade, 2015→2023) |
| Trade concentration (HHI) | 623 (2015) → 619 (2023) — low and broadly stable concentration |
| Overall trade balance | Persistent deficit every year, from -$2.0B (2015) to -$3.3B (2023) |

Full figures and supporting tables are in `results/`.

## Project structure

```
cameroon-trade-partner-analysis/
├── data/
│   ├── raw/                 # Original UN Comtrade extract
│   └── cleaned/             # Cleaned, analysis-ready dataset
├── notebooks/
│   └── cameroon_trade_partner_analysis.ipynb   # Full, reproducible analysis
├── results/
│   ├── figures/             # 18 charts (PNG)
│   └── tables/              # 11 analytical tables (CSV)
├── README.md
└── requirements.txt
```

## Methodology

1. **Data understanding & cleaning** — validated that the reporter is always Cameroon, the second
   partner is always World, and both Import/Export flows are present; fixed a header/data column
   misalignment in the raw file; standardized column names and types; dropped rows with missing
   trade values (none found beyond that check); separated the `World` aggregate rows from
   bilateral partner rows.
2. **Overall trade** — annual exports, imports, total trade, and trade balance, with year-over-year
   growth rates.
3. **Partner ranking** — all ~230 partners ranked by total bilateral trade, exports, and imports,
   with each partner's percentage share of Cameroon's total trade.
4. **Export & import partner analysis** — fastest-growing/declining and emerging partners on each
   side of the trade flow, plus a detailed profile of the seven priority countries.
5. **Bilateral trade analysis** — exports, imports, balance, and share of total trade for each
   priority country, with year-by-year trend charts.
6. **Trade balance by partner** — cumulative bilateral balances, with partners classified as
   *persistent deficit*, *persistent surplus*, or *mixed* based on the share of years with a
   negative or positive balance.
7. **Partner importance over time** — 2015 vs. 2023 comparison of trade value, share of total
   trade, and growth, with partners classified as growing / declining / stable / emerging.
8. **Trade concentration** — top-5 and top-10 partner shares and the Herfindahl-Hirschman Index
   (HHI), tracked across all nine years.
9. **Priority partner comparison** — a single ranked comparison table across all seven countries
   of interest, built entirely from measured indicators (no assumed importance).

## Key findings (data-supported, see notebook for full detail)

- China is Cameroon's largest trading partner by a wide margin, but the relationship runs a large,
  persistent trade deficit for Cameroon (Cameroon imports far more from China than it exports).
- The Netherlands is Cameroon's largest *export* destination among the priority countries and one
  of the very few large partners with a persistent trade surplus for Cameroon.
- Nigeria's importance to Cameroon's trade fell sharply over the period, driven mainly by a large
  drop in imports from Nigeria.
- Cameroon's overall trade concentration (HHI) is comparatively low and has stayed broadly flat,
  meaning trade is spread across a wide set of partners rather than a handful of dominant ones —
  even though China alone still accounts for roughly one-sixth of total trade.
- Cameroon ran an overall merchandise trade deficit in every year from 2015 to 2023.

## Limitations

- Aggregate ("Total") product data only — no individual agricultural product or commodity can be
  identified from this dataset. Product-level analysis is planned as **Phase 2**.
- Values are nominal (current US$); no inflation or exchange-rate adjustment applied.
- Study period is 2015-2023, not 2015-2025, due to data availability at the time of extraction.
- Descriptive only — findings do not establish causation behind observed growth or decline.

Full limitations are documented in the notebook.

## How to reproduce

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace notebooks/cameroon_trade_partner_analysis.ipynb
```

The notebook runs end-to-end with no manual intervention and regenerates every figure in
`results/figures/` and every table in `results/tables/`.

## Data source

UN Comtrade — Cameroon (reporter), All partners, World (second partner), Imports & Exports,
Total product, annual, 2015-2023.
