# Beyan takvimi, geç ödeme, pişmanlık, izaha davet, ceza tutarı ve tecil

## Ne zaman
- "KDV / muhtasar / geçici vergi / yıllık beyan son gün ne?", "son gün pazara denk geldi".
- "Geç ödedim, gecikme zammı ne kadar?", "beyannameyi unuttum, pişmanlıkla verirsem ne öderim?".
- "İzaha davet yazısı geldi", "ceza ihbarnamesindeki tutar doğru mu, 376 ile ne öderim?", "borcu taksitlendirebilir miyim (tecil)?".

Bu dosya **tutarı ve günü** verir. İzaha davete cevabın içeriği, pişmanlık şartlarının tartışmalı olduğu durum, uzlaşma ya da dava seçimi → `../../vergi/SKILL.md` (bkz. "Uyuşmazlığa dönüş").

---

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Vergi türü ve dönemi (ör. KDV 2026/09) | Kanuni son gün ve vade | Sor |
| Kanuni vade (ödeme süresinin son günü) | Zam ve faizin başlangıcı | Aşağıdaki tablodan bul, tatil kaydırmasını uygula `[doğrula]` |
| Ödeme / haber verme tarihi | Bitiş ve 15 günlük süre | Bugün varsay, sonucun başına yaz |
| Tutar (vergi aslı, ziyaa uğratılan vergi) | Hesabın tabanı | `[___]` |
| Beyanname hiç verilmedi mi, eksik mi verildi? | m.371/3 ya da /4 | Sor |
| İnceleme, takdir sevki, muhbir ihbarı ya da izaha davet var mı, tarihi? | m.371/1-2 ve m.370 kapısı | Sor; cevap belirsizse 🔴 ve kapıyı aç |
| Ceza türü ve ihbarname tebliğ tarihi | `vergi_cezasi` ve m.376 süresi | Sor |
| Tecilde başvuru tarihi, taksit planı | `tecil_faizi` dilimleri | Tecil yazısını iste |

---

## Araç çağrıları

```json
{ "hesap": "gecikme_zammi",   "gecikme_zammi": { "tutar": 0, "vade": "2026-09-26", "odeme": "2026-11-02" }, "tarih": "2026-11-02" }
{ "hesap": "pismanlik_zammi", "pismanlik_zammi": { "tutar": 0, "vade": "2026-09-26", "odeme": "2026-11-10" }, "tarih": "2026-11-10" }
{ "hesap": "gecikme_faizi",   "gecikme_faizi": { "tutar": 0, "vade": "2025-04-30", "odeme": "2026-10-15" }, "tarih": "2026-10-15" }
{ "hesap": "vergi_cezasi",    "vergi_cezasi": { "tur": "vergi_ziyai", "vergi": 0, "gec_beyan": true }, "tarih": "2026-11-02" }
{ "hesap": "vergi_cezasi",    "vergi_cezasi": { "tur": "usulsuzluk", "derece": 1, "grup": "sermaye_sirketi" }, "tarih": "2026-11-02" }
{ "hesap": "vergi_cezasi",    "vergi_cezasi": { "tur": "ozel_usulsuzluk", "kod": "<had kodu>", "adet": 1 }, "tarih": "2026-11-02" }
{ "hesap": "had",             "had": { "ara": "353" }, "tarih": "2026-11-02" }
{ "hesap": "tecil_faizi",     "tecil_faizi": { "tutar": 0, "baslangic": "2026-10-01", "odeme": "2027-01-31", "basvuru": "2026-09-25" }, "tarih": "2026-11-02" }
```

Araç davranışı:
- `gecikme_zammi`: ay kesri **günlük**; oran değişikliğinde dilim dilim; zam asgari tutarın altında kalırsa uyarıyla yükseltilir. GİB hesaplayıcısıyla karşılaştır uyarısı döner.
- `pismanlik_zammi`: ay **ve kesri tam ay**; uyarıda m.371 şartlarının ve 15 günün ayrıca kontrolü ister; emlak vergisinde uygulanmaz.
- `gecikme_faizi`: ay kesri **dikkate alınmaz**; `odeme` alanı bitiş tarihidir (tahakkuk / kararın tebliği / vazgeçme dilekçesi) ve kullanıcı seçer.
- `vergi_cezasi`: sonuçta `ceza` ve `m376_indirimli_ceza` birlikte gelir; tekerrür için `tekerrur_onceki_ceza`; özel usulsüzlükte yıllık üst sınır **kontrol edilmez** (uyarı).
- `tecil_faizi`: gün/365 basit faiz; başvurudan sonra yalnız yeni başvurulara uygulanan oran değişikliklerini atlar; tecil yazısındaki plan esastır.
- `ödeme ≤ vade` ise zam/faiz sıfır döner.

Süre kodları (`legal_calculate_deadline`): `tax_penalty_reduction_376`, `tax_settlement_request`, `iyuk_tax_lawsuit`. Pişmanlık 15 günü ve beyan son günü için kod yok: madde metninden say, son günü `legal_check_holiday` ile denetle.

---

## Hukuki çerçeve — son günler

| Beyan / ödeme | Kanuni süre | Dayanak |
|---|---|---|
| KDV beyanı ve ödemesi | Kanun: dönemi izleyen ayın belirli günü beyan, beyan ayının belirli günü ödeme; sorumlular için ayrı gün | [KDVK m.41](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/), [m.46](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla] |
| Muhtasar | Kanun: tevkifat yapılan ayı izleyen ayın belirli günü; az sayıda hizmet erbabı çalıştıranlara üç aylık seçenek | [GVK m.98](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]; KV muhtasarında ödeme [KVK m.21/4](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla] |
| Geçici vergi | Üç aylık dönemi izleyen ikinci ayın belirli günü beyan, belirli günü ödeme | [GVK mük.120](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] |
| Yıllık gelir vergisi | İzleyen yılın Mart ayında beyan; Mart ve Temmuz'da iki taksit | [GVK m.92](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/), [m.117](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] |
| Kurumlar vergisi | Hesap döneminin kapandığı ayı izleyen dördüncü ayda beyan; beyan ayının sonuna kadar ödeme | [KVK m.14/3](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/), [m.21/1](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla] |
| Damga (makbuz karşılığı) | Bakanlıkça belirlenenler: ertesi ayın belirli günü beyan ve ödeme; diğerleri kâğıdın düzenlenmesini izleyen 15 gün | [DVK m.22](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla] |

🔴 **Kanundaki gün uygulamadaki gün olmayabilir.** GİB, beyan ve ödeme son gününü kanuni süreden itibaren bir ayı geçmemek üzere yeniden belirleyebilir ([VUK mük.28](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]). Uygulamada KDV, muhtasar ve prim hizmet ve damga beyannamelerinin son günü kanundaki günden farklıdır; GİB sirkülerlerinde KDV için "28", muhtasar ve prim hizmet için "26/27" günlü uzatmalar görünür ([GİB Sirküler 689](https://gib.gov.tr/mevzuat/kanun/434/sirkuler/689) [soorgla]). Güncel son günü her dönem o yılın VUK genel tebliği ya da GİB duyurusundan teyit et `[doğrula]`. Yıllık GV ve KV beyan son günlerinin de bu yetkiyle kaydırılıp kaydırılmadığı `[doğrula]`.

- **Tatil:** son gün resmî tatile rastlarsa izleyen ilk iş gününün tatil saatinde biter ([VUK m.18/4](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]).
- **Mali tatil:** her yıl Temmuz'un ilk yirmi günü; son günü tatile rastlayan beyan ve bazı ödeme süreleri tatilin bitiminden itibaren uzar; ÖTV, BSMV, gümrük ve belediye vergilerinde uygulanmaz ([5604 m.1](https://soorgla.com/mevzuat/5604-mali-tatil-ihdas-edilmesi-hakkinda-kanun/) [soorgla]).
- **Gecikme zammı:** vadede ödenmeyen kısma vadenin bitiminden itibaren her ay için ayrı; ay kesri günlük ([6183 m.51](https://soorgla.com/mevzuat/6183-amme-alacaklarinin-tahsil-usulu-hakkinda-kanun/) [soorgla]).
- **Gecikme faizi:** ikmalen / re'sen / idarece tarhiyatta normal vadeden tahakkuka (davada kararın tebliğine, vazgeçmede dilekçe tarihine) kadar, gecikme zammı oranında; ay kesri nazara alınmaz ([VUK m.112/3](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]).
- **Tecil:** vadesinde ödeme borçluyu çok zor duruma düşürecekse, yazılı istek ve teminatla, faiz alınarak; teminatsız tecil sınırı ve süre üst sınırı madde metninden ([6183 m.48](https://soorgla.com/mevzuat/6183-amme-alacaklarinin-tahsil-usulu-hakkinda-kanun/) [soorgla]). Tecil şartlarına uyulmazsa alacak muaccel olur.

## Hukuki çerçeve — pişmanlık, izaha davet, ceza

| Yol | Ne zaman | Sonuç | Dayanak |
|---|---|---|---|
| **Pişmanlık** | Mükellef kendiliğinden dilekçeyle haber verir; önceden muhbir ihbarı yok, inceleme / takdir sevki başlamamış | Vergi ziyaı cezası kesilmez; beyan **15 gün** içinde verilir/düzeltilir, vergi pişmanlık zammıyla **15 gün** içinde ödenir | [VUK m.371/1-5](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] |
| **İzaha davet** | İdare ön tespit yapıp yazı tebliğ eder (inceleme / takdir sevkinden önce) | Davet konusunda **pişmanlıktan yararlanılamaz**; tebliğden itibaren **30 gün** içinde izah; izah yetersizse değerlendirme yazısından itibaren **30 gün** içinde beyan ve zamla ödeme şartıyla ceza madde metnindeki indirimli oranda | [VUK m.370](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] |
| **Kendiliğinden geç beyan** (pişmanlık şartsız) | İnceleme / takdirden önce süresi geçmiş beyan | Vergi ziyaı cezası azaltılmış uygulanır (`gec_beyan: true`) | VUK m.344/3 — `../../vergi/references/vergi-cezalari-ve-pismanlik.md` |
| **Cezada indirim** | İhbarname tebliğinden itibaren **30 gün** içinde başvuru, vadede (teminatla üç ay içinde) ödeme, dava açmama | Kesilen cezanın yarısı indirilir (`m376_indirimli_ceza`) | [VUK m.376](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] |

Pişmanlık **emlak vergisinde uygulanmaz** (m.371 son fıkra). m.370/b: 359 fiillerine ilişkin ön tespitte izaha davet yapılmaz; sahte / yanıltıcı belge kullanımında madde metnindeki sınırın altındakilere ön tespit yazısı tebliğ edilebilir → **doğrudan vergi becerisi**.

---

## Kontrol listesi

- ✅ Kanuni vadeyi ve tatil / mali tatil kaydırmasını ayrı yazdım; araca **asıl** vadeyi verdim.
- ✅ `pismanlik_zammi` ile `gecikme_zammi` farkını (ay kesri tam ay / günlük) çıktıda belirttim.
- 🔴 Pişmanlık dilekçesinden önce inceleme, takdir sevki, muhbir ihbarı ya da **izaha davet** var mı? Varsa pişmanlık hesabı verme, kapıyı aç.
- 🔴 Beyan ve ödeme haber vermeden itibaren 15 gün içinde mi? Geçtiyse pişmanlık düşer; `vergi_cezasi` ile tam ceza hesapla.
- 🟠 Pişmanlık zammı yalnız **ödeme süresi geçmiş** vergiye; KDV'de devreden / iade durumu ayrıca `[incele]`.
- 🟠 m.376 başvurusu 30 gün içinde mi, ödeme vadede mi? Dava açılırsa indirim kaybolur.
- 🟠 Tecilde teminat sınırı ve taksit sayısı madde metninden ve tecil yazısından; araç faizi gün/365 alır.
- 🟡 Aracın tüm `uyarilar` satırları Uyarılar bölümüne taşındı.
- [incele] İzaha davete verilecek izahın içeriği ve ön tespite itiraz.

## Sık hatalar

- 🔴 Kanundaki günü (ör. KDVK m.41) uygulamadaki son gün sanmak; mük.28 kaydırmasını atlamak.
- 🔴 İzaha davet tebliğ edilmişken aynı konu için pişmanlık zammı hesaplamak (m.370/a).
- 🟠 Pişmanlık zammında ay kesrini günlük hesaplamak (m.371/5 "her ay ve kesri").
- 🟠 Gecikme faizinde ay kesrini saymak (m.112/3 "ay kesirleri nazara alınmaz").
- 🟠 Gecikme zammını ceza tutarına uygulamayı unutmak ya da usulsüzlük cezasına uygulamak (6183 m.51/3: vergi ziyaı cezasına uygulanır).
- 🟡 Emlak vergisinde pişmanlık önermek.

## Uyuşmazlığa dönüş işareti

İzaha davet ya da ön tespit yazısı, vergi incelemesi başlangıcı, ihbarname, ödeme emri, haciz, sahte / yanıltıcı belge iddiası, "pişmanlık şartı tutuyor mu" tartışması, uzlaşma mı dava mı sorusu → başlığı değiştir (SKILL.md "Başlık ve uyuşmazlık kapısı") ve `../../vergi/SKILL.md`'ye devret. Taşı: hesaplanan zam/faiz/ceza tabloları, vade ve tebliğ tarihleri, aracın uyarıları.

## Çıktı

SKILL.md Adım 4 iskeleti. Hesap tablosunda sıra: vade → (tatil kaydırması) → ödeme/haber verme → gün / ay → oran dilimleri → zam/faiz → toplam. Ceza hesabında: esas ceza → azaltım/artırım → tekerrür → m.376 indirimli tutar. Sonda: "Pişmanlık 15 gününü ve m.376 30 gününü süre defterine ekleyeyim mi?" → `../../sure-takibi/SKILL.md`.
