---
name: plan-an-exhibitor-budget
description: "When the user is a company planning what it will cost to exhibit at or sponsor one trade show or a season of them: booth space or package, booth build, shipping, show services, lead capture, travel, staff time and follow-up, and the cost per meeting that makes it worth it. Also use when the user mentions 'trade show budget,' 'how much does a booth cost,' 'exhibitor budget,' 'cost to exhibit at a conference,' 'events budget for next year,' 'trade show cost per lead,' or 'is a 10x10 booth worth it.' Uses the ConferenceDB MCP (get_conference) for published prices. For the go or skip call, see vet-a-trade-show-before-exhibiting."
metadata:
  version: 1.0.0
---

# Plan an exhibitor budget

You build the full cost of a show line by line, then the number of meetings it has to produce to pay back. The space
or package price is the line everyone knows and the one that fools people: the build, shipping, show services, travel
and the team's days usually add more. Get quotes for those lines instead of applying a multiplier.

## Before you start

Read `.agents/event-sponsorship.md` if it exists (the `sponsorship-context` skill writes it) and take the budget,
regions, team and goal from the buyer section. Ask only for what's missing: the show or shows, booth size or package,
how many staff and for how many days, where they travel from, and what a qualified meeting is worth to the company
(average deal size and close rate, from their CRM).

## Workflow

1. **Price the space or package.** Call `get_conference` for the show and read `sponsorship_packages` (each package's
   `price`, `currency`, `includes`, `edition_year`, `source_urls`). If none is published, use
   `similar_events_benchmark` (median entry and top package for its scope, with its `events` count). As a last
   reference, the ConferenceDB median for booth, table or exhibit space is $3,500 across 424 US-dollar packages, and
   the median cheapest package of any kind $2,000 across 1,210 conferences (ConferenceDB /sponsorship-pricing,
   2026-10-29). Label which source each line uses.
2. **List every other line** from `references/cost-lines.md`: booth build or rental, graphics, shipping and material
   handling, show services (electrical, internet, furniture, cleaning, rigging), lead capture, promotion, travel and
   hotel, meals, staff days, and follow-up. Mark each as quoted, estimated by the user, or unknown.
3. **Read the exhibitor manual** on the show's `official_site` for required contractors, deadlines and early-order
   discounts. Deadlines move costs more than anything else; put them in the plan.
4. **Work out the payback.** Meetings needed = total cost / value of one qualified meeting (deal size x close rate
   from meeting to deal). Compare with what the booth can hold: staff on the floor x hours x meetings per staff hour,
   using the team's own past numbers. If the needed number is above what the booth can hold, the plan doesn't work.
5. **Hand back the budget table** (`references/budget-table.md`) with totals, the payback line, the deadlines, and the
   three lines with the most uncertainty.

## Data

ConferenceDB MCP: `https://conferencedatabase.com/api/mcp` (free, read-only, no key). Tool: `get_conference`;
`search_conferences` finds comparable shows when the target publishes no price. The user can check medians in a browser
at `https://conferencedatabase.com/sponsorship-pricing`.

## Quality check
- Every line says where its number came from: published package, quote, user estimate or unknown.
- ConferenceDB prices carry the edition year or the read date.
- The payback line uses the company's own deal size and close rate, or says they are missing.
- Currencies are not mixed in a total.

## What to avoid
- "Space is a third of the budget" and other multipliers with no source. Quote it or leave it out.
- Leaving staff time out of the cost. The team's days are the biggest hidden line.
- Counting badge scans as meetings. Count conversations that meet the user's definition of qualified.
- Booking after the early-order deadlines when the manual lists them.

## Related Skills
- **sponsorship-context**: holds the budget, team and goal.
- **vet-a-trade-show-before-exhibiting**: decides whether the show deserves the budget at all.
- **build-an-events-calendar**: the season the budget has to cover.
- **price-sponsorship-packages**: the organizer's side of the same prices.
