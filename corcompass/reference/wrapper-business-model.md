# CorCompass Wrapper Business Model

**Document ID:** REF-WRAPPER-BIZ
**Version:** 1.4.0 — March 3, 2026
**Classification:** Internal — Operator Use Only
**Series:** CorCompass Protected Series, Cor Infinitum LLC

---

## The Core Thesis

Every major platform shift produces the same pattern: a new infrastructure layer emerges, most people use it, a small group sells pre-configured access to it. WordPress created agencies. Shopify created store builders. The App Store created indie developers. OpenClaw is producing the next iteration: operators who sell pre-configured AI agents for specific, high-value jobs.

The business opportunity is not in running OpenClaw. It is in selling it. OpenClaw costs nothing to host and pennies per hour to run. The value is entirely in the configuration — API architecture, custom skills, prompt engineering, workflow design, and niche domain knowledge. Ninety-five percent of the buyers who want this outcome will never configure it themselves. That gap is the entire business model.

CorCompass is positioned to own this market in its target verticals before competitors arrive. The window is open now and will not remain open indefinitely.

---

## The CorCompass Wrapper Positioning

CorCompass does not sell software. CorCompass sells a pre-trained digital worker that shows up ready to do one specific job — configured, tested, and handed off with a client cockpit (OpenClaw Studio) so the client can observe and control it without touching a terminal.

The buyer is not an engineer. The buyer is a coach, creator, agency owner, hospitality operator, or founder who wants the outcome without the complexity. The CorCompass value proposition is: **hide the complexity, sell the feeling**.

The feeling being sold: waking up on Monday morning and everything is already done. Content scheduled. Calls booked. Deals analyzed. Rent collected. Inventory managed.

---

## Pricing Architecture

The cardinal rule: **price against the human the agent replaces, not against SaaS software.**

| Role Replaced | Market Rate | CorCompass Wrapper Price (10–20%) |
|---|---|---|
| SDR / Outreach Specialist | $3,000–5,000/month | $300–1,000/month |
| Ecommerce VA + Media Buyer | $2,000–4,000/month | $200–800/month |
| Investment Analyst | $6,000–10,000/month | $600–2,000/month |
| Property Manager (8–10% gross rent) | $800–2,000/month (12-unit) | $80–400/month |
| Content Agency | $5,000–10,000/month | $500–2,000/month |

The buyer saves 80–90% compared to the human equivalent. CorCompass captures 10–20% of the human cost as recurring monthly revenue. At five active Harbor Build clients across different niches, this produces $2,500–8,000/month in recurring wrapper revenue on top of the initial build fee.

---

## The CorCompass Wrapper Tiers

Wrapper products map to the existing CorCompass service tier structure:

| Tier | Product | What Is Delivered |
|---|---|---|
| **Flow Scan** | Wrapper Audit | Assessment of the client's workflow, identification of the 80% that is automatable, and a written spec for the recommended niche agent |
| **Coherence Sprint** | Wrapper Build | Full agent configuration, skill installation, workspace setup, USER.md population, and 30-day operator support |
| **Harbor Build** | Wrapper + Cockpit | Everything in Coherence Sprint plus OpenClaw Studio deployment, Tailscale setup, client onboarding, and 90-day operator support |

---

## The Five Priority Niche Agents

The following five niche agents represent the highest-value, fastest-to-sell wrapper opportunities in the CorCompass target market. Each has a dedicated SKILL.md in `role-skills/`.

### 1. Meridian — Cold Outreach Closer

**Target buyer:** B2B founders, agency owners, consultants, coaches with a defined ICP.
**Human replaced:** SDR / outreach specialist ($3,000–5,000/month).
**Core capability:** Builds lead lists from LinkedIn, Apollo, and Google Maps; writes hyper-personalized outreach referencing recent activity; runs multi-channel sequences across email, LinkedIn DMs, and Twitter DMs; tracks engagement; books discovery calls and delivers prospect briefing docs.
**Outcome delivered:** "3 calls booked today. Here is who they are and what they care about."

### 2. Flux — Ecommerce Operator

**Target buyer:** Shopify and Amazon sellers with $20k–$500k/month GMV.
**Human replaced:** VA + customer support rep + media buyer ($2,000–4,000/month combined).
**Core capability:** Monitors store metrics around the clock; tracks inventory and auto-reorders; watches competitor pricing and adjusts dynamically; handles support tickets, returns, and refunds; generates ad creatives from product photos; delivers daily P&L breakdowns.
**Outcome delivered:** "Revenue today: $4,200. Ad spend: $380. 3 returns processed. Inventory alert: blue hoodie XL drops below 50 units Friday."

### 3. Vantage — Deal Flow Analyst

**Target buyer:** Real estate investors, angel investors, fund managers evaluating opportunities at volume.
**Human replaced:** Investment analyst ($6,000–10,000/month).
**Core capability:** Scrapes listings, pitch decks, and SEC filings; runs every opportunity through the client's custom scoring criteria; pulls comps, market data, and due diligence into one-page summaries; delivers ranked daily briefings.
**Outcome delivered:** "47 new deals reviewed. 3 match your criteria. Here is the breakdown with my recommendation."

### 4. Steward — Property Manager

**Target buyer:** Residential landlords with 4–50 units who self-manage or pay a property manager 8–10% of gross rent.
**Human replaced:** Property management company ($800–2,000/month for a 12-unit portfolio).
**Core capability:** Receives maintenance requests via text, diagnoses issues, sources contractors, and routes quotes for approval; sends rent reminders, tracks payments, flags late tenants, generates late notices; handles lease renewal workflows; monitors local rental market for pricing opportunities.
**Outcome delivered:** "All 12 units collected. 1 maintenance request resolved. Unit 4B lease expires in 60 days. Market rate is $200 above current rent."

### 5. Lumen — Content Machine

**Target buyer:** Creators, coaches, and brands spending $5,000–10,000/month on content agencies or 20+ hours/week producing content themselves.
**Human replaced:** Content agency or full-time content manager.
**Core capability:** Monitors X, Reddit, RSS feeds, and YouTube transcripts for trending topics; writes a full week of content matched to the client's tone and style; generates thumbnails and graphics; schedules across platforms; delivers a Monday morning briefing.
**Outcome delivered:** "14 posts, 2 newsletters, 3 video scripts queued up. Review and publish."

*Note: Lumen is also the CorCompass Content Engine agent for internal use. The same SKILL.md serves both purposes.*

---

## Go-to-Market Strategy

### Niche Selection Principle

A general-purpose OpenClaw setup is worth nothing. The winning wrapper does one specific job better than any human assistant in a specific vertical. The selection criteria: study the buyer's daily routine until the operator knows it better than the buyer does, identify the 80% that is repetitive and automatable, wire the agent to handle all of it, and package it so setup takes 10 minutes instead of 10 hours.

The winners will not be the best coders. They will be the operators who understand a niche deeply enough to automate it.

### Sales Framing

Nobody is buying OpenClaw. Nobody cares about API architecture. The sale is the feeling of waking up Monday morning and everything is already done. Every sales conversation, landing page, and demo should lead with the outcome, not the technology.

### Timing

The OpenClaw community is small, the skills marketplace is early, and new capabilities are shipping weekly. Within six months, every niche will have multiple competitors. The operators building wrappers now will own those niches before anyone else arrives. The window is open. It will not remain open.

---

## Operational Checklist for Each Wrapper Deployment

- [ ] Conduct Flow Scan to identify the client's automatable 80%
- [ ] Select the appropriate niche agent SKILL.md from the library
- [ ] Customize the SKILL.md for the client's specific ICP, tools, and workflows
- [ ] Complete the five-phase build protocol (see SOP-AGENT-BUILD.md)
- [ ] Deploy OpenClaw Studio via Phase 6 client handoff (see REF-STUDIO-INTEGRATION)
- [ ] Populate the client's USER.md with their profile, preferences, and active context
- [ ] Run a live demo session in Studio with the client present
- [ ] Deliver the handoff package: Studio URL, access token, Quick Start guide
- [ ] Schedule the 14-day check-in per the Cor Infinitum New Tool Guidance Protocol

---

## Keywords

`wrapper-business-model` `openclaw-wrappers` `niche-agents` `pricing-strategy` `harbor-build` `meridian` `flux` `vantage` `steward` `lumen` `outreach-closer` `ecommerce-operator` `deal-flow-analyst` `property-manager` `content-machine` `recurring-revenue` `client-handoff` `go-to-market` `flow-scan` `coherence-sprint`
