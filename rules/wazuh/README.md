# Wazuh-Regeln

Dieses Verzeichnis dokumentiert lokale Wazuh-Regeln des SOC-Labors. Die Regeldefinitionen werden ergänzt, nachdem sie mit der aktiven Konfiguration abgeglichen wurden.

## Bestätigter Anwendungsfall

### Erkennung einer Netzwerkverbindung von Kali

- **Regel-ID:** `100110`
- **Logquelle:** Windows Filtering Platform, Event ID `5156`
- **Bedingung:** Netzwerkverbindung mit der Quell-IP `192.168.20.7`
- **Ziel:** Autorisierte Netzwerkaktivität des Kali-Testsystems im Labor erkennen
- **Validierung:** Die Erkennung wurde im Labor getestet und im Wazuh-Dashboard geprüft.
- **MITRE ATT&CK:** Zuordnung nur angeben, wenn sie für diese Regel in der Projektdokumentation belegt ist.

## Weitere lokale Regeln

Die IDs `100111`, `100120` und `100121` werden hier erst beschrieben, nachdem ihre aktiven Regeldefinitionen und Testergebnisse geprüft wurden.

## Ablage und Prüfung

- Regeldefinitionen werden als XML-Dateien in diesem Verzeichnis abgelegt.
- Zu jeder Regel werden Zweck, Logquelle, Auslösebedingung und ein belegter Test dokumentiert.
- Vor einer Veröffentlichung werden IP-Adressen, Hostnamen und andere Umgebungsdetails geprüft und bei Bedarf anonymisiert.
