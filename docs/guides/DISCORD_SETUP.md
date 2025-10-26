# 🎮 MESH112 Discord Sunucusu Kurulum Rehberi

> **Alternatif**: Slack Free yerine Discord kullanımı  
> **Maliyet**: ₺0 (tamamen ücretsiz)  
> **Kurulum Süresi**: 15 dakika

---

## 📋 Adım Adım Kurulum

### 1️⃣ Discord Sunucusu Oluşturma (5 dakika)

```
1. discord.com → Giriş yapın (hesap yoksa oluşturun)
2. Sol sidebar → "+" butonu → "Create My Own"
3. "For me and my friends" seçin
4. Sunucu Adı: "MESH112 Team"
5. İkon yükleyin: MESH112 logosu
6. "Create" butonuna tıklayın
```

---

### 2️⃣ Kategori ve Kanal Yapısı (5 dakika)

#### Kategoriler ve Kanallar

```
📁 BİLGİLENDİRME
   📄 #hoşgeldin - Yeni üye karşılama
   📄 #duyurular - Önemli bildirimler (PM only)
   📄 #kaynaklar - Döküman linkleri

📁 GÜNLÜK İLETİŞİM
   💬 #genel - Günlük sohbet
   💬 #random - Off-topic konuşmalar
   💬 #daily-standup - Her sabah 09:00 notları

📁 GELİŞTİRME
   👨‍💻 #mesh112-dev - Geliştirme tartışmaları
   🐛 #bug-reports - Bug bildirimleri
   💡 #feature-ideas - Yeni özellik önerileri
   🤖 #github-updates - Otomatik GitHub bildirimleri

📁 SPRINT YÖNETİMİ
   📊 #sprint-planning - Sprint planlama notları
   ✅ #sprint-review - Sprint review sonuçları
   📈 #metrics - Performans metrikleri

📁 SESLİ KANALLAR
   🔊 Toplantı Odası
   🔊 Pair Programming
   🔊 AFK Odası
```

#### Kanal Oluşturma
```
1. Kategori adına sağ tık → "Create Category"
2. Kategori içine sağ tık → "Create Channel"
3. # (metin) veya 🔊 (sesli) seçin
4. İzinleri ayarlayın (gerekirse)
```

---

### 3️⃣ Roller ve İzinler (3 dakika)

#### Roller
```
Server Settings → Roles → Create Role

🔴 Proje Yöneticisi (@PM)
   - Yönetici izinleri
   - Tüm kanallara erişim
   - #duyurular'a yazma yetkisi

🟠 Takım Lideri (@Lead)
   - Mesaj sabitleme
   - Kullanıcı susturma (toplantılarda)
   
🟢 Geliştirici (@Developer)
   - Standart izinler
   - Tüm kanallara erişim

🔵 Misafir (@Guest)
   - Sadece #genel ve #random
   - Geliştirme kanallarına erişim yok
```

#### Üye Rolleri
```
Emre → @PM + @Developer
Ayşe → @Lead + @Developer (AI Engineer)
Mehmet → @Developer (Network Engineer)
Fatma → @Developer (UI/UX Designer)
Ali → @Developer (Mobile Developer)
```

---

### 4️⃣ GitHub Webhook Entegrasyonu (10 dakika)

#### Discord Webhook Oluşturma
```
1. #github-updates kanalına git
2. Kanal ayarları (⚙️) → Integrations → Webhooks
3. "New Webhook" → "Copy Webhook URL"
4. URL'i kaydet (örn: https://discord.com/api/webhooks/123456...)
```

#### GitHub'da Ayarlama
```
1. https://github.com/frambuaz-crew/mesh112/settings/hooks
2. "Add webhook"
3. Payload URL: (Discord webhook URL'i)/github
4. Content type: application/json
5. Events seçin:
   ☑️ Pull requests
   ☑️ Pull request reviews
   ☑️ Pushes
   ☑️ Issues
   ☑️ Issue comments
6. "Add webhook"
```

#### Test Etme
```
1. GitHub'da test PR açın
2. Discord #github-updates kanalında bildirim görünmeli:

   🔔 [mesh112] New pull request by @emre
   feat: add hello screen
   feature/emre/hello-screen → develop
   🔗 View PR
```

---

### 5️⃣ Botlar Ekleme (İsteğe Bağlı)

#### Yararlı Botlar

**1. Reminder Bot** (Toplantı hatırlatmaları)
```
https://top.gg/bot/reminder-bot

Komutlar:
!remind #daily-standup "Daily Standup zamanı!" in 24 hours
!remind @everyone "Sprint Planning" on Friday at 14:00
```

**2. Poll Bot** (Oylama)
```
https://top.gg/bot/poll-bot

Komutlar:
!poll "Sprint retrospective: En iyi pratik?"
"Daily standup" "Code review" "Pair programming"
```

**3. GitHub Bot** (Resmi Discord GitHub botu)
```
https://discord.com/application-directory/487431320314576937

Komutlar:
!github subscribe frambuaz-crew/mesh112
!github issues
!github prs
```

---

### 6️⃣ Bildirim Ayarları (Tavsiyeler)

#### Takım için Öneriler
```
Server Ayarları → Notifications

@everyone mentions: Sadece admins
Suppress @everyone: ✅ (Spam önleme)

Kişisel Ayarlar:
#duyurular → Tüm mesajlar (🔔)
#daily-standup → Tüm mesajlar (🔔)
#github-updates → Sadece mention'lar (@)
#genel → Sadece mention'lar (@)
#random → Kapalı (🔕)
```

---

### 7️⃣ Mobil Uygulama Kurulumu

```
📱 iOS: App Store → "Discord"
📱 Android: Play Store → "Discord"
💻 Desktop: discord.com/download

Giriş yaptıktan sonra:
Servers → MESH112 Team görünecek
```

---

## 🎯 Günlük Kullanım Örnekleri

### Sabah Rutini (09:00 Daily Standup)
```
#daily-standup kanalında:

@everyone Günaydın ekip! 🌅

📝 Daily Standup Formatı:
1️⃣ Dün neler yaptım?
2️⃣ Bugün neler yapacağım?
3️⃣ Engellerim var mı?

Emre (PM):
1️⃣ Workflow guide hazırladım
2️⃣ Discord sunucusunu kuracağım
3️⃣ Yok

(Herkes kendi durumunu yazar)
```

### GitHub Bildirimleri
```
#github-updates otomatik bildirir:

🟢 @emre pushed to develop
   feat: add workflow guide
   📝 View commit

🔵 @ayse opened PR #5
   feature/ayse/ai-model → develop
   🔗 Review needed
```

### Sprint Planning
```
#sprint-planning kanalında:

📊 Sprint 2 Planning (27 Ekim - 16 Kasım)

🎯 Sprint Hedefi: BLE mesh networking MVP

📌 Görevler:
- [ ] BLE scanning (@ali)
- [ ] Message routing (@mehmet)
- [ ] UI mockups (@fatma)
- [ ] AI model integration (@ayse)
- [ ] Sprint yönetimi (@emre)

Sorular? 👇
```

---

## 🔧 İleri Seviye Özellikler

### Ses Toplantıları
```
1. 🔊 Toplantı Odası'na tıklayın
2. Ekran paylaşımı: Video butonunun yanında
3. Kayıt: Toplantı başlat (Nitro gerektirir - alternatif OBS Studio)
```

### Forum Kanalları (Tartışma Konuları)
```
Kategori → Create Channel → Forum

Kullanım:
#feature-ideas → Her yeni özellik bir thread
Avantaj: Konular düzenli, arama kolay
```

### Webhooks ile Custom Entegrasyonlar
```javascript
// Node.js ile Discord'a mesaj gönderme
const axios = require('axios');

const WEBHOOK_URL = 'https://discord.com/api/webhooks/...';

axios.post(WEBHOOK_URL, {
  content: '🚨 Production hatası: GPS tracking çalışmıyor!',
  username: 'MESH112 Monitoring',
  avatar_url: 'https://...'
});
```

---

## 📊 Slack vs Discord Karşılaştırma

| Özellik | Slack Free | Discord Free |
|---------|-----------|--------------|
| **Mesaj Geçmişi** | 90 gün | ♾️ Sınırsız |
| **Dosya Depolama** | 5GB toplam | 25MB/dosya |
| **Toplantı Süresi** | 1:1 only | Sınırsız (25 kişi) |
| **Ekran Paylaşımı** | ❌ | ✅ (1080p 60fps) |
| **Webhook** | ✅ 10 webhook | ✅ Sınırsız |
| **Mobil App** | ✅ | ✅ |
| **Desktop App** | ✅ | ✅ |
| **Arama** | Sadece son 90 gün | Tüm mesajlar |
| **Bot Desteği** | Sınırlı | Tam destek |
| **Özel Emoji** | ❌ | ✅ 50 emoji |
| **Ses Kalitesi** | -- | 96kbps |
| **Maliyet** | **₺0** | **₺0** |

---

## ✅ Kurulum Checklist

- [ ] Discord sunucusu oluşturuldu
- [ ] Kategoriler ve kanallar yapılandırıldı
- [ ] Roller tanımlandı (@PM, @Developer)
- [ ] Takım üyeleri davet edildi (5 kişi)
- [ ] GitHub webhook entegrasyonu yapıldı
- [ ] Reminder bot eklendi
- [ ] Bildirim ayarları yapılandırıldı
- [ ] Mobil uygulama kuruldu (tüm ekip)
- [ ] İlk test mesajı gönderildi
- [ ] #hoşgeldin kanalına kurallar yazıldı

---

## 🆘 Sorun Giderme

### GitHub Webhook Çalışmıyor
```
1. GitHub Settings → Webhooks → Son webhook'u kontrol et
2. "Recent Deliveries" → Hata mesajını oku
3. Discord webhook URL'inde /github suffix var mı kontrol et
4. Test delivery gönder
```

### Bildirimler Gelmiyor
```
1. Discord Settings → Notifications → Server override kontrol et
2. Kanalın notification ayarlarını kontrol et
3. Sunucu susturulmuş mu kontrol et (sağ tık → Mute Server)
```

### Ses/Video Çalışmıyor
```
1. Discord Settings → Voice & Video
2. Input/Output device'ları kontrol et
3. "Let's Check" ile test et
4. Tarayıcı yerine Desktop app kullanın (daha stabil)
```

---

## 📚 Ek Kaynaklar

- [Discord Markdown Rehberi](https://support.discord.com/hc/en-us/articles/210298617)
- [Webhook Dokümantasyonu](https://discord.com/developers/docs/resources/webhook)
- [Discord Bot Geliştirme](https://discord.js.org/)

---

**Hazırlayan**: Emre (PM)  
**Tarih**: 26 Ekim 2025  
**Versiyon**: 1.0

**Sorular?** Discord'da @emre'ye mention atın! 🚀
