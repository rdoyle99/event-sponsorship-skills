# Calendar table

```markdown
<Topic> events, <region>, <months> (ConferenceDB MCP, read YYYY-MM-DD)

| Month | Event | City | Dates | Sponsors + exhibitors listed | Published packages (year, currency) | Competitors listed | Deadline (source) | Tier | Why | ConferenceDB page |
|---|---|---|---|---|---|---|---|---|---|---|
```

## Reading `search_conferences`
- `sponsors_listed` and `exhibitors_listed`: companies on the current edition's lists. Zero can mean the list isn't
  published yet.
- `publishes_sponsorship_prices`: whether `get_conference` will return package prices.
- `upcoming`: false means the edition on file has happened; the next one may not be listed yet.
- `official_site`: the event's own website, where deadlines and exhibitor manuals live.
- `page_url`: the ConferenceDB page to cite.

`total_matches` can be larger than what's returned; results come largest list first, so narrow by month or place to
see smaller events.
