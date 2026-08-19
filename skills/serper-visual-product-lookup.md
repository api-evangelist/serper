---
name: serper-visual-product-lookup
description: Identify a product from an image URL with Serper's Lens endpoint, then price it across retailers with a shopping search.
api: serper
generated: '2026-08-13'
method: generated
source: openapi/serper-lens-api-openapi.yml, openapi/serper-shopping-api-openapi.yml, openapi/serper-images-api-openapi.yml, rate-limits/serper-rate-limits.yml
operations:
  - lensSearch
  - shoppingSearch
  - imageSearch
---

# Visual product lookup with Serper

Start from a picture, end with prices. Two calls, and both are above the base rate — this
is one of the more expensive flows in Serper's catalog, so check the budget before you
loop it.

## Budget

- `lensSearch` — **3** credits per call.
- `shoppingSearch` — **2** credits per call.
- `imageSearch` — 1 credit, or **2** if you ask for `num` > 10.

A single identify-then-price pass is 5 credits, not 2.

## Step 1 — identify from the image

`POST https://google.serper.dev/lens` (operation `lensSearch`)

```json
{
  "url": "https://example.com/photo-of-the-shoe.jpg",
  "gl": "us",
  "hl": "en"
}
```

- `url` must be a publicly reachable image URL. Serper's Lens surface takes a URL, not an
  upload — if your image is local, host it first.
- `location` and `tbs` are also accepted, matching the rest of the search family.
- Serper publishes no response schema for this endpoint, so read defensively: pull the
  strongest product name or title you can find and treat every field as optional.

## Step 2 — price it

`POST https://google.serper.dev/shopping` (operation `shoppingSearch`)

```json
{ "q": "<product name from step 1>", "gl": "us", "hl": "en", "num": 40 }
```

Serper's playground offers `40` as the result count for shopping — that is the value the
provider itself uses, and it does not carry the images-style doubling.

## Step 3 — optional visual confirmation

`POST https://google.serper.dev/images` (operation `imageSearch`) with the product name
gives you comparison imagery to confirm you matched the right item. Keep `num` at 10:
going to 100 doubles this call's cost.

## Rules that bite here

- Nothing is cached by Serper. If you run the same image twice, you pay twice.
- Mini-batch multiplies by 3, so batching a set of images costs 9 credits per image on
  Lens. Batch for latency only.
- `403` means the key is bad; `429` means QPS or an empty balance. No `Retry-After` is
  sent. Failed calls are not billed.
- No result in any of these responses carries a Serper identifier — dedupe by `link`.
