# Bodyfit Marketing Workspace

This is the marketing team workspace for Bodyfit — an independent, community-focused Australian gym chain with 8 locations across NSW, offering 24/7 access, group fitness, personal training, crèche, fuel bar and sauna under one all-in-one weekly membership.

## Workspace Structure

```
_context/        Brand foundation files — load these before producing any output
_sop/            Standard operating procedures for marketing workflows
_templates/      Reusable output templates
ads/             Finished ad copy and creative briefs
pages/           Landing page and web copy
presentations/   Pitch decks and presentations
reports/         Performance reports and analysis
research/        Market research, competitor analysis, audience insights
seo/             SEO content and keyword work
social/          Social media copy and content calendars
```

## Core Rules

### 1. Always load brand context first
Before producing any output, read the relevant files from `_context/`. At minimum:
- `_context/01-brand-context.md` — brand positioning, audience, business metrics
- `_context/03-brand-voice-guide.md` — tone, voice pillars, do/don't examples

Load additional context files when directly relevant to the task:
- `_context/02-brand-style-guide.md` — visual identity, colours, typography, photography rules
- `_context/04-growth-marketing-context.md` — funnel strategy, audience targeting, KPIs
- `_context/05-product-offerings.md` — full service catalogue, offers, ad copy quick reference
- `_context/06-accounts.md` — account IDs, Looker URL, Slack channels

### 2. Follow the brand voice without exception
Bodyfit speaks like a supportive, community-focused local — warm, encouraging, inclusive, down-to-earth. Never corporate, never bro-speak, never pushy. Locals training locals. "For Locals. For Good." is the pilot positioning line. Check the voice guide before writing any copy.

### 3. Save outputs to the right folder
Finished work goes in the output folder that matches the content type. Do not leave outputs in `_context/`, `_sop/`, or `_templates/`.

### 4. Follow SOPs when they exist
Before starting any workflow, check `_sop/` for a matching procedure.

### 5. Use templates as starting points
Check `_templates/` before building a new output from scratch.

### 6. Dual-channel reporting
Bodyfit runs BOTH Meta Ads and Google Ads. Weekly reports must cover both channels in the established format (see `.claude/skills/weekly-report/references/weekly-template.md`). Location-level breakdown is required for Meta.

### 7. Visual / creative rules
Use real gym footage, real members, diverse bodies (including adaptive members and LGBTQIA+ members where authentic). Avoid generic stock imagery and "ladies vs blokes" defaults.

## Skills and Agents

### Keep skills brand-agnostic
Skills define workflow and process only. Never bake Bodyfit-specific details (brand name, voice, audience, metrics) into a skill file. Skills must pull brand context at runtime by reading `_context/` files. This keeps them reusable across brands.

## Key Brand Facts (for quick reference — always verify against `_context/` files)

| Property | Value |
|---|---|
| Market | Australia — NSW (8 gym locations) |
| Category | Independent health club / gym chain |
| Business type | Lead generation (subscription memberships) |
| Primary conversion | Free trial sign-up ("2-Day Free Pass") |
| Locations | Auburn, Blacktown, Emerton, Glebe, Marrickville, Miranda, Redfern, Shellharbour |
| Current Meta CPA | > A$120 |
| Target Meta CPA | A$70 |
| Paid-media CAC benchmark | A$70–90 |
| Current new members/month | ~700 |
| Stage 1 target | 1,000+ new members/month |
| Daily lead target (digital) | 40 leads/day (web + Meta + Google) |
| Tagline (pilot) | "For Locals. For Good." |
| Current tagline | "Got It In One" (under review) |
| Agency | indstrai (Andrew D'Ambrosio) |
