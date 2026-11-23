# Grundsatz 10: Modulare Design-Kombinationstechnik

## Zweck

Die Methode zerlegt visuelle Gestaltung in unabhängige, versionierte Achsen und führt sie über eine regelbasierte Engine zu einer konsistenten, zugänglichen Laufzeitgestaltung zusammen.

Sie besteht aus zwei Teilen:

1. **Achsenmodell** – standardisierte Beschreibung unabhängiger Gestaltungsdimensionen,
2. **Kombinations-Engine** – Validierung, Auflösung, Konfliktbehandlung und Token-Erzeugung.

## Achsenmodell

### UI-Stil

Definiert Geometrie und Formsprache:

- Komponentenform,
- Ecken und Konturen,
- Materialwirkung,
- Typografiecharakter,
- Schatten und Tiefe,
- grundlegende Interaktionsbewegung.

### Palette

Definiert keine Komponenten, sondern semantische Farbbeziehungen:

- Flächenhierarchie,
- Textstufen,
- Akzent und Fokus,
- Erfolg, Warnung und Gefahr,
- Datenvisualisierungsreihen,
- Hell-/Dunkelcharakter.

### Atmosphäre

Definiert optionale dekorative und emotionale Ebenen:

- Texturen,
- Hintergrundmotive,
- Partikel,
- Umgebungsbewegung,
- Sound- oder Lichtcharakter, sofern das Produkt dies unterstützt.

Atmosphäre darf keine fachliche Bedeutung tragen.

### Dichte und Maßstab

Definiert Informationsmenge und räumliche Skalierung unabhängig von Farbe und Stil.

### Accessibility-Overrides

Persönliche, höherrangige Regeln für Kontrast, Fokus, Schrift, Bewegung, Shader und alternative Signale.

## Normalisiertes Eingabemodell

Jede Achse liefert:

- stabile ID,
- Schemaversion,
- semantische Tokens,
- Fähigkeiten und Anforderungen,
- Kompatibilitätsregeln,
- Fallback-ID,
- Herkunft und Lizenzmetadaten.

Beispiel:

```json
{
  "id": "example-palette",
  "axis": "palette",
  "schemaVersion": 1,
  "provides": ["dark-surfaces", "semantic-status-colors"],
  "requires": ["text-contrast-validation"],
  "fallback": "accessible-dark",
  "tokens": {
    "surface": "#171820",
    "text": "#f5f2e8",
    "accent": "#d7ae62"
  }
}
```

## Kombinationspipeline

1. **Einlesen** – Quellen und Schemaversionen prüfen.
2. **Normalisieren** – Achsen in ein gemeinsames semantisches Modell überführen.
3. **Fähigkeiten auflösen** – `provides`, `requires` und Ausschlüsse vergleichen.
4. **Tokens mergen** – feste Rangfolge statt zufälliger Überschreibung.
5. **Accessibility anwenden** – persönliche Overrides haben Vorrang.
6. **Validieren** – Kontrast, Fokus, Bewegung, Vollständigkeit und erlaubte Werte prüfen.
7. **Reparieren** – kuratierte sichere Ersatzwerte einsetzen.
8. **Fallback** – bei nicht reparierbaren Konflikten auf bekannte Kombination zurückfallen.
9. **Kompilieren** – deterministischen Laufzeit-Token-Satz erzeugen.
10. **Protokollieren** – verwendete Versionen, Reparaturen und Warnungen nachvollziehbar machen.

## Rangfolge

```text
Sicherheitsregeln
> Accessibility-Overrides
> Geräte-/Plattformgrenzen
> Nutzerpräferenzen
> Projekt-/Organisationsvorgabe
> Preset
> Produktstandard
```

Eine niedrigere Ebene darf eine höhere nicht still überschreiben.

## Kompatibilitätsregeln

Regeln sind deklarativ und testbar, zum Beispiel:

- Mindestkontrast für Text und Controls,
- maximal erlaubte Bewegungsintensität,
- benötigte Tokenmenge,
- unzulässige Kombination aus transparenter Oberfläche und unruhigem Hintergrund,
- erforderliche Nicht-Farbsignale für Status,
- begrenzte Shaderleistung auf schwachen Geräten.

## Determinismus

Gleiche Eingaben, Schemaversion und Engineversion müssen denselben Output erzeugen. Der Output erhält eine reproduzierbare Kombinations-ID beziehungsweise einen Hash.

## Sichere Erweiterbarkeit

- Erweiterungen dürfen nur deklarative Daten liefern.
- Beliebiger JavaScript-, CSS- oder nativer Code ist kein Themebestandteil.
- Unbekannte Felder werden gemäß Schemaregel behandelt.
- Migrationen sind versioniert.
- Herkunft und Lizenz jeder Achse bleiben erhalten.

## Vorschau und Commit

Die Engine unterscheidet:

- `preview`: flüchtig, jederzeit verwerfbar,
- `validated`: vollständig geprüft,
- `committed`: persistent gespeichert,
- `fallback`: reparierter sicherer Zustand.

## Teststrategie

- Unit-Tests pro Regel,
- paarweise Kombinationstests,
- risikobasierte Mehrfachkombinationen,
- Property-based Tests für Tokeninvarianten,
- visuelle Regressionen,
- Accessibility-Prüfungen,
- Performancebudgets,
- deterministische Snapshot-Hashes.

## Abgrenzung

Die Methode ist kein einzelner Look und keine Sammlung bestimmter Farben. Sie ist eine allgemeine Architektur zur sicheren Kombination visueller Systeme. Konkrete Produkte können völlig unterschiedliche Achseninhalte verwenden und dennoch dieselbe Methode implementieren.
