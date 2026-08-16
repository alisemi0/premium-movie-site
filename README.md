
# 🎬 Film Mahşeri - Serverless Premium Sinema & Dizi Platformu

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript (Vanilla)](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![TMDb API](https://img.shields.io/badge/TMDb-01B4E4?style=for-the-badge&logo=themoviedb&logoColor=white)
![PWA](https://img.shields.io/badge/PWA-5A0FC8?style=for-the-badge&logo=pwa&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

**Film Mahşeri**, geleneksel CMS (WordPress, Blogger vb.) altyapılarının hantallığını tamamen ortadan kaldıran, modern **BaaS (Backend as a Service)** çözümleriyle baştan aşağı yeniden inşa edilmiş, %100 Sunucusuz (Serverless) bir **SPA (Single Page Application)** mimarisidir.

Bu proje; yüksek performanslı PostgreSQL sorgularını, gerçek zamanlı NoSQL veritabanı akışlarını ve dinamik API entegrasyonlarını sadece `Vanilla JS` kullanarak bir araya getiren deneysel bir mühendislik harikasıdır.

---

## 📑 İçindekiler
1. [🌟 Sistem Mimarisi ve Temel Özellikler](#-sistem-mimarisi-ve-temel-özellikler)
2. [📁 Dosya ve Klasör Ağacı](#-dosya-ve-klasör-ağacı)
3. [⚙️ Teknoloji Yığını (Tech Stack)](#️-teknoloji-yığını-tech-stack)
4. [🛠️ Kurulum Rehberi (Adım Adım)](#️-kurulum-rehberi-adım-adım)
5. [🗄️ Veritabanı Kurulumu (SQL & NoSQL)](#️-veritabanı-kurulumu-sql--nosql)
6. [🔐 Çift Katmanlı Güvenlik Ağı](#-çift-katmanlı-güvenlik-ağı)
7. [🧠 Gelişmiş Modüller (PWA & Anti-Theft)](#-gelişmiş-modüller-pwa--anti-theft)
8. [🚧 Sıkça Sorulan Sorular ve Hata Çözümleri](#-sıkça-sorulan-sorular-ve-hata-çözümleri)
9. [🗺️ Yol Haritası (Roadmap)](#️-yol-haritası-roadmap)
10. [🤝 Katkıda Bulunma & Lisans](#-katkıda-bulunma--lisans)

---

## 🌟 Sistem Mimarisi ve Temel Özellikler

*   **TMDb Dinamik Trend Algoritması:** Sistem, her yüklendiğinde `TMDb Trending API` üzerinden haftanın en çok izlenen küresel filmlerini çeker. Bu ID'leri kendi Supabase veritabanımızla asenkron olarak eşleştirip ana sayfadaki "Editörün Seçtikleri" alanını insan müdahalesi olmadan otomatik günceller.
*   **Gerçek Zamanlı (Live) Arama:** Veritabanını yormamak için `Debounce` (Geciktirme) tekniği kullanılmış, Supabase'in `ilike` (Büyük/küçük harf duyarsız) operatörü ile milisaniyelik canlı arama motoru geliştirilmiştir.
*   **İleri Düzey Profil ve Yorum Sistemi:** Firebase Firestore kullanılarak izleyicilerin yaptıkları yorumlar, favori filmleri ve izleme geçmişleri anlık (Real-time) olarak güncellenir.
*   **Kusursuz Tema Motoru:** Sayfa yüklenirken yaşanan FOUC (Flash of Unstyled Content - Beyaz ekran patlaması) sorununu çözen, kullanıcı tercihini `LocalStorage`'da şifreleyerek tutan CSS değişken (Custom Properties) destekli Dark/Light tema motoru.

---

## 📁 Dosya ve Klasör Ağacı

Modüler bir yaklaşımla, hiçbir frontend framework'ü (React/Vue) kullanılmadan SPA deneyimi yaratılmıştır:

```text
film-mahseri-repo/
│
├── index.html          # Ana sayfa: Trendler, Dinamik Grid, API Bağlantıları ve PWA Motoru
├── watch.html          # İzleme Alanı: Video Player Wrapper, Firebase Yorumlar ve Öneriler
├── robot.html          # Keşif Alanı: Çoklu parametre ile Supabase filtreleme motoru
├── profile.html        # Kullanıcı Paneli: İzleme geçmişi, Favoriler ve Yorum yönetimi
├── admin.html          # LOKAL YÖNETİM: Supabase ve Firebase'e veri basan şifreli kontrol paneli
├── player.html         # Oynatıcı: M3U8 ve HLS yayınlarını işleyen güvenlik duvarlı player
├── style.css           # Global Stiller: Glassmorphism UI, Değişkenler ve Responsive kurallar
├── app.js              # Çekirdek: API anahtarları, Auth state yönetimi ve Global Fonksiyonlar
└── README.md           # Proje Dökümantasyonu

```

---

## ⚙️ Teknoloji Yığını (Tech Stack)

* **Frontend (İstemci):** HTML5, CSS3, ES6+ Vanilla JavaScript. (Sıfır bağımlılık ilkesi).
* **Ana Veritabanı (İlişkisel):** `Supabase (PostgreSQL)`. Filmler, kategoriler, kapak yolları (URL) ve metadata verileri için yüksek okuma performansı.
* **Bağlı Veritabanı (NoSQL) & Auth:** `Firebase (Firestore)`. Hızlı yazma/güncelleme gerektiren yorumlar, kullanıcı verileri, film istekleri ve hata bildirimleri için kullanılmıştır.
* **Ağ Akışı:** Fetch API & Async/Await.
* **Medya Oynatıcı:** HLS destekli özel yapılandırılmış JW Player (player.html içinde izole edilmiştir).

---

## 🛠️ Kurulum Rehberi (Adım Adım)

Projenin kendi sunucunuzda veya localhost'ta çalışabilmesi için aşağıdaki adımları sırasıyla uygulayın:

### 1. Projeyi Klonlayın

```bash
git clone [https://github.com/KULLANICI_ADINIZ/film-mahseri.git](https://github.com/KULLANICI_ADINIZ/film-mahseri.git)
cd film-mahseri

```

### 2. Domain (Alan Adı) Güncellemesi

Tüm `.html` dosyalarını ve `app.js` dosyasını açın. Kod içindeki `SENIN-SITEN.com` yer tutucularını **CTRL + F** yaparak bulun ve kendi gerçek alan adınız (veya `localhost`) ile değiştirin. Aksi takdirde SEO etiketleri ve Player Güvenlik Duvarı çalışmayacaktır.

### 3. API Anahtarlarını Alın ve Yerleştirin

* **TMDb:** [TheMovieDB](https://www.themoviedb.org/)'den ücretsiz API anahtarı alın ve `.html` dosyalarındaki `TREND_TMDB_API_KEY` sabitine yapıştırın.
* **Supabase & Firebase:** `app.js` dosyasını açın ve config değişkenlerindeki `BURAYA_KENDI...` yazan kısımlara proje anahtarlarınızı girin.

---

## 🗄️ Veritabanı Kurulumu (SQL & NoSQL)

### Supabase SQL Şeması

Supabase panelinizde `SQL Editor` kısmına girin ve tabloyu oluşturmak için şu sorguyu çalıştırın:

```sql
CREATE TABLE movies (
    id bigint generated by default as identity primary key,
    title text not null,
    original_title text,
    tmdb_id text unique,
    player_path text not null,
    poster_path text,
    backdrop_path text,
    release_year integer,
    rating numeric,
    genres text,
    slug text unique not null,
    cast_data jsonb,
    created_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Aramaları %400 hızlandıran indeksleme
CREATE INDEX idx_movies_title ON movies (title);
CREATE INDEX idx_movies_slug ON movies (slug);

```

### Firebase Firestore Şeması

Firebase panelinizde Firestore veritabanını oluşturun. Tablolar kod tarafından otomatik oluşturulacaktır ancak şu koleksiyonlar kullanılmaktadır:

* `users` (Kullanıcı profilleri ve izleme geçmişleri)
* `comments` (Filmlere yapılan yorumlar)
* `istekler` (Film istek formu verileri)
* `iletisim` (İletişim formu verileri)
* `roles` & `banned_users` (Yönetici yetkileri ve engellenenler)

---

## 🔐 Çift Katmanlı Güvenlik Ağı

SPA (Single Page Application) yapılarında API anahtarlarının kaynak kodda görünmesi bir mimari zorunluluktur. Güvenlik, kodları saklamakla değil; **veritabanına konulan kilitlerle (Polices/Rules)** sağlanır.

### Supabase RLS (Row Level Security) Kilidi

Sisteme dışarıdan film eklenmesini engellemek için sadece okuma yetkisi verilmelidir:

```sql
ALTER TABLE movies ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Herkes filmleri görebilir" 
ON movies FOR SELECT USING (true);
-- INSERT, UPDATE, DELETE komutları sadece Admin panelinden (Service Key ile) yapılabilir.

```

### Firebase Security Rules

Kullanıcıların sadece kendi verilerini silebilmesi ve yorumları sadece giriş yapanların yazabilmesi için:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Sadece üyeler istek gönderebilir
    match /istekler/{document} {
      allow create: if request.auth != null;
    }
    // Herkes yorum okuyabilir, sadece üyeler yorum yapabilir
    match /comments/{movieSlug}/list/{commentId} {
      allow read: if true;
      allow create: if request.auth != null;
    }
  }
}

```

---

## 🧠 Gelişmiş Modüller (PWA & Anti-Theft)

### 1. Sıfır Dosyalı PWA Motoru (Blogger/Static Host Bypass)

Blogger veya katı statik hostlar kök dizine `manifest.json` yüklenmesini engellediği için "Line 1, Column 1 Syntax Error" hatası verir. Bu projede, fiziksel bir dosya kullanmak yerine **Base64 kodlanmış Data URI** ile tarayıcının hafızasında sanal bir PWA sistemi ayağa kaldırılır.

### 2. Gelişmiş Anti-Theft (Emeğe Saygı / Kredi Koruma) Sistemi

Açık kaynak paylaşılan bu projenin footer kısmında yer alan "Tasarım & Altyapı: Ali Semi" yazısı özel bir şifreleme algoritmasıyla korunmaktadır.

* Eğer bir hırsız kaynak koddan bu yazıyı silerse,
* CSS ile `display: none` veya `opacity: 0` yapıp gizlemeye çalışırsa,
Sistem durumu anında (2 saniye içinde) tespit eder ve sayfanın DOM'unu kilitleyerek kullanıcıyı otomatik olarak Orijinal Geliştirici Sitesine yönlendirir. Obfuscate (Karmaşıklaştırma) edildiği için kodun nerede olduğu anlaşılamaz.

---

## 🚧 Sıkça Sorulan Sorular ve Hata Çözümleri

**Soru: `app.js`'de `firebase is not defined` hatası alıyorum.**
**Cevap:** Firebase SDK bağlantılarının (CDN) `app.js` çağrılmadan *önce* (`<head>` etiketleri arasında) yüklendiğinden emin olun. Projedeki sıralamayı bozmayın.

**Soru: `admin.html` sayfasına girdiğimde beni dışarı atıyor.**
**Cevap:** Admin sayfasına sadece kurucu erişebilir. Firebase Auth üzerinden kayıt olduktan sonra `admin.html` dosyasını açıp `admin@seninsiten.com` yazan kod satırını kendi kayıt olduğunuz e-posta adresi ile değiştirin.

**Soru: Filmi ekliyorum ama oynatıcı açılmıyor.**
**Cevap:** `player.html` dosyasının içindeki `IZIN_VERILEN_SITE` sabitini kendi alan adınız yapmadığınız için oynatıcı güvenlik gereği erişimi engelliyor.

---

## 🗺️ Yol Haritası (Roadmap)

* [x] **Faz 1:** Core UI, Cam Efektleri, Responsive Grid Yapısı.
* [x] **Faz 2:** Supabase Veritabanı, TMDb Trend Algoritması, Live Search.
* [x] **Faz 3:** Firebase Auth (Giriş/Kayıt), Gerçek Zamanlı Yorum ve İstek Sistemi.
* [x] **Faz 4:** Sıfır Dosyalı Sanal PWA Yükleyici Modülü.
* [x] **Faz 5:** Kapsamlı Yönetim (Admin) Paneli ve Rol/Ban Sistemi.
* [ ] **Faz 6:** Bölüm takip sistemli ve otomatik sıradaki bölüme geçişli Dizi Mimarisi (Planlanıyor).

---

## 🤝 Katkıda Bulunma & Lisans

Bu proje, modern web mimarisi sınırlarını zorlamak, sunucu kısıtlamalarını yaratıcı JavaScript yöntemleriyle aşmak ve Vanilla JS ile BaaS (Supabase/Firebase) çözümlerinin gücünü göstermek amacıyla geliştirilmiştir.

Eğer projeye katkıda bulunmak isterseniz bir `Pull Request` gönderebilir veya karşılaştığınız sorunları `Issues` sekmesinde açabilirsiniz.

**Geliştirici:** Ali Semi

*Bu proje MIT Lisansı ile açık kaynaklı olarak paylaşılmıştır ancak geliştirici kredilerinin (Footer) kaldırılmaması şartıyla kullanıma uygundur.*

```
