---
name: gayrimenkul-insaat
description: >
  Taşınmaz ve inşaat uyuşmazlıklarını değerlendirir (TMK eşya hukuku, 634 KMK,
  6306): tapu iptali ve tescil, satın alma öncesi tapu ve takyidat kontrolü,
  ortaklığın giderilmesi, önalım, ecrimisil, el atmanın önlenmesi, kat
  mülkiyeti ve aidat, kat karşılığı inşaatta geç teslim ve eksik iş, kentsel
  dönüşüm. Malik, alıcı, arsa sahibi ve avukatlar için. Kullanıcı "tapumu geri
  almak istiyorum", "hisseli tapu satılsın", "müteahhit evi teslim etmedi"
  dediğinde kullan. Kira kira-hukuku'nda, imar ve ruhsat
  idare-davalari-imar'da, muris muvazaası aile-miras'ta; dilekçe metni
  hukuk-yargilamasi-dilekce'de yazılır.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: tapu kaydı, takyidat belgesi, kat karşılığı sözleşmesi, kat malikleri kurulu kararı, ihtarname]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /gayrimenkul-insaat

Taşınmaz mülkiyeti, tapu sicili, paylı mülkiyet, kat mülkiyeti ve kat karşılığı inşaat uyuşmazlıkları için birleşik alan becerisi. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- **Konular ve mevzuat:** Türk taşınmaz ve inşaat uyuşmazlıkları (TMK 683-1027, 634 KMK, 6306, 4708, 2644): tapu iptali ve tescil, yolsuz tescil, iyiniyetli üçüncü kişi, sahte vekâlet, ehliyetsizlik, olağanüstü zamanaşımı (TMK 713), Hazinenin tapu sicili sorumluluğu (TMK 1007), ev alımı öncesi tapu ve takyidat kontrolü, satış vaadi şerhi, hisseli tapu, ortaklığın giderilmesi (izale-i şuyu), önalım (şufa) davası, ecrimisil, intifadan men, el atmanın önlenmesi, kat mülkiyeti, aidat, işletme projesi, kat malikleri kurulu kararının iptali, kat karşılığı inşaatta geç teslim, eksik iş, geriye/ileriye etkili fesih, yükleniciden daire alan, kentsel dönüşümde arsa payı satışı, yapı denetimi.
- **Tipik kullanıcı ifadeleri:** "tapumu geri almak istiyorum", "hisseli tapu satılsın", "kardeşim evi kullanıyor", "müteahhit evi teslim etmedi", "aidat ödemiyor".
- **Komşu beceriler:** Kira kira-hukuku'nda, imar ve ruhsat idare-davalari-imar'da, muris muvazaası aile-miras'ta; dilekçe hukuk-yargilamasi-dilekce'ye devredilir.

## Kapsam

**Kapsar:** tapu iptali ve tescil (yolsuz tescil, iyiniyet, irade sakatlığı, sahte vekâlet, ehliyetsizlik, inanç sözleşmesi, haricen satış ve zilyetliğe dayalı tescil, olağanüstü zamanaşımı); taşınmaz alımı öncesi tapu ve takyidat incelemesi; Hazinenin TMK 1007 sorumluluğu; paylı ve elbirliği mülkiyet, ortaklığın giderilmesi; yasal önalım; el atmanın önlenmesi, kal, ecrimisil (paydaşlar arası dahil); kat mülkiyeti ve kat irtifakı uyuşmazlıkları (aidat, işletme projesi, kurul kararının iptali, ortak yerler, kullanım amacı, devir mecburiyeti); kat karşılığı inşaatın tapu, teslim, ayıp ve gecikme uyuşmazlıkları; 6306 sonrası paydaşlar arası ilişki ve arsa payı satışı; 4708 yapı denetim sorumluluğu ve yapı hasarı. İdare tarafı: tapu müdürlüğü, Hazine ve 6306 uygulayıcısının bakışı (her referansta "İdare tarafı" başlığı).

**Kapsamaz ya da yönlendirir:**
- Kira sözleşmesi, kira artışı, tahliye → `../kira-hukuku/SKILL.md`. Paydaşın taşınmazı üçüncü kişiye kiraya vermesi ve ecrimisil burada; kiracı-kiralayan ilişkisi orada.
- İmar planı, ruhsat, yıkım ve imar para cezası, riskli yapı tespitine karşı iptal davası, kamulaştırma bedeli ve idari el atma → `../idare-davalari-imar/SKILL.md` (`references/imar-plani-ruhsat-ve-donusum.md`, `references/kamulastirma.md`). Kamulaştırmasız **fiilî** el atmanın adli yargı yönü burada kısaca, ayrıntı orada.
- Kat karşılığı ya da eser sözleşmesinin **metin incelemesi** (madde madde, pazarlık) → `../sozlesme-incelemesi-tbk/references/eser-ve-insaat.md`; taşınmaz satışı, satış vaadi, bağışlama ve trampa sözleşmesi metni → `../sozlesme-incelemesi-tbk/references/satis-trampa-bagislama.md`. Bu beceri sözleşme kurulduktan sonra çıkan tapu, teslim, ayıp ve gecikme uyuşmazlığını işler.
- Muris muvazaası, tenkis, mirasçılar arası paylaşım ayrıntısı → `../aile-miras/references/mirascilik-sakli-pay-ve-tenkis.md`; aile konutu şerhi ve rızasız devir → `../aile-miras/SKILL.md` (aile mahkemesi). Burada yalnız tapu iptali iskeletiyle birleşme noktası işlenir.
- Konut alımında tüketici olarak ayıp, ön ödemeli konut satışı → `../tuketici/SKILL.md`.
- Kamu taşınmazının satışı, kiralanması ve 2886 ecrimisili → `../kamu-ihale/references/devlet-ihale-2886.md`.
- Tapu harcı, KDV, emlak vergisi, değer artış kazancı → `../vergi/SKILL.md`.
- Taşınmaz haczi, ihale, ipoteğin paraya çevrilmesi, tasarrufun iptali → `../icra-iflas/SKILL.md`.
- Yabancının taşınmaz edinimi (2644 m.35) ve yatırım yoluyla vatandaşlık → `../yabancilar-vatandaslik/SKILL.md` (`references/tasinmaz-edinimi-ve-tenfiz.md`, `references/vatandaslik.md`).
- Kamu ihalesiyle yapılan yapım işi → `../hakedis/SKILL.md`.
- Dilekçe, arabuluculuk başvurusu ve ihtarname metni → `../hukuk-yargilamasi-dilekce/SKILL.md`; istinaf ve temyiz → `../kanun-yollari-dilekce/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "4721"`, `law_type: "Kanun"`, `article_no: "733"`) çağır. Yanıt gelirse `soorgla ✓`; metinde "(Değişik birinci fıkra:24/12/2025-7571/35 md.)" notunu görmen güncel metnin geldiğini gösterir. 

Profili oku: rol (avukat / değil) ve taraf (malik, paydaş, arsa sahibi, yüklenici, bağımsız bölüm alıcısı, kat maliki, yönetici, tapu müdürlüğü ya da Hazine temsilcisi).

**Numara çakışmaları:** `legal_resolve_statute` yalnız `query: "634"` ile çağrılırsa bir "genel yazı" kaydını seçiyor; Kat Mülkiyeti Kanunu `statute_id 54748`. 4721 iki kayıtlı (`statute_id 69462` doğru), 6306 bir yönetmelikle karışıyor, 6325 üç aday (`statute_id 69230`). Her çağrıda `law_type: "Kanun"` ver ya da `statute_id` kullan; dönen başlığı kontrol et. 

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Tapu iptali ve tescil (yolsuz tescil, sahtecilik, ehliyetsizlik, hile, vekâletin kötüye kullanılması, inanç sözleşmesi, haricen satış, zilyetlikle kazanma) | tapum elimden gitti, sahte vekâlet, ehliyetsizdi, babam satmadı, haricen aldım tapusu verilmiyor, 20 yıldır kullanıyorum | `references/tapu-iptali-ve-tescil.md` |
| B. Taşınmaz alımı öncesi inceleme; satış vaadi; Hazinenin 1007 sorumluluğu | ev alacağım kontrol et, takyidat, ipotek, haciz şerhi, satış vaadi sözleşmesi şerhi, tapu müdürlüğü hata yaptı | `references/tasinmaz-edinimi-ve-tapu-incelemesi.md` |
| C. Paylı ve elbirliği mülkiyet, ortaklığın giderilmesi | hisseli tapu, izale-i şuyu, satış yoluyla ortaklığın giderilmesi, aynen taksim, kardeşler anlaşamıyor | `references/payli-mulkiyet-ve-ortakligin-giderilmesi.md` |
| D. Önalım (şufa) | hissemi sattılar haberim yok, önalım davası, rayiç bedel depo | `references/onalim-hakki.md` |
| E. El atmanın önlenmesi, kal, ecrimisil (paydaşlar arası dahil), kamulaştırmasız fiilî el atma | işgal, ecrimisil, kira gibi tazminat, intifadan men ihtarı, komşu duvarı taşmış, belediye yol yaptı | `references/el-atma-ve-ecrimisil.md` |
| F. Kat mülkiyeti (634) | aidat, işletme projesi, yönetici, kat malikleri kurulu kararı, ortak alan işgali, meskende işyeri, çatı/otopark | `references/kat-mulkiyeti-634.md` |
| G. Kat karşılığı inşaat uyuşmazlığı | müteahhit teslim etmedi, inşaat yarım kaldı, geç teslim kira kaybı, eksik iş, iskân yok, yükleniciden daire aldım | `references/kat-karsiligi-insaat-uyusmazliklari.md` |
| H. Kentsel dönüşüm (6306) sonrası paydaş ilişkileri | salt çoğunluk kararı, payım satılacak, müteahhit işe başlamadı, kira yardımı | `references/kentsel-donusum-ozel-hukuk.md` |
| I. Yapı denetimi ve yapı hasarı | yapı denetim firması sorumlu mu, taşıyıcı sistem kusuru, deprem hasarı, karot | `references/yapi-denetimi-ve-yapi-hasari.md` |

Bir olay birden çok tipe giriyorsa (ör. yükleniciden daire alan kişinin tapusu iptal ediliyor: G + A; paydaş taşınmazı kullanıyor ve satmak istiyorlar: C + E) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa). Kontrol listesi aynıdır; vurgu değişir. İdare tarafı (tapu müdürlüğü, Hazine, 6306 uygulayıcısı) her referansta ayrı başlıktadır: amaç işlemi hukuka uygun kurmak ve tazminat riskini azaltmaktır.

**Ad-hoc doktrin sorusu** (ör. "önalım süresi ne kadar?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Süreleri ve dava şartlarını en başta çek

Her referans dosyasında **süre ve dava şartı tablosu** vardır; her satırın dayanağını `legal_get_statute_article` ile çek.

- `legal_calculate_deadline` taşınmaz sürelerini tanımıyor; elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle. 
- **Dava şartı arabuluculuk:** ortaklığın giderilmesi (taşınır ve taşınmaz), 634 KMK'dan kaynaklanan uyuşmazlıklar ve komşu hakkı uyuşmazlıkları dava açılmadan önce arabulucuya götürülür; taşınmazla ilgili anlaşma belgesine icra edilebilirlik şerhi taşınmazın bulunduğu yer sulh hukuk mahkemesinden alınır ve 7531 ile şerhli belgeyle doğrudan tapuda tescil istenebilir. Metni her seferinde `legal_list_statute_articles` (`statute_id: 69230`, `article_query: "ortaklığın giderilmesi"`, `include_content: true`) ile çek. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat** — `legal_get_statute_article` (`law_type: "Kanun"` ver):
- 4721 TMK (m.683-1027 eşya hukuku; m.194 aile konutu; m.713 olağanüstü zamanaşımı), 634 KMK, 2644 Tapu K. (m.26 resmî senet ve şerh), 6098 TBK (m.19 muvazaa, m.28-39 irade sakatlıkları, m.237 taşınmaz satışı, m.470-486 eser), 6306, 4708, 3402 Kadastro K., 6100 HMK (m.4 sulh hukuk görevi, m.12 kesin yetki), 6325 m.18/B.
- **Son değişiklikler (bu beceriye işlendi):** 7445 (2023, 18/B arabuluculuk), 7471 (2023, 6306 m.3, m.6), 7531 (2024, 18/B-5 arabuluculuk belgesiyle tescil), 7534 (2024, 4708 m.8), **7571** (RG 25.12.2025: TMK 733 ve 734, önalım), **7579** (RG 22.05.2026: KMK m.35, 37, 70; 4708 zemin etüdü; 3402 m.41; 1163 kooperatif tapu devri yasağı).  Yeni değişiklik için `legal_search_official_gazette` (`query: "Kat Mülkiyeti Kanunu"` ya da `"Türk Medeni Kanunu"`, `document_type: "kanun"`, `sort_by: "date_desc"`, `date_from: "<son kontrol>"`).
- **Tarihçe eksik:** `legal_get_statute_article_history` TMK 733'te 2013'te bitiyor, 7571 değişikliği yalnız güncel metinde görünüyor. Eski metin gerekirse değiştiren kanunun RG metnini oku. 

**Kararlar** — `legal_search_cases` `mahkeme: "yargitay"`. Daire iş bölümü her yıl Yargıtay Büyük Genel Kurulu kararıyla değişir; aşağıdaki tablo **yalnız arama filtresi önerisidir**, hüküm kurmadan ve dilekçeye yazmadan önce güncel BGK kararını `legal_search_official_gazette` (`query: "Yargıtay Büyük Genel Kurulu"`, `search_in: "title"`, `sort_by: "date_desc"`) ile bul ve "Gayrimenkul Hukuku" bölümünü oku `[doğrula]`. RG PDF'inin OCR metninde daire numaraları okunmuyor; sıra ve hatırlatmalardan çıkarıldı.

| Konu (2026/1 BGK'ya göre) | Arama filtresi |
|---|---|
| Tapu kaydına ve mülkiyete dayalı tapu iptali-tescil, muris muvazaası, TMK 1025 ve sahtecilik/ehliyetsizlik, irade sakatlığı, tapuda bağışın geri alınması, vekâletin kötüye kullanılması, TMK 1027 düzeltme, kadastro öncesi nedenler | `"1. Hukuk Dairesi"` |
| Kamulaştırma, kamulaştırmasız el atma (ecrimisil birlikte açılmışsa dahil), TMK 1007 tazminatı, 634 KMK uyuşmazlıkları, kat mülkiyeti kurularak ortaklığın giderilmesi, toplu yapı, 6306 riskli yapı uyuşmazlıkları | `"5. Hukuk Dairesi"` |
| Arsa payı/kat karşılığı inşaat, yükleniciden haricen alınan bağımsız bölüm (1988/2 İBK), 6306 kapsamında arsa sahibi-yüklenici yapım uyuşmazlığı, kooperatif | `"6. Hukuk Dairesi"` |
| Sınırlı ayni haklar, önalım, satış vaadi, inanç sözleşmesi (şahsi hakka dayalı), ortaklığın giderilmesi (kat mülkiyeti kurulmadan), komşuluk, el atmanın önlenmesi, kal ve ecrimisil, haricen satış ve zilyetliğe dayalı tescil, TMK 713/1 ve 713/2, imar mevzuatı | `"7. Hukuk Dairesi"` |
| Kadastro mahkemesi kararları, 3402 m.41 | `"8. Hukuk Dairesi"` |
| Genel muvazaa (TBK 19) | `"12. Hukuk Dairesi"` |
| Aile konutu (TMK 194) | `"2. Hukuk Dairesi"` (aile mahkemesi) |

 

- Kapatılan 15. HD (eser) ve 14. HD kararları eski emsal olarak taranır (`tarih_bitis` ile); aktarırken "kapatılan" notunu koru.
- `legal_case_facets` daire tespiti için güvenilir değil (sözcükleri VEYA ile eşleştiriyor); yalnız yoğunluk fikri verir.
- **Zorunlu adım:** her analizde son 3 yıldan en az bir Yargıtay kararının tam metnini `legal_get_case_document` ile oku ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7). Kat karşılığı ve 1007 kararlarında karşı oy sık; çoğunluk gerekçesini ayır.
- **İçtihadı birleştirme:** 1974/1-2 (muris muvazaası), 1947/20-6 (inanç sözleşmesi), 1988/2 (yükleniciden haricen satın alma), **İBBGK 16.05.2025 E.2024/1 K.2025/2** (geriye etkili fesihte yükleniciden iyiniyetle edinen üçüncü kişi korunur; RG 18.07.2025/32959), **İBBGK 08.05.2026 E.2021/8 K.2026/1** (dava dilekçesinde yer almayan talep kısmi ıslahla eklenemez).  

**İdari görüş** — `legal_search_admin_guidance`:
- **GİB özelgeleri** taşınmazın vergisel yönünü verir (kat karşılığı inşaatta KDV ve belge düzeni, tapu harcının doğduğu an, 6306 harç ve damga vergisi istisnası): `kurum: "Gelir İdaresi Başkanlığı"`, `belge_tur: "ozelge"`, gerekirse `tarih_baslangic`. Vergisel değerlendirme `../vergi/SKILL.md`'ye gider. 
- **Kültür Varlıklarını Koruma Yüksek Kurulu** ilke kararları (tescilli taşınmazda onarım ve yapılanma): `kurum: "Kültür Varlıklarını Koruma Yüksek Kurulu"` (22 parça). 
- **Tapu ve Kadastro Genel Müdürlüğü genelgeleri yok:** `kurum: "Tapu ve Kadastro Genel Müdürlüğü"` yalnız iki teşkilat yönetmeliği döndürüyor. TKGM genelgesi gerekiyorsa kullanıcıdan iste ya da web araması `[web araması — doğrulayın]`. 
- **Çevre, Şehircilik ve İklim Değişikliği Bakanlığı** genelge ve yönergeleri var (`kurum: "Çevre, Şehircilik ve İklim Değişikliği Bakanlığı"`; ör. 6306 riskli yapı tahliye/yıkım işlemleri Genelge 2021/23, 6360 tespit formları Genelge 2013/5); Kentsel Dönüşüm Başkanlığının tek tek görüşleri yok.  6306 Uygulama Yönetmeliği değişiklikleri RG'den (`legal_search_official_gazette` `query: "6306 Sayılı Kanunun Uygulama Yönetmeliği"`).

**Sayısal parametreler** — beceri metnine hiçbir tutar, oran ve sınır yazılmaz:
- Harç: `legal_calculate_court_fee` (`basvurma_sulh`, `basvurma_asliye`, `karar_ilam_nispi`); tapu iptali ve ortaklığın giderilmesinde dava değeri ve nispi harç esası `[doğrula]`. 
- Kesinlik ve temyiz sınırları → `legal_get_social_parameters`.
- Aidat gecikme tazminatı oranı KMK m.20'de yazılıdır; madde metninden çek. Ecrimisil ve rayiç değer bilirkişi işidir; endeks gerekiyorsa `legal_calculate_cpi_change` (ÜFE/TÜFE ayrımı `[incele]`).
- Yasal faiz için `legal_get_legal_interest_rates` 7589 sonrası yanlış oran verebilir; faizi 3095 m.1 güncel metniyle karşılaştır `[doğrula]`.

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

**Sıra:** (1) dava şartı (arabuluculuk) ve hak düşürücü süre, (2) görevli ve kesin yetkili mahkeme (HMK m.4, m.12; KMK ek m.1), (3) tapu kaydı ve kronoloji, (4) hukuki sebebin nitelendirilmesi (ayni hak mı şahsi hak mı; hangi İBK), (5) iyiniyetli üçüncü kişi ve şerhler, (6) tazminat, ecrimisil ve bedel kalemleri `[incele]`.

**Tapu kaydı kronolojisi** (upstream `litigation-legal/chronology` becerisinden uyarlandı): tapu iptali, muvazaa, önalım ve kat karşılığı dosyalarında tapu kaydını (tedavül) tarih sırasıyla tabloya dök: tarih | yevmiye | işlem (satış, bağış, ipotek, şerh, haciz) | malik/alıcı | bedel | kaynak | önem (🔴/🟡/⚪). Süreler ve iyiniyet tartışması bu tablodan okunur.

**Orantılılık:** "önalım davası ne zamana kadar açılır?" iki cümle ister.

### Adım 5 — Çıktı
Referans dosyasındaki iskeleti kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [taşınmaz il/ilçe/ada/parsel] — [taraf] — [tarih]

### Sonuç (tek paragraf)

### Süre ve dava şartı tablosu
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |

### Tapu kaydı kronolojisi
| Tarih | Yevmiye | İşlem | Malik/alıcı | Bedel | Önem |

### Bulgular
[her madde: işaret + kısa açıklama + atıf etiketi]

### Görevli mahkeme, yetki, temyiz dairesi
### Dayanaklar
### Eksik bilgi

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Avukat olmayan kullanıcı şunları yapmadan önce ORTAK-KURALLAR.md §1 kapısını uygula: tapuda satış ya da ipotek işlemi yapmak, satış vaadi ya da kat karşılığı sözleşmesini noterde imzalamak, sözleşmeden dönme/fesih ihtarı göndermek, intifadan men ihtarı çekmek, arabuluculuk başvurusu yapmak ya da anlaşma belgesi imzalamak, dava açmak, kat malikleri kurulunda oy kullanmak (devir mecburiyeti, 6306 salt çoğunluk), 6306 teklifini kabul ya da reddetmek.

Geriye etkili fesih ile ileriye etkili fesih arasındaki seçim, önalım bedelinin depo edilip edilmemesi ve 6306 teklifine 15 günlük süre içinde cevap tek yönlü kapılardır: her zaman `[incele]`.

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Ortaklığın giderilmesi ve KMK uyuşmazlığı için zorunlu arabuluculuk başvurusu | `../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md` |
| Tapu iptali-tescil, ortaklığın giderilmesi, önalım, el atmanın önlenmesi-ecrimisil, kat malikleri kurulu kararının iptali, aidat alacağı, kat karşılığı fesih ve tazminat, TMK 1007 tazminatı dava dilekçesi | `../hukuk-yargilamasi-dilekce/references/dava-dilekcesi.md` |
| Tapuya ihtiyati tedbir (devir yasağı) talebi | `../hukuk-yargilamasi-dilekce/references/ihtiyati-tedbir.md` |
| İnşaat seviyesi, ayıp ya da işgal için delil tespiti | `../hukuk-yargilamasi-dilekce/references/delil-tespiti.md` |
| İntifadan men, temerrüt ve dönme ihtarı, aidat ihtarı | `../hukuk-yargilamasi-dilekce/references/ihtarname.md` |
| Bilirkişi (inşaat seviyesi, rayiç bedel, ecrimisil) raporuna itiraz | `../hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md` |
| İstinaf ve temyiz | `../kanun-yollari-dilekce/SKILL.md` (`references/hukuk-istinaf.md`, `references/hukuk-temyiz.md`) |
| Riskli yapı tespitine, 6306 idari işlemine karşı iptal davası | `../idare-davalari-imar/references/idari-dava-dilekcesi.md` |
| Avukatsız kat malikinin komşuya/yöneticiye uyarı yazısı | `../vatandas-basvurulari/SKILL.md` |

Devrederken taşı: taraflar ve rolleri, taşınmaz künyesi (il/ilçe/mahalle/ada/parsel/bağımsız bölüm), tapu kaydı kronolojisi, süre ve dava şartı tablosu (arabuluculuk son tutanak tarihi dahil), görevli/yetkili mahkeme, çekilmiş madde ve karar künyeleri (etiketleriyle), istem önerisi (iptal-tescil, satış, bedel, ecrimisil dönemi), açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Uzun ya da çok belgeli dosya** (tapu kayıt dökümü, kat karşılığı sözleşmesi ve ekleri, kentsel dönüşüm dosyası): okuma [uzun belge protokolüyle](../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md).
- **Kronoloji / unsur-delil tablosu:** tapu kaydı kronolojisi uzunsa ya da belge çoksa → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).
- **Süreyi kaydet:** önalım, dava ve itiraz süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Hesap araçları** (ecrimisil güncellemesi; ÜFE araçta yok): araç kullanımı ve bilinen eksikler → [hesaplamalar/tufe-ve-endeks](../hesaplamalar/references/tufe-ve-endeks.md); tutarlar araçtan çekilir.

## Bu beceri ne yapmaz

- Taşınmazın değerini, ecrimisil tutarını ya da inşaat seviyesini kendisi belirlemez; bilirkişi raporunu denetler ve soru listesi çıkarır.
- Daire iş bölümünü, harcı, kesinlik sınırını ve faiz oranını metinden söylemez; araçtan ya da güncel BGK/RG metninden çeker.
- Tapuda işlem yapmaz, e-Devlet'ten tapu kaydı çekmez; kayıt kullanıcıdan istenir (`[kullanıcı verdi]`).

---

