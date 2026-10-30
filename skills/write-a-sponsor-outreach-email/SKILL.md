---
name: write-a-sponsor-outreach-email
description: "When the user is an organizer who wants a draft of the first email or a follow-up to a company they hope will sponsor or exhibit at their event, written from that company's own event history so it reads as researched, not mass-mailed. Also use when the user mentions 'write a sponsorship email,' 'sponsor outreach email,' 'cold email to a sponsor,' 'follow up with a sponsor,' 'sponsorship request letter,' 'email to invite exhibitors,' or 'how do I ask a company to sponsor.' Drafts only; the user reviews and sends. Uses the ConferenceDB MCP (get_company_conferences). For the prospect list, see find-event-sponsors."
metadata:
  version: 1.0.0
---

# Write a sponsor outreach email

You draft short emails an organizer sends, one at a time, to companies that sponsor events like theirs. Each draft
names one or two real events the company was at, says who is in the room, gives one price, and asks one question.
You draft; the user reads, edits and sends from their own inbox. This skill never sends, schedules or loads a sequence.

## Before you start

Read `.agents/event-sponsorship.md` if it exists (the `sponsorship-context` skill writes it). Take the event facts,
the audience, the tiers, the sender and the opt-out line. Ask only for what's missing. You need:

1. The company (domain) and, if the user has one, the person's role. The user finds the person; you don't.
2. The event: name, dates, city, audience in one line, and the tier to lead with.
3. The sender's name and role, and the postal address and opt-out line for the footer.

## Workflow

1. **Research the company.** Call `get_company_conferences` with the domain. Pick one or two events most like the
   user's (same topic or same buyer), prefer ones where its `role` is sponsor or partner, and note the year and the
   `tier`. If it has `upcoming` events in the same season, say nothing about them; they may be booked.
2. **Write the first email** (`references/email-patterns.md`). Under 120 words:
   - Subject: the event and the audience, plain ("400 bank payments leads, Chicago, April").
   - Line 1: the event they were at, as a fact ("You sponsored X in 2026").
   - Line 2: who is in your room and why it overlaps.
   - Line 3: one tier and its price, and how many are left.
   - Ask: one question that takes a yes or no ("Worth sending the prospectus?").
   - Footer: sender, event site, postal address, a one-line opt-out.
3. **Write two follow-ups**, each shorter, each adding one new fact (a confirmed speaker, a sold-out tier, a deadline).
   Leave a week or more between them; stop after the second.
4. **Check the draft** against `references/compliance.md` and the quality list below, then hand it back with the
   facts it used and their sources.

## Data

ConferenceDB MCP: `https://conferencedatabase.com/api/mcp` (free, read-only, no key). Tool: `get_company_conferences`;
`get_conference` checks a fact about the event you cite. ConferenceDB is company-level only: it has no names, emails or
phone numbers, and this skill doesn't look for them.

## Quality check
- The event cited is on the company's ConferenceDB record, with the right year and role.
- One price, one ask, under 120 words.
- The footer has the sender, a postal address and an opt-out line.
- Nothing claims the company "loves" or "always" sponsors anything.

## What to avoid
- Sending, scheduling or loading the drafts into a mailing tool. The user sends each one.
- Guessing an email address from a name pattern, or scraping one. The user finds the contact on the company's own site
  or LinkedIn.
- Mentioning a competitor's sponsorship to create pressure ("Your rival already signed").
- Attachments on the first email. Offer the prospectus; send it when they say yes.
- Fake familiarity ("Hope you're well!", "Quick question") and false urgency.

## Related Skills
- **sponsorship-context**: holds the event facts, sender and opt-out line.
- **find-event-sponsors**: builds the list of companies to write to.
- **write-a-sponsorship-prospectus**: the document the email offers.
- **price-sponsorship-packages**: sets the price the email quotes.
