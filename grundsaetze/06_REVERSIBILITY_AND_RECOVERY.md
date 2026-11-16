# Grundsatz 6: Reversibilität, Zustand und Wiederherstellung

## Ziel

Nutzer dürfen experimentieren, ohne berechtigte Angst vor Datenverlust. Kritische Aktionen sind vorhersehbar, nachvollziehbar und möglichst rückgängig zu machen.

## Verbindliche Regeln

- Archivieren ist bei historisch referenzierten Daten der Standard vor Löschen.
- Endgültiges Löschen benennt betroffene Objekte und Folgen.
- Vor irreversiblen Migrationen wird ein geprüftes Backup erstellt.
- Netzwerk- oder App-Abbruch erzeugt keine halben Transaktionen.
- Optimistic Updates besitzen Rollback oder Konfliktbehandlung.
- Versionskonflikte erklären, dass Daten auf einem anderen Gerät geändert wurden.
- Reset unterscheidet persönliche Einstellungen, Projekt- oder Organisationseinstellungen und Daten.
- Automatische Wiederherstellung überschreibt niemals stillschweigend neuere Daten.

## Zustandswahrheit

- „Gespeichert“ wird erst nach bestätigter Persistenz angezeigt.
- „Bereit“ wird erst nach bestandenem Health-/Readiness-Check angezeigt.
- Hintergrundprozesse zeigen `starting`, `ready`, `degraded`, `failed` oder `stopped`.
- Ein Diagnose-Fallback darf nicht als vollständige Funktion dargestellt werden.

## Wiederherstellungsleiter

1. Aktion erneut versuchen
2. lokalen Zustand neu laden
3. Konflikt auflösen
4. letzten sicheren Stand wiederherstellen
5. Backup importieren
6. kontrollierter Reset mit expliziter Bestätigung

## Protokollierung

Sicherheitsrelevante und irreversible Vorgänge protokollieren mindestens Zeitpunkt, Akteur, Objekt und Ergebnis. Geheimnisse und private Inhalte gehören nicht ungefiltert in Logs.

## Abnahmekriterien

- Objekte mit referenzierter Historie können nicht versehentlich endgültig gelöscht werden.
- Abgebrochene Abschluss- oder Veröffentlichungsprozesse hinterlassen keine halben Snapshots.
- Migrationstests umfassen eine befüllte ältere Datenbank.
- Start-/Stop-Abläufe werden mehrfach im selben Prozess getestet.
- Jeder destructive Button besitzt eine dokumentierte Recovery-Strategie.
