# Scott Campfire — Cowork Workspace

This is my daily Cowork workspace for my role as an Enterprise Account Executive at Campfire. It's structured following [Nav Toor's Cowork setup guides](https://x.com/heynavtoor) for maximum Claude effectiveness.

---

## How This Workspace Works

When Claude opens this folder, it automatically reads `CLAUDE.md` for primary instructions — my role, tools, key links, and guardrails. The `_MANIFEST.md` file tells Claude which files to load and when, using a 3-tier system so context is used efficiently.

### Tier 1 — Always Loaded
These files are read at the start of every session:

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Primary instructions: role, tool stack, Notion links, sales stages, segment rules, key contacts, guardrails |
| `_MANIFEST.md` | Tiered file index — tells Claude what to load and when |
| `about-me.md` | Role context, what Campfire does, targets, competitors, calendar patterns |
| `brand-voice.md` | Communication style for emails, calls, Slack, and reports |
| `working-style.md` | How Claude should operate: task priorities, sub-agent patterns, output preferences |

### Tier 2 — Domain Folders
Each folder has its own `CLAUDE.md` with domain-specific instructions. Claude loads these when working in that area:

| Folder | Domain |
|--------|--------|
| `deals/` | Deal workspace, HubSpot stage workflow, handoff process |
| `prospecting/` | Outbound strategy, territory rules (501+ FTE), target personas |
| `meetings/` | 5-step meeting prep process, brief template, follow-up workflow |
| `collateral/` | Master deck reference, standard materials package |
| `reports/` | Weekly pipeline report template, data sources |
| `templates/` | Email templates: discovery follow-up, demo follow-up, handoff intro |
| `reference/` | Notion KB, competitive landscape, enterprise discovery questions |

### Tier 3 — Archives
Old deal folders, past reports, and retired templates. Claude only reads these when explicitly asked.

---

## Custom Skills

Located in `.skills/` — these are specialized workflows Claude can run:

| Skill | What It Does |
|-------|-------------|
| **meeting-prep** | Compiles pre-meeting briefs using parallel sub-agents across Calendar, HubSpot, Slack, Notion, and Todoist |
| **deal-review** | Pulls HubSpot pipeline, flags stalled/at-risk deals, generates weighted forecast |
| **follow-up-drafter** | Drafts personalized post-meeting emails using the right template by meeting type |

## Scheduled Tasks

These run automatically on a cron schedule:

| Task | Schedule | What It Does |
|------|----------|-------------|
| **morning-briefing** | Weekdays 8am | Calendar, tasks, deal movement, Slack catch-up |
| **weekly-pipeline-report** | Fridays 4pm | Full pipeline snapshot with week-over-week changes |
| **daily-slack-digest** | Weekdays 6pm | #team-ignite summary, mentions, action items |

---

## Chroma DB — Persistent Memory & Sales Best Practices

Two Chroma collections power long-term memory and sales methodology across sessions:

| Collection | Contents | Usage |
|-----------|----------|-------|
| `scott-campfire-memory` | Deal context, meeting outcomes, account insights, decisions, learnings | Written to after significant tasks (meeting prep, deal reviews, follow-ups). Queried at the start of related tasks to maintain continuity across sessions. |
| `30mpc` | 2,300+ episode transcripts from "30 Minutes to Presidents Club" podcast | Queried for tactical sales advice — cold calling openers, discovery techniques, objection handling, negotiation, pipeline management, and closing. |

**How memory works:** Skills automatically write to `scott-campfire-memory` after completing key tasks (meeting prep, pipeline reviews, follow-ups). This means Claude remembers prior account context, past decisions, and what was discussed — even in a brand new session. The `30mpc` collection acts as an always-available sales coach grounded in real practitioner advice.

---

## Scott Wiki (Notion)

My personal Campfire sales knowledge base lives in Notion ([Scott Wiki](https://www.notion.so/meetcampfire/Scott-Wiki-3164fe173c4a801f8eb7e263d2ed1b2d)). It contains pitch scripts, competitive battle cards (vs NetSuite, Rillet, QuickBooks), objection handling playbooks, accounting concepts for selling ERP, and messaging analysis. Claude references this when prepping for meetings, handling objections, drafting outreach, or needing product/competitive context.

---

## Connected Tools

| Tool | Purpose | Access |
|------|---------|--------|
| HubSpot | CRM, deals, sequences, contacts | MCP Connector |
| Gmail | Email communication | MCP Connector |
| Google Calendar | Scheduling, meetings | MCP Connector |
| Calendly | External meeting scheduling | No connector |
| Sybill.ai | Call recording & AI notes | Chrome only |
| Default | Lead router | No connector |
| Todoist | Personal & work task management | MCP Connector |
| Slack | Team comms (#team-ignite) | MCP Connector |
| Notion | Team & company docs, Sales KB | MCP Connector |
| Public Wiki | Customer-facing docs | Web (meetcampfire.notion.site) |
| Loom | Video messaging | No connector |
| Google Drive | Contracts, shared files | MCP Connector |
| Chroma DB | Vector memory & sales best practices | MCP Connector |

---

## Global Instructions (Manual Step)

For best results, paste the following into **Settings → Cowork → Global Instructions** so Claude always has core context even before opening this folder:

> I'm Scott Sowers, Enterprise Account Executive at Campfire (modern ERP/accounting platform). I handle 501+ FTE accounts. My tools: HubSpot (CRM), Gmail, Google Calendar, Todoist, Slack (#team-ignite), Notion (Sales KB). Be direct and action-oriented — draft it, build it, pull the data. Don't just describe what you'd do. Check HubSpot for deal context before any meeting prep. Always include next steps and clear CTAs in customer emails.

---

## Key Rules

- **Don't send** customer emails without my review — always draft
- **Don't modify** HubSpot deal stages without confirming with me
- **Don't edit** Notion source-of-truth pages — flag changes to content owners
- **Don't share** pricing externally — draft for my review first
