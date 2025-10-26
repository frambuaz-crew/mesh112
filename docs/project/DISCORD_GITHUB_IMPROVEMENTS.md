# 🚀 Discord & GitHub İyileştirmeler - Ekip Gelmeden Yapılacaklar

> **Hedef**: Ekip geldiğinde profesyonel, hazır bir ortam bulsun  
> **Süre**: 1-2 hafta  
> **Sorumluluk**: Emre (PM)

---

## 🎮 DISCORD İYİLEŞTİRMELERİ

### 1. Özel Emoji'ler Ekle (30 dakika)

**Neden?** Türkçe acil durum terimleri için emoji yok, kendimiz ekleyelim.

#### Eklenecek Emoji'ler
```
🆘 :sos_mesh:          → SOS buton icon
🩸 :blood_type:        → Kan grubu
📡 :mesh_network:      → Mesh ağ ikonu
🔴 :critical:          → Kritik öncelik
🟡 :medium:            → Orta öncelik
🟢 :low:               → Düşük öncelik
✅ :task_done:         → Görev tamamlandı
🏗️ :in_progress:      → Üzerinde çalışılıyor
🐛 :bug_found:         → Bug bulundu
🎯 :sprint_goal:       → Sprint hedefi
🚀 :deployed:          → Production'a çıktı
⚡ :hotfix:            → Acil düzeltme
```

**Nasıl eklerim?**
```
1. Discord → MESH112 Team → Server Settings
2. Emoji → Upload Emoji
3. İsimleri yukarıdaki gibi ver
4. Test et: Discord'da :sos_mesh: yaz
```

**Emoji dosyaları nereden?**
- Flaticon.com (ücretsiz, credit ver)
- Emojipedia (kopyala-yapıştır)
- Canva'da kendin çiz (32x32px PNG)

---

### 2. Karşılama Mesajı Botu (45 dakika)

**Neden?** Yeni üye geldiğinde otomatik hoş geldin mesajı + rehber.

#### Seçenek A: Discord'un Kendi Özelliği (Ücretsiz)
```
Server Settings → Community → Welcome Screen

Karşılama Mesajı:
"
👋 Hoş geldin {user}!

📋 İlk adımlar:
1. #hoşgeldin kanalında kendini tanıt
2. Rolünü al: #roller kanalında react at
3. Dökümanları oku: https://github.com/frambuaz-crew/mesh112

Sorular? #genel kanalında sor!

🚨 MESH112 - Afet durumunda bağlantıyı sağla
"
```

#### Seçenek B: MEE6 Bot (Daha gelişmiş)
```
1. https://mee6.xyz/dashboard
2. Add to Server → MESH112 Team
3. Welcome Plugin aktif et
4. Custom mesaj yaz (yukarıdaki gibi)
5. #hoşgeldin kanalına gönder
```

---

### 3. Role-Based Kanal İzinleri (1 saat)

**Neden?** Hassas kanalları korumak, spam önlemek.

#### İzin Matrisi

| Kanal | @everyone | @Geliştirici | @PM |
|-------|-----------|--------------|-----|
| #duyurular | 👁️ Görür | 👁️ Görür | ✍️ Yazar |
| #genel | ✍️ Yazar | ✍️ Yazar | ✍️ Yazar |
| #mesh112-dev | ❌ Göremez | ✍️ Yazar | ✍️ Yazar |
| #sprint-planning | ❌ Göremez | 👁️ Görür | ✍️ Yazar |
| #github-updates | 👁️ Görür | 👁️ Görür | 👁️ Görür |

**Nasıl ayarlanır?**
```
1. Kanal ayarları (⚙️) → Permissions
2. @everyone rolünü seç → "View Channel" ❌ kapat
3. @Geliştirici rolünü ekle → İzinleri ayarla
4. @PM rolünü ekle → Tüm izinleri ver
```

---

### 4. Voice Channel Quality Ayarları (15 dakika)

**Neden?** Toplantılarda ses kalitesi kritik.

#### 🔊 Toplantı Odası Ayarları
```
Kanal ayarları → Overview

🎙️ Bitrate: 96kbps (maksimum - Free server)
👥 User Limit: 10 kişi
🎥 Video Quality: 720p
🔒 Permissions: 
   - Sadece @Geliştirici girebilir
   - @PM mute/unmute yetkisi var
```

#### 🔊 Pair Programming Odası
```
Bitrate: 64kbps (yeterli)
User Limit: 2 kişi (pair programming için)
Screen share: Aktif
```

---

### 5. Scheduled Events (Toplantı Hatırlatma) (30 dakika)

**Neden?** Daily standup'ları unutmamak için.

```
Server Settings → Events → Create Event

Event 1: Daily Standup
- Tarih: Her gün (Recurring)
- Saat: 09:00 (GMT+3 Türkiye)
- Konum: #daily-standup (metin kanalı)
- Açıklama: "Günlük 15 dakikalık standup. Dün/bugün/engeller."

Event 2: Sprint Planning
- Tarih: 2 haftada bir Pazartesi
- Saat: 14:00
- Konum: 🔊 Toplantı Odası
- Açıklama: "3 haftalık sprint hedeflerini belirleyelim"

Event 3: Sprint Review
- Tarih: 2 haftada bir Cuma
- Saat: 15:00
- Konum: 🔊 Toplantı Odası
- Açıklama: "Sprint tamamlananları demo + retrospective"
```

---

### 6. Forum Channels (Tartışma Konuları) (20 dakika)

**Neden?** Uzun tartışmalar thread'lerde daha düzenli.

```
GELİŞTİRME kategorisine sağ tık → Create Channel → Forum

Kanal adı: 💡 feature-discussions
Açıklama: "Her feature önerisi bir thread olarak açılır"

Tags oluştur:
- 🆕 New Idea
- 💬 Under Discussion
- ✅ Approved
- ❌ Rejected
- 🚀 Implemented
```

**Kullanım**:
```
Kullanıcı: "BLE mesajları şifrelensin mi?" thread'i açar
Ekip: Thread içinde tartışır
PM: Tag'i "Approved" yapar → Issue'ya çevrilir
```

---

### 7. Auto-Moderation (Spam Önleme) (15 dakika)

```
Server Settings → Safety Setup → AutoMod

Aktif et:
☑️ Block commonly flagged words
☑️ Block spam content (duplicate messages)
☑️ Timeout users sending too many messages (5+ mesaj/10 saniye)

Exceptions:
@Geliştirici ve @PM için kurallar geçerli değil
```

---

## 🐙 GITHUB İYİLEŞTİRMELERİ

### 1. Issue Templates (30 dakika)

**Neden?** Standart issue formatı → daha az eksik bilgi.

#### Template 1: Bug Report

**Dosya**: `.github/ISSUE_TEMPLATE/bug_report.yml`

```yaml
name: 🐛 Bug Report
description: Bir bug bildirin
title: "[BUG] "
labels: ["bug", "needs-triage"]
assignees: []

body:
  - type: markdown
    attributes:
      value: |
        ## 🐛 Bug Raporu
        Sorunu detaylı açıklayın.
  
  - type: textarea
    id: description
    attributes:
      label: Açıklama
      description: Bug ne yapıyor?
      placeholder: "SOS butonu tıklayınca uygulama çöküyor"
    validations:
      required: true
  
  - type: textarea
    id: steps
    attributes:
      label: Adımlar (Reproduce)
      description: Bug'ı tekrar yaratmak için:
      placeholder: |
        1. Ana ekrana git
        2. SOS butonuna tıkla
        3. Uygulama çöküyor
    validations:
      required: true
  
  - type: dropdown
    id: platform
    attributes:
      label: Platform
      options:
        - Android
        - iOS
        - Her ikisi
    validations:
      required: true
  
  - type: input
    id: version
    attributes:
      label: Uygulama Versiyonu
      placeholder: "v1.0.0-sprint-2"
  
  - type: textarea
    id: logs
    attributes:
      label: Loglar / Hata Mesajı
      description: Console output varsa buraya yapıştır
      render: shell
```

#### Template 2: Feature Request

**Dosya**: `.github/ISSUE_TEMPLATE/feature_request.yml`

```yaml
name: ✨ Feature Request
description: Yeni özellik öner
title: "[FEATURE] "
labels: ["enhancement"]

body:
  - type: textarea
    id: problem
    attributes:
      label: Problem
      description: Hangi sorunu çözüyor?
      placeholder: "Kullanıcılar gece karanlıkta ekranı göremiyorlar"
    validations:
      required: true
  
  - type: textarea
    id: solution
    attributes:
      label: Önerilen Çözüm
      description: Nasıl çözülmeli?
      placeholder: "Dark mode ekleyelim"
    validations:
      required: true
  
  - type: dropdown
    id: priority
    attributes:
      label: Öncelik
      options:
        - Critical (Acil)
        - High (Yüksek)
        - Medium (Orta)
        - Low (Düşük)
    validations:
      required: true
```

#### Template 3: Sprint Task

**Dosya**: `.github/ISSUE_TEMPLATE/sprint_task.yml`

```yaml
name: 🎯 Sprint Task
description: Sprint görevi oluştur
title: "[TASK] "
labels: ["sprint"]

body:
  - type: input
    id: sprint
    attributes:
      label: Sprint
      placeholder: "Sprint 1"
    validations:
      required: true
  
  - type: textarea
    id: description
    attributes:
      label: Görev Açıklaması
      placeholder: "Firebase Authentication entegrasyonu"
    validations:
      required: true
  
  - type: textarea
    id: checklist
    attributes:
      label: Checklist
      value: |
        - [ ] Adım 1
        - [ ] Adım 2
        - [ ] Adım 3
  
  - type: input
    id: estimate
    attributes:
      label: Tahmini Süre (saat)
      placeholder: "8"
  
  - type: dropdown
    id: assignee_role
    attributes:
      label: Rol
      options:
        - PM
        - AI Engineer
        - Network Engineer
        - UI/UX Designer
        - Mobile Developer
```

---

### 2. Pull Request Template (20 dakika)

**Dosya**: `.github/PULL_REQUEST_TEMPLATE.md`

```markdown
## 🎯 Ne Değişti?

<!-- PR'ın amacını özetle -->

Closes #<!-- Issue numarası -->

## 🔨 Değişiklikler

- [ ] Yeni özellik eklendi
- [ ] Bug düzeltildi
- [ ] Döküman güncellendi
- [ ] Test eklendi
- [ ] Refactoring yapıldı

## ✅ Checklist

Merge'den önce kontrol et:

- [ ] Kod derlenebiliyor (`npm run build`)
- [ ] Testler geçiyor (`npm test`)
- [ ] Linter hataları yok (`npm run lint`)
- [ ] TypeScript hataları yok (`npm run type-check`)
- [ ] Commit mesajları anlamlı
- [ ] Branch `develop`'tan oluşturuldu
- [ ] Conflict yok

## 📱 Test Edildi

- [ ] Android emulator
- [ ] iOS simulator
- [ ] Fiziksel cihaz (hangi model?)
- [ ] Offline mode
- [ ] Battery impact (<5% per hour)

## 📸 Ekran Görüntüleri

<!-- UI değişikliği varsa buraya ekle -->

## 🔗 İlgili Linkler

- Figma design: 
- API dökümanı:
- İlgili PR'lar:

## 💬 Notlar

<!-- Reviewer'ın bilmesi gereken özel durumlar -->
```

---

### 3. CODEOWNERS Dosyası (10 dakika)

**Neden?** Otomatik reviewer atama - yanlış kişi review etmesin.

**Dosya**: `.github/CODEOWNERS`

```plaintext
# MESH112 Code Owners
# Specific files/folders require approval from designated owners

# Default owner (tüm dosyalar için)
* @mehmetemrekayacan

# AI/ML kodu (sadece AI Engineer review eder)
/src/ai/ @ai-engineer-github-username
/models/ @ai-engineer-github-username
*.onnx @ai-engineer-github-username

# Networking kodu (sadece Network Engineer)
/src/networking/ @network-engineer-username
/src/bluetooth/ @network-engineer-username

# UI Components (sadece Designer + Mobile Dev)
/src/components/ @ui-designer-username @mobile-dev-username
/src/screens/ @ui-designer-username @mobile-dev-username

# Infrastructure (sadece PM)
/.github/ @mehmetemrekayacan
/docs/ @mehmetemrekayacan
docker-compose.yml @mehmetemrekayacan

# Backend API (PM + Backend varsa)
/backend/ @mehmetemrekayacan

# Package dependencies (PM approval gerekli)
package.json @mehmetemrekayacan
package-lock.json @mehmetemrekayacan
```

---

### 4. GitHub Discussions Aktif Et (5 dakika)

**Neden?** Uzun tartışmalar issue'da değil, Discussions'ta olmalı.

```
Repository → Settings → Features → ☑️ Discussions

Kategoriler oluştur:
📢 Announcements     → Proje duyuruları (PM only)
💡 Ideas             → Feature önerileri
🙏 Q&A               → Sorular (StackOverflow gibi)
🗳️ Polls             → Oylama (hangi teknoloji?)
📚 Knowledge Base    → How-to guides
```

**Kullanım örnekleri**:
```
Poll: "AI model için TinyLlama mı Phi-2 mi?"
Q&A: "React Native'de BLE background scanning nasıl yapılır?"
Idea: "Offline haritalar için mbtiles kullanılabilir mi?"
```

---

### 5. Branch Protection Rules (Güçlendirilmiş) (15 dakika)

**Şu an**: Basic protection  
**Hedef**: Enterprise-level protection

```
Settings → Branches → develop branch → Edit

☑️ Require a pull request before merging
  ☑️ Require approvals: 1
  ☑️ Dismiss stale reviews (kod değişince review geçersiz)
  ☑️ Require review from Code Owners

☑️ Require status checks to pass
  ☑️ Require branches to be up to date
  Status checks (CI/CD tamamlanınca):
    - ✅ lint
    - ✅ type-check
    - ✅ test
    - ✅ build

☑️ Require conversation resolution (tüm yorumlar çözülmeli)

☑️ Require linear history (clean git history)

☑️ Do not allow bypassing (PM bile kuralları atlayamaz)
```

**Main branch** için daha sıkı:
```
☑️ Require approvals: 2 (PM + başka biri)
☑️ Require signed commits (güvenlik)
☑️ Lock branch (emergency dışında kimse değiştiremesin)
```

---

### 6. GitHub Projects Automation (30 dakika)

**Neden?** Manuel sürükle-bırak yerine otomatik kolon değişimi.

```
Projects → MESH112 Development → ⚙️ Workflows

Workflow 1: Issue Oluşturulunca
- Tetikleyici: Issue created
- Aksiyon: Add to project → "To Do" kolonuna ekle

Workflow 2: PR Açılınca
- Tetikleyici: PR opened
- Aksiyon: Issue'yu "In Review" kolonuna taşı

Workflow 3: PR Merge Edilince
- Tetikleyici: PR merged
- Aksiyon: Issue'yu "Done" kolonuna taşı + kapat

Workflow 4: Sprint Bitti
- Tetikleyici: Manual (Cuma akşamı)
- Aksiyon: Tüm "Done" issue'ları arşivle
```

---

### 7. Security Scanning (15 dakika)

**Neden?** Güvenlik açıkları erken tespit edilmeli.

```
Settings → Code security and analysis

☑️ Dependabot alerts (npm paket güvenlik açıkları)
☑️ Dependabot security updates (otomatik güncelleme PR'ları)
☑️ Secret scanning (API key'ler commit edilmesin)
☑️ Code scanning (CodeQL - potential bugs)
```

**Test et**:
```
Yanlışlıkla API key commit et:
const FIREBASE_KEY = "AIzaSyABC123...";

→ GitHub otomatik uyarı verir: "Secret detected!"
```

---

## 📊 Tamamlanma Checklist

### Discord ✅
- [ ] Özel emoji'ler eklendi (12 adet)
- [ ] Karşılama mesajı aktif
- [ ] Kanal izinleri ayarlandı
- [ ] Voice quality optimize edildi
- [ ] Scheduled events oluşturuldu
- [ ] Forum channels eklendi
- [ ] Auto-moderation aktif

### GitHub ✅
- [ ] 3 issue template oluşturuldu
- [ ] PR template eklendi
- [ ] CODEOWNERS dosyası hazır
- [ ] Discussions aktif
- [ ] Branch protection güçlendirildi
- [ ] Projects automation kuruldu
- [ ] Security scanning aktif

---

## 🚀 Sonraki Adımlar

Bu iyileştirmeler tamamlandıktan sonra:

1. **Ekibi davet et** → Hazır ortamı görsünler
2. **Onboarding session** → Tool'ları tanıt
3. **İlk görevleri ata** → Araştırma issue'ları
4. **Sprint 1 planning** → 25 Kasım'da başla!

---

**Tahmini Tamamlanma Süresi**: 6-8 saat  
**Öncelik**: Ekip gelmeden önce mutlaka tamamla!

**Hazırlayan**: Emre (PM)  
**Tarih**: 26 Ekim 2025
