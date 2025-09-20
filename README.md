# 🎮 Taş Kağıt Makas Oyunu

Vue.js ile geliştirilmiş bir Taş Kağıt Makas oyunudur.

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

## Ekran Görüntüleri
Oyuna başlamadan bilgilendirme mesajı
<img width="700" height="500" alt="bilgi" src="https://github.com/user-attachments/assets/a6aefc82-b56c-446e-9257-fadcc6e84c44" />
<img width="700" height="500" alt="bilgi2" src="https://github.com/user-attachments/assets/021b407f-123f-4a66-bd7d-25f385ebcd00" />

Tur seçimi sayfası
<img width="700" height="500" alt="tur" src="https://github.com/user-attachments/assets/851bffde-fcc0-43b1-a893-0b3a8eeb0672" />

Oyun başlangıç sayfası
<img width="700" height="500" alt="ana" src="https://github.com/user-attachments/assets/ade18a57-bbbf-40bd-9f3c-59fa28bcf206" />

<img width="700" height="500" alt="1" src="https://github.com/user-attachments/assets/86928dd5-2a73-4e37-aa56-bba659a9dd4c" />
<img width="700" height="500" alt="2" src="https://github.com/user-attachments/assets/d237269b-564f-4d7d-9abe-dbbe7598b339" />
<img width="700" height="500" alt="3" src="https://github.com/user-attachments/assets/484677cd-ce51-4c7d-a254-81ea6952f39f" />

Kazanma sayfası
<img width="700" height="500" alt="kazanma" src="https://github.com/user-attachments/assets/2d847d2d-b804-46b3-8781-6d3b4c2de5db" />

Kaybetme sayfası
<img width="700" height="500" alt="kaybetme" src="https://github.com/user-attachments/assets/e40722a8-669e-4f41-a67b-01b3259edd7f" />








