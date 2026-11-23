# Meine Software-Grundsätze

Dieses Repository enthält allgemeine, produkt- und technologieunabhängige Grundsätze für verständliche, zugängliche, anpassbare und zuverlässige Software sowie eine ausführliche Referenzspezifikation für ein modulares Designsystem.

> **Leitsatz:** Einfach und freundlich im Standard, nahezu grenzenlos anpassbar bei Bedarf.

## Rangfolge bei Konflikten

1. Sicherheit und Datenintegrität
2. Barrierefreiheit und persönliche Nutzbarkeit
3. Verständlichkeit im aktuellen Kontext
4. Zuverlässigkeit und Reversibilität
5. Rollengerechter Informationszugang
6. Visuelle Individualisierung und Atmosphäre
7. Technische Eleganz

Visuelle Wirkung darf niemals Lesbarkeit, Bedienbarkeit, Datenschutz oder Datenintegrität verschlechtern.

## Grundsätze

Die vollständige Übersicht und die Review-Fragen stehen in [`grundsaetze/README.md`](grundsaetze/README.md).

1. [Happy UI](grundsaetze/01_HAPPY_UI.md)
2. [Einfache Standards und progressive Anpassung](grundsaetze/02_SIMPLE_DEFAULTS_PROGRESSIVE_CUSTOMIZATION.md)
3. [Rollen- und kontextgerechte UX](grundsaetze/03_ROLE_AND_CONTEXT_UX.md)
4. [Navigation und Arbeitsflächen](grundsaetze/04_NAVIGATION_AND_WORKSPACES.md)
5. [Barrierefreiheit](grundsaetze/05_ACCESSIBILITY.md)
6. [Reversibilität, Zustand und Wiederherstellung](grundsaetze/06_REVERSIBILITY_AND_RECOVERY.md)
7. [Local-first und Datensouveränität](grundsaetze/07_LOCAL_FIRST_DATA_SOVEREIGNTY.md)
8. [Visuelles System und Individualisierung](grundsaetze/08_VISUAL_SYSTEM_AND_CUSTOMIZATION.md)
9. [Engineering-Qualität und Experimente](grundsaetze/09_ENGINEERING_QUALITY.md)
10. [Modulare Design-Kombinationstechnik](grundsaetze/10_MODULAR_DESIGN_COMBINATION_METHOD.md)

## Gesamtspezifikation

Die [allgemeine Gesamtspezifikation des modularen adaptiven Designsystems](MODULARES_DESIGNSYSTEM_ALLGEMEINE_GESAMTSPEZIFIKATION.md) beschreibt unabhängige Designachsen, Tokens, Stil- und Palettenbibliotheken, Effekte, Accessibility, Projektintegration, Validierung und Kombinations-Engine. Illustrative Beispiele sind dabei von verbindlichen Regeln abgegrenzt.

## Lizenzstatus

Für die Inhalte dieses Repositorys ist derzeit keine allgemeine Lizenz festgelegt. Die in der Designsystem-Spezifikation erwähnten Lizenzfelder beziehen sich auf die Herkunfts- und Lizenzangaben importierter Themes und Assets; sie legen keine Lizenz für dieses Repository fest.

## Verbindlichkeit

- **MUSS**: Abnahmekriterium; Abweichungen blockieren eine stabile Veröffentlichung.
- **SOLL**: Standard; Abweichungen benötigen eine dokumentierte Begründung.
- **KANN**: optionale Ausbaustufe.
- Experimentelle Funktionen müssen sichtbar als experimentell gekennzeichnet und vom stabilen Hauptablauf getrennt sein.
