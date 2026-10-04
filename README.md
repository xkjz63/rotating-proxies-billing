# buy rotating proxies: per-IP vs per-GB billing, rotation modes, and how to test a pool before you commit

Most people shopping for rotating proxies start with the wrong question. They compare pool sizes, success rates and review scores, then get a first invoice that has nothing to do with any of it.

The number that decides what you pay is the billing model, and the billing model has to match your traffic pattern. The same provider can charge you 5x more or 5x less for identical work depending on which of its two products you pick. So before you compare vendors, work out which of these is actually you:

- **You need many different IPs, each used briefly.** Scraping SERPs, price checks, ad verification, anything where every request should look like it came from somewhere new. Volume is measured in requests, not gigabytes.
- **You need a small number of IPs held open for hours.** Logged-in accounts, long crawls, uploads. Volume is measured in bytes, and it can be huge.
- **Both, on different projects.** This is more common than people admit, and it's the case bundles exist for.

9Proxy is a residential proxy platform that sells both models side by side — per IP with unlimited bandwidth, or per GB with unlimited endpoints — across 20M+ residential IPs in 90+ countries, HTTP/HTTPS and SOCKS5. Because it publishes both price grids, it makes a decent test case for the whole "should I buy rotating proxies by the IP or by the gigabyte" question. That's what this article walks through.

## Three numbers that predict your bill better than any review

Before you look at a single price, estimate these:

1. **Requests per run.** 10,000 product pages, 400 SERP queries, whatever your job actually is.
2. **Average bytes transferred per request.** The raw HTML is the small part. Images, fonts, scripts and tracking pixels are the rest, and they only load if you're rendering pages in a browser.
3. **How long each session has to stay on one IP.** One request, or two minutes, or six hours.

Now the arithmetic. Ten thousand pages with an average of 500KB each is roughly 5GB of traffic. On 9Proxy's entry GB tier at $3.00/GB, that's about $15. At a $4/GB provider, closer to $20. At $6/GB, roughly $30. Same job, double the cost, and that's before retries and the CAPTCHA pages you pay for whether they return data or not. Browser-based collection usually overshoots a raw HTML estimate considerably once JavaScript, images and failed retries are counted, so treat any bandwidth estimate as a floor rather than a budget.

Flip it around: if that same job runs through 30 IPs with unlimited bandwidth, a per-GB bill is irrelevant. What matters is how much IP inventory those 30 sessions consume and how long each IP stays alive.

## Per-IP billing: unlimited traffic, finite inventory

On an IP-based plan you buy a fixed number of residential IPs and pay nothing for the bytes that flow through them. Each IP lives a few hours up to around 24 hours depending on the address, unused IPs don't expire, and the per-IP price drops sharply as you buy more.

That last point matters more than the headline rate. Here's the current grid after the 1 June 2026 adjustment, which raised IP and bundle prices while leaving GB pricing untouched:

| Package | Total cost | Effective per IP | Buy |
| --- | --- | --- | --- |
| 100 IPs | $24 | $0.24 | [ Buy the 100 IP pack](https://bit.ly/9-Proxy) |
| 500 IPs | $72 | $0.144 | [ Buy 500 IPs](https://bit.ly/9-Proxy) |
| 1,000 IPs (+500 bonus) | $126 | $0.084 | [ Buy the 1,500 IP pack](https://bit.ly/9-Proxy) |
| 2,500 IPs | $210 | $0.084 | [ Buy 2,500 IPs](https://bit.ly/9-Proxy) |
| 5,000 IPs | $360 | $0.072 | [ Buy 5,000 IPs](https://bit.ly/9-Proxy) |
| 15,000 IPs | $720 | $0.048 | [ Buy 15,000 IPs](https://bit.ly/9-Proxy) |
| 25,000 IPs | $863 | $0.035 | [ Buy 25,000 IPs](https://bit.ly/9-Proxy) |
| 50,000 IPs | $1,438 | $0.029 | [ Buy 50,000 IPs](https://bit.ly/9-Proxy) |
| 100,000 IPs (business) | $2,300 | $0.023 | [ Buy the 100,000 IP business pack](https://bit.ly/9-Proxy) |
| 200,000 IPs (business) | $4,140 | $0.021 | [ Buy the 200,000 IP business pack](https://bit.ly/9-Proxy) |
| 500,000 IPs (business) | $8,625 | $0.018 | [ Buy the 500,000 IP business pack](https://bit.ly/9-Proxy) |

The "$0.015 per IP" figure in most 9Proxy advertising refers to the deepest volume tiers, and it moved up a notch with the June adjustment. The jump from 100 IPs to 500 IPs is the one worth noticing: you pay 3x more and get 5x the inventory.

Two limits come attached to this model, and reviews tend to bury them. The IP-based product runs through the 9Proxy desktop app, which handles local port forwarding, so your traffic has to route through a machine running that app. And residential IPs die naturally within hours. If you need an address to survive for weeks — a parked account, a monitored listing — this is the wrong product; you want static ISP proxies instead.

## Per-GB billing: rotation without inventory management

The GB-based product inverts everything. You buy a traffic balance, generate as many proxy endpoints as you want from the dashboard, and pay only for what flows through them. No activation fee per IP, no app, no counting how many addresses you've burned through.

| Package | Total cost | Per GB | Validity | Buy |
| --- | --- | --- | --- | --- |
| 5 GB | $15 | $3.00 | 180 days | [ Buy the 5GB pack](https://bit.ly/9-Proxy) |
| 50 GB (+5 bonus) | $105 | $2.10 | 180 days | [ Buy the 55GB pack](https://bit.ly/9-Proxy) |
| 100 GB | $150 | $1.50 | 180 days | [ Buy 100GB](https://bit.ly/9-Proxy) |
| 200 GB | $200 | $1.00 | 180 days | [ Buy 200GB](https://bit.ly/9-Proxy) |
| 1,000 GB | $800 | $0.80 | 180 days | [ Buy the 1TB pack](https://bit.ly/9-Proxy) |
| 2,000 GB | $1,500 | $0.75 | 180 days | [ Buy the 2TB pack](https://bit.ly/9-Proxy) |
| 10,000 GB (enterprise tier) | — | $0.68 | Unlimited | [ Ask about the 10TB enterprise tier](https://bit.ly/9-Proxy) |

Between the 5GB pack and the 1TB pack the price per gigabyte drops by about 73%. That gap is the whole reason GB plans get sold as "scale-friendly" and also the reason small buyers should not expect the rate they saw in a blog headline.

Authentication here is standard: username and password, or whitelist your server's IP. Targeting runs to country, state, city, ZIP and ISP. Endpoint generation happens in the dashboard, and the 180-day validity window applies to all of it — nothing evaporates at the end of a calendar month, which matters if your projects come in bursts.

## What "rotating" actually means on each product

This is the part of buying rotating proxies that catches people out. Rotation is not one feature; it's a setting that behaves differently depending on which product you bought.

**On GB plans**, you choose the session mode per endpoint:

- **Rotating** — a new IP on every request or session. The default for breadth: no single address ever builds a history on the target.
- **Sticky** — the same IP held for a set number of minutes, which is what login flows, carts and multi-page navigation need.

**On IP-based plans**, addresses don't rotate on their own. There's an Auto Rotation Proxy that rotates at intervals you configure on selected ports — useful for feigning a residential rhythm, but it's a deliberate setup step, not a default. If you buy 100 IPs expecting per-request rotation out of the box, you'll spend an afternoon in configuration instead of scraping.

> The practical rule: rotating by default is a GB-plan behaviour. On a per-IP plan, rotation is something you build.

The other difference is where your client runs. GB plans work directly from the dashboard with host:port:user:pass credentials, which drops into AdsPower, Dolphin Anty, BitBrowser or a Python `requests` call without extra moving parts. IP plans require the desktop app in the request chain.

## Bundles, for when your workload doesn't pick a side

Selling both models to the same customer eventually looks silly, so 9Proxy bundles them:

| Bundle | Contents | Price | Buy |
| --- | --- | --- | --- |
| Starter | 100 IPs + 5 GB | $30 | [ Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Popular | 1,500 IPs + 50 GB | $180 | [ Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Pro | 5,000 IPs + 500 GB | $720 | [ Buy the Pro bundle](https://bit.ly/9-Proxy) |

The Starter bundle is the cheapest way to see both models behave on your own targets. It's also the honest answer for anyone who genuinely doesn't know yet whether their job is session-heavy or traffic-heavy — which, at the research stage, is most people.

Enterprise customers get unlimited data validity instead of 180 days, a team of one owner plus up to five members, per-member traffic controls, activity logs, unlimited share codes and VIP pricing. If you're an agency billing clients for collection work, the team controls are the interesting part; if you're solo, they're noise.

## Where 9Proxy sits against other rotating residential proxies

Third-party benchmark reporting in May 2026 put entry-level residential pricing across the market roughly here:

| Provider | Advertised entry price | Notes |
| --- | --- | --- |
| DataImpulse | $1.00/GB | Non-expiring traffic |
| Webshare | $1.75/GB | Per-request rotation |
| NetNut | ~$3.45/GB | $99/28GB tier |
| Rayobyte | $3.50/GB | HTTP only, no SOCKS5 |
| Decodo | ~$4.00/GB | 24h sticky sessions |
| Infatica | $4.00/GB | 5–60 min rotation |
| SOAX | $4.00/GB | Residential, ISP and mobile |
| Oxylabs | ~$6.00/GB | $30/5GB tier |
| **9Proxy** | **$3.00/GB at 5GB, $0.68/GB at 10TB** | HTTP/HTTPS and SOCKS5, per-IP model alongside |

Read that honestly: at small volumes 9Proxy's $3.00/GB entry is mid-market — DataImpulse and Webshare undercut it. Past a few hundred gigabytes it starts winning, and at the enterprise tier $0.68/GB is well below what the premium networks charge at any volume. Pool size is not the pitch here either; 20M+ IPs is respectable but Oxylabs and Decodo advertise far larger networks, and advertised pool numbers should always be treated as claims rather than audited figures.

Where 9Proxy is genuinely hard to beat is the per-IP model. $24 for 100 residential IPs with unlimited bandwidth is a low entry point for anyone whose job is "hold sessions open, transfer a lot, don't count bytes." [👉 Check the current per-IP and per-GB grids side by side](https://bit.ly/9-Proxy) before deciding — the relative value of each flips depending on the tier you're buying.

## A 30-minute test before you commit to anything

Buy the smallest plan that covers a real project, then run this:

- **Verify the ASN, not just the location.** Check your exit IP against ipinfo.io and BrowserLeaks. Residential means a consumer ISP; if you see Amazon, Google or DigitalOcean in the ASN field, you were sold datacenter addresses.
- **Test targeting at the level you actually need.** Country-level targeting is table stakes. If local SEO or ad verification is the job, confirm city or ZIP targeting returns what the target site shows, not just what the IP checker says.
- **Point it at your real targets.** Proxy checkers measure nothing. Run 200 requests against the sites you're actually collecting from and count blocks, CAPTCHAs and empty responses.
- **Watch the bandwidth burn.** Log actual bytes consumed per 1,000 requests on day one, then multiply. This is the number that tells you whether GB billing was the right call.
- **Check whether you need the desktop app.** If your collection runs in the cloud or across several machines, an IP-based plan means keeping that app in the chain everywhere.

9Proxy's trials are limited and issued on request depending on availability — when you contact support, say whether you want the IP-based or the GB-based trial, because they're separate products.

## Payment, and the referral discount

Payment options are broader than most proxy vendors: credit cards, bank cards, crypto (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay and Google Pay. 9Proxy also advertises a 5% discount for users who sign up through a referral link, which is what the invite links in this article are. If you were going to pay by card anyway, there's no downside to taking it. [👉 Open 9Proxy through the invite link and pick a plan](https://bit.ly/9-Proxy)

## What you should know before paying

- **IP plans need the desktop app.** Fine on a workstation, awkward for headless cloud pipelines.
- **Residential IPs are short-lived by design.** Hours, not months. Long-lived identity means static ISP proxies, a different product category.
- **IP plans don't rotate by default.** You configure rotation through the Auto Rotation Proxy.
- **The 180-day validity on GB plans is not unlimited.** Only the enterprise tier removes the expiry.
- **Advertised pool sizes are marketing.** 20M+ IPs across 90+ countries is the claim; your tested success rate on your targets is the reality.

## FAQ

**Is per-IP or per-GB cheaper for scraping?**
It depends on bytes per request. Under roughly 200KB per request with high rotation, GB billing usually wins. Above that, with sessions that stay open, a per-IP plan with unlimited bandwidth is normally cheaper — 100 IPs for $24 covers a lot of requests when the traffic itself is free.

**Can I rotate the IP on every request with a 9Proxy IP-based plan?**
Not natively. Per-request rotation is a GB-plan behaviour. On IP plans you set rotation intervals on selected ports via the Auto Rotation Proxy.

**Do unused IPs expire?**
No. Unused IPs from an IP-based package stay on your balance until you use them. GB balances carry a 180-day validity, unlimited on enterprise.

**What protocols does it support?**
HTTP, HTTPS and SOCKS5, which covers anti-detect browsers, headless automation and most scraping stacks.

**Does it work with AdsPower and Dolphin Anty?**
Yes — credentials are standard host:port:user:pass, and the vendor explicitly targets multi-account and automation workflows.

The short version: decide your billing model from your traffic pattern before you read another provider comparison. Get that right and the vendor shortlist mostly sorts itself out. [👉 Compare 9Proxy's plans and start with the smallest one that fits](https://bit.ly/9-Proxy)
