# Grundsatz 4: Navigation und Arbeitsflächen

## Ziel

Große Arbeitsbereiche, geringe Seitenscrolltiefe und eine Navigation, die sich dem aktuellen Arbeitskontext anpasst.

## Navigationsmodell

### Globale Ebene

Enthält nur produktweite Ziele, beispielsweise Projekte, Bibliothek, Suche, Konto und Administration.

### Kontextuelle Ebene

Beim Öffnen eines Projekts, Dokuments oder Arbeitsbereichs ersetzt eine spezifische Navigation die globale Hauptnavigation. Ein sichtbarer Rückweg zur globalen Ebene ist verpflichtend.

### Fokussierter Arbeitsplatz

- kompakte Kopfleiste,
- optionale linke Auswahl- oder Baumleiste,
- große zentrale Arbeitsfläche,
- optionale rechte Detail- oder Inspektorleiste,
- interner Panel-Scroll statt unnötigem Ganzseitenscrollen.

## Darstellungsregeln

- Grid, wenn ausreichend Fläche vorhanden ist und keine Reihenfolge dominiert.
- Liste für Navigation, Chronologie, Nachrichten, Prioritäten und Baumstrukturen.
- Grid/List-Umschaltung nur, wenn beide Darstellungen einen echten Nutzen haben.
- Hohe Informationsdichte darf Touchziele und Lesbarkeit nicht verkleinern.
- Vollbild konzentriert sich auf Inhalt; Exit und aktueller Zustand bleiben erreichbar.
- Mobilgeräte priorisieren Hauptaktion und Inhalt statt alle Desktop-Panels zu stapeln.

## Orientierung

Jeder Kontext zeigt:

- globalen oder projektspezifischen Bereich,
- geöffnetes Objekt und Lebenszyklusstatus,
- aktuelle Rolle oder Berechtigungsstufe, soweit relevant,
- aktuelle Auswahl,
- sichtbaren Rückweg.

## Anti-Patterns

- globale und kontextuelle Navigation gleichzeitig in voller Größe,
- tiefe Breadcrumbs ohne klare Rückaktion,
- ganze Seiten für einzelne kleine Widgets,
- horizontale Navigation, die Hauptaktionen auf Mobilgeräten versteckt,
- modale Dialogketten für normale Arbeit,
- Browser-Zurück mit Datenverlust.

## Abnahmekriterien

- Der Kernarbeitsbereich nutzt auf großen Bildschirmen den überwiegenden Teil der Höhe.
- Zentrale Aktionen sind mit höchstens zwei bewussten Navigationsebenen erreichbar.
- Browser-Zurück und sichtbarer Zurück-Button sind vorhersehbar.
- Mobile Navigation bleibt mit Touch und Bildschirmtastatur bedienbar.
- Panels besitzen sinnvolle minimale, maximale und zurücksetzbare Größen.
