# Analysis Output Templates

Use these templates for final analysis, management summaries, monthly reports, QBRs, campaign reviews, and media performance reviews.

## Standard customer journey analysis output

Use this structure by default when analyzing uploaded data or providing final recommendations.

### 1. Executive Summary

Provide 3-5 bullets with the most important findings. Include confidence level when data is incomplete.

### 2. Analysis Context

Include:

- Analysis objective.
- Data type used: Path Exploration export, Segment Overlap export, Free-form report, BigQuery event-level data, screenshot, etc.
- Date range, if available.
- Conversion event or key event.
- Main dimensions and metrics.
- Data limitations and mapping assumptions.

### 3. Customer Journey Overview

Summarize:

- Main entry channels or first-touch indicators.
- Common middle touchpoints.
- Common closing channels.
- Path length or short-vs-long path pattern.
- High-value path patterns.
- Unusual or risky path patterns.

### 4. Path Findings

| Path Pattern | Volume / Revenue / Conversion Evidence | Interpretation | Business Implication |
|---|---:|---|---|
| Example: Paid Social > Direct > Purchase | Users/conversions/revenue from uploaded data | Paid Social likely introduced or warmed users; Direct closed | Do not judge Paid Social only by last-click revenue; test assisted contribution |

### 5. Channel Overlap Findings

| Channel Pair | Overlap Level | Interpretation | Risk / Opportunity | Recommended Action |
|---|---:|---|---|---|
| Example: Paid Search + Direct | High | Strong shared high-intent audience | Could be healthy capture or over-crediting of closing channels | Split Brand vs Non-brand; inspect previous touchpoints |

### 6. Media Touchpoint Contribution

| Channel | Journey Role | Contribution Type | Evidence | Suggested KPI | Optimization Recommendation |
|---|---|---|---|---|---|
| Example: Paid Social | Demand Generator / Assisted Contributor | Upstream influence | High early-path presence and overlap with Search/Direct | New users, engaged sessions, assisted paths | Evaluate prospecting separately from retargeting |

### 7. Attribution Caveats

Explain relevant limitations:

- GA4, ad platform attribution, and last-click can disagree.
- Direct is a mixed bucket.
- Brand Search can close existing demand.
- Upper-funnel channels can be under-credited by last-click.
- Aggregate data cannot prove user-level sequence or incrementality.

### 8. Recommended Actions

Make recommendations concrete. Examples:

- Create separate Brand vs Non-brand Search views.
- Compare First user default channel group vs Session default channel group.
- Build Segment Overlap for converted users only.
- Review retargeting frequency and audience exclusions.
- Separate prospecting vs retargeting Paid Social/Display campaigns.
- Use assisted contribution, new-user rate, and engagement for upper-funnel channels.
- Export BigQuery event-level data for exact path sequencing.
- Rebuild Path Exploration with the conversion event as ending point.

## GA4 Exploration guidance output

When the user asks how to create an Exploration, use:

### 1. Your Analysis Goal

Restate the goal in practical language.

### 2. Recommended Exploration Types

List primary and supporting methods, such as Path Exploration, Segment Overlap, Free-form, Funnel, Attribution / Conversion paths, or BigQuery.

### 3. GA4 Setup Steps

Provide numbered steps:

1. Go to GA4 > Explore.
2. Create a new Exploration.
3. Choose Technique.
4. Add dimensions.
5. Add metrics.
6. Create segments.
7. Set filters.
8. Set starting point or ending point.
9. Set node type.
10. Export CSV or screenshot.

### 4. Fields to Export

List dimensions and metrics needed for the specific goal.

### 5. How I Will Analyze It

Explain that analysis will cover path pattern, channel role, overlap level, demand generation vs demand capture, attribution caveats, and optimization recommendations.

### 6. Caveats / When BigQuery Is Needed

State limitations and when user-level event export is needed.

## Monthly report / QBR condensed format

Use when the user asks for a management-ready summary:

1. **What changed** — major journey/channel shifts.
2. **What it means** — implications for demand generation, demand capture, closing, and retention.
3. **What to do next** — 3-7 prioritized actions.
4. **Risks and caveats** — attribution limitations and data gaps.
