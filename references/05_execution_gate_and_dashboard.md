# Module 05: Execution Gate & Dashboard

**Purpose:** Draft the schema and page copy, stop at a human review gate, then build a single-screen dashboard.

Nothing in this module publishes anything.

---

## 1. JSON-LD: Defer to the Schema Risk Protocol

The source summary suggests generating a broad "digital business card" of schema types. Do not follow that. The schema rules in [`kirby-technical-aeo`](../../kirby-technical-aeo/SKILL.md), "Phase 4: Schema Risk De-escalation Protocol", override it. That protocol is written for penalty and drop recovery. Here, its "Retain Unassailable Entity Core" list is the baseline for all new markup, and its full de-escalation steps apply when the domain has a traffic drop or a structured-data warning (see "Check before delivery"). Read that section before you write any markup.

**Allowed (identity and structural schema only)**

- `Organization` or `Person`, with verified legal name, address and contact details. Phase 4 keeps these two types and no others.
- `sameAs` arrays that link to real profiles the owner controls.
- Breadcrumbs.
- Article author markup that matches the visible byline.

**Not allowed**

- `AggregateOffer`, price ranges or other offer markup written to win rich results.
- Third-party review aggregates or star ratings copied from other sites.
- FAQ markup of any kind. FAQ copy stays visible page text.
- Any markup built to chase a snippet.

**Check before delivery**

1. Fetch the rendered page. Every value in the JSON-LD must be visible there without a click, tab or accordion.
2. If a value is not on the page, remove it from the markup or add it to the page first.
3. Quote the source URL for each value in the review notes.
4. If the domain has a recent traffic drop or a structured-data warning, run the de-escalation steps in `kirby-technical-aeo` first.

Local business markup and GBP matching: follow [`kirby-local-seo`](../../kirby-local-seo/SKILL.md). Do not add `LocalBusiness` or `WebSite` markup from this module.

---

## 2. On-Page Assets

Draft these for the pages in the scorecard. Use only facts from `about-my-business.md` and the crawl.

| Asset | Rule |
|---|---|
| Title tag | Names the offer and the buyer's query. Draft within normal display length. Show the current title beside the new one. |
| H1 | One per page. Matches the title's promise. |
| BLUF hero | Bottom line first: what it is, who it is for, price or range, proof. No definition opener. |
| FAQ copy | Real buyer questions from module 02 and owner source material. Visible page text only. No FAQ schema (section 1). |

Hand the wording rules (anti-slop, BLUF layout, GEO structure) to [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md).

**Delivery format** (save as `onpage-assets.md`)

```markdown
## [URL]
- Current title: ...
- Proposed title: ...
- Current H1: ...
- Proposed H1: ...
- Proposed hero (BLUF): ...
- FAQ items: ...
- Evidence for each fact: [URL / owner file / E-number]
- Schema: [core type] - values checked against rendered HTML: yes/no
```

---

## 3. Human Review Gate

No auto-publish. No CMS write, no repo push, no deploy until the owner approves.

1. Present the assets and any code diff as files or a patch. Do not apply them.
2. List what each change affects (URL, element, risk).
3. Ask for a clear "approved" for each item or batch.
4. After approval, apply only what was approved. Use the release rules in [`kirby-seo-deployment`](../../kirby-seo-deployment/SKILL.md).
5. Log each live change with its date, so results can be matched to it. The change-log method is in [`kirby-seo-telemetry`](../../kirby-seo-telemetry/SKILL.md) (isolated SEO changelog protocol).

If the owner uses a coding agent or CMS plugin, give the diff as a prompt for it. Say that the gate still applies.

---

## 4. Dashboard

Build one screen. A single HTML or React artifact, saved as `dashboard.html` (or the React equivalent). Plain-English labels. Readable on a laptop and a phone.

**Tiles**

1. Organic trend: last 7 days and last 30 days (clicks and sessions).
2. Top 10 queries: query, clicks, impressions, CTR, position.
3. Top landing pages: URL, sessions, key events.
4. 30-day milestone checklist: from the roadmap, with done/not done.
5. Top 3 actions this week: from the scorecard, highest Priority first, each with its evidence.

**Data rules**

- Every tile reads from a named source (GSC, GA4, scorecard, roadmap).
- If the source is missing, the tile shows `[Pending Connection]` and the name of the source. No placeholder numbers. No sample data. No zero.
- Show the date range and last refresh time on every data tile.
- The checklist and actions tiles use the user's own roadmap and scorecard files. If those do not exist, they show `[Pending Connection]` too.
- A static page cannot call a connector. State whether the numbers are a snapshot (pulled now, with the date) or live. Do not call a snapshot live.

**Layout**

- Header: domain, date range, refresh time.
- Row 1: organic trend tile.
- Row 2: top queries and top landing pages side by side.
- Row 3: milestone checklist and top 3 actions.
- Light and dark mode. No decoration that hides data.

---

## 5. Ongoing Cadence

- Weekly: refresh the dashboard, tick the checklist, take the next 3 actions.
- Monitoring, GSC triage, drops and attribution: [`kirby-seo-telemetry`](../../kirby-seo-telemetry/SKILL.md).
- Monthly: re-run modules 03 and 04 with fresh data and re-score.
- After 14 weeks: repeat the full audit from the dispatcher.
