# 👋 MESH112 Ekip Üyesi Hoş Geldin!

Hoş geldin! Bu rehber seni 10 dakikada ekibe hazırlayacak.

## 🎯 İlk 10 Dakika

### 1. GitHub Access (2 dakika)

- [ ] GitHub'da organization invitation'ı kabul et
- [ ] Repository'yi star'la: https://github.com/[ORG]/mesh112
- [ ] Repository'yi clone'la:
  ```bash
  git clone https://github.com/[ORG]/mesh112.git
  cd mesh112
  ```

### 2. Slack Workspace (2 dakika)

- [ ] Email'indeki Slack invitation'ı kabul et
- [ ] Profil fotoğrafını ekle
- [ ] Bio'ya rolünü yaz (örn: "AI/ML Engineer")
- [ ] Kanalları incele:
  - `#general` → Günlük duyurular
  - `#dev` → Teknik tartışmalar
  - `#standup` → Günlük güncellemeler
  - `#random` → Eğlence!

### 3. GitHub Projects (1 dakika)

- [ ] Projects tabına git
- [ ] "MESH112 Development" board'unu aç
- [ ] Sprint 0'daki kendi task'larını gör

### 4. Rollere Göre Ekstra Setup

#### 🤖 AI/ML Engineer (Kişi 2)

- [ ] Python 3.10+ yükle
- [ ] PyTorch kurulumu:
  ```bash
  pip install torch transformers onnx onnxruntime
  ```
- [ ] Jupyter Notebook / Google Colab hazır
- [ ] Hugging Face hesabı oluştur

#### 📱 Mobile Developer (Kişi 3)

- [ ] Node.js 18+ yükle
- [ ] React Native CLI kurulumu:
  ```bash
  npm install -g react-native-cli
  ```
- [ ] Android Studio / Xcode yükle
- [ ] Fiziksel test cihazı hazırla

#### 🌐 Network Engineer (Kişi 4)

- [ ] Node.js 18+ yükle
- [ ] SQLite browser kurulumu
- [ ] Wireshark (network analysis)
- [ ] Python NetworkX library:
  ```bash
  pip install networkx matplotlib
  ```

#### 🎨 UI/UX Designer (Kişi 5)

- [ ] Figma hesabı oluştur
- [ ] Education plan başvurusu (figma.com/education)
- [ ] "MESH112" team'e katıl
- [ ] Plugin'leri yükle (Iconify, Unsplash)

#### 👔 Project Manager (Kişi 1)

- [ ] Tüm araçlara admin erişimi kontrol et
- [ ] Firebase console erişimi
- [ ] Sentry dashboard erişimi
- [ ] GitHub repository settings

---

## 📚 Önemli Dökümanlar

| Dosya | Ne İçin Oku? |
|-------|--------------|
| `README.md` | Proje genel bakış |
| `PROJE_PLANI.md` | 18 haftalık detaylı plan |
| `CONTRIBUTING.md` | Nasıl katkıda bulunulur |
| `.github/copilot-instructions.md` | AI asistan için kılavuz |
| `SETUP_CHECKLIST.md` | PM için kurulum adımları |

**İlk gün oku**: `README.md` + `PROJE_PLANI.md` (en az Bölüm 3 - kendi rolün)

---

## 🔧 Development Workflow

### Yeni Feature Geliştirme

```bash
# 1. Latest kodu çek
git checkout main
git pull origin main

# 2. Yeni branch oluştur
git checkout -b feat/your-feature-name

# 3. Kod yaz, commit'le
git add .
git commit -m "feat(scope): your message"

# 4. Push et
git push origin feat/your-feature-name

# 5. GitHub'da Pull Request aç
# main ← feat/your-feature-name

# 6. Code review bekle (< 24 saat)
# 7. Merge sonrası branch'i sil
```

### Commit Message Formatı

```
<type>(<scope>): <subject>

type: feat, fix, perf, docs, style, refactor, test, chore, ai
scope: ble, ai, chat, map, profile, sos, network
subject: kısa açıklama (lowercase, imperative)

Örnek:
feat(ble): add multi-hop routing algorithm
fix(chat): resolve message duplication bug
perf(ai): optimize inference latency
```

---

## 🗓️ Toplantılar

### Daily Standup (Async - Slack)

**Her gün 09:00'da** `#standup` kanalına yaz:

```
📅 Tarih: 26 Ekim 2025

✅ Dün ne yaptım:
- BLE library dokümantasyonu okudum
- Profil ekranı mockup'ını tamamladım

🎯 Bugün ne yapacağım:
- React Native proje setup
- Figma component library başlangıç

🚧 Blocker var mı:
- Yok / iOS Developer hesabı approval bekliyor
```

### Sprint Planning (2 saatte bir - Sprint başı)

- Tarih: 3 haftada bir
- Süre: 2 saat
- Agenda:
  1. Geçmiş sprint review
  2. Yeni sprint goal
  3. Task estimation (story points)
  4. Task assignment

### Sprint Review (1.5 saat - Sprint sonu)

- Tarih: 3 haftada bir
- Süre: 1.5 saat
- Demo: Çalışan özellikler gösterilir
- Danışman + tüm ekip

### Retrospective (1 saat - Sprint sonu)

- What went well?
- What could be better?
- Action items

---

## 🎓 Öğrenme Kaynakları

### React Native

- Docs: https://reactnative.dev/
- Tutorial: https://reactnative.dev/docs/tutorial

### BLE (Bluetooth Low Energy)

- BLE Basics: https://www.bluetooth.com/learn-about-bluetooth/
- react-native-ble-plx: https://github.com/dotintent/react-native-ble-plx

### ONNX Runtime

- Docs: https://onnxruntime.ai/docs/
- Mobile: https://onnxruntime.ai/docs/tutorials/mobile/

### Mesh Networking

- AODV Protocol: https://tools.ietf.org/html/rfc3561
- Bridgefy case study: https://bridgefy.me/

---

## ❓ Sıkça Sorulan Sorular

**Q: İlk task'ımı nereden bulabilirim?**  
A: GitHub Projects → MESH112 Development → Assigned to you

**Q: Hangi branch'e commit yapmalıyım?**  
A: Asla `main`'e direkt commit yapma! Kendi feature branch'ini oluştur.

**Q: Code review kim yapacak?**  
A: En az 1 ekip üyesi (genellikle PM veya ilgili component owner)

**Q: Daily standup'ı kaçırırsam?**  
A: Günün geç saatinde de olsa `#standup`'a yaz

**Q: Blocker varsa ne yapmalıyım?**  
A: Hemen `#dev` kanalına yaz veya ilgili kişiye DM at

**Q: Test cihazım yok, ne yapmalıyım?**  
A: PM ile konuş, ekip havuzundan ödünç al veya arkadaştan/aileden

**Q: AI model nereden indirilecek?**  
A: Hugging Face'den (link AI Engineer paylaşacak - Hafta 3)

---

## 🚀 İlk Task'ını Al!

1. GitHub Projects'e git
2. Sprint 0 → Assigned to you
3. Task'ı "In Progress"'e taşı
4. Slack'te `#dev`'de duyur: "🚀 [Task adı] üzerinde çalışıyorum!"
5. İşini bitirince PR aç
6. Task'ı "Review"'a taşı

---

## 💬 İletişim

**Acil sorular**: `#dev` kanalı (hızlı cevap)  
**Bug buldum**: GitHub Issues → New issue  
**Feature önerisi**: GitHub Discussions  
**Kişisel konu**: PM'e DM (Slack)

---

## 🎉 Hoş Geldin Tekrar!

Sorularını sormaktan çekinme. Ekip burada yardım etmek için! 💪

**İlk adım**: Slack'te `#general`'de kendini tanıt!

```
👋 Merhaba! Ben [İsim], projeye [Rol] olarak katıldım.
[Üniversite/Bölüm] öğrencisiyim.
[İlgi alanlarım: React Native / AI / Design / vb.]
Heyecanlıyım! 🚀
```

---

*Son güncelleme: 26 Ekim 2025*  
*Sorular için: PM'e ulaş*
