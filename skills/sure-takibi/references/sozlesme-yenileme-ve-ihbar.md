# Sözleşme yenileme ve fesih ihbar süreleri

**Ne zaman kullanılır:** `--yenileme` kipinde; "ne yenileniyor", "hangi sözleşmeyi ne zamana kadar feshetmeliyiz", "yenilememe bildirimini kaçırdık mı", "bu sözleşmeyi takibe al" sorularında; sözleşme incelemesinin sonunda yenileme hükmü bulunduğunda.

Upstream `commercial-legal/skills/renewal-tracker` uyarlaması. Temel fikir: sözleşme bir kez okunur; yenileme tarihi o anda çıkarılmazsa bir daha görülmez. Bu dosya o tarihi bir kez çıkarır, deftere koyar ve pencere kapanmadan uyarır.

Sözleşmenin **içeriği** (yenileme hükmü geçerli mi, fesih hakkı var mı, cezai şart, genel işlem koşulu denetimi) bu dosyanın işi değildir → `../../sozlesme-incelemesi-tbk/SKILL.md`. Kira sözleşmesi → önce `../../kira-hukuku/references/kira-takvimi-ve-ihtarlar.md` (kiraya özgü uzama ve bildirim kuralları orada); bu dosya oradaki tarihleri deftere taşır. Kamu sözleşmesi (4735) → `../../hakedis/references/degisiklik-izi-ve-takvim.md`. İş sözleşmesinde bildirim süreleri → `../../is-hukuku/SKILL.md`.

---

## 1. Kayıt alanları

Defter satırına (`sure-defteri-ve-takvim.md` §2) `tur: sozlesme-bildirim` ile şu ek alanlar eklenir:

```yaml
    sozlesme:
      karsi_taraf: "[kısa ad]"
      sozlesme_adi: "[ör. yazılım lisans ve destek sözleşmesi]"
      imza_tarihi: 2025-06-15
      ilk_donem_sonu: 2026-06-15 # yalnız kayıt için
      yururlukteki_donem_sonu: 2026-06-15 # hesap bundan yapılır; her yenilemede ileri sarılır
      yenileme_bicimi: "kendiliğinden bir yıl" # sözleşmeden aynen
      bildirim_suresi: "[sözleşmeden aynen, ör. 'bitimden en az altmış gün önce']"
      bildirim_maddesi: "md. 14.2" # [kullanıcı verdi]
      bildirim_sekli: "noter | iadeli taahhütlü | KEP | e-posta | sözleşmede yazılı adres"
      kanuni_sekil: "TTK m.18/3 [soorgla] | TBK m.348 [soorgla] | yok"
      gonderim_payi_gun: 0 # elektronik 0; noter/PTT için kullanıcıya sor [incele]
      ulasma_son_gunu_takvim: 2026-04-16 # yürürlükteki dönem sonu − bildirim süresi
      ulasma_son_gunu: 2026-04-16 # tatilse geriye çekilmiş hâli
      gonderme_son_gunu: 2026-04-16 # ulaşma son günü − gönderim payı; UYARILAR BUNA GÖRE
      kaydirma_notu: "" # ör. "Pazar 2026-04-19'dan geriye çekildi"
      fiyat_yenilemede: "[sabit | endeksli | o günkü liste fiyatı (sınırsız)]"
      yillik_bedel: "[kullanıcı verdi]"
      is_birimi_sorumlusu: "[ad/e-posta — şirket içi]"
```

`son_gun` alanı **gönderme son günüdür**; uyarı bandı ona göre hesaplanır. Rapor ayrıntı sütununda ulaşma son günü, bildirim şekli ve gönderim payı görünür ki okuyucu farkı sorgulayabilsin.

---

## 2. Hesap

1. **Yürürlükteki dönem sonu.** İlk dönem sonu yalnız kayıttır. Sözleşme kendiliğinden yenilendiyse dönem sonunu ileri sar; ilk yılın tarihiyle hesap ikinci yıldan itibaren yanlıştır.
2. **Bildirim süresi** sözleşmeden **aynen** alınır ("altmış gün", "iki ay", "üç ay önce", "dönem sonundan önceki ayın sonuna kadar"). Gün/hafta/ay sayımı TBK m.92'ye göre yapılır; sözleşmenin kendi tanımı ("iş günü", "takvim günü") varsa o geçerlidir. "15 gün" ile "2 hafta" aynı değildir (TBK m.92/1).
3. **Ulaşma son günü (takvim)** = yürürlükteki dönem sonu − bildirim süresi.
4. **Tatil kontrolü ve yön.** Ulaşma son günü hafta sonu ya da resmî tatilse `legal_check_holiday` ile kontrol et ve **geriye** (önceki iş günü) çek. Neden: bildirim karşı tarafa bu tarihte ulaşmış olmalıdır; ileri kaydırma bildirimi geç bırakabilir. TBK m.93 son günü ileri kaydırır ama ifa zamanı için yazılmıştır ve "aksine anlaşma geçerlidir"; geriye doğru sayılan bildirim sürelerine uygulanıp uygulanmadığı `[incele]`. Güvenli yön her zaman erken tarihtir. İki tarihi de yaz (`ulasma_son_gunu_takvim`, `ulasma_son_gunu`, `kaydirma_notu`).
5. **Sözleşmenin tebliğ hükmü.** "Bildirim … tarihinde yapılmış sayılır", "teslim alındığı gün", "gönderildiği gün", "KEP'e ulaştığı an" gibi hükümler hesabı değiştirir. Yoksa genel kural: bildirim karşı tarafa ulaştığında hüküm doğurur `[model bilgisi — doğrulayın]`.
6. **Gönderme son günü** = ulaşma son günü − gönderim payı. Noter ihtarnamesinde ve iadeli taahhütlü mektupta tebliğ günler sürebilir, adres yanlışsa haftalar; KEP'te kısa. Payı kullanıcıya sor, sorulamıyorsa birkaç iş günü öner ve `[incele]`.
7. Hesap gerekçesini tek satıra yaz: `Dönem sonu 15.06.2026 − 60 gün (md.14.2) → 16.04.2026 Perşembe; tatil değil; noter payı 5 iş günü → gönder: 09.04.2026`.

## 3. Şekil

- **Tacirler arası:** temerrüde düşürme, fesih ve dönme ihbarları için TTK m.18/3'teki yollar (noter, taahhütlü mektup, telgraf, güvenli elektronik imzalı KEP). Yenilememe bildiriminin bu kapsama girip girmediği `[incele]`; güvenli yol bu şekillerden biridir.
- **Konut ve çatılı işyeri kirası:** fesih bildirimi yazılı (TBK m.348) → `kira-hukuku`.
- **Sözleşmedeki şekil** (ör. "yalnız noter kanalıyla", "md. 20'deki adrese") kanuni şekle ek olarak uygulanır. Uymayan bildirim tartışmaya açıktır.
- E-posta ve mesajlaşma uygulamasıyla bildirim: sözleşme izin vermiyorsa ispat ve geçerlilik riski `[incele]` 🟠.

---

## 4. Rapor (`--yenileme`)

Varsayılan pencere 90 gün; bantlar **gönderme son gününe** göre ve SKILL.md'deki ortak bantlarla (⛔ / 🔴 0–6 / 🟠 7–13 / 🟡 14–29 / 🟢 30–89).

```markdown
## Sözleşme bildirimleri — önümüzdeki [N] gün

### 🔴 Gönderme son günü 0–6 gün içinde
| Karşı taraf | Sözleşme | Gönderme son günü | Ulaşma son günü | Dönem sonu | Şekil / pay | Fiyat yenilemede | Sorumlu | Hesap gerekçesi |

### 🟠 … / 🟡 … / 🟢 …
[aynı tablo]

**Önerilen işler:**
- [ ] [karşı taraf] — [iş birimi sorumlusu]na sor: devam mı?
- [ ] [karşı taraf] — fiyat yenilemede sınırsız: pencere kapanmadan alternatif teklif al
- [ ] [karşı taraf] — bildirim noterle gidecek: metni [dilekçe becerisi] ile hazırla, gönderme son günü [tarih]
```

### Kaçırılmış pencereler (`--yenileme --kacan`)

```markdown
## Kaçırılmış bildirim pencereleri
| Karşı taraf | Gönderme son günü idi | Dönem sonu | Durum |
|---|---|---|---|
| [ad] | [tarih] | [tarih] | [tarih]'te kendiliğinden yenilenecek / yenilendi |

**Seçenekler** (esas değerlendirmesi `sozlesme-incelemesi-tbk`):
- Karşı tarafla geç fesih için müzakere
- Yenilemeyi kabul et, bir sonraki dönemin gönderme son gününü şimdi deftere yaz
- Sözleşmede başka bir fesih hakkı (haklı sebep, olağan fesih, TBK genel hükümleri) var mı `[incele]`
```

### Kendiliğinden yenileme gerçekleştiğinde

Pencere geçti ve bildirim kaydı yoksa sor:
> "Bu sözleşme [tarih]'te kendiliğinden yenilenmiş görünüyor. Defteri ileri sarayım mı? Yeni dönem sonu [tarih], yeni ulaşma son günü [tarih], yeni gönderme son günü [tarih]. Onaylıyor musunuz?"

Onay olmadan ileri sarma; eski satırı `kapatildi` (gerekçe: "yenilendi") yap, yenisini ekle.

---

## 5. Kapı: yenilemeyi kabul etmek ya da reddetmek

Tarihi izlemek araştırmadır. Bildirim göndermek, yenilemenin geçmesine izin vermek ya da yenileme formunu imzalamak **hukuki sonuç doğuran adımdır**.

Avukat olmayan kullanıcıda (`ORTAK-KURALLAR.md` §1) dur ve sor: "Bunu bir avukatla gözden geçirdiniz mi?" Cevap hayırsa avukata götürülecek tek sayfalık özet ver:
- Karşı taraf, sözleşme, yürürlükteki dönem sonu
- Ulaşma son günü ve gönderme son günü (hesap gerekçesiyle)
- Hiçbir şey yapılmazsa ne olur (kendiliğinden yenileme, fiyat mekanizması)
- Şekil şartı (sözleşme ve kanun)
- Alternatif tedarikçi ya da müzakere imkânı (kullanıcı verdiyse)
- Avukata sorulacak üç soru: (1) bildirim şekli ve adresi doğru mu, (2) başka fesih hakkımız var mı, (3) yenilememenin cezai şart ya da tazminat sonucu var mı

Açık bir "evet" olmadan bildirimi "gönderilebilir" diye işaretleme. Bildirim metni → `../../hukuk-yargilamasi-dilekce/references/ihtarname.md` (noter ihtarnamesi) ya da tacirler arası yazışmada `sozlesme-incelemesi-tbk`.

---

## 6. Yenileme kaydı nereden gelir?

- **Sözleşme incelemesinden devir:** `sozlesme-incelemesi-tbk` bir yenileme ya da bildirim hükmü bulduğunda alanları doldurup "Süre defterine ekleyeyim mi?" diye sorar.
- **Toplu yükleme:** kullanıcı birden çok sözleşme yüklerse önce her birinden yalnız §1 alanlarını çıkar, tablo hâlinde göster, tarihi belirlenemeyenleri ayrı listele ("bu sözleşmeyi bir insanın okuması gerekiyor"), sonra tek onayla deftere yaz. Çok belgeli işlerde tablolu belge incelemesi becerisi (yüklüyse) kullanılabilir.
- **Bu dosya sözleşmeyi baştan sona incelemez;** yalnız süre alanlarını çıkarır. Yenileme hükmünü bulamazsa "yenileme hükmü bulunamadı — md. [okunan aralık] okundu" der, sessizce "yenileme yok" demez.
