# Required Data Fields Reference

Use this reference to tell users what to export and to assess whether uploaded data is sufficient.

## Field groups

### Minimum fields for aggregate channel analysis

- Date or date range.
- Session default channel group or Session source / medium.
- Users or active users.
- Sessions.
- Key events or conversion count.
- Purchases or transactions, if ecommerce.
- Revenue, if ecommerce or monetized conversion.
- Campaign, if campaign-level interpretation is requested.

Supports: directional channel performance and basic demand capture vs conversion closer inference.

Does not support: exact path sequence, real user overlap, or assisted contribution.

### Minimum fields for Path Exploration export

- Path step, node, or sequence column.
- Node type definition: Event name, Page path, Page title, Session default channel group, or Session source / medium.
- Users or active users.
- Event count or step count.
- Conversion/key event count, if available.
- Purchases and revenue, if available.
- Ending point or starting point definition.
- Date range, filters, and segment definitions.

Supports: common pre-conversion path patterns and likely entry/mid/closing touchpoints.

Limitations: exported GA4 paths may be aggregated and may not allow exact user-level sequencing or custom attribution.

### Minimum fields for Segment Overlap export

- Segment names and definitions.
- Overlap user counts or percentages.
- Total users per segment.
- Converted users or purchasers segment, if conversion-specific overlap is requested.
- Date range and filters.

Supports: overlap diagnosis and duplicate-vs-complementary reach hypotheses.

Limitations: does not prove incremental lift or exact sequence.

### Minimum fields for media touchpoint contribution

- First user default channel group or first user source / medium.
- Session default channel group or session source / medium.
- Campaign or source/medium detail.
- Users and new users.
- Sessions and engaged sessions.
- Key events, purchases, or qualified leads.
- Revenue or lead value where available.
- Date and device category where relevant.
- Conversion path or path sequence if available.

Supports: role classification across acquisition, consideration, demand capture, closing, retention, and assisted contribution.

### Minimum fields for BigQuery event-level journey analysis

- `user_pseudo_id` or another user identifier.
- Session identifier, commonly `ga_session_id` from event parameters.
- `event_timestamp`.
- `event_name`.
- `event_date`.
- Traffic source fields, including available first-user, session, and collected traffic source values.
- Source, medium, campaign, default channel group if transformed.
- Page location, page path, page title, landing page if relevant.
- `transaction_id` or lead ID when applicable.
- Purchase revenue, lead value, or conversion value.
- Consent/tracking caveats if known.

Supports: user-level sequencing, path length, first/mid/last-touch classification, custom attribution, and exact overlap.

## Common field mapping assumptions

State assumptions explicitly when mapping fields:

| Uploaded field | Possible interpretation |
|---|---|
| `source_medium`, `source / medium` | Session source / medium unless labeled as first user. |
| `channel`, `default_channel_group` | Default channel group; verify whether it is session or first user scope. |
| `first_channel`, `first_user_channel` | First user default channel group. |
| `event_count` filtered to purchase | Purchase volume or purchase event count. |
| `conversions`, `key_events` | GA4 key events; verify the exact conversion event. |
| `revenue`, `purchase_revenue`, `transaction_revenue` | Ecommerce revenue; verify currency and tax/shipping inclusion. |
| `path`, `conversion_path`, `sequence` | Aggregated path string unless user-level IDs and timestamps are present. |
| `step_1`, `step_2`, `touchpoint_order` | Ordered path steps if the export preserves order. |

## Sufficiency checks

Use these checks before drawing conclusions:

- No user ID, session ID, or timestamp: cannot reconstruct exact user-level path sequence.
- Only channel-level revenue: cannot measure true overlap or assisted contribution.
- Only last-click channel: cannot evaluate upstream contribution.
- No first-user channel: acquisition role is uncertain.
- No event sequence: path analysis is directional only.
- No segment definitions in overlap screenshot: overlap interpretation is low confidence.
- No date range: trend and seasonality conclusions are not supported.
- No conversion event definition: conversion-quality interpretation is uncertain.
- No campaign/source detail: Brand vs Non-brand Search and retargeting/coupon incrementality cannot be assessed.
