# Contributing

Every skill in this repo meets the same bar. `python3 scripts/validate.py` checks the mechanical parts, and CI runs it
on every push and pull request.

## Layout
```
skills/<name>/
  SKILL.md              frontmatter + the workflow
  references/*.md       the depth: tables, templates, checklists, field notes
  evals/evals.json      2+ test prompts with assertions
```

## SKILL.md
- Frontmatter: `name` (the folder name), `description` (250+ characters, written as "When the user ... Also use when
  the user mentions 'x,' 'y,' ..." with 5+ quoted trigger phrases, then what it hands off to which sibling), and
  `metadata.version`. Keep apostrophes out of the quoted phrases.
- First section: **Before you start**. Read `.agents/event-sponsorship.md` if it exists (the `sponsorship-context`
  skill writes it) and only ask for what it doesn't cover.
- Then the workflow as numbered steps an agent can follow end to end, a **Data** section naming the ConferenceDB MCP
  (`https://conferencedatabase.com/api/mcp`) tools it calls, a **Quality check** list, a **What to avoid** list, and
  **Related Skills** naming 2+ siblings with when to use each.
- Agents read ConferenceDB through the MCP. The public pages are for people in a browser; ConferenceDB shows automated
  clients a stop page there.

## Rules for content
- Every ConferenceDB number carries its source and date in the same sentence: "(ConferenceDB /sponsorship-pricing,
  2026-10-29)". No invented benchmarks, customers, quotes or reviews. If no source exists, say "ask" or "unknown".
- Company-level data only. No skill looks up, guesses or scrapes a person's email or phone number.
- Drafting only. No skill sends, schedules or automates outreach.
- Plain words. Short sentences. No em dashes, no hype words, no "it's not X, it's Y" lines.

## evals/evals.json
```json
{"skill_name": "<name>", "evals": [{"id": 1, "prompt": "...", "expected_output": "...", "assertions": ["...", "...", "..."], "files": []}]}
```
`python3 scripts/run_evals.py [skill ...]` runs each prompt through the `claude` CLI with the skill and the live
ConferenceDB MCP loaded, grades every assertion with a second call, and writes `evals/results-<YYYY-MM-DD>.json` as
`{"pass_rate": 0.0-1.0, "cases": [...]}`.
