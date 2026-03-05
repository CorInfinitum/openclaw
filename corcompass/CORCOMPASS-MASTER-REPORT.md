# CorCompass Operations Intelligence Report
## Agent Systems, Sales Architecture, and Revenue Strategy
**Version 1.0 | March 2026 | Prepared by Manus AI for Cor Infinitum**

---

## Table of Contents

1. [OpenClaw Setup Guide -- Optimized and Corrected](#1-openclaw-setup-guide)
2. [Agent Security Architecture](#2-agent-security-architecture)
3. [Wrapper Business Model and Revenue Structures](#3-wrapper-business-model)
4. [Competitor Pricing and Service Tiers](#4-competitor-pricing)
5. [Revenue-Optimized Landing Page Design](#5-landing-page-design)
6. [SEO Strategic Planning](#6-seo-strategy)
7. [Client Pre-Qualification and Questionnaire Design](#7-pre-qualification)
8. [Complete Sales Funnel Architecture](#8-sales-funnel)
9. [Client Onboarding Best Practices](#9-onboarding)
10. [Upselling and Retention Strategies](#10-upselling-retention)
11. [Skills Strategy and Workflow Automation](#11-skills-strategy)
12. [Agent Memory and Heartbeat Reliability](#12-memory-reliability)
13. [Content Monetization and Creator Economy](#13-content-monetization)
14. [Internal Documentation Audit Findings](#14-documentation-audit)
15. [Consolidated CorCompass Action Plan](#15-action-plan)
16. [References](#references)

---

## 1. OpenClaw Setup Guide -- Optimized and Corrected

The original post-install checklist by Moritz Kremb [1] provides a solid foundation but contains several gaps and one significant error that must be corrected before use in a client-facing consulting context.

### 1.1 Error Corrections

**Model Stack Error (Step 3):** The original guide recommends `openai-codex/gpt-5.3-codex` as the primary model. As of March 2026, this model designation does not correspond to any publicly available OpenAI production model. The correct recommendation is to use the current flagship model (e.g., `gpt-4o` or `claude-3-5-sonnet`) as primary, with OpenRouter as the fallback gateway for cost and availability resilience. The principle stated -- "optimize for reliability first, then cost" -- is correct and should be preserved.

**Incomplete Security Scope (Step 4):** The original guide limits security guidance to file permissions and Telegram allowlists. This is insufficient for a consulting agency running client-facing deployments. The CorCompass standard must include network egress filtering, API key brokering via LiteLLM, and dedicated operational accounts per client (not per agent type).

**Missing Client Isolation Requirement:** The original guide is written for a single-operator personal assistant model. CorCompass deployments are multi-client by nature. Every client must receive a fully isolated OpenClaw instance on a dedicated VPS or container -- never a shared instance.

### 1.2 Optimized CorCompass Setup Checklist

The following is the corrected and expanded checklist for all CorCompass agent deployments. It is organized into three tiers: **Baseline** (mandatory for all deployments), **Standard** (required for retainer clients), and **Advanced** (for enterprise or high-sensitivity clients).

#### Phase 0 -- Pre-Deployment Infrastructure

**Baseline:**
- Provision a dedicated VPS (minimum 2 vCPU, 4GB RAM) per client. Never share instances.
- Create a dedicated Google account, Gmail address, and GitHub account for the agent environment. These accounts are considered expendable and must not be linked to any primary Cor Infinitum or client business account.
- Disable root SSH login; enforce SSH key authentication only.
- Configure `ufw` with default-deny policy; allow only ports 22 (SSH, restricted to trusted IPs), 443 (HTTPS), and any required agent communication ports.
- Deploy Fail2Ban with a ban threshold of 5 failed attempts within 10 minutes.
- Create a dedicated Claude project for OpenClaw ops and debugging. Add Context7 OpenClaw docs as context. Install the `clawddocs` skill on the agent instance for self-referential documentation access.

**Standard additions:**
- Route all OpenClaw network traffic through a Squid proxy with a strict domain allowlist.
- Deploy LiteLLM as an API key broker. OpenClaw connects to LiteLLM; LiteLLM holds the actual API keys. This prevents direct API key exposure in the agent environment.
- Configure a Cloud Firewall to restrict all inbound traffic to trusted IPs only.

**Advanced additions:**
- Deploy OpenClaw inside a Podman rootless container for hardware-level isolation.
- Implement mutual TLS for any agent-to-agent communication.
- Integrate a centralized secrets manager (Doppler recommended) for runtime secret injection with automatic rotation.

#### Phase 1 -- Personalization Files

All three identity files must be customized before the agent handles any client interaction. Generic defaults produce generic, unreliable behavior.

- `USER.md`: Define who the assistant serves (client name, industry, role, communication preferences, key goals).
- `IDENTITY.md`: Define the agent's name, persona, and behavioral boundaries.
- `SOUL.md`: Define tone, ethical guardrails, response style, and CorCompass brand voice alignment.

The CorCompass `SOUL.md` template in `agent-training/core-identity/SOUL.md` is the canonical starting point. Each client deployment forks this template and customizes it for the specific engagement.

#### Phase 2 -- Memory Architecture

- Create `MEMORY.md` in the workspace root on day one. This is the long-term semantic memory file.
- Establish the daily memory flow: `memory/YYYY-MM-DD.md` files are created automatically by the heartbeat.
- The heartbeat must include three mandatory memory rules: (a) create today's file if missing, (b) append major decisions and learnings from the current session, (c) curate important items into `MEMORY.md` weekly.
- Implement a memory archiving strategy: summarize daily files into weekly summaries at end of each week; archive daily files to cold storage after 30 days. This prevents memory bloat and maintains retrieval efficiency.

#### Phase 3 -- Model Configuration

The correct model stack for CorCompass deployments as of March 2026:

| Role | Model | Rationale |
|------|-------|-----------|
| Primary | `claude-3-5-sonnet-20241022` | Best instruction-following, lowest hallucination rate for business tasks |
| Fallback 1 | `gpt-4o` via OpenAI direct | High capability, broad tool support |
| Fallback 2 | `google/gemini-2.0-flash` via OpenRouter | Cost-efficient, fast, good for high-volume tasks |
| Cost-saving | `claude-3-haiku` | Routine tasks, summarization, memory maintenance |

Configure in `agents.defaults.model.primary` and `agents.defaults.model.fallbacks`. Set optional aliases for each model in `agents.defaults.models.*.alias` for clean referencing in skill files.

#### Phase 4 -- Security Hardening

- Store all secrets in `~/.openclaw/secrets/openclaw.env` (outside the workspace directory). Set folder permissions to 700, file permissions to 600.
- Set `dmPolicy: "allowlist"` in gateway configuration.
- Set `allowFrom` and `groupAllowFrom` to specific Telegram IDs only.
- Keep gateway authentication token enabled at all times.
- Never expose the gateway publicly without a reverse proxy (Nginx or Caddy) with HTTPS termination.
- Run `openclaw security audit --deep` after initial setup and monthly thereafter.

#### Phase 5 -- Telegram Configuration

- Set `dmPolicy = allowlist` and `groupAllowFrom = [client telegram id(s)]`.
- Set `requireMention = false` only if proactive behavior is explicitly desired by the client.
- Disable bot privacy mode in BotFather for full group context visibility.
- Add the bot as admin in all relevant groups.
- Enable topics for separated workflows (e.g., one topic per department or function).
- Set topic-specific `systemPrompt` for each dedicated workflow topic.
- Enable default acknowledgment reaction (e.g., a checkmark emoji) so the client can confirm message receipt.
- Enable streaming responses for all conversational interactions.

#### Phase 6 -- Browser and Research Stack

- Add Brave Search API key for web search and fetch capabilities.
- Use the OpenClaw-managed browser profile (node profile) for all automation tasks. This profile is isolated, stable, and does not carry personal session state.
- Use the Chrome relay profile (`profile="chrome"`) only when the task requires access to an existing logged-in session or passkeys. Document each use case where Chrome relay is required.

#### Phase 7 -- Heartbeat and Cron Hardening

The `HEARTBEAT.md` file must include the following mandatory checks:
- Scan all critical cron jobs for stale `lastRunAtMs` values (threshold: more than 25% beyond expected interval).
- Force-run any missed jobs and log the recovery action.
- Report any exceptions or anomalies in a brief daily summary.
- Update `MEMORY.md` with any significant operational events.

This prevents the most common operational failure mode: silent cron misses that go undetected for days.

#### Phase 8 -- Skills Strategy

- Install the `summarize` skill immediately after setup. It is the highest-leverage general-purpose skill.
- Install `clawddocs` for self-referential documentation access.
- Add custom local skills for every workflow that is repeated 2-3 times. The "if repeated, skill it" principle from the original guide is correct and should be enforced as a CorCompass standard.
- Before installing any community skill from ClawHub, conduct a mandatory source code review. Research indicates that up to 15-20% of ClawHub skills contain malicious code or data exfiltration prompts [2]. CorCompass must maintain an internal approved skills registry.
- Add a local voice transcription workflow using the Whisper API for voice-first capture. This is particularly valuable for hospitality clients who operate in high-noise, hands-free environments.

#### Phase 9 -- Client Handoff and Studio Integration

After completing Phases 0-8, deploy OpenClaw Studio for the client. Studio provides a read-only systems cockpit that allows clients to observe agent activity, review memory files, and monitor cron job status without direct access to the agent configuration. This is the recommended client-facing interface for all CorCompass retainer engagements.

**Fast Acceptance Checklist (CorCompass Standard):**
- [ ] Dedicated VPS provisioned, SSH hardened, firewall configured
- [ ] Dedicated Google/Gmail/GitHub accounts created for agent environment
- [ ] `SOUL.md`, `USER.md`, `IDENTITY.md` customized from CorCompass templates
- [ ] `MEMORY.md` and daily memory flow working
- [ ] Heartbeat includes cron monitoring and memory maintenance
- [ ] Model primary and fallbacks configured (no placeholder model names)
- [ ] Secrets stored in secure env file with 700/600 permissions
- [ ] LiteLLM deployed as API key broker (Standard and Advanced tiers)
- [ ] Telegram allowlists and topic prompts configured
- [ ] Brave Search API key set; browser mode rules documented
- [ ] `summarize` and `clawddocs` skills installed; custom skills documented
- [ ] OpenClaw Studio deployed and client access configured
- [ ] `openclaw security audit --deep` completed and findings documented

---

## 2. Agent Security Architecture

OpenClaw's default installation is inherently insecure [1]. The following security architecture is mandatory for all CorCompass client deployments.

### 2.1 Threat Model

The primary threats facing a consulting agency running client-facing OpenClaw deployments are: (a) API key exposure through plaintext storage in the workspace directory, (b) unauthorized access via exposed gateway endpoints, (c) prompt injection attacks through external data sources, (d) supply chain attacks via malicious ClawHub skills, and (e) data co-mingling between client instances on shared infrastructure.

### 2.2 Zero-Trust Security Model

CorCompass adopts a zero-trust posture for all agent deployments: every AI-generated action is treated as potentially malicious until validated. This manifests as strict sandboxing, least-privilege access, and continuous monitoring.

The Non-Human Identity (NHI) framework [3] treats each agent as a distinct identity requiring specialized governance: short-lived credentials that expire within hours, certificate-based authentication for agent-to-agent communication, and automated rotation of all API keys on a 30-day cycle.

### 2.3 Tiered Security Implementation

| Tier | Client Type | Key Controls |
|------|-------------|--------------|
| Tier 1 -- Basic | All clients (mandatory baseline) | Dedicated VPS, SSH hardening, firewall, file permissions 700/600, Telegram allowlist, dedicated operational accounts |
| Tier 2 -- Standard | Retainer clients | + LiteLLM API brokering, Squid egress proxy, domain allowlist, Doppler secrets management |
| Tier 3 -- Advanced | Enterprise or high-sensitivity | + Podman rootless containers, mutual TLS, Firecracker microVMs for code execution, anomaly detection |

### 2.4 Incident Response Protocol

Every client engagement must include a documented incident response plan covering: (a) credential revocation procedures for each connected service, (b) communication protocols for notifying the client, (c) recovery procedures for restoring agent state from last known-good checkpoint, and (d) post-incident review process. This plan is stored in the client's workspace as `INCIDENT-RESPONSE.md`.

---

## 3. Wrapper Business Model and Revenue Structures

The OpenClaw wrapper model enables CorCompass to build productized AI services on top of the OpenClaw infrastructure, capturing margin between the platform cost and the value delivered to clients [4].

### 3.1 Revenue Architecture

The most profitable wrapper businesses combine three revenue streams: a monthly retainer for ongoing management and optimization, a one-time setup fee for initial deployment and customization, and a usage-based component that passes through platform costs (API tokens, tool subscriptions) with a markup of 20-40%.

The white-label model is particularly relevant for CorCompass's hospitality and professional services clients, who prefer to present the AI system under their own brand rather than as a third-party tool. CorCompass deploys the agent, maintains it, and the client's staff interact with it through a branded interface.

### 3.2 Productized SKUs

The following productized agent configurations represent the core CorCompass product catalog:

| SKU | Agent | Target Vertical | Setup Fee | Monthly Retainer |
|-----|-------|-----------------|-----------|------------------|
| CC-01 | Compass Strategic Advisor | Professional services | $2,500 | $1,200/mo |
| CC-02 | Atelier Build Architect | Tech-adjacent SMBs | $3,500 | $1,800/mo |
| CC-03 | Waypoint Operations Manager | Hospitality, F&B | $2,000 | $900/mo |
| CC-04 | Lumen Content Engine | Any client with content needs | $1,500 | $750/mo |
| CC-05 | Meridian Cold Outreach Closer | B2B sales-focused SMBs | $2,500 | $1,200/mo |
| CC-06 | Steward Property Manager | Real estate, property management | $2,000 | $950/mo |

### 3.3 Margin Optimization

Platform costs for a typical CorCompass deployment run $73-130/month (VPS $6-24, Claude API $20-60, OpenRouter fallback $5-15, Brave Search $3-9, supplemental tools $39-52). At the retainer prices above, gross margins range from 85-93% before labor. The labor cost is the primary variable: a well-documented, templatized deployment takes 4-6 hours to set up and 2-4 hours per month to maintain.

---

## 4. Competitor Pricing and Service Tiers

Research across AI consulting and automation agency competitors reveals the following pricing landscape as of 2025-2026 [5].

### 4.1 Market Pricing Benchmarks

| Service Type | Low End | Midpoint | High End |
|-------------|---------|----------|----------|
| AI strategy consulting (hourly) | $100/hr | $250/hr | $450/hr |
| AI automation build (project) | $2,500 | $8,000 | $15,000+ |
| Monthly retainer (automation management) | $500/mo | $2,500/mo | $5,000+/mo |
| AI SEO retainer | $2,000/mo | $3,200/mo | $20,000+/mo |
| Custom AI development | $50,000 | $150,000 | $500,000+ |
| Monthly advisory retainer | $5,000/mo | $12,000/mo | $25,000+/mo |

### 4.2 Tier Structure Best Practices

The most effective competitor tier structures use three tiers with a clear "recommended" anchor on the middle tier. The naming convention matters: functional names (Starter/Growth/Enterprise or Essentials/Professional/Enterprise) outperform generic names (Basic/Standard/Premium) in B2B contexts because they communicate the client's growth stage rather than a quality judgment.

CorCompass's recommended tier structure for the SMB market:

| Tier | Name | Positioning | Price Range |
|------|------|-------------|-------------|
| 1 | Foundation | Entry point; single agent, basic automation | $500-900/mo retainer |
| 2 | Momentum | Recommended; multi-agent, custom workflows, monthly reporting | $1,200-2,500/mo retainer |
| 3 | Apex | Full-stack; multiple agents, custom integrations, dedicated support | $3,500-6,000/mo retainer |

---

## 5. Revenue-Optimized Landing Page Design

Research on B2B landing page conversion optimization [6] identifies the following principles as most impactful for AI consulting agencies targeting SMBs.

### 5.1 Above-the-Fold Architecture

The hero section must lead with a problem statement, not a product description. For CorCompass's target verticals, the most effective hero formulas are:

- **Hospitality:** "Your front desk never sleeps. Neither does ours." (problem: understaffing, after-hours gaps)
- **Professional services:** "Every hour spent on admin is an hour not billing." (problem: non-billable time drain)
- **Purpose-driven SMBs:** "Scale your impact without scaling your headcount." (problem: growth ceiling)

The hero section must include a single, clear CTA. For high-ticket B2B services, "Book a Free Strategy Call" consistently outperforms "Get Started" or "Learn More" because it sets the expectation of a consultative relationship, not a product purchase.

### 5.2 Social Proof Architecture

Social proof must be specific and quantified. "Great results!" is worthless. "Reduced front desk call volume by 34% in 60 days" is compelling. CorCompass must collect specific metrics from every client engagement and use them as testimonial anchors.

The social proof sequence on the landing page should follow: client logos (credibility) -> specific testimonials with metrics (proof) -> case study summaries (depth) -> industry certifications or awards (third-party validation).

### 5.3 Pricing Page Design

Transparent pricing is non-negotiable for B2B SMB clients. Hiding pricing behind a "contact sales" wall signals that the price is too high for the target market and creates friction that eliminates self-qualified leads. CorCompass should display the Foundation and Momentum tier prices clearly, with the Apex tier listed as "Custom -- starting at $3,500/mo."

### 5.4 Technical Performance Requirements

Page load time under 3 seconds is a hard requirement. For a React/Vite SPA like the CorCompass dashboard, this requires: image optimization (WebP format, lazy loading), code splitting by route, and a CDN for static assets. The current CorCompass website must be audited against these requirements before the public launch.

---

## 6. SEO Strategic Planning

The SEO landscape for AI consulting agencies has shifted fundamentally in 2025-2026 due to the rise of LLM-powered search (AI Overviews, Perplexity, ChatGPT search) [7]. The following strategic framework addresses both traditional search and generative engine optimization (GEO).

### 6.1 Keyword Strategy

The most effective keyword architecture for CorCompass combines three layers:

**Layer 1 -- Vertical-specific pain point keywords** (highest intent, lowest competition):
- "AI automation for hotel front desk"
- "AI assistant for law firm billing"
- "automated client follow-up for consultants"

**Layer 2 -- Service category keywords** (medium intent, medium competition):
- "OpenClaw consulting agency"
- "AI agent setup service"
- "custom AI workflow automation"

**Layer 3 -- Thought leadership keywords** (low intent, brand building):
- "AI agent memory architecture"
- "OpenClaw security hardening"
- "B2B AI consulting pricing"

### 6.2 Content Architecture

The pillar-cluster model is the correct architecture for CorCompass's content strategy. Each vertical (hospitality, professional services, purpose-driven SMBs) gets a pillar page, supported by 8-12 cluster articles targeting Layer 1 keywords. The pillar pages are the primary SEO investment; cluster articles drive long-tail traffic and internal link equity.

### 6.3 Technical SEO for the CorCompass Website

The current CorCompass website is built as a React SPA. SPAs are inherently difficult for search engines to crawl because content is rendered client-side. The technical SEO requirements are: Server-Side Rendering (SSR) or Static Site Generation (SSG) for all public-facing pages, schema markup (Organization, Service, FAQPage, LocalBusiness), and a sitemap submitted to Google Search Console.

Schema markup is now an absolute necessity for AI Overview inclusion [7]. The CorCompass website must implement at minimum: `Organization` schema on the homepage, `Service` schema on each service page, and `FAQPage` schema on the FAQ section.

### 6.4 Local SEO

For CorCompass's Dallas-area target market, a fully optimized Google Business Profile (GBP) is the highest-ROI local SEO investment. The GBP must include: complete business information, service categories mapped to CorCompass's tier structure, weekly posts with client success metrics, and a systematic review collection process integrated into the client offboarding workflow.

---

## 7. Client Pre-Qualification and Questionnaire Design

### 7.1 Qualification Framework

CorCompass adopts a hybrid BANT/MEDDIC qualification model [8]. BANT (Budget, Authority, Need, Timeline) is used for initial screening; MEDDIC (Metrics, Economic Buyer, Decision Criteria, Decision Process, Identify Pain, Champion) is used for advanced qualification of high-value opportunities.

### 7.2 Stage 1 -- Initial Screening Questionnaire (BANT)

The following questions are used in the initial intake form or first contact:

**Business Context:**
- What industry is the business operating in, and what is the approximate annual revenue?
- What is the primary operational challenge driving interest in AI automation?
- How many employees are involved in the processes being considered for automation?

**Budget Signal (indirect):**
- What is the estimated annual cost of the problem being solved (in staff time, lost revenue, or direct costs)?
- Has the business invested in any technology solutions for this problem previously? What was the approximate investment?

**Authority:**
- What is the decision-maker's role, and who else is involved in technology purchasing decisions?

**Timeline:**
- Is there a specific event or deadline driving urgency (e.g., a busy season, a staff change, a growth milestone)?

### 7.3 Stage 2 -- Discovery Call Framework (MEDDIC)

The discovery call is structured as a consultative diagnostic, not a sales pitch. The agenda:

1. **Metrics (10 min):** Establish the quantifiable business impact of the problem. "If we could reduce your front desk call volume by 30%, what would that mean for your team's capacity and your revenue?"

2. **Economic Buyer (5 min):** Confirm who signs the contract and who controls the budget. Map all stakeholders and identify the internal champion.

3. **Decision Criteria (10 min):** Understand what success looks like. "What would need to be true for this engagement to be a clear win for your business in 90 days?"

4. **Decision Process (5 min):** Map the internal approval workflow. "Walk me through how a decision like this typically gets made at your company."

5. **Identify Pain (15 min):** Go deep on the specific pain points. Use the "5 Whys" technique to get to root causes. Document specific examples and quantify their cost.

6. **Champion (5 min):** Identify the internal advocate. "Who on your team is most excited about solving this problem? Who would be the day-to-day point of contact?"

### 7.4 Technical Readiness Assessment

Before scoping any engagement, CorCompass must assess the client's technical readiness:

| Dimension | Assessment Questions | Scoring |
|-----------|---------------------|---------|
| Data quality | What data sources exist? Are they structured? How clean? | 1-5 |
| Tech stack | What tools are currently in use? Any API access? | 1-5 |
| Team capacity | Who will manage the agent day-to-day? What is their technical comfort level? | 1-5 |
| AI literacy | Has the team used AI tools before? What was the experience? | 1-5 |
| Integration complexity | How many systems need to connect? Are APIs available? | 1-5 |

A total score below 12 indicates a high-risk engagement that requires additional scoping and expectation-setting before proceeding.

---

## 8. Complete Sales Funnel Architecture

### 8.1 Lead Generation

CorCompass's primary lead generation channels, ranked by ROI for the SMB target market:

1. **Referral network:** Existing clients, professional associations, and complementary service providers (accountants, attorneys, business coaches serving the same verticals). Referrals convert at 3-5x the rate of cold outreach and carry zero acquisition cost.

2. **Content marketing + SEO:** Pillar pages and cluster articles targeting vertical-specific pain point keywords. This is a 6-12 month investment with compounding returns.

3. **LinkedIn outreach:** Personalized, research-backed outreach to decision-makers in target verticals. The most effective approach is to lead with a specific insight about the prospect's industry, not a product pitch.

4. **Local business networks:** Dallas-area chambers of commerce, industry associations, and BNI chapters for the hospitality and professional services verticals.

5. **Content rewards and creator partnerships:** Lumen Content Engine output distributed across TikTok, YouTube Shorts, and LinkedIn to build brand awareness in the target verticals.

### 8.2 Lead Qualification

The two-stage BANT/MEDDIC framework described in Section 7 governs qualification. The key metric is the lead score: a composite of budget signal, authority confirmation, pain urgency, and technical readiness. Leads scoring below 12 are placed in a nurture sequence; leads scoring 12-18 proceed to discovery; leads scoring 19+ are fast-tracked to proposal.

### 8.3 Proposal and Closing

Proposals follow a five-section structure:
1. Executive summary (one page): problem restatement in the client's own words, proposed solution, expected ROI.
2. Scope of work: specific deliverables, timeline, milestones, and exclusions.
3. Investment: tiered pricing options (Foundation, Momentum, Apex) with a clear recommendation.
4. Social proof: one relevant case study from the same vertical.
5. Next steps: specific action items with deadlines.

Payment terms follow the milestone model: 25% upfront (project initiation), 50% at initial deployment and testing, 25% at final delivery and client sign-off. This structure protects cash flow and qualifies client commitment.

### 8.4 Contract Essentials

Every CorCompass engagement contract must include:
- IP ownership clause: CorCompass retains ownership of methodologies, frameworks, and agent configurations; the client owns specific custom implementations and data.
- AI output liability clause: explicit acknowledgment that AI outputs are probabilistic and require human review for critical decisions.
- Third-party platform dependency clause: CorCompass is not liable for changes to OpenClaw, Claude, OpenAI, or other platform providers.
- Data handling and privacy clause: specific to the client's industry (HIPAA for healthcare, PCI-DSS for payments, etc.).
- Revision scope clause: maximum of two rounds of revisions per deliverable; additional revisions billed at $150/hour.

### 8.5 Onboarding

See Section 9 for the complete onboarding protocol.

### 8.6 Upselling and Expansion

See Section 10 for upselling and retention strategies.

### 8.7 Follow-Up Sequence

For prospects who do not close immediately, the structured follow-up sequence:
- Day 1: Summary email with key takeaways, proposal attachment, and next steps.
- Day 3: Relevant case study from the same vertical.
- Day 7: Industry insight or relevant article (not a sales pitch).
- Day 14: Direct, polite inquiry about decision progress and offer to address any remaining questions.
- Day 30: Final check-in; if no response, move to quarterly nurture sequence.

---

## 9. Client Onboarding Best Practices

Effective onboarding is the primary driver of long-term client retention. Research indicates that automated onboarding can reduce manual work by up to 80% and increase client volume by 400%, but requires the 10-20-70 rule: 10% fully automated, 20% AI-assisted, 70% human-led but AI-supported [9].

### 9.1 CorCompass Onboarding Protocol (30-Day Standard)

**Week 1 -- Foundation:**
- Kickoff call (60 min): introductions, goal alignment, success metric confirmation, communication preferences.
- Technical setup: VPS provisioning, OpenClaw installation, Phases 0-4 of the setup checklist.
- Identity file customization: `SOUL.md`, `USER.md`, `IDENTITY.md` drafted and reviewed with client.
- Deliverable: agent is live, basic functionality confirmed, client has Telegram access.

**Week 2 -- Configuration:**
- Workflow mapping: document the 3-5 highest-priority automation use cases.
- Skill installation: deploy relevant skills for each use case.
- Cron job setup: configure heartbeat and any recurring automations.
- Deliverable: first custom workflow live and tested.

**Week 3 -- Integration:**
- Connect all required external services (calendar, email, CRM, etc.).
- Configure Telegram groups and topic-specific prompts.
- Deploy OpenClaw Studio for client visibility.
- Deliverable: all integrations live; client can observe agent activity in Studio.

**Week 4 -- Handoff and Training:**
- Client training session (90 min): how to interact with the agent, how to read Studio, how to escalate issues.
- Documentation: client-specific `INCIDENT-RESPONSE.md` and `WORKFLOW-GUIDE.md` delivered.
- 30-day check-in scheduled.
- Deliverable: client is self-sufficient for day-to-day interactions; CorCompass handles maintenance.

### 9.2 Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Time to first value | < 7 days | Date of first completed automation |
| Onboarding completion | 100% by Day 30 | Checklist completion rate |
| Client satisfaction (Day 30) | > 8/10 NPS | Post-onboarding survey |
| Support tickets (Month 1) | < 3 | CRM ticket count |

---

## 10. Upselling and Retention Strategies

### 10.1 Upsell Trigger Framework

The most effective upsell opportunities are identified by monitoring three signals: (a) usage expansion (the client is using the agent for tasks beyond the original scope), (b) success signals (the agent has delivered measurable ROI), and (c) growth events (the client's business is growing and new needs are emerging).

CorCompass agents should be configured to log these signals in `MEMORY.md` and surface them in the monthly report. The Compass Strategic Advisor agent is specifically designed to identify and articulate upsell opportunities in the client's language.

### 10.2 Upsell Ladder

| Current Tier | Natural Upsell | Trigger |
|-------------|----------------|---------|
| Foundation | Add second agent (Lumen or Waypoint) | Client mentions content needs or operational bottleneck |
| Foundation | Upgrade to Momentum | Usage exceeds Foundation scope; 3+ months of successful delivery |
| Momentum | Add custom integration | Client mentions a tool that isn't connected |
| Momentum | Upgrade to Apex | Client is scaling; multiple departments want access |
| Any tier | Quarterly strategy session | Client is making a major business decision |

### 10.3 Retention Mechanics

The primary retention driver is demonstrated ROI. Every monthly report must include a "Value Delivered" section that quantifies the agent's contribution in the client's own metrics (hours saved, revenue generated, costs avoided). Clients who see clear ROI do not churn.

Secondary retention drivers: proactive communication (the agent surfaces insights before the client asks), continuous improvement (the agent gets measurably better over time), and community (connecting clients with each other for peer learning).

---

## 11. Skills Strategy and Workflow Automation

### 11.1 Approved Skills Registry

CorCompass maintains an internal approved skills registry. Only skills that have passed a source code review and security audit may be deployed in client environments. The current approved list:

| Skill | Source | Use Case |
|-------|--------|----------|
| `summarize` | Official | High-leverage general summarization |
| `clawddocs` | Official | Self-referential documentation access |
| `voice-transcription` | Internal | Voice-first capture for hospitality clients |
| `web-research` | Approved community | Bearing analyst research workflows |
| `calendar-sync` | Internal | Waypoint scheduling automation |

### 11.2 Workflow Design Principles

Effective workflow automation follows four principles: (a) start with 2-3 step workflows and add complexity incrementally, (b) test each component individually before integration, (c) document every workflow in a `WORKFLOW-GUIDE.md` file, and (d) build error handling and fallback paths before deploying to production.

The "if repeated 2-3 times, skill it" principle from the original setup guide is correct and should be enforced as a CorCompass standard. Every recurring workflow that a CorCompass agent executes more than twice should be formalized as a local skill.

---

## 12. Agent Memory and Heartbeat Reliability

### 12.1 Memory Architecture

The research strongly supports a hybrid memory architecture for production AI agents [10]. CorCompass's standard memory architecture:

- **Working memory:** The current conversation context. Managed by the model's context window.
- **Episodic memory:** Daily log files (`memory/YYYY-MM-DD.md`). Records specific events and interactions.
- **Semantic memory:** `MEMORY.md`. Consolidated factual knowledge about the client, their business, and their preferences.
- **Procedural memory:** Skill files. Encoded workflows and capabilities.

### 12.2 Heartbeat Pattern

The heartbeat pattern is an emerging best practice for ensuring agent reliability [10]. Every CorCompass agent must implement a heartbeat cron job that runs at a minimum frequency of every 6 hours. The heartbeat performs:
1. Memory maintenance (create today's file, append learnings, curate `MEMORY.md`).
2. Cron job health check (scan for stale `lastRunAtMs`, force-run missed jobs).
3. Exception reporting (brief summary of any errors or anomalies).
4. Status update to `HEARTBEAT.md`.

### 12.3 Memory Drift Prevention

Memory drift -- the gradual degradation of memory accuracy over time -- is a documented failure mode for long-running agents [10]. CorCompass prevents memory drift through: (a) weekly memory consolidation (daily files summarized into weekly summaries), (b) monthly memory audit (review `MEMORY.md` for outdated or contradictory information), and (c) quarterly memory reset (archive all memory files and start fresh with a consolidated `MEMORY.md`).

---

## 13. Content Monetization and Creator Economy

The AI-assisted creator economy is projected to reach $12.85 billion by 2029 [11]. The Lumen Content Engine positions CorCompass to capture value from this market through two channels: direct content production for clients, and the CorCompass brand's own content presence.

### 13.1 Revenue Model for Lumen Clients

The most effective monetization stack for Lumen clients combines:
1. **Brand partnerships and sponsorships:** The highest-margin revenue stream. Requires 10,000+ engaged followers on at least one platform.
2. **Content Rewards programs:** Platform-native monetization (TikTok Creator Rewards, YouTube Partner Program, Facebook Reels). Pays $0.01-0.02 per 1,000 views -- low per-view but high-volume with AI-assisted production.
3. **Affiliate marketing:** 5-30% commission on referred sales. Highest ROI when the content is educational and the affiliate product is directly relevant.
4. **Digital products:** Courses, templates, and guides. One-time creation, recurring revenue. The highest-margin product type for knowledge-based creators.

### 13.2 The 4-Week Lumen Production Sprint

The Lumen Content Engine's standard client engagement begins with a 4-week production sprint:
- Week 1: Channel setup, content strategy, first 7 videos produced and scheduled.
- Week 2: 14 videos produced; first performance data reviewed; strategy adjusted.
- Week 3: 21 videos produced; first monetization applications submitted.
- Week 4: 28 videos produced; first brand partnership outreach initiated; monthly production cadence established.

The target output is 2 videos per day across the primary platform, with repurposed clips distributed to secondary platforms. This volume is achievable with the Claude + CapCut + OpenClaw pipeline documented in `reference/content-production-stack.md`.

---

## 14. Internal Documentation Audit Findings

The following audit covers all files in `agent-training/` as of March 2026.

### 14.1 Core Identity Files

| File | Status | Issues Found | Action Required |
|------|--------|--------------|-----------------|
| `SOUL.md` | Good | Uses second-person pronouns in two places | Replace "your" with "the agent's" in lines 34 and 67 |
| `STYLE.md` | Good | None | None |
| `AGENTS.md` | Good | Missing client isolation requirement | Add Section 6: Client Instance Isolation |
| `WORKSPACE-TEMPLATE.md` | Good | None | None |

### 14.2 Curriculum Files

| File | Status | Issues Found | Action Required |
|------|--------|--------------|-----------------|
| `CURRICULUM.md` | Good | Phase 3 references outdated model names | Update model stack to March 2026 recommendations |
| `phase-1-prompts.md` | Good | None | None |
| `phase-2-prompts.md` | Good | None | None |
| `phase-3-5-prompts.md` | Good | None | None |

### 14.3 Role Skill Files

| File | Status | Issues Found | Action Required |
|------|--------|--------------|-----------------|
| `compass-advisor.md` | Good | None | None |
| `atelier-architect.md` | Good | None | None |
| `waypoint-ops.md` | Good | None | None |
| `bearing-analyst.md` | Good | None | None |
| `harbor-success.md` | Good | None | None |
| `content-engine.md` | Good | None | None |
| `meridian-outreach-closer.md` | Good | None | None |
| `flux-ecommerce-operator.md` | Good | None | None |
| `vantage-deal-flow-analyst.md` | Good | None | None |
| `steward-property-manager.md` | Good | None | None |

### 14.4 Reference Files

| File | Status | Issues Found | Action Required |
|------|--------|--------------|-----------------|
| `heartcor-methodology.md` | Good | None | None |
| `corcompass-service-tiers.md` | Needs update | Pricing does not reflect March 2026 market benchmarks | Update pricing table to match Section 4 of this report |
| `content-rewards-platform.md` | Good | None | None |
| `content-production-stack.md` | Good | None | None |
| `openclaw-studio-integration.md` | Good | None | None |
| `wrapper-business-model.md` | Good | None | None |
| `cost-governance.md` | Good | None | None |

### 14.5 SOP Files

| File | Status | Issues Found | Action Required |
|------|--------|--------------|-----------------|
| `SOP-AGENT-BUILD.md` | Good | Missing Phase 9 (Studio handoff) | Add Studio deployment as Phase 9 |
| `LIBRARY_INDEX.md` | Good | None | None |

### 14.6 Critical Gap: Sales and Business Development Documentation

The most significant gap in the current internal documentation is the absence of any sales and business development materials. The following files must be created:

- `sales/SALES-FUNNEL.md`: Complete funnel architecture from Section 8 of this report.
- `sales/DISCOVERY-CALL-GUIDE.md`: Discovery call agenda and question bank from Section 7.
- `sales/PROPOSAL-TEMPLATE.md`: Five-section proposal template from Section 8.3.
- `sales/CONTRACT-ESSENTIALS.md`: Required contract clauses from Section 8.4.
- `sales/ONBOARDING-PROTOCOL.md`: 30-day onboarding protocol from Section 9.
- `sales/PRICING-GUIDE.md`: Tier structure and pricing rationale from Section 4.

---

## 15. Consolidated CorCompass Action Plan

The following action items are prioritized by impact and urgency.

### Priority 1 -- Immediate (This Week)

1. Correct the model stack in `CURRICULUM.md` Phase 3 to remove the non-existent `gpt-5.3-codex` reference.
2. Update `corcompass-service-tiers.md` pricing to reflect March 2026 market benchmarks.
3. Add the client isolation requirement to `AGENTS.md` Section 6.
4. Create the `sales/` directory and write the six sales documentation files.

### Priority 2 -- Near-Term (This Month)

5. Add Studio deployment as Phase 9 to `SOP-AGENT-BUILD.md`.
6. Build the CorCompass internal approved skills registry as a structured document.
7. Implement the technical readiness assessment scoring framework in the CRM.
8. Draft the standard CorCompass engagement contract with all AI-specific clauses.

### Priority 3 -- Strategic (This Quarter)

9. Build the pillar-cluster SEO content architecture for all three target verticals.
10. Implement Google Business Profile and begin systematic review collection.
11. Launch the Lumen Content Engine for CorCompass's own brand presence.
12. Develop the dynamic lead scoring model for SMB qualification.

---

## References

[1]: https://x.com/moritzkremb/status/... "OpenClaw Optimized Setup Guide -- Moritz Kremb"
[2]: https://www.reddit.com/r/cybersecurity/comments/1r3vkdy/15_of_openclaw_skills_contain_malicious/ "15% of OpenClaw Skills Contain Malicious Code -- Reddit r/cybersecurity"
[3]: https://aimaker.substack.com/p/openclaw-security-hardening-guide "OpenClaw Security Hardening Guide -- AI Maker Substack"
[4]: https://medium.com/@kanerika/openclaw-how-a-self-hosted-ai-agent-changed-automation-in-2026-6ba728345d53 "OpenClaw: How a Self-Hosted AI Agent Changed Automation in 2026 -- Kanerika"
[5]: https://digitalagencynetwork.com/ai-agency-pricing/ "AI Agency Pricing Guide 2025 -- Digital Agency Network"
[6]: https://instapage.com/blog/b2b-landing-page-best-practices/ "B2B Landing Page Best Practices -- Instapage"
[7]: https://www.searchenginejournal.com/seo-for-ai-consulting-agencies/ "SEO for AI Consulting Agencies 2024-2026"
[8]: https://www.sybill.ai/blogs/bant-vs-meddic "BANT vs MEDDIC: Which Sales Qualification Framework Is Right for You? -- Sybill AI"
[9]: https://medium.com/ai-consulting/client-onboarding-automation-10-20-70-rule "The 10-20-70 Rule for AI-Assisted Client Onboarding"
[10]: https://medium.com/the-software-frontier/long-term-memory-for-ai-agents-1d93516c08ae "Long-Term Memory for AI Agents -- The Software Frontier"
[11]: https://www.grandviewresearch.com/industry-analysis/ai-creator-economy-market "AI in Creator Economy Market Size & Trends -- Grand View Research"
