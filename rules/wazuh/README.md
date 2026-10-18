# Lokale Wazuh-Regeln

Dieses Verzeichnis enthält die im SOC-Labor erstellten und getesteten lokalen Wazuh-Regeln.

## Kali-Netzwerkerkennung

Datei: [`100110-100111_kali_network_detection.xml`](100110-100111_kali_network_detection.xml)

### Regel 100110 – Einzelne Netzwerkverbindung

- **Level:** 5
- **Übergeordnete Regel:** 60103
- **Logquelle:** Windows Filtering Platform
- **Windows Event ID:** 5156
- **Quelladresse:** 192.168.20.7
- **Zweck:** Erkennung einzelner Netzwerkverbindungen des autorisierten Kali-Testsystems

### Regel 100111 – Korrelierter Netzwerk-Scan

- **Level:** 10
- **Abhängigkeit:** Regel 100110
- **Schwellwert:** 10 erkannte Verbindungen innerhalb von 60 Sekunden
- **Ignore-Zeit:** 60 Sekunden
- **MITRE ATT&CK:** T1046 – Network Service Discovery
- **Zweck:** Erkennung eines möglichen Netzwerk-Scans

## Suricata-Integration

Datei: [`suricata_custom_rules.xml`](suricata_custom_rules.xml)

### Regel 100121 – Suricata TCP-SYN-Port-Scan

- **Level:** 8
- **Übergeordnete Regel:** 86601
- **Suricata Signature ID:** 1000002
- **MITRE ATT&CK:** T1046 – Network Service Discovery
- **Zweck:** Erzeugung eines Wazuh-Alerts, wenn Suricata den definierten TCP-SYN-Port-Scan erkennt

## Sigma-basierte Regel

Die Sigma-basierte Wazuh-Regel 100120 wird mit ihrer Erkennungslogik im Verzeichnis [`../sigma`](../sigma) dokumentiert.

## Validierung

Die Regeln wurden durch autorisierte Tests innerhalb der isolierten Laborumgebung ausgelöst. Die erzeugten Ereignisse und Alerts wurden im Wazuh-Dashboard geprüft und dokumentiert.
