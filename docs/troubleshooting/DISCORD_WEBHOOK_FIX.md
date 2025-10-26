# 🔧 Discord Webhook Hata Düzeltme

## Hata Mesajı
```json
{"message": "Cannot send an empty message", "code": 50006}
```

## Neden Oluyor?

GitHub'un `ping` eventi Discord'un beklediği mesaj formatında değil. `/github` suffix Discord'a "bu GitHub'dan geliyor, özel işle" diyor.

---

## ✅ ÇÖZÜM 1: URL'yi Düzelt (En Hızlı)

### GitHub Webhook Ayarları

1. **GitHub'a git**: 
   ```
   https://github.com/frambuaz-crew/mesh112/settings/hooks
   ```

2. Webhook'a tıklayın → **Edit**

3. **Payload URL** kontrol edin:
   ```
   ❌ YANLIŞ:
   https://discord.com/api/webhooks/123456789/abcdefgh
   
   ✅ DOĞRU:
   https://discord.com/api/webhooks/123456789/abcdefgh/github
   ```

4. Sonunda `/github` yoksa ekleyin

5. **Update webhook** tıklayın

6. **Test**: Recent Deliveries → Redeliver

---

## ✅ ÇÖZÜM 2: Sıfırdan Yeniden Oluştur

### Discord Tarafı

1. Discord → **#github-updates** kanalı

2. Kanal ayarları (⚙️) → **Integrations** → **Webhooks**

3. Eski webhook'u **Delete** et

4. **Create Webhook** → Yeni webhook oluştur

5. İsim: `GitHub Notifications`

6. **Copy Webhook URL** tıklayın
   ```
   Örnek: https://discord.com/api/webhooks/987654321/xyz123abc
   ```

7. **Kopyaladığınız URL'in SONUNA `/github` ekleyin**:
   ```
   https://discord.com/api/webhooks/987654321/xyz123abc/github
   ```

### GitHub Tarafı

1. **GitHub webhook ayarları**:
   ```
   https://github.com/frambuaz-crew/mesh112/settings/hooks
   ```

2. Eski webhook'u **Delete** et

3. **Add webhook** tıklayın

4. **Form doldur**:
   ```
   Payload URL: 
   https://discord.com/api/webhooks/987654321/xyz123abc/github
                                                         ^^^^^^ ÖNEMLİ!
   
   Content type: application/json
   
   Secret: (boş bırak)
   
   Which events:
   ● Let me select individual events
   ```

5. **Event'leri seç**:
   ```
   ☑️ Pull requests
   ☑️ Pull request reviews
   ☑️ Pull request review comments
   ☑️ Pushes
   ☑️ Issues
   ☑️ Issue comments
   ☑️ Commit comments
   ```

6. **☑️ Active** işaretle

7. **Add webhook** tıklayın

---

## 🧪 Test Etme

### Yöntem 1: GitHub Test Delivery

1. GitHub → Webhook → **Recent Deliveries**

2. En son delivery'ye tıklayın

3. **Redeliver** butonuna tıklayın

4. Başarılı yanıt:
   ```json
   Response: 200 OK
   Body: (boş olabilir)
   ```

### Yöntem 2: Gerçek Event

1. GitHub → Code

2. Herhangi bir dosyayı düzenle (örn: README.md)

3. Küçük değişiklik yap:
   ```markdown
   # MESH112
   Test webhook - 26 Ekim 2025
   ```

4. **Commit changes** → `test: discord webhook integration`

5. Discord **#github-updates** kanalına git

6. 2-3 saniye içinde mesaj görünmeli:
   ```
   🟢 [mesh112] emre pushed to develop
      test: discord webhook integration
      📝 View commit
   ```

---

## 🐛 Hala Çalışmıyor mu?

### Kontrol Listesi

- [ ] Discord webhook URL'inde `/github` suffix var mı?
- [ ] GitHub'da Content type `application/json` seçili mi?
- [ ] GitHub'da Active ✅ işaretli mi?
- [ ] Discord webhook kanalı `#github-updates` mi?
- [ ] Discord'da webhook silinmemiş mi? (Integrations'da görünmeli)

### Alternatif Tanı: cURL ile Test

PowerShell'de manuel test:

```powershell
# Discord webhook URL'inizi buraya yazın (sonunda /github OLMADAN)
$webhookUrl = "https://discord.com/api/webhooks/123456789/abcdefgh"

# Test mesajı gönder
$body = @{
    content = "🧪 Manuel test mesajı - Discord webhook çalışıyor!"
    username = "Test Bot"
} | ConvertTo-Json

Invoke-RestMethod -Uri $webhookUrl -Method Post -Body $body -ContentType 'application/json'
```

**Başarılı ise**: Webhook çalışıyor, sorun GitHub entegrasyonunda

**Hata verirse**: Discord webhook URL'i yanlış veya webhook silinmiş

---

## 📊 Başarılı Webhook Görünümü

### GitHub Recent Deliveries

```
✅ Status: 200
   Request URL: https://discord.com/api/webhooks/.../github
   Delivery ID: abc123...
   Event: push
   
   Response Headers:
   Status: 200 OK
   X-Discord-Features: webhooks
   
   Response Body:
   (boş veya minimal JSON)
```

### Discord #github-updates Kanalı

```
🟢 [mesh112] emre pushed to develop
   feat: add discord setup guide
   📝 1 commit

🔵 [mesh112] ayse opened pull request #5
   feature/ayse/ai-model → develop
   🔗 View pull request

🟣 [mesh112] mehmet reviewed pull request #5
   💬 2 comments
   ✅ Approved
```

---

## 💡 İpuçları

### 1. Event Filtresi
Çok fazla bildirim geliyorsa, sadece önemli event'leri seçin:
```
☑️ Pull requests
☑️ Pull request reviews
☑️ Pushes (sadece develop/main için)
❌ Issues (çok spam olabilir)
❌ Wiki (genelde gereksiz)
```

### 2. Branch Filtresi
Sadece `develop` ve `main` branch'lerinden bildirim almak için webhook'u özelleştirin (GitHub Pro gerektirir - FREE'de yok).

**Alternatif**: Discord'da bot ile filtreleme yapın.

### 3. Birden Fazla Webhook
Farklı event'ler için farklı Discord kanalları:

```
#github-prs → Sadece Pull Request event'leri
#github-commits → Sadece Push event'leri
#github-issues → Sadece Issue event'leri
```

Her kanal için ayrı webhook oluşturun ve GitHub'da ayrı webhook'lar ekleyin.

---

## 🆘 Acil Destek

Hala çalışmıyorsa:

1. **Discord Developer Portal**: https://discord.com/developers/applications
   - Webhook permissions kontrol edin

2. **GitHub Webhook Logs**: 
   - Recent Deliveries → Full error stack trace

3. **Discord Support**: 
   - https://support.discord.com

---

**Son Güncelleme**: 26 Ekim 2025  
**Hazırlayan**: Emre (PM)

Webhook çalıştı mı? #genel'de bize bildirin! 🚀
