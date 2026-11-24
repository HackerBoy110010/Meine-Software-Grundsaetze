# Grundsatz 8: Visuelles System und Individualisierung

## Ziel

Ein Produkt besitzt eine konsistente, zugängliche Grundgestaltung und erlaubt weitreichende Individualisierung, ohne Bedienlogik oder Barrierefreiheit zu fragmentieren.

## Unabhängige visuelle Achsen

1. **UI-Stil** – Geometrie, Materialwirkung, Typografie und Controls
2. **Palette** – semantische Farben und Kontrastbeziehungen
3. **Atmosphäre** – optionale Texturen, Hintergründe, Partikel und Bewegung
4. **Dichte und Maßstab** – Abstände, Informationsdichte und Skalierung
5. **Accessibility-Overrides** – Kontrast, Fokus, Bewegung und Lesbarkeit

Die Achsen werden unabhängig modelliert, aber nicht ungeprüft zusammengesetzt. Die Kombinations-Engine aus [Grundsatz 10](10_MODULAR_DESIGN_COMBINATION_METHOD.md) erzeugt semantische Tokens, prüft Kompatibilität und wählt sichere Fallbacks.

## Null-Konfigurationsstandard

Jedes Produkt benötigt mindestens einen vollständig ausgearbeiteten Referenzzustand:

- klare Informationshierarchie,
- verständliche Primäraktion,
- ausreichender Kontrast,
- geringe unnötige Bewegung,
- konsistente Komponenten,
- getestete Desktop-, Touch- und Mobilgeometrie.

## Design-Tokens

Komponenten verwenden semantische Tokens statt harter Einzelwerte:

- Flächen: `surface`, `surface-raised`, `workspace`
- Text: `text`, `text-muted`, `text-inverse`
- Aktion: `accent`, `accent-hover`, `focus`
- Status: `success`, `warning`, `danger`, jeweils zusätzlich mit Icon/Text
- Layout: Dichte, Radius, Schatten, Bewegung, Typografie und Z-Ordnung

## Anpassungsgrenzen

- Nutzerpaletten müssen Mindestkontrast erfüllen oder eine sichere Alternative erhalten.
- Kritische Zustände behalten semantische Zusatzkennzeichnung.
- Organisations- oder Projektthemes dürfen persönliche Accessibility-Overrides nicht sperren.
- Importierte Themes werden validiert und führen keinen beliebigen Code aus.
- Jede Konfiguration besitzt Vorschau, Export und Reset.
- Unbekannte Token werden ignoriert oder migriert, nicht blind als CSS/Code ausgeführt.

## Abnahmekriterien

- Alle Kernkomponenten funktionieren im Referenzzustand, Hochkontrastmodus und mit reduzierter Bewegung.
- Themewechsel verändert keine fachlichen Daten oder Berechtigungen.
- Keine Komponente benötigt fest codierte produkt- oder projektspezifische Hexwerte.
- Kombinationen sind deterministisch und versionierbar.
- Referenzzustände werden als visuelle Regressionstests archiviert.
