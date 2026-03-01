# CorCompass Agent Training System — Version Log

*Maintained by Cor Infinitum LLC. Internal use only.*

---

## v1.0.0 — February 27, 2026

### Initial Release: Agent Training & Development System

This release introduces the complete CorCompass agent training and development infrastructure, organized as a structured curriculum and identity system for the CorCompass AI agent roster.

#### Core Identity Files (new)

| File | Purpose |
|---|---|
| `core-identity/SOUL.md` | Collective brand identity for all CorCompass agents — worldview, voice, vocabulary, opinions, and boundaries |
| `core-identity/STYLE.md` | Voice and formatting guide — sentence structure, tone calibration by context, anti-patterns, and CorCompass-specific phrases |
| `core-identity/AGENTS.md` | Universal operating principles — agent roster, escalation protocol, output quality standards, interaction patterns |

#### Training Curriculum (new)

| File | Purpose |
|---|---|
| `curriculum/CURRICULUM.md` | Five-phase agent development protocol — Deep Research → Skill Construction → Plugin Assembly → Validation → Refinement |
| `curriculum/prompts/phase-1-prompts.md` | Seven deep research prompts for building agent knowledge bases from scratch |
| `curriculum/prompts/phase-2-prompts.md` | Four skill construction prompts for writing SKILL.md files and reference documents |
| `curriculum/prompts/phase-3-5-prompts.md` | Plugin assembly, validation, scaling, and bonus prompts including "Convert a workflow to a skill" and "Build a skill from a job description" |

#### Role Skills (new)

| File | Agent | Domain |
|---|---|---|
| `role-skills/compass-advisor.md` | Compass | Strategic Advisor — client intake, HeartCor assessment, service tier recommendation |
| `role-skills/atelier-architect.md` | Atelier | Build Architect — OpenClaw skill/tool configuration, Blueprint design, plugin assembly |
| `role-skills/waypoint-ops.md` | Waypoint | Operations Manager — project management, workflow design, milestone tracking |
| `role-skills/bearing-analyst.md` | Bearing | Research Analyst — market research, competitive analysis, data synthesis |
| `role-skills/harbor-success.md` | Harbor | Client Success — onboarding, relationship management, renewals, referrals |

#### Reference Files (new)

| File | Purpose |
|---|---|
| `reference/heartcor-methodology.md` | Proprietary HeartCor framework — Heart/Logic/Coherence dimensions, diagnostic questions, common misalignment patterns, service tier selection matrix |
| `reference/corcompass-service-tiers.md` | Service tier reference — Flow Scan, Coherence Sprint, Harbor Build definitions, conversion signals, tier selection decision framework, pricing principles |

#### Website Backend (new)

Added **Agent Training & Development** tab to the Operator HQ dashboard (`/operator`). The tab provides a three-panel viewer with:

- Section navigation (Core Identity, Curriculum, Role Skills, Reference)
- File list with badge indicators (Load First/Second/Third, role type, phase count)
- Full markdown viewer with copy-to-clipboard and GitHub link for each file
- Quick Load Order footer showing the five-step agent initialization sequence

---

## v1.1.0 — March 1, 2026

### Content Engine Agent Build + Agent Library Index

This release introduces the Lumen Content Engine agent, two new reference files, a master library index, and the Agent Library tab in Operator HQ.

#### New Role Skill (new)

| File | Agent | Domain |
|---|---|---|
| `role-skills/content-engine.md` | Lumen | Content Engine — short-form video production pipeline, pop culture content mining, Content Rewards monetization, OpenClaw + Claude + CapCut stack orchestration |

#### New Reference Files (new)

| File | Purpose |
|---|---|
| `reference/content-rewards-platform.md` | Content Rewards platform briefing — campaign matching protocol, payout structure by category, submission best practices |
| `reference/content-production-stack.md` | Full pipeline configuration — OpenClaw skills, Claude script prompts, CapCut template specs, source library management, quality control checkpoints |

#### Master Library Index (new)

| File | Purpose |
|---|---|
| `LIBRARY_INDEX.md` | Keyword-tagged index of all 34 compiled assets across 7 asset types: identity files, curriculum, agent SKILL.md files, reference files, training prompts, OpenClaw skills, and topic clusters |

#### Website Backend (updated)

Added **Agent Library** tab to the Operator HQ dashboard (`/operator`). The tab provides:

- Full-text keyword search across all 34 indexed assets (title, subtitle, description, keywords, agent, ID)
- Filter panel: asset type (7 types) and agent (6 agents)
- Expandable asset cards showing all keywords as clickable search tags
- GitHub link and copy-reference button per asset
- Stats bar: total assets, agents, OpenClaw skills, topic clusters, references
- Standard Load Order footer with clickable filter shortcuts

Also added **Lumen** and two new reference files to the Agent Training tab viewer.

#### Lumen Content Engine Summary

Lumen is the CorCompass content production and monetization agent. The name derives from the Latin unit of luminous flux. Lumen orchestrates an end-to-end automated pipeline:

```
Topic Cluster → Claude Batch Scripts → Clip Matching → CapCut Assembly → Scheduler → Content Rewards + Platform Monetization
```

**Monetization pathways:** YouTube Partner Program, TikTok Creator Rewards, Instagram Reels Bonuses, Content Rewards (brand-funded, per 1,000 verified views).

**Production Sprint Protocol:** Week 1 pipeline build → Weeks 2–3 bulk production (200–300 videos) → Week 4 monetization activation → Ongoing 3–5 videos/day across 3+ channels.

**Key insight:** The same pipeline built for YouTube/TikTok is the identical pipeline pointed at a Content Rewards brief. One system, two revenue streams.

---

## Load Order Reference

When initializing any CorCompass agent session, load files in this order:

1. `core-identity/SOUL.md` — collective identity
2. `core-identity/STYLE.md` — voice and formatting
3. `core-identity/AGENTS.md` — operating principles
4. `role-skills/[agent-name].md` — domain expertise
5. `reference/[relevant-file].md` — task-specific reference

---

## Architecture Notes

The training system is designed to be:

**Modular** — each file is self-contained and can be loaded independently or in combination.

**Layered** — core identity files apply to all agents; role skills apply to specific agents; reference files apply to specific tasks.

**Extensible** — new role skills can be added by following the five-phase curriculum. New reference files can be added to the `reference/` directory and will appear automatically in the Operator HQ viewer.

**Version-controlled** — all training files are tracked in the CorInfinitum/openclaw repository under `corcompass/`. Changes to training files create a permanent audit trail.

---

*CorCompass is a protected series of Cor Infinitum LLC, a Texas Protected Series Limited Liability Company.*
