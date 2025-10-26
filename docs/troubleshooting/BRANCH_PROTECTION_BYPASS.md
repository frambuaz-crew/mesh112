# 🔒 Branch Protection Bypass - Geliştirme Aşaması İçin

## Sorun
`develop` branch'ine merge yaparken "Review required" hatası alıyorsun.

---

## ✅ Çözüm 1: Branch Protection'ı Geliştirme İçin Gevşet (ÖNERİLEN)

### Şimdi Yap (1 dakika):

1. GitHub → **frambuaz-crew/mesh112** → **Settings** → **Branches**
2. **develop** branch protection rule'unu bul → **Edit**
3. Şu ayarı değiştir:
   - ❌ **"Require a pull request before merging"** → **KAPAT** (geçici olarak)
   
   veya
   
   - ✅ **"Require a pull request before merging"** → **AÇIK BIRAK** ama:
     - ✅ **"Allow specified actors to bypass required pull requests"** → **AÇIK YAP**
     - **Add** → **@emre** (kendini ekle)

4. **Save changes**

---

## ✅ Çözüm 2: Checkbox'ı İşaretle (Şimdi Kullanabilirsin)

PR ekranında gördüğün:
```
☐ Merge without waiting for requirements to be met (bypass rules)
```

**Bu checkbox'ı işaretle** → **Merge pull request**

Bu sadece admin/owner'lar için çalışır (sen owner'sın, çalışacak).

---

## ✅ Çözüm 3: Direct Push (En Hızlısı)

Ekip toplanana kadar doğrudan push yapabilirsin:

```bash
# develop branch'indeysen:
git push origin develop

# main'e de geçirebilirsin:
git checkout main
git merge develop
git push origin main
```

**Not**: Branch protection kuralları sadece PR üzerinden merge'de devreye giriyor. Direct push ile bypass olur (şimdilik sorun değil, tek kişisin).

---

## 🎯 Öneri: Ekip Toplanana Kadar

### develop branch için:
- ❌ **PR requirement** → Kapat
- ✅ Direct push yapabilirsin
- Ekip gelince tekrar aç

### main branch için:
- ✅ **PR requirement** → Açık kalsın
- ✅ **1 approval** → Açık kalsın
- Haftalık release'lerde kendin approve et

---

## 📋 Ekip Toplandığında (4 Kişi Gelince)

O zaman branch protection'ı tekrar sıkılaştır:

### develop:
- ✅ Require PR
- ✅ 1 approval (herhangi bir team member)
- ✅ Status checks (CI passed)

### main:
- ✅ Require PR
- ✅ 2 approvals (PM + 1 developer)
- ✅ Status checks
- ✅ Require up-to-date branches

---

## 🚀 Şimdi Ne Yapmalısın?

### Hızlı Yol (30 saniye):
1. PR'daki checkbox'ı işaretle: **"Merge without waiting for requirements (bypass rules)"**
2. **Merge pull request**

### Kalıcı Yol (1 dakika):
1. Settings → Branches → develop rule → Edit
2. **"Allow specified actors to bypass"** → Add yourself
3. Save
4. Artık her zaman bypass edebilirsin

---

Hangisini tercih edersin? Ben checkbox'u işaretlemeni öneririm (en hızlısı). 🚀
