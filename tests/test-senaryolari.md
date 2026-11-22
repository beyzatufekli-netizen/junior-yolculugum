# Test Senaryoları: Giriş / Kayıt Formu

- Test edilen özellik: Trendyol e-posta ile Giriş Yap / Üye Ol akışı (`/giris`)
- Test türü: Manuel, işlevsel (functional) + temel kullanılabilirlik
- Tarayıcı: Chrome (güncel sürüm), masaüstü ve mobil görünüm (DevTools cihaz modu)
- Önkoşul: Sistemde var olan gerçek bir hesabın şifresini **yazmıyoruz**. Sadece e-posta adımına kadar test ediyoruz.

> Sonuç sütunlarını testi kendin çalıştırıp doldur. Bu tabloda "Gerçekleşen" kısmı bilerek boş.

| ID | Senaryo | Adımlar | Test verisi | Beklenen sonuç | Gerçekleşen | Durum |
|---|---|---|---|---|---|---|
| TC-01 | Geçerli e-posta ile devam | 1. Sayfayı aç 2. E-posta gir 3. **Devam Et**'e bas | `ornek.test@mail.com` | Sonraki adıma (şifre veya üyelik) geçilir | | |
| TC-02 | Boş e-posta | 1. Alanı boş bırak 2. **Devam Et**'e bas | (boş) | Hata mesajı çıkar, sonraki adıma geçilmez | | |
| TC-03 | `@` işareti olmayan e-posta | 1. Gir 2. **Devam Et** | `ornekmail.com` | Geçersiz e-posta uyarısı | | |
| TC-04 | Alan adı eksik e-posta | 1. Gir 2. **Devam Et** | `ornek@` | Geçersiz e-posta uyarısı | | |
| TC-05 | Başında/sonunda boşluk olan e-posta | 1. Gir 2. **Devam Et** | ` ornek.test@mail.com ` | Boşluklar temizlenir ya da net bir uyarı gösterilir | | |
| TC-06 | Çok uzun e-posta | 1. 300 karakterlik e-posta gir | `aaaa...@mail.com` | Sayfa bozulmaz, hata verir ya da kabul etmez | | |
| TC-07 | Türkçe karakterli e-posta | 1. Gir 2. **Devam Et** | `çağrı@mail.com` | Davranış net ve tutarlı (kabul veya anlamlı hata) | | |
| TC-08 | Klavye ile kullanım | 1. Sadece `Tab` ve `Enter` kullan | | Odak sırası mantıklı, `Enter` formu gönderir, odak çerçevesi görünür | | |

## Ek notlar

- **Bot koruması:** Sayfada Cloudflare Turnstile var. Sık sık tekrar deneme yaparsan doğrulama çıkabilir. Bunu bypass etmeye çalışma, normal kullanıcı akışını test et.
- **Sosyal giriş:** Google/Facebook butonları üçüncü taraf hesap gerektirdiği için kapsam dışı bıraktım.
- **Neden bu senaryolar?** Form testinde en sık hata sınır değerlerde çıkar: boş, çok uzun, özel karakter ve format hatası. TC-02 ile TC-07 arası bu mantıkla seçildi.

## Hata bulursan bug raporu şablonu

```
Başlık:   [Giriş] Boş e-posta ile Devam Et'e basınca hata mesajı çıkmıyor
Ortam:    Chrome 130, Windows 11, masaüstü
Adımlar:  1. ... 2. ... 3. ...
Beklenen: ...
Gerçekleşen: ...
Ekran görüntüsü: docs/img/bug-01.png
Önem:     Düşük / Orta / Yüksek
```
