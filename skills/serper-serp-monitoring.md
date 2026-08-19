---
name: serper-serp-monitoring
description: Track a keyword set's Google ranking and news coverage over time with Serper, using mini-batch to cut round trips and controlling credit burn deliberately.
api: serper
generated: '2026-08-13'
method: generated
source: openapi/serper-search-api-openapi.yml, openapi/serper-news-api-openapi.yml, conventions/serper-conventions.yml, rate-limits/serper-rate-limits.yml
operations:
  - webSearch
  - newsSearch
  - autocomplete
---

# SERP monitoring with Serper

A repeated, scheduled read of the same keyword set. The whole difficulty here is cost
control, because Serper never caches — a daily run over 500 keywords is 500 live Google
queries every day, every day.

## Step 1 — run the keyword set

`POST https://google.serper.dev/search` (operation `webSearch`), one object per keyword:

```json
{ "q": "api governance platform", "gl": "us", "hl": "en", "num": 10, "page": 1 }
```

Use **mini-batch** for the round-trip savings: send an ARRAY of up to 100 query objects
to the same path in one call.

```json
[
  { "q": "api governance platform", "gl": "us" },
  { "q": "openapi linting tool",   "gl": "us" }
]
```

Read the trade honestly before you turn it on: mini-batch costs **3x** the single-query
rate. It buys you latency and fewer connections, not credits. If your run is not
latency-sensitive, 100 separate 1-credit calls is the cheaper path — subject to your
plan's QPS ceiling (50 on Starter, 100 Standard, 200 Scale, 300 Ultimate).

## Step 2 — hold the variables still

A rank comparison is only meaningful if the query origin is identical between runs. Pin
`gl`, `hl` and `location` explicitly and store them alongside the result. Note that
Serper's own client drops `gl` and `hl` from the wire when they equal `us`/`en`, so an
absent value in a stored request means the default, not "unset".

Set `autocorrect: false` when you are tracking an exact term you do not want Google to
silently rewrite.

## Step 3 — record rank correctly

`position` in `organic[]` is **per page**, not global. If you paginate with `page`,
compute absolute rank yourself:

```
absolute_rank = ((page - 1) * num) + position
```

Serper attaches no stable identifier to a result, so diff runs by `link`.

## Step 4 — add news and query expansion

- `POST /news` (operation `newsSearch`) with `tbs: "qdr:d"` gives the last day's coverage
  for the same terms. 1 credit each.
- `POST /autocomplete` (operation `autocomplete`) is 1 credit and returns what Google
  suggests for a prefix — a cheap way to grow the keyword set from real demand rather
  than guesses.

## Cost table you should encode in the job

- search, news, videos, places, scholar, patents, autocomplete: 1 credit
- images: 1 credit, **2** when `num` > 10
- shopping: 2 credits
- maps and lens: 3 credits
- mini-batch: 3x whatever the above would be
- credits expire 6 months after purchase — size the package to the 6-month run rate, not
  to the annual one

## Failure handling

- `429` is the only exhaustion signal, and it means either QPS or a zero balance. Serper
  publishes no `Retry-After`, no `RateLimit-*` headers and no balance field on search
  responses, so a long-running job must track its own consumption and alert before the
  balance runs out. When credits hit zero, Serper stops accepting queries outright.
- Failed calls are not billed, so retries are credit-free.
- Check https://serper.betteruptime.com before treating a spike in errors as your bug.
