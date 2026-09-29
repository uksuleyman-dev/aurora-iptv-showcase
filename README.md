# Aurora IPTV 📺

> Cross-Platform IPTV-Streaming-Anwendung mit professionellem Release-Management

Eine moderne IPTV-Anwendung für Desktop und Mobile mit Unterstützung für Live-TV, VOD (Video-on-Demand) und umfassenden Benutzerverwaltung.

## 🎯 Features

- **Cross-Platform-Support**: Desktop (Windows, macOS, Linux) und Mobile (iOS, Android via Flutter)
- **Live-TV Streaming**: Unterstützung für HLS, DASH und weitere Streaming-Protokolle
- **VOD-Katalog**: Umfangreiche Verwaltung von On-Demand-Inhalten
- **Benutzerprofile**: Multi-User-Support mit persönlichen Favoriten
- **Session-State-Management**: Nahtlose Wiederaufnahme von Streams
- **Deep Linking**: Direkte Links zu Inhalten
- **Offline-Modus**: Download und lokale Wiedergabe (optional)

## 🛠️ Tech Stack

### Desktop
- **Framework**: Native Desktop (C++/Qt oder Electron)
- **Streaming**: ffmpeg, LibVLC
- **Database**: SQLite

### Mobile (Flutter)
- **Framework**: Flutter (Dart)
- **Video Player**: video_player Plugin
- **State Management**: Provider / Riverpod
- **Storage**: Hive / Sqflite

### Backend
- **API**: REST/GraphQL
- **Authentication**: JWT-basiert
- **Content Delivery**: CDN-optimiert

## 📦 Installation

### Desktop
```bash
git clone https://github.com/uksuleyman-dev/aurora-iptv.git
cd aurora-iptv

# Abhängigkeiten installieren
brew install ffmpeg libvlc  # macOS
# oder apt-get für Linux

# Build
make build
```

### Mobile (Flutter)
```bash
git clone https://github.com/uksuleyman-dev/aurora-iptv-flutter.git
cd aurora-iptv-flutter

flutter pub get
flutter run
```

## 🎬 Streaming Unterstützung

| Format | Desktop | Mobile |
|--------|---------|--------|
| HLS (m3u8) | ✅ | ✅ |
| DASH (mpd) | ✅ | ✅ |
| RTMP | ✅ | ⚠️ |
| HTTP Progressive | ✅ | ✅ |

## 🚀 Build & Release

```bash
# Desktop-Build
make release

# Flutter-Build (APK/IPA)
flutter build apk
flutter build ios
```

## 📊 Architektur

```
auora-iptv/
├── desktop/           # Desktop-Anwendung
├── mobile/            # Flutter Mobile App
├── backend/           # Backend-API
├── docs/              # Dokumentation
└── tests/             # Tests
```

## 🔗 Links

- **Desktop-Repo**: [aurora-iptv](https://github.com/uksuleyman-dev/aurora-iptv)
- **Mobile-Repo**: [aurora-iptv-flutter](https://github.com/uksuleyman-dev/aurora-iptv-flutter)
- **Dokumentation**: [Siehe Hauptprojekt](https://github.com/uksuleyman-dev/aurora-iptv-flutter)

## 📝 Lizenz

Privates Projekt von [uksuleyman-dev](https://github.com/uksuleyman-dev)

---

*Professionelle IPTV-Lösung mit moderner Architektur und umfassender Plattformunterstützung.*