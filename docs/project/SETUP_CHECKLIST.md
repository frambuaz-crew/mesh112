# 🚀 MESH112 - Project Manager Setup Checklist

**Hazırlayan**: Emre (PM)  
**Tarih**: 26 Ekim 2025  
**Durum**: ⏳ Kurulum Aşamasında

Bu dokümandaki her adımı tamamladıkça checkboxları işaretleyin!

---

## ✅ Faz 1: Version Control & Code Repository (15 dakika)

### GitHub Organization & Repository

- [x] **Lokal Git Init** (✅ TAMAMLANDI)
- [x] **GitHub'da Organization Oluştur** (✅ TAMAMLANDI - frambuaz-crew)
- [x] **Repository Oluştur** (✅ TAMAMLANDI - mesh112)
- [x] **Lokal Repo'yu GitHub'a Bağla** (✅ TAMAMLANDI)
- [x] **Repository Settings Ayarları** (✅ Branch protection main + develop)
- [x] **Labels Oluştur** (✅ 23 label oluşturuldu)

---

## ✅ Faz 2: GitHub Projects Automation (30 dakika)

**NOT**: Issue templates kaldırıldı! Basit issue açıp, GitHub Projects automation ile yönetiyoruz.

### GitHub Projects Kurulumu

- [x] **GitHub Projects Oluştur** (✅ TAMAMLANDI - MESH112 Development)
- [ ] **Kolonları Yeniden Düzenle**
  - Backlog
  - To Do
  - In Progress
  - Review
  - Ready to Test
  - Done

- [ ] **Custom Fields Ekle**
  - [ ] Sprint (Select): Sprint 1, Sprint 2, Sprint 3, Sprint 4, Sprint 5, Sprint 6
  - [ ] Story Points (Number): 1, 2, 3, 5, 8, 13
  - [ ] Priority (Select): 🔴 High, 🟡 Medium, 🟢 Low
  - [ ] Assignee: Emre, Furkan, Oğuz, Hasan, Sümeyye

- [ ] **Automation Workflows Kur** (ÖNEMLİ!)
  - [ ] **Kural 1**: Yeni issue → Backlog
  - [ ] **Kural 2**: Assignee eklendi → In Progress
  - [ ] **Kural 3**: PR açıldı → Review
  - [ ] **Kural 4**: PR merged (develop) → Ready to Test
  - [ ] **Kural 5**: PR merged (main) → Done + Close issue

**Detaylı Kurulum**: `docs/guides/GITHUB_PROJECTS_AUTOMATION.md`
  - [ ] #2 GitHub organization configuration
  - [ ] #3 Slack workspace setup
  - [ ] #4 TÜBİTAK 2204 başvuru hazırlığı
  
  Kişi 2 (AI):
  - [ ] #5 TinyLlama vs Phi-2 benchmark
  - [ ] #6 Turkish disaster dataset research
  - [ ] #7 ONNX quantization tutorial
  - [ ] #8 Python environment setup
  
  (devam eden...)
  ```

### Seçenek B: Notion (ÜCRETSİZ - Alternatif)

**Neden?** Daha esnek dokümantasyon, güzel wiki, AI asistan

- [ ] **Notion Workspace Oluştur**
  - Notion.so → Sign up with GitHub
  - Workspace adı: "MESH112 Team"
  - Plan: **FREE** (unlimited pages, 10 guest'e kadar)
  - Ekip üyelerini davet et

- [ ] **Template Kurulumu**
  - Sol menü → Templates → "Product Roadmap"
  - Sayfalar oluştur:
    - 📋 Sprint Backlog
    - 📅 Project Timeline (Gantt chart)
    - 📝 Meeting Notes
    - 📚 Documentation Hub
    - 🐛 Bug Tracker

### Seçenek C: Jira (ÜCRETLİ - Profesyonel)

**Neden?** Enterprise-grade, sprint reporting, burndown charts

- [ ] **Jira Free Tier Kontrol**
  - Atlassian → Jira Software Free (10 user'a kadar)
  - Site adı: `mesh112.atlassian.net`
  - Project template: **Scrum**
  - Ekip üyelerini davet et

**Karar**: GitHub Projects (ücretsiz + entegre) ✅ ÖNERİLEN

---

## ✅ Faz 3: İletişim Kanalları (15 dakika)

### Discord Sunucusu (ÜCRETSİZ - ÖNERİLEN) ⭐

> **Neden Discord?** Slack Free 90 günlük mesaj geçmişi sınırı koyuyor, Pro $43.75/ay. Discord tamamen ücretsiz ve sınırsız!

- [ ] **Discord Sunucusu Oluştur**
  - discord.com → Giriş yap → "+" → Create My Own
  - Sunucu adı: `MESH112 Team`
  - Detaylı rehber: `DISCORD_SETUP.md`

- [ ] **Kategoriler ve Kanallar Oluştur**
  ```
  📁 BİLGİLENDİRME
     #hoşgeldin, #duyurular, #kaynaklar
  
  📁 GÜNLÜK İLETİŞİM
     #genel, #random, #daily-standup
  
  📁 GELİŞTİRME
     #mesh112-dev, #bug-reports, #feature-ideas, #github-updates
  
  📁 SPRINT YÖNETİMİ
     #sprint-planning, #sprint-review, #metrics
  
  📁 SESLİ KANALLAR
     🔊 Toplantı Odası, 🔊 Pair Programming
  ```

- [ ] **GitHub Webhook Entegrasyonu**
  - Discord: #github-updates → Ayarlar → Webhooks → New Webhook → Copy URL
  - GitHub: Settings → Webhooks → Add webhook → Paste Discord URL/github
  - Events: Pull requests, Pushes, Issues
  - Test et: Dummy PR aç, Discord'da bildirim gelsin

- [ ] **Roller ve İzinler**
  - @PM (Proje Yöneticisi) - Admin
  - @Developer (Tüm ekip üyeleri)
  - Roller: Server Settings → Roles → Create Role

- [ ] **Yararlı Botlar Ekle** (İsteğe Bağlı)
  - Reminder Bot (toplantı hatırlatmaları)
  - Poll Bot (oylama)
  - GitHub Bot (resmi Discord GitHub entegrasyonu)

**Alternatif**: Microsoft Teams (Office 365 varsa) veya Slack Pro ($43.75/ay)

---

## ✅ Faz 4: Dokümantasyon & Wiki (15 dakika)

### GitHub Wiki (ÜCRETSİZ)

- [ ] **Wiki'yi Aktifleştir**
  - Repository → Settings → Features → ✅ Wiki

- [ ] **İlk Sayfaları Oluştur**
  ```
  Home
  ├─ Getting Started
  ├─ Development Setup
  │  ├─ React Native Setup
  │  ├─ AI Model Setup
  │  └─ Backend Setup
  ├─ Architecture
  │  ├─ System Design
  │  ├─ Database Schema
  │  └─ API Endpoints
  ├─ Coding Standards
  ├─ Testing Guide
  └─ Deployment Guide
  ```

- [ ] **Notion Knowledge Base (Opsiyonel)**
  - Daha detaylı dökümanlar için
  - Meeting notes, brainstorming
  - Research findings

---

## ✅ Faz 5: CI/CD Pipeline (30 dakika)

### GitHub Actions (ÜCRETSİZ)

- [ ] **Workflow Dosyaları Oluştur**
  - `.github/workflows/ci.yml` (test + lint)
  - `.github/workflows/android.yml` (Android build)
  - `.github/workflows/ios.yml` (iOS build)

**Not**: Dosyalar React Native proje setup'tan sonra oluşturulacak

- [ ] **Secrets Ekle**
  - Repository → Settings → Secrets and variables → Actions
  - Eklenecekler (sonra):
    - `FIREBASE_API_KEY`
    - `GOOGLE_SERVICES_JSON` (base64)
    - `IOS_CERTIFICATE` (base64)

---

## ✅ Faz 6: Tasarım Araçları (20 dakika)

### Figma (ÜCRETSİZ - Education Plan)

- [ ] **Figma Education Plan Başvuru**
  - figma.com/education
  - Üniversite email'i ile başvur
  - Onay: ~2-3 gün
  - Avantaj: Pro features ücretsiz (unlimited pages, advanced prototyping)

- [ ] **Team Oluştur**
  - Figma → New team → "MESH112"
  - Ekip üyelerini davet et (özellikle Designer)

- [ ] **Design System Setup**
  - Yeni proje: "MESH112 Design System"
  - Sayfalar:
    - Color Palette
    - Typography
    - Icons
    - Components (Button, Input, Card, etc.)
    - Screens (Chat, Map, Profile, SOS)

- [ ] **Plugin'ler Yükle**
  - Unsplash (stock photos)
  - Iconify (icon library)
  - Stark (accessibility checker)
  - Autoflow (user flow diagrams)

---

## ✅ Faz 7: Geliştirme Araçları (15 dakika)

### VS Code Extensions (Tüm Ekip için)

- [ ] **Zorunlu Extension'lar**
  ```
  - ESLint (code linting)
  - Prettier (formatting)
  - GitLens (git history)
  - GitHub Copilot (AI pair programming) - ÜCRETLİ ama öğrenci ücretsiz
  - React Native Tools
  - TypeScript + JavaScript
  - Thunder Client (API testing)
  - Live Share (pair programming)
  ```

- [ ] **GitHub Copilot Öğrenci Paketi**
  - education.github.com/pack
  - Üniversite email ile başvur
  - Copilot + diğer araçlar ücretsiz

### Postman (API Testing)

- [ ] **Postman Workspace**
  - postman.com → Sign up
  - Workspace: "MESH112 API"
  - Plan: **FREE** (unlimited requests)
  - Collection oluştur: "Backend API v1"

---

## ✅ Faz 8: Monitoring & Analytics (10 dakika)

### Sentry (Crash Reporting)

- [ ] **Sentry Hesap Oluştur**
  - sentry.io → Sign up with GitHub
  - Plan: **Developer** (5,000 events/ay ücretsiz)
  - Organization: "MESH112"
  - Project: `mesh112-mobile` (React Native)

- [ ] **Integration Keys Al**
  - Settings → Client Keys (DSN)
  - `.env` dosyasına eklenecek (sonra)

### Firebase (Analytics + Hosting)

- [ ] **Firebase Console Setup**
  - console.firebase.google.com
  - New project: "MESH112"
  - Google Analytics: ✅ Enable
  - Plan: **Spark** (ücretsiz)

- [ ] **Apps Ekle**
  - Android app: `com.mesh112.app`
  - iOS app: `com.mesh112.app`
  - Web app: `mesh112-web` (landing page için)

- [ ] **Services Aktifleştir**
  - ✅ Authentication (Anonymous auth)
  - ✅ Firestore (optional cloud sync)
  - ✅ Storage (AI model hosting)
  - ✅ Hosting (landing page)
  - ✅ Performance Monitoring
  - ✅ Crashlytics

---

## ✅ Faz 9: Domain & Hosting (15 dakika)

### Domain (İHTİYARİ - ama profesyonel görünüm)

- [ ] **Domain Satın Al** (Opsiyonel)
  - Seçenekler:
    - **mesh112.org** (~$10/yıl) - ÖNERİLEN
    - **mesh112.com** (~$12/yıl)
    - **mesh112.com.tr** (~₺50/yıl)
  - Provider: Namecheap, Google Domains, GoDaddy

### Landing Page Hosting (ÜCRETSİZ)

- [ ] **Vercel Hesap Oluştur**
  - vercel.com → Sign up with GitHub
  - Plan: **Hobby** (ücretsiz, unlimited deploys)
  - Import repository: `mesh112` (landing page branch)

**Alternatifler**:
- GitHub Pages (ücretsiz)
- Netlify (ücretsiz)
- Firebase Hosting (ücretsiz)

---

## ✅ Faz 10: Ekip Onboarding (30 dakika)

### Kickoff Meeting Hazırlığı

- [ ] **Meeting Zamanı Belirle**
  - Google Meet / Zoom link oluştur
  - Takvim daveti gönder (tüm ekip)
  - Tarih: __________ Saat: __________

- [ ] **Kickoff Agenda Hazırla**
  ```
  1. Tanışma (10 dk)
  2. Proje vizyonu (PROJE_PLANI.md) (15 dk)
  3. Roller ve sorumluluklar (10 dk)
  4. Araçlar tanıtımı (GitHub, Slack, Figma) (15 dk)
  5. Hafta 1 task'ları (10 dk)
  6. Q&A (10 dk)
  Total: 70 dakika
  ```

- [ ] **Onboarding Dokümantasyonu**
  - GitHub Wiki → "Onboarding Guide" sayfası
  - İçerik:
    - Tüm araçlara erişim linkleri
    - İlk task'lar
    - Code of Conduct
    - Slack kanal açıklamaları

### İlk Sprint Planning

- [ ] **Sprint 0 Planning**
  - Tarih: Kickoff meeting sonrası
  - Süre: 2 saat
  - GitHub Projects → Sprint 0 kartları
  - Story point estimation
  - Task assignment

---

## 📊 Maliyet Özeti

| Araç | Plan | Maliyet | Durum |
|------|------|---------|-------|
| GitHub | Free | ₺0 | ✅ Seçildi |
| GitHub Projects | Free | ₺0 | ✅ Seçildi |
| Slack | Free | ₺0 | ✅ Seçildi |
| Figma | Education | ₺0 | ⏳ Başvuru gerekli |
| VS Code | Free | ₺0 | ✅ Mevcut |
| GitHub Copilot | Education | ₺0 | ⏳ Başvuru gerekli |
| Postman | Free | ₺0 | ✅ Seçildi |
| Sentry | Developer | ₺0 | ✅ Seçildi |
| Firebase | Spark | ₺0 | ✅ Seçildi |
| Vercel | Hobby | ₺0 | ✅ Seçildi |
| Domain (mesh112.org) | İHTİYARİ | ~$10/yıl (~₺350) | ⏳ Sonra |

**Toplam Aylık Maliyet**: **₺0** 🎉  
**İlk yıl one-time maliyet**: ~₺350 (sadece domain, opsiyonel)

---

## 🎯 Öncelik Sırası (Bugün Yapılacaklar)

### ⚡ Yüksek Öncelik (30 dakika)
1. ✅ GitHub organization + repository oluştur
2. ✅ Slack workspace + kanallar kur
3. ✅ GitHub Projects (kanban board)

### 🔶 Orta Öncelik (1 saat)
4. ⏳ Figma Education başvurusu
5. ⏳ GitHub Copilot öğrenci paketi
6. ⏳ Firebase project setup
7. ⏳ Sentry project setup

### 🔵 Düşük Öncelik (yarın/bu hafta)
8. ⏳ Domain satın alma
9. ⏳ Landing page prototipi
10. ⏳ Wiki sayfaları oluşturma

---

## 📞 Yardım Kaynakları

**Sorularınız için**:
- GitHub Docs: https://docs.github.com
- Slack Help: https://slack.com/help
- Figma Learn: https://help.figma.com

**Ekip için quick links** (sonra Slack'e pin'le):
```
🏠 GitHub Repo: https://github.com/ORGANIZATION/mesh112
💬 Slack: https://mesh112-team.slack.com
🎨 Figma: https://figma.com/files/team/TEAM_ID
📋 Projects: https://github.com/orgs/ORGANIZATION/projects/1
📚 Wiki: https://github.com/ORGANIZATION/mesh112/wiki
```

---

## ✅ Final Checklist

Setup tamamlandığında bu sorular EVET olmalı:

- [ ] Ekip GitHub repo'yu görebiliyor mu?
- [ ] Herkes Slack workspace'e katıldı mı?
- [ ] İlk issue'lar oluşturuldu mu?
- [ ] Kickoff meeting planlandı mı?
- [ ] Figma/Copilot başvuruları yapıldı mı?
- [ ] Firebase credentials alındı mı?

**Hepsi EVET ise** → 🎉 **SETUP TAMAMLANDI!**

---

**Sonraki Adım**: Hafta 1 task'larına başla (PROJE_PLANI.md → Bölüm 10.1)

*Hazırlayan: Project Manager*  
*Son Güncelleme: 26 Ekim 2025*
