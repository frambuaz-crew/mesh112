# 🔑 GitHub Projects Automation - Token Kurulumu

## Neden Token Gerekiyor?

GitHub Actions'ın GitHub Projects'i yönetebilmesi için **Personal Access Token (Classic)** veya **Fine-grained token** gerekiyor.

---

## 🚀 Adım Adım Token Oluşturma

### 1. GitHub Settings'e Git

1. GitHub'da sağ üst → **Profil fotoğrafı** → **Settings**
2. Sol menüde en altta → **Developer settings**
3. **Personal access tokens** → **Tokens (classic)**
4. **Generate new token** → **Generate new token (classic)**

---

### 2. Token Ayarları

**Note (İsim)**: `MESH112 Projects Automation`

**Expiration**: 
- ✅ **No expiration** (süresi dolmasın)
- veya `90 days` (3 ayda bir yenilersin)

**Select scopes** (İZİNLER):
```
✅ repo (full control)
   ✅ repo:status
   ✅ repo_deployment
   ✅ public_repo
   ✅ repo:invite
   ✅ security_events

✅ workflow

✅ write:org
   ✅ read:org

✅ project (full control)
   ✅ read:project
```

**Generate token** butonuna bas!

---

### 3. Token'ı Kopyala

⚠️ **ÖNEMLİ**: Token sadece bir kez gösteriliyor!

Token şuna benzer:
```
ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Kopyala** ve güvenli bir yere kaydet (şimdilik Notepad'e yapıştır)

---

### 4. Token'ı Repository Secret Olarak Ekle

1. GitHub → **frambuaz-crew/mesh112** repository'sine git
2. **Settings** (repo settings, profil değil!)
3. Sol menü → **Secrets and variables** → **Actions**
4. **New repository secret** butonu

**Secret Bilgileri**:
- **Name**: `PROJECT_TOKEN`
- **Secret**: Token'ı yapıştır (ghp_xxx...)
- **Add secret**

---

## ✅ Kurulum Tamamlandı!

Artık `.github/workflows/project-automation.yml` dosyası çalışacak.

### Test Et:

#### 1. Yeni Issue Oluştur
```markdown
Title: [Test] Automation test

Body: GitHub Actions test

Labels: type:test
```

**Beklenen**: Otomatik Backlog'a düşer

---

#### 2. Issue'ya Assign Ol
Issue sayfasında → Assignees → @emre

**Beklenen**: Otomatik In Progress'e geçer

---

#### 3. PR Aç
```bash
git checkout develop  # ÖNEMLİ: develop'dan başla!
git checkout -b test/automation
echo "test" > test.txt
git add . && git commit -m "test: automation"
git push origin test/automation
```

**GitHub'da PR aç**:
- Base: **develop** ← Compare: test/automation (DEVELOP'A MERGE ET!)
- Title: `test: automation workflow`
- Description: `Closes #X` (issue numarası)

**Beklenen**: Otomatik Review'a geçer (manuel taşıman gerek şimdilik)

---

#### 4. PR Merge (develop)
**Merge pull request** → **develop** branch'ine

**Beklenen**: Issue otomatik **Ready to Test** kolonuna geçer ✅

---

#### 5. Haftalık Release - Main'e Merge (Cuma günleri)
```bash
git checkout main
git pull origin main
git merge develop
git push origin main
```

**Beklenen**: 
- Issue otomatik **Done** kolonuna geçer ✅
- Issue otomatik **kapanır** ✅

---

## 🎯 Doğru Workflow Özeti

```
Feature branch → develop (PR) → Ready to Test
                    ↓
              (Hafta sonu)
                    ↓
              develop → main → Done + Close
```

**ÖNEMLİ**: 
- ❌ Feature branch → main (YAPMA! Direkt Done'a gider)
- ✅ Feature branch → develop → Ready to Test (DOĞRU!)
- ✅ develop → main (haftada 1 kez) → Done

---

## 🔧 Sorun Giderme

### "Resource not accessible by integration" Hatası

**Sebep**: Token yetersiz izinlere sahip

**Çözüm**:
1. Token'ı yeniden oluştur
2. Tüm gerekli scope'ları seç (yukarıdaki liste)
3. Repository secret'ı güncelle

---

### Workflow Çalışmıyor

**Kontrol Et**:
1. GitHub → Actions → Workflow runs (hata var mı?)
2. Settings → Secrets → PROJECT_TOKEN var mı?
3. `.github/workflows/project-automation.yml` dosyası develop branch'inde mi?

---

### Project ID Nasıl Bulunur?

Eğer automation çalışmazsa, project ID'yi kontrol et:

1. https://github.com/orgs/frambuaz-crew/projects/1
2. URL'deki son sayı = Project ID (1)

Workflow dosyasında:
```yaml
project_id: 1  # Bu sayıyı kontrol et
```

---

## 🎯 Final Workflow

Artık TAM OTOMATIK:

```
✅ Issue oluştur → Backlog (otomatik)
👉 Backlog → To Do (manuel - sprint planning)
✅ Assign → In Progress (otomatik)
✅ PR aç → Review (otomatik)
✅ Merge develop → Ready to Test (otomatik)
✅ Merge main → Done + Close (otomatik)
```

**Manuel sadece**: Backlog → To Do (sprint planning)

---

**Hazırlayan**: Emre (PM)  
**Tarih**: 26 Ekim 2025  
**Durum**: 🚀 Tam otomasyon aktif!
