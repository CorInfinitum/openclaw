# CorCompass Cost Governance -- Operational Cost-Savings Reference

**Document ID:** REF-COST-GOV-001
**Version:** 1.0.0 -- March 3, 2026
**Classification:** Internal -- Operator Use Only
**Source:** Adapted from Ziwen Xu's "$50/Month AI Company" playbook + CorCompass operational experience

---

## The Core Principle: Execution Over Tokens

The most expensive mistake in multi-agent deployments is paying premium API rates for tasks that do not require premium intelligence. The CorCompass cost governance framework separates agent workloads into three tiers and routes each tier to the cheapest capable model.

> "Complexity is expensive. Optimize for output, not tokens." -- Ziwen Xu

---

## The Three-Tier Model Routing Framework

| Tier | Task Type | Examples | Recommended Model | Cost |
|---|---|---|---|---|
| Tier 1: Heartbeat | Autonomous check-ins, polling, routing | "Is there a new task?" "Any messages?" | Local LM Studio (Qwen 3 4B or Gemma 3 4B) | $0 |
| Tier 2: Reasoning | Logic, planning, tool use, structured output | Research synthesis, workflow decisions, CRM updates | MiniMax M2.5 or Claude Haiku | $10-50/mo |
| Tier 3: Deep Work | Complex writing, code generation, client-facing output | Proposal drafts, strategy documents, code | Claude Sonnet / GPT-4o | Per-use |

**Rule:** Never use a Tier 3 model for a Tier 1 task. The heartbeat trap -- running premium models for constant background pings -- is the single largest source of runaway API costs.

---

## The Heartbeat Trap (and How to Avoid It)

### What It Is

Every autonomous OpenClaw agent has a heartbeat: a recurring check that wakes the agent and asks "is there work to do?" With multiple agents running 24/7, these heartbeats fire every few seconds. If each heartbeat calls a premium API (Claude, GPT-4o, Gemini Pro), the cost compounds rapidly.

### Real-World Cost Example

- 9 agents x 1 heartbeat per 30 seconds x 24 hours = 25,920 API calls/day
- At $0.003 per call (Claude Haiku) = $77.76/day = $2,332/month
- At $0.015 per call (Claude Sonnet) = $388.80/day -- catastrophic

### The Fix: Local Heartbeats

Route all Tier 1 heartbeat tasks to a locally-running model via LM Studio. The model only needs to answer: "Is there a new task in my queue?" -- a 3B parameter model handles this perfectly.

**Recommended local models for heartbeats (M4 Mac Mini / 16GB RAM):**

| Model | Response Time | Best For |
|---|---|---|
| Qwen 3 4B | ~30 sec | Agentic routing, tool-use decisions |
| Gemma 3 4B | ~21 sec | Instruction following, stable output |
| Gemma 2 3B | ~15 sec | Simple polling, status checks |
| Qwen 2.5 3B | ~10 sec | Speed-critical pings (less reliable) |

---

## The Elite Squad Principle (Freshman Rule)

### The Problem with Large Agent Teams

More agents = more heartbeats + more inter-agent communication + more context overhead. A 9-agent team does not produce 9x the output of a 2-agent team -- it produces 2x the output at 9x the cost.

### The Freshman Rule

Treat every agent like a new employee who knows nothing about your project history:

1. **One task per agent at a time.** Multi-tasking agents fail at most tasks.
2. **Explicit context every session.** Do not assume the agent remembers previous work. Load the relevant workspace files at the start of each task.
3. **Minimal agent count.** Start with 2 agents. Add a third only when the first two are consistently at capacity.
4. **Clear task boundaries.** Each agent owns one domain. No overlap, no ambiguity.

### CorCompass Recommended Squad Sizes

| Deployment Type | Recommended Agent Count | Rationale |
|---|---|---|
| Solo operator (CorCompass internal) | 2-3 | Compass + Bearing + Lumen |
| Harbor Build client (small business) | 2-3 | Role-specific + general ops |
| Harbor Build client (scaling business) | 4-5 | Add Waypoint + Harbor |
| Wrapper product deployment | 1-2 | Single-purpose niche agent |

---

## The Hybrid Engine: Budget Stack for CorCompass

### Recommended Monthly Stack

| Component | Tool | Cost | Purpose |
|---|---|---|---|
| Local hardware | M4 Mac Mini 16GB (one-time ~$600) or VPS | $0-20/mo | Heartbeats + LM Studio |
| Primary reasoning model | MiniMax M2.5 Max Plan | $50/mo | Tier 2 tasks, high volume |
| Deep work model | Claude API (pay-per-use) | $20-50/mo | Client deliverables, proposals |
| Web search | Brave Search API | $3-10/mo | Agent research capability |
| Communication | Telegram Bot API | $0 | Agent notifications |
| **Total** | | **$73-130/mo** | Full autonomous operation |

### Alternative Stack (Cloud-Only, No Hardware)

| Component | Tool | Cost |
|---|---|---|
| VPS (2 vCPU, 4GB RAM) | Hetzner / DigitalOcean | $6-12/mo |
| Primary model | MiniMax M2.5 Standard | $20/mo |
| Deep work | Claude API | $20-50/mo |
| Search | Brave Search | $5/mo |
| **Total** | | **$51-87/mo** |

---

## The "Free Start" Path (Zero-Cost Bootstrap)

For new CorCompass clients or operators testing a deployment before committing to paid infrastructure:

1. **Google Cloud $300 free credit** -- Run Gemini 2 Flash for 2-3 months at zero cost. Warning: rate limits are aggressive; expect throttling during peak hours.
2. **Ollama local models** -- Run Llama 3.1 8B or Qwen 3 8B locally for free on any machine with 8GB+ RAM.
3. **Telegram bot** -- Free. Use as the primary agent interface during the bootstrap phase.
4. **Brave Search** -- Add $5 for web access. Non-negotiable for research agents.

**Bootstrap runway:** A $5 Brave Search credit + Google Cloud free tier can run a 2-agent setup for 60-90 days at zero recurring cost. Use this window to validate the deployment before investing in paid infrastructure.

---

## Cost Monitoring Checklist

Run this checklist monthly for every active CorCompass deployment:

- [ ] Review API dashboard for each model provider -- flag any single-day spikes above 2x average
- [ ] Confirm heartbeat agents are routing to local/cheap models, not premium APIs
- [ ] Check agent count -- any agents added since last review? Apply the Freshman Rule before activating
- [ ] Review MiniMax prompt usage -- are prompts being consumed by heartbeats or by actual work?
- [ ] Confirm LM Studio is running on the client's local hardware (if applicable)
- [ ] Check for "zombie agents" -- agents that are active but not producing output
- [ ] Review Brave Search usage -- are agents making unnecessary search calls?

---

## Warning Signs of Cost Runaway

| Warning Sign | Likely Cause | Fix |
|---|---|---|
| API costs spike overnight | Heartbeats on premium model | Move heartbeats to local LM Studio |
| Rate limit bans from provider | Too many agents on same API key | Separate API keys per agent tier |
| "Token bloat" in conversations | Agents passing full context unnecessarily | Implement context summarization in MEMORY.md |
| Costs double when adding one agent | New agent has premium heartbeat | Audit new agent's model routing before activation |
| Costs spike on weekends | Scheduled tasks overlapping | Stagger heartbeat intervals across agents |

---

## Integration with CorCompass SOP

This reference file supplements Phase 3 (Configuration) of the SOP-AGENT-BUILD.md. Before activating any agent:

1. Assign the agent to a model tier (1, 2, or 3) based on task type
2. Configure the heartbeat to use a Tier 1 model
3. Set the agent's task scope to a single domain (Freshman Rule)
4. Add the agent to the monthly cost monitoring checklist

See SOP-AGENT-BUILD.md Phase 3 for the full configuration protocol.

---

## Keywords

\`cost-governance\` \`budget-control\` \`heartbeat-trap\` \`lm-studio\` \`minimax\` \`local-models\` \`freshman-rule\` \`elite-squad\` \`api-costs\` \`token-optimization\` \`hybrid-engine\` \`qwen\` \`gemma\` \`rate-limits\` \`cost-monitoring\` \`autonomous-agents\` \`operational-savings\`
