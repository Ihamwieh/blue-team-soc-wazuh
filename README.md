# Blue Team SOC Lab with Wazuh

A hands-on Blue Team laboratory project focused on security monitoring, detection engineering, alert triage, and incident response.

## Project Overview

This portfolio documents a virtual SOC lab built with Wazuh and integrated endpoint and network telemetry. It demonstrates how security events are collected, analyzed, mapped to MITRE ATT&CK, and reviewed through a repeatable triage workflow.

## Lab Architecture

- Virtualized lab environment using Hyper-V
- Wazuh Manager and Indexer for centralized event collection and analysis
- Windows endpoints monitored with Sysmon and Windows Event Logs
- Ubuntu endpoint monitored with Suricata network telemetry
- Kali Linux used only as an authorized lab test system

**Event flow:** Endpoints and Suricata → Wazuh Manager → Indexer → SOC dashboards and alert triage

## Validated Detection Use Cases

| Use case | Detection evidence | MITRE ATT&CK |
|---|---|---|
| Encoded PowerShell execution | Sysmon Event ID 1; Wazuh Rule 92057, Level 12 | T1059.001 – PowerShell |
| TCP SYN port scan | Suricata SID 1000002; Wazuh Rule 100121, Level 8 | T1046 – Network Service Discovery |

## Repository Contents

- `docs/` – Project documentation and selected evidence
- `rules/` – Reviewed Wazuh, Sigma, and Suricata rules
- `configs/` – Sanitized configuration examples
- `runbooks/` – Triage and incident response procedures
- `tests/` – Controlled test scenarios and results

## Project Status

The lab contains documented endpoint and network detection use cases. Further improvements are organized according to the project roadmap.

## Safety and Privacy

All tests were conducted in an isolated, authorized lab. Sensitive values and environment-specific details are excluded from the public version.
