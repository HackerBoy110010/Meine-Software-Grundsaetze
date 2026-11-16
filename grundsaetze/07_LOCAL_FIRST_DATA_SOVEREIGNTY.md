# Grundsatz 7: Local-first und Datensouveränität

## Ziel

Kernfunktionen funktionieren ohne Pflichtkonto bei einem Cloudanbieter. Nutzer kontrollieren Speicherort, Backups, Synchronisation und Freigaben ihrer Daten.

## Verbindliche Regeln

- Lokale Nutzung ist ein vollständiger, getesteter Betriebsmodus und kein degradierter Demozustand.
- Cloudidentität und Cloudspeicher-Autorisierung bleiben getrennte optionale Funktionen.
- Backup, Synchronisation und Live-Mehrbenutzerbetrieb werden technisch und sprachlich unterschieden.
- Externe Berechtigungen folgen dem Least-Privilege-Prinzip.
- Private Imports bleiben privat, solange keine bewusste Freigabe erfolgt.
- Exporte kennzeichnen Herkunft, Umfang und mögliche Weitergaberechte.
- Telemetrie ist optional, transparent und datensparsam.
- Geheimnisse, Sitzungstokens und private Schlüssel werden nie in Dokumentation, Logs oder Supportchats verlangt.

## Synchronisation

- Ein dokumentiertes Autoritätsmodell bestimmt, welcher Zustand bei Konflikten maßgeblich ist.
- Offlineänderungen benötigen Versionierung und Konfliktstrategie.
- Realtime-Ereignisse ersetzen keine persistente Zustandswahrheit.
- Wiederverbindung gleicht Zustand ab, statt nur verpasste Animationen nachzuholen.
- Backups besitzen Formatversion, Integritätsprüfung und nachvollziehbare Wiederherstellung.

## Gerätebetrieb

- Appdaten liegen im privaten Anwendungsspeicher.
- Hintergrund- oder Hostbetrieb ist sichtbar und bewusst steuerbar.
- Netzwerkfreigabe wird absichtlich aktiviert.
- Unsichere Debugtransporte sind klar von Releasebetrieb getrennt.
- Energiespar-, Neustart- und Speicherknappheitsfälle werden berücksichtigt.

## Portabilität

- Nutzer können ihre Daten in dokumentierten Formaten exportieren.
- Anbieterwechsel darf nicht künstlich blockiert werden.
- Löschen eines Cloudbackups löscht nicht ungefragt lokale Daten.
- Importer bewahren Rohdaten oder Herkunft, wenn verlustfreie Konvertierung nicht garantiert ist.

## Abnahmekriterien

- Kernfunktionen verlangen kein Konto eines Drittanbieters.
- Backup und Restore werden auf frischer sowie älterer Datenbank getestet.
- Konflikte werden sichtbar, nicht still per „last write wins“ verborgen.
- Datenexport beschreibt enthaltene sensible Inhalte.
- Nutzer können lokale Daten und Cloudkopien getrennt verwalten.
