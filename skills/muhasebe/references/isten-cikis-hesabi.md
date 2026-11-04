# İşten çıkış (son) bordrosu

Bu dosya **kesinti ve neti** kurar: kıdem tazminatının GV istisnası ve damgası, ihbar tazminatı ve kullanılmayan izin ücretinin GV, damga ve SGK durumu. Kıdem ve ihbar **tutarı** (süre, giydirilmiş ücret, tavan, hak kazanma) burada hesaplanmaz → `legal_calculate_employment_claims` ya da `../../is-hukuku/SKILL.md` (`references/iscilik-alacaklari.md`). Fesih geçerliliği ve hak kazanma tartışması uyuşmazlıktır.

## Ne zaman

- "Çıkış bordrosunu yapalım", "Kıdemden ne kesilir?", "İhbardan SGK kesilir mi?", "Kalan izinler ne kadar net eder?"
- İkale/karşılıklı sonlandırmada ek ödeme (iş kaybı, iş güvencesi tazminatı adı altında).

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Çıkış tarihi ve son bordro ayı | Tarife, asgari ücret, kıdem tavanı dönemi | Sor 🔴 |
| Brüt kıdem, ihbar, izin ücreti tutarları | Bu dosya tutar üretmez | `is-hukuku` / `legal_calculate_employment_claims` aracından ya da kullanıcıdan `[kullanıcı verdi]` |
| Kıdemin dayanağı: 1475 m.14 kanuni mi, sözleşme/ikale ile fazlası mı | Tavanı aşan kısım ücret | Sor 🟠 |
| Son ay ücret ve çalışılan gün | Son bordro | Sor |
| Yıl içi kümülatif GV matrahı | İhbar ve izin dilim atlatır | Bordro programından iste 🟠 |
| Başka işverenden ücret | Asgari ücret istisnası tekliği | Sor |
| Ödeme tarihi (çıkış ayından farklı mı) | Vergi ve SGK hangi aya | Sor |

İşçi adı ve kimlik bilgisi çıktıya yazılmaz.

## Araç çağrıları

1. **Son ay ücreti + izin ücreti** (ikisi de ücret, ikisi de prime tabi; `ucret` aracında aynı brüte eklenebilir — izin ücretinin SGK ayı için aşağıdaki genelgeye bak):
```json
{ "hesap": "ucret", "ucret": { "ay": "2026-09", "brut": 0, "onceki_kumulatif_matrah": 0 }, "tarih": "2026-09-30" }
```
2. **Kıdem tavanı** (o dönem):
```
legal_get_social_parameters   → kıdem tazminatı tavanı, dönemi
```
3. **İhbar ve kıdem damgası** (oranı araçtan; nüsha 1):
```json
{ "hesap": "damga", "damga": { "sira": "IV.1.b", "tutar": 0 }, "tarih": "2026-09-30" }
```
4. **İhbarın GV'si — elle:** `GV_ihbar = tarife(K + İ) − tarife(K)`; K = ihbar öncesi kümülatif matrah (son ay ücreti dahil), İ = brüt ihbar. Tarife dilimleri: `legal_get_statute_article 193 m.103` ya da `{ "hesap": "had", "had": { "ara": "gelir vergisi tarife" } }` `[doğrula]`.

**Yapma:** ihbarı `ucret` aracında son ayın brütüne eklemek. `ucret` aracında `kalem` alanı yok; ihbara SGK primi ve PEK sınırı uygular — yanlış. (Ortak çekirdek `kalem: ihbar/kidem` destekliyor ama bu araç dışarı vermiyor.)

## Hukuki çerçeve

- **Kıdem — GV istisnası:** 1475 ve 854 sayılı Kanunlara göre ödenmesi gereken kıdem tazminatının tamamı (5953'te hizmet erbabının kanundaki aylık sayısını aşmayan kısmı) istisna; hizmet ifa etmeksizin ödenen ücret tazminat sayılmaz. İkale/karşılıklı sonlandırmada iş kaybı, iş sonu, iş güvencesi gibi adlarla yapılan ödemeler (a) bendindeki istisna tutarının hesabında dikkate alınmak şartıyla istisna. [GVK m. 25/7](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Tavanı aşan kısım:** 1475 m.14'e göre hesaplanacak kıdem tazminatına tekabül eden kısım istisna; istisnayı aşan kısım ile ihbar tazminatının tamamı GVK m.61 uyarınca ücret, GV tevkifatına tabi. [GİB Özelge 84098128-120.01.02.07[40-2013-3]-143, 20.03.2015](https://gib.gov.tr/mevzuat/kanun/435/ozelge/34546) [soorgla] Özelge yalnız talep edeni bağlar; emsal olarak kullan.
- **İkale ödemeleri ücret sayılır** (istisnayı aşan kısım): [GVK m. 61/7](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **İşe başlatmama tazminatı:** GV'den istisna. [GVK m. 25/1](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] Damga durumu `[doğrula]`.
- **SGK:** kıdem ve ihbar tazminatı ile iş sonu tazminatı niteliğindeki toplu ödemeler prime esas kazanca **girmez**. [5510 m. 80/1-b-4,5](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Kullanılmayan izin ücreti — SGK:** 4857 m.59'a göre sözleşmenin sona erdiği tarihteki ücretten ödenir; prime esas kazanca dahil edilme ve askıdaki dönemde ödeme kuralı SGK genelgesinde. [SGK Genelge 2020/20](https://kms.kaysis.gov.tr/Home/Goster/163634) [soorgla] Hangi ayın kazancına ekleneceği (son ay / izin süresine yayma) genelge metninden okunmalı `[doğrula]`.
- **Kullanılmayan izin ücreti — GV ve damga:** ücret (GVK m.61); damga kesilir. [GİB Özelge B.07.1.GİB.4.34.16.01-GVK 61-88, 17.05.2010](https://gib.gov.tr/mevzuat/kanun/433/ozelge/23410) [soorgla]
- **Asgari ücret istisnası:** ödemenin yapıldığı aydaki asgari ücrete göre ve ayda bir kez (GVK 23/18). İhbar ve izin ücreti aynı ay ücretle birlikte ödeniyorsa istisna ay toplamına bir kez uygulanır; kıdemde damga istisnası uygulanıp uygulanmayacağı `[doğrula]` (ortak çekirdek kıdemde damga istisnasını uygulamıyor).

## Kontrol listesi

- 🔴 Kıdem tavanı çıkış tarihinin dönemiyle mi alındı (`legal_get_social_parameters`)?
- 🔴 İhbara SGK primi kesilmiş mi? Kesilmişse yanlış (m.80/b-4).
- 🟠 Sözleşmesel/ikale fazlası tavanı aşıyor mu? Aşan kısım GV'li ücret.
- 🟠 İhbar ve izin kümülatif matrahı üst dilime taşıyor mu? Tarife farkıyla hesapla, tek oranla değil.
- 🟠 Ödeme çıkış ayından sonraki ayda mı? GV ve muhtasar dönemi, SGK'da ek APHB/MUHSGK gerekebilir → `sgk-gecikme-ve-bildirge.md`.
- 🟡 İzin ücreti SGK ayı genelgeyle uyumlu mu?
- 🟡 İşten ayrılış bildirgesi süresinde verildi mi (5510 m.102/1-j yaptırımı) `[incele]`.
- [incele] Kıdeme hak kazanma, fesih türü, tutar → `is-hukuku`.

## Sık hatalar

- Kıdemden GV kesmek (tavan içindeki kısımdan kesilmez) ya da tavanı aşan kısmı istisna saymak.
- İhbarı `ucret` aracına son ay brütü olarak vermek (SGK yanlış kesilir).
- İzin ücretinden SGK kesmemek.
- İhbar GV'sini son ayın marjinal oranıyla tek çarpımla bulmak; dilim sınırı aşılıyorsa yanlış.
- Kıdem tutarını bu becerinin hesapladığını söylemek; tutar `is-hukuku` / `legal_calculate_employment_claims` aracındandır.

## Uyuşmazlığa dönüş

İşçi kıdem/ihbar tutarına itiraz ediyor, arabuluculuk başvurusu ya da dava var, fesih türü tartışmalı → kapıyı aç, `../../is-hukuku/SKILL.md`. SGK ayrılış bildirgesi cezası → `../../sosyal-guvenlik-sgk/SKILL.md`.

## Çıktı

SKILL.md Adım 4. Tablo: Kalem | Brüt | SGK işçi | İşsizlik | GV matrahı | GV | Damga | Net | Dayanak. Satırlar: son ay ücreti, izin ücreti, ihbar, kıdem (istisna içi), kıdem (tavan aşan), toplam. Tutar kaynağı satırı: "kıdem/ihbar brütü: [is-hukuku / legal_calculate_employment_claims / kullanıcı verdi]".
