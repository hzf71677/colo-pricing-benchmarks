# colo data center: what you're actually paying for, current pricing benchmarks, and how to pick the right facility

If you're holding a server that deserves better than a closet shelf, or you've noticed your cloud bill climbing every quarter while the workload stays flat, you've probably landed on the idea of a colo data center. The concept is simple. The pricing is not. Quotes arrive with line items like "0.5A redundant power," "95th percentile commit," and "NRC," and half the providers you contact won't even talk to you unless you're renting half a rack on a three-year contract.

This guide covers what a colocation data center actually gives you, what each line on the bill means, what 1U space costs across major US markets right now, and how to evaluate a facility before you ship hardware to it. Along the way, we'll use a real, orderable pricing sheet — Sharktech's colocation plans — as a concrete reference point, including the setup fees and contract terms that most comparison tables quietly leave out.

## What a colo data center is, in plain terms

A colocation data center (usually shortened to "colo") is a facility where you rent space for hardware you own. The provider supplies everything the building is responsible for: rack space, power with backup generators, cooling, physical security, and network connectivity. You supply the servers, and you keep full control over the operating system, applications, and configuration. Nothing about your hardware changes hands.

Colocation comes in a few standard sizes, and knowing the vocabulary saves you from awkward sales calls:

- **1U to 6U** — the "U" is a rack unit, 1.75 inches of vertical cabinet space. This tier covers one to a few standalone servers. It's the entry point for most small businesses and homelab-graduates.
- **10U to 42U (full rack)** — a dedicated cabinet. A 42U rack holds a serious fleet of machines, and power allocations scale up accordingly, typically into multiple kilowatts.
- **Half racks and private cages** — the territory between and beyond, usually quoted custom for companies with dozens of machines or compliance requirements that demand physical isolation.

The dividing line between these tiers matters more than most guides admit. Plenty of large colo operators are structurally uninterested in a customer with one 1U box — the sales overhead isn't worth the revenue. Providers that actively publish 1U-friendly pricing are the ones worth shortlisting if you're small.

## What you're actually paying for

A colo bill looks like one number but behaves like five. Here's how the pieces break down.

**Space** is the line everyone expects — so many dollars per rack unit. But space is rarely the expensive part. In most markets, the real constraint is the next item.

**Power** is what actually drives price in modern facilities. A standard 1U server draws roughly 300–800W at peak. Providers allocate power per circuit — often 1–2A at 120V for a small colo slot — and charge steeply beyond that envelope. Some providers quote in amps, some in watts, some in kilowatts; converting between them at 120V is straightforward ($1\text{A} \approx 120\text{W}$), but you should always confirm whether your allocation is measured at the circuit or the meter, and what happens when you burst over it.

**Bandwidth** comes in two layers: the port speed (100Mbps, 1Gbps, 10Gbps, and up) and the billing model. The three common models:

1. **Included transfer** — a flat allowance, e.g. 10TB or 300TB per month, with overage billing after.
2. **95th percentile (burstable) billing** — the facility samples your usage every 5 minutes, sorts the samples, discards the top 5%, and bills you on the highest remaining sample. In plain terms: you can burst for about 36 hours a month for free, and sustained usage is what you pay for. It's the industry-standard model in colocation, and Sharktech's own knowledge base has a decent explainer on it.
3. **Unmetered/committed** — a fixed rate for a fixed pipe, whatever you push through it.

None of these is inherently a scam, but comparing a 95th-percentile quote against an included-transfer quote without converting between them is how budgets die.

**The line items that surprise first-timers** deserve their own mention, because they're where "cheap" colo quotes stop being cheap:

- **Setup fees (NRC — non-recurring charges)** for racking, cabling, and cross-connects. These range from trivial to hundreds of dollars.
- **Remote hands** — basic reboots and visual checks are usually included; anything involving a screwdriver typically runs $2–$4 per minute at market rates.
- **Cross-connects** — if you need a direct fiber run to a specific carrier in the building, that's a separate fee, sometimes monthly, sometimes one-time.
- **IP addresses** — often one or two IPv4 included, more costs extra, because IPv4 space is genuinely scarce.

### What 1U costs in different US markets

Colocation pricing is hyper-local. The same 1U slot can vary by a factor of three between markets. QuoteColo, a colocation brokerage that publishes estimated market ranges, currently lists 1U–2U pricing by market roughly like this:

| Market | Estimated 1U–2U price (USD/mo) | Notes from QuoteColo |
| --- | --- | --- |
| Los Angeles, CA | $120–$240 | One Wilshire competitive; 1G unmetered standard |
| Ashburn / NoVA | $120–$240 | Interconnect premium |
| New York / New Jersey | $95–$160 | Good regional provider options |
| Chicago, IL | $120–$140 | Lowest primary-market pricing for small servers |
| Phoenix, AZ | $50–$100 | Strong small-footprint pricing |

Their benchmark assumes a shared 42U–48U cabinet, 1–2A of power, a 100Mbps–1Gbps unmetered port, 1–2 IPv4 addresses, and a 12-month term. In other words: the bare-minimum configuration, before any DDoS protection or premium networking.

Two practical readings from this table. First, coastal interconnect hubs cost double what secondary markets charge for the same steel. Second, anything dramatically below these ranges deserves scrutiny — either you've found a regional provider that genuinely wants small customers, or the quote has constraints you haven't seen yet.

## Colocation vs. cloud vs. renting a dedicated server

Since every colo guide is legally required to address this, here's the short version with actual decision logic.

**Cloud (AWS, Azure, GCP, OpenStack providers)** bills you for elasticity. If your workload spikes unpredictably or you need to spin things up and tear them down hourly, cloud earns its premium. The catch is egress pricing: push serious traffic and a $40/month VM becomes a $400/month habit. Cloud costs are predictable only when usage is predictable.

**Dedicated servers** mean renting the provider's hardware. You get the isolation of bare metal without capital expenditure, and the provider handles hardware failures. What you give up is control over the spec and the ability to keep using hardware you already paid for. If you don't own servers and don't want to, this is the sane path.

**Colocation** means you already own — or plan to buy — the metal. Your monthly cost is space, power, and network, which is dramatically less than renting equivalent compute once the hardware pays for itself. A server you own sitting in a $65–$99/month slot typically undercuts a comparably specced cloud instance within the first year or two. The trade-offs are real though: you're responsible for hardware failures, spares, and the OS layer, and getting your hands on the machine requires scheduling a facility visit rather than walking down the hall.

The blunt decision rule: variable workload → cloud; no hardware and no interest in owning any → dedicated; steady workload plus owned hardware → colo.

## A real order form you can check against: Sharktech's colocation plans

Most colo pricing content on the internet quotes numbers that either expired years ago or never existed. So instead of paraphrasing a marketing page, this section is built from Sharktech's actual client-portal order catalog — the thing you'd click through before paying.

Quick context on the provider: Sharktech is a Las Vegas-headquartered infrastructure company founded in 2003 as a DDoS-protection-first host. They run their own network (AS46844 in public routing records) and colocate their cages inside enterprise facilities — Equinix AM11 in Amsterdam, the H5 Data Centers campus in Denver, a Flexential facility in Las Vegas, a site near One Wilshire in Los Angeles, and a Chicago facility with 2N generator backup and three diverse utility feeds from ComEd's downtown grid. They publish a 99.99% uptime guarantee, and their SLA provides service credits if the network guarantee isn't met. DDoS protection is bundled into services rather than sold as an add-on tier.

Here is their complete current colocation catalog — five locations, two size tiers, ten plans, exactly as listed on their order page:

| Plan | Space | Power | Network | Monthly price | Setup fee | Order |
| --- | --- | --- | --- | --- | --- | --- |
| Server Colocation – Las Vegas | 1–6U | 200–1200W | 1–40Gbps | $65.00 | $150.00 | [Order Las Vegas colocation](https://bit.ly/SharKTech) |
| Server Colocation – Denver | 1–6U | 200–1200W | 1–40Gbps | $65.00 | $150.00 | [Order Denver colocation](https://bit.ly/SharKTech) |
| Server Colocation – Chicago | 1–6U | 200–1200W | 1–40Gbps | $65.00 | $150.00 | [Order Chicago colocation](https://bit.ly/SharKTech) |
| Server Colocation – Los Angeles | 1–6U | 200–1200W | 1–40Gbps | $99.00 | $150.00 | [Order Los Angeles colocation](https://bit.ly/SharKTech) |
| Server Colocation – Amsterdam | 1–6U | 200–1200W | 1–40Gbps | $99.00 | $150.00 | [Order Amsterdam colocation](https://bit.ly/SharKTech) |
| Full Rack Colocation – Las Vegas | 10–42U | 1600–5500W | 1–100Gbps | $520.00 | $500.00 | [Order a Las Vegas full rack](https://bit.ly/SharKTech) |
| Full Rack Colocation – Denver | 10–42U | 1600–5500W | 1–100Gbps | $520.00 | $500.00 | [Order a Denver full rack](https://bit.ly/SharKTech) |
| Full Rack Colocation – Chicago | 10–42U | 1600–5500W | 1–100Gbps | $520.00 | $500.00 | [Order a Chicago full rack](https://bit.ly/SharKTech) |
| Full Rack Colocation – Los Angeles | 10–42U | 1600–5500W | 1–100Gbps | $792.00 | $500.00 | [Order a Los Angeles full rack](https://bit.ly/SharKTech) |
| Full Rack Colocation – Amsterdam | 10–42U | 1600–5500W | 1–100Gbps | $792.00 | $500.00 | [Order an Amsterdam full rack](https://bit.ly/SharKTech) |

A few things worth pointing out that you'd only notice by reading both the order form and the colocation page side by side:

**The 1–6U tier is unusually generous on power.** A 200–1200W envelope on an entry-level slot covers beefy 2U machines, not just thin web servers. Compare that to the market-standard 1–2A (~120–240W) allocation QuoteColo assumes, and the $65–$99/month prices sit well below the $120–$240 ranges for coastal markets. The port spec also runs higher than the typical 100Mbps–1Gbps benchmark — the order form lists options from 1Gbps up to 40Gbps on the 1–6U tier (up to 100Gbps on full racks), and the colocation page's spec sheet advertises included transfer starting at 300TB. Those two pages describe the network slightly differently, so treat the order form's configurable options as the ground truth and confirm your exact port and transfer terms at checkout.

**The setup fees are real and recurring-content-adjacent sites get them wrong.** Some third-party write-ups circulating online claim "free setup" on these plans. The actual order form says $150 one-time on 1–6U plans and $500 on full racks. It's still a modest NRC by industry standards, but budget for it — and note it's nonrefundable.

**Location strategy is worth five minutes of thought.** Las Vegas (inside Flexential) offers sub-10ms latency to Los Angeles, Phoenix, and Salt Lake City, plus low natural-disaster risk. Denver (H5 campus) sits mid-continent with strong fiber and low disaster exposure. Chicago puts you in the market QuoteColo rates as the cheapest primary hub for small servers. Los Angeles near One Wilshire is the classic US–Asia traffic corridor. Amsterdam (Equinix AM11, 8,320 m²) is the European entry point. Two 1U servers in different Sharktech facilities — say Las Vegas and Amsterdam — gets you geographic redundancy for about $164/month plus setups, which is cheaper than most DR strategies.

If any of that maps onto your situation, you can 👉 [check current plan availability and configure a slot on Sharktech's order page](https://bit.ly/SharKTech). Anything outside the standard tiers — half racks, cages, unusual power density — gets a custom quote through their sales team rather than a published price.

## The fine print most comparison tables skip

This is the section that separates a useful colo guide from a brochure, and it comes straight from Sharktech's published Terms of Service. Most of these terms are standard for the colo industry, which is exactly why you should know them before signing anywhere, not just here:

- **All payments are nonrefundable.** This includes the setup fee and all subsequent charges, regardless of usage. There's no money-back window on colocation, so don't ship hardware you're not sure about.
- **Terms run month-to-month or twelve months.** Your service auto-renews at the end of each term unless you cancel at least 5 days before the term ends. Miss that window and you've bought yourself another month.
- **Invoicing is advance-billed.** You get the invoice at least 5 days before the term ends, and payment is due within 5 days of the invoice date. Late payments accrue a 1.5% monthly late fee, and non-payment leads to suspension after a 48-hour notice window.
- **Billing disputes have a 30-day window** from the invoice date. After that, you're paying it.
- **Facility access requires scheduling.** Visits must be arranged at least 24 hours in advance with photo ID on file — which is normal for enterprise colo, but a genuine lifestyle change if you're used to your own server room. Emergency access for local users requires 15 minutes' advance notice to support.
- **Promotions rotate.** Sharktech runs recurring promotions and publishes coupon offers on its own site, and discount codes sometimes travel attached to order links. The reliable move is checking the order total before you submit payment rather than trusting any third-party coupon list — aggregator sites frequently list stale or invented codes.

None of these terms is scandalous. But if you came from consumer hosting, where refunds and instant cancellation are the norm, this is the part of colocation that actually changes your operational habits. If you want to read the contract before deciding anything, you can 👉 [review the current terms and plans through Sharktech's portal](https://bit.ly/SharKTech) — the TOS and order catalog both live there.

## How to choose a colo data center: a working checklist

Given everything above — market pricing, bill anatomy, and one fully documented provider — here's the checklist I'd actually run before committing hardware anywhere:

1. **Start with latency, not price.** Map where your users are. A $65 slot 40ms from your audience beats a $50 slot 80ms away. If you serve both coasts or two continents, budget for two small slots instead of one big one.
2. **Do the power math before the space math.** Add up your machines' peak draw in watts, add 20% headroom, and only then look at which tier fits. Buying a 1U slot for a server that peaks at 300W when the allocation is 200W creates an overage problem on day one.
3. **Compare bandwidth models, not just numbers.** A 1Gbps port with 300TB included and a 1Gbps 95th-percentile commit are different products. Ask what happens when you exceed your allowance, and get the overage rate in writing.
4. **Ask for the full rate card.** Setup fee, remote hands per-minute rate, cross-connect pricing, extra IPv4 costs, and what exceeding power allocation costs. A provider that answers these in one email is telling you something about their future support quality.
5. **Verify the facility, not just the brand.** Which building is your rack actually in? Enterprise campuses (Equinix, CoreSite, H5, Flexential) have documented redundancy, cooling, and security standards. A provider cage inside one of those inherits the building's engineering.
6. **Check whether DDoS protection is included or an upsell.** If your workload is a game server, a high-traffic site, or anything else that attracts attacks, standalone mitigation can cost more than the colo slot itself. Sharktech bundling it in is the structural reason its plans compare well despite the setup fees.
7. **Read the cancellation and refund terms before you fall in love with the price.** Nonrefundable payments, renewal notice windows, and access scheduling are normal in this industry — but "normal" still deserves a calendar reminder five days before your term renews.

## What outside reviews say

Independent review data on Sharktech exists but is thin. Their Trustpilot profile shows roughly 3.4 out of 5 from 13 reviews — a small sample that splits in both directions, which is worth describing honestly rather than averaging into a verdict.

The positive reviews cluster around price and reliability: a January 2026 reviewer called it the best yearly VPS deal around; another reported nearly a year of service with no downtime; a December 2025 reviewer praised an $8/month VPS as the cheapest on the market; and an earlier review specifically called out live chat staff for being helpful with dedicated-server questions.

The negative reviews are older but specific: a 2025 complaint about billing confusion involving PayPal subscriptions that kept charging after cancellation (the reviewer's takeaway — and fair warning for any provider — is to manually kill the PayPal subscription on PayPal's side when you cancel); a 2022 data-loss complaint; and a March 2026 review describing a server suspended 23 hours after activation pending identity verification. Treat that last pattern as a heads-up to complete any ID verification steps promptly at signup.

Two honest caveats apply. The sample is 13 reviews, which proves nothing statistically. And the reviews skew toward VPS and dedicated products rather than colocation specifically, so they're a signal about the company's operations and billing, not a direct report card on cage service. The colo-specific testimonial content Sharktech publishes on its own site leans heavily on game-hosting and ISP customers — exactly the DDoS-exposed, bandwidth-heavy profiles their bundled protection targets — but self-published testimonials deserve the usual discount.

## FAQ

**Is a colo data center actually cheaper than cloud?**
For steady workloads on hardware you own, usually yes — a $65–$99/month slot undercuts comparably powered cloud instances within a year or two, and colo bills don't spike with egress traffic the way cloud does. For elastic workloads you spin up and down, no — cloud's pricing model is genuinely better suited to that pattern.

**Do I manage my own server in colocation?**
Yes. The facility handles space, power, cooling, network, and physical security; you handle the OS, applications, and hardware maintenance. Sharktech's own FAQ describes it exactly this way. If you want the provider managing the software layer too, that's a dedicated server or managed hosting conversation instead.

**Can I start with one server and scale up?**
At Sharktech, the published path runs from 1U through 6U slots to 10–42U full racks, with custom cages quoted by sales beyond that. Generally across the industry, growing within one provider's facility beats migrating hardware between buildings.

**Is there a setup fee?**
On Sharktech's current order form: $150 one-time on 1–6U plans, $500 on full racks — contrary to some third-party write-ups claiming free setup. Setup fees are nonrefundable industry-wide, so confirm them before ordering anywhere.

**What if I need to physically access my hardware?**
Scheduled visits, arranged at least 24 hours ahead with photo ID, are the norm in enterprise colo. That's a feature (controlled physical security) that behaves like a bug when your server dies at 2 a.m. — which is why remote-hands service quality and 24/7 on-site staffing should be part of your provider evaluation, not an afterthought.

## The short version

A colo data center rents you the expensive parts of infrastructure — redundant power, industrial cooling, carrier-rich networking, physical security — while you keep the hardware and the control. Current market rates put a basic 1U slot anywhere from $50 in secondary markets to $240 in coastal interconnect hubs, and the price you see is rarely the price you pay until you've counted setup fees, power envelopes, and bandwidth models.

Sharktech's published catalog makes a useful reference point precisely because it's fully documented: $65/month 1–6U slots in Las Vegas, Denver, and Chicago; $99 in Los Angeles and Amsterdam; full racks from $520; generous power envelopes; bundled DDoS protection; and honest, listed setup fees of $150/$500 attached to nonrefundable, month-to-month-or-annual terms. Against the QuoteColo benchmarks, the 1–6U pricing sits below typical market ranges for the same cities — with the trade-offs being the setup fee, the no-refund policy, and doing your own server management.

If that trade reads favorably for your hardware and your workload, 👉 [configure a colocation plan on Sharktech's order page](https://bit.ly/SharKTech) and check the final terms at checkout. And whichever provider you pick, run the checklist first: the colo market punishes nobody quite as reliably as the buyer who skipped the fine print.
