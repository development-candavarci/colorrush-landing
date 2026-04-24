# Color Rush — Landing Page

Tek sayfa (tam statik) pazarlama + tanıtım sitesi. Unity 6 mobil oyun Color Rush: Araba Oyunu için App Store + Google Play listing destek, press kit, privacy/terms host.

**Konum:** `Color Rush Araba Oyunu/website/`
**Üretim tarihi:** 2026-04-24
**Sürüm:** v1.0
**Dil:** Türkçe (ana) + İngilizce (dil toggle)

---

## 📁 Dosya Yapısı

```
website/
├── index.html              Ana sayfa (1644 satır, 10 section, TR+EN)
├── privacy.html            Gizlilik Politikası (KVKK + GDPR uyumlu)
├── terms.html              Kullanım Şartları
├── robots.txt              SEO temel + AEO bots allow
├── sitemap.xml             3 URL (ana + privacy + terms), hreflang dahil
├── llms.txt                AEO/GEO — LLM accessible content map
├── favicon.svg             4-renk palet logo (scalable)
├── README.md               Bu dosya
└── assets/
    ├── og/
    │   └── hero-og.png     OG image (1200×630 hedef — şu an game banner)
    └── screenshots/        6 gameplay ekran görüntüsü
        ├── 01-mainmenu.png
        ├── 02-gameplay.png
        ├── 03-gameover.png
        ├── 04-garage.png
        ├── 05-tutorial.png
        └── 06-store.png
```

**Toplam boyut:** ~3.5 MB

---

## ✅ Neler Uygulandı (Modül Referansları)

### Modül 2 — İkna Mimarisi (CRO)
- Hero 6-element formülü (H1 + subheadline + primary/secondary CTA + visual + trust bar)
- 10 psikolojik silah: Anchoring, Scarcity, Social Proof, Reciprocity, Authority, Commitment, Loss Aversion, Peak-End, Von Restorff, Paradox of Choice
- 3-kart mekanik (3-tier decision)
- 6-feature USP grid
- 4-adım nasıl oynanır (Fogg B=MAP Ability)
- 3 testimonial (Social Proof + Authority)
- Final CTA (Peak-End Rule)

### Modül 3 — SEO Mimarisi
- JSON-LD @graph 6 block: Organization + WebSite + VideoGame + MobileApplication + FAQPage + BreadcrumbList
- Meta title 55 char + description 155 char (ASO destek keyword)
- Open Graph + Twitter Card + hreflang TR/EN + canonical
- Semantic HTML5 (section, article, figure, details)
- Core Web Vitals hedef: LCP <1.8s, INP <150ms, CLS <0.05
- Image optimization: explicit width/height, loading=lazy (hero hariç), fetchpriority=high (hero)
- Font: Inter + Space Grotesk, preload woff2, font-display swap
- AEO/GEO: llms.txt + FAQ schema + yapılandırılmış özet

### Modül 7 — Kalite Kapısı
- Türkçe diacritic %100 (TRAP-1 zero tolerance — 0 match)
- WCAG 2.2 AA: color contrast 4.5:1, keyboard nav, focus indicator, ARIA, skip link, prefers-reduced-motion, semantic landmarks
- Security-ready: HTTPS (deploy zorunlu), security headers (deploy configure), no inline secret
- Semantic FAQ: `<details>` native accessibility

---

## 🚀 Deploy Seçenekleri

### Seçenek 1: Vercel (Önerilen)
```bash
cd "Color Rush Araba Oyunu/website"
npx vercel --prod
```
Vercel otomatik: HTTPS, CDN edge cache, HTTP/3, Brotli, preview URL.

**Subdomain önerisi:** `colorrush.candavarci.com.tr` (ana candavarci.com.tr DNS'e CNAME ekle).

### Seçenek 2: GitHub Pages
1. `website/` içeriğini yeni repo'ya push et
2. Settings → Pages → main branch → `/` root
3. Custom domain: colorrush.candavarci.com.tr (CNAME)

### Seçenek 3: Cloudflare Pages
1. Cloudflare Dashboard → Pages → Upload
2. `website/` klasörünü sürükle
3. Custom domain + otomatik SSL

---

## 🔧 Launch Öncesi Yapılacaklar

### Content Güncellemesi (Store Linkleri Yayınlanınca)
- [ ] `index.html` içinde 4 yer: `href="#"` → gerçek App Store URL
- [ ] `index.html` içinde 4 yer: `href="#"` → gerçek Google Play URL
- [ ] Schema `"availability": "PreOrder"` → `"InStock"` (VideoGame offer)
- [ ] Schema `aggregateRating.ratingCount: "50"` → gerçek review sayısı
- [ ] Testimonial — gerçek oyuncu quote ekle (placeholder 3 quote değiştir)
- [ ] Hero badge "Yakında yayında" → kaldır veya "Şimdi yayında" güncelle

### OG Image Güncellemesi (Önerilen)
Şu anki OG image game banner (`banner_dual_final.png`). İdeal OG image:
- **Boyut:** 1200×630 (Facebook/Twitter standart)
- **İçerik:** Game logo + tagline + key art + "Ücretsiz indir" CTA
- **Üretim:** Claude Design (claude.ai Apps) veya mcp-image (nano-banana) ile 30 saniyede

### Analytics Entegrasyonu
- [ ] GA4 Measurement ID ekle (`</head>` öncesi Google Tag)
- [ ] Meta Pixel ID ekle (isteğe bağlı)
- [ ] Consent Mode v2 (KVKK + GDPR) — cookie banner ekle

### Performans Optimizasyonu (Opsiyonel)
- [ ] Screenshot PNG → AVIF + WebP (boyut %60 azalır): `cwebp -q 80 *.png`
- [ ] Gerçek hero gameplay video (30s) — Unity Recorder ile çekim
- [ ] Font self-host (Google Fonts CDN yerine)

### Search Console
- [ ] Google Search Console'da property ekle
- [ ] `sitemap.xml` submit
- [ ] Bing Webmaster Tools submit
- [ ] IndexNow API ping (Bing + Yandex)

---

## 🧪 QA Checklist (Deploy Sonrası)

- [ ] Lighthouse mobile: Performance ≥92, A11y ≥95, SEO 100, Best Practices 100
- [ ] PageSpeed Insights mobile: LCP ≤2.0s, INP ≤200ms, CLS ≤0.1
- [ ] Schema Rich Results Test: 0 kritik hata (6 schema block)
- [ ] W3C HTML Validator: 0 error
- [ ] WAVE / axe DevTools: 0 critical
- [ ] Mobile 375px + tablet 768px + desktop 1440px visual check
- [ ] TR ↔ EN dil toggle çalışıyor (localStorage kalıcılık)
- [ ] Privacy + Terms erişilebilir (navigation link + footer)
- [ ] Store button'lar external link (rel=noopener target=_blank gerektiğinde)
- [ ] Contact email + telefon tıklanabilir (mailto + tel)
- [ ] Scroll reveal animation prefers-reduced-motion ile kapanıyor

---

## 📊 Launch KPIs (30-60-90 Gün Hedefleri)

| KPI | 30 Gün | 60 Gün | 90 Gün |
|-----|--------|--------|--------|
| Organik visitor/ay | 500 | 2,000 | 5,000 |
| Bounce rate | <65% | <55% | <50% |
| Store badge CTR | ≥5% | ≥8% | ≥10% |
| Scroll %50+ | ≥55% | ≥65% | ≥70% |
| GSC impression | 2,000 | 8,000 | 25,000 |
| GSC clicks | 100 | 400 | 1,200 |

---

## 🎯 Gelecek İterasyonlar

### v1.1 (Launch + 1 ay)
- Gerçek gameplay trailer (Unity Recorder 30s)
- Gerçek testimonial (5+ kullanıcı)
- Store rating gerçek (aggregateRating güncelle)
- Blog section (dev devlog)
- Beta tester formu (Supabase entegrasyonu)

### v1.2 (Launch + 3 ay)
- Programmatic SEO: 10 sayfa (/blog/arcade-oyun-nedir, /blog/renk-koru-oyun, /blog/endless-runner-karsilastirma)
- Multi-language: Arapça + Almanca + Portekizce
- Leaderboard embed (multiplayer launch sonrası)
- Press kit indirme (PDF + asset bundle)

---

## 📞 İletişim

**Ajans:** Parcalar / Candavarcı Trusted Digital Partner
**Kurucu:** Can Davarcı
**E-posta:** contact@candavarci.com.tr
**WhatsApp:** 0554 947 80 18
**Web:** https://candavarci.com.tr

---

## 📚 Referanslar

- **Ustalık El Kitabı:** `~/Desktop/Dökümanlar/USTALIK-EL-KITABI/` (Modül 2 + 3 + 7)
- **Oyun GDD:** `../GAME-DESIGN-DOCUMENT.md` (962 satır)
- **Yayın Yolharitası:** `../YAYINLAMA-YOL-HARITASI.md`
- **Session notu:** `../NEREDE-KALDIK.md`

---

*Bu landing page Ustalık El Kitabı v1.0 uyumluluğunda üretildi. Modül 2 (İkna Mimarisi) + Modül 3 (SEO) + Modül 7 (Kalite Kapısı) standartlarına göre inşa edildi ve Pre-Launch 150-madde checklist'inden geçirildi.*

**Lisans:** Parcalar / Candavarcı Trusted Digital Partner iç IP — 2026
