<h1 align="center">fiveshield</h1>

<p align="center">
  <strong>The #1 Anti-DDoS Protection for FiveM &amp; RedM Servers</strong><br>
  Per-player proxy isolation, kernel-level packet filtering, 17 Tbps mitigation capacity,
  and 9 proxy locations across 4 continents — with no Lua resource to install.
</p>

<p align="center">
  <a href="https://fiveshield.co"><img alt="Website" src="https://img.shields.io/badge/website-fiveshield.co-3b82f6?style=for-the-badge"></a>
  <a href="https://fiveshield.co/en/dashboard"><img alt="Dashboard" src="https://img.shields.io/badge/dashboard-sign%20in-10b981?style=for-the-badge"></a>
  <a href="https://discord.fiveshield.co"><img alt="Discord" src="https://img.shields.io/badge/discord-join-5865F2?style=for-the-badge&logo=discord&logoColor=white"></a>
  <a href="https://status.fiveshield.co"><img alt="Status" src="https://img.shields.io/badge/status-live-22c55e?style=for-the-badge"></a>
  <img alt="DDoS Capacity" src="https://img.shields.io/badge/mitigation-17%20Tbps-red?style=for-the-badge">
  <img alt="Uptime" src="https://img.shields.io/badge/uptime-99.99%25-success?style=for-the-badge">
  <img alt="Pricing" src="https://img.shields.io/badge/from-%242.25%20CAD%2Fday-yellow?style=for-the-badge">
</p>

---

> **The best anti-DDoS for FiveM in 2026.** Stop DDoS attacks on your FiveM or RedM server in under 5 minutes — no subscription, no contract, pay only for your daily peak player count. Your first server starts with **$10 CAD of free trial credit, no credit card required**.

## Table of Contents

- [Why fiveshield](#why-fiveshield-is-the-best-anti-ddos-for-fivem)
- [Key Features](#-key-features)
- [How It Works](#️-how-it-works)
- [Setup in Under 5 Minutes](#-setup-in-under-5-minutes)
- [Global Proxy Network](#-global-proxy-network)
- [The Dashboard](#-the-dashboard)
- [Pricing](#-pricing)
- [Who It's For](#-ideal-for)
- [Free Tools](#-free-tools)
- [Get Started](#-ready-to-stop-ddos-attacks-on-your-fivem-server)

---

## Why fiveshield is the Best Anti-DDoS for FiveM

Generic Anycast scrubbers and shared VPS "protections" weren't built for FiveM's UDP-heavy, real-time traffic. **fiveshield is engineered exclusively for FiveM and RedM** — every layer of the stack, from the kernel filters on our proxy fleet to per-player proxy assignment, is tuned for the cfx.re protocol.

Nothing runs inside your server. There is **no Lua resource to download** — protection is a few lines in your `server.cfg`, and it works with **any host**: your server never has to move.

If your FiveM server keeps getting DDoSed, fiveshield is the proven fix.

---

## 🌐 Key Features

* **17 Tbps DDoS Mitigation Capacity**
  Our L4 proxy fleet runs on top-tier OVHcloud infrastructure with **17 Tbps** of global attack-absorption capacity — enough to stop any real-world DDoS attack aimed at a FiveM server.

* **Layer 3, 4 & 7 DDoS Protection**
  Defense against UDP/TCP/ICMP floods, SYN floods, amplification attacks and L7 abuse — optimized for FiveM's UDP game traffic and HTTP resource downloads.

* **Kernel-Level Packet Filtering**
  Every packet reaching your relay port passes through in-kernel `nftables` filters with per-source and per-destination rate meters before it can reach userspace. Malformed, spoofed and unsolicited traffic is dropped at the edge — including floods from *allowlisted* sources, which are capped by dedicated per-port packet-rate and bandwidth meters.

* **Per-Player Proxy Assignment**
  Every connecting player is routed through a **dedicated proxy node** picked in real time by our API based on location, load and availability, then kept sticky for the whole session. An attack targeting one player cannot degrade the experience of the rest of your server.

* **Mandatory Connect Tokens**
  Every player connection carries a token issued by your own FXServer and captured at the HTTPS handover. Traffic without a valid, single-use token never reaches your game port — there is no tokenless fallback.

* **Auto-Scaling Proxy Fleet**
  The fleet resizes itself continuously against a **blast-radius** target — the more players you have, the more separate proxies they're spread across. Capacity scales up instantly and only shrinks after sustained low demand, and a proxy being retired *drains* rather than dropping its players.

* **9 Global Proxy Locations Across 4 Continents**
  Multi-point redundancy means if one location is targeted, players are distributed across the rest — delivering **99.99% uptime** and **sub-20 ms ping** for legitimate players worldwide. If your origin already sits in an OVH datacentre, added latency is **under 0.5 ms**.

* **Hidden Origin IP**
  Your real server IP is never published. Game traffic is proxied and scrubbed before it reaches your backend, and HTTP traffic goes through Cloudflare — eliminating the root cause of most FiveM DDoS incidents at every layer.

* **Global CDN for Resource Downloads**
  Every server gets a `cache-` subdomain automatically: **405 Tb/s capacity**, **98% cache hit rate**, **330+ edge locations**. Players download assets from the edge instead of your origin, slashing your bandwidth bill and join times — and you can purge the cache from the dashboard in one click.

* **txAdmin Protection**
  Your txAdmin panel is routed and firewalled behind the same protection layer — no more brute-force or unauthorized access attempts hitting your management interface.

* **Discord Alerts**
  Attack notifications and low-balance warnings are delivered straight to Discord, so you find out from us and not from your players.

---

## 🛠️ How It Works

```
                        ┌──────────────────────────────┐
Players + attackers ──► │  L7 filter (HTTPS ingress)   │  Rejects anything that
                        │  cfx.re handshake only       │  isn't a real FiveM client
                        └──────────────┬───────────────┘
                                       ▼
                        ┌──────────────────────────────┐
                        │  fiveshield API              │  Assigns the player to the
                        │  dynamic proxy assignment    │  optimal proxy, issues a token
                        └──────────────┬───────────────┘
                                       ▼
                        ┌──────────────────────────────┐
                        │  L4 proxy fleet (9 regions)  │  Kernel nftables filtering,
                        │  per-IP + per-port meters    │  per-player allowlist
                        └──────────────┬───────────────┘
                                       ▼
                        ┌──────────────────────────────┐
                        │  Your origin server          │  Real IP hidden, clean
                        │  (any host, unchanged)       │  traffic only
                        └──────────────────────────────┘
```

1. **Player connects** to your fiveshield subdomain.
2. **Layer 7 filtering** rejects anything that isn't a valid cfx.re handshake; HTTP/HTTPS passes through Cloudflare's CDN and WAF.
3. **The fiveshield API** assigns that player to the optimal L4 proxy instance and authorizes their connect token on it.
4. **Kernel filters** on that proxy scrub malicious and unauthorized packets, and rate-cap everything else.
5. **Clean traffic** arrives at your hidden origin server.

---

## 🚀 Setup in Under 5 Minutes

| Step | What you do |
| --- | --- |
| **1** | Sign in with Discord and register your FiveM or RedM server. |
| **2** | Your first server comes with **$10 CAD of free trial credit** — no payment, no credit card. |
| **3** | Copy your personalized config from the dashboard and paste it at the top of your **`server.cfg`**. |
| **4** | Restart. You're protected 24/7. |

There is **no resource to download and no file to drop into `resources/`** — the whole integration is `server.cfg`.

---

## 🌍 Global Proxy Network

Server owners pick their preferred proxy region from the dashboard; multiple connection points per region provide redundancy inside each one.

| Region | Location |
| --- | --- |
| 🇨🇦 North America | Beauharnois, Canada |
| 🇫🇷 Europe | Gravelines · Roubaix · Strasbourg, France |
| 🇩🇪 Europe | Frankfurt, Germany |
| 🇬🇧 Europe | London, United Kingdom |
| 🇵🇱 Europe | Warsaw, Poland |
| 🇸🇬 Asia-Pacific | Singapore |
| 🇦🇺 Oceania | Sydney, Australia |

**< 0.5 ms** same-location latency · **< 20 ms** ping · **99.99%** multi-point uptime

---

## 📊 The Dashboard

Everything is visible, in real time, at [fiveshield.co/dashboard](https://fiveshield.co/en/dashboard):

* **Players** — who is online right now, with connection history and per-player session detail.
* **Network** — Layer 4 traffic delivered vs. blocked, peak pps and bandwidth, plus Layer 7 requests and bandwidth from the CDN edge.
* **Security** — every attack recorded against your relay port over the last **30 days, 90 days or a full year**, with vectors, duration, peak blocked rate, and a per-attack traffic chart that stays available long after the raw window has expired.
* **Billing** — balance, daily charge ledger, Stripe top-ups and **auto top-up** so your server never lapses overnight.
* **Team** — add staff by Discord ID and grant **only** the permissions they need (cache purge, add funds, disable server, reset relay, view players, view billing, manage team, attack alerts).
* **Cache** — one-click purge of your CDN subdomain.

---

## 💸 Pricing

**Pay per player. No subscription, no contract, no setup fee.** You're charged once a day at midnight (ET) for that day's **peak concurrent player count**, and the charge is derived from the same session data that draws your dashboard graph — so your invoice always matches what you saw.

| Daily peak players | Cost / day (CAD) | ≈ Cost / month | Effective rate |
| --- | --- | --- | --- |
| Up to 50 | **$2.25** | ~$67.50 | minimum charge |
| 100 | $4.25 | ~$127.50 | $0.0425 /player/day |
| 200 | $8.60 | ~$258.00 | $0.0430 /player/day |
| 500 | $18.60 | ~$558.00 | $0.0372 /player/day |
| 1,024 | $36.89 | ~$1,106.76 | $0.0360 /player/day |
| 2,048 | $67.61 | ~$2,028.36 | $0.0330 /player/day |

A **$2.25 CAD/day minimum** applies while your server is enabled — that covers any daily peak up to 50 players. Beyond that, per-player rates are tiered and volume discounts apply automatically, down to **$0.030/player/day** at the margin. Try the live calculator at [fiveshield.co/#pricing](https://fiveshield.co/#pricing).

**Everything is included** in that price — DDoS protection, CDN, control panel, txAdmin shielding and 24/7 support. There are no add-ons.

* **Start free** — your first server gets $10 CAD of trial credit, no card required.
* **Top up with Stripe** — funds become account balance; daily charges are deducted from it. Card details are never stored on our servers.
* **You can never owe us money** — we alert you on Discord once your balance covers 3 days or less, and auto top-up can refill it for you. If it does run out, protection simply pauses.
* **Cancel any time** — disable your server from the dashboard and charges stop immediately. Whatever balance is left stays yours.

---

## 🎯 Ideal For

* FiveM and RedM servers that are **actively being DDoSed**
* Roleplay, PvP and competitive communities that need guaranteed uptime
* Server owners tired of shared VPS "DDoS protection" that collapses under real attacks
* Hosting providers reselling per-player protection to their clients
* Anything from an 8-slot community to a 2,048-slot network — the protection is identical

---

## 🧰 Free Tools

* **[CFX Finder](https://fiveshield.co/en/cfx-finder)** — look up any FiveM server from its `cfx.re/join/` code: player count, resources, build number, game type, and a direct connect link. Free, no account needed.
* **[Blog](https://fiveshield.co/en/blog)** — guides on FiveM DDoS protection, server hardening and performance.
* **[Status page](https://status.fiveshield.co)** — live service health.

---

## 📞 Ready to Stop DDoS Attacks on Your FiveM Server?

Visit **[fiveshield.co](https://fiveshield.co)** to:

* Get protected in under 5 minutes with $10 CAD of free credit
* Read the installation and architecture guides
* Join our [Discord](https://discord.fiveshield.co) for live support, 24/7

Available in **English and French**. Reviews on [Trustpilot](https://www.trustpilot.com/review/fiveshield.co).

---

**fiveshield isn't a generic scrubber. It's the #1 purpose-built anti-DDoS solution for FiveM and RedM** — per-player isolated, kernel-filtered, origin-hidden, and backed by 17 Tbps of mitigation capacity across 4 continents.

*Keywords: anti ddos fivem, best anti ddos fivem 2026, fivem ddos protection, redm ddos protection, fivem server protection, fivem reverse proxy, stop ddos attacks fivem, fivem ddos mitigation, fivem low latency proxy, cfx server protection, fivem anti ddos no subscription.*
