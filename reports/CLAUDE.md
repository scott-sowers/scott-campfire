# Reports Folder — Instructions

This folder contains pipeline reports, forecasts, and weekly summaries.

## Weekly Pipeline Report Format
```markdown
# Pipeline Report — Week of {date}
## Summary
- Total pipeline: ${amount}
- Weighted forecast: ${amount}
- Deals added this week: {count}
- Deals advanced: {count}
- Deals closed: {count}

## By Stage
| Stage | Count | Value | Weighted |
|-------|-------|-------|----------|
| Discovery | | | |
| Demo | | | |
| Pricing | | | |
| Compliance | | | |

## Deals Needing Attention
- {deal name}: {why it needs attention}

## Wins & Losses
- Won: {details}
- Lost: {details and reasons}

## Next Week Focus
- {priorities}
```

## Data Source
Pull all deal data from HubSpot using the CRM connector. Filter by my ownership (hubspot_owner_id).

## File Organization
```
reports/
├── weekly/         # Weekly pipeline reports
├── forecasts/      # Quarterly forecast docs
├── qbrs/           # Quarterly business review materials
└── _archive/       # Previous quarter reports
```
