# Sigma-Regel in Wazuh

Dieses Verzeichnis dokumentiert eine Sigma-basierte Erkennungslogik, die für Wazuh als lokale XML-Regel umgesetzt und im SOC-Labor getestet wurde.

## Security Privileges Enumeration via whoami.exe

- **Wazuh-Regel-ID:** 100120
- **Level:** 8
- **Übergeordnete Wazuh-Regel:** 61603
- **Logquelle:** Sysmon Process Creation, Event ID 1
- **Prozess:** `whoami.exe`
- **Parameter:** `/priv` oder `-priv`
- **MITRE ATT&CK:** T1033 – System Owner/User Discovery
- **Taktik:** Discovery
- **Datei:** `sigma_rules.xml`

## Erkennungslogik

Die Regel prüft, ob `whoami.exe` mit dem Parameter `/priv` oder `-priv` gestartet wurde. Dieser Befehl zeigt die Sicherheitsprivilegien des aktuell angemeldeten Benutzers an und kann während der Systemerkundung eingesetzt werden.

## Umsetzung

Die Erkennungslogik basiert auf einer Sigma-Regel und wurde an die von Wazuh verarbeiteten Sysmon-Felder angepasst. Die veröffentlichte XML-Datei ist eine Wazuh-Regel und keine direkt importierbare Sigma-YAML-Datei.

## Validierung

Der Befehl wurde kontrolliert in der isolierten Laborumgebung ausgeführt. Sysmon protokollierte den Prozessstart und Wazuh erzeugte den erwarteten Alert der Regel 100120.

## Mögliche False Positives

Administratoren können `whoami /priv` bei legitimer Fehleranalyse oder Rechteprüfung verwenden. Deshalb müssen Benutzer, übergeordneter Prozess, Zeitpunkt und Systemkontext während der Triage geprüft werden.
