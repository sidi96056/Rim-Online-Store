# 🎮 Rim Online Store

> **Dijital Oyun Kartları E-Ticaret Platformu**  
> Full-stack Next.js · Prisma · Supabase · TypeScript

---

## 📋 Proje Tanıtım Formu

| Alan | Bilgi |
|------|-------|
| **Grup İsmi** | RIM STORE — E-Commerce Dev Team |
| **Grup Sözcüsü** | Sidi Ahmed |
| **Proje Adı** | Rim Online Store — Dijital Oyun Kartları Platformu |
| **Framework** | Next.js 15 (App Router) + TypeScript |
| **Veritabanı** | PostgreSQL via Supabase (Frankfurt EU) |
| **ORM** | Prisma v6 |
| **Auth** | Supabase Auth (SSR) |
| **Başlangıç** | Mart 2026 |
| **Durum** | 🟡 Aktif Geliştirme — %85 Tamamlandı |

---

## 🎯 Projenin Tanımı

**Rim Online Store**, oyuncuların PUBG UC, Free Fire Diamonds, Netflix, Google Play, Apple Store gibi dijital oyun ve abonelik kartlarını anında satın alabileceği tam kapsamlı bir e-ticaret platformudur.

Platform **üç ana bileşenden** oluşmaktadır:

- 🛒 **Müşteri Mağazası** — Ürün listeleme, sepet, ödeme, anlık kod teslimi
- 👤 **Müşteri Paneli** — Sipariş takibi, KYC doğrulama, bildirimler, bakiye
- 🔧 **Yönetici Paneli** — Ürün/kategori/stok yönetimi, kullanıcı kontrolü

---

## 🚀 Projenin Amacı

- 🌍 Mauritanya ve Türkiye'deki oyunculara **yerel ödeme** (Bankily, Masrivi, Sadead) ile anlık erişim
- ₿ **Kripto para** (USDT, Binance, KuCoin, Bybit, OKX, Bitget) desteği
- 🌐 **Çok dilli** (Arapça/İngilizce RTL), **çok para birimli** (USD/MRU/TRY/EUR)
- ⚡ **Otomatik oyun kodu teslimi** — ödeme onayı anında
- 🪪 **KYC sistemi** — yerel ödemeler için güvenli kimlik doğrulama
- 🔔 **Gerçek zamanlı bildirimler** — uygulama içi + e-posta + Telegram

---

## 💡 Çözdüğü Problemler

| Problem | Çözüm |
|---------|-------|
| Mauritanyalılar Visa/Mastercard kullanamıyor | Bankily/Masrivi/Sadead entegrasyonu |
| Manuel kod teslimi saatler alıyor | Otomatik GameCode sistemi → **< 5 sn teslimat** |
| Döviz kuru belirsizliği | DB'den gerçek zamanlı MRU/TRY/EUR dönüşümü |
| Sahte hesap riski | KYC zorunluluğu (yerel ödeme için) |
| Stok takibi zorluğu | Her ürün için ayrı `GameCode` tablosu |

---

## 🔧 Teknik Altyapı

```
┌─────────────────────────────────────────────────────┐
│                  RIM ONLINE STORE                    │
├─────────────┬───────────────────┬───────────────────┤
│  FRONTEND   │     BACKEND       │    SERVICES        │
│             │                   │                    │
│ Next.js 15  │ Next.js API       │ Supabase Auth      │
│ React 18    │ Routes (REST)     │ Supabase Storage   │
│ TypeScript  │ Prisma ORM v6     │ Nodemailer (SMTP)  │
│ CSS Modules │ PostgreSQL        │ Telegram Bot API   │
│ Tailwind    │ bcryptjs          │ Paddle / Stripe    │
└─────────────┴───────────────────┴───────────────────┘
```

| Katman | Teknoloji |
|--------|-----------|
| Frontend | Next.js 15, React 18, TypeScript, CSS Modules |
| Backend | Next.js API Routes, Prisma v6, PostgreSQL |
| Auth | Supabase Auth (SSR), Admin SDK |
| Veritabanı | Supabase PostgreSQL — Frankfurt EU |
| E-posta | Nodemailer (Gmail SMTP) — 8 şablon |
| Telegram | Telegram Bot API |
| Ödeme | Paddle, Stripe, Bankily, Masrivi, Sadead, USDT/Binance/KuCoin/Bybit/OKX/Bitget |
| Responsive | 5 breakpoint (480 / 768 / 1024 / 1440px) |
| Depolama | Supabase Storage (KYC belgeleri) |
| Node.js | v22 LTS (Prisma WASM uyumluluğu) |

---

## 🗄️ Veritabanı Modelleri (17 Model)

```prisma
User                  // KYC, blok, bakiye, telegramUsername
KycSubmission         // Selfie + kimlik ön/arka
Product               // Çift dil (EN/AR), stok, featured
Category              // Slug, görsel
GameCode              // productId, sold, orderId
Order                 // userId, paymentMethod, approved
OrderItem             // productName, price, qty
PromoCode             // usedBy[] ile kişi başı limit
Transaction           // Bakiye hareketleri
PaymentMethodConfig   // Ülke bazlı aktif/pasif
CurrencyConfig        // USD/MRU/TRY/EUR kurları
AdminNotification     // Yönetici bildirimleri
CustomerNotification  // Müşteri bildirimleri (çan)
Review                // Ürün yorumu (onay gerektirir)
GameRequest           // 10+ talep = otomatik bildirim
LoginAttempt          // Giriş denemesi kaydı
PasswordResetToken    // 1 saatlik token
```

---

## ✅ Tamamlanan Özellikler

### 🛒 Müşteri Mağazası
- [x] Dinamik ana sayfa — Hero section, kategori kartları, ürün grid
- [x] Canlı arama — DB'den gerçek zamanlı (300ms debounce)
- [x] Ürün detay sayfası — çoklu görsel, seçenek, stok kontrolü
- [x] Sepet — adet kontrolü, yerel para birimi
- [x] Checkout — 3 adımlı, promosyon kodu, KYC kontrolü
- [x] Çok para birimi — USD / MRU / TRY / EUR
- [x] Çift dil — İngilizce / Arapça (RTL)
- [x] Koyu / Açık tema
- [x] Canlı satış bildirimleri (ticker)

### 💳 Ödeme Sistemi
- [x] Website Bakiyesi
- [x] Kredi Kartı / PayPal (Paddle)
- [x] Stripe
- [x] USDT TRC20, Binance (UID: 466857557), KuCoin, Bybit, OKX, Bitget
- [x] Bankily, Masrivi, Sadead (KYC zorunlu)

### 👤 Müşteri Paneli
- [x] Sipariş geçmişi + oyun kodları
- [x] Bakiye ve işlem geçmişi
- [x] KYC doğrulama (Supabase Storage)
- [x] Bildirimler — filtreli, 30 sn otomatik yenileme
- [x] Profil — Telegram username

### 🔧 Yönetici Paneli
- [x] Dashboard istatistikleri
- [x] Sipariş yönetimi
- [x] Hesap yönetimi (blok/bant/KYC talep/bakiye)
- [x] KYC inceleme (onay/red + gerekçe)
- [x] Ürün + oyun kodu yönetimi
- [x] Kategori yönetimi
- [x] Promosyon kodu sistemi
- [x] Ödeme yöntemi yapılandırması
- [x] Döviz kuru yönetimi
- [x] Bildirimler sayfası
- [x] Site durumu (bakım modu)

### 🔔 Bildirim Sistemi

| Olay | 🔔 Uygulama | 📧 E-posta | ✈️ Telegram |
|------|------------|-----------|------------|
| Kayıt (Hoş geldin) | — | ✅ | — |
| KYC gönderildi | ✅ | ✅ | — |
| KYC onaylandı/reddedildi | ✅ | ✅ | ✅ (kullanıcı) |
| Sipariş tamamlandı + kodlar | ✅ | ✅ | ✅ (kullanıcı) |
| Promosyon kodu duyurusu | ✅ (tümü) | ✅ (tümü) | ✅ (admin) |
| Bakiye eklendi/düşüldü | ✅ | ✅ | ✅ (kullanıcı) |
| Hesap blok/bant/geri al | ✅ | ✅ | ✅ (kullanıcı) |
| Oyun talebi karşılandı | ✅ | ✅ | ✅ (kullanıcı) |
| Oyun talebi 10+ kişi | ✅ (admin) | — | ✅ (admin) |

---

## 🔌 API Rotaları (~40+ rota)

```
POST   /api/register                          Kayıt + hoş geldin email
GET    /api/kyc                               KYC durumu sorgula
POST   /api/kyc                               KYC gönder + email + admin bildirim
POST   /api/orders                            Sipariş + kod ata + bildirim + email
GET    /api/products/search?q=               Canlı arama (DB)
GET    /api/user/notifications               Müşteri bildirimleri
PUT    /api/user/notifications               Okundu işaretle
PUT    /api/user/telegram                    Telegram username kaydet
POST   /api/admin/send-notification          Manuel bildirim (1 kişi veya tümü)
POST   /api/admin/promo-codes/notify         Promosyon duyurusu (app+email+tg)
PUT    /api/admin/kyc/[id]                   KYC onayla/reddet + email + bildirim
PUT    /api/admin/accounts/[id]              Hesap işlemleri + email + bildirim
POST   /api/admin/customers/[id]/balance     Bakiye + email + bildirim
PUT    /api/admin/requests/[id]              Oyun talebi karşıla + tüm kanallar
GET    /api/admin/products/codes?productId=  Oyun kodlarını listele
POST   /api/admin/products/codes             Toplu kod ekle (virgül/satır/noktalı virgül)
```

---

## 📱 Responsive Tasarım

| Kırılma Noktası | Hedef Cihazlar | Özellikler |
|----------------|----------------|-----------|
| `< 480px` | iPhone 11, Galaxy S24 Ultra | 2 sütun grid, modal alt kaymaca, 44px tap target, `100dvh`, admin bottom tab |
| `480–767px` | Büyük telefonlar | 2 sütun grid, yan yana butonlar |
| `768–1023px` | iPad Pro 12.9, Galaxy Tab S9 | 3 sütun grid, 52px girdi, ikon sidebar |
| `1024–1439px` | Dell XPS 13, Zephyrus G14 | Tam sidebar 220px, 1100px konteyner |
| `1440px+` | MacBook Pro 16 M3 | 1440px konteyner, büyük fontlar, 5 sütun grid |

**Ek özellikler:**
- Safe area insets (iPhone 14 Pro Max çentik desteği)
- `hover: none` — dokunmatik ekranlarda hover animasyonu kaldırıldı
- Retina/HiDPI görüntü optimizasyonu (MacBook Pro 16, Dell XPS 4K)

---

## 📊 Proje Durumu

| Modül | Durum | Not |
|-------|-------|-----|
| Müşteri Mağazası | ✅ Tamamlandı | Canlı |
| Checkout & Ödeme | ✅ Tamamlandı | 8 ödeme yöntemi |
| Oyun Kodu Otomasyonu | ✅ Tamamlandı | < 5 sn teslimat |
| KYC Sistemi | ✅ Tamamlandı | Supabase Storage |
| Müşteri Paneli | ✅ Tamamlandı | 6 sekme |
| Yönetici Paneli | ✅ Tamamlandı | 11 bölüm |
| Bildirim Sistemi | ✅ Tamamlandı | App + Email + Telegram |
| E-posta Şablonları | ✅ Tamamlandı | 8 ayrı şablon |
| Responsive CSS | ✅ Tamamlandı | 5 breakpoint |
| Promosyon Kodu | ✅ Tamamlandı | Kişi başı limit |
| Oyun Talebi | ✅ Tamamlandı | 10+ = otomatik bildirim |
| Yorum Sistemi | ✅ Tamamlandı | Onay gerektirir |
| Binance Pay Otomatik | ⏳ Bekliyor | Merchant hesabı gerekli |
| Production Deployment | ⏳ Bekliyor | Vercel / VPS |

---

## ⚙️ Kurulum

```bash
# Bağımlılıkları yükle
npm install
npm install --save-dev prisma dotenv

# Veritabanını kur
npx prisma db push
npx prisma generate

# Seed verileri
node scripts/seed-payment-methods.js
node scripts/sync-supabase-user.js

# Geliştirme sunucusu
npm run dev
# → http://localhost:3000
```

---

## 🔑 Ortam Değişkenleri

```env
# Veritabanı
DATABASE_URL=postgresql://...

# Supabase
NEXT_PUBLIC_SUPABASE_URL=https://xxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJ...
SUPABASE_SERVICE_ROLE_KEY=eyJ...

# Ödeme
NEXT_PUBLIC_PAYMENT_PROVIDER=paddle
PADDLE_API_KEY=...
STRIPE_SECRET_KEY=...

# E-posta (Gmail SMTP)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_SECURE=false
EMAIL_USER=youremail@gmail.com
EMAIL_PASS=your_app_password

# Telegram
TELEGRAM_BOT_TOKEN=...
TELEGRAM_CHAT_ID=...

# Site
NEXTAUTH_URL=http://localhost:3000
NEXT_PUBLIC_TELEGRAM_USERNAME=sidiahmed9
NEXT_PUBLIC_USDT_ADDRESS=TS6XLCy5qsEELt6nGU4EvJfVoUnn9x5ph8
```

---

## 🏗️ Proje Yapısı

```
C:\RimStore\
├── app/
│   ├── api/                    # ~40+ API rotası
│   │   ├── admin/              # Yönetici API'leri
│   │   ├── user/               # Kullanıcı API'leri
│   │   ├── payment/            # Ödeme webhook'ları
│   │   ├── orders/             # Sipariş işlemleri
│   │   ├── kyc/                # KYC doğrulama
│   │   └── ...
│   ├── components/             # React bileşenleri
│   │   ├── Navbar.tsx          # Canlı arama + bildirim çanı
│   │   ├── Hero.tsx            # Dinamik kategori kartları
│   │   ├── CheckoutModal.tsx   # 3 adımlı ödeme
│   │   ├── NotificationBell.tsx# Gerçek zamanlı bildirimler
│   │   ├── NotificationsPage.tsx
│   │   ├── ReviewSection.tsx   # Ürün yorumları
│   │   └── GameRequestWidget.tsx
│   ├── context/
│   │   ├── StoreContext.tsx    # Global state
│   │   └── CurrencyContext.tsx # Döviz dönüşümü
│   ├── admin/                  # Yönetici paneli
│   ├── dashboard/              # Müşteri paneli
│   ├── products/[id]/          # Ürün detay sayfası
│   └── globals.css             # Global stiller + responsive
├── lib/
│   ├── mailer.ts               # 8 e-posta şablonu
│   ├── notify.ts               # Bildirim helper'ı
│   ├── prisma.ts               # Prisma client
│   ├── admin-guard.ts          # API koruması
│   └── supabase.ts             # Supabase client
├── prisma/
│   └── schema.prisma           # 17 model
└── scripts/
    ├── seed-payment-methods.js
    └── sync-supabase-user.js
```

---

## 👨‍💻 Geliştirici

**Sidi Ahmed** — Grup Sözcüsü  
Proje: Rim Online Store  
Tarih: Mart 2026  

---

*Next.js 15 · Prisma · Supabase · TypeScript · Nodemailer · Telegram Bot API*
