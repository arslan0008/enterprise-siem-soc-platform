# enterprise-siem-soc-platform
Enterprise-grade SIEM and SOC platform built using Wazuh for centralized security monitoring, threat detection, file integrity monitoring, threat intelligence enrichment, and automated incident response.
# Delta Radar — Enterprise SIEM & SOC Platform

![Wazuh]

![OpenSearch](https://img.shields.io/badge/OpenSearch-Dashboard-orange?style=flat-square)
![Suricata](https://img.shields.io/badge/Suricata-IDS-red?style=flat-square)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=flat-square&logo=ubuntu)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Production-brightgreen?style=flat-square)

> Production-ready SIEM platform deployed on a cloud VPS using Wazuh, OpenSearch, and Suricata for centralized security monitoring, threat detection, File Integrity Monitoring, Threat Intelligence enrichment, and automated incident response.

---

![Dashboard](screenshots/dashboard.png)

---

## Overview

Delta Radar is an enterprise SIEM platform that centralizes security telemetry from Windows endpoints, Linux servers, IDS sensors, and web applications into a unified SOC dashboard. It enables real-time detection, threat hunting, compliance monitoring, and automated response — deployed on a live cloud VPS, not a local lab.

---

## Deployment Environment

| Component | Details |
|-----------|---------|
| Deployment | Cloud VPS |
| OS | Ubuntu Server 24.04 |
| SIEM | Wazuh |
| Search Engine | OpenSearch |
| Dashboard | Wazuh Dashboard |
| IDS | Suricata |
| Endpoint Monitoring | Wazuh Agents (Windows & Linux) |
| Remote Access | SSH |

![VPS Terminal](screenshots/vps-terminal.png)

---

## Architecture

```
Windows Endpoints  ──┐
Linux Servers      ──┤
Suricata (IDS)     ──┤──► Wazuh Agents ──► Wazuh Manager ──► Threat Intelligence
Web Applications   ──┘                            │
                                                  ▼
                                            OpenSearch
                                                  │
                                                  ▼
                                       Wazuh Dashboard (SOC Analyst)
```

![Architecture](architecture/architecture.png)

---

## Features

### Centralized Log Collection
Ingests logs from Windows Event Logs, Sysmon, Linux Syslog, Auditd, Suricata, Apache, Nginx, and SSH — normalized and indexed in OpenSearch.

### File Integrity Monitoring (FIM)
Monitors file creation, modification, deletion, and hash changes in real time using `syscheck` with `report_changes="yes"`.

![FIM Alert](screenshots/fim-alert.png)

### Threat Intelligence Enrichment
Automated IOC lookups against VirusTotal, AbuseIPDB, and MISP. Alerts are enriched with reputation data before reaching the analyst.

![Threat Intelligence](screenshots/threat-intelligence.png)

### Detection Engineering
Custom XML rules and decoders with MITRE ATT&CK mapping. Correlation rules cover brute force, privilege escalation, persistence, and lateral movement.

### Automated Active Response
Firewall-based IP blocking, account lockout, and custom scripts triggered by rule conditions — no manual intervention required for common attacks.

![Active Response](screenshots/active-response.png)

### Compliance Monitoring
CIS benchmark results via SCA. Mapped to PCI DSS, HIPAA, GDPR, NIST, and CIS frameworks.

![SCA](screenshots/sca.png)

### Vulnerability Detection
Agent-based CVE scanning with severity classification and remediation guidance.

![Vulnerabilities](screenshots/vulnerability.png)

---

## Detection Capabilities

| Technique | Coverage |
|-----------|----------|
| Brute Force (SSH, RDP, Web) | ✅ |
| PowerShell Obfuscation | ✅ |
| Mimikatz / Credential Dumping | ✅ |
| Registry Persistence | ✅ |
| Scheduled Task Abuse | ✅ |
| Webshell Detection | ✅ |
| Malware Indicators | ✅ |
| File Integrity Violations | ✅ |
| Threat Intelligence Matches | ✅ |
| Active Response Trigger | ✅ |

---

## Dashboards

### Security Events
![Security Events](screenshots/dashboard.png)

### MITRE ATT&CK
![MITRE](screenshots/mitre.png)

### Connected Agents
![Agents](screenshots/agents.png)

### Suricata IDS
![Suricata](screenshots/suricata.png)

---

## Incident Workflow

```
Log Ingestion → Decoder → Rule Match → MITRE Mapping
      → Threat Intelligence → Dashboard Alert → SOC Analyst → Incident Response
```

---

## Repository Structure

```
delta-radar-enterprise-siem/
├── configs/              # Sanitized Wazuh configuration files
│   ├── ossec.conf
│   ├── local_rules.xml
│   ├── local_decoder.xml
│   └── integration.xml
├── rules/                # Custom detection rules and decoders
├── scripts/              # Python integrations (TI enrichment, active response)
├── architecture/         # Architecture and data flow diagrams
├── screenshots/          # Dashboard and detection evidence
├── docs/                 # Deployment guide, detection notes, IR workflows
└── README.md
```

---

## Skills Demonstrated

`SIEM Engineering` · `Detection Engineering` · `Threat Hunting` · `SOC Operations`  
`Threat Intelligence` · `Python Automation` · `Linux Administration` · `Windows Security`  
`XML Rule Development` · `Incident Response` · `Log Analysis` · `MITRE ATT&CK`

---

## Future Improvements

- SOAR integration (TheHive / Shuffle)
- YARA rule scanning
- Sigma rule conversion pipeline
- CloudTrail / AWS log ingestion
- Slack / webhook alerting
- Docker-based deployment

---

## License

MIT License — see [LICENSE](LICENSE) for details.
