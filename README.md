# Cheap NVMe VPS: Is Evoxt's $2.99 Plan Usable, Which Tier Do You Need, and What Will You Actually Pay? (Full Plan Table)

Evoxt's cheapest NVMe VPS is **VM-0.5 at $2.99/month**: 1 vCPU, 512 MB RAM, 5 GB NVMe and 500 GB transfer on the Standard network. It is enough for a static page, a WireGuard relay, an uptime monitor or a disposable test box. It is not enough for a database-backed app, a Docker stack or anything that needs more than a few hundred MB of free RAM.

This guide separates the usable floor from the advertised floor. Below you get the full nine-plan table, the add-on math that decides whether to upgrade, the bandwidth penalty in Hong Kong, Osaka and Malaysia, and the renewal and refund questions to settle before you pay.

> **Quick pick:** Most readers should start at **VM-1, $5.99/month** (1 vCPU, 2 GB RAM, 20 GB NVMe, 1 TB transfer). It is the first Evoxt plan that runs a small database plus a web app, or two lightweight containers, without constant swapping. The $2.99 VM-0.5 is the right buy only for a relay, static site or disposable test server. 👉 [Check VM-1's current price and deploy](https://bit.ly/EvoXt)

## Evoxt's full NVMe VPS lineup

Evoxt lists nine KVM plans on AMD EPYC, all with NVMe, IPv6, a 1 Gbps port and weekly offsite backups. Prices below are **USD per month on the Standard network**, billed monthly. Evoxt also offers prepaid terms up to three years, and the checkout shows the final total.

| Plan | CPU / RAM | NVMe | Transfer | Price | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 vCPU / 512 MB | 5 GB | 500 GB | **$2.99** | [ Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 vCPU / 1 GB | 10 GB | 750 GB | **$4.99** | [ Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 vCPU / 2 GB | 20 GB | 1 TB | **$5.99** | [ Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 vCPU / 2 GB | 20 GB | 1.5 TB | **$6.99** | [ Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 vCPU / 4 GB | 30 GB | 2 TB | **$11.99** | [ Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 vCPU / 4 GB | 40 GB | 3 TB | **$14.99** | [ Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 vCPU / 8 GB | 60 GB | 4 TB | **$23.99** | [ Deploy VM-4](https://bit.ly/EvoXt) |
| VM-8 | 8 vCPU / 16 GB | 80 GB | 8 TB | **$47.99** | [ Deploy VM-8](https://bit.ly/EvoXt) |
| VM-16 | 16 vCPU / 32 GB | 160 GB | 16 TB | **$95.99** | [ Deploy VM-16](https://bit.ly/EvoXt) |

Premium regions (Hong Kong and Osaka) keep the same plan names and mostly the same prices but cut monthly transfer. Premium Plus (Malaysia) raises the entry plan to $3.49 and cuts transfer further. The table is the Standard baseline.

## What the $2.99 plan can and cannot do

The 512 MB RAM limit is the real constraint. A minimal Debian install with SSH and a firewall sits around 100 MB. Add a small Go binary, a Caddy or Nginx process, and a monitoring agent, and you still have headroom. Add MySQL or PostgreSQL plus a PHP or Node app, and you will hit swap or the OOM killer.

The 5 GB disk is the second limit. A base Debian install, Docker, two images, logs and package caches can eat most of it. A small SQLite database fits. A MySQL dataset with indexes, binlogs and nightly dumps does not fit comfortably.

NVMe does not create RAM. Evoxt's AMD EPYC and NVMe base is the right hardware for a cheap box, and the 1 Gbps port is fine for a small site or relay. Storage interface is not a performance guarantee. Arct Cloud says this about its own NVMe comparison: "These figures compare storage interfaces; they are not VPS performance guarantees." The same caution applies here. A 5 GB slice on a shared host will not sustain database IOPS just because the label says NVMe.

If your workload is a static site, a DNS resolver, a Tailscale exit node or an uptime monitor, 👉 [deploy the $2.99 VM-0.5](https://bit.ly/EvoXt). If it needs a database, go to VM-1.

## Why upgrading the $2.99 box rarely makes sense

Evoxt sells extra RAM at $2/GB/month, extra vCores at $3/month each, extra IPv4 at $3/month, and extra transfer at $3/TB on Standard, $12/TB on Premium and $24/TB on Premium Plus.

Do the math on VM-0.5. Moving from 512 MB to 2 GB means 1.5 GB of add-on RAM, or $3/month. The total is $5.99, the same as VM-1. But VM-1 also gives you 20 GB NVMe instead of 5 GB and 1 TB transfer instead of 500 GB. Buying RAM piecemeal on the entry plan is the worse deal.

The same applies to vCPU. Adding one vCore to VM-0.5 costs $3 and leaves you at $5.99 with 512 MB RAM. VM-1 is still the better buy. Add-ons make sense when you need one extra IP or a small transfer top-up, not when you are trying to turn the entry plan into the next tier.

👉 [Compare VM-1 with the add-on total in Evoxt's console](https://bit.ly/EvoXt)

## What "cheap" means at renewal

Evoxt's $2.99 is the listed monthly rate for VM-0.5. A current annual listing puts the same plan at $35.88/year, which is exactly 12 × $2.99. That is the standard rate, not a first-month promotion. If you use a coupon, check the wording: a recurring discount and a first-invoice discount produce different second-year costs.

Not every cheap NVMe VPS price works this way. Cloudzy's page says "Currently 50% off all plans" and shows both the promo and the original: $3.48 vs $6.95 for 1 GB, $7.48 vs $14.95 for 2 GB. If the campaign ends, the 1 GB plan doubles. Cloudzy's header also says "From $7.48/mo" while its price table starts at $3.48. The table is the more specific figure; use $3.48 as the current promo and $6.95 as the regular rate.

Exabytes Singapore is another example. Its NVMe C1 is listed at S$20.71/mo, but the page says all prices are for the lowest available billing cycle, which is triennial. It also states that promotional pricing applies to new registrations only and renews at the default price. A low monthly number can hide a three-year commitment. Evoxt's entry price is simpler, but the checkout is still the only place to confirm the term, tax and renewal total.

👉 [See Evoxt's current checkout total before you prepay](https://bit.ly/EvoXt)

## Backups and the limits that do not show up in the price table

Every Evoxt plan includes weekly offsite backups at no extra cost. At $2.99, that is included, not a $5 add-on. The interval matters: a weekly restore point can be up to seven days old. If you run a database, take your own daily dump or ask support whether a daily option exists.

Each plan also includes IPv6, a layer 3 firewall, private IP between VMs, rescue mode, VNC and API access. Deployment is automated and ready in about 2.5 minutes. Evoxt accepts PayPal, Alipay, credit card and cryptocurrency.

Two policy questions need an answer before you pay. Evoxt's public plan information does not list a money-back window, so if a refund guarantee is part of your decision, ask support in writing before you pay. The add-on list covers RAM, vCores, IPs and transfer, but not extra disk. If you need more than the plan's NVMe allocation, choose a larger plan rather than trying to bolt on storage.

## Regions: same plan, less transfer in Asia

Evoxt has 16 locations: Hong Kong, Osaka, Tokyo, Seoul, Kuala Lumpur, Jakarta, Sydney, Los Angeles, New York, Montreal, London, Paris, Amsterdam, Frankfurt, Warsaw and Zurich. The plan name stays the same across regions, but the network tier changes the transfer cap.

| Plan | Standard | Premium (HK / Osaka) | Premium Plus (Malaysia) |
| --- | --- | --- | --- |
| VM-0.5 | 500 GB at $2.99 | 250 GB at $2.99 | 150 GB at $3.49 |
| VM-1 | 1 TB at $5.99 | 500 GB at $5.99 | 300 GB at $5.99 |

Larger plans follow the same pattern. The VM-16 gets 16 TB on Standard, 5 TB on Premium and 4 TB on Premium Plus. If you pick Hong Kong or Osaka for latency, plan around the smaller cap. If you need the full transfer, pick a Standard location.

Premium Plus is the only tier with a different entry price: $3.49 for VM-0.5 instead of $2.99. That is a $6/year difference, small enough that latency should decide it, not the price.

## How Evoxt compares on the cheap end

| Provider | Entry price | Entry specs | Note |
| --- | --- | --- | --- |
| Evoxt | **$2.99/mo** | 1 vCPU, 512 MB, 5 GB NVMe, 500 GB | Lowest entry price, but 512 MB RAM |
| Arct Cloud | **$3.89/mo** | 1 vCPU, 1 GB, 15 GB NVMe | All plans NVMe; claims up to 25 Gbps network |
| Cloudzy | **$3.48/mo** promo, $6.95 regular | 1 vCPU, 1 GB, 25 GB NVMe, 1 TB | 50% off is labeled "Currently"; 14-day refund |
| OmneHosting | **$7.99/mo** | 2 vCPU, 4 GB, 40 GB NVMe | No refunds; no in-place plan resize |
| AsiaWebHost | **S$55/mo** | 2 vCPU, 4 GB, 60 GB NVMe, 3 TB | SGD pricing; Singapore; daily backups |

Evoxt has the lowest entry price in this group and includes weekly backups. Its weak point is RAM at that price. A 512 MB box is not a substitute for a 1 GB box if your app has a JVM, a database or a control panel. Arct Cloud and Cloudzy both put 1 GB in the $3.48–$3.89 range, which is the more practical floor for many small apps. OmneHosting starts at $7.99 but gives 4 GB and 2 vCPU, so its cost per GB of RAM is lower than Evoxt's until you reach VM-2.

AsiaWebHost is a Singapore-specific option at S$55/month for 2 vCPU, 4 GB and 60 GB NVMe, with daily backups. Do not compare that SGD figure to Evoxt's USD price without a currency conversion. The point is the region and the daily backup, not the headline number.

Cloudzy offers a 14-day money-back guarantee. OmneHosting states that VPS services are not refundable and plans cannot be resized in place. Those policies change the cost of trying a small plan. Evoxt's refund terms need to be confirmed before you rely on the same tactic.

## Which Evoxt plan fits your workload

- **Static site, DNS, WireGuard, uptime monitor, disposable test:** VM-0.5, $2.99. 512 MB is enough if the process is small.
- **One small app with SQLite, a Tailscale node, one or two lightweight containers:** VM-1, $5.99. The 2 GB RAM and 20 GB disk give room for logs and updates. VM-0.75 at $4.99 is only worth it if $1/month matters more than 1 GB RAM.
- **MySQL or PostgreSQL plus a web app, a CI runner, a small Redis:** VM-2, $11.99. 4 GB RAM is the safer floor once the database and app share the box.
- **Docker Compose with several services, a small team, or a staging environment:** VM-4, $23.99. 8 GB RAM and 60 GB NVMe.
- **High transfer:** VM-8 or VM-16, but check the Premium caps first.

## Before you order

1. Pick the network at checkout. Standard gives the full transfer; Premium and Premium Plus cut it. The plan name alone does not tell you the cap.
2. Confirm the term and renewal total. $2.99 is the monthly list price; $35.88/year is 12 payments. A coupon may be recurring or first-invoice only.
3. Ask about refunds and daily backups if either is a dealbreaker. Weekly backups are included; a money-back guarantee is not listed in the plan information.

If you want the plan most readers should buy, start with VM-1. If you only need a relay or a static page, take VM-0.5. 👉 [Deploy Evoxt's VM-1 or compare the full lineup](https://bit.ly/EvoXt)
