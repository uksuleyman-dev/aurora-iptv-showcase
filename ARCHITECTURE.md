# Architektur — Aurora IPTV

## Architekturziele

- Gemeinsame Anwendung über mehrere Plattformen
- Begrenzung plattformspezifischer Abhängigkeiten
- Einheitliche Verarbeitung heterogener IPTV-Daten
- Austauschbare Player- und Provider-Implementierungen
- Klare Trennung von UI, Domäne, Persistenz und Infrastruktur

## Logische Schichten

### Presentation
Flutter-Oberfläche und Navigation. Sie konsumiert normalisierte Domänenobjekte statt roher Provider-Antworten.

### Provider / Data Sources
Adapter für Xtream, M3U und EPG übernehmen Abruf, Parsing und Übersetzung in interne Strukturen.

### Domain / Application
Enthält den plattformunabhängigen Anwendungszustand und koordiniert Use Cases.

### Persistence
Lokale Speicherung von Einstellungen und Anwendungsdaten. Sensible Werte werden getrennt und geschützt gespeichert.

### Playback
Eine gemeinsame Player-Schnittstelle kapselt plattformspezifische Wiedergabetechnik wie MPV oder ExoPlayer.

### Build & Delivery
Build-, Release- und Update-Mechanismen berücksichtigen die Anforderungen der jeweiligen Zielplattform.

## Schnittstellenprinzip

```text
ExternalSource
     │
     ▼
ProviderAdapter
     │
     ▼
NormalizedModel
     │
     ├──── UI
     ├──── Persistence
     └──── PlaybackService
                │
                ▼
          PlatformPlayer
```

## Fehlergrenzen

Netzwerkfehler, fehlerhafte Playlists oder Provider-Probleme werden möglichst an der Provider-Grenze behandelt. Player-Fehler bleiben in der Playback-Schicht. Dadurch soll ein Fehler in einem Subsystem nicht unnötig in andere Schichten ausstrahlen.

## Trade-offs

Eine gemeinsame Flutter-Codebasis reduziert Duplizierung, beseitigt aber nicht alle Plattformunterschiede. Abstraktionsschichten verursachen zusätzlichen Code, reduzieren dafür Kopplung und erleichtern den Austausch technischer Implementierungen.
