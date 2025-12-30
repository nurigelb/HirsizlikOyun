# 🎯 HRSIZLIK OYUNU - SUNUM REHBERİ

## 📊 SUNUM SÜRELERİ
- **5 Dakika**: Hızlı demo + temel özellikler
- **10 Dakika**: Detaylı anlatım + teknik detaylar
- **15 Dakika**: Kapsamlı sunum + kod örnekleri

---

## 🎬 SUNUM AKIŞI (10 Dakika Önerilen)

### 1️⃣ GİRİŞ (1 dakika)
**Ne söylemeli:**
- "Merhaba, ben [adınız]. Sizlere Three.js kullanarak geliştirdiğim 3D birinci şahıs gizlilik oyunumu tanıtacağım."
- "Bu proje, modern web teknolojileri ile masaüstü kalitesinde oyun deneyimi sunmayı amaçlıyor."

**Gösterim:**
- Ana ekran görünümü
- Kısa oynanış videosu (10-15 saniye)

---

### 2️⃣ PROJE TANITIMI (2 dakika)

**Oyun Konsepti:**
- "Oyun, bir sanat galerisinde gizlilik temelli bir hırsızlık simülasyonu"
- "Oyuncu, görevlilerden saklanarak belirli tabloları çalmaya çalışıyor"
- "4 farklı harita, her biri farklı zorluk seviyesi ve mimari tasarım sunuyor"

**Temel Özellikler (Tek tek gösterin):**
1. ✅ **4 Farklı Seviye**: Ekranda seviyeleri gösterin
2. ✅ **Akıllı Yapay Zeka**: Görevlilerin devriye sistemi
3. ✅ **Gerçek Zamanlı Minimap**: Sağ alttaki minimap'i işaretleyin
4. ✅ **Dinamik Hedef Sistemi**: Her oyunda farklı tablolar hedef olur
5. ✅ **Özelleştirilebilir Ayarlar**: Mouse hassasiyeti, müzik kontrolü

**Gösterim:**
- 4 seviyeyi kısaca gezdirin (her biri 15 saniye)
- Minimap'i gösterin
- Ayarlar panelini açın

---

### 3️⃣ TEKNİK DETAYLAR (3 dakika)

**Kullanılan Teknolojiler:**
```
✨ Three.js r128        → 3D rendering motoru
🎮 PointerLockControls → FPS tarzı kamera kontrolü
🎨 WebGL               → Hardware-accelerated grafik
🔊 HTML5 Audio API     → Müzik sistemi
```

**Öne Çıkan Teknik Başarılar:**

1. **Gelişmiş Yapay Zeka Sistemi**
   - Görevliler devriye rotaları izliyor
   - 120° görüş açısı ile oyuncuyu tarama
   - Gerçek zamanlı mesafe hesaplama

2. **Optimizasyonlar**
   - DoubleSide rendering ile duvar görünüm sorunları çözüldü
   - Fog sistemi ile performans optimizasyonu
   - Minimap için ayrı camera sistemi

3. **Kullanıcı Deneyimi**
   - Autoplay politikalarına uyumlu müzik sistemi
   - Dinamik crosshair ve HUD
   - Gerçek zamanlı süre ve hedef takibi

**Gösterim:**
- Kod editörde önemli fonksiyonları gösterin
- Minimap sistemini açıklayın
- Yapay zeka devriye rotasını gösterin

---

### 4️⃣ CANLI DEMO (3 dakika)

**Demo Senaryosu:**
1. Oyunu başlatın
2. **Kare Galeri** seviyesini oynayın
3. Görevliden saklanmayı gösterin
4. Bir hedef tablo çalın (E tuşu)
5. Yakalanmayı gösterin
6. Minimap'i kullanarak görevli pozisyonlarını gösterin
7. Farklı bir seviyeye geçin (örn: Büyük Salon)

**Konuşma İpuçları:**
- "Gördüğünüz gibi, görevli beni fark etmeden yaklaşabiliyorum..."
- "Minimap'te görevlilerin pozisyonunu takip edebiliyoruz..."
- "Kırmızı çerçeveli tablolar hedefimiz, diğerlerine dokunmamamız gerekiyor..."
- "Yakalandığımda oyun bitiyor ve tekrar başlıyoruz..."

---

### 5️⃣ ZORLUKLAR VE ÇÖZÜMLER (1 dakika)

**Karşılaşılan Problemler:**

1. **Problem**: Duvarların arkası görünüyordu
   **Çözüm**: DoubleSide rendering + backdrop sistemi

2. **Problem**: Müzik tarayıcıda otomatik başlamıyordu
   **Çözüm**: İlk kullanıcı etkileşiminde başlatma mekanizması

3. **Problem**: Çarpışma tespiti yetersizdi
   **Çözüm**: Gelişmiş collision detection sistemi

4. **Problem**: Performans sorunları
   **Çözüm**: Fog sistemi ve optimized rendering

---

### 6️⃣ SONUÇ VE GELECEKTEKİ PLANLAR (1 dakika)

**Proje Başarıları:**
- ✅ Tek HTML dosyasında tam özellikli 3D oyun
- ✅ Tarayıcı tabanlı, kurulum gerektirmez
- ✅ Modern web standartlarına uyumlu
- ✅ Mobil uyumlu tasarım (gelecek güncelleme)

**Geliştirme Fırsatları:**
- 🔄 Daha fazla seviye eklenebilir
- 🔄 Çoklu oyuncu modu
- 🔄 Puan tablosu sistemi
- 🔄 Mobil dokunmatik kontroller
- 🔄 Daha fazla görevli tipi
- 🔄 İtem sistemi (anahtarlar, kameralar vb.)

**Kapanış:**
- "Bu proje, web teknolojilerinin oyun geliştirmede ne kadar güçlü olabileceğini gösteriyor."
- "Sorularınız varsa memnuniyetle cevaplayabilirim. Teşekkür ederim!"

---

## 🎯 ÖNEMLİ İPUÇLARI

### ✅ YAPILMASI GEREKENLER:
1. **Demo'dan önce hazırlık:**
   - Oyunu önceden test edin
   - Tarayıcı ses seviyesini ayarlayın
   - Tüm seviyeleri deneyin

2. **Sunum sırasında:**
   - Yavaş ve açık konuşun
   - Teknik terimleri basit açıklayın
   - Kod gösterirken satır satır açıklayın
   - Soru-cevap için zaman bırakın

3. **Gösterim:**
   - Ekranınızı paylaşmadan önce gereksiz sekmeleri kapatın
   - Tam ekran modunda oyunu gösterin
   - Minimap'i mutlaka vurgulayın

### ❌ YAPILMAMASI GEREKENLER:
1. Çok hızlı konuşmak
2. Teknik jargonla boğmak
3. Demo sırasında hata yapmaktan çekinmek
4. Kodun her detayını açıklamaya çalışmak
5. Zaman aşımına dikkat etmemek

---

## 📝 SORU-CEVAP HAZIRLıĞı

### Sıkça Sorulan Sorular:

**S: Neden Three.js kullandınız?**
C: "Three.js, WebGL'in karmaşıklığını soyutlayarak 3D sahne oluşturmayı kolaylaştırıyor. Ayrıca geniş topluluk desteği ve dokümantasyon avantajı var."

**S: Mobil cihazlarda çalışır mı?**
C: "Şu anda masaüstü için optimize edildi. Mobil için dokunmatik kontroller eklenmesi gerekiyor ancak teknik olarak çalışabilir."

**S: Geliştirme süreci ne kadar sürdü?**
C: [Gerçek süreyi söyleyin ve ana aşamaları açıklayın]

**S: En zorlu kısım neydi?**
C: "Yapay zeka yol bulma algoritması ve çarpışma tespiti en çok zaman alan kısımlardı."

**S: Neden tek HTML dosyası?**
C: "Basitlik ve taşınabilirlik için. Tek dosyayı açmak yeterli, başka kurulum gerekmiyor."

---

## 🎨 GÖRSEL DESTEK ÖNERİLERİ

Eğer PowerPoint/Google Slides kullanacaksanız:

### Slayt 1: Başlık
- Oyun adı ve logosu
- Adınız
- Teknoloji stack (Three.js, WebGL)

### Slayt 2: Oyun Konsepti
- Screenshot'lar
- Ana özellikler listesi

### Slayt 3: Seviyeler
- 4 seviyenin görselleri
- Her seviye için kısa açıklama

### Slayt 4: Teknik Mimari
- Diyagram: Three.js → Scene → Camera → Renderer
- Kullanılan teknolojiler

### Slayt 5: Yapay Zeka
- Görevli görüş açısı şeması
- Devriye rotası gösterimi

### Slayt 6: Zorluklar ve Çözümler
- Problem-Çözüm tablosu

### Slayt 7: Demo
- "Canlı Demo" yazısı
- QR kod (eğer online ise)

### Slayt 8: Sonuç
- Başarılar
- Gelecek planları
- Teşekkür

---

## ⏱️ ZAMAN PLANLAMASI

| Bölüm | Süre | Kümülatif |
|-------|------|-----------|
| Giriş | 1 dk | 1 dk |
| Tanıtım | 2 dk | 3 dk |
| Teknik Detaylar | 3 dk | 6 dk |
| Demo | 3 dk | 9 dk |
| Zorluklar | 1 dk | 10 dk |
| Sonuç | 1 dk | 11 dk |
| **TOPLAM** | **11 dk** | - |

*Soru-cevap için +5 dakika ekleyin*

---

## 🚀 SON KONTROL LİSTESİ

**Sunum öncesi 1 saat:**
- [ ] Oyunu test edin
- [ ] Tarayıcı önbelleğini temizleyin
- [ ] Ses seviyesini kontrol edin
- [ ] Sunumunuzu bir kez prova edin
- [ ] Yedek plan hazırlayın (video kaydı)

**Sunum öncesi 10 dakika:**
- [ ] Gereksiz programları kapatın
- [ ] Bildirim seslerini kapatın
- [ ] Ekran çözünürlüğünü ayarlayın
- [ ] Oyunu arka planda açık tutun

**Sunum sırasında:**
- [ ] Sakin ve güvenli konuşun
- [ ] Göz teması kurun
- [ ] Heyecanınızı gösterin
- [ ] Zamanı takip edin

---

## 💡 EK ÖNERİLER

### Video Hazırlığı:
Canlı demo riskli geliyorsa, önceden 2-3 dakikalık oynanış videosu çekin:
- OBS Studio (ücretsiz) kullanabilirsiniz
- 1080p, 60fps kayıt yapın
- Seslendirme ekleyin

### İnteraktif Öğeler:
- Dinleyicilere kontrolleri deneme fırsatı verin
- QR kod ile oyunu paylaşın (online ise)
- GitHub reposuna yönlendirin

### Profesyonel Dokunuşlar:
- Business card hazırlayın (GitHub linkli)
- README dosyasını düzenli tutun
- Demo sırasında console hatalarını gizleyin

---

**Başarılar dilerim! 🎮🚀**
