---
description: Check that String Web Access is connected and its read tools respond
---

# String Web Access setup check

1. If the String tools are not available or report a missing or invalid key, tell the user to
   create a key at https://portal.usestring.ai and export it as `STRING_API_KEY`, then stop.
2. Read `https://example.com` with `web_access_fetch` and confirm Markdown comes back.
3. Run one `web_access_search` for a simple query and confirm the results carry `title`, `url` and
   `snippet`.
4. Report which tools responded. If both fail, the key or the connection is likely the cause.
   Report a partial failure tool by tool. Do not retry failures in a loop.

Do not call `web_access_request` here. It sends whatever request it is given, and a connectivity
check has no business sending one nobody asked for. The crawl tools are skipped for the same
reason: quoting a crawl is free, but starting one spends money.

Keep it to a few lines. This is a connectivity check, not a demo.
