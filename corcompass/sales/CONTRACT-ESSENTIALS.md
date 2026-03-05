# CorCompass Contract Essentials
## Required Clauses for All Engagement Agreements
**Version 1.0 | March 2026**

**Keywords:** contract, legal, IP-ownership, liability, AI-output, data-handling, scope, revision, milestone-payment, compliance

---

## Overview

Every CorCompass engagement agreement must include the following clauses. These are non-negotiable and protect both CorCompass and the client from the unique risks of AI consulting engagements. Standard consulting agreements written for human service providers do not address these risks adequately.

This document is a reference guide for CorCompass internal use. It is not a legal document and does not constitute legal advice. All client contracts must be reviewed by a qualified attorney before execution.

---

## Required Clauses

### 1. Intellectual Property Ownership

**CorCompass retains ownership of:**
- All methodologies, frameworks, and agent configuration templates developed by CorCompass
- The CorCompass training curriculum, SOUL.md templates, SKILL.md files, and all internal documentation
- Any general-purpose skills or workflows that are not specific to the client's business

**Client owns:**
- Specific custom implementations built exclusively for the client's business
- Client-specific data, content, and configurations stored in the client's agent workspace
- Any deliverables explicitly designated as "client-owned" in the scope of work

**Rationale:** This structure allows CorCompass to reuse and improve methodologies across clients while ensuring clients have full ownership of their specific implementations.

---

### 2. AI Output Liability

**Required language:** "Client acknowledges that AI-generated outputs are probabilistic in nature and may contain errors, omissions, or inaccuracies. CorCompass does not warrant the accuracy, completeness, or fitness for purpose of any AI-generated content, analysis, or recommendation. Client is solely responsible for reviewing, validating, and approving any AI-generated output before acting upon it, particularly for decisions involving financial, legal, medical, or safety implications."

**Rationale:** AI models hallucinate. Clients must understand that all AI outputs require human review for critical decisions. This clause prevents liability for AI errors that the client acts upon without review.

---

### 3. Third-Party Platform Dependencies

**Required language:** "CorCompass's services depend on third-party platforms including but not limited to OpenClaw, Anthropic Claude, OpenAI, and other AI model providers. CorCompass is not liable for service interruptions, feature changes, pricing changes, or discontinuation of any third-party platform. In the event of a material change to a third-party platform that affects the services, CorCompass will notify the client within 5 business days and propose a remediation plan."

**Rationale:** OpenClaw, Claude, and other platforms can change their pricing, features, or terms at any time. This clause protects CorCompass from liability for events outside its control.

---

### 4. Data Handling and Privacy

**Required language:** "CorCompass will handle client data in accordance with applicable privacy laws, including [specific laws relevant to the client's industry and jurisdiction]. Client data will not be shared with third parties except as required to provide the services (e.g., AI model providers for processing). Client is responsible for ensuring that any data provided to CorCompass for use in AI systems complies with applicable privacy laws and does not include data for which the client does not have appropriate rights or consent."

**Industry-specific additions:**
- Healthcare clients: HIPAA Business Associate Agreement required
- Payment processing clients: PCI-DSS compliance acknowledgment required
- EU clients: GDPR Data Processing Agreement required

---

### 5. Scope of Work and Change Management

**Required language:** "The scope of work is defined in Exhibit A attached hereto. Any work outside the defined scope requires a written change order signed by both parties before work commences. Change orders will be priced at CorCompass's then-current hourly rate of $150/hour unless otherwise agreed in writing."

**Rationale:** Scope creep is the primary cause of unprofitable engagements. A clear scope definition with a formal change management process protects both parties.

---

### 6. Revision Scope

**Required language:** "Each deliverable includes a maximum of two (2) rounds of revisions. Additional revision rounds will be billed at $150/hour. A revision round is defined as a set of changes requested in a single written communication. Revision requests must be submitted within 10 business days of deliverable delivery; after this period, the deliverable is deemed accepted."

**Rationale:** Without revision limits, AI output refinement (prompt engineering, model tuning) can extend indefinitely. This clause sets clear boundaries.

---

### 7. Payment Terms and Milestone Structure

**Required language:** "Payment is structured as follows: (a) 25% of the total project fee is due upon contract execution; (b) 50% is due upon completion of the initial deployment and testing phase (approximately Day 14); (c) 25% is due upon final delivery and client sign-off (approximately Day 30). Monthly retainer fees are due on the first business day of each month. Invoices not paid within 15 days of due date are subject to a 1.5% monthly late fee. CorCompass reserves the right to suspend services for invoices more than 30 days past due."

---

### 8. Confidentiality

**Required language:** "Each party agrees to keep confidential all non-public information received from the other party in connection with this agreement, including but not limited to business strategies, client lists, pricing, and technical configurations. This obligation survives termination of the agreement for a period of three (3) years."

---

### 9. Termination

**Required language:** "Either party may terminate this agreement with 30 days written notice. In the event of termination, the client is responsible for all fees incurred through the termination date. CorCompass will provide a transition package including all client-owned configurations, data, and documentation within 10 business days of termination."

---

### 10. Limitation of Liability

**Required language:** "CorCompass's total liability under this agreement shall not exceed the total fees paid by the client in the 3 months preceding the claim. In no event shall CorCompass be liable for indirect, incidental, special, or consequential damages, including lost profits, even if advised of the possibility of such damages."

---

## Contract Review Checklist

Before sending any contract to a client, confirm:
- [ ] All 10 required clauses are present
- [ ] Scope of Work (Exhibit A) is specific, measurable, and includes explicit exclusions
- [ ] Payment amounts and milestone dates are correct
- [ ] Industry-specific additions (HIPAA, PCI-DSS, GDPR) are included if applicable
- [ ] Contract reviewed by qualified attorney (required for Apex tier; recommended for all tiers)
- [ ] Client has had at least 48 hours to review before signing
