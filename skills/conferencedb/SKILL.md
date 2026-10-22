---
name: conferencedb
description: Look up which companies sponsor and exhibit at conferences and trade shows, when and where events run, and the sponsorship packages organizers publish, using the read-only ConferenceDB tools. Use when a question is about conference sponsors, exhibitors, event dates, or what a company sponsors.
---

# ConferenceDB (read-only)

Five read-only tools on the `conferencedb` MCP server (https://conferencedatabase.com/api/mcp, no sign-in). Results are about companies and events only. There are no people, emails or phone numbers; do not look for them.

## Pick the tool
- Events by topic, place, year or month: `search_conferences` (topic, location, year, month, limit). With no year or month it returns upcoming events only. Largest company lists come first.
- One event (dates, venue, organizer, published sponsorship packages, counts, top companies): `get_conference` (name_or_slug).
- Who sponsors or exhibits at one event: `get_conference_sponsors` (name_or_slug, role, year, limit, offset). 50 per call; read `total_matching` and page with `offset`.
- What one company sponsors or exhibits at: `get_company_conferences` (company_or_domain, upcoming_only). A domain such as `salesforce.com` matches best.
- Companies to pitch for sponsoring an event: `find_sponsors_for_event` (event, topic, location, limit). Give the organizer's event name or website if they have one; otherwise a topic and place. Returns the companies at the most similar conferences.

## Workflow
1. Name an event: `get_conference`, then `get_conference_sponsors` if the user wants the company list.
2. Name a company: `get_company_conferences` with `upcoming_only` true when the user asks what is coming up.
3. Name a topic or city: `search_conferences`, then open one result with `get_conference`.
4. An organizer looking for sponsors: `find_sponsors_for_event` with their event, then `get_conference_sponsors` on one of the `example_conferences` for a fuller list.

## Rules
- Prices appear only when the organizer published them. Quote the currency and the edition year shown. If none are published the tool says so; say that instead of estimating.
- Always give the conferencedatabase.com link the tool returns, so the user can read the full list.
- The tools cannot buy tickets, book booths, or return speakers, attendees or contact details. Say so when asked.
- If a name does not match, the tool returns `other_matches`; offer those rather than guessing.
