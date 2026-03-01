# Reference — Content Production Stack

**Series:** CorCompass Protected Series — Cor Infinitum LLC  
**Maintained by:** Lumen (Content Engine Agent) + Atelier (Build Architect)  
**Version:** 1.0.0 — February 27, 2026  

---

## Stack Overview

The CorCompass Content Engine runs on three tools in sequence. OpenClaw is the orchestration layer that connects and automates the other two. No tool in this stack requires on-camera presence, manual editing, or real-time human supervision during production runs.

| Tool | Role | Human Touchpoint |
|---|---|---|
| **OpenClaw** | Orchestration — batches prompts, moves content through stages, manages scheduling | Configuration (one-time) + quarterly audit |
| **Claude** | Scripting — generates short-form scripts from topic cluster prompts | Sample review (10–20% of batch) |
| **CapCut** | Assembly — applies captions, voiceover, music, exports finished vertical video | Template setup (one-time) |

---

## OpenClaw Configuration

OpenClaw is the agent layer. It does not just run tools — it orchestrates the entire pipeline, makes decisions, and moves content through each stage without supervision.

### Required OpenClaw Skills for This Pipeline

The following OpenClaw skills must be configured before the pipeline runs:

**1. `batch-claude-prompts`**  
Runs a list of topic cluster prompts against Claude in sequence, collects the output scripts, and saves them to the production queue. Configured with the topic cluster list and the script template (hook / body / CTA format).

**2. `clip-library-matcher`**  
Matches each script to a source clip from the pre-loaded clip library. Selection criteria: 5–8 second clips, hook-compatible opening, royalty-free or transformation-cleared source. Outputs a clip assignment for each script.

**3. `capcut-template-runner`**  
Drops the matched clip and script into the pre-built CapCut template. Applies captions (from script), TTS voiceover, music bed, and exports the finished vertical short. Saves the export to the distribution queue.

**4. `multi-channel-scheduler`**  
Takes finished videos from the distribution queue and schedules them across configured channels. Supports TikTok, YouTube Shorts, Instagram Reels, and Pinterest Video. Configurable posting cadence (default: 1 video/day per channel).

**5. `content-rewards-submitter`**  
Monitors active Content Rewards campaigns, matches finished videos to qualifying briefs, and queues submissions. Requires bi-weekly human review to confirm campaign alignment before submission.

### OpenClaw Agent Configuration File (AGENTS.md excerpt)

```yaml
agent:
  name: lumen
  role: content-engine
  model: claude-3-5-sonnet
  skills:
    - batch-claude-prompts
    - clip-library-matcher
    - capcut-template-runner
    - multi-channel-scheduler
    - content-rewards-submitter
  params:
    scripts_per_session: 15
    clip_duration_min: 5
    clip_duration_max: 8
    hook_window_seconds: 2
    export_format: "9:16 1080x1920 H.264"
    review_sample_rate: 0.15
  schedule:
    production_sessions: "Mon/Wed/Fri 09:00"
    posting_cadence: "1/day/channel"
    campaign_scan: "every 14 days"
```

---

## Claude Scripting Configuration

Claude generates scripts from topic cluster prompts. The prompt template follows a consistent structure:

### Master Script Prompt Template

```
You are a short-form content scriptwriter specializing in pop culture retrospectives.

Write a 60-second script about: [TOPIC]

Format:
HOOK (first 5 words — must create immediate curiosity or tension):
[hook text]

BODY (45 seconds of content — 3–4 punchy facts or story beats):
[body text]

CTA (final 5 seconds — question or invitation to engage):
[cta text]

Rules:
- No filler phrases ("In this video we'll...")
- Every sentence must earn its place
- Historical facts only — no speculation
- End on a question or unresolved tension
```

### Topic Cluster Prompt Examples

**Celebrity Feuds:**
> "Write a 60-second script about the origin of the Mariah Carey and Jennifer Lopez feud — specifically what actually started it and why it lasted so long."

**Film Production History:**
> "Write a 60-second script about 10 wild facts about the making of Titanic that most people don't know — budget disasters, near-deaths, and behind-the-scenes chaos."

**Music Drama:**
> "Write a 60-second script breaking down why the Kanye and Drake beef actually started — the real timeline, not the public version."

**Throwback Compilations:**
> "Write a 60-second script about the most unhinged celebrity moments of 2009 — things people have completely forgotten happened."

---

## CapCut Template Configuration

CapCut handles final assembly. The pipeline uses pre-built templates that OpenClaw populates automatically.

### Template Specifications

| Element | Specification |
|---|---|
| **Aspect ratio** | 9:16 vertical |
| **Resolution** | 1080×1920 |
| **Frame rate** | 30fps minimum |
| **Export codec** | H.264 |
| **Caption style** | Bold, high-contrast, center-bottom position, 2–4 words per frame |
| **Caption timing** | Synced to TTS voiceover output |
| **Music bed** | -12dB under voiceover, trending audio or royalty-free |
| **Voiceover** | CapCut built-in TTS, neutral or energetic tone depending on topic cluster |
| **Opening frame** | Hook text on screen within 0.5 seconds of video start |

### Template Variants

Three template variants cover the primary content categories:

**Template A — Fast Cut (Celebrity Feuds, Music Drama)**  
Rapid cuts at 5-second intervals. High-energy music bed. Bold caption font. Designed for maximum retention on conflict-based content.

**Template B — Documentary (Film History, TV Retrospectives)**  
Slower cuts at 7–8 seconds. Cinematic music bed. Serif caption font. Designed for storytelling-based content.

**Template C — Compilation (Throwback, Rankings)**  
Mixed cut pace. Nostalgic or trending music bed. Clean sans-serif captions. Designed for list-format and compilation content.

---

## Source Library Management

The clip library is the raw material input for the pipeline. Lumen maintains a structured source library organized by topic cluster.

### Sourcing Guidelines

**Royalty-Free Sources:**
- Internet Archive (archive.org) — public domain footage, historical broadcasts
- Wikimedia Commons — public domain images and video
- Pexels / Pixabay — free stock video for B-roll

**Transformation-Cleared Sources:**
- YouTube clips used under commentary/criticism fair use doctrine (short clips, transformative context, non-commercial commentary)
- News broadcast clips used under news reporting fair use doctrine

**Avoid:**
- Full music videos (DMCA risk)
- Feature film scenes longer than 30 seconds
- Sports broadcast footage (highly litigated)
- Any clip from a platform with automated Content ID enforcement without transformation context

### Library Organization

```
/clip-library/
  /celebrity-feuds/
  /film-history/
  /music-drama/
  /award-shows/
  /tv-retrospectives/
  /throwback-compilations/
  /b-roll/
    /crowds/
    /cities/
    /abstract/
```

---

## Quality Control Checkpoints

The pipeline includes three automated quality checkpoints before a video enters the scheduling queue:

**Checkpoint 1 — Script Review (Human)**  
Sample 10–20% of each batch. Flag scripts that contain: unverified claims, potentially defamatory content, living persons in a negative context without documented source, or content that conflicts with active Content Rewards brief requirements.

**Checkpoint 2 — Export Validation (Automated)**  
OpenClaw verifies: correct aspect ratio, minimum resolution, audio levels within spec, caption sync within 0.2 seconds of voiceover, file size under platform limits.

**Checkpoint 3 — Quarterly Audit (Human)**  
Review a random sample of 20 videos from the past 90 days. Assess quality drift, caption accuracy, hook effectiveness, and platform performance metrics. Adjust topic clusters and template variants based on findings.

---

## Keywords

`content-production-stack` `openclaw-configuration` `claude-scripting` `capcut-templates` `clip-library` `source-management` `quality-control` `pipeline-architecture` `batch-processing` `tts-voiceover` `vertical-video` `export-settings` `fair-use` `royalty-free` `automation` `agent-configuration`
