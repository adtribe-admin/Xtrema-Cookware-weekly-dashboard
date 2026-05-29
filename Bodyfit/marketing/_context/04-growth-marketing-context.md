# Bodyfit — Growth Marketing Context

## Active channels

- **Meta Ads** (Facebook + Instagram) — primary paid lead driver
- **Google Ads** — search + display, scaling rapidly
- **Organic social** — 8 location-specific Instagram profiles, 12k+ followers each
- **SEO / local search** — 8 local pages, Google Business Profiles, organic
- **Email (Mailchimp)** — current data source, migrating to Salesforce Marketing Cloud
- **Google Reviews** — review management layer

**Not currently active:** TikTok, paid search beyond Google, OOH.

## Primary KPIs

| KPI | Current | Target |
|---|---|---|
| Daily digital leads (web + Meta + Google) | — | **40 / day** |
| Weekly Meta leads | ~50 | — |
| Weekly Google leads | ~16–25 | growing |
| Meta Cost per Lead | ~$49–$57 | lower + stable |
| Google Cost per Lead | ~$24 | maintain |
| New members/month | ~700 | 1,000+ |
| Digital share of new joins | ~35% | ≥40% by FY26 |
| Meta CPA | >A$120 | A$70 |

## Meta Ads strategy (full-funnel)

### TOF — Awareness
- **Objective:** Awareness / maximise reach
- **Audience:** Advantage+ with controls — 7km pin-drop radius per gym, exclude current/past members via custom audiences, layer first-party signals
- **Creative:** Persona-aligned short-form video anchored in the four narrative pillars. Minimum 5 variants per campaign (1 per persona).
- **CTA:** None that feels salesy — let them see themselves in the ad

### MOF — Consideration
- **Objective:** Engagement / Video Views (optimised for ThruPlays)
- **Audience:** Custom audiences ONLY — retarget TOF video viewers + page engagers. Turn off Advantage+.
- **Creative:** Social proof — review screenshots, video testimonials, micro-influencer content

### BOF — Conversion
- **Objective:** Advantage+ Leads (with Pixel + CAPI)
- **Audience:** Advantage+ with controls + custom audience layering (MOF engagers, website visitors)
- **Creative:** Meta Instant Form with custom qualifying questions ("What are you most interested in?") → routed to Salesforce nurture flows
- **Additional BOF segments:** Retarget site visitors who didn't submit, leads who submitted but didn't show, trial users who didn't convert

## Google Ads strategy

- **Primary event:** Form starts + form submits (both currently counted as conversions)
- **Note for reporting:** Always disclose that "Conversions" and "Cost per Conversion" include both form starts AND form submits. When possible, also break out form submits only.
- Strong CTR (12%+) — indicates high search intent
- Continue keyword + creative optimisation
- Recent addition of static creatives is positively impacting performance
- Most efficient channel on CPL at present (~$24)

## Location-level targeting

| Location | Recommended radius | Notes |
|---|---|---|
| Auburn | 7km | Strong Pilates driver |
| Blacktown | 7km | Original location, 60%+ male |
| Emerton | 7km | Scale candidate — needs location-specific creative |
| Glebe | 7km | Balanced gender, efficient — scale candidate |
| Marrickville | 7km | Balanced gender, efficient — scale candidate |
| Miranda | 7km | Strong Pilates driver |
| Redfern | 4km | Dense urban — tight radius |
| Shellharbour | 10km | Lower density, wider radius |

Creative should reflect each location's dominant persona mix.

## Rotating offer calendar (12-month plan)

| Month | Offer | Pillar |
|---|---|---|
| Aug | Your Pace Pass — 2 free sessions over 2 weeks | Community / Flexibility |
| Sept | No-Pressure Promise — full refund if cancel within 30 days | Flexibility |
| Oct | Choose Your Trial — 3 visits / 2 people / 7 days | Flexibility |
| Nov | Train for Good / Movember — $10 donation/new join | Purpose |
| Dec | 2-Week Intro Pass — 2 weeks for $10 | Flexibility |
| Jan | Local Legends + Scarcity — double trial for first 20 locals | Community |
| Feb | 2-for-1 Trial — Valentine's | Community |
| Mar | Train for Good / IWD — $10 donation/new join | Purpose |
| Apr | 3-Day Flexi Pass — 3 visits in April | Flexibility |
| May | Train to Win — 3 workouts in 10 days → win 3 months free | Competition |
| Jun | 5-Visit Pass — 5 visits for $25 | Flexibility |
| Jul | Ultimate Local Legend Pack — 3 workouts → prize draw | Community |

## Referral program — "Stronger Together"

**New-join perk:** $0 joining fee + free fitness/body scan + 50% off first month.

| Tier | Criteria | Reward |
|---|---|---|
| Local Advocate | 1–2 joins/yr | 50% off next month + $25 fuel bar credit |
| Local Champion | 3–5 joins or 5 nominations | 100% off next month OR 1 free PT + merch bundle + $100 fuel bar credit |
| Local Ambassador | 6+ joins or 10 nominations | 10% revenue share + unlimited membership + content collab budget |

**Target referral CAC:** ≤ A$55.

## SEO / local strategy

- Top-3 Google local pack + LLM mentions for all 8 locations within 12 months
- Weekly location-specific pages and FAQ content (e.g. "Does Bodyfit Miranda have a rowing machine?", "Best gyms in Auburn with a crèche")
- LocalBusiness + HealthClub + FAQPage schema
- Disavow toxic backlinks; acquire high-authority local backlinks
- Target keyword types: commercial, navigational-competitor (e.g. "anytime fitness miranda"), generic ("gym with creche")

### Top branded search terms (monthly)
- bodyfit miranda (1.3K)
- bodyfit auburn (1.3K)
- bodyfit blacktown (1.0K)
- bodyfit redfern (880)
- bodyfit marrickville (720)
- bodyfit near me (720)
- bodyfit emerton (590)
- bodyfit glebe (480)
- bodyfit shellharbour (390)

## Sales journey redesign

**Old (problematic):** Daily call barrage first week, weekly calls thereafter → negative reviews.

**New (target):** 1 phone call + 1 voicemail + 1 personalised SMS within 15 minutes of form submission, via Marketing Cloud. Auto-respond with digital pass. Escalate to human only when ready.

## Tech stack

**Current:** WordPress (site), ClubFit (club management + app), Salesforce (CRM), Meta Ads (Pixel + CAPI), Mailchimp (email), Google Analytics (partial).

**Proposed:** n8n (automation), Postgres/Supabase with pgvector (CDP + vector DB), LangChain (RAG), Referral Factory (referral engine), BigQuery + Looker Studio (dashboarding), A/B testing + heatmaps + GTM.

## Reporting cadence

- **Weekly performance report** — Meta + Google, location breakdown, posted to internal Slack channel
- Monthly leadership huddle
- Quarterly lobby-screen infographic (local gym-level stats)

## Execution roadmap

- **Q1 (Jul–Sep 25):** Launch TOF/MOF, select 3 monthly offers, frontend dev complete, design partner program, brand voice Custom GPT + AI blog generator
- **Q2 (Oct–Dec 25):** Integrate LTV audiences, full site launch, Referral Factory setup, CDP build, speed-to-lead voice AI
- **Q3 (Jan–Mar 26):** Community + business partnerships, churn model
- **Q4 (Apr–Jun 26):** Strategic alliances, Member Concierge

## Main competitors

### National chains
Anytime Fitness, Fitness First, Goodlife Health Clubs, Jetts Fitness, Snap Fitness, Plus Fitness, Fernwood Fitness, Body Fit Training (BFT — different brand, often confused), F45 Training, Orangetheory.

### Local (per suburb) — top 3 per location
- **Miranda:** Anytime Fitness, Gold's Gym, EMF Performance
- **Glebe:** King Beats, Fitness 247, Plus Fitness
- **Blacktown:** Fitness 247, Club Lime, Anytime Fitness
- **Auburn:** Planet Fitness, Anytime Fitness, Snap Fitness
- **Marrickville:** One Playground, Strive Fitness, At 137 Health Club
- **Redfern:** NCIE, FoxFit, Elouera Tony Mundine
- **Emerton:** Anytime Fitness, Iron Gym, Ozone
- **Shellharbour:** *(to be added)*

## Reviews / reputation priority issues

Fix first (per review audit):
1. Membership cancellation difficulty
2. Maintenance / air-con (Miranda specifically)
3. Communication gaps
4. "Hidden" access fees
5. Aggressive phone calls

**Policy:** No negative review goes unanswered. Official Reddit account to be created.
