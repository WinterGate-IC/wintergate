# WinterGate IC — Standard Operating Procedures

**Version 1.0 — June 2026**

---

## 1. Intelligence Gathering

### 1.1 Sources
All intelligence is gathered exclusively from:
- **Public sources**: Discord server listings, public profiles, community reports
- **Honeypot telemetry**: Automated systems (WinterGate Lite HTTP tarpit)
- **Voluntary submissions**: Community-submitted reports via GateKeeper
- **System logs**: SSH auth logs, web server access logs (attack patterns only)

### 1.2 Prohibited Methods
The following are **strictly prohibited**:
- Unauthorized access to any system or account
- Social engineering or deception
- Malware, exploits, or code injection against targets
- Surveillance of non-threatening individuals
- Collection of personal data unrelated to threat activity

### 1.3 Verification
Before any identifier is classified as a threat:
1. Cross-reference against at least 2 independent sources
2. Document the evidence
3. Apply appropriate classification (undetected / authenticated / blacklisted)

---

## 2. Data Classification

| Level | Label | Description | Access |
|---|---|---|---|
| 0 | Public | Aggregate statistics, service status | Anyone |
| 1 | Internal | Non-sensitive operational data | All operators |
| 2 | Restricted | Threat actor identifiers, IPs | Authorized operators only |
| 3 | Confidential | Authenticated operator identities, API keys | Collective leadership |

---

## 3. Data Handling

### 3.1 Collection
- Only collect data relevant to threat detection
- Minimize collection to what is necessary for the specific operation
- Document the reason for each collection

### 3.2 Storage
- Threat data stored in encrypted databases where possible
- Cold storage archives use AES-256-CBC encryption
- Access logs maintained for all database modifications

### 3.3 Retention
- Attack logs: 30 days active, 365 days for blacklisted IPs
- Threat identifiers: retained until removal requested
- Security events: 7 days (routine), 90 days (critical)

### 3.4 Destruction
- Data past retention period is purged automatically
- Deletion requests from affected individuals are honored within 14 days

---

## 4. Threat Validation

### 4.1 Automated Detection
- Honeypot hits are automatically classified by URL path, user-agent, and IP reputation
- SSH attacks are classified by type (invalid user, PAM failure, protocol mismatch)
- Thresholds: >3 failed SSH attempts or >1 honeypot hit triggers review

### 4.2 Manual Validation
Before adding to the global blacklist:
1. Verify the attack pattern is malicious (not a false positive)
2. Check for previous occurrences from the same IP
3. Document findings in the audit log

---

## 5. Notification Procedures

### 5.1 Community Notification
- Affected communities are notified through established channels
- Notifications include: threat type, severity, recommended actions
- No public disclosure of individual identifiers unless legally required

### 5.2 Transparency Reports
- Aggregate statistics are publicly available via the GateKeeper dashboard
- No identifying information is included in public reports

---

## 6. Incident Response

### 6.1 Detection
- Monitored through GateKeeper autonomous checks (every 15 min)
- Deep Sentinel scans (continuous log monitoring)
- Data Enrichment processing (every 60 seconds)

### 6.2 Triage
1. Assess severity (low / medium / high / critical)
2. Determine if automated response is appropriate
3. Escalate to collective leadership for critical incidents

### 6.3 Response Actions
| Severity | Action | Responsible |
|---|---|---|
| Low | Log and monitor | Automated |
| Medium | IP block, log review | On-call operator |
| High | IP block, community notification | Collective |
| Critical | Full lockdown, incident review | Leadership |

---

## 7. Access Control

### 7.1 Operator Authentication
- GateKeeper operators authenticate via the `_auth` command
- Roles: user, authenticated, leadership (owner)
- API access requires a valid API key

### 7.2 Revocation
- Operator access can be revoked at any time by collective leadership
- Deauthorized operators have all tokens invalidated immediately

---

## 8. Data Breach Procedure

1. Identify the scope and cause of the breach
2. Contain: revoke affected tokens, rotate keys, block affected IPs
3. Assess: determine what data was accessed
4. Notify: inform affected parties if personal data was compromised
5. Review: update procedures to prevent recurrence

---

## 9. Amendments

These SOPs are reviewed quarterly and may be updated by collective leadership. All amendments are documented with rationale and effective date.

---

*WinterGate Intelligence Collective — Where the shadows end, and the people stand.*
