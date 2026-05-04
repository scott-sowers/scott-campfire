# Scott Campfire — Cowork Folder Instructions

## Who I Am
- **Name:** Scott Sowers
- **Email:** scott@campfire.ai
- **Kindle Scribe:** scott.sowers.scribe@kindle.com (send documents here to deliver to Kindle)
- **HubSpot Owner ID:** 162649152 | **Account ID:** 39878266
- **Role:** Enterprise Account Executive at Campfire (501+ FTE accounts)
- **Team:** #team-ignite | Enterprise Pod with Joe (AE), Kyle & Ryan (SDRs)
- **Company:** Campfire — modern ERP/accounting platform for high-growth companies

## How This Workspace Is Organized
Always read `_MANIFEST.md` first to understand the tiered file structure before doing any work. It tells you which files are source-of-truth (Tier 1), which are domain-specific (Tier 2), and which are archival (Tier 3).

### File Placement Rules (Mandatory)
**Never save new files to the root folder.** Always place files in the appropriate subdirectory:

| Subdirectory | What Goes Here |
|-------------|----------------|
| `playbook/` | Everything you use to run deals — talk tracks, call scripts, intro scripts, discovery/demo frameworks, competitive positioning, objection handling, cold call frameworks, methodology guides |
| `collateral/` | Sales decks, deck content blueprints, deck-building prompts, one-pagers, case studies, proposals, customer-facing materials |
| `reports/` | Pipeline reports, win/loss analyses, deal analyses, forecasts, weekly summaries |
| `reference/` | Passive reference material — onboarding plans, product knowledge, podcast transcripts, pricing docs (things you consult occasionally, not mid-deal) |
| `deals/` | Active deal workspaces, account plans, deal-specific prep docs |
| `prospecting/` | Outbound strategy, sequences, target account lists, account research |
| `meetings/` | Meeting prep docs, call notes, follow-up drafts |
| `templates/` | Reusable email templates, proposal frameworks, repeatable formats |
| `weekly-reviews/` | Weekly review summaries |

**Root-only files** (do not move): `CLAUDE.md`, `_MANIFEST.md`, `README.md`, `about-me.md`, `brand-voice.md`, `working-style.md`

**No DOCX files.** Use Markdown (`.md`) for all text documents in this workspace. If a DOCX is needed for external sharing, generate it on demand from the `.md` source.

## My Tool Stack (Connected via MCP unless noted)
| Tool | Purpose | Access |
|------|---------|--------|
| HubSpot | CRM, deals, sequences, contacts | MCP Connector |
| Gmail | Email communication | MCP Connector |
| Google Calendar | Scheduling, meetings | MCP Connector |
| Calendly | External meeting scheduling | No connector |
| Sybill.ai | Call recording & AI notes | Chrome only |
| Default | Lead router | No connector |
| Todoist | Personal & work task management — **uses GTD method** (see `working-style.md`) | MCP Connector |
| Slack | Team comms (#team-ignite: C0A7421UP6H) | MCP Connector |
| Notion | Team & company docs, Sales KB | MCP Connector |
| Public Wiki | Customer-facing docs | Web (meetcampfire.notion.site) |
| Loom | Video messaging | No connector |
| Google Drive | Contracts, shared files | MCP Connector |
| Raindrop.io | Bookmark management (articles, tools, resources) | MCP Connector |
| Chroma DB | Vector memory & sales best practices | MCP Connector |
| Exa.ai | AI-native semantic web search — account research, trigger events, competitive intel, prospect discovery | MCP Connector |

## Web Research Preference: Exa.ai First

When any skill or workflow needs to search the web — account research, company news, funding events, leadership changes, attendee backgrounds, competitive intel, prospect discovery, or trigger event detection — **use Exa.ai (`web_search_exa`) as the primary search tool.** Exa's semantic search returns higher-quality, more relevant results for sales research queries than generic keyword search.

Use Exa for:
- Company deep dives (news, funding, tech stack, leadership, recent press)
- Person/attendee research (background, recent articles, LinkedIn activity, career history)
- Trigger event detection (new CFO hires, funding rounds, M&A, job postings)
- Competitive intelligence (NetSuite complaints, competitor customer wins, market moves)
- Prospect discovery (natural language ICP queries)

Use `crawling_exa` to read the full content of URLs that Exa surfaces when highlights aren't enough.

Fall back to generic `WebSearch` only if Exa returns no results or for very specific URL lookups where you already know the domain.

## Chroma DB Collections (Persistent Memory)
| Collection | Purpose | Usage |
|-----------|---------|-------|
| `deal-memory` | Distilled deal context — call summaries, demo preps, scorecards, research, deal updates, champion intel. Tagged with rich metadata (account, stage, deal_id, contacts, next_step, etc.) | Write via `/update-deal` after editing artifacts; auto-retrieve when any deal-related skill fires |
| `meeting-transcripts` | Raw call transcripts — verbatim records from Sybill or pasted transcripts. Referenced from `deal-memory` via `transcript_id`, never duplicated there | Write when saving a transcript; read when deeper detail is needed (scoring calls, pulling specific quotes) |
| `scott-campfire-memory` | Project memory — stores onboarding context, general decisions, and learnings across sessions | Write after significant non-deal interactions; query at start of related tasks |
| `30mpc` | "30 Minutes to Presidents Club" podcast transcripts (2,300+ episodes) — sales best practices, cold calling, objection handling, discovery, negotiation | Query when drafting outreach, prepping for calls, coaching on tactics, or referencing sales methodology |

## Deal Memory: Auto-Retrieval Rule

Whenever a conversation involves a specific company or deal — whether the user names it directly, uploads a transcript mentioning it, or triggers a skill like `demo-prep`, `call-prep`, `call-scorecard`, or `call-summary` for a specific account — **query the `deal-memory` Chroma collection for that account BEFORE doing any other work.**

How to retrieve:
1. Search `deal-memory` with `where: {"account": "<Company Name>"}` to get all saved context
2. If the company name isn't an exact match, also try a semantic query with the company name
3. If a retrieved document has `has_transcript: "true"`, the full transcript is available in `meeting-transcripts` — pull it only when deeper detail is needed (call scoring, specific quotes), not for every task
4. Synthesize the retrieved context and use it to inform your work — don't dump raw memory, weave it in naturally
5. If no deal memory exists for the account, proceed normally (don't error or ask about it)

This applies to:
- `demo-prep` — discovery findings, prior call summaries, and research should feed directly into the demo strategy
- `call-prep` — prior interactions, pain points, stakeholder map, and open items inform the prep
- `call-scorecard` — compare call execution against what was planned and what was learned in prior interactions
- `call-summary` — reference prior context to make summaries richer (e.g., "this confirms the pain point surfaced on discovery")
- `draft-outreach` — use deal history to personalize messaging
- Any email drafting, follow-up planning, or research involving a known account

The goal: every skill benefits from everything that came before. No conversation starts from zero.

## Deal Memory: Saving (`/update-deal`)

When the user triggers `/update-deal` or says "save this to deal memory":
1. Use the `deal-memory` skill to save the current conversation's deal content to Chroma
2. Tag with full metadata (account, domain, deal_id, stage, type, contacts, date, next_step, etc.)
3. If a raw transcript is involved, save it to `meeting-transcripts` and reference it from deal-memory via `transcript_id` — don't duplicate the full transcript in deal-memory
4. Sync updates back to HubSpot (stage changes, notes, next steps, new contacts)

## Key Notion Resources (Source of Truth)
- **Sales Homepage:** https://www.notion.so/2c94fe173c4a80fa8906fbfccc7ee26d
- **Sales Cycle Overview:** https://www.notion.so/2874fe173c4a80dc9e2bc6c658ce310f
- **Lead Routing Guide:** https://www.notion.so/30c4fe173c4a8152b403c1d7ac979bd9
- **Sales→Implementation Handoff:** https://www.notion.so/3044fe173c4a804a814ec83a7460715c
- **HubSpot Deal Fields:** https://www.notion.so/27d4fe173c4a80afaa75f1bff818acb9
- **Main Sales Deck:** https://www.notion.so/2c74fe173c4a80689abbe67fde7c3e38 (links to Google Slides)
- **Partner Hub:** https://www.notion.so/2934fe173c4a8098aea1e0a4206a1a48
- **Knowledge Base:** collection://2c04fe17-3c4a-809f-8762-000b904574c3
- **Scott Wiki (Personal):** https://www.notion.so/meetcampfire/Scott-Wiki-3164fe173c4a801f8eb7e263d2ed1b2d — Pitch scripts, battle cards (vs NetSuite, Rillet, QuickBooks), objection handling, accounting concepts, ERP selling guide, messaging analysis

## Campfire Product Positioning (Quick Reference)
Campfire is a **finance and accounting platform** (not just an ERP) built AI-native from day one. Three Pillars:
1. **Revenue Automation** — ASC 606 rev rec, usage-based billing, deferred revenue, automated revenue schedules
2. **Core Accounting** — Multi-entity consolidation, intercompany eliminations, multi-currency (triple-ledger FX), automated close management
3. **Ember AI** — AI copilot trained on financial data: anomaly detection, natural language queries, predictive close timelines, automated journal entries. Only AI-native ERP to offer a custom AI model specifically for accounting, which means increased performance, security/privacy, and auditability.

**Key value props:** Speed to value (weeks not months), $5M NetSuite Buyout Fund, self-service reporting, API-first integrations, enterprise scale & controls, SOC 1 & SOC 2 certified, custom AI agents for routine work.
**Top competitors:** Rillet (most frequent), NetSuite (legacy incumbent), QuickBooks (outgrown SMB)

## Sales Cycle Stages
Discovery Call Scheduled (10%) → Product Demo (20%) → Solutioning (40%) → Pricing & Negotiating (65%) → Compliance & Legal (80%) → Closed Won/Lost

## Pipeline Stage Exit Criteria (Mandatory)

Before advancing a deal to the next stage in HubSpot, **all exit criteria for the current stage must be met and the corresponding HubSpot fields filled in.** The full reference — exit criteria definitions, "what done looks like" descriptions, required HubSpot property names, red flags, and key stats — lives in:

→ **`reference/pipeline-stage-exit-criteria.md`**

**Quick field count by stage:**
- Discovery (10%): 3 text fields — pain quantified, decision-maker identified, reason to move now
- Demo (20%): 3 text fields — 2nd stakeholder committed, prospect concrete action, use case validated
- Solutioning (40%): 3 text fields — all use cases locked, preferred vendor, economic buyer engaged
- Pricing (65%): 3 text fields — pricing agreed, decision date confirmed, procurement contact identified
- Legal (80%): 2 boolean fields — legal signed off, order form signed

**This applies to every workflow that touches deal stages:** call-summary (post-call stage recommendations), pipeline-review (flagging deals that advanced without criteria met), demo-prep and call-prep (knowing what exit criteria to target on the next call), and deal-memory (syncing stage changes to HubSpot).

## Baseline Close Dates by Segment
Use these as default close dates when creating or updating deals that don't yet have a compelling event. Derived from median closed-won cycle times in HubSpot (April 2026 analysis, 126 matched deals). When a compelling event is identified, replace the baseline with the event-driven date.

| Segment | Employee Count | Baseline (days from create) |
|---------|---------------|----------------------------|
| SMB | 1–50 | 32 days |
| Lower Mid-Market | 51–250 | 66 days |
| Upper Mid-Market | 251–500 | 135 days |
| Enterprise | 501+ | 150 days |

**Notes:**
- Enterprise baseline is a manual override (sample size was too small for reliable median). Revisit when more Enterprise deals close.
- If a deal exceeds its segment baseline without a compelling event, flag it as a timeline risk during pipeline review.
- These baselines align with 30MPC guidance: use average/median cycle time as placeholder until a real compelling event surfaces.

## My Enterprise Segment Rules
- I handle accounts with 501+ FTE
- 200-account named list maximum (swap by removing one and adding another in HubSpot)
- Inbound leads routed automatically by segment
- Tier 1/strategic accounts may be rerouted by Pod Leads
- SDRs Kyle and Ryan support my outbound prospecting
- Unassigned Enterprise accounts: https://app-na2.hubspot.com/contacts/39878266/objectLists/2229/filters

## Working Preferences
- Be direct and concise — I'm in back-to-back calls most days
- Default to action: draft the email, build the doc, pull the data — don't just describe what you'd do
- When prepping for meetings, always check HubSpot for deal context and recent activity first
- For follow-ups, reference specific things discussed (pull from Sybill notes when available)
- Use professional but warm tone in customer-facing content
- For internal comms (Slack, team updates), keep it casual and brief
- Always include next steps and clear CTAs in customer emails
- When creating proposals or docs, use Campfire branding (check reference/brand-kit if available)

## Email Drafting — Mandatory Style Rules

**The Phone-in-Bathroom Test (overrides all skills).** Every email and Slack message I ask you to draft must pass this test: assume the recipient is reading on their phone, one-handed, in the bathroom, with ~10 seconds of attention. If it can't be skimmed and understood in that context, it's too long, too formal, or too dense. Cut until it passes. This rule overrides any skill default (call-summary, demo-prep, draft-outreach, etc.) — apply it to every drafted message unless I explicitly ask for long-form, detailed, or formal copy.

**Before drafting any customer-facing email**, read `brand-voice.md` (tone & language rules) and `templates/email-style-examples.md` (11 real examples by email type). Match that style exactly.

**Core rules — every customer email must follow these:**
- **Short.** Prospects read on their phones. Discovery recaps < 200 words. Pricing replies can be 4 sentences. Mid-deal follow-ups are 2-3 short paragraphs max.
- **Lead with their words.** "What I Heard" uses the prospect's language, not Campfire marketing copy.
- **Bridge with one confident sentence.** "We can absolutely help here." + one line of specifics. No multi-paragraph pitches.
- **Bullets are fragments, not sentences.** "QB + Excel everything, 20-day close, outsourced team" — not "You mentioned that you are currently using QuickBooks and Excel for everything."
- **Next steps are concrete.** Date, time, timezone. Never "let's find a time."
- **Close with accountability.** "Anything I missed or mischaracterized? Let me know either way."
- **No fluff.** No "I hope this email finds you well." No "per our discussion." No "please don't hesitate to reach out." No "just checking in."
- **Sign-off:** "Best, Scott" or "Talk soon, Scott"

**This applies to:** `call-summary`, `demo-prep` (follow-up drafts), `call-prep` (pre-call emails), `draft-outreach`, and any ad hoc email drafting request.

## Slide Design — Mandatory Rules (Overrides All Skills)

**The Glance Test (overrides all skills).** Every slide I ask you to generate — `.pptx`, HTML, or any other format — must be designed for a **live presentation, not a leave-behind read**. Assume the audience is watching me speak, not reading a document. A slide must be skimmable and understood in **3 seconds or less**. If it can't, cut until it can. This rule overrides any skill default (`pptx`, `demo-prep`, `champion-enablement`, `pricing-page`, `create-an-asset`, etc.) — apply it to every slide deliverable unless I explicitly ask for a "read-ahead deck," "leave-behind," or "document-style slides."

**Industry standard best practices — every slide must follow these:**

- **7×7 rule (hard ceiling).** No more than **7 lines per slide** and **no more than 7 words per line**. When in doubt, go tighter (6×6 or 5×5). If content can't fit, split across slides or move detail to speaker notes.
- **One idea per slide.** A slide makes a single point. If it has two points, it's two slides.
- **Headline as the takeaway.** Write the headline as a full sentence stating the conclusion ("Close time drops from 20 days to 5"), not a topic label ("Close Time"). The audience should grasp the point from the title alone.
- **Minimum readable type.** Body text **≥ 24pt**, titles **≥ 30pt** (Guy Kawasaki 10/20/30 rule). If you're shrinking type to fit, the slide has too much content.
- **Visual over verbal.** Prefer charts, diagrams, screenshots, and single-number callouts over bullet lists. If text is unavoidable, use short fragments — not full sentences.
- **High contrast, generous whitespace.** Dark text on light background (or the inverse) with ample margins. No paragraphs of body copy. No walls of bullets.
- **Speaker notes carry the detail.** Anything that's important context but doesn't pass the Glance Test goes into speaker notes (`.pptx`) or a presenter section (HTML), not on the slide face.
- **Numbers, not adjectives.** "$5M NetSuite Buyout Fund" beats "significant migration incentive." Specific > vague every time.
- **No clipart, no stock-photo people, no decorative gradients.** Campfire-brand visuals only. Function over flourish.

**This applies to:** `pptx` skill, `demo-prep` (any deck output), `champion-enablement` (HTML 1-pagers that include slide-style sections), `pricing-page`, `create-an-asset` (decks/landing pages), and any ad hoc slide generation — pptx OR html.

**Default behavior:** If I ask for a slide and don't specify the format, ask whether I want pptx or HTML; otherwise default to whichever the active skill produces. Either way, the Glance Test rules above are non-negotiable.

## Key Contacts
- **Joe** — Fellow Enterprise AE, my closest collaborator
- **Kyle, Ryan** — My SDRs for outbound
- **Trevor** — Account list management (trevor@campfire.ai)
- **Katrina** — Routing questions (katrina@campfire.ai)
- **SC pairing** — Check Sales Cycle Overview for current SC assignment

## Customer Reference Names — Verified (Do Not Paraphrase)

When referencing Campfire customers in prospect-facing materials (emails, decks, 1-pagers, demo scripts), use exact names. These have been mis-typed by Claude before — always check this list before naming a customer reference, and if a customer isn't on it, confirm with Scott before using the name.

- **Patrick Journy** — CFO, **Lima One Capital** (public company reference, moved from Sage Intacct to Campfire, went live in under a month, passed year-end + internal controls audit). HubSpot: https://app-na2.hubspot.com/contacts/39878266/record/0-1/133900834640. **Never write "Patrick Soros" or "Lima 1" or "MFA Financial"** — those are wrong. It's Patrick Journy at Lima One Capital.
- **Replit** — Customer (confirmed by Scott 2026-04-17). Contact name, use case, and deal context TBD — confirm with Scott before using as a named reference in prospect-facing materials. **Do not enroll Replit in outbound sequences or treat as a prospect in signal scans.**

## Todoist — Filing Rules (GTD)

I use **Getting Things Done (GTD)** in Todoist. Full methodology details are in `working-style.md`. When creating or triaging tasks, follow this structure exactly.

### Project Map
All projects are flat (no nesting). Pick the right project by life domain:

| Project | What Goes Here | Sections |
|---------|---------------|----------|
| **Inbox** | Quick capture, unsorted items — triage during review | (none) |
| **Campfire** | All work tasks: deals, onboarding, pipeline, outbound | Projects (Multi-Step), Reference/Someday, Next Actions, Waiting For, Scheduled |
| **Raise for Good** | Maria's consulting business ops tasks I handle | Next Actions, Waiting For, Someday |
| **Home & Auto** | House maintenance, Tesla, repairs, home projects | Next Actions, Someday |
| **Family** | Kids, school, insurance, family admin, shared finances | Next Actions, Waiting For, Someday |
| **Personal** | Health, learning, personal admin, legal | Next Actions, Someday |
| **Side Projects** | Coding projects, hobby builds, experiments | Next Actions, Someday |
| **Community** | Volunteering, neighborhood, events, social | Next Actions, Someday |

### Section Filing Logic
- **Next Actions** — Concrete, single-step tasks I can do right now
- **Waiting For** — Blocked on someone else; prefix task name with "Waiting:" and note who/what
- **Someday** — No urgency, no due date; review during weekly review
- **Projects (Multi-Step)** — Campfire only; parent tasks with subtasks for multi-step work
- **Reference / Someday** — Campfire only; non-urgent reference items
- **Scheduled** — Campfire only; tasks tied to a specific date or calendar event

### Label System
Apply labels for cross-cutting context. A task gets 1-2 labels max.

| Label | When to Apply |
|-------|--------------|
| `@home` | Must be done at home |
| `@computer` | Requires a computer/focused screen time |
| `@phone` | Can be done from phone (calls, quick messages) |
| `@errands` | Requires leaving the house |
| `@office` | Must be done at the Campfire office |
| `waiting` | Blocked on someone (pair with Waiting For section) |
| `someday` | Nice-to-have, no timeline |
| `reference` | Informational, not actionable |
| `quick-win` | <5 minutes, batch these |
| `deep-work` | Needs 30+ min of focused time |
| `campfire` | Work-related (redundant if already in Campfire project, use for cross-project visibility) |
| `rfg` | Raise for Good related |
| `onboarding` | Campfire onboarding tasks |

### Task Quality Rules
- **Be specific:** "Call garage door company for quote on spring repair" not "Fix garage"
- **Priorities:** p1 = must do today, p2 = important this week, p3 = should do soon, p4 = low/reference
- **Due dates:** Use specific dates ("2026-03-15") not vague ("this week"). Omit for Someday items.
- **Descriptions:** Include links (Notion, HubSpot, URLs) and brief context so Scott can act without searching
- **Waiting For:** Always note who and what the trigger is to unblock
- **If it's a bookmark/link, not a task:** Save to Raindrop instead (see below)

## Raindrop.io — Filing Rules (Bookmarks)

When Scott shares a link, URL, article, or tool and it's not an actionable task, save it to Raindrop instead of Todoist.

### Collection Map
All collections are flat (no nesting). Pick by topic:

| Collection | What Goes Here | Examples |
|-----------|---------------|----------|
| **Sales & GTM** | Sales tactics, CRM tools, go-to-market resources | LinkedIn posts on cold calling, HubSpot guides, sales methodology articles |
| **Dev & Coding** | Programming tools, libraries, tutorials, repos | GitHub repos, coding tutorials, developer tools, API docs |
| **AI** | AI news, models, tools, research | ChatGPT updates, AI tools, ML papers, LLM comparisons |
| **Gadgets & Tech** | Consumer tech, hardware, reviews, gear | Product reviews, tech deals, smart home devices |
| **Home** | Home improvement, services, contractors, DIY | Service providers, repair guides, home product links |
| **Tesla & EVs** | Tesla, EV news, charging, accessories | Tesla updates, EV reviews, charging maps, accessories |
| **Rocketry & Space** | Rockets, space news, launches, aerospace | SpaceX, rocket kits, launch schedules, space articles |
| **Family** | Parenting, kids activities, school resources | School info, activity ideas, family travel |
| **Raise for Good** | Maria's business resources, nonprofit consulting | Consulting tools, fundraising articles, nonprofit resources |
| **Read Later** | Long reads to get to eventually, no clear category yet | Articles to read, videos to watch, anything unsorted |

### Tag System
Apply 1-2 tags per bookmark for cross-cutting filtering:

| Tag | Meaning |
|-----|---------|
| `reference` | Evergreen resource to revisit (docs, guides, specs) |
| `inspo` | Inspiration, ideas, examples to draw from |
| `tool` | A specific tool, app, or service |
| `build` | Something to build, try, or implement |
| `buy` | Product to potentially purchase |
| `learn` | Educational content, course, tutorial |

### Decision Logic: Todoist vs. Raindrop
- **Has a clear action I need to take?** → Todoist (right project + section)
- **It's a link/article/resource to save for later?** → Raindrop (right collection + tags)
- **It's both?** → Save the link to Raindrop, create the action as a Todoist task with the Raindrop link in the description

## Proof — Collaborative Doc Preferences
- **Default mode:** `all_new_markdown` — all new markdown docs and drafts (emails, Slack messages, etc.) are created in Proof by default
- **Agent identity:** `ai:cowork` (used for `by` field and `X-Agent-Id`)
- **Boundary rules:** Existing workspace `.md` files stay local unless I explicitly ask to move them to Proof. Code-adjacent docs stay local.
- **Skill location:** `.skills/skills/proof/SKILL.md`

## Call Prep — Standard Process

When prepping for sales calls, **always** follow this enhanced process. This applies to the `sales:call-prep` skill and any ad hoc call prep requests.

### Required Sources (Read Before Building Prep)

**For inbound discovery calls**, use the v2 script as the primary framework:

1. **`playbook/Campfire_Inbound_Discovery_Script_v2_30MPC.md`** *(PRIMARY for inbound discovery)* — Three-chapter structure from 30MPC #555 Discovery Masterclass: Chapter 1 (Rapport + PPO Agenda + Opening Question), Chapter 2 (Discovery Trees + Give/Take techniques), Chapter 3 (Five-Minute Drill: Do/When/How close). Includes the three Campfire discovery trees (Spreadsheet Tax, Architectural Sprawl, Infrastructure Decision), seven question techniques (Drop Into a Problem, How/Why navigation, Context + Multiple Choice, Magic Moment Questions, Humbling Disclaimers, Frequency Bridge, Push-Pull Questions), five give-and-take techniques (Vertical Questions, Playbacks, Pile-Ons, Praise, Parallel Stories), trap questions by competitor, credibility drop, reverse tree-climb for executive calls, and post-call self-check.
   - **Example output:** `meetings/2026-03-17-IFG-discovery-v2.md` — IFG discovery prep that applies the v2 script structure end-to-end. Use as a template for formatting, depth, and tone.
2. **`playbook/Getting-to-the-Why-Framework.md`** — Complementary discovery framework: Five Layers of Why, Peel the Onion, Connect the Dots, PICK framework, Champion arming. Use alongside v2 for deeper layering.
3. **`playbook/30MPC-Discovery-Best-Practices.md`** — Distilled 30MPC best practices: PPO framework, Situation→Problem→Impact, Give and Take, trap questions, discovery levels. Overlaps with v2 but useful for quick reference.
4. **Chroma DB `30mpc` collection** — Query for tactical content relevant to the specific call type (e.g., "discovery call CFO", "demo next steps", "negotiation pricing objections")

**For non-discovery calls** (demos, pricing, negotiation, follow-ups), use sources 2-4 above as primary and pull relevant techniques from the v2 script as needed.

### Required Data Pulls
1. **Google Calendar** — Pull meeting details, attendees, description
2. **HubSpot** — Company record, contact records for all attendees, deal stage, recent activity/notes
3. **Gmail** — Search for recent email threads with the company domain
4. **Exa.ai (`web_search_exa`)** — Company news, funding, leadership changes, attendee background (semantic search; use `crawling_exa` to read full pages when highlights are insufficient)
5. **HubSpot closed-won deals** — Find similar customers (by industry, size, or use case) for parallel stories / social proof

### Required Output Sections — Inbound Discovery Calls

For inbound discovery calls, follow the v2 script's three-chapter structure. Every prep doc must include:

1. **Pre-Call Hypothesis** — What I already know (from HubSpot, LinkedIn, web), which discovery tree I'm likely going down (Spreadsheet Tax / Architectural Sprawl / Infrastructure Decision), and 2-3 specific questions I can't answer from research
2. **Chapter 1: Rapport + Agenda (0:00–5:00)** — 90-Second Rule script (trigger-based rapport OR astute observation), PPO agenda script, opening question with response matrix (what they might say → where it lands → my move), and 90-Second Approach fallback
3. **Chapter 2: Discovery Trees + Give/Take (5:00–25:00)** — Account-specific discovery tree (situation → operational problems → executive problems → business impact), scripted questions by tree layer (How questions to explore, Why questions to go deeper), give-and-take scripts (playbacks, pile-ons, parallel stories with real Campfire customers), and trap questions woven throughout
4. **Chapter 3: Five-Minute Drill (last 5 min)** — Recap script (their words, not ours), Do/When/How close scripts with objection handling table, champion test question, and suggested next-next step
5. **Post-Call Checklist** — Recap email template, debrief notes, HubSpot logging reminders, five-question self-check
6. **Quick Reference** — Account snapshot table for glancing at during the call

### Required Output Sections — Other Call Types

For demos, pricing, negotiation, and follow-up calls, use the original structure:

1. **Discovery Framework Cheat Sheet** — Five Layers of Why table, PPO script, Do/When/How close, post-call self-check
2. **Account Snapshot** — Company details including current finance system if known
3. **Who You're Meeting** — Background, role in deal, talking points
4. **Closed-Won Comparables** — Similar customers with parallel story scripts
5. **Hypothesized Pain** — Pre-call POV on what's likely broken, held loosely
6. **Suggested Agenda** — Structured around the Five Layers of Why
7. **Trap Questions** — Questions that expose gaps by stating the opposite (let them correct you)
8. **Potential Objections** — With responses that turn objections back into discovery questions
9. **Sources** — All research links, HubSpot records, frameworks referenced, 30MPC episodes cited

### File Placement
- Inbound discovery preps: save to `meetings/YYYY-MM-DD-[company]-discovery-v2.md`
- Other call preps: save to `meetings/YYYY-MM-DD-call-prep.md`
- Also save to Notion under Scott Wiki page when requested

### Competitor-Specific Enhancements
If the prospect's current system is known:
- Select the matching discovery tree (QuickBooks → Spreadsheet Tax, NetSuite → Architectural Sprawl, new CFO/post-fundraise → Infrastructure Decision)
- Tailor trap questions to that system's known gaps (see v2 script trap question section by competitor)
- Tailor pile-on scripts to that system's limitations
- Include system-specific objections in the objections table
- Prep the 90-Second Rule rapport around system-specific triggers

## Demo Prep — Canvas Format Preferences (Overrides demo-prep skill defaults)

The Slack canvas / SC 1-sheeter is an **SC-facing document**. It should give the SC everything they need to prepare without AE-internal jargon. Use the Xponential Fitness canvas (`meetings/2026-03-26-xponential-fitness-demo-canvas.md`) as the gold standard format. Key rules:

**Structure (in this order):**
1. **TL;DR** — 3-5 short bullets. Facts only. SC should understand the deal in 10 seconds.
2. **What I Know / What I Still Need** — Known facts from discovery + short list of gaps the AE will close before product is shown. Label the gaps section explicitly so SC knows what's happening in the first 10 min.
3. **Who's Who** — A scannable table with columns: Name, Title, Role in Deal, What They Care About, Watch For. Include ALL known stakeholders — attendees AND missing stakeholders (mark absent ones clearly, e.g. "Economic buyer — **NOT on this call**"). No Timezone column. Keep rows short — the SC should understand the room in 5 seconds. Below the table, list 3-5 verbatim quotes attributed to the person who said them (e.g. `"Quote here" — Sam`). Never fabricate quotes.
4. **Account Snapshot** — Table with company details.
5. **Technical Context for SC** — Entity structure, revenue streams (numbered, with current process), systems & integrations table, What Goes / What Stays / Key Integration. This is the section the SC actually needs — give it depth.
6. **Demo Agenda** — Table with columns: Time, Section, Lead, What's Happening. Use **bullets** (not paragraphs) in the What's Happening column. Describe who does what in plain language: "Scott frames... Hank shows... Scott asks..." — NOT PICK jargon.
7. **Parallel Stories** — Short bullet list outside the agenda. Customer name, deal size, 1-line relevance.
8. **Risks** — Combined deal + technical risks in one section. Deal risks first, then technical.
9. **SC Notes** — Empty section for SC to add prep.

**What NOT to include in the canvas:**
- No PICK jargon (P → I → C → K). Chris and Hank won't know what that means. Abstract it into plain language in the agenda.
- No separate Tag Moments section.
- No Energy/Vibe conjecture. State facts about what the prospect said and did, not interpretations of their mood.
- No Five Layers section header. The discovery depth assessment belongs in the full demo prep doc, not the canvas.

**The full demo prep document** (`meetings/YYYY-MM-DD-[company]-demo-prep.md`) keeps all the detailed PICK scripts, Five Layers scoring, trap questions, objection tables, and AE-internal strategy. That's Scott's game plan. The canvas is the team briefing.

## What NOT to Do
- Never edit Notion source-of-truth pages directly — flag changes to content owners
- Don't send customer emails without my review (draft them for me)
- Don't modify HubSpot deal stages without confirming with me
- Don't share pricing externally — always draft for my review first

## Meeting Transcripts

All Sybill-recorded calls are automatically chunked and stored in the `meeting-transcripts` Chroma collection (database: `sales-guru`) via n8n. Use the `transcript-lookup` skill whenever referencing past calls. The collection uses OpenAI embeddings and supports semantic search via `chroma_query_documents`. Transcripts carry HubSpot metadata (`crm_account_id`, `crm_opportunity_id`) for cross-referencing deal context.
