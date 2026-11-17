# Kitbay for AI agents

[Kitbay](https://kitbay.app/) is a directory of MCP servers and agent skills. Every fact on it has a source URL and the date it was checked, and "unknown" is kept as unknown rather than guessed.

This repository gives AI agents direct access to it (setup for every client: https://kitbay.app/agents/):

- **Kitbay MCP server**: a remote, read-only server at `https://kitbay.app/mcp` (streamable HTTP, no sign-in).
- **kitbay skill**: tells an agent when and how to use it: find a server or skill for a tool, show the user the facts, and install it only with their permission.

## Install

**Claude Code (plugin: server and skill together)**

```
/plugin marketplace add northlarkhq/kitbay-mcp
/plugin install kitbay@kitbay
```

**Any MCP client (server only):** add `https://kitbay.app/mcp` as a remote MCP server. For example, in Claude Code:

```
claude mcp add --transport http kitbay https://kitbay.app/mcp
```

[skills/kitbay/reference/clients.md](skills/kitbay/reference/clients.md) shows where other clients keep their MCP config.

**Skill only:** copy `skills/kitbay/` into your client's skills folder (for example `~/.claude/skills/kitbay/`). Without the server, the skill reads Kitbay's public pages.

## Tools

| Tool | What it answers |
|---|---|
| `search_listings` | Search servers and skills by text, or browse by tool, category or AI client; filter by type, official, can change data, needs credentials |
| `get_tool` | Is there a server or skill for a tool, and is one official? |
| `get_listing` | Every fact for one listing, each with its source URL and checked date |
| `get_install_config` | How to add one listing to one AI client, from the project's own documentation; credentials are placeholders |
| `list_categories` | Categories and capabilities, with counts |

All tools are read-only. Results come in relevance order, not a ranking. Kitbay records facts and does not audit code; check a project before you install it.

## Privacy

The server stores the text, filters and result count of searches and tool lookups, to learn what agents look for and do not find. It stores no IP address or client identity. Details: https://kitbay.app/privacy/

## Limits

60 requests a minute per IP address.

## Problems

Open an issue in this repository, or use https://kitbay.app/submit/ to suggest a project or report a listing.

## Licence

MIT (this repository: the skill, plugin and configuration files). Kitbay's data is described at https://kitbay.app/methodology/.
