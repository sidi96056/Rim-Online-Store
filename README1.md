# 🎮 RIM Online Store

<div align="center">

![RIM Online Store](https://img.shields.io/badge/RIM-Online%20Store-7c3aed?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0yMSA2SDNhMSAxIDAgMCAwLTEgMXYxMGExIDEgMCAwIDAgMSAxaDE4YTEgMSAwIDAgMCAxLTFWN2ExIDEgMCAwIDAtMS0xem0tMTAgOWgtMnYtMmgyem0wLTRoLTJWOWgyeiIvPjwvc3ZnPg==)
![Next.js](https://img.shields.io/badge/Next.js-16-000000?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

**Your #1 destination for instant digital game cards, gift cards & subscriptions.**

*Targeting Mauritania 🇲🇷 and Turkey 🇹🇷 — with global reach.*

[🌐 Live Site](https://rim-store.vercel.app) · [✈️ Telegram Support](https://t.me/sidiahmed9) · [📋 FAQ](/app/faq)

</div>

---

## 📸 Screenshots

> *(Add screenshots of: Home page, Admin dashboard, Customer dashboard, Checkout modal, KYC tab, AI chatbot)*

---

## 🚀 Tech Stack

| Layer | Technology | Description |
|-------|-----------|-------------|
| **Frontend** | Next.js 16 + TypeScript | App Router, SSR, Client Components |
| **Database** | PostgreSQL (Supabase) | 22 Prisma models, relational |
| **ORM** | Prisma | Type-safe DB access + migrations |
| **Auth** | Supabase Auth + JWT | Role-based, session management |
| **Styling** | Tailwind CSS + CSS Variables | Dark theme, full responsive |
| **Payments** | Stripe + Paddle + Manual | 19 payment methods |
| **SMS / OTP** | Vonage → Twilio → Telegram | Cascading fallback system |
| **AI Chatbot** | Claude claude-sonnet-4-6 API | Offline FAQ fallback |
| **Deployment** | Vercel | Auto deploy, no GitHub needed |

---

## ✅ Completed Features

### 🔐 Authentication & Security
- [x] Supabase Auth + Prisma dual sync registration/login
- [x] Password reset via email link (10-minute token)
- [x] VPN detection: 1st = warning, 2nd = auto ban
- [x] 5 account statuses: Active / Pending / Blocked / Banned / Deleted
- [x] Role-based API protection (admin/user)
- [x] Login attempt logging (IP, user-agent, VPN status)

### 💳 Payment System (19 Methods)
- [x] Credit/Debit cards via **Stripe** or **Paddle** → USD
- [x] Crypto: **USDT TRC20, Binance, KuCoin, Bybit, OKX, Bitget** → USDT
- [x] Mauritania local: **Bankily, Masrivi, Sadead** → MRU
- [x] Turkey IBAN: **10 banks** (Ziraat, Vakıf, Akbank, İş, YapıKredi...) → TRY
- [x] Website balance — instant, no external payment
- [x] **3D Secure OTP** — SMS verification before card payment
- [x] Inactive payment method "Not Available" banner

### 🌍 Multi-Currency System
- [x] Admin sets rates: 1 USD = X MRU / TRY / USDT
- [x] Auto-display in correct currency by payment method
- [x] Real-time conversion table in customer dashboard

### 🪪 KYC & Phone Verification
- [x] Identity verification: selfie + ID/Passport/Driver's license
- [x] Phone OTP: **Vonage → Twilio → Telegram** fallback
- [x] OTP stored in **database** (survives server restarts)
- [x] Admin can verify phone/email manually
- [x] KYC required for Mauritanian local payments + refund protection

### 👑 Admin Dashboard
- [x] Account management — 5 status filters, balance add/remove
- [x] Product CRUD — EN/AR name, images, stock, price
- [x] Game code bulk upload (comma / newline / semicolon separated)
- [x] KYC approve/reject with reason
- [x] Payment method management — enable/disable, IBAN editing
- [x] Phone numbers for local methods (Bankily/Masrivi/Sadead)
- [x] Currency rate management (MRU/TRY/USDT)
- [x] Order management — approve/cancel, code assignment
- [x] Support ticket management
- [x] Telegram bot alerts (low stock, KYC, new orders)
- [x] Real-time stats — 30s auto refresh

### 📱 Customer Dashboard
- [x] Order history with game code display + copy
- [x] Balance in USD + local currency (MRU/TRY) simultaneously
- [x] KYC tab — phone OTP + identity status
- [x] Transaction history — last 50 entries
- [x] Exchange rate info bar

### 🤖 AI Customer Assistant
- [x] Floating chat widget — **left side**, above Telegram button
- [x] Claude claude-sonnet-4-6 API integration
- [x] **Offline FAQ fallback** — works without API key (9 common topics)
- [x] Auto Telegram redirect when question exceeds knowledge
- [x] EN/AR bilingual responses

### 🗣️ Language System
- [x] Persistent EN/AR with `localStorage` (`rim-lang` key)
- [x] Single source of truth — all pages sync automatically
- [x] Cross-tab sync via `storage` event listener
- [x] RTL support for Arabic on all pages

### 📄 Support Pages
- [x] `/about` — About Us
- [x] `/privacy-policy` — Privacy Policy
- [x] `/refund-policy` — Refund Policy (KYC required for refund)
- [x] `/cookies-policy` — Cookie Policy
- [x] `/terms` — Terms of Service (10 sections + Quick Nav)
- [x] `/faq` — FAQ Accordion (8 questions, EN/AR)
- [x] `/support` — Contact form → saved to DB + Telegram alert
- [x] `/track-order` — Order tracking (no code exposure)
- [x] `/how-to-redeem` — DB-synced product redemption guide

---

## 🗄️ Database Schema (22 Models)

```
User                  — accounts, balance, KYC, VPN status
KycSubmission         — identity document verification
OtpCode               — SMS OTP (DB-backed, restart-safe)
SupportTicket         — customer support messages
Order                 — orders, payment, approval
OrderItem             — order line items
GameCode              — codes (sold/unsold, auto-assign)
Product               — EN/AR name, category, stock, images
Category              — slug, image
PromoCode             — discount %, usage limits
Transaction           — balance movement history
PaymentMethodConfig   — 19 methods, IBAN, phone numbers
CurrencyConfig        — MRU/TRY/USDT rates
CartItem              — real-time cart sync
LoginAttempt          — IP, VPN, success logging
PasswordResetToken    — 10-min expiry tokens
AdminNotification     — low stock, KYC alerts
CustomerNotification  — read/unread per user
SiteStatus            — maintenance mode
Review                — product ratings (moderated)
GameRequest           — user product requests
```

---

## 📁 Project Structure

```
rim_online_store/
├── app/
│   ├── admin/page.jsx              ← Full admin dashboard
│   ├── dashboard/page.jsx          ← Customer dashboard
│   ├── about/page.tsx
│   ├── privacy-policy/page.tsx
│   ├── refund-policy/page.tsx
│   ├── cookies-policy/page.tsx
│   ├── terms/page.tsx
│   ├── faq/page.tsx
│   ├── support/page.tsx
│   ├── track-order/page.tsx
│   ├── how-to-redeem/page.tsx
│   ├── login/page.tsx
│   ├── register/page.tsx
│   ├── components/
│   │   ├── CheckoutModal.tsx       ← 3D OTP + all payments
│   │   ├── ChatWidget.tsx          ← AI assistant (left side)
│   │   ├── SharedComponents.tsx    ← Footer (linked), Telegram, Notifications
│   │   └── ...
│   ├── context/
│   │   ├── StoreContext.tsx        ← Global state + lang persistence
│   │   └── CurrencyContext.tsx
│   ├── hooks/
│   │   └── useLang.ts              ← Shared language hook (all pages)
│   └── api/                        ← 50+ API routes
│       ├── auth/
│       ├── admin/
│       ├── payment/
│       └── user/
├── lib/
│   ├── prisma.ts
│   ├── supabase.ts / supabase-server.ts
│   ├── otp-store.ts               ← DB-backed OTP
│   ├── sms.ts                     ← Vonage→Twilio→Telegram
│   ├── currency.ts
│   └── admin-guard.ts
├── prisma/schema.prisma            ← 22 models
└── middleware.ts                   ← VPN, status, route protection
```

---

## ⚙️ Environment Variables

```env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
DATABASE_URL=

# SMS
VONAGE_API_KEY=
VONAGE_API_SECRET=
VONAGE_FROM_NUMBER=+90XXXXXXXXXX
TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_PHONE_NUMBER=

# Telegram
TELEGRAM_BOT_TOKEN=
TELEGRAM_ADMIN_CHAT_ID=
NEXT_PUBLIC_TELEGRAM_USERNAME=sidiahmed9

# Payments
STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=
PADDLE_API_KEY=
PADDLE_WEBHOOK_SECRET=
NEXT_PUBLIC_PAYMENT_PROVIDER=paddle

# AI
ANTHROPIC_API_KEY=

# Config
REQUIRE_ADMIN_APPROVAL=false
REQUIRE_EMAIL_VERIFICATION=true
NEXT_PUBLIC_SITE_DOWN=false
INTERNAL_API_SECRET=rim-internal-2024
```

---

## 🚀 Deploy

```bash
# Install dependencies
npm install

# Push database schema
npx prisma db push
npx prisma generate

# Seed payment methods
node scripts/seed-payment-methods.js

# Make yourself admin
node scripts/make-admin.js your@email.com

# Deploy to production
vercel --prod
```

---

## 📄 License

© 2026 RIM Online Store — All rights reserved.

Built with ❤️ by **Sidi Ahmed** · [Telegram](https://t.me/sidiahmed9)
