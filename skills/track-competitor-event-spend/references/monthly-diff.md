# Monthly diff

Keep last month's merge table (in the repo or the user's drive) and compare:

```markdown
Competitor events: changes since YYYY-MM-DD (read YYYY-MM-DD)

New listings
- rival-a.com: <event> <year>, exhibitor

Dropped (on the previous edition, not on the current list)
- rival-b.com: <event>, was sponsor at the <year> edition

Tier changes
- rival-c.com: <event>, exhibitor (2025) to Platinum sponsor (2026)

New gaps (2+ competitors, user not listed)
- <event> <year>
```

Before calling something dropped, check the current edition's list exists: `get_conference` on the show shows
`counts`. If the current edition has no list yet, the competitor is "not yet listed", not dropped.
