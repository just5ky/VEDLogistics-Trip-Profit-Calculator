# VED Logistics — Trip Profit Calculator

Live, single-page webapp for calculating per-trip and monthly profit for trucking operations. No backend, no build step — pure HTML/CSS/JS. Loads JetBrains Mono from Google Fonts (requires network; falls back to system monospace offline).

## Features

- Live calculation (updates on every keystroke)
- Per-trip net profit and full monthly projection
- Dark / Light theme toggle
- Responsive: 2-column no-scroll layout on desktop, stacked scroll on mobile
- Cost breakdown accordion per trip

## Inputs

| Field | Note |
|---|---|
| Rate | Base rate per trip |
| Distance | One-way KM |
| Trip Time | Duration in hours |
| Diesel Price | Defaults to ₹94/L if blank |
| Commission | Manual |
| Driver / Trip | Manual |
| Toll | Enter amount + toggle 1-way or 2-way |
| Misc | Any other per-trip cost |

## Formulas

| Output | Formula |
|---|---|
| Round Trip KM | Distance × 2 |
| Bhada (Revenue) | Rate × 38 |
| TDS | Bhada × 1% |
| Diesel Cost | Round Trip × Diesel Price ÷ 2.5 |
| Adblue | Round Trip ÷ 100 × ₹300 |
| Net / Trip | Bhada − (TDS + Commission + Driver + Diesel + Adblue + Toll + Misc) |
| Trips / Month | 30 ÷ (Trip Time ÷ 24) |
| Monthly Run | Trips/Month × Round Trip KM |
| Gross Monthly | Net/Trip × Trips/Month |
| Net Monthly | Gross Monthly − ₹90,000 fixed |

**Fixed monthly deductions:** Vehicle EMI ₹60,000 · Driver Salary ₹15,000 · Vehicle Maintenance ₹15,000

## Deploy on GitHub Pages

1. Create a new GitHub repository
2. Push this folder to the `main` branch
3. Go to **Settings → Pages → Source**: `main` branch, `/ (root)`
4. Site will be live at `https://<username>.github.io/<repo-name>`

The `.nojekyll` file is already included to prevent GitHub's Jekyll processor from interfering.

## Local Use

Open `index.html` directly in any browser — no server required.
