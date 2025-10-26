# 🎬 MESH112 Proje Ön Hazırlık - 4 Haftalık Plan

> **Durum**: Ekip henüz toplanmadı, proje altyapısı kurulacak  
> **Süre**: 4 hafta (28 Ekim - 24 Kasım 2025)  
> **Amaç**: Ekip geldiğinde projeye hemen başlayabilsin

---

## 📅 Haftalık Plan

### 🗓️ Hafta 1 (28 Eki - 3 Kas): Ekip Toplama & Altyapı

#### Öncelik 1: Ekip Oluşturma
- [ ] **Kişi 2 (AI/ML Engineer)** - Aday bul ve davet et
  - Kriterler: Python, TensorFlow/PyTorch, NLP tecrübesi
  - Teklif: TÜBİTAK 2204 proje üyeliği
  - İletişim: Discord/WhatsApp/LinkedIn
  
- [ ] **Kişi 3 (Network Engineer)** - Aday bul ve davet et
  - Kriterler: Mesh networking, BLE/WiFi, Protocol bilgisi
  - Teklif: Patent çıkarma fırsatı
  
- [ ] **Kişi 4 (UI/UX Designer)** - Aday bul ve davet et
  - Kriterler: Figma, Mobile UI, Emergency design tecrübesi
  - Portfolio kontrol
  
- [ ] **Kişi 5 (Mobile Developer)** - Aday bul ve davet et
  - Kriterler: React Native, iOS+Android, Published app
  - GitHub profili incelemesi

#### Öncelik 2: İletişim Altyapısı (Tek Başına)
- [x] ✅ Discord sunucusu kuruldu
- [x] ✅ GitHub repository oluşturuldu
- [ ] **Discord iyileştirmeleri**:
  - [ ] Özel emoji'ler ekle (🆘 SOS, 🩸 Blood, 📡 Mesh)
  - [ ] Karşılama mesajı bot'u kur
  - [ ] Role-based kanal izinleri ayarla
  - [ ] Voice channel'lar için quality ayarları
  
- [ ] **GitHub iyileştirmeleri**:
  - [ ] Issue templates oluştur
  - [ ] PR template oluştur
  - [ ] CODEOWNERS dosyası ekle
  - [ ] GitHub Discussions aktif et

#### Öncelik 3: Döküman Hazırlığı
- [x] ✅ Proje planı (PROJE_PLANI.md)
- [x] ✅ Workflow guide (WORKFLOW_GUIDE.md)
- [ ] **Yeni dökümanlar**:
  - [ ] TEAM_ROLES.md - Her kişinin rol ve sorumlulukları
  - [ ] TECH_STACK_DECISIONS.md - Neden bu teknolojileri seçtik?
  - [ ] GETTING_STARTED.md - İlk 24 saat rehberi

---

### 🗓️ Hafta 2 (4-10 Kas): Ekip Onboarding & Tooling

#### Öncelik 1: Ekip Entegrasyonu
- [ ] **Kickoff Meeting Organize Et** (Discord sesli)
  - Tarih: İlk 4 kişi toplandığında
  - Ajanda:
    1. Proje tanıtımı (15 dk)
    2. Takım tanışması (10 dk)
    3. Rol ve sorumluluklar (15 dk)
    4. Tooling walkthrough (20 dk)
    5. Soru-cevap (10 dk)
  
- [ ] **1-on-1 Görüşmeler**
  - Her kişiyle 30 dakikalık görüşme
  - Beklentiler, tecrübeler, çalışma saatleri
  - Notları al: `docs/team/onboarding-notes.md`

#### Öncelik 2: GitHub Organization Setup
- [ ] **frambuaz-crew organization ayarları**:
  - [ ] Team'ler oluştur:
    - @mesh112-leads (PM + Tech Lead)
    - @mesh112-developers (Tüm ekip)
    - @mesh112-designers (UI/UX)
  - [ ] Repository izinleri düzenle
  - [ ] Security policies ekle
  - [ ] Code scanning aktif et (Dependabot)

#### Öncelik 3: Development Environment
- [ ] **Geliştirme ortamı hazırlığı**:
  - [ ] .editorconfig oluştur
  - [ ] .prettierrc oluştur
  - [ ] ESLint config hazırla
  - [ ] VS Code workspace settings
  - [ ] Recommended extensions listesi

---

### 🗓️ Hafta 3 (11-17 Kas): Araştırma & Prototip Planlama

#### Öncelik 1: Teknoloji Araştırma Görevleri Dağıt
- [ ] **Ekip toplantısı**: Araştırma görevleri
  - AI Engineer → AI model seçimi
  - Network Engineer → BLE kütüphaneleri
  - Mobile Developer → React Native setup
  - UI/UX Designer → Competitor analysis

- [ ] **Araştırma template'i hazırla**:
  ```markdown
  ## Araştırma: [Konu]
  **Araştıran**: [İsim]
  **Tarih**: [TT.AA.YYYY]
  
  ### Seçenekler
  1. Seçenek A
     - Artıları:
     - Eksileri:
  2. Seçenek B
     ...
  
  ### Öneri
  [Seçenek X] kullanmalıyız çünkü...
  
  ### Benchmark Sonuçları
  ...
  ```

#### Öncelik 2: Firebase & Backend Setup
- [ ] **Firebase projesi kur**:
  - [ ] Authentication (Email/Password, Google)
  - [ ] Firestore Database (kullanıcı profilleri için)
  - [ ] Storage (profil fotoları)
  - [ ] Cloud Functions (opsiyonel bildirimler)
  - [ ] google-services.json hazırla

- [ ] **Backend altyapısı** (opsiyonel):
  - [ ] Node.js + Express boilerplate
  - [ ] PostgreSQL veya MongoDB seçimi
  - [ ] API authentication (JWT)
  - [ ] Swagger/OpenAPI dökümanı

#### Öncelik 3: Design System Başlangıcı
- [ ] **Figma workspace kurulumu**:
  - [ ] Figma team oluştur (Free plan - 3 proje)
  - [ ] Design system starter kit
  - [ ] Color palette (emergency red, safe green, info blue)
  - [ ] Typography (accessibility için büyük fontlar)
  - [ ] Component library başlangıcı

---

### 🗓️ Hafta 4 (18-24 Kas): İlk Sprint Hazırlığı

#### Öncelik 1: Sprint Infrastructure
- [ ] **GitHub Projects setup**:
  - [ ] Sprint 1 milestone oluştur
  - [ ] Issue templates test et
  - [ ] Velocity tracking için field'lar ekle
  - [ ] Automation rules (To Do → In Progress)

- [ ] **Sprint planning hazırlığı**:
  - [ ] Sprint 1 hedeflerini belirle
  - [ ] User stories yaz
  - [ ] Story points tahmin et
  - [ ] Dependency map çıkar

#### Öncelik 2: CI/CD Pipeline
- [ ] **GitHub Actions workflows**:
  - [ ] Lint & Type check
  - [ ] Unit test runner
  - [ ] Build Android APK
  - [ ] Build iOS IPA (macOS runner gerekli)
  - [ ] Deploy to Firebase (staging)

#### Öncelik 3: İlk Sprint Planning Meeting
- [ ] **25 Kasım Pazartesi - Sprint 1 Planning**:
  - Ajanda hazırla
  - Sprint goals belirle
  - Issue'ları oluştur
  - Ekip commitment al

---

## 🎯 4 Hafta Sonunda Hedef Durum

### ✅ Ekip
- 5 kişilik ekip tam
- Herkes Discord, GitHub, Figma'ya erişebiliyor
- Roller ve sorumluluklar net

### ✅ Altyapı
- Discord + GitHub + Figma entegre çalışıyor
- Development environment hazır
- CI/CD pipeline çalışıyor

### ✅ Planlama
- Sprint 1 hazır (25 Kasım başlangıç)
- İlk 3 haftalık roadmap net
- Teknoloji kararları alınmış

### ✅ Motivasyon
- Ekip heyecanlı 🚀
- İlk demo hedefi belirlendi
- Takım ruhu oluşmuş

---

## 📋 Haftalık Checklist Format

Her hafta sonunda kontrol et:

```markdown
### Hafta X Review (TT Kasım)

#### Tamamlananlar ✅
- [x] Ekip üyesi X katıldı
- [x] Discord iyileştirmeleri yapıldı
- [x] ...

#### Eksik Kalanlar ⏳
- [ ] Ekip üyesi Y henüz bulunamadı
- [ ] Firebase setup yarım kaldı

#### Gelecek Hafta Hedefleri 🎯
- [ ] ...
```

---

## 🆘 Risk Yönetimi

### Risk 1: Ekip Üyesi Bulunamıyor
**Çözüm**:
- LinkedIn'de aktif ilan
- Üniversite kulüplerinden duyuru
- Profesörlerden referans
- En kötü: Roller birleştir (PM + Mobile Dev)

### Risk 2: Tooling Öğrenme Süresi Uzuyor
**Çözüm**:
- 1-on-1 eğitim seansları
- Video tutorial'lar hazırla
- Pair programming ile öğret

### Risk 3: 4 Hafta Yetmezse
**Çözüm**:
- Sprint 1'i 4 haftaya uzat
- MVP kapsamını daralt
- Kritik olmayan özellikleri Sprint 2'ye ertele

---

**Hazırlayan**: Emre (Kişi 1 - PM)  
**Başlangıç**: 28 Ekim 2025  
**Sprint 1 Başlangıcı**: 25 Kasım 2025

**Not**: Bu plan esnek! Ekip erken toplanırsa hızlanırız, geç olursa esneklik gösteririz.
