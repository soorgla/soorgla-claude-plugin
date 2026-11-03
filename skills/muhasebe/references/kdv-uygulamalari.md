# KDV uygulamaları

## Ne zaman
Fatura ya da makbuz KDV'si (dahil/hariç), oran seçimi, kısmi veya tam tevkifat, indirim hakkı ve süresi, istisna ve iade ön kontrolü soruları. İnceleme, sahte belge iddiası ya da ihbarname varsa bu dosya değil, `../../vergi/SKILL.md`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| İşlem tarihi (fatura / vergiyi doğuran olay) | Oran, tevkifat payı, VUK 232 sınırı o güne göre gelir | Sor; "kaba hesap" isteniyorsa bugünü yaz ve sonucun başına koy |
| Tutar ve türü (KDV hariç / dahil) | Matrah | Sor; belirsizse iki satır hesapla |
| Mal / hizmetin cinsi | Oran ve tevkifat bölümü | Sor; bölümü tahmin etme `[incele]` |
| Alıcının sıfatı (KDV mükellefi mi; tebliğde sayılan alıcılardan mı) | Kısmi tevkifatın uygulanıp uygulanmayacağı | Sor; araç bunu kontrol etmez |
| Satıcının durumu (yurt dışı mukim mi, mükellef mi) | Tam tevkifat / sorumlu sıfatıyla beyan | Sor |
| Belgenin deftere kayıt dönemi | İndirim süresi (m.29/3) | Sor |

## Aracı çağırma

`legal_calculate_tax`, hesap `fatura_kirilim`:

```json
{ "hesap": "fatura_kirilim",
  "girdi": { "tutar": "<tutar>", "tutar_turu": "kdv_haric", "kdv_orani": "<ondalık oran; had sonucundan>", "tevkifat": "2.1.3.2.10" },
  "tarih": "<işlem tarihi YYYY-AA-GG>" }
```
(Sayısal alanlara sayı ver; oranı ondalık yaz, ör. yüzde değil `0,xx` biçiminde. Oranı kullanıcıdan ya da `had` hesabından al.)

- `tutar_turu`: `kdv_haric` (varsayılan), `kdv_dahil`; `net` yalnız stopajlı belgede.
- `kdv_orani` verilmezse araç **tarihteki genel oranı** kullanır. İndirimli orana tabi işlemde mutlaka ver; oranı `had` hesabıyla ya da CB kararından çek.
- `tevkifat`: KDV GUT bölüm numarası (`2.1.3.2.1` … `2.1.3.2.15`, `2.1.3.3.1` … `2.1.3.3.8`; yük ve servis taşımacılığında `2.1.3.2.11.yuk` / `2.1.3.2.11.servis`). Hangi bölümün var olduğunu bilmiyorsan yanlış bir bölümle çağır; araç örnek listeyle hata döndürür.
- Yanıt: `kdv_haric`, `kdv`, `kdv_dahil`, `tevkif_edilen_kdv`, `saticiya_odenecek_kdv`, `net_odenecek`; `ara_degerler.tevkifat` içinde oran (pay/10), sınır ve `sinir_altinda`.
- Oran sorusu tek başınaysa: `{"hesap":"had","girdi":{"ara":"kdv"},"tarih":"…"}`.

**Araç sınırları (koddan):**
- Tevkifat yalnız **KDV dahil bedel VUK 232 fatura sınırını aşarsa** uygulanır; altında kalırsa tevkif sıfır döner ve uyarı yazar. 1.1–29.2.2024 arasında sınır sabit tutardı; araç orada da VUK 232 tutarını kullanır ve uyarır.
- Yapım işlerinde (`2.1.3.2.1`) alıcı grubunu `girdi.alici` ile ver: `"a"` (2.1.3.1/a alıcılar) için araç KDV dahil bedeli tebliğdeki ayrı eşikle (`kdv_tevkifat_yapim_esik`) karşılaştırır, `"b"` (2.1.3.1/b) için her tutarda tevkifat yapar. Verilmezse eşik uygulanmaz ve uyarı döner. Bedel sonradan eşiği aşarsa aşıldığı tarihten itibaren tevkifat yapılır; araç bunu izlemez.
- Tevkifat tablosu 1.1.2024'ten itibaren yüklü; daha eski tarih için bölüm bulunamaz ve hata döner. Öncesi elle, tebliğin o tarihteki metninden `[doğrula]`.
- **Tam tevkifat** hesaplanmaz; sorumlu sıfatıyla beyan edilecek KDV = matrah × oran, elle kur.
- Alıcının tevkifat yapmakla yükümlü olup olmadığını araç **kontrol etmez** (uyarıda yazar).

## Hukuki çerçeve

- **Oran:** kanuni oran m.28'de; Cumhurbaşkanı artırma, indirme ve mal/hizmet bazında farklı oran belirleme yetkisine sahip. Uygulanan oran CB kararındadır; metne yazma, `had` ile çek. [Katma Değer Vergisi Kanunu m. 28](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **Tevkifatın dayanağı:** Bakanlık, vergi alacağının emniyeti için işleme taraf olanları verginin ödenmesinden sorumlu tutabilir. [Katma Değer Vergisi Kanunu m. 9](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **Tevkifat zorunludur ve sınırlıdır:** kapsama alınan işlemde alıcı tevkifat yapmak zorunda; kapsama alınmayan işlemde tevkifat yapılamaz. Kısmi tevkifat yalnız I/C-2.1.3.2 (hizmetler) ve I/C-2.1.3.3 (teslimler) bölümlerinde sayılanlarla sınırlıdır; tevkifat yapacak alıcılar I/C-2.1.3.1/a ve b'de ayrılır. [KATMA DEĞER VERGİSİ GENEL UYGULAMA TEBLİĞİ (19631)](https://soorgla.com/mevzuat/19631-katma-deger-vergisi-genel-uygulama-tebligi/) [soorgla]
- **Uygulama sınırı:** I/C-2.1.3.4.1; KDV dahil bedel sınırı aşmıyorsa tevkifat uygulanmaz. Fiyat/kur farkında asıl işlem sınırı aşmışsa fark faturasına sınıra bakılmaksızın tevkifat. [KATMA DEĞER VERGİSİ GENEL UYGULAMA TEBLİĞİ (19631)](https://soorgla.com/mevzuat/19631-katma-deger-vergisi-genel-uygulama-tebligi/) [soorgla]
- **Beyan:** tevkif edilen KDV alıcı tarafından 2 No.lu KDV Beyannamesiyle, satıcı tarafından 1 No.lu beyannamenin ilgili tablosunda bildirilir; satıcı tevkifatlı satış listesini 1 No.lu beyanname ekinde verir. [KATMA DEĞER VERGİSİ GENEL UYGULAMA TEBLİĞİ (19631)](https://soorgla.com/mevzuat/19631-katma-deger-vergisi-genel-uygulama-tebligi/) [soorgla]
- **Tam tevkifat:** yurt dışı mukimden alınan hizmette KDV'yi Türkiye'deki alıcı sorumlu sıfatıyla 2 No.lu beyannameyle beyan eder (KDV mükellefi olmayan alıcı dahil); KDV'ye tabi kiralamada kiraya veren başka faaliyetle KDV mükellefiyse tam tevkifat olmaz. Bölüm numarası I/C-2.1.2 `[doğrula]`. [KATMA DEĞER VERGİSİ GENEL UYGULAMA TEBLİĞİ (19631)](https://soorgla.com/mevzuat/19631-katma-deger-vergisi-genel-uygulama-tebligi/) [soorgla]
- **İndirim hakkı:** fatura ve benzeri vesikada gösterilen, ithalde ödenen ve sorumlu sıfatıyla beyan edilip ödenen KDV indirilir (m.29/1-a, b, ç). İndirim, vergiyi doğuran olayın takvim yılını izleyen takvim yılı aşılmamak şartıyla, belgenin kanuni defterlere kaydedildiği dönemde kullanılır (m.29/3). Değersiz alacağın KDV'si zarar yazıldığı dönemde (m.29/4). [Katma Değer Vergisi Kanunu m. 29](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **İndirilemeyen KDV:** istisna/vergi dışı işlemlere ait (17/2-b,c,d ve 17/4-ı,ö hariç), binek otomobil alış KDV'si (kiralama/işletme faaliyeti hariç), zayi mallar, KKEG'e ait KDV, değersiz alacakta alıcının ödemediği KDV. [Katma Değer Vergisi Kanunu m. 30](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **İndirimli oran devri:** fark sonraki döneme devreder, iade edilmez; indirimli orana tabi işlemlerde CB'nin belirlediği sınırı aşan kısım mahsuben, şartla nakden iade. Sınırı yazma. [Katma Değer Vergisi Kanunu m. 29](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **İstisna ve iade:** ihracat ve ilgili hizmetler m.11'de; m.11, 13, 14, 15 ve 17/4-s istisnalarına ait yüklenilen KDV indirilir, indirilemeyen kısım işlemin gerçekleştiği dönemi izleyen ikinci takvim yılı sonuna kadar talep şartıyla iade edilir. [Katma Değer Vergisi Kanunu m. 11](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla] · [Katma Değer Vergisi Kanunu m. 32](https://soorgla.com/mevzuat/3065-katma-deger-vergisi-kanunu/) [soorgla]
- **İade belge seti:** her istisna türü için tebliğin kendi "İade" alt bölümünde (standart iade talep dilekçesi, indirilecek KDV listesi, yüklenilen KDV listesi, iadesi talep edilen KDV hesaplama tablosu, satış faturaları listesi + türe özgü belgeler). Türün bölümünü çalışma anında çek. [KATMA DEĞER VERGİSİ GENEL UYGULAMA TEBLİĞİ (19631)](https://soorgla.com/mevzuat/19631-katma-deger-vergisi-genel-uygulama-tebligi/) [soorgla]

## Kontrol listesi

- 🔴 İndirim, m.29/3 süresi içinde mi (vergiyi doğuran olay yılı + izleyen yıl, deftere kayıt dönemi)?
- 🔴 Tevkifat bölümü işin niteliğine uyuyor mu; alıcı I/C-2.1.3.1/a-b'de sayılanlardan mı? `[incele]`
- 🟠 KDV dahil bedel VUK 232 sınırını aşıyor mu (araç `sinir_altinda`)? Yapım işinde alıcı grubu (`alici`) verildi mi?
- 🟠 Oran: genel mi, indirimli mi? `kdv_orani` açıkça verildi mi?
- 🟠 Binek otomobil, istisna işlemi ya da KKEG kalemine ait KDV indirime alınmış mı (m.30)?
- 🟡 Yurt dışından hizmet: 2 No.lu beyanname ile sorumlu sıfatıyla beyan yapıldı mı, indirim m.29/1-ç ile mi alındı?
- 🟡 İade: talep süresi (m.32) ve türün belge seti; teminat / YMM raporu / inceleme yolu `[doğrula]`.
- [incele] Bir işlemin hangi tevkifat bölümüne girdiği tartışmalıysa özelge emsali → `ozelge-emsali-ve-celiski.md`.

## Sık hatalar

- 🔴 Tevkifat payını ya da KDV oranını bellekten yazmak; her zaman araçtan ya da tebliğden.
- 🔴 Kapsamda olmayan işlemde "ihtiyaten" tevkifat yapmak (tebliğe göre yapılamaz).
- 🟠 Sınır kontrolünü KDV hariç bedelle yapmak (sınır KDV dahil bedele bakar).
- 🟠 `kdv_orani` vermeden indirimli orana tabi işlemi hesaplamak (araç genel oranı kullanır).
- 🟡 Satıcının tevkifatlı satış listesini 1 No.lu beyanname ekine koymayı unutmak.

## Uyuşmazlığa dönüş

İzaha davet, vergi inceleme raporu, ihbarname, KDV iadesinde olumsuz rapor, sahte / muhteviyatı yanıltıcı belge iddiası, belgesiz mal tespiti (m.9/2) görünürse başlığı değiştir ve `../../vergi/SKILL.md`'ye devret; hesapladığın tutarları, dönemleri ve araç uyarılarını taşı (SKILL.md Adım 5).

## Çıktı

SKILL.md Adım 4 iskeleti. Tek soruluk "KDV dahil X'in KDV'si" iki satır; tevkifatlı faturada hesap tablosu: matrah → KDV → tevkif (bölüm, pay/10, sınır) → satıcıya ödenecek KDV → net. Dayanak satırına KDV GUT bölüm numarasını ve `parametre` dönemini yaz.
