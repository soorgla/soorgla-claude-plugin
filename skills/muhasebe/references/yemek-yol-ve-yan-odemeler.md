# Yemek, yol ve yan ödemeler

Gelir vergisi ve SGK aynı ödemeyi farklı ele alır: bir kalem GV'den istisna olup prime tabi olabilir ya da tersi. Her kalem için **iki sütun** (GV / SGK) ayrı karar verilir. İstisna tutarları `legal_calculate_tax` `hesap: "had"` ile çekilir; bu dosyaya tutar yazılmaz.

## Ne zaman

- Yemek kartı, işyerinde yemek, yemek parası nakit ödeniyor.
- Servis, toplu taşıma kartı, nakit yol parası.
- İkramiye, prim, performans, bayram/evlenme/doğum yardımı, kreş, aynî yardım (gıda kolisi, yakacak).
- `ucret` aracı bu istisnaları **hesaba katmaz** (uyarıda yazar): istisna dışı kısım brüte eklenip `brutten-nete.md` ile yeniden hesaplanır.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Ödeme ayı ve tarih | İstisna tutarı yıllık güncellenir | Sor |
| Ödeme biçimi: işyerinde yemek / kart-çek / nakit | 23/8 ve 23/10 biçime bağlı | Sor 🔴 |
| Fiilen çalışılan gün sayısı | İstisna "çalışılan günlere ait" | Sor; izin, rapor, hafta tatili düşülür |
| Kart/çek tutarı (günlük ve aylık) | İstisnayı aşan kısım ücret | Sor |
| Taşıma: işveren servisi mi, toplu taşıma kartı/bileti mi, nakit mi | 23/10 şartı | Sor |
| İkramiye/prim: hangi ayda ödendi, hangi döneme ait | SGK ödendiği ay, PEK aşımı devri | Sor |
| Aynî mi nakdî mi | SGK m.80/b-1 ve 80/c | Sor |

## Araç çağrıları

```json
{ "hesap": "had", "had": { "ara": "yemek" }, "tarih": "2026-05-31" }
```
```json
{ "hesap": "had", "had": { "kod": "gvk_23_10_ulasim_gunluk" }, "tarih": "2026-05-31" }
```
SGK tarafındaki yemek istisnası kodunu `ara: "yemek"` sonucundan seç; yoksa tutarı 5510 m.80 metninden ve SGK duyurusundan al `[doğrula]`. İstisna dışı kalan tutarı brüte ekleyip:
```json
{ "hesap": "ucret", "ucret": { "ay": "2026-05", "brut": 0, "onceki_kumulatif_matrah": 0 }, "tarih": "2026-05-31" }
```
Not: GV matrahına giren tutar ile prime esas kazanca giren tutar farklıysa `ucret` aracı ikisini ayırmaz (tek `brut` alır). İki ayrı çağrı yapma; farkı elle düzelt ve tabloda göster `[doğrula]`.

## Hukuki çerçeve

- **Yemek (GV):** işverenin yemek vermesiyle sağlanan menfaat istisna; işyerinde/müştemilatında yemek verilmiyorsa çalışılan günlere ait günlük yemek bedelinin kanundaki tutarı aşmayan kısmı istisna; aşan kısım ve bu amaçla sağlanan diğer menfaatler ücret. [GVK m. 23/8](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] Nakit yemek parasının istisnadan yararlanıp yararlanmadığı tebliğ/özelge sorusudur `[doğrula]`.
- **Yol (GV):** toplu taşıma için işverenin yaptığı taşıma giderleri istisna; taşıma verilmiyorsa günlük ulaşım bedelinin kanundaki tutarı aşmaması **ve** ödemenin toplu taşıma kartı, bileti ya da bu amaçla kullanılan ödeme aracıyla yapılması şart; aşan kısım ile **nakden** yapılan ulaşım ödemeleri ücret. [GVK m. 23/10](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Kreş (GV):** kadın çalışana kreş/gündüz bakımevi hizmeti ya da doğrudan hizmet sağlayana ödeme şartıyla istisna; nakit ödeme ücret. [GVK m. 23/16](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Evlenme ve doğum yardımı (GV):** kanunda belirtilen aylık tutarına kadar istisna. [GVK m. 25/5](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Aynî ödemeler (GV):** ayınlar da ücrettir; verildiği gün ve yerdeki ortalama perakende fiyatla değerlenir. [GVK m. 61](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/), [GVK m. 63](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **SGK — prime esas kazanç:** hak edilen ücret, o ay ödenen prim-ikramiye ve benzeri istihkak, işverenin ödediği özel sağlık sigortası ve BES katkısı brüt toplamı. [5510 m. 80/1-a](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **SGK — prime tabi olmayanlar:** aynî yardımlar; ölüm, doğum, evlenme yardımları; görev yollukları; seyyar görev, kıdem, ihbar ve kasa tazminatı; iş sonu tazminatı niteliğindeki toplu ödemeler; keşif ücreti; Kurumca belirlenen çocuk ve aile zamları; kanundaki sınırı aşmayan işveren ÖSS/BES katkısı; işyerinde yemek verilmeyen durumda çalışılan günlere ait günlük yemek bedelinin kanundaki tutara kadar olan kısmı (tutar yeniden değerleme oranıyla güncellenir). [5510 m. 80/1-b](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]  Bent 2/4/2026'da değişti; bu tarihten önceki aylarda eski metin uygulanır `[doğrula]` (`legal_get_statute_article_history`).
- **SGK — her şey prime tabi, nakit aynî yerine geçen dahil:** (b) dışında her ne adla yapılırsa yapılsın tüm ödemeler ile aynî yardım yerine geçen **nakdî** ödemeler prime tabi; diğer kanunlardaki muafiyetler SGK'da dikkate alınmaz. [5510 m. 80/1-c](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla] Sonuç: GVK 23/10 yol istisnası 5510 m.80/b listesinde **yok**; yol ödemesinin SGK durumu `[incele]`.
- **SGK — ikramiyenin ayı:** ücret hak edildiği aya; ücret dışı ödemeler ödendiği aya mal edilir; PEK üst sınırı aşılırsa aşan kısım sonraki en çok iki ayın kazancına eklenir. [5510 m. 80/1-d](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]

## Kontrol listesi

- 🔴 Ödeme nakit mi? Nakit yol parası GV'de ücret; aynî yerine nakit ödeme SGK'da prime tabi.
- 🟠 Yemek istisnası çalışılan gün sayısıyla mı sınırlandı (izin, rapor, hafta tatili)?
- 🟠 Kart yüklemesi istisna tutarını aşıyor mu? Aşan kısım hem GV hem (yemek için) SGK'da ücret.
- 🟠 İkramiye PEK üst sınırını aşıyor mu? Aşan kısım iki aya devreder; devri izleyen bordrolarda göster.
- 🟡 Ödeme tarihi 7577 değişikliğinden önce mi sonra mı (5510 m.80/b)?
- 🟡 ÖSS/BES işveren katkısı sınırı aşıyor mu?
- 🟡 Gıda kolisi/yakacak gibi aynî yardım: GV'de ücret (perakende fiyatla), SGK'da istisna.
- [incele] Yemek bedelinin nakit ödenmesinin istisna kapsamı; yol ödemesinin SGK durumu.

## Sık hatalar

- GV istisnasını SGK istisnası sanmak (ve tersi). Her kalemde iki sütun.
- Yemek istisnasını 30 güne uygulamak; çalışılmayan günler istisna dışı.
- İkramiyeyi ait olduğu döneme dağıtmak: SGK'da ödendiği ay esastır.
- Aynî yardımı GV'den de muaf sanmak.
- `ucret` çıktısını istisna dahil sanmak: araç istisnayı hesaba katmaz, uyarısını taşı.

## Uyuşmazlığa dönüş

SGK denetiminde yemek/yol/ikramiyenin prime eklenmesi ya da GİB incelemesinde ücret sayılması → başlığı değiştir; SGK → `../../sosyal-guvenlik-sgk/SKILL.md`, vergi → `../../vergi/SKILL.md`. Özelge emsali → `ozelge-emsali-ve-celiski.md`.

## Çıktı

SKILL.md Adım 4. Hesap tablosu: Kalem | Tutar | Gün | GV istisnası | GV'ye giren | SGK istisnası | Prime giren | Dayanak. Altında yeniden hesaplanmış `ucret` sonucu ve uyarılar.
