# 🏡 Reservation Platform — Showcase & Canlı Demo

[![Live Demo](https://img.shields.io/badge/Canl%C4%B1%20Demo-reservation--omega--nine.vercel.app-blue?style=for-the-badge&logo=vercel&logoColor=white)](https://reservation-omega-nine.vercel.app/)
[![Next.js](https://img.shields.io/badge/Next.js-16.3.4-black?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?style=for-the-badge&logo=react&logoColor=white)](https://react.dev/)
[![Supabase](https://img.shields.io/badge/Supabase-Database%20%26%20Auth-emerald?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)
[![License](https://img.shields.io/badge/Status-Canl%C4%B1da%20Yay%C4%B1nda-success?style=for-the-badge)](#)

> Modern konaklama ve tatil kiralama platformlarından ilham alınarak geliştirilmiş; uçtan uca üyelik, ilan yönetimi, dinamik takvim kilitleri, yönetici onay paneli ve e-posta bildirim motoru barındıran **tam teşekküllü (Full-Stack) Rezervasyon Platformu**.

---

## 🌐 Canlı Uygulama

Projeyi doğrudan tarayıcınızda canlı olarak test edebilirsiniz:  
👉 **[https://reservation-omega-nine.vercel.app/](https://reservation-omega-nine.vercel.app/)**

---

## 📸 Projeye Genel Bakış

Bu depo, projenin mimarisini, teknik yeteneklerini ve canlı demosunu sergilemek amacıyla hazırlanmış vitrin (**showcase**) deposudur. Güvenlik, veritabanı şemaları ve özel iş mantığı nedeniyle ana kaynak kodlar özel (**private**) depoda barındırılmaktadır.

---

## 🚀 Öne Çıkan Özellikler

### 1. 👥 Kullanıcı Yetkilendirme & Profil Yönetimi
* **Kayıt ve Güvenlik:** Ad, Soyad, Doğum Tarihi, E-posta, Şifre ve Şifre Tekrarı doğrulaması.
* **E-posta Aktivasyonu:** Supabase Auth ve Gmail SMTP entegrasyonuyla gelen kutusuna aktivasyon linki gönderimi.
* **Hesap & Profil Paneli (`/profile`):** Kullanıcının kişisel bilgilerini güncellemesi ve güvenli şifre değiştirme ekranı.

### 2. 🔍 İlan Keşfi, Arama & Canlı Filtreleme
* **Akıllı Arama Çubuğu:** İlan başlığı, ilçe veya şehir bazında canlı metin araması.
* **Dinamik Şehir Seçici:** Sistemdeki aktif ilanların konumlarını otomatik algılayan şehir dropdown filtresi.
* **Bütçe Filtresi:** Gecelik maksimum tutara göre anında sonuç filtreleme.
* **Kategori Navigasyonu:** Evler, Oteller, Etkinlikler, Konserler, Aktiviteler ve Spor kategorileri arasında geçiş *(yalnızca ana sayfada görünür, alt sayfalarda arayüzü sade tutar)*.

### 3. 📅 Akıllı Rezervasyon Takvimi & Çift Rezervasyon Koruması
* **Tarih Aralığı Seçimi:** Giriş ve Çıkış tarihlerinin görsel takvim üzerinden seçilmesi.
* **Misafir Sayacı:** Yetişkin, Çocuk ve Bebek misafir sayılarına göre anlık kapasite kontrolü.
* **Dinamik Fiyatlandırma:** Gün sayısı x gecelik ücret üzerinden toplam tutar hesaplama.
* **Otomatik Takvim Kilitleme:** Onaylanan ve onay bekleyen tüm tarihler takvimde anında kilitlenir (grileşir), başka kullanıcıların aynı tarihlere rezervasyon yapması hem arayüzde hem de veritabanı seviyesinde engellenir.

### 4. 🛠️ Yönetici (Admin) Kontrol Merkezi
* **Korumalı Rotalar:** Next.js Middleware ve PostgreSQL RLS ile sadece yetkili yöneticilere açık `/admin` alanı.
* **İlan Ekleme & Yönetimi:**
  * Supabase Storage ile çoklu görsel yükleme.
  * Olanaklar (Wifi, Havuz, Otopark vb.), konum, ulaşım rehberi ve kural tanımlama.
  * İlan yayından kaldırma (gizleme) ve silme işlemleri.
* **Rezervasyon Onay Masası (`/admin/reservations`):**
  * **Bekleyenler, Onaylananlar** ve **Red / İptal** sekmeleri.
  * Tek tıkla rezervasyon **Onaylama** veya **Reddetme**.

### 5. 📧 E-posta ve Bildirim Sistemi
* **Yöneticiye Anlık Rezervasyon Maili:** Misafir talep oluşturduğu anda yöneticiye misafirin Adı-Soyadı, E-postası, tarihleri ve toplam tutarını içeren özel tasarımlı HTML maili gönderilir.
* **Misafire Durum Maili:** Yönetici rezervasyonu onayladığında veya reddettiğinde misafire bilgilendirme e-postası iletilir.
* **Site İçi Zil Bildirimleri (`/notifications`):**
  * Header'da anlık okunmamış bildirim sayısı rozeti (badge).
  * Bildirime tıklandığında **otomatik okundu işaretleme** ve doğrudan ilgili rezervasyon detayına **akıllı yönlendirme**.

### 6. ❌ Misafire İptal Hakkı
* Kullanıcılar **"Rezervasyonlarım"** (`/reservations`) sayfasından bekleyen veya onaylanan rezervasyonlarını diledikleri zaman iptal edebilirler.
* İptal edildiğinde takvimdeki kilit otomatik olarak kalkar ve yöneticiye anında bilgilendirme e-postası gider.

---

## 🛠️ Mimari ve Teknoloji Yığını

| Alan | Kullanılan Teknoloji / Kütüphane |
| :--- | :--- |
| **Framework** | **Next.js 16** (App Router, Server Components & Turbopack) |
| **Frontend Kütüphanesi** | **React 19** & TypeScript |
| **Veritabanı & BaaS** | **Supabase** (PostgreSQL 15+, Triggers, PL/pgSQL Fonksiyonları) |
| **Güvenlik** | **Row Level Security (RLS)** ile veri izolasyonu |
| **Depolama (Storage)** | **Supabase Storage** (Görsel optimizasyonu ve CDN) |
| **E-posta Motoru** | **Nodemailer** (Gmail SMTP Entegrasyonu) |
| **İkonlar & Tarih** | **Lucide React**, `date-fns` (Türkçe yerelleştirme) |
| **Tasarım & Stil** | Özel CSS Design System (CSS Modules, Glassmorphism, HSL Renk Paleti) |
| **Dağıtım (Hosting)** | **Vercel** (Global Edge Network, Otomatik SSL) |

---

## 🔒 Güvenlik Mimarisi

* **Rol Tabanlı Erişim:** Admin ve standart kullanıcı yetkileri PostgreSQL veritabanı seviyesinde RLS (Row Level Security) ile birbirinden ayrılmıştır.
* **Veri Gizliliği:** Kullanıcılar sadece kendilerine ait rezervasyon ve bildirimleri görebilir; takvim kilitlerinde diğer kullanıcıların kişisel bilgileri sızdırılmaz.
* **Tersine Mühendislik Koruması:** Ortam değişkenleri (`.env.local`), veritabanı şifreleri ve SMTP kimlik bilgileri sunucu tarafında (Server-Side) izole edilmiştir.

---

## 👨‍💻 Geliştirici & İletişim

**Engin Basmaya**
* **Canlı Proje:** [https://reservation-omega-nine.vercel.app/](https://reservation-omega-nine.vercel.app/)
* **GitHub:** [@enginbasmaya](https://github.com/enginbasmaya)
* **İletişim:** enginbasmaya@gmail.com

---

*(c) 2026 Reservation Platform. Tüm hakları saklıdır.*
