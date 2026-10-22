# Pre-registration: Paper 1 — Life-insurer forward commitments and the ultra-long G-sec market (India)

Registered: 2026-10-22, before any data collection. Amendments only as dated, appended sections (never edits in place).

## Question
Do Indian life insurers' off-balance-sheet forward commitments (FRAs / bond forwards) hide a large economic ownership of ultra-long G-secs that on-balance-sheet holdings understate?

## Sample
- Top 10 life insurers by FY25 non-linked assets (IRDAI Handbook). Ranking fixed on Day 1 and committed before extraction.
- Period: FY22–FY26 (fiscal years ending 31 March).
- Sources: annual reports / public disclosures from insurer investor-relations pages and NSE/BSE filings.

## Definitions
- **forward_commitments**: FRA notional + bond-forward notional outstanding at FY end, INR crore. Merged into one series; hedge scope flagged (all | highly_effective_only | unclear).
- **Coverage rate**: sum of sampled insurers' non-linked assets / industry non-linked assets.
- **Economic ownership** = (insurer G-sec holdings + forward book) / total G-secs outstanding. Reported as an UPPER BOUND.
- Denominators extracted in the same pass: non-par book value, G-sec holdings, non-par premium.

## Hypotheses and decision rules
- **H1 (smoking gun)**: aggregate forward notional at least doubles FY22 to FY25 (growth >= 100%) while insurers' G-sec share of total G-secs (RBI Bulletin Table 45) is flat or falling (change <= 0).
- **Kill conditions** (Paper 1 is reported as null/negative if any holds): (a) forward notional growth FY22–FY25 < 50%; (b) top two insurers account for > 70% of the growth.
- **H2 (adds up)**: aggregate sampled forward book >= 80% of INR 3.5 trillion benchmark = "adds up"; < 50% = "falls short"; between = "inconclusive". Benchmark source/date/definition traced Day 1 into `logs/benchmarks.csv` before testing.
- **H3 (material)**: implied forward book >= 10% of one year's ultra-long G-sec issuance.
- **H4 (sales-enabler)**: across insurers and years, forward notional is positively related to non-par premium growth (sign test, insurer FE, clustered SE; one-sided at 10%).

## Go/no-go gate (Day 1, manual)
Open FY25 and FY26 annual reports of HDFC Life, ICICI Prudential Life, SBI Life. Record in `logs/gate.csv`: notional outstanding disclosed; MTM, counterparties, hedge scope shown; FY26 lists bond forwards separately. **Pass** if >= 2 of 3 insurers disclose notional outstanding in both years. **Fail** -> dated amendment and switch to the L-42 reserving-cushion design.

## Data and extraction protocol
- Double extraction by two model families (GLM via Z.ai, Kimi K2), temperature 0, same pages, same `prereg/schema.json`. Pre-filter is a plain keyword script (no LLM).
- Auto-validation: snippet must appear verbatim on cited page; units normalised to INR crore; FY end must be 31 March.
- Diff report field by field; hand-verify every latest-year figure, every mismatch, and a random 10% of the rest; log in `logs/verification_log.csv`.
- No hypothesis test is run before the Day 3 v0.1 panel freeze.

## Deviations
Any deviation is committed as a dated amendment below, with reason.

## Amendments
(none)
