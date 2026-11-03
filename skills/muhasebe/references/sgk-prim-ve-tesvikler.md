# SGK prim oranları, PEK sınırları ve teşvik şart kontrolü

Oran ve sınır: `legal_calculate_tax` `hesap: "had"` (kodlar `sgk_*`). Bu dosya **teşvik tutarı hesaplamaz**; teşvikten yararlanma şartlarını kontrol listesine çevirir. SGK işlemine itiraz ve teşvik iptali uyuşmazlığı `../../sosyal-guvenlik-sgk/SKILL.md`'de kalır.

## Ne zaman

- "Bu ay prim oranları ne?", "PEK tavanı ne kadar?", "İşveren payı yüzde kaç?"
- "Hazine indiriminden yararlanabilir miyiz?", "İmalat indirimi bize uygulanır mı?"
- "Yeni işe aldığımız kişi için teşvik var mı?", "Borç yapılandırması teşviki keser mi?"
- Brüt-net hesabı → `brutten-nete.md`; geç ödeme → `sgk-gecikme-ve-bildirge.md`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Dönem (YYYY-AA) | Oran ve sınır dönemden gelir | Sor |
| İşveren türü: özel / kamu; kamu ihalesi işi mi | m.81/1-ı ve 4447 geç.10 kapsam dışı sayar | Sor 🟠 |
| Faaliyet: imalat mı (NACE) | geç.108 | Sor; vergi levhası/NACE iste |
| APHB/MUHSGK süresinde verildi mi, primler süresinde ödendi mi | Şart | Sor 🔴 |
| SGK'ya prim, İPC, gecikme borcu var mı; tecil/yapılandırma devam ediyor mu | Şart | Borç dökümü iste 🔴 |
| Sigortalı türü: 4/a, SGDP'li (emekli), yurt dışı | Kapsam dışı olabilir | Sor |
| Yeni işe alım ise: işe giriş tarihi, önceki aylarda bildirim, İŞKUR kaydı, yaş, belge | Teşvik şartı | Sor |
| Son bir yılda kaçak/fiktif sigortalı tespiti | Bir yıl yararlanamama | Sor |

## Araç çağrıları

Listeyi çek, sonra tek kodla dönemi doğrula:
```json
{ "hesap": "had", "girdi": { "ara": "sgk" }, "tarih": "2026-03-31" }
```
```json
{ "hesap": "had", "girdi": { "kod": "sgk_pek_ust_aylik" }, "tarih": "2026-03-31" }
```
Başlıca kodlar: `sgk_myo_sigortali`, `sgk_myo_isveren`, `sgk_kvs_isveren`, `sgk_gss_sigortali`, `sgk_gss_isveren`, `sgk_issizlik_sigortali`, `sgk_issizlik_isveren`, `sgk_issizlik_devlet`, `sgk_pek_alt_gunluk`, `sgk_pek_alt_aylik`, `sgk_pek_ust_aylik`, `sgk_pek_ust_kat`, `sgk_hazine_indirimi`, `sgk_hazine_indirimi_imalat`, `sgk_sgdp_sigortali`, `sgk_sgdp_isveren`, `sgk_istege_bagli`. Listede olmayan kodu tahmin etme; `ara` ile bul. Kaynak alanı "İKİNCİL" ise `[doğrula]`.

Mevzuat:
```
legal_get_statute_article law_no: "5510" article_no: "81" law_type: "Kanun"
legal_get_statute_article law_no: "5510" article_no: "82" law_type: "Kanun"
legal_get_statute_article law_no: "5510" article_no: "geçici 108" law_type: "Kanun"
legal_get_statute_article law_no: "4447" article_no: "geçici 10" law_type: "Kanun"
legal_search_admin_guidance sorgu: "<teşvik adı> uygulama genelgesi" kurum: "Sosyal Güvenlik Kurumu"
```

## Hukuki çerçeve

- **Prim oranları ve paylaşım:** MYÖ işçi/işveren payı, KVS'nin tamamı işverende, GSS işçi/işveren payı, fiili hizmet zammı ek puanının tamamı işverende. [5510 m. 81](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **İşsizlik primi:** işçi, işveren ve Devlet payı; işveren işsizlik payını işçiden kesemez. [4447 m. 49](https://soorgla.com/mevzuat/4447-issizlik-sigortasi-kanunu-sosyal-sigortalar-kanunu-tarim-iscileri-sosyal-sigortalar-kanunu-turkiye-cumhuriyeti-emekli/) [soorgla]
- **PEK alt/üst sınırı:** günlük alt sınır yaşa uygun asgari ücretin otuzda biri; üst sınır alt sınırın kanunda yazılı katı; birden çok işte üst sınırı aşan prim talep üzerine iade. [5510 m. 82](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Hazine indirimi (m.81/1-ı) şartları:** özel sektör, 4/a sigortalı; APHB ve MUHSGK yasal sürede verilmiş; sigortalı hissesi ile Hazinece karşılanmayan işveren hissesi yasal sürede ödenmiş; prim, İPC, gecikme cezası ve zammı borcu yok — **ama** 6183 m.48 tecil/taksit ve yapılandırma devam ettiği sürece yararlanılır. Kapsam dışı: 5335 m.30/2 kurumları, 2886/4734 ve uluslararası anlaşma kapsamındaki alım-yapım işyerleri, SGDP'liler, yurt dışında çalışanlar. Hazinece karşılanan tutar GV/KV'de gider yazılamaz; diğer desteklerle birlikte uygulanırsa önce bu uygulanır. [5510 m. 81/1-ı](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Yaptırım:** kontrolde sigortasız ya da fiilen çalışmayan bildirilen kişi tespitinde işveren bir yıl m.81 desteklerinden yararlanamaz; yersiz yararlanma gecikme cezası ve zammıyla geri alınır. [5510 m. 81](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **İmalat:** m.81/1-ı'deki puan imalat sektöründe artırılmış uygulanır; madde süre sınırlı, CB uzatabilir. [5510 geç. m. 108](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla] Hesap döneminde yürürlükte mi, uzatma CBK'sı var mı → `[doğrula]` (RG araması).
- **İl bazlı ilave puan:** CB'ye m.81/1-ı puanına alt sınır üzerinden ilave puan ekleme yetkisi. [5510 m. 81](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **6111 istihdam teşviki (4447 geç.10):** ilave istihdam, önceki altı ayda bildirilmemiş olma, yaş/belge/İŞKUR kaydına göre süre; m.81/1-ı'den sonra kalan işveren hissesine uygulanır; Fondan karşılanan tutar gider yazılamaz; uygulama süresi kanunda sınırlı, CB uzatma yetkisi var. [4447 geç. m. 10](https://soorgla.com/mevzuat/4447-issizlik-sigortasi-kanunu-sosyal-sigortalar-kanunu-tarim-iscileri-sosyal-sigortalar-kanunu-turkiye-cumhuriyeti-emekli/) [soorgla] 2026 için uzatma kararı çıktı mı `[doğrula]`.
- **7103 prim desteği (4447 geç.19):** işe alım dönemi kanunda sınırlı, CB uzatma yetkisi sınırlı; yeni işe alımda güncel olarak uygulanabilirliği `[doğrula]`. Aynı ayda aynı sigortalı için başka teşvikle birleşmez. [4447 geç. m. 19](https://soorgla.com/mevzuat/4447-issizlik-sigortasi-kanunu-sosyal-sigortalar-kanunu-tarim-iscileri-sosyal-sigortalar-kanunu-turkiye-cumhuriyeti-emekli/) [soorgla]
- **Engelli çalıştırma teşviki:** kontenjan dahilinde/fazlası engelli için işveren hissesinin alt sınır üzerinden Hazinece karşılanması. [İş Kanunu m. 30](https://soorgla.com/mevzuat/4857-is-kanunu/) [soorgla] 5510 dönemindeki uygulama ve atıf karşılığı `[doğrula]`.
- Diğer teşvikler (genç/kadın istihdamı, Ar-Ge, bölgesel yatırım teşvik belgesi primi, ek 2 vb.) bu dosyada sayılmaz: güncel liste için SGK genelgesini `legal_search_admin_guidance` ile ara; yatırım teşviki → `../../tesvik-yatirim/SKILL.md`.

## Kontrol listesi — teşvik şartı

- 🔴 Primler ve bildirge yasal sürede mi? Bir günlük gecikme o ay indirimi düşürebilir; geriye dönük iptal riski.
- 🔴 Kesinleşmiş, yapılandırılmamış SGK borcu var mı (İPC ve gecikme zammı dahil)?
- 🟠 Tecil/yapılandırma devam ediyor mu, taksit aksadı mı? Aksadıysa yararlanma kesilir `[incele]`.
- 🟠 İşyeri kamu ihalesi kapsamında mı (m.81/1-ı ve 4447 geç.10 dışlar)?
- 🟠 SGDP'li (emekli) çalışan için Hazine indirimi uygulanmaz.
- 🟠 Birden çok teşvik aynı sigortalı/ay için çakışıyor mu? Öncelik ve birleşme yasağı madde metninden.
- 🟡 İmalat: faaliyet kodu imalatta mı, geç.108 dönemde yürürlükte mi?
- 🟡 Son bir yılda kaçak/fiktif sigortalı tespiti var mı?
- [incele] "Fiilen çalışmayan" tespiti ya da yersiz teşvik geri alma yazısı geldiyse → uyuşmazlık.

## Sık hatalar

- İşveren paylarını toplarken KVS'yi (tamamı işveren) unutmak ya da işçi payına eklemek.
- Hazine indirimini PEK üst sınırı yerine tüm brüte uygulamak.
- Teşviki "otomatik" sanmak: bildirgede doğru kanun numarası seçilmezse yararlanılmaz; yanlış seçilen belge düzeltmesi → `sgk-gecikme-ve-bildirge.md`.
- Hazine/Fon karşılığı tutarı gider yazmak (kanunen gider değil).
- Teşvik tutarını bu dosyadan hesaplamaya çalışmak: tutar SGK sisteminde; burada yalnız şart.

## Uyuşmazlığa dönüş

Teşvik iptali, yersiz teşvik geri istemi, borç tahakkuku, idari para cezası ya da hizmet tespiti → başlığı değiştir ve `../../sosyal-guvenlik-sgk/SKILL.md` (`references/sgk-uyum-ve-itiraz.md`). Taşı: dönemler, teşvik kanun numarası, borç dökümü, tebliğ tarihi, bu listedeki bulgular ve önem dereceleri.

## Çıktı

SKILL.md Adım 4. "Hesap" yerine **Şart tablosu**: Şart | Durum (✅/🔴/🟠/🟡/bilinmiyor) | Belge | Dayanak. Oranlar istendiyse ayrı tablo: Kod | Dönem başı | Değer | Kaynak.
