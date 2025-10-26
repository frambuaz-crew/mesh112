# 🤖 GitHub Projects Otomasyonu - MESH112

## 📋 Workflow Aşamaları

```
Issue Oluştur → Backlog → To Do → In Progress → Review → Ready to Test → Done
     (Manuel)   (Otomatik)  (Manuel)  (Otomatik)   (Otomatik)   (Otomatik)    (Otomatik)
```

---

## 🎯 Workflow Detayları

### 1️⃣ Issue Oluşturma (Manuel - Emre)
```markdown
**Ne yapılacak?**
Title: [Component] Kısa açıklama
Body: Detaylı açıklama, gereksinimler, kabul kriterleri

**Etiketler**:
- priority:high / priority:medium / priority:low
- type:feature / type:bug / type:task
- component:ai / component:network / component:ui vb.
```

**Otomatik:** Yeni issue açıldığında → **Backlog**'a düşer

---

### 2️⃣ Backlog → To Do (Manuel - Emre)
Sprint planning yapılırken:
- Backlog'dan issue'yu sürükle → **To Do** kolonuna at
- Sprint alanını seç (Sprint 1, Sprint 2, vb.)
- Story point ekle (1, 2, 3, 5, 8)

**Tetikleyici**: Manuel drag & drop

---

### 3️⃣ To Do → In Progress (Otomatik)
Ekip üyesi kendini assignee olarak eklediğinde:
```
Assignee eklendi → Status otomatik "In Progress" olur
```

**Automation Kuralı**:
```yaml
Trigger: Item is assigned
Action: Set Status to "In Progress"
```

---

### 4️⃣ In Progress → Review (Otomatik)
Developer feature branch'inden PR açtığında:
```
PR açıldı (feature/* → develop) → Status otomatik "Review" olur
```

**Automation Kuralı**:
```yaml
Trigger: Pull request opened
Action: Set Status to "Review"
```

**PR Workflow**:
```bash
# Developer
git checkout -b feature/ai-message-classification
# ... kod yaz ...
git add .
git commit -m "feat: add AI message classification"
git push origin feature/ai-message-classification
# GitHub'da PR aç: feature/ai-message-classification → develop
```

---

### 5️⃣ Review → Ready to Test (Otomatik)
Emre (PM) PR'ı approve edip merge ettiğinde:
```
PR merged → develop branch'e → Status otomatik "Ready to Test" olur
```

**Automation Kuralı**:
```yaml
Trigger: Pull request merged
Condition: Base branch = develop
Action: Set Status to "Ready to Test"
```

---

### 6️⃣ Ready to Test → Done (Otomatik)
Hafta sonu develop → main merge edildiğinde:
```
develop → main merge (weekly release) → Status otomatik "Done" olur
```

**Automation Kuralı**:
```yaml
Trigger: Pull request merged
Condition: Base branch = main
Action: Set Status to "Done"
Action: Close issue
```

**Haftalık Release Workflow**:
```bash
# Cuma günü (Emre)
git checkout main
git pull origin main
git merge develop
git push origin main
# → Tüm "Ready to Test" issue'lar "Done" olur
```

---

## ⚙️ GitHub Projects Kurulumu

### 1. Yeni Project Oluştur
1. GitHub → frambuaz-crew → Projects → **New project**
2. Template: **Kanban**
3. İsim: **MESH112 Development**
4. Visibility: **Private** (sadece ekip görsün)

---

### 2. Kolonları Düzenle
Varsayılan kolonları şuna çevir:

| Sıra | Kolon Adı | Açıklama |
|------|-----------|----------|
| 1 | **Backlog** | Henüz planlamamış görevler |
| 2 | **To Do** | Sprint'e alınmış, yapılacak işler |
| 3 | **In Progress** | Şu anda üzerinde çalışılan |
| 4 | **Review** | PR açılmış, code review bekliyor |
| 5 | **Ready to Test** | Merge edilmiş, test edilecek |
| 6 | **Done** | Tamamlanmış ve main'e alınmış |

**Kolonları oluşturma**:
- Settings (⚙️) → Add field → Status (single select)
- Options: Backlog, To Do, In Progress, Review, Ready to Test, Done

---

### 3. Custom Fields Ekle

#### Sprint (Select)
- Field name: **Sprint**
- Type: **Single select**
- Options: `Sprint 1`, `Sprint 2`, `Sprint 3`, `Sprint 4`, `Sprint 5`, `Sprint 6`

#### Story Points (Number)
- Field name: **Story Points**
- Type: **Number**
- Values: 1, 2, 3, 5, 8, 13

#### Assignee (Kişi)
- Zaten var (default GitHub field)
- Options: @emre, @furkan, @oguz, @hasan, @sumeyye

#### Priority (Select)
- Field name: **Priority**
- Type: **Single select**
- Options: `🔴 High`, `🟡 Medium`, `🟢 Low`

---

### 4. Automation Kuralları Ekle

#### Kural 1: Yeni Issue → Backlog
```
Workflow: Auto-add to project
Trigger: Item added to project
Action: Set Status to "Backlog"
```

**Kurulum**:
1. Project → ⚙️ Settings → Workflows
2. **Auto-add to project** → Enable
3. **Default status** → `Backlog`

---

#### Kural 2: Assignee Eklendi → In Progress
```
Workflow: Item assigned
Trigger: Assignee added
Condition: Status = "To Do"
Action: Set Status to "In Progress"
```

**Kurulum**:
1. Workflows → **+ Add workflow**
2. Trigger: **Item assigned**
3. Action: **Set field value** → Status = `In Progress`

---

#### Kural 3: PR Açıldı → Review
```
Workflow: Pull request opened
Trigger: PR opened and linked to issue
Action: Set Status to "Review"
```

**Kurulum**:
1. Workflows → **+ Add workflow**
2. Trigger: **Pull request opened**
3. Action: **Set field value** → Status = `Review`

**PR'yi Issue'ya Bağlama**:
```markdown
PR Description:
Closes #42
```
veya commit message'da:
```bash
git commit -m "feat: add BLE scanning (fixes #42)"
```

---

#### Kural 4: PR Merge (develop) → Ready to Test
```
Workflow: Pull request merged to develop
Trigger: PR merged
Condition: Base branch = develop
Action: Set Status to "Ready to Test"
```

**Kurulum**:
1. Workflows → **+ Add workflow**
2. Trigger: **Pull request merged**
3. Filter: **Base branch** = `develop`
4. Action: **Set field value** → Status = `Ready to Test`

---

#### Kural 5: PR Merge (main) → Done
```
Workflow: Pull request merged to main
Trigger: PR merged
Condition: Base branch = main
Actions:
  1. Set Status to "Done"
  2. Close issue
```

**Kurulum**:
1. Workflows → **+ Add workflow**
2. Trigger: **Pull request merged**
3. Filter: **Base branch** = `main`
4. Action 1: **Set field value** → Status = `Done`
5. Action 2: **Close item**

---

## 📝 Günlük Kullanım Senaryoları

### Senaryo 1: Emre Yeni Görev Oluşturuyor
```bash
# GitHub'da
1. Issues → New issue
2. Title: [AI] Message classification pipeline
3. Body: 
   TinyLlama modelini entegre et, mesajları kategorize et.
   
   **Kabul Kriterleri**:
   - [ ] ONNX model yükleniyor
   - [ ] Mesaj input alınıyor
   - [ ] Category + priority score dönüyor
   
4. Labels: type:feature, component:ai, priority:high
5. Create issue

# Otomatik → Backlog kolonuna düşer
```

---

### Senaryo 2: Sprint Planning (Emre)
```bash
# GitHub Projects → MESH112 Development
1. Backlog'dan 10 issue seç
2. Sürükle → To Do kolonuna at
3. Her birine Sprint 1 ata
4. Story point tahmin et (1-8)
5. Sprint planning toplantısı: Görevleri ekibe dağıt
```

---

### Senaryo 3: Furkan Göreve Başlıyor (AI Engineer)
```bash
# GitHub'da issue #42'yi aç
1. Assignees → @furkan ekle
2. Otomatik → In Progress kolonuna geçer

# Lokal
git checkout develop
git pull origin develop
git checkout -b feature/ai-message-classification

# ... kod yaz ...
# ... test et ...

git add .
git commit -m "feat: implement AI message classification (fixes #42)"
git push origin feature/ai-message-classification

# GitHub'da PR aç
Title: feat: AI message classification
Description: 
  Implements TinyLlama-based message categorization.
  
  Closes #42
  
Base: develop ← feature/ai-message-classification
```

**Otomatik → Issue #42, Review kolonuna geçer**

---

### Senaryo 4: Emre Code Review Yapıyor
```bash
# GitHub → Pull requests → Furkan'ın PR'ı
1. Files changed → Kodu incele
2. Yorumlar yap (gerekirse)
3. Approve (✅ yeşil buton)
4. Merge pull request → Squash and merge
5. Delete branch (feature/ai-message-classification)

# Otomatik → Issue #42, Ready to Test kolonuna geçer
```

---

### Senaryo 5: Haftalık Release (Cuma - Emre)
```bash
# Tüm "Ready to Test" issue'ları test et
# Beta tester feedback topla
# Sorun yoksa main'e merge

git checkout main
git pull origin main
git merge develop
git push origin main

# GitHub'da release notu yaz
Tag: v0.1.0-sprint1
Title: Sprint 1 Release - Basic Infrastructure
Description: 
  - ✅ React Native setup
  - ✅ BLE scanning
  - ✅ Profile screen
  
# Otomatik → Tüm "Ready to Test" issue'lar "Done" olur ve kapanır
```

---

## 🎨 GitHub Projects Görünümü (Örnek)

### Hafta Ortası (Çarşamba)
```
┌─────────────┬─────────────┬─────────────┬─────────────┬─────────────┬─────────────┐
│  Backlog    │   To Do     │ In Progress │   Review    │Ready to Test│    Done     │
├─────────────┼─────────────┼─────────────┼─────────────┼─────────────┼─────────────┤
│ #50 Map UI  │ #35 GPS     │ #42 AI      │ #38 BLE     │ #30 Setup   │ #25 Docs    │
│ @sumeyye    │ @hasan      │ @furkan ⚙️  │ @oguz 👀    │ @emre ✅    │ @emre ✔️    │
│ 5 SP        │ 3 SP        │ 5 SP        │ 8 SP        │ 2 SP        │ 1 SP        │
│             │             │             │             │             │             │
│ #51 SOS btn │ #36 SQLite  │ #44 Route   │             │ #32 CI/CD   │ #27 README  │
│ @sumeyye    │ @oguz       │ @oguz ⚙️    │             │ @emre ✅    │ @emre ✔️    │
│ 3 SP        │ 5 SP        │ 8 SP        │             │ 3 SP        │ 1 SP        │
│             │             │             │             │             │             │
│ #52 i18n    │ #37 UI kit  │             │             │             │             │
│ Unassigned  │ @sumeyye    │             │             │             │             │
│ 2 SP        │ 5 SP        │             │             │             │             │
├─────────────┼─────────────┼─────────────┼─────────────┼─────────────┼─────────────┤
│   25 SP     │   21 SP     │   13 SP     │    8 SP     │    5 SP     │    2 SP     │
│  3 issues   │  3 issues   │  2 issues   │  1 issue    │  2 issues   │  2 issues   │
└─────────────┴─────────────┴─────────────┴─────────────┴─────────────┴─────────────┘
```

Legend:
- ⚙️ = Actively being worked on
- 👀 = In code review
- ✅ = Merged, ready to test
- ✔️ = Completed and released

---

## 📊 Sprint Tracking

### Sprint Velocity Hesaplama
```
Sprint sonunda Done kolonundaki SP'leri topla:

Sprint 1: 35 SP tamamlandı
Sprint 2: 42 SP tamamlandı (velocity artıyor ✅)
Sprint 3: 38 SP (biraz düştü, tatil vardı)

Ortalama: (35 + 42 + 38) / 3 = 38.3 SP/sprint
```

### Burndown Chart
Projects → ⚙️ → Insights → **Create chart**
- Type: **Burndown**
- X-axis: Sprint duration (3 weeks)
- Y-axis: Story points
- Filter: Sprint = Sprint 1

---

## 🔔 Bildirim Ayarları

### Emre (PM)
- 🔔 Tüm PR'lar (review gerekli)
- 🔔 Issue'lar "Review" kolonuna geçtiğinde
- 🔔 Sprint sonunda (Done kolonu değiştiğinde)

### Ekip Üyeleri
- 🔔 Assign edildiklerinde
- 🔔 PR'larına yorum geldiğinde
- 🔔 PR merge edildiğinde

**Ayarlama**:
1. GitHub → Settings → Notifications
2. **Watching**: frambuaz-crew/mesh112
3. Custom: Pull requests, Issues, Mentions

---

## 🆘 Sorun Giderme

### Issue Otomatik Backlog'a Düşmüyor
- **Çözüm**: Project settings → Auto-add → Enable
- Repository settings → Projects → Link MESH112 Development

### Assignee Eklenince In Progress'e Geçmiyor
- **Çözüm**: Workflow kuralını kontrol et
- Condition: Status = "To Do" olmalı (Backlog'daysa çalışmaz)

### PR Merge Sonrası Status Değişmiyor
- **Çözüm**: PR description'da issue'yu bağla:
  ```
  Closes #42
  Fixes #43
  Resolves #44
  ```

### Haftalık Release'de Done'a Geçmiyor
- **Çözüm**: PR base branch = main olmalı
- Workflow: Base branch = main filter'ı kontrol et

---

## 📚 Ek Kaynaklar

- [GitHub Projects Docs](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [Automation Workflows](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project)
- [GitFlow Tutorial](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

---

**Son Güncelleme**: 26 Ekim 2025  
**Hazırlayan**: Emre (PM)  
**Durum**: 🚀 Aktif kullanımda
