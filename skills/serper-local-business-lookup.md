---
name: serper-local-business-lookup
description: Find a local business through Serper's places or maps search, then pull its Google reviews using the place identifier the first call returns.
api: serper
generated: '2026-08-13'
method: generated
source: openapi/serper-places-api-openapi.yml, openapi/serper-maps-api-openapi.yml, openapi/serper-reviews-api-openapi.yml, data-model/serper-data-model.yml
operations:
  - placesSearch
  - mapsSearch
  - placeReviews
  - listLocations
---

# Local business lookup with Serper

This is the one genuine two-call flow in Serper's surface: a place lookup returns a
Google identifier, and that identifier is the input to the reviews endpoint. Nothing
else in Serper joins across requests.

## Budget first

`placesSearch` is 1 credit. `mapsSearch` is **3** credits — three times the price for a
similar-looking result, so choose deliberately. `placeReviews` is 1 credit per page.

Use `placesSearch` when you have a name and a rough area. Use `mapsSearch` when you have
coordinates (`ll`), a `placeId` or a `cid` and want map-shaped results.

## Step 1 — pin the location

`GET https://api.serper.dev/locations?q=brooklyn&limit=25` (operation `listLocations`,
no API key required). Pass the returned `canonicalName` — for example
`"New South Wales,Australia"` — as the `location` parameter. Guessing a free-text
location string is the most common way this flow returns the wrong city.

## Step 2 — find the place

`POST https://google.serper.dev/places` (operation `placesSearch`)

```json
{ "q": "coffee roaster", "location": "Brooklyn,New York,United States", "gl": "us", "hl": "en" }
```

Or, with coordinates, `POST https://google.serper.dev/maps` (operation `mapsSearch`):

```json
{ "q": "coffee roaster", "ll": "@40.6782,-73.9442,14z", "hl": "en" }
```

Capture `placeId`, `cid` or `fid` from the result you want. These are Google's
identifiers, not Serper's — they are stable across providers.

## Step 3 — pull reviews

`POST https://google.serper.dev/reviews` (operation `placeReviews`)

```json
{ "placeId": "ChIJN1t_tDeuEmsRUsoyG83frY4", "sortBy": "mostRelevant", "gl": "us", "hl": "en" }
```

- Any one of `placeId`, `cid` or `fid` identifies the place. You do not need all three.
- Pagination here is a **cursor**, not `page`/`num`: take `nextPageToken` from the
  response and send it back to get the next page. This is the only endpoint in Serper
  that works this way, so do not reuse your search-pagination code.
- `topicId` filters to a Google-assigned review topic when you only want, say, reviews
  mentioning service.
- Mini-batch is **not supported** on `/reviews`. Do not send an array here.

## Stopping

There is no total-count field. Keep requesting pages until `nextPageToken` is absent,
and set your own hard cap — each page is a credit, and a busy place has a lot of pages.

## Failure handling

`403` means the key is bad. `429` means QPS or credits. No `Retry-After` header exists;
back off on your own schedule. Credits are only deducted on success, so a retry after an
error costs nothing extra.
