# neuralacademy.net

Neural Academy Danışmanlık Eğitim Sağlık Ticaret Ltd. Şti.'nin kurumsal web sitesi.
Türkçe ana sayfa ve tam İngilizce sürüm (`/en/`). Saf HTML + CSS; build adımı, JavaScript,
harici font, analitik veya çerez yok.

## Dosyalar

| Dosya | Açıklama |
|---|---|
| `index.html` | Türkçe sayfa |
| `en/index.html` | İngilizce sayfa (aynı yapı, tam çeviri) |
| `style.css` | Ortak stiller (sistem fontları: başlıklarda serif, metinde sans) |
| `CNAME` | GitHub Pages özel alan adı: `neuralacademy.net` |
| `robots.txt` | Tüm taramaya izin verir |
| `assets/Neural-Academy-logo.jpeg` | Kaynak logo (orijinal dosya, sayfada kullanılmıyor) |
| `assets/logo.png` | Kaynak logonun kayıpsız PNG kopyası (sayfada kullanılmıyor) |
| `assets/logo-mark.png`, `logo-mark-96.png` | Yuvarlak amblem, şeffaf; yalnızca üst barda 36 px olarak kullanılıyor |
| `assets/favicon.ico`, `favicon-32.png` | Favicon (16/32/48 px), amblemden |
| `assets/apple-touch-icon.png` | 180×180, krem zemin üzerinde amblem |
| `assets/og-image.png` | 1200×630 sosyal paylaşım görseli (dallar fotoğrafı + şirket adı) |
| `assets/background.jpg` | Kaynak fotoğraf, 3024×4032 (sayfada doğrudan kullanılmıyor) |
| `assets/hero-800.*`, `hero-1200.*` | Kaynak fotoğrafın web boyutları (JPEG + WebP), giriş bölümünde |
| `assets/lumia/lumia-logo.png` | Kaynak Lumia logosu |
| `assets/lumia/lumia-logo-640.png` | Kenarları kırpılmış, 640 px web kopyası |
| `assets/lumia/lumia-background.jpg` | Kaynak Lumia zemini (sayfada doğrudan kullanılmıyor) |
| `assets/lumia/lumia-bg-720.*`, `lumia-bg-1080.*` | Lumia zemininin web boyutları (JPEG + WebP) |

Kaynak dosyalar (`background.jpg`, `lumia-background.jpg`, `logo.png`) sayfadan çağrılmaz;
yalnızca yeniden üretim için depoda durur. Depo boyutunu küçültmek istenirse silinebilir.

## Tasarım kararları

- **Neural Academy logosu** yalnızca üst barda (36 px) ve tarayıcı ikonlarında kullanılır.
  Sayfada büyük logo yoktur.
- **Giriş bölümü** `assets/background.jpg` (kar üstünde dallar) fotoğrafını dikey bir panel olarak
  kullanır; mobilde 4:3 oranında kırpılır. Fotoğraf 800 ve 1200 px genişliklerinde, JPEG ve WebP
  olarak sunulur (`<picture>` + `srcset`).
- **Lumia kartı** kendi görsel kimliğini taşır: sol panelde Lumia zemini ve logosu, sağda metin.
  Lumia yeşilleri logodan ölçüldü: `#1A4336` (koyu), `#5E8663` (orta), `#ACBD96` (açık).
- **Renk paleti** Neural Academy logosundan ölçüldü: `#10222A` (yazı), `#152A33` (koyu yarı),
  `#2C4951` (halka orta ton), `#74979D` (halka açık ton).
- **Tipografi:** başlıklar sistem serif yığını (`ui-serif`, Iowan Old Style, Palatino, Georgia),
  gövde metni sistem sans yığını. Harici font yüklenmez.
- **Dil:** `/` Türkçe, `/en/` İngilizce. Üst bardaki `EN` / `TR` düğmesi diller arasında geçiş yapar.
  Bağlantılar `en/index.html` ve `../index.html` biçimindedir; böylece dosya doğrudan açıldığında
  (`file://`), yerel sunucuda ve GitHub Pages'te aynı şekilde çalışır. Her iki sayfada `hreflang`
  alternatifleri ve `x-default` tanımlıdır.
- **Amblem kesimi:** Kaynak logodaki dış daire en küçük kareler yöntemiyle oturtuldu
  (merkez 510.8, 451.7; yarıçap 315.4 px) ve amblem bu dairenin 1.5 px içinden, kenar yumuşatmalı
  dairesel maskeyle şeffaf PNG olarak kesildi.

Türetilmiş görseller Python/Pillow ile kaynak dosyalardan üretildi.

## Yerelde açma

```sh
python3 -m http.server 8000
# http://localhost:8000      Türkçe
# http://localhost:8000/en/  İngilizce
```

## GitHub Pages ile yayın

1. Depo: <https://github.com/noralakademi/neuralacademy-site> (public).
2. Dosyaları `main` dalına gönder:
   ```sh
   git add . && git commit -m "Site" && git push -u origin main
   ```
3. GitHub'da **Settings > Pages**:
   - **Source:** Deploy from a branch
   - **Branch:** `main`, klasör `/ (root)` > Save
4. **Custom domain** alanına `neuralacademy.net` yaz, Save. (Depodaki `CNAME` dosyası bunu zaten içerir.)
5. DNS kayıtları yayıldıktan ve GitHub sertifikayı ürettikten sonra **Enforce HTTPS** kutusunu işaretle.
   (Sertifika hazır olana kadar kutu pasif görünebilir; birkaç dakika ile birkaç saat sürebilir.)

İsteğe bağlı ama önerilir: alan adını hesaba bağlı doğrula
(GitHub > profil **Settings > Pages > Add a domain**), başkasının alan adını ele geçirmesini önler.

## DNS kayıtları

Kaynak: GitHub resmi dokümanı, "Managing a custom domain for your GitHub Pages site"
(<https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site>),
9 Ekim 2026'da kontrol edildi.

Apex (`neuralacademy.net`):

| Tür | Ad | Değer |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA (isteğe bağlı, IPv6) | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

`www`:

| Tür | Ad | Değer |
|---|---|---|
| CNAME | `www` | `noralakademi.github.io` |

Alan adında bu kayıtlarla çakışan eski A/AAAA/CNAME kayıtları (ör. park sayfası) varsa silinmeli.
Kontrol:

```sh
dig neuralacademy.net +noall +answer -t A
dig www.neuralacademy.net +noall +answer -t CNAME
```

## E-posta

`info@neuralacademy.net` adresinin çalışması için alan adında MX kaydı gerekir (ör. bir e-posta
yönlendirme servisi). Bu, GitHub Pages'ten bağımsızdır.
