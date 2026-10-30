# Merge table

```markdown
Competitor events (ConferenceDB get_company_conferences, read YYYY-MM-DD)

| Conference | Edition | Dates | City | us.com | rival-a.com | rival-b.com | rival-c.com | Competitors listed |
|---|---|---|---|---|---|---|---|---|
| <event> | 2026 | Oct 18-21 | Las Vegas | - | sponsor, Gold | exhibitor | sponsor | 3 |

Gaps (2+ competitors, user not listed):
- <event> <year>: rival-a.com (Gold sponsor), rival-c.com (sponsor)

Totals per company:
| Domain | Events listed (total_events) | As sponsor or partner | As exhibitor | Upcoming |
|---|---|---|---|---|

Not found: <domains with found: false, and the other_matches offered>
Capped: <companies with more than 50 events; only the newest 50 are in the table>
```

## Roles
`role` is one of sponsor, partner, media partner or exhibitor. `tier` is the level name the show uses (Gold, Diamond,
Startup Pavilion). Tier names are the show's own; compare within a show, not across shows.
