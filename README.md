# Best VPS for China: CN2 GIA, AS9929 or CMIN2? How to Pick the Right Return Route and the Cheapest Evoxt Plan That Fits (Full Plan Table)

Buy the route before you buy the server. A $2.99 Evoxt instance in Kuala Lumpur with a clean return path into mainland China will outperform a $40/month machine sitting on generic international transit at 9 PM Beijing time, and the gap has almost nothing to do with core count.

Evoxt's entry plan is VM-0.5 at $2.99/month for 512MB RAM and 250GB of monthly transfer, which is enough for a single proxy node or a small low-traffic site. Below is how to read a provider's routing claims, what every Evoxt plan costs, where the useful tiers stop, and what the cheaper annual deals from other providers quietly give up.

> **Quick pick:** Evoxt VM-1 at $5.99/month (1 core, 2GB RAM, 20GB storage, 500GB transfer, free weekly offsite backup) is the tier that covers a 3X-UI panel with several users or a small WordPress site without paying for RAM you won't touch. Pick Tokyo if physical distance to eastern China matters most; look at the Kuala Lumpur region if you want the three-carrier return path that independent testing has measured on Evoxt's Malaysian network. 👉 [Check VM-1 pricing and deploy](https://bit.ly/EvoXt)

## Why "China Optimized" on a spec sheet tells you nothing

Four route names show up in every listing, and each one only helps customers of one carrier.

**AS4134 (ChinaNet / 163)** is the default backbone most cloud providers hand you. Cheap to buy, congested after 8 PM CST.

**AS4809 CN2 GT (Global Transit)** was the original fix for AS4134. It stopped being a fix around 2019 and now performs close to standard transit while still costing noticeably more. There were partial improvements in 2021, but it never became CN2 GIA. Paying a premium for a GT plan is one of the more common ways to waste money on a China-facing server.

**AS4809 CN2 GIA (Global Internet Access)** is the premium tier with a separate backbone and far less contention. IP transit on it can run as high as $120 per megabit, which is why it normally lives in enterprise budgets. Providers that own their infrastructure instead of reselling can offer it at consumer prices.

**AS9929** is China Unicom's premium path. **CMIN2 (AS58807)** and CMI do the same job for China Mobile. **CTGNet (AS23764)** is China Telecom's newer layer, functionally comparable to CN2 GIA in both performance and cost.

The practical consequence: a plan that advertises CN2 GIA and nothing else is a China Telecom plan. If a third of your users are on China Mobile and a third on Unicom, they still route over congested transit. You need GIA plus 9929 plus CMIN2 on the same product before "optimized" means anything for a mixed audience.

Independent testing from March 2026 measured CN2 GIA-E class plans at roughly 158ms average from China to Los Angeles with zero packet loss during the 8–10 PM CST rush, while standard-routing competitors on the same hour showed 300ms+ latency and 15–30% packet loss. That test was run by a third party, not by us, and it describes one product family rather than the whole market. It does explain why two servers with identical specs can feel like different products.

Evoxt does not publish route names or China latency figures on its pricing page, so treat any China performance claim about it as something to verify rather than assume. A May 2026 third-party review of Evoxt's Kuala Lumpur optimized network did trace the return paths: China Telecom back through CTGNet to CN2 GIA, China Unicom through AS9929, China Mobile via direct CMI. The same review reported roughly 92ms average across China, about 86ms for Telecom with 53ms in Guangdong, 85ms for Mobile, and 109ms for Unicom. Those are review-benchmark numbers on one plan family in one region, not a guarantee for every Evoxt location.

## Every Evoxt plan, with the monthly price

Evoxt sells one plan family across nine regions: United States, United Kingdom, Canada, Germany, Poland, Amsterdam, Japan (Tokyo), Malaysia, and Australia. All plans list CPU boost clocks up to 6.0 GHz and include a free weekly offsite backup.

| Plan | vCPU / RAM | Storage | Transfer / month | Price | Deploy |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 core / 512 MB | 5 GB | 250 GB | $2.99/mo | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 core / 1 GB | 10 GB | 250 GB | $4.99/mo | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 core / 2 GB | 20 GB | 500 GB | $5.99/mo | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 cores / 2 GB | 20 GB | 500 GB | $6.95/mo | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 cores / 4 GB | 30 GB | 1,000 GB | $11.99/mo | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 cores / 4 GB | 30 GB | 1,000 GB | $14.99/mo | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 cores / 8 GB | 60 GB | 2,000 GB | $23.99/mo | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 cores / 8 GB | 60 GB | 2,000 GB | $29.99/mo | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 cores / 16 GB | 80 GB | 3,000 GB | $47.99/mo | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 cores / 16 GB | 80 GB | 3,000 GB | $60.95/mo | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 cores / 32 GB | 100 GB | 5,000 GB | $95.99/mo | [Deploy VM-16](https://bit.ly/EvoXt) |

Resource add-ons, priced separately from the plan:

| Add-on | Price |
| --- | --- |
| Extra IPv4 address | $3/month |
| Extra vCPU core | $3/month |
| Extra 1 GB RAM | $2/month |
| Extra transfer, Standard tier | $3/TB |
| Extra transfer, Premium tier | $12/TB |
| Extra transfer, Premium Plus tier | $24/TB |
| Paid backup plan | Varies with storage size |

Billing runs from monthly up to a three-year prepayment, and you can top up account credit and let the system apply it to future invoices. Payment methods are credit card, debit card, PayPal, Bitcoin, and USDt on Tron. Deployment is advertised as under five minutes.

Two details matter more than they look. First, scaling is per-resource, so a 1GB box that runs out of RAM costs $2/month to fix rather than a jump to the next tier. Second, IP addresses can be swapped and reassigned between servers from the panel, and additional floating IPs can be ordered at $3/month. If your node's address gets null-routed, that is the cheapest recovery path on the market outside of providers that hand out free replacements.

## Which tier actually fits a China-facing workload

A single-user proxy node or a personal blog on 150ms latency lives comfortably on **VM-0.5 at $2.99**. 512MB runs Xray or Hysteria2 fine, and 250GB of transfer covers a lot of browsing.

A 3X-UI panel shared with a small team, a Docker stack, or a WordPress install with plugins needs **VM-1 at $5.99**. The jump from 512MB to 2GB is the single most useful $3 you will spend here, because 512MB leaves no room for a database and a web server at the same time.

Running several protocols side by side, a mail relay, or a build agent pushes you into **VM-2 at $11.99** for 4GB. Everything above VM-2 is general-purpose compute. If you are shopping for a proxy node, VM-4 and up buy nothing you can feel, because the limiting factor is the return path, not the CPU.

Region choice matters more than plan size for China traffic. Tokyo is the closest Evoxt location to eastern China and the natural pick for latency-sensitive work. Kuala Lumpur carries the three-carrier return path reported in the May 2026 review, which is the more interesting option for a mixed Telecom/Unicom/Mobile audience despite the extra distance. Confirm which network tier you are provisioning at deploy time, since regional product lines differ.

## The latency ladder, and what each step costs

The price gap between regions is not arbitrary. It tracks distance.

Los Angeles sits around 120–140ms to mainland China on a good China-optimized route. Tokyo lands in between. Hong Kong reaches under 50ms to Guangdong and can drop into single-digit milliseconds for southern users. Each step down that ladder multiplies the monthly cost by a larger factor, which is why Hong Kong plans on established providers run into the hundreds per month while Los Angeles equivalents sit in the tens.

A blog, an API, or a proxy for email and GitHub does not need single-digit latency. 150ms is imperceptible for page loads and fine for SSH. Live streaming, real-time collaboration, and gaming are the cases where the Hong Kong premium earns its money, and even then you should price the delta against your actual user distribution before committing.

## The part that bites: prepayment, overage, and burned IPs

Cheap annual pricing usually comes with a trade. Sometimes that trade is a refund policy.

ZgoCloud's $52/year Los Angeles triple-route plan explicitly does not refund special offers, so a misjudged purchase is a total loss. BandwagonHost offers a 30-day refund window and does not auto-charge stored payment methods, which is worth real money when you are buying a route you have never tested. Evoxt's pricing page does not state a refund window, so confirm the terms with support before you prepay three years to lock a rate.

Overage handling differs too, and it is the thing that produces surprise bills. Evoxt bills extra transfer at $3/TB on the Standard tier rather than suspending the machine, which suits a node that must stay up. BandwagonHost suspends on overage until the next cycle and charges nothing extra, which suits a buyer who would rather be offline than billed.

Then there is the address. Any node serving mainland China will eventually have its IP blocked, and the recovery cost ranges from free to a full migration. Evoxt's $3/month extra IP and in-panel IP reassignment is the cheapest option in this comparison. Providers that charge for replacements or force a region migration turn a five-minute fix into a support ticket.

👉 [Compare Evoxt plans and add-on pricing before you prepay](https://bit.ly/EvoXt)

## Evoxt against the three names you will see everywhere

This is not an apples-to-apples price comparison. The entry tiers differ substantially in RAM and transfer, so read the configuration column, not just the number.

| Provider | Closest China-optimized entry plan | Entry price | Billing | Refund |
| --- | --- | --- | --- | --- |
| Evoxt | VM-0.5: 1 core / 512MB / 5GB / 250GB | $2.99/mo | Monthly to 3 years | Not stated on pricing page |
| BandwagonHost | CN2 GIA-E: 1GB / 20GB / 1TB, GIA + 9929 + CMIN2, 13+ locations | $169.99/yr or $49.99/quarter | Annual, quarterly | 30 days, no auto-charge |
| ZgoCloud | LA AMD Optimised Starter: 1C / 1GB / 10GB / 500GB @200Mbps, GIA + 9929 + CMIN2 | $52/yr | Annual | None on special offers |
| LightNode | Start: 1 vCPU / 2GB / 50GB / 1TB, Hong Kong or Taiwan | $7.71/mo | Hourly | Not stated |

BandwagonHost's CN2 GIA-E plan is the reference point for a reason: triple-carrier routing across 13+ data centers, free migration between them in about five minutes, and a refund window that lets you test the route and walk away. At $169.99/year it costs roughly five times Evoxt's entry plan, and the hardware is thinner than the price suggests.

ZgoCloud undercuts everyone on paper with the same three-carrier routing at $52/year, on EPYC hardware with NVMe. The trade is a newer provider (established around 2021) with a smaller track record, a 200Mbps fair-use cap on the optimized line, 100Mbps on the ISP variant, and no refunds on the deals that make it cheap. Hong Kong on that lineup is plain BGP with no premium route branding, so routing quality depends on upstream behavior.

LightNode sells Hong Kong and Taiwan on hourly billing from $7.71/month with 2GB RAM, which is the most flexible commitment of the four if you need to run something for two weeks and stop. Its Hong Kong location offers both a CN2-class line and BGP. Treat the marketing claims on that page cautiously; the same page states two different uptime figures and describes transfer as both unlimited and capped.

Where Evoxt lands: the lowest entry price, the most flexible resource scaling, and the cheapest IP replacement, without published route names or China latency guarantees. That combination suits someone who wants a cheap node now and the option to grow it, less so someone who needs a documented triple-carrier SLA on day one.

## Before you deploy: protocol, backups, and the ICP question

A server is a carrier. What determines whether it works from inside China is the protocol and the cleanliness of the IP.

OpenVPN, standard WireGuard, and basic IPSec are identified by DPI quickly and blocked. The setups that survive are Xray with VLESS and XTLS Reality, and UDP-based Hysteria2 or TUIC. 3X-UI runs on the server and generates configs and QR codes for a team; Shadowrocket, v2rayN, Nekoray, Clash variants, Sing-box, and Hiddify handle the client side.

Field reports split, and both sides are worth reading. One traveler through Guangdong on China Unicom reported GreenCloud Tokyo with Hysteria2 and Shadowrocket working without incident. Others report Hysteria2 packets dropped outright, or a Japan-based Xray Reality node passing a national TCP check in exactly one region and timing out everywhere else. The honest conclusion is that nothing is reliably permanent, which is why the recurring advice in these threads is to keep a second node, including something as simple as a home Raspberry Pi, and to buy from providers that make swapping IPs cheap.

For redundancy, Evoxt's hourly-equivalent flexibility is limited by monthly billing, but the $2.99 tier means a spare node costs less than a coffee. Two nodes in two regions beats one expensive node in the best region.

If you plan to host a public website rather than a private tunnel, note that mainland China hosting requires an ICP license or your domain gets filtered. Hong Kong and Taiwan do not require one, which is a large part of why their plans cost what they cost.

## The decision, in one pass

A single user tunneling out of China → Evoxt VM-0.5 at $2.99/month, Tokyo region.

A small team on a shared panel or a WordPress site → Evoxt VM-1 at $5.99/month, and budget $2 more if RAM gets tight instead of jumping a tier.

A mixed Telecom/Unicom/Mobile audience where routing quality is the whole point → pay for a documented triple-carrier plan, whether that is Evoxt's Kuala Lumpur network as measured by third-party testing or a provider that publishes the route names outright.

Latency-critical work like streaming or gaming, with users concentrated in Guangdong → Hong Kong, and accept the multiple.

Before you check out, confirm two things on the order page: the refund terms for the billing cycle you selected, and which network tier the region you picked actually runs on. Everything else you can change later.

👉 [Start with Evoxt's $2.99 plan and scale resources as you need them](https://bit.ly/EvoXt)
