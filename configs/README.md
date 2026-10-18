# Konfigurationsauszüge

Dieses Verzeichnis enthält geprüfte Konfigurationsauszüge aus dem SOC-Labor. Die Dateien zeigen nur die für die dokumentierten Anwendungsfälle relevanten Einstellungen und sind keine vollständigen Konfigurationsdateien.

## Windows Sysmon

Datei: [`windows-sysmon-eventchannel.xml`](windows-sysmon-eventchannel.xml)

Der Wazuh Agent überwacht den Ereigniskanal:

`Microsoft-Windows-Sysmon/Operational`

Dadurch werden unter anderem Sysmon-Prozessstarts als Event ID 1 erfasst und zur Analyse an den Wazuh Manager übertragen.

## Ubuntu und Suricata

Datei: [`ubuntu-suricata-wazuh-agent.xml`](ubuntu-suricata-wazuh-agent.xml)

Der Wazuh Agent liest die Suricata-Ereignisse aus:

`/var/log/suricata/eve.json`

Die Ereignisse werden als JSON verarbeitet und an den Wazuh Manager übertragen.

## Datenfluss

1. Sysmon oder Suricata erzeugt ein Ereignis.
2. Der Wazuh Agent liest das Ereignis.
3. Der Wazuh Manager analysiert es anhand der Regeln.
4. Der Wazuh Indexer speichert und indexiert das Ergebnis.
5. Der Alert wird im Wazuh Dashboard untersucht.

## Sicherheit

Vollständige Konfigurationsdateien, Zugangsdaten, Schlüssel und vertrauliche Verbindungsinformationen werden nicht veröffentlicht.
