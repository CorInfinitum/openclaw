# OpenClaw Agent Training Curriculum
## CorCompass Expert Agent Development Protocol

*Version 1.0 — February 2026*

---

## Overview

This curriculum transforms a base LLM into an expert CorCompass agent through five structured phases. Each phase builds on the last. Skipping phases produces mediocre agents. Following the protocol in order produces agents that perform at the level of a seasoned human professional in their domain.

The curriculum is adapted from the OpenClaw Agent Development Framework and calibrated specifically for CorCompass's luxury consulting context, HeartCor methodology, and client-facing quality standards.

---

## The Five-Phase Protocol

| Phase | Name | Duration | Output |
|---|---|---|---|
| 1 | **Deep Research** | 2–4 hours | Knowledge base files |
| 2 | **Skill Construction** | 1–2 hours | SKILL.md + reference files |
| 3 | **Plugin Assembly** | 30–60 min | Slash commands + plugin structure |
| 4 | **Installation & Validation** | 30 min | Tested, working agent |
| 5 | **Refinement & Scaling** | Ongoing | Improved skills, new capabilities |

---

## Phase 1: Deep Research — Build the Brain

The quality of your agent is bounded by the quality of its knowledge base. This phase cannot be rushed.

### Step 1.1 — Define the Agent Role

Before researching, answer three questions precisely:

1. What domain is this agent an expert in?
2. What specific tasks should it perform repeatedly?
3. What does a finished deliverable look like?

Use the **Role Definition Prompt** (see `curriculum/prompts/phase-1-prompts.md`, Prompt 1.1) to generate a structured role document. Save the output as `role-skills/[agent-name]-role-definition.md`.

### Step 1.2 — Research the Core Process

Map the expert workflow step by step. For each step, capture: what triggers it, what inputs are needed, what tools are used, what the decision criteria are, and what the output looks like.

Use the **Core Process Research Prompt** (Prompt 1.2). Save output as `reference/[agent-name]-process.md`.

### Step 1.3 — Research Tools and Data Sources

Identify every tool, API, database, and platform the agent will need access to. Categorize by: primary data sources, calculation tools, reference databases, output/delivery tools, and automation connectors.

Use the **Tools Research Prompt** (Prompt 1.3). Save output as `reference/[agent-name]-tools.md`.

### Step 1.4 — Research Decision Frameworks

Capture the expert judgment that separates senior professionals from juniors. This includes quantitative thresholds, qualitative heuristics, risk frameworks, and the "expert vs. novice" gap.

Use the **Decision Frameworks Prompt** (Prompt 1.4). Save output as `reference/[agent-name]-decisions.md`.

### Step 1.5 — Research Output Format Standards

Define exactly what the finished work product looks like: document structure, formatting standards, tone, required elements, and what separates good from great.

Use the **Output Standards Prompt** (Prompt 1.5). Save output as `reference/[agent-name]-output-standards.md`.

### Step 1.6 — Research Edge Cases and Failure Modes

Document the unusual situations, common mistakes, and failure modes the agent must handle gracefully. This is what separates a reliable agent from a brittle one.

Use the **Edge Cases Prompt** (Prompt 1.6). Save output as `reference/[agent-name]-edge-cases.md`.

### Step 1.7 — Organize into Knowledge Files

Review all research outputs. Consolidate, deduplicate, and organize into a clean knowledge base. The agent will read these files as its domain expertise.

**Knowledge base structure:**
```
reference/
├── [agent-name]-process.md
├── [agent-name]-tools.md
├── [agent-name]-decisions.md
├── [agent-name]-output-standards.md
└── [agent-name]-edge-cases.md
```

---

## Phase 2: Build the Skill

The SKILL.md file is the agent's operating manual. It tells the agent what to do, in what order, to what standard, and when to stop and ask.

### Step 2.1 — Generate SKILL.md

Using the research from Phase 1, write the SKILL.md file. It must include:
- Role definition and trigger conditions
- Step-by-step process with decision criteria
- Output format specification
- Reference file pointers
- Explicit guardrails and escalation rules

Use the **SKILL.md Generation Prompt** (see `curriculum/prompts/phase-2-prompts.md`, Prompt 2.1).

### Step 2.2 — Create Reference Files

Write any reference files the SKILL.md points to. These are the agent's "cheat sheets" — condensed, structured versions of the Phase 1 research that the agent can read quickly during a task.

### Step 2.3 — Test with Three Scenarios

Run three test tasks through the agent:
1. A straightforward, well-defined task (the easy case)
2. A task with incomplete or ambiguous information (the realistic case)
3. A task that hits an edge case or failure mode (the stress test)

Document what worked, what failed, and what was missing.

### Step 2.4 — Iterate and Fix

Update the SKILL.md and reference files based on test results. Repeat until all three scenarios produce output that meets the CorCompass quality standard.

---

## Phase 3: Build the Plugin

The plugin packages the skill into a deployable unit with slash commands, folder instructions, and any necessary integrations.

### Step 3.1 — Generate Plugin Structure

Create the plugin directory structure:
```
[agent-name]-plugin/
├── SKILL.md
├── commands/
│   ├── [primary-command].md
│   └── [secondary-command].md
├── instructions/
│   └── global.md
└── reference/
    └── [linked reference files]
```

Use the **Plugin Structure Prompt** (see `curriculum/prompts/phase-3-prompts.md`, Prompt 3.1).

### Step 3.2 — Write Slash Commands

Each slash command is a trigger that activates a specific workflow. Commands should be:
- Named intuitively (what the user would naturally type)
- Scoped precisely (one command, one workflow)
- Self-documenting (the command description tells the agent exactly what to do)

### Step 3.3 — Write Global and Folder Instructions

Global instructions apply to every interaction with the agent. Folder instructions apply when the agent is working in a specific directory. Both should reinforce the SOUL.md identity and STYLE.md voice.

---

## Phase 4: Install and Validate

### Step 4.1 — Install and Validate Structure

Before testing, validate:
- All SKILL.md files are properly formatted
- All slash command files are syntactically correct
- All reference file pointers resolve to actual files
- The plugin directory structure matches the expected format

Use the **Validation Prompt** (Prompt 4.1).

### Step 4.2 — First Full Test Run

Run a complete, realistic task from start to finish. After delivery, the agent self-assesses:
- Which steps from SKILL.md were executed?
- Which steps were skipped or modified, and why?
- Where was data missing, and how was it handled?
- What would improve this output?

Document the self-assessment. Use it to drive the first round of Phase 5 refinement.

---

## Phase 5: Refine and Scale

### Step 5.1 — Post-Review Refinement

After the first real-world use, update the SKILL.md based on what worked and what didn't. Use the **Skill Refinement Prompt** (see `curriculum/prompts/phase-5-prompts.md`, Prompt 5.1).

### Step 5.2 — Add New Skills

Once the primary skill is stable, expand the agent's capabilities by adding secondary skills. Each new skill follows the same Phase 1–4 process, but can reference existing reference files to avoid duplication.

### Step 5.3 — Design Multi-Step Workflows

Chain skills together into automated workflows. Define: which steps run in parallel, which are sequential, what the decision points are, and how errors are handled.

### Step 5.4 — Weekly Performance Review (Recurring)

Every week, review the agent's output against the CorCompass quality standard. Use the **Weekly Review Prompt** (Prompt 5.4) to systematically improve the agent over time.

---

## The 60-Minute Fast Track

For agents needed urgently, use this compressed protocol:

**Minutes 0–15:** Run the Role Definition Prompt and Core Process Research Prompt. Save outputs.

**Minutes 15–30:** Run the SKILL.md Generation Prompt with the research as input.

**Minutes 30–45:** Build the plugin structure and write the primary slash command.

**Minutes 45–60:** Run three test tasks. Note what needs fixing.

The fast-track agent will be functional but not expert-level. Schedule a full Phase 5 refinement cycle within the first week of use.

---

## Quality Gates

An agent is not ready for client-facing deployment until it passes all quality gates:

| Gate | Criterion | How to Test |
|---|---|---|
| **Identity** | Speaks in CorCompass voice, never breaks character | Run 5 varied prompts, check STYLE.md compliance |
| **Domain** | Produces expert-level output in its primary domain | Compare output to a human expert's work on the same task |
| **Escalation** | Asks for help appropriately, does not fabricate | Give it an ambiguous task with missing information |
| **Edge Cases** | Handles unusual situations gracefully | Run the stress-test scenarios from Phase 2.3 |
| **Output Quality** | Every deliverable is actionable, specific, calibrated, branded | Run the quality checklist from AGENTS.md |

---

## Maintenance Schedule

| Frequency | Activity |
|---|---|
| Weekly | Performance review (Prompt 5.4) |
| Monthly | Reference file updates (new tools, changed benchmarks, updated regulations) |
| Quarterly | Full SKILL.md review and revision |
| Annually | Role definition review — does the agent's scope still match business needs? |
