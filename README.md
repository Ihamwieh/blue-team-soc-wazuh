# Blue Team SOC Lab mit Wazuh

Praxisorientiertes Blue-Team-Laborprojekt mit Schwerpunkt auf Security Monitoring, Detection Engineering, Alert-Triage und Incident Response.

## Projektübersicht

Dieses Portfolio dokumentiert eine virtualisierte SOC-Laborumgebung mit Wazuh sowie integrierter Endpoint-, Active-Directory- und Netzwerk-Telemetrie.

Sicherheitsereignisse werden gesammelt, analysiert, MITRE ATT&CK zugeordnet und mithilfe wiederholbarer Triage-Workflows bewertet.

## Projektdokumentation

- [Portfolio – Deutsch (PDF)](Docs/Portfolio/Blue_Team_SOC_Wazuh_Portfolio_DE_Stand_17-10-2026.pdf)
- [Portfolio – English (PDF)](Docs/Portfolio/Blue_Team_SOC_Wazuh_Portfolio_EN_Stand_17-10-2026.pdf)
- [Portfolio – Arabisch (PDF)](Docs/Portfolio/Blue_Team_SOC_Wazuh_Portfolio_AR_Stand_17-10-2026.pdf)
- [Ausgewählte Nachweise](Docs/Belege)

## Laborarchitektur

- Virtualisierte Laborumgebung mit Hyper-V
- Wazuh Manager zur Ereignisverarbeitung und Alert-Erzeugung
- Wazuh Indexer zur Speicherung und Indexierung der Sicherheitsdaten
- Windows-Endpunkte mit Sysmon und Windows-Ereignisprotokollen
- Active Directory auf Windows Server
- Suricata auf Ubuntu zur Netzwerküberwachung
- Kali Linux als autorisiertes Testsystem
- Wazuh Dashboard zur Analyse und Visualisierung

### Ereignisfluss

Windows- und Ubuntu-Agenten einschließlich Suricata-Ereignissen aus `eve.json` → Wazuh Manager → Wazuh Indexer → Wazuh Dashboard

## Validierte Detection Use Cases

| Use Case | Detection-Nachweis | MITRE ATT&CK | Ergebnis |
|---|---|---|---|
| Encoded PowerShell | Sysmon Event ID 1, Wazuh-Regel 92057, Level 12 | T1059.001 | Benign True Positive |
| Security Privileges Enumeration | Wazuh-Regel 100120, Level 8 | T1033 | Benign True Positive |
| Windows-basierter Netzwerk-Scan | Event ID 5156, Regeln 100110 Level 5 und 100111 Level 10 | T1046 | Benign True Positive |
| Suricata TCP-SYN-Port-Scan | Signature ID 1000002, Wazuh-Regel 100121, Level 8 | T1046 | Benign True Positive |
| Änderung der Domain-Admins-Gruppe | Event IDs 4728 und 4729, Wazuh-Regel 60159, Level 12 | T1484 | Benign True Positive |

## Ausgewählte Ergebnisse

### Encoded PowerShell Detection

![Wazuh PowerShell Alert](Docs/Belege/Wazuh_PowerShell_92057_Triage_Result.png)

### Suricata TCP-SYN-Port-Scan

![Wazuh Suricata Alert](Docs/Belege/Wazuh_Suricata_Nmap_SYN_Scan_1000002.png)

### Active-Directory-Gruppenänderung

![Wazuh Domain Admins Alert](Docs/Belege/20_AD_Domain_Admins_Changed_Rule_60159.png)

## Inhalt des Repositories

| Pfad | Inhalt |
|---|---|
| [Docs/Portfolio](Docs/Portfolio) | Vollständige Projektdokumentation auf Deutsch, Englisch und Arabisch |
| [Docs/Belege](Docs/Belege) | Ausgewählte und geprüfte Screenshots |
| [Regeln/Wazuh](Regeln/Wazuh) | Lokale Wazuh-Regeln und Suricata-Integration |
| [Regeln/Sigma](Regeln/Sigma) | In Wazuh XML umgesetzte Sigma-Erkennungslogik |
| [Regeln/Suricata](Regeln/Suricata) | Lokale Suricata-Regeln |
| [Konfigurationen](Konfigurationen) | Bereinigte Konfigurationsauszüge |
| [Runbooks](Runbooks) | Triage- und Incident-Response-Anleitungen |
| [Tests](Tests) | Dokumentierte und validierte Detection-Tests |

## Technische Schwerpunkte

- Security Information and Event Management mit Wazuh
- Windows Event Logging und Sysmon
- Active-Directory-Sicherheitsüberwachung
- Suricata Network IDS
- Lokale Wazuh-Regeln und Ereigniskorrelation
- Umsetzung von Sigma-Erkennungslogik in Wazuh XML
- MITRE-ATT&CK-Mapping
- Alert-Triage und Incident Response
- Bewertung von True Positives, False Positives und Detection Gaps

## Sicherheitshinweis

Alle Tests wurden ausschließlich in einer isolierten und autorisierten Laborumgebung durchgeführt. Veröffentlicht werden nur bereinigte Konfigurationsauszüge und ausgewählte Nachweise ohne Passwörter oder andere Zugangsdaten.
