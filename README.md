# Aurora IPTV — Showcase

> Architektur-Showcase einer plattformübergreifenden IPTV-Anwendung mit mehreren Datenquellen, Player-Backends und gerätespezifischen Integrationen.

## Projektidee

Aurora IPTV verfolgt das Ziel, unterschiedliche IPTV-Quellen und Zielplattformen hinter einer gemeinsamen Anwendungsschicht zusammenzuführen. Die eigentliche Herausforderung liegt nicht nur in der Benutzeroberfläche, sondern in der **Integration heterogener Datenquellen, Player-Technologien, Plattformen und Persistenzmechanismen**.

Dieses Repository dokumentiert die Architektur des Projekts. Es enthält keine Zugangsdaten, privaten Playlists oder produktiven Nutzerdaten.

## Systemkontext

```text
 Xtream API ─┐
 M3U ────────┼──→ Daten-/Provider-Schicht
 EPG ────────┘             │
                           ▼
                  Domänen-/App-Logik
                    │             │
                    ▼             ▼
              lokale Daten    Player-Abstraktion
              / Settings       │          │
                               ▼          ▼
                              MPV      ExoPlayer
                               │          │
                               └────┬─────┘
                                    ▼
                         Windows / Linux /
                         Android / Fire TV
```

## Technische Schwerpunkte

- **Flutter / Dart** als gemeinsame Cross-Platform-Basis
- Zielplattformen: **Windows, Linux, Android und Fire TV**
- Unterstützung unterschiedlicher IPTV-Quellen wie **Xtream, M3U und EPG**
- Plattformabhängige Wiedergabe über unterschiedliche Player-Technologien
- Lokale Persistenz über geeignete Storage-Mechanismen
- Secure Storage für schützenswerte lokale Informationen
- Build-, Release- und Update-Prozesse als Teil des Gesamtsystems

## Zentrale Architekturidee

Externe IPTV-Quellen liefern Daten in unterschiedlichen Formaten. Diese Unterschiede sollen nicht durch die gesamte Anwendung propagiert werden. Eine Provider-/Normalisierungsschicht übersetzt sie in ein gemeinsames internes Modell.

Ähnlich wird die Wiedergabe nicht direkt an eine einzelne Player-Technologie gekoppelt. Eine Player-Abstraktion erlaubt, plattformspezifische Implementierungen hinter einer gemeinsamen Schnittstelle zu verwenden.

## Datenfluss

```text
Provider / Playlist
        ↓
Parsing & Normalisierung
        ↓
internes Datenmodell
        ├────→ UI / Navigation
        ├────→ lokale Persistenz
        └────→ Player-Abstraktion
                       ↓
             plattformspezifischer Player
```

## Architekturentscheidungen

### Gemeinsames internes Modell
Xtream-, M3U- und EPG-Daten werden an einer definierten Systemgrenze verarbeitet. Dadurch bleibt die restliche Anwendung möglichst unabhängig vom Eingabeformat.

### Player-Abstraktion
Unterschiedliche Betriebssysteme haben unterschiedliche Wiedergabeanforderungen. Statt diese Unterschiede in UI und Geschäftslogik zu verteilen, werden sie hinter einer Player-Schnittstelle gekapselt.

### Trennung von Konfiguration und Secrets
Normale Einstellungen und schützenswerte Informationen haben unterschiedliche Sicherheitsanforderungen und werden entsprechend getrennt behandelt.

### Release-Prozess als Architekturthema
Eine Cross-Platform-Anwendung ist nicht mit dem Quellcode abgeschlossen. Build, Paketierung, Updates und Plattformunterschiede gehören zum Systemdesign.

## Was dieses Projekt demonstriert

Aurora zeigt besonders **Systemintegration und Abstraktion**: mehrere externe Datenquellen, unterschiedliche Laufzeitplattformen und verschiedene technische Implementierungen werden über definierte Schnittstellen in einem konsistenten Gesamtsystem zusammengeführt.

## Inhalt dieses Showcases

- `README.md` — System- und Projektüberblick
- `ARCHITECTURE.md` — Komponenten, Schnittstellen und Designentscheidungen
- `examples/provider-flow.md` — anonymisierter Datenfluss vom Provider bis zum Player

## Datenschutz

Playlists, Accounts, Tokens und produktive Konfigurationen werden nicht veröffentlicht. Der Showcase konzentriert sich auf Architektur und Engineering-Muster.

---

**Portfolio-Schwerpunkt:** Cross-Platform Architecture · Schnittstellen · Datenflüsse · System Integration
