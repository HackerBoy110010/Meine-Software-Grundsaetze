# Grundsatz 11: Schutzrechte und Lizenzierung der Kombinationstechnik

> **Hinweis:** Allgemeine Orientierung für Deutschland und die EU, keine Rechtsberatung. Vor Offenbarung, Anmeldung oder Lizenzvertrag sollte ein Patent- beziehungsweise Fachanwalt die konkrete Technik und den Stand der Technik prüfen.

## Kurzbewertung

Die Kombinationstechnik besteht aus mehreren rechtlich unterschiedlich behandelbaren Ebenen:

| Ebene | Typischer Schutzansatz |
| --- | --- |
| abstrakte Idee unabhängiger Designachsen | kaum exklusiv schützbar |
| Regeln und Spezifikation als konkreter Text | Urheberrecht an der Darstellung, nicht an der Idee |
| Quellcode der Engine | Urheberrecht und Softwarelizenz |
| nicht öffentliche Regelbasis/Optimierung | Geschäftsgeheimnis bei echten Geheimhaltungsmaßnahmen |
| Name und Logo der Methode | Marke |
| konkret erzeugte Oberflächen | Designschutz und eventuell Urheberrecht |
| neue technische Engine mit technischem Effekt | möglicherweise Patent; Einzelfallprüfung |

## 1. Kann man die Methode patentieren?

### Nicht als bloße Designidee

Das Prinzip „UI-Stil, Palette und Atmosphäre getrennt auswählen und kombinieren“ ist zunächst ein abstraktes Organisations- und Gestaltungsprinzip. Patente schützen technische Erfindungen; ästhetische Formschöpfungen gehören grundsätzlich zum Designschutz. Eine reine Taxonomie, Gestaltungsregel oder visuelle Empfehlung ist daher normalerweise kein Patentgegenstand.

### Möglicherweise als technische Implementierung

Eine Prüfung kann sinnvoll sein, wenn die Engine mehr leistet als Designauswahl, zum Beispiel:

- automatische Konfliktauflösung über formalisierte Constraints,
- deterministische Kompilierung heterogener Themequellen,
- technische Laufzeitoptimierung für unterschiedliche Renderinghardware,
- messbare Reduktion von Speicher-, Energie- oder Renderingkosten,
- sichere Isolation nicht vertrauenswürdiger Themedaten,
- neuartige automatische Accessibility-Reparatur mit technischer Systemwirkung.

Auch dann müssen Neuheit, erfinderische Tätigkeit und technischer Charakter vorliegen. Eine lediglich automatisierte mentale oder gestalterische Regel bleibt voraussichtlich zu schwach.

### Wichtig vor Veröffentlichung

Eine Patentanmeldung ist besonders neuheitssensibel. Quellcode, öffentliche Spezifikation, Vortrag, Video oder Repository können eine eigene Offenbarung darstellen. Anders als beim Designschutz sollte man sich nicht auf eine allgemeine zwölfmonatige Schonfrist verlassen. Vor weiterer detaillierter Veröffentlichung einer möglichen technischen Erfindung ist anwaltliche Prüfung sinnvoll.

## 2. Designschutz

Ein eingetragenes Design schützt die sichtbare Erscheinungsform eines konkreten Produkts, nicht die Engine, die sie erzeugt. Schutzfähig können einzelne erzeugte Referenzoberflächen, Komponenten oder Übergangszustände sein, wenn sie neu sind und Eigenart besitzen.

Damit lassen sich konkrete Ergebnisse schützen, aber nicht jede andere Oberfläche, die dieselbe Achsenmethode verwendet.

- Deutschland: Eintragung beim DPMA, maximal 25 Jahre.
- EU: eingetragenes EU-Design, maximal 25 Jahre.
- Nicht eingetragenes EU-Design: drei Jahre ab geeigneter Offenbarung, primär Kopierschutz.
- Eigene Designoffenbarung: grundsätzlich zwölfmonatige Neuheitsschonfrist für spätere Designanmeldung.

Allgemeine Ideen, Konzepte und Gestaltungsprinzipien sind laut DPMA nicht als Design schützbar. Die eingereichten Darstellungen bestimmen den konkreten Schutzumfang.

## 3. Urheberrecht

Automatischer urheberrechtlicher Schutz kann bestehen an:

- Quellcode,
- ausführlicher Spezifikation,
- Diagrammen und Texten,
- konkreten Icons, Grafiken und Oberflächen,
- individuell gestalteten Regelwerken in ihrer konkreten Ausdrucksform.

Nicht geschützt ist dadurch die abstrakte Funktionsidee. Eine unabhängige Neuimplementierung derselben Methode kann urheberrechtlich zulässig sein, wenn weder Code noch geschützte Ausdrucksform übernommen werden.

Nutzungsrechte können nach § 31 UrhG einfach oder ausschließlich sowie räumlich, zeitlich und inhaltlich beschränkt eingeräumt werden.

## 4. Marke für den Methodennamen

Ein eigenständiger Name kann als Wort- oder Wort-/Bildmarke geschützt werden. Das schützt die Herkunftskennzeichnung, nicht die Methode selbst.

Sinnvoll ist ein Name, der:

- nicht bloß „Theme Combination Engine“ beschreibt,
- recherchierbar und unterscheidungskräftig ist,
- nicht an fremde Marken anlehnt,
- konsistent für Spezifikation, Engine und Zertifizierung verwendet wird.

Eine abstrakte Farbmarke ist möglich, aber regelmäßig schwer durchzusetzen, weil Farben meist dekorativ und nicht als Herkunftshinweis verstanden werden.

## 5. Geschäftsgeheimnis

Nicht veröffentlichte Gewichtungen, Optimierungsverfahren, Kompatibilitätsdaten oder Trainings-/Testdaten können als Geschäftsgeheimnis behandelt werden, wenn angemessene Geheimhaltungsmaßnahmen bestehen.

Das kollidiert mit vollständiger Open-Source-Veröffentlichung. Eine mögliche Trennung:

- öffentliche Spezifikation und Basismotor,
- private Optimierungsprofile oder Zertifizierungsregeln,
- klar geregelter Zugriff und Vertraulichkeit.

Sobald Informationen öffentlich sind, kann diese Schutzstrategie für diese Informationen nicht mehr greifen.

## 6. Lizenzieren ohne Patent

Eine Methode kann vertraglich lizenziert werden, auch wenn kein Patent besteht. Die Lizenz bindet jedoch grundsätzlich nur Vertragspartner. Ohne Patent kann eine unabhängige Implementierung nicht allein deshalb verboten werden, weil sie dieselbe abstrakte Methode nutzt.

Lizenzierbar sind insbesondere:

- Spezifikationsdokumente,
- Referenzimplementierung,
- Test-Suite und Zertifizierungsmarke,
- konkrete Achsenbibliotheken,
- Designassets,
- Support, Updates und Kompatibilitätsdaten.

## 7. Empfohlene modulare Lizenzarchitektur

### Spezifikation

Mögliche Optionen:

- **offener Standard:** CC BY 4.0,
- **reziproke Dokumentation:** CC BY-SA 4.0,
- **kontrollierte Nutzung:** proprietäre Spezifikationslizenz,
- **Open Specification Promise:** Implementierung erlaubt, Name/Zertifizierung kontrolliert.

### Referenzimplementierung

- AGPL-3.0-or-later für starke Netzwerk-Copyleft-Wirkung,
- Apache-2.0 für breite industrielle Nutzung mit ausdrücklicher Patentklausel,
- Dual Licensing für Open Source plus kommerzielle Ausnahmen.

Die konkrete Wahl hängt davon ab, ob Verbreitung, Offenheit oder Lizenzumsatz priorisiert wird.

### Name und Zertifizierung

Eine separate Markenrichtlinie kann erlauben:

- wahrheitsgemäße Kompatibilitätsangaben,
- Community-Forks mit anderem Namen,
- Nutzung eines Zertifizierungslogos nur nach bestandenem Testpaket.

### Achsenpakete und Assets

Jedes Paket trägt eigene Herkunfts- und Lizenzmetadaten. Engine-Lizenz und Asset-Lizenz sind getrennt.

## 8. Gab es die Methode schon?

Einzelne Bausteine sind bekannt:

- Design Tokens,
- Theme Engines,
- Farbpalettenwechsel,
- Material-/Skin-Systeme,
- CSS Custom Properties,
- Accessibility-Modi,
- Constraint-Systeme und regelbasierte Konfiguration.

Die allgemeine Aussage „mehrere Themeachsen kombinieren“ dürfte deshalb breiten vorbekannten Stand haben. Potenziell neu kann die genaue technische Kombination sein: Datenmodell, Prioritätsordnung, Constraintauflösung, automatische Reparatur, Provenienz, Determinismus und sichere Runtime-Kompilierung.

Vor einer Patententscheidung ist eine Stand-der-Technik-Recherche erforderlich, unter anderem in:

- Espacenet,
- DEPATISnet,
- Google Patents ergänzend,
- wissenschaftlicher Literatur,
- GitHub und Paketregistern,
- Dokumentation bestehender Designsysteme und Game-Theme-Engines.

Für konkrete visuelle Ergebnisse zusätzlich:

- DesignView,
- DPMAregister,
- WIPO Global Design Database,
- Produkt- und App-Marktrecherche.

## 9. Empfohlene Strategie

### Wenn Offenheit das Hauptziel ist

1. Methode präzise versionieren.
2. defensive Veröffentlichung mit Datum und Hash.
3. Spezifikation offen lizenzieren.
4. Referenzengine unter passender Open-Source-Lizenz veröffentlichen.
5. Namen und Zertifizierungslogo als Marke kontrollieren.
6. konkrete hochwertige Designs separat schützen oder lizenzieren.

### Wenn Exklusivität das Hauptziel ist

1. vor weiterer technischer Offenbarung stoppen,
2. Erfinder und Beiträge dokumentieren,
3. professionelle Patent- und Prior-Art-Prüfung,
4. mögliche Anmeldung vor Veröffentlichung,
5. Kernregeln bis dahin vertraulich behandeln,
6. konkrete Referenzdesigns zusätzlich anmelden.

### Hybrides Modell

- offene Basisspezifikation,
- offene Referenzengine,
- geschützter Name und Konformitätszeichen,
- kommerzielle Achsenbibliotheken,
- geschützte konkrete Designs,
- optionale private Optimierungs-/Zertifizierungsdienste.

## 10. Sofortige Dokumentationsmaßnahmen

- Erstellungsdatum und Autoren festhalten.
- Git-Historie und signierte Releases aufbewahren.
- Achsenmodell und Engine getrennt versionieren.
- menschliche Beiträge und KI-Unterstützung dokumentieren.
- Abhängigkeiten und Vorbilder mit Herkunft notieren.
- vor Patentprüfung keine detaillierten noch geheimen Algorithmen veröffentlichen.
- keine Exklusivität an allgemeinen Farben, Stilen oder Standard-UI-Mustern behaupten.

## Offizielle Quellen

- DPMA: Designschutz – https://www.dpma.de/designs/schutz/index.html
- DPMA: Allgemeine Ideen und Gestaltungsprinzipien – https://www.dpma.de/designs/pruefung_eintragung/
- DPMA: Schutzrechte im Überblick – https://www.dpma.de/service/schutzrechte_kurz_erklaert/portrait/index.html
- DPMA: Farbmarken – https://www.dpma.de/marken/anmeldung/erforderliche_angaben/markenformenundderendarstellung/index.html
- EUIPO: Design-Grundfragen – https://www.euipo.europa.eu/en/help-centre/design/faq-basic-questions
- EUIPO: Nicht eingetragenes EU-Design – https://www.euipo.europa.eu/en/help-centre/design/faq-unregistered-community-designs
- EUIPO: DesignView – https://www.euipo.europa.eu/en/designs/before-applying/availability
- UrhG §§ 2 und 31 – https://www.gesetze-im-internet.de/urhg/BJNR012730965.html
