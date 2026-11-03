# Damga vergisi ve harç

## Ne zaman
Sözleşme, taahhütname, kira kontratı, beyanname, bordro gibi kâğıtların damga vergisi; nüsha, birden çok akit, üst sınır ve istisna soruları. Tapu, noter ve ticaret sicili harcı. Dava ve icra harcı bu dosyanın değil, `../../hesaplamalar/references/harc.md` (`legal_calculate_court_fee`).

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Kâğıdın düzenlenme (imza) tarihi | Oran, maktu tutar ve üst sınır yıla göre | Sor |
| Kâğıdın türü ve içeriği (tek akit mi, bağlı akitler mi) | (1) sayılı tablodaki sıra; m.6 | Belgeyi iste; sıra tahmin etme `[incele]` |
| Kâğıtta yazılı belli para (KDV dahil/hariç, süre, yıllık mı toplam mı) | Nispi vergi matrahı | Sor; belirsizse `[incele]` |
| Nüsha sayısı ve imzalayan taraflar | m.5 nüsha; m.3 mükellef | Sor |
| Tarafların istisna durumu (ihracat, kamu, kredi, ücret vb.) | (2) sayılı tablo; araç kontrol etmez | Sor; istisnayı tablodan elle kontrol et |
| Harçta: işlem türü, beyan edilen bedel, emlak vergi değeri | Harç tarifesi ve m.63 matrahı | Sor |

## Aracı çağırma

`legal_calculate_tax`, hesap `damga`:

```json
{ "hesap": "damga", "girdi": { "ara": "kira" }, "tarih": "<imza tarihi>" }
```
Sıra bilinmiyorsa `ara` ile çağır; yanıt `adaylar` (sıra, açıklama, binde oran ya da maktu tutar) döner ve "kâğıt seçilmedi" uyarısı verir. Doğru sırayı kullanıcıyla seç, sonra:

```json
{ "hesap": "damga", "girdi": { "sira": "I.A.2", "tutar": "<sayı>", "nusha": 2 }, "tarih": "<imza tarihi>" }
```
Yanıt: `damga_vergisi`, `ust_sinir_uygulandi`; `ara_degerler` içinde binde oran, ham vergi, üst sınır ve yürürlük. Üst sınır tek başına: `{"hesap":"had","girdi":{"kod":"dvk_14_ust_sinir"}}`.

**Araç sınırları (koddan):**
- Maktu vergide sonuç = maktu × nüsha; nispi vergide nüsha sayısı tutarı değiştirmez ve uyarı yazar.
- **(2) sayılı tablodaki istisnalar ve m.14'teki tablo sınırlamaları kontrol edilmez**; her yanıtta uyarı olarak gelir. İstisnayı elle kontrol etmeden sonucu kesinleştirme.
- O tarih için üst sınır kaydı yoksa vergi **sınırsız** hesaplanır ve uyarı yazar; bu durumda üst sınırı genel tebliğden `[doğrula]`.
- Bir kâğıtta birden çok akit (m.6), sözleşme değişikliği, süre uzatımı, devir (m.14) için tek çağrı yetmez; her akit / artış için ayrı çağır ve sonucu m.6 ve m.14'e göre birleştir.
- Ücret bordrosundaki damga `ucret` hesabının içindedir; ayrıca çağırma.
- **Harç hesabı bu araçta yok.** Tapu, noter ve ticaret sicili harcı için tarife oranını ve maktu tutarı yıllık Harçlar Kanunu Genel Tebliği'nden çek, hesabı elle kur ve `[doğrula]` işaretle. (Parametre tablosunda harç tarifeleri var ama araç bunları bir hesap olarak açmıyor.)
- `legal_calculate_court_fee` yalnız yargı harçlarını tanır (`basvurma_sulh`, `basvurma_asliye`, `karar_ilam_nispi`, `pesin_harc`, `icra_tahsil_*`, `dava_masrafi_asliye`); `tapu_harci` gibi türlerde hata ve geçerli liste döner.

## Hukuki çerçeve — damga

- **Konu ve kâğıt tanımı:** (1) sayılı tablodaki kâğıtlar vergiye tabidir; kâğıt, imzalanarak ya da imza yerine geçen işaretle düzenlenen ve bir hususu ispat veya belli etmek için ibraz edilebilen belge ile elektronik imzalı elektronik belgedir. [Damga Vergisi Kanunu m. 1](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Mükellef:** kâğıdı imza edenler; resmî dairelerle kişiler arasındaki kâğıtlarda vergiyi kişiler öder. [Damga Vergisi Kanunu m. 3](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Nüsha:** maktu vergili kâğıtlarda her nüsha ayrı ayrı; nispi vergili kâğıtlarda yalnız bir nüsha vergilenir; poliçe ve emre yazılı senetlerde tedavüle çıkan nüshalar. [Damga Vergisi Kanunu m. 5](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Birden çok akit:** birbirinden tamamen ayrı akitlerin her birinden ayrı vergi; birbirine bağlı ve bir asıldan doğan akitlerde en yüksek vergiyi gerektiren üzerinden; başka bir kişinin eklediği akit ayrıca vergiye tabi; birden çok adi kefalet / garantiden yalnız biri; cezai şart, cayma tazminatı gibi müeyyide taahhütleri başlı başına sözleşme değilse vergilenmez. [Damga Vergisi Kanunu m. 6](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **İstisnalar:** (2) sayılı tablodaki kâğıtlar müstesnadır. Tablonun ilgili satırını çalışma anında çek (`legal_search_statute_semantic`, `mevzuat_no: "488"`, `yalniz_tablolar: true`); satırı tablodan doğrula `[doğrula]`. [Damga Vergisi Kanunu m. 9](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Oran ve üst sınır:** vergi (1) sayılı tablodaki nispet veya miktarlarda alınır; her bir kâğıt için vergi, tablodaki sınırlamalar saklı kalmak üzere kanunda yazılı ve her yıl yeniden değerleme oranında artırılan azami tutarı aşamaz. Belli parayı içeren mukavelenamenin değiştirilmesinde artan miktar aynı nispette vergilenir (azami tutardan vergilenmiş sözleşmede yalnız bedel artışı hariç); süre uzatımında aynı miktar veya nispette vergi; devirde azami tutardan vergilenmiş sözleşmede aslından alınan verginin dörtte biri. [Damga Vergisi Kanunu m. 14](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Ödeme:** makbuz karşılığı ödemede Bakanlıkça belirlenen mükellefler bir ayda düzenlenen kâğıtların vergisini ertesi ay beyannameyle bildirir ve öder; diğer hâllerde kâğıdın düzenlendiği tarihi izleyen kanunda yazılı süre içinde beyan ve ödeme. Günleri madde metninden ve beyan takviminden kontrol et. [Damga Vergisi Kanunu m. 22](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/) [soorgla]
- **Maktu tutar ve oranlar** yıllık Damga Vergisi Kanunu Genel Tebliği ile güncellenir; araçtaki `parametre` / `kaynak` alanını dayanak satırına yaz.

## Hukuki çerçeve — harç

- **Tapu harcı matrahı:** gayrimenkul devir ve iktisaplarında harç, emlak vergisi değerinden az olmamak üzere beyan edilen devir ve iktisap bedeli üzerinden hesaplanır; düşük bedelle harç ödendiğinin sonradan tespiti hâlinde eksik harç aranır. Oran ve taraf (devreden / devralan) (4) sayılı tarifede `[doğrula]`. [HARÇLAR KANUNU (492) m.63](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-63) [soorgla]
- **Noter harçları:** (2) sayılı tarifedeki işlemler harca tabidir; müeyyide niteliğindeki taahhütlerden ayrıca harç alınmaz; işlemin yapılmasını isteyen öder; değer veya ağırlığa göre nispi, diğerlerinde maktu; işlem bitmeden peşin alınır. [HARÇLAR KANUNU (492) m.38](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-38) [soorgla] · [m.40](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-40) · [m.41](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-41) · [m.49](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-49) [soorgla]
- **Ticaret sicili harçları:** (1) sayılı tarifenin "C) Ticaret sicili harçları" bölümündeki işlemlerin harcı odalarca tahsil edilir; harcı tam almadan işlem yapan sicil görevlileri ve odalar mükellefle birlikte müteselsilen sorumludur. [HARÇLAR KANUNU (492) m.132](https://soorgla.com/mevzuat/492-harclar-kanunu/#madde-132) [soorgla]
- **Tarife tutarları** her yıl Harçlar Kanunu Genel Tebliği ile ilan edilir; RG'den çek (`legal_search_official_gazette`, `query: "Harçlar Kanunu Genel Tebliği"`, `search_in: "title"`, `sort_by: "date_desc"`).

## Kontrol listesi

- 🔴 Kâğıt (1) sayılı tabloda var mı; sıra doğru seçildi mi (kira, mukavelename, taahhütname ayrımı)? `[incele]`
- 🔴 (2) sayılı tablodaki bir istisna uygulanıyor mu? Araç kontrol etmez.
- 🟠 Nispi vergide yalnız bir nüsha; maktu vergide her nüsha (m.5).
- 🟠 Bir kâğıtta birden çok akit: ayrı mı, bağlı mı (m.6)? Kefalet ve cezai şart ayrımı.
- 🟠 Üst sınır uygulandı mı (`ust_sinir_uygulandi`), o yılın sınırı yanıtta var mı?
- 🟡 Matrah: kira sözleşmesinde süre ve toplam bedel; KDV dahil/hariç ayrımı `[doğrula]` (tebliğ ve özelgeden).
- 🟡 Beyan ve ödeme süresi (m.22) ve sürekli mükellefiyet durumu.
- 🟡 Tapu harcında beyan edilen bedel emlak vergi değerinin altında mı (m.63)?

## Sık hatalar

- 🔴 Binde oranı, maktu tutarı, üst sınırı ya da harç tarifesini bellekten yazmak.
- 🟠 Nispi vergili sözleşmede her nüsha için vergi hesaplamak.
- 🟠 Cezai şart / cayma tazminatı için ayrıca damga vergisi hesaplamak (m.6 son fıkra).
- 🟠 Tapu, noter ya da sicil harcını `legal_calculate_court_fee` ile hesaplamaya çalışmak.
- 🟡 Sözleşme süre uzatımı ve devrini yeni sözleşme gibi tam vergilendirmek ya da hiç vergilendirmemek (m.14).

## Uyuşmazlığa dönüş

Damga vergisi ya da harç için ihbarname, inceleme raporu, tapuda düşük bedel tespiti nedeniyle eksik harç tarhı ya da usulsüzlük cezası görünürse `../../vergi/SKILL.md`'ye devret; hesaplanan tutar, sıra numarası ve araç uyarılarını taşı.

## Çıktı

SKILL.md Adım 4. Damga: kâğıt (tablo sırası) → matrah → binde oran ya da maktu × nüsha → üst sınır kontrolü → sonuç; "(2) sayılı tablo istisnası kontrol edildi mi" satırı her zaman Uyarılar'da. Harç: işlem → tarife satırı ve dönemi (tebliğ künyesi) → matrah (m.63 karşılaştırması) → harç `[doğrula]`.
