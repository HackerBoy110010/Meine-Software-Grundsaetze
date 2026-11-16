# Modulares adaptives Designsystem – allgemeine Gesamtspezifikation

**Version:** 2.0 – allgemeine Fassung  
**Sprache:** Produktabhängig; alle Inhalte und Layouts müssen lokalisierbar sein  
**Zweck:** Produktunabhängige Spezifikation für kombinierbare, zugängliche und performante Oberflächensysteme

---

## Inhaltsübersicht

1. Ziel, Geltungsbereich und Beispielregeln
2. Grundsätze und unabhängige Designachsen
3. technische Theme-Identität und Design-Tokens
4. illustrative Stil-, Paletten-, Atmosphären- und Presetbibliotheken
5. Shader-, Effekt- und Performance-System
6. Komponenten-, Responsive- und Accessibility-Regeln
7. Icon-, Import-/Export- und Dateiformate
8. Projektstruktur, Provider, Geltungsbereiche und Migration
9. Abnahmekriterien und Mindeststandard
10. formale Kombinations-Engine
11. produktunabhängige Übernahmecheckliste

Die Nummerierung folgt den ausführlichen Hauptabschnitten; Anhänge vertiefen die Engine und Implementierungsprüfung.

---

## 1. Ziel

Dieses Dokument beschreibt ein allgemeines, modulares Designsystem. Unterschiedliche Anwendungen können damit konsistent gestaltet werden, ohne technisch voneinander abhängig zu sein oder denselben visuellen Look verwenden zu müssen.

Das System ist inspiriert vom kombinierbaren Ansatz moderner Theme-Systeme: **Oberflächenstil, Farbpalette und Atmosphäre sind voneinander getrennt**. Nutzer können ein fertiges Preset wählen oder diese Ebenen selbst kombinieren.

Das Design-System muss:

- auf Desktop, Tablet und Smartphone funktionieren,
- Web, PWA, Capacitor/Android und optionale Desktop-Hüllen unterstützen,
- komplett offline funktionieren,
- Deutsch und Englisch berücksichtigen,
- barrierefrei und mit Touch bedienbar sein,
- dekorativ wirken, ohne die Lesbarkeit zu verschlechtern,
- private, öffentliche und rollenspezifische Zustände eindeutig darstellen,
- ohne fest codierte Farben in einzelnen Komponenten auskommen.

> Dieses Dokument beschreibt eine vollständige Referenzarchitektur. Kein Produkt muss alle Beispielstile, Paletten oder Effekte implementieren. Verbindlich sind die Prinzipien, Schnittstellen, Sicherheitsgrenzen und Validierungsregeln; konkrete Beispiele sind austauschbar.

---

## 1.1 Normative Regeln und illustrative Beispiele

Dieses Dokument unterscheidet zwei Arten von Inhalt:

- **Normativ:** Prinzipien, Sicherheitsgrenzen, Prioritäten, Tokenrollen, Validierung, Accessibility, Fallbacks und Tests.
- **Illustrativ:** Namen, Hexwerte, Stile, Atmosphären, Presets, Komponentenbeispiele und Codeausschnitte.

Illustrative Beispiele dienen ausschließlich dem Verständnis. Sie sind **keine Pflichtvorgabe**, keine vollständige Implementierung und keine Aussage, dass ein Produkt exakt so aussehen oder funktionieren muss. Ein Produkt darf Beispiele ersetzen, reduzieren, erweitern oder völlig anders benennen, solange die normativen Regeln erhalten bleiben.

Insbesondere gilt:

- Beispielpaletten sind keine universell richtigen Farbsysteme.
- Beispielstile sind keine abschließende Taxonomie.
- Beispielshader sind optional und benötigen geräteabhängige Fallbacks.
- Beispielpresets sind Ausgangspunkte, keine Produktanforderungen.
- Codebeispiele zeigen Verträge und Datenfluss, nicht zwingend die endgültige Programmiersprache oder Architektur.

---

## 2. Unabhängige Designachsen

### 2.0 Übergeordnete Grundsätze

### Happy UI

- Keine leeren oder bedeutungslosen Ansichten.
- Jeder Zustand erklärt Kontext, Ursache und nächsten sinnvollen Schritt.
- Lade-, Fehler-, Offline-, Berechtigungs- und Leerzustände sind gestaltete Produktzustände.
- Primäraktionen verwenden konkrete Verben.

### Einfacher Standard, tiefe Anpassung

1. polierter Null-Konfigurationsstandard,
2. wenige kuratierte Presets,
3. normale Anpassung,
4. bewusst geöffnete Expertenebene.

### Reversibilität

- Vorschau ist flüchtig.
- Änderungen werden erst nach Validierung persistent.
- Reset, Export und sichere Fallbacks sind Bestandteil des Systems.

### Accessibility vor Atmosphäre

Persönlicher Kontrast, Schriftmaßstab, Fokus und reduzierte Bewegung überschreiben dekorative oder organisatorische Vorgaben. Status wird nie nur durch Farbe dargestellt.

### Determinismus

Gleiche Eingaben, Engineversion und Schemaversion erzeugen denselben Tokenoutput und dieselbe Kombinations-ID.

### 2.1 Oberflächenstil

Steuert Form und Verhalten der Oberfläche:

- Schriftfamilien und Überschriften
- Kartenform und Rahmen
- Eckenradien
- Schatten
- Navigation
- Buttons und Eingabefelder
- Schalter und Auswahlfelder
- Icon-Familie
- Informationsdichte
- Animationen

### 2.2 Farbpalette

Steuert ausschließlich semantische Farben:

- Hintergrund
- Oberflächen
- Text und gedämpfter Text
- Primär- und Sekundärakzent
- Fokus
- Erfolg, Warnung und Gefahr
- optionale domänenspezifische Akzente
- vertraulich/privat
- optionale Kategorien oder Datenreihen

### 2.3 Atmosphäre

Steuert optionale Dekoration:

- Texturen
- Hintergrundmuster
- Ornamente
- Partikel
- Licht- und Nebeleffekte
- sehr dezente Umgebungsanimationen

Atmosphäre darf niemals Navigation, Kontrast oder Bedienlogik verändern. Sie muss vollständig abschaltbar sein.

---

## 3. Technische Theme-Identität

Am Wurzelelement der App werden drei Attribute gesetzt:

```html
<html
  data-ui-style="adventurer"
  data-color-palette="dragonfire"
  data-atmosphere="torch-dungeon"
>
```

Empfohlene Speicherung:

```ts
export interface ThemeSelection {
  uiStyle: string;
  colorPalette: string;
  atmosphere: string;
  iconSet: string;
  density: "comfortable" | "compact";
  motion: "none" | "reduced" | "subtle" | "full";
  fontScale: number;
}
```

Persönliche Einstellungen gehören ins Nutzerprofil und zusätzlich als lokaler Fallback in den Gerätespeicher. Ein Projekt oder eine Organisation darf ein Theme **empfehlen**, aber niemals persönliche Barrierefreiheitseinstellungen überschreiben.

---

## 4. Verbindliche Design-Tokens

Komponenten dürfen nur semantische Tokens verwenden. Direkte Werte wie `#ff0000` gehören ausschließlich in Palettendateien.

### 4.1 Farben

Die folgenden Werte und zusätzlichen Rollen wie `magic`, `secret` oder `rarity` sind illustrative Erweiterungsbeispiele. Allgemeine Implementierungen dürfen sie entfernen oder durch eigene fachliche Rollen ersetzen. Verbindlich ist die semantische Trennung, nicht der konkrete Name.

```css
:root {
  --color-bg: #17131f;
  --color-bg-elevated: #201827;
  --color-surface: #291f31;
  --color-surface-raised: #382a42;
  --color-surface-hover: #473550;
  --color-border: #66536d;

  --color-text: #fff7e6;
  --color-text-muted: #cbbdca;
  --color-text-disabled: #918492;
  --color-on-accent: #ffffff;

  --color-accent: #d55238;
  --color-accent-hover: #eb684d;
  --color-accent-secondary: #e6a84f;
  --color-focus: #ffd166;

  --color-success: #55b978;
  --color-warning: #e3a63b;
  --color-danger: #e45c67;
  --color-info: #5aa9e6;
  --color-magic: #a987e8;
  --color-secret: #cc73d9;

  --color-rarity-common: #aeb3ba;
  --color-rarity-uncommon: #58ad6b;
  --color-rarity-rare: #4f91e8;
  --color-rarity-very-rare: #9a63df;
  --color-rarity-legendary: #e79b3b;
  --color-rarity-artifact: #d95b5b;
}
```

### 4.2 Abstände

Grundraster: **4 px**.

```css
:root {
  --space-0: 0;
  --space-1: 0.25rem;  /* 4 px */
  --space-2: 0.5rem;   /* 8 px */
  --space-3: 0.75rem;  /* 12 px */
  --space-4: 1rem;     /* 16 px */
  --space-5: 1.25rem;  /* 20 px */
  --space-6: 1.5rem;   /* 24 px */
  --space-8: 2rem;     /* 32 px */
  --space-10: 2.5rem;  /* 40 px */
  --space-12: 3rem;    /* 48 px */
  --space-16: 4rem;    /* 64 px */
}
```

### 4.3 Radien

```css
:root {
  --radius-xs: 4px;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-pill: 999px;
}
```

Der Oberflächenstil darf diese Werte überschreiben. Pixel- und Stein-Stile verwenden beispielsweise kleine oder keine Rundungen, komfortable und moderne Stile größere Radien.

### 4.4 Schatten

```css
:root {
  --shadow-sm: 0 2px 8px rgb(0 0 0 / 0.22);
  --shadow-md: 0 8px 24px rgb(0 0 0 / 0.30);
  --shadow-lg: 0 18px 60px rgb(0 0 0 / 0.38);
  --shadow-focus: 0 0 0 3px color-mix(in srgb, var(--color-focus), transparent 20%);
}
```

### 4.5 Typografie

```css
:root {
  --font-body: "Inter", system-ui, sans-serif;
  --font-heading: "Cinzel", "Georgia", serif;
  --font-mono: "JetBrains Mono", ui-monospace, monospace;

  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-md: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.375rem;
  --text-2xl: 1.75rem;
  --text-3xl: clamp(2rem, 5vw, 3rem);
}
```

Dekorative Schrift wird nur für kurze Überschriften eingesetzt. Regeltexte, Formulare, Tabellen und Nachrichten verwenden immer eine gut lesbare Schrift.

### 4.6 Bewegung

```css
:root {
  --duration-fast: 120ms;
  --duration-normal: 200ms;
  --duration-slow: 360ms;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
  --ease-emphasized: cubic-bezier(0.2, 0.8, 0.2, 1);
}
```

Bei `prefers-reduced-motion: reduce` beziehungsweise Theme-Einstellung `motion = reduced/none`:

- keine Partikel,
- kein Parallax,
- kein Screen-Shake,
- kein automatisches Scrollen,
- Übergänge höchstens als sehr kurzes Überblenden.

---

## 5. Beispielbibliothek: Oberflächenstile (nicht normativ)

| ID | Name | Charakteristik |
|---|---|---|
| `parchment` | Klassisches Pergament | Buchseiten, Tintenlinien, Siegel, Serif-Überschriften |
| `pixel-tavern` | Pixel-Taverne | Harte Kanten, Pixel-Icons, Retro-Schrift für kurze Überschriften |
| `rune-minimal` | Runen-Minimal | Reduziert, feine Konturen, subtile Runen- und Punktmuster |
| `adventurer` | Abenteurer-Komfort | Große Titel, großzügige Karten, Pillen-Buttons, mobil optimiert |
| `arcane-tonal` | Arkane Flächen | Tonale Flächen, magische Akzente, moderne klare Geometrie |
| `crystal-glass` | Kristallglas | Halbtransparenz, Blur, Lichtkanten; automatischer Fallback ohne Blur |
| `dungeon-stone` | Dungeon-Stein | Gemeißelte Rahmen, schwere Karten, Metallakzente |
| `scholar-codex` | Gelehrtenkodex | Regelbuch, Bibliothek, klare Kapitelstruktur und Marginalien |
| `expert-console` | Expertenkonsole | Kompakt, informationsreich, hohe Datendichte |
| `dice-table` | Würfeltisch | Holz, Filz, Leder, physischer Tabletop-Charakter |
| `prophecy` | Prophezeiung | Ornamente, Sternzeichen, elegante fließende Übergänge |
| `accessible-clear` | Barrierefrei Klar | Maximale Lesbarkeit, klare Zustände, reduzierte Dekoration |

Jeder Stil definiert mindestens:

```ts
interface UiStyleTokens {
  bodyFont: string;
  headingFont: string;
  radiusScale: number;
  shadowStrength: number;
  borderWidth: string;
  cardStyle: "flat" | "raised" | "outlined" | "glass";
  buttonStyle: "square" | "rounded" | "pill";
  navigationStyle: "rail" | "sidebar" | "bottom" | "tabs";
  iconSet: string;
  defaultDensity: "comfortable" | "compact";
}
```

---

## 6. Beispielbibliothek: Farbpaletten (nicht normativ)

Die Hexwerte sind Startwerte. Vor Veröffentlichung müssen alle Kombinationen automatisiert auf WCAG-Kontrast geprüft werden.

| ID | Name | Hintergrund | Oberfläche | Text | Primär | Sekundär |
|---|---|---:|---:|---:|---:|---:|
| `dragonfire` | Drachenfeuer | `#17131f` | `#291f31` | `#fff7e6` | `#d55238` | `#e6a84f` |
| `arcane-blue` | Arkanblau | `#0d1630` | `#17284d` | `#f1f6ff` | `#8b7cff` | `#42d9ff` |
| `emerald-grove` | Smaragdhain | `#101b17` | `#1c3026` | `#f1f4df` | `#4f9e68` | `#c49a55` |
| `feywild` | Feywild | `#17132b` | `#282048` | `#fff3ff` | `#d65cd6` | `#54d8cf` |
| `underdark` | Underdark | `#0d0915` | `#1e142b` | `#eee9ff` | `#b64fd1` | `#4eb6d8` |
| `ravenloft` | Ravenloft | `#151416` | `#292528` | `#f3e8dc` | `#9f2639` | `#b9bec8` |
| `celestial` | Celestisch | `#edf4fa` | `#ffffff` | `#18293d` | `#327ab5` | `#c99b31` |
| `infernal` | Infernalisch | `#170e0d` | `#2c1714` | `#ffe9d2` | `#c83a24` | `#d2a23f` |
| `necromancy` | Nekromantie | `#101310` | `#1d251d` | `#edf0df` | `#6aae45` | `#b9b29d` |
| `frost` | Frostweite | `#10202c` | `#1c3545` | `#f2fbff` | `#54a9ca` | `#b9e8ed` |
| `desert-sun` | Wüstensonne | `#2b1d14` | `#4a3120` | `#fff1d1` | `#cc7138` | `#3c83a4` |
| `coast` | Küstenabenteuer | `#0d2636` | `#173e50` | `#eefcff` | `#2fa5b3` | `#bd7542` |
| `dwarven-forge` | Zwergenschmiede | `#181716` | `#302b27` | `#f2e9dd` | `#b56b3b` | `#c49b51` |
| `elven-moon` | Elfenmond | `#11182c` | `#202a46` | `#f2f2ff` | `#8b86c9` | `#69a77a` |
| `royal-court` | Königlicher Hof | `#21142a` | `#392143` | `#fff4dc` | `#8e4fa5` | `#d0a144` |
| `alchemist` | Alchemistenlabor | `#102423` | `#1b3a36` | `#edf9ec` | `#3f9f91` | `#d0903d` |
| `mimic` | Mimic | `#231812` | `#3b261c` | `#fff0d8` | `#a64337` | `#d5a84d` |
| `pastel-adventure` | Pastell-Abenteuer | `#f5eff7` | `#fffafd` | `#352d3b` | `#9b6fa8` | `#579b91` |
| `monochrome` | Monochrom | `#161616` | `#282828` | `#f5f5f5` | `#b8b8b8` | `#ffffff` |
| `contrast-dark` | Hoher Kontrast dunkel | `#000000` | `#111111` | `#ffffff` | `#ffdf00` | `#00e5ff` |
| `contrast-light` | Hoher Kontrast hell | `#ffffff` | `#f1f1f1` | `#111111` | `#8b0000` | `#004c99` |
| `custom` | Eigene Palette | nutzerdefiniert | nutzerdefiniert | automatisch geprüft | nutzerdefiniert | nutzerdefiniert |

---

## 7. Beispielbibliothek: Atmosphären (nicht normativ)

| ID | Atmosphäre |
|---|---|
| `none` | Keine Textur |
| `ink-parchment` | Pergament und Tinte |
| `wood-tavern` | Taverne und Holz |
| `castle-stone` | Burg und Stein |
| `torch-dungeon` | Verlies und Fackelschein |
| `arcane-runes` | Arkane Runen |
| `dragon-hoard` | Drachenhort |
| `fey-particles` | Feywild-Partikel |
| `underdark-glow` | Underdark-Pilzleuchten |
| `gothic-fog` | Gothic-Nebel |
| `astral` | Sternenebene |
| `infernal-embers` | Infernalische Glut |
| `frost-snow` | Eis und Schnee |
| `desert-dust` | Wüste und Staub |
| `ocean-waves` | Ozean und Wellen |
| `jungle-vines` | Dschungel und Ranken |
| `dwarven-forge` | Zwergische Schmiede |
| `magitech` | Zahnräder und Magitech |

Atmosphären bestehen aus lokalen Assets. Externe Netzwerkbilder, CDN-Schriften oder Online-Partikelbibliotheken sind für den Grundbetrieb verboten.


## 7.1 Shader-, Effekt- und Rendering-System

Shader und visuelle Effekte sind eine optionale Unterachse der Atmosphäre. Sie dürfen weder Navigation noch fachliche Bedeutung kontrollieren.

### Effektklassen

- **CSS-basiert:** Farbverlauf, Schatten, Blur, Masken und einfache Übergänge.
- **Canvas/2D:** Partikel, leichte Texturen, Diagramm- oder Hintergrundeffekte.
- **WebGL/GPU:** Verzerrung, Licht, prozedurale Texturen und komplexe Komposition.
- **Native GPU:** plattformspezifische Effekte mit gleichwertigem statischem Fallback.

### Verbindliche Shaderregeln

- Jeder Shader besitzt `off`, `reduced` und einen statischen Fallback.
- Kein Effekt darf Textkontrast, Fokus, Touchziele oder Lesereihenfolge verändern.
- Fachliche Zustände bleiben ohne Shader vollständig verständlich.
- Shader erhalten keine geheimen oder unvalidierten Nutzerdaten als Quelltext.
- Benutzerdefinierter Shadercode wird standardmäßig nicht ausgeführt.
- Ressourcen-, Speicher- und Framebudgets werden pro Leistungsklasse begrenzt.
- Bei Kontextverlust, Überhitzung, Akkusparen oder `prefers-reduced-motion` wird automatisch reduziert.

### Leistungsstufen

```text
Tier 0: keine Effekte, statische Flächen
Tier 1: CSS-Effekte und statische Texturen
Tier 2: leichte Canvas-/Partikeleffekte
Tier 3: begrenzte GPU-Shader
Tier 4: erweiterte Effekte auf ausdrücklich geeigneten Geräten
```

Die Engine wählt standardmäßig konservativ. Nutzer können Effekte reduzieren; eine automatische Hochstufung erfolgt nur nach erfolgreicher Fähigkeits- und Leistungserkennung.

### Beispiel für ein deklaratives Effektmanifest

```json
{
  "id": "example-ambient-glow",
  "axis": "effect",
  "schemaVersion": 1,
  "tier": 2,
  "requires": ["canvas2d"],
  "respectsReducedMotion": true,
  "fallback": "static-gradient",
  "budgets": {
    "maxFps": 30,
    "maxParticles": 80,
    "maxMemoryMb": 24
  }
}
```

Das Manifest ist illustrativ. Konkrete Grenzwerte müssen zum Produkt, Gerät und Einsatzkontext passen.

### Testanforderungen

- Start mit deaktivierter GPU,
- Kontextverlust und Wiederherstellung,
- reduzierte Bewegung,
- hoher Kontrast,
- niedriger Akkustand beziehungsweise Energiesparmodus,
- langsame und schnelle Geräte,
- Hintergrund/Foreground-Wechsel,
- lange Laufzeit ohne Speicherwachstum.

---

## 8. Beispielbibliothek: kuratierte Presets (nicht normativ)

Presets sind fertige Kombinationen für Nutzer, die nichts selbst konfigurieren möchten.

| Preset | Stil | Palette | Atmosphäre |
|---|---|---|---|
| Vergessene Reiche | `adventurer` | `dragonfire` | `ink-parchment` |
| Klassischer Dungeon | `dungeon-stone` | `monochrome` | `torch-dungeon` |
| Taverne bei Nacht | `dice-table` | `dragonfire` | `wood-tavern` |
| Drachenhort | `dungeon-stone` | `dragonfire` | `dragon-hoard` |
| Fluch des Vampirs | `scholar-codex` | `ravenloft` | `gothic-fog` |
| Tiefes Underdark | `rune-minimal` | `underdark` | `underdark-glow` |
| Reise ins Feywild | `crystal-glass` | `feywild` | `fey-particles` |
| Himmlische Zitadelle | `prophecy` | `celestial` | `astral` |
| Neun Höllen | `dungeon-stone` | `infernal` | `infernal-embers` |
| Frostige Wildnis | `adventurer` | `frost` | `frost-snow` |
| Wüstenkönigreich | `parchment` | `desert-sun` | `desert-dust` |
| Piratenküste | `dice-table` | `coast` | `ocean-waves` |
| Zwergenfestung | `dungeon-stone` | `dwarven-forge` | `dwarven-forge` |
| Elfenhain | `prophecy` | `elven-moon` | `jungle-vines` |
| Arkane Akademie | `arcane-tonal` | `arcane-blue` | `arcane-runes` |
| Nekromantengruft | `scholar-codex` | `necromancy` | `gothic-fog` |
| Königlicher Hof | `scholar-codex` | `royal-court` | `ink-parchment` |
| Alchemistenwerkstatt | `rune-minimal` | `alchemist` | `magitech` |
| Magitech Noir | `arcane-tonal` | `monochrome` | `magitech` |
| Minimaler Spielabend | `accessible-clear` | `contrast-dark` | `none` |

---

## 9. Komponentenregeln

### 9.1 Buttons

Varianten:

- `primary`: wichtigste Aktion, höchstens einmal pro klarer Aktionsgruppe
- `secondary`: alternative Aktion
- `ghost`: Navigation und schwache Aktionen
- `danger`: destructive Aktion
- `icon`: benötigt immer `aria-label` und Tooltip

Mindestgröße für Touch: **44 × 44 CSS-Pixel**.

Zustände:

- normal
- hover
- focus-visible
- active
- disabled
- loading

Loading darf die Buttonbreite nicht verändern.

### 9.2 Karten

Eine Karte enthält optional:

- Header mit Titel und Status
- Inhalt
- Footer mit Aktionen

Verschachtelte Karten nur verwenden, wenn eine echte Hierarchie besteht. Nicht jede Textgruppe bekommt einen sichtbaren Rahmen.

### 9.3 Formulare

- Label immer sichtbar; Placeholder ist kein Ersatz.
- Fehler direkt am Feld und zusätzlich zusammenfassbar.
- Pflichtfelder semantisch markieren.
- Speichern mit sichtbarem Erfolg oder Fehler.
- Keine Browser-`prompt()`-/`confirm()`-Dialoge.
- Gefährliche Aktionen über App-Dialog bestätigen.
- Zahlenfelder erhalten sinnvolle Grenzen.

### 9.4 Navigation

Desktop:

- Seitenleiste oder Rail
- Kopfzeile für Kontext, Verbindung und Nutzer

Mobil:

- Bottom-Navigation für Hauptbereiche
- kontextuelle Aktionen als erreichbare Buttons
- keine reine Hover-Navigation

Aktiver Bereich ist durch Farbe **und** Form/Hintergrund gekennzeichnet.

### 9.5 Dialoge und Sheets

- Desktop: zentrierter Dialog
- Mobil: Bottom Sheet oder Vollbilddialog
- Fokus bleibt im Dialog
- Escape schließt nur ungefährliche Dialoge
- destruktive Aktionen benötigen klare Beschriftung

### 9.6 Status-Badges

Status nie nur über Farbe ausdrücken. Immer Text oder Icon ergänzen.

Beispiele:

- Aktiv
- Geplant
- Beendet
- Ungelesen
- Privat
- DM
- Offline
- Konflikt

### 9.7 Private Inhalte

Sensible Nachrichten und vertrauliche Ergebnisse verwenden `--color-secret`, Schloss-/Flüster-Icon und sichtbaren Text „Privat“. In öffentlichen Präsentationsansichten dürfen diese Komponenten nicht gerendert werden.

### 9.8 Echtzeitdaten und aktive Prozessschritte

- aktiver Prozessschritt: Akzentrahmen plus Badge
- Messwert: Zahl und optional Balken, niemals nur Farbe
- Zustände: Badge mit Name und optional Restdauer
- automatisch/manuell erzeugte Werte klar kennzeichnen
- Rohwert, Modifikator und Gesamtwert getrennt darstellbar
- Animationen optional; Ergebnis steht immer als Text bereit

---

## 10. Responsive Breakpoints

Nicht nach Gerätenamen, sondern nach verfügbarem Platz gestalten.

```css
/* klein */
@media (max-width: 599px) { }

/* mittel */
@media (min-width: 600px) and (max-width: 899px) { }

/* groß */
@media (min-width: 900px) { }

/* sehr groß / Expertenarbeitsfläche */
@media (min-width: 1280px) { }
```

Regeln:

- Einspaltig unter 600 px.
- Zwei Spalten nur, wenn jede Spalte mindestens ca. 280 px behält.
- Tabellen auf Mobil in Karten oder horizontal scrollbare Regionen umwandeln.
- Modale Arbeitsflächen auf Mobil als Vollbild.
- Safe Areas auf Android/iOS berücksichtigen.

---

## 11. Barrierefreiheit

Verbindliche Mindestanforderungen:

- WCAG 2.2 AA für Text und Bedienelemente
- Fokusindikator mit mindestens 3:1 Kontrast
- vollständige Tastaturbedienung
- Screenreader-Namen für Icon-Buttons
- mindestens 44 × 44 px Touchfläche
- Zoom und größere Systemschrift unterstützen
- Inhalt nie nur über Farbe erklären
- hoher Kontrast hell und dunkel
- reduzierte Bewegung
- Texturen und Partikel abschaltbar
- Dekorschrift nie für längere Texte
- Fehler verständlich und feldbezogen
- Reihenfolge im DOM entspricht visueller Reihenfolge

Eigene Farben werden vor dem Speichern automatisch geprüft. Unterschreitet eine Kombination die Kontrastanforderung, zeigt der Editor einen Fehler und bietet eine korrigierte Farbe an.

---

## 12. Icons

Geplante Icon-Sets:

- `pixel`
- `outline-thin`
- `outline-bold`
- `filled`
- `runes`
- `parchment-sketch`
- `system`

Regeln:

- Icons sind SVG oder lokal gebündelte Komponenten.
- Icons dürfen keine einzige Informationsquelle sein.
- Gleiche Aktion verwendet appübergreifend dasselbe Symbol.
- Mindestgröße 20 px, Touchfläche trotzdem 44 px.
- Keine Emoji als dauerhaftes Kern-Icon; Emoji nur als dekorative Ergänzung.

---

## 13. Theme-Dateiformat

Themes enthalten keine ausführbaren Skripte.

```json
{
  "schema": "modular-theme",
  "version": 1,
  "id": "custom-night-grove",
  "name": "Nacht im Hain",
  "author": "Name",
  "license": "CC0-1.0",
  "selection": {
    "uiStyle": "rune-minimal",
    "colorPalette": "emerald-grove",
    "atmosphere": "jungle-vines",
    "iconSet": "outline-thin",
    "density": "comfortable",
    "motion": "subtle",
    "fontScale": 1
  },
  "overrides": {
    "colorAccent": "#6dc58a"
  }
}
```

Nicht erlaubt:

- JavaScript
- HTML
- externe URLs als automatisch geladene Assets
- absolute Dateipfade
- CSS mit `url(http...)`
- unbekannte Dateitypen

Import prüft Schema, Version, Wertebereiche, Kontraste und Asset-Lizenzen.

---

## 14. Empfohlene Projektstruktur

```text
packages/
├── theme/
│   ├── tokens/
│   │   ├── colors.css
│   │   ├── spacing.css
│   │   ├── typography.css
│   │   └── motion.css
│   ├── styles/
│   ├── palettes/
│   ├── atmospheres/
│   ├── presets/
│   ├── schema.ts
│   ├── validation.ts
│   └── ThemeProvider.tsx
└── ui/
    ├── Button/
    ├── Card/
    ├── Dialog/
    ├── Field/
    ├── Navigation/
    ├── Badge/
    ├── EmptyState/
    ├── ErrorState/
    └── LoadingState/
```

Eine Anwendung darf diese Struktur direkt übernehmen oder das Theme-Paket als versionierte interne beziehungsweise öffentliche Abhängigkeit beziehen. Zur Laufzeit darf keine unnötige Kopplung an eine andere Anwendung entstehen.

---

## 15. ThemeProvider-Verhalten

Der Provider:

1. liest lokale Einstellungen sofort,
2. setzt die `data-*`-Attribute vor dem ersten sichtbaren Rendern,
3. lädt danach das Nutzerprofil,
4. migriert alte Theme-Versionen,
5. respektiert Systemkontrast und reduzierte Bewegung,
6. aktualisiert `theme-color` für PWA/Android,
7. verhindert einen hellen oder ungestylten Startblitz.

Beispiel:

```tsx
function applyTheme(theme: ThemeSelection) {
  const root = document.documentElement;
  root.dataset.uiStyle = theme.uiStyle;
  root.dataset.colorPalette = theme.colorPalette;
  root.dataset.atmosphere = theme.atmosphere;
  root.dataset.iconSet = theme.iconSet;
  root.dataset.density = theme.density;
  root.dataset.motion = theme.motion;
  root.style.setProperty("--user-font-scale", String(theme.fontScale));
}
```

---

## 16. Theme-Geltungsbereiche

Priorität von niedrig nach hoch:

1. App-Standard
2. Projekt- oder Organisationsempfehlung
3. persönliche Nutzerwahl
4. Barrierefreiheit des Nutzers

Zusätzliche getrennte Bereiche:

- Administrations- oder Expertenbereich
- Nutzerbereich
- öffentliche Präsentationsansicht
- Android-Widget, falls vorhanden

Eine Organisation darf ein Präsentationstheme festlegen, aber niemals persönliche Kontrast-, Schriftgrößen- oder Bewegungsprofile überschreiben.

---

## 17. Übertragung auf die andere App

### Phase A – Inventur

- Alle direkten Hexfarben suchen.
- Alle Abstände, Radien, Schatten und Schriftgrößen erfassen.
- Wiederkehrende Buttons, Karten, Dialoge, Felder und Navigation identifizieren.
- Inline-Styles und doppelte CSS-Regeln markieren.

### Phase B – Tokens

- Gemeinsame Token-Dateien anlegen.
- Bestehende Werte zunächst 1:1 in Tokens überführen.
- Komponenten auf semantische Tokens umstellen.
- Keine optische Neugestaltung während dieser technischen Migration erzwingen.

### Phase C – Kernkomponenten

In dieser Reihenfolge:

1. Button
2. Eingabefeld
3. Auswahlfeld
4. Card
5. Badge
6. Dialog/Bottom Sheet
7. Navigation
8. Lade-, Fehler- und Leerzustand

### Phase D – Theme-Engine

- `data-ui-style`
- `data-color-palette`
- `data-atmosphere`
- Persistenz
- Live-Vorschau
- Systempräferenzen

### Phase E – Presets

Zunächst wenige produktspezifische Basispresets umsetzen. Die folgenden Kombinationen sind nur Beispiele:

1. Abenteurer-Komfort + Drachenfeuer
2. Arkane Flächen + Arkanblau
3. Barrierefrei Klar + Hoher Kontrast dunkel
4. Barrierefrei Klar + Hoher Kontrast hell

Danach weitere Stile und Paletten schrittweise ergänzen.

### Phase F – Tests

- Screenshot-/Visual-Regression-Tests
- Kontrasttests
- Tastaturtest
- Touchgrößen
- reduzierte Bewegung
- Smartphone, Tablet und Desktop
- Deutsch und Englisch
- sehr lange Namen und Texte
- Offline-Start

---

## 18. Abnahmekriterien

Die Übertragung ist abgeschlossen, wenn:

- keine Kernkomponente direkte Produktfarben enthält,
- alle Bildschirme mit den vier Basispresets funktionieren,
- Themewechsel ohne Reload möglich ist,
- die Auswahl nach Neustart erhalten bleibt,
- Android und Web dieselben Tokens verwenden,
- Deutsch und Englisch keine Layouts zerstören,
- hoher Kontrast vollständig bedienbar ist,
- reduzierte Bewegung respektiert wird,
- alle Touchziele mindestens 44 × 44 px groß sind,
- Fokus und Screenreader-Beschriftungen vorhanden sind,
- private Inhalte klar markiert und nie auf öffentlichen Displays sichtbar sind,
- keine externen Theme-Ressourcen für den Offlinebetrieb erforderlich sind.

---

## 19. Empfohlener Mindeststandard für eine Implementierung

Eine neue Implementierung sollte mindestens unterstützen:

- einen normalen und einen barrierefrei reduzierten UI-Stil
- eine helle, eine dunkle sowie zwei Hochkontrastpaletten
- Atmosphäre `none`
- Deutsch und Englisch
- responsive Ein- und Zweispaltenlayouts
- Tastatur und Touch
- reduzierte Bewegung
- zentrale Fehler- und Ladezustände

Erst danach gelten weitere dekorative Themes als sinnvoll.

---

## 20. Zusammenfassung für die übernehmende KI oder das Entwicklerteam

> Implementiere keinen einzelnen starren Look. Baue eine Engine aus unabhängigen Designachsen, semantischen Tokens, validierten Kombinationen und sicheren Fallbacks. Stelle zuerst Kernkomponenten, Zustandsverständlichkeit und Barrierefreiheit fertig. Ergänze dekorative Stile und Effekte anschließend schrittweise. Persönliche Barrierefreiheit besitzt immer Vorrang vor Projekt-, Organisations- oder Präsentationsthemes.

---

# Anhang A: Formale Kombinations-Engine

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

## Schutz- und Veröffentlichungsstrategie

Die abstrakte Methode allein ist regelmäßig schwer exklusiv zu schützen. Schutzfähiger beziehungsweise praktisch kontrollierbarer sind:

- konkrete technische Implementierung und Quellcode,
- genaue Spezifikation und Dokumentation,
- Name und Logo der Methode,
- konkrete erzeugte Designs,
- möglicherweise eine nachweisbar neue technische Engine mit weiterem technischem Effekt.

Schutz- und Lizenzfragen werden getrennt von der technischen Spezifikation bewertet.

# Anhang B: Checkliste für produktunabhängige Übernahme

- [ ] Beispiele wurden nicht versehentlich als feste Produktanforderungen behandelt.
- [ ] Ein eigener Null-Konfigurationsstandard ist definiert.
- [ ] Alle Komponenten verwenden semantische Tokens.
- [ ] Achsen besitzen IDs, Versionen, Fähigkeiten, Anforderungen und Fallbacks.
- [ ] Accessibility-Overrides haben dokumentierten Vorrang.
- [ ] Kontrast, Fokus, Bewegung und Touchgrößen werden geprüft.
- [ ] Atmosphären und Shader lassen sich vollständig abschalten.
- [ ] Leistungsklassen und Ressourcenbudgets sind definiert.
- [ ] Importierte Themes enthalten keinen ausführbaren Fremdcode.
- [ ] Vorschau, Commit, Reset, Export und Migration sind getrennt.
- [ ] Kombinationen sind deterministisch und reproduzierbar.
- [ ] Herkunft und Lizenz jeder Achse bleiben erhalten.
- [ ] Visuelle Regressionen und Fallbackpfade sind getestet.

# Schlussformel

Dieses System beschreibt **wie** visuelle Entscheidungen sicher kombiniert werden, nicht **welchen** Look ein Produkt besitzen muss. Konkrete Farben, Namen, Stile, Shader und Presets sind austauschbare Beispiele. Die dauerhaften Grundlagen sind Semantik, unabhängige Achsen, deterministische Regeln, Accessibility, Reversibilität, Sicherheit und überprüfbare Fallbacks.
