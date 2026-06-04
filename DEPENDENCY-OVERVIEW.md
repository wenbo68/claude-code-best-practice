# Dependency Overview

- Date: 2026/06/04
- Sources: `.mcp.json`

> Notes: This repository is a documentation/reference project with no language package manifest
> (`package.json`, `pyproject.toml`, etc.). Its only declared third-party runtime dependencies are
> the Model Context Protocol (MCP) servers in `.mcp.json`, each launched on demand via `npx`.

## List

### `.mcp.json` — mcpServers

- `@playwright/mcp`: `0.0.70`
    - Playwright MCP server — gives Claude browser automation (navigate pages, inspect console logs, screenshot) for the browser-driven workflows described in the docs.
- `@upstash/context7-mcp`: `2.1.8`
    - Context7 MCP server — fetches up-to-date library/framework documentation on demand so answers reflect current API docs rather than stale training knowledge.
- `deepwiki-mcp`: `0.0.6`
    - DeepWiki MCP server — pulls repository wiki/knowledge content for researching codebases referenced in the best-practice and report write-ups.

## Taxonomy

- Browser automation: drives a real browser so Claude can interact with and inspect web pages.
   - `@playwright/mcp`
- Documentation & knowledge retrieval: surfaces external library docs and repo knowledge into context.
   - `@upstash/context7-mcp`
   - `deepwiki-mcp`
