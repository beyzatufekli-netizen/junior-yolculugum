# Figma Ekran Tasarımı: Giriş / Üye Ol

Hedef: Trendyol analizinden öğrendiklerimle "Fincan & Co." markası için sade bir giriş ekranı.
Figma hesabı ücretsiz: figma.com adresinden e-posta ile açabilirsin.

## 1. Dosya kurulumu

1. Figma'da **New design file** aç, adı: `Junior Projesi - Giriş Ekranı`
2. `F` tuşu ile Frame al, sağdan **Phone > iPhone 14** (390 x 844) seç.
3. Frame adı: `Giriş`

## 2. Renk ve yazı stilleri (Variables / Styles)

| Ad | Değer |
|---|---|
| Primary | `#6F4E37` (kahve) |
| Primary-dark | `#4A3324` |
| Background | `#FAF6F1` |
| Text | `#2B2118` |
| Text-muted | `#7A6A5D` |
| Error | `#C62828` |
| Border | `#D9CFC5` |

Yazı tipi: **Inter**. Başlık 24 / Bold, etiket 14 / Medium, gövde 16 / Regular, yardımcı metin 12 / Regular.

## 3. Component'ler (hepsini `Ctrl + Alt + K` ile oluştur)

| Component | Varyantlar (Variants) | Ölçü |
|---|---|---|
| `Button/Primary` | State: Default, Pressed, Disabled | Yükseklik 48, köşe 12 |
| `Button/Social` | Type: Google, Apple | Yükseklik 48, çerçeveli |
| `Input/Text` | State: Default, Focus, Error, Filled | Yükseklik 48, köşe 8 |
| `Divider/Or` | tek hâl | "veya" yazılı çizgi |

Her component için sağ panelde **Create component set** ile varyantları birleştir.

## 4. Auto Layout (en kritik madde)

1. Tüm ekran öğelerini seç, `Shift + A` ile Auto Layout ekle (dikey).
2. Ana kart: padding 24, gap 16, hizalama üstten sola.
3. `Input/Text` içinde: etiket + alan + yardımcı metin, dikey, gap 4.
4. `Button` içinde: padding yatay 16, dikey 12, içerik ortalı, **Hug contents** yerine genişlik **Fill container**.
5. Sosyal butonlar: yatay Auto Layout, gap 12, her biri Fill container.

Kontrol: Metni uzatınca kutu kendiliğinden büyüyorsa Auto Layout doğru çalışıyor.

## 5. Ekran içeriği (yukarıdan aşağıya)

1. Logo (Fincan & Co.)
2. Başlık: **Giriş Yap veya Üye Ol**
3. `Input/Text`, etiket: E-posta
4. `Button/Primary`, metin: Devam Et
5. `Divider/Or`
6. `Button/Social` Google, `Button/Social` Apple
7. Küçük yazı: "Devam ederek Kullanım Koşulları'nı kabul etmiş olursun."

## 6. Teslim öncesi kontrol listesi

- [ ] Tüm renkler Style/Variable'dan geliyor, elle renk yok
- [ ] En az 4 component var, varyantlı
- [ ] Auto Layout her yerde açık
- [ ] Error durumunu gösteren ikinci bir frame var (`Giriş - Hata`)
- [ ] Metin kontrastı yeterli (Text on Background rahatça okunuyor)
- [ ] Figma linki **"Anyone with the link can view"** olarak paylaşıldı ve README'ye eklendi
- [ ] Ekran görüntüsü `docs/img/figma-giris.png` olarak kaydedildi
