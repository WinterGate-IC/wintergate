# WinterGate Intelligence Collective

**Where the shadows end, and the people stand.**

WinterGate IC is a private, membership-based security and intelligence collective. We use open-source intelligence (OSINT) and honeypot telemetry to research online abuse, track threat actors, and help communities defend themselves. No illegal surveillance, no hacking, no deception.

Founded April 9, 2025.

---

## Operational Principles

1. **OSINT Only** — All intelligence from publicly available sources, honeypot telemetry, and user-submitted reports. No illegal activity.
2. **Privacy First** — Normal users are never logged or tracked. Only attackers hitting our infrastructure are recorded.
3. **No Spectacle** — No public exposés or performative action. Our work is quiet and measured.
4. **Measured Response** — All responses are legal, transparent, and limited to reviewing public information and sharing practical advice.
5. **Community Defense** — Our goal is protecting safe digital spaces, not punishing bad actors.

---

## Active Services

### Honeypot Network

A low-interaction HTTP tarpit on port 8899 that catches port scanners, crawlers, and automated attackers.

- Classifies attack types by URL path (wp-admin probes, phpMyAdmin scans, .env/git leaks, sqlmap user-agents)
- Maps detections to MITRE ATT&CK techniques (T1190, T1083, T1046, T1202, T1110, T1059.007)
- Automatically drops attacker IPs via iptables
- Logs all attacks to a SQLite database
- **305 attacks logged from 298 unique attackers** and counting

### GateKeeper — Discord Security Bot

An active Discord bot with a Flask API and web dashboard. Tracks threat actor identifiers across Discord.

**Stats:** 7,897 tracked users, 10 authenticated operators, global blacklist enforcement.

**Bot Commands:**
- Security: auth, unauth, grant, verify, threat lookup, blacklist management
- Hunter: username resolution, cross-referencing, alt-account detection (85% similarity threshold)
- Config: server configuration, logging, blacklist actions

**API Endpoints:**
- `GET /api/health` — health check (public)
- `GET /api/global/stats` — public statistics
- `GET /api/stats/detailed` — detailed platform stats
- `GET /api/search?q=` — search users by ID or username (authenticated)
- `GET /api/stats` — all statistics (authenticated)

**Background:**
- Autonomous monitoring every 15 minutes
- Daily report generation
- Username resolution via Discord API with rate-limit protection
- Cold storage backup with AES-256-CBC encryption pushed to GitHub releases

### Deep Sentinel — Log Monitor

Monitors system logs for attack signatures:
- SSH auth logs: invalid users, PAM failures, protocol mismatches
- Web server logs: SQL injection, path traversal, prototype pollution, scraper bots
- Automatically blocks detected IPs via ipset

### Data Enrichment

Adds geolocation context to blocked IP addresses using GeoIP lookup. Runs every 60 seconds.

### WinterGate Website

**wintergate.org** — Public-facing site with:
- Collective mission and principles
- Portal to active services
- GateKeeper web dashboard with live stats and search
- About the collective

---

## Coming Services

### TEL API — Threat Entity Library _(concept)_

A planned programmatic API for curated threat intelligence data. Would allow server owners and moderation tools to query threat data in real time.

### Safe Haven Registry _(concept)_

A planned directory of vetted, trusted community spaces assessed by WinterGate IC operators.

---

## Data Handling

### Core Principle: We Do Not Log Normal Users

WinterGate IC never tracks, logs, or monitors ordinary users. Data collection is strictly limited to:

| Data | Source | Retention | Purpose |
|---|---|---|---|
| Attacker IPs | Honeypot, SSH logs, web logs | 30 days (active), 365 days (blacklist) | Threat detection, blocking |
| HTTP attack paths | Honeypot | 30 days | Attack classification |
| Discord IDs | Community reports, public sources | Until removal requested | Threat intelligence |
| Attack metadata | Automated detection | 7 days (routine), 90 days (critical) | Pattern analysis |

**Not collected:**
- No tracking of normal website visitors
- No cookies, analytics, or fingerprinting
- No browsing behavior
- No personal data from non-threatening users
- No message content surveillance
- No social media monitoring of ordinary users

[Read the full Data Handling Sheet →](DATA-HANDLING.md)

---

## Standard Operating Procedures

Our operations follow documented SOPs covering intelligence methodology, data handling, threat validation, incident response, and data retention.

[Read the full SOP →](SOP.md)

---

## Contact

General inquiries: **[wintergate.org](https://wintergate.org)**

---

*WinterGate Intelligence Collective — Where the shadows end, and the people stand.*
