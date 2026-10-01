# Beispiel — Provider bis Wiedergabe

> Vereinfachtes Architekturbeispiel ohne produktive Providerdaten.

```text
Xtream / M3U
    ↓
Provider-Adapter
    ↓
normalisierte Kanäle / Inhalte
    ↓
Anwendungszustand
    ↓
Nutzerauswahl
    ↓
Player-Service
    ↓
MPV oder ExoPlayer
```

Die UI muss dadurch weder das ursprüngliche Providerformat noch die konkrete Player-Implementierung kennen. Neue Provider oder Player können über ihre jeweilige Systemgrenze ergänzt werden, ohne den gesamten Datenfluss neu zu entwerfen.
