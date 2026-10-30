# Ranking sponsor prospects

Score each company 0-3 on four factors. Fit is a gate: a 0 on fit drops the company.

| Factor | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| Fit | sells to a different buyer | adjacent buyer | same buyer, different budget owner | sells to exactly the people in the room |
| Sponsor history (`as_sponsor_at`) | none | 1 similar event | 2 | 3 or more |
| Breadth (`similar_conferences_at`) | 1 | 2 | 3-4 | 5 or more |
| Timing (`get_company_conferences`) | nothing in the last two years | listed last year only | listed this year | upcoming events in your season |

Read the fields this way:
- `similar_conferences_at` counts how many of the compared conferences list the company (any role).
- `as_sponsor_at` counts how many of those it was at as a sponsor or partner, not only as an exhibitor.
- `seen_at` names a few of the events. Quote them in the reason so the organizer can check.
- `conferences_compared` and `scope` tell you which set was compared. Put the scope on the table: "fintech events in
  the United States" is a different list from "events like Money20/20".

## Lapsed sponsors
A company listed at a rival event's previous edition and not its current one may have budget free. Call
`get_conference_sponsors` with `year` set to the previous edition to compare. Mark these "lapsed at <event>". An
empty current list can also mean the event hasn't published it yet; check the event's dates before calling it a lapse.

## Bands
- **Sponsor prospects**: score 9+ with sponsor history 2+. Pitch tiers.
- **Exhibitor prospects**: fit 2+, no sponsor history. Pitch a booth or a starter package.
- **Long shots**: fit 3, thin history. One email, no follow-up sequence.
