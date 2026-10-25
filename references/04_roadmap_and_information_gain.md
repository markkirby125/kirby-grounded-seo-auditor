# Module 04: Roadmap & Information Gain

**Purpose:** Turn the scorecard into a content plan: fix the money pages, build topical clusters, and write from material only the owner has.

Inputs: `about-my-business.md`, `buyer-gap-audit.md`, `fixes-scorecard.md`. If one is missing, run its module first.

---

## 1. Money-Page Optimisation

A money page is a URL that sells: a service, product, course or booking page. Pick them from GA4 conversion data or the owner's list. Do not guess.

For each money page:

1. Fetch the live page. Quote the current title, H1 and first 100 words.
2. Name the target query and its intent. Take volume and CPC from `get_keyword_metrics` or `[Pending Connection]`.
3. Check the SERP for the query (`get_serp_results`). Note what the top results show that this page does not (price, proof, comparison, FAQ).
4. List the changes:
   - Title and H1 that match the query and say what the buyer gets.
   - A hero that confirms intent and gives proof in the first screen. Do not open with a definition of the service.
   - Missing buyer facts from the gap audit (price, risks, comparison).
   - Conversion elements: one clear action, proof near it.
5. Hand the copy rules (BLUF structure, banned wording, anti-slop) to [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md). Do not restate them here.

```markdown
| Money page (URL) | Target query | Intent | Volume / CPC | Current title / H1 | Change | Evidence | Payoff | Effort | Priority |
|---|---|---|---|---|---|---|---|---|---|
```

---

## 2. Pillars and Clusters

1. Choose 3 to 4 topical pillars. Each must tie to a service the business sells and to the buyer questions in module 02.
2. For each pillar, list 5 to 10 cluster articles. Each cluster article:
   - Answers one specific buyer question.
   - Links to its pillar and to the money page.
   - Has a target query with data, or `[Pending Connection]`.
3. Check each target query against the site's existing pages. Do not plan an article for a query an existing page already ranks for. Improve that page.
4. Drop any cluster idea you cannot tie to a buyer question or a query.

```markdown
## Pillar 1: [Topic]  -> money page: [URL]
| # | Article working title | Buyer question | Target query | Volume | Intent | Existing URL for this query? | Source material needed |
|---|---|---|---|---|---|---|---|
| 1 | ... | Cost | "..." | [Pending Connection] | Commercial | None | Call recordings on pricing |
```

The cap is 4 pillars and 40 articles. A small site needs fewer. More pages is not better.

---

## 3. Information Gain from the Owner's Material

Generic articles add nothing a searcher cannot already read. Write from material only the owner holds.

**Ask the user for, in this order:**

1. Transcripts of their own videos, podcasts, webinars or workshops.
2. Sales and onboarding call recordings or notes (with client consent and names removed).
3. Client questions from email, chat and support.
4. Internal data: results, benchmarks, pricing history, before and after cases.

**Rules**

- Each article draws its main claims from at least one named source file. Record it: `Source: workshop-2026-03.txt, 14:20-19:05`.
- Quote or paraphrase what the owner said. Do not add facts the source does not contain.
- If no source exists for a topic, mark the article `Needs owner input` and ask. Do not fill it with general SERP knowledge.
- Do not paste personal data from calls. Remove client names unless they agreed in writing.
- Run the draft through the anti-slop rules in [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md) before review.

---

## 4. Calendar

Build two views. Use real owner capacity: ask how many hours a week they have.

**30-day plan**

| Week | Focus | Items |
|---|---|---|
| 1 | Quick wins and money pages | Title and H1 fixes, missing price/risk facts, core schema (module 05) |
| 2 | Gap pages | Comparison page, alternatives page, cost page |
| 3 | First pillar | Pillar page plus the first 2 to 3 clusters |
| 4 | Measure and adjust | GSC and GA4 check, update the scorecard |

**14-week plan**

| Weeks | Focus |
|---|---|
| 1-2 | Quick wins, money pages, core schema |
| 3-4 | Buyer-gap pages (Cost, Risks, Comparisons, Alternatives) |
| 5-8 | Pillar 1 and its clusters |
| 9-11 | Pillar 2 and its clusters |
| 12-13 | Pillar 3 (and 4 if planned); internal linking pass |
| 14 | Review: re-run modules 03 and the dashboard, re-score |

Adjust to the evidence. Move a fix earlier if its Priority score is high.

**Publishing pace.** Do not release a batch at once. Staging, release pace and network rules are in [`kirby-seo-deployment`](../../kirby-seo-deployment/SKILL.md), `references/module_7_deployment_staging_publishing_velocity_network_isolation.md`. Follow them.

**Expectation.** Rankings move slowly after a change. Do not promise results or dates. Set timing expectations from [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md) `references/module_16_post_update_indexing_latency.md`. Check progress with [`kirby-seo-telemetry`](../../kirby-seo-telemetry/SKILL.md) (isolated changelog and 90-day gate, module 15).

---

## 5. Output

Save as `roadmap.md`: money-page table, pillar tables, source-material list, 30-day and 14-week calendars, and a "Needs owner input" list.
