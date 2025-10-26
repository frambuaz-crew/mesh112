# 🚨 MESH112 - Emergency Disaster Communication Network

<div align="center">

![MESH112 Logo](https://via.placeholder.com/200x200/e74c3c/ffffff?text=MESH112)

**Offline-First Emergency Communication Platform**  
*When infrastructure fails, we connect.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![React Native](https://img.shields.io/badge/React%20Native-0.74-blue.svg)](https://reactnative.dev/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![TÜBİTAK 2204](https://img.shields.io/badge/TÜBİTAK-2204-red.svg)](https://tubitak.gov.tr/)

[English](#english) | [Türkçe](#turkce)

</div>

---

## 🇹🇷 Türkçe

### 📱 Proje Nedir?

**MESH112**, deprem ve afet durumlarında GSM ve internet altyapısının çökmesi durumunda **internet gerektirmeyen**, Bluetooth ve WiFi Direct üzerinden çalışan, **yapay zeka destekli acil durum iletişim platformudur**.

Türkiye'nin 112 acil yardım hattına referansla adlandırılan proje, akıllı telefonlar arasında **mesh (örgü) ağ yapısı** oluşturarak:
- 📨 Mesajlaşma (WhatsApp benzeri arayüz)
- 📍 GPS konum paylaşımı ve harita
- 🆘 Tek dokunuşla SOS yayını
- 🧠 AI tabanlı mesaj önceliklendirme (kritik/acil/bilgi)
- 🩸 Kan grubu eşleştirme
- 🌐 Çok dilli destek (Türkçe, İngilizce, Arapça, Kürtçe)

özelliklerini sunar.

---

### 🎯 Neden MESH112?

#### Problem
- **2023 Kahramanmaraş Depremi**: 50,000+ kayıp, GSM ağları çöktü
- Türkiye'nin **%92'si** deprem riski altında
- Afet anında **iletişim kopukluğu** = daha fazla can kaybı

#### Çözüm
- ✅ **Merkezi altyapı gerektirmez** → GSM/internet olmadan çalışır
- ✅ **Her telefon bir relay** → 10 cihaz × 50m = 500m+ menzil
- ✅ **On-device AI** → İnternet olmadan akıllı önceliklendirme
- ✅ **Açık kaynak** → Herkes katkıda bulunabilir

---

### 🏗️ Mimari

```
┌─────────────────────────────────────┐
│   UI Layer (React Native)          │
│  Chat | Map | Profile | SOS        │
├─────────────────────────────────────┤
│   Business Logic                    │
│  Msg Manager | AI | Location       │
├─────────────────────────────────────┤
│   Network Layer                     │
│  BLE Mesh | WiFi Direct | Routing  │
├─────────────────────────────────────┤
│   Data Layer                        │
│  SQLite | AsyncStorage             │
└─────────────────────────────────────┘
```

**Veri Akışı**:
1. Kullanıcı mesaj yazar → AI analiz eder (kategori + aciliyet 0.0-1.0)
2. GPS koordinatları otomatik eklenir
3. BLE/WiFi mesh üzerinden tüm ağa yayınlanır
4. Her cihaz mesajı sonraki cihaza iletir (multi-hop)
5. Alıcılar mesajları öncelik sırasına göre görür (🔴 Kritik → 🟡 Düşük)

---

### 💻 Teknoloji Stack

| Kategori | Teknoloji |
|----------|-----------|
| **Framework** | React Native + TypeScript |
| **Mesh Network** | BLE (react-native-ble-plx) + WiFi Direct |
| **AI Model** | TinyLlama 1.1B (4-bit quantized) |
| **AI Runtime** | ONNX Runtime Mobile |
| **Database** | SQLite + AsyncStorage |
| **Maps** | react-native-maps + OpenStreetMap (offline) |
| **Backend** | Node.js + Express (opsiyonel cloud sync) |
| **CI/CD** | GitHub Actions |

---

### 🚀 Hızlı Başlangıç

#### Gereksinimler
- Node.js 18+
- React Native CLI
- Xcode (iOS) / Android Studio (Android)
- Physical devices (BLE, emülatörde çalışmaz!)

#### Kurulum
```bash
# Repository'yi klonla
git clone https://github.com/your-team/mesh112.git
cd mesh112

# Dependencies yükle
npm install

# iOS pods yükle (sadece macOS)
cd ios && pod install && cd ..

# Android'de çalıştır
npx react-native run-android

# iOS'ta çalıştır
npx react-native run-ios
```

#### AI Model İndirme
```bash
# TinyLlama 4-bit ONNX model (~600MB)
npm run download-model
# Model assets/models/ dizinine indirilecek
```

---

### 📅 Proje Durumu

**Mevcut Faz**: Araştırma & Analiz (Hafta 1-3)  
**Hedef**: 18 hafta sonunda MVP (Beta release)

| Sprint | Haftalar | Hedef | Durum |
|--------|----------|-------|-------|
| Sprint 0 | 1-3 | Araştırma & Analiz | 🔄 Devam Ediyor |
| Sprint 1 | 4-6 | Tasarım & Prototip | ⏳ Bekliyor |
| Sprint 2 | 7-9 | BLE Mesh Core | ⏳ Bekliyor |
| Sprint 3 | 10-12 | Advanced Networking | ⏳ Bekliyor |
| Sprint 4 | 13-15 | AI & Geolocation | ⏳ Bekliyor |
| Sprint 5 | 16-17 | Test & Optimizasyon | ⏳ Bekliyor |
| Sprint 6 | 18 | Deployment & Sunum | ⏳ Bekliyor |

Detaylı plan için: [PROJE_PLANI.md](PROJE_PLANI.md)

---

### 👥 Ekip

| Rol | Sorumluluklar |
|-----|---------------|
| **Project Manager** | Sprint planning, backend API, cloud sync |
| **AI/ML Engineer** | On-device AI, ONNX integration |
| **Mobile Developer** | React Native, BLE/WiFi, builds |
| **Network Engineer** | Mesh routing, multi-hop logic |
| **UI/UX Designer** | Figma design, React Native UI |

---

### 🤝 Katkıda Bulunma

Katkılarınızı bekliyoruz! Lütfen [CONTRIBUTING.md](CONTRIBUTING.md) dosyasını okuyun.

**Hemen yapabilecekleriniz**:
- 🐛 Bug report (Issues)
- ✨ Feature request
- 📖 Dokümantasyon iyileştirme
- 🌍 Çeviri (İngilizce, Arapça, Kürtçe)
- 🧪 Test senaryoları

---

### 📄 Lisans

Bu proje [MIT License](LICENSE) altında lisanslanmıştır.

---

### 🏆 Destekleyenler ve İş Birlikleri

- 🎓 [Üniversite Adı] - Akademik Destek
- 🇹🇷 TÜBİTAK 2204 - Proje Fonu (Başvuru Aşamasında)
- 🚨 AFAD - Pilot Proje Görüşmeleri (Planlanıyor)
- ❤️ Kızılay - İş Birliği Görüşmeleri (Planlanıyor)

---

### 📞 İletişim

- **Website**: [mesh112.org](https://mesh112.org) (yakında)
- **Email**: team@mesh112.org
- **GitHub Issues**: [github.com/your-team/mesh112/issues](https://github.com/your-team/mesh112/issues)
- **Discord**: MESH112 Community (yakında)

---

### 📊 Başarı Metrikleri (Hedef)

| Metrik | Hedef |
|--------|-------|
| **Mesh Network Menzil** | 500m+ (10 cihaz) |
| **Message Latency** | <2 saniye (3-hop) |
| **AI Inference** | <1 saniye |
| **Battery Life** | 24+ saat |
| **App Size** | <100MB |
| **Beta Users** | 50+ |

---

## 🇬🇧 English

### 📱 What is MESH112?

**MESH112** is an **offline-first emergency communication platform** using mesh networking and on-device AI, designed for disaster scenarios when GSM/internet infrastructure fails.

Named after Turkey's 112 emergency hotline, the app creates a **decentralized peer-to-peer network** via Bluetooth Low Energy and WiFi Direct, enabling:
- 📨 Messaging (WhatsApp-like interface)
- 📍 GPS location sharing with map
- 🆘 One-tap SOS broadcast
- 🧠 AI-based message prioritization (critical/urgent/info)
- 🩸 Blood type matching
- 🌐 Multi-language support (Turkish/English/Arabic/Kurdish)

---

### 🎯 Why MESH112?

#### Problem
- **2023 Kahramanmaraş Earthquake**: 50,000+ casualties, GSM network collapse
- **92% of Turkey** at earthquake risk
- Communication blackout = increased casualties

#### Solution
- ✅ **No central infrastructure required** → Works without GSM/internet
- ✅ **Every phone is a relay** → 10 devices × 50m = 500m+ range
- ✅ **On-device AI** → Smart prioritization without internet
- ✅ **Open source** → Anyone can contribute

---

### 💻 Tech Stack

| Category | Technology |
|----------|-----------|
| **Framework** | React Native + TypeScript |
| **Mesh Network** | BLE (react-native-ble-plx) + WiFi Direct |
| **AI Model** | TinyLlama 1.1B (4-bit quantized) |
| **AI Runtime** | ONNX Runtime Mobile |
| **Database** | SQLite + AsyncStorage |
| **Maps** | react-native-maps + OpenStreetMap (offline) |
| **Backend** | Node.js + Express (optional cloud sync) |
| **CI/CD** | GitHub Actions |

---

### 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/your-team/mesh112.git
cd mesh112

# Install dependencies
npm install

# Run on Android
npx react-native run-android

# Run on iOS (macOS only)
cd ios && pod install && cd ..
npx react-native run-ios

# Download AI model
npm run download-model
```

---

### 🤝 Contributing

We welcome contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md).

**Quick wins**:
- 🐛 Report bugs
- ✨ Request features
- 📖 Improve documentation
- 🌍 Translate (English, Arabic, Kurdish)
- 🧪 Add test scenarios

---

### � Documentation

```
docs/
├── guides/                          # Usage guides
│   ├── WORKFLOW_GUIDE.md           # Git workflow & PR process
│   ├── DISCORD_SETUP.md            # Team communication setup
│   └── TEAM_ONBOARDING.md          # New member quick start
│
├── project/                         # Project documentation
│   ├── PROJE_PLANI.md              # 18-week development plan (Turkish)
│   ├── MESH112_DETAYLI_ACIKLAMA.md # Detailed project description (Turkish)
│   └── SETUP_CHECKLIST.md          # PM infrastructure checklist
│
└── troubleshooting/                 # Problem solving
    └── DISCORD_WEBHOOK_FIX.md      # Discord webhook integration fixes
```

**Start here**:
- 👨‍💼 **Project Manager**: [docs/project/SETUP_CHECKLIST.md](docs/project/SETUP_CHECKLIST.md)
- 👨‍💻 **Developers**: [docs/guides/WORKFLOW_GUIDE.md](docs/guides/WORKFLOW_GUIDE.md)
- 🆕 **New Team Members**: [docs/guides/TEAM_ONBOARDING.md](docs/guides/TEAM_ONBOARDING.md)
- 📋 **Full Project Plan**: [docs/project/PROJE_PLANI.md](docs/project/PROJE_PLANI.md)

---

### �📄 License

This project is licensed under the [MIT License](LICENSE).

---

### 📞 Contact

- **Website**: [mesh112.org](https://mesh112.org) (coming soon)
- **Email**: team@mesh112.org
- **GitHub Issues**: [github.com/your-team/mesh112/issues](https://github.com/your-team/mesh112/issues)

---

<div align="center">

**MESH112 - Disaster-Resilient Turkey Initiative**

🇹🇷 *Afet anında her telefon bir umut, her bağlantı bir hayat.*  
*In disasters, every phone is hope, every connection is life.*

**#MESH112** | **#AcilDurum** | **#DisasterResponse**

</div>
