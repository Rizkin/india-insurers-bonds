# india-insurers-bonds

Two papers on Indian life insurers and the ultra-long G-sec market.

1. Paper 1: insurer forward commitments (FRA / bond forwards) and hidden economic ownership of ultra-long G-secs.
2. Paper 2: insurance premium demand and the long-end spread at RBI auctions.

Pre-registrations are in `prereg/` and were committed before any data collection; the commit timestamp is the registration.

## Layout
- `prereg/` paper1.md, paper2.md, schema.json
- `data/raw/` PDFs/HTML (gitignored; `manifest.csv` with SHA256 committed)
- `data/interim/` extractions, diff reports
- `data/final/` panels (DuckDB, CSV)
- `src/` collect/ extract/ auction/ analysis/
- `logs/` gate.csv, benchmarks.csv, verification_log.csv
- `paper1/`, `paper2/`

## Environment
WSL. `pip install -r requirements.txt`; `sudo apt install ocrmypdf tesseract-ocr`; `playwright install chromium`.
