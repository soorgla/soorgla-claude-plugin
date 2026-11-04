# Brütten nete, netten brüte ve işveren maliyeti

Araç: `legal_calculate_tax`, `hesap: "ucret"` (eş adlar `bordro`, `maas`, `maaş`, `ücret`). Oran, tarife, asgari ücret ve PEK sınırları araçtan dönemine göre gelir; bu dosyaya sayı yazılmaz.

## Ne zaman

- "Brüt X ise net ne olur?", "Net Y vermek istiyorum, brüt ne yazayım?", "İşçinin bize maliyeti ne?"
- Yıl içinde dilim atlaması (Ekim-Aralık neti düşüyor), ay ay değişen ücret, yıl ortasında işe giriş.
- Asgari ücret istisnasının ve Hazine indiriminin (imalat dahil) maliyete etkisi.
- Çıkış bordrosu → `isten-cikis-hesabi.md`; yemek/yol/ikramiye → `yemek-yol-ve-yan-odemeler.md`; prim oranı ve teşvik şartı → `sgk-prim-ve-tesvikler.md`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Bordro ayı (YYYY-AA) ya da yıl | Tarife, asgari ücret, PEK sınırı ve prim oranı dönemden gelir | Sor; araç `ay` yoksa `tarih`in ayını kullanır ve uyarır |
| Brüt ya da hedef net | Hesabın yönü (`mod`) | Sor |
| Yıl içi önceki GV matrahı (bu işverende) | Kümülatif dilim | 0 varsayılır; yıl ortası girişte mutlaka sor 🟠 |
| Ay ay ücret farklı mı | `aylar` dizisi | Tek tutar 12 aya yayılır |
| Başka işverenden ücret var mı | Asgari ücret istisnası yalnız en yüksek ücrete | Sor; varsa `[incele]` |
| İşveren Hazine indirimi şartlarını sağlıyor mu, imalat mı | İşveren maliyeti | Varsayılan: indirimsiz; şart listesi `sgk-prim-ve-tesvikler.md` |
| Prim gün sayısı (eksik gün, ay içi giriş/çıkış, kısmi süreli) | PEK alt/üst sınırı ve asgari ücret istisnası gün oranında | 30 varsayılır; giriş/çıkış ayında mutlaka sor 🟠 → `prim_gun` |
| İstisna ödemeler (yemek, yol, kreş, aile yardımı…) | SGK ve gelir vergisi matrahı ayrı düşer | Sor; tutarları `sgk_istisna` ve `gelir_vergisi_istisna` olarak ayrı ver (sınırları `yemek-yol-ve-yan-odemeler.md`) |
| Engellilik, BES, özel sigorta, sendika aidatı | Araç hesaplamaz | Sor; varsa elle düzelt ve `[doğrula]` |

İşçinin adı ve kimlik bilgisi çıktıya yazılmaz; "[Çalışan]" kullan.

## Araç çağrıları

```json
{ "hesap": "ucret", "ucret": { "mod": "brutten_nete", "ay": "2026-03", "brut": 0 }, "tarih": "2026-03-31" }
```
```json
{ "hesap": "ucret", "ucret": { "mod": "brutten_nete", "yil": 2026, "brut": 0, "hazine_indirimi": true, "imalat": false }, "tarih": "2026-12-31" }
```
```json
{ "hesap": "ucret", "ucret": { "aylar": [{"ay": "2026-07", "brut": 0}, {"ay": "2026-08", "brut": 0}], "onceki_kumulatif_matrah": 0 }, "tarih": "2026-08-31" }
```
```json
{ "hesap": "ucret", "ucret": { "ay": "2026-03", "brut": 0, "prim_gun": 0, "sgk_istisna": 0, "gelir_vergisi_istisna": 0 }, "tarih": "2026-03-31" }
```
```json
{ "hesap": "ucret", "ucret": { "mod": "netten_brute", "ay": "2026-03", "net": 0, "onceki_kumulatif_matrah": 0 }, "tarih": "2026-03-31" }
```
```json
{ "hesap": "ucret", "ucret": { "mod": "netten_brute", "yil": 2026, "net": 0 }, "tarih": "2026-12-31" }
```
(`0` yer tutucudur; kullanıcının tutarını yaz.) `prim_gun`, `sgk_istisna`, `gelir_vergisi_istisna` üst düzeyde verilirse her aya, `aylar[]` içinde verilirse o aya uygulanır. Netten brüte `yil` ya da `aylar` (her ay `net` ile) ile ay ay çözülür; kümülatif matrah sıradaki aya taşınır. İkinci işverende ya da istisnanın başka işverende kullanıldığı durumda `"asgari_ucret_istisnasi": false`. Parametreyi tek başına göstermek için: `{ "hesap": "had", "had": { "ara": "sgk" } }`.

Yanıtta `ara_degerler.aylar[]` her ay için `prim_gun`, `sgk_istisna`, `gelir_vergisi_istisna`, `pek_alt_siniri`, `pek_ust_siniri`, `prime_esas_kazanc`, `sgk_isci`, `issizlik_isci`, (alt sınırın altındaysa) `alt_sinir_farki_isci_payi`, `gelir_vergisi_matrahi`, `kumulatif_matrah`, `hesaplanan_gelir_vergisi`, `asgari_ucret_vergi_istisnasi`, `odenecek_gelir_vergisi`, `damga`, `agi`, `net`, işveren tarafında `sgk_isveren`, `hazine_indirimi_puan`, `issizlik_isveren`, `isveren_maliyeti` döndürür; hepsini hesap tablosuna taşı.

## Hukuki çerçeve

- **Ücretin tanımı:** hizmet karşılığı para, ayın ve para ile temsil edilebilen menfaat; prim, ikramiye, tazminat adı altında ödenmesi niteliğini değiştirmez. [Gelir Vergisi Kanunu (gvk) m. 61](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Gerçek ücret:** sigorta primi işçi payı ve sendika aidatı gibi indirimler düşülür; GV gibi şahsi vergiler düşülmez. [GVK m. 63](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] İşsizlik primi işçi payı da matrahtan indirilir. [4447 m. 49](https://soorgla.com/mevzuat/4447-issizlik-sigortasi-kanunu-sosyal-sigortalar-kanunu-tarim-iscileri-sosyal-sigortalar-kanunu-turkiye-cumhuriyeti-emekli/) [soorgla]
- **Tarife:** artan oranlı; ücret gelirlerinde üçüncü dilimin üst sınırı ayrı. Dilim tutarları her yıl güncellenir, araçtan çek. [GVK m. 103](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla] Yıl içi kümülatif matrah uygulaması m.104'tedir; madde metninden doğrula `[doğrula]`.
- **Asgari ücret GV istisnası (2022+):** ödeme ayında geçerli asgari ücretin brütünden işçi SGK ve işsizlik payı düşülmüş tutara isabet eden ücret istisna; dilimler istisna tutarı da dikkate alınarak bulunur, istisnaya isabet eden vergi düşülür; alınmayan vergi o ay asgari ücretin vergisini aşamaz; **birden fazla işverende yalnız en yüksek ücrete** uygulanır. [GVK m. 23/18](https://soorgla.com/mevzuat/193-gelir-vergisi-kanunu-gvk/) [soorgla]
- **Damga istisnası:** asgari ücreti aşmayan kısmı damga vergisinden istisna, aşan kısım üzerinden damga kesilir; dayanak DVK (2) sayılı tablo IV/34. [Damga Vergisi Kanunu m. 9](https://soorgla.com/mevzuat/488-damga-vergisi-kanunu/#madde-9) [soorgla] Tablo fıkrasının güncel metni `[doğrula]`.
- **Prim oranları ve paylar:** MYÖ, KVS ve GSS işçi/işveren payları. [5510 m. 81](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **PEK alt ve üst sınırı:** alt sınırın altındaki kazanç alt sınırdan, üst sınırı aşan üst sınırdan primlendirilir; alt sınır farkının primi işverene aittir. [5510 m. 82](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Hazine indirimi ve imalat:** 5510 m.81/1-ı; imalatta geç.108 ile artırılmış puan, yürürlük süresi madde metninde. [5510 geç. m. 108](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla] Şartlar: `sgk-prim-ve-tesvikler.md`.
- **AGİ (2008-2021):** araç dönemine göre ekler; mülga GVK m.32 dayanağı `[doğrula]`.

## Kontrol listesi

- 🔴 Bordro ayı belirsiz → tarife ve asgari ücret yanlış dönemden gelir. Ay olmadan sonuç verme.
- 🟠 Yıl ortası işe giriş ya da önceki işveren: `onceki_kumulatif_matrah` aynı işverenin yıl içi matrahıdır. Önceki işverendeki matrahın devri ve beyan yükümlülüğü ayrı soru `[incele]`.
- 🟠 Birden çok işveren: istisna yalnız en yüksek ücrete (GVK 23/18). Diğer bordroda `asgari_ucret_istisnasi: false`; hangisinin en yüksek olduğu ay ay değişebilir `[incele]`.
- 🟠 Eksik gün / kısmi süreli: `prim_gun` verilmezse 30 gün sayılır; giriş/çıkış ayında prim fazla, istisna fazla çıkar. Araç asgari ücret gelir ve damga vergisi istisnasını gün oranında uygular; bunun dayanağını özelge/tebliğden doğrula `[doğrula]`.
- 🟠 PEK alt sınırının altında kalan kazanç: işçi payı gerçek kazançtan kesilir, farkın primi (işçi payı dahil) işverene yazılır (`alt_sinir_farki_isci_payi`). Tam ayda asgari ücretin altında brüt ayrıca asgari ücret ihlali olabilir `[incele]` → `../../is-hukuku/SKILL.md`.
- 🟡 Hazine indirimi işaretlendi mi? Şartlar sağlanmıyorsa maliyet düşük çıkar.
- 🟡 Engellilik indirimi (GVK m.31 `[doğrula]`), BES/özel sigorta, sendika aidatı hesapta yok.
- 🟡 Yıllık "sabit net" sözleşmede netten brüteyi `yil` ya da `aylar` ile çöz; tek ay çözümü dilim atlamasını kaçırır.
- 🟡 `gelir_vergisi_istisna` damga matrahından düşülmez; istisna ödemenin damga durumu ayrıca değerlendirilir `[doğrula]`.
- [incele] Sözleşmede ücretin net mi brüt mü kararlaştırıldığı hukuki yorumdur → `../../is-hukuku/SKILL.md`.

## Sık hatalar

- Tek ay hesabını yıl için 12 ile çarpmak: dilim atlaması kaçar. `yil` ya da `aylar` kullan.
- Yemek, yol gibi istisna ödemeyi brüte katıp istisnayı vermemek: iki matrah da şişer. SGK ve gelir vergisi istisnası farklı tutarlar olabilir; ayrı ayrı ver.
- Asgari ücret istisnasını iki işverende birden uygulamak.
- PEK üst sınırını aşan ücrette primi tüm brütten hesaplamak (araç sınırı uygular; elle hesapta unutulur).
- İşsizlik işçi payını GV matrahından düşmemek.
- Hazine indirimi "her işverene var" sanmak; borç ve süre şartları vardır.
- Kâğıt bordroyla karşılaştırırken kuruş farkını hata saymak: araç her kalemi kuruşa yuvarlar, program farklı sırayla yuvarlayabilir.

## Aracın bilinen sınırları (çıktıya taşı)

- `sgk_pek_ust_kat` o dönem tabloda yoksa üst sınır uygulanmaz; araç bunu `uyarilar`da söyler. `pek_ust_siniri: null` görürsen 🔴 işaretle ve kullanıcıya söyle.
- İşveren oranlarının bir kısmı dönem tablosunda yoksa işveren maliyeti `null` döner (tarihçe 2025-2026'dan eksiksiz).
- 2006 öncesi hesap yok; 2008-10 öncesi prim kuralları doğrulanmamış (araç uyarır).
- Teşvikler (6111, 7103 vb.), engellilik indirimi, yemek/yol istisnası hesaba katılmaz (araç uyarır).

## Uyuşmazlığa dönüş

Ücretin eksik bildirildiği SGK tespiti, idari para cezası, işçinin ücret farkı talebi ya da GİB incelemesi görünürse kapıyı aç: SGK → `../../sosyal-guvenlik-sgk/SKILL.md`, işçilik alacağı → `../../is-hukuku/SKILL.md`, vergi incelemesi → `../../vergi/SKILL.md`.

## Çıktı

SKILL.md Adım 4 iskeleti. Hesap tablosu sütunları: Ay | Brüt | SGK işçi | İşsizlik işçi | GV matrahı | Kümülatif | GV | İstisna | Ödenecek GV | Damga | Net | İşveren SGK | İşveren işsizlik | Maliyet. Altına `formul`, `dayanak`, `parametre.tablolar` ve tüm `uyarilar`.
