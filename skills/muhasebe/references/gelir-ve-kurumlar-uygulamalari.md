# Gelir ve kurumlar vergisi uygulamaları

## Ne zaman
Kira geliri beyanı, binek otomobil gider ve amortisman sınırı, KKEG ayrımı, yıllık beyan gerekip gerekmediği ve geçici vergi soruları. Kurumlar ve asgari kurumlar vergisi **hesabı** için `kurumlar-ve-asgari-kv.md`; amortisman tablosu için `amortisman.md`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Gelir yılı / hesap dönemi | Tarife, istisna ve sınırlar yıla göre | Sor |
| Mükellef türü (gerçek kişi, ticari / serbest meslek / ücretli, kurum) | İstisna şartı, geçici vergi, m.40 / m.68 ayrımı | Sor |
| Kira: konut ve işyeri yıllık brüt tutarları ayrı ayrı | İstisna yalnız konuta; işyeri stopajlı | Sor |
| Kira: diğer gelirlerin gayrisafi toplamı ve stopajlı diğer gelirler | m.21/2 istisna şartı, m.86/1-c beyan sınırı | Sor; yoksa `[incele]` ve iki senaryo |
| Kira: gider yöntemi, gerçek giderse belgeler | m.74 | Götürü varsay, yaz |
| Binek: iktisap tarihi, ÖTV ve KDV hariç bedel, ÖTV, KDV, maliyete eklendi mi, ikinci el mi | m.40/1-7 sınırları iktisap tarihine göre | Sor |
| Binek: kiralıksa aylık kira; yıllık işletme giderleri | m.40/1, 40/5 | Sor |

## Aracı çağırma

**Kira geliri** (`kira_geliri`):
```json
{ "hesap": "kira_geliri",
  "kira_geliri": { "yil": 2025, "konut": "<yıllık TL>", "isyeri": "<yıllık brüt TL>",
             "gider_yontemi": "goturu", "diger_gayrisafi": "<TL>", "diger_stopajli": "<TL>", "ticari_beyan": false },
  "tarih": "2026-03-01" }
```
Yanıt: `beyan_gerekli`, `matrah`, `hesaplanan_vergi`, `mahsup_edilecek_stopaj`, `odenecek` / `iade_mahsup`; `ara_degerler` içinde istisna tutarı, istisnanın neden uygulanmadığı, m.86/1-c sınırı ve işyerinin beyana girip girmediği.

**Binek otomobil** (`binek_oto`):
```json
{ "hesap": "binek_oto",
  "binek_oto": { "iktisap_tarihi": "2025-05-10", "bedel": "<TL>", "otv": "<TL>", "kdv": "<TL>",
             "yillik_amortisman": "<TL>", "isletme_giderleri": "<TL>", "serbest_meslek": false },
  "tarih": "2026-12-31" }
```
Yanıt kalem kalem `gider_yazilabilir` ve `kkeg`, toplam `toplam_kkeg`.

**Tek bir sınır** (beyan sınırı, istisna tutarı): `{"hesap":"had","had":{"ara":"kira"}}` ya da `{"ara":"binek"}`.

**Araç sınırları (koddan):**
- `kira_geliri` yalnız kira gelirini hesaplar; başka gelirle birlikte beyanda tarife toplam matraha uygulanır, sonuç ayrıca kurulmalı (uyarıda yazar).
- m.86/1-c beyan sınırına araç yalnız `isyeri` + `diger_stopajli` toplamını koyar; maddedeki "vergiye tabi gelir toplamı" kapsamını (konut kirası dahil mi) kendin kontrol et `[incele]`.
- Hakları kiraya verenlerin götürü gider seçemeyeceği ve iki yıl dönememe kuralı **kontrol edilmez**, uyarıda yazar.
- Konut kira zararının mahsup edilip edilemeyeceği (m.74/1-4 ve 7566 değişikliği) hesaplanmaz → `../../vergi/references/kdv-gvk-kvk-temel-sorular.md` `[incele]`.
- `binek_oto`'da işletme giderlerindeki oran **kodda sabittir** ve yalnız işletme giderlerine uygulanır; sınır içi amortisman ve kiraya da uygulanıp uygulanmadığını araç uyarısı GVGT 312 ile doğrulamanı ister `[doğrula]`.
- `binek_oto` ÖTV+KDV ve amortisman sınırını **iktisap tarihinden**, aylık kira sınırını **`tarih`'ten** okur.
- Serbest meslekte (`serbest_meslek: true`) m.68 kodları kullanılır; m.68 metnini çalışma anında çek `[doğrula]`.

## Hukuki çerçeve

- **Mesken kira istisnası:** konut kirası hasılatının kanunda yazılı (yeniden değerlenen) kısmı istisnadır; istisna haddi üzerinde hasılat beyan edilmez ya da eksik beyan edilirse istisnadan yararlanılamaz. Ticari, zirai veya mesleki kazancını yıllık beyanla bildirenler ile gayrisafi gelirler toplamı tarifenin üçüncü diliminde ücretler için yazılı tutarı aşanlar yararlanamaz. [Gelir Vergisi Kanunu (gvk) m. 21](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Kira giderleri:** istisna edilen hasılata isabet edenler hariç m.74'te sayılan giderler indirilir; hakları kiraya verenler hariç mükellefler bunlar yerine hasılatın kanunda yazılı oranını götürü indirebilir; götürü usulü seçen iki yıl geçmedikçe dönemez; para ve vergi cezaları gider yazılmaz. [Gelir Vergisi Kanunu (gvk) m. 74](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Beyan edilmeyen gelirler:** istisna hadleri içinde kalanlar (m.86/1-a); tek işverenden, tevkif edilmiş ve dördüncü dilimi aşmayan ücret (b); toplamı ikinci dilimi aşmayan tevkifata tabi ücret, menkul ve gayrimenkul sermaye iratları (c); tevkifata ve istisnaya konu olmayan, kanundaki tutarı aşmayan menkul ve gayrimenkul sermaye iratları (d). [Gelir Vergisi Kanunu (gvk) m. 86](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Binek otomobil:** kiralık binekte aylık kiranın ve iktisaba ilişkin ÖTV+KDV toplamının kanunda yazılı tutara kadarlık kısmı gider (m.40/1); binek giderlerinin kanunda yazılı oranı indirilebilir (m.40/5); amortismanda ÖTV ve KDV hariç ilk iktisap bedeli ya da vergilerin maliyete eklendiği / ikinci el hâlde amortismana tabi tutar sınırına isabet eden kısım gider, **iktisap tarihindeki tutar** esas (m.40/7). Faaliyeti binek kiralama ya da işletme olanların bu amaçla kullandıkları hariç. [Gelir Vergisi Kanunu (gvk) m. 40](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Binek KDV'si indirilemez** (kiralama / işletme faaliyeti hariç). [Katma Değer Vergisi Kanunu m. 30](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **KKEG — gerçek kişi:** teşebbüs sahibinin çekişleri, kendisine ve ailesine ödenen ücret ve faizler, ilişkili kişilerle emsale aykırı farklar, para ve vergi cezaları, belirli reklam giderleri, işle ilgisiz deniz/hava taşıtları, finansman gider kısıtlaması. [Gelir Vergisi Kanunu (gvk) m. 41](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **KKEG — kurum:** öz ve örtülü sermaye faizi, TF ile örtülü kazanç, yedek akçeler, kurumlar vergisi, para ve vergi cezaları, gecikme zammı ve faizleri, suç tazminatları, belirli reklam giderleri, finansman gider kısıtlaması. [Kurumlar Vergisi Kanunu m. 11](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]
- **Geçici vergi (gerçek kişi):** ticari kazanç sahipleri ve serbest meslek erbabı üçer aylık dönem kazancı üzerinden, tarifenin ilk dilim oranında; beyan dönemi izleyen ikinci ayın on dördüncü, ödeme on yedinci günü akşamı; dönem içinde tevkif edilen vergi mahsup edilir; incelemede kanunda yazılı oranı aşan eksik beyan hâlinde tarhiyat; yıllık vergiden mahsup edilemeyen tutar yıl sonuna kadar yazılı talep hâlinde iade. [Gelir Vergisi Kanunu (gvk) m. mükerrer 120](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Geçici vergi (kurum):** cari dönemin kurumlar vergisi oranında, GVK esaslarına göre; Cumhurbaşkanı oranı belirli puan indirebilir. [Kurumlar Vergisi Kanunu m. 32](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]

## Kontrol listesi

- 🔴 Konut kirası istisna haddini aşıyor ve beyan edilmemiş / eksik beyan edilmişse istisna tümden kaybedilir (m.21/1).
- 🟠 m.21/2 istisna yasağı: ticari/mesleki beyan ya da gayrisafi toplam sınırı aşıldı mı? Araç `istisna_yok_nedeni` alanını oku.
- 🟠 İşyeri kirası m.86/1-c sınırını aştı mı; aştıysa stopaj mahsubu (`mahsup_edilecek_stopaj`) yapıldı mı?
- 🟠 Götürü gider seçimi önceki yıl yapılmış mı (iki yıl kuralı); hakları kiraya veren mi?
- 🟠 Binek: iktisap tarihi doğru mu; ÖTV/KDV maliyete eklendi mi; serbest meslek mi (m.68)?
- 🟡 KKEG kalemleri (ceza, gecikme zammı, binek fazlası) beyannamede kanunen kabul edilmeyen gider satırına eklendi mi?
- 🟡 Geçici vergide dönem içi tevkifat mahsubu yapıldı mı?
- [incele] Diğer gelirlerle birlikte beyan: toplam matraha tarife uygulanarak yeniden hesap.

## Sık hatalar

- 🔴 İstisna tutarını ya da beyan sınırını bellekten yazmak; araçtan (`had`) çek.
- 🟠 Binek amortisman sınırını bugünün tutarıyla uygulamak (iktisap tarihindeki tutar esas).
- 🟠 Binek KDV'sini indirmek (m.30/b).
- 🟠 İşyeri kirasının stopajını beyan sınırını aşmasına rağmen nihai vergi saymak.
- 🟡 Kira gelirinde gerçek gideri istisnaya isabet eden kısımla birlikte indirmek (m.74 ilk fıkra).

## Uyuşmazlığa dönüş

Kira geliri için izaha davet ya da ihbarname, binek / KKEG nedeniyle inceleme, istisnanın kaybı iddiasıyla tarhiyat görünürse `../../vergi/SKILL.md`'ye devret; hesaplanan tutar ve araç uyarılarını taşı.

## Çıktı

SKILL.md Adım 4. Kira geliri: hasılat → istisna → gider → matrah → vergi → stopaj mahsubu → ödenecek/iade. Binek: kalem bazında gider / KKEG tablosu ve toplam KKEG; yevmiye önerisinde KKEG'in nazım hesap ya da beyanname satırı olduğunu belirt.
