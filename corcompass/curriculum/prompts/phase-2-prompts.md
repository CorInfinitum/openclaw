# Phase 2 Prompts — Build the Skill

*Use these prompts to convert Phase 1 research into a deployable SKILL.md file.*

---

## Prompt 2.1 — Generate SKILL.md

```
Using the research below, write a complete SKILL.md file for a CorCompass OpenClaw agent.

**Agent Role:** [JOB TITLE]
**Primary Task:** [PRIMARY TASK]

**Research Inputs:**
[PASTE PHASE 1 KNOWLEDGE FILES]

**SKILL.md Requirements:**

The file must include:

1. **Frontmatter table** with `name` and `description` fields. The description must be aggressive about trigger conditions — it should activate whenever a task falls within this agent's domain.

2. **Role Definition** — who this agent is, what it knows, what it does

3. **Trigger Conditions** — exact phrases, task types, or contexts that should activate this skill

4. **Step-by-Step Process** — the complete workflow, numbered, with:
   - What the agent does at each step
   - What inputs are needed
   - What decision criteria apply
   - What the output of each step looks like
   - When to stop and ask vs. proceed with stated assumptions

5. **Output Format Specification** — exactly what the final deliverable looks like, including structure, length, tone, and required elements

6. **Reference File Pointers** — list the reference files the agent should read for each part of the workflow

7. **Guardrails** — explicit rules about what the agent will and will not do, when it escalates, and how it handles edge cases

8. **Quality Checklist** — the self-assessment the agent runs before delivering output

**CorCompass Standards:**
- Voice: warm, authoritative, sophisticated (see STYLE.md)
- Every output must be actionable, specific, calibrated, and branded
- Use CorCompass vocabulary: Blueprint, Atelier, HeartCor, Bearing, Waypoint, Harbor
- Never break character; express uncertainty in-character

Make the description field aggressive — it should trigger on any task that falls within this agent's domain, not just exact keyword matches.
```

---

## Prompt 2.2 — Create Reference Files

```
I've written a SKILL.md for a [JOB TITLE] agent. The skill references these knowledge areas:
[LIST REFERENCE FILES MENTIONED IN SKILL.MD]

For each reference file, write a clean, structured markdown document that:

1. Is optimized for an AI agent to read quickly during task execution (not for human reading)
2. Uses tables, numbered lists, and clear headers for scannability
3. Includes only information the agent will actually use — no background or context padding
4. Quantifies everything that can be quantified (thresholds, benchmarks, timeframes)
5. Flags anything that requires human judgment with a clear [ESCALATE] marker

Here is the research the reference files should be based on:
[PASTE RELEVANT PHASE 1 RESEARCH]

Output one markdown file per knowledge domain.
```

---

## Prompt 2.3 — Test with Three Scenarios

```
I've built a SKILL.md for a [JOB TITLE] agent. Here is the skill file:
[PASTE SKILL.MD]

Run three test scenarios and evaluate the output against the CorCompass quality standard:

**Scenario 1 — The Easy Case:**
[DESCRIBE A STRAIGHTFORWARD, WELL-DEFINED TASK]

**Scenario 2 — The Realistic Case:**
[DESCRIBE A TASK WITH INCOMPLETE OR AMBIGUOUS INFORMATION]

**Scenario 3 — The Stress Test:**
[DESCRIBE A TASK THAT HITS AN EDGE CASE OR FAILURE MODE]

For each scenario:
1. Execute the full workflow as defined in SKILL.md
2. Produce the deliverable in the specified output format
3. Run the quality checklist
4. Self-assess: what worked, what was missing, what would improve the output

After all three scenarios, provide a consolidated assessment:
- What is the skill doing well?
- What is it getting wrong consistently?
- What is missing from the SKILL.md that would fix the failures?
- What reference files are needed that don't exist yet?
```

---

## Prompt 2.4 — Iterate and Fix

```
I've run test scenarios on my [AGENT-NAME] agent. Here's my review:

**What's working well (KEEP):**
[LIST WHAT WORKED — e.g., "Process steps are clear, output format is correct, escalation rules are appropriate"]

**What needs improvement (FIX):**
[LIST SPECIFIC ISSUES — e.g., "The recommendation section is too hedged — I want a clear verdict in the first sentence", "It's not handling the case where client data is incomplete"]

**What's missing (ADD):**
[LIST THINGS THAT SHOULD BE THERE — e.g., "Need a section on how to handle conflicting data sources", "Add a quick-scan version of the workflow for time-sensitive situations"]

**What's excessive (REMOVE or REDUCE):**
[LIST THINGS TO CUT — e.g., "The background section is too long", "Don't repeat the client name in every section header"]

**Instructions:**
1. Update the SKILL.md to address every point above
2. Update any reference files that need changes
3. Show me the changes as a before/after for each modification
4. If any change might break other parts of the workflow, flag it
5. After changes, re-run the quality checklist against the updated skill

Here is the current SKILL.md:
[PASTE CURRENT SKILL.MD]
```
