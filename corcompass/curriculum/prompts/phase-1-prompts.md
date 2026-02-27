# Phase 1 Prompts — Deep Research

*Use these prompts in sequence to build the knowledge base for any CorCompass agent.*
*Replace all [BRACKETED] placeholders with your specific values before running.*

---

## Prompt 1.1 — Define the Agent Role

```
I'm building an expert AI agent for CorCompass, a luxury AI consulting firm, to serve in the role of [YOUR ROLE — e.g., "hospitality operations analyst"].

Help me define this role precisely by answering these questions in a structured format:

1. **Job Title:** What would this role be called at a high-end consulting firm? Give me the most accurate professional title.

2. **Core Function:** In one sentence, what does this person do all day?

3. **Top 5 Recurring Tasks:** List the 5 tasks this person performs most frequently, ranked by frequency. For each task, note:
   - What triggers it (what causes them to start this task)
   - What the finished output looks like
   - How long it typically takes a human expert

4. **Tools of the Trade:** What software, databases, APIs, spreadsheets, or platforms does someone in this role use daily?

5. **Decision Authority:** What decisions does this person make independently vs. what do they escalate? This tells us where the AI can act autonomously vs. where it should pause and ask.

6. **Quality Bar:** How do you know if this person's work is excellent? What do clients or senior partners check?

7. **Common Mistakes:** What do junior people in this role get wrong that seniors don't?

8. **CorCompass Fit:** How does this role serve CorCompass's mission of "Guided by Heart, Powered by Logic"? What is the emotional intelligence component of this role?

Format your response as a clean reference document I can save as the foundation for this agent.
```

---

## Prompt 1.2 — Research the Core Process

```
Research the complete professional workflow that an expert [JOB TITLE — e.g., "hospitality revenue manager"] follows when performing [PRIMARY TASK — e.g., "conducting a monthly revenue optimization review for a boutique hotel"].

I need this at an operational level — not theory, but what they actually DO in sequence. For each step, include:

- What specific actions they take
- What data or inputs they need at that step
- What tools or calculations they use
- What they're looking for (decision criteria, thresholds, benchmarks)
- What would cause them to stop and flag a problem
- What the output of that step looks like before moving to the next

Also cover:
- The typical order of operations and WHY that order matters
- Where experienced professionals deviate from the textbook process
- What shortcuts experts use that juniors don't know about
- How long each step typically takes
- The difference between a "quick scan" version and a "full analysis" version

Focus on 2024–2026 methodology. Include any recent changes in tools, data sources, regulations, or best practices.

I'm using this to build an automated expert agent, so precision and completeness matter more than brevity.
```

---

## Prompt 1.3 — Research Tools and Data Sources

```
Research every tool, data source, API, database, platform, and service that a professional [JOB TITLE] uses or could use when [PRIMARY TASK].

Organize into these categories:

**Primary Data Sources:**
- Where do they get their core input data?
- What's free vs. paid?
- What's the most authoritative source for each data type?

**Calculation & Analysis Tools:**
- What software do they use to run their analysis?
- What formulas, models, or frameworks are standard?
- Are there industry-standard templates?

**Reference & Benchmarking:**
- What databases do they check for benchmarks or comparables?
- What industry reports or indices do they reference?
- What government or regulatory sources are relevant?

**Output & Delivery:**
- What format do they deliver results in? (reports, spreadsheets, presentations, dashboards)
- What templates or formatting standards exist?
- What software generates the final deliverable?

**Automation & Integration:**
- What APIs exist that could feed data into this workflow?
- What can be automated vs. what requires human judgment?
- What MCP servers, web services, or connectors could an AI agent use to access this data?

For each tool or source: name, what it provides, URL if applicable, free/paid, and how it fits into the workflow.
```

---

## Prompt 1.4 — Research Decision Frameworks

```
Research the decision frameworks, rules of thumb, heuristics, and evaluation criteria that experienced [JOB TITLE] professionals use when [PRIMARY TASK].

I need two levels:

**Level 1 — Hard Rules (quantitative thresholds):**
- What specific numbers, ratios, scores, or benchmarks trigger a "yes," "no," or "investigate further" decision?
- What are the industry-standard thresholds for each metric?
- How do these thresholds vary by [RELEVANT VARIABLE — e.g., "property type, market tier, seasonality"]?
- What combinations of metrics matter? (e.g., "If A is good but B is bad, then...")

**Level 2 — Soft Judgment (qualitative assessment):**
- What do experienced professionals "sense" that can be articulated as rules?
- What patterns do they recognize that signal opportunity or danger?
- What questions do they ask themselves at each decision point?
- What do they weigh more heavily when metrics conflict?

**Risk Assessment Framework:**
- How do professionals categorize and rank different types of risk in this domain?
- What's an automatic disqualifier?
- What risks are acceptable and at what level?

**The Expert vs. Novice Gap:**
- What do experts check that novices skip?
- What do experts ignore that novices obsess over?
- What counterintuitive decisions do experts make that would surprise a beginner?

Present this as a structured decision tree or framework I can encode into an AI agent's instructions.
```

---

## Prompt 1.5 — Research Output Format Standards

```
Research the standard professional output format for a [DELIVERABLE TYPE — e.g., "strategic recommendations memo"] produced by a [JOB TITLE] when [PRIMARY TASK].

Cover:

**Document Structure:**
- What sections are included and in what order?
- What goes in each section? (be specific — not just "executive summary" but what an executive summary contains in this context)
- How long is each section typically?
- What's the total typical length?

**Formatting Standards:**
- What visual formatting is standard? (tables, charts, headers, color coding)
- What data is best presented as a table vs. narrative vs. chart?
- Are there industry-standard templates or formats?

**Tone & Language:**
- What tone is appropriate for this deliverable?
- What jargon is expected vs. what should be explained?
- How are recommendations framed? (direct, hedged, conditional)

**Required Elements:**
- What must ALWAYS be included regardless of the situation?
- What disclaimers, caveats, or qualifications are standard?
- What supporting evidence or citations are expected?

**What Separates Good from Great:**
- What makes a client or senior partner say "this is excellent work"?
- What are common formatting or presentation mistakes?
- What level of detail shows competence without being excessive?

Provide a detailed template/outline I can use as the basis for this agent's output format instructions.
```

---

## Prompt 1.6 — Research Edge Cases and Failure Modes

```
Research the edge cases, failure modes, common mistakes, and unusual situations that a [JOB TITLE] encounters when [PRIMARY TASK].

**Unusual Situations:**
- What scenarios break the standard workflow? (e.g., incomplete data, contradictory signals, unusual market conditions)
- How should each unusual situation be handled?
- What's the right response when the standard process doesn't apply?

**Common Mistakes:**
- What do even experienced professionals get wrong occasionally?
- What are the most costly mistakes in this domain?
- What mistakes are easy to make but hard to catch?

**Data Quality Issues:**
- What does bad, incomplete, or misleading input data look like?
- How should the agent handle missing data vs. corrupted data vs. contradictory data?
- What's the minimum data quality threshold to proceed vs. flag for human review?

**Ethical and Legal Boundaries:**
- What actions in this domain require human authorization?
- What information must never be shared or acted upon without verification?
- What regulatory or compliance considerations apply?

**Graceful Degradation:**
- When the agent can't complete the full workflow, what's the best partial output?
- How should the agent communicate limitations without undermining confidence?
- What's the escalation path when the agent is out of its depth?

Format as a structured reference I can encode into the agent's guardrails.
```

---

## Prompt 1.7 — Organize into Knowledge Files

```
I've completed research for a [JOB TITLE] agent across these areas:
- Core process
- Tools and data sources
- Decision frameworks
- Output format standards
- Edge cases and failure modes

Here are the research outputs:
[PASTE ALL RESEARCH OUTPUTS]

Now organize this into a clean, structured knowledge base. For each knowledge file:

1. Remove redundancy — if the same information appears in multiple research outputs, consolidate it
2. Resolve contradictions — if sources conflict, note the conflict and provide the most defensible position
3. Add structure — use headers, tables, and numbered lists to make the information scannable
4. Flag gaps — note any areas where the research is thin and additional research would improve the agent
5. Prioritize — mark the 20% of information that will drive 80% of the agent's quality

Output format: one clean markdown file per knowledge domain (process, tools, decisions, output-standards, edge-cases).
```
