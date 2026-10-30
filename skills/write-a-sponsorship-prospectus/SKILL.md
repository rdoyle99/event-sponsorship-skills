---
name: write-a-sponsorship-prospectus
description: "When the user is an organizer who needs a sponsorship prospectus, sponsor deck or one-page sponsor sheet that sponsors will read and act on: the audience, the tiers and prices, add-ons, dates and one contact. Also use when the user mentions 'write a sponsorship prospectus,' 'sponsor deck,' 'sponsorship proposal,' 'sponsor packet,' 'sponsorship kit,' 'one-pager for sponsors,' or 'make our sponsorship pitch better.' Uses the ConferenceDB MCP (find_sponsors_for_event) for category proof. For the prices, see price-sponsorship-packages. For the email that goes with it, see write-a-sponsor-outreach-email."
metadata:
  version: 1.0.0
---

# Write a sponsorship prospectus

You write a 2-4 page prospectus a sponsor can say yes to without a call: who is in the room, what each tier costs and
includes, and when to decide. Sponsors skim for three things: the audience, the price, and whether companies like
them already sponsor events like this. Lead with those.

## Before you start

Read `.agents/event-sponsorship.md` if it exists (the `sponsorship-context` skill writes it) and take the audience
facts, tiers and dates from the organizer section. Ask only for what's missing. Audience numbers come from the
organizer: attendee count, job titles, seniority, industries and countries, and last year's numbers with their source.
Never estimate them.

## Workflow

1. **Collect the audience facts.** Ask; mark anything unknown as unknown. A prospectus with "about 1,000 decision
   makers" and no source is the first thing a sponsor discounts.
2. **Price the tiers** with `price-sponsorship-packages` if they aren't priced yet.
3. **Find category proof.** Call `find_sponsors_for_event` (the event, or its topic and place) and pick 8-12
   companies that sponsor similar events. Use them as "companies that sponsor events like this", never as "past
   sponsors" unless they really sponsored this event. Past sponsors come from the organizer's own records.
4. **Write the prospectus** in this order (`references/structure.md`):
   - a one-line audience promise;
   - audience numbers with their source;
   - the tier table: price, what's included, how many are available;
   - add-ons;
   - dates and deadlines (contract, logo, booth build, payment);
   - one named contact role and how to reach it.
   Keep it to 2-4 pages.
5. **End with a claim checklist**: every number and claim in the document with its source, so the organizer can
   verify it before sending (`references/claim-checklist.md`).

## Data

ConferenceDB MCP: `https://conferencedatabase.com/api/mcp` (free, read-only, no key). Tool: `find_sponsors_for_event`;
`get_conference` on the organizer's own event shows what ConferenceDB already lists for it. If the prospectus quotes a
market price, use the ConferenceDB median with its date: median top package $15,400 across 1,210 conferences that
publish US-dollar prices (ConferenceDB /sponsorship-pricing, 2026-10-29).

## Quality check
- The audience section has a source for each number.
- The tier table has price, inclusions and a count for every tier.
- No company is called a past sponsor without the organizer's confirmation.
- The document has one call to action and one contact.
- The claim checklist covers every number.

## What to avoid
- Pages about the city, the venue's history or the organizer's mission before the audience.
- "Exposure", "visibility" and "brand awareness" as the only benefits. Say what the sponsor gets: minutes on stage,
  scans, meetings, square meters.
- Attendee lists or personal data as a benefit. Offer opt-in meetings or lead scans, which attendees agree to.
- Logo walls of companies that never sponsored.

## Related Skills
- **sponsorship-context**: holds the audience facts and tiers.
- **price-sponsorship-packages**: sets the prices in the tier table.
- **find-event-sponsors**: supplies the category-proof companies and the send list.
- **write-a-sponsor-outreach-email**: the email that carries the prospectus.
