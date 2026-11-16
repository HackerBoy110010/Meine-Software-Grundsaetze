# Grundsatz 5: Barrierefreiheit

## Ziel

Die Software bleibt unabhängig von Sehvermögen, Motorik, Gerät, Umgebungslicht und Bewegungsempfindlichkeit nutzbar. Barrierefreiheit ist kein Theme, sondern eine übergeordnete Produkteigenschaft.

## Persönliche Overrides

Folgende Einstellungen überschreiben Projekt-, Marken- und Atmosphärenvorgaben:

- Schrift- und UI-Skalierung,
- hoher Kontrast,
- reduzierte Bewegung,
- deaktivierte Shader, Partikel und Nebelanimationen,
- stärkere Fokusmarkierung,
- alternative Informationsdarstellung.

## Verbindliche Regeln

- Kein Zustand wird ausschließlich durch Farbe vermittelt.
- Interaktive Elemente besitzen sichtbaren Fokus und verständliche Beschriftung.
- Tastaturbedienung folgt einer logischen Reihenfolge.
- Touchziele bleiben ausreichend groß, auch bei kompakter Geometrie.
- Kontrast wird für Text, Controls und Zustände geprüft.
- Animationen respektieren `prefers-reduced-motion`.
- Grafische Werkzeuge benötigen textuelle Statusanzeigen und bedienbare Alternativen.
- Formulare verbinden Label, Hilfe und Fehler programmatisch.
- Dialoge verwalten Fokus korrekt und lassen sich schließen.
- Screenreader erhalten keine rein dekorativen Informationen.

## Datenvisualisierung und Echtzeitstatus

- Aktiver Schritt: Farbe plus Symbol, Text oder Umrandung.
- Sichtbar/verborgen: Farbe plus Icon und Beschriftung.
- Werkzeugmodi: aktueller Modus als Text.
- Messwerte und Zustände: Zahlen/Text zusätzlich zu Balken.
- Kurzzeitige Hinweise und Timer dürfen nicht nur kurz animiert sichtbar sein.

## Abnahmekriterien

- Hauptabläufe sind nur mit Tastatur ausführbar.
- 200 % Zoom zerstört keine Kernfunktion.
- Reduzierte Bewegung stoppt nicht nur Animationen, sondern verhindert auch unnötiges Parallax/Flackern.
- Automatisierte Prüfungen werden durch manuelle Touch-, Tastatur- und Screenreader-Checks ergänzt.
- Barrierefreiheitsfehler haben Vorrang vor atmosphärischen Verbesserungen.
