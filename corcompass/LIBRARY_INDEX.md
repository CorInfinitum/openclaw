# CorCompass Agent Library — Master Index

**Series:** CorCompass Protected Series — Cor Infinitum LLC  
**Version:** 1.1.0 — February 27, 2026  
**Maintained by:** Waypoint (Operations Manager)  

This index catalogs every compiled skill, tool, agent build, reference file, and training document in the CorCompass agent library. Each entry includes a type classification, load order, a brief description, and searchable keywords.

---

## Index Structure

| Column | Meaning |
|---|---|
| **ID** | Unique identifier for this asset |
| **Type** | `identity` / `curriculum` / `agent` / `reference` / `prompt` |
| **File** | Path relative to `agent-training/` |
| **Load Order** | When to load this file relative to others |
| **Keywords** | Searchable tags for this asset |

---

## Core Identity Files

| ID | Type | File | Load Order | Description |
|---|---|---|---|---|
| `CI-001` | identity | `core-identity/SOUL.md` | 1st — always | Collective brand identity: worldview, voice, vocabulary, opinions, boundaries |
| `CI-002` | identity | `core-identity/STYLE.md` | 2nd — always | Voice and formatting guide: sentence structure, tone calibration, anti-patterns |
| `CI-003` | identity | `core-identity/AGENTS.md` | 3rd — always | Universal operating principles: agent roster, escalation protocol, output standards |

**Keywords:** `identity` `brand-voice` `soul` `style` `agents` `corcompass` `operating-principles` `tone` `vocabulary` `escalation` `worldview` `luxury` `consulting`

---

## Training Curriculum

| ID | Type | File | Load Order | Description |
|---|---|---|---|---|
| `CU-001` | curriculum | `curriculum/CURRICULUM.md` | 4th — before role skill | Five-phase agent development protocol overview and phase map |
| `CU-002` | prompt | `curriculum/prompts/phase-1-prompts.md` | Phase 1 | 7 deep research prompts for building agent knowledge bases from scratch |
| `CU-003` | prompt | `curriculum/prompts/phase-2-prompts.md` | Phase 2 | 4 skill construction prompts for writing SKILL.md files and reference documents |
| `CU-004` | prompt | `curriculum/prompts/phase-3-5-prompts.md` | Phases 3–5 | Plugin assembly, validation, scaling, and bonus prompts |

**Keywords:** `curriculum` `training` `five-phase` `prompts` `knowledge-base` `skill-construction` `plugin-assembly` `validation` `scaling` `agent-development` `onboarding`

---

## Agent Role Skills

| ID | Type | File | Agent | Domain | Load Order |
|---|---|---|---|---|---|
| `RS-001` | agent | `role-skills/compass-advisor.md` | Compass | Strategic Advisor | 5th — after identity |
| `RS-002` | agent | `role-skills/atelier-architect.md` | Atelier | Build Architect | 5th — after identity |
| `RS-003` | agent | `role-skills/waypoint-ops.md` | Waypoint | Operations Manager | 5th — after identity |
| `RS-004` | agent | `role-skills/bearing-analyst.md` | Bearing | Research Analyst | 5th — after identity |
| `RS-005` | agent | `role-skills/harbor-success.md` | Harbor | Client Success | 5th — after identity |
| `RS-006` | agent | `role-skills/content-engine.md` | Lumen | Content Production & Monetization | 5th — after identity |

### Compass — Strategic Advisor
**Keywords:** `compass` `strategic-advisor` `client-intake` `heartcor-assessment` `service-tier-recommendation` `discovery` `qualification` `consulting` `intake-questions` `tier-selection` `flow-scan` `coherence-sprint` `harbor-build`

### Atelier — Build Architect
**Keywords:** `atelier` `build-architect` `openclaw-configuration` `skill-files` `plugin-assembly` `blueprint-design` `tool-configuration` `technical-build` `agent-setup` `workflow-design` `automation-architecture`

### Waypoint — Operations Manager
**Keywords:** `waypoint` `operations-manager` `project-management` `milestone-tracking` `workflow-design` `timeline` `sprint-planning` `task-management` `delivery` `coordination` `status-reporting`

### Bearing — Research Analyst
**Keywords:** `bearing` `research-analyst` `market-research` `competitive-analysis` `data-synthesis` `industry-intelligence` `competitor-profiling` `trend-analysis` `similarweb` `sec-filings` `financial-data`

### Harbor — Client Success
**Keywords:** `harbor` `client-success` `onboarding` `relationship-management` `renewals` `referrals` `retention` `satisfaction` `check-ins` `upsell` `client-portal` `long-term-engagement`

### Lumen — Content Engine
**Keywords:** `lumen` `content-engine` `content-monetization` `short-form-video` `openclaw-pipeline` `claude-scripting` `capcut` `content-rewards` `pop-culture` `faceless-content` `tiktok` `youtube-shorts` `instagram-reels` `evergreen-content` `brand-campaigns` `passive-income` `content-production` `video-automation` `topic-clusters` `sprint-protocol`

---

## Reference Files

| ID | Type | File | Agent(s) | Description |
|---|---|---|---|---|
| `RF-001` | reference | `reference/heartcor-methodology.md` | Compass | HeartCor framework: Heart/Logic/Coherence dimensions, diagnostic questions, misalignment patterns |
| `RF-002` | reference | `reference/corcompass-service-tiers.md` | Compass, Harbor | Service tier definitions: Flow Scan, Coherence Sprint, Harbor Build |
| `RF-003` | reference | `reference/content-rewards-platform.md` | Lumen | Content Rewards platform briefing, campaign matching protocol, payout structure |
| `RF-004` | reference | `reference/content-production-stack.md` | Lumen, Atelier | OpenClaw + Claude + CapCut pipeline configuration, template specs, quality control |

### HeartCor Methodology
**Keywords:** `heartcor` `methodology` `heart-dimension` `logic-dimension` `coherence-dimension` `diagnostic` `misalignment` `emotional-intelligence` `operational-logic` `assessment` `client-evaluation` `consulting-framework`

### CorCompass Service Tiers
**Keywords:** `service-tiers` `flow-scan` `coherence-sprint` `harbor-build` `pricing` `tier-selection` `deliverables` `engagement-model` `consulting-packages` `conversion` `upsell`

### Content Rewards Platform
**Keywords:** `content-rewards` `brand-campaigns` `payout-per-view` `faceless-content` `ai-content` `clipping` `monetization` `campaign-matching` `creator-economy` `short-form-monetization` `passive-income` `brand-funded`

### Content Production Stack
**Keywords:** `content-production-stack` `openclaw-configuration` `claude-scripting` `capcut-templates` `clip-library` `source-management` `quality-control` `pipeline-architecture` `batch-processing` `tts-voiceover` `vertical-video` `automation`

---

## OpenClaw Skills Referenced

The following OpenClaw built-in and custom skills are referenced across the agent library:

| Skill ID | Skill Name | Used By | Category | Keywords |
|---|---|---|---|---|
| `OC-001` | `batch-claude-prompts` | Lumen | Content Production | `batch` `claude` `prompts` `scripting` `automation` |
| `OC-002` | `clip-library-matcher` | Lumen | Content Production | `clip-matching` `source-library` `video-selection` |
| `OC-003` | `capcut-template-runner` | Lumen | Content Production | `capcut` `video-assembly` `export` `captions` `tts` |
| `OC-004` | `multi-channel-scheduler` | Lumen | Distribution | `scheduling` `tiktok` `youtube` `instagram` `posting-cadence` |
| `OC-005` | `content-rewards-submitter` | Lumen | Monetization | `content-rewards` `campaign-submission` `brand-campaigns` |
| `OC-006` | `heartcor-intake-flow` | Compass | Client Intake | `intake` `heartcor` `assessment` `qualification` |
| `OC-007` | `blueprint-generator` | Atelier | Build | `blueprint` `skill-file` `agent-config` `openclaw` |
| `OC-008` | `similarweb-research` | Bearing | Research | `similarweb` `traffic-data` `competitive-analysis` |
| `OC-009` | `stock-analysis` | Bearing | Research | `stock` `financial-data` `sec-filings` `company-profile` |
| `OC-010` | `crm-contact-update` | Harbor, Waypoint | Operations | `crm` `contact` `notes` `relationship-management` |

---

## Topic Clusters (Content Engine)

Pre-loaded topic clusters for the Lumen Content Engine pipeline:

| Cluster ID | Name | Tier | Keywords |
|---|---|---|---|
| `TC-001` | Celebrity Feuds & Beefs | Evergreen | `celebrity` `feuds` `beef` `conflict` `drama` `pop-culture` |
| `TC-002` | Film Production History | Evergreen | `film` `movies` `behind-the-scenes` `production` `hollywood` `cinema` |
| `TC-003` | Music Drama & Industry | Evergreen | `music` `industry` `labels` `ghostwriting` `samples` `artist-drama` |
| `TC-004` | Award Show Moments | Evergreen | `awards` `oscars` `grammys` `emmys` `red-carpet` `speeches` |
| `TC-005` | TV Show Retrospectives | Evergreen | `tv` `television` `cancellations` `cast` `endings` `revivals` |
| `TC-006` | Cultural Anniversaries | Evergreen | `anniversaries` `throwback` `historical` `decades` `nostalgia` |
| `TC-007` | Ranking Debates | Trending Evergreen | `rankings` `lists` `debates` `best-of` `worst-of` `opinions` |
| `TC-008` | Throwback Compilations | Trending Evergreen | `throwback` `compilations` `forgotten-moments` `2000s` `2010s` |
| `TC-009` | Artist/Brand Origin Stories | Trending Evergreen | `origin-stories` `founding` `early-career` `pivotal-moments` `brand-history` |
| `TC-010` | AI Content (Campaign-Matched) | Campaign | `ai-content` `content-rewards` `brand-campaigns` `faceless` |
| `TC-011` | Lifestyle & Consumer (Campaign) | Campaign | `lifestyle` `consumer` `brand-campaigns` `content-rewards` |
| `TC-012` | Music & Audio (Campaign) | Campaign | `music` `audio` `licensed` `brand-campaigns` `content-rewards` |

---

## Quick Search Guide

**To find files for a specific agent:** Search the agent's codename (compass, atelier, waypoint, bearing, harbor, lumen).

**To find files for a specific task:** Search the task keyword (e.g., `intake`, `research`, `content-production`, `monetization`, `onboarding`).

**To find files for a specific platform:** Search the platform name (e.g., `tiktok`, `youtube`, `instagram`, `content-rewards`).

**To find files for a specific methodology:** Search the methodology name (e.g., `heartcor`, `blueprint`, `sprint-protocol`).

**To find all agent builds:** Filter by type `agent`.

**To find all reference files:** Filter by type `reference`.

**To find all training prompts:** Filter by type `prompt`.

---

## Load Order Summary

When initializing any CorCompass agent session, load files in this order:

```
1. core-identity/SOUL.md          (CI-001) — collective identity
2. core-identity/STYLE.md         (CI-002) — voice and formatting
3. core-identity/AGENTS.md        (CI-003) — operating principles
4. curriculum/CURRICULUM.md       (CU-001) — development protocol (training sessions only)
5. role-skills/[agent-name].md    (RS-00X) — domain expertise
6. reference/[relevant-file].md   (RF-00X) — task-specific reference (as needed)
```

---

*CorCompass is a protected series of Cor Infinitum LLC, a Texas Protected Series Limited Liability Company.*
