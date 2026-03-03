# Meetings Folder — Instructions

This folder holds meeting prep docs, notes, and follow-up materials.

## Meeting Prep Workflow
1. Pull meeting details from Google Calendar
2. Look up the company/contact in HubSpot for deal context
3. Check Slack for any recent mentions of the account
4. Search Notion Knowledge Base for relevant resources
5. Query `scott-campfire-memory` in Chroma for prior account interactions
6. Review Sybill for notes from prior calls (use Chrome)
7. Create a prep doc in `meetings/prep/`

## Stage-Specific Prep Notes (from Scott Wiki)

### Discovery Calls
- Use the 3-pillar discovery framework: Finance Operating Model → Cost of Pain → Why Now (see reference/CLAUDE.md for full question set)
- Query `30mpc` for discovery call best practices
- Reference the Mock Sales Pitch Script structure in Scott Wiki for flow: Why Campfire Exists → Positioning → Pain Tie-Back → ROI → Three Pillars → Social Proof → Integrations → Close for Demo
- Key red flags to listen for: "We do rev rec in spreadsheets," "Our close takes 15+ days," "We consolidate in Excel"

### Demo Prep
- Coordinate with SC on features to highlight — prioritize demo "aha" moments: Ember AI queries, Triple-Ledger FX, Credit Memo workflow, One-Click Consolidation, Rule Engine Close
- Share prior call recording (Sybill) with SC before the demo
- AI demo (Ember) drives +35% deal velocity — always include it

### Pricing/Solutioning Meetings
- Reference pricing guide from Notion before the call
- Have objection responses ready (top 7 objections in reference/CLAUDE.md)
- If NetSuite incumbent: lead with $5M Buyout Fund (+40% deal velocity)
- If stalled: offer reference call with similar company (+50% deal velocity)

## Prep Doc Format
```markdown
# Meeting Prep: {Company Name}
**Date:** {date} | **Time:** {time}
**Attendees:** {names and roles}
**Deal Stage:** {current stage from HubSpot}
**Meeting Type:** Discovery / Demo / Pricing / Other

## Context
- {Deal background, how they found us, key pain points}

## Agenda
1. {topic}
2. {topic}

## Questions to Ask
- {tailored questions based on deal stage}

## Materials to Reference
- {relevant decks, case studies, docs}

## Internal Notes
- {anything from Slack or prior calls}
```

## Follow-Up Workflow
After every customer meeting:
1. Draft follow-up email within 2 hours
2. Include any promised materials
3. Propose next steps with specific dates
4. Update HubSpot deal record with notes

## File Organization
```
meetings/
├── prep/           # Pre-meeting prep docs
├── notes/          # Post-meeting notes & summaries
└── follow-ups/     # Follow-up email drafts
```
