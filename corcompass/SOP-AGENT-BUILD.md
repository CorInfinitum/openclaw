# CorCompass Standard Operating Procedure
## Agent Build, Deployment, and Maintenance

**Document ID:** SOP-AGENT-BUILD  
**Version:** 1.2.0 — March 1, 2026  
**Classification:** Internal — Operator Use Only  
**Series:** CorCompass Protected Series, Cor Infinitum LLC

---

## Purpose and Scope

This SOP defines the authoritative process for building, deploying, and maintaining OpenClaw agents under the CorCompass banner. It supersedes any informal build notes, prior curriculum drafts, or ad hoc configurations. Every new agent built for internal CorCompass use or for client delivery under a Harbor Build engagement must follow this protocol.

The SOP is grounded in the six-component OpenClaw architecture documented by the OpenClaw administrator community and calibrated against the five critical configuration mistakes that degrade agent performance and increase token spend. Adherence to this protocol is estimated to reduce token costs by 60–70% compared to unoptimized builds while producing agents that operate at measurably higher quality.

---

## Part I — Architecture Reference

### The Six OpenClaw Components

Every CorCompass agent deployment consists of six interdependent components. Understanding the role of each is prerequisite to building correctly.

| Component | Role | CorCompass Implication |
|---|---|---|
| **Gateway** | The circulatory system. Routes messages, assembles context, executes tool calls, maintains persistent channel connections. | Gateway must be running continuously as a daemon. All channel bindings (Telegram, Slack, Discord, WhatsApp) are configured here. The WebSocket API (port 18789) is the integration surface for external tools. |
| **Agent** | The brain. Receives assembled context from Gateway, reasons, calls tools, builds responses. | Each CorCompass agent (Compass, Atelier, Waypoint, Bearing, Harbor, Lumen) is a separate agent folder with its own workspace and sessions. |
| **Workspace** | Long-term persistent memory. A folder of `.md` files the agent reads before every response. | The most commonly under-configured component. See Part II for the complete required file set. |
| **Sessions** | Single-conversation memory. The `.jsonl` history of one dialogue. | Sessions must be isolated per user via `dmScope: "per-channel-peer"`. Failure to set this is the most common multi-user bug. |
| **Tools** | The agent's hands. `exec`, `browser`, `file`, `message`, `memory`. | `exec` mode must be set to `sandbox` or `gateway` with whitelist. Never `full` on a production deployment. |
| **Nodes** | Physical devices connected to Gateway. Expand what the agent can do (screenshots, geolocation, local file access). | Relevant for client deployments where the agent needs access to local systems. Not required for cloud-only CorCompass agents. |

### The Two Memory Tiers

OpenClaw uses two distinct memory mechanisms. Using only one is the single largest source of wasted token spend and degraded agent performance.

**Tier 1 — Bootstrap Memory (always loaded)**

Gateway injects the following files into every single LLM request, before the user's message is processed:

- `AGENTS.md` — operating instructions and playbook
- `SOUL.md` — personality, tone, priorities
- `USER.md` — the profile of the person the agent is serving
- `IDENTITY.md` — agent name and vibe
- Today's daily log (`YYYY-MM-DD.md`)

Every token in these files costs money on every request. Bootstrap files must be kept lean. The rule: **bootstrap contains only what the agent needs to know in every single message, without exception.** Everything else belongs in Tier 2.

**Tier 2 — Semantic Search Memory (pulled on demand)**

When the `memory` tool is enabled, the agent can search `MEMORY.md` and other notes via a vector index — retrieving relevant facts by meaning, not by keyword. This memory does not consume context tokens unless actively retrieved.

The rule: **everything that is important but not needed in every message goes into `MEMORY.md` or daily logs.** Client-specific facts, past decisions, project context, and domain knowledge all belong here.

**The Token Efficiency Formula:**

```
Bootstrap = Identity + Tone + Active Rules + Today's Log
Semantic   = Client Facts + Past Decisions + Domain Knowledge + Project History
```

An agent running only bootstrap is operating at half capacity. An agent with neither configured is burning 3× the tokens it should.

---

## Part II — Required Workspace File Set

Every CorCompass agent workspace must contain the following files. Files marked **[Bootstrap]** are loaded into every request. Files marked **[Semantic]** are searched on demand.

| File | Memory Tier | Purpose | CorCompass Notes |
|---|---|---|---|
| `SOUL.md` | Bootstrap | Collective brand identity — worldview, voice, vocabulary, opinions, boundaries | Shared across all agents. Load from `core-identity/SOUL.md`. |
| `AGENTS.md` | Bootstrap | Operating manual — how to think, which tools to use, safety rules, playbook | Shared across all agents. Load from `core-identity/AGENTS.md`. |
| `IDENTITY.md` | Bootstrap | Agent name and vibe — "My name is Compass, I am the CorCompass Strategic Advisor." | Write one per agent. Short file. Sets the tone for everything. |
| `USER.md` | Bootstrap | Profile of the person being served — how to address them, their role, their preferences | Write one per client engagement. Update as the relationship deepens. |
| `STYLE.md` | Bootstrap | Voice and formatting guide — sentence structure, tone calibration, anti-patterns | Shared across all agents. Load from `core-identity/STYLE.md`. |
| `MEMORY.md` | Semantic | Long-term facts — client decisions, project context, domain knowledge, preferences | Agent writes here autonomously or when instructed. The primary semantic index. |
| `YYYY-MM-DD.md` | Bootstrap | Daily log — what happened today, tasks in progress, context for tomorrow | Gateway injects today's log. Agent writes to it during the session. |
| `HEARTBEAT.md` | Cron | Periodic health checklist — items the agent checks on a schedule | Required for any agent running automated monitoring or scheduled tasks. |
| `TOOLS.md` | Bootstrap | Local tool hints — where scripts live, which commands are available, shortcuts | Required for any agent using `exec` tool. Prevents guessing. |

### IDENTITY.md Template

```markdown
# Identity

My name is [Agent Name]. I am the CorCompass [Role Title].

[One sentence describing the primary function.]

[One sentence describing the tone and style this agent brings to interactions.]

I operate under the CorCompass banner — a protected series of Cor Infinitum LLC, Dallas, Texas. Every interaction reflects the standard: Guided by Heart, Powered by Logic.
```

### USER.md Template

```markdown
# User Profile — [Client Name or "Operator"]

**Name:** [How to address this person]  
**Role:** [Their title or function]  
**Organization:** [Company or context]  
**Communication preference:** [Direct / narrative / bullet-heavy / etc.]  
**Primary focus:** [What they are working on right now]  
**Known preferences:** [Specific things they like or dislike in responses]  
**Avoid:** [Topics, formats, or approaches that do not serve this person]  

## Active Context

[Brief summary of the current engagement, project, or ongoing work. Updated at the start of each new phase.]

## Relationship Notes

[How long this relationship has been active, key milestones, trust level, any sensitivities.]
```

### MEMORY.md Template

```markdown
# Long-Term Memory

*This file is searched semantically. Write facts here that must not be lost between sessions.*
*The agent writes here autonomously when instructed to remember something.*

## Decisions

[Date] — [Decision made, context, reasoning]

## Preferences

[Fact about preferences that should persist across sessions]

## Project Facts

[Key facts about active projects, clients, or engagements]

## Domain Knowledge

[Specialized knowledge relevant to this agent's domain that has been refined through experience]
```

### HEARTBEAT.md Template

```markdown
# Heartbeat Checklist

*Gateway runs this checklist on the configured schedule. The agent checks each item and reports anomalies.*

## Daily Checks
- [ ] [Check item 1 — e.g., "Confirm pipeline ran and produced expected output"]
- [ ] [Check item 2 — e.g., "Verify no error logs in the last 24 hours"]
- [ ] [Check item 3 — e.g., "Confirm scheduled posts went out on time"]

## Weekly Checks
- [ ] [Weekly item 1 — e.g., "Review Content Rewards active campaigns for new briefs"]
- [ ] [Weekly item 2 — e.g., "Check platform monetization status for all active channels"]

## Escalation Threshold
If any check fails, send alert to [channel] with: item name, failure description, and recommended action.
```

---

## Part III — Configuration Checklist (The Five Critical Mistakes)

Before any CorCompass agent goes into production, the operator must confirm all five of the following are correctly configured. These are the most common failure modes in the OpenClaw administrator community.

### Mistake 1 — `dmScope` Not Set for Multi-User Deployments

**The problem:** OpenClaw's default `dmScope: "main"` collapses all direct messages in a channel into a single session. If two different people message the agent, it sees both conversations as one and can respond to one person with context from the other's conversation. This is not a bug — it is the default behavior that must be changed manually.

**The fix:** Set `dmScope: "per-channel-peer"` in `config.json` for any agent that will be accessed by more than one person. Each user receives an isolated session.

**CorCompass application:** All client-facing agents (Compass, Harbor) must have `dmScope: "per-channel-peer"`. Internal single-operator agents (Atelier, Bearing) may use `dmScope: "per-agent"`.

### Mistake 2 — `exec` Tool Set to `full` Mode

**The problem:** `full` mode gives the LLM unrestricted shell access to the server. The agent can delete files, install packages, read any data, and execute any command. Acceptable for local experimentation; catastrophic on a production server.

**The fix:** Use `sandbox` mode (Docker container, fully isolated) for any agent that does not need server-level access. Use `gateway` mode with a defined `exec-approvals.json` whitelist for agents that need controlled server access. Never use `full` on a deployment that handles client data or financial operations.

**CorCompass application:**
- Lumen (content pipeline): `gateway` mode with whitelist limited to CapCut CLI, scheduling tools, and file operations
- Atelier (build architect): `sandbox` mode for skill testing; `gateway` for production deployments
- All other agents: `sandbox` mode by default

### Mistake 3 — Empty or Absent Workspace

**The problem:** An agent without a configured workspace wakes up with no memory of who it is, who it is serving, or what has been decided. Every session starts from zero. Every re-explanation of context costs tokens. The agent cannot maintain continuity across conversations.

**The fix:** Configure the complete workspace file set (Part II) before the agent handles any real task. The minimum viable workspace is: `SOUL.md` + `IDENTITY.md` + `AGENTS.md` + `USER.md`. The full workspace adds `MEMORY.md`, daily logs, `HEARTBEAT.md`, and `TOOLS.md`.

**CorCompass application:** No CorCompass agent is considered "built" until all required workspace files are present and populated. A SKILL.md without a workspace is a prompt, not an agent.

### Mistake 4 — No Memory Flush Before Session Compaction

**The problem:** Long dialogues grow into thousands of tokens. OpenClaw compresses old messages into a summary when the context window fills. If the agent has not written important facts to `MEMORY.md` before compression, those facts are gone. The agent forgets decisions made three sessions ago.

**The fix:** Enable memory flush before compaction. The agent automatically dumps important facts into `MEMORY.md` before the session is compressed. Additionally, instruct agents explicitly in `AGENTS.md` to write to `MEMORY.md` whenever a significant decision, preference, or fact is established.

**CorCompass application:** Add the following instruction to every agent's `AGENTS.md` or `IDENTITY.md`:

> "When a client states a preference, makes a decision, or shares a fact that should persist across sessions, write it to `MEMORY.md` immediately. Use the format: `[Date] — [Fact or decision, with context].`"

### Mistake 5 — Port 18789 Exposed to the Open Internet

**The problem:** Gateway's WebSocket API listens on localhost by default. If port 18789 is forwarded for remote access without access controls, anyone who finds that port has full access to all agents, sessions, workspace files, and the ability to send commands. This is a complete data breach.

**The fix:** Use Tailscale (VPN bridge into private network) or SSH tunnel (`ssh -L 18789:127.0.0.1:18789 user@server`) for remote access. Never expose port 18789 directly to the public internet.

**CorCompass application:** All CorCompass production deployments must use Tailscale or SSH tunnel. Document the access method in the deployment record for each agent.

---

## Part IV — The Build Protocol

### Phase 0 — Pre-Build Checklist (15 minutes)

Before writing a single file, answer these three questions precisely:

1. What domain is this agent an expert in, and what specific tasks will it perform repeatedly?
2. What does a finished deliverable from this agent look like?
3. Who will use this agent, and how many people will access it simultaneously?

The answers to these questions determine: the workspace file set required, the `dmScope` setting, the `exec` mode, and the bootstrap vs. semantic memory split.

### Phase 1 — Workspace Construction (2–4 hours)

Build the workspace files in this order. Each file is a prerequisite for the next.

**Step 1.1 — Write `IDENTITY.md`**  
One paragraph. Agent name, role title, primary function, tone. This is the agent's self-concept. Keep it under 150 words. Every token here costs money on every request.

**Step 1.2 — Populate `USER.md`**  
Write the profile of the primary person this agent will serve. For internal agents, this is the CorCompass operator. For client-facing agents, this is the client. Update this file as the relationship deepens — it is a living document.

**Step 1.3 — Write `MEMORY.md` (seed entries)**  
Do not leave `MEMORY.md` empty at launch. Seed it with the three to five most important facts the agent should know from day one: the client's primary goal, any known constraints, key decisions already made, and any preferences established during intake.

**Step 1.4 — Write `TOOLS.md`** (if `exec` tool is enabled)  
Document every script, command, and shortcut the agent has access to. Include the full path, the purpose, and the expected output. An agent that knows its tools does not guess — it executes.

**Step 1.5 — Write `HEARTBEAT.md`** (if scheduled tasks are required)  
Define the periodic check items. Set the cron schedule in Gateway config. Test the heartbeat before going live.

**Step 1.6 — Write the SKILL.md**  
Using the workspace as the foundation, write the SKILL.md file. The SKILL.md is the agent's operating manual for its specific domain. It must include: role definition, trigger conditions, step-by-step process with decision criteria, output format specification, reference file pointers, and explicit guardrails.

**Step 1.7 — Write Reference Files**  
Write any reference files the SKILL.md points to. These are the agent's domain cheat sheets — condensed, structured knowledge that the agent reads during a task. Reference files belong in semantic memory (not bootstrap) unless they are needed in every single request.

### Phase 2 — Token Optimization (30 minutes)

After writing all workspace files, conduct a token audit:

1. Read every bootstrap file (`SOUL.md`, `AGENTS.md`, `IDENTITY.md`, `USER.md`, `STYLE.md`, today's log). Ask: is every sentence in these files needed in every single request? If not, move it to `MEMORY.md`.
2. Calculate the approximate token count of the bootstrap set. Target: under 2,000 tokens for the combined bootstrap load. The CorCompass shared files (`SOUL.md`, `AGENTS.md`, `STYLE.md`) account for approximately 1,200 tokens. This leaves approximately 800 tokens for `IDENTITY.md`, `USER.md`, and the daily log.
3. Confirm that `MEMORY.md` is populated and that the `memory` tool is enabled. An empty `MEMORY.md` with the memory tool disabled means the agent is running on bootstrap only — half capacity.

### Phase 3 — Security Configuration (15 minutes)

Confirm the following before any agent handles real data:

- `dmScope` is set correctly for the expected number of users
- `exec` mode is `sandbox` or `gateway` with whitelist (never `full`)
- Port 18789 is not exposed to the public internet
- Memory flush before compaction is enabled
- The deployment access method (Tailscale or SSH tunnel) is documented

### Phase 4 — Validation (30–60 minutes)

Run three test tasks through the agent before any client-facing deployment:

1. **The straightforward case** — a well-defined task with complete information
2. **The ambiguous case** — a task with incomplete or unclear information (the agent should ask one targeted clarifying question, not a list)
3. **The stress test** — a task that hits an edge case, a boundary condition, or a failure mode documented in the SKILL.md

After each test, verify: Did the agent maintain CorCompass voice? Did it write to `MEMORY.md` when appropriate? Did it escalate correctly? Did it produce output that meets the quality checklist in `AGENTS.md`?

### Phase 5 — Cron and Heartbeat Setup (15 minutes, if applicable)

For any agent with scheduled tasks:

```bash
openclaw cron add --schedule "0 9 * * *" --agent [agent-name] --prompt "[Task description]" --announce
```

The `--announce` flag delivers results to the configured channel. Use `--no-deliver` for silent background execution. Test the cron job manually before relying on the schedule.

---

## Part V — The 60-Minute Fast Track

For agents needed urgently, use this compressed protocol. The result will be functional but not fully optimized. Schedule a Phase 5 refinement cycle within the first week of use.

| Time | Action |
|---|---|
| 0–10 min | Write `IDENTITY.md` and seed `USER.md` |
| 10–20 min | Write `MEMORY.md` with five seed facts |
| 20–35 min | Write `SKILL.md` using the SKILL.md Generation Prompt |
| 35–45 min | Configure `dmScope`, `exec` mode, and confirm port security |
| 45–60 min | Run three test tasks; note what needs fixing |

---

## Part VI — Multi-Agent Architecture

When deploying multiple CorCompass agents on a single Gateway:

Each agent lives in its own folder under `~/.openclaw/agents/`. Each has its own workspace, sessions, and memory files. The agents share the CorCompass core identity files (`SOUL.md`, `AGENTS.md`, `STYLE.md`) but have distinct `IDENTITY.md`, `USER.md`, and `MEMORY.md` files.

Channel routing is configured in `config.json` via bindings. A message to the Compass channel routes to the Compass agent. A message to the Lumen channel routes to the Lumen agent. The same Gateway serves all agents simultaneously.

Agent isolation is enforced via `dmScope`. Set `dmScope: "per-agent"` to ensure each agent only sees its own dialogues. The Compass agent does not see what the Lumen agent is doing. The Bearing agent does not see client conversations from the Harbor agent.

The CorCompass agent roster on a single Gateway:

```
~/.openclaw/agents/
├── compass/          ← Strategic Advisor
│   ├── SOUL.md       (symlink to shared)
│   ├── AGENTS.md     (symlink to shared)
│   ├── STYLE.md      (symlink to shared)
│   ├── IDENTITY.md   (unique to Compass)
│   ├── USER.md       (per-client, updated per engagement)
│   ├── MEMORY.md     (Compass-specific long-term memory)
│   └── YYYY-MM-DD.md (daily log)
├── atelier/          ← Build Architect
├── waypoint/         ← Operations Manager
├── bearing/          ← Research Analyst
├── harbor/           ← Client Success
└── lumen/            ← Content Engine
```

---

## Part VII — Maintenance Schedule

| Frequency | Activity | Responsible |
|---|---|---|
| Daily | Agent writes to `MEMORY.md` and daily log | Automated (agent) |
| Daily | Heartbeat check runs via cron | Automated (Gateway) |
| Weekly | Review agent output against quality checklist | Operator |
| Weekly | Scan `MEMORY.md` for stale or contradictory entries | Operator |
| Bi-weekly | Content Rewards campaign scan (Lumen only) | Lumen + Operator |
| Monthly | Update reference files (new tools, changed benchmarks) | Operator |
| Quarterly | Full SKILL.md review and revision | Operator |
| Quarterly | Token audit — review bootstrap file sizes | Operator |
| Annually | Role definition review — does the agent's scope still match business needs? | Operator |

---

## Part VIII — Quality Gates

An agent is not ready for client-facing deployment until it passes all five quality gates:

| Gate | Criterion | Test Method |
|---|---|---|
| **Identity** | Speaks in CorCompass voice; never breaks character | Run 5 varied prompts; check STYLE.md compliance |
| **Memory** | Writes to `MEMORY.md` when appropriate; retrieves facts correctly | Ask about a fact seeded in `MEMORY.md`; instruct it to remember something; verify it persists |
| **Domain** | Produces expert-level output in its primary domain | Compare output to a human expert's work on the same task |
| **Escalation** | Asks for help appropriately; does not fabricate | Give it an ambiguous task with missing information |
| **Security** | `dmScope`, `exec` mode, and port access are correctly configured | Review `config.json` against the Part III checklist |

---

## Appendix A — Audit Findings: Existing CorCompass Build

The following gaps were identified when auditing the existing CorCompass training files (v1.1.0) against this SOP:

| Gap | Severity | Status |
|---|---|---|
| `IDENTITY.md` template missing from workspace | High — every agent needs this file | **Resolved in this SOP** |
| `USER.md` template missing from workspace | High — bootstrap memory is incomplete without client profile | **Resolved in this SOP** |
| `MEMORY.md` template missing — semantic search tier not configured | High — agents running on bootstrap only (half capacity, 3× token cost) | **Resolved in this SOP** |
| `HEARTBEAT.md` template missing | Medium — scheduled task agents have no health check structure | **Resolved in this SOP** |
| `TOOLS.md` template missing | Medium — `exec`-enabled agents have no tool reference | **Resolved in this SOP** |
| `dmScope` not specified in any existing SKILL.md or AGENTS.md | High — multi-user deployments will bleed sessions | **Resolved in Part III** |
| `exec` mode not specified — default may be `full` | Critical — production security risk | **Resolved in Part III** |
| No token audit step in curriculum | Medium — bootstrap files may grow without constraint | **Resolved in Phase 2** |
| No cron/heartbeat setup step in curriculum | Medium — scheduled automation not addressed | **Resolved in Phase 5** |
| Multi-agent folder structure not documented | Medium — operators building multiple agents have no reference | **Resolved in Part VI** |

**What was correct in the existing build:**

The five-phase curriculum structure, SKILL.md format, quality gates, escalation protocol, and CorCompass identity files (SOUL.md, AGENTS.md, STYLE.md) were all well-designed and consistent with community best practices. The SKILL.md files for Compass, Atelier, Waypoint, Bearing, Harbor, and Lumen are production-quality. The gaps were in the workspace infrastructure layer, not in the identity or skill layer.

---

## Appendix B — Reference

This SOP was developed against the following source material:

- **OpenClaw Administrator Community Literature** — "Anatomy of OpenClaw: a guide after which you'll build agents differently" (may.crypto, February 26, 2026): six-component architecture, two memory tiers, five critical mistakes, token efficiency analysis
- **CorCompass Training Files v1.1.0** — SOUL.md, AGENTS.md, STYLE.md, CURRICULUM.md, all SKILL.md files
- **GitHub Best Practices for AGENTS.md** — GitHub Blog, "How to write a great agents.md: lessons from over 2,500 repositories"
- **soul.md Project** — aaronjmars/soul.md: SOUL.template.md, SKILL.md format conventions

---

*CorCompass is a protected series of Cor Infinitum LLC, a Texas Protected Series Limited Liability Company.*  
*This document is confidential and intended for internal operator use only.*
