# 🚨 MESH112 - Proje Geliştirme Planı

## 📋 Yönetici Özeti

**MESH112**, 5 kişilik bir ekip tarafından 18 haftalık sürede geliştirilecek, afet anında internet altyapısı olmadan çalışan mesh network tabanlı acil durum iletişim platformudur. Bu belge, projenin teknik, organizasyonel ve operasyonel olarak nasıl yürütüleceğini detaylandırır.

**Hedef**: 18 hafta sonunda App Store ve Google Play'de yayınlanabilir, gerçek afet senaryolarında test edilmiş, TÜBİTAK ve AFAD'a sunuma hazır bir MVP (Minimum Viable Product) teslim etmek.

---

## 1. 🎯 Proje Yaklaşımı

Proje, **Agile/Scrum** metodolojisi ile 3 haftalık sprint'lerle yürütülecektir.

### 1.1 Analiz (Hafta 1-3)

**Hedef**: Teknik gereksinimleri netleştirmek, teknoloji seçimlerini onaylamak, tasarım dokümanlarını hazırlamak.

**Aktiviteler**:
- ✅ Mevcut afet iletişim çözümlerini araştırma (Bridgefy, FireChat, Zello analizi)
- ✅ BLE mesh networking protokollerini inceleme (AODV, Flooding, Gossip)
- ✅ On-device AI model seçimi (TinyLlama vs Phi-2 benchmark testleri)
- ✅ Kullanıcı senaryoları (User Stories) oluşturma
- ✅ Teknik mimari dokümantasyonu (System Design Document)
- ✅ Database şeması tasarımı
- ✅ API endpoint'leri planlama (opsiyonel cloud sync için)

**Çıktılar**:
- Technical Requirements Document (TRD)
- System Architecture Diagram
- Wireframe'ler ve UI mockup'ları
- Sprint backlog (Jira/Notion)

---

### 1.2 Tasarım (Hafta 4-6)

**Hedef**: Kullanıcı arayüzünü finalize etmek, veri akış diyagramlarını çıkarmak, network protokollerini tasarlamak.

**Aktiviteler**:
- 🎨 **UI/UX Design**: Figma'da high-fidelity mockup'lar (Chat, Map, Profile, SOS ekranları)
- 🏗️ **Component Architecture**: React Native component hierarchy
- 🔄 **Data Flow Diagrams**: Mesaj yayılımı, SOS broadcast, AI pipeline
- 📡 **Network Protocol Design**: Message format (JSON schema), routing algoritması
- 🧠 **AI Pipeline Design**: Input preprocessing, model inference, output post-processing
- 🗄️ **Database Design**: SQLite schema (messages, users, locations, network_nodes)

**Çıktılar**:
- Figma design system (color palette, typography, components)
- Message Protocol Specification v1.0
- AI Model Integration Plan
- Navigation flow diagram

---

### 1.3 Geliştirme (Hafta 7-15)

**Hedef**: Modüler geliştirme ile her sprint'te demo edilebilir özellikler teslim etmek.

#### Sprint 1 (Hafta 7-9): Temel Altyapı
- ✅ React Native projesi setup (TypeScript, ESLint, Prettier)
- ✅ Navigation yapısı (React Navigation)
- ✅ SQLite entegrasyonu (react-native-sqlite-storage)
- ✅ AsyncStorage yapılandırması
- ✅ BLE bağlantı kurma ve scanning (react-native-ble-plx)
- ✅ Temel UI component'leri (Button, Input, Card, Modal)
- ✅ Profil ekranı (kullanıcı bilgileri + kan grubu)

**Demo**: Profil oluşturma ve BLE cihazları tarama

#### Sprint 2 (Hafta 10-12): Mesh Network Core
- ✅ BLE advertise/scan logic
- ✅ Peer discovery ve connection management
- ✅ Message routing algoritması (multi-hop)
- ✅ Message deduplication (UUID tracking)
- ✅ TTL (Time To Live) yönetimi
- ✅ Chat ekranı (mesaj gönderme/alma)
- ✅ Offline message queue

**Demo**: 3+ cihaz arası mesajlaşma (2-hop relay)

#### Sprint 3 (Hafta 13-15): AI & Geolocation
- ✅ ONNX Runtime Mobile entegrasyonu
- ✅ TinyLlama model quantization (4-bit)
- ✅ Message classification pipeline (Medical/Emergency/Info/Need)
- ✅ Priority scoring (0.0-1.0)
- ✅ GPS location tracking (react-native-geolocation-service)
- ✅ Harita ekranı (OpenStreetMap offline tiles)
- ✅ SOS butonu ve emergency broadcast
- ✅ Priority-based message sorting

**Demo**: AI önceliklendirme + haritada konum paylaşımı

---

### 1.4 Test (Hafta 16-17)

**Hedef**: Fonksiyonel, performans ve kullanılabilirlik testlerini tamamlamak.

**Test Katmanları**:

#### Unit Tests
- Message routing logic (Jest)
- AI inference accuracy (>85% target)
- Database operations (SQLite CRUD)
- Utility functions (date formatting, distance calculation)

**Coverage hedefi**: >70%

#### Integration Tests
- BLE connection lifecycle
- Multi-hop message relay (3-5 hops)
- GPS + message attachment
- AI + message queue integration

#### End-to-End Tests
- Complete user flow: Profil oluştur → Mesaj gönder → Haritada gör
- SOS flow: Tek tap → Broadcast → Haritada kırmızı marker

#### Performance Tests
- **Latency**: <2 saniye message delivery (3-hop)
- **Battery**: <5% drain per hour (Detox + manual testing)
- **AI Inference**: <1 saniye (50 mesaj benchmark)
- **Network Load**: 100+ concurrent users (simülasyon)

#### Field Tests
- **Kampüs testi**: 20+ cihaz, 500m+ menzil
- **Afet simülasyonu**: Airplane mode, GSM kapalı, gerçek senaryolar
- **Kan grubu matching**: AB+ ihtiyacı → donor bulma testi

**Çıktılar**:
- Test Report (coverage, passed/failed rates)
- Performance Benchmark Results
- Bug fix backlog (Jira)

---

### 1.5 Deployment (Hafta 18)

**Hedef**: App Store ve Google Play'e beta yayını, dokümantasyon finalizasyonu, sunum hazırlığı.

**Aktiviteler**:
- 📱 **iOS**: TestFlight beta distribution
- 🤖 **Android**: Internal testing track (Google Play Console)
- 📄 **Dokümantasyon**: README, API docs, user guide (Türkçe + İngilizce)
- 🎥 **Demo Video**: 3-5 dakikalık tanıtım videosu (YouTube)
- 📊 **Sunum Hazırlığı**: PowerPoint/Keynote slides (AFAD, TÜBİTAK için)
- 🐛 **Beta Feedback**: 50+ tester'dan geri bildirim toplama
- 🔐 **Security Audit**: Encryption, data privacy review

**Çıktılar**:
- Beta build (iOS + Android)
- GitHub release (v0.9.0-beta)
- Project website (mesh112.org - basit landing page)
- Final presentation deck

---

## 2. 💻 Teknoloji Seçimi

### 2.1 Mobil Uygulama

| Kategori | Teknoloji | Versiyon | Justification |
|----------|-----------|----------|---------------|
| **Framework** | React Native | 0.74+ | Cross-platform (iOS+Android), geniş community, hızlı development |
| **Language** | TypeScript | 5.0+ | Type safety, daha az bug, IntelliSense desteği |
| **Navigation** | React Navigation | 6.x | Declarative routing, native-like transitions |
| **State Management** | Zustand | 4.x | Lightweight, Redux'a göre daha basit, performanslı |
| **BLE Library** | react-native-ble-plx | 3.x | Aktif geliştirme, iOS+Android desteği, scan/advertise |
| **WiFi Direct** | Native Modules | Custom | Platform-specific code (Java/Swift) |
| **Location** | react-native-geolocation-service | 5.x | Background location, high accuracy |
| **Maps** | react-native-maps | 1.x | OpenStreetMap offline tile desteği |
| **Database** | react-native-sqlite-storage | 6.x | SQL queries, migration support |
| **Storage** | @react-native-async-storage/async-storage | 1.x | Key-value storage |
| **UI Library** | React Native Paper | 5.x | Material Design components, theming |

---

### 2.2 Yapay Zeka

| Kategori | Teknoloji | Detaylar |
|----------|-----------|----------|
| **Model** | TinyLlama 1.1B | 4-bit quantized, ~600MB, Hugging Face |
| **Runtime** | ONNX Runtime Mobile | Cross-platform inference engine |
| **Quantization** | ONNX Quantization Tools | 32-bit → 4-bit (INT4) |
| **Fine-tuning** | LoRA/QLoRA | Turkish disaster message dataset (custom) |
| **Translation** | NLLB-200 (distilled) | Multilingual (TR/EN/AR/KU), ~300MB |
| **Embedding** | Sentence-BERT | Message similarity için (spam detection) |

**Model Pipeline**:
```
Input Message (String)
    ↓
Tokenization (BPE)
    ↓
ONNX Inference (TinyLlama)
    ↓
Output: {category: "medical", urgency: 0.85}
```

**Alternatif**: Eğer TinyLlama ağır gelirse, **DistilBERT-Turkish** (150MB) classification modeli kullanılabilir.

---

### 2.3 Backend (Opsiyonel Cloud Sync)

| Kategori | Teknoloji | Kullanım |
|----------|-----------|----------|
| **API Framework** | Node.js + Express | RESTful API (message history sync) |
| **Database** | PostgreSQL | Cloud'da message backup |
| **Authentication** | Firebase Auth | Anonymous auth (privacy-first) |
| **Cloud Storage** | Firebase Storage | AI model distribution (CDN) |
| **Hosting** | Vercel / Railway | Ücretsiz tier (MVP için yeterli) |
| **Analytics** | Sentry | Crash reporting, error tracking |

**Not**: Backend zorunlu değil, sadece internet varsa sync için. Offline-first öncelik!

---

### 2.4 CI/CD ve Test Araçları

| Kategori | Araç | Amaç |
|----------|------|------|
| **Version Control** | GitHub | Source code repository |
| **CI/CD** | GitHub Actions | Automated build/test/deploy |
| **Unit Test** | Jest | JavaScript/TypeScript unit tests |
| **E2E Test** | Detox | React Native end-to-end testing |
| **Code Quality** | ESLint + Prettier | Linting, formatting |
| **Type Checking** | TypeScript Compiler | Static type checking |
| **Performance** | Flipper | React Native debugging, profiling |
| **Crash Reporting** | Sentry | Production crash analytics |

**GitHub Actions Pipeline**:
```yaml
on: [push, pull_request]
jobs:
  test:
    - Lint check (ESLint)
    - Type check (tsc)
    - Unit tests (Jest)
    - Build iOS/Android
  deploy:
    - TestFlight upload (iOS)
    - Play Console upload (Android)
```

---

## 3. 👥 Ekip Rolleri ve Görev Dağılımı

### 3.1 Ekip Yapısı (5 Kişi)

| Rol | Kişi | Ana Sorumluluklar |
|-----|------|-------------------|
| **Project Manager / Full Stack Dev** | Kişi 1 | Sprint planning, backend API, cloud sync, ekip koordinasyonu |
| **AI/ML Engineer** | Kişi 2 | On-device AI model, ONNX entegrasyonu, message classification |
| **Mobile Developer (iOS/Android)** | Kişi 3 | React Native core, BLE/WiFi integration, navigation |
| **Network Engineer / Backend** | Kişi 4 | Mesh routing algoritması, multi-hop logic, message deduplication |
| **UI/UX Designer / Frontend** | Kişi 5 | Figma design, React Native UI components, user testing |

---

### 3.2 Detaylı Rol Açıklamaları

#### 👔 Project Manager / Full Stack Developer (Kişi 1)

**Sorumluluklar**:
- ✅ Sprint planning ve daily standup'lar organize etme
- ✅ Jira/Notion'da task tracking
- ✅ Opsiyonel backend API geliştirme (Node.js + Express)
- ✅ PostgreSQL database setup ve migration'lar
- ✅ Firebase entegrasyonu (Auth, Storage, Analytics)
- ✅ GitHub Actions CI/CD pipeline kurulumu
- ✅ Dokümantasyon koordinasyonu
- ✅ Dış paydaşlarla iletişim (AFAD, TÜBİTAK)

**Teknik Stack**: Node.js, PostgreSQL, Firebase, GitHub Actions

**Haftalık Çıktı**: Sprint report, backend endpoint'leri, deployment logs

---

#### 🤖 AI/ML Engineer (Kişi 2)

**Sorumluluklar**:
- ✅ TinyLlama/Phi-2 model araştırma ve seçimi
- ✅ Model quantization (32-bit → 4-bit ONNX)
- ✅ Turkish disaster message dataset oluşturma (web scraping + manual labeling)
- ✅ Fine-tuning (LoRA/QLoRA) veya prompt engineering
- ✅ ONNX Runtime Mobile entegrasyonu (React Native)
- ✅ Message classification pipeline (input → inference → output)
- ✅ Translation model entegrasyonu (NLLB-200)
- ✅ AI model performans testleri (accuracy, latency)

**Teknik Stack**: Python, PyTorch, ONNX, Hugging Face Transformers, React Native

**Haftalık Çıktı**: Model benchmark reports, inference latency graphs, classification accuracy

---

#### 📱 Mobile Developer (Kişi 3)

**Sorumluluklar**:
- ✅ React Native proje setup (TypeScript, ESLint, Prettier)
- ✅ React Navigation yapılandırması (stack, tab, drawer navigators)
- ✅ BLE library entegrasyonu (react-native-ble-plx)
- ✅ WiFi Direct native module geliştirme (Java/Kotlin + Swift/Objective-C)
- ✅ GPS location tracking (react-native-geolocation-service)
- ✅ Offline map entegrasyonu (react-native-maps + OpenStreetMap tiles)
- ✅ Push notification setup (Firebase Cloud Messaging)
- ✅ iOS/Android build ve release management
- ✅ App Store / Google Play submission

**Teknik Stack**: React Native, TypeScript, Java/Kotlin (Android), Swift (iOS)

**Haftalık Çıktı**: Feature branches (GitHub), weekly build (TestFlight/Play Console)

---

#### 🌐 Network Engineer / Backend Developer (Kişi 4)

**Sorumluluklar**:
- ✅ Mesh network routing algoritması tasarımı (AODV/Flooding hybrid)
- ✅ Message protocol design (JSON schema, header fields)
- ✅ Multi-hop relay logic (max 10 hops)
- ✅ Message deduplication (UUID tracking, cache management)
- ✅ TTL (Time To Live) yönetimi (24 saat)
- ✅ Network topology visualization (D3.js grafik)
- ✅ BLE advertise/scan scheduling (battery optimization)
- ✅ SQLite database CRUD operations (messages, peers, locations)
- ✅ Network performance testing (latency, throughput, packet loss)

**Teknik Stack**: React Native, BLE protocols, SQLite, Graph algorithms

**Haftalık Çıktı**: Network simulator (Python/JavaScript), routing test reports

---

#### 🎨 UI/UX Designer / Frontend Developer (Kişi 5)

**Sorumluluklar**:
- ✅ User research ve persona oluşturma (afetzede, kurtarma ekibi, doktor)
- ✅ Wireframe'ler (low-fidelity, Balsamiq/Sketch)
- ✅ High-fidelity mockup'lar (Figma)
- ✅ Design system (color palette, typography, iconography)
- ✅ React Native UI component geliştirme (Button, Card, Modal, Input)
- ✅ Animasyonlar (react-native-reanimated)
- ✅ Accessibility (a11y) compliance (VoiceOver, TalkBack)
- ✅ Usability testing (50+ beta tester feedback)
- ✅ Emergency UX patterns (one-tap SOS, high contrast, large buttons)

**Teknik Stack**: Figma, React Native, React Native Paper, Reanimated

**Haftalık Çıktı**: Figma design files, component library (Storybook), usability test reports

---

### 3.3 Çapraz Fonksiyonel Görevler

Bazı görevler tüm ekibin katılımını gerektirir:

| Görev | Katılımcılar | Süre |
|-------|--------------|------|
| **Sprint Planning** | Tüm ekip | 2 saat (her sprint başı) |
| **Daily Standup** | Tüm ekip | 15 dakika (günlük) |
| **Code Review** | İlgili 2-3 kişi | 30 dakika (PR başı) |
| **Sprint Retrospective** | Tüm ekip | 1 saat (her sprint sonu) |
| **Demo Day** | Tüm ekip + danışman | 2 saat (her sprint sonu) |

---

## 4. 📅 Zaman Planı (18 Hafta)

### Sprint Bazlı Zaman Çizelgesi

| Faz | Haftalar | Sprint | Ana Hedef | Deliverables |
|-----|----------|--------|-----------|--------------|
| **Faz 1: Araştırma & Analiz** | 1-3 | Sprint 0 | Teknik araştırma, mimari tasarım | TRD, System Design, Wireframes |
| **Faz 2: Tasarım & Prototip** | 4-6 | Sprint 1 | UI/UX finalize, temel altyapı | Figma mockups, React Native skeleton |
| **Faz 3: MVP Geliştirme** | 7-12 | Sprint 2-3 | BLE mesh network + Chat | 3-cihaz mesajlaşma demo |
| **Faz 4: AI & Geolocation** | 13-15 | Sprint 4 | AI entegrasyonu, harita | AI önceliklendirme + GPS demo |
| **Faz 5: Test & Optimizasyon** | 16-17 | Sprint 5 | Unit/E2E test, battery optimization | Test report, bug fixes |
| **Faz 6: Deployment & Sunum** | 18 | Sprint 6 | Beta release, dokümantasyon | App Store beta, final presentation |

---

### Detaylı Haftalık Plan

#### **Hafta 1-3: Araştırma & Analiz**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **1** | Proje planı, Jira setup | TinyLlama vs Phi-2 araştırma | React Native best practices | Mesh routing araştırma (AODV) | User persona oluşturma |
| **2** | Backend tech stack seçimi | Turkish NLP dataset araştırma | BLE library benchmark | Message protocol tasarımı | Wireframe'ler (4 ekran) |
| **3** | API endpoint tasarımı | ONNX quantization POC | Navigation yapı tasarımı | Graph algoritması POC | Figma mockup başlangıç |

**Milestone**: Technical Requirements Document tamamlandı ✅

---

#### **Hafta 4-6: Tasarım & Prototip**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **4** | Firebase setup | Model fine-tuning dataset | RN proje init (TypeScript) | SQLite schema tasarımı | Figma design system |
| **5** | CI/CD pipeline (GitHub Actions) | ONNX model export | BLE library entegrasyonu | Message queue tasarımı | Chat ekranı mockup |
| **6** | Database migration scriptleri | Inference pipeline test | Profil ekranı geliştirme | Routing simulator (Python) | Map + SOS ekranı mockup |

**Milestone**: Figma design tamamlandı, RN skeleton çalışıyor ✅

---

#### **Hafta 7-9: Sprint 2 - BLE Mesh Core**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **7** | Backend API endpoints | Mock AI responses | BLE scan/advertise | Peer discovery logic | Chat UI components |
| **8** | User auth (Firebase) | Model entegrasyonu başlangıç | Message send/receive | Multi-hop routing | Message bubble styling |
| **9** | Sprint review hazırlık | Offline inference test | BLE connection stability | Deduplication cache | Priority color indicators |

**Milestone**: 2-hop mesajlaşma çalışıyor 🎉

---

#### **Hafta 10-12: Sprint 3 - Advanced Networking**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **10** | Analytics entegrasyonu | Classification accuracy test | GPS location tracking | TTL yönetimi | Harita ekranı geliştirme |
| **11** | Cloud sync logic | Priority scoring optimize | OpenStreetMap tiles | Network topology graph | User marker tasarımı |
| **12** | Beta tester recruitment | Spam filtering | Background location | Message flood control | SOS button tasarımı |

**Milestone**: 5-cihaz mesh network stabil ✅

---

#### **Hafta 13-15: Sprint 4 - AI & Geolocation**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **13** | Performance monitoring | Translation model | SOS broadcast logic | Emergency message routing | SOS animation |
| **14** | Crash reporting setup | Blood type matching AI | Map + GPS entegrasyonu | Location-based proximity | Filter UI (category) |
| **15** | Sprint demo AFAD'a | AI latency optimization | Offline map caching | Battery optimization | Usability testing |

**Milestone**: AI + GPS tam entegre 🧠📍

---

#### **Hafta 16-17: Sprint 5 - Test & Optimizasyon**

| Hafta | Kişi 1 (PM) | Kişi 2 (AI) | Kişi 3 (Mobile) | Kişi 4 (Network) | Kişi 5 (UI/UX) |
|-------|-------------|-------------|-----------------|------------------|----------------|
| **16** | Test plan yazma | AI accuracy report | E2E test (Detox) | Network stress test | A11y compliance check |
| **17** | Bug triage | Model size optimization | iOS build fix | Message latency optimize | Beta feedback analizi |

**Milestone**: Test coverage >70%, major buglar çözüldü ✅

---

#### **Hafta 18: Sprint 6 - Deployment & Sunum**

| Tüm Ekip | Görevler |
|----------|----------|
| **Pazartesi** | TestFlight + Play Console beta upload |
| **Salı** | README, API docs, user guide finalize |
| **Çarşamba** | Demo video çekimi ve editing |
| **Perşembe** | Final presentation hazırlık (PowerPoint) |
| **Cuma** | **Final Sunumu** (danışman + jüri) 🎉 |

**Milestone**: Beta yayında, sunum tamamlandı 🚀

---

## 5. 💰 Maliyet Analizi

### 5.1 Donanım ve Ekipman

| Kalem | Birim Maliyet | Adet | Toplam |
|-------|---------------|------|--------|
| **Test Cihazları** (eski Android/iOS telefonlar) | ₺2,000 | 5 | ₺10,000 |
| **Development Lisansları** (Apple Developer) | $99/yıl | 1 | ₺3,500 |
| **Google Play Developer** | $25 (tek seferlik) | 1 | ₺900 |
| **Laptop/PC** (ekip zaten sahipse) | - | - | ₺0 |

**Alt Toplam**: ₺14,400

---

### 5.2 Yazılım ve Servisler

| Servis | Maliyet | Süre | Toplam |
|--------|---------|------|--------|
| **GitHub** (ücretsiz public repo) | ₺0 | - | ₺0 |
| **Firebase** (Spark Plan - ücretsiz) | ₺0 | - | ₺0 |
| **Vercel/Railway** (Hobby Plan - ücretsiz) | ₺0 | - | ₺0 |
| **Figma** (Education Plan - ücretsiz) | ₺0 | - | ₺0 |
| **Sentry** (Developer Plan - ücretsiz 5K events) | ₺0 | - | ₺0 |
| **OpenAI API** (AI fine-tuning - opsiyonel) | $50 | - | ₺1,800 |
| **Hugging Face Pro** (model hosting - opsiyonel) | $9/ay | 4 ay | ₺1,300 |

**Alt Toplam**: ₺3,100

---

### 5.3 Test ve Operasyonel

| Kalem | Maliyet | Detay |
|-------|---------|-------|
| **Beta Tester İncentive** | ₺5,000 | 50 tester × ₺100 hediye kartı |
| **Afet Simülasyonu** (saha testi) | ₺3,000 | Ulaşım, ekipman kiralama |
| **Domain + Hosting** (mesh112.org) | ₺500 | 1 yıllık domain |
| **Cloud Credits** (AWS/GCP opsiyonel) | ₺2,000 | Model training için |

**Alt Toplam**: ₺10,500

---

### 5.4 Dokümantasyon ve Sunum

| Kalem | Maliyet |
|-------|---------|
| **Profesyonel video editing** (demo video) | ₺2,000 |
| **Poster/Banner tasarımı** (sunum için) | ₺1,000 |
| **Printed materials** (AFAD sunumu) | ₺500 |

**Alt Toplam**: ₺3,500

---

### 📊 Toplam Bütçe

| Kategori | Tutar |
|----------|-------|
| Donanım & Ekipman | ₺14,400 |
| Yazılım & Servisler | ₺3,100 |
| Test & Operasyonel | ₺10,500 |
| Dokümantasyon & Sunum | ₺3,500 |
| **TOPLAM** | **₺31,500** |

**Not**: Bu bütçe **maksimum senaryo** için. Eğer ekipte test cihazları varsa ve cloud hizmetleri gereksizse, maliyet **₺10,000 altına** düşebilir.

---

### 5.5 Fon Kaynakları

| Kaynak | Tutar | Olasılık |
|--------|-------|----------|
| **TÜBİTAK 2204** | ₺25,000 | Yüksek (proje profili uygun) |
| **Üniversite Proje Fonu** | ₺10,000 | Orta |
| **Teknofest** (ödül) | ₺100,000 | Düşük (yarışma kazanma durumu) |
| **Angel Investor** (sosyal etki fonu) | ₺50,000+ | Orta (MVP sonrası) |
| **Kendi Katkı** | ₺5,000 | Kesin (ekip payı) |

**Önerilen Strateji**: TÜBİTAK 2204'e başvuru (Kasım 2025) + üniversite fonlarını birleştir.

---

## 6. ⚠️ Risk ve Çözüm Planı

### 6.1 Teknik Riskler

| Risk | Olasılık | Etki | Azaltma Stratejisi |
|------|----------|------|-------------------|
| **BLE bağlantı instability** | Yüksek | Kritik | Extensive testing, WiFi Direct fallback, connection retry logic |
| **AI model boyutu** (>100MB app size) | Orta | Yüksek | Agresif quantization (4-bit), model distillation, opsiyonel download |
| **Battery drain** (>10%/saat) | Yüksek | Kritik | Adaptive scanning, background task throttling, power profiling (Flipper) |
| **iOS BLE restrictions** | Orta | Orta | Background mode testing, CoreBluetooth API optimize |
| **Android fragmentation** | Yüksek | Orta | Test on Android 9+ (API 28+), compatibility matrix |
| **Multi-hop latency** (>5 saniye) | Orta | Yüksek | Routing algorithm optimize, message priority queue |
| **GPS accuracy** (enkaz altında) | Yüksek | Kritik | Last known location cache, manual coordinate entry option |

---

### 6.2 Organizasyonel Riskler

| Risk | Olasılık | Etki | Azaltma Stratejisi |
|------|----------|------|-------------------|
| **Ekip üyesi ayrılması** | Düşük | Kritik | Knowledge sharing (weekly docs), pair programming, cross-training |
| **Scope creep** (özellik patlaması) | Yüksek | Yüksek | Strict MVP definition, feature freeze week 15, backlog prioritization |
| **Danışman feedback gecikmesi** | Orta | Orta | Bi-weekly sync meeting, Slack channel, async dokümantasyon |
| **Sprint deadline kaçırma** | Orta | Orta | Buffer week (18. hafta), feature degradation plan, MVP-first mindset |
| **Ekip iletişim kopukluğu** | Orta | Yüksek | Daily standup (non-negotiable), Slack 24/7, pair programming |

---

### 6.3 Operasyonel Riskler

| Risk | Olasılık | Etki | Azaltma Stratejisi |
|------|----------|------|-------------------|
| **Test cihazı yetersizliği** | Orta | Orta | Arkadaşlardan/aileden cihaz ödünç alma, kampüste beta tester recruitment |
| **AFAD toplantısı iptal** | Orta | Düşük | Video demo hazırlığı, asenkron sunum materyali |
| **App Store rejection** | Orta | Yüksek | Guideline research (önceden), TestFlight extensive beta (1000+ tester) |
| **Beta tester bulma zorluğu** | Düşük | Orta | Kampüs posterleri, sosyal medya, deprem farkındalığı kampanyası |
| **Cloud service downtime** | Düşük | Düşük | Offline-first architecture (backend opsiyonel), local fallback |

---

### 6.4 Acil Durum Planları

#### Plan A: MVP Scope Reduction
Eğer hafta 14'te %50 completion < hedef:
- ❌ Translation feature → v2.0'a ertelenir
- ❌ Blood type matching → manual search ile replace
- ✅ Core: BLE mesh + Chat + GPS + SOS (korunur)

#### Plan B: Hybrid Approach
AI model çok ağır gelirse:
- ✅ Simple rule-based classification (keyword matching)
- ✅ Cloud-based AI (internet varsa)
- ❌ On-device AI → future work

#### Plan C: Single Platform Launch
18 hafta yetmezse:
- ✅ Android-only release (market share %72 Türkiye'de)
- ❌ iOS → post-graduation

---

## 7. 🛠️ Verimlilik Araçları

### 7.1 Geliştirme Araçları

| Kategori | Araç | Kullanım Amacı | Maliyet |
|----------|------|----------------|---------|
| **IDE** | VS Code | Primary editor (RN, JS, Python) | Ücretsiz |
| **Version Control** | GitHub | Source code, issue tracking, wiki | Ücretsiz |
| **Code Review** | GitHub Pull Requests | Peer review, automated checks | Ücretsiz |
| **Linting** | ESLint + Prettier | Code quality, formatting | Ücretsiz |
| **Debugging** | Flipper | React Native network, Redux, performance | Ücretsiz |
| **Mobile Testing** | Xcode + Android Studio | Native debugging, profiling | Ücretsiz |
| **AI Development** | Jupyter Notebook + Google Colab | Model training, experimentation | Ücretsiz |
| **API Testing** | Postman | Backend endpoint testing | Ücretsiz |

---

### 7.2 Proje Yönetimi

| Araç | Kullanım | Sorumlular | Plan |
|------|----------|------------|------|
| **Jira** / **Notion** | Sprint planning, backlog, task tracking | PM (Kişi 1) | Ücretsiz (Education) |
| **Slack** | Ekip iletişimi, kanal bazlı (dev, ai, design) | Tüm ekip | Ücretsiz |
| **Google Meet** / **Zoom** | Daily standup, sprint review | Tüm ekip | Ücretsiz |
| **Miro** / **Figma** | Brainstorming, architecture diagrams | Designer + PM | Ücretsiz (Education) |
| **Google Drive** | Döküman paylaşımı (TRD, reports) | Tüm ekip | Ücretsiz |

---

### 7.3 Tasarım Araçları

| Araç | Kullanım | Sorumlular |
|------|----------|------------|
| **Figma** | UI/UX design, prototyping | Kişi 5 (Designer) |
| **Storybook** | Component library showcase | Kişi 5 + Kişi 3 |
| **Unsplash** / **Flaticon** | Stock images, icons | Kişi 5 |
| **Lottie** | Animasyonlar (SOS pulse effect) | Kişi 5 |

---

### 7.4 Test ve Quality Assurance

| Araç | Kullanım | Sorumlular |
|------|----------|------------|
| **Jest** | Unit testing (JS/TS) | Tüm dev ekibi |
| **Detox** | E2E testing (RN) | Kişi 3 (Mobile) |
| **Sentry** | Crash reporting, error tracking | Kişi 1 (PM) |
| **Firebase Performance** | App performance monitoring | Kişi 3 |
| **Lighthouse** | Web performance (landing page) | Kişi 5 |

---

### 7.5 Dokümantasyon

| Araç | Kullanım | Format |
|------|----------|--------|
| **GitHub Wiki** | Technical documentation | Markdown |
| **JSDoc** | Code documentation (inline) | JavaScript comments |
| **Swagger** / **Postman** | API documentation | OpenAPI 3.0 |
| **README.md** | Project overview, setup guide | Markdown |
| **CONTRIBUTING.md** | Contributor guidelines | Markdown |

---

### 7.6 İletişim ve Koordinasyon

#### Slack Kanal Yapısı
```
#general          → Genel duyurular, sosyal
#dev              → Development discussions
#ai               → AI/ML specific
#design           → UI/UX feedback
#testing          → Bug reports, test results
#random           → Memes, offtopic
#standup          → Daily standup async updates
```

#### Meeting Schedule
| Toplantı | Sıklık | Süre | Katılımcılar |
|----------|--------|------|--------------|
| **Daily Standup** | Her gün (09:00) | 15 dk | Tüm ekip |
| **Sprint Planning** | Sprint başı | 2 saat | Tüm ekip |
| **Sprint Review** | Sprint sonu | 1.5 saat | Tüm ekip + danışman |
| **Retrospective** | Sprint sonu | 1 saat | Tüm ekip |
| **Code Review Session** | Haftada 2× | 1 saat | Dev ekibi (Kişi 1-4) |
| **Design Critique** | Haftada 1× | 1 saat | Kişi 5 + Kişi 3 |

---

## 8. 📈 Başarı Metrikleri ve KPI'lar

### 8.1 Teknik KPI'lar

| Metrik | Hedef | Ölçüm Aracı |
|--------|-------|-------------|
| **Code Coverage** | >70% | Jest + Istanbul |
| **Build Success Rate** | >95% | GitHub Actions |
| **Crash-Free Rate** | >99% | Sentry |
| **App Size** | <100MB | Android Studio / Xcode |
| **Message Latency (3-hop)** | <2 saniye | Custom benchmark |
| **AI Inference Time** | <1 saniye | Performance profiler |
| **Battery Drain** | <5%/saat | Xcode Energy Log |
| **BLE Connection Success** | >90% | Field test |

---

### 8.2 Proje Yönetim KPI'lar

| Metrik | Hedef | Ölçüm Aracı |
|--------|-------|-------------|
| **Sprint Completion Rate** | >80% | Jira burndown chart |
| **Velocity (Story Points)** | 40-60 / sprint | Jira |
| **Code Review Turnaround** | <24 saat | GitHub metrics |
| **Bug Resolution Time** | <48 saat (kritik) | Jira SLA |
| **Daily Standup Attendance** | 100% | Slack poll |

---

### 8.3 Kullanıcı KPI'lar (Beta)

| Metrik | Hedef | Ölçüm Aracı |
|--------|-------|-------------|
| **Beta Tester Sayısı** | 50+ | TestFlight / Play Console |
| **Aktif Kullanıcı (DAU)** | 30+ | Firebase Analytics |
| **Retention (7-day)** | >40% | Firebase Analytics |
| **User Feedback Score** | >4.0/5.0 | Google Form survey |
| **Feature Adoption (SOS)** | >70% test etti | Firebase Events |

---

## 9. 🎓 Akademik ve Sosyal Etki

### 9.1 Akademik Çıktılar

**Potansiyel Makale**:
- **Başlık**: "MESH112: On-Device AI-Powered Emergency Communication via Bluetooth Mesh Networks"
- **Venue**: IEEE International Conference on Pervasive Computing and Communications (PerCom)
- **Katkı**: Novel mesh routing + AI prioritization hybrid approach
- **Deadline**: Ocak 2026 (submission)

**Açık Kaynak Katkı**:
- GitHub repository (MIT License)
- NPM package: `@mesh112/routing` (mesh network library)
- AI model: Hugging Face (Turkish disaster classification)

---

### 9.2 Yarışmalar ve Ödüller

| Yarışma | Başvuru Tarihi | Potansiyel Ödül |
|---------|----------------|-----------------|
| **TÜBİTAK 2204** | Kasım 2025 | ₺25,000 + sertifika |
| **Teknofest Yazılım** | Mart 2026 | ₺100,000 (birinci) |
| **Google Solution Challenge** | Şubat 2026 | $1,000 + mentorship |
| **IEEE Xtreme** | Ekim 2025 | Uluslararası recognition |

---

### 9.3 Sosyal Etki Hedefleri

**6 Ay İçinde**:
- ✅ AFAD'a resmi sunum (pilot proje teklifi)
- ✅ 3+ üniversite kampüsünde deprem tatbikatında test
- ✅ Kızılay ile iş birliği görüşmeleri

**1 Yıl İçinde**:
- ✅ 10,000+ aktif kullanıcı (Türkiye)
- ✅ 5+ belediye ile acil durum protokolü entegrasyonu
- ✅ Uluslararası konferansta makale sunumu

**2+ Yıl Vizyonu**:
- ✅ Türkiye genelinde resmi afet uygulaması statüsü
- ✅ Deprem riskli ülkelere ihracat (Japonya, Nepal, Şili)
- ✅ WHO/UNDP iş birliği (global disaster response toolkit)

---

## 10. 📝 Sonuç ve Eylem Adımları

### 10.1 Hemen Başlanacak Görevler (Hafta 1)

**Kişi 1 (PM)**:
- [ ] Jira/Notion workspace oluştur
- [ ] GitHub organization + repository setup
- [ ] Ekip ile kickoff meeting (proje planı sunumu)
- [ ] TÜBİTAK 2204 başvuru dosyası hazırlığı

**Kişi 2 (AI)**:
- [ ] TinyLlama ve Phi-2 model download + benchmark
- [ ] Turkish disaster message dataset research (Twitter, news archives)
- [ ] ONNX quantization tutorial çalış
- [ ] Python environment setup (PyTorch, Transformers)

**Kişi 3 (Mobile)**:
- [ ] React Native kurulum (MacBook/PC)
- [ ] react-native-ble-plx dokümantasyonu oku
- [ ] Boilerplate proje oluştur (TypeScript template)
- [ ] iOS Developer hesabı aç ($99)

**Kişi 4 (Network)**:
- [ ] Mesh routing makaleleri oku (AODV, DSR, Flooding)
- [ ] BLE protocol specification oku
- [ ] Python network simulator başlat (NetworkX library)
- [ ] Message protocol JSON schema taslağı

**Kişi 5 (UI/UX)**:
- [ ] Figma workspace oluştur
- [ ] Competitor analysis (Bridgefy, FireChat, Zello UI)
- [ ] User persona oluştur (3 tip: afetzede, kurtarma, doktor)
- [ ] Low-fidelity wireframe (kağıt sketch)

---

### 10.2 İlk Sprint Hedefi (Hafta 1-3)

**Sprint Goal**: "Technical foundation hazır, tasarım %70 tamamlanmış, ekip synchronized"

**Definition of Done**:
- ✅ Technical Requirements Document (20+ sayfa) yazıldı
- ✅ Figma'da 4 ekran high-fidelity mockup tamamlandı
- ✅ React Native boilerplate projesi çalışıyor (Hello World)
- ✅ AI model seçimi yapıldı (TinyLlama vs Phi-2 benchmark sonucu)
- ✅ Mesh routing algoritması seçildi (literatür araştırması)
- ✅ GitHub repository'de 10+ commit
- ✅ İlk sprint review yapıldı (danışman + ekip)

---

### 10.3 Motivasyon ve Ekip Kültürü

**Değerlerimiz**:
- 🚀 **Move Fast, Break Things**: Hızlı prototipleme, fail fast
- 🤝 **Collaboration Over Competition**: Ekip başarısı > bireysel ego
- 📚 **Learn in Public**: Her sprint bir blog post (Medium/Dev.to)
- 💡 **User-Centric**: Afetzede empati, gerçek ihtiyaçlar öncelik
- 🔓 **Open Source First**: Topluluk için, toplulukla birlikte

**Ekip Ritüelleri**:
- ☕ **Coffee Chat Friday**: Haftalık casual sohbet (non-work topics)
- 🎉 **Sprint Celebration**: Her sprint sonunda küçük kutlama (pizza/kahve)
- 🏆 **MVP of the Sprint**: En çok katkıda bulunan kişiye sembolik ödül
- 📖 **Learning Session**: Haftada 1× birisi yeni öğrendiği teknolojiyi anlatır

---

## 📚 Ek Kaynaklar

### Teknik Dökümanlar
- [React Native Documentation](https://reactnative.dev/)
- [ONNX Runtime Mobile](https://onnxruntime.ai/docs/tutorials/mobile/)
- [BLE Mesh Networking Specification](https://www.bluetooth.com/specifications/specs/mesh-protocol/)
- [AODV Routing Protocol](https://tools.ietf.org/html/rfc3561)

### Benzer Projeler
- [Bridgefy](https://bridgefy.me/) - Mesh messaging app
- [FireChat](https://en.wikipedia.org/wiki/FireChat) - Offline chat (2014)
- [Briar](https://briarproject.org/) - P2P secure messaging

### Afet Yönetimi
- [AFAD Deprem Yönetmeliği](https://www.afad.gov.tr/)
- [WHO Emergency Response Framework](https://www.who.int/emergencies)

---

## ✅ Son Kontrol Listesi

Projeye başlamadan önce tüm ekip şu soruları cevaplamalı:

- [ ] Her ekip üyesi rolünü ve sorumluluklarını anladı mı?
- [ ] Gerekli yazılım/donanım temin edildi mi?
- [ ] GitHub repository ve Jira/Notion hazır mı?
- [ ] İlk 3 haftanın task'ları net mi?
- [ ] Danışman ile ilk toplantı planlandı mı?
- [ ] Ekip iletişim kanalları (Slack) aktif mi?
- [ ] Risk planları okundu ve anlaşıldı mı?
- [ ] Herkes 18 haftalık commitment verebilir mi?

**Cevaplar EVET ise** → 🚀 **BAŞLAYALIM!**

---

**MESH112 Ekibi**  
*Afete Dirençli Türkiye İçin*  
🇹🇷 #MESH112 #AcilDurum #YapayZeka

**Versiyon**: 1.0  
**Tarih**: 26 Ekim 2025  
**Durum**: Onay Bekliyor

---

*"Afet anında her telefon bir umut, her bağlantı bir hayat."*
