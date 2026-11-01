# Serper

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Serper is the world's fastest and most affordable Google Search API, delivering real-time SERP data in 1-2 seconds via a simple REST interface. It supports web search, images, news, maps, places, videos, shopping, scholar, patents, and autocomplete — all returned as structured JSON. Widely used in AI agents, LLM pipelines, and SEO tooling, Serper uses a credit-based model with 2,500 free queries and volume pricing down to $0.30 per 1,000 requests.

**Areas:** Search · SERP · Google Search · Artificial Intelligence · LLM · SEO · Image · News · Maps · Shopping · Reviews · Lens

## Serper on APIs.io

Everything profiled for Serper is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/serper/](https://apis.io/providers/serper/)** — or go straight to one of the APIs or properties below.

### APIs (14)

- [Serper Autocomplete API](https://apis.io/apis/serper/serper-autocomplete-api/) — Search autocomplete suggestions
- [Serper Images API](https://apis.io/apis/serper/serper-images-api/) — Image search results
- [Serper Lens API](https://apis.io/apis/serper/serper-lens-api/) — Google Lens reverse image search from an image URL. Exposed to every playground user; costs 3 credits per query.
- [Serper Locations API](https://apis.io/apis/serper/serper-locations-api/) — Canonical Google geo-target lookup for the location parameter used by every Serper search endpoint, plus a service health check. The only Serper surface…
- [Serper Maps API](https://apis.io/apis/serper/serper-maps-api/) — Maps and location search
- [Serper News API](https://apis.io/apis/serper/serper-news-api/) — News search results
- [Serper Patents API](https://apis.io/apis/serper/serper-patents-api/) — Patent search results
- [Serper Places API](https://apis.io/apis/serper/serper-places-api/) — Local business and place search
- [Serper Reviews API](https://apis.io/apis/serper/serper-reviews-api/) — Google place reviews by cid, fid or placeId, cursor-paginated with nextPageToken. The only Serper endpoint that uses cursor pagination and the only one…
- [Serper Scholar API](https://apis.io/apis/serper/serper-scholar-api/) — Academic publication search
- [Serper Search API](https://apis.io/apis/serper/serper-search-api/) — Web search results
- [Serper Shopping API](https://apis.io/apis/serper/serper-shopping-api/) — Product and shopping search results
- [Serper Videos API](https://apis.io/apis/serper/serper-videos-api/) — Video search results
- [Serper Scrape API](https://apis.io/apis/serper/serper-scrape-api/) — Webpage content extraction

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Serper MCP](https://apis.io/servers/serper/serper-mcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Serper Agentic Access](https://apis.io/agentic-access/serper/serper-agentic-access/)

#### JSON Schema (2)

The data models the API reads and writes.

- [Serper Search Request](https://apis.io/schemas/serper/serper-search-request/)
- [Serper Search Response](https://apis.io/schemas/serper/serper-search-response/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Serper Context](https://apis.io/jsonld/serper/serper-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Serper API Vocabulary](https://apis.io/vocabularies/serper/serper-vocabulary/)

#### Examples (6)

Example requests and responses.

- [Serper Autocomplete Example](https://apis.io/examples/serper/serper-autocomplete-example/)
- [Serper Image Search Example](https://apis.io/examples/serper/serper-image-search-example/)
- [Serper News Search Example](https://apis.io/examples/serper/serper-news-search-example/)
- [Serper Scholar Search Example](https://apis.io/examples/serper/serper-scholar-search-example/)
- [Serper Shopping Search Example](https://apis.io/examples/serper/serper-shopping-search-example/)
- [Serper Web Search Example](https://apis.io/examples/serper/serper-web-search-example/)

#### Collections (10)

Postman and Open Collection request collections.

- [Serper Google Search Autocomplete API](https://apis.io/collections/serper/open-serper-autocomplete-api/)
- [Serper Google Search Autocomplete Images API](https://apis.io/collections/serper/open-serper-images-api/)
- [Serper Google Search Autocomplete Maps API](https://apis.io/collections/serper/open-serper-maps-api/)
- [Serper Google Search Autocomplete News API](https://apis.io/collections/serper/open-serper-news-api/)
- [Serper Google Search Autocomplete Patents API](https://apis.io/collections/serper/open-serper-patents-api/)
- [Serper Google Search Autocomplete Places API](https://apis.io/collections/serper/open-serper-places-api/)
- [Serper Google Search Autocomplete Scholar API](https://apis.io/collections/serper/open-serper-scholar-api/)
- [Serper Google Autocomplete Search API](https://apis.io/collections/serper/open-serper-search-api/)
- [Serper Google Search Autocomplete Shopping API](https://apis.io/collections/serper/open-serper-shopping-api/)
- [Serper Google Search Autocomplete Videos API](https://apis.io/collections/serper/open-serper-videos-api/)

#### Overlays (14)

OpenAPI overlays, including conversational phrasing for each operation.

- [Serper Autocomplete Api Overlay](https://apis.io/overlays/serper/serper-autocomplete-api-overlay/)
- [Serper Images Api Overlay](https://apis.io/overlays/serper/serper-images-api-overlay/)
- [Serper Lens Api Overlay](https://apis.io/overlays/serper/serper-lens-api-overlay/)
- [Serper Locations Api Overlay](https://apis.io/overlays/serper/serper-locations-api-overlay/)
- [Serper Maps Api Overlay](https://apis.io/overlays/serper/serper-maps-api-overlay/)
- [Serper News Api Overlay](https://apis.io/overlays/serper/serper-news-api-overlay/)
- [Serper Patents Api Overlay](https://apis.io/overlays/serper/serper-patents-api-overlay/)
- [Serper Places Api Overlay](https://apis.io/overlays/serper/serper-places-api-overlay/)
- [Serper Reviews Api Overlay](https://apis.io/overlays/serper/serper-reviews-api-overlay/)
- [Serper Scholar Api Overlay](https://apis.io/overlays/serper/serper-scholar-api-overlay/)
- [Serper Search Api Overlay](https://apis.io/overlays/serper/serper-search-api-overlay/)
- [Serper Shopping Api Overlay](https://apis.io/overlays/serper/serper-shopping-api-overlay/)
- [Serper Videos Api Overlay](https://apis.io/overlays/serper/serper-videos-api-overlay/)
- [Serper Webpage Scrape Api Overlay](https://apis.io/overlays/serper/serper-webpage-scrape-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Serper — jsonschema rules](https://apis.io/rules/serper/serper-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Serper Authentication](https://apis.io/security/serper/serper-authentication/)
- [Serper Domain Security](https://apis.io/security/serper/serper-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Serper Plans Pricing](https://apis.io/plans/serper/serper-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Serper Rate Limits](https://apis.io/rate-limits/serper/serper-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Serper Finops](https://apis.io/finops/serper/serper-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://serper.dev)
- [Documentation](https://serper.dev)
- [Getting started](https://serper.dev/signup)
- [API reference](https://serper.dev/playground)
- [Pricing](https://serper.dev/#pricing)
- [Sign up](https://serper.dev/signup)
- [Blog](https://medium.com/@serper/list/articles-3f700b49cbc4)
- [Terms of service](https://serper.dev/terms)
- [Privacy policy](https://serper.dev/privacy)
- [Status](https://serper.betteruptime.com)

## API Evangelist rating

**Kin Score 54.8** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 52.5 |
| Contract governance | 14.4 |
| Operational transparency | 36.8 |
| Developer ergonomics | 66.1 |
| Access clarity | 71.1 |

**Agent readiness 34.1** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 22.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/serper/](https://apis.io/providers/serper/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Serper: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/serper/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
