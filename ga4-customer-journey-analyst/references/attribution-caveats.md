# Attribution Caveats

Use these caveats when interpreting GA4 customer journey, channel overlap, and media contribution data.

## Core caveats

- GA4 attribution, ad platform attribution, and last-click attribution may produce different answers because they use different scopes, attribution windows, identity logic, modeling, and conversion definitions.
- Last-click revenue is not the same as true media contribution.
- Platform-reported attribution can over-credit the platform's own media because it may use different lookback windows, view-through logic, modeled conversions, or cross-device assumptions.
- Aggregate reports can show directional patterns but cannot replace user-level path sequencing.
- User-level BigQuery data improves sequencing but still depends on consent, cookie persistence, identity stitching, tagging quality, and event implementation.

## Channel caveats

### Direct

Direct should be treated as a mixed bucket. It can include true direct navigation, bookmarks, returning users, dark social, untagged campaigns, app/email leakage, cookie loss, cross-device gaps, and brand demand created elsewhere. Do not call Direct “free growth” without checking prior touchpoints and returning-user behavior.

### Paid Search

Paid Search, especially Brand Search, often captures existing demand and closes conversions. Separate Brand vs Non-brand Search where possible. Non-brand Search can create incremental acquisition for generic/category queries, but high last-click ROAS alone does not prove demand generation.

### Paid Social, Display, and Video

These channels are often under-credited by last-click because their role may be discovery, awareness, or consideration. Evaluate them with first-user share, new-user rate, engagement, assisted paths, path inclusion, and downstream Search/Direct conversion patterns.

### Affiliate, coupon, and loyalty partners

These sources may be valuable, but they require incrementality checks. Late-stage coupon or loyalty touchpoints may intercept users who were already likely to convert. Separate content/editorial partners from coupon/toolbar/loyalty partners if possible.

### Retargeting

Retargeting can assist consideration or simply re-hit users with existing intent. Review audience definitions, recency windows, frequency, exclusions, and overlap with Direct, Brand Search, Email, and Affiliate.

### Email and SMS

Email and SMS often represent retention or re-engagement rather than new demand creation. Evaluate them separately for lifecycle stage, returning-user share, repeat purchase, conversion quality, and fatigue.

## How to phrase confidence

Use confidence qualifiers:

- **High confidence** when user-level IDs, timestamps, conversion events, traffic-source fields, and revenue/conversion IDs are available.
- **Medium confidence** when GA4 Path Exploration, Segment Overlap, or Attribution reports include clear date ranges, segments, and metrics.
- **Low confidence** when only screenshots, last-click reports, or aggregate channel revenue are available.

## Recommended next steps when attribution is unclear

- Split Brand vs Non-brand Search.
- Compare First user channel with Session channel.
- Build converted-user Segment Overlap.
- Separate prospecting vs retargeting campaigns.
- Add campaign/source/medium and landing page detail.
- Export BigQuery event-level data.
- Run geo, holdout, audience exclusion, or incrementality tests for retargeting, affiliates, and upper-funnel media.
