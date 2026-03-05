# CorCompass Client Onboarding Protocol
## 30-Day Standard Onboarding Framework
**Version 1.0 | March 2026**

**Keywords:** onboarding, client-success, kickoff, setup, training, handoff, 30-day, workflow, integration, Studio

---

## Overview

The 30-day onboarding protocol transforms a signed contract into a fully operational AI agent deployment. The protocol follows the 10-20-70 rule: 10% of tasks are fully automated, 20% are AI-assisted, and 70% are human-led but AI-supported. This balance ensures quality and client trust while maintaining efficiency.

---

## Pre-Onboarding (Before Day 1)

**Triggered by:** Contract signed and initial payment received.

**CorCompass actions:**
- Create client record in CRM with all discovery call notes, technical readiness score, and agreed scope.
- Provision dedicated VPS (DigitalOcean or Hetzner; region closest to client's primary location).
- Create dedicated Google account, Gmail address, and GitHub account for the agent environment.
- Prepare identity file drafts (SOUL.md, USER.md, IDENTITY.md) based on discovery call notes.
- Schedule kickoff call within 48 hours of contract signing.

**Client actions:**
- Provide access credentials for any systems to be integrated (calendar, CRM, email, etc.).
- Identify the day-to-day point of contact and their Telegram handle.
- Complete the pre-onboarding questionnaire (sent via email).

---

## Week 1 -- Foundation (Days 1-7)

### Day 1: Kickoff Call (60 minutes)

**Agenda:**
1. Introductions and relationship establishment (10 min)
2. Goal alignment: confirm success metrics from discovery call (10 min)
3. Communication preferences: Telegram setup, response time expectations, escalation path (10 min)
4. Technical overview: what the agent can and cannot do (15 min)
5. Week 1 plan: what will be delivered by Day 7 (10 min)
6. Q&A (5 min)

**Deliverable:** Kickoff call notes documented in CRM; client has CorCompass contact information.

### Days 2-5: Technical Setup

Execute Phases 0-4 of the SOP-AGENT-BUILD.md:
- Phase 0: VPS hardening, SSH configuration, firewall setup
- Phase 1: Identity file customization (review drafts with client on Day 3)
- Phase 2: Memory architecture setup (MEMORY.md, daily memory flow, heartbeat)
- Phase 3: Model configuration (primary + fallbacks)
- Phase 4: Security hardening (secrets management, Telegram allowlist)

### Day 6: Identity File Review

30-minute call with client to review and finalize:
- SOUL.md: Does the tone and personality feel right?
- USER.md: Is the client profile accurate and complete?
- IDENTITY.md: Does the agent name and persona resonate?

**Deliverable:** All three identity files approved and locked.

### Day 7: Agent Live

- Agent is live and responsive in Telegram.
- Basic functionality confirmed (can answer questions, access memory, execute simple tasks).
- Client sends first message to the agent.

**Success metric:** Client sends first message and receives a useful, on-brand response.

---

## Week 2 -- Configuration (Days 8-14)

### Days 8-10: Workflow Mapping

Document the 3-5 highest-priority automation use cases identified in discovery. For each use case:
- Current state: how the task is done today (step by step)
- Desired state: how the agent should handle it
- Success criteria: what does "working correctly" look like?
- Edge cases: what are the exceptions and how should they be handled?

### Days 11-13: Skill Installation and Workflow Build

- Install relevant skills for each use case (from approved skills registry only).
- Configure cron jobs for any recurring automations.
- Build and test each workflow individually before integration.

### Day 14: First Workflow Live

- First custom workflow deployed and tested.
- Client demonstrates the workflow independently.
- 50% payment milestone triggered.

**Success metric:** Client can trigger and observe the first workflow without CorCompass assistance.

---

## Week 3 -- Integration (Days 15-21)

### Days 15-18: External Integrations

Connect all required external services:
- Calendar integration (Google Calendar or Outlook)
- Email integration (Gmail or Outlook)
- CRM integration (if applicable)
- Any vertical-specific tools (e.g., property management software for Steward clients)

### Days 19-20: Telegram Configuration

- Configure Telegram groups and topic-specific prompts.
- Set up any team members who will interact with the agent.
- Test group interactions and topic-specific workflows.

### Day 21: Studio Deployment

- Deploy OpenClaw Studio for client visibility.
- Configure Studio access for the client and any designated team members.
- Walk the client through Studio in a 30-minute screen share.

**Success metric:** Client can log into Studio and observe agent activity independently.

---

## Week 4 -- Handoff and Training (Days 22-30)

### Days 22-25: Documentation

Deliver two client-specific documents:
1. **WORKFLOW-GUIDE.md:** Step-by-step guide to every configured workflow, including how to trigger it, what to expect, and how to report issues.
2. **INCIDENT-RESPONSE.md:** What to do if something goes wrong -- who to contact, what information to provide, and what to expect in terms of response time.

### Day 28: Client Training Session (90 minutes)

**Agenda:**
1. How to interact with the agent effectively (prompting best practices) (20 min)
2. How to read and use OpenClaw Studio (15 min)
3. How to trigger and monitor each configured workflow (20 min)
4. How to escalate issues (10 min)
5. What to expect in the monthly report (10 min)
6. Q&A (15 min)

### Day 30: Completion and Check-In

- Final payment (25%) triggered.
- 30-day satisfaction survey sent.
- 60-day check-in call scheduled.
- Upsell opportunity assessment documented in CRM.

**Success metric:** Client NPS score >= 8/10 on Day 30 survey.

---

## Onboarding Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Time to first value | < 7 days | Date of first completed automation |
| Onboarding completion | 100% by Day 30 | Checklist completion rate |
| Client satisfaction (Day 30) | >= 8/10 NPS | Post-onboarding survey |
| Support tickets (Month 1) | < 3 | CRM ticket count |
| Client self-sufficiency | Confirmed by Day 30 | Client can operate agent without CorCompass assistance |

---

## Onboarding Checklist

**Pre-Onboarding:**
- [ ] Client record created in CRM
- [ ] VPS provisioned and hardened
- [ ] Dedicated operational accounts created
- [ ] Identity file drafts prepared
- [ ] Kickoff call scheduled

**Week 1:**
- [ ] Kickoff call completed and documented
- [ ] VPS security hardening complete
- [ ] Identity files reviewed and approved by client
- [ ] Agent live and responsive in Telegram

**Week 2:**
- [ ] All workflows documented (current state + desired state)
- [ ] Skills installed from approved registry
- [ ] Cron jobs configured
- [ ] First workflow live and tested by client

**Week 3:**
- [ ] All external integrations connected and tested
- [ ] Telegram groups and topics configured
- [ ] OpenClaw Studio deployed and client access confirmed

**Week 4:**
- [ ] WORKFLOW-GUIDE.md delivered
- [ ] INCIDENT-RESPONSE.md delivered
- [ ] Client training session completed
- [ ] Day 30 satisfaction survey sent
- [ ] 60-day check-in call scheduled
- [ ] Final payment received
- [ ] Upsell opportunity documented in CRM
