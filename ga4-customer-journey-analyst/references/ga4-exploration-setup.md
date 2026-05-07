# GA4 Exploration Setup Reference

Use this reference when giving concrete GA4 Explore setup instructions.

## Choose the exploration type

| User question | Recommended method | Why |
|---|---|---|
| What do users do before conversion? | Path Exploration | Shows event/page/channel nodes before a conversion ending point. |
| Where do users drop off in a known sequence? | Funnel Exploration | Measures step completion and drop-off in a defined journey. |
| Which channels/campaigns perform better? | Free-form Exploration | Compares dimensions and metrics in a table or pivot. |
| Do channels touch the same users? | Segment Overlap | Compares user membership across channel-based segments. |
| What does a specific user path look like? | User Explorer, if available | Supports QA or qualitative individual journey review. |
| Do users return or repeat over time? | Cohort Exploration | Evaluates retention, re-engagement, repeat purchase, or subscription behavior. |
| Which channels assist conversions? | Advertising > Attribution / Conversion paths, Path Exploration, or BigQuery | Shows conversion path/touchpoint patterns when available. |
| Do we need exact user-level sequencing? | BigQuery export | GA4 Explore is not sufficient for custom user-level path reconstruction. |

## Path Analysis setup

Purpose: analyze common paths before a conversion.

1. Go to **GA4 > Explore**.
2. Create a new Exploration and select **Path Exploration**.
3. Set the analysis direction:
   - Prefer **Ending point** when analyzing what happened before conversion.
   - Use the primary conversion event as the ending point: `purchase`, `generate_lead`, `form_submit`, `sign_up`, `trial_start`, `subscription`, `booking_complete`, `add_to_cart`, `begin_checkout`, or another key event.
4. Test multiple **Node type** views:
   - Event name.
   - Page path + query string.
   - Page title and screen name.
   - Session default channel group.
   - Session source / medium.
   - First user default channel group, if available and relevant.
5. Add useful segments:
   - Converted users or purchasers.
   - New users vs returning users.
   - Users with Paid Search sessions.
   - Users with Paid Social sessions.
   - Users with Organic Search sessions.
   - Users with Direct sessions.
   - High-value purchasers or qualified leads, if available.
6. Add filters when needed:
   - Event name equals the target conversion.
   - Country/region, device category, campaign, source/medium, or landing page.
   - Exclude internal traffic and test events if those are not already filtered.
7. Export CSV or provide screenshots with the date range, filters, segments, node type, and visible metrics.

Recommended analysis questions:

- What are the most common pre-conversion paths?
- Are paths concentrated in a few channels or pages?
- Does Direct or Paid Search frequently close journeys?
- Which upstream channels appear before Search/Direct conversion?
- Are paths unusually long or fragmented?
- Which pages/events repeatedly appear before conversion?

## Channel Overlap setup

Purpose: identify whether channels reach the same users.

1. Go to **GA4 > Explore**.
2. Create a new Exploration and select **Segment Overlap**.
3. Create user segments such as:
   - Users with Paid Search sessions.
   - Users with Organic Search sessions.
   - Users with Direct sessions.
   - Users with Paid Social sessions.
   - Users with Email sessions.
   - Users with Display or Video sessions.
   - Users with Affiliate or Referral sessions.
   - Users who converted.
   - Users who purchased.
   - New users.
   - Returning users.
4. Define each segment using session-level dimensions where possible, such as Session default channel group or Session source / medium.
5. Add supporting Free-form Exploration:
   - Dimensions: Session default channel group, First user default channel group, Session source / medium, Campaign, Device category, Country/region, Landing page.
   - Metrics: Total users, Active users, Sessions, Key events, Purchases, Revenue, Engagement rate, Transactions, Conversion rate if available or calculable.
6. Export overlap table or provide screenshots. Include date range and segment definitions.

Recommended analysis questions:

- Which channel pairs have the highest overlap?
- Is high overlap complementary reinforcement or duplicate reach?
- Do Paid Search and Direct jointly appear among many converted users?
- Does Paid Social introduce users who later convert through Search/Direct?
- Are retargeting, Affiliate, or coupon sources mostly touching already high-intent users?

## Media Touchpoint Contribution setup

Purpose: infer the role each channel plays in the journey.

Recommended methods:

- Path Exploration with conversion ending point.
- Segment Overlap with converted-user channel segments.
- Free-form Exploration by acquisition/session/campaign dimensions.
- Advertising > Attribution / Conversion paths if the property has access.
- BigQuery export for reliable user-level sequencing.

Recommended dimensions:

- First user default channel group.
- Session default channel group.
- Session source / medium.
- Session campaign.
- Google Ads campaign.
- Manual campaign name.
- Landing page.
- Event name.
- Date.
- Device category.
- New / established.

Recommended metrics:

- Users.
- New users.
- Sessions.
- Engaged sessions.
- Key events.
- Purchases.
- Revenue.
- Average purchase revenue.
- Conversion rate.
- Event count.
- Engagement rate.

Recommended analysis questions:

- Which channels drive first-time users?
- Which channels capture existing demand?
- Which channels close conversions?
- Which channels frequently assist but do not dominate last click?
- Which channels have high ROAS because they capture existing demand?
- Which channels should be evaluated with assisted contribution, new-user rate, engagement, or downstream lift?

## Funnel setup

Use Funnel Exploration when the journey has a known sequence, such as product view > add to cart > begin checkout > purchase, or landing page > lead form start > lead form submit.

Recommended steps:

1. Select **Funnel Exploration**.
2. Add steps using events or page paths.
3. Compare segments by Session default channel group, source/medium, campaign, device, new vs returning users, or landing page.
4. Use an open funnel for flexible entry or a closed funnel for strict sequence analysis.
5. Export step completion, abandonment, conversion rate, and segment comparisons.

## When to recommend BigQuery

Recommend BigQuery when the user needs:

- Exact user-level path sequencing.
- Session stitching logic beyond GA4 Explore.
- Custom attribution windows or attribution models.
- Channel overlap by users and sessions with precise timestamps.
- Deduplication by transaction ID or qualified lead ID.
- Path length distributions across full user histories.
- Brand vs non-brand search logic joined from ad platforms.
