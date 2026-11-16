# Grundsatz 1: Happy UI

## Ziel

Software soll die aktuelle Aufgabe erleichtern und niemals unnötige Verwaltungsarbeit erzeugen. Jede Ansicht vermittelt Orientierung, aktuellen Zustand und einen sinnvollen nächsten Schritt.

## Verbindliche Regeln

- Es gibt keine absichtlich leeren oder bedeutungslosen Seiten.
- Jede Ansicht zeigt mindestens Kontext, Zustand und verfügbare Hauptaktion.
- Jeder Leerzustand erklärt:
  1. warum noch nichts angezeigt wird,
  2. wie Inhalte entstehen,
  3. welche Aktion jetzt empfohlen wird,
  4. welche Alternative oder Rückkehrmöglichkeit existiert.
- Lade-, Offline-, Fehler-, gesperrte und schreibgeschützte Zustände sind eigene gestaltete Zustände.
- Fehlertexte benennen Problem, Auswirkung und nächsten Handlungsschritt.
- Primäraktionen verwenden konkrete Verben: „Veröffentlichung starten“ statt „OK“.
- Erfolgreiche Aktionen geben angemessenes Feedback, ohne den Spielfluss zu unterbrechen.
- Unfertige Funktionen werden nicht als tote Navigation angeboten. Sie werden verborgen oder klar experimentell gekennzeichnet.

## Zustandsmodell einer Ansicht

Jede datenabhängige Ansicht berücksichtigt mindestens:

- `loading`
- `ready-with-content`
- `ready-empty`
- `permission-limited`
- `offline/reconnecting`
- `recoverable-error`
- `fatal-error`
- `read-only/finished`

## Tonalität

- freundlich, direkt und respektvoll,
- keine Schuldzuweisung,
- keine unnötigen Fachbegriffe,
- Deutsch als Referenzsprache; Englisch inhaltlich gleichwertig,
- keine ironischen Fehlermeldungen in kritischen Situationen.

## Anti-Patterns

- weiße oder dunkle leere Fläche ohne Erklärung,
- deaktivierter Button ohne Begründung,
- technische Exception als einzige Nutzerinformation,
- fünf gleichgewichtete Hauptaktionen,
- Erfolgsmeldung ohne sichtbares Ergebnis,
- automatische Navigation ohne erkennbaren Zustand.

## Abnahmekriterien

- Ein neuer Nutzer kann in höchstens 10 Sekunden erklären, wo er ist.
- Für jeden Leerzustand existiert mindestens eine sinnvolle Aktion.
- Fehler lassen sich ohne Neuladen der gesamten App erneut versuchen, sofern technisch möglich.
- Der aktuelle Arbeits- und Lebenszyklusstatus ist jederzeit sichtbar.
- Ein Playtest protokolliert keine Situation „Ich weiß nicht, was ich jetzt tun soll“ ohne nachfolgende UX-Aufgabe.
