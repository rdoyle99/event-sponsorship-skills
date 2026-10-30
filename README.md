# Event Sponsorship Skills for AI Agents

Skills that teach Claude Code, Codex, Cursor and any agent that reads the [Agent Skills spec](https://agentskills.io)
the work around event and conference sponsorship: finding sponsors for an event, pricing the packages, writing the
prospectus and the outreach drafts, deciding whether a trade show is worth a booth, budgeting it, and tracking where
competitors show up.

The skills run on live data. They call the free, read-only
[ConferenceDB](https://conferencedatabase.com?ref=event-sponsorship-skills) MCP, which lists who sponsors and exhibits
at which conference and the package prices organizers publish: 187,433 sponsor and exhibitor listings on the current
editions of 3,589 conferences, and published sponsorship packages for 1,540 conferences (ConferenceDB, 2026-10-29).
Your agent ranks sponsor prospects by where companies already paid for packages, and prices tiers from what
comparable events publish.

Built by [Ryan Doyle](https://www.linkedin.com/in/ryan-doyle). Found a better way to do something here?
[Open a PR](#contributing). A question or a problem? [Open an issue](https://github.com/rdoyle99/event-sponsorship-skills/issues).

## Install in one paste

Paste this into Claude Code, Codex or Cursor:

```text
Install the event sponsorship skills from https://github.com/rdoyle99/event-sponsorship-skills for this project:
1. Run `npx skills add rdoyle99/event-sponsorship-skills -a claude-code` (or `-a codex` / `-a cursor` for those agents).
2. Add the ConferenceDB MCP server: `claude mcp add --transport http conferencedb https://conferencedatabase.com/api/mcp`
   (no sign-in; Codex and Cursor take the same URL in their MCP settings).
3. Run the sponsorship-context skill to write .agents/event-sponsorship.md for this project, then show me the file.
```

## How the skills fit together

```
                    sponsorship-context  (.agents/event-sponsorship.md, read first by every skill)
                                 |
              +------------------+-------------------+
              |                                      |
   Organizers (selling sponsorship)        Companies (buying it)
   find-event-sponsors                     build-an-events-calendar
   price-sponsorship-packages              vet-a-trade-show-before-exhibiting
   write-a-sponsorship-prospectus          plan-an-exhibitor-budget
   write-a-sponsor-outreach-email          track-competitor-event-spend
```

Every skill ends with a Related Skills section that says which one to run next.

## Skills

<!-- SKILLS:START -->
| Skill | Use it when |
|---|---|
| [build-an-events-calendar](skills/build-an-events-calendar/) | The user needs a shortlist of conferences and trade shows to attend, exhibit at or sponsor over a period, laid out as a calendar with dates, place, list size, published prices and deadlines. |
| [find-event-sponsors](skills/find-event-sponsors/) | The user is organizing a conference, trade show, meetup or summit and needs a ranked list of companies likely to sponsor or exhibit at it, built from where those companies already sponsor and exhibit. |
| [plan-an-exhibitor-budget](skills/plan-an-exhibitor-budget/) | The user is a company planning what it will cost to exhibit at or sponsor one trade show or a season of them: booth space or package, booth build, shipping, show services, lead capture, travel, staff time and follow-up, and the cost per meeting that makes it worth it. |
| [price-sponsorship-packages](skills/price-sponsorship-packages/) | The user is an organizer deciding what to charge for sponsorship tiers, booths or add-ons, or wants a tier ladder that matches what comparable events publish. |
| [sponsorship-context](skills/sponsorship-context/) | The user wants to set up or update the shared event sponsorship context every other skill in this repo reads first: which side they are on (organizer selling sponsorship, or a company buying it), their events or their company, the audience, industry, region, competitors, budget and goals. |
| [track-competitor-event-spend](skills/track-competitor-event-spend/) | A marketing or events team wants to know which conferences and trade shows their competitors sponsor or exhibit at, where two or more of them show up and the user doesn't, and what changed since the last check. |
| [vet-a-trade-show-before-exhibiting](skills/vet-a-trade-show-before-exhibiting/) | The user is a company deciding whether to exhibit at, sponsor, or skip a particular trade show or conference, and wants a verdict backed by who exhibits there, how many come back, and what it costs. |
| [write-a-sponsor-outreach-email](skills/write-a-sponsor-outreach-email/) | The user is an organizer who wants a draft of the first email or a follow-up to a company they hope will sponsor or exhibit at their event, written from that company's own event history so it reads as researched, not mass-mailed. |
| [write-a-sponsorship-prospectus](skills/write-a-sponsorship-prospectus/) | The user is an organizer who needs a sponsorship prospectus, sponsor deck or one-page sponsor sheet that sponsors will read and act on: the audience, the tiers and prices, add-ons, dates and one contact. |
<!-- SKILLS:END -->

## Installation options

### Option 1: npx skills (recommended)
```bash
npx skills add rdoyle99/event-sponsorship-skills            # all skills
npx skills add rdoyle99/event-sponsorship-skills --skill find-event-sponsors price-sponsorship-packages
npx skills add rdoyle99/event-sponsorship-skills --list
```
Inside an agent session the CLI runs non-interactively; pass the agent with `-a claude-code` so the files land in
`.claude/skills/`.

### Option 2: Claude Code plugin (skills + the MCP server in one step)
```bash
/plugin marketplace add rdoyle99/event-sponsorship-skills
/plugin install event-sponsorship-skills
```
Outside an interactive session: `claude plugin marketplace add rdoyle99/event-sponsorship-skills` then
`claude plugin install event-sponsorship-skills@event-sponsorship-skills`.

### Option 3: clone and copy
```bash
git clone https://github.com/rdoyle99/event-sponsorship-skills.git
cp -r event-sponsorship-skills/skills/* .claude/skills/
```

## The data behind it

The ConferenceDB MCP (`https://conferencedatabase.com/api/mcp`) is read-only and free, with no key. Five tools:

| Tool | Takes | Returns |
|---|---|---|
| `search_conferences` | topic, place, year, month | events with dates, city, list sizes, whether prices are published, the ConferenceDB page |
| `get_conference` | a conference name or slug | dates, organizer, published packages and prices, counts, returning and new companies, similar events |
| `get_conference_sponsors` | a conference, optional role and year | its sponsors and exhibitors with domain, role and tier, 50 per call |
| `get_company_conferences` | a company name or domain | the events it sponsors or exhibits at, with role and year |
| `find_sponsors_for_event` | your event, or a topic and place | companies listed at the most similar conferences, and how often as a sponsor |

Market medians in the pricing skills come from the
[sponsorship pricing page](https://conferencedatabase.com/sponsorship-pricing?ref=event-sponsorship-skills): median
cheapest package $2,000 and median top package $15,400 across 1,210 conferences that publish US-dollar prices
(ConferenceDB, 2026-10-29). People in a browser can read every list at
[conferencedatabase.com](https://conferencedatabase.com?ref=event-sponsorship-skills); agents use the MCP.

## Ground rules every skill follows

- Company-level data only. The skills never look up, guess or scrape a person's email address or phone number. Find
  the right person on the company's own site or LinkedIn.
- Drafting only. `write-a-sponsor-outreach-email` writes drafts the user reads and sends; no skill sends, schedules
  or automates email.
- Every number carries its source and date. Where no source exists, the skill asks or says "unknown".
- "Sponsors similar events" is never presented as "sponsors this event".

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md). Run `python3 scripts/validate.py` before you open a PR; CI runs it too.
`python3 scripts/sync_readme.py` rebuilds the skills table. `python3 scripts/run_evals.py` runs the evals with the
`claude` CLI and writes `skills/<name>/evals/results-<date>.json`.

## License

[MIT](LICENSE)
