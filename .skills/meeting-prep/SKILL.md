---
name: meeting-prep
description: "**Meeting Prep Agent**: Automatically prepares comprehensive meeting briefs for sales calls. Triggers whenever the user mentions prepping for a meeting, call, demo, or discussion with a prospect or customer. Also triggers for phrases like 'what do I need to know before my call', 'brief me on', 'prep me for', 'get me ready for my meeting', or any mention of an upcoming customer interaction. Uses HubSpot, Google Calendar, Slack, Notion, and Todoist to compile a complete pre-meeting brief."
---

# Meeting Prep Skill

Compile a comprehensive pre-meeting brief by pulling data from multiple sources in parallel.

## Trigger Contexts
- User mentions an upcoming meeting, call, demo, or customer interaction
- User asks to be "prepped", "briefed", or "ready" for a conversation
- Calendar shows an upcoming external meeting

## Execution Steps

### Step 1: Identify the Meeting
Check Google Calendar for the meeting the user is referring to. Extract:
- Meeting title, date, time, duration
- Attendees (names and emails)
- Any links or agenda in the description

### Step 2: Gather Context (Parallel Sub-Agents)
Launch these in parallel:

**CRM Sub-Agent:**
- Search HubSpot for the company and contact records
- Pull deal stage, pipeline value, last activity, deal notes
- Check for recent email engagement and sequence status
- Note any open tasks or upcoming activities on the deal

**Slack Sub-Agent:**
- Search Slack for recent mentions of the company name or contact name
- Check #team-ignite (C0A7421UP6H) for any relevant team discussions
- Look for any internal context from the past 2 weeks

**Notion Sub-Agent:**
- Search the Sales Knowledge Base for relevant resources
- Check if there are industry-specific case studies or collateral
- Pull any relevant commercial policies or pricing guidelines

**Todoist Sub-Agent:**
- Check for any open tasks related to this company or deal
- Flag overdue items that should be addressed before the call

**Memory Sub-Agent (Chroma DB):**
- Query `scott-campfire-memory` for any prior context on this account (past meetings, decisions, notes)
- Query `30mpc` for relevant tactical advice based on the meeting type (e.g., discovery best practices, demo tips, objection handling techniques)

### Step 3: Compile the Brief
Create a markdown file in `meetings/prep/` using this structure:

```markdown
# Meeting Prep: {Company Name}
**Date:** {date} | **Time:** {time} | **Duration:** {duration}
**Meeting Type:** {Discovery / Demo / Pricing / Follow-up}

## Attendees
| Name | Role | Notes |
|------|------|-------|
| {name} | {title} | {any context from CRM/Slack} |

## Deal Context
- **Stage:** {current stage}
- **Value:** ${amount}
- **Last Activity:** {what and when}
- **Days in Stage:** {count}

## Key Topics & Agenda
1. {topic based on deal stage and context}
2. {topic}

## Questions to Ask
- {tailored questions based on deal stage per Sales Cycle Overview}

## Internal Intelligence
- {relevant Slack mentions or team discussions}
- {any flags or concerns}

## Materials to Reference
- {relevant case studies, decks, or docs from Notion KB}

## Open Tasks
- {from Todoist, related to this account}

## Suggested Next Steps
- {based on deal stage, what should the outcome of this meeting be}
```

### Step 4: Draft Follow-Up Template
Pre-draft a follow-up email shell in `meetings/follow-ups/` that can be customized after the meeting.

### Step 5: Save to Memory
After the prep is compiled, write a summary to `scott-campfire-memory` in Chroma DB with:
- ID format: `{account-slug}::{YYYY-MM-DD}::meeting-prep`
- Metadata: `{"account": "{company}", "type": "meeting-prep", "stage": "{deal_stage}", "date": "{YYYY-MM-DD}"}`
- Content: Brief summary of the account context, deal stage, and key topics for this meeting

## Important Notes
- For discovery calls: use the 3-pillar discovery framework (Finance Operating Model → Cost of Pain → Why Now) from reference/CLAUDE.md. Include standard discovery questions from the Sales Cycle Overview. Query `30mpc` for discovery call best practices. Reference the Mock Sales Pitch Script in Scott Wiki for meeting flow structure.
- For demos: remind about SC prep requirements (share recording, features to highlight, pre-demo sync). Prioritize demo "aha" moments: Ember AI natural language queries, Triple-Ledger FX, Credit Memo workflow, One-Click Consolidation, Rule Engine Close. AI demo drives +35% deal velocity.
- For pricing: reference the pricing guide from Notion. Have objection responses ready (top 7 objections in reference/CLAUDE.md). If NetSuite incumbent, lead with $5M Buyout Fund (+40% velocity). If stalled, suggest reference call (+50% velocity).
- For competitive situations: fetch the relevant battle card from Scott Wiki (vs Rillet, NetSuite, or QuickBooks) and include key positioning points in the brief.
- Always check if there are action items from prior meetings that need follow-up
- Always check `scott-campfire-memory` for prior context on the account before compiling the brief
- Reference Scott Wiki in Notion for deep product, competitive, and accounting context: https://www.notion.so/meetcampfire/Scott-Wiki-3164fe173c4a801f8eb7e263d2ed1b2d
