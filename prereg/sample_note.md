# Sample fix (Day 1)

Rule (from prereg/paper1.md): top 10 life insurers by FY25 (31 Mar 2025) non-linked assets.
Non-linked assets = Life Fund total + Pension & General Annuity & Group Fund total (excludes Unit Linked Fund), INR crore, par and non-par together.
Source: IRDAI Annual Report 2024-25, Statement 16 (pdf pages 172-173), https://lifeinscouncil.org/component/IRDAI%20Annual%20Report%202024-25.pdf
Industry total non-linked = 59,49,913 INR crore (Table I.22), matches Statement 16 sum (5,949,912.69). Verified by parsing the PDF.
LIC is included by rule (rank 1, ~79.9% of industry). Top 10 cover about 96.9% of industry non-linked assets (coverage rate). Rank 11 (Reliance Nippon, 30,854) is 26% below rank 10 (41,882).
Parsing script output checked against the industry total; spot-check a few rows against the PDF before relying on them.
