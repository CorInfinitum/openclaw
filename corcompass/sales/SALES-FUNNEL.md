# CorCompass Sales Funnel Architecture
## Complete Lead-to-Retention Pipeline
**Version 1.0 | March 2026**

---

## Overview

The CorCompass sales funnel is a seven-stage pipeline designed for B2B AI consulting engagements with hospitality, professional services, and purpose-driven SMBs. Each stage has defined entry criteria, exit criteria, and responsible agents.

**Keywords:** sales-funnel, lead-generation, qualification, closing, onboarding, upselling, retention, B2B, SMB, pipeline

---

## Stage 1 -- Lead Generation

### Primary Channels (Ranked by ROI)

1. **Referral network** -- Existing clients, professional associations, complementary service providers (accountants, attorneys, business coaches). Referrals convert at 3-5x the rate of cold outreach with zero acquisition cost. Every client engagement must include a referral request at the 30-day and 90-day marks.

2. **Content marketing + SEO** -- Pillar pages and cluster articles targeting vertical-specific pain point keywords. 6-12 month investment with compounding returns. See `reference/SEO-STRATEGY.md` for the full keyword architecture.

3. **LinkedIn outreach** -- Personalized, research-backed outreach to decision-makers in target verticals. Lead with a specific insight about the prospect's industry, not a product pitch. Maximum 20 new outreach messages per week to maintain quality.

4. **Local business networks** -- Dallas-area chambers of commerce, industry associations, and BNI chapters. Hospitality and professional services verticals respond well to in-person relationship building.

5. **Lumen Content Engine** -- CorCompass brand content distributed across TikTok, YouTube Shorts, and LinkedIn. Builds awareness in target verticals and generates inbound interest.

### Lead Capture

All inbound leads are captured in the CRM within 24 hours of first contact. Required fields at capture:
- Name, company, role, contact information
- Source channel
- Initial stated problem or interest
- Date of first contact

---

## Stage 2 -- Initial Qualification (BANT)

### Entry Criteria
- Lead captured in CRM
- Initial contact made within 24 hours

### Qualification Questions

**Business Context:**
- What industry is the business operating in, and what is the approximate annual revenue?
- What is the primary operational challenge driving interest in AI automation?
- How many employees are involved in the processes being considered for automation?

**Budget Signal (indirect):**
- What is the estimated annual cost of the problem being solved (in staff time, lost revenue, or direct costs)?
- Has the business invested in any technology solutions for this problem previously?

**Authority:**
- What is the decision-maker's role, and who else is involved in technology purchasing decisions?

**Timeline:**
- Is there a specific event or deadline driving urgency?

### Lead Scoring

| Dimension | Score 1 | Score 2 | Score 3 |
|-----------|---------|---------|---------|
| Budget signal | Vague or none | Indirect evidence ($10-50K problem) | Direct statement ($50K+ problem) |
| Authority | Influencer only | Influencer + economic buyer access | Economic buyer direct |
| Need urgency | Exploring | Active problem | Crisis or deadline |
| Timeline | 6+ months | 3-6 months | < 3 months |

**Scoring thresholds:**
- 4-6: Nurture sequence (monthly touchpoint)
- 7-9: Proceed to discovery call
- 10-12: Fast-track to discovery call within 48 hours

### Exit Criteria
- Lead scored and categorized
- Nurture sequence activated OR discovery call scheduled

---

## Stage 3 -- Discovery Call (MEDDIC)

### Entry Criteria
- Lead score >= 7
- Discovery call scheduled

### Call Agenda (60 minutes)

**Opening (5 min):** Confirm agenda, set expectations, establish rapport.

**Metrics (10 min):** Establish the quantifiable business impact of the problem. "If the front desk call volume were reduced by 30%, what would that mean for the team's capacity and revenue?"

**Economic Buyer (5 min):** Confirm who signs the contract and who controls the budget. Map all stakeholders and identify the internal champion.

**Decision Criteria (10 min):** Understand what success looks like. "What would need to be true for this engagement to be a clear win for the business in 90 days?"

**Decision Process (5 min):** Map the internal approval workflow. "Walk through how a decision like this typically gets made at the company."

**Identify Pain (15 min):** Go deep on specific pain points using the 5 Whys technique. Document specific examples and quantify their cost.

**Champion (5 min):** Identify the internal advocate and day-to-day point of contact.

**Next Steps (5 min):** Confirm the proposal timeline and any additional information needed.

### Technical Readiness Assessment

| Dimension | Score 1 | Score 3 | Score 5 |
|-----------|---------|---------|---------|
| Data quality | No structured data | Some structured data | Clean, accessible data |
| Tech stack | No API access | Some integrations possible | Full API access |
| Team capacity | No dedicated owner | Part-time owner | Dedicated owner |
| AI literacy | No prior experience | Some tool usage | Active AI users |
| Integration complexity | 5+ systems, no APIs | 3-4 systems, some APIs | 1-2 systems, full APIs |

**Readiness thresholds:**
- < 12: High-risk; additional scoping required before proposal
- 12-18: Standard engagement; proceed to proposal
- 19-25: Ideal client; fast-track proposal

### Exit Criteria
- Discovery call completed and documented in CRM
- Technical readiness score calculated
- Proposal timeline confirmed

---

## Stage 4 -- Proposal and Closing

### Proposal Structure

1. **Executive Summary (1 page):** Problem restatement in the client's own words, proposed solution, expected ROI.
2. **Scope of Work:** Specific deliverables, timeline, milestones, and explicit exclusions.
3. **Investment:** Tiered pricing options (Foundation, Momentum, Apex) with a clear recommendation.
4. **Social Proof:** One relevant case study from the same vertical.
5. **Next Steps:** Specific action items with deadlines.

### Pricing Tiers

| Tier | Setup Fee | Monthly Retainer | Included Agents |
|------|-----------|------------------|-----------------|
| Foundation | $1,500 | $500-900/mo | 1 agent, basic automation |
| Momentum | $2,500 | $1,200-2,500/mo | 2 agents, custom workflows, monthly reporting |
| Apex | $4,000+ | $3,500-6,000/mo | Multi-agent, custom integrations, dedicated support |

### Payment Terms

- 25% upfront (project initiation)
- 50% at initial deployment and testing (Day 14)
- 25% at final delivery and client sign-off (Day 30)

### Follow-Up Sequence

- Day 1: Summary email with key takeaways, proposal attachment, next steps
- Day 3: Relevant case study from the same vertical
- Day 7: Industry insight or relevant article (not a sales pitch)
- Day 14: Direct, polite inquiry about decision progress
- Day 30: Final check-in; if no response, move to quarterly nurture sequence

### Exit Criteria
- Contract signed
- Initial payment received
- Kickoff call scheduled

---

## Stage 5 -- Onboarding

See `sales/ONBOARDING-PROTOCOL.md` for the complete 30-day onboarding protocol.

**Key milestones:**
- Day 1: Kickoff call completed
- Day 7: Agent live, basic functionality confirmed
- Day 14: First custom workflow live and tested
- Day 21: All integrations live, Studio deployed
- Day 30: Client training completed, 30-day check-in scheduled

---

## Stage 6 -- Upselling and Expansion

### Upsell Trigger Signals

The Compass Strategic Advisor agent monitors and logs three upsell signals in `MEMORY.md`:
1. **Usage expansion:** Client using the agent for tasks beyond original scope
2. **Success signals:** Agent has delivered measurable, quantifiable ROI
3. **Growth events:** Client's business is scaling; new needs are emerging

### Upsell Ladder

| Current Tier | Natural Upsell | Trigger |
|-------------|----------------|---------|
| Foundation | Add Lumen or Waypoint agent | Client mentions content needs or operational bottleneck |
| Foundation | Upgrade to Momentum | Usage exceeds scope; 3+ months of successful delivery |
| Momentum | Add custom integration | Client mentions an unconnected tool |
| Momentum | Upgrade to Apex | Client is scaling; multiple departments want access |
| Any tier | Quarterly strategy session | Client is making a major business decision |

---

## Stage 7 -- Retention and Referral

### Monthly Reporting

Every client receives a monthly report including:
- **Value Delivered:** Quantified ROI in the client's own metrics (hours saved, revenue generated, costs avoided)
- **Activity Summary:** What the agent did this month
- **Optimization Highlights:** Improvements made to workflows or configurations
- **Next Month Preview:** Planned optimizations and upcoming automations

### Referral Request Protocol

- At 30-day mark: "The engagement is going well. Is there anyone in the network who might benefit from a similar setup?"
- At 90-day mark: Formal referral request with a specific incentive (one month credit for a successful referral).
- At annual renewal: Referral request included in renewal conversation.

### Churn Prevention

The primary churn indicator is a drop in the client's engagement with the agent (fewer messages, fewer tasks). The Harbor Client Success agent monitors engagement metrics and flags declining engagement for proactive outreach within 48 hours.

---

## CRM Stage Definitions

| Stage | Label | Definition |
|-------|-------|------------|
| 1 | Lead | Captured in CRM, not yet qualified |
| 2 | Qualified | BANT score >= 7, discovery call scheduled |
| 3 | Discovery | Discovery call completed, proposal in progress |
| 4 | Proposal | Proposal sent, awaiting decision |
| 5 | Closed Won | Contract signed, payment received |
| 6 | Onboarding | Active onboarding (Days 1-30) |
| 7 | Active Client | Ongoing retainer engagement |
| 8 | At Risk | Declining engagement or satisfaction signal |
| 9 | Closed Lost | Did not convert; reason documented |
