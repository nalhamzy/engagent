# Engagent — Platform Expansion Decision Brief

**Date**: 2026-09-06
**Question**: apply the Engagent Instagram idea to another platform (X? YouTube?) and pick the version that earns real money.
**Full research + sources**: `IdealIntelligenceWebTeam/research/market-trends/2026-09-06-engagent-platform-expansion.md`

---

## The finding

The reusable asset is not "Instagram." It is the engine:

> OAuth into an official API → ingest an inbound public message stream → classify by **commercial
> intent** → draft a reply grounded in the **Business Brain** → approvals queue + audit log →
> Arabic-first.

That engine has been built **twice** already — Engagent (Instagram) and `apps/tawasul` (WhatsApp
Cloud API, multi-tenant, EN/AR + RTL, same classify → ground → approve → escalate loop). The next
build must be a **channel adapter on a shared engine**, not a third silo.

Two things Engagent owns that do not need to be re-earned, and that should decide the next platform:

- **Meta App Review already passed**, with server-side token storage
- **Compliance surface already live** — privacy policy, support page, Meta data-deletion callback
  and status lookup

Staying inside the Meta ecosystem inherits both.

## The trap

"AI replies to your comments" is a **commodity on every platform**. Verified price floors
(2026-09-06): Google reviews **$10** (Reply Champion, RightResponse AI, Easy-Peasy.AI) · FB/IG ad
comments **$19** (Rypl, MyComments.io $29, FeedGuardians $39) · YouTube comments **$9.90**
(CommentFinder; replient.ai ~€49; free native YouTube Studio) · app store reviews **$49** (Appbot;
AppFollow free for 2 apps) · X replies **$29** (Tweet Hunter; Fireply $69–129).

Porting Engagent to a new platform at $19–49/mo is a price war against 4–6 funded incumbents on
their home turf. **Change who buys it or what it is priced against — never just the platform.**

## The three wedges nobody has priced

1. **Arabic / Gulf-native.** Every incumbent is English-first, US-first. GCC digital ad spend is
   **$12.4B in 2026, +19% YoY** (Saudi ~48%, UAE ~35%); MENA social commerce ~**$9.92B**; **79% of
   MENA consumers** have bought a product discovered on social. Dialect handling (Khaleeji, Egyptian,
   Levantine) is hard and unserved. The operator is in Muscat with an Omani CR.
2. **Revenue attribution, not moderation.** Everyone sells "hours saved moderating" → $19/mo.
   Nobody sells "we recovered N buying-intent messages worth ~$X" → $99–499/mo. Same tech, **5–10× the price.**
3. **Comments under *paid ads*.** The advertiser already paid $1–5 to generate that comment. An
   ignored buying-intent comment under an ad is a purchased lead thrown away. Price anchors to ad
   spend (1–3%), not to "a SaaS tool."

## Recommendation

| # | Build | What it is | Pricing | $100k ARR needs |
|---|---|---|---|---|
| 1 | **`adcatch`** | Paid-ad comment revenue agent — Meta + TikTok ads, Arabic-first, recovered-revenue reporting | $99 / **$299** / $799 | **28 customers** |
| 2 | **`tubelead`** | YouTube comment → lead capture for high-ticket course/coaching creators (the YouTube port, done right) | $79 / **$199** / $499 | 45 customers |
| 3 | `storereply` | App Store + Google Play review agent, grounded in release notes | $29 / $79 / $199 | 112 customers |
| — | **Consolidate** | Merge Engagent + tawasul into one Arabic-first Gulf commerce inbox; ship `adcatch` as a channel adapter | — | — |

## Do not build

- **X / Twitter — decline.** Since 2026-02-06 X is pay-per-use only for new developers (no free
  tier, Basic closed and auto-migrated 2026-06-01, Pro deprecated 2026-08-14). $0.005/post read,
  $0.015/post created, and **$0.20 per post containing a link** — a lead-capture agent's core action
  is replying *with* a link, so the one thing you monetize is the most expensive call on the platform
  (~$88/customer/mo COGS, underwater below ~$120/mo). Plus reply-ranking now favours paying accounts,
  and X carries the lowest commercial intent of any stream screened.
- **Generic YouTube comment manager.** Six incumbents, a $9.90 floor, free native moderation, and
  `comments.insert` at 50 quota units against a 10,000-unit/day project quota = **200 replies/day
  across all tenants**. Only the lead-capture reframing survives — and because it replies to just the
  1–3% of comments with buying intent, ~100 channels fit inside the default quota. The constraint
  *selects for* the high-value positioning.
- **TikTok organic.** No public API to read, hide, delete, or reply to comments outside the ads
  context; the Research API is read-only and academics-only. Not buildable — reach TikTok through
  its ads surface, which is what `adcatch` does.
- **Google Business Profile reviews — parked.** Rich at the top (Birdeye $299–449/location) but
  commoditized at $10 at the bottom and bundled in the middle. Only defensible as an Arabic + Gulf
  multi-location *channel* of the unified inbox. Revisit once `adcatch` has 10 paying customers.

## First two actions

1. File the **Meta App Review** request for ads-comment scopes and the **YouTube Data API quota
   extension** audit on the same day. Both are multi-week external clocks; everything else is faster
   than they are. Filing them first costs nothing and takes both off the critical path.
2. Instrument the **recovered-revenue report** before the first agency demo — it is the entire sales
   pitch for `adcatch`, and it is what moves the price from $29 to $299.
