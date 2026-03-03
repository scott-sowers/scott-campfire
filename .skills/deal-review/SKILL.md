---
name: deal-review
description: "**Deal Review & Pipeline Agent**: Reviews deal health, pipeline status, and CRM hygiene. Triggers whenever the user asks about their pipeline, deals, forecast, deal status, CRM updates, or wants to review their book of business. Also triggers for 'how are my deals', 'pipeline check', 'what needs attention', 'forecast update', 'deal hygiene', 'stalled deals', or any mention of reviewing, updating, or analyzing active opportunities. Uses HubSpot data to produce actionable deal insights."
---

# Deal Review Skill

Analyze deal health and pipeline status from HubSpot, producing actionable insights.

## Trigger Contexts
- User asks about their pipeline, deals, or forecast
- User wants to review stalled or at-risk deals
- User needs to prepare for a pipeline review meeting
- User asks about CRM hygiene or deal updates needed

## Execution Steps

### Step 1: Pull Deal Data
Query HubSpot for all deals owned by the user. Group by stage:
- Discovery
- Demo
- Pricing/Solutioning
- Compliance/Legal

For each deal, pull: deal name, company, value, stage, days in stage, last activity date, next scheduled activity, close date.

### Step 2: Analyze Deal Health
Flag deals that need attention:
- **Stalled:** No activity in 7+ days
- **At Risk:** Close date in the past or within 7 days with no next step
- **Missing Data:** Required fields empty for current stage (reference HubSpot Deal Fields in Notion)
- **Aging:** In same stage for 2x the average cycle time

### Step 3: Generate Pipeline Summary

```markdown
# Pipeline Review — {Date}

## Summary
| Metric | Value |
|--------|-------|
| Total Pipeline | ${total} |
| Weighted Forecast | ${weighted} |
| Deals in Pipeline | {count} |
| Avg Deal Size | ${avg} |
| Avg Days in Pipeline | {days} |

## By Stage
| Stage | Count | Value | Avg Days |
|-------|-------|-------|----------|
| Discovery | {n} | ${v} | {d} |
| Demo | {n} | ${v} | {d} |
| Pricing | {n} | ${v} | {d} |
| Compliance | {n} | ${v} | {d} |

## Deals Needing Attention
### Stalled (No activity 7+ days)
- {Deal}: ${value} — Last activity {date}, {reason}

### At Risk
- {Deal}: ${value} — {reason}

### CRM Hygiene Issues
- {Deal}: Missing {field} (required at {stage} stage)

## Recent Wins & Losses
- Won: {details}
- Lost: {details}

## Recommended Actions
1. {Specific action for highest-priority deal}
2. {Action}
3. {Action}
```

### Step 4: Save Report
Save to `reports/weekly/pipeline-review-{YYYY-MM-DD}.md`

### Step 5: Save to Memory
After generating the report, write a pipeline snapshot to `scott-campfire-memory` in Chroma DB with:
- ID format: `pipeline-review::{YYYY-MM-DD}`
- Metadata: `{"type": "pipeline-review", "date": "{YYYY-MM-DD}", "total_pipeline": "{value}", "deal_count": "{count}"}`
- Content: Summary of pipeline totals, notable movements, and key action items

## Important Notes
- Use the HubSpot Deal Fields reference in Notion to know which fields are required at each stage
- Weight forecast using standard probability by stage (Discovery: 10%, Demo: 30%, Pricing: 60%, Compliance: 80%)
- For pipeline review meeting prep, also draft talking points for each deal
- Query `scott-campfire-memory` for the prior pipeline review to highlight week-over-week changes
- Query `30mpc` for pipeline management and deal progression tactics when flagging at-risk deals
- When flagging at-risk deals, reference deal velocity drivers from Scott Wiki: NetSuite Buyout Fund (+40%), AI demo (+35%), reference call (+50%), exec alignment (+60%), sandbox access (+25%)
- For stalled deals, suggest specific unblocking tactics: reference calls with similar companies, sandbox/trial access, executive alignment meetings
- For competitive deals, note which competitor and reference the relevant battle card from Scott Wiki (vs Rillet, NetSuite, QuickBooks)
