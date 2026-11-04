---
name: idare-davalari-imar
description: >
  İdari yargıda iptal ve tam yargı davalarını, imar ve kamulaştırma
  uyuşmazlıklarını ele alır: dava süresi, idareye başvuru ve zımni ret,
  yürütmenin durdurulması, imar planı, ruhsat, yıkım ve imar cezası,
  kamulaştırma bedeli ve el atma; idari dava dilekçesi iskeleti de buradadır.
  Vergi davası ya da ihale şikâyet zinciri için değil, genel idari dava için.
  Kullanıcı "belediye yıkım kararı verdi", "imar cezası geldi", "plan
  değişikliğine dava açacağım", "idareye başvurdum cevap yok" dediğinde
  kullan.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: idari işlem/tebligat, encümen kararı, yapı tatil tutanağı, plan ilanı, kamulaştırma davetiyesi]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu beceri Anthropic claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC) deposundaki
litigation-legal eklentisinin chronology (olay ve tebliğ kronolojisi, boşluk listesi) ve
brief-section-drafter (alıntı sadakati, atıf etiketleme, zayıf argüman dürüstlüğü) becerilerindeki
iş akışı fikirlerinden Türk idari yargısına uyarlanmıştır; ABD usul kuralları alınmamıştır.
İdare hukuku içeriği upstream'de yoktur, sıfırdan yazılmıştır. Ayrıntı: NOTICE.md.
-->

# /idare-davalari-imar

İdari işlem ve eylemlere karşı idari yargı yolu (2577 İYUK), imar hukuku (3194 ve bağlantılı mevzuat) ve kamulaştırma (2942) için birleşik beceri. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- 2577 İYUK: iptal davası, tam yargı davası, genel dava süresi, idareye başvuru ve zımni ret (m.10-11), idari eylemden zarar için ön başvuru (m.13)
- Yürütmenin durdurulması, ivedi yargılama, hizmet kusuru ve kusursuz sorumluluk
- 3194 imar: imar planı ve plan değişikliğinin iptali, askı ilanı, parselasyon ve DOP (18. madde)
- Yapı ruhsatı, iskân, yapı tatil tutanağı, mühürleme, yıkım kararı, encümen imar para cezası, imar barışı ve yapı kayıt belgesi
- 6306 kentsel dönüşüm ve riskli yapı
- 2942 kamulaştırma: kamulaştırmanın iptali, bedel tespiti, acele kamulaştırma, kamulaştırmasız ve hukuki el atma
- İdari dava dilekçesi iskeleti (KVKK/SGK idari para cezası davaları dahil)
- Tipik cümleler: "ruhsat iptal edildi", "iptal davası dilekçesi", "yürütmeyi durdurma", "kamulaştırma tebligatı"
- Devir: vergi davası → vergi becerisi

## Kapsam

**Kapsar:** iptal ve tam yargı davalarının dava şartları ve süreleri; idareye başvuru, zımni ret, üst makama başvuru; yürütmenin durdurulması; görev ve yetki; ivedi yargılama; idarenin hizmet kusuru ve kusursuz sorumluluğu; imar planları, parselasyon, ruhsat, yapı kullanma izni, işyeri açma ruhsatı ve kapatma; kaçak yapı, yıkım, imar para cezası, imar barışı; kentsel dönüşüm (riskli yapı tespiti); kamulaştırma, acele kamulaştırma, kamulaştırmasız ve hukuki el atma; **idari dava dilekçesi iskeleti** (vergi dışı bütün idari işlemler ve idari para cezaları için).

**İki taraf:** Bu becerinin her referansında iki akış vardır:
- **İlgili / davacı tarafı** (vatandaş, şirket, malik, avukatı): süre, dava şartı, hukuka aykırılık iddiaları, YD.
- **İdare / kamu görevlisi tarafı** (belediye imar müdürlüğü, encümen, il müdürlüğü, hukuk müşaviri): işlemin usulüne uygun kurulması, tebliğ, savunma dilekçesi, karar sonrası uygulama (İYUK m.28). Eski sistemdeki `bureaucrat/*` görevleri bu akışa dönüştü; ayrı persona yoktur.

**Kapsamaz ya da yönlendirir:**
- Vergi, resim, harç ve vergi cezası davaları (2577 + 213 VUK, 30 gün), 6183 ödeme emri → `../vergi/SKILL.md`.
- Kamu ihalesi (4734, KİK, ihale işlemlerine dava) → `../kamu-ihale/SKILL.md`; ihale sözleşmesinin yürütülmesi, hakediş → `../hakedis/SKILL.md`. İvedi yargılama usulü burada anlatılır.
- Memur atama, disiplin, görevden uzaklaştırma (657, 4483) → `../kamu-personeli/SKILL.md`. Bu beceri yalnız genel iptal davası usulünü ve İYUK m.33 yetki kuralını verir.
- KVKK Kurul kararı ve İPC'nin esası → `../kvkk/SKILL.md`; SGK İPC ve işlemlerinin esası → `../sosyal-guvenlik-sgk/SKILL.md`. Bu iki beceri **dava dilekçesini buraya devreder** (`references/idari-dava-dilekcesi.md`).
- Kamulaştırma bedel tespiti ve tescil, kamulaştırmasız fiili el atma tazminatı, kat mülkiyeti ve arsa payı satışı (6306 m.6), tapu iptal-tescil → adli yargı; esas değerlendirme `../gayrimenkul-insaat/SKILL.md` (`references/kentsel-donusum-ozel-hukuk.md`, `references/tapu-iptali-ve-tescil.md`, `references/el-atma-ve-ecrimisil.md`), dilekçe `../hukuk-yargilamasi-dilekce/SKILL.md`. Kat karşılığı inşaat sözleşmesinin metni → `../sozlesme-incelemesi-tbk/SKILL.md`; teslim, ayıp, gecikme uyuşmazlığı → `../gayrimenkul-insaat/references/kat-karsiligi-insaat-uyusmazliklari.md`.
- İmar kirliliği suçu (TCK m.184), mühür bozma → yalnız işaret; ceza yargılaması → `../ceza-ve-infaz-dilekce/SKILL.md`.
- Kamu görevlisinin kişisel kusuru, hekim/hastane malpraktisinde adli/idari ayrım → `../tazminat-haksiz-fiil/SKILL.md` ile birlikte; idari yargı yolu buradadır.
- İstinaf ve temyiz (İYUK m.45-50, m.20/A temyiz) → `../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`.
- İdareye başvuru dilekçesi (m.10 istem, m.11 itiraz, m.13 ön başvuru, plan askısına itiraz), bilgi edinme → avukatsız vatandaş için `../vatandas-basvurulari/SKILL.md` (`kamu-kurumuna-dilekce.md`); kurum yazısı ve idarenin cevabı → `../idari-ve-kurum-basvurulari/SKILL.md` (`resmi-yazi-ve-olur.md`). Esas ve süre değerlendirmesi buradan taşınır.
- AYM bireysel başvuru (mülkiyet hakkı, makul süre) → `../aym-aihm-basvuru/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "2577"`, `article_no: "7"`) çağır. Yanıt gelirse `soorgla ✓`. Profili oku: rol (avukat / değil), taraf (ilgili / idare).

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Bir idari işleme karşı iptal davası (genel), süre, idareye başvuru, YD | işlem tebliğ edildi, ret cevabı, cevap vermediler, 60 gün, iptal davası, yürütmeyi durdurma, görevsizlik | `references/iptal-davasi-ve-sureler.md` |
| B. İdarenin eylem veya işleminden zarar — tam yargı | belediye yol çukuru, kamu hastanesi, kolluk eylemi, hizmet kusuru, idareden tazminat, ön başvuru, 1 yıl/5 yıl | `references/tam-yargi-ve-hizmet-kusuru.md` |
| C. İmar planı, parselasyon, ruhsat, iskân, işyeri ruhsatı, kentsel dönüşüm | plan değişikliği, askı ilanı, DOP, 18. madde uygulaması, ruhsat iptali, iskân vermiyorlar, işyeri mühürlendi, riskli yapı, rezerv alan | `references/imar-plani-ruhsat-ve-donusum.md` |
| D. Kaçak yapı, yıkım, imar para cezası, imar barışı | yapı tatil tutanağı, mühür, encümen kararı, yıkım, imar cezası, 32. madde, 42. madde, yapı kayıt belgesi | `references/kacak-yapi-yikim-ve-imar-cezasi.md` |
| E. Kamulaştırma | kamulaştırma davetiyesi, bedel tespiti, acele kamulaştırma, kamulaştırmasız el atma, plan kısıtlaması, hukuki el atma | `references/kamulastirma.md` |
| F. İdari dava dilekçesi (iptal / tam yargı / iptal + tam yargı; KVKK, SGK ve diğer İPC davaları dahil) | dava dilekçesi yaz, idare mahkemesine dava, İPC iptal davası | `references/idari-dava-dilekcesi.md` (önce ilgili A-E dosyası ya da devreden alan becerisi) |

Bir olay birden fazla tipe giriyorsa (ör. yıkım kararı + yıkım sonrası zarar: D + B; plan değişikliği + ruhsat iptali: C + A) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa): işlemin muhatabı/ilgili adına mı, idare adına mı? İdare tarafında soru tipi çoğu zaman "bu işlemi nasıl kurarız / savunmayı nasıl yazarız / mahkeme kararını nasıl uygularız"dır; referanslardaki "İdare tarafı" bölümünü kullan.

**Ad-hoc doktrin sorusu** (ör. "zımni ret kaç gün?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Süreleri en başta çek

İdari yargıda süre **kamu düzenindendir** ve ilk incelemede re'sen bakılır (İYUK m.14/3-e, m.15/1-b).  Her referansta **süre tablosu** vardır; her satırın dayanağını `legal_get_statute_article` ile çek.

- Genel dava süresi: **özel kanunda ayrı süre yoksa** Danıştay ve idare mahkemelerinde altmış gün; yazılı bildirimi izleyen günden başlar (İYUK m.7/1-2). Önce **özel süre** ara: 2942 m.14 (30 gün), 6306 (30 gün), 5510 m.102 (İPC itiraz reddinden sonra 30 gün), İYUK m.20/A ivedi yargılama (30 gün), m.20/B sınav (10 gün). 
- **2021 değişikliği:** idareye başvuruda zımni ret ve ön başvuru cevap süreleri 7331 sayılı Kanunla (RG 14.07.2021) **altmış günden otuz güne**, m.10'daki kesin cevap bekleme üst sınırı **altı aydan dört aya** indi. Başvuru tarihi 2021 öncesiyse eski metni uygula (Danıştay da başvuru tarihindeki metni uyguluyor).  7331 aynı değişikliği m.11/2 (üst makama başvuruda zımni ret) ve m.13/1'de (eylemden doğan zararda başvuruya cevap) de yaptı; geçici m.10: 7331'in yürürlüğünden önce m.10, 11, 13 uyarınca yapılmış başvurularda eski süreler uygulanır. 
- `legal_calculate_deadline` idari **dava açma** sürelerini tanımıyor ("iyuk_dava" → Kural bulunamadı); yalnız kanun yolu kodlarını (`iyuk_appeal`, `iyuk_cassation`) hesaplıyor. Dava süresini elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.
- **Kronoloji önce (upstream chronology'den):** işlem tarihi, tebliğ/öğrenme tarihi, askı-ilan tarihleri, idareye başvuru tarihleri, cevap/ret tarihleri, dava tarihleri tek tabloda; çelişen tarih varsa ikisini de yaz ve işaretle, sen çözme.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referansta konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat** — `legal_get_statute_article`:
- 2577 İYUK; 2576 (bölge idare/idare mahkemeleri); 2575 Danıştay K. m.24 (Danıştay'ın ilk derece davaları: Cumhurbaşkanı kararları, ülke çapındaki düzenleyici işlemler vb.). 
- 3194 İmar K. (`law_type: "Kanun"` ver), 6306, 2942, 2981, 3572 (işyeri açma), 5393/5216 (belediye/encümen yetkisi), 2863 (koruma kurulları), 5326 m.27/8.
- **Numara çakışması:** `6306` bir yönetmelikle çakışıyor (`legal_list_statute_articles` "ambiguous"); `statute_id: 69233` ya da `law_type: "Kanun"` ver. 
- **Harfli maddeler:** `legal_get_statute_article` İYUK m.20/A için boş dönebiliyor; `legal_list_statute_articles` (`law_no: "2577"`, `article_no: "20"`, `include_content: true`) 20, 20/A, 20/B, 20/C'yi birlikte getiriyor. 
- Madde tarihçesi: `legal_get_statute_article_history` 2577 için 2015'te duruyor (2021 7331 değişikliği yok). Değişiklik şüphesinde `legal_search_official_gazette` (`document_type: "kanun"`, sorgu "2577 sayılı İdari Yargılama Usulü Kanununun") ile değiştiren kanunu bul. 

**Kararlar** — `legal_search_cases`:
- `mahkeme: "danistay"`; olayı serbest cümleyle yaz. **Daireyi sabitleme.** Daireler arası iş bölümü **Danıştay Başkanlık Kurulu** kararıyla belirlenir (2575 m.27) ve Resmî Gazete'de yayımlanır; son görülen: **Başkanlık Kurulunun 2026/6 sayılı kararı (RG 25.02.2026/33179)**. Buna göre: **4. Daire** — 3194 ve diğer mevzuat uyarınca mühürleme, durdurma, **yıkım** kararları ve bunlara bağlı **para cezaları**; çevre, Boğaziçi, kültür ve tabiat varlıkları, gecekondu, kıyı, turizm; imar mevzuatından doğan hizmet kusuru/kusursuz sorumluluğa dayanan deprem ve afet zararları; **3572 işyeri açma ve çalışma ruhsatı** işlemleri. **6. Daire** — her tür ve ölçekte plan, arsa ve arazi düzenlemesi, ifraz-tevhit, imar durumu, **ruhsat ve kamulaştırma** işlemleri ve 4. Daireye ait olmayan diğer imar işleri. **10. Daire** — 5233, sağlık hizmetine ilişkin tam yargı, tüketici mevzuatı ve diğer dairelere ait olmayan uyuşmazlıklar. **13. Daire** — kamu ihale, rekabet, enerji, elektronik haberleşme, bankacılık, sermaye piyasası vb. Tam yargı davaları için tek bir daire yok; konuya göre dağılır. İş bölümü yıl içinde değişebilir: `legal_search_official_gazette` (`query: "Danıştay Başkanlık Kurulu Kararı"`, `search_in: "title"`, `sort_by: "date_desc"`) ile en yenisini çek; RG metni OCR'lı ve kısmi gelebilir, eksik kalan daireyi `[ARAŞTIRMA GEREKLİ]` diye işaretle. Arama yine de önce daire filtresiz yapılır, `legal_case_facets` ile dağılıma bakılır. 
- **Daire etiketi tutarsız:** aynı daire "6. Daire", "Danıştay 6. Daire Başkanlığı" ve "danistay" etiketleriyle geliyor; `daire` filtresi tek etiketi seçer, diğerlerini kaçırır. Daire filtresi yerine sorguya daire adını yazmak daha geniş sonuç verir `[incele]`. 
- İDDK kararları: sorguya "İdari Dava Daireleri Kurulu" ekle; içtihadı birleştirme kararları için `legal_search_official_gazette` (`query: "Danıştay İçtihatları Birleştirme Kurulu"`).
- **Bölge idare mahkemesi ve idare mahkemesi kararları araçta yok**: `mahkeme: "bam"` yalnız bölge **adliye** mahkemelerini, `mahkeme: "mahkeme"` adli yerel mahkemeleri getiriyor. İstinaf aşamasındaki BİM içtihadı için kullanıcıdan karar iste. 
- Görev uyuşmazlıkları (adli/idari): Uyuşmazlık Mahkemesi kararları `legal_search_admin_guidance` içinde RG'de yayımlanmış toplu karar olarak (çoğu 2000-2014) çıkıyor; güncel UM kararı için `legal_search_official_gazette` (`query: "Uyuşmazlık Mahkemesi"`, `sort_by: "date_desc"`).
- AYM norm denetimi ve bireysel başvuru (mülkiyet hakkı) → `mahkeme: "anayasa"`.
- **Zorunlu adım:** her analizde son 3 yıldan en az bir Danıştay kararının tam metnini `legal_get_case_document` ile oku ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7). **Kapsam uyarısı:** araçtaki Danıştay kararları 2025 ortasından sonra çok seyrek (2025-07 sonrası ~5.200, 2026'da 30 karar); "son 3 yıl" pratikte 2023-2025 demektir, notta yaz. 

**İdari görüş ve kurul kararları** — `legal_search_admin_guidance`: **Çevre, Şehircilik ve İklim Değişikliği Bakanlığı** genelge, yönerge ve Merkez Komisyon ilke kararları artık var (~490 belge; `kurum: "Çevre, Şehircilik ve İklim Değişikliği Bakanlığı"`, gerekirse `belge_tur: "genelge"` / `"yonerge"` / `"ilke_karar"`; ör. Genelge 2015/09 "Sağlık ve Eğitim Yapılarında Emsal Hesabı", ıslah imar planı genelgeleri). Çoğu eski tarihli; uygulanan yönetmelik değiştiyse genelgenin dayanağını kontrol et `[incele]`.  Tabiat Varlıklarını Koruma Merkez Komisyonu ilke kararları, koruma bölge kurulu kararları ve eski Uyuşmazlık Mahkemesi kararları var. 2026-10-31 yüklemesiyle RG'de yayımlanan diğer kurul kararları da girdi: sit ve koruma alanında `kurum: "Kültür Varlıklarını Koruma Yüksek Kurulu"` (ilke kararları), enerji ve lisans işlerinde EPDK, özelleştirmede Özelleştirme Yüksek Kurulu. Tapu ve Kadastro GM genelgeleri ve Kentsel Dönüşüm Başkanlığı görüşleri hâlâ yok; Bakanlığın tek tek başvurulara verdiği yazılı imar görüşleri de yok (yalnız genelge/yönerge/ilke kararı). Danıştay kararı yerine geçmez. 

**Sayısal parametreler** — beceri metnine tutar, oran, eşik yazılmaz:
- İmar para cezası birim tutarları ve artırım oranları 3194 m.42 metninde **taban** olarak yazılıdır ve her yıl VUK mük. m.298 yeniden değerleme oranıyla artırılır; hesabı madde metni + o yılın oranı (kullanıcıdan ya da Bakanlık duyurusundan) ile göster, `[doğrula]`. 
- İdari yargı kesinlik ve temyiz sınırları (İYUK m.45-46) ek m.1'e göre her yıl yeniden değerlenir; 7550 ile (RG 04.06.2025) **davanın açıldığı tarihteki** sınır esas alınır. Tutar maddeden ve yıllık değerlemeden; `legal_get_social_parameters` bu sınırı döndürmüyor. 
- Harç: `legal_calculate_court_fee` idari yargı harçlarını tanımıyor (yalnız adli türler); harcı kullanıcıdan ya da Harçlar Kanunu tarifesinden iste, `[doğrula]`. 
- Faiz (tam yargı): yasal faiz için `legal_get_legal_interest_rates` 7589 sonrasını yanlış verebilir; idarenin karar sonrası ödeyeceği faiz İYUK m.28/6'ya göre 6183 m.48 tecil faizidir — oranı araçtan değil ilgili Cumhurbaşkanı kararından al, `[incele]`. 

### Adım 4 — Analiz
İlgili referanstaki kontrol listesini sırayla yürüt; her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. İptal davasında hukuka aykırılık **beş unsur** üzerinden kurulur (yetki, şekil, sebep, konu, maksat; İYUK m.2/1-a)  ve idari yargının **yerindelik denetimi yapamayacağı** (m.2/2) hatırlanır: "işlem yerinde değil" argümanı değil, "hukuka aykırı" argümanı kurulur.

**Zayıf argüman dürüstlüğü (upstream brief-section-drafter'dan):** dava açmanın sonucu belirsizse ya da en güçlü iddia usule ilişkinse (ör. tebliğ eksikliği yalnız süreyi kurtarır, işlemi sakatlamaz) bunu açıkça yaz; avukat hangi iddiayı öne çıkaracağına karar verir.

### Adım 5 — Çıktı
Referans dosyasındaki iskeleti kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [ilgili / idare] — [tarih]

### Sonuç (tek paragraf)
[Dava açılabilir / önce idareye başvuru şart / süre geçmiş — tek cümle neden]

### Kronoloji ve süre tablosu
| Olay | Tarih | Süre | Son gün | Dayanak | Durum |

### Dava şartları
| Şart | Durum | Not |  (görev, yetki, ehliyet/menfaat, kesin ve yürütülmesi gereken işlem, süre, husumet, idari merci tecavüzü)

### Hukuka aykırılık iddiaları
| # | Unsur | İddia | Dayanak | Güç (🟢/🟡/🟠) |

### Yürütmenin durdurulması
[telafisi güç zarar + açık hukuka aykırılık; teminat]

### Dayanaklar
[madde, karar — etiketli]

### Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Avukat olmayan kullanıcı şunlardan önce ORTAK-KURALLAR.md §1 kapısını uygula: idari dava açmak, YD istemek, idareye m.11 itirazı ya da m.13 ön başvurusu yapmak (süreyi etkiler), plan askısına itiraz, kamulaştırma uzlaşma tutanağı imzalamak, yapı kayıt belgesine dayanmak. İdare tarafında: yıkım kararı, encümen cezası, ruhsat iptali gibi işlemlerin metnini yayımlamadan önce hukuk müşavirliği onayı.

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| İdare mahkemesi / Danıştay **dava dilekçesi** (iptal, tam yargı, iptal + tam yargı, İPC iptali), YD istemi, cevaba cevap (ikinci dilekçe) | Bu beceri: `references/idari-dava-dilekcesi.md` |
| İdarenin **savunma dilekçesi** | Bu beceri: `references/idari-dava-dilekcesi.md` (idare tarafı iskeleti) |
| YD kararına itiraz (7 gün), istinaf, temyiz | `../kanun-yollari-dilekce/SKILL.md` (`idari-istinaf-temyiz.md`); YD itirazı iskeleti bu becerinin dilekçe dosyasında |
| İdareye istem (m.10), üst makama itiraz (m.11), ön başvuru (m.13), plan askısına itiraz, riskli yapı tespitine itiraz | Avukatsız vatandaş → `../vatandas-basvurulari/SKILL.md`; avukat/şirket → bu becerideki kısa iskeletler + `../idari-ve-kurum-basvurulari/SKILL.md` biçim kuralları |
| Encümen kararı, yapı tatil tutanağı, makam oluru (idare tarafı) | `../idari-ve-kurum-basvurulari/SKILL.md` (`resmi-yazi-ve-olur.md`, `tutanak.md`); içerik kontrol listesi bu beceriden |
| Kamulaştırma bedel tespiti/artırım, kamulaştırmasız el atma, kat mülkiyeti davaları (adli yargı) | `../hukuk-yargilamasi-dilekce/SKILL.md` |
| AYM bireysel başvuru | `../aym-aihm-basvuru/SKILL.md` |

Devrederken taşı: taraf (ilgili/idare), işlem ve tebliğ künyesi, kronoloji ve süre tablosu, dava şartları tablosu, hukuka aykırılık iddiaları, çekilmiş madde ve karar künyeleri (etiketleriyle), istem önerisi (iptal, tazminat kalemleri, YD), açık sorular.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** dava açma, idareye başvuru ve zımni ret süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Kronoloji / unsur-delil tablosu:** kronoloji ve süre tablosu belge çoksa → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).

## Bu beceri ne yapmaz

- Danıştay daire iş bölümünü, parasal sınırları, harç ve imar cezası tutarını metinden söylemez; çeker ya da `[doğrula]` der.
- Teknik imar ölçümü (emsal, TAKS/KAKS, gabari, inşaat alanı) yapmaz; tutanak ve proje verisini karşılaştırır, ölçüm farkını bilirkişiye bırakır.
- Dilekçeyi UYAP'a yüklemez, idareye başvuru göndermez.

---

