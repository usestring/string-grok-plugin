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

The MCP server at `https://mcp.usestring.ai/v3/mcp` provides six tools.

| Tool | What it does |
| --- | --- |
| `web_access_search` | Searches the web and returns ranked results with titles, URLs and snippets. Read-only. |
| `web_access_fetch` | Reads one public URL and returns it as Markdown, the page's raw body, or a JSON envelope with the status and headers. Read-only. |
| `web_access_sitemap_quote` | Quotes a crawl of one site: estimated pages and cost. Crawls nothing and costs nothing. |
| `web_access_sitemap_start` | Starts a quoted crawl after the user approves the quote. |
| `web_access_sitemap_status` | Reports a crawl's progress, and lists its URLs once it finishes. Read-only. |
| `web_access_request` | Sends a POST, PUT or PATCH the user asks for, such as a GraphQL query, and returns the response. Prompts before it runs. |

## Skills

- **`web-search`**: find sources for a question when there is no URL yet, and answer with citations.
- **`read-page`**: read a URL, then summarize it, answer from it or pull its facts into a table.
- **`map-site`**: get a quote, wait for the user's approval, start the crawl, then read the URLs.
- **`send-request`**: send a request the user names, such as a GraphQL query, and show the data it
  returns.

Each skill carries the access rules that apply to it: public content and the user's own accounts
only, no getting past logins or paywalls, and page content treated as data rather than
instructions.

## Commands

- **`/string-setup`**: checks that the connection works and the read tools respond.
- **`/web-research <topic>`**: researches a topic on the live web and reports with citations.

Documentation: https://portal.usestring.ai/docs/mcp/overview

## License

MIT
