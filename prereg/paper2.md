# Pre-registration: Paper 2 — Insurance demand and the ultra-long yield spread at RBI auctions

Registered: 2026-10-22, before any data collection. Amendments only as dated, appended sections.

## Question
Does life-insurance premium demand (abnormal first-year premium) widen or compress the long-end spread in RBI G-sec auctions?

## Data
- RBI "Auction Results: Cut-off" releases 2017–2026 (~400–500), plus half-yearly borrowing calendars. Crawl rate: 1 request / 2 s.
- Individual first-year premium: monthly, IRDAI / Life Insurance Council.
- Security master of maturity dates: CCIL outstanding-debt page.
- Deterministic HTML parser covering three layout eras, unit-tested with one fixture per era.
- Reconcile accepted amounts to gross borrowing per fiscal year; hand-check 20 rows and every row with devolvement.

## Variables
- **Spread** (per auction day): cut-off of a bond with 25+ years residual maturity minus cut-off of a bond with 8–14 years residual, same auction day.
- **Abnormal premium**: residual of log individual first-year premium after month dummies and a linear trend.
- **Ultra-long supply share**: share of 25+ year bonds in that period's issuance (calendar/accepted).
- Controls fixed before estimation: repo rate, 10Y benchmark level, auction size. Any addition is an amendment.

## Model
spread_t = month FE + b0*AbnPrem_t + b1*AbnPrem_{t-1} + g*UltraLongShare_t + controls + e_t
Newey-West SE, 3 lags. Hypothesis: abnormal premium has negative sign on spread (demand compresses it); tested at 10%.

## Placebo
Same model, spread = cut-off(8–14Y) minus cut-off(<=5Y).

## Kill conditions
Paper 2 is reported null if (a) abnormal premium is not significant at 10% with the expected sign, or (b) the placebo shows an effect of similar size (|placebo coef| >= 0.5 x |main coef|, same sign).

## Horse race
Add CCIL forward volumes only if coverage >= 36 months; otherwise omitted and stated.

## Deviations
Dated amendments below.

## Amendments
(none)
