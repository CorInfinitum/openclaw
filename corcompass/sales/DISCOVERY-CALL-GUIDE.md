# CorCompass Discovery Call Guide
## Consultative Diagnostic Framework
**Version 1.0 | March 2026**

**Keywords:** discovery-call, qualification, MEDDIC, BANT, sales-script, objection-handling, consultative-selling, B2B, SMB

---

## Purpose

The discovery call is a consultative diagnostic session, not a sales pitch. The goal is to understand the prospect's business deeply enough to determine whether CorCompass can deliver measurable value, and if so, to build the foundation for a proposal that resonates.

A discovery call that ends with the prospect saying "this is exactly what we need" is a successful discovery call, regardless of whether a proposal is sent that day.

---

## Pre-Call Preparation (30 minutes)

Before every discovery call, the Bearing Research Analyst agent prepares a brief covering:

1. **Company overview:** Industry, size, revenue range, years in operation, key products or services.
2. **Decision-maker profile:** Role, tenure, LinkedIn activity, any public statements about technology or operations.
3. **Industry context:** Current trends, challenges, and technology adoption patterns in the prospect's vertical.
4. **Competitive landscape:** What AI or automation tools are commonly used in this vertical.
5. **Hypothesis:** What is the most likely pain point driving the prospect's interest, based on available information?

This brief is loaded into the Compass Strategic Advisor agent's context before the call.

---

## Call Structure (60 Minutes)

### Opening (5 minutes)

Establish rapport and confirm the agenda. The opening sets the tone for the entire call.

Suggested opening: "Thank you for making time. The goal for today is to understand the business and the challenges driving interest in AI automation -- not to pitch anything. At the end of the call, both parties will have a clear picture of whether there is a fit, and what that might look like. Does that agenda work?"

### Metrics (10 minutes)

Establish the quantifiable business impact of the problem before discussing any solution.

**Core questions:**
- "What does a typical week look like for the team handling [the problem area]? Walk through the process step by step."
- "How much time per week is spent on [the problem]? What is that time worth in salary cost?"
- "What happens when [the problem] is not handled well? What does that cost the business?"
- "If this problem were solved completely, what would change for the business in the next 90 days?"

**Probe for specifics:** Vague answers ("it takes a lot of time") must be converted to numbers ("about 15 hours per week across three staff members, at $25/hour, so roughly $1,500/week or $78,000/year").

### Economic Buyer (5 minutes)

Confirm who has the authority to make this decision and who controls the budget.

**Core questions:**
- "Who else is involved in evaluating a solution like this?"
- "When a technology investment of this size is made, who is typically involved in the final decision?"
- "Is there a budget already allocated for this, or would this need to go through an approval process?"

**Stakeholder mapping:** Document every person mentioned. Identify the Economic Buyer (who signs the check), the Champion (who wants this to happen), and any potential blockers.

### Decision Criteria (10 minutes)

Understand what success looks like from the client's perspective before defining it from CorCompass's perspective.

**Core questions:**
- "What would need to be true for this engagement to be a clear win for the business in 90 days?"
- "How will the team know if this is working? What metrics will be tracked?"
- "What has been tried before to solve this problem? What worked and what did not?"
- "Are there any non-negotiables -- things that any solution must do or must not do?"

### Decision Process (5 minutes)

Map the internal approval workflow to avoid surprises at the closing stage.

**Core questions:**
- "Walk through how a decision like this typically gets made at the company."
- "What is the typical timeline from deciding to move forward to signing a contract?"
- "Are there any internal processes -- IT review, legal review, budget approval -- that would need to happen?"

### Identify Pain (15 minutes)

Go deep on the specific pain points. Use the 5 Whys technique to get to root causes.

**5 Whys example:**
- "The front desk is overwhelmed." Why? "Too many calls." Why? "Guests call for information that is already on the website." Why? "They cannot find it easily." Why? "The website is not organized well." Why? "No one has had time to update it."

Root cause: information architecture problem, not a staffing problem. The AI solution is a conversational interface that surfaces the right information instantly.

**Core questions:**
- "What is the single biggest operational headache right now?"
- "How long has this been a problem? What has been tried to fix it?"
- "What is the cost of not solving this problem in the next 12 months?"
- "Who is most affected by this problem on the team? How does it affect them?"

### Champion Identification (5 minutes)

Identify the internal advocate who will drive the decision internally.

**Core questions:**
- "Who on the team is most excited about solving this problem?"
- "Who would be the day-to-day point of contact for an engagement like this?"
- "Is there anyone on the team who has experience with AI tools or automation?"

### Next Steps (5 minutes)

Close the call with specific, time-bound next steps.

**Standard close:** "Based on what has been shared today, there is a clear fit for [specific CorCompass solution]. The next step is to put together a proposal that outlines the specific scope, timeline, and investment. That will be ready by [specific date]. Does that timeline work?"

If the prospect is not ready for a proposal: "It sounds like there are a few things to work through internally first. The next step is to schedule a follow-up call for [specific date] to revisit once [specific condition] has been resolved. Does that work?"

---

## Objection Handling

### "We are not ready for AI yet."

Response: "That is actually one of the most common things heard from businesses that end up being the best candidates for this. 'Not ready' usually means one of two things: either the team is not sure what AI can realistically do, or there is a concern about the disruption of implementing something new. Which of those resonates more?"

### "We cannot afford it right now."

Response: "That is fair. Can the cost of not solving [the problem] be quantified? Earlier it was mentioned that [the problem] costs approximately [X] per year. The question is whether the investment in solving it is less than the cost of continuing to live with it."

### "We tried AI tools before and they did not work."

Response: "That is really useful context. What specifically did not work? Was it the tool itself, the implementation, or the ongoing management?" (Listen carefully -- this reveals the real objection and the specific gap CorCompass can address.)

### "We need to think about it."

Response: "Of course. What specific questions or concerns would be most helpful to address before making a decision? And what is the timeline for making a decision -- is there a specific date by which this needs to be resolved?"

### "We are looking at other options."

Response: "That makes sense. What other options are being evaluated? What would make one option clearly better than another for the business?" (This reveals the decision criteria and competitive positioning.)

---

## Post-Call Protocol

Within 2 hours of the call:
1. Update CRM with all notes, stakeholder map, pain points, decision criteria, and next steps.
2. Calculate the technical readiness score (see `SALES-FUNNEL.md` Stage 3).
3. Send a follow-up email summarizing key takeaways and confirming next steps.
4. If proceeding to proposal, brief the Compass Strategic Advisor agent with the discovery call notes.

---

## Technical Readiness Assessment

| Dimension | Score 1 | Score 3 | Score 5 |
|-----------|---------|---------|---------|
| Data quality | No structured data | Some structured data | Clean, accessible data |
| Tech stack | No API access | Some integrations possible | Full API access |
| Team capacity | No dedicated owner | Part-time owner | Dedicated owner |
| AI literacy | No prior experience | Some tool usage | Active AI users |
| Integration complexity | 5+ systems, no APIs | 3-4 systems, some APIs | 1-2 systems, full APIs |

**Score < 12:** High-risk engagement. Additional scoping session required before proposal. Flag for Compass Strategic Advisor review.

**Score 12-18:** Standard engagement. Proceed to proposal with standard scope.

**Score 19-25:** Ideal client. Fast-track proposal. Consider Momentum or Apex tier recommendation.
