# Stopaj ve muhtasar

## Ne zaman
Serbest meslek makbuzu, kira ödemesi, gider pusulası ya da hakediş ödemesinde gelir vergisi stopajı (GVK m.94), net/brüt çevirme ve muhtasar ve prim hizmet beyannamesi (MUHSGK) soruları. Ücret stopajı ve bordro için `brutten-nete.md`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Ödeme / tahakkuk tarihi | Stopaj oranı CB kararıyla değişir; beyan dönemi | Sor |
| Ödemeyi yapanın sıfatı (kurum, ticaret / serbest meslek erbabı, çiftçi…) | m.94 tevkifat yükümlülüğü yalnız sayılanlarda | Sor |
| Ödemenin niteliği ve alanın durumu (serbest meslek, kiraya veren gerçek kişi, muaf esnaf, yıllara yaygın inşaat…) | Bent seçimi | Sor; bent tahmin etme `[incele]` |
| Tutar ve türü (brüt / net, KDV hariç) | Stopaj matrahı KDV hariç brüttür | Sor |
| KDV durumu ve tevkifat bölümü | Aynı belgede KDV kırılımı | Sor → `kdv-uygulamalari.md` |
| İşçi sayısı ve üç aylık beyan seçimi | m.98 üç aylık beyan imkânı | Sor |

## Aracı çağırma

`legal_calculate_tax`, hesap `fatura_kirilim`, alan `belge` (+ gerekiyorsa `stopaj_bent`):

```json
{ "hesap": "fatura_kirilim",
  "girdi": { "tutar": "<sayı>", "tutar_turu": "net", "belge": "serbest_meslek" },
  "tarih": "<ödeme tarihi>" }
```

| İş | `belge` | `stopaj_bent` |
|---|---|---|
| Serbest meslek makbuzu (m.94/2-b) | `serbest_meslek` | — (araç `2b` kullanır) |
| m.18 kapsamı (yazar, mucit vb., m.94/2-a) | `gider_pusulasi` ya da başka bir değer | `2a` |
| İşyeri kirası (m.94/5-a) | `kira` | — (araç `5a`) |
| Muaf esnaftan mal / hizmet (m.94/13) | `gider_pusulasi` | `13a`, `13b`, `13c`, `13ç`, `13d` |
| Yıllara yaygın inşaat hakedişi (m.94/3) | `gider_pusulasi` | `3a`, `3b`, `3c`, `3d` — tarihe göre bent anlamı değişti `[doğrula]` |
| Çiftçiden ürün / hizmet (m.94/11) | `gider_pusulasi` | `11a-i`, `11a-ii`, `11b-i`, … |

- `tutar_turu: "net"` = stopaj düşülmüş, KDV hariç ("eline geçecek"); araç brüte çevirir. KDV dahil tutar verilirse önce KDV ayrılır.
- KDV tevkifatı da varsa aynı çağrıya `tevkifat` ekle (ör. işgücü, temizlik); sonuç `stopaj` ve `tevkif_edilen_kdv` alanlarını birlikte verir.
- Stopaj oranı için tek başına: `{"hesap":"had","girdi":{"ara":"stopaj"}}` sonuç vermezse `fatura_kirilim` yanıtındaki `ara_degerler.stopaj.oran`.

**Araç sınırları (koddan):**
- Yalnız **tek oranlı** bentler hesaplanır; vadeye göre kademeli bentler (ör. 7b-ba, 7b-bb) ve oranı olmayan satırlar hata döndürür. Menkul sermaye iradı stopajları bu hesabın işi değil; madde ve CB kararından elle `[doğrula]`.
- `belge: "serbest_meslek"` her zaman 2-b'yi seçer; m.18 kapsamındaki ödemede `stopaj_bent: "2a"` ver.
- Yıllara yaygın inşaatta 1.6.2026'dan itibaren bent sonekleri değişti (tabloda `3c` önce "diğer", sonra başka iş); tarihe göre doğru soneki seç ve yanıttaki `konu` alanıyla teyit et.
- Ödeyenin tevkifat yükümlüsü olup olmadığını, alanın sıfatını ve işin niteliğini araç **kontrol etmez** (uyarıda yazar).
- Noter ödemeleri m.94/2'nin dışındadır; araç ayırt etmez.

## Hukuki çerçeve

- **Tevkifat yükümlüleri ve kapsam:** kamu idareleri, kurumlar, ticaret şirketleri, iş ortaklıkları, dernek ve vakıflar ile iktisadi işletmeleri, kooperatifler, gerçek gelirini beyan eden ticaret ve serbest meslek erbabı ve bilanço / zirai işletme hesabı esasındaki çiftçiler, bentlerde sayılan ödemeleri (avans dahil) nakden veya hesaben yaptıkları sırada tevkifat yapar. Tüccar, serbest meslek erbabı ve çiftçilerin tevkifatı ticari, mesleki ve zirai işleriyle ilgili ödemelerine münhasırdır. Oranları Cumhurbaşkanı her ödeme için ayrı belirleyebilir. [Gelir Vergisi Kanunu (gvk) m. 94](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Bentler (özet):** 1 ücret; 2-a m.18 serbest meslek, 2-b diğer serbest meslek; 3 yıllara yaygın inşaat hakedişi (kurumlar dahil); 5-a m.70 mal ve hak kiraları; 11 çiftçiden alınan ürün ve hizmet; 13 esnaf muaflığından yararlananlara ödemeler; 19 aracı hizmet sağlayıcı ödemeleri; 20 CB'nin belirlediği sektörlerde mal ve hizmet alımları. Ayrıca karşı tarafa yükletilen vekâlet ücretini ödeyenler tevkifat yapar. [Gelir Vergisi Kanunu (gvk) m. 94](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Belgeler:** serbest meslek erbabı her tahsilat için iki nüsha makbuz düzenler (VUK m.236); belge düzenleme zorunluluğu olmayanlardan alımda gider pusulası, malın teslimi / hizmetin yapıldığı tarihten itibaren madde metnindeki süre içinde; süresinde düzenlenmeyen gider pusulası hiç düzenlenmemiş sayılır (VUK m.234). [Vergi Usul Kanunu m. 236](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] · [Vergi Usul Kanunu m. 234](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Muhtasar beyan süresi (kanun):** tevkifat yapanlar bir ay içindeki ödemeleri ve tevkif ettikleri vergiyi kanunda yazılı günde bildirir; on ve daha az hizmet erbabı çalıştıranlar (zirai ürün tevkifatı yapanlar hariç) vergi dairesine önceden bildirerek üç aylık dönemler hâlinde verebilir. [Gelir Vergisi Kanunu (gvk) m. 98](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **MUHSGK:** muhtasar beyanname ile aylık prim ve hizmet belgesinin birleştirilmesinde şekil, dönem ve verilme süresi ortak tebliğle belirlenir; eksik gün nedeni MUHSGK ile bildirilir. Güncel verilme ve ödeme günü tebliğden çekilir; GVK m.98'deki günle aynı olduğunu varsayma `[doğrula]`. [Sosyal Sigortalar Ve Genel Sağlık Sigortası Kanunu m. 86](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla] · [MUHTASAR VE PRİM HİZMET BEYANNAMESİ GENEL TEBLİĞİ (SIRA NO: 1) (23345)](https://soorgla.com/mevzuat/23345-muhtasar-ve-prim-hizmet-beyannamesi-genel-tebligi-sira-no-1/#madde-12) [soorgla]

## Kontrol listesi

- 🔴 Ödeyen m.94 ilk fıkradaki yükümlülerden mi; ödeme ticari / mesleki işle ilgili mi? Değilse stopaj yok `[incele]`.
- 🔴 Bent doğru mu (2-a / 2-b; 5-a; 13 alt bentleri; inşaatta tarihe göre sonek)? Yanıttaki `konu` alanını kullanıcıya göster.
- 🟠 Matrah KDV hariç brüt mü; net anlaşmada `tutar_turu: "net"` kullanıldı mı?
- 🟠 Gider pusulası süresinde (VUK m.234) düzenlendi mi?
- 🟠 Aynı belgede KDV tevkifatı da var mı (işgücü, temizlik, danışmanlık vb.)? → `kdv-uygulamalari.md`
- 🟡 Üç aylık muhtasar seçimi için hizmet erbabı sayısı ve vergi dairesine bildirim (m.98).
- 🟡 MUHSGK'da eksik gün nedeni ve belgesi (5510 m.86).
- 🟡 Kira stopajı kiraya veren tarafta beyan sınırını aşıyorsa yıllık beyanda mahsup → `gelir-ve-kurumlar-uygulamalari.md`.

## Sık hatalar

- 🔴 Stopaj oranını bellekten yazmak; CB kararıyla değişir, araçtan çek.
- 🟠 Stopajı KDV dahil tutar üzerinden hesaplamak.
- 🟠 Bireysel (ticari olmayan) kiracının, ya da işle ilgisiz ödemede tevkifat yapılacağını söylemek.
- 🟠 Basit usuldeki esnafla muaf esnafı karıştırmak (13. bent yalnız esnaf muaflığından yararlananlar).
- 🟡 Net anlaşılan makbuzda brütü stopajı yeniden ekleyerek yanlış yuvarlamak; `net` modunu kullan.

## Uyuşmazlığa dönüş

Stopaj yapılmadığı / eksik yapıldığı gerekçesiyle sorumlu sıfatıyla tarhiyat, ihbarname ya da SGK'nın MUHSGK üzerinden re'sen tahakkuku görünürse vergi tarafı `../../vergi/SKILL.md`, SGK tarafı `../../sosyal-guvenlik-sgk/SKILL.md`. Gecikme zammı ve pişmanlık tutarı bu becerinin `beyan-takvimi-ve-odemeler.md` dosyasında hesaplanır.

## Çıktı

SKILL.md Adım 4. Makbuz / gider pusulası tablosu: brüt (KDV hariç) → KDV → KDV tevkifatı → stopaj (bent, oran kaynağı) → net ödenecek; altına MUHSGK'da hangi satıra gireceği ve beyan dönemi.
