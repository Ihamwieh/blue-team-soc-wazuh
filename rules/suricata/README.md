# Suricata-Regeln

Dieses Verzeichnis enthält die im SOC-Labor erstellten und getesteten lokalen Suricata-Regeln.

## Regel 1000001 – ICMP-Erkennung

- **Protokoll:** ICMP
- **ICMP-Typ:** 8 (Echo Request)
- **Zielsystem:** Ubuntu, 192.168.20.20
- **Zweck:** Erkennung von ICMP-Ping-Anfragen
- **Signatur-ID:** 1000001
- **Revision:** 1

## Regel 1000002 – TCP-SYN-Port-Scan

- **Protokoll:** TCP
- **TCP-Flag:** SYN
- **Modus:** Stateless
- **Zielsystem:** Ubuntu, 192.168.20.20
- **Schwellwert:** 20 SYN-Pakete derselben Quelladresse innerhalb von 10 Sekunden
- **Klassifizierung:** `attempted-recon`
- **Signatur-ID:** 1000002
- **Revision:** 1
- **MITRE ATT&CK:** T1046 – Network Service Discovery

## Ereignisweiterleitung

Suricata schreibt die erkannten Netzwerkereignisse in die Datei `eve.json`. Der Wazuh Agent auf Ubuntu überwacht diese Datei und überträgt die Ereignisse an den Wazuh Manager.

## Validierung

Die Regel 1000002 wurde durch einen autorisierten Nmap-Test innerhalb der isolierten Laborumgebung ausgelöst. Das Suricata-Ereignis und der zugehörige Wazuh-Alert wurden im Dashboard geprüft und dokumentiert.
