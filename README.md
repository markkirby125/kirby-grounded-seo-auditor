# Kirby Grounded SEO Auditor

*This skill is part of the [Kirby Skills Collection](https://github.com/markkirby125/kirby-skills-collection).*

An agent skill for SEO and AI search (GEO) audits that use live data. It never invents metrics. If a data source is missing, it prints `[Pending Connection]` and asks for a manual GSC or GA4 export. It crawls the live page before it gives on-page advice, cites a URL, query or data point for every recommendation, and stops at a human review gate before anything is published.

The root `SKILL.md` points to a dispatcher. The agent loads only the module it needs from `references/`.

## Modules

- **00 Dispatcher**: guardrails, module routing, stage order
- **01 Tool Stack & Grounding**: openseo MCP, `seo-dataforseo`, `seo-firecrawl`, `seo-google`; Composio as an option
- **02 Positioning & Buyer Gap Audit**: `about-my-business.md` and the Big Five buyer questions
- **03 Multi-Vector Audit Scorecard**: branded vs unbranded split, AI citation benchmark, top-10 fixes
- **04 Roadmap & Information Gain**: money pages, pillars and clusters, 30-day and 14-week calendar
- **05 Execution Gate & Dashboard**: core schema, on-page assets, review gate, single-screen dashboard

## Installation & Magic Prompt

Copy the prompt below into your AI coding tool (Claude Code, Cursor, Windsurf, GitHub Copilot).

```markdown
@agent Please install the Kirby Grounded SEO Auditor skill into this workspace.
1. Read the `SKILL.md` and `references/` directory from this repository: https://github.com/markkirby125/kirby-grounded-seo-auditor
2. Identify the correct rules system for our current environment (e.g., `.cursor/rules/` for Cursor, `.windsurfrules` for Windsurf, `.clinerules` for Cline, or `~/.agents/skills/` for Antigravity).
3. If our environment requires a single file, concatenate the modules appropriately. If it supports multi-file dispatcher skills (like `.agents/skills`), clone the directory structure exactly.
4. Confirm when the installation is complete.
```

Manual install for Claude Code or Antigravity:

```bash
git clone https://github.com/markkirby125/kirby-grounded-seo-auditor ~/.agents/skills/kirby-grounded-seo-auditor
```

## Source

Workflow adapted from Eliot Prince's video "Claude Just Changed SEO & AI Search Forever", received as a Gemini summary (Oct 2026). Second-hand and unverified.
