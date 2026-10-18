# Validierte Detection-Tests

Alle Tests wurden ausschließlich in der autorisierten und isolierten SOC-Laborumgebung durchgeführt.

## Test 1: Encoded PowerShell

### Ziel

Prüfen, ob eine Base64-codierte PowerShell-Ausführung durch Sysmon protokolliert und von Wazuh erkannt wird.

### Testsystem

Windows-Endpunkt `ham1`

### Erwartetes Ergebnis

- Sysmon erzeugt Event ID 1.
- Wazuh erkennt die codierte PowerShell-Ausführung.
- Der Alert wird MITRE ATT&CK T1059.001 zugeordnet.

### Tatsächliches Ergebnis

- Sysmon Event ID: 1
- Wazuh-Regel: 92057
- Level: 12
- MITRE ATT&CK: T1059.001 – PowerShell
- Taktik: Execution
- Status: Erfolgreich
- Klassifizierung: Benign True Positive

---

## Test 2: Security Privileges Enumeration

### Ziel

Prüfen, ob die Ausführung von `whoami.exe` mit dem Parameter `/priv` durch die Sigma-basierte Wazuh-Regel erkannt wird.

### Erwartetes Ergebnis

- Sysmon protokolliert den Prozessstart.
- Wazuh-Regel 100120 erkennt `whoami.exe` mit `/priv` oder `-priv`.

### Tatsächliches Ergebnis

- Wazuh-Regel: 100120
- Level: 8
- Parent Rule: 61603
- MITRE ATT&CK: T1033 – System Owner/User Discovery
- Taktik: Discovery
- Status: Erfolgreich
- Klassifizierung: Benign True Positive

---

## Test 3: Netzwerk-Scan über Windows-Telemetrie

### Ziel

Prüfen, ob mehrere Netzwerkverbindungen des autorisierten Kali-Testsystems durch Windows und Wazuh erkannt und korreliert werden.

### Erwartetes Ergebnis

- Windows erzeugt Event ID 5156.
- Regel 100110 erkennt Verbindungen von der Kali-Adresse.
- Regel 100111 erzeugt nach mindestens zehn Verbindungen innerhalb von 60 Sekunden einen korrelierten Alert.

### Tatsächliches Ergebnis

- Quellsystem: Autorisiertes Kali-Testsystem
- Windows Event ID: 5156
- Wazuh-Grundregel: 100110, Level 5
- Wazuh-Korrelationsregel: 100111, Level 10
- MITRE ATT&CK: T1046 – Network Service Discovery
- Status: Erfolgreich
- Klassifizierung: Benign True Positive

---

## Test 4: TCP-SYN-Port-Scan mit Suricata

### Ziel

Prüfen, ob Suricata einen kontrollierten TCP-SYN-Port-Scan gegen den Ubuntu-Sensor erkennt und das Ereignis an Wazuh übermittelt.

### Erwartetes Ergebnis

- Suricata erzeugt einen Alert mit Signature ID 1000002.
- Der Alert wird in `eve.json` gespeichert.
- Der Wazuh Agent übermittelt das Ereignis an den Manager.
- Wazuh-Regel 100121 erzeugt einen Alert.

### Tatsächliches Ergebnis

- Suricata Signature ID: 1000002
- Wazuh-Regel: 100121
- Level: 8
- MITRE ATT&CK: T1046 – Network Service Discovery
- Status: Erfolgreich
- Klassifizierung: Benign True Positive

---

## Test 5: Änderung der Domain-Admins-Gruppe

### Ziel

Prüfen, ob das Hinzufügen und Entfernen eines Testkontos in der Gruppe `Domain Admins` erkannt wird.

### Erwartetes Ergebnis

- Windows erzeugt Event ID 4728 beim Hinzufügen.
- Windows erzeugt Event ID 4729 beim Entfernen.
- Wazuh erkennt die Änderung der privilegierten Gruppe.

### Tatsächliches Ergebnis

- Windows Event IDs: 4728 und 4729
- Wazuh-Regel: 60159
- Level: 12
- MITRE ATT&CK: T1484 – Domain Policy Modification
- Taktiken: Defense Evasion und Privilege Escalation
- Status: Erfolgreich
- Klassifizierung: Benign True Positive

## Gesamtergebnis

Die fünf kontrollierten Tests erzeugten die erwartete Telemetrie und die vorgesehenen Wazuh-Alerts. Dadurch wurden Erkennungen auf Endpoint-, Active-Directory- und Netzwerkebene nachvollziehbar validiert.
