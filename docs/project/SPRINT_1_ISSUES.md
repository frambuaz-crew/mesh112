# 🚀 Sprint 1: Araştırma & Prototip (Hafta 1-3)

**Sprint Tarihleri**: 28 Ekim 2025 - 17 Kasım 2025 (3 hafta)

**Sprint Hedefi**: Proje altyapısını kurmak ve teknoloji araştırmasını tamamlamak

---

## 📊 Sprint 1 Issue'ları

### Hafta 1 (28 Ekim - 3 Kasım) - Altyapı Kurulumu

#### Issue #1: Firebase Projesi Kurulumu
```
Başlık: Setup Firebase project for analytics and cloud sync
Atanan: @emre (PM)
Priority: High
Sprint: Sprint 1
Labels: setup, infrastructure

Açıklama:
Firebase projesi oluştur ve temel servisleri yapılandır:
- [ ] Firebase Console'da yeni proje oluştur (mesh112-app)
- [ ] Authentication (Email/Google) aktif et
- [ ] Realtime Database oluştur (opsiyonel sync için)
- [ ] Storage bucket oluştur (kullanıcı profil fotoları)
- [ ] Analytics ekle
- [ ] google-services.json (Android) indir
- [ ] GoogleService-Info.plist (iOS) indir
- [ ] README.md'ye Firebase setup dökümanı ekle

Kabul Kriterleri:
✅ Firebase projesi oluşturulmuş
✅ Tüm servisler aktif
✅ Konfigürasyon dosyaları indirilmiş
✅ Döküman hazır

Tahmini Süre: 2 saat
```

---

#### Issue #2: İlk Sprint Planning ve Sprint Backlog
```
Başlık: Conduct Sprint 1 planning and create sprint backlog
Atanan: @emre (PM)
Priority: High
Sprint: Sprint 1
Labels: project-management, sprint-planning

Açıklama:
İlk sprint planning meeting'i organize et:
- [ ] Zoom/Discord toplantı linki oluştur
- [ ] Hafta 1-3 görevlerini issue'lara çevir
- [ ] Her issue'ya kişi ata
- [ ] Priority ve story points belirle
- [ ] GitHub Projects board'unda organize et
- [ ] Sprint başlangıç notlarını docs/sprints/sprint-1.md'ye yaz

Kabul Kriterleri:
✅ Tüm Hafta 1-3 görevleri issue olarak oluşturulmuş
✅ Herkes kendi görevlerini biliyor
✅ Sprint dökümanı hazır

Tahmini Süre: 3 saat
```

---

#### Issue #3: AI Model Araştırması - TinyLlama vs Phi-2
```
Başlık: Research and compare on-device AI models (TinyLlama 1.1B vs Phi-2)
Atanan: @ayse (AI Engineer)
Priority: High
Sprint: Sprint 1
Labels: research, ai-ml

Açıklama:
On-device AI için en uygun modeli belirle:

**Araştırılacaklar**:
- [ ] TinyLlama 1.1B model boyutu (4-bit quantized)
- [ ] Phi-2 2.7B model boyutu (4-bit quantized)
- [ ] ONNX Runtime Mobile performance benchmarks
- [ ] Android/iOS cihazlarda inference süresi
- [ ] RAM kullanımı
- [ ] Battery impact
- [ ] Türkçe NLP accuracy (mesaj kategorileri için)

**Deliverable**:
`docs/research/ai-model-comparison.md` dosyası oluştur:
- Model karşılaştırma tablosu
- Benchmark sonuçları
- **Öneri**: Hangi model kullanılmalı? Neden?

Kabul Kriterleri:
✅ Her iki model test edilmiş
✅ Performance metrikleri ölçülmüş
✅ Nihai karar verilmiş (örn: TinyLlama seçildi çünkü...)
✅ Döküman hazır

Tahmini Süre: 8 saat (2 gün)
```

---

#### Issue #4: BLE Mesh Networking Kütüphane Araştırması
```
Başlık: Research BLE mesh networking libraries for React Native
Atanan: @mehmet (Network Engineer)
Priority: High
Sprint: Sprint 1
Labels: research, networking, ble

Açıklama:
React Native için en uygun BLE mesh kütüphanesini belirle:

**Araştırılacak Kütüphaneler**:
- [ ] react-native-ble-plx (önerilen)
- [ ] react-native-ble-manager
- [ ] react-native-bluetooth-classic
- [ ] Custom native module (Java/Kotlin + Swift/Obj-C)

**Kriterler**:
- Android + iOS desteği
- BLE Central + Peripheral mode
- Background scanning
- Mesaj relay (multi-hop) yapılabilirliği
- Aktif bakım (son 6 ay içinde commit)
- Community size

**Test Senaryosu**:
- [ ] Basit BLE scanner app yap (2 cihaz arası)
- [ ] Mesaj gönder/al test et
- [ ] Range test et (kaç metre?)
- [ ] Battery impact ölç

**Deliverable**:
`docs/research/ble-library-comparison.md`

Kabul Kriterleri:
✅ 3+ kütüphane karşılaştırılmış
✅ Test app çalışıyor
✅ Performans metrikleri ölçülmüş
✅ Öneri: [kütüphane adı] kullanılmalı

Tahmini Süre: 10 saat (2-3 gün)
```

---

#### Issue #5: UI/UX Wireframe Tasarımları (Figma)
```
Başlık: Create wireframes for main screens in Figma
Atanan: @fatma (UI/UX Designer)
Priority: Medium
Sprint: Sprint 1
Labels: design, ui-ux, figma

Açıklama:
Ana ekranların wireframe'lerini Figma'da oluştur:

**Ekranlar**:
1. [ ] **Splash Screen** - Uygulama açılış
2. [ ] **Chat Screen** - WhatsApp-like mesajlaşma
3. [ ] **Map Screen** - GPS konum + SOS marker'ları
4. [ ] **Profile Screen** - Kan grubu, tıbbi bilgi
5. [ ] **SOS Button** - Acil durum butonu (tüm ekranlarda)

**Tasarım Gereksinimleri**:
- High contrast (deprem anında okunabilir)
- Büyük touch target'lar (40x40px minimum)
- Offline-first indicators
- Türkçe UI (ı, ğ, ş karakterleri test et)
- Dark mode desteği (battery saving)

**Figma Workspace**:
- [ ] Figma team workspace oluştur
- [ ] Design system başlangıcı (renkler, tipografi)
- [ ] Ekip üyelerini davet et (view-only)

**Deliverable**:
Figma link + `docs/design/wireframes-v1.md` (ekran açıklamaları)

Kabul Kriterleri:
✅ 5 ana ekran wireframe'i tamamlanmış
✅ Acil durum UX prensipleri uygulanmış
✅ Figma workspace ekibe paylaşılmış

Tahmini Süre: 12 saat (3 gün)
```

---

#### Issue #6: React Native Kurulum Dökümanı Hazırlama
```
Başlık: Create comprehensive React Native setup documentation
Atanan: @ali (Mobile Developer)
Priority: Medium
Sprint: Sprint 1
Labels: documentation, setup, react-native

Açıklama:
Ekip için detaylı React Native kurulum rehberi hazırla:

**Kapsam**:
- [ ] Windows kurulum (Android Studio, JDK, SDK)
- [ ] macOS kurulum (Xcode, CocoaPods, iOS simulator)
- [ ] VS Code extensions (React Native Tools, ESLint, Prettier)
- [ ] Troubleshooting (yaygın hatalar + çözümler)
- [ ] Proje oluşturma:
  ```bash
  npx react-native init MESH112 --template react-native-template-typescript
  ```

**Test**:
- [ ] Kendi bilgisayarında sıfırdan kurulum yap
- [ ] Android emulator'de "Hello World" çalıştır
- [ ] iOS simulator'de çalıştır (macOS varsa)
- [ ] Tüm adımları dökümanla

**Deliverable**:
`docs/guides/REACT_NATIVE_SETUP.md`

Kabul Kriterleri:
✅ Windows + macOS adımları mevcut
✅ Ekran görüntüleriyle desteklenmiş
✅ Common errors bölümü var
✅ Test edilmiş (birisi bu dökümanla kurulum yapabilmeli)

Tahmini Süre: 6 saat (1.5 gün)
```

---

### Hafta 2 (4-10 Kasım) - Mimari Tasarım

#### Issue #7: Sistem Mimarisi Dökümanı
```
Başlık: Design and document system architecture
Atanan: @emre (PM) + @mehmet (Network)
Priority: High
Sprint: Sprint 1
Labels: architecture, documentation

Açıklama:
Detaylı mimari tasarım dökümanı oluştur:

**Katmanlar**:
1. UI Layer (React Native screens)
2. Business Logic (Message manager, AI engine, Location service)
3. Network Layer (BLE mesh, WiFi Direct, Routing)
4. Data Layer (SQLite, AsyncStorage)

**Diyagramlar**:
- [ ] Component diagram (draw.io veya Excalidraw)
- [ ] Data flow diagram (kullanıcı mesaj gönderdiğinde ne olur?)
- [ ] Network topology (mesh network nasıl çalışır?)
- [ ] State management (Zustand store'ları)

**Deliverable**:
`docs/architecture/system-design.md`

Kabul Kriterleri:
✅ 4 katman detaylı açıklanmış
✅ Görsel diyagramlar mevcut
✅ Tech stack kararları belgelenmiş

Tahmini Süre: 8 saat
```

---

#### Issue #8: AI Message Classification Dataset Hazırlama
```
Başlık: Prepare Turkish disaster message dataset for AI training
Atanan: @ayse (AI Engineer)
Priority: Medium
Sprint: Sprint 1
Labels: ai-ml, dataset, turkish

Açıklama:
AI modelini fine-tune etmek için Türkçe veri seti hazırla:

**Kategoriler**:
- Medical (Tıbbi yardım: "AB+ kan grubu gerekli")
- Emergency (Acil: "Enkaz altındayım")
- Location (Konum: "Toplanma noktasındayım")
- Need (İhtiyaç: "Su ve battaniye lazım")
- Info (Bilgi: "Durumdayız, endişelenmeyin")

**Veri Toplama**:
- [ ] 2023 depreminden Twitter/sosyal medya mesajları (100+ örnek)
- [ ] Simüle edilmiş acil durum mesajları (50+ örnek)
- [ ] Her kategori için 30+ örnek

**Format**:
```json
{
  "message": "AB+ kan grubu acil gerekli, Hatay Antakya",
  "category": "Medical",
  "urgency": 0.95,
  "language": "tr"
}
```

**Deliverable**:
`data/training/disaster-messages-tr.json`

Kabul Kriterleri:
✅ 150+ mesaj toplanmış
✅ 5 kategoriye balanced dağılmış
✅ JSON formatında hazır

Tahmini Süre: 6 saat
```

---

#### Issue #9: Offline Map Tiles Stratejisi
```
Başlık: Research offline map solution (OpenStreetMap tiles)
Atanan: @ali (Mobile Developer)
Priority: Medium
Sprint: Sprint 1
Labels: research, maps, offline

Açıklama:
Offline harita çözümü araştır:

**Seçenekler**:
- [ ] react-native-maps + cached tiles
- [ ] Mapbox Offline SDK
- [ ] OpenStreetMap mbtiles

**Test**:
- [ ] Türkiye haritası boyutu (zoom level 8-16)
- [ ] İndirme süresi
- [ ] Depolama (kaç GB?)
- [ ] Offline rendering performance

**Deliverable**:
`docs/research/offline-maps-solution.md`

Kabul Kriterleri:
✅ Çözüm seçilmiş
✅ Boyut hesaplamaları yapılmış
✅ Test app oluşturulmuş

Tahmini Süre: 8 saat
```

---

### Hafta 3 (11-17 Kasım) - Prototip

#### Issue #10: BLE Mesajlaşma Proof of Concept
```
Başlık: Build BLE messaging proof-of-concept (2 devices)
Atanan: @mehmet (Network Engineer)
Priority: High
Sprint: Sprint 1
Labels: prototype, ble, networking

Açıklama:
2 cihaz arası basit BLE mesajlaşma app'i yap:

**Özellikler**:
- [ ] Device discovery (scan nearby BLE devices)
- [ ] Connect to peer
- [ ] Send text message
- [ ] Receive and display message
- [ ] Disconnect

**Test**:
- [ ] 2 fiziksel Android cihazla test et
- [ ] Range test (kaç metre?)
- [ ] Message latency ölç (<2 saniye hedef)

**Deliverable**:
`prototypes/ble-messenger/` klasöründe kod + README

Kabul Kriterleri:
✅ 2 cihaz mesaj alışverişi yapabiliyor
✅ Code GitHub'da
✅ Video demo (30 saniye)

Tahmini Süre: 12 saat
```

---

#### Issue #11: AI Model Integration Proof of Concept
```
Başlık: Integrate TinyLlama model into React Native (PoC)
Atanan: @ayse (AI Engineer)
Priority: High
Sprint: Sprint 1
Labels: prototype, ai-ml, onnx

Açıklama:
ONNX Runtime ile AI modeli entegre et:

**Adımlar**:
- [ ] TinyLlama 1.1B modelini 4-bit quantize et
- [ ] ONNX formatına çevir (.onnx dosyası)
- [ ] react-native-onnxruntime kütüphanesi kur
- [ ] Basit test app: "Bu mesaj hangi kategori?"

**Test Mesajları**:
- "AB+ kan grubu gerekli" → Medical
- "Enkaz altındayım yardım" → Emergency
- "Durumdayız" → Info

**Performans**:
- [ ] Inference time <1 saniye
- [ ] Model size <700MB

**Deliverable**:
`prototypes/ai-classifier/` + demo video

Kabul Kriterleri:
✅ AI model çalışıyor
✅ Türkçe mesaj kategorize ediyor
✅ Performance kabul edilebilir

Tahmini Süre: 16 saat
```

---

#### Issue #12: Sprint 1 Review & Retrospective Dökümanı
```
Başlık: Conduct Sprint 1 review and retrospective
Atanan: @emre (PM)
Priority: Medium
Sprint: Sprint 1
Labels: sprint-review, retrospective

Açıklama:
Sprint 1 sonunda review meeting organize et:

**Sprint Review** (15:00-16:00):
- [ ] Her issue demo et (prototype'lar göster)
- [ ] Tamamlananları listele
- [ ] Tamamlanamayanları listele (neden?)

**Retrospective** (16:00-17:00):
- [ ] What went well? (iyi gidenler)
- [ ] What can be improved? (geliştirilebilir)
- [ ] Action items for Sprint 2

**Deliverable**:
`docs/sprints/sprint-1-review.md`

Kabul Kriterleri:
✅ Meeting yapılmış
✅ Notlar alınmış
✅ Sprint 2 için aksiyonlar belirlenmiş

Tahmini Süre: 3 saat
```

---

## 📊 Sprint 1 Özet

**Toplam Issue**: 12  
**Toplam Tahmini Süre**: ~100 saat  
**Ekip**: 5 kişi × 3 hafta × 40 saat/hafta = 600 saat mevcut  
**Sprint Yoğunluğu**: %17 (rahat başlangıç)

### Issue Dağılımı
- **Emre (PM)**: 4 issue (Altyapı, planning, mimari, review)
- **Ayşe (AI)**: 3 issue (Model araştırma, dataset, prototip)
- **Mehmet (Network)**: 3 issue (BLE araştırma, mimari, prototip)
- **Fatma (UI/UX)**: 1 issue (Wireframe'ler)
- **Ali (Mobile)**: 2 issue (RN döküman, offline maps)

---

## ✅ Sprint Başarı Kriterleri

Sprint 1 sonunda elimizde olmalı:
1. ✅ Teknoloji kararları alınmış (AI model, BLE kütüphanesi, map çözümü)
2. ✅ Mimari tasarım tamamlanmış
3. ✅ 2 çalışan prototip (BLE messenger + AI classifier)
4. ✅ Wireframe'ler hazır
5. ✅ Firebase altyapısı kurulu

**Sprint hedefi**: Proje fizibilitesini kanıtla! ✨

---

**Hazırlayan**: Emre (PM)  
**Tarih**: 26 Ekim 2025  
**Sprint Başlangıcı**: 28 Ekim 2025 (Pazartesi)
