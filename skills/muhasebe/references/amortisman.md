# Amortisman (VUK 313-321)

Yılsonu ve geçici vergi dönemlerinde amortisman tablosu, faydalı ömür seçimi, normal / azalan bakiyeler, binek otomobilde kıst amortisman ve doğrudan gider yazma sınırı. Oran, ömür ve sınır tutarı bu metne yazılmaz; `legal_calculate_tax` (`amortisman`, `had`) ve madde metninden çekilir.

## Ne zaman
- "Bu makineyi kaç yılda amortismana tabi tutarım, yıllık ne ayırırım?"
- "Azalan bakiyelere geçebilir miyim?", "binek aracın ilk yıl amortismanı neden düşük?"
- "Bu demirbaşı doğrudan gider yazabilir miyim?"
- Yeniden değerleme sonrası amortisman (→ önce `yeniden-degerleme.md`, sonra bu dosya).

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Amortismana esas bedel (TL) | Tablonun tabanı | Sor; maliyete giren unsurlar (nakliye, montaj, ÖTV/KDV tercihi) `[incele]` |
| Kıymetin ne olduğu | Listedeki sıra ve faydalı ömür | `ara` ile listeyi tara, kullanıcıya seçtir |
| Aktife giriş tarihi | İlk yıl, binek kıstı, gün esası | Sor |
| Defter türü (bilanço / işletme) | Azalan bakiyeler yalnız bilanço esasında | Sor |
| Binek otomobil mi, kiralama işinde mi kullanılıyor | Kıst kuralı ve istisnası (m.320/2) | Sor |
| Önceki yıllarda seçilen yöntem ve ömür | Yöntem ve ömür sonradan değiştirilemez (m.320) | Sor |

## Araç çağrıları

```json
{ "hesap": "amortisman", "girdi": { "ara": "bilgisayar" }, "tarih": "2026-12-31" }
{ "hesap": "amortisman", "girdi": { "maliyet": 850000, "sira": "<listeden dönen sıra>", "yontem": "normal", "aktife_giris": "2026-03-15" }, "tarih": "2026-12-31" }
{ "hesap": "amortisman", "girdi": { "maliyet": 2400000, "omur": 5, "binek": true, "aktife_giris": "2026-09-10" }, "tarih": "2026-12-31" }
{ "hesap": "had", "girdi": { "kod": "vuk_313_demirbas" }, "tarih": "2026-12-31" }
```

- `ara` tek başına verilirse araç listede eşleşen sıraları (`sira`, `ad`, `omur`, `oran`) döndürür; kalemi kullanıcıyla seç, sonra `sira` + `maliyet` ile yeniden çağır.
- Listede tek ömür yoksa (özel oranlı kalem) araç hata verir ve `omur` ister.
- Binek gider/amortisman **sınırı** (KKEG kısmı) bu hesapta yok → `{ "hesap": "binek_oto", ... }` ve `gelir-ve-kurumlar-uygulamalari.md`.
- Tutarlar örnektir; her çağrıda kullanıcının rakamlarını kullan.

## Hukuki çerçeve

- **Konu:** işletmede bir yıldan fazla kullanılan, yıpranmaya, aşınmaya veya kıymetten düşmeye maruz gayrimenkuller, alet, edevat, mefruşat, demirbaş ve sinema filmleri amortismana tabidir. [Vergi Usul Kanunu m. 313](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Doğrudan gider yazma:** değeri kanundaki haddi aşmayan peştemallıklar ile alet, edevat, mefruşat ve demirbaşlar doğrudan gider yazılabilir; iktisadi ve teknik bütünlük arz edenlerde had topluca dikkate alınır. Had yıllık yeniden değerlenir: `had` `vuk_313_demirbas`. [Vergi Usul Kanunu m. 313](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Normal amortisman:** Bakanlığın faydalı ömre göre ilan ettiği oranlarla; m.320/4 saklı. [Vergi Usul Kanunu m. 315](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Faydalı ömür listesi:** 333 Sıra No.lu VUK Genel Tebliği eki liste ve değişiklikleri (339, 365, 389, 399, 406, 418 …). [VUK GT 333](https://soorgla.com/mevzuat/6120-vergi-usul-kanunu-genel-tebligi-sira-no-333/) [soorgla] Listede olmayan kıymet için Bakanlığa başvuru yolu VUK GT 399'da `[doğrula]`.
- **Azalan bakiyeler:** yalnız bilanço esasına göre defter tutanlar; oran normal oranın katı olup üst sınırı ve son yılda kalanın tamamen itfası maddede. [Vergi Usul Kanunu m. mükerrer 315](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Süre, binek kıstı, gün esası, ömür seçimi:** amortisman aktife girilen yıldan başlar; binek otomobilde (kiralama/işletme amacıyla kullananlar hariç) aktife girilen dönem için ay kesri tam ay sayılarak kalan ay kadar ayrılır, ayrılmayan kısım son yılda itfa edilir; dileyen yeni kıymette gün esasına göre ayırabilir (m.320/3); Bakanlık ömründen kısa olmamak ve maddedeki üst sınırları aşmamak üzere ömrü uzatabilir, tercih envantere alındığı geçici vergi dönemi sonunda kullanılır ve değiştirilemez (m.320/4); başlanan hesaplama şeklinden vazgeçilemez (m.320/7); bir yıl ayrılmaması süreyi uzatmaz. [Vergi Usul Kanunu m. 320](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- Yöntem değişikliği (normalden azalana / azalandan normale) ve 318, 321 (fevkalade amortisman, ilk tesis) madde metninden doğrulanmalı `[doğrula]`.

## Kontrol listesi

- ✅ Kalem listede bulundu, sıra ve ömür araçtan geldi.
- 🔴 Önceki yıllarda başka ömür/yöntem seçilmişse tablo değişmez (m.320/4, /7); kullanıcı "yeniden hesapla" diyorsa dur.
- 🔴 Azalan bakiyeler işletme hesabı esasında **uygulanamaz** (mük.315).
- 🟠 Binek otomobil: kıst (m.320/2) + gider sınırı (`binek_oto`) ikisi birlikte; birini unutmak KKEG hatası.
- 🟠 Doğrudan gider: bütünlük arz eden takım (bilgisayar + monitör + yazılım seti gibi) topluca değerlendirilir `[incele]`.
- 🟡 Yeniden değerleme yapıldıysa amortisman yeni değer üzerinden devam eder (mük.298/Ç-5).
- 🟡 Gün esası (m.320/3) seçildiyse araç bunu **hesaplamaz**; elle kur `[doğrula]`.
- [incele] Maliyete eklenen kur farkı ve kredi faizi (aktifleştirme yılı sonrası) — `yeniden-degerleme.md` ve VUK 262/274.

## Sık hatalar
- Binek otomobilin ilk yılında tam yıl amortisman ayırmak.
- Azalan bakiyelerde her yıl maliyet üzerinden hesaplamak (kalan değer üzerinden olmalı).
- Doğrudan gider haddini fatura toplamına değil kalem bazına uygulamak ya da bütünlüğü atlamak.
- Önceki yılın haddini kullanmak: `tarih` alım tarihine göre ver.
- Listedeki ömür yerine "ekonomik ömür" (TFRS) kullanmak; vergi tablosu ile ticari tablo ayrı tutulabilir `[incele]`.

## Aracın sınırları (uyarılardan)
- Gün esası (m.320/3) ve ömür uzatma (m.320/4) uygulanmaz; yeniden değerleme ya da enflasyon düzeltmesi sonrası değerler ayrıca hesaplanır.
- Binek kıstında ay kesri tam ay sayılır; ayrılmayan kısım son yılda itfa edilir.
- Azalan bakiyeler seçildiğinde "yalnız bilanço esası" uyarısı döner; defter türünü araç kontrol etmez.

## Yevmiye kaydı önerisi

```
31.12.AAAA
770 / 760 / 730 … Gider hesabı (gider yerine göre) [yıllık amortisman]
        257 Birikmiş Amortismanlar [yıllık amortisman]
```
- 257 kodu VUK GT 537 örnek kayıtlarından.
- Gider hesabının seçimi (770 Genel Yönetim, 760 Pazarlama, 730 Genel Üretim) ve maddi olmayan duran varlıkta 268 kodu MSUGT'den okunmadı `[doğrula]`.
- Doğrudan gider yazılan demirbaş: ilgili gider hesabı (borç) / 100-102-320 (alacak) `[doğrula]`.

## Uyuşmazlığa dönüş
İnceleme amortisman oranını, maliyet unsurunu ya da binek KKEG'ini eleştirdiyse, ihbarname geldiyse → kapıyı aç, `../../vergi/SKILL.md`. Taşı: tablo, araç uyarıları, seçim tarihleri.

## Çıktı
SKILL.md Adım 4 iskeleti. Hesap tablosu araçtaki `yillik` dizisinden (yıl, amortisman, birikmiş, net değer); altına formül ve `uyarilar` satırları.
