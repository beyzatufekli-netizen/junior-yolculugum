# Test Senaryoları: Giriş / Kayıt Formu

- Test edilen özellik: Trendyol e-posta ile Giriş Yap / Üye Ol akışı (`/giris`)
- Test türü: Manuel, işlevsel (functional) + temel kullanılabilirlik
- Tarayıcı: Chrome (güncel sürüm), masaüstü
- Önkoşul: Sistemde var olan gerçek bir hesabın şifresini **yazmıyoruz**. Sadece e-posta adımına kadar test ediyoruz.

## Sonuç özeti

| Toplam | Çalıştırılan | Başarılı (Pass) | Başarısız (Fail) | Çalıştırılmadı |
|---|---|---|---|---|
| 8 | 5 | 4 | 1 | 3 |

## Test senaryoları ve sonuçları

| ID | Senaryo | Adımlar | Test verisi | Beklenen sonuç | Gerçekleşen | Durum |
|---|---|---|---|---|---|---|
| TC-01 | Geçerli e-posta ile devam | 1. Sayfayı aç 2. E-posta gir 3. **Devam Et**'e bas | `ornek.test@mail.com` | Sonraki adıma (şifre veya üyelik) geçilir | Şifre girme ekranına başarıyla geçildi. | ✅ Başarılı (Pass) |
| TC-02 | Boş e-posta | 1. Alanı boş bırak 2. **Devam Et**'e bas | (boş) | Hata mesajı çıkar, sonraki adıma geçilmez | "Bu alan zorunludur" uyarısı çıktı, sayfa ilerlemedi. | ✅ Başarılı (Pass) |
| TC-03 | `@` işareti olmayan e-posta | 1. Gir 2. **Devam Et** | `ornekmail.com` | Geçersiz e-posta uyarısı | Uyarı çıkmadı, buton tepkisiz kaldı. | ❌ Başarısız (Fail) |
| TC-04 | Alan adı eksik e-posta | 1. Gir 2. **Devam Et** | `ornek@` | Geçersiz e-posta uyarısı | Henüz çalıştırılmadı. | ⏳ Çalıştırılmadı |
| TC-05 | Başında/sonunda boşluk olan e-posta | 1. Gir 2. **Devam Et** | ` ornek.test@mail.com ` | Boşluklar temizlenir ya da net bir uyarı gösterilir | Boşluklar otomatik silindi ve şifre ekranına geçildi. | ✅ Başarılı (Pass) |
| TC-06 | Çok uzun e-posta | 1. 255 karakteri aşan e-posta yazmayı dene | `aaaa...@mail.com` | Sayfa bozulmaz, hata verir ya da kabul etmez | 255 karakterden fazlasını yazmaya izin vermedi, tasarım bozulmadı. | ✅ Başarılı (Pass) |
| TC-07 | Türkçe karakterli e-posta | 1. Gir 2. **Devam Et** | `çağrı@mail.com` | Davranış net ve tutarlı (kabul veya anlamlı hata) | Henüz çalıştırılmadı. | ⏳ Çalıştırılmadı |
| TC-08 | Klavye ile kullanım | 1. Sadece `Tab` ve `Enter` kullan | | Odak sırası mantıklı, `Enter` formu gönderir, odak çerçevesi görünür | Henüz çalıştırılmadı. | ⏳ Çalıştırılmadı |

## Bulunan hata

### BUG-01: Geçersiz e-posta formatında kullanıcıya uyarı gösterilmiyor (TC-03)

```
Başlık:      [Giriş] "@" işareti olmayan e-posta ile Devam Et'e basınca uyarı çıkmıyor
Ortam:       Chrome (güncel), Windows 11, masaüstü
Adımlar:     1. https://www.trendyol.com/giris sayfasını aç
             2. E-posta alanına "ornekmail.com" yaz
             3. "Devam Et" butonuna bas
Beklenen:    "Geçersiz e-posta" benzeri bir uyarı gösterilir
Gerçekleşen: Hiçbir uyarı çıkmıyor, buton tepkisiz kalıyor
Ekran görüntüsü: docs/img/bug-01.png
Önem:        Orta (kullanıcı neyin yanlış olduğunu anlayamıyor)
```

İlişkili gözlem: Form `novalidate` ile tanımlı olduğu için tarayıcının kendi uyarısı devreye girmiyor. Doğrulama ve hata mesajı tamamen sitenin kendi koduna bırakılmış. TC-02'de boş alan için uyarı çıkması, ama TC-03'te çıkmaması bu doğrulamanın format kontrolünde eksik kaldığını gösteriyor.

## Ek notlar

- **Bot koruması:** Sayfada Cloudflare Turnstile var. Sık sık tekrar deneme yaparsan doğrulama çıkabilir. Bunu bypass etmeye çalışma, normal kullanıcı akışını test et.
- **Sosyal giriş:** Google/Facebook butonları üçüncü taraf hesap gerektirdiği için kapsam dışı bıraktım.
- **Neden bu senaryolar?** Form testinde en sık hata sınır değerlerde çıkar: boş, çok uzun, özel karakter ve format hatası. TC-02 ile TC-07 arası bu mantıkla seçildi.
- **Kalan işler:** TC-04, TC-07 ve TC-08 çalıştırılınca tablo ve özet güncellenecek.
