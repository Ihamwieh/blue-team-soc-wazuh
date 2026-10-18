# Wazuh-Regeln

Dieses Verzeichnis enthält die im SOC-Labor erstellten und getesteten lokalen Wazuh-Regeln.

## Kali-Netzwerkerkennung

Datei: `100110-100111_kali_network_detection.xml`

### Regel 100110 – Einzelne Netzwerkverbindung

- **Level:** 5
- **Übergeordnete Regel:** 60103
- **Logquelle:** Windows Filtering Platform
- **Windows Event ID:** 5156
- **Quelladresse:** 192.168.20.7 (autorisiertes Kali-Testsystem)
- **Zweck:** Erkennung einzelner Netzwerkverbindungen des Kali-Testsystems
- **Gruppen:** `network_scan`, `kali_activity`

### Regel 100111 – Korrelierter Netzwerk-Scan

- **Level:** 10
- **Abhängigkeit:** Regel 100110
- **Schwellwert:** Mindestens 10 erkannte Verbindungen innerhalb von 60 Sekunden
- **Ignore-Zeit:** 60 Sekunden
- **Zweck:** Erkennung eines möglichen Netzwerk-Scans
- **MITRE ATT&CK:** T1046 – Network Service Discovery
- **Gruppen:** `network_scan`, `kali_activity`, `correlation`

## Validierung

Die Regeln wurden durch einen autorisierten Nmap-Test innerhalb der isolierten Laborumgebung ausgelöst. Die erzeugten Ereignisse und Alerts wurden anschließend im Wazuh-Dashboard geprüft und dokumentiert.
