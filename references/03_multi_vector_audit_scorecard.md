# Module 03: Multi-Vector Audit & Scorecard

**Purpose:** Measure where organic visibility comes from, check who AI search cites instead of the site, and turn the findings into ten ranked fixes.

**Inputs:** `about-my-business.md` and `buyer-gap-audit.md` from module 02. For a scorecard-only request, do not run module 02. Ask the user for the buyer questions and target queries to use. The scorecard then carries no gap-derived rows and says in one line that the gap audit was not run. For a full audit, if either file is missing, run module 02 first.

Every figure here comes from the evidence log (module 01, section 6). No source, no figure: write `[Pending Connection]`.

The position bands below and the "under a day" Quick Wins limit are working heuristics from the source summary. They are not measured rules.

---

## 1. Branded vs Unbranded Split

1. Pull GSC queries for the last 30 to 90 days. State the exact range. If GSC is missing, ask for a manual export.
2. Define the brand terms list with the user: the brand name, its misspellings, the domain, product names, founder names. Record the list.
3. Split queries into branded (match the list) and unbranded.
4. For each group report clicks, impressions, CTR and average position.
5. Read the split:
   - Almost all clicks branded: people find the site only after they already know it. Unbranded discovery is the gap.
   - Unbranded impressions high, clicks low: titles and snippets are not winning the click.
   - Unbranded commercial queries at positions 4 to 20: closest wins.
6. Pull the top unbranded commercial queries. Mark which URL ranks for each. Flag queries where the ranking URL is not the intended money page.

```markdown
| Group | Clicks | Impressions | CTR | Avg position | Source / range |
|---|---|---|---|---|---|
| Branded | [Pending Connection] | | | | |
| Unbranded | [Pending Connection] | | | | |
```

Use GA4 organic landing pages (when connected) to check that GSC clicks reach pages that convert.

---

## 2. AI Search Citation Benchmark

1. Choose 5 to 15 core queries: the buyer questions from module 02 (or the ones the user supplies for a scorecard-only run) plus the top unbranded commercial queries. Label any query that does not come from GSC, keyword data or the user as `candidate (unverified)` in the Query column. A candidate query gets no volume, CPC or position, and it does not feed a score until data confirms it.
2. For each query, record which brands and URLs the AI answers cite. Use `get_ai_visibility_results` and `get_ai_visibility_sources` when connected, or the DataForSEO AI data via `seo-dataforseo`.
3. If no tool is connected, ask the user to run the queries by hand in the engines they care about and paste the answers. Do not recall from memory what an engine "usually" says.
4. Record whether the site is cited, mentioned without a link, or absent.

```markdown
| Query | Engine | Site cited? | Cited instead (brand / URL) | What the cited page has that ours lacks | Evidence |
|---|---|---|---|---|---|
| "[query]" | [engine] | No | competitor.com/page | Price table | E7 |
```

Before the batch, state the estimated total credits in one sentence from `estimate_ai_visibility_cost`. If there is no estimate tool, state the call count (queries × engines), say that it is a count and not a cost, and ask the user for the per-call price. Ask for approval if the estimate, added to the credits already spent in this audit, is over 2,000.

---

## 3. Technical and On-Page Crawl

Crawl the money pages and top landing pages (module 01, section 5). Check for each URL:

- Title tag and H1: present, unique, matches the query intent.
- Meta description and first screen of copy.
- Canonical, indexability, status code.
- Schema present, and whether every value is visible on the page (see module 05).
- Internal links in and out. Orphan pages.
- Page speed: use a measured result only.

Record findings with the URL. Pull the audit with `run_site_audit` and `get_audit_issues` when connected.

---

## 4. Top-10 Fixes Scorecard

Rank fixes from sections 1 to 3 and, when it was run, from the module 02 gap audit.

**Categories**

- **Quick Wins:** under a day, no development, clear evidence (title rewrite, adding a price range).
- **On-Page:** page copy, headings, internal links, comparison pages.
- **Technical:** crawl, index, speed, schema, redirects.
- **AI Search:** content and entity changes aimed at citations.

**Scoring**

- Business Payoff, 1 to 5: effect on leads or revenue if fixed. 5 = a money page or a high-intent query.
- Implementation Effort, 1 to 5: time and skill needed. 5 = large build or many teams.
- Priority = Payoff / Effort. Round to one decimal. Sort high to low. Break ties by higher Payoff, then lower effort. A 5/5 fix and a 1/1 fix both score 1.0, and the 5/5 fix is the one that matters more.

Scores are judgement. State the reason for each in the row. Do not present a score as measured.

**Template** (save as `fixes-scorecard.md`)

```markdown
# Top 10 Fixes: [Domain]
Date: [YYYY-MM-DD]   Sources: [list, with any [Pending Connection]]

| Rank | Category | Fix | Evidence (URL / query / metric) | Payoff (1-5) | Effort (1-5) | Priority score | Why these scores |
|---|---|---|---|---|---|---|---|
| 1 | Quick Wins | Rewrite title on /pricing to include "[service] cost" | /pricing title is "Pricing"; query "[service] cost" position 8 (E3) | 4 | 1 | 4.0 | Money page, one-line change |
```

Rules:

- Fewer than 10 supported fixes: list the ones you have. Do not pad.
- A row with no evidence is deleted from the table and listed under "Needs data" with the data it needs. Never score it.
- Fixes tied to a drop or penalty go to `kirby-seo-telemetry` (GSC triage) before scoring.
