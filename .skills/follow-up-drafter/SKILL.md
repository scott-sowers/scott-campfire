---
name: follow-up-drafter
description: "**Follow-Up Email Drafter**: Drafts personalized follow-up emails after sales meetings. Triggers whenever the user asks to write, draft, or compose a follow-up email after a call, meeting, demo, or customer interaction. Also triggers for 'send the follow-up', 'recap email', 'post-call email', 'thank them for the meeting', or any request to communicate with a prospect after an interaction. References templates, meeting context, and Campfire collateral to create actionable follow-ups."
---

# Follow-Up Email Drafter Skill

Draft personalized, action-oriented follow-up emails after customer interactions.

## Trigger Contexts
- User asks to draft a follow-up email after a meeting
- User asks to send a recap or thank-you email
- User wants to share materials after a call

## Execution Steps

### Step 1: Gather Meeting Context
Determine which meeting this follow-up is for:
- Check Google Calendar for recent meetings (last 24 hours)
- Pull the HubSpot deal record for the company
- Check if there are meeting prep notes in `meetings/prep/`
- Ask the user for any specific discussion points to include

### Step 2: Determine Follow-Up Type
Based on the deal stage and meeting type, select the appropriate template:

| Meeting Type | Template | Key Elements |
|-------------|----------|-------------|
| Discovery | `templates/discovery-follow-up.md` | Materials package, demo scheduling |
| Demo | `templates/demo-follow-up.md` | Highlights recap, next steps |
| Pricing | Custom | Proposal/pricing follow-up |
| General | Custom | Meeting recap, action items |

### Step 3: Draft the Email
Follow these rules:
- **Under 150 words** for the body
- Open with something specific to the conversation (never "just checking in")
- Reference 1-2 specific discussion points
- Include any promised materials or resources
- End with a clear CTA and proposed next step with specific timing
- Professional but warm tone (see brand-voice.md)
- Sign off: "Best," + name

### Step 4: Standard Materials Package
For discovery follow-ups, always include links to:
1. Customized slide deck (or main deck if no custom version exists)
2. Integration list
3. SOC 1 & SOC 2 reports
4. API documentation

### Step 5: Present Draft
Show the draft to the user for review. Do NOT send without explicit approval.
Save draft to `meetings/follow-ups/follow-up-{company}-{YYYY-MM-DD}.md`

### Step 6: Save to Memory
After the draft is approved or finalized, write to `scott-campfire-memory` in Chroma DB with:
- ID format: `{account-slug}::{YYYY-MM-DD}::follow-up`
- Metadata: `{"account": "{company}", "type": "follow-up", "meeting_type": "{type}", "date": "{YYYY-MM-DD}"}`
- Content: Brief summary of what was discussed, what was sent, and next steps agreed upon

## Important Notes
- Never send customer emails without user review
- Always personalize — no generic templates going out the door
- If the user provides Sybill notes or a meeting recording summary, use specific quotes and topics from the conversation
- For demo follow-ups, coordinate with the SC on any technical items to include
- Query `scott-campfire-memory` for prior interactions with this account to maintain continuity
- Query `30mpc` for follow-up best practices relevant to the meeting type (e.g., post-discovery, post-demo)
- Use CTA patterns from brand-voice.md matched to the deal stage (Discovery→Demo, Demo→Pricing, Pricing→Close, Stalled→Reference Call)
- Use language patterns from Scott Wiki messaging analysis: "AI-native" not "AI-powered," "finance operating system" not "ERP," lead with their specific pain point
- For competitive situations, weave in relevant positioning from the battle cards (Scott Wiki) without being overtly competitive
- For NetSuite replacement deals, mention the Buyout Fund in follow-up when appropriate
