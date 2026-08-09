# Top Attack Lists — Live Data From Our Own Honeypots

**What attackers actually type when they knock on your door.** These lists are generated from [LureScope](https://lurescope.com)'s own passive honeypot sensor network — real brute-force telemetry, not recycled wordlists, not crowdsourced reports.

> **84,365 attack events · 3,054 unique IPs · 115 countries** — and counting. Observation window opened 2026-07-28.

## What's here

| File | Contents |
|---|---|
| `data/top-usernames.txt` | Top 47 most-probed usernames (with attempt counts) |
| `data/top-passwords.txt` | Top 50 most-probed passwords (with attempt counts) |
| `data/empty-password-probes.txt` | Usernames probed with an **empty** password — a targeted misconfiguration sweep |

## Why these lists are different

- **First-party data.** Every line comes from unsolicited inbound connections to our own sensors. We never scan anyone, and we don't resell third-party feeds.
- **Counts included.** Most public wordlists are unranked. These carry real attempt volumes, so you can weight your detections.
- **It moves.** `wallet` was nowhere in our top 10 on August 5. By August 8 it was #2 overall — 3,253 attempts, **every single one with an empty password**. Crypto-themed usernames (`wallet`, `binance`, `blockchain`, `crypto`, `bitcoin`) now account for 3,646 attempts and form the clearest targeting wave we've observed. See [Report #3](https://lurescope.com/reports/after-the-tsunami).

## How to use

- **Detection:** flag SSH/auth attempts against these username+password pairs, especially any `wallet` login attempt with an empty password.
- **Hardening audits:** if any account on your systems matches a row in `top-usernames.txt` with a password from `top-passwords.txt`, that combination is being actively probed *right now*.
- **Honeypot research:** compare with your own telemetry — we'd love to hear how it overlaps.

## Methodology & ethics

- Passive honeypot sensors only (SSH + Windows-service emulation). We never initiate connections or interact with attacking systems.
- Attacker IPs are **never** published here. These files contain only attempted credentials — which attackers already know, since they supplied them.
- Hex-encoded artifacts (e.g. `\x726f6f74` = `root` from MSSQL-layer probes) are filtered out of the lists.
- Geolocation of sources reflects hosting infrastructure, not attacker nationality.

## Updates

Weekly, alongside our [threat reports](https://lurescope.com/reports). Machine-readable, scored, per-IP indicators with HASSH tooling clusters are available through the [LureScope API](https://lurescope.com/api/v1/docs) — free early access, 100 queries/month.

## License

[CC BY 4.0](LICENSE) — use it, remix it, ship it in your product. Attribution: link to `lurescope.com`.

---

*Data: LureScope global sensor network · Questions: support@lurescope.com*
