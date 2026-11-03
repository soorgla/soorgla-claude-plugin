# Yönetici / iş birimi özeti ve dış avukattan durum isteme

Uyarlama: Anthropic `commercial-legal/stakeholder-summary` (uzunluk sınırı, kitle tablosu, alıntı disiplini, takip iddiası kuralı, yükseltme mutabakatı) ve `litigation-legal/oc-status` (dış avukata haftalık durum isteme, toplu çalışma özeti) (Apache 2.0). Privilege header, Gmail taslağı ve ABD "work product" işaretleri Türk karşılığıyla değiştirildi (ORTAK-KURALLAR.md §1 sır saklama notu).

Sözleşme incelemesinin iş birimi özeti için ayrı akış vardır: `../../sozlesme-incelemesi-tbk/references/degisiklik-gecmisi-ve-is-birimi-ozeti.md` (B bölümü). Bu dosya **dava, icra, idari süreç, soruşturma ve genel dosya** özetleri içindir.

---

## 1. Ne zaman kullanılır

- Şirket müvekkilin yönetimine dava/icra/denetim durumu ("karşılık ayıralım mı, sulh mü?").
- Şirket içi hukukçunun iş birimine ("bu ceza ihbarnamesi ne demek, ne yapmalıyız?").
- Yönetim kurulu toplantısı öncesi dosya portföyü özeti (birden çok dosya).

Okuyucu hukukçu değildir; iki dakikada okur ve tek soruya cevap arar: **beni ne bekliyor, benden ne karar istiyorsunuz?**

---

## 2. Kitle ayarı

| Okuyucu | Önemser | Önemsemez |
|---|---|---|
| Genel müdür / patron | Toplam risk, itibar, karar gereken nokta | Usul ayrıntısı |
| Mali işler / CFO | Olası tutar aralığı, faiz, masraf, karşılık ayırma, nakit çıkışının zamanı | Hangi dairenin baktığı |
| İK | İşçi tarafındaki etkisi, benzer dosya riski, yapılacak iç işlem | Faiz türü |
| Satın alma / satış | Tedarikçi/müşteri ilişkisine etkisi, sözleşmede ne değişmeli | Kanun yolu ayrıntısı |
| Yönetim kurulu | Portföy: kaç dosya, toplam risk, en büyük üç dosya | Tek dosyanın tarihçesi |

Profilde tanımlı değilse ve bağlamdan anlaşılmıyorsa sor: "Bu özet kime gidiyor?"

---

## 3. Uzunluk ve biçim (zorunlu)

- **Bir paragraf:** ne olduğu, iş diliyle ("X Ltd. bize 2,1 milyon TL'lik alacak davası açtı; dava İstanbul'da, ilk duruşma Mart'ta").
- **Bir paragraf:** dikkat edilecek nokta — sonradan sürpriz olacak şey ("Kaybedersek faizle birlikte tutar ciddi artar; faiz dava tarihinden işliyor").
- **En fazla üç madde:** okuyucunun yapacağı ya da karar vereceği şey.
- **Tek satır:** sonraki rapor tarihi / karar için son gün.
- **200 sözcüğü geçmez.** Geçiyorsa ayrıntı iç nota gider.

**Yazılmaz:** madde numaraları (en fazla bir), Latince/eski terimler, olasılık yüzdesi ("%70 kazanırız" — `kotu-haber-ve-sonuc-vaadi.md` §1), "bu hukuki tavsiye değildir" kalıbı (okuyucu kimden geldiğini biliyor; ORTAK-KURALLAR.md §1 başlığı yalnız iç kopyada).

**Risk ifadesi:** olasılık yüzdesi yerine üç kademe ve gerekçesi: "düşük / orta / yüksek — çünkü [tek cümle]". Kademe alan becerisinin önem derecesinden gelir (🔴 → yüksek); gerekçesiz düşürülmez (ORTAK-KURALLAR.md §8). Tutar aralığı veriliyorsa "en kötü durumda" senaryosu da yazılır (anapara + faiz + yargılama gideri + karşı vekâlet ücreti).

**Alıntı disiplini:** karardan ya da yazıdan alıntı yapılıyorsa koşullu cümle bütün olarak alınır; kısaltma şartı düşürüyorsa alıntı yerine dürüst bir özet yazılır.

### Çeviri tablosu

| Hukuki bulgu | İş diline çeviri |
|---|---|
| "Davada zamanaşımı def'i ileri sürülebilir" | "Alacağın bir kısmı süre geçtiği için istenemeyebilir; bunu mahkemede ileri süreceğiz." |
| "İhtiyati haciz kararı verildi" | "Dava bitmeden karşı taraf hesaplarımıza/malımıza geçici olarak el koydurabildi." |
| "Ticari temerrüt faizi işler" | "Borç ödenene kadar yüksek bir faiz işliyor; beklemek tutarı büyütür." |
| "Bilirkişi raporu aleyhe" | "Mahkemenin uzmanı karşı tarafı haklı buldu; buna itiraz ediyoruz ama hâkim çoğu zaman rapora yakın karar verir." |
| "Kesinlik sınırının altında" | "Bu karara üst mahkemeye itiraz yolu yok; karar bununla biter." |
| "İdari para cezası, 30 gün içinde dava" | "Cezaya itiraz için mahkemeye son gün [tarih]; ödeme indirimi varsa onu kullanmak itiraz hakkını etkileyebilir `[incele]`." |

### İskelet

````markdown
[ORTAK-KURALLAR.md §1 başlığı — yalnız iç kopyada]

**[Dosya kısa adı] — [DURUM: izleniyor | KARAR GEREKİYOR | ACİL — son gün TARİH]**

[Paragraf 1 — ne oldu, iş diliyle]

[Paragraf 2 — dikkat: risk kademesi + en kötü durum + zamanlama]

**Sizden istenen:**
- [ ] [Karar ya da işlem — son tarih]
- [ ] [En fazla üç madde; yoksa "Şu an karar gerekmiyor; [tarih]'te güncelleme göndereceğim."]

**Sonraki rapor:** [tarih]
````

### Takip ve yükseltme iddiası kuralı

- "Takvime ekledim", "takip ediyoruz", "hatırlatma kurdum" ifadeleri ancak gerçekten yapıldıysa yazılır (süre takibi becerisi çalıştırıldıysa, günlük dosyası yazıldıysa). Yapılmadıysa: "Bu tarihi takviminize eklemenizi öneririm; ben eklemedim."
- Alan becerisinin değerlendirmesi birden çok kişiye yükseltme önerdiyse (ör. CFO + İK + yönetim kurulu), özetin altına iç kullanım için **yükseltme durumu** bloğu eklenir: "[N] kişiden [M]'sine iletildi; iletilmeyenler: …". Bu blok 200 sözcük sınırına dahil değildir ve iş birimine gidecek kopyadan çıkarılabilir; ama iç kopyada mutlaka bulunur.

---

## 4. Portföy özeti (birden çok dosya)

Yönetim kurulu ya da CFO için:

| Dosya | Karşı taraf | Konu | Aşama | Risk | Olası tutar (en kötü) | Sonraki kritik tarih | Karar gerekiyor mu |
|---|---|---|---|---|---|---|---|

Kurallar: tablo yalnız dosya klasöründeki (etkinse) ya da kullanıcının verdiği bilgilerle doldurulur; boş hücre `[___]`. Tutarlar araçtan ya da karardan; tahmini değer "tahmin" diye işaretli. Tablonun üstünde iki cümlelik genel durum, altında "en çok dikkat isteyen üç dosya".

---

## 5. Dış (anlaşmalı) avukattan durum isteme (G kipi)

Şirket içi hukuk biriminin, dosyaları yürüten anlaşmalı avukat/büroya düzenli durum sorusu.

### Hangi dosyalar

Varsayılan süzgeç (kullanıcı başka bir şey demedikçe): kapanmamış, dış avukat atanmış, son durum bilgisinden bu yana belirli bir süre geçmiş ya da yakında kritik tarihi olan dosyalar. Süre eşiği profildeki tercihten; yoksa sor. Dosya listesi yoksa kullanıcıdan iste; dosya klasörü etkinse oradan oku. Başka dosyanın bilgisi bir dosyanın e-postasına girmez.

### E-posta iskeleti (dosya başına bir e-posta)

```
Konu: [Dosya kısa adı] — durum bilgisi talebi

Sayın Av. [Ad Soyad],

[Dosya] hakkında güncel durumu rica ederim:

1. [Son bilgi tarihi]'nden bu yana gelişmeler: duruşma, dilekçe, tebligat,
   bilirkişi raporu, karar var mı?
2. Yaklaşan tarihler: bizde [tarih — ne] görünüyor. Doğru mu, eklenecek tarih var mı?
3. Bizden beklenen karar ya da belge: [dosya notundaki açık sorulardan; yoksa bu maddeyi çıkar]
4. Masraf ve ücret: [profil bütçe tercihi — aylık/aşama sonu] bugüne kadarki
   masraf ve onaylı bütçeye göre durum; öngörülen ek masraf var mı?

[Varsa 5. özel istek — ör. "Cevap dilekçesi taslağını [tarih]'e kadar
görebilir miyiz?"]

Saygılarımla,
[Ad Soyad] — [Unvan], [Şirket] Hukuk Müdürlüğü
```

Dış avukatla yazışma avukat-müvekkil ilişkisi içindedir; yine de e-postaya iç strateji, sulh sınırı ya da yönetimin iç değerlendirmesi yazılmaz (yanlış alıcıya iletilme riski). Avukat notunda: "Göndermeden önce: alıcı doğru mu, iç değerlendirme sızıyor mu, ton büro alışkanlığına uygun mu kontrol edin."

### Toplu çalışma özeti

Birden çok dosya için taslak üretildiyse sonunda:

| Dosya | Dış avukat | Son bilgi | Neden dahil edildi |
|---|---|---|---|

**Atlananlar:** [dosya — neden: yakın tarihte bilgi alındı / dış avukatın e-postası yok]
**Dikkat:** dış avukat atanmamış yüksek riskli dosyalar.

### Kanal

- Ortamda e-posta taslağı aracı (ör. Outlook bağlayıcısı) varsa yalnız **taslak** oluştur; gönderme. Araç yoksa ya da hata verirse markdown taslak ver ve bunu söyle.
- Claude Code'da ve dosya klasörü etkinse taslaklar `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/yazismalar/<AAAA-AA-GG>-dis-avukat.md` altına yazılabilir; yazmadan önce kullanıcı onayı. Claude Code dışı istemcilerde e-postalar sohbette ayrı kopyalanabilir bloklar olarak verilir.
- Düzenli (haftalık) çalıştırma bu becerinin işi değildir; ortamda zamanlanmış görev aracı varsa kullanıcı isterse önerilir, yoksa "takviminize hatırlatma koyun" denir.

---

## 6. MCP adımları

Bu kip esas araştırması yapmaz; yalnız özetteki sayı ve tarihleri doğrular:
- Faiz türü ve oranı → `legal_get_legal_interest_rates`
- Kesinlik/temyiz sınırı ("itiraz yolu var mı") → `legal_get_social_parameters`
- Kanun yolu son günü → `legal_calculate_deadline`; diğer süreler alan becerisinden
- Karar künyesi → kullanıcı verdi ya da `legal_get_case_by_number`

## 7. Sık hatalar

- Hukuk notunu kısaltıp özet sanmak; özet karar odaklıdır, anlatı odaklı değil.
- Olasılık yüzdesi vermek.
- En kötü durum senaryosunda faizi ve karşı vekâlet ücretini unutmak.
- Yapılmamış takibi "takip ediyoruz" diye yazmak.
- "GİZLİDİR" başlığını geniş dağıtıma giden kopyada bırakıp korunduğunu sanmak.
