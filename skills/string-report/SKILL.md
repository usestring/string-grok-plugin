---
name: string-report
description: |
  Report a failed String Web Access tool result to String support. Use automatically after
  web_access_fetch, web_access_request, web_access_search, or web_access_sitemap errors, times
  out, or returns output that is unusable for that tool's own step. An intermediate result the
  next call still consumes is not a failure. Redact credentials and personal data, report once,
  and never retry only to collect more diagnostic context.
---

# String failure reporting

Send one compact, safe diagnostic when a String Web Access tool fails.

## When to use

Call `web_access_report` after one of these tools errors, times out, or returns output that is
unusable for that tool's own step:

- `web_access_fetch`
- `web_access_request`
- `web_access_search`
- `web_access_sitemap`

Judge the output against the step it was called for, not against the user's final request. Search
results and sitemap URLs exist to feed the next call, and a successful write can return an empty
`204` body — none of those are failures. A block screen returned instead of the page, a truncated
body where content was expected, or a transport error is.

Report at most once for the failure. This report is authenticated with the configured String API
key, but it does not consume Web Access credits.

## Before calling

Include only what String support needs to investigate:

- the failed tool name
- a short error description
- optional compact request or response context

Remove Authorization and proxy-authorization headers, API keys, cookies, session tokens,
passwords, personal data, and unrelated conversation content. The report endpoint redacts common
credential forms again, but that server-side pass is a backstop rather than permission to send
secrets.

## Call it

```json
{
  "tool": "web_access_fetch",
  "error": "Timed out before the page returned content",
  "request": "{\"url\":\"https://example.com/article\"}",
  "response": "HTTP 504"
}
```

`request` and `response` are optional strings. Keep them short and credential-free.

## Never recurse

Never use `web_access_report` to report its own failure. If the report fails, stop reporting.
Do not repeat the original Web Access call only to gather more context for a report.
