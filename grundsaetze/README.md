# Allgemeine Produkt- und Softwaregrundsätze

Diese Dokumente bilden einen technologie- und produktunabhängigen Entscheidungsrahmen für verständliche, individualisierbare und zuverlässige Software. Sie können für Web-, Mobile-, Desktop-, Embedded- und Multiuser-Produkte verwendet werden.

## Leitsatz

> Einfach und freundlich im Standard, nahezu grenzenlos anpassbar bei Bedarf.

## Rangfolge bei Konflikten

1. Sicherheit und Datenintegrität
2. Barrierefreiheit und persönliche Nutzbarkeit
3. Verständlichkeit im aktuellen Kontext
4. Zuverlässigkeit und Reversibilität
5. Rollengerechter Informationszugang
6. Visuelle Individualisierung und Atmosphäre
7. Technische Eleganz

Visuelle Wirkung darf niemals Lesbarkeit, Bedienbarkeit, Datenschutz oder Datenintegrität verschlechtern.

## Dokumente

1. [Happy UI](01_HAPPY_UI.md)
2. [Einfache Standards und progressive Anpassung](02_SIMPLE_DEFAULTS_PROGRESSIVE_CUSTOMIZATION.md)
3. [Rollen- und kontextgerechte UX](03_ROLE_AND_CONTEXT_UX.md)
4. [Navigation und Arbeitsflächen](04_NAVIGATION_AND_WORKSPACES.md)
5. [Barrierefreiheit](05_ACCESSIBILITY.md)
6. [Reversibilität, Zustand und Wiederherstellung](06_REVERSIBILITY_AND_RECOVERY.md)
7. [Local-first und Datensouveränität](07_LOCAL_FIRST_DATA_SOVEREIGNTY.md)
8. [Visuelles System und Individualisierung](08_VISUAL_SYSTEM_AND_CUSTOMIZATION.md)
9. [Engineering-Qualität und Experimente](09_ENGINEERING_QUALITY.md)
10. [Modulare Design-Kombinationstechnik](10_MODULAR_DESIGN_COMBINATION_METHOD.md)
11. [Schutzrechte und Lizenzierung](11_DESIGN_IP_AND_LICENSING.md)

## Verbindlichkeit

- **MUSS**: Abnahmekriterium; Abweichungen blockieren eine stabile Veröffentlichung.
- **SOLL**: Standard; Abweichungen benötigen eine dokumentierte Begründung.
- **KANN**: optionale Ausbaustufe.
- Experimentelle Funktionen müssen sichtbar als experimentell gekennzeichnet und vom stabilen Hauptablauf getrennt sein.

## Review-Fragen für jede Änderung

- Versteht ein neuer Nutzer, wo er ist und was als Nächstes möglich ist?
- Ist der Standard ohne Konfiguration sinnvoll?
- Werden nur Informationen gezeigt, die die aktuelle Rolle sehen darf?
- Bleibt die Funktion mit Tastatur, Touch, großer Schrift und hohem Kontrast nutzbar?
- Kann die Aktion rückgängig gemacht oder sicher abgefangen werden?
- Bleiben bestehende Daten nach Update, Abbruch und Neustart erhalten?
- Ist der tatsächlich getestete Stand klar vom geplanten Stand getrennt?
