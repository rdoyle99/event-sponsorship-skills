---
name: price-sponsorship-packages
description: "When the user is an organizer deciding what to charge for sponsorship tiers, booths or add-ons, or wants a tier ladder that matches what comparable events publish. Also use when the user mentions 'how much should I charge sponsors,' 'sponsorship package pricing,' 'what does a gold sponsorship cost,' 'price our booths,' 'sponsorship tiers,' 'are our sponsor prices too low,' or 'sponsorship benchmark.' Reads ConferenceDB published package prices through the MCP (search_conferences, then get_conference) and the dated medians below. For the document that sells the tiers, see write-a-sponsorship-prospectus."
metadata:
  version: 1.0.0
---

# Price your sponsorship packages

You set a tier ladder from what comparable events publish, not from a guess. Most organizers price by copying one
rival or by what last year's top sponsor paid. Both miss the market. Five to ten comparable events with published
prices, plus the medians below, give you a range you can defend to a sponsor who asks why.

## Before you start

Read `.agents/event-sponsorship.md` if it exists (the `sponsorship-context` skill writes it). Take the industry, city,
attendee count and current tiers from it. Without it, ask for: industry, place, expected attendance, the tiers they
plan to sell, and what each tier includes.

## Workflow

1. **Start from the market medians** (ConferenceDB, read on `/sponsorship-pricing` 2026-10-29, US-dollar packages only,
   each conference's latest priced edition, across 1,210 conferences and 9,018 published prices):
   - Median cheapest package $2,000; median top package $15,400. Half of all cheapest packages fall between $861 and
     $5,000.
   - By level: Platinum median $20,000 (1,021 packages), Gold $10,000 (794), Silver $6,000 (646), Bronze $4,000 (532),
     booth, table or exhibit space $3,500 (424).
   - By industry: Healthcare and Medicine cheapest $2,500, top $20,400 (330 events); Education cheapest $1,000, top
     $11,700 (129 events).
   These describe the data set on that date. They are a starting range, not a target for your event.
2. **Find 5-10 comparables.** Call `search_conferences` with the same `topic` and a similar `location` (`limit` 25),
   keep events with `publishes_sponsorship_prices: true` and a similar size, then call `get_conference` on each. Read
   `sponsorship_packages.packages` (name, `price`, `currency`, `price_usd`, `includes`) and `edition_year`. If an event
   publishes none, `similar_events_benchmark` gives the median entry and top package for its scope; quote it with its
   `events` count.
3. **Build the ladder** (`references/tier-ladder.md`):
   - Entry tier near the comparables' cheapest package.
   - Top tier near their top package, and sell only one or two of it.
   - 2-3 tiers in between, each adding one clear benefit (stage time, lead scans, branding, meetings).
   - Add-ons priced on their own (lanyards, coffee, app banner) so the tiers stay simple.
4. **Show the comparison table** (event, year, cheapest and top package, currency) next to the proposed prices. Mark
   each proposed price as below, inside or above the comparables' middle half.
5. **Say what the audience changes.** A room of 300 buyers with budget can price above a room of 3,000 students. Ask
   the user for the evidence (titles, seniority, last year's renewals) and say which way it moves each tier.

## Data

ConferenceDB MCP: `https://conferencedatabase.com/api/mcp` (free, read-only, no key). Tools: `search_conferences` and
`get_conference`. The medians above come from `https://conferencedatabase.com/sponsorship-pricing`; the user can open
it in a browser for the current figures and read date.

## Quality check
- Every median carries its count and date.
- Comparables show their edition year; prices from 3+ years ago are flagged.
- No currencies are mixed in one median. Convert with a stated rate and date, or keep them apart.
- Each tier has one benefit the tier below doesn't.

## What to avoid
- Presenting a median without its count and date.
- Counting ticket prices, per-person rates or per-square-meter rates as packages. ConferenceDB's medians leave them out;
  your comparison should too.
- Ten tiers. Sponsors compare two neighbors and pick the cheaper one.
- Promising a sponsor "ROI" numbers the event can't measure.

## Related Skills
- **sponsorship-context**: supplies the audience and current tiers.
- **find-event-sponsors**: who to sell the tiers to.
- **write-a-sponsorship-prospectus**: puts the ladder into the document sponsors read.
- **plan-an-exhibitor-budget**: the same prices from the buyer's side.
