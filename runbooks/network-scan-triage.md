# Triage-Runbook: Netzwerk-Scan

## Ziel

Strukturierte Untersuchung eines möglichen Netzwerk-Scans, der durch Windows-Telemetrie oder Suricata erkannt wurde.

## Erkennungsdaten

### Windows-basierte Erkennung

- **Wazuh-Regel:** 100111
- **Level:** 10
- **Grundregel:** 100110
- **Logquelle:** Windows Filtering Platform
- **Windows Event ID:** 5156
- **MITRE ATT&CK:** T1046 – Network Service Discovery

### Suricata-basierte Erkennung

- **Suricata Signature ID:** 1000002
- **Wazuh-Regel:** 100121
- **Level:** 8
- **Klassifizierung:** `attempted-recon`
- **MITRE ATT&CK:** T1046 – Network Service Discovery

## Triage-Schritte

1. Quell- und Ziel-IP-Adresse prüfen.
2. Zeitpunkt und Dauer der Aktivität bestimmen.
3. Betroffene Zielports und verwendetes Protokoll untersuchen.
4. Anzahl und Häufigkeit der Verbindungsversuche prüfen.
5. Feststellen, ob die Quelladresse zu einem autorisierten Testsystem gehört.
6. Windows-, Suricata- und Wazuh-Ereignisse zeitlich miteinander vergleichen.
7. Nach weiteren Aktivitäten derselben Quelle suchen.
8. Prüfen, ob auf dem Zielsystem anschließend Anmelde- oder Prozessereignisse aufgetreten sind.

## Bewertung

- **Benign True Positive:** Ein autorisierter Nmap-Test wurde korrekt erkannt.
- **True Positive / Incident:** Ein nicht autorisiertes System führt einen Scan durch.
- **False Positive:** Normaler Netzwerkverkehr erfüllt unbeabsichtigt den definierten Schwellwert.

## Reaktion bei nicht autorisierter Aktivität

1. Quelladresse vorübergehend blockieren oder System isolieren.
2. Umfang des Scans und betroffene Systeme feststellen.
3. Erreichbare Dienste und mögliche Folgeaktivitäten untersuchen.
4. Firewall- und Netzwerkprotokolle sichern.
5. Ursache beseitigen und Erkennungsregel bei Bedarf abstimmen.
6. Ergebnis und durchgeführte Maßnahmen dokumentieren.

## Laborergebnis

Ein autorisierter Nmap-Test aus dem Kali-Testsystem wurde durch die Wazuh- und Suricata-Erkennungen identifiziert. Die Alerts wurden als **Benign True Positive** klassifiziert.
