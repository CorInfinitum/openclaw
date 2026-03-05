# CorCompass SEO Strategy
## Pillar-Cluster Architecture and GEO Framework
**Version 1.0 | March 2026**

**Keywords:** SEO, content-strategy, pillar-cluster, GEO, AI-search, local-SEO, keyword-research, schema-markup, technical-SEO, Google-Business-Profile

---

## Strategic Context

The SEO landscape for AI consulting agencies has shifted fundamentally in 2025-2026 due to the rise of LLM-powered search (Google AI Overviews, Perplexity, ChatGPT search). Generative Engine Optimization (GEO) -- optimizing for inclusion in AI-generated search responses -- is now as important as traditional keyword ranking.

The CorCompass SEO strategy addresses both traditional search and GEO through a pillar-cluster content architecture, technical SEO hardening, and local SEO optimization.

---

## Keyword Architecture

### Layer 1 -- Vertical-Specific Pain Point Keywords (Highest Intent)

These keywords target prospects who are actively searching for solutions to specific problems. Lowest competition, highest conversion rate.

**Hospitality vertical:**
- "AI automation for hotel front desk"
- "AI guest communication system"
- "automated hotel inquiry response"
- "AI concierge for boutique hotels"

**Professional services vertical:**
- "AI assistant for law firm billing"
- "automated client follow-up for consultants"
- "AI admin automation for accounting firms"
- "AI workflow automation for professional services"

**Purpose-driven SMB vertical:**
- "AI automation for nonprofit operations"
- "AI tools for small business efficiency"
- "automated workflows for growing businesses"

### Layer 2 -- Service Category Keywords (Medium Intent)

These keywords target prospects who are researching AI consulting services. Medium competition, medium conversion rate.

- "OpenClaw consulting agency"
- "AI agent setup service"
- "custom AI workflow automation"
- "AI consulting for small business"
- "done-for-you AI automation"
- "AI agent management service"

### Layer 3 -- Thought Leadership Keywords (Low Intent, Brand Building)

These keywords target researchers, potential clients in early awareness stage, and referral partners. Low conversion but high brand-building value.

- "AI agent memory architecture"
- "OpenClaw security hardening"
- "B2B AI consulting pricing"
- "how to set up OpenClaw"
- "AI automation ROI for SMBs"

---

## Pillar-Cluster Content Architecture

### Pillar 1: AI Automation for Hospitality

**Pillar page:** "The Complete Guide to AI Automation for Hotels and Hospitality Businesses"

**Cluster articles (8-12):**
- "How AI Can Handle Hotel Guest Inquiries 24/7"
- "AI Concierge Systems: What Boutique Hotels Need to Know"
- "Reducing Front Desk Workload with AI: A Case Study"
- "AI Automation for Restaurant Operations: A Practical Guide"
- "The ROI of AI in Hospitality: Calculating the Business Case"
- "OpenClaw for Hotels: Setup and Configuration Guide"
- "AI Guest Communication: Best Practices for Hospitality"
- "Automating Hotel Check-In and Check-Out with AI"

### Pillar 2: AI Automation for Professional Services

**Pillar page:** "AI Automation for Professional Services Firms: The Complete Playbook"

**Cluster articles (8-12):**
- "How Law Firms Are Using AI to Reduce Non-Billable Time"
- "AI Client Follow-Up Automation for Consultants"
- "Automating Billing and Invoicing with AI: A Guide for Accountants"
- "AI Research Assistant for Professional Services: Setup and Use"
- "The Business Case for AI in Professional Services: ROI Analysis"
- "AI Workflow Automation for Consulting Firms"
- "Client Communication Automation: Best Practices for Service Firms"
- "OpenClaw for Professional Services: Configuration Guide"

### Pillar 3: AI Automation for Purpose-Driven SMBs

**Pillar page:** "AI Automation for Small Businesses: Scale Impact Without Scaling Headcount"

**Cluster articles (8-12):**
- "AI Tools for Nonprofit Operations: A Practical Guide"
- "How Small Businesses Are Using AI to Compete with Larger Competitors"
- "AI Automation for E-Commerce: From Order Management to Customer Service"
- "The Small Business Owner's Guide to AI Agents"
- "AI Workflow Automation: A Step-by-Step Guide for SMBs"
- "Measuring AI ROI for Small Businesses: Metrics That Matter"
- "AI and Data Privacy for Small Businesses: What to Know"
- "Getting Started with AI Automation: A Beginner's Guide for SMBs"

---

## Technical SEO Requirements

### Server-Side Rendering

The CorCompass website is built as a React SPA. SPAs are inherently difficult for search engines to crawl because content is rendered client-side. All public-facing pages must be converted to SSR or SSG before the public launch.

**Implementation options:**
- Vite SSR plugin for the current stack
- Migrate public-facing pages to Next.js or Astro
- Use a prerendering service (Prerender.io) as an interim solution

### Schema Markup

Schema markup is required for AI Overview inclusion. Minimum required schemas:

| Page | Schema Type |
|------|-------------|
| Homepage | Organization, LocalBusiness |
| Service pages | Service |
| Blog/article pages | Article, BlogPosting |
| FAQ section | FAQPage |
| Case study pages | Article |
| About page | Organization, Person |

### Core Web Vitals

| Metric | Target | Current Status |
|--------|--------|----------------|
| Largest Contentful Paint (LCP) | < 2.5s | To be measured |
| First Input Delay (FID) | < 100ms | To be measured |
| Cumulative Layout Shift (CLS) | < 0.1 | To be measured |
| Page load time | < 3s | To be measured |

### Sitemap and Robots.txt

- XML sitemap submitted to Google Search Console
- Robots.txt configured to allow all public pages and block admin/API routes
- Canonical tags on all pages to prevent duplicate content issues

---

## Local SEO

### Google Business Profile

The Google Business Profile (GBP) is the highest-ROI local SEO investment for CorCompass's Dallas-area target market.

**Required GBP optimizations:**
- Complete business information (name, address, phone, website, hours)
- Service categories mapped to CorCompass's tier structure
- Weekly posts with client success metrics or industry insights
- Photo gallery with team photos and office images
- Q&A section populated with common client questions
- Systematic review collection process (see below)

### Review Collection Process

Reviews are collected at two points in the client lifecycle:
1. **Day 30 (post-onboarding):** "The onboarding is complete. If the experience has been positive, a Google review would be greatly appreciated. Here is the direct link: [GBP REVIEW LINK]"
2. **90-day check-in:** "The engagement has been running for 90 days. If the results have been positive, a Google review with specific metrics (e.g., 'reduced admin time by 10 hours/week') would be very helpful for other businesses evaluating CorCompass."

Target: 2 new Google reviews per month minimum.

---

## Generative Engine Optimization (GEO)

For inclusion in AI-generated search responses (Google AI Overviews, Perplexity, ChatGPT), content must be:

1. **Authoritative and specific:** AI search engines prefer content with specific data, named sources, and clear expertise signals. Every article must include at least 3 specific statistics with sources.

2. **Structured for extraction:** Use clear headings, tables, and lists that AI models can extract and summarize. The pillar-cluster architecture naturally supports this.

3. **Schema-marked:** FAQPage and HowTo schema markup significantly increases the likelihood of AI Overview inclusion.

4. **Cited and linked:** Content that cites authoritative sources (academic papers, industry reports, government data) is more likely to be included in AI-generated responses.

5. **Updated regularly:** AI search engines favor recently updated content. All pillar pages must be reviewed and updated quarterly.
