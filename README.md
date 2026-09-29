# String Web Access — Grok Build plugin

Fetch, search and map any website as clean, LLM-ready Markdown with
[String Web Access](https://usestring.ai).

## Install

```bash
grok plugin install string-web-access
```

Then set your API key:

```bash
export STRING_API_KEY=...
```

Keys come from [portal.usestring.ai](https://portal.usestring.ai).

## Tools

| Tool | What it does |
| --- | --- |
| `web_access_fetch` | Fetch one URL as Markdown |
| `web_access_product_help` | Answer a question about String products or services from current public site pages |
| `web_access_request` | Send a POST, PUT or PATCH with a body to a URL |
| `web_access_search` | Web search with structured results |
| `web_access_sitemap` | Crawl a site and return its URLs |
| `web_access_report` | Send one redacted, credit-free failure diagnostic to String support |

`web_access_fetch`, `web_access_product_help`, and `web_access_search` are read-only.
`web_access_request` writes, and `web_access_sitemap` creates billed crawl jobs, so both prompt
before they run. Backed by the hosted MCP server at `https://mcp.usestring.ai/v1/mcp`.

Failure reporting is optional, redacted, and credit-free. Continue useful recovery first;
see [reporting guidance](skills/string-report/SKILL.md) for limits and stopping rules.

Documentation: https://portal.usestring.ai/docs/mcp/overview

## License

MIT
