# Grundsatz 9: Engineering-Qualität und Experimente

## Ziel

Technische Breite zählt nur, wenn sie in zuverlässige, verständliche Abläufe mündet. Getestete Realität wird strikt von Zielbild und Experiment getrennt.

## Verbindliche Regeln

- Vor Änderung von Logik oder Datenfluss wird der tatsächliche Code gelesen.
- Änderungen erfolgen in begrenzten Blöcken mit klaren Abbruchkriterien.
- Fehlgeschlagene lange Befehle werden nicht unverändert wiederholt.
- Jeder Block meldet, was bestanden, blockiert und noch experimentell ist.
- Shared Contracts, Importformate und Designsystemänderungen aktualisieren die Projektbrücke.
- Datenbankänderungen erhalten Migration, Altbestandstest und Rollback-/Backupstrategie.
- Backendberechtigungen werden getestet, nicht nur UI-Sichtbarkeit.
- Realtime besitzt Reconnect, Zustandssynchronisierung und kontrollierten Fallback.
- Debug- und Release-Sicherheitsregeln bleiben getrennt.

## Definition of Done

Eine Funktion ist erst fertig, wenn:

1. Hauptablauf implementiert ist,
2. Leer-, Lade-, Fehler- und Berechtigungszustände existieren,
3. Deutsch und Englisch vollständig sind,
4. relevante Tests bestehen,
5. Migration und Altbestand berücksichtigt sind,
6. Dokumentation den echten Stand beschreibt,
7. keine bekannte kritische Sackgasse offen bleibt.

## Experimente

- eigene Flags, Builds oder Workflows,
- keine automatische Aktivierung im stabilen Build,
- feste Zeitlimits,
- messbare Erfolgskriterien,
- Diagnoseartefakte ohne Geheimnisse,
- explizite Entscheidung: übernehmen, weiter untersuchen oder verwerfen.

## Kommunikation

Nicht zulässig:

- „vollständig“, wenn nur ein Fundament existiert,
- „grün“, wenn der falsche Workflow betrachtet wurde,
- „wie das Original“, wenn nur eine grobe Ähnlichkeit besteht,
- Verschweigen von Fallbacks oder fehlenden nativen Abhängigkeiten.

## Abnahmekriterien

- CI trennt schnelle Standardprüfungen und teure manuelle Spikes.
- Patchserien haben klare Voraussetzungen und Reihenfolge.
- Repository ist vor Übergabe sauber.
- Release Notes nennen Einschränkungen sichtbar.
- Ein realer Playtest beeinflusst die Priorisierung stärker als reine Featureanzahl.
