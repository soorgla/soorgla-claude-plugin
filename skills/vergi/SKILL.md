---
name: vergi
description: >
  Vergi uyuşmazlıklarında mükellef ya da idare tarafı için çalışır: ihbarname
  ve tarhiyatın incelenmesi, yol seçimi (uzlaşma, cezada indirim, dava,
  düzeltme ve şikâyet), vergi incelemesi, vergi cezaları ve zamanaşımı, vergi
  davası, ödeme emri ve haciz gibi tahsil işlemleri. Kullanıcı "vergi cezası
  geldi", "uzlaşmaya gideyim mi", "ödeme emri geldi", "vergi davası açacağım"
  dediğinde kullan. Günlük beyan, bordro ve hesap işi muhasebe'de yapılır;
  uzlaşma, indirim ve özelge dilekçesi idari-ve-kurum-basvurulari'na
  devredilir.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: ihbarname, vergi inceleme raporu, ödeme emri, haciz bildirimi, özelge sorusu]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /vergi

213 sayılı Vergi Usul Kanunu (VUK), 2577 sayılı İdari Yargılama Usulü Kanunu'nun vergi davalarına ilişkin hükümleri, 6183 sayılı Amme Alacaklarının Tahsil Usulü Hakkında Kanun ve temel vergi kanunları (3065 KDV, 193 GVK, 5520 KVK) için birleşik alan becerisi. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- Kanunlar: 213 VUK, 2577 (vergi davası hükümleri), 6183 amme alacağı; 3065 KDV, 193 GVK, 5520 KVK.
- Vergi/ceza ihbarnamesi, ikmalen ya da re'sen tarhiyat, vergi incelemesi ve raporu.
- Sahte fatura, vergi ziyaı, usulsüzlük ve özel usulsüzlük cezası.
- Uzlaşma, cezada indirim (VUK 376), pişmanlık (VUK 371), düzeltme ve şikâyet.
- Tarh ve tahsil zamanaşımı, e-tebligat.
- Vergi mahkemesinde 30 günlük dava, yürütmenin durdurulması, ödeme emrine 15 gün içinde dava.
- Haciz, tecil, kanuni temsilci ve limited ortağı sorumluluğu.
- KDV indirimi, iadesi ve tevkifatı, KKEG, örtülü sermaye, transfer fiyatlandırması, asgari kurumlar vergisi, özelge, vergi kanunu değişiklikleri.
- İdare tarafı: vergi dairesi ve uzlaşma komisyonu.
- Tipik cümleler: "ihbarname", "sahte fatura", "KDV iadesi".
- Devir: uzlaşma, indirim ve özelge dilekçesi → idari-ve-kurum-basvurulari.

## Kapsam

**Kapsar:** ihbarnamenin incelenmesi ve yol seçimi (uzlaşma / cezada indirim / dava / düzeltme-şikâyet), vergi cezaları ve pişmanlık, tarh ve ceza zamanaşımı, tebligat, vergi incelemesi süreci, vergi davasının esası ve süreleri, ödeme emri ve haciz dahil 6183 tahsil işlemleri, tecil, kanuni temsilci ve ortak sorumluluğu, KDV/GVK/KVK temel uygulama ve planlama soruları, özelge araştırması, vergi mevzuatı değişikliklerinin etkisi. İdare tarafı: vergi dairesi, uzlaşma komisyonu ve tahsil dairesi görevlisinin bakışı.

**Kapsamaz ya da yönlendirir:**
- Uzlaşma talebi, cezada indirim, düzeltme-şikâyet ve özelge **dilekçe metni** → `../idari-ve-kurum-basvurulari/SKILL.md` (`references/vergi-uzlasma-indirim-duzeltme.md`, `references/ozelge-talebi.md`). Bu beceri yolu seçer ve süreyi hesaplar; metni orası yazar.
- **Vergi davası dilekçesi** → idari dava dilekçesi iskeleti `../idare-davalari-imar/references/idari-dava-dilekcesi.md`; vergiye özgü ek unsurlar bu becerinin `references/vergi-davasi.md` dosyasında. İstinaf ve temyiz dilekçesi → `../kanun-yollari-dilekce/SKILL.md` (`references/idari-istinaf-temyiz.md`).
- Vergi dışındaki idari işlemler (imar, ruhsat, idari para cezası, kamulaştırma) → `../idare-davalari-imar/SKILL.md`.
- SGK prim borcu, İPC ve 5510 → `../sosyal-guvenlik-sgk/SKILL.md` (6183'e atıfla tahsil edilse bile esas orada).
- VUK m.359 kaçakçılık suçları (sahte / yanıltıcı belge) ceza yargılaması → bu beceri yalnız vergi tarhiyatı yönünü ve iki yargılamanın ilişkisini işaretler; savunma ve dilekçe → `../ceza-ve-infaz-dilekce/SKILL.md`.
- Gümrük vergileri ve gümrük uyuşmazlıkları (ithalde alınan vergiler, 4458 m.242 itirazı, gümrük uzlaşması) → `../gumruk-dis-ticaret/SKILL.md`.
- Yatırım teşvik belgesine bağlı KDV istisnası, KVK m.32/A indirimli kurumlar vergisi, 5746/4691 istisnaları → `../tesvik-yatirim/SKILL.md` (`references/destek-unsurlari-vergi-sgk-gumruk.md`, `references/ar-ge-tasarim-ve-teknopark.md`); tarhiyat ve vergi davası burada.
- VUK m.359 kaçakçılık suçunda TCK genel hükümleri (iştirak, zincirleme, zamanaşımı) → `../ceza-hukuku-suclar/SKILL.md`.
- Belediye gelirleri (emlak vergisi, ilan-reklam, harçlar) temel soruları bu becerinin kapsamındadır; belediye işleminin imar yönü `idare-davalari-imar`'da.
- Veraset ve intikal vergisinin miras hukuku yönü → `../aile-miras/SKILL.md`; vergisel yönü burada (oran ve istisna tutarları araçtan ya da RG'den, metne yazılmaz).
- İcra takibinde amme alacağının sırası ve konkordato kesişimi → `../icra-iflas/SKILL.md`.
- Şirket işlemlerinin (birleşme, bölünme, pay devri) ticaret hukuku yönü → `sirketler-ticaret`; vergisel sonucu burada.
- Meslek işi ve tutar hesabı (bordro, KDV tevkifatı, stopaj, damga, gecikme ve pişmanlık zammı, vergi cezası tutarı, SGK gecikme, amortisman, yılsonu) → `../muhasebe/SKILL.md` (`legal_calculate_tax`). Uyuşmazlıkta yol seçimi burada kalır; tutarlar oradan alınır.
- Kamu ihale sözleşmelerinde damga vergisi ve hakediş kesintileri → esas `hakedis` becerisinde; vergisel kesinti sorusu buraya gelebilir.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "213"`, `article_no: "376"`) çağır. Yanıt gelirse `soorgla ✓`; metinde "(Mülga:28/7/2024-7524/14 md.)" notunu görmen 7524 sonrası metnin geldiğini gösterir. 

Profili oku: rol (avukat / mali müşavir / mükellef / vergi dairesi görevlisi), taraf (mükellef, kanuni temsilci, ortak, idare).

**213 numarası çakışıyor:** `law_type` vermeden yapılan tarihçe çağrılarında 213 bir köy tüzel kişiliği kaydıyla karışıyor; `law_type: "Kanun"` ya da `statute_id: 69796` ver. 

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. İhbarname geldi, ne yapmalı (yol seçimi, süre, zamanaşımı, tebligat) | ihbarname, tarhiyat, uzlaşma mı dava mı, 30 gün, e-tebligat, zamanaşımı | `references/ihbarname-ve-yol-secimi.md` |
| B. Vergi cezaları, indirim, pişmanlık, kaçakçılık bağlantısı | vergi ziyaı, üç kat, usulsüzlük, özel usulsüzlük, 376, pişmanlık, tekerrür | `references/vergi-cezalari-ve-pismanlik.md` |
| C. Vergi davası (açma, YD, tahsilin durması, istinaf/temyiz sınırları) | vergi mahkemesi, dava açalım, yürütmeyi durdurma, istinaf, Danıştay, VDDK | `references/vergi-davasi.md` |
| D. Ödeme emri, haciz, tecil, kanuni temsilci / ortak sorumluluğu | ödeme emri, 15 gün, haciz, mal bildirimi, tecil, şirket borcu bana geldi, limited ortağı | `references/amme-alacagi-tahsili-6183.md` |
| E. Vergi incelemesi sürüyor; idare tarafı (vergi dairesi, uzlaşma komisyonu, rapor değerlendirme) | müfettiş geldi, inceleme tutanağı, defter ibrazı, takdir komisyonu, tarhiyat öncesi uzlaşma, komisyon üyesiyim | `references/vergi-incelemesi-ve-idare-tarafi.md` |
| F. KDV, GVK, KVK uygulama ve planlama | KDV indirimi, iade, tevkifat, sahte fatura, KKEG, örtülü sermaye, transfer fiyatlandırması, asgari kurumlar vergisi | `references/kdv-gvk-kvk-temel-sorular.md` |
| G. Özelge araştırması ve idari görüşün ağırlığı | özelge var mı, mukteza, GİB görüşü, sirküler, tebliğe aykırı | `references/ozelge-ve-idari-gorus.md` |
| H. "Bu değişiklik bizi etkiler mi", son vergi kanunları | yeni kanun, torba kanun, 7524, 7566, RG'de çıktı, yürürlük | `references/vergi-mevzuati-degisiklik-takibi.md` |

Bir olay birden fazla tipe giriyorsa (ör. sahte fatura nedeniyle cezalı tarhiyat: A + B + F; ödeme emrine dava: D + C) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa): mükellef mi, kanuni temsilci mi, ortak mı, vergi dairesi / uzlaşma komisyonu / tahsil dairesi görevlisi mi? İdare tarafında amaç hukuka uygun işlem kurmak ve dava riskini azaltmaktır; mükellef tarafı savunmasını kurma. İdare tarafı akışı her referans dosyasında "İdare tarafı" başlığıyla ayrıca yazılıdır.

**Ad-hoc doktrin sorusu** (ör. "usulsüzlük cezası uzlaşmaya konu olur mu?") geldiyse görüşme akışını atla: ilgili maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Süreleri en başta çek

Vergide süreler kısa ve birbirine bağlıdır; yol seçimi süreyle belirlenir. Her referans dosyasında **süre tablosu** vardır; her satırın dayanağını `legal_get_statute_article` ile çek.

- `legal_calculate_deadline` vergi kodlarını tanır: `iyuk_tax_lawsuit`, `tax_settlement_request`, `tax_penalty_reduction_376`, `tax_payment_order_objection`. Kodu olmayan süreyi elle hesapla (tebliğ günü sayılmaz, süre ertesi gün başlar), son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle. 
- **Elektronik tebligatta** tebliğ, iletildiği tarihi izleyen beşinci günün sonunda yapılmış sayılır; süreyi oradan başlat. 107/A 7587 ile yeniden yazıldı.  `legal_get_statute_article 213 107/A` boş dönüyor (harfli madde); metni 7587'den ya da `legal_search_statute_semantic` ile al.
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat** — `legal_get_statute_article` (`law_type: "Kanun"` ver):
- 213 VUK (usul, ceza, uzlaşma ek m.1-11), 6183 (tahsil), 2577 İYUK (m.7, 27, 45, 46), 3065 KDV, 193 GVK, 5520 KVK, 4760 ÖTV, 488 Damga, 492 Harçlar, 1319 Emlak, 7338 / 7524 / 7566 / 7587 / 7590 değişiklik kanunları.
- **Harfli ve mükerrer maddeler** (VUK 107/A, mükerrer 355, KVK 32/C, 6183 mükerrer 35) `legal_get_statute_article` ile çoğu zaman boş döner. Yollar: `legal_list_statute_articles` (`article_query` ile; ör. 6183 mükerrer 35 m.35 kaydının içinde geliyor) ya da `legal_search_statute_semantic` (`mevzuat_no` ile; ör. KVK m.32/C bu yolla geliyor). 
- **Madde tarihçesi:** `legal_get_statute_article_history` VUK ek m.1 için boş geliyor (`total_count: 0`). Değişikliği madde metnindeki "(Değişik/Mülga: …-7524/14 md.)" notlarından ve değiştiren kanunun RG metninden (`legal_get_official_gazette_document`) oku. 
- Olay tarihinde yürürlükteki metin gerekiyorsa (cezalı tarhiyatlar çoğu zaman 3-5 yıl öncesine ait) `legal_search_statute_versions` dene; sonuç yoksa değiştiren kanunun geçiş maddesine bak (ör. VUK geçici m.35) ve `[incele]`.

**Kararlar** — `legal_search_cases` `mahkeme: "danistay"`; vergi uyuşmazlıklarında içtihat birliği için **Vergi Dava Daireleri Kurulu** kararlarını ara (`daire: "Vergi Dava Daireleri Kurulu"`). Vergi dairelerinin iş bölümü (hangi vergi hangi dairede) **sabit yazılmaz**: eski YAML'lar aynı vergiyi (gelir/kurumlar) kimi 3., kimi 4. Daireye veriyordu. Daireyi seçmeden ara, dönen kararın dairesine bak; şüphede güncel Danıştay iş bölümü kararını iste. İş bölümü RG'de "Danıştay Başkanlık Kurulunun 2026/6 Sayılı Kararı" (RG 25.02.2026, 33179) başlığıyla bulunur (`query: "Danıştay Başkanlık Kurulu Kararı"`, `search_in: "title"`); araçtaki OCR metninde okunabilen vergi kısmı yalnız 9. D: gelir, kurumlar ve KDV (ithalde alınan KDV hariç) için Adana, Ankara, Antalya, Bursa, Diyarbakır, Erzurum, Gaziantep, İzmir, Kayseri, Konya ve Samsun BİM vergi dava dairelerinin kararlarına karşı temyiz; damga, emlak, belediye/il özel idare vergi-resim-harçları ve Harçlar Kanunu davaları. 3., 4. ve 7. D bölümleri OCR'da yok — diğer bölgeler için daireyi dönen karardan oku.  `legal_case_facets` vergi konularında güvenilir değil: sorgu sözcüklerinden birini içeren her kararı saydığı için idari dava dairelerini (5., 8., 10.) öne çıkarıyor. 
- **Kapsam uyarısı:** Danıştay kararlarının 2026 kapsamı çok seyrek (aynı sorguda 2024: ~80 bin, 2025: ~24 bin, 2026: 30 karar). "Son 3 yıl" emsalini 2024-2025'ten seç, 2026 boşluğunu notta yaz. 
- Bölge idare mahkemesi vergi dava dairesi kararları → `mahkeme: "bam"` (seyrek olabilir).
- AYM (mülkiyet hakkı, vergi cezalarında kanunilik, ödeme emri kesinliği) → `mahkeme: "anayasa"`.
- **Zorunlu adım:** her analizde son 3 yıldan en az bir Danıştay kararının tam metnini `legal_get_case_document` ile oku ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7); karşı oy ile çoğunluk gerekçesini ayır (vergi kararlarında karşı oy sık).

**İdari görüş** — GİB özelgeleri, sirkülerleri, iç genelgeleri ve genel yazıları **2026-10-31'den beri** `legal_search_admin_guidance` kapsamında (~19.500 belge; bkz. `references/ozelge-ve-idari-gorus.md`):
- Özelge: `belge_tur: "ozelge"`; tarih filtresi (`tarih_baslangic`/`tarih_bitis`) çalışır. `kurum` özelgeyi veren birimin **tam adıdır**: "Gelir İdaresi Başkanlığı" ağırlıkla 2011-2018 özelgelerini, 2019 sonrası özelgeler "<il> Vergi Dairesi Başkanlığı" ya da "<il> Defterdarlığı" adıyla gelir; güncel özelge için `kurum` vermeden `belge_tur` + tarih filtresiyle ara.
- Sirküler, iç genelge, genel yazı, gerekçe: `kurum: "Gelir İdaresi Başkanlığı"` ve `belge_tur: "sirkuler"` | `"ic_genelge"` | `"genel_yazi"` | `"gerekce"`. Sirkülerlerde `belge_tarihi` boş gelebilir; tarih filtresi bunları dışarıda bırakır, sirküleri tarihsiz ara.
- 🔴 **Özelge yalnız talep edeni bağlar** (VUK m.369 koruması özelgeyi alan mükellef içindir); başkasına verilmiş özelgeyi "idarenin görüşü" diye göster, bağlayıcı sayma. Aynı konuda farklı birimlerin çelişen özelgeleri olabilir; tarihe ve birime bak, Danıştay kararıyla karşılaştır.
VUK genel tebliğlerinin metinleri bu araçta değil: Genel tebliğleri `legal_search_official_gazette` (`search_in: "title"`, ör. "Vergi Usul Kanunu Genel Tebliği") ve `legal_search_statute_semantic` (`mevzuat_tur: "teblig"`) ile bul. 

**Sayısal parametreler** — beceri metnine hiçbir tutar, oran ve sınır yazılmaz:
- Usulsüzlük ve özel usulsüzlük ceza tutarları, uzlaşma eşiği, VUK'taki diğer tutarlar her yıl **yeniden değerleme oranıyla** güncellenir; kanun metninde parantez içinde güncel değer gösterilir. Madde metninden oku ve o yılın VUK genel tebliğiyle karşılaştır, `[doğrula]`.
- Gecikme zammı (6183 m.51), gecikme faizi (VUK m.112) ve tecil faizi oranları Cumhurbaşkanı kararıyla değişir. `legal_get_legal_interest_rates` aylık gecikme zammını (`gecikme_zammi_aylik`) başlangıç tarihi ve CBK dayanağıyla döndürür; tecil faizi **yok**. Tecil faizini ve geçmiş dönem oranlarını RG'den çek (`legal_search_official_gazette` "tecil faizi" / "gecikme zammı oranı", `sort_by: "date_desc"`). 
- İstinaf kesinlik ve temyiz sınırları İYUK m.45 ve m.46'da TL olarak yazılı ve her yıl yeniden değerlenir; davanın açıldığı tarihteki sınır esas alınır (İYUK ek m.1). Güncel yıl için `legal_get_social_parameters` (`iyuk_istinaf_siniri`, `iyuk_temyiz_siniri`); geçmiş yıl için RG ilanından al, `[doğrula]`.  
- Harç: `legal_calculate_court_fee`; vergi mahkemesi başvurma harcı ve Danıştay temyiz harcı `legal_get_social_parameters` (`harc_basvurma_asliye` "Asliye / İdare mahkemesi", `harc_temyiz_danistay`). Vergi davalarında nispi karar harcı uygulamasını `[doğrula]`.
- Kur (dövizli işlem, yurt dışı kazanç) → `legal_get_exchange_rate`; endeks (enflasyon düzeltmesi, değer artışı) → `legal_calculate_cpi_change` (ÜFE/TÜFE ayrımı için RG'den teyit, `[doğrula]`).

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

**Sıra (eski YAML'lardaki "vergi denetim mantığı", doğrulanarak korundu):** (1) tebligat usulü ve süre, (2) tarh ve ceza zamanaşımı, (3) tarhiyatın dayanağı ve raporun somut tespitleri, (4) hesap ve vergilendirme hataları, (5) ceza türü, kat ve indirim imkânı, (6) uzlaşma / indirim / dava seçimi ve parasal karşılaştırma `[incele]`.

**Orantılılık:** "30 gün ne zaman bitiyor?" iki cümle ister; tam dosya analizi değil.

### Adım 5 — Çıktı
Referans dosyasındaki iskeleti kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [mükellef / kanuni temsilci / idare] — [tarih]

### Sonuç (tek paragraf)
[Önerilen yol ve son gün — tek cümle neden]

### Kritik süreler
| İşlem | Başlangıç (tebliğ / e-tebliğ +5) | Süre | Son gün | Dayanak | Durum |

### Seçenekler ve parasal sonuçları
| Yol | Vergi aslı | Ceza | Gecikme faizi/zammı | Dava hakkı | Not |

### Bulgular
[her madde: işaret + kısa açıklama + atıf etiketi]

### Dayanaklar
[madde, Danıştay/VDDK kararı, tebliğ — her biri etiketli]

### Eksik bilgi
[açık sorular]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Avukat ya da mali müşavir olmayan kullanıcı şunları yapmadan önce ORTAK-KURALLAR.md §1 kapısını uygula: uzlaşma talebi vermek ya da uzlaşma tutanağı imzalamak, m.376 indirim başvurusu yapmak (dava hakkı düşer), pişmanlık dilekçesi vermek, vergi davası açmak, ödeme emrine dava açmak, tecil talep etmek, inceleme tutanağını imzalamak.

Uzlaşma ile dava arasındaki seçim tek yönlü kapıdır (uzlaşma vaki olmazsa yeniden istenemez; indirim isteyip dava açan indirimi kaybeder): her zaman `[incele]` ve parasal karşılaştırma tablosu.

**İdare tarafı:** vergi dairesi ya da uzlaşma komisyonu görevlisine "bu tarhiyat iptal edilir mi" sorusunda mükellefe yönelik dilekçe yazma; işlem dosyasının eksiklerini (tebliğ, rapor, gerekçe, zamanaşımı) ve dava riskini çıkar. İç değerlendirme ile mükellefe gidecek yazıyı ayır (ORTAK-KURALLAR.md §1 gönderim yeri kontrolü). Vergi mahremiyeti (VUK m.5) nedeniyle mükellef bilgisini dosya dışına taşıma. 

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Tarhiyat sonrası uzlaşma talebi, VUK 376 indirim başvurusu, düzeltme ve şikâyet dilekçesi | `../idari-ve-kurum-basvurulari/SKILL.md` (`references/vergi-uzlasma-indirim-duzeltme.md`) |
| Özelge talebi | `../idari-ve-kurum-basvurulari/SKILL.md` (`references/ozelge-talebi.md`) |
| Pişmanlık dilekçesi, tecil talebi, mal bildirimi üst yazısı, vergi dairesine cevap yazısı | Bu becerinin referans iskeleti + `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` biçimi |
| Vergi davası ve ödeme emrine karşı dava dilekçesi | İskelet `../idare-davalari-imar/references/idari-dava-dilekcesi.md` + `references/vergi-davasi.md` ek unsurları |
| Vergi mahkemesi kararına istinaf, BİM kararına temyiz | `../kanun-yollari-dilekce/SKILL.md` (`references/idari-istinaf-temyiz.md`) |
| AYM bireysel başvuru (mülkiyet, adil yargılanma, vergi cezası) | `../aym-aihm-basvuru/SKILL.md` |
| Avukatsız vatandaşın basit ödeme emri ya da emlak vergisi başvurusu | `../vatandas-basvurulari/SKILL.md` |
| VUK 359 kaçakçılık suçu soruşturmasında savunma | `../ceza-ve-infaz-dilekce/SKILL.md` |

Devrederken taşı: taraf ve rolü, ihbarname/ödeme emri künyesi ve tebliğ tarihi (e-tebliğse iletim tarihi), süre tablosu, seçilen yol ve gerekçesi, çekilmiş madde ve karar künyeleri (etiketleriyle), istem önerisi, açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** uzlaşma, dava ve ödeme emri süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Hesap araçları** (gecikme zammı ve gecikme faizi): araç kullanımı ve bilinen eksikler → [hesaplamalar/faiz](../hesaplamalar/references/faiz.md); tutarlar araçtan çekilir.
- **Genel mevzuat taraması, takip listesi, boşluk tablosu:** vergi dışı alanlarla birlikte genel tarama (alana özgü takip `references/vergi-mevzuati-degisiklik-takibi.md`'de kalır) → [mevzuat-takibi](../mevzuat-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Vergi hesabı, beyanname ya da mali tablo düzenlemez; mali müşavir ya da YMM işinin yerine geçmez.
- Ceza tutarını, gecikme zammı oranını, kesinlik ve temyiz sınırını, vergi oranını metinden söylemez; araçtan, madde metninden ya da RG'den çeker veya `[doğrula]` der.
- Danıştay daire iş bölümünü sabit yazmaz.
- GİB'e, vergi dairesine ya da mahkemeye başvuru göndermez; e-tebligat kutusunu kontrol etmez.

---

