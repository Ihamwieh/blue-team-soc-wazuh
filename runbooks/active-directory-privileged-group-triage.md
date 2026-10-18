# Triage-Runbook: Änderung einer privilegierten Active-Directory-Gruppe

## Ziel

Strukturierte Untersuchung, wenn ein Benutzer zu einer privilegierten Active-Directory-Gruppe hinzugefügt oder daraus entfernt wurde.

## Erkennungsdaten

- **Logquelle:** Windows Security Event Log
- **Windows Event ID 4728:** Mitglied wurde einer globalen Sicherheitsgruppe hinzugefügt
- **Windows Event ID 4729:** Mitglied wurde aus einer globalen Sicherheitsgruppe entfernt
- **Wazuh-Regel:** 60159
- **Level:** 12
- **MITRE ATT&CK:** T1484 – Domain Policy Modification
- **Taktiken:** Defense Evasion, Privilege Escalation

## Triage-Schritte

1. Zeitpunkt und betroffenen Domain Controller prüfen.
2. Ausführendes Benutzerkonto ermitteln.
3. Geänderte Sicherheitsgruppe identifizieren.
4. Hinzugefügtes oder entferntes Mitglied bestimmen.
5. Prüfen, ob eine genehmigte administrative Änderung vorliegt.
6. Ereignisse 4728 und 4729 zeitlich miteinander vergleichen.
7. Nach weiteren Änderungen durch dasselbe Benutzerkonto suchen.
8. Zugehörige Anmelde-, Prozess- und PowerShell-Ereignisse untersuchen.
9. Berechtigungen des betroffenen Kontos kontrollieren.
10. Ergebnis und Beweise dokumentieren.

## Bewertung

- **Benign True Positive:** Eine autorisierte administrative Änderung wurde korrekt erkannt.
- **True Positive / Incident:** Ein Konto wurde ohne Genehmigung einer privilegierten Gruppe hinzugefügt oder daraus entfernt.
- **False Positive:** Die Regel wurde ausgelöst, obwohl keine relevante Gruppenänderung stattfand.

## Reaktion bei nicht autorisierter Änderung

1. Gruppenänderung rückgängig machen.
2. Betroffenes Konto sperren oder dessen Sitzungen beenden.
3. Zugangsdaten des ausführenden Kontos zurücksetzen.
4. Weitere privilegierte Gruppen und Konten überprüfen.
5. Windows- und Wazuh-Protokolle sichern.
6. Ursache, Auswirkungen und Maßnahmen dokumentieren.

## Laborergebnis

Im kontrollierten Labortest wurde ein Testkonto zur Gruppe **Domain Admins** hinzugefügt und anschließend wieder entfernt. Windows erzeugte die Ereignisse **4728** und **4729**. Wazuh erkannte die privilegierte Gruppenänderung mit **Regel 60159 auf Level 12**. Der autorisierte Test wurde als **Benign True Positive** klassifiziert.
