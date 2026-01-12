---
description: Analyze a company to identify their Ideal Customer Profiles (ICPs) - buyer personas, verticals, and tiers
---

# ICP Analysis

Use this skill when: user asks to "analyze ICPs", "identify target customers", "who should [company] sell to", or any request to understand buyer profiles for a business.

---

## Input Gathering

Before analyzing, collect:

1. **Company name** (required)
2. **Website** (required - primary research source)
3. **Product/service description** (optional - will research if not provided)
4. **Existing customers** (optional - helpful for pattern recognition)

If the user doesn't provide website or description, use web search to find the company first.

---

## Research Phase

### Step 1: Website Analysis

Fetch the company website and extract:

- **Products/Services**: What exactly do they sell?
- **Value proposition**: What problem do they solve?
- **Pricing signals**: Enterprise, SMB, consumer?
- **Case studies/testimonials**: Who are their current customers?
- **Industries mentioned**: What verticals do they serve?
- **Company sizes**: Startup, mid-market, enterprise?
- **Job titles**: Who do they market to?

### Step 2: Market Context

Search for:

- Competitors and their customers
- Industry reports or analyses
- Reviews and customer mentions
- LinkedIn company page (employee count, industry)

### Step 3: Pattern Recognition

Look for signals:

- **Direct fit**: Companies that obviously need this product
- **Adjacent fit**: Companies with similar needs but different context
- **Expansion opportunities**: New markets or use cases
- **Anti-patterns**: Who would NOT be a good fit

---

## ICP Framework

Build a 4-tier structure:

### Tier 1: Direct Buyers (Highest Priority)

Companies with:
- Immediate, obvious need for the product
- Clear budget authority
- Short sales cycle potential
- Exact product-market fit

**Example criteria to define:**
- Industry vertical
- Company size (employees, revenue)
- Tech stack or infrastructure
- Specific pain points
- Decision-maker titles

### Tier 2: Strong Fit (High Priority)

Companies with:
- Strong need, may require some education
- Adjacent use cases
- Likely buyers with longer cycle
- Good fit with minor customization

### Tier 3: Potential Buyers (Medium Priority)

Companies with:
- Broader market appeal
- Need exists but not urgent
- May require more nurturing
- Cross-sell or upsell potential

### Tier 4: Long-shot (Lower Priority)

Companies with:
- Diversification opportunity
- Emerging need
- Future potential
- Experimental fit

---

## Exclusion Criteria

Define who NOT to target:

### Automatic Exclusions

| Category | Why Exclude |
|----------|-------------|
| Wrong industry | No product fit |
| Wrong size | Below/above ideal customer size |
| Wrong geography | Can't serve their market |
| Wrong stage | Too early/late for their needs |
| Competitors | Conflict of interest |
| DIY solutions | Build vs buy preference |

### Exclusion Keywords

List specific keywords/patterns that indicate non-fit:
- Industry terms that suggest wrong vertical
- Company name patterns (e.g., "consulting" if selling to product companies)
- Product categories that don't overlap

---

## Scoring System (0-5)

| Score | Definition | Criteria |
|-------|------------|----------|
| **5** | Hot Lead | Direct fit + buying signals + contact available |
| **4** | High Priority | Strong fit + clear need + reachable |
| **3** | Standard | Good fit + some indicators |
| **2** | Low Priority | Uncertain fit OR missing info |
| **1** | Minimal | Weak connection, keep for reference |
| **0** | Exclude | No fit OR can't reach |

### Scoring Modifiers

| Modifier | Score Impact |
|----------|--------------|
| Recent funding | +1 |
| Hiring for relevant roles | +1 |
| Competitor customer (churn opportunity) | +1 |
| Direct contact available | +1 |
| No website or contact info | -1 |
| Generic email only (info@) | -0.5 |

---

## Decision-Maker Titles

For each tier, identify relevant titles to target:

### Executive (strategic deals)
- CEO, Founder, President, Owner
- CTO, CIO, COO, CFO
- VP of [relevant function]

### Manager (operational deals)
- Director of [function]
- Head of [function]
- [Function] Manager

### Practitioner (bottoms-up adoption)
- Senior [role]
- Lead [role]
- [Function] Specialist

---

## Output Formats

### Option 1: Methodology Document

Generate a markdown document like:

```markdown
# ICP Methodology for [Company]

## Overview
[Brief description of the company and their product]

## Tier Definitions

### Tier1_[Name] (Highest Priority)
**Score: 4-5**

[Description of who belongs here]

| Criteria | Examples |
|----------|----------|
| [Signal 1] | [Company types] |
| [Signal 2] | [Company types] |

**Why Priority:** [Business rationale]
**Decision Makers:** [Titles to target]

### Tier2_[Name] (High Priority)
...

## Exclusion Criteria
[Categories and keywords to skip]

## Scoring System
[Customized scoring with modifiers]

## Enrichment Priority
[Which tiers to enrich first and what to look for]
```

### Option 2: Structured Data

Output as structured data for CSV import:

```csv
tier,tier_name,description,criteria,examples,decision_makers,priority_score_range
1,Direct_Buyers,Companies with immediate need,[criteria],[examples],[titles],4-5
2,Strong_Fit,Adjacent use cases,[criteria],[examples],[titles],3-4
...
```

### Option 3: Both

Generate methodology doc AND structured data.

---

## Quality Checklist

Before delivering:

- [ ] All 4 tiers defined with clear criteria
- [ ] Exclusion criteria are specific (not generic)
- [ ] Scoring modifiers are relevant to this business
- [ ] Decision-maker titles match the buying process
- [ ] Examples are concrete, not theoretical
- [ ] Output format matches what user requested

---

## Example Analysis

For a B2B SaaS project management tool:

**Tier1_TechStartups**: VC-backed startups (50-500 employees) with engineering teams, using modern stack, hiring PMs
**Tier2_ScaleUps**: Growing companies (500-2000) consolidating tools, have existing PM solution
**Tier3_Enterprise**: Large companies (2000+) with complex approval processes, long sales cycles
**Tier4_Agencies**: Service businesses with project-based work, smaller budgets

**Exclusions**: Solo consultants, very early stage (<10 employees), industries with specialized PM needs (construction, film)

---

*This skill is generic - works for any company, not just Performance Leather.*
