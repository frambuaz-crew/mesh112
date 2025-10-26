# 🎯 Sprint Sistemi Nasıl Çalışır?

## Temel Kavramlar

### Sprint = 3 Haftalık İş Döngüsü
```
Sprint Planning (Pazartesi)
    ↓
Daily Development (Salı-Perşembe × 3 hafta)
    ↓
Sprint Review + Retrospective (Cuma)
    ↓
YENİ SPRINT BAŞLAR
```

---

## 🔄 Günlük Akış (Bir Geliştiricinin Gününde)

### Sabah 09:00 - Daily Standup (Discord #daily-standup)
```
@emre:
1️⃣ Dün: Firebase kurulumunu tamamladım
2️⃣ Bugün: Sprint planning dökümanını yazacağım
3️⃣ Engel: Yok

@ayse:
1️⃣ Dün: TinyLlama modelini indirdim
2️⃣ Bugün: Phi-2 ile karşılaştırma testleri
3️⃣ Engel: TinyLlama'nın Türkçe accuracy'si düşük görünüyor

@mehmet:
1️⃣ Dün: react-native-ble-plx dökümanlarını okudum
2️⃣ Bugün: Basit BLE scanner yazmaya başlayacağım
3️⃣ Engel: iOS cihazım yok, sadece Android test edebiliyorum

... (herkes sırayla)
```

### 09:15-12:00 - Sabah Geliştirme Bloğu
```
1. GitHub Projects board'una git
2. "In Progress" kolonundaki KENDI issue'na bak
3. Feature branch'te çalış:
   git checkout feature/mehmet/ble-scanner
4. Kod yaz, test et
5. Commit at:
   git commit -m "feat: add BLE device discovery"
```

### 12:00-13:00 - Öğle Arası
```
Discord #random'da sohbet, kahve ☕
```

### 13:00-17:00 - Öğleden Sonra Geliştirme
```
1. Devam et, kod yaz
2. Issue tamamlandıysa PR aç:
   - GitHub → Pull Requests → New PR
   - feature/mehmet/ble-scanner → develop
   - Ekip arkadaşını reviewer olarak ekle
3. PR review bekle (genelde 2-4 saat)
```

### 17:00-18:00 - Review Saati
```
1. Başkalarının PR'larını review et
2. Yorum yaz: "LGTM 👍" veya "Bu kısım değişmeli"
3. Approve et → Merge edilir
4. Issue'yu kapat → "Done" kolonuna taşı
```

---

## 📊 GitHub Projects Board Kolonları

```
┌─────────────┬─────────────┬─────────────┬─────────────┬─────────────┬─────────────┐
│  Backlog    │   To Do     │ In Progress │  In Review  │   Testing   │    Done     │
├─────────────┼─────────────┼─────────────┼─────────────┼─────────────┼─────────────┤
│ Issue #13   │ Issue #1 ✋ │ Issue #3 👨  │ Issue #4 👀 │ Issue #5 🧪 │ Issue #2 ✅ │
│ Issue #14   │ Issue #6    │ Issue #7    │             │             │             │
│ Issue #15   │ Issue #8    │             │             │             │             │
│ (Sprint 2)  │ (Sprint 1)  │ (Sprint 1)  │ (Sprint 1)  │ (Sprint 1)  │ (Sprint 1)  │
└─────────────┴─────────────┴─────────────┴─────────────┴─────────────┴─────────────┘

✋ Seni bekliyor    👨 Üzerinde çalışıyorsun    👀 Review'da    🧪 Test ediliyor    ✅ Bitti
```

### Kolon Açıklamaları

1. **Backlog**: Gelecek sprint'lerde yapılacak işler
2. **To Do**: Bu sprint'te yapılacak, henüz başlanmamış
3. **In Progress**: Şu an üzerinde çalışılıyor (1 kişi max 2 issue)
4. **In Review**: PR açılmış, review bekleniyor
5. **Testing**: Merge edilmiş, test ediliyor
6. **Done**: Tamamlanmış, sprint sonunda demoya hazır

---

## 🎯 Issue Yaşam Döngüsü

### 1. Issue Oluşturma (PM yapar - Sprint başında)
```
GitHub → Issues → New Issue

Başlık: Setup Firebase project for analytics
Assignee: @emre
Labels: setup, infrastructure
Sprint: Sprint 1
Priority: High
Story Points: 3
```

### 2. Issue'yu Alma (Geliştirici - Pazartesi sabahı)
```
1. Projects board'unda issue'ya tıkla
2. Detayları oku
3. "To Do" → "In Progress" sürükle
4. Feature branch aç:
   git checkout -b feature/emre/firebase-setup
```

### 3. Geliştirme (Salı-Çarşamba)
```
Kod yaz → Commit → Push → Tekrar yaz...
```

### 4. PR Açma (Çarşamba öğleden sonra)
```
GitHub → Pull Requests → New PR
- Base: develop
- Compare: feature/emre/firebase-setup
- Title: "feat: setup Firebase project with Auth and Storage"
- Description: (Issue #1'deki checklist'i kopyala, tamamlananları işaretle)
- Reviewers: @mehmet ekle
- Link to Issue: "Closes #1"
```

### 5. Code Review (Perşembe sabahı)
```
@mehmet review yapar:
- "firebase.json'da API key exposed olmuş, .gitignore ekle"
- "docs/setup.md'de Android adımları eksik"

@emre düzeltir:
- git commit -m "fix: add firebase config to gitignore"
- git push (PR otomatik güncellenir)

@mehmet tekrar review:
- "LGTM 👍" → Approve
```

### 6. Merge (Perşembe öğleden sonra)
```
PM veya reviewer "Squash and Merge" tıklar
→ develop branch'ine birleşir
→ Issue otomatik kapanır (Closes #1 sayesinde)
→ Projects board'unda "Done"'a taşınır
```

---

## 📅 Sprint Timeline Örneği (Sprint 1)

### Hafta 1: 28 Ekim - 3 Kasım

**Pazartesi 28 Ekim**
```
09:00 - Sprint Planning Meeting (Discord sesli)
  → PM tüm issue'ları açıklar
  → Herkes kendi issue'larını alır
  → Sorular-cevaplar

10:30 - Herkes kendi feature branch'ini açar
11:00 - Geliştirme başlar
```

**Salı 29 Ekim**
```
09:00 - Daily Standup
09:15 - Geliştirme
17:00 - İlk PR'lar açılmaya başlar
```

**Çarşamba 30 Ekim**
```
09:00 - Daily Standup
10:00 - İlk merge'ler (basit issue'lar)
14:00 - Discord'da: "🎉 Issue #1 tamamlandı!"
```

**Perşembe 31 Ekim**
```
09:00 - Daily Standup
  → Mehmet: "BLE kütüphanesi seçimi bitti, prototipe geçiyorum"
  → Ayşe: "TinyLlama çok yavaş, Phi-2 ile devam ediyorum"
```

**Cuma 1 Kasım**
```
09:00 - Daily Standup
14:00 - Haftalık progress check (opsiyonel mini-demo)
17:00 - Hafta sonu!
```

### Hafta 2: 4-10 Kasım
(Benzer ritim devam eder)

### Hafta 3: 11-17 Kasım

**Cuma 17 Kasım - Sprint Sonu** 🏁
```
09:00 - Daily Standup (son!)

14:00 - Sprint Review Meeting (1.5 saat)
  → Her issue demo edilir:
    - Mehmet: BLE messenger app'i gösterir (2 telefon mesajlaşıyor)
    - Ayşe: AI classifier demo (mesaj kategorileri)
    - Fatma: Figma wireframe'leri sunar
    - Ali: React Native kurulum guide'ı gösterir
    - Emre: Firebase console'u gösterir

15:30 - Sprint Retrospective (30 dk)
  → İyi gidenler:
    ✅ BLE prototip çalıştı!
    ✅ Herkes zamanında teslim etti
  
  → Geliştirilebilir:
    ⚠️ Code review'lar biraz gecikmeli oldu
    ⚠️ Daily standup'lara katılım %80 (hedef %100)
  
  → Sprint 2 için aksiyonlar:
    📌 Review'ları 24 saat içinde yapmaya çalışalım
    📌 Standup'lar için Discord reminder bot kuralım

16:00 - Develop → Main Merge (PM)
  → PM son PR'ı açar: develop → main
  → 2 kişi review eder
  → Merge edilir
  → Tag atılır: v1.0.0-sprint-1
  → Release notes yazılır

17:00 - Sprint 1 kapanır ✅
  → Sprint 2 planning Pazartesi 20 Kasım'da!
```

---

## 🎓 Öğrenilen Dersler

### İyi Pratikler ✅
- Her gün commit at (yedekleme)
- Küçük, odaklanmış PR'lar (200-400 satır)
- Review'da yapıcı olun ("Bu kötü" ❌ → "Şöyle yaparsak daha iyi olur" ✅)
- Issue'larınızı güncel tutun (checklist işaretleyin)

### Kötü Pratikler ❌
- Haftalar boyunca PR açmamak
- Dev commit atmak ("update", "asdasd")
- Review beklerken yeni feature'a başlamak (conflict riski)
- Sprint sonunda tüm işi yapmaya çalışmak

---

## 🆘 Sorun Çözme

### "Issue çok büyük, 3 haftada bitmez!"
```
→ Issue'yu böl! (PM ile konuş)
Örnek:
  Issue #10: BLE Messaging App (16 saat)
  ↓ BÖLÜNÜR ↓
  Issue #10a: BLE Device Discovery (6 saat)
  Issue #10b: Message Send/Receive (6 saat)
  Issue #10c: UI + Testing (4 saat)
```

### "Başka bir issue'ya bağımlıyım, onu beklemem lazım"
```
→ Dependency belirt!
GitHub'da yorum yaz:
"#3 (AI model seçimi) tamamlanmadan başlayamıyorum"

→ PM önceliği değiştirir:
Issue #3 → Priority: Critical (diğerleri bekliyor)
```

### "Hasta oldum, issue'mu tamamlayamıyorum"
```
→ Discord'da bildir:
"Hastayım, Issue #7'yi bitiremeyeceğim"

→ PM yeniden atar:
Issue #7: Assignee: @mehmet → @ali
```

---

**Özet**: Sprint = Küçük hedeflerle düzenli ilerleme! 🚀

**Sprint başarısı = Tüm issue'lar Done kolonunda ✅**

Sorular? Discord #mesh112-dev kanalında sor! 💬
