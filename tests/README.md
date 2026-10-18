# Testdokumentation

Dieser Ordner dokumentiert reproduzierbare und kontrollierte Detection-Tests aus der isolierten SOC-Laborumgebung.

## Validierte Tests

[Übersicht der validierten Detection-Tests](validated-detection-tests.md)

Die Testdokumentation enthält folgende Anwendungsfälle:

1. Base64-codierte PowerShell-Ausführung
2. Security Privileges Enumeration mit `whoami.exe /priv`
3. Netzwerk-Scan über Windows Event ID 5156
4. TCP-SYN-Port-Scan mit Suricata
5. Änderung der privilegierten Active-Directory-Gruppe `Domain Admins`

## Dokumentationsprinzip

Für jeden Test werden folgende Punkte festgehalten:

- Ziel des Tests
- verwendetes Testsystem
- erwartete Telemetrie
- tatsächlich erzeugte Ereignisse
- ausgelöste Wazuh-Regel
- Alert-Level
- MITRE-ATT&CK-Zuordnung
- Testergebnis
- SOC-Klassifizierung

Alle beschriebenen Aktivitäten wurden autorisiert und ausschließlich innerhalb der eigenen Laborumgebung durchgeführt.
