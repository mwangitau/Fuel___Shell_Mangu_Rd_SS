# ⛽ Kiryan Energy Ltd — Mangu Shell Service Station Dashboards

![Status](https://img.shields.io/badge/Status-Active-success)
![License](https://img.shields.io/badge/License-Proprietary-red)
![Dashboards](https://img.shields.io/badge/Dashboards-4-blue)
![Version](https://img.shields.io/badge/Latest-v3.3-blueviolet)

**Comprehensive performance analytics dashboards for Shell Mangu Road Service Station operations in Kenya.**

🔗 **Live Site:** [https://shell-mangu-rd-service-station.vercel.app/](https://shell-mangu-rd-service-station.vercel.app/)

---

## 📁 Repository Structure

```
Fuel___Shell_Mangu_Rd_SS/
├── index.html                           # Landing page — links to all dashboards
├── README.md                            # This file
├── LICENSE.txt                          # Proprietary licence
├── staff_dashboard.html                 # Staff shortages & balance tracking (v2.1)
├── fuel/
│   └── fuel_dashboard_easy_config.html  # Per-pump volume & target dashboard (v3.0)
├── Product/
│   └── product_dashboard.html           # Fuel product inventory & variance (v2.2)
└── Gas/
    └── gas_dashboard_pivot_format.html  # LPG gas cylinder dashboard (v3.3)
```

---

## 📊 Dashboard Suite

### ⛽ 1. Pump Performance Dashboard — `v3.0`
**File:** `fuel/fuel_dashboard_easy_config.html`

Tracks daily pump volumes for all three fuel pumps against monthly targets with per-pump CSA accreditation.

**Key features:**
- Per-pump monthly target progress cards with pace markers
- Daily volume vs daily target chart with green/red shaded gap (above/below target)
- Tab switcher: All Pumps · Pump 1 · Pump 2 · Pump 3
- CSA (Customer Service Attendant) performance rankings
- Filters: Month · Attendant · Pump
- Data table with per-pump vs target comparison, CSA names per pump per day

**Monthly targets (litres):**
| Pump | UX (Unleaded) | DX (Diesel) | VP (V-Power) | Total |
|------|:---:|:---:|:---:|:---:|
| Pump 1 | 35,437 | 22,788 | — | **58,225** |
| Pump 2 | 53,156 | 36,461 | — | **89,617** |
| Pump 3 | — | 31,903 | 11,104 | **43,007** |
| **Station Total** | | | | **190,849** |

**Data months:** September 2025 → February 2026

---

### 📊 2. Fuel Product Analysis Dashboard — `v2.2`
**File:** `Product/product_dashboard.html`

Tracks inventory, meter vs dip sale variance, stock levels, and target performance across all three fuel products.

**Key features:**
- Monthly target progress cards (DX · UX · VP) with pace markers
- Daily sales vs daily target per product (tabbed: DX · UX · VP) with shaded gap chart
- Target vs Actual bar chart comparison
- Variance distribution doughnut (Low / Medium / High)
- Animated stock level alerts (Safe / Warning / Critical)
- Delivery analysis by product
- Filters: Month · Product · Variance level

**Monthly targets (litres):**
| Product | Target |
|---------|:------:|
| UX — Unleaded Super | 88,593 |
| DX — Diesel | 91,152 |
| VP — V-Power | 11,104 |

**Data months:** October 2025 → February 2026

---

### 🔥 3. LPG Gas Dashboard — `v3.3`
**File:** `Gas/gas_dashboard_pivot_format.html`

Tracks LPG cylinder refill sales and new customer acquisition across all four cylinder sizes.

**Key features:**
- **Refills vs New Customers clearly separated** — products containing `EMPTY` = new customer onboarding, not gas volume
- Monthly refill target: **3,114.5 KG/month** (refills only)
- Target progress cards for all 4 sizes + station total
- New customer acquisition cards for all 4 sizes (6KG · 13KG · 25KG · 45KG), counts in whole numbers only
- Daily refill KG vs daily target with shaded gap chart
- Refill trend by cylinder size (4 lines)
- New customers daily bar chart — stacked by all 4 sizes
- Pieces sold comparison chart (refills vs new customers)
- Filters: Month · Product Size (All/6KG/13KG/25KG/45KG) · Sale Type (All/Refills/New Customers)
- 45KG weekly supply tracking vs 135 KG/week benchmark

**Cylinder sizes supported:** 6KG · 13KG · 25KG · 45KG

**Target breakdown:**
| Size | Role | Target Share |
|------|------|:------:|
| 13KG | Dominant | ~55% of monthly target |
| 45KG | Weekly supply | 540 KG/month (135 KG/week × 4) |
| 25KG | Secondary | ~18% of monthly target |
| 6KG | Low volume | ~10% of monthly target |

**Data months:** October 2025 → February 2026

---

### 👥 4. Staff Shortages Dashboard — `v2.1`
**File:** `staff_dashboard.html`

Monitors daily cash balances per CSA, flagging shortages and surpluses.

**Key features:**
- Per-staff daily KES balance tracking
- Multi-month combined or individual month view
- Bar/line chart toggle with date range filter
- Real-time search across all records (Ctrl+F)
- Shortage / Surplus / Balanced status per day
- KES ±180 threshold indicators on chart axes
- Fullscreen chart mode

**Data months:** September 2025 → January 2026

---

### 🏠 5. Landing Page — `index.html`
Navigation hub with animated glassmorphism cards linking to all four dashboards, live status bar, and the Kiryan Energy Ltd SVG logo.

---

## ⚙️ Adding a New Month

All dashboards read live data from Google Sheets published as CSV. To add a new month:

1. Open the relevant dashboard HTML file
2. Find the `dataSources` object near the top of the `<script>` section
3. Add the new month entry:

```javascript
const dataSources = {
  "March 2026": "YOUR_NEW_CSV_LINK_HERE",
  "February 2026": "...",
  // ... existing months
};
```

4. Save and push — the new month appears automatically in the filter dropdown.

### Publishing a Google Sheet as CSV
1. Open the sheet → **File → Share → Publish to web**
2. Select the specific **tab** you want
3. Choose **CSV** format
4. Copy the published link and paste it into `dataSources`

---

## 📐 Data Format Requirements

### Fuel Pump Dashboard
Pivot format — columns: `DAY`, `NAME OF CSA`, `PUMP 1`, `NAME OF CSA.1`, `PUMP 2`, `NAME OF CSA.2`, `PUMP 3`

### Product Dashboard
Row format — columns: `DATE`, `PRODUCT`, `OPEN DIP`, `DELIVERY`, `CLOSE DIP`, `DIP SALE`, `METER SALE`, `VAR`, `EXPLAIN > 5%`

Products recognised: `UX`, `DX`, `VP`

### Gas Dashboard
Pivot table format:
- **Row 1 (header):** Dates as `2025.11.01`, `2025.11.02` etc.
- **Column A:** Product names — e.g. `13KG REFILL`, `13KG EMPTY`, `6KG EMPTY`, `25KG REFILL`, `45KG REFILL`
- **Cells:** Pieces sold (integers)

> **Business logic:** Any product name containing `EMPTY` is a new customer (empty cylinder sold). All other products are refills. Only refill KG counts toward the monthly target.

### Staff Dashboard
Row format — columns: `DAY`, `[Staff Name 1]`, `[Staff Name 2]`, ...

### Date Formats Supported
Both `YYYY.MM.DD` and `DD.MM.YYYY` are handled automatically across all dashboards.

---

## 🎨 Design System

All dashboards (except Staff) share a unified design language:

- **Fonts:** Barlow Condensed (headings, numbers) · Barlow (body)
- **Header:** Dark navy → blue-mid → product accent gradient with oversized emoji watermark
- **Cards:** White background, 4px coloured top border, hover lift effect
- **Charts:** Chart.js 3.9.1 · Custom `shadedGapPlugin` (green above / red below target with crossover handling)
- **Table headers:** Dark navy gradient, sticky

**Colour palette:**
| Token | Hex | Usage |
|-------|-----|-------|
| `--blue-deep` | `#0f1f3d` | Header, table headers |
| `--blue-mid` | `#1e3c72` | Section titles, borders |
| `--purple` | `#7e22ce` | Fuel product · Pump 2 |
| `--orange` | `#ea580c` | LPG accent |
| `--green` | `#059669` | On track, above target |
| `--amber` | `#d97706` | Below pace warning |
| `--red` | `#dc2626` | Critical / behind target |

---

## 🌐 Deployment

The site deploys via **GitHub Pages** from the `main` branch root. Changes go live within ~1 minute of pushing.

```bash
git add .
git commit -m "Update: description of change"
git push origin main
```

**Live URL:** `https://mwangitau.github.io/Fuel___Shell_Mangu_Rd_SS/`

---

## 📱 Browser Compatibility

| Browser | Support |
|---------|:-------:|
| Chrome / Edge | ✅ Recommended |
| Firefox | ✅ |
| Safari | ✅ |
| Mobile (iOS/Android) | ✅ Responsive |

---

## 🔒 Security & Confidentiality

> ⚠️ **These dashboards contain sensitive business data for official use only.**

- Do not share Google Sheets CSV links publicly — they expose raw operational data
- Do not commit data files (CSV, XLSX) to this repository
- Consider making the GitHub repository **private** (GitHub Pro ~$4/month) while keeping Pages live
- For external sharing (auditors, Shell) — export to PDF via browser print, do not share live links

---

## 📝 Version History

| Version | Dashboard | Changes |
|---------|-----------|---------|
| **v3.3** | Gas | New customer tracking expanded to all 4 sizes; whole-number counts throughout |
| **v3.2** | Gas | 25KG cylinder support; updated target proportions; 45KG weekly supply tracking |
| **v3.1** | Gas | Business logic fix (empties = new customers); refills-only target; full redesign |
| **v3.0** | Fuel Pump | Per-pump monthly targets; shaded gap chart; CSA rankings; tab switcher |
| **v2.2** | Product | Per-product daily target charts; tab switcher; animated stock alerts |
| **v2.1** | Staff | Multi-month view; per-staff filter; real-time search; date range filter |

---

## 📞 Contact

| | |
|--|--|
| Email | mwangijohngitau1@gmail.com |
| Station Manager | +254 717 034 328 |
| Location | Shell Mangu Road Service Station, Kenya |

---

## 📄 Licence

**PROPRIETARY SOFTWARE — ALL RIGHTS RESERVED**

Copyright © 2026 Kiryan Energy Ltd · Shell Mangu Road Service Station, Kenya

This software and all associated source code, dashboards, data visualisations, and documentation are the exclusive intellectual property of Kiryan Energy Ltd. Unauthorised copying, reproduction, distribution, modification, or use is strictly prohibited under the Kenya Copyright Act (Cap. 130) and the Computer Misuse and Cybercrimes Act 2018.

**Permitted use:** Internal use by authorised Kiryan Energy Ltd personnel only.

Licensing enquiries: mwangijohngitau1@gmail.com

---

<div align="center">

**[🚀 View Live Dashboards](https://shell-mangu-rd-service-station.vercel.app/)**

*Built for operational excellence at Shell Mangu Road Service Station*

**© 2026 Kiryan Energy Ltd — All Rights Reserved**

</div>
