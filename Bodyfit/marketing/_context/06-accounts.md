# Bodyfit — Account IDs & Platform Access

This file maps Bodyfit's advertising accounts across platforms. Claude Code should reference this file whenever pulling data via GoMarble AI MCP or any other platform integration to ensure data is always pulled from the correct account.

---

## Meta Ads

| Field | Value |
|---|---|
| **Account Name** | Bodyfit |
| **Account ID** | act_1106229700657129 |
| **Market** | Australia — NSW (8 locations) |
| **Currency** | AUD |

---

## Google Ads

| Field | Value |
|---|---|
| **Account ID** | 6825327749 |
| **Manager ID** | 7903984544 |
| **Market** | Australia |
| **Currency** | AUD |

When calling GoMarble `google_ads_run_gaql`, always pass **both** `customer_id: "6825327749"` and `manager_id: "7903984544"` — the account is managed and queries will fail without the manager_id.

---

## Looker Studio

| Field | Value |
|---|---|
| **Report Name** | Bodyfit Performance Dashboard |
| **Direct Link** | https://lookerstudio.google.com/reporting/0be31193-fe41-4b7f-a0b1-7d0db87dad81/page/p_fqffzarhtd |

---

## TikTok Ads

| Field | Value |
|---|---|
| **Account ID** | *(not currently active)* |

---

## Slack

| Channel | ID | Use |
|---|---|---|
| Bodyfit internal | C09VCEZEL14 | ✅ Send reports here |

---

## Website

| Field | Value |
|---|---|
| **Primary domain** | bodyfit.com.au |
| **CMS** | WordPress |

---

## CRM & ops tools

| Tool | Use |
|---|---|
| Salesforce | CRM / nurture flows |
| ClubFit | Club management, member app, access barcode |
| Mailchimp | Email (migrating to Salesforce Marketing Cloud) |

---

## Gym locations (NSW)

- Auburn
- Blacktown
- Emerton
- Glebe
- Marrickville
- Miranda — 522 Kingsway, Miranda NSW 2228 — 02 9531 6682
- Redfern
- Shellharbour

---

## Notes

- Always use `act_1106229700657129` when calling any GoMarble Meta tool for Bodyfit
- Always use `6825327749` when calling any Google Ads tool for Bodyfit
- Always use `C09VCEZEL14` when sending reports to the Bodyfit Slack channel
- This is a **lead generation** client — primary conversion event is `lead` (free trial sign-up)
- Google Ads "Conversions" includes both form starts AND form submits — disclose this in every report and, where possible, also show form-submit-only numbers
- **Current lead target:** 40 digital leads/day total (web + Meta + Google)
- Never default to another account — confirm against this file if unsure
