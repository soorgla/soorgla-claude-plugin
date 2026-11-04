# İdare belgeleri — zorunlu unsurlar ve iskeletler

İhaleyi yapan idarenin belgeleri. Kullanıcı çoğunlukla ihale birimi personeli, komisyon üyesi ya da idarenin hukuk müşaviridir. **İmza yetkisi olmayan kullanıcı adına imza satırı doldurulmaz**; onay zinciri `[Ad SOYADI — unvan]` kalır. Her başlıkta: dayanak, e-form, zorunlu unsurlar, **İdare ne yapmalı**, **İstekli neye bakar / nasıl itiraz eder**.

Resmî yazının genel biçimi (sayı, konu, ilgi, dağıtım, olur): `../../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md`. E-form sürümleri `[KİK e-form listesi 2026-10-31 — doğrula]`; formu form bankası kimliğiyle an (`KIK-KIK0xx-<TÜR>`, ör. `KIK-KIK001-YAPIM`) — ayrıntı `form-kutuphanesi-ve-ekap.md`.

---

## 1. İhale onay belgesi

**Dayanak:** Mal Yön. m.16 (ön ilan varsa ilandan önce onay belgesi + yaklaşık maliyet hesap cetveli; ihale/ön yeterlik ilanından önce yeniden onay); m.18 (ihale işlem dosyasının ilk belgesi). Karşılık maddeler: Hizmet Yön. m.18, Yapım Yön. m.19, Danışmanlık Yön. m.18 ("İhale onayının alınması"; danışmanlıkta ön yeterlik ilanından önce yeniden onay) `[soorgla]`.  Fiyat dışı unsurda gerekçeli açıklama belgesi onay belgesine eklenir (Hizmet Yön. m.61/4). 

**E-form:** KİK001 İhale Onay Belgesi (iki bölüm: ön ilan aşaması / ihale aşaması). Eki: yaklaşık maliyet hesap cetveli; yapımda KİK002 Yaklaşık Maliyet İcmal Tablosu; birim fiyat teklifinde KİK003 Teklif Türünün Belirlenmesi.

| # | KİK001 alanı | İdare dikkat | İstekli neye bakar |
|---|---|---|---|
| 1 | İhaleyi yapan idare; "[ihale yetkilisinin unvanı] MAKAMINA" | yetkili makam doğru mu (4734 m.4 ihale yetkilisi) | — |
| 2 | İşin adı; türü ve miktarı/kapsamı | ilan ve dokümanla aynı ad | adla doküman çelişkisi şikâyet konusu olabilir |
| 3 | Yaklaşık maliyet | **gizli** — dışa giden metne konmaz | açıklanmaz (ihale saatinde açıklanır) |
| 4 | Kullanılabilir ödenek; yatırım proje no; bütçe tertibi | **ödeneksiz ihale yapılmaz** (4734 m.5: "Ödeneği bulunmayan hiçbir iş için ihaleye çıkılamaz" `[soorgla]`)  | — |
| 5 | İhale usulü; ilanın şekli ve adedi | usul ve ilan süresi `legal_calculate_tender` `usul_kontrol` | yanlış usul / kısa ilan → şikâyet (`ihale-sikayet`) |
| 6 | Avans şartları; fiyat farkı dayanağı (CB kararı) | 4735 m.8 esaslarıyla tutarlı | — |
| 7 | Teklif ve sözleşme türü | KİK003 eki (birim fiyat) | — |
| 8 | Ekler: YM hesap cetveli, FDU gerekçe belgesi | eksikse Sayıştay riski | — |
| 9 | Hazırlayan ve "Uygundur" — ihale yetkilisi ad, unvan, imza, tarih | tarih ilandan önce | onay ilandan sonraysa `[incele]` |

## 2. İlan metni kontrolü

**Dayanak:** 4734 m.24 — ilanda dokümanda olmayan hususa yer verilemez; zorunlu hususlar (a)-(n): idarenin adı-adres-telefon; işin adı, niteliği, türü, miktarı; teslim/iş yeri; işe başlama ve bitiş; usul, katılım şartları ve istenen belgeler; yeterlik kriterleri; yerli istekliye açıklık / fiyat avantajı; dokümanın görülebileceği yer; ihalenin yeri, tarihi, saati; tekliflerin nereye verileceği; teklif ve sözleşme türü; en az %3 geçici teminat; teklif geçerlilik süresi; konsorsiyum. Hatalı ilan → m.26: m.13, 24, 25'e aykırı ilan geçersizdir; ilan yapılmaması ya da ilan süresine uyulmaması dışındaki m.24-25 hatalarında, 25 ve 40 günlük ilan süreli ihalelerde ilanı izleyen 15, diğerlerinde 10 gün içinde düzeltme ilanı yapılarak ihale yapılabilir. 

**E-form:** KİK004 İhale İlanı (V4, 02.09.2026 2026/DK.D-278 — en yeni sürümlerden; eski ilan şablonunu kullanma); fiziki teklifte KİK201; ön yeterlik KİK200 / KİK224; ön ilan KİK005.

Kontrol: m.24 harflerini tek tek tablo yap (✅/🔴); her satırı idari şartnamenin ilgili maddesiyle karşılaştır (ör. yeterlik → m.7; geçici teminat → m.26; geçerlilik → m.24). **İstekli:** ilan-doküman çelişkisi doküman şikâyeti konusudur; süre ilk ilan tarihinden başlar (4734 m.55/1) → `ihale-sikayet`.

## 3. Zeyilname ve düzeltme ilanı

**Dayanak:** 4734 m.29 — ilandan sonra doküman değiştirilmemesi esas; maddi/teknik hata veya eksiklikte değişiklik yapılabilir; **zeyilname** dokümanın bağlayıcı parçasıdır ve **son teklif gününden en az 10 gün önce** bilgi sahibi olunacak şekilde dokümanı alanların tamamına gönderilir; ek süre gerekiyorsa ihale tarihi **bir defaya mahsus en fazla 20 gün** zeyilnameyle ertelenir; zeyilnameden önce teklif verenlere geri çekip yeniden verme imkânı. Esaslı değişiklik zorunluysa tutanakla ilan iptal, yeniden ilan. 

Zeyilname için KİK e-form listesinde ayrı form yok `[doğrula]` ; düzeltme ilanı KİK006 (4734 m.26), iptal ilanı KİK007.

```markdown
                                  ZEYİLNAME NO: [__]
İKN            : [___]
İşin adı       : [___]
İhale tarihi   : [mevcut] → [ertelendiyse yeni tarih/saat — en fazla 20 gün, bir defa]

[İhale dokümanının] aşağıda belirtilen maddeleri 4734 sayılı Kanunun 29 uncu maddesi uyarınca
değiştirilmiştir. Bu zeyilname ihale dokümanının bağlayıcı bir parçasıdır.

| Belge / madde | Eski metin | Yeni metin |
|---|---|---|
| [İdari Şartname m.__] | [___] | [___] |

Zeyilnameden önce teklif vermiş istekliler tekliflerini geri çekerek yeniden teklif verebilir.

                                                   [Ad SOYADI — İhale Yetkilisi / unvan]
Dağıtım: dokümanı EKAP'tan indiren bütün istekliler
```

- **İdare:** gönderim tarihini son teklif gününden geriye **10 gün** hesapla (olay günü sayılmaz; süre kodu yok → elle, `legal_check_holiday`, `[incele]`). Zeyilname esaslı değişikliğe dönüyorsa (yeterlik kriterini genişletme gibi) yeniden ilan değerlendir `[incele]`. Şikâyet üzerine düzeltme kararında erteleme m.55/2.
- **İstekli:** zeyilname geç geldiyse (10 gün kuralı) ya da yeni aykırılık getiriyorsa ona karşı doküman şikâyeti süresi zeyilnamenin bildiriminden `[incele]` → `ihale-sikayet`.

## 4. Açıklama isteme yazıları

| Yazı | Dayanak | E-form | Zorunlu unsur |
|---|---|---|---|
| Aşırı düşük teklif açıklama talebi | 4734 m.38; Hizmet Yön. m.59, Mal Yön. m.58 | KİK022 (V4, 2025/DK.D-393) | İKN, işin adı, EKAP tebliğ tarihi/sayısı, istekli, teklif tarihi, **son gün ve saat**, **açıklanması istenen önemli bileşenler listesi**, ekler, idare yetkilisi |
| Bilgi eksikliğinin tamamlatılması | 4734 m.37/2; Mal Yön. m.55, Hizmet Yön. m.56; danışmanlıkta en az 2 iş günü (Danışmanlık Yön. m.54/4; kod `kik_info_completion_min`, canlı) | listede yok `[doğrula]` | eksik **bilgi** ve dayandığı belge, süre, tamamlamamanın sonucu (değerlendirme dışı + teminat gelir kaydı) |
| Belgelerin fiziki sunulması | idari şartname m.29.6, 29.12 | KİK030 | istenen belge, süre, sunuluş şekli |
| Teklife açıklık getirme (net olmayan husus) | 4734 m.37/1 — fiyat değiştirilemez, uygunsuz teklif uygun hâle getirilemez | yok | soru, süre, "fiyat değişikliği kabul edilmez" cümlesi |
| Numune / demonstrasyon | idari şartname m.29.9 | KİK021 | — |

- **İdare:** aşırı düşük sorgusunda bileşenleri KİGT'deki ölçüte göre seç ve yaz; sorgu süresi asgari süreden kısa olamaz: yapımda en az **5 iş günü** (KİGT 45.1.2), hizmette en az **3 iş günü** (KİGT m.79); malda ve danışmanlıkta süreyi komisyon belirler `[soorgla]`. Kodlar `kik_low_bid_explanation_works_min` / `_services_min` canlı; araç yanıt vermezse elle say.   Belge eksikliğini "bilgi eksikliği" diye tamamlatma.
- **İstekli:** yazıda bileşen belirtilmemişse ya da süre asgari süreden kısaysa bunu şikâyette kullan → `ihale-sikayet`.

## 5. İhale komisyonu kararı — gerekçe bölümü

Tam iskelet: `../../idari-ve-kurum-basvurulari/references/ihale-idare-kararlari.md` §1. Burada yalnız e-form eşlemesi ve gerekçe denetimi.

**E-form:** KİK024 İhale Komisyonu Kararı (e-ihale); fiziki/danışmanlıkta KİK239; danışmanlıkta ayrıca KİK240 Teklif Nihai Değerlendirme Tutanağı. **Dayanak:** 4734 m.40 (gerekçeli karar, 5 iş günü onay, onaydan önce ilk iki teklif sahibinin yasaklılık teyidi); Hizmet Yön. m.65, Mal Yön. m.64. 

KİK024 başlık alanları: İKN, karar no, idare, işin adı, ihale tarih-saati, usul, YM, **sınır değer**, doküman indiren sayısı, toplam teklif, aşırı düşük teklif sayısı, geçerli teklif sayısı, EAAT ve ikinci EAAT (sahip + tutar), tutanak tarih-saati, istekli tablosu (teklif, FDU puanı, yerli avantajı sonrası bedel).

**Gerekçe bölümü denetimi** (formdaki talimat: işlemler başından itibaren ayrıntılı, karşı oy gerekçesi, değerlendirme dışı bırakma gerekçeleri, iptalde reddetme gerekçeleri):
- Her elenen istekli için **somut** gerekçe: hangi belge, idari şartnamenin hangi maddesi, hangi eksiklik. "Belgeler uygun değil" 🟠.
- Aşırı düşükte: sorgulanan bileşenler, açıklamanın neden yetersiz olduğu bileşen bileşen.
- Sınır değer hesabı ve hangi tekliflerin "geçerli" sayıldığı (yöntem tür becerisinde).
- Yasaklılık teyidinin tarihi ve eki. Karşı oy varsa gerekçesi ve imzası.
- **İstekli:** gerekçe soyutsa ya da şartname maddesi gösterilmemişse şikâyet konusu; farkına varma tarihi çoğu olayda KİK025 bildirimidir → `ihale-sikayet`.

## 6. Kesinleşen ihale kararı bildirimi

**Dayanak:** 4734 m.41 (onayı izleyen en geç 3 gün içinde teklif veren bütün isteklilere komisyon kararıyla birlikte; iptalde gerekçeli bildirim; bildirimden 21/b-c'de 5, diğerlerinde 10 gün geçmeden sözleşme imzalanamaz); Hizmet Yön. m.66. 

**E-form:** KİK025 Kesinleşen İhale Kararının Tebliği; bütün tekliflerin reddiyle iptal KİK026; iptal kararının tebliği KİK027.

Zorunlu: İKN, ihalenin adı, EKAP tebliğ tarihi ve sayısı, muhatap istekli, ihalenin kimde kaldığı, **ekonomik açıdan en avantajlı ikinci teklif sahibi** (ya da "bulunmamaktadır"), ek: onaylı komisyon kararı (sayfa sayısıyla), **şikâyet süresi cümlesi** ("tebliğ tarihini izleyen günden itibaren [on / 21-b,c'de beş] gün içinde idaremize EKAP üzerinden e-şikâyet"). 🔴 süre cümlesi yanlışsa (21/b-c'de 10 yazmak gibi) bildirim tartışmalı olur `[incele]`.

## 7. Sözleşmeye davet

**Dayanak:** 4734 m.42 (m.41 sürelerinin bitimini, ön mali kontrolde kontrolün tamamlandığı tarihi izleyen günden itibaren **3 gün** içinde; tebliği izleyen **10 gün** içinde kesin teminat vererek imza; yabancıya +12 gün; imza günü yasaklılık teyidi); m.43 kesin teminat; Hizmet Yön. m.67. 

**E-form:** KİK028 (V4, 17.12.2025 2025/DK.D-465); fiziki teklifte KİK221 (V6, aynı karar). Zorunlu: İKN, işin adı, EKAP tebliğ tarihi/sayısı, istekli, işin uhdesinde kaldığı, **10 günlük** süre ve EKAP'taki "Sözleşme Belgelerinin EKAP Üzerinden Gönderilmesi" sayfası (KİK029), m.10/1-b oda kaydı ve m.10/4 (a), (b), (e), (g) belgeleri, ihale kararı ve sözleşme damga vergisi, sözleşme bedeli eşiği aşıyorsa **onbinde beş KİK payı**, kesin teminat oranı (**teklif fiyatının %6'sı / sınır değer altında yaklaşık maliyetin %9'u**), teminat mektubunun asgari süresi, dokümanda istenen diğer belgeler. Eşik tutarı yazılmaz → `legal_get_social_parameters`.

- **İdare:** davet tarihini bekleme süresinin bitiminden say (`kik_standstill`, `kik_contract_invitation` — canlı; `kural_adi`'yi kontrol et, `[incele]`). Şikâyet ya da itirazen şikâyet varsa nihai karar beklenir (4734 m.55 son fıkra).
- **İstekli:** 10 günü tebliği izleyen günden say; belgeyi ve teminatı son güne bırakma. İmzalamamanın sonucu: geçici teminat gelir kaydı ve yasaklama (Hizmet Yön. m.67/3, m.68) → `kamu-ihale`.
- **İdare imzalamazsa (istekli):** m.42 ve 44'teki sürede idare görevini yapmazsa istekli, sürenin bitmesini izleyen günden itibaren en geç **5 gün** içinde **10 gün süreli noter ihbarnamesiyle** bildirerek taahhüdünden vazgeçebilir; geçici teminat geri verilir, belgelendirilmiş teminat giderleri istenebilir (4734 **m.45**) `[soorgla]`. Kodlar `kik_contract_withdrawal_notice` / `kik_contract_withdrawal_period` canlı. 

## 8. Şikâyete karar (KİK113)

Tam iskelet ve karar türleri: `../../idari-ve-kurum-basvurulari/references/ihale-idare-kararlari.md` §2; kurgu `ihale-sikayet`. **E-form:** KİK113 E-Şikâyet Başvurusu Üzerine İdare Tarafından Alınacak Karar. Alanlar (her biri doldurulmalı): EKAP tebliğ tarihi; ihalenin adı ve İKN; ihale tarihi; ihale kararının onay tarihi; başvuru sahibi ve adresi; vekil; **başvuru sahibinin ehliyeti** (aday / istekli / istekli olabilecek / diğer); dilekçenin kayda alındığı tarih ve sayı; kararın tarihi; ara kararlar (raportör, bilgi-belge istemi); iddiaların özeti; **iddiaların değerlendirilmesi**; hukuki sebepler, gerekçe ve sonuç; haklı bulunursa düzeltici işlem; **itiraz mercii ve süresi**; ihale yetkilisi imza. Kanun yolu cümlesi: bildirimi izleyen 10 gün içinde Kuruma itirazen şikâyet; iptal kararında 5 gün doğrudan Kuruma (4734 m.55/4, m.56/1).

## 9. KİK'e görüş / bilgi-belge yazısı

İtirazen şikâyet üzerine Kurum ihale işlem dosyasını ve idarenin görüşünü ister; istenen bilgi ve belgelerin belirtilen süre içinde verilmesi zorunludur (Başvurular Yön. m.19/1, 4; 4734 m.53/b) `[soorgla]`.  Ayrı e-form yok `[doğrula]` ; resmî yazı biçimi.

```markdown
                                     T.C.
                                [İDARENİN ADI]
Sayı : E-[___]                                                       [gg.aa.yyyy]
Konu : [İKN] İKN'li ihaleye ilişkin itirazen şikâyet başvurusu hk.
İlgi : Kamu İhale Kurumunun [tarih] tarihli ve [sayı] sayılı yazısı.

KAMU İHALE KURUMU BAŞKANLIĞINA
                                                                       ANKARA
İlgi yazı ile istenen bilgi ve belgeler ekte sunulmuştur.
İtirazen şikâyet dilekçesindeki iddialara ilişkin İdaremiz görüşü:
1) İddia [no]: [iddianın özeti] — [ilgili doküman maddesi] — [mevzuat] — [idare görüşü]
2) [___]
Başvurunun süre/ehliyet yönünden değerlendirmesi: [şikâyet tarihi, farkına varma tarihi, bedel — varsa] [incele]

Bilgilerinize arz ederim.                                   [Ad SOYADI — İhale Yetkilisi / unvan]
EKLER: 1- İhale işlem dosyası ([___] klasör / EKAP)  2- Şikâyet dilekçesi ve idare kararı  3- [___]
```

- **İdare:** görüşü **yalnız dilekçedeki iddialar** üzerinden, numarasıyla ver; şikâyet kararında olmayan yeni gerekçe eklemek Kurul incelemesinde tartışma yaratır `[incele]`. Süresinde gönderilmeyen belge idare aleyhine sonuç doğurabilir 🔴.
- **İstekli:** bu yazıya erişimi sınırlıdır; Kurul kararında idare görüşü aktarılır — dava aşamasında incele.
