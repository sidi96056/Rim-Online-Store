# Rim-Online-Store
**Rim Online Store** is a high-performance Next.js 16 platform for instant digital game card delivery. Supporting **Arabic/English** and currencies like **USD, MRU, TRY, &amp; USDT**, it bridges global gaming with local Mauritanian/Turkish payments (**Bankily, IBAN, Crypto**). Features include a Pro-Admin panel, automated code release, and VPN security


## 1. Proje Durum Raporu (Project Status Report)

Bu rapor, projenin mevcut durumunu ve teknik altyapısını özetler. Ortaklarına veya yatırımcılarına sunmak için mükemmeldir.

### 🚀 Proje Durum Raporu: Rim Online Store

**Mevcut Tarih:** 17 Mart 2026

**Durum:** Alfa / Temel Altyapı Tamamlandı

#### 1. Yönetici Özeti

"Rim Online Store", oyun ve abonelik kartlarının (PUBG, Free Fire, Netflix vb.) dijital satışı konusunda uzmanlaşmış, yüksek performanslı ve çift dilli (Arapça/İngilizce) bir e-ticaret platformudur. Proje; karmaşık çoklu para birimi mantığını, kapsamlı çift panel (Admin/Müşteri) sistemini ve küresel/yerel (Moritanya/Türkiye) pazarlara uygun ödeme altyapısını başarıyla entegre etmiştir.

#### 2. Teknik Yığın (Stack)

| Kategori | Teknoloji |
| --- | --- |
| **Framework** | **Next.js 16** (App Router, Server Components) |
| **Dil** | **TypeScript** (Sıkı Tip Güvenliği) |
| **Veritabanı** | **PostgreSQL** (Supabase üzerinden) |
| **ORM** | **Prisma** |
| **Kimlik Doğrulama** | **Supabase Auth** (Güvenli, çoklu oturum yönetimi) |
| **Tasarım** | **Tailwind CSS** + **Lucide Icons** |
| **Ödemeler** | **Stripe, Paddle, Kripto ve Yerel Banka Geçitleri** |

#### 3. Temel Başarılar ve Tamamlanan Özellikler

* **Mimari ve Veritabanı:** `User`, `Order`, `GameCode` ve `PaymentMethodConfig` içeren yüksek doğruluklu bir şema tasarlandı.
* **Stok Kontrolü:** Kodların yalnızca doğrulanmış ödemelerden sonra teslim edilmesini sağlayan `GameCode` mantığı uygulandı.
* **Ödeme ve Para Birimi Motoru:** USD, MRU, TRY ve USDT tam entegrasyonu sağlandı. Yönetici kontrollü dinamik döviz kurları eklendi.
* **Uzmanlaşmış Paneller:** Ürün kategorileri, hesap durumları ve işlem izleme özelliklerine sahip Admin Paneli ile müşteri işlem geçmişi ve bakiye takibini içeren Müşteri Paneli tamamlandı.
* **Küresel Yerelleştirme:** %100 Arapça ve İngilizce desteği, RTL (Sağdan Sola) tasarım optimizasyonu ve VPN tespiti ile güvenlik katmanları eklendi.

---

## 2. Yönetici Paneli Kullanım Kılavuzu (Admin User Manual)

Sistemin nasıl çalıştığını takip etmek için bu kılavuzu `ADMIN_GUIDE.md` olarak kaydedebilirsin.

### 🛠️ Yönetici Paneli Kullanım Kılavuzu: Rim Online Store

#### 1. Envanter ve Ürün Yönetimi

Mağazanızın kalbi, Ürün (Product) ve Oyun Kodu (GameCode) ilişkisidir.

* **Kategoriler:** Önce bunları oluşturun (Örn: "Battle Royale", "Streaming").
* **Ürünler:** Ürün adını ekleyin (Örn: "PUBG 660 UC").
* **Oyun Kodları:** Bu ayrı bir bölümdür. Dijital kodları buraya yüklemeli ve belirli bir ürünle ilişkilendirmelisiniz.
* **Durum (Status):** Kodlar varsayılan olarak `Available` (Müsait) olarak işaretlenir ve sipariş tamamlandığında `Sold` (Satıldı) olarak değişir.

#### 2. Küresel Para Birimi Kontrolü

Mağazanız dört farklı para birimini yönetir. **Para Birimi (Currency)** bölümü, kurlar değişse bile kârda kalmanızı sağlar.

* **Kur Belirleme:** Bir "Temel Para Birimi" belirlersiniz (Genellikle USD veya USDT).
* **Çarpanlar (Multipliers):** MRU ve TRY için oranı tanımlarsınız.
* **Örnek:** 1 USD = 34 TRY ise, çarpan alanına `34` girersiniz. Sitedeki tüm fiyatlar anında bu sayıya göre güncellenir.

#### 3. Sipariş İşleme Akışı

Müşteri bir kart satın aldığında, sipariş şu durumlardan geçer:

* **Pending (Beklemede):** Müşteri ödeme aşamasına geldi ama henüz ödemedi.
* **Awaiting Approval (Onay Bekliyor):** Müşteri **Bankily/Masrivi/IBAN** dekontu yükledi. (Manuel işlem gerekir: Banka uygulamanızı kontrol edin ve "Onayla"ya tıklayın).
* **Paid (Ödendi):** Ödeme doğrulandı (Stripe/Kripto için otomatiktir). Sistem Oyun Kodunu otomatik olarak teslim eder.
* **Completed (Tamamlandı):** Müşteri kodunu görüntüledi veya teslim aldı.

#### 4. Kullanıcı ve Güvenlik Yönetimi

**Hesaplar (Accounts)** bölümü üzerinden kimlerin siteyi kullanabileceğini kontrol edebilirsiniz.

* **Doğrulama:** Kullanıcının e-postasını veya telefonunu doğrulayıp doğrulamadığını görün.
* **VPN Tespiti:** Bir IP adresi VPN gösteriyorsa sistem bunu bayrakla işaretler. Şüpheli durumlarda hesabı `Blocked` (Engelli) yapabilirsiniz.
* **Durum Kontrolü:** Dolandırıcılar için `Banned`, yüksek limitli alışverişten önce kimlik onayı gerekenler için `Pending` durumunu kullanın.

#### 5. Ödemeler ve Promosyon Kodları

* **PaymentConfig:** Ödeme yöntemlerini açıp kapatmanızı sağlar. Örneğin, Bankily bakımda ise kod değiştirmeden buradan devre dışı bırakabilirsiniz.
* **İndirim Kodları:** Yüzdelik veya sabit tutarlı kodlar oluşturun. Bunları belirli kategorilerle sınırlayabilir veya son kullanma tarihi ekleyebilirsiniz.

---
