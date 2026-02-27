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
