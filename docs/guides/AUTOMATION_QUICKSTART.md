
# ⚡ GitHub Actions Automation - Hızlı Başlangıç

## 🎯 Ne Yapıyor?

Tam otomatik GitHub Projects workflow:

```
Issue aç → Backlog (otomatik)
Assign → In Progress (otomatik)
PR aç → Review (otomatik)
Merge develop → Ready to Test (otomatik)
Merge main → Done + Close (otomatik)
```

---

## 🚀 3 Adımda Kurulum

### 1. Token Oluştur (2 dakika)

1. GitHub → Settings → Developer settings → Personal access tokens (classic)
2. **Generate new token (classic)**
3. İzinleri seç:
   - ✅ `repo` (full control)
   - ✅ `workflow`
   - ✅ `write:org`
   - ✅ `project`
4. **Generate token** → Token'ı kopyala (ghp_xxx...)

---

### 2. Token'ı Ekle (1 dakika)

1. GitHub → frambuaz-crew/mesh112 → **Settings** (repo)
2. **Secrets and variables** → **Actions** → **New repository secret**
3. Name: `PROJECT_TOKEN`
4. Secret: Token'ı yapıştır
5. **Add secret**

---

### 3. Workflow'u Push Et (1 dakika)

Zaten yaptın! `.github/workflows/project-automation.yml` dosyası develop branch'inde.

```bash
# Eğer henüz push etmediysen:
git add .github/workflows/project-automation.yml
git commit -m "feat: add GitHub Projects automation workflow"
git push origin develop
```

---

## ✅ Test Et

### Test 1: Yeni Issue → Backlog

```
GitHub → Issues → New issue
Title: [Test] Automation check
Submit → Otomatik Backlog'a düşmeli
```

### Test 2: Assign → In Progress

```
Issue → Assignees → @emre ekle
Otomatik In Progress'e geçmeli
```

### Test 3: PR → Review → Ready to Test → Done

```bash
git checkout develop  # Önce develop'a geç!
git pull origin develop
git checkout -b test/automation
echo "test" > test.txt
git add . && git commit -m "test: automationn"
git push origin test/automation
```

**GitHub'da PR aç**:
- **Base: develop** ← Compare: test/automation (ÖNEMLİ!)
- Title: `test: automation workflow`
- **Description (ÖNEMLİ!)**:
  ```markdown
  Closes #1
  ```
  (Issue numarasını değiştir, örneğin #5, #10 vb.)

**Beklenen**: 
- PR ve issue otomatik bağlanır
- Workflow log'unda "Found linked issues" mesajı görülür

**Merge PR (develop'a) → Otomatik Ready to Test ✅**

**Sonra main'e merge (haftalık release)**:
```bash
git checkout main
git merge develop
git push origin main
```

**→ Otomatik Done + Close ✅**

---

## 🔍 Workflow Çalışıyor mu?

GitHub → **Actions** sekmesi → Workflow runs

Yeşil ✅ = Başarılı  
Kırmızı ❌ = Hata (logs'a bak)

---

## 📚 Detaylı Rehberler

- **Token kurulumu**: `docs/guides/GITHUB_TOKEN_SETUP.md`
- **Sorun giderme**: `docs/guides/GITHUB_TOKEN_SETUP.md#sorun-giderme`

---

**Kurulum Süresi**: 4 dakika  
**Sonuç**: Tam otomatik proje yönetimi 🚀
