# 🎯 GitHub Projects Automation - Adım Adım Kurulum

**Mevcut Proje**: https://github.com/orgs/frambuaz-crew/projects/1  
**Süre**: 10 dakika  
**Hedef**: Tam otomatik workflow (Backlog → Done)

**NOT**: GitHub Projects'te yeni workflow ekleme özelliği YOK. Sadece mevcut **varsayılan workflow'ları** açıp özelleştireceğiz!

---

## 📋 ŞU ANDA YAPMAN GEREKENLER

### Adım 1: Projeyi Aç
1. https://github.com/orgs/frambuaz-crew/projects/1
2. Sağ üstte **Workflows** (5 sayısı ile) tıkla

---

### Adım 2: Mevcut Workflow'ları Gör

GitHub Projects'te şu **default workflow'lar** var (soldaki listede):

**Aktif olanlar (yeşil nokta ✅)**:
- Auto-close issue
- Item added to project
- Item closed
- Pull request merged

**Pasif olanlar (gri nokta ⚪)**:
- Auto-add to project
- Auto-archive items
- Code changes requested
- Code review approved
- Item reopened

**Bizim kullanacaklarımız**:
1. ✅ **Item added to project** → Backlog
2. ⚪ **Auto-add to project** → Backlog (alternatif)
3. **YOK** - Assignee için manuel trigger yok ❌
4. ✅ **Pull request merged** → Review / Ready to Test / Done

---

### Adım 3: Status Kolonlarını Düzenle (3 dakika)

**ÖNCELİKLE** status kolonlarını oluştur:

1. Project board'a dön (← Back)
2. Sağ üst **⚙️ Settings** tıkla
3. **Fields** bölümü → **Status** → **Edit**
4. Mevcut kolonları düzenle/ekle:

```
Backlog          (gri)
To Do            (mavi)
In Progress      (sarı)
Review           (turuncu)
Ready to Test    (mor)
Done             (yeşil)
```

5. **Save changes**

---

### Adım 4: Custom Fields Ekle (2 dakika)

Settings → Fields → **+ New field**

#### Sprint Field
- **Field name**: `Sprint`
- **Field type**: **Single select**
- **Options**: `Sprint 1`, `Sprint 2`, `Sprint 3`, `Sprint 4`, `Sprint 5`, `Sprint 6`

#### Story Points Field
- **Field name**: `Story Points`
- **Field type**: **Number**

#### Priority Field
- **Field name**: `Priority`
- **Field type**: **Single select**
- **Options**: `🔴 High`, `🟡 Medium`, `🟢 Low`

---

### Adım 5: Workflow'ları Yapılandır (5 dakika)

Şimdi **Workflows** sayfasına geri dön.

---

#### 🤖 Workflow 1: Item added to project → Backlog

**Sol menüden**: **"Item added to project"** tıkla

**Şu anda ne yapıyor?** Muhtemelen hiçbir şey (sadece ekliyor)

**Düzenle**:
1. Sağ üstte **Edit** butonuna bas
2. **+ Add action** (veya mevcut action'ı düzenle)
3. Action: **Set field value**
4. Field: **Status**
5. Value: **Backlog**
6. **Save**

**Test**:
```
Yeni issue oluştur → Project'e ekle → Otomatik Backlog kolonuna düşmeli
```

---

#### 🤖 Workflow 2: Assignee → In Progress

**⚠️ SORUN**: GitHub Projects'te **"assignee added"** trigger'ı YOK!

**Çözüm**: MANUEL yönetim gerekiyor

**Alternatif çözümler**:
1. **Manuel**: Issue'ya assign olunca, developer kendisi status'u "In Progress" yapar
2. **GitHub Actions** (kod gerektirir - daha sonra ekleyebiliriz)
3. **Basit kural**: To Do'dan In Progress'e geçirince assign et

**Şimdilik**: Bu adımı ATLA, manuel yönet ✋

---

#### 🤖 Workflow 3: Pull request merged → Review / Ready to Test / Done

**ÖNEMLİ**: GitHub Projects'te **"Pull request opened"** trigger'ı YOK!

Sadece **"Pull request merged"** var. Bu yüzden:
- PR açıldığında → **Manuel** "Review" kolonuna taşı
- PR merge edildiğinde → **Otomatik** "Ready to Test" veya "Done"

**Sol menüden**: **"Pull request merged"** tıkla

**Düzenle**:
1. **Edit** butonuna bas
2. **Şu anda ne görüyorsun?** 
   - Trigger: Pull request merged
   - Action: (muhtemelen Set status to Done)

**Bizim ihtiyacımız**: 
- develop'a merge → Ready to Test
- main'e merge → Done

**SORUN**: Aynı trigger'dan 2 tane workflow yapamıyoruz!

**Çözüm**: 
1. Bu workflow'u **main branch için** ayarla:
   - **+ Add filter**
   - Filter: **Base branch** = `main`
   - Action: **Set Status** → **Done**
   - **+ Add action** → **Close item**
   
2. develop için **başka workflow gerekiyor** ama YOK!

**Geçici Çözüm**:
- PR merge (main) → Done (otomatik)
- PR merge (develop) → Manuel "Ready to Test"e taşı

---

#### 🤖 Workflow 4: Auto-close issue → Done

**Sol menüden**: **"Auto-close issue"** tıkla

**Bu ne yapar?** Issue kapatıldığında otomatik Done'a atar

**Düzenle**:
1. **Edit**
2. Action: **Set Status** → **Done**
3. **Save**

**Yararlı mı?** Evet! Issue manuel kapatırsan Done'a düşer.

---

#### 🤖 Workflow 5: Item closed → Archive (Opsiyonel)

**Sol menüden**: **"Item closed"** tıkla

**Düzenle**:
1. **Edit**
2. Action: **Archive item** (board'dan kaldırır, geçmişte saklar)
3. **Save** (veya kapalı bırak, arşivlemek istemiyorsan)

---

## ✅ Özet: Hangi Workflow'lar Kullanılabilir?

| Olay | Workflow Var mı? | Çözüm |
|------|-----------------|-------|
| Issue oluşturuldu | ✅ **Item added** | Otomatik Backlog |
| Backlog → To Do | ❌ | **Manuel** (sprint planning) |
| Assignee eklendi | ❌ | **Manuel** (developer kendisi In Progress yapar) |
| PR açıldı | ❌ | **Manuel** (Review kolonuna taşı) |
| PR merged (develop) | ⚠️ Kısmi | **Manuel** (Ready to Test'e taşı) |
| PR merged (main) | ✅ **PR merged** | Otomatik Done + Close |
| Issue closed | ✅ **Auto-close** | Otomatik Done |

---

## 🎯 Gerçekçi Workflow (Mevcut GitHub Projects Limitleri İle)

```
┌─────────────────────────────────────────────────────────┐
│  1. Issue Oluştur (Sen)                                 │
│     ↓ Otomatik (Item added workflow)                    │
│  2. BACKLOG                                             │
│     ↓ Manuel (Sprint planning - sen)                    │
│  3. TO DO                                               │
│     ↓ Manuel (Developer assign olup status değiştirir) │
│  4. IN PROGRESS                                         │
│     ↓ Manuel (Developer PR açınca Review'a taşır)      │
│  5. REVIEW                                              │
│     ↓ Manuel (Sen merge edince Ready to Test'e taşır)  │
│  6. READY TO TEST                                       │
│     ↓ Manuel (Test sonrası main'e merge)               │
│  7. develop → main MERGE                                │
│     ↓ Otomatik (PR merged workflow)                    │
│  8. DONE + CLOSED ✅                                    │
└─────────────────────────────────────────────────────────┘
```

**Otomatik**: Sadece 2 adım
- ✅ Issue → Backlog
- ✅ main merge → Done

**Manuel**: Geri kalan tüm adımlar

---

## 🔧 Gelecekte İyileştirme (GitHub Actions ile)

Eğer daha fazla otomasyon istersen, **GitHub Actions** workflow dosyası yazman gerekiyor:

`.github/workflows/project-automation.yml`

Bu sayede yapabilirsin:
- Assignee eklenince → In Progress
- PR açılınca → Review
- develop'a merge → Ready to Test

**Ama şimdilik**: Basit tut, manuel yönet! 👍

---

## ✅ Tamamlandı mı? Kontrol Listesi

### Field'lar
- [ ] Status: 6 kolon (Backlog, To Do, In Progress, Review, Ready to Test, Done)
- [ ] Sprint: Single select (Sprint 1-6)
- [ ] Story Points: Number
- [ ] Priority: Single select (High/Medium/Low)

### Workflows (5 tane)
- [ ] Workflow 1: Item added → Backlog
- [ ] Workflow 2: Assignee added → In Progress
- [ ] Workflow 3: PR opened → Review
- [ ] Workflow 4: PR merged (develop) → Ready to Test
- [ ] Workflow 5: PR merged (main) → Done + Close

---

## 🧪 Test Senaryosu (Manuel Yönetim)

### 1. Test Issue Oluştur

```markdown
Title: [Test] Automation test

Body:
GitHub Projects workflow test.

Labels: type:test
```

**Beklenen**: Otomatik Backlog'a düşer ✅

---

### 2. Sprint Planning (Manuel)

1. Issue'yu **Backlog**'dan **To Do**'ya sürükle
2. Sprint = Sprint 1
3. Story Points = 3
4. Priority = 🟡 Medium

---

### 3. Developer Göreve Başlıyor (Manuel)

1. Issue'yu aç
2. **Assignees** → @emre ekle
3. **Status** → Manuel **In Progress** yap (sürükle-bırak veya dropdown)

---

### 4. PR Açma (Manuel Review'a Taşıma)

```bash
git checkout -b test/automation
echo "test" > test.txt
git add . && git commit -m "test: automation"
git push origin test/automation
```

GitHub'da PR aç:
- Title: `test: automation workflow`
- Description: `Closes #[ISSUE_NO]`
- Base: develop

**PR açtıktan sonra**: Issue'yu manuel **Review** kolonuna taşı

---

### 5. Merge to Develop (Manuel Ready to Test)

1. PR'ı approve
2. **Merge pull request**
3. Issue'yu manuel **Ready to Test** kolonuna taşı

---

### 6. Main'e Merge (Otomatik Done!)

```bash
git checkout main
git merge develop
git push origin main
```

**Beklenen**: Issue otomatik **Done** + **Closed** ✅

---

## 📊 Final Workflow Özeti

```
OTOMATIK (2 adım):
✅ Issue oluştur → Backlog
✅ main merge → Done + Close

MANUEL (5 adım):
👉 Backlog → To Do (sprint planning)
👉 To Do → In Progress (assign + status değiştir)
👉 In Progress → Review (PR aç + taşı)
👉 Review → Ready to Test (merge develop + taşı)
👉 Ready to Test → main merge (sonra otomatik Done)
```

---

## 🚀 Gelecekte Tam Otomasyon (GitHub Actions)

Eğer her şeyi otomatik yapmak istersen:

**Dosya**: `.github/workflows/project-automation.yml`

Bu workflow ile:
- Assignee eklendi → In Progress
- PR açıldı → Review  
- PR merged (develop) → Ready to Test

**Şimdilik gerek yok!** 5 kişilik ekip için manuel yeterli. 

Ekip büyüdükçe (10+ kişi) GitHub Actions ekleriz.

---

## 🔧 Sorun Giderme

### Issue Otomatik Backlog'a Düşmüyor
**Sebep**: "Item added to project" workflow'u açık değil

**Çözüm**:
1. Workflows → "Item added to project" → **Edit**
2. Action: **Set Status** → **Backlog**
3. **Save**
4. Workflow'un **On** (açık) olduğundan emin ol

---

### Main'e Merge Sonrası Done'a Geçmiyor
**Sebep**: "Pull request merged" workflow'unda filter yanlış

**Çözüm**:
1. Workflows → "Pull request merged" → **Edit**
2. **+ Add filter** → **Base branch** = `main`
3. Action: **Set Status** → **Done**
4. **+ Add action** → **Close item**
5. **Save**

---

## � Ek Kaynaklar

- [GitHub Projects Docs](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [Default Workflows](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/using-the-built-in-automations)

---

**Son Güncelleme**: 26 Ekim 2025  
**Hazırlayan**: Emre (PM)  
**Durum**: 🎯 Gerçekçi sınırlamalarla güncellendi

**NOT**: GitHub Projects'in built-in automation'ları sınırlı. Tam otomasyon için GitHub Actions gerekiyor (gelecekte eklenecek).
