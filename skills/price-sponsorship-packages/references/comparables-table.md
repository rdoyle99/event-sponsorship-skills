# Comparables table

```markdown
Comparable events with published sponsorship prices (ConferenceDB MCP, read YYYY-MM-DD)

| Event | Edition | City | Cheapest package | Top package | Currency | Packages listed | ConferenceDB page |
|---|---|---|---|---|---|---|---|

Middle half of cheapest packages across these events: <low> to <high>
Proposed ladder:
| Tier | Proposed price | Inside, below or above the middle half | Benefit added |
|---|---|---|---|
```

## Reading `get_conference`
- `sponsorship_packages.published`: false means the organizer publishes no prices; don't treat it as free.
- `price` is in `currency`; `price_usd` is the US-dollar value where ConferenceDB has one. Compare in one currency.
- `price_text` is the price as the organizer wrote it ("from $5,000", "EUR 4,500 + VAT"). Read it for qualifiers.
- `includes` is the organizer's own description of the package.
- `source_urls` are the organizer's pages the prices came from. Link one per row so the user can check.
- `edition_year` is the year the prices are for. Old prices usually rose since.
