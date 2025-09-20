# 🎮 Taş Kağıt Makas Oyunu

Vue.js ile geliştirilmiş interaktif bir Taş Kağıt Makas oyunu. Modern arayüzü ve kullanıcı dostu deneyimi ile klasik oyunu web ortamında deneyimleyin.

## Özellikler

- **Interaktif Arayüz**: Modern ve kullanıcı dostu tasarım
- **Esnek Tur Sistemi**: 1-10 arası tur sayısı seçimi
- **Gerçek Zamanlı Skor**: Anlık skor takibi
- **Oyun Kuralları**: Başlangıçta detaylı kural açıklaması
- **Responsive Tasarım**: Tüm cihazlarda uyumlu çalışma

## Nasıl Oynanır

1. **Başlangıç**: Sayfa açıldığında oyun kuralları gösterilir
2. **Tur Sayısı**: 1-10 arasında tur sayısını seçin
3. **Oyunu Başlatın**: "Oyunu Başlat" butonuna tıklayın
4. **Hamle Yapın**: TAŞ, KAĞIT veya MAKAS butonlarından birini seçin
5. **Sonuç**: Bilgisayar da hamlesini yapar ve sonuç gösterilir
6. **Kazanan**: En çok turu kazanan oyunu alır

## Oyun Kuralları

- **Taş** → Makas'ı yener
- **Makas** → Kağıt'ı yener
- **Kağıt** → Taş'ı yener
- Aynı hamle seçilirse berabere kalınır

## Kurulum ve Çalıştırma

### Gereksinimler

- Node.js (v16 veya üzeri)
- npm veya yarn

### Kurulum

```bash
# Depoyu klonlayın
git clone [repository-url]

# Proje dizinine gidin
cd tas-kagit-makas

# Bağımlılıkları yükleyin
npm install
```

### Geliştirme Modunda Çalıştırma

```bash
npm run dev
```

Tarayıcınızda `http://localhost:5173` adresini açın.

### Production Build

```bash
npm run build
```

### Build Önizleme

```bash
npm run preview
```

## Teknolojiler

- **Vue.js 3** - Progressive JavaScript Framework
- **Vite** - Modern build tool
- **JavaScript (ES6+)** - Modern JavaScript özellikleri
- **CSS3** - Modern stil özellikleri ve animasyonlar
- **HTML5** - Semantic markup

