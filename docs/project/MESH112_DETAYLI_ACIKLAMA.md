# 🚨 MESH112 - Afet Anında Hayat Kurtaran İletişim Ağı

## 📱 Proje Özeti

**MESH112**, deprem ve afet durumlarında GSM ve internet altyapısının çökmesi sonucu ortaya çıkan iletişim krizine karşı geliştirilmiş, **akıllı telefonlar üzerinden çalışan, internet gerektirmeyen, yapay zeka destekli acil durum iletişim platformudur**.

Türkiye'nin 112 acil yardım hattına referansla adlandırılan proje, Bluetooth ve WiFi Direct teknolojilerini kullanarak cihazlar arası **mesh (örgü) ağ yapısı** oluşturur ve insanların afet anında birbirleriyle iletişim kurmasını, yardım istemesini ve hayatta kalmalarını kolaylaştırır.

---

## 🎯 Projenin Amacı

### Ana Hedef
Deprem, sel, yangın gibi doğal afetlerde **iletişim altyapısı çöktüğünde** insanların:
- Birbirleriyle mesajlaşabilmesini
- Konumlarını paylaşabilmesini
- Acil yardım talebinde bulunabilmesini
- Toplanma noktalarını ve güvenli bölgeleri işaretleyebilmesini
- Tıbbi ihtiyaçlarını (kan grubu, ilaç, ambulans) bildirebilmesini

sağlayan **merkezi olmayan, özerk bir iletişim ağı** kurmak.

### Hedef Kullanıcılar
1. **Afetzedeler**: Enkaz altında veya güvenli bölgedeki vatandaşlar
2. **Arama-Kurtarma Ekipleri**: AFAD, UMKE, itfaiye, gönüllüler
3. **Sağlık Personeli**: Hastaneler, ambulanslar, doktorlar
4. **Kamu Kurumları**: AFAD, Kızılay, belediyeler

---

## 🔬 Teknik Yaklaşım

### 1. Mesh Network (Örgü Ağ Yapısı)

**Nasıl Çalışır?**

Geleneksel iletişimde herkes merkezi bir sunucuya (GSM kulesi, internet) bağlıdır. MESH112'de ise:

```
Geleneksel:                    MESH112:
    📱                            📱
     ↓                          ↗ ↓ ↘
   📡 GSM Kulesi               📱 📱 📱
     ↓                        ↗ ↓ ↘ ↓ ↘
    📱                      📱 📱 📱 📱 📱

GSM çökerse → İletişim YOK    Her telefon relay → İletişim VAR
```

**Her telefon hem alıcı hem verici!**
- **Kişi A** mesaj gönderir
- **Kişi B** (menzil içinde) alır ve **Kişi C**'ye iletir
- **Kişi C** mesajı **Kişi D**'ye iletir
- Böylece **kilometrelerce mesafe** kat edilebilir!

**Teknik Detaylar:**
- **Bluetooth Low Energy (BLE)**: 10-50 metre menzil, düşük pil tüketimi
- **WiFi Direct**: 100+ metre menzil, daha hızlı veri transferi
- **Multi-hop Routing**: Mesajlar otomatik olarak en kısa yoldan iletilir
- **Adaptive Network**: Kişiler gelip gidince ağ kendini yeniden düzenler

---

### 2. Yapay Zeka Entegrasyonu

Projenin **benzersiz** yanı: **On-device (cihaz üzerinde) yapay zeka** kullanması!

#### 2.1 Acil Mesaj Önceliklendirme

**Problem**: Afet anında binlerce mesaj gelir. Hangisi gerçekten acil?

**Çözüm**: AI mesajları otomatik kategorize eder ve sıralar.

**Örnek:**
```
Gelen Mesajlar:
1. "Merhaba nasılsınız?"           → AI: Öncelik DÜŞÜK (sohbet)
2. "Su ihtiyacı var"                → AI: Öncelik ORTA (yardım)
3. "Enkaz altındayım, kan kaybı var" → AI: Öncelik KRİTİK (hayati)
4. "AB+ kan grubu acil lazım"       → AI: Öncelik YÜKSEK (tıbbi)

Ekranda Sıralama:
🔴 Enkaz altındayım, kan kaybı var
🟠 AB+ kan grubu acil lazım
🟡 Su ihtiyacı var
⚪ Merhaba nasılsınız?
```

**Nasıl Çalışır?**
- **TinyLlama** veya **Phi-2** gibi küçük dil modeli (1-2GB) telefona yüklenir
- Model **quantize** edilir (boyutu küçültülür, 4-bit precision)
- Mesaj geldiğinde **1 saniye içinde** analiz edilir
- Kategori: Tıbbi / Yardım / Konum / Genel
- Aciliyet skoru: 0.0-1.0 arası

#### 2.2 Otomatik Kategorizasyon

AI mesajları otomatik etiketler:
- 🏥 **Tıbbi**: Yaralı, kan, ambulans, ilaç
- 🆘 **Acil Yardım**: Enkaz, kurtarma, yangın
- 📍 **Konum Bildirimi**: GPS koordinat, adres
- 💧 **İhtiyaç**: Su, yiyecek, battaniye, jeneratör
- ℹ️ **Bilgilendirme**: Toplanma noktası, güvenli bölge

#### 2.3 Çok Dilli Çeviri

**Problem**: Afetzedeler arasında yabancı uyruklu, göçmen veya turist olabilir.

**Çözüm**: AI mesajları anlık çevirir!
```
Kişi A (Türkçe): "Yardım edin, bacağım kırık!"
      ↓ AI Çevirisi
Kişi B (İngilizce): "Help, my leg is broken!"
Kişi C (Arapça): "ساعدوني، ساقي مكسورة!"
```

Desteklenen diller: Türkçe, İngilizce, Arapça, Kürtçe (genişletilebilir)

#### 2.4 Spam Filtreleme

AI gereksiz, tekrarlı veya spam mesajları filtreler:
- Aynı mesajın 10 kez gönderilmesi → 1 tanesi gösterilir
- Alakasız içerik (reklam, vb.) → Otomatik filtrelenir

---

### 3. Kullanıcı Arayüzü ve Özellikler

#### 3.1 Ana Ekranlar

**📱 Chat Ekranı** (Mesajlaşma)
- WhatsApp benzeri arayüz (kullanıcı dostu)
- Mesajlar öncelik sırasına göre (kırmızı, turuncu, sarı)
- Timestamp (zaman damgası)
- Gönderen kişinin ismi ve mesafe bilgisi

**🗺️ Harita Ekranı**
- Tüm kullanıcıların konumları (GPS)
- 🔴 Acil yardım talepleri (enkaz noktaları)
- 🟢 Toplanma noktaları (güvenli bölgeler)
- 🏥 Hastaneler, sağlık ocakları
- 💧 Su dağıtım noktaları
- 📍 Kendi konumunuz (mavi nokta)

**👤 Profil Ekranı**
- Ad, soyad, telefon
- **Kan grubu** (kritik!)
- **Kronik hastalıklar** (diyabet, kalp, vb.)
- **Acil durum kişileri** (yakınlar)
- **Özel notlar** (alerjiler, kullanılan ilaçlar)

**🆘 SOS Butonu**
- **Tek dokunuşla** acil yardım talebi!
- Otomatik GPS konum paylaşımı
- "ACİL YARDIM! [İsim] [Konum] [Zaman]" mesajı
- Tüm ağa yayınlanır (broadcast)

#### 3.2 İleri Seviye Özellikler

**🩸 Kan Grubu Eşleştirme**
```
Kişi A: "0 RH- kan grubu lazım!"
   ↓
Sistem otomatik 0 RH- olan kullanıcıları bulur:
   ↓
"Kişi B (0 RH-) 500m uzakta. İletişime geç?"
```

**🏥 Yardım Kategorileri**
- Su / Yiyecek
- Barınak / Battaniye
- Tıbbi Malzeme / İlaç
- Ambulans / Doktor
- Arama-Kurtarma Ekibi

**📊 Network Görselleştirme**
- Mesh ağında kimler var?
- Kaç "hop" (zıplama) uzaktalar?
- Bağlantı kalitesi nasıl?
- Network topology (grafik gösterimi)

**🔋 Pil Tasarrufu Modu**
- Bluetooth scanning aralığını artırır (30sn → 2dk)
- Ekran parlaklığını düşürür
- Background işlemleri minimize eder
- **Hedef**: 24 saat+ sürekli çalışma

---

## 🏗️ Teknik Mimari

### Katmanlar

```
┌─────────────────────────────────────────────┐
│         Kullanıcı Arayüzü (React Native)     │
│  Chat Ekranı | Harita | Profil | SOS        │
├─────────────────────────────────────────────┤
│            İş Mantığı Katmanı                │
│  Mesaj Yönetimi | AI Engine | Konum Servisi │
├─────────────────────────────────────────────┤
│            Network Katmanı                   │
│  BLE Mesh | WiFi Direct | Routing Engine   │
├─────────────────────────────────────────────┤
│            Veri Katmanı                      │
│  SQLite (Mesajlar) | AsyncStorage (Ayarlar) │
└─────────────────────────────────────────────┘
         ↕                    ↕
┌──────────────────┐  ┌──────────────────┐
│  On-Device AI    │  │  Optional Cloud  │
│  TinyLlama 1.1B  │  │  Sync & Analytics│
│  ONNX Runtime    │  │  (İnternet varsa)│
└──────────────────┘  └──────────────────┘
```

### Veri Akışı Örneği

```
1. Kullanıcı mesaj yazar: "Enkaz altındayım!"
   ↓
2. AI analiz eder → Kategori: Acil | Öncelik: Kritik
   ↓
3. GPS konumu otomatik eklenir → 37.8746, 32.4932
   ↓
4. BLE/WiFi üzerinden yayınlanır → Tüm mesh ağa
   ↓
5. Her cihaz mesajı alır ve relay eder
   ↓
6. Harita üzerinde kırmızı işaret belirir
   ↓
7. Arama-kurtarma ekibi konumu görür
```

---

## 🌟 Projenin Benzersiz Yönleri

### 1. Türkiye'ye Özel Çözüm
- **Deprem riski yüksek** bir ülkede kritik ihtiyaç
- 1999 Marmara, 2023 Kahramanmaraş depremleri deneyimlerinden ilham
- AFAD ve Kızılay iş birliği potansiyeli

### 2. On-Device AI (İnternet Gerektirmeyen Yapay Zeka)
- Çoğu AI uygulaması **cloud API** gerektirir (GPT-4, Claude)
- MESH112 ise AI'ı **telefona indirir** → İnternet olmadan çalışır!
- Bu, afet anında **hayati önem** taşır

### 3. Merkezi Olmayan Yapı (Decentralized)
- Tek bir sunucu yok → Hack edilemez, çökemez
- Her kullanıcı eşit (peer-to-peer)
- Cenzürlenemez, durduralamaz

### 4. Düşük Maliyet
- Özel donanım gerektirmez (herkesin telefonunda çalışır)
- Ücretsiz ve açık kaynak
- Topluluk destekli geliştirme

---

## 📊 Kullanım Senaryoları

### Senaryo 1: Deprem Anı
```
Saat 04:17 - 7.8 büyüklüğünde deprem
   ↓
GSM kuleleri hasar görür → İnternet yok
   ↓
100 kişi MESH112'yi açar
   ↓
Otomatik mesh network kurulur
   ↓
Ahmet (enkaz altında): "ACİL! Bacağım sıkışmış, çıkamıyorum!"
   ↓
Mesaj 5 hop üzerinden Mehmet'e (AFAD gönüllüsü) ulaşır
   ↓
Mehmet haritada Ahmet'in konumunu görür
   ↓
Kurtarma ekibi yönlendirilir
```

### Senaryo 2: Kan İhtiyacı
```
Ayşe (hastane): "0 RH- kan acil gerekli, 5 ünite"
   ↓
AI mesajı analiz eder → Kategori: Tıbbi, Öncelik: Yüksek
   ↓
Sistem 0 RH- kan grubundaki kullanıcıları filtreler
   ↓
3 kişi bulunur: Ali (200m), Veli (500m), Can (1.2km)
   ↓
Ali'ye bildirim: "Kan bağışınıza ihtiyaç var, 200m uzakta"
   ↓
Ali hastaneye gider
```

### Senaryo 3: Toplanma Noktası
```
Belediye (internet olan bölgede): "Atatürk Stadyumu toplanma noktası"
   ↓
Mesaj mesh ağa yayınılır
   ↓
Haritada 🟢 yeşil işaret belirir
   ↓
Vatandaşlar stadyuma yönlenir
   ↓
Su, yiyecek, çadır dağıtımı başlar
```

---

## 🎓 Akademik Değer

### Bilgisayar Mühendisliği Açısından

**1. Networking (Ağ Teknolojileri)**
- Mesh network protokolleri (Flooding, Gossip, AODV)
- Routing algoritmaları
- Peer-to-peer (P2P) mimarisi
- Network topology optimization

**2. Yapay Zeka / Makine Öğrenmesi**
- On-device AI deployment
- Model quantization (4-bit, 8-bit)
- Natural Language Processing (NLP)
- Text classification
- Multi-language translation

**3. Mobile Development**
- Cross-platform development (React Native)
- Bluetooth Low Energy (BLE) programming
- GPS and geolocation services
- Offline-first architecture
- Battery optimization

**4. Distributed Systems (Dağıtık Sistemler)**
- Decentralized architecture
- Data replication
- Eventual consistency
- Fault tolerance

**5. Software Engineering**
- Agile/Scrum metodolojisi
- CI/CD pipelines
- Test-driven development (TDD)
- Code review ve pair programming

### Potansiyel Makale Konuları

1. **"Disaster-Resilient Mesh Communication with On-Device AI"**
   - IEEE veya ACM konferanslarına gönderilebilir

2. **"Emergency Message Prioritization Using Lightweight LLMs"**
   - NLP konferanslarına uygun

3. **"Bluetooth Mesh Network Optimization for Disaster Scenarios"**
   - Networking konferanslarına

---

## 🚀 Proje Çıktıları

### Teknik Çıktılar
- ✅ Cross-platform mobile app (Android + iOS)
- ✅ On-device AI model (ONNX format)
- ✅ Mesh networking library (açık kaynak)
- ✅ Backend API (opsiyonel cloud sync)
- ✅ Web admin dashboard

### Akademik Çıktılar
- 📄 **Makale**: IEEE/ACM konferanslarına paper
- 📊 **Sunum**: Teknofest, TÜBİTAK yarışmaları
- 📚 **Dökümentasyon**: Technical documentation + user guide
- 🎥 **Demo Video**: 3-5 dakikalık tanıtım videosu

### Sosyal Etki Çıktıları
- 🏆 **Yarışmalar**: TÜBİTAK 2204, Teknofest, Google Solution Challenge
- 🤝 **İş Birlikleri**: AFAD, Kızılay, belediyeler
- 📱 **Gerçek Deployment**: App Store/Play Store yayını
- 🌍 **Açık Kaynak**: GitHub'da topluluk projesi

---

## 📈 Başarı Kriterleri

### Minimum Viable Product (MVP)
- ✅ 10+ cihaz arası stabil mesh network
- ✅ Text mesajlaşma (offline)
- ✅ AI önceliklendirme (>85% accuracy)
- ✅ GPS konum paylaşımı
- ✅ SOS butonu
- ✅ Battery life: 24+ saat

### Performance Benchmarks
- **Message Latency**: <2 saniye (3-hop)
- **AI Inference**: <1 saniye
- **Network Range**: 10 cihaz × 50m = 500m+
- **Battery Drain**: <5% per hour (aktif kullanım)
- **App Size**: <100MB
- **Crash-free Rate**: >99%

---

## 🌍 Sosyal Etki ve Vizyonu

### Kısa Vadeli Hedef (6 ay)
- Kampüste 50+ kişiyle beta test
- AFAD'a demo sunumu
- TÜBİTAK yarışmasına başvuru

### Orta Vadeli Hedef (1 yıl)
- App Store/Play Store yayını
- 10,000+ indirme
- Belediyelerle pilot projeler
- Deprem tatbikatlarında kullanım

### Uzun Vadeli Hedef (2-3 yıl)
- Türkiye genelinde yaygın kullanım
- Diğer ülkelere adaptasyon (Japonya, Nepal, vb.)
- Açık kaynak topluluğu oluşturma
- WHO/UN ile iş birliği

---

## 💡 Neden Bu Proje?

### Problem
- Her yıl dünyada **100+ milyon kişi** afetten etkileniyor
- Türkiye'nin **%92'si** deprem riski altında
- 2023 Kahramanmaraş depremi: 50,000+ ölü
- **İletişim kopukluğu** can kaybını artırıyor

### Çözüm
- **Herkesin cebindeki telefon** → Hayat kurtarma aracı
- **Merkezi altyapı gerektirmez** → Çökme riski yok
- **AI destekli** → Kaos ortamında düzen
- **Açık kaynak** → Herkes geliştirebilir

### Etki
- ❤️ **Hayat kurtarabilir** (gerçek dünya etkisi)
- 🇹🇷 **Türkiye'ye özel** (deprem gerçeği)
- 🚀 **Teknolojik yenilik** (on-device AI + mesh)
- 🏆 **Akademik değer** (makale + yarışma)
- 💰 **Startup potansiyeli** (sosyal girişimcilik)

---

## 🎯 Sonuç

**MESH112**, sadece bir mezuniyet projesi değil; **potansiyel olarak hayat kurtarabilecek, Türkiye'nin ihtiyaç duyduğu, global anlamda değeri olan** bir sosyal etki projesidir.

Bluetooth mesh networking + on-device AI kombinasyonu ile **teknik olarak yenilikçi**, afet senaryolarına odaklanmasıyla **sosyal olarak anlamlı**, açık kaynak ve düşük maliyetli olmasıyla **ölçeklenebilir** bir çözüm sunmaktadır.

5 kişilik ekip olarak, 18 haftalık süreçte bu projeyi hayata geçirip:
- ✅ **Teknik becerilerinizi** geliştirirsiniz (AI, networking, mobile dev)
- ✅ **Akademik katkı** sağlarsınız (makale, yarışma)
- ✅ **Sosyal etki** yaratırsınız (gerçek insanlara yardım)
- ✅ **Kariyer fırsatları** yakalarsınız (portfolio, startup)

**MESH112 ile Türkiye'nin afet direncini artıralım! 🇹🇷🚀**

---

**Proje Website**: https://mesh112.org (yakında)  
**GitHub**: https://github.com/your-team/mesh112  
**Discord**: MESH112 Community  
**Email**: team@mesh112.org

**#AfeteDirençliTürkiye #MESH112 #AcilDurum #YapayZeka #MeshNetwork**
