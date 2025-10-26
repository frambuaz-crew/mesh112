# 🔄 MESH112 Git Workflow Eğitim Rehberi

> **Hedef Kitle**: Tüm takım üyeleri (Kişi 1-5)  
> **Süre**: 30 dakika okuma + 1 saat pratik  
> **Önkoşul**: Git temel bilgisi, GitHub hesabı

---

## 📋 İçindekiler

1. [Workflow'a Hızlı Bakış](#workflow-a-hızlı-bakış)
2. [Branch Yapısı](#branch-yapısı)
3. [Günlük Geliştirme Döngüsü](#günlük-geliştirme-döngüsü)
4. [Pull Request Süreci](#pull-request-süreci)
5. [Haftalık Sprint Döngüsü](#haftalık-sprint-döngüsü)
6. [Git Komutları Cheat Sheet](#git-komutları-cheat-sheet)
7. [Sık Karşılaşılan Sorunlar](#sık-karşılaşılan-sorunlar)
8. [Best Practices](#best-practices)

---

## 🚀 Workflow'a Hızlı Bakış

### Bizim Sistemimiz: GitFlow

```
main (Production)           ─────●────────────●─────────────●──────→
                                  ↑            ↑             ↑
                                  │ (Cuma)    │ (Cuma)      │ (Cuma)
                                  │            │             │
develop (Staging)           ──●──●──●──●──●──●──●──●──●──●──●──●──→
                               ↑  ↑  ↑  ↑  ↑  ↑  ↑  ↑  ↑  ↑  ↑  ↑
                               │  │  │  │  │  │  │  │  │  │  │  │
feature/* (Geliştirme)      ●─●  │  │  ●─●  │  │  ●────●  │  │  ●─●
                                 │  │       │  │           │  │
                              ●──●  │    ●──●  │        ●──●  │
                                    │           │              │
                                 ●──●        ●──●           ●──●
```

### 3 Seviyeli Sistem

| Branch Tipi | Amacı | Kimler Push Edebilir | Merge Sıklığı |
|-------------|-------|----------------------|---------------|
| `main` | **Production** - Canlı uygulamanın kodu | ❌ Sadece PR (PM onayı) | Haftalık (Cuma) |
| `develop` | **Staging** - Test edilmiş güncel kod | ❌ Sadece PR (1 kişi onayı) | Günlük (her gün) |
| `feature/*` | **Development** - Kişisel geliştirmeler | ✅ Kendi branch'inize serbestçe | Görev bitince |

---

## 🌳 Branch Yapısı

### 1. Main Branch (Ana Dal)
- **Amaç**: Production-ready kod (App Store/Play Store'a gidebilecek kalite)
- **Merge Zamanı**: Her sprint sonunda (Cuma günleri)
- **Koruma**: 
  - ✅ 2 kişi onayı zorunlu
  - ✅ Tüm testler geçmeli
  - ✅ Sadece `develop`'tan PR kabul edilir

### 2. Develop Branch (Geliştirme Dalı)
- **Amaç**: Günlük geliştirmelerin birleştiği yer
- **Merge Zamanı**: Her feature tamamlandığında (günlük)
- **Koruma**:
  - ✅ 1 kişi onayı zorunlu
  - ✅ Testler geçmeli
  - ✅ Sadece `feature/*` branch'lerinden PR kabul edilir

### 3. Feature Branches (Özellik Dalları)
- **İsimlendirme**: `feature/<kişi-ismi>/<görev-açıklaması>`
- **Örnekler**:
  ```
  feature/emre/ble-scanning-logic
  feature/ayse/ai-message-classification
  feature/mehmet/map-sos-markers
  feature/fatma/profile-blood-type-ui
  feature/ali/mesh-routing-algorithm
  ```
- **Ömür**: Görev başlangıcından PR merge'ine kadar (1-3 gün)

---

## 🔄 Günlük Geliştirme Döngüsü

### Sabah Rutini (09:00 Daily Standup Sonrası)

#### Adım 1: Yeni Görev Başlatma
```powershell
# 1. Develop branch'i güncel hale getirin
git checkout develop
git pull origin develop

# 2. Yeni feature branch oluşturun
git checkout -b feature/emre/ble-connection-manager

# 3. Çalışmaya başlayın! 🎉
```

#### Adım 2: Gün İçi Geliştirme
```powershell
# Düzenli olarak commit atın (her mantıklı değişiklikte)
git add .
git commit -m "feat: add BLE device discovery logic"

# Kendi branch'inize push edin (yedekleme + görünürlük)
git push origin feature/emre/ble-connection-manager
```

**💡 İyi Commit Mesajları**:
```
✅ feat: add GPS location tracking service
✅ fix: resolve BLE connection timeout issue
✅ perf: optimize message deduplication algorithm
✅ docs: update API documentation for mesh routing

❌ update code
❌ changes
❌ asdasd
```

#### Adım 3: Develop'taki Güncellemeleri Almak
```powershell
# Başkaları develop'a merge etmişse, güncellemeleri alın
git checkout develop
git pull origin develop

# Kendi branch'inize geri dönün ve develop'ı merge edin
git checkout feature/emre/ble-connection-manager
git merge develop

# Conflict varsa çözün, yoksa devam edin
git push origin feature/emre/ble-connection-manager
```

### Akşam Rutini (Görev Tamamlandığında)

#### Adım 4: Pull Request Açma
```powershell
# Son kontrol: testler çalışıyor mu?
npm test

# Son commit ve push
git add .
git commit -m "feat: complete BLE connection manager implementation"
git push origin feature/emre/ble-connection-manager

# Şimdi GitHub'a gidin ve PR açın! 👇
```

---

## 🔀 Pull Request Süreci

### 1. GitHub'da PR Açma

**URL**: https://github.com/frambuaz-crew/mesh112/pulls

#### Yeni PR Butonu
```
feature/emre/ble-connection-manager  →  develop
```

#### PR Şablonu (Her zaman doldurun!)
```markdown
## 🎯 Görev
Sprint 1, Hafta 1: BLE Connection Manager Implementation

## 🔨 Değişiklikler
- BLE device scanning logic eklendi
- Connection timeout handling
- Auto-reconnect mechanism
- 50 unit test eklendi

## ✅ Test Edildi
- [x] Unit testler geçti (50/50)
- [x] Manuel BLE device ile test edildi
- [x] Battery impact ölçüldü (<2% per hour)
- [ ] iOS simulator'de test (BLE yok, atlandı)

## 📱 Ekran Görüntüleri
(Varsa UI değişiklikleri için)

## 📝 Notlar
- react-native-ble-plx kütüphanesi kullanıldı
- Android API 31+ için permission handling eklendi
- iOS için Info.plist'e NSBluetoothAlwaysUsageDescription eklenmeli
```

### 2. PR Checklist (Göndermeden Önce)

- [ ] ✅ Kod derlenebiliyor (`npm run build`)
- [ ] ✅ Testler geçiyor (`npm test`)
- [ ] ✅ Linter hataları yok (`npm run lint`)
- [ ] ✅ Yorum satırları temizlendi (console.log, debugger)
- [ ] ✅ Gereksiz dosyalar commitlenmemiş (.env, node_modules)
- [ ] ✅ Commit mesajları anlamlı
- [ ] ✅ PR description dolu

### 3. Code Review Süreci

#### Reviewer'ın Sorumluluğu
- **Kim Review Eder?**: 
  - `develop` PR'lar → Aynı rolden veya PM (1 kişi yeterli)
  - `main` PR'lar → 2 farklı kişi (biri mutlaka PM)

#### Review Kriterleri
```markdown
✅ Kod okunaklı ve anlaşılır mı?
✅ Best practice'lere uygun mu?
✅ Testler yeterli mi?
✅ Performance etkileri düşünülmüş mü?
✅ Offline-first prensibi korunmuş mu?
✅ Battery optimization göz önünde bulundurulmuş mu?
✅ Türkçe karakter desteği var mı (ı, ş, ğ)?
```

#### Review Yorumları
```
🟢 LGTM (Looks Good To Me): Onay ver
🟡 Comment: Öneri/soru (blocker değil)
🔴 Request Changes: Düzeltme gerekli (merge engellenir)
```

### 4. Merge Etme

#### Develop Branch'e Merge
```
Approve → Merge Pull Request → Squash and Merge
```
- **Squash and Merge**: Tüm commitler tek commit'e birleşir (temiz tarihçe)
- **Delete Branch**: PR merge olduktan sonra feature branch silinir

#### Main Branch'e Merge (Haftalık)
```
develop → main (Sadece Cuma günleri)
```
- **PM yapar**: Sprint Review Meeting sonrası
- **Tag eklenir**: v1.0.0-sprint-1 gibi
- **Release Notes**: Haftalık değişiklikler yazılır

---

## 📅 Haftalık Sprint Döngüsü

### Pazartesi (Sprint Başlangıcı)
```
09:00 - Sprint Planning Meeting
10:00 - GitHub Issues atanır (Projects board'dan)
10:30 - Herkes kendi feature branch'ini açar
11:00 - Geliştirme başlar
```

### Salı-Çarşamba-Perşembe (Aktif Geliştirme)
```
09:00 - Daily Standup (15 dk)
09:15 - Geliştirme
12:00 - Öğle arası
13:00 - Geliştirme devam
17:00 - PR review zamanı (birbirinin kodunu okuma)
18:00 - Develop branch'e merge edilen PR'lar
```

### Cuma (Sprint Teslimi)
```
09:00 - Daily Standup
10:00 - Son PR'lar merge edilir (develop'a)
14:00 - Sprint Review Meeting (demo + retrospective)
15:00 - PM develop → main PR açar
16:00 - Develop → Main merge (2 onay sonrası)
16:30 - Release tag eklenir (v1.0.0-sprint-1)
17:00 - Sprint kapanır ✅
```

---

## 📖 Git Komutları Cheat Sheet

### Temel Komutlar

```powershell
# Mevcut branch'i görme
git branch

# Branch değiştirme
git checkout develop

# Yeni branch oluşturup geçiş
git checkout -b feature/emre/new-feature

# Değişiklikleri görme
git status

# Dosya ekleme
git add src/components/NewComponent.tsx
git add .  # Tüm değişiklikler

# Commit atma
git commit -m "feat: add new component"

# Remote'a gönderme
git push origin feature/emre/new-feature

# Remote'dan çekme
git pull origin develop

# Branch silme (local)
git branch -d feature/emre/old-feature

# Branch silme (remote)
git push origin --delete feature/emre/old-feature
```

### İleri Seviye

```powershell
# Son commit mesajını değiştirme
git commit --amend -m "feat: corrected commit message"

# Develop'taki güncellemeleri kendi branch'ine alma
git checkout feature/emre/my-feature
git merge develop

# Conflict çözme sonrası
git add .
git commit -m "merge: resolve conflicts with develop"

# Son commit'i geri alma (dosyalar kalır)
git reset --soft HEAD~1

# Tüm değişiklikleri geri alma (DİKKATLİ!)
git reset --hard HEAD

# Stash (geçici saklama)
git stash  # Değişiklikleri sakla
git stash pop  # Sakladığın değişiklikleri geri getir

# Log görme
git log --oneline
git log --graph --oneline --all  # Grafik halinde
```

---

## 🚨 Sık Karşılaşılan Sorunlar

### Sorun 1: Merge Conflict
**Belirtiler**: `CONFLICT (content): Merge conflict in src/...`

**Çözüm**:
```powershell
# 1. Conflict'li dosyaları aç (VS Code otomatik gösterir)
# 2. Conflict marker'ları bul:
<<<<<<< HEAD
// Senin kodun
=======
// Develop'taki kod
>>>>>>> develop

# 3. Doğru kodu seç veya ikisini birleştir
# 4. Marker'ları sil
# 5. Kaydet ve commit et
git add .
git commit -m "merge: resolve conflicts with develop"
git push
```

### Sorun 2: "Branch is X commits behind develop"
**Çözüm**:
```powershell
git checkout feature/emre/my-feature
git merge develop
git push
```

### Sorun 3: Yanlış Branch'e Commit Attım!
**Çözüm**:
```powershell
# 1. Commit'i kopyala (hash'i al)
git log --oneline  # Örn: a1b2c3d

# 2. Doğru branch'e geç
git checkout feature/emre/correct-branch

# 3. Commit'i buraya taşı
git cherry-pick a1b2c3d

# 4. Yanlış branch'ten sil
git checkout wrong-branch
git reset --hard HEAD~1
```

### Sorun 4: PR'ım CI/CD Testlerinden Geçmiyor
**Kontrol Listesi**:
```powershell
# Local'de testleri çalıştır
npm test

# Linter hataları
npm run lint

# TypeScript hataları
npm run type-check

# Build çalışıyor mu?
npm run build
```

### Sorun 5: "Protected Branch" Hatası
**Neden**: `main` ve `develop` branch'lerine direkt push engellenmiştir.

**Çözüm**: Her zaman PR üzerinden merge edin!

---

## ✨ Best Practices

### 1. Commit Sıklığı
```
✅ Her mantıklı değişiklikte commit atın
✅ Günde 3-5 commit ideal
❌ Gün sonunda tek bir dev commit atma
❌ Her satır değişikliğinde commit atma
```

### 2. Branch İsimlendirme
```
✅ feature/emre/ble-scanning
✅ feature/ayse/ai-priority-model
✅ fix/mehmet/map-crash-bug
❌ emre-branch
❌ test123
❌ asdasd
```

### 3. PR Boyutu
```
✅ Küçük, odaklanmış PR'lar (200-400 satır)
✅ Tek bir feature/bug fix
❌ 1000+ satır "everything" PR
❌ 10 farklı feature bir arada
```

### 4. Code Review Hızı
```
✅ PR açıldıktan sonra 24 saat içinde review
✅ Blocker yorumlar için aynı gün çözüm
❌ Günlerce bekletmek
```

### 5. Merge Zamanlaması
```
✅ Develop'a günlük merge (çalışma saatleri içinde)
✅ Main'e sadece Cuma (sprint sonunda)
❌ Gece yarısı main'e merge
❌ Hafta ortası main'e merge
```

---

## 📚 Ek Kaynaklar

### Takım İçi Dökümanlar
- [PROJE_PLANI.md](./PROJE_PLANI.md) - 18 haftalık plan
- [SETUP_CHECKLIST.md](./SETUP_CHECKLIST.md) - Proje altyapısı
- [CONTRIBUTING.md](./CONTRIBUTING.md) - Katkı kuralları
- [.github/copilot-instructions.md](./.github/copilot-instructions.md) - AI agent rehberi

### Harici Kaynaklar
- [Git Documentation](https://git-scm.com/doc)
- [GitFlow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- [GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Semantic Versioning](https://semver.org/)

---

## 🎓 Pratik Alıştırma

### Senaryo: İlk Feature'ınızı Geliştirin

**Görev**: Basit bir "Hello MESH112" ekranı oluşturun

#### Adımlar
```powershell
# 1. Develop'ı güncelleyin
git checkout develop
git pull origin develop

# 2. Feature branch açın
git checkout -b feature/<adiniz>/hello-screen

# 3. Dosya oluşturun
mkdir src/screens
echo "import React from 'react'; export default function HelloScreen() { return <Text>Hello MESH112</Text>; }" > src/screens/HelloScreen.tsx

# 4. Commit atın
git add .
git commit -m "feat: add hello screen component"

# 5. Push edin
git push origin feature/<adiniz>/hello-screen

# 6. GitHub'da PR açın
# https://github.com/frambuaz-crew/mesh112/pulls

# 7. PM'den review isteyin (Slack'te @emre)

# 8. Onaylandıktan sonra merge edin

# 9. Branch'i silin (GitHub otomatik sorar)

# 10. Local'de temizlik
git checkout develop
git pull origin develop
git branch -d feature/<adiniz>/hello-screen
```

**Beklenen Süre**: 15 dakika  
**Başarı Kriteri**: PR merge edildi ve develop'ta kodunuz görünüyor

---

## 🆘 Yardım

### Takım İçi Destek
- **Git Sorunları**: @emre (PM) - Slack
- **Merge Conflicts**: @mehmet (Network Engineer) - Slack
- **CI/CD Hataları**: @emre (PM) - Slack

### Acil Durum
```powershell
# Herşey karıştıysa, temiz başlangıç:
git stash  # Değişiklikleri sakla
git checkout develop
git pull origin develop
git checkout -b feature/<adiniz>/new-clean-branch
git stash pop  # Değişiklikleri geri getir
```

---

**Son Güncelleme**: 26 Ekim 2025  
**Versiyon**: 1.0  
**Hazırlayan**: Emre (Proje Yöneticisi)

**Sorular?** Slack'te #mesh112-dev kanalında sorun! 🚀
