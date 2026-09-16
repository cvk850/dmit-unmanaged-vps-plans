# unmanaged vps hosting: pick the right bare-metal-style server without paying for hand-holding

When you search "unmanaged vps hosting," you're usually past the shared-hosting phase. You want root, you want to install what you want, and you don't want to pay someone $30/month extra to "manage" a box you can run yourself. The trade-off is simple: the provider gives you a server, an IP, and a network — and everything else (OS hardening, firewall, updates, backups, troubleshooting your own app stack) is on you.

This guide walks through what unmanaged actually means in 2026, where it makes sense, where it doesn't, and how a provider like **DMIT** fits into the picture if you're shopping for a VPS with serious network engineering rather than a generic $5 droplet.

## What unmanaged VPS hosting actually includes (and doesn't)

An unmanaged VPS is a virtualized server — usually KVM these days — where the host hands you:

- A fresh OS install (Linux distro of your choice)
- Root or administrator access
- A set amount of CPU, RAM, storage, and monthly transfer
- A network uplink at a rated port speed
- A control panel for reboot / reinstall / snapshot / billing — and nothing more

What you do **not** get, by default:

- Help installing or configuring Nginx, Apache, MySQL, Docker, cPanel, etc.
- Security patching of your applications
- Proactive monitoring of your services
- Application-level troubleshooting ("why is my WordPress slow")
- Backups unless you set them up yourself or pay for an add-on
- A guaranteed human on live chat at 3 a.m.

DMIT is explicit about this in its own terms: most services are unmanaged, and the only support guarantee is a 72-hour ticket response window. That's not a flaw — it's the model. You're buying infrastructure, not a managed platform.

If any of the "you don't get" items above made you nervous, unmanaged is the wrong product for you. Look at managed VPS providers instead. You'll pay more, but you'll sleep better.

## Who should actually buy unmanaged VPS hosting

The unmanaged model works for:

- **Developers and sysadmins** who already SSH into a box and configure it
- **Self-hosters** running Nextcloud, Vaultwarden, Jellyfin, Gitea, and the rest of the *arr stack
- **SaaS / API builders** who want a predictable monthly cost and full control of the runtime
- **VPN and proxy operators** who need a clean IP and full root to install their own tooling
- **People serving users in mainland China or APAC** from outside those regions, where network routing matters more than raw specs
- **Staging / CI / dev environments** where you spin things up and tear them down yourself

It does **not** work well for:

- Non-technical store owners who expect "managed" to mean "someone fixes my WooCommerce plugin"
- Anyone who panics at the words `systemctl`, `ufw`, or `journalctl`
- Teams that need a 24/7 NOC watching their box

## The thing most "best unmanaged VPS" lists miss: routing

Most comparison articles rank providers by price-per-GB-of-RAM and call it a day. That's fine if your users are all in the same country as your server. It's misleading if you're serving users across the Pacific, and especially if any of them are in mainland China.

Standard Tier 1 transit into China is congested and lossy during peak hours. A 4-core VPS with mediocre routing will consistently underperform a 1-core VPS on a premium network for latency-sensitive workloads. This is why providers like DMIT exist — they sell the same CPU/RAM/SSD spec everyone else sells, but the network behind it is the actual product.

DMIT splits its plans into three network series, and the difference is routing, not specs:

- **Premium Network** — Tier 1 transit plus China Telecom CN2 GIA (AS23764) and DMIT's own backbone. Lowest latency and packet loss into China. Most expensive.
- **Eyeball Network** — Tier 1 transit plus "reasonable-effort" China routing via CMIN2 / CMI (AS58453) and other Chinese eyeball ISPs. A middle ground on price and China reach.
- **Tier 1 Network** — clean international routing, no China-specific optimization. Cheapest. Good for global workloads where China isn't a target.

If you're serving users in Beijing, Shanghai, or Shenzhen from overseas, the Premium series is the one that actually matters. If you're serving a global audience and China is incidental, Tier 1 is fine. If China is part of your audience but not the main one, Eyeball is the reasonable middle.

## DMIT: an unmanaged VPS built around network, not specs

DMIT (dmit.io) is an unmanaged KVM VPS provider operating out of three locations — **Los Angeles**, **Hong Kong**, and **Tokyo** — with AMD EPYC hardware across three generations and the three network series described above. It's not the cheapest unmanaged VPS on the market; it's the one you pick when routing into China or across the Pacific is the actual reason you're shopping.

What's consistent across all DMIT plans:

- KVM virtualization with full root access
- AMD EPYC CPUs (AN5 = Zen 5 / 9005 series, AN4 = Zen 4 / 9004 series, AS3 = Zen 3 / 7003 series)
- NVMe SSD storage
- Free instant setup
- 1 IPv4 + 1 IPv6 /64 per instance
- Automated backups and instant snapshots available in the control panel
- SSH key authentication
- A wide OS template list: Ubuntu, Debian, CentOS, CentOS Stream, AlmaLinux, Rocky Linux, Fedora, openSUSE Leap, Arch Linux, Alpine Linux
- Unmanaged service with a 72-hour ticket SLA
- 99% uptime SLA, with compensation tiers if it drops below 95% or 90%

What's **not** included, and worth knowing before you buy:

- No managed support — tickets are answered, but not for application-level issues
- No automatic backups of your data unless you enable the feature or do it yourself; DMIT explicitly says it's not liable for data loss
- No refund on renewal orders, and no refund if you've used more than 3 GB of transfer and then claim the IP isn't reachable in your region
- OFAC-restricted countries are blocked: Cuba, Iran, Lebanon, Libya, Myanmar, North Korea, Somalia, Sudan, Syria
- Discount codes are for new customers only; using someone else's code on an existing account gets the service suspended

If you want to look at the live plan list and current pricing, 👉 [check the DMIT plans page](https://bit.ly/DmiT).

## DMIT plan comparison: all current plans across locations and networks

DMIT's product catalog is large because it multiplies locations × networks × hardware platforms. Below is the full set of plans currently shown on the official pricing and location pages, with the monthly price as listed. Where a plan is only sold on annual billing (the LAX.AS3.T1 WEE entry tier), that's noted explicitly.

> Prices below are the standard list prices shown on dmit.io at the time of writing. DMIT states it can change prices at any time without notice, and some plans are out of stock periodically. Promotional codes can stack recurring discounts on top — see the promotions section below.

### Los Angeles — Tier 1 Network (LAX.AS3.T1, entry tier)

The LAX AS3 platform is still being built out, and DMIT warns you may see reduced disk performance and a lower SLA than its mature platforms. These are the cheapest entry points in the entire lineup.

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Billing | Order |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| WEE | 1 | 1 GB | 20 GB | 1000 GB | 1 Gbps | $36.90 | Annually | [Get WEE](https://bit.ly/DmiT) |
| TINY | 1 | 2 GB | 20 GB | 1000 GB | 1 Gbps | $10.90 / mo | Monthly | [Get TINY](https://bit.ly/DmiT) |
| Pocket | 2 | 2 GB | 40 GB | 1500 GB | 4 Gbps | $16.90 / mo | Monthly | [Get Pocket](https://bit.ly/DmiT) |
| STARTER | 2 | 2 GB | 80 GB | 3000 GB | 10 Gbps | $34.90 / mo | Monthly | [Get STARTER](https://bit.ly/DmiT) |
| MINI | 4 | 4 GB | 80 GB | 5000 GB | 10 Gbps | $62.90 / mo | Monthly | [Get MINI](https://bit.ly/DmiT) |
| MICRO | 4 | 4 GB | 160 GB | 7000 GB | 10 Gbps | $87.90 / mo | Monthly | [Get MICRO](https://bit.ly/DmiT) |
| MEDIUM | 6 | 8 GB | 160 GB | 15000 GB | 10 Gbps | $199.90 / mo | Monthly | [Get MEDIUM](https://bit.ly/DmiT) |

### Los Angeles — Tier 1 Network (LAX.AN5.T1, current-gen hardware)

Same Tier 1 routing, newer AMD EPYC 9005 (Zen 5) hardware. Two plan families: VOLUME (more transfer, lower compute) and GENERAL (more compute, less transfer).

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AN5.T1 (VOLUME) V2C2G | 2 | 2 GB | 40 GB | 5000 GB | 10 Gbps | $14.90 / mo | [Get this plan](https://bit.ly/DmiT) |
| LAX.AN5.T1 (GENERAL) G2C4G | 2 | 4 GB | 80 GB | 4000 GB | 10 Gbps | $23.90 / mo | [Get this plan](https://bit.ly/DmiT) |
| LAX.AN5.T1 (VOLUME) higher tiers | up to 6 vCore | up to 8 GB | up to 160 GB | up to 15000 GB | 10 Gbps | up to $199.90 / mo | [See full AN5.T1 lineup](https://bit.ly/DmiT) |

### Los Angeles — Premium Network (LAX.AN5.Pro, CN2 GIA)

The flagship LAX lineup. CN2 GIA routing into China, AN5 hardware. DMIT only shows a curated selection on the public cloud-instance page; the full MINI / MICRO / MEDIUM tiers are listed below from the official pricing page.

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AN5.Pro.MINI | 4 | 4 GB | 80 GB | 5000 GB | 10 Gbps | $79.90 / mo | [Get Pro MINI](https://bit.ly/DmiT) |
| LAX.AN5.Pro.MICRO | 4 | 4 GB | 160 GB | 7000 GB | 10 Gbps | $110.90 / mo | [Get Pro MICRO](https://bit.ly/DmiT) |
| LAX.AN5.Pro.MEDIUM | 6 | 8 GB | 160 GB | 15000 GB | 10 Gbps | $289.90 / mo | [Get Pro MEDIUM](https://bit.ly/DmiT) |

### Los Angeles — Eyeball Network (LAX.EB)

Eyeball sits between Tier 1 and Premium on China reach. DMIT runs periodic launch promos on this series; the recurring-discount code from the last launch promo (LAX-EB-LAUNCH-NON-MONTHLY-RECURRING-20OFF, 20% off quarterly+ billing) was tied to a 2024 launch window and is not confirmed to still work — verify on the EB product page before relying on it.

| Plan | vCore | RAM | SSD | Transfer | Port | Price (monthly) | Annual price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| PVM.LAX.EB.TINY | 1 | 2 GB | 20 GB | 1200 GB | 2 Gbps | $14.90 / mo | $88.88 / yr | [Get EB TINY](https://bit.ly/DmiT) |
| PVM.LAX.EB.Pocket | 2 | 2 GB | 40 GB | — | — | — | $159.98 / yr | [Get EB Pocket](https://bit.ly/DmiT) |
| PVM.LAX.EB (2 vCPU tier) | 2 | — | — | — | — | — | $322.99 / yr | [See EB lineup](https://bit.ly/DmiT) |

> The LAX EB page lists several tiers as annual-only pricing; DMIT's published EB page shows TINY at $88.88/yr and Pocket at $159.98/yr as the entry points. Higher tiers (STARTER, MINI, MICRO, MEDIUM) follow the same naming convention as the rest of the LAX lineup. Confirm current availability on the EB product page, as EB inventory rotates.

### Hong Kong — Premium Network (HKG.AN5.Pro)

AN5 hardware is only offered on the Premium network in Hong Kong. Latency to mainland China averages ~15 ms with under 0.1% packet loss — the lowest in DMIT's lineup for China-facing workloads.

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| HKG.AN5.Pro.MINI | 4 | 4 GB | 80 GB | 1500 GB | 1 Gbps | $149.90 / mo | [Get HKG Pro MINI](https://bit.ly/DmiT) |
| HKG.AN5.Pro.MICRO | 4 | 4 GB | 160 GB | 2000 GB | 1 Gbps | $199.90 / mo | [Get HKG Pro MICRO](https://bit.ly/DmiT) |
| HKG.AN5.Pro.MEDIUM | 6 | 8 GB | 160 GB | 2500 GB | 1 Gbps | $279.90 / mo | [Get HKG Pro MEDIUM](https://bit.ly/DmiT) |
| HKG.AN5.Pro.LARGE | 8 | 16 GB | 320 GB | 3000 GB | 1 Gbps | $359.90 / mo | [Get HKG Pro LARGE](https://bit.ly/DmiT) |
| HKG.AN5.Pro.GIANT | 12 | 24 GB | 640 GB | 6000 GB | 1 Gbps | $759.90 / mo | [Get HKG Pro GIANT](https://bit.ly/DmiT) |

### Hong Kong — Eyeball and Tier 1 (HKG.AS3)

AS3 hardware (AMD EPYC 7003 / Milan) is offered on both Eyeball and Tier 1 networks in Hong Kong. The HKG T1 entry tiers start at $36.90/yr on annual billing — one of the lowest entry points in the lineup.

| Plan family | Network | Entry price | Order |
| --- | --- | --- | --- |
| HKG.AS3.T1 (WEE / TINY / STARTER...) | Tier 1 | from $36.90 / yr | [See HKG T1 plans](https://bit.ly/DmiT) |
| HKG.AS3.EB | Eyeball | from ~$39.90 / mo (STARTER tier) | [See HKG EB plans](https://bit.ly/DmiT) |

> The Hong Kong AS3 lineup covers a wide plan range on both T1 and EB networks. DMIT periodically runs HKG-specific promos (a recent one offered 33% off on annual HKG T1 orders). Check the HKG location page for the current plan list and any active promo.

### Tokyo — Premium Network (TYO.AN5.Pro / TYO.AS3.Pro)

Tokyo Premium uses CN2 GIA with ~28 ms average latency to mainland China — the lowest of DMIT's three locations thanks to Tokyo's geographic proximity. The full Premium plan list from the Tokyo location page:

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TYO.Pro.TINY | 1 | 1 GB | 20 GB | 500 GB | 1 Gbps | $21.90 / mo | [Get TYO Pro TINY](https://bit.ly/DmiT) |
| TYO.Pro.STARTER | 1 | 2 GB | 40 GB | 1000 GB | 1 Gbps | $45.90 / mo | [Get TYO Pro STARTER](https://bit.ly/DmiT) |
| TYO.Pro.MINI | 2 | 4 GB | 60 GB | 2000 GB | 1 Gbps | $89.90 / mo | [Get TYO Pro MINI](https://bit.ly/DmiT) |
| TYO.Pro.MICRO | 4 | 4 GB | 80 GB | 4000 GB | 1 Gbps | $189.90 / mo | [Get TYO Pro MICRO](https://bit.ly/DmiT) |
| TYO.Pro.MEDIUM | 4 | 8 GB | 160 GB | 6000 GB | 1 Gbps | $320.90 / mo | [Get TYO Pro MEDIUM](https://bit.ly/DmiT) |
| TYO.Pro.LARGE | 8 | 16 GB | 320 GB | 8000 GB | 1 Gbps | $429.90 / mo | [Get TYO Pro LARGE](https://bit.ly/DmiT) |
| TYO.Pro.GIANT | 8 | 24 GB | 640 GB | 15000 GB | 1 Gbps | $829.90 / mo | [Get TYO Pro GIANT](https://bit.ly/DmiT) |

### Tokyo — Tier 1 Network (TYO.AS3.T1)

Tokyo Tier 1 is the budget Japan-IP option. The TINY at $6.90/mo is one of the lower entry points for a Japan-IP VPS from a serious provider.

| Plan | vCore | RAM | SSD | Transfer | Port | Price | Order |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TYO.AS3.T1.TINY | 1 | 1 GB | 20 GB | 2000 GB | 1 Gbps | $6.90 / mo | [Get TYO T1 TINY](https://bit.ly/DmiT) |
| TYO.AS3.T1.STARTER | 1 | 2 GB | 40 GB | 4000 GB | 1 Gbps | $12.90 / mo | [Get TYO T1 STARTER](https://bit.ly/DmiT) |
| TYO.AS3.T1 (higher tiers) | up to 8 vCore | up to 24 GB | up to 640 GB | up to 15000 GB | 1 Gbps | up to ~$429.90 / mo | [See full TYO T1 lineup](https://bit.ly/DmiT) |

## How to actually pick a plan

If you're shopping unmanaged VPS hosting and DMIT is on your shortlist, the decision tree is mostly about network and location, not specs:

1. **Where are your users?** If they're in mainland China, Premium is the only series that meaningfully solves the routing problem. Pick Hong Kong Premium for lowest latency (~15 ms), Tokyo Premium if you also serve Japan/Korea/Taiwan (~28 ms), or LAX Premium if you need a US-IP presence with premium China routing.
2. **Is China incidental to your audience?** Eyeball is the right answer. You get reasonable-effort CMI/CMIN2 routing without paying for CN2 GIA. Good for blogs, SaaS backends, dev boxes with a mixed global/China audience.
3. **No China users at all?** Tier 1 is the cheapest and perfectly fine. Pick it for VPN relays, backups, CI runners, internal tooling, anything where the routing into China doesn't matter.
4. **How much transfer do you actually need?** DMIT's AN5.T1 VOLUME plans trade compute for transfer — useful if you're running a download mirror or backup target. The GENERAL plans flip that. The AS3 WEE/TINY plans are the cheapest entry but capped at 1 Gbps and 1000 GB.
5. **Annual or monthly?** Annual billing unlocks the recurring-discount promo codes and the cheapest entry tiers (WEE on LAX T1, the $36.90/yr HKG T1 entry). Monthly is fine for testing but you'll pay list price.

For a single self-hosted box serving a global audience with light China traffic, the LAX Eyeball TINY at $14.90/mo (or $88.88/yr) is the sweet spot — 1 vCPU, 2 GB RAM, 20 GB SSD, 1200 GB transfer, with CMI routing that handles Chinese residential ISPs noticeably better than plain Tier 1.

For a China-facing production site, skip the entry tiers and go straight to LAX.AN5.Pro.MINI at $79.90/mo or Hong Kong Premium MINI at $149.90/mo. The price jump buys you CN2 GIA and the AN5 platform, which is the actual product.

## Promotions and discount codes

DMIT runs time-limited promos and releases recurring-discount codes during them. The most recent confirmed event was the **Christmas 2025** promotion, which has now ended. The codes from that event are listed here for reference; treat them as expired unless DMIT re-confirms them:

- `2025-XMAS-LAX-PRO-EB-ANNUALLY-STARTER-AND-HIGHER-15OFF-RECURRING` — 15% recurring off + 10% account cashback on LAX Pro & EB annual STARTER or higher
- `2025-XMAS-LAX-PRO-EB-10-OFF-RECURRING` — 10% recurring off + 5% cashback on LAX Pro & EB regular plans
- `2025-XMAS-LAX-T1-ANNUALLY-EXCL-WEE-TINY-20OFF-RECURRING` — 20% recurring off + 10% cashback on LAX T1 annual (excl. WEE & TINY)
- `2025-XMAS-LAX-T1-10-OFF-RECURRING` — 10% recurring off + 5% cashback on LAX T1 (excl. WEE)

A few things worth knowing about how DMIT promo codes work, taken from its terms:

- Discount codes only apply to **new customers**. Using a code that was issued to a specific existing user on your own account gets the service suspended and forfeits any refund.
- Recurring discounts apply for the life of the plan as long as you keep renewing.
- Cashback is paid as account credit, settled monthly over the billing cycle.
- Refunded orders forfeit all promo benefits, including cashback and referral bonuses.
- Promos typically run for a defined window; once the window closes, the code stops working even if it's still published on coupon sites.

If you want to see what's currently active, 👉 [check the live DMIT promotions page](https://bit.ly/DmiT) before checking out. Third-party coupon sites frequently list expired DMIT codes as "verified" — always confirm on the official site.

## Refund and IP policy: read before you buy

DMIT's refund window is tighter than most providers, and it's tied to transfer usage:

- **Full refund** within 3 days of a new order, only if you've used ≤ 30 GB of transfer
- **Partial refund** within 30 days of a new order, calculated on the lower of remaining transfer or remaining service time
- **No refund** on renewal orders, on orders paid with account credit, on orders flagged for DDoS, on orders where you've used > 3 GB and then claim the IP isn't reachable in your region, or after 3 refunds on the same product series
- IP replacement is free every 7 days on Premium/Eyeball with the `IP Care+` add-on, every 15 days without it on monthly billing, or $5 per replacement otherwise. Tier 1 IPs are not guaranteed globally reachable without the `IP Guarantee+` add-on.

The IP-reachability clause is the one that catches people. If you buy a Tier 1 plan and the assigned IP happens to be unreachable from China, you have to contact sales **the same day** — wait past 3 GB of transfer and the refund door closes. Premium and Eyeball plans guarantee first-connection reachability in all countries (subject to force-majeure exceptions).

## Where DMIT fits in the unmanaged VPS landscape

Against the usual unmanaged-VPS suspects — DigitalOcean, Vultr, Linode/Akamai, OVHcloud — DMIT occupies a specific niche: similar KVM + AMD EPYC + NVMe specs, but with a network engineered for China and APAC that the hyperscalers don't bother with. You're not buying DMIT to save money on raw specs. You're buying it because:

- Your users are in China and you don't want to host inside China
- You want CN2 GIA or CMI routing without assembling it yourself from a transit broker
- You want a single provider across LAX / HKG / TYO with consistent tooling
- You're fine with unmanaged and a 72-hour ticket SLA in exchange for lower prices than the China-optimized competitors

If none of those apply, a $4/mo DigitalOcean droplet or a $6/mo Vultr instance will serve you just as well for a generic global workload. DMIT is the right answer to a specific question, not a universal one.

## Getting started

If you've decided unmanaged is right for you and DMIT's network fits your audience, the setup is the standard unmanaged flow:

1. Create an account and verify your email
2. Pick a location, network series, and plan from the pricing page
3. Choose an OS template (Ubuntu and Debian are the safe defaults; Alpine if you want minimal footprint)
4. Add an SSH public key during provisioning — disable password auth as soon as you log in
5. Run your own initial hardening: `ufw` or `nftables` for the firewall, `fail2ban` for SSH, unattended-upgrades for security patches
6. Set up your own backups — either DMIT's automated backup feature or off-box backups to S3-compatible storage
7. Enable monitoring (Uptime Kuma, Healthchecks, or a paid APM) — DMIT won't tell you if your app is down

To look at current plans and pricing and open an account, 👉 [visit the DMIT plans page](https://bit.ly/DmiT).

Unmanaged VPS hosting is a trade-off: you give up the hand-holding and pay a lot less in exchange. DMIT sharpens that trade-off in one direction — slightly higher prices than the cheapest unmanaged providers, but a network that actually solves the China and APAC routing problem. If that's the problem you're trying to solve, it's worth the premium. If it isn't, the cheaper generic options are the better call.
