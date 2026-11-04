---
name: ceza-hukuku-suclar
description: >
  Ceza hukuku esas değerlendirmesi yapar (TCK, CMK): suç vasfı ve unsurları,
  kast ve taksir, teşebbüs, iştirak, hukuka uygunluk, ceza hesabı, HAGB,
  erteleme, seçenek yaptırım, uzlaştırma, şikâyet süresi, zamanaşımı ve etkin
  pişmanlık; dolandırıcılık, uyuşturucu, bilişim ve cinsel suçlar gibi suç
  tipleri. Müdafi, vekil, şüpheli ve mağdur için. Kullanıcı "bu fiil hangi
  suç", "ne kadar ceza çıkar", "HAGB alır mıyım", "uzlaşmaya tabi mi"
  dediğinde kullan. Esas değerlendirmeyi bu beceri yapar; dilekçe metnini
  ceza-ve-infaz-dilekce ve kanun-yollari-dilekce yazar. VUK 359 vergi'de,
  karşılıksız çek sirketler-ticaret'te.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: ifade tutanağı, iddianame, mütalaa, gerekçeli karar, şikâyet dilekçesi]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /ceza-hukuku-suclar

5237 sayılı Türk Ceza Kanunu (TCK) genel ve özel hükümleri, 5271 sayılı Ceza Muhakemesi Kanunu'nun (CMK) uzlaştırma, önödeme bağlantılı ve HAGB hükümleri ile 5395 sayılı Çocuk Koruma Kanunu için **esas değerlendirme** becerisi: fiil hangi suçu oluşturur, unsurlar ve kusur var mı, hangi indirim ve artırımlar uygulanır, ceza ne aralıkta çıkar, hangi yaptırım seçenekleri açıktır, dava şartları (şikâyet, uzlaştırma, önödeme, zamanaşımı) karşılanmış mı. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

**Ceza dosyasında özgürlük söz konusudur.** Emin-ve-yanlış cevabın bedeli hukukun diğer alanlarından ağırdır: tutukluluk, hapis, adli sicil. Her süre ve her oran madde metninden çekilir; çekilemeyen her şey `[doğrula]` ya da `[incele]` alır.

---

## Ne zaman kullanılır

- **Konular ve mevzuat:** Türk ceza hukuku esas değerlendirmesi (5237 TCK, CMK 253-254, 5395): suç vasfı ve unsurları, kast, olası kast, bilinçli taksir, teşebbüs, iştirak, meşru müdafaa, haksız tahrik, yaş küçüklüğü, zincirleme suç, ceza hesabı (TCK 61 sırası), HAGB, erteleme, seçenek yaptırım, önödeme, uzlaştırma kapsamı, şikâyet süresi, dava zamanaşımı, etkin pişmanlık; hakaret, tehdit, şantaj, yaralama, öldürme, hırsızlık, yağma, dolandırıcılık, güveni kötüye kullanma, uyuşturucu ticareti ve kullanma, bilişim suçları, sahtecilik, zimmet, rüşvet, ihaleye fesat, örgüt ve terör, cinsel suçlar, adli süreçteki çocuk; 7531, 7571, 7589, 7593 değişiklikleri.
- **Tipik kullanıcı ifadeleri:** "bu fiil hangi suç", "dolandırıcılık mı hukuki ihtilaf mı", "ne kadar ceza çıkar", "HAGB alır mıyım", "uzlaşmaya tabi mi", "şikâyet süresi geçti mi", "zamanaşımı doldu mu", "içici mi satıcı mı".
- **Komşu beceriler:** Dilekçe metni ceza-ve-infaz-dilekce ve kanun-yollari-dilekce'ye; VUK 359 vergi'ye, karşılıksız çek sirketler-ticaret'e gider.

## Kapsam

**Kapsar:** TCK genel hükümleri (kanunilik, zaman bakımından uygulama ve lehe kanun, kast/taksir, teşebbüs, iştirak, hukuka uygunluk nedenleri, kusurluluğu etkileyen nedenler, içtima), yaptırımlar (hapis, adli para, seçenek yaptırımlar, erteleme, güvenlik tedbirleri), HAGB'nin esas koşulları, şikâyet, uzlaştırma ve önödeme kapsamı, dava ve ceza zamanaşımı, etkin pişmanlık hükümleri; sık suç tipleri (hayata ve vücut dokunulmazlığına, hürriyete, şerefe, malvarlığına, cinsel dokunulmazlığa, aile düzenine, kamu idaresine karşı suçlar; uyuşturucu; bilişim ve sahtecilik; örgüt, terör ve devlet güvenliği); adli süreçteki çocuk; soruşturma evresinde delil ve ifadenin hukuka uygunluğunun **esas** değerlendirmesi; son yargı paketlerinin etkisi. İdare / kamu görevlisi tarafı: suçu bildirme yükümlülüğü, soruşturma izni, kurum zararının şikâyeti.

**Kapsamaz ya da yönlendirir:**
- **Dilekçe metni** (tutuklamaya itiraz, esasa ilişkin savunma, mütalaaya karşı beyan, HAGB beyanı, davaya katılma, infaz) → `../ceza-ve-infaz-dilekce/SKILL.md`. İstinaf ve temyiz dilekçesi → `../kanun-yollari-dilekce/SKILL.md` (`references/ceza-istinaf-temyiz.md`). AYM / AİHM (uzun tutukluluk, ifade özgürlüğü) → `../aym-aihm-basvuru/SKILL.md`. Bu beceri esası kurar, devir özetini hazırlar (ORTAK-KURALLAR.md §14).
- **İnfaz hesabı** (koşullu salıverilme, denetimli serbestlik, mahsup, müddetname, cezaların toplanması) → `../ceza-ve-infaz-dilekce/SKILL.md`; burada yalnız suç tarihinin infaz rejimine etkisi işaretlenir.
- **VUK m.359 kaçakçılık** (sahte / yanıltıcı belge) → vergi tarhiyatı ve iki yargılamanın ilişkisi `../vergi/SKILL.md` (`references/vergi-cezalari-ve-pismanlik.md`); ceza savunması metni `ceza-ve-infaz-dilekce`. Bu beceri yalnız TCK genel hükümlerinin (iştirak, zincirleme, zamanaşımı) uygulanışını değerlendirir.
- **Karşılıksız çek (5941)** ve kambiyo senedi uyuşmazlıkları → `../sirketler-ticaret/SKILL.md` (`references/kiymetli-evrak-ve-cek.md`).
- **Kaçakçılık (5607)**, ateşli silahlar (6136) ve diğer özel ceza kanunları → yalnız TCK genel hükümleri ve kontrol listesi iskeleti; özel kanun ayrıntısı `[incele]`. Gümrük ve vergi yönü (el koyma, gümrük vergisi, idari yaptırım ayrımı) → `../gumruk-dis-ticaret/SKILL.md` (`references/kacakcilik-ve-idari-yaptirim-ayrimi.md`).
- **İhaleye fesadın** ihale hukuku yönü → `../kamu-ihale/SKILL.md` (`references/yasak-fiil-ve-yasaklama.md`); kamu zararı ve Sayıştay → `../kamu-mali-denetim-sayistay/SKILL.md`; memur disiplini ve 4483 soruşturma izni → `../kamu-personeli/SKILL.md`.
- **6284 koruma kararı** (aile içi şiddet tedbirleri) → `../aile-miras/references/aile-ici-siddet-6284.md`; burada yalnız zorlama hapsi ve TCK 232-233 ilişkisi.
- **Suçtan doğan tazminat** (manevi tazminat, haksız fiil) → `../tazminat-haksiz-fiil/SKILL.md`. Kişisel verilerle ilgili suçlar (TCK 135-140) ile KVKK idari yaptırımının ayrımı → `../kvkk/SKILL.md`.
- **Fikri mülkiyet suçları** (FSEK, SMK cezai hükümleri) ve 5651 erişim engeli → `../fikri-mulkiyet-bilisim/SKILL.md` (`references/internet-icerik-kaldirma.md`, `references/telif-fsek-eser-ve-ihlal.md`); burada yalnız TCK genel hükümleri.
- Askerî ceza hukuku, disiplin hukuku, kabahatler (5326 idari para cezası) → kapsam dışı; idari para cezası iptali `../idare-davalari-imar/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "5271"`, `law_type: "Kanun"`, `article_no: "253"`) çağır. Yanıt gelirse `soorgla ✓`; üçüncü fıkrada "(Ek cümle:24/12/2025-7571/24 md.)" notunu görmen 7571 sonrası metnin geldiğini gösterir. 

Profili oku: rol (avukat / avukat olmayan), taraf (şüpheli-sanık müdafii, mağdur-katılan vekili, kurum, kamu görevlisi). Avukat olmayan şüpheliye ya da mağdura ORTAK-KURALLAR.md §1 kapısını uygula: ifade vermeden, uzlaşma teklifini kabul ya da reddetmeden, önödeme yapmadan, şikâyetten vazgeçmeden önce "Bunu bir avukatla gözden geçirdiniz mi?" Soruşturma evresindeki herkes **CMK m.150 uyarınca müdafiden yararlanabilir**; baro CMK bürosunu hatırlat. 

**TCK m.61 MCP'de yok.** `legal_get_statute_article 5237 61`, `legal_list_statute_articles` ve anlam araması boş dönüyor; cezanın belirlenmesi sırasını madde metniyle gösteremiyorsan `[madde çekilemedi — doğrulayın]` de, sırayı `references/ceza-hesaplama.md`'deki iskeletle kur ve Yargıtay kararından teyit et. 

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Suç vasfı ve genel hükümler: kast-taksir, teşebbüs, iştirak, hukuka uygunluk, kusur, içtima | öldürmek mi istedi, olası kast, bilinçli taksir, yardım eden, azmettirme, meşru müdafaa, tahrik, akıl hastalığı, zincirleme | `references/suc-vasfi-ve-genel-hukumler.md` |
| B. Ceza hesabı: temel ceza, artırım-indirim sırası, "ne kadar çıkar" | kaç yıl yatar, ceza hesapla, takdiri indirim, 1/6, tekerrür | `references/ceza-hesaplama.md` |
| C. Yaptırım seçenekleri: HAGB, erteleme, seçenek yaptırım, güvenlik tedbiri, müsadere | HAGB, sabıka, ertelenir mi, paraya çevrilir mi, ehliyet, hak yoksunluğu | `references/yaptirimlar-hagb-erteleme.md` |
| D. Dava şartları ve düşme: şikâyet, uzlaştırma, önödeme, zamanaşımı, vazgeçme | şikâyetçi oldum, şikâyetten vazgeç, uzlaştırmacı aradı, önödeme tebligatı, zamanaşımı, 6 ay | `references/sikayet-uzlastirma-onodeme-zamanasimi.md` |
| E. Hayata ve vücut dokunulmazlığına karşı suçlar | öldürme, yaralama, kemik kırığı, hayati tehlike, trafik kazası ölüm, iş kazası, taksir | `references/hayata-ve-vucuda-karsi-suclar.md` |
| F. Hürriyete ve şerefe karşı suçlar | tehdit, şantaj, alıkoyma, hakaret, küfür, WhatsApp mesajı, sosyal medya, ısrarlı takip, konut | `references/hurriyet-ve-serefe-karsi-suclar.md` |
| G. Malvarlığına karşı suçlar | hırsızlık, yağma, gasp, dolandırıcılık, güveni kötüye kullanma, emanet, borç ödemedi, hesabımı kullandırdım, mala zarar | `references/malvarligi-suclari.md` |
| H. Uyuşturucu suçları | uyuşturucu, esrar, hap, kullanıcı mı satıcı mı, hassas terazi, denetimli serbestlik, tedavi | `references/uyusturucu-suclari.md` |
| I. Bilişim, sahtecilik, kamu idaresine karşı suçlar (beyaz yaka); kamu görevlisi tarafı | bilişim sistemi, kart kopyalama, sahte belge, imza taklidi, zimmet, rüşvet, irtikap, görevi kötüye kullanma, ihaleye fesat, suç duyurusu yükümlülüğü | `references/bilisim-sahtecilik-ve-kamu-idaresi-suclari.md` |
| J. Cinsel suçlar ve aile düzenine karşı suçlar | cinsel saldırı, istismar, taciz, rıza, mağdur beyanı, kötü muamele, nafaka ödememe, 6284 ihlali | `references/cinsel-ve-aile-duzeni-suclari.md` |
| K. Örgüt, terör, devlet güvenliği | örgüt üyeliği, propaganda, ByLock, gizli tanık, casusluk, etkin pişmanlık 221 | `references/orgut-teror-ve-devlet-guvenligi.md` |
| L. Adli süreçteki (suça sürüklenen) çocuk | 12-15 yaş, 15-18 yaş, farik mümeyiz, sosyal inceleme, çocuk mahkemesi | `references/adli-surecteki-cocuk.md` |
| M. Soruşturma evresi: ifade, delilin hukuka uygunluğu, gözaltı, tutuklama şartlarının esası | ifadeye çağrıldım, avukatsız ifade, arama kararı yok, HTS, gözaltı süresi, tutuklama şartları | `references/sorusturma-evresi-delil-ve-ifade.md` (dilekçe → `ceza-ve-infaz-dilekce`) |
| N. "Bu değişiklik dosyamı etkiler mi", yargı paketleri, lehe kanun | yeni yargı paketi, 7571, 7589, kanun değişti, lehe hüküm | `references/ceza-mevzuati-degisiklik-takibi.md` |

Bir olay birden fazla tipe giriyorsa (ör. hakaret + tehdit: F + D; nitelikli dolandırıcılıkta ceza hesabı: G + B + C; çocuk sanığın hırsızlığı: L + G + C) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa): şüpheli/sanık mı, mağdur/katılan mı, kurum (şirket, banka) mı, kamu görevlisi mi? Kontrol listesi aynıdır; vurgu değişir. Savunma tarafında unsurların yokluğu, şüpheden sanık yararlanır ilkesi ve lehe hükümler; mağdur tarafında şikâyet ve katılma süreleri, delil koruma, nitelikli hâllerin ispatı öne çıkar. **İdare / kamu görevlisi tarafı** (bureaucrat bakışı): öğrenilen suçun bildirimi (TCK m.279), kurumun suçtan zarar gören sıfatıyla şikâyeti ve katılması, memur hakkında 4483 izin süreci — `references/bilisim-sahtecilik-ve-kamu-idaresi-suclari.md` "İdare tarafı" başlığı.

**Ad-hoc doktrin sorusu** (ör. "hırsızlık uzlaştırmaya tabi mi?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Suç tarihini ve süreleri en başta çek

Ceza hukukunda **suç tarihi** her şeyi belirler: uygulanacak kanun (TCK m.7 lehe kanun), uzlaştırma ve önödeme kapsamı (7531, 7571 geçiş maddeleri), zamanaşımı, çocuklarda yaş. İlk iş olay tarihini, şikâyet tarihini, ifade/iddianame/hüküm tarihlerini topla.

- **Şikâyet süresi** 6 ay; fiili ve faili öğrenmeden başlar, zamanaşımını geçemez; **hakarette** fiilden itibaren her hâlde 2 yıl (7531, 14.11.2024'ten sonra soruşturmaya geçilen dosyalar). 
- **Dava zamanaşımı** cezanın üst sınırına göre kademelidir; çocuklarda kısalır; kesme nedenleriyle en fazla yarısı kadar uzar. 
- `legal_calculate_deadline` yalnız **ceza istinafını** (`cmk_appeal`, iki hafta) hesaplıyor; şikâyet, uzlaşma teklifine cevap (7 gün), önödeme (10 gün), itiraz süreleri için "Kural bulunamadı" döner. Elle hesapla (olay günü sayılmaz), son günü `legal_check_holiday` ile kontrol et, `[doğrula]`. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴. Tutuklu dosyada her süre 🔴 öncelikle.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat** — `legal_get_statute_article` (`law_type: "Kanun"` ver):
- 5237 TCK, 5271 CMK, 5395 ÇKK, 5275 (yalnız suç tarihine bağlı infaz rejimi işareti), 3713 TMK, 6415, 2313 ve 3298 (uyuşturucu), 5607, 6136, 213 VUK m.359 (`law_type: "Kanun"` zorunlu; 213 bir köy kaydıyla çakışıyor), 4483.
- **TCK m.61 boş** (yukarıda). Harfli maddeler (TCK 123/A, 217/A, 245/A; CMK 128/A) `legal_get_statute_article` ile doğrudan geliyor (`article_no: "123/A"`); boş dönerse `legal_list_statute_articles` (`article_query`) ya da `legal_search_statute_semantic` (`mevzuat_no: "5237"`). **TCK m.328 ayrı kayıt olarak gelmiyor**; metni m.327 kaydının içinde. 
- **Madde tarihçesi CMK için 2014'te duruyor** (`legal_get_statute_article_history 5271 253` son sürüm 2014-06-18). Değişikliği madde metnindeki "(Değişik/Ek: …-7571/24 md.)" notlarından ve değiştiren kanunun RG metninden (`legal_get_official_gazette_document`) oku. Olay tarihindeki metin için `legal_search_statute_versions` 2014 öncesine kadar işe yarar (ör. HAGB'de 6008 "sanığın kabulü" cümlesi). 
- Lehe kanun karşılaştırmasında (TCK m.7) eski ve yeni metni **ayrı ayrı** çek, somut olaya iki kanunu ayrı ayrı uygula; karma uygulama yapma `[incele]`. 

**Kararlar** — `legal_search_cases`:
- `mahkeme: "yargitay"`; suç vasfı tartışmalarında önce **Ceza Genel Kurulu** (`daire: "Ceza Genel Kurulu"`), sonra ilgili ceza dairesi. Olayı serbest cümleyle yaz (ör. `sorgu: "borcun ödenmemesi hileli davranış bulunmadığından dolandırıcılık suçu oluşmaz"`).
- **Daire iş bölümü sabit yazılmaz.** Güncel liste Yargıtay Büyük Genel Kurulu 2026/1 kararındadır (RG 30.06.2026, `legal_get_official_gazette_document` `url: "https://www.resmigazete.gov.tr/eskiler/2026/06/20260630-6.pdf"` `offset: 58000`). OCR'da daire başlıkları çoğunlukla okunmuyor; daire, bloklar sırayla (1. → 12. Ceza Dairesi) dizildiği için sıradan çıkarılır — `[doğrula]`. Eski YAML'lardaki daire eşlemelerinin bir kısmı bu kararla çelişiyor (bkz. "Kaynak görev tanımları"). Şüphede daireyi seçmeden ara, dönen kararın dairesine bak. 
- Kapatılmış dairelerin (ör. 15., 16., 18., 20. Ceza Dairesi) kararları yalnız **eski emsal** olarak taranır; dönen kararın tarihine bak.
- `legal_case_facets` daire tespiti için güvenilmez: sorgu sözcüklerinden en az biriyle eşleşen kararları sayıyor (ceza sorgusunda hukuk daireleri de çıkıyor). 
- **Kapsam:** Yargıtay ceza kararları 2024-2025 yoğun, 2026 kısmi (aynı sorguda 2024: ~71 bin, 2025: ~68 bin, 2026: ~7,4 bin). "Son 3 yıl" emsalini 2024-2026'dan seç. 
- Bölge adliye mahkemesi ceza daireleri → `mahkeme: "bam"`; AYM (kişi özgürlüğü, ifade özgürlüğü, adil yargılanma) → `mahkeme: "anayasa"`; AİHM → `mahkeme: "aihm"`.
- **Zorunlu adım:** her analizde son 3 yıldan en az bir Yargıtay kararının tam metnini `legal_get_case_document` ile oku ve **alıntı-önerme kontrolünü** yap (ORTAK-KURALLAR.md §7). Ceza kararlarında karşı oy sık ve uzun; arama özetindeki pasaj çoğu zaman **karşı oydan** geliyor (ör. uyuşturucu miktar ölçütü). 

**İdari görüş ve kurul kararları** — ceza hukuku alanında `legal_search_admin_guidance` kapsamında **Adalet Bakanlığı / Ceza İşleri Genel Müdürlüğü genelgeleri yok**; ceza sorgusu GİB özelgeleri ve Rekabet Kurulu kararları döndürüyor. Kurul verisi yalnız dolaylı ilgili alanlarda kullanılır: VUK 359 bağlantısında GİB (`kurum: "Gelir İdaresi Başkanlığı"`), kişisel veri suçlarıyla idari yaptırım ayrımında KVKK (`kurum: "Kişisel Verileri Koruma Kurulu"`, `belge_tur: "karar_ozeti"`), ihaleye fesatta KİK uyuşmazlık kararları (`legal_search_cases` `mahkeme: "kik"`), bankacılık suçlarında BDDK (`kurum: "Bankacılık Düzenleme ve Denetleme Kurulu"`). 

**Sayısal parametreler** — beceri metnine hiçbir tutar, sınır ve harç yazılmaz:
- Önödemede gün başına miktar ve adli para cezasının gün karşılığı kanun metninde TL olarak yazılı ve değişir; `legal_get_statute_article 5237 75` ve `5237 52` metninden oku, `[doğrula]`. 
- Ceza aralıkları (alt-üst sınır) **her seferinde madde metninden**; son paketlerde birçok suçun cezası değişti (ör. 7571 ile TCK 89, 170, 220; 7593 ile 31 ve 233). 
- Yargılama giderleri ve harç → `legal_calculate_court_fee` / `legal_get_social_parameters` (ceza yargılamasında sınırlı). Suçtan elde edilen menfaatin güncellenmesi → `legal_calculate_cpi_change` yalnız gösterge amaçlı, `[incele]`.

### Adım 4 — Analiz

İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

**Ceza dosyasının sabit sırası** (eski YAML'lardaki "usul filtresi" ve "suç vasfı" adımları birleştirilerek korundu, upstream `litigation-legal/claim-chart` unsur tablosu fikriyle):
1. **Olay kronolojisi** (upstream `chronology` fikri): suç tarihi, öğrenme, şikâyet, ifade, gözaltı, tutuklama, iddianame, hüküm. Her olayın yanına dayanağı (tutanak, rapor, HTS).
2. **Usul ön kontrolü:** şikâyet var mı ve süresinde mi; uzlaştırma kapsamında mı ve uzlaştırma yapıldı mı; önödeme teklif edildi mi; zamanaşımı; çocuk yaşı; soruşturma izni (kamu görevlisi). Bunlardan biri eksikse esasa girmeden 🔴.
3. **Unsur tablosu** (upstream `claim-chart` uyarlaması): seçilen suçun her unsuru için satır — maddi unsur (fiil, netice, illiyet), manevi unsur (kast türü/taksir), hukuka aykırılık, kusur — ve her satıra dosyadaki delil ile **delilin hukuka uygunluğu**. Boş kalan satır **öncelikli çıktıdır** (eksik unsur = beraat ya da vasıf değişikliği argümanı).
4. **Alternatif vasıflar:** en az bir alternatif suç tipini aynı tabloyla karşılaştır (hırsızlık/güveni kötüye kullanma/yağma; öldürmeye teşebbüs/yaralama; ticaret/kullanma; dolandırıcılık/hukuki ihtilaf).
5. **Ceza hesabı** (`references/ceza-hesaplama.md`) ve **yaptırım seçenekleri** (`references/yaptirimlar-hagb-erteleme.md`).
6. **Strateji `[incele]`:** etkin pişmanlık, zarar giderme (HAGB ve erteleme şartı), uzlaşma, önödeme — her birinin geri dönüşü olmayan sonucu ayrıca yazılır.

**Orantılılık:** "Hakaret uzlaştırmaya tabi mi?" iki cümle ister (7571'den sonra hayır; geçiş maddesine bak); tam dosya analizi değil.

### Adım 5 — Çıktı
Referans dosyasındaki iskeleti kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Suç / soru]: [şüpheli-sanık / mağdur / kurum] — suç tarihi [GG.AA.YYYY]

### Sonuç (tek paragraf)
[Muhtemel vasıf, en güçlü argüman, en acil süre]

### Kritik tarihler ve süreler
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |

### Usul ön kontrolü
| Konu | Durum | Dayanak | İşaret |
(şikâyet · uzlaştırma · önödeme · zamanaşımı · yaş · soruşturma izni)

### Unsur tablosu — [suç adı, madde]
| Unsur | Dosyadaki delil | Delil hukuka uygun mu | Değerlendirme | İşaret |

### Alternatif vasıf
| Vasıf | Ayırt edici unsur | Dosyada var mı | Ceza aralığı (madde metninden) |

### Muhtemel ceza ve yaptırım seçenekleri
[ceza-hesaplama iskeleti; HAGB / erteleme / seçenek yaptırım uygunluğu]

### Dayanaklar
[madde, CGK/daire kararı — her biri etiketli; tam metni okunan karar işaretli]

### Eksik bilgi
[açık sorular]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı ve tek yönlü kapılar
Avukat olmayan kullanıcı şu adımlardan önce ORTAK-KURALLAR.md §1 kapısını uygula: kollukta ya da savcılıkta ifade vermek, uzlaşma teklifini kabul ya da reddetmek (sonuçsuz uzlaştırma tekrarlanamaz), önödeme yapmak, şikâyetten vazgeçmek (vazgeçme geri alınamaz; şahsi haklardan da vazgeçtiğini açıklarsa hukuk davası açamaz), etkin pişmanlık beyanında bulunmak (ikrar niteliği), HAGB'ye ilişkin beyan. 

**Susma hakkı ve ifade:** ifade öncesinde kullanıcıya olayı anlatması için yönlendirme yapma; "ne söylemeliyim" sorusunda ifade stratejisi avukatın işidir `[incele]` — müdafi ile görüşmeden ifade verilmemesini öner.

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Tutuklamaya / adli kontrole itiraz, tahliye talebi | `../ceza-ve-infaz-dilekce/SKILL.md` (`references/tutuklama-itiraz-ve-tahliye.md`) |
| Esasa ilişkin savunma, mütalaaya karşı beyan, suç vasfı değişikliği talebi | `../ceza-ve-infaz-dilekce/SKILL.md` (`references/esas-savunma.md`) |
| Tevsi-i tahkikat, bilirkişi, keşif, HTS talebi; vareste | `../ceza-ve-infaz-dilekce/SKILL.md` (`references/durusma-ici-talepler.md`) |
| HAGB beyanı ve HAGB kararına karşı yol | `../ceza-ve-infaz-dilekce/SKILL.md` (`references/hagb.md`) |
| Davaya katılma (mağdur, kurum) | `../ceza-ve-infaz-dilekce/SKILL.md` (`references/davaya-katilma.md`) |
| İstinaf ve temyiz dilekçesi | `../kanun-yollari-dilekce/SKILL.md` (`references/ceza-istinaf-temyiz.md`) |
| Suç duyurusu / şikâyet dilekçesi, KYOK kararına itiraz | Ayrı dilekçe referansı yok: `../ceza-ve-infaz-dilekce/SKILL.md` kapsamında işaret; iskelet bu becerinin `references/sikayet-uzlastirma-onodeme-zamanasimi.md` dosyasında; ORTAK-KURALLAR.md §13 kuralları |
| AYM bireysel başvuru (kişi özgürlüğü, ifade özgürlüğü), AİHM | `../aym-aihm-basvuru/SKILL.md` |
| VUK 359 savunması | `../ceza-ve-infaz-dilekce/SKILL.md`; vergi yönü `../vergi/SKILL.md` |
| Karşılıksız çek şikâyeti (5941) | `../ceza-ve-infaz-dilekce/SKILL.md`; esas `../sirketler-ticaret/SKILL.md` |

Devrederken taşı: taraf ve rolü, suç tarihi, soruşturma/esas numarası, kritik tarihler ve süre tablosu, usul ön kontrolü sonucu, unsur tablosu ve boş satırlar, alternatif vasıf, muhtemel ceza aralığı, çekilmiş madde ve karar künyeleri (etiketleriyle; tam metni okunanlar işaretli), istem önerisi, açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** şikâyet, itiraz, kanun yolu ve dava zamanaşımı süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Kronoloji / unsur-delil tablosu:** olay kronolojisi belge çoksa (suç unsuru tablosu bu becerinin kendi akışıdır) → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).
- **Genel mevzuat taraması, takip listesi, boşluk tablosu:** ceza dışı alanlarla birlikte genel tarama (alana özgü takip `references/ceza-mevzuati-degisiklik-takibi.md`'de kalır) → [mevzuat-takibi](../mevzuat-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Kesin ceza tahmini vermez; "çıkabilecek ceza aralığı" ve "uygulanabilecek indirimler" verir, hâkim takdirini `[incele]` diye işaretler.
- İfade stratejisi, tanık yönlendirmesi ya da delil karartmaya yarayabilecek tavsiye vermez.
- Ceza aralığını, önödeme miktarını, adli para cezasının gün karşılığını ve daire iş bölümünü metinden söylemez; araçtan, madde metninden ya da RG'den çeker veya `[doğrula]` der.
- UYAP'a, savcılığa ya da mahkemeye başvuru göndermez; uzlaştırmacıyla görüşmez.

---

