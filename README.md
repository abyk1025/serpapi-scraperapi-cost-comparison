# SerpAPI alternatives: what 1,000 searches really costs, which plans cap your hourly quota, and when one API for results plus page content wins (full plan table)

At the $100-a-month mark, 1,000 Google searches cost anywhere from $0.45 to $15.00 depending on the vendor, and the spread has almost nothing to do with result quality. Most people shopping for SerpAPI alternatives need one of three things: raw Google rankings as JSON, AI Overview or AI Mode output, or the landing page text sitting behind each link. ScraperAPI is built for the third case, and its pricing only becomes legible once you convert credits into actual search calls.

This breakdown groups vendors by those three needs, puts every price on the same per-1,000 basis, and flags the charges that never appear in the headline rate: hourly quota caps, credit expiry, AI Overview surcharges and one-hour caching.

> **Quick answer:** ScraperAPI runs Google results and page scraping off one credit pool. The $49 Hobby plan carries 100,000 credits a month, which is roughly 4,000 Google SERP calls at 25 credits each, or 100,000 ordinary page fetches. Buy it when you need the page text as well as the links. For pure rankings it is not the cheap option: Hobby works out to $12.25 per 1,000 searches, and the $149 Startup tier ($3.73 per 1,000) is where the SERP rate becomes competitive. 👉 [See ScraperAPI's plans and start the free trial](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## ScraperAPI's plans, and what one credit actually buys

ScraperAPI prices everything in credits, and the credit cost of a request depends on the target. A standard page costs 1 credit. Google and Bing, including subdomains, cost 25. Amazon, Walmart and eBay cost 5, LinkedIn costs 30. Turning on JavaScript rendering, premium proxies or bot-protection bypass adds 10 credits each, and ultra premium mode adds 30. Every response reports its own cost in an `sa-credit-cost` header, and you can cap any single request with a `max_cost` parameter.

That 25-credit rate is the number that matters for SERP work, because it sets your real cost per search.

| Plan | Credits/month · concurrent threads | Price | Google SERP calls · effective $/1,000 | Sign up |
| --- | --- | --- | --- | --- |
| Hobby | 100,000 · 20 | $49/mo ($44.10 annual) | ~4,000 · $12.25 | [$49/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | 1,000,000 · 50 | $149/mo ($134.10 annual) | ~40,000 · $3.73 | [$149/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | 3,000,000 · 100 | $299/mo ($269.10 annual) | ~120,000 · $2.49 | [$299/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | 5,000,000 · 200 | $475/mo ($427.50 annual) | ~200,000 · $2.38 | [$475/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | 10,500,000 · 300 | $975/mo ($877.50 annual) | ~420,000 · $2.32 | [$975/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 · 500 | $1,975/mo ($1,777.50 annual) | ~860,000 · $2.30 | [$1,975/mo](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | 22,000,000+ · 500+ | Custom | Custom | [Request pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

Four plan differences sit outside the price column:

- **Geotargeting.** Hobby and Startup cover the US and EU only. Country-level targeting across 50+ countries starts at Business, which matters if you track localized results in Asia, Latin America or the Middle East.
- **Credit overrun.** Hobby through Professional can auto-upgrade to the next tier when credits run out. True pay-as-you-go overflow is limited to Scaling and above, with a monthly cap you set. On the lower tiers, exhaustion means requests stop until renewal.
- **Analytics history.** 30 days on Hobby and Startup, unlimited from Business upward.
- **Concurrency.** Exceeding your thread limit returns HTTP 429 and no charge; the request is rejected rather than queued.

The page-fetch side of the same pool is where the economics flip. At 1 credit per standard page, Hobby covers 100,000 pages for $49, or about $0.49 per 1,000. A pipeline that pulls one Google result page and then ten product pages per keyword spends 25 credits on the search and 10 on the fetches, so the SERP call is the dominant cost, not the scraping.

## The same 1,000 searches, priced side by side

Per-1,000 pricing only means something at a stated tier, because nearly every vendor slides the rate with volume. The figures below sit as close to $100/month as each vendor's ladder allows.

| Provider | Price per 1,000 Google searches | Billing rule | AI Overview |
| --- | --- | --- | --- |
| Scrapingdog | $0.45 (Light) · $0.90 (Advance) | Failed requests never charged | Field in the response |
| DataForSEO | $0.60 queued · $1.20 priority · $2.00 live | Per task; overview doubles the base price | Paid parameter |
| Serper | $1.00 on a $50 top-up (50,000 credits) | Not stated on its site | Not listed |
| String | $1.00 (Growth: $100 fee plus usage) | Successful requests only | Same call, bills as 2 searches |
| Bright Data | $1.50 pay as you go | Successful requests only | Browser flag, +5–10s |
| SearchApi | $2.86 ($100 for 35,000) | Only HTTP 200 responses billed | Own endpoint, one request |
| Apify | $4.50 free plan · $2.45 business plan | Per extracted result | AI Mode extraction add-on |
| ScraperAPI | $12.25 (Hobby) · $3.73 (Startup) | Credit-based, shared with page scraping | Not documented |
| SerpApi | $10–$25 depending on tier ($15 on the $75 Developer plan) | Successful searches only, cache free | Token fetch counts as 2 searches |

Two caveats on the table. The Apify numbers come from a vendor post dated October 2025 and may have moved since. SerpApi's range is real rather than sloppy: a $25 entry plan works out near $25 per 1,000, a $75 Developer plan at $15, and higher tiers land closer to $10, so quoting a single number for SerpApi misrepresents it either way.

Serper's pricing page is client-rendered, and at least one competitor claims it could not be verified; the $1.00 figure above comes from a third-party check in October 2026 and is worth confirming on the page before you commit budget. Five of the seven vendors that publish a billing rule charge only successful requests. Serper and DataForSEO do not state a failed-request rule on the pages reviewed, which is a question to ask support rather than assume.

## The costs that never make it into the headline rate

**Hourly quota caps.** SerpApi limits most plans to 20% of the monthly quota per hour, and unused queries do not roll over. That cap is widely reported. What gets left out is that SearchApi applies the same 20%-per-hour ceiling, so switching vendors does not automatically remove the throttle. If your workload is bursty (a nightly rank check of 30,000 keywords), a 20% hourly rule turns a one-hour job into five.

**Credit expiry.** Serper credits expire after six months. cloro resets credits monthly. DataForSEO balances never expire. Scrapingdog shares one credit pool between SERP calls and general scraping, so a heavy scraping month silently eats your search budget. These rules change the real cost far more than a cent or two on the per-1,000 rate.

**AI Overview billing, four different ways.** SerpApi and String count an overview fetched by token as two searches. DataForSEO doubles the base price for an async overview. SearchApi returns the overview inside the same request for one charge. Bright Data needs a browser flag that adds 5 to 10 seconds per request, and the company says overviews appear on roughly 15–20% of queries, which makes the cost per captured overview several times the advertised per-request rate. If AI Overview coverage is the reason you are switching, price it per captured overview, not per request.

**Caching.** SerpApi serves a repeat query from a one-hour cache for free unless you set `no_cache`. On a dashboard that refreshes every few minutes this cuts spend noticeably. On a rank tracker that runs twice an hour, it means you are partly paying to watch a cached page.

**Published reliability.** SerpApi's own metrics, as displayed on 19 October 2026, show 93.658% average success and 9.06 seconds average response time over the previous 30 days. That is a useful baseline for judging any replacement's claims, since most competitors publish nothing comparable.

## Google's own results move faster than your billing cycle

A test published by String, a vendor that sells a competing Google API, ran the same 56 questions twice, 31 minutes apart. The top results changed order on 50 of the 56. On 55 of the 56 questions Google returned fewer than ten organic results, with a median of eight, and 54 carried an AI Overview.

Treat the source with the usual discount, since the company benefits from the conclusion. The implication still holds: if Google's top ten reshuffles inside half an hour, a plan priced at $15 per 1,000 for maximum positional fidelity is buying precision the source data does not have. Sample the same keyword several times a day and store the timestamps, or accept a coarser picture and spend the difference on coverage.

That test also explains why AI Overview handling has become the deciding feature for SEO and AI-visibility teams. If 54 of 56 commercial queries carry an overview, an API without overview output is returning a partial page.

## When ScraperAPI is the wrong pick

It has five Google endpoints (Search, Shopping, Maps, News, Jobs) behind one key and one bill, which covers most SEO and market-research work. It does not cover everything.

- **Google Flights, Hotels, Scholar or Play Store.** SerpApi parses those verticals; ScraperAPI's documented Google coverage stops at the five endpoints above.
- **ChatGPT, Gemini or Copilot answer text.** SearchApi exposes those as engines under one request pattern, Bright Data sells them at $1.50 per 1,000 records, and ScrapingBee returns ChatGPT and Gemini answers at 15 credits each, though its AI Mode access is mobile-only.
- **The cheapest possible Google JSON.** DataForSEO's standard queue at $0.60 per 1,000 or Serper at $1.00 will undercut every credit-based scraper, at the cost of queue latency (DataForSEO targets completion within 45 minutes on the standard queue).
- **Semantic search over a proprietary index.** Exa runs its own crawl at $4–$7 per 1,000 with page text included, and cannot return Google rank positions or local pack data because it does not query Google.
- **AI Overview extraction today.** ScraperAPI's documentation reviewed for this piece does not describe an overview or AI Mode field. If that data is a requirement, confirm support before buying rather than assuming it arrives with the SERP endpoint.

That last point is the honest boundary. ScraperAPI's advantage is one contract for results plus page content plus geotargeting, not the widest engine list or the lowest per-search price. 👉 [Check the $149 Startup plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) if your volume lands near 40,000 searches a month, since that tier cuts the per-1,000 rate by two thirds versus Hobby.

## Legal exposure, and who actually covers it

Google sued SerpApi in December 2025; the case was dismissed in July 2026 and Google filed again. SerpApi sued SearchApi in January 2026. Against that backdrop, SerpApi includes up to $2 million in US legal protection from its $150 Production tier, and SearchApi offers a similar guarantee from its $100 Production plan. Most other vendors place compliance responsibility on the customer. If your organization needs contractual cover for scraping Google, the guarantee is tied to specific tiers, and it is worth reading the terms rather than the pricing page.

## FAQ

**Does the 20% hourly cap really change anything?**
Only for bursty workloads. A steady 10,000 searches spread across a month never touches it. A monthly batch job that runs in one night hits the ceiling within the first hour on both SerpApi and SearchApi and finishes over five hours instead.

**Why does an AI Overview cost two searches on some APIs?**
Because the overview arrives as a separate, token-bearing payload that the vendor fetches in a second request. SerpApi and String bill it that way; SearchApi returns it inline for one charge; DataForSEO doubles the page price. On a dataset where 90%+ of queries carry an overview, that difference can nearly double your bill.

**What happens to unused credits at the end of the month?**
It depends entirely on the vendor. Serper expires them after six months, cloro clears them every month, DataForSEO balances persist indefinitely, and ScraperAPI pauses scraping until credits renew unless auto-upgrade or pay-as-you-go is enabled.

**Is the free trial enough to evaluate parsing quality?**
Enough to validate the JSON shape on a few dozen queries, not enough to benchmark success rates. At 25 credits per Google search, trial credits disappear quickly. Pull 40–80 real keywords from your own list, check the fields you depend on, then decide.

**Can I get Google Shopping and Maps from the same account?**
Yes. ScraperAPI exposes Search, Shopping, Maps, News and Jobs endpoints under one API key and one credit balance, which removes the second contract most SEO teams end up buying.

## How to choose

Match the vendor to the job rather than the price list:

- **Pure Google JSON at the lowest rate:** DataForSEO's queue or Serper.
- **Google verticals beyond web search:** SerpApi.
- **Consumer AI answers from ChatGPT, Gemini or Copilot:** SearchApi, Bright Data or ScrapingBee.
- **Results plus the page behind each result, one bill:** ScraperAPI, with Startup as the first tier where the SERP rate makes sense.
- **Semantic retrieval over an independent index:** Exa.

Two things to confirm before you enter a card number. First, the credit or token cost of one Google SERP call on your specific plan, including whether rendering and premium proxies stack on top of it. Second, whether failed requests are billed, because a 93% success rate on 100,000 searches means 7,000 paid-for failures if they are.

👉 [Compare ScraperAPI's plans against your monthly search volume](https://www.scraperapi.com/pricing/?fp_ref=coupons)
