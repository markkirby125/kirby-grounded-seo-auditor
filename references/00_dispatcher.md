# Grounded SEO & AI Search Auditor - Dispatcher

**Purpose:** Run an SEO and AI search (GEO) audit that rests on live data and a crawl of the live page, not on model memory. Output a gap audit, a scored top-10 fixes list, a content roadmap, reviewed on-page assets and a dashboard.
**Source:** Eliot Prince, "Claude Just Changed SEO & AI Search Forever" (YouTube, `setxOzrPVkU`), received as a Gemini summary in Oct 2026. Second-hand and unverified. The tool names, the Dunford and Sheridan frameworks and the stage order come from that summary. Treat them as a working method, not as tested fact.
**Related:** On-page GEO and anti-slop rules: [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md). Schema risk rules: [`kirby-technical-aeo`](../../kirby-technical-aeo/SKILL.md). Ongoing monitoring: [`kirby-seo-telemetry`](../../kirby-seo-telemetry/SKILL.md). Publishing and deploy: [`kirby-seo-deployment`](../../kirby-seo-deployment/SKILL.md). Local and GBP work: [`kirby-local-seo`](../../kirby-local-seo/SKILL.md).

---

## Core Operating Principles

These apply in every module. A module may add rules. It may not relax these.

1. **Never invent metrics.** Search volume, clicks, impressions, CTR, rankings, CPC, backlinks and citation counts come from a connected tool or a file the user supplies. Nothing else.
2. **Missing source means `[Pending Connection]`.** If a connector is not available, write the literal string `[Pending Connection]` where the number would go. Then ask the user for a manual GSC or GA4 export (CSV or pasted table) and stop analysing that metric until it arrives. Do not estimate. Do not use training-set averages.
3. **Crawl the live page first.** Fetch the current page before any on-page advice. Quote what is on the page now (title, H1, hero, price, schema). If the page cannot be fetched, say so and give no on-page advice for it.
4. **Cite evidence.** Every recommendation names a specific URL, query or data point. A recommendation with no evidence is deleted, not softened.
5. **No auto-publish.** Nothing goes to a CMS, repo or live site without a human review gate. See module 05.
6. **Score every fix the same way.** `Priority = Business Payoff (1-5) / Implementation Effort (1-5)`. Higher is better. Show both inputs and the result.
7. **Plain English.** Explain jargon the first time it appears. Short sentences.
8. **Mark the source.** When you cite a number, name the tool and the date range it came from.
9. **Respect the credit gate.** Any tool that spends credits follows the running-total approval rule in module 01, section 4, in every module and on every re-run.

A **money page** is a URL that sells: a service, product, course or booking page.

---

## Module Routing

Read only the module you need.

| If the request is about | Read |
|---|---|
| Which tools to use, connecting GSC/GA4/DataForSEO/crawler, what to do when a tool is missing | [`01_tool_stack_and_grounding.md`](01_tool_stack_and_grounding.md) |
| Building the business positioning file, "what do buyers ask that the site does not answer", pricing/comparison/risk gaps, why AI search skips the brand | [`02_positioning_and_buyer_gap_audit.md`](02_positioning_and_buyer_gap_audit.md) |
| Branded vs unbranded traffic, AI citation benchmark, the top-10 fixes scorecard | [`03_multi_vector_audit_scorecard.md`](03_multi_vector_audit_scorecard.md) |
| Money-page rewrite plan, pillar and cluster map, content from the owner's own material, 30-day and 14-week calendar | [`04_roadmap_and_information_gain.md`](04_roadmap_and_information_gain.md) |
| JSON-LD, title/H1/hero/FAQ copy, review gate, dashboard, weekly cadence | [`05_execution_gate_and_dashboard.md`](05_execution_gate_and_dashboard.md) |

Requests that belong to a sibling skill:

| Request | Go to |
|---|---|
| Anti-slop rules, BLUF and on-page GEO structure | [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md) |
| Schema removal after a drop, `sameAs` triangulation | [`kirby-technical-aeo`](../../kirby-technical-aeo/SKILL.md) |
| Publishing speed, staging, batch release | [`kirby-seo-deployment`](../../kirby-seo-deployment/SKILL.md) |
| GSC triage, change logs, post-launch monitoring | [`kirby-seo-telemetry`](../../kirby-seo-telemetry/SKILL.md) |
| GBP, map pack, service-area audits | [`kirby-local-seo`](../../kirby-local-seo/SKILL.md) |

---

## Stage Order for a Full Audit

Run the stages in this order. Do not skip ahead: later stages use the output of earlier ones.

1. **Ground** (module 01). List connected tools. Mark each missing one `[Pending Connection]`. Confirm the domain and the money pages.
2. **Position** (module 02). Crawl the live site. Draft `about-my-business.md`. Ask the user to fill every gap you cannot verify.
3. **Gap audit** (module 02). Test the site against the Big Five buyer questions. Run the AI-simulation check.
4. **Score** (module 03). Pull the branded/unbranded split and the AI citation benchmark. Build the top-10 fixes scorecard.
5. **Plan** (module 04). Money-page changes, pillars and clusters, source material, calendar.
6. **Draft and gate** (module 05). Draft on-page assets and core schema. Stop at the human review gate.
7. **Dashboard** (module 05). Build the single-screen view. Hand ongoing monitoring to `kirby-seo-telemetry`.

A partial request (for example "just the scorecard") runs stage 1 plus the stage it names. Say which stages you skipped.

---

## Output Rules

- Save each stage output as its own markdown file so the user can review it: `about-my-business.md`, `buyer-gap-audit.md`, `fixes-scorecard.md`, `roadmap.md`, `onpage-assets.md`. The dashboard (module 05) is the one HTML file: `dashboard.html`.
- Start each file with the domain, the date, and the list of data sources used, with any `[Pending Connection]` items.
- End the audit with a short list of what you could not verify and what the user must supply.
