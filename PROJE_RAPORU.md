# HIRSIZLIK OYUNU - PROJE RAPORU

## 1. PROJE TANITIMI

### 1.1 Genel Bakış
Hırsızlık Oyunu, Three.js kütüphanesi kullanılarak geliştirilmiş birinci şahıs 3D gizlilik (stealth) oyunudur. Oyuncular, farklı galeri ve koridor düzenlerinde dolaşarak görevlilerden saklanmalı ve hedef tabloları çalmalıdır.

### 1.2 Proje Amacı
- Modern web teknolojileri ile 3D oyun geliştirme yeteneklerini göstermek
- Three.js motor kullanımında uzmanlaşmak
- Yapay zeka ve oyun mekaniği tasarımı deneyimi kazanmak
- Tam fonksiyonel bir web oyunu sunmak

### 1.3 Teknik Özellikler
- **Motor**: Three.js r128
- **Render**: WebGL ile donanım hızlandırmalı rendering
- **Kontrol Sistemi**: PointerLockControls (FPS benzeri)
- **Mimari**: Tek sayfa HTML uygulaması
- **Bağımlılıklar**: Minimal (sadece Three.js CDN)

---

## 2. OYUN TASARIMI

### 2.1 Oynanış Mekaniği

#### 2.1.1 Ana Hedef
Her seviyede rastgele seçilen 5 tablo çalınarak seviye tamamlanır. Görevliler tarafından yakalanmak oyunu kaybettirir.

#### 2.1.2 Hareket Sistemi
- **WASD Tuşları**: İleri, geri, sola, sağa hareket
- **Fare Hareketi**: 360° etrafına bakabilme
- **Hız**: 0.08 birim/frame sabit hareket hızı
- **Çarpışma**: Duvar penetrasyonu önleme sistemi

#### 2.1.3 Etkileşim
- **E Tuşu**: Hedef tablolara yakınken çalma
- **Mesafe Kontrolü**: 2 birim yarıçap içinde etkileşim
- **Geri Bildirim**: Ekran mesajları ve HUD güncellemesi

### 2.2 Seviye Tasarımı

#### Seviye 1: Kare Galeri
- **Düzen**: 4 koridor kare şeklinde dizilmiş
- **Boyut**: 28x28 birim
- **Tablo Sayısı**: 20 tablo (5'i hedef)
- **Görevli**: 2 görevli (kırmızı ve mavi)
- **Devriye**: Kare çevre rotası
- **Zorluk**: Kolay - açık görüş hatları

#### Seviye 2: H Tipi Koridor
- **Düzen**: H harfi şeklinde 3 koridor
- **Özellik**: Geçiş boşluklarıyla bağlı koridorlar
- **Tablo Sayısı**: 20 tablo
- **Görevli**: 2 görevli (farklı devriye rotaları)
- **Devriye**: H şeklinde karmaşık rota
- **Zorluk**: Orta - görüş kırılma noktaları

#### Seviye 3: Zikzak Tünel
- **Düzen**: 5 segment zikzak koridor
- **Özellik**: Dar geçitler ve ani dönüşler
- **Tablo Sayısı**: 12 tablo
- **Görevli**: 2 görevli (magenta ve cyan)
- **Devriye**: İleri-geri zikzak rotası
- **Zorluk**: Zor - kaçış alanı sınırlı

#### Seviye 4: Büyük Salon
- **Düzen**: 40x40 birimlik açık alan
- **Özellik**: Merkezi sütunlar (saklanma alanları)
- **Tablo Sayısı**: 22 tablo
- **Görevli**: 3 görevli (sarı, turuncu, kırmızı)
- **Devriye**: Dış çevre rotası
- **Zorluk**: Çok Zor - açık alan, çoklu görevli

### 2.3 Yapay Zeka Sistemi

#### 2.3.1 Görevli Davranışları

**Devriye Durumu (Walk State)**
- Waypoint tabanlı navigasyon
- 0.03 birim/frame hareket hızı
- Waypoint'e varınca durum değiştirme kararı
- %50 olasılıkla tarama moduna geçiş

**Tarama Durumu (Scan State)**
- Sabit pozisyonda 360° dönüş
- 0.015 radyan/frame dönüş hızı
- Tam tur sonrası devriye moduna dönüş

#### 2.3.2 Görüş Sistemi
- **Görüş Açısı**: 120° (±60°)
- **Görüş Mesafesi**: 10 birim
- **Hesaplama**: Vektör dot product ile açı kontrolü
- **Arkadan Geçiş**: Güvenli (görüş konisi dışında)

#### 2.3.3 Çarpışma Engelleme
- 0.5 birim yarıçap güvenlik marjı
- Walkable area sınırlarına saygı
- Sütun/engel çarpışma tespiti

---

## 3. TEKNİK UYGULAMA

### 3.1 Render Sistemi

#### 3.1.1 Sahne Yapısı
```javascript
- Scene (Ana sahne)
  - Ambient Light (Genel aydınlatma)
  - Hemisphere Light (Gök-yer aydınlatma)
  - Point Light (Nokta ışık kaynağı)
  - Spot Light (Hedefli ışık)
  - Backdrop (200x200x200 arka plan kutusu)
  - Level Objects (Dinamik seviye geometrileri)
  - Guards (Görevli mesh'leri)
  - Paintings (Tablo çerçeveleri)
```

#### 3.1.2 Materyal Sistemi
- **DoubleSide Rendering**: Duvar şeffaflık sorunlarını önleme
- **Fog Integration**: Materyal bazında sis desteği
- **Shadow Mapping**: Gölge haritası aktif
- **Color Palette**: 
  - Duvarlar: 0x808080 (gri)
  - Zemin: 0x333333 (koyu gri)
  - Tavan: 0x111111 (çok koyu gri)

#### 3.1.3 Aydınlatma
```javascript
Ambient: 0x404040, intensity: 0.5
Hemisphere: Sky 0x87ceeb, Ground 0x362b1f, intensity: 0.4
Point: 0xffffff, intensity: 0.3, position: (0, 5, 0)
Spot: 0xffffff, intensity: 0.5, angle: Math.PI/3
```

#### 3.1.4 Fog Sistemi
- **Renk**: 0x1a1a1a (sahne arka planı ile uyumlu)
- **Near**: 15 birim (sis başlangıcı)
- **Far**: 50 birim (tam sis)
- **Amaç**: Uzak geometri gizleme ve atmosfer

### 3.2 Geometri Oluşturma

#### 3.2.1 createSegment() Fonksiyonu
Koridor segmentleri oluşturur:
- Zemin ve tavan (PlaneGeometry)
- Sol/sağ duvarlar (opsiyonel)
- Ön/arka duvarlar (dar tüneller için)
- Her duvarın çift yüzü (DoubleSide için)

#### 3.2.2 createCorridor() Fonksiyonu
H-tipi koridor için özel fonksiyon:
- Geçiş boşluklarıyla duvar segmentleri
- Yatay/dikey yönlendirme desteği
- Bağlantı noktaları için gap kontrolü

#### 3.2.3 createRoom() Fonksiyonu
Kapalı odalar için:
- 4 duvar + zemin + tavan
- Her duvarın çift yüzlü renderi
- Simetrik geometri

#### 3.2.4 createBlock() Fonksiyonu
Sütun/engel blokları:
- BoxGeometry (w × 4 × l)
- Collision rectangle tanımı
- Dinamik pozisyonlama

### 3.3 Çarpışma Sistemi

#### 3.3.1 Walkable Area Kontrolü
```javascript
checkCollision(x, z):
  - 0.5 birim yarıçap margin
  - Rectangle içerik kontrolü
  - OR operasyonu (herhangi bir walkable içinde)
```

#### 3.3.2 Blok Çarpışması
- Dikdörtgen sınır kutusu (AABB)
- Genişletilmiş sınırlar (oyuncu yarıçapı dahil)
- Overlap tespiti

### 3.4 Minimap Sistemi

#### 3.4.1 Ortografik Kamera
- 20 birim görüş alanı
- Yukarıdan bakış (0, 50, 0)
- Oyuncu pozisyonunu takip

#### 3.4.2 Render Pipeline
```javascript
1. Ana kamera render
2. Viewport değişimi (sağ alt köşe)
3. Minimap kamera render
4. Viewport restore
```

#### 3.4.3 Dinamik İkonlar
- Görevli başına bir ikon (SphereGeometry)
- Gerçek zamanlı pozisyon güncellemesi
- Renk kodlu görevli tipleri

### 3.5 Ses Sistemi

#### 3.5.1 HTML5 Audio Implementation
```html
<audio id="bgMusic" loop autoplay>
  <source src="..." type="audio/mpeg">
</audio>
```

#### 3.5.2 Autoplay Policy Compliance
- İlk user interaction (click/keydown) bekler
- Promise based play() çağrısı
- Fallback error handling
- Event listener temizleme

#### 3.5.3 Kontroller
- Toggle butonu (açma/kapama)
- Volume slider (0-100%)
- Real-time volume update

---

## 4. KULLANICI ARAYÜZÜ

### 4.1 HUD Elementleri

#### 4.1.1 Bilgi Paneli (#info)
- Kontrol listesi
- Dinamik opacity (0.3 oyunda, 1.0 menüde)
- Pozisyon: Sol üst

#### 4.1.2 Mesaj Paneli (#message)
- Oyun geri bildirimleri
- 2 saniye auto-hide
- Merkez pozisyon

#### 4.1.3 Target Counter (#targetMsg)
- Kalan hedef sayısı
- Sürekli görünür
- Sağ üst köşe

#### 4.1.4 Ayarlar Paneli (#settingsPanel)
- Toggle visibility
- Mouse sensitivity slider (0.1x - 3x)
- Müzik kontrolü (açık/kapalı)
- Volume slider (0-100%)
- Pozisyon: Sol üst (butona yakın)

### 4.2 Stil Tasarımı
- **Font**: Arial, sans-serif
- **Renk Paleti**: Beyaz metin, koyu arka planlar
- **Transparanlar**: rgba kullanımı
- **Responsive**: Sabit pixel değerleri

---

## 5. GELİŞTİRME SÜRECİ

### 5.1 İterasyon 1: Temel Oyun
- Tek harita implementasyonu
- Basit görevli AI
- Çarpışma sistemi ilk versiyon

### 5.2 İterasyon 2: Çoklu Harita
- 4 seviye ekleme
- Dinamik level loading sistemi
- Waypoint tabanlı navigasyon

### 5.3 İterasyon 3: Görsel İyileştirmeler
- DoubleSide material uygulaması
- Duvar arkası görünme düzeltmeleri
- Fog sistemi optimizasyonu
- Backdrop ekleme

### 5.4 İterasyon 4: Görevli AI Geliştirme
- Görüş konisi implementasyonu
- Duvardan geçiş engelleme
- Waypoint çakışma düzeltmeleri
- Başlangıç pozisyonu optimizasyonu

### 5.5 İterasyon 5: UI/UX
- Ayarlar paneli ekleme
- Mouse sensitivity kontrolü
- Müzik sistemi
- Minimap iyileştirmeleri

### 5.6 İterasyon 6: Bug Fixes
- H-tipi koridor karmaşıklık azaltma
- Zikzak tünel duvar düzeltmesi
- Müzik autoplay compliance
- Tüm seviyelerde duvar rendering kontrolü

---

## 6. SORUN GİDERME

### 6.1 Çözülen Teknik Sorunlar

#### Sorun 1: Duvarların Arkası Görünüyor
**Neden**: Three.js default front-face culling
**Çözüm**: 
- DoubleSide material property
- Her duvara ters yönlü ikinci mesh
- Backdrop ekleme (200x200x200 kutu)

#### Sorun 2: Görevliler Duvardan Geçiyor
**Neden**: Yetersiz collision margin
**Çözüm**:
- 0.5 birim güvenlik marjı
- Waypoint rotaları yeniden tasarım
- Walkable area sınırları genişletme

#### Sorun 3: H Tipi Koridor Karmaşık
**Neden**: Overlapping geometri
**Çözüm**:
- 3 basit koridora sadeleştirme
- Gap sistemi ile geçiş noktaları
- Collision box optimizasyonu

#### Sorun 4: Zikzak Tünel Tek Koridor
**Neden**: customBuild() bozuk implementasyon
**Çözüm**:
- Segment tabanlı sisteme geri dönüş
- 5 ayrı koridor segment
- Ön/arka duvar ekleme

#### Sorun 5: Görevli İç İçe Başlıyor
**Neden**: Aynı waypoint index
**Çözüm**:
- Farklı wpIndex ataması
- Farklı yön değerleri (dir: 1 vs -1)

#### Sorun 6: Arkası Dönükken Yakalanma
**Neden**: Sadece mesafe kontrolü
**Çözüm**:
- Vektör dot product hesabı
- 120° görüş konisi implementasyonu
- cos(60°) = 0.5 threshold

#### Sorun 7: Müzik Otomatik Çalmıyor
**Neden**: Browser autoplay policy
**Çözüm**:
- User interaction event listener
- Promise based play() call
- Fallback error handling

### 6.2 Performans Optimizasyonları
- Object pooling (levelObjects array)
- Geometry reuse
- Efficient rendering pipeline
- Minimal DOM manipulation

---

## 7. SONUÇ VE DEĞERLENDİRME

### 7.1 Başarılar
✅ 4 tam fonksiyonel seviye
✅ Akıllı görevli yapay zekası
✅ Sağlam çarpışma sistemi
✅ Tam UI/UX implementasyonu
✅ Görsel bug'ların çözümü
✅ Müzik ve ses sistemi
✅ Responsive kontroller

### 7.2 Öğrenilen Dersler
- Three.js material sisteminin derinliği
- Browser API kısıtlamaları (autoplay)
- Geometri optimizasyonunun önemi
- Yapay zeka davranış tasarımı
- Iterative development methodology

### 7.3 Gelecek Geliştirmeler (Potansiyel)
- Daha fazla seviye
- Zorluk seviyeleri
- Leaderboard sistemi
- Ses efektleri (adım sesi, alarm)
- Mobil kontrol desteği
- Multiplayer özelliği
- Save/Load sistemi
- Achievement sistemi

### 7.4 Sonuç
Hırsızlık Oyunu, modern web teknolojileri kullanılarak başarıyla tamamlanmış tam özellikli bir 3D oyundur. Proje, Three.js motor kullanımı, oyun mekaniği tasarımı, yapay zeka implementasyonu ve problem çözme becerilerinde önemli deneyim kazandırmıştır.

---

## 8. TEKNIK DÖKÜMAN

### 8.1 Dosya Yapısı
```
hırsızlık oyun/
├── main.html                           # Ana oyun dosyası (865 satır)
├── README.md                           # Proje açıklaması
├── Hırsızlık Oyunu - Proje Raporu.pdf # PDF rapor
└── .git/                               # Git repository
```

### 8.2 Kod İstatistikleri
- **Toplam Satır**: ~865 satır
- **HTML**: ~90 satır
- **CSS**: ~100 satır
- **JavaScript**: ~675 satır
- **Fonksiyon Sayısı**: ~15 ana fonksiyon
- **Class Sayısı**: 1 (Guard class)

### 8.3 Bağımlılıklar
```html
<!-- Three.js Core -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<!-- Pointer Lock Controls -->
<script src="https://cdn.jsdelivr.net/npm/three@0.128/examples/js/controls/PointerLockControls.js"></script>

<!-- Background Music (External) -->
<audio src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>
```

### 8.4 Tarayıcı Uyumluluğu
- ✅ Chrome 90+ (Önerilen)
- ✅ Firefox 88+
- ✅ Edge 90+
- ✅ Safari 14+ (WebGL desteği gerekli)
- ⚠️ Mobile: Sınırlı (PointerLock desteği yok)

### 8.5 Sistem Gereksinimleri
- **GPU**: WebGL 1.0 destekli herhangi bir kart
- **RAM**: Minimum 2GB
- **İşlemci**: Modern dual-core CPU
- **Ekran**: Minimum 1280x720 çözünürlük

---

**Proje Sahibi**: nurigelb  
**Repository**: https://github.com/nurigelb/HirsizlikOyun  
**Son Güncelleme**: 29 Aralık 2025  
**Versiyon**: 1.0.0
