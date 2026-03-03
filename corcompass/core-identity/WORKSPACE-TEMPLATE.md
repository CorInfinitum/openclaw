# CorCompass Workspace Template
## Canonical File Set for Any New Agent Deployment

**Version:** 1.2.0 — March 1, 2026  
**Usage:** Copy this template directory when creating a new CorCompass agent workspace. Replace all `[bracketed]` fields before the agent handles any real task.

---

## Directory Structure

```
~/.openclaw/agents/[agent-name]/
├── SOUL.md           ← symlink to shared core-identity/SOUL.md
├── AGENTS.md         ← symlink to shared core-identity/AGENTS.md
├── STYLE.md          ← symlink to shared core-identity/STYLE.md
├── IDENTITY.md       ← unique to this agent (write from template below)
├── USER.md           ← profile of the person being served (write from template below)
├── MEMORY.md         ← long-term semantic memory (seed before first session)
├── HEARTBEAT.md      ← periodic health checklist (required if cron is used)
├── TOOLS.md          ← local tool hints (required if exec tool is enabled)
├── YYYY-MM-DD.md     ← today's daily log (Gateway creates automatically)
└── role-skills/
    └── [agent-name].md  ← the agent's SKILL.md
```

**Bootstrap files** (loaded into every request — keep lean, target < 2,000 tokens combined):
`SOUL.md` + `AGENTS.md` + `STYLE.md` + `IDENTITY.md` + `USER.md` + today's `YYYY-MM-DD.md`

**Semantic files** (searched on demand — no token cost unless retrieved):
`MEMORY.md` + reference files in `role-skills/reference/`

---

## IDENTITY.md Template

```markdown
# Identity

My name is [Agent Name]. I am the CorCompass [Role Title].

[One sentence describing the primary function — what this agent does every day.]

[One sentence describing the tone and style this agent brings — warm/analytical/precise/etc.]

I operate under the CorCompass banner — a protected series of Cor Infinitum LLC, Dallas, Texas.
Every interaction reflects the standard: Guided by Heart, Powered by Logic.
```

**Word budget:** 80–120 words maximum. Every word here costs tokens on every request.

---

## USER.md Template

```markdown
# User Profile — [Client Name or "Operator"]

**Name:** [How to address this person — first name, title, or handle]
**Role:** [Their title or function — "Founder," "Operations Director," "CorCompass Operator"]
**Organization:** [Company, practice, or context]
**Communication preference:** [Direct / narrative / structured / informal]
**Primary focus:** [What they are working on right now — update each engagement]
**Known preferences:** [Specific things they like in responses — bullet lists, short answers, etc.]
**Avoid:** [Topics, formats, or approaches that do not serve this person]

## Active Context

[2–4 sentences describing the current engagement, project phase, or ongoing work.
Update this section at the start of each new phase or major milestone.]

## Relationship Notes

[How long this relationship has been active. Key milestones. Trust level.
Any sensitivities or communication patterns to be aware of.]
```

**Update cadence:** Revise the Active Context section at the start of each new engagement phase. Add to Relationship Notes whenever a significant milestone or preference is established.

---

## MEMORY.md Template

```markdown
# Long-Term Memory — [Agent Name]

*This file is searched semantically via the memory tool.*
*Write facts here that must persist across sessions.*
*The agent writes here autonomously when instructed to remember something.*
*Format: [YYYY-MM-DD] — [Fact or decision, with context.]*

---

## Decisions

[YYYY-MM-DD] — [Decision made, who made it, context, and reasoning.]

## Preferences

[YYYY-MM-DD] — [Preference established — e.g., "Client prefers bullet lists over prose for status updates."]

## Project Facts

[YYYY-MM-DD] — [Key fact about an active project, client, or engagement.]

## Domain Knowledge

[YYYY-MM-DD] — [Specialized knowledge refined through experience — e.g., "Hospitality clients in DFW typically have 3–5 person ops teams."]

## Client History

[YYYY-MM-DD] — [Significant event in a client relationship — e.g., "Client paused Harbor Build in March due to staffing change. Resume Q2."]
```

**Memory flush instruction** (add to AGENTS.md or IDENTITY.md):
> "When a client states a preference, makes a decision, or shares a fact that should persist across sessions, write it to `MEMORY.md` immediately using the format: `[YYYY-MM-DD] — [Fact or decision, with context].`"

---

## HEARTBEAT.md Template

```markdown
# Heartbeat Checklist — [Agent Name]

*Gateway runs this checklist on the configured cron schedule.*
*The agent checks each item and reports anomalies to [channel].*

## Daily Checks (run at [HH:MM] via cron)

- [ ] [Check item — e.g., "Confirm pipeline ran and produced expected output count"]
- [ ] [Check item — e.g., "Verify no error logs in the last 24 hours"]
- [ ] [Check item — e.g., "Confirm scheduled posts went out on time"]

## Weekly Checks (run on [day] at [HH:MM] via cron)

- [ ] [Weekly item — e.g., "Review Content Rewards active campaigns for new briefs"]
- [ ] [Weekly item — e.g., "Check platform monetization status for all active channels"]
- [ ] [Weekly item — e.g., "Review MEMORY.md for stale or contradictory entries"]

## Escalation Threshold

If any check fails, send alert to [channel] with:
- Item name
- Failure description
- Recommended action
- Severity: [INFO / WARNING / CRITICAL]
```

**Cron setup command:**
```bash
openclaw cron add --schedule "0 9 * * *" --agent [agent-name] --prompt "Run heartbeat checklist from HEARTBEAT.md. Report any failures to [channel]." --announce
```

---

## TOOLS.md Template

```markdown
# Available Tools — [Agent Name]

*Read this file before using the exec tool.*
*Every script and command available to this agent is documented here.*

## exec Mode: [sandbox / gateway]

[If gateway mode: list the whitelisted commands from exec-approvals.json]

## Scripts

| Script | Path | Purpose | Expected Output |
|---|---|---|---|
| [script-name] | [/full/path/to/script.sh] | [What it does] | [What it returns] |

## Commands

| Command | Purpose | Example |
|---|---|---|
| [command] | [What it does] | `[example invocation]` |

## File Locations

| Resource | Path | Notes |
|---|---|---|
| [Resource name] | [/full/path/] | [Any relevant notes] |

## Shortcuts

[Any aliases, shortcuts, or compound commands that save time]
```

---

## config.json Security Settings

The following settings must be confirmed before any agent handles real data:

```json
{
  "agents": {
    "[agent-name]": {
      "dmScope": "per-channel-peer",
      "exec": {
        "mode": "sandbox"
      }
    }
  }
}
```

**`dmScope` values:**
- `"per-channel-peer"` — required for any agent accessed by more than one person
- `"per-agent"` — acceptable for single-operator internal agents
- `"main"` — never use in production; all users share one session

**`exec` mode values:**
- `"sandbox"` — Docker container, fully isolated; use by default
- `"gateway"` — controlled server access with whitelist; use when server access is required
- `"full"` — no restrictions; never use on production deployments

---

*CorCompass is a protected series of Cor Infinitum LLC, a Texas Protected Series Limited Liability Company.*
