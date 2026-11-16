# Grundsatz 3: Rollen- und kontextgerechte UX

## Ziel

Unterschiedliche Rollen sind nicht bloß Farbvarianten derselben Oberfläche. Jede Rolle erhält die Informationen und Werkzeuge, die sie im aktuellen Arbeitskontext benötigt.

## Rollenmodell

Rollen werden aus fachlichen Aufgaben und Berechtigungen abgeleitet, zum Beispiel:

- Administration und Systemeinstellungen,
- Erstellung und Freigabe,
- Bearbeitung eigener Inhalte,
- Prüfung oder Moderation,
- reine Ansicht,
- öffentlicher Präsentationsmodus.

Eine Rolle beschreibt nicht nur, was sichtbar ist, sondern welche Entscheidungen, Risiken und Hauptaktionen relevant sind.

## Kontext vor Konfiguration

Die Oberfläche berücksichtigt zusätzlich:

- aktuell geöffnetes Projekt oder Objekt,
- Lebenszyklusstatus wie Entwurf, aktiv, pausiert oder abgeschlossen,
- ausgewählte Person, Ressource oder Datensicht,
- Gerätetyp und Präsentationsmodus,
- online, reconnecting oder offline,
- persönliche Accessibility- und Dichtepräferenzen.

## Verbindliche Regeln

- Sichere Berechtigungen werden serverseitig beziehungsweise in der vertrauenswürdigen Datenschicht durchgesetzt.
- Ausblenden in der UI ersetzt keine Autorisierung.
- Nicht freigegebene Daten sind standardmäßig privat.
- Hauptaktionen unterscheiden sich strukturell nach Rolle und Kontext.
- Eingeschränkte Ansichten erklären ihren Umfang, ohne verborgene Inhalte zu verraten.
- Status wird nicht nur durch Farbe kommuniziert.
- Rollenwechsel und Kontextwechsel dürfen keine ungespeicherten Änderungen still verwerfen.

## Präsentations- und Kioskmodus

- aus Entfernung lesbar,
- keine privaten Daten oder Verwaltungsnavigation,
- automatischer Reconnect,
- klarer Warte-, Offline- und Fehlerzustand,
- keine Steuerung, die nur über versteckte Gesten erreichbar ist.

## Anti-Patterns

- dieselbe überladene Navigation für alle Rollen,
- deaktivierte Adminaktionen in Nutzeransichten statt passender Nutzerabläufe,
- clientseitig versteckte, aber direkt abrufbare vertrauliche Daten,
- Rollenname als Ersatz für konkrete Berechtigungen,
- öffentliche Displays mit Kontodaten oder internen Notizen.

## Abnahmekriterien

- Direkte URLs und APIs respektieren dieselben Berechtigungen wie die Oberfläche.
- Jede Hauptrolle besitzt einen dokumentierten primären Einstieg.
- Lebenszyklusstatus verändern erlaubte Aktionen nachvollziehbar.
- Präsentationsansichten enthalten ausschließlich freigegebene Daten.
- Berechtigungstests umfassen positive und negative Fälle.
