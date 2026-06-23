[README.md](https://github.com/user-attachments/files/29246207/README.md)
# Hotel Revenue Analysis — Four-Year PMS Data Study

Independent revenue analysis conducted on four years of property management system (PMS) exports for a 130-room extended-stay hotel in Ann Arbor, Michigan. Initiated and executed outside of formal job duties while working as a night auditor.

---

## The question

The property's headline numbers looked fine — occupancy was up, gross revenue was growing. But something felt off at the operational level. This analysis asked: **what's actually driving performance, and is the business mix sustainable?**

---

## What I found

Occupancy grew from 61.9% (2023) to 74.4% (2026 YTD). Gross room revenue grew ~14%. By surface metrics, the property was improving.

But underneath:

- **ADR dropped from $140.86 to $120.60** — a $20/night decline over three years
- **7 of 20 active market segments disappeared entirely**, all from outbound-sales-dependent categories (Associations, Corporate Groups, Trade Shows, Leisure Groups, Corp-Package contracts)
- **Long-Term segment grew 47%** (7,269 → 10,675 rooms) while its ADR declined 9% annually
- **30+ night stays grew from 24% to 29% of total rooms**, the lowest-ADR length-of-stay bucket
- **Group Rooms In-House collapsed from 2,375 (2023) to 12 (2026 YTD)** — an independent metric that confirms segment disappearance isn't a coding artifact
- **Estimated annual premium revenue gap: ~$290K+**, representing business that existed at the property in 2023 and no longer appears in any segment

RevPAR peaked in 2025 at $100.71 and fell back to $90.60 in 2026 YTD despite higher occupancy — the signature of rate-for-occupancy tradeoff without a compensating premium business pipeline.

---

## Data sources

All data pulled directly from PMS report exports (Opera-style format):

| File | Description |
|------|-------------|
| `manager_report{year}.txt` | Occupancy, ADR, RevPAR, revenue, room counts |
| `market_code_statistics_{year}.txt` | Segment mix, ADR and room nights by market code |
| `stats_by_length_of_stay_{year}.txt` | LOS bucket breakdown, extended stay metrics |

Years covered: **2023, 2024, 2025** (full year) and **2026** (YTD through June 21)

> Raw data files are not included in this repository to protect property confidentiality.

---

## Files

```
hotel-revenue-analysis/
├── analysis.py              # Data extraction and summary report
├── hotel_analysis_onepager.html  # Printable one-page owner brief
└── README.md
```

---

## How to run

```bash
# Place PMS export .txt files in the same directory
python analysis.py
```

Output: printed summary tables + `compiled_data.json` for use in other tools.

**Requirements:** Python 3.7+, standard library only (csv, json, pathlib). No dependencies to install.

---

## Key methodology notes

**Why the segment disappearance isn't a miscoding issue:**
Market code data and Group Rooms In-House data are tracked independently in the PMS. Group Rooms In-House collapsed from 2,375 to 12 in parallel with the segment data — confirming the group/premium business genuinely left, rather than being recoded into other segments.

**2026 comparability:**
2026 data is YTD through late June. Direct year-over-year comparisons to full-year figures are noted where relevant.

**What this data can't show:**
Monthly seasonality (would require monthly stats reports), rate code detail within segments (would require Rate Code Statistics or Source of Business reports), and guest-level quality data (would require incident/guest history reports).

---

## Skills demonstrated

- Parsing and interpreting raw hospitality PMS exports (no documentation provided)
- Revenue management concepts: ADR, RevPAR, market segment mix, rate-occupancy tradeoff
- Identifying data artifacts vs. real operational trends (miscoding vs. actual segment loss)
- Independent analysis initiated outside formal job scope
- Translating operational intuition into quantifiable findings

---

*Conducted independently. Property identifying details anonymized.*
