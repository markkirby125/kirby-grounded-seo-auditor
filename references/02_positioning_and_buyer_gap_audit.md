# Module 02: Positioning & Buyer Gap Audit

**Purpose:** Build a verified description of the business, then test the live site against the questions a buyer asks before they buy. Search engines and AI answer engines skip or misdescribe sites that hide these facts.

Both frameworks below are named in the source summary. They are attributed methods, not tested findings.

---

## 1. Positioning Intake: `about-my-business.md`

Method: April Dunford, *Obviously Awesome*. Work as a positioning analyst.

**Steps**

1. Crawl the root domain and the main service or product pages (module 01, section 5).
2. Draft the file from the live site and the user's own words only. End every line in the file with one tag, not only the ICP lines the template shows:
   - `Verified (URL)`: a fact you read on the live page.
   - `User-stated`: a fact the user's request or reply states, in words you can quote. Use this tag only when the user said it, and use it on a whole line or not at all. Never write "User-stated (partly)". If a line mixes what the user said with something else, split it into one line per fact and tag each line on its own.
   - `Missing`: everything else. A fact you infer from a URL, the business type or common sense is not `User-stated`. A `Missing` line keeps its template label and the tag, with nothing in the value position, and at most a note "inferred from [source], unconfirmed". Never put a guessed value or example in it, such as a customer type or a credential. Put hints about what to supply under "Facts the owner must supply".
3. Ask the user to fill every `Missing` line. Voice dictation or pasted text is fine.
4. Do not invent prices, guarantees, case studies or client names to fill a gap.
5. Save the file and use it as context for modules 03 to 05.

**Template**

```markdown
# About My Business: [Domain]
Date: [YYYY-MM-DD]
(End every line below with `Verified (URL)`, `User-stated` or `Missing`.)

## Ideal customer (ICP)
- Who they are: ...                         [Verified (URL) / User-stated / Missing]
- Situation that makes them buy: ...        [Verified (URL) / User-stated / Missing]
- Who it is NOT for: ...                    [Verified (URL) / User-stated / Missing]

## Value proposition
- What it does, in one sentence: ...
- Outcome the buyer gets: ...

## Exact pricing
- Price or price range, per unit, billing frequency: ...
- Where it appears on the site: [URL / not shown]
- Refund, guarantee, cancellation terms: ...

## Alternatives the buyer considers
- Direct competitors: ...
- Substitutes (DIY, agency, in-house, spreadsheet): ...
- Doing nothing: ...

## Differentiators
- What only this business does, and why it matters to the ICP: ...

## Verifiable proof
- Case studies with named clients and results: [URL]
- Reviews and where they live: [URL]
- Credentials, awards, press: [URL]
```

---

## 2. The Big Five Buyer Questions

Method: after Marcus Sheridan, *They Ask, You Answer*. The source summary calls these five questions his "Big Five". His published list is cost, problems, comparisons, reviews and best-of, so Risks and Alternatives are this skill's substitution for Reviews and Best-of. Read the site as a sceptical first-time buyer. For each question, find the page that answers it. If you cannot find one, it is a gap.

| Question | Test | Typical gap |
|---|---|---|
| **Cost** | Is exact pricing, a price range, or what drives price shown before checkout or a sales call? | "Contact us for a quote" with nothing else |
| **Problems** | Does the site say what can go wrong, what it does not do, and who should not buy? | Only benefits listed |
| **Risks** | Are the guarantee, contract length, cancellation, data and delivery terms clear? | Terms buried or absent |
| **Comparisons** | Is there a page that compares the offer with named alternatives, with criteria? | No comparison page |
| **Alternatives** | Does the site discuss other ways to solve the problem, including DIY or an agency? | Competitors never mentioned |

For each gap record: the question, the URL checked, what you found, and the buyer search it fails (for example "[service] cost", "[brand] vs [competitor]"). Label any search that does not come from GSC, keyword data or the user as `candidate (unverified)` in the "Search it fails" column, and give it no volume. Check volume for the rest with module 01 tools. If keyword data is missing, write `[Pending Connection]`.

---

## 3. AI-Simulation Check

Ask this of the model, using only the crawled pages as the evidence base:

> If an AI search engine (ChatGPT, Perplexity, Google AI Overviews) read only this domain to recommend a [niche] provider to a buyer in [location], which buying criteria could it not answer from the HTML? List each criterion, the page where it should be, and what the AI would have to guess.

Rules for this check:

- List only criteria you can tie to a page you fetched.
- State that this is a simulation. It shows likely omissions. It does not show how any engine actually ranks the site.
- Where `get_ai_visibility_results` is connected, compare the simulation with the real answers (module 03, section 2).

---

## 4. Gap Audit Output Template

Save as `buyer-gap-audit.md`.

```markdown
# Buyer Question Gap Audit: [Domain]
Date: [YYYY-MM-DD]   Pages crawled: [n]   Data sources: [list, with any [Pending Connection]]

## Summary
- Gaps found: [n of 5]
- Highest payoff gap: [question] on [URL]

## Gaps
| # | Question | Page checked (URL) | What the page says now | Missing buyer fact | Search it fails | Volume | Payoff (1-5) | Effort (1-5) | Priority |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Cost | https://... | "Contact us" | Price range and what drives it | "[service] cost" | [Pending Connection] | 5 | 2 | 2.5 |

## AI-simulation findings
- Criterion the AI could not answer: ... (should live at: URL)

## Facts the owner must supply
- ...
```

Priority = Payoff / Effort. Give both scores and a one-line reason for each.
