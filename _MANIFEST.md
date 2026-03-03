# _MANIFEST.md — Scott Campfire Workspace

> This file tells Claude which documents matter, in what order, and what to skip.
> Always read this file first before doing any work in this folder.

## Tier 1 — Canonical (Always Read First)
These are source-of-truth documents. Read before starting any task.

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Folder instructions — who I am, tools, preferences, rules |
| `about-me.md` | Detailed context about my role, goals, and background |
| `brand-voice.md` | How I communicate in writing — tone, style, patterns |
| `working-style.md` | How I want Claude to operate and prioritize |

## Tier 2 — Domain (Load When Task Touches This Area)

| Subfolder | Domain | Load When... |
|-----------|--------|-------------|
| `deals/` | Active deal workspaces, account plans | Working on a specific deal, prepping for a call, updating CRM |
| `prospecting/` | Outbound strategy, sequences, target accounts | Building pipeline, crafting outreach, account research |
| `meetings/` | Meeting prep docs, notes, follow-ups | Prepping for or following up after a meeting |
| `collateral/` | Sales decks, one-pagers, case studies, proposals | Creating or customizing customer-facing materials |
| `reports/` | Pipeline reports, forecasts, weekly summaries | Building reports, analyzing pipeline, forecast updates |
| `templates/` | Reusable email templates, proposal frameworks | Drafting repeatable content |
| `reference/` | Product knowledge, competitors, pricing, integrations | Answering product questions, competitive positioning |

## Tier 3 — Archival (Only When Explicitly Asked)
- Old deal files moved to `deals/_archive/`
- Previous quarter reports in `reports/_archive/`
- Superseded templates in `templates/_old/`

## External Source-of-Truth References
These live in Notion and should be queried via the Notion connector, not stored locally:
- Sales Knowledge Base (collection://2c04fe17-3c4a-809f-8762-000b904574c3)
- Sales Cycle Overview, Lead Routing Guide, Handoff Process (see CLAUDE.md for URLs)
- HubSpot Deal Fields reference
- **Scott Wiki** (https://www.notion.so/meetcampfire/Scott-Wiki-3164fe173c4a801f8eb7e263d2ed1b2d) — Personal sales knowledge base with pitch scripts, battle cards, objections, accounting concepts, and messaging frameworks. Fetch from Notion when handling competitive questions, prepping objection responses, or needing deep product/accounting context.

## Chroma DB Collections (Persistent Memory)
These live in Chroma and should be queried via the Chroma MCP connector:
- **`scott-campfire-memory`** — Project memory. Write to this after significant deal interactions, meeting outcomes, strategy decisions, and learnings. Query when starting tasks related to a known account or revisiting a prior topic.
- **`30mpc`** — "30 Minutes to Presidents Club" podcast transcripts (2,300+ episodes). Query for sales best practices on cold calling, objection handling, discovery, demos, negotiation, pipeline management, and closing.

## Context Loading Rules
1. Always read `_MANIFEST.md` and `CLAUDE.md` first
2. Load Tier 1 files for any task
3. Load Tier 2 subfolders only when the task touches that domain
4. Never load Tier 3 unless explicitly asked
5. When decomposing into sub-agents, scope each sub-agent to minimum required context
6. Query `scott-campfire-memory` in Chroma when a task references a prior interaction, known account, or past decision
7. Query `30mpc` in Chroma when drafting outreach, prepping for calls, handling objections, or referencing sales methodology
8. Write to `scott-campfire-memory` after completing significant tasks (meeting prep, deal reviews, strategy calls) to build persistent context
