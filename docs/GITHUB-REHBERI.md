# GitHub Rehberi: Hesap Aç, Repo Oluştur, Dosyaları Yükle

## 1. Hesap açma (5 dakika, sen yapmalısın)

1. https://github.com/signup adresine git.
2. E-posta adresini yaz, bir **şifre** belirle.
3. Kullanıcı adı seç. İpucu: işveren de görecek, `ad-soyad` gibi profesyonel bir şey seç.
4. Robot doğrulamasını geç, e-postana gelen **kodu** gir.
5. Plan olarak **Free** (ücretsiz) seç.

Şifreni ve doğrulama kodunu başkasına (bana da) yazma.

## 2. Git'i bilgisayara kur

PowerShell'de kontrol et:

```powershell
git --version
```

Çıktı vermezse https://git-scm.com/download/win adresinden kur. Sonra bir kez ayarla:

```powershell
git config --global user.name "Adın Soyadın"
git config --global user.email "github-e-postan@mail.com"
```

## 3. Repo oluştur

1. GitHub'da sağ üstte **+ > New repository**
2. Repository name: `junior-yolculugum`
3. Description: `10 haftalık junior yolculuğum: tasarım + test + paylaşım`
4. **Public** seç
5. "Add a README" kutusunu **işaretleme** (bizde hazır README var)
6. **Create repository**

## 4. Dosyaları yükle ve commit'le

`junior-yolculugum` klasörünün içinde PowerShell aç:

```powershell
git init
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/junior-yolculugum.git
```

Commit'leri tek tek, anlamlı yap (madde "temiz commit" için önemli):

```powershell
git add README.md
git commit -m "docs: README iskeleti ve DevTools bulgularını ekle"

git add tests
git commit -m "test: giriş formu için 8 test senaryosu ekle"

git add figma
git commit -m "docs: Figma ekran tasarım notlarını ekle"

git add social
git commit -m "docs: 1 aylık içerik takvimi ve 3 post ekle"

git add sunum blog docs
git commit -m "docs: sunum metni, Blog #10 taslağı ve rehber ekle"

git push -u origin main
```

Push ederken GitHub giriş penceresi açılır, tarayıcıdan giriş yap.

## 5. İyi commit mesajı kuralları

- Format: `tür: ne yaptım` (`docs`, `test`, `feat`, `fix`)
- 50 karakteri aşma, fiil ile bitir ("ekle", "düzelt")
- "update", "asdf", "son hali" gibi mesajlar yazma
- Küçük ve odaklı commit yap, tek commit'e her şeyi doldurma

## 6. Son kontrol

- [ ] Repo Public
- [ ] README GitHub'da düzgün görünüyor
- [ ] En az 5-6 anlamlı commit var (Commits sayfasından bak)
- [ ] README'deki Figma ve blog linkleri çalışıyor
