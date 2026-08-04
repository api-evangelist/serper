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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Serper is the world's fastest and most affordable Google Search API, delivering real-time SERP data in 1-2 seconds via a simple REST interface. It supports web search, images, news, maps, places, videos, shopping, scholar, patents, and autocomplete — all returned as structured JSON. Widely used in AI agents, LLM pipelines, and SEO tooling, Serper uses a credit-based model with 2,500 free queries and volume pricing down to $0.30 per 1,000 requests.

**Website:** https://serper.dev  
**GitHub:** https://github.com/Serper-API  
**X:** https://x.com/serperapi  

## APIs

- **Serper Google Search API** — POST `https://google.serper.dev/search` — structured Google SERP results (web, images, news, maps, places, videos, shopping, scholar, patents, autocomplete) authenticated via `X-API-KEY` header.

## Authentication

API key passed as an HTTP header: `X-API-KEY: <your-key>`. Keys are available after creating an account at https://serper.dev.

## Pricing

Credit-based model. Credits are purchased in advance and valid for 6 months.

| Plan | Credits | Price | Per 1K |
|------|---------|-------|--------|
| Free Trial | 2,500 | $0 | — |
| Starter | 50,000 | $50 | $1.00 |
| Standard | 500,000 | $375 | $0.75 |
| Scale | 2,500,000 | $1,250 | $0.50 |
| Ultimate | 12,500,000 | $3,750 | $0.30 |

Requesting 100 results per page (non-default) doubles credit consumption.

## Rate Limits

Default limit on the Ultimate plan is 300 queries per second (~18,000/minute). Lower tiers have lower concurrency limits. Higher limits are available upon request.

## Resources

- [APIs.json](apis.yml)
- [Plans & Pricing](plans/serper-plans-pricing.yml)
- [Rate Limits](rate-limits/serper-rate-limits.yml)
- [FinOps](finops/serper-finops.yml)
