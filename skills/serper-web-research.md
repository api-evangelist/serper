---
name: serper-web-research
description: Ground an answer in live web sources — run a Google web search through Serper, pick the best results, and scrape the winning pages into markdown for citation.
api: serper
generated: '2026-08-13'
method: generated
source: openapi/serper-search-api-openapi.yml, openapi/serper-webpage-scrape-api-openapi.yml, conventions/serper-conventions.yml
operations:
  - webSearch
  - scrapeWebpage
  - listLocations
---

# Web research with Serper

Use this when you need current, citable web content rather than recalled knowledge.
Serper does not cache, so every call is a live Google query.

## Before you start

- Get a key at https://serper.dev/api-keys. Send it as `X-API-KEY`. Never put it in a
  query string — Serper accepts `?apiKey=` but that leaks the credential into logs.
- Budget: `webSearch` costs 1 credit. `scrapeWebpage` costs 2 credits normally and 6 or
  10 for hard pages. A three-page research pass is roughly 7 credits, not 4. Failed
  calls are not billed.

## Step 1 — search

`POST https://google.serper.dev/search` (operation `webSearch`)

```json
{ "q": "openapi overlay specification 1.0", "gl": "us", "hl": "en", "num": 10 }
```

- If the question is regional, resolve the location first with `listLocations`:
  `GET https://api.serper.dev/locations?q=amsterdam&limit=25` (no key required) and pass
  the returned `canonicalName` as `location`.
- If the question is time-sensitive, add `tbs`: `qdr:d` (past day), `qdr:w`, `qdr:m`.
- Read `answerBox` and `knowledgeGraph` first — when present they often answer the
  question without a scrape, saving credits.
- Treat every top-level block as optional. `organic` is not guaranteed to be present.

## Step 2 — choose what to read

Rank `organic[]` by `position`, but drop results whose `snippet` already contains the
answer. Only scrape when you need the full text, a quote, or a figure. Positions are
per-page, not global — if you paginate with `page`, compute absolute rank yourself.

## Step 3 — scrape the winners

`POST https://scrape.serper.dev` (operation `scrapeWebpage`)

```json
{ "url": "https://spec.openapis.org/overlay/v1.0.0.html", "includeMarkdown": true }
```

- `includeMarkdown: true` is what you want for citation. Add `includeLinks` only if you
  intend to crawl further.
- The response reports the credits that call consumed — log it if you are tracking spend.
- Scrape at most the top 2-3 results. Scraping the whole page of 10 costs more than the
  search that found them, by a factor of twenty or more.

## Step 4 — cite

Carry `title` and `link` from the `organic` entry through to your answer. Serper returns
no stable identifier for any result, so the URL is the only durable key you have.

## Failure handling

- `403 {"message":"Unauthorized. Sign up for a free account.","statusCode":403}` — the
  key is missing or wrong. The gateway returns 403, not 401, and sends no
  `WWW-Authenticate` header.
- `429` — either the account's QPS ceiling was exceeded or the credit balance hit zero.
  Serper sends no `Retry-After` and no `RateLimit-*` headers, so back off on your own
  schedule: exponential with jitter, and check the balance in the dashboard if 429s
  persist rather than escalate.
- There is no request ID in any response. If you need to report a problem to
  support@serper.dev, capture the request body and timestamp yourself.

## Batching

If you have many independent queries, send an ARRAY of up to 100 query objects to
`/search` in one call. It costs 3x the single-query rate — cheaper than 100 round trips
in latency, more expensive in credits than 100 separate 1-credit calls. Use it for
latency, not for savings.
