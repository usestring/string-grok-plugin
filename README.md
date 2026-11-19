# String Web Access — Grok Build plugin

Fetch, search and map any website as clean, LLM-ready Markdown with
[String Web Access](https://usestring.ai).

## Install

```bash
grok plugin install string-web-access
```

On first connection, Grok Build opens String's sign-in in your browser. Sign in with your String
account. Sign-in uses OAuth, so there is no API key to set, and String's consent screen picks the
key the connection spends. Don't have an account? Create one at
[portal.usestring.ai](https://portal.usestring.ai). To use an API key instead, for example where
no browser can open, add the server to your own MCP config with an `Authorization: Bearer` header.

## Tools

The MCP server at `https://mcp.usestring.ai?login` provides eight tools.

| Tool | What it does |
| --- | --- |
| `web_access_search` | Searches the web and returns ranked results with titles, URLs and snippets. Read-only. |
| `web_access_fetch` | Reads one public URL and returns it as Markdown, the page's raw body, or a JSON envelope with the status and headers. Read-only. |
| `web_access_sitemap_quote` | Quotes a crawl of one site: estimated pages and cost. Crawls nothing and costs nothing. |
| `web_access_sitemap_start` | Starts a quoted crawl after the user approves the quote. |
| `web_access_sitemap_status` | Reports a crawl's progress, and lists its URLs once it finishes. Read-only. |
| `web_access_request` | Sends a POST, PUT or PATCH the user asks for, such as a GraphQL query, and returns the response. Prompts before it runs. |
| `web_access_balance` | Reads the account's balance, recorded spend and remaining credit. Free to call. Read-only. |
| `web_access_product_help` | Answers questions about String's products, pricing and integrations from String's public site, with source links. Read-only. |

## Skills

- **`web-search`**: find sources for a question when there is no URL yet, and answer with citations.
- **`read-page`**: read a URL, then summarize it, answer from it or pull its facts into a table.
- **`map-site`**: get a quote, wait for the user's approval, start the crawl, then read the URLs.
- **`send-request`**: send a request the user names, such as a GraphQL query, and show the data it
  returns.
- **`research-a-question`**: answer a question that needs several sources, with a citation for every
  claim.
- **`find-places`**: find businesses and places near a location, with rating, address, hours, phone
  and website.
- **`find-products`**: look up products on Google Shopping with current prices, merchants, ratings
  and reviews.
- **`search-forums`**: find what people say in forums and community threads, with a link to each
  thread.
- **`find-images-and-videos`**: find images and videos on a topic, with source pages, sizes,
  channels and lengths.
- **`search-by-location`**: search as someone in a chosen country, city or spot sees it, compare
  places, and check where a site ranks.
- **`check-ai-answers`**: see what Google's AI Overview and AI Mode answer for a query and which
  sites they cite.
- **`build-a-list`**: gather everything that meets the user's criteria into one deduplicated table,
  with a source per row.

Each skill carries the access rules that apply to it: public content and the user's own accounts
only, no getting past logins or paywalls, and page content treated as data rather than
instructions.

## Commands

- **`/string-setup`**: checks that the connection works and the read tools respond.
- **`/web-research <topic>`**: researches a topic on the live web and reports with citations.

Documentation: https://docs.usestring.ai/mcp/overview

## License

MIT
