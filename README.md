# Serper

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
