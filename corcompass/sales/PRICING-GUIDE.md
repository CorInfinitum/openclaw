# CorCompass Pricing Guide
## Tier Structure, Rationale, and Negotiation Boundaries
**Version 1.0 | March 2026**

**Keywords:** pricing, tiers, service-menu, competitor-analysis, value-based-pricing, retainer, setup-fee, SMB, B2B

---

## Market Context

The AI consulting and automation agency market as of March 2026 shows the following pricing benchmarks:

| Service Type | Low End | Midpoint | High End |
|-------------|---------|----------|----------|
| AI strategy consulting (hourly) | $100/hr | $250/hr | $450/hr |
| AI automation build (project) | $2,500 | $8,000 | $15,000+ |
| Monthly retainer (automation management) | $500/mo | $2,500/mo | $5,000+/mo |
| AI SEO retainer | $2,000/mo | $3,200/mo | $20,000+/mo |
| Monthly advisory retainer | $5,000/mo | $12,000/mo | $25,000+/mo |

CorCompass targets the SMB segment, positioning in the midpoint range for retainers and below midpoint for setup fees to reduce friction at the entry point.

---

## CorCompass Tier Structure

### Tier 1 -- Foundation

**Positioning:** Entry point for SMBs exploring AI automation. Single agent, basic automation, monthly check-in.

**Included:**
- 1 OpenClaw agent deployment (client's choice of role)
- Dedicated VPS provisioning and security hardening
- Identity file customization (SOUL.md, USER.md, IDENTITY.md)
- 1 custom workflow automation
- Telegram integration and configuration
- Monthly 30-minute check-in call
- Email support (48-hour response SLA)

**Pricing:**
- Setup fee: $1,500 (one-time)
- Monthly retainer: $500-900/mo (based on agent complexity)

**Ideal client:** Business owner exploring AI for the first time; single high-priority use case; budget-conscious.

---

### Tier 2 -- Momentum (Recommended)

**Positioning:** The primary tier for established SMB clients. Multi-agent, custom workflows, proactive reporting.

**Included:**
- 2 OpenClaw agent deployments (client's choice of roles)
- Dedicated VPS with LiteLLM API brokering
- Full identity file customization for both agents
- Up to 3 custom workflow automations
- All integrations (calendar, email, CRM, Telegram)
- OpenClaw Studio deployment for client visibility
- Monthly detailed report (Value Delivered, Activity Summary, Next Month Preview)
- Monthly 60-minute strategy call
- Priority email support (24-hour response SLA)
- Quarterly optimization review

**Pricing:**
- Setup fee: $2,500 (one-time)
- Monthly retainer: $1,200-2,500/mo (based on agent count and integration complexity)

**Ideal client:** Growing SMB with multiple automation needs; has seen initial AI results and wants to expand; values proactive reporting and strategic guidance.

---

### Tier 3 -- Apex

**Positioning:** Full-stack AI operations for scaling SMBs and small enterprises. Multi-agent ecosystem, custom integrations, dedicated support.

**Included:**
- Up to 5 OpenClaw agent deployments
- Dedicated VPS cluster with full security stack (LiteLLM, Squid proxy, Doppler)
- Custom integrations (any tool with an API)
- Unlimited workflow automations
- OpenClaw Studio with custom dashboard
- Weekly detailed report
- Weekly 60-minute strategy call
- Dedicated Slack channel for real-time support (4-hour response SLA)
- Quarterly business review with ROI analysis
- Priority access to new CorCompass agent builds

**Pricing:**
- Setup fee: $4,000+ (custom, based on scope)
- Monthly retainer: $3,500-6,000+/mo (custom, based on agent count and complexity)

**Ideal client:** Scaling business with complex automation needs across multiple departments; values dedicated support and strategic partnership; has demonstrated ROI from previous AI investments.

---

## Productized Agent SKUs

For clients who want a specific agent rather than a tier package:

| SKU | Agent | Target Vertical | Setup Fee | Monthly Retainer |
|-----|-------|-----------------|-----------|------------------|
| CC-01 | Compass Strategic Advisor | Professional services | $2,500 | $1,200/mo |
| CC-02 | Atelier Build Architect | Tech-adjacent SMBs | $3,500 | $1,800/mo |
| CC-03 | Waypoint Operations Manager | Hospitality, F&B | $2,000 | $900/mo |
| CC-04 | Lumen Content Engine | Any client with content needs | $1,500 | $750/mo |
| CC-05 | Meridian Cold Outreach Closer | B2B sales-focused SMBs | $2,500 | $1,200/mo |
| CC-06 | Steward Property Manager | Real estate, property management | $2,000 | $950/mo |
| CC-07 | Bearing Research Analyst | Any client needing market intelligence | $2,000 | $900/mo |

---

## Pricing Rationale

### Why Not Hourly Billing

Hourly billing caps income, punishes efficiency, and fails to capture the true value delivered. CorCompass agents automate parts of the workflow and solve problems faster over time -- hourly billing would mean earning less as the system improves. Value-based and project-based pricing captures the transformation delivered, not the time spent.

### Platform Cost Structure

The underlying platform cost for a typical CorCompass deployment:

| Component | Monthly Cost Range |
|-----------|-------------------|
| VPS (DigitalOcean, Hetzner) | $6-24 |
| Claude API (primary model) | $20-60 |
| OpenRouter (fallback models) | $5-15 |
| Brave Search API | $3-9 |
| Supplemental tools (calendar, email, etc.) | $39-52 |
| **Total platform cost** | **$73-130/mo** |

At the Foundation retainer of $500-900/mo, gross margins are 85-93% before labor. Labor cost (2-4 hours/month for maintenance) is the primary variable.

---

## Negotiation Boundaries

### What Can Be Negotiated

- Setup fee: Can be reduced by up to 20% for multi-agent commitments or 6-month prepayment.
- Monthly retainer: Can be reduced by up to 10% for annual prepayment (12 months upfront).
- Payment terms: Milestone structure can be adjusted (e.g., 50% upfront, 50% at completion for smaller projects).

### What Cannot Be Negotiated

- Minimum retainer: Foundation tier floor is $500/mo. Below this, the engagement is not profitable.
- Security requirements: All security hardening steps are mandatory. No client receives a discounted "insecure" deployment.
- Contract terms: IP ownership, AI output liability, and revision scope clauses are non-negotiable.

### Discount Policy

Discounts are only offered in exchange for something of value:
- Annual prepayment: 10% discount
- Referral that converts: One month credit
- Case study participation: $200 credit
- Testimonial with specific metrics: $100 credit

Discounts are never offered simply because a prospect asks. If a prospect cannot afford the minimum retainer, the correct response is to recommend the Foundation tier and explain the value clearly, not to reduce the price.

---

## Competitor Positioning

| Competitor Type | Typical Positioning | CorCompass Differentiation |
|----------------|--------------------|-----------------------------|
| Freelance AI consultant | $50-150/hr, no ongoing support | CorCompass provides ongoing management and optimization, not just setup |
| Large AI consulting firm | $250-450/hr, enterprise focus | CorCompass specializes in SMBs; faster deployment, lower overhead, more personal |
| Generic automation agency | $500-2,000/mo, generic tools | CorCompass uses OpenClaw (self-hosted, private, customizable) vs. SaaS tools |
| DIY OpenClaw setup | $0 setup, ongoing time cost | CorCompass handles all technical complexity; client gets results without the learning curve |

The primary CorCompass differentiator is the combination of OpenClaw's self-hosted privacy model with CorCompass's done-for-you deployment and ongoing management. Clients get enterprise-grade AI capabilities without enterprise-grade complexity or cost.
