# Hırsızlık Oyunu (3D Stealth Game)

## 🎮 Oyun Hakkında
Hırsızlık Oyunu, Three.js kullanılarak geliştirilmiş birinci şahıs 3D gizlilik oyunudur. Oyuncular farklı haritaları keşfederken görevlilerden gizlenmeli ve hedef tabloları çalmalıdır.

## ✨ Özellikler

### 🗺️ 4 Farklı Seviye
- **Kare Galeri**: Kare şeklinde koridor düzeni
- **H Tipi Koridor**: H şeklinde karmaşık geçitler
- **Zikzak Tünel**: Zikzak şeklinde dar tünel
- **Büyük Salon**: Sütunlarla çevrili büyük açık alan

### 🎯 Oyun Mekaniği
- **Hedef Sistemi**: Her seviyede rastgele seçilen 5 tablo çalınmalı
- **Görevli Yapay Zekası**: Devriye gezen ve tarama yapan akıllı görevliler
- **Görüş Açısı Sistemi**: 120° görüş açısı ile gerçekçi yakalanma mekaniği
- **Çarpışma Tespiti**: Gelişmiş fizik ile duvarlardan geçiş engellendi

### 🎨 Görsel Özellikler
- **Dinamik Aydınlatma**: Atmosferik sis ve çoklu ışık kaynakları
- **Minimap**: Gerçek zamanlı miniharita ile konum takibi
- **Görevli İkonları**: Minimap üzerinde dinamik görevli gösterimi
- **DoubleSide Rendering**: Duvar şeffaflık sorunlarının giderilmesi

### ⚙️ Ayarlar
- **Mouse Hassasiyeti**: 0.1x - 3x arasında ayarlanabilir
- **Müzik Kontrolü**: Açma/kapama ve ses seviyesi ayarı
- **Otomatik Müzik**: İlk etkileşimde otomatik başlatma

### 🎵 Ses Sistemi
- HTML5 Audio API ile arka plan müziği
- Tarayıcı autoplay politikasına uyumlu başlatma
- Dinamik ses seviyesi kontrolü

## 🕹️ Kontroller
- **WASD**: Hareket
- **Fare**: Etrafına bakınma
- **E**: Tablo çalma
- **ESC**: Menüye dönüş
- **Ayarlar Butonu**: Sol üst köşede

## 🛠️ Teknik Detaylar
- **Motor**: Three.js r128
- **Kontrol**: PointerLockControls
- **Render**: WebGL ile gölge haritası
- **Dosya**: Tek HTML dosyası (main.html)
- **Bağımlılıklar**: Sadece Three.js CDN

## 🚀 Nasıl Oynanır?
1. `main.html` dosyasını bir web tarayıcısında açın
2. Herhangi bir yere tıklayarak oyunu başlatın
3. Görevlilerden saklanarak hedef tabloları çalın
4. Tüm seviyeleri tamamlayın!

## 📝 Geliştirme Notları
- Tüm seviyelerde duvar rendering sorunları giderildi
- Müzik otomatik başlatma sistemi eklendi
- Backdrop ile arka görünüm engellendi
- Fog sistemi optimize edildi
- Çoklu duvar yüzleri ile şeffaflık sorunu çözüldü

## 🎓 Proje Bilgileri
Bu proje, 3D web oyun geliştirme tekniklerini göstermek amacıyla Three.js kullanılarak geliştirilmiştir.

**Geliştirici**: [GitHub/nurigelb](https://github.com/nurigelb)

**Lisans**: MIT