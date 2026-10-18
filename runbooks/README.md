# SOC Triage-Runbooks

Dieser Ordner enthält kurze und wiederholbare Anleitungen zur Untersuchung validierter Sicherheitsereignisse im SOC-Labor.

## Verfügbare Runbooks

### 1. Encoded PowerShell

[PowerShell Encoded Command Triage](powershell-encoded-command-triage.md)

Untersuchung einer codierten PowerShell-Ausführung, die durch Sysmon und Wazuh-Regel 92057 erkannt wurde.

- Wazuh-Regel: 92057
- Level: 12
- MITRE ATT&CK: T1059.001
- Taktik: Execution

### 2. Netzwerk-Scan

[Network Scan Triage](network-scan-triage.md)

Untersuchung eines möglichen Netzwerk-Scans mithilfe von Windows- und Suricata-Telemetrie.

- Wazuh-Regeln: 100110, 100111 und 100121
- Suricata Signature ID: 1000002
- MITRE ATT&CK: T1046
- Taktik: Discovery

### 3. Privilegierte Active-Directory-Gruppe

[Active Directory Privileged Group Triage](active-directory-privileged-group-triage.md)

Untersuchung des Hinzufügens oder Entfernens eines Mitglieds in einer privilegierten Active-Directory-Gruppe.

- Windows Event IDs: 4728 und 4729
- Wazuh-Regel: 60159
- Level: 12
- MITRE ATT&CK: T1484
- Taktiken: Defense Evasion und Privilege Escalation

## Einheitlicher Triage-Ablauf

Jedes Runbook umfasst:

1. Erkennungsdaten und Logquelle
2. Prüfung des betroffenen Systems und Benutzerkontos
3. Untersuchung zusammengehöriger Ereignisse
4. Klassifizierung des Alerts
5. Reaktion bei nicht autorisierter Aktivität
6. Dokumentation des Ergebnisses

Die kontrollierten Labortests wurden als **Benign True Positive** klassifiziert, weil die Aktivitäten autorisiert durchgeführt und von den vorgesehenen Regeln korrekt erkannt wurden.
