# Triage-Runbook: Codierte PowerShell-Ausführung

## Ziel

Strukturierte Untersuchung eines Wazuh-Alerts zu einer PowerShell-Ausführung mit codiertem Befehl.

## Erkennungsdaten

- **Wazuh-Regel:** 92057
- **Level:** 12
- **Logquelle:** Sysmon
- **Sysmon Event ID:** 1
- **MITRE ATT&CK:** T1059.001 – PowerShell
- **Taktik:** Execution

## Triage-Schritte

1. Zeitpunkt, Agent und betroffenen Windows-Endpunkt prüfen.
2. Benutzerkonto und Anmeldesitzung identifizieren.
3. Prozesspfad von `powershell.exe` kontrollieren.
4. Vollständige Command Line untersuchen.
5. Parent Process und auslösende Anwendung prüfen.
6. Codierten Inhalt sicher decodieren und analysieren.
7. Nach weiteren Alerts desselben Benutzers oder Endpunkts suchen.
8. Prüfen, ob die Ausführung Teil eines autorisierten Tests oder administrativen Vorgangs war.

## Bewertung

- **Benign True Positive:** Die Aktivität wurde korrekt erkannt und war ein autorisierter Labortest.
- **True Positive / Incident:** Die Ausführung war nicht autorisiert oder zeigt weitere verdächtige Aktivitäten.
- **False Positive:** Die Erkennungslogik hat ein Ereignis technisch falsch bewertet.

## Reaktion bei nicht autorisierter Aktivität

1. Betroffenen Endpunkt isolieren.
2. Relevante Logs und Prozessinformationen sichern.
3. Benutzerkonto und mögliche Folgeaktivitäten untersuchen.
4. Weitere Ausführungen desselben Befehls in der Umgebung suchen.
5. Ursache beseitigen und Zugangsdaten bei bestätigter Kompromittierung schützen oder ändern.
6. Maßnahmen, Ergebnis und Lessons Learned dokumentieren.

## Laborergebnis

Der kontrollierte PowerShell-Test wurde durch Sysmon erfasst und von Wazuh mit Regel 92057 auf Level 12 erkannt. Der Alert wurde als **Benign True Positive** klassifiziert.
