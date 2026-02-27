# Phase 3–5 Prompts — Plugin, Validation, and Scaling

---

## PHASE 3: BUILD THE PLUGIN

### Prompt 3.1 — Generate Plugin Structure

```
I've built a SKILL.md for a [JOB TITLE] agent named [AGENT-NAME]. I want to package it as an OpenClaw plugin.

Here is the SKILL.md:
[PASTE SKILL.MD]

Create the complete plugin structure:

1. **Plugin directory layout** — show the full file tree
2. **Plugin manifest** — the configuration file that registers the plugin with OpenClaw
3. **Global instructions file** — instructions that apply to every interaction with this agent, reinforcing the CorCompass identity and STYLE.md voice
4. **Folder instructions** (if applicable) — instructions for when the agent is working in specific directories

The plugin should feel like a CorCompass professional, not a generic AI assistant. Embed the SOUL.md identity principles into the global instructions.
```

---

### Prompt 3.2 — Write Slash Commands

```
I'm building slash commands for my [AGENT-NAME] plugin. The agent's primary skill is [PRIMARY SKILL DESCRIPTION].

For each of these workflows, write a complete slash command file:

**Primary command:** /[prefix]:[primary-command]
- Purpose: [WHAT THIS COMMAND DOES]
- Input: [WHAT THE USER PROVIDES]
- Output: [WHAT THE AGENT DELIVERS]
- Workflow: [BRIEF DESCRIPTION OF THE STEPS]

**Secondary command:** /[prefix]:[secondary-command]
- Purpose: [WHAT THIS COMMAND DOES]
- Input: [WHAT THE USER PROVIDES]
- Output: [WHAT THE AGENT DELIVERS]

Each slash command file should:
1. State the command's purpose in the first line
2. Define what input the agent expects
3. List the exact steps the agent will follow
4. Specify the output format
5. Include error handling for common failure cases
6. End with a self-assessment prompt the agent runs before delivering

Name commands intuitively — what a user would naturally type to trigger this workflow.
```

---

### Prompt 3.3 — Write Global and Folder Instructions

```
Write the global instructions file for my [AGENT-NAME] OpenClaw plugin.

**Agent identity:** [AGENT-NAME] is a CorCompass [JOB TITLE] agent. It operates under the CorCompass brand identity (SOUL.md) and voice guide (STYLE.md).

**Global instructions must:**
1. Establish the agent's identity and role in the first paragraph
2. Reference the SOUL.md and STYLE.md files for identity and voice
3. State the agent's primary domain and what it will and will not do
4. Define the escalation protocol (when to ask vs. proceed)
5. Embed the CorCompass quality standard (actionable, specific, calibrated, branded)
6. List the three-tier boundaries (always do / ask first / never do)

**Tone:** The instructions should read like an onboarding document for a new CorCompass employee — professional, clear, and imbued with the brand's values.

Here is the agent's SKILL.md for reference:
[PASTE SKILL.MD]
```

---

## PHASE 4: INSTALL AND VALIDATE

### Prompt 4.1 — Install and Validate

```
I've built a complete plugin for my [AGENT-NAME] agent. Before I install it, I want you to audit the structure.

Here are all the plugin files:
[PASTE ALL PLUGIN FILES]

Please:

1. **Audit the structure:**
   - Check that all SKILL.md files are properly formatted
   - Check that all slash command files are syntactically correct
   - Check that all reference file pointers resolve to actual files
   - Check that the global instructions are consistent with SOUL.md and STYLE.md
   - Report any structural issues

2. **Validate the identity:**
   - Does the agent speak in the CorCompass voice?
   - Are the CorCompass vocabulary terms used correctly?
   - Are the three-tier boundaries (always do / ask first / never do) clearly defined?

3. **Validate the workflow:**
   - Is the step-by-step process complete and unambiguous?
   - Are the decision criteria specific enough to act on?
   - Are the output format specifications detailed enough to produce consistent results?

4. **Report and fix:**
   - List every issue found
   - Provide the corrected version of each file with issues
   - Confirm the plugin is ready for installation
```

---

### Prompt 4.2 — First Full Test Run

```
Let's do a full test run of my [AGENT-NAME] plugin.

**Test task:**
[DESCRIBE A REAL, REALISTIC TASK — be specific with actual details, not placeholders]

**Run the full workflow:**
1. Use the [PRIMARY SKILL] skill
2. Follow every step in the SKILL.md process
3. Apply all decision frameworks from the reference files
4. Run the quality checklist
5. Generate the final deliverable in the specified output format

**After delivery, provide a self-assessment:**
- Which steps from the SKILL.md did you execute? (list them)
- Which steps did you skip or modify? Why?
- Where did you lack data and how did you handle it?
- What would improve this output?
- Does this output meet the CorCompass quality standard (actionable, specific, calibrated, branded)?

I'll review the output and give you feedback for Phase 5 refinement.
```

---

## PHASE 5: REFINE AND SCALE

### Prompt 5.1 — Post-Review Refinement

```
I've run [NUMBER] tasks through my [AGENT-NAME] skill. Here's my review:

**What's working well (KEEP):**
[LIST WHAT YOU LIKED]

**What needs improvement (FIX):**
[LIST SPECIFIC ISSUES WITH EXAMPLES]

**What's missing (ADD):**
[LIST THINGS THAT SHOULD BE THERE]

**What's excessive (REMOVE or REDUCE):**
[LIST THINGS TO CUT]

**Instructions:**
1. Update the SKILL.md to address every point above
2. Update any reference files that need changes
3. Show me the changes as a before/after for each modification
4. If any change might break other parts of the workflow, flag it
5. After changes, re-run the quality checklist against the updated skill to confirm nothing was lost

Here's my current SKILL.md:
[PASTE CURRENT SKILL.MD]
```

---

### Prompt 5.2 — Add a New Skill

```
I have a working [AGENT-NAME] plugin with a primary skill for [PRIMARY TASK]. I want to add a new skill to expand what this agent can do.

**New Skill:**
- Name: [SKILL-NAME]
- Purpose: [WHAT THIS SKILL DOES]
- Trigger phrases: [WHEN SHOULD THIS ACTIVATE]
- Input: [WHAT THE USER PROVIDES]
- Output: [WHAT THE DELIVERABLE LOOKS LIKE]

**Consistency requirements:**
- Use the same CorCompass voice and tone as the primary skill
- Reference the same benchmarks and thresholds from existing reference files where applicable
- Follow the same escalation rules
- The output should feel like it came from the same agent

**Create:**
1. A complete SKILL.md file for this new skill
2. A slash command file to trigger it
3. Any new reference files it needs (that don't already exist)
4. Suggestions for how this skill should interact with or reference existing skills

Here's my primary SKILL.md for reference:
[PASTE PRIMARY SKILL.MD]
```

---

### Prompt 5.3 — Design Multi-Step Automated Workflows

```
I want to design an automated multi-step workflow for my [AGENT-NAME] plugin that handles [COMPLEX TASK].

**The workflow should:**

When I trigger /[prefix]:[command], the agent should:

1. **Step 1:** [FIRST ACTION]
2. **Step 2:** [SECOND ACTION]
3. **Step 3:** [THIRD ACTION]
4. **Step 4:** [FOURTH ACTION]
5. **Step 5:** [FINAL ACTION — always ends with a deliverable]

**Parallel execution:** Steps [WHICH STEPS] can run simultaneously. Steps [WHICH STEPS] must be sequential because they depend on prior results.

**Decision points:** At Step [NUMBER], if [CONDITION], then [BRANCH A] instead of continuing. [DESCRIBE CONDITIONAL LOGIC]

**Error handling:** If [SPECIFIC FAILURE], then [HOW TO HANDLE — skip, flag, escalate, or use fallback].

**Create:**
1. A slash command file that orchestrates this workflow
2. Any modifications needed to existing skills to support this workflow
3. A skill file for any new capability needed
4. A workflow diagram (in text/ASCII) showing execution order, parallelism, and decision points
```

---

### Prompt 5.4 — Weekly Performance Review

```
It's time for a weekly performance review of my [AGENT-NAME] agent.

**This week's usage:**
- Number of tasks run: [NUMBER]
- Tasks that produced excellent output: [LIST OR COUNT]
- Tasks that needed corrections: [LIST WHAT WENT WRONG]
- Tasks I had to redo manually: [LIST AND EXPLAIN WHY]

**Specific feedback from this week:**
[PASTE ANY NOTES YOU TOOK — be specific about what went wrong and when]

**Based on this feedback:**

1. **Diagnose:** What patterns do you see in the failures? Is it a data issue, a process issue, a judgment issue, or a formatting issue?

2. **Prescribe:** For each pattern, propose a specific change to the SKILL.md, reference files, or commands that would fix it.

3. **Prioritize:** Rank the changes by impact — what single change would produce the biggest improvement?

4. **Implement:** Make the top 3 changes to the skill files. Show me exactly what changed.

5. **Predict:** Based on these improvements, what should I watch for next week to confirm the fixes are working?

Here's my current SKILL.md:
[PASTE OR REFERENCE CURRENT SKILL.MD]
```

---

## BONUS PROMPTS

### Convert an Existing Workflow to a Skill

```
I have a task I do manually and regularly. I want to turn it into a CorCompass OpenClaw skill.

**The task:** [DESCRIBE WHAT YOU DO]

**My current process (step by step):**
1. [STEP 1]
2. [STEP 2]
3. [STEP 3]
[CONTINUE AS NEEDED]

**Tools I currently use:** [LIST]

**My preferences and rules:**
[LIST YOUR PERSONAL RULES AND THRESHOLDS]

**Create:**
1. A complete SKILL.md that replicates my exact process
2. A slash command to trigger it
3. Recommendations for connectors that would make it more automated
4. Suggestions for improvements I might not have thought of (things an AI can do that I can't easily do manually)

Make the skill sound like a CorCompass professional, not a generic AI assistant.
```

---

### Build a Skill from a Job Description

```
I found this job description for the role I want my CorCompass agent to fill. Using this as the starting point, build me a complete skill.

**Job Description:**
[PASTE THE FULL JOB DESCRIPTION]

**Instructions:**
1. Extract every task, responsibility, and skill mentioned
2. Research the professional methodology for the top 3 most important tasks
3. Identify which tasks are automatable by AI vs. which require human judgment
4. For the automatable tasks, write a complete SKILL.md that covers the full workflow
5. For tasks requiring human judgment, write those as "escalation points" where the agent pauses and asks
6. Create a prioritized roadmap: which skill should I build first, second, third?

Focus on tasks that are: high-frequency (done often), process-driven (follow clear steps), and high-value (save significant time or reduce errors).

The resulting agent should speak in the CorCompass voice and embody the HeartCor methodology.
```

---

### Clone an Expert's Process from an Interview or Article

```
I have content from an expert in [NICHE] who describes their exact process for [TASK]. I want to turn their methodology into a CorCompass skill.

**Source content:**
[PASTE THE TRANSCRIPT, ARTICLE, OR NOTES]

**Instructions:**
1. Extract the expert's process into numbered steps
2. Identify any implicit knowledge they assume but don't state explicitly
3. Fill in those gaps with standard industry practice
4. Convert their casual language into precise, executable instructions
5. Add quantitative thresholds where they use vague terms (e.g., if they say "a good return," define what number that means)
6. Identify their personal preferences vs. industry standard (note both)
7. Write a complete SKILL.md based on their methodology
8. Flag anything that might be outdated or specific to their situation

The resulting skill should capture their expertise in a form the agent can reliably execute, expressed in the CorCompass voice.
```
