# ConferenceDB plugin

Read-only conference sponsor and exhibitor data for AI agents (Claude, ChatGPT, Cursor, Grok Build).

This plugin connects your agent to the ConferenceDB MCP server at `https://conferencedatabase.com/api/mcp` (streamable HTTP, no sign-in) and adds a skill that tells the agent which tool to use.

## Tools
| Tool | What it does |
|---|---|
| `search_conferences` | Events by topic, place, year or month |
| `get_conference` | One event: dates, venue, organizer, published sponsorship packages, top companies |
| `get_conference_sponsors` | The companies that sponsor or exhibit at one event (50 per call, paged) |
| `get_company_conferences` | The conferences one company sponsors or exhibits at |
| `find_sponsors_for_event` | For organizers: the companies that sponsor and exhibit at the most conferences like yours |

Company-level data only: no people, emails or phone numbers. Every tool is read-only.

## Try it
- "Which companies sponsor Money20/20 USA?"
- "How much does it cost to sponsor NAB Show?"
- "Which conferences does Salesforce sponsor or exhibit at?"
- "I run a 400-person fintech conference in Chicago. Which companies should I pitch as sponsors?"

## Install
- **Claude Code:** this repo is a plugin marketplace. Install the plugin (MCP server + skill) with:
  ```
  /plugin marketplace add rdoyle99/conferencedb-plugin
  /plugin install conferencedb@conferencedb
  ```
  On Claude Code 2.1.275 or later, one step: `/plugin install conferencedb --marketplace rdoyle99/conferencedb-plugin`
- **Server only (Claude Code, Cursor, other hosts):**
  `claude mcp add --transport http conferencedb https://conferencedatabase.com/api/mcp`
- **Any MCP client:** use `.mcp.json` / `mcp.json` in this repo.

Also listed in the official MCP registry as `com.conferencedatabase/conferencedb`.

Data and docs: https://conferencedatabase.com · Privacy: https://conferencedatabase.com/privacy-policy · Support: support@conferencedatabase.com

License: MIT (this plugin). The data stays ConferenceDB's.
