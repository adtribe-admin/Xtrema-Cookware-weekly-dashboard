# [CLIENT BRAND] Dashboard — Refresh Procedure

This file is read by the scheduled Claude agent every Monday. The agent has access to the GoMarble MCP tools and to this GitHub repo (via `gh` / `git`).

> 📝 **Before first use**: fill in the five placeholders in the **Inputs** block below (brand, Meta ad account, Google customer ID, optional Google manager ID, and the GitHub repo path). Save. Then the weekly agent has everything it needs.

## Inputs

- **Brand**: Xtrema Cookware
- **Meta ad account**: `act_1597243657678825` (e.g. `act_1234567890`)
- **Google Ads customer**: `3271683076` (10 digits, no dashes), manager `` (blank)
- **Repo**: `adtribe-admin/Xtrema-Cookware-weekly-dashboard` (main branch, GitHub Pages)
- **Window**: pull a rolling 52-week window ending on yesterday.

## Steps the agent must perform

1. **Clone or pull the repo locally**:
   ```bash
   gh repo clone [INSERT_GITHUB_OWNER]/[INSERT_REPO_NAME] /tmp/dash || (cd /tmp/dash && git pull --rebase)
   ```

2. **Pull Meta weekly insights** via the GoMarble MCP tool `facebook_get_adaccount_insights`:
   - `act_id`: `[INSERT_META_ACCOUNT_ID]`
   - `level`: `account`
   - `time_increment`: `7`
   - `time_range`: `{"since": "<today minus 364 days>", "until": "<yesterday>"}`
   - `fields`: `["spend", "impressions", "reach", "clicks", "ctr", "cpm", "cpc", "frequency", "actions", "action_values", "purchase_roas", "video_thruplay_watched_actions"]`
   - **Important**: Meta paginates at 25 weeks per page. The agent MUST follow `paging.next` via `facebook_fetch_pagination_url` until exhausted.
   - For each weekly row, extract:
     - `spend`, `impressions`, `reach`, `clicks`, `ctr`, `cpm`, `cpc`, `frequency`
     - `purchases` = the `omni_purchase` entry in `actions` (fallback: `purchase`)
     - `revenue`  = the `omni_purchase` entry in `action_values` (fallback: `purchase`)
     - `roas`     = the `omni_purchase` entry in `purchase_roas`
     - Derive `cpa = spend / purchases` (or 0 if purchases==0)
     - `video_3s`   = the `video_view` entry in `actions` (Meta's 3-second video play count)
     - `thruplays`  = the `video_view` entry in `video_thruplay_watched_actions` (≥15s or full video, whichever shorter)
     - Derive `hook_rate = video_3s / impressions` (decimal 0..1; render as %)
     - Derive `hold_rate = thruplays / video_3s` (decimal 0..1; render as %)

3. **Pull Google Ads weekly metrics** via `google_ads_run_gaql`:
   - `customer_id`: `"[INSERT_GOOGLE_CUSTOMER_ID]"`, `manager_id`: `"[INSERT_GOOGLE_MANAGER_ID_OR_BLANK]"` (omit if blank)
   - Query:
     ```
     SELECT segments.week, metrics.cost_micros, metrics.impressions, metrics.clicks, metrics.conversions, metrics.conversions_value
     FROM customer
     WHERE segments.date BETWEEN '<since>' AND '<until>'
     ORDER BY segments.week ASC
     ```
   - **Note**: although the field name is `cost_micros`, this MCP returns `metrics.cost` in actual currency units. Use `metrics.cost` directly.

4. **Pull Google Ads impression-share** at the campaign level (impression share is not exposed on `customer`), then aggregate per week weighted by impressions:
   ```
   SELECT segments.week, metrics.impressions, metrics.search_budget_lost_impression_share, metrics.search_rank_lost_impression_share, metrics.search_absolute_top_impression_share, metrics.search_top_impression_share
   FROM campaign
   WHERE campaign.advertising_channel_type = 'SEARCH'
     AND segments.date BETWEEN '<since>' AND '<until>'
   ORDER BY segments.week ASC
   ```
   For each week, compute the impression-weighted average of the four shares across SEARCH campaigns.

5. **Build `data.json`** with the schema below and write it to the repo root. Weeks ordered newest first.
   ```json
   {
     "account": {
       "brand": "[INSERT_BRAND_NAME]",
       "meta_account_id":   "[INSERT_META_ACCOUNT_ID]",
       "meta_account_name": "[INSERT_META_ACCOUNT_DISPLAY_NAME]",
       "google_customer_id":  "[INSERT_GOOGLE_CUSTOMER_ID]",
       "google_manager_id":   "[INSERT_GOOGLE_MANAGER_ID_OR_BLANK]",
       "google_account_name": "[INSERT_GOOGLE_ACCOUNT_DISPLAY_NAME]"
     },
     "generated_at": "<ISO8601 UTC>",
     "weeks_count":  53,
     "date_range":   {"from": "<oldest_week>", "to": "<latest_week>"},
     "thresholds":   {"roas_meta_min": [INSERT_META_ROAS_TARGET], "roas_google_min": [INSERT_GOOGLE_ROAS_TARGET]},
     "weeks": [
       {
         "week_start": "YYYY-MM-DD",
         "meta":   { "week_start", "week_end", "spend", "impressions", "reach", "clicks", "ctr", "cpm", "cpc", "frequency", "purchases", "revenue", "roas", "cpa", "video_3s", "thruplays", "hook_rate", "hold_rate" },
         "google": { "week_start", "spend", "impressions", "clicks", "purchases", "revenue", "cpa", "roas", "cpm", "ctr", "cpc", "abs_top_pct", "top_pct", "budget_lost_pct", "rank_lost_pct" }
       }
     ]
   }
   ```

6. **Rebuild the dashboard**:
   ```bash
   cd /tmp/dash && python3 build.py
   ```

7. **Commit and push**:
   ```bash
   git -C /tmp/dash add data.json index.html
   git -C /tmp/dash commit -m "Refresh data through $(date -u +%Y-%m-%d)" || echo "no changes"
   git -C /tmp/dash push
   ```

8. **Sanity checks before pushing**:
   - `weeks_count` should be ≥ 50 and ≤ 53.
   - Latest week's date should be ≥ (today − 7 days).
   - No week should have both `meta == null` and `google == null`.
   - If any check fails, do NOT commit. Stop and report.

## Partial-week handling (handled by build.py automatically)

The dashboard distinguishes between *complete* and *partial* weeks:
- A week is **complete** if it started ≥ 7 days ago (i.e. `week_start <= today − 7 days`).
- A week is **partial** if `week_start > today − 7 days` (i.e. it's still in progress when the data was pulled).

`build.py` automatically:
- Picks the first complete week (newest-first) for all "Latest Week" KPI cards and the 4-week compliance check.
- Renders partial-week rows in tables with a "PARTIAL" tag next to the date.

You do NOT need to filter partial weeks out of `data.json` — include them. The HTML rendering layer flags them.

## What not to change

- Do not touch the design/style of `index.html` — `build.py` regenerates it from scratch each run.
- Do not edit `build.py` schema fields unless you are explicitly asked to add a new metric.
- KPI thresholds (`roas_meta_min`, `roas_google_min`) live in `data.json` and are read by `build.py`. To change them, edit `data.json` and re-run `build.py`.
