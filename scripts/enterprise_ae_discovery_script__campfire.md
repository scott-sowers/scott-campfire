# Enterprise AE Discovery Script

**Based on Talk Tracks from Joseph Riley & John Glasgow**

* * *

## I. OPENING & RAPPORT (3-5 min)

### Warm Introduction

*   **Personal connection**: "Happy Friday! How's your week been?"
    
*   **Location/context**: "Where are you based? We're in San Francisco..."
    
*   **Build rapport**: Find common ground (location, background, industry)
    

### Set the Agenda

> "Typically how I run these is: quick intro, learn what brings you to the call today, share high-level information about Campfire, answer your questions, and if it makes sense, get a full product demonstration scheduled. Does that work for you or is there anything else you're looking to get out of this call?"

* * *

## II. DISCOVERY FRAMEWORK

### A. Company Background & Context

**Ask:**

*   Company size, employees, revenue scale
    
*   Industry/vertical
    
*   Years in business, stage (Series A-D, pre-IPO, public)
    
*   Geographic footprint (entities, countries)
    

**Joseph's approach:**

> "Could you give a quick intro and share what brings you to the call today?"

**Listen for:**

*   Growth trajectory
    
*   Complexity indicators (multi-entity, multi-currency)
    
*   Regulatory requirements (audit, IPO-readiness)
    

* * *

### B. Current Tech Stack Deep Dive

**Essential questions:**

#### ERP/GL

*   "What ERP are you using today?" (NetSuite, Sage Intacct, QuickBooks, Oracle)
    
*   "How long have you been on it?"
    
*   "What's your contract look like? Multi-year?"
    

#### Order-to-Cash

*   "What does your order-to-cash flow look like?"
    
*   "Are you using Salesforce/HubSpot? Do you have CPQ?"
    
*   "How are you handling revenue recognition today?" (Zuora, Maxio, RevPro, Tabs)
    
*   "Are you using Stripe or another payment processor?"
    

#### Procure-to-Pay

*   "What AP solution are you using?" (Bill.com, Ramp, Brex, Approval Max)
    
*   "How are you handling vendor payments?"
    

#### Supporting Systems

*   "What payroll provider?" (UKG, ADP, Rippling, Deel)
    
*   "Tax system?" (Avalara, Anrok)
    
*   "FP&A tool?" (Adaptive, Mosaic)
    
*   "Close management?" (FloQast, Numeric, Blackline)
    

**John's framing:**

> "Challenge with NetSuite was customer reporting sucks, very hard to integrate stuff. Most folks don't even have ADP integrated for payroll. Everything's very manual, not scalable at all."

* * *

### C. Pain Points Discovery (CRITICAL)

#### NetSuite-Specific Pains

**Ask directly:**

*   "What are the biggest pain points with NetSuite today?"
    

**Listen & validate common issues:**

1.  **Clunky UI / Poor User Experience**
    

> "Typical things I hear: very clunky user interface, poor customization, poor integrations, reporting is clunky and difficult"

1.  **Transaction Volume Limitations**
    

> "NetSuite can't handle very high transaction volume. You end up summarizing your transaction data, which really limits reporting capabilities, makes audits a pain, and limits AI capabilities"

1.  **Integration Hell**
    

> "Every time you try to do something innovative, you have to get systems resources to build an integration. These legacy systems aren't flexible."

1.  **Cost Escalation**
    

> "Change requests – every single one is 100+ hours with consultants. And then there's the renewal where they double your cost with no added value"

1.  **Support Issues**
    

> "Very limited support from NetSuite. You're basically on your own"

#### Revenue Recognition Pains

*   "High frequency of modifications to contracts?"
    
*   "Struggle with usage-based billing?"
    
*   "Issues with multi-element arrangements / SSP?"
    
*   "Manual revenue waterfalls and deferrals?"
    

**Joseph's validation:**

> "The biggest areas customers were looking to solve: very clunky UI, difficult customization, poor integrations, clunky reporting, and NetSuite can't handle high transaction volume"

* * *

### D. Business Requirements Deep Dive

#### Multi-Entity & Currency

*   "How many entities do you have?"
    
*   "Which countries/currencies?"
    
*   "Do you need multi-book? (Local GAAP + US GAAP)"
    
*   "How do you handle consolidations and eliminations today?"
    

**Validate fit:**

> "We have customers with hundreds of entities, operate in almost every continent. We have triple ledger – every transaction shows transactional, functional, and consolidating currency. Makes FX revaluation and translation much easier."

#### Transaction Volume & Scale

*   "What's your monthly transaction volume?"
    
*   "How many invoices per month?"
    
*   "How do you get data into NetSuite today – summarized or detailed?"
    

**Differentiate Campfire:**

> "We can ingest billions of rows of data. Most fintech customers bring every single transaction in – no summarization. That means AI can parse through everything, audit is cleaner, reporting is more powerful"

#### Revenue Complexity

*   "Subscription, usage, milestone, or hybrid?"
    
*   "Do you have overage billing?"
    
*   "Contract modifications mid-term?"
    
*   "Minimum commitments?"
    
*   "Professional services/T&M?"
    

**Joseph's qualifying:**

> "We support subscription, usage, and milestone very well in Campfire. You can modify contracts mid-contract easily – much more flexible than NetSuite's 'set it and forget it' approach"

* * *

### E. AI & Automation Interest

**Gauge appetite:**

*   "Are there any AI initiatives at the company?"
    
*   "How open is your team to using AI for accounting workflows?"
    

**John's pitch:**

> "We have our own foundational model called Accounting Intelligence. It's our own foundational model running on our own GPUs here in SF. From a performance, auditability, and security perspective, we can be better than off-the-shelf models."

**Use cases to highlight:**

*   Flux analysis: "AI drafts commentary based on transaction details"
    
*   Accrual identification: "AI identifies missing accruals every month"
    
*   Policy compliance: "Upload your accounting policies – fixed asset, prepaid, lease – and AI will audit against them"
    
*   Receipt ingestion: "Ramp receipts flow in automatically, AI categorizes"
    

* * *

### F. Timing & Decision Process

**Critical questions:**

#### Contract Status

*   "What does your NetSuite/current ERP contract look like?"
    
*   "When does it expire?"
    
*   "Are you in the first year or later?"
    

**If early in contract:**

> "Just so you know, we have a $5M buyout fund. We can buy out the prorated remainder of your NetSuite contract so you're not double-paying. We did this for customers like Kelly at Speedy"

#### Evaluation Stage

*   "Where are you in the evaluation process?"
    
*   "Are you looking at other solutions?" (Tabs, Rillet, Sage Intacct)
    
*   "Who's involved in the decision?" (CFO, Controller, VP Finance, Engineering)
    
*   "What's driving the urgency?" (IPO prep, audit issues, growth, M&A)
    

**John's framing for early-stage evaluations:**

> "I know you just went live with NetSuite, but we've moved companies who spent three months on NetSuite, realized it wasn't going to work, and ripped it out for Campfire"

* * *

## III. CAMPFIRE VALUE PROPOSITION

### A. Core Differentiation

**The Elevator Pitch (John's version):**

> "We're a modern NetSuite. Challenge with NetSuite: customer reporting sucks, very hard to integrate, everything's manual and not scalable. We have core accounting (NetSuite competitor), plus close management (replaces FloQast/Numeric), revenue automation (replaces Maxio/Zuora), and the AI layer – much broader context than just plugging NetSuite into Claude"

### B. Key Capabilities to Emphasize

#### 1\. **Unlimited Scale**

*   Billions of rows of transaction data
    
*   No summarization needed
    
*   Million+ transactions per month customers
    

#### 2\. **Integration Superiority**

*   Open API, strong API documentation
    
*   200+ native payroll integrations
    
*   Native Salesforce/HubSpot integrations (no Celigo needed)
    
*   12,000+ bank connections
    
*   Custom integrations built by our team
    

#### 3\. **AI-Native Platform**

*   Own foundational model (Accounting Intelligence)
    
*   AI agents: accruals, flux, compliance, collections
    
*   Continuous close automation
    
*   Policy audit and anomaly detection
    

#### 4\. **Revenue Automation**

*   Handle subscription, usage, milestone
    
*   Easy contract modifications
    
*   SSP automation (v2 with ranges coming)
    
*   Prorated renewals and credit memos
    
*   Usage sub-ledgers from Snowflake/Databricks
    

#### 5\. **Fast Implementation**

*   2-3 months average (vs. 6-12 for NetSuite)
    
*   In-house implementation team
    
*   No third-party consultant required
    
*   Implementation cost included in platform fee
    

#### 6\. **Superior Support**

*   Unlimited live support
    
*   Direct Slack/Teams channel
    
*   Can jump on calls anytime for reconfigs
    

#### 7\. **Audit & Compliance Ready**

*   SOC 2 compliant
    
*   Big Four audited
    
*   IPO-ready customers (Replit, Decagon)
    
*   Public company customers
    
*   Strong ITGC framework with AI controls
    

* * *

### C. Pricing Positioning

**Joseph's approach:**

> "Typically we're coming in about 75% of a NetSuite contract \[25% cheaper\], and implementation and support are included – no extra cost. We do 2-3 year contracts typically because companies don't plan to change ERP in that time"

**User/Entity model:**

*   Price on users (GL-posting only) + entities
    
*   Unlimited viewer licenses (auditors, executives, analysts)
    
*   Can project growth: "If you have 50 users today but projecting 60, we build that in"
    

**Cost comparison points:**

*   NetSuite: license + consultant fees + support + customization hours
    
*   Campfire: all-in platform fee (implementation, support included)
    

**For complex integrations:**

> "For Salesforce custom objects and complex integrations, we're looking at $12-17K/year range depending on complexity. Standard integrations are included in base pricing around $6K"

* * *

## IV. QUALIFICATION CRITERIA

### Must-Haves for Good Fit:

✅ **100-5,000 employees** (sweet spot: 250-1,500)  
✅ **Tech or tech-enabled company**  
✅ **High transaction volume** or complex revenue  
✅ **Multi-entity/multi-currency** needs  
✅ **Currently on NetSuite, Intacct, or QuickBooks**  
✅ **Audit requirements** (Big Four, IPO-prep, public)  
✅ **Open to AI** and modern tools  
✅ **Integration-heavy** tech stack

### Watch-Outs:

⚠️ **Using NetSuite as one-stop-shop for everything** (AP, AR, everything)  
⚠️ **Highly specialized industry** (heavy manufacturing with MRP needs)  
⚠️ **Extreme localization** (e.g., UAE data residency)  
⚠️ **No pain with current system** ("if it ain't broke...")  
⚠️ **Just signed multi-year NetSuite deal** (but mention buyout fund!)

* * *

## V. OBJECTION HANDLING

### "We just implemented NetSuite"

**Response:**

> "I hear you. We've had customers like Kelly at Speedy who spent three months on NetSuite, realized it wouldn't work, and moved to Campfire. We have a $5M buyout fund to cover your remaining contract, so you're not double-paying. That said, we can also explore timing that makes sense – would love to show you what modern ERP looks like even if timing is 12-18 months out"

* * *

### "We need AP in the ERP"

**Response:**

> "Totally understand. We integrate with AP solutions like Bill.com, Ramp, Brex, Approval Max. Most customers prefer best-in-class AP tools anyway. We can show you how seamless the integration is – and honestly, you get better AP functionality than NetSuite's native module"

* * *

### "Too new / want something mature"

**John's response:**

> "We're about 4 years old, have customers processing $2B+ in volume, customers with 500+ employees, and we're Big Four audited ourselves. Replit went from $10M to $300M ARR on Campfire with only 3 finance people. We're newer than NetSuite, but that's the point – we're built on modern infrastructure that can actually handle AI natively, not bolted on to 30-year-old architecture"

* * *

### "Already looking at Tabs/Rillet"

**Response:**

> "Great companies. From what we've seen, customers evaluate Tabs when they need very specific revenue scenarios we don't cover natively. But for 80% of companies, we cover subscription, usage, milestone, and can build custom usage sub-ledgers. Tabs alone costs as much or more than Campfire – and you'd still need a separate ERP. We do it all in one platform. Happy to do a demo and let you compare"

* * *

### "Can your AI be trusted?"

**Response:**

> "Great question – this is why we built Accounting Intelligence as our own foundational model. We worked closely with PwC to build AI with controls baked in. AI will draft journal entries, accruals, flux analysis – but there's always human approval before posting to GL. We publish the audit trail – every AI-generated entry shows the chat context, prompts, and source data. Big Four auditors have cleared our IPO-ready customers with AI in use"

* * *

## VI. CLOSING & NEXT STEPS

### Strong Close (Joseph's approach):

> "Based on what you've shared today – \[summarize their pain points\] – I think Campfire could be a great fit. What I'd love to do is get a full product demo scheduled with you and \[key stakeholders\]. We'd focus on \[their top 3 priorities: GL/reporting/revenue\]. We need about an hour. What does your calendar look like over the next 1-2 weeks?"

### If They Need to Debrief:

> "Totally understand you'll want to discuss internally. What I'll do is send over a placeholder for \[specific date/time\], and you can move it as needed. I'll also send a follow-up email with some resources. If any questions come up as you're discussing, just hit reply – or here's my cell if texting is easier: \[number\]"

### If Timing Is Far Out:

> "I hear you on timing – makes total sense given you're \[closing the quarter / just implemented / etc.\]. What I'd still love to do is get a demo on your calendar even if it's exploratory. That way you see what modern ERP looks like, and when the timing is right, you're already familiar with us. How about we shoot for \[2-3 weeks out\]?"

* * *

## VII. FOLLOW-UP

### Immediate After Call:

1.  Send calendar invite for demo with Zoom link
    
2.  Send follow-up email with:
    
    *   Recap of pain points discussed
        
    *   Link to recorded Campfire overview (if available)
        
    *   Case study relevant to their industry
        
    *   Your contact info (email + cell)
        
    *   NDA if they want to share contracts/data
        

### Before Demo:

*   Request contract examples if revenue is complex
    
*   Ask for entity/currency list if multi-entity
    
*   Confirm who's attending from their side
    
*   Prepare custom talking points based on their stack
    

* * *

## VIII. KEY TALK TRACKS BY SCENARIO

### For Fintech / High Transaction Volume:

**Joseph's pitch:**

> "We have fintech customers processing billions of dollars and 500K+ merchants. Campfire can ingest billions of rows – no summarization like NetSuite forces you to do. That means our AI can parse every transaction, you can do granular revenue analysis, and auditors can sample at transaction level inside the ERP rather than going to your data warehouse"

* * *

### For IPO-Readiness:

**Joseph's pitch:**

> "Most of our customers are audited today, many are pre-IPO, and we have public customers. We work closely with PwC on audit readiness. From internal controls, approval workflows, audit trails – we've built this with Big Four audits in mind. Replit, for example, went from $10M to $300M ARR with only 3 people in finance because of automation"

* * *

### For Multi-Entity/Multi-Currency:

**Joseph's pitch:**

> "We have customers with hundreds of entities across every continent. Triple ledger means every transaction shows transactional, functional, and consolidating currency on a single screen – makes revaluation and translation way easier. We auto-book elimination entries, support verticalized sub structures, and can handle multiple elimination subs if needed"

* * *

### For Complex Revenue:

**Joseph's pitch:**

> "We handle subscription, usage, milestone, and T&M. You can modify contracts mid-term easily – not like NetSuite's 'set it and forget it.' For usage, we can build custom sub-ledgers in Snowflake that handle min commits, overages, discounting, token-based pricing – whatever you need. We do SSP automation, product bundles, early renewals with prorated credit memos – all native"

* * *

### For AI Skeptics:

**John's pitch:**

> "I get it – AI in accounting sounds risky. Here's how we think about it: AI is like a new junior accountant. It does the grunt work – drafts entries, finds missing accruals, writes flux commentary – but YOU review and approve before it posts. We publish the audit trail so you see exactly how AI got to its answer. And because we built our own foundational model with PwC input, it's designed for ITGC compliance from day one"

* * *

## IX. POWER QUESTIONS

Use these to go deeper:

1.  **"What's the one thing that if we could solve it, would be a game-changer for your team?"**
    
2.  **"If you could wave a magic wand and redesign your finance tech stack, what would it look like?"**
    
3.  **"What's the most manual, time-consuming process your team does every month?"**
    
4.  **"When you close the books, what keeps you up at night?"**
    
5.  **"If NetSuite disappeared tomorrow, what would you replace it with?"**
    
6.  **"What would make you want to rip out NetSuite before your contract expires?"**
    
7.  **"How much time does your team spend on integrations, customizations, and fixing NetSuite issues vs. actual accounting?"**
    

* * *

## X. SAMPLE DISCOVERY FLOW

**Opening (2 min):**

*   Rapport building
    
*   Agenda setting
    

**Their Background (5 min):**

*   Company overview
    
*   Your role and tenure
    

**Current State (10 min):**

*   Tech stack deep dive
    
*   Pain points discovery
    
*   Transaction volume and complexity
    

**Requirements (10 min):**

*   Revenue model
    
*   Multi-entity/currency needs
    
*   Integration requirements
    
*   Audit and compliance
    

**Campfire Overview (5 min):**

*   Hit their top 3 pain points with Campfire solutions
    
*   Differentiation (AI, scale, implementation speed)
    
*   Pricing ballpark
    

**Next Steps (3 min):**

*   Schedule demo
    
*   Identify stakeholders to include
    
*   Set expectations
    

* * *

## FINAL TIPS

✅ **Listen 70%, talk 30%** in discovery  
✅ **Take detailed notes** – use them in the demo  
✅ **Name-drop relevant customers** in their industry  
✅ **Be consultative, not sales-y** – you're solving problems  
✅ **Always mention the buyout fund** if they're in contract  
✅ **Get multiple stakeholders on the demo** (don't single-thread)  
✅ **Use their language** – if they say "committals," say "committals"  
✅ **Validate their pain** – "I hear that all the time from NetSuite customers"  
✅ **Create urgency** – "The longer you wait, the more manual work piles up"  
✅ **End with confidence** – "Based on what you've shared, I think we can help"

* * *

**Good luck! Remember: you're not selling software, you're offering freedom from NetSuite pain.**