# WinterGate IC — Data Handling Sheet

**Last updated: June 2026**

---

## Core Principle

**Normal users are never logged, tracked, or monitored.**

WinterGate IC's data collection is narrowly scoped to defensive security operations. We collect data only from systems actively attacking our infrastructure or threat actors reported through our community channels.

---

## 1. What We Collect

### Honeypot Data (WinterGate Lite — HTTP Tarpit)
| Data | Example | Retention | Purpose |
|---|---|---|---|
| Attacker IP address | `185.220.101.x` | 30 days (active), 365 days (if blacklisted) | Blocking via iptables |
| HTTP path requested | `/wp-admin/admin-ajax.php` | 30 days | Attack classification |
| HTTP method | `GET`, `POST` | 30 days | Attack classification |
| User-Agent | `sqlmap/1.8` | 30 days | Tool identification |
| Timestamp | `2026-05-21T14:23:11Z` | 30 days | Temporal pattern analysis |

### SSH Attack Data (Deep Sentinel)
| Data | Retention | Purpose |
|---|---|---|
| Attacker IP | 30 days / 365 days if blocked | Blocking via ipset |
| Attack type (invalid user, PAM failure, etc.) | 30 days | Pattern analysis |
| Username attempted | 30 days | Dictionary attack identification |

### GateKeeper Threat Intelligence
| Data | Retention | Purpose |
|---|---|---|
| Discord user IDs | Until removal requested | Threat tracking across communities |
| Discord username history | Until removal requested | Alt-account detection |
| Threat classification (undetected/blacklisted) | Indefinite (until removed) | Community protection |
| Authenticated user records | Indefinite (until deauthorized) | Operator access control |

### Community Reports
| Data | Retention | Purpose |
|---|---|---|
| Submitted Discord IDs | Until removed by request | Threat intelligence validation |
| Report metadata | 90 days | Abuse pattern analysis |

---

## 2. What We Do NOT Collect

- ❌ **No website visitor tracking** — wintergate.org has no analytics, cookies, or fingerprinting
- ❌ **No normal user data** — we do not track, log, or profile ordinary internet users
- ❌ **No browsing behavior** — no history, clicks, navigation, or session recording
- ❌ **No personal data** — no names, addresses, phone numbers, or financial information
- ❌ **No message content** — we do not read or store communications content
- ❌ **No social media monitoring** — we do not scrape or monitor ordinary users' social media
- ❌ **No third-party data** — we do not buy, sell, or exchange data with anyone

---

## 3. Data Storage & Security

- Honeypot data stored in a local SQLite database accessible only by the application user
- Geolocation enrichment stored in local JSON files
- GateKeeper uses SQLite with WAL mode and AES-256-CBC encrypted archives
- Encrypted cold storage backups pushed to a private GitHub repository
- All data stored on the same physical server — no cloud data processing
- No data leaves the server except encrypted archives pushed to GitHub

---

## 4. Data Retention & Deletion

| Data Type | Active Retention | Archive Retention | Deletion |
|---|---|---|---|
| Honeypot attack logs | 30 days | 365 days (blacklisted IPs) | Auto-purged after retention period |
| Attack log database | Indefinite (active operations) | — | Manual on request |
| SSH attack data | 30 days | — | Auto-purged |
| Discord threat IDs | Indefinite (until removed) | AES-256 encrypted cold storage | On request |
| Geolocation data | Tied to IP retention | — | Auto-purged with IP |

---

## 5. Data Access

- Access to threat intelligence data is limited to authorized WinterGate IC operators
- GateKeeper's API requires an API key for detailed searches
- Public stats (user count, global threat totals) are available without authentication
- No data is sold, shared, or made available to third parties

---

## 6. Removal Requests

If you believe your Discord ID or other data is in our database and you want it removed:
1. Contact us through **[wintergate.org](https://wintergate.org)**
2. Provide the relevant identifier
3. We will verify and remove it promptly

---

## 7. Accountability

This data handling sheet is a living document. We are committed to:
- Maintaining accurate records of what we collect and why
- Retaining data only as long as necessary
- Deleting data when it no longer serves its purpose
- Being transparent about our practices

---

*WinterGate Intelligence Collective — Where the shadows end, and the people stand.*
