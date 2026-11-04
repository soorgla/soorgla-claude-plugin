---
name: tesvik-yatirim
description: >
  Yatırım teşvikleri ve devlet destekleri için çalışır: teşvik belgesi
  başvurusu ve uygunluk, bölge ve program seçimi, revize, süre uzatımı,
  tamamlama vizesi, belge iptali ve geri alma; Ar-Ge ve tasarım merkezi,
  teknopark, KOSGEB ve kalkınma ajansı destekleri, teşvikli fizibilite.
  Kullanıcı "teşvik belgesi alabilir miyiz", "tamamlama vizesi", "teşvik
  belgemiz iptal edildi", "teknokent istisnası" dediğinde kullan. SGK prim
  teşvikleri sosyal-guvenlik-sgk'da; vergi tarhiyatı ve dava vergi'de; dilekçe
  idari-ve-kurum-basvurulari'nda yapılır.
argument-hint: "[yatırımı anlatın ya da belgeyi ekleyin: teşvik belgesi, Bakanlık yazısı, iptal/müeyyide bildirimi, vergi ihbarnamesi, fizibilite verisi]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /tesvik-yatirim

Yatırım teşvik sistemi (9903 sayılı Cumhurbaşkanı Kararı ve uygulama tebliği), teşvik belgesinin hayat döngüsü (başvuru → revize → tamamlama vizesi → iptal/müeyyide), destek unsurlarının vergi ve SGK yönü, Ar-Ge/tasarım merkezi ve teknoloji geliştirme bölgesi teşvikleri, KOSGEB/kalkınma ajansı gibi diğer destekler ve teşvikli fizibilite için birleşik alan becerisi. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

**Bu alanın temel tuzağı:** teşvik mevzuatı sık ve büyük değişir. 2012/3305 sayılı BKK sistemi (ve Cazibe Merkezleri Programı) **9903 sayılı Karar ile kaldırıldı**; eski "1-6. bölge, öncelikli yatırıma 5. bölge desteği" anlatımı bugünkü sistemi anlatmaz. Ama 9903 öncesi belgelere **dayandıkları eski karar** uygulanmaya devam eder. Her dosyada önce "belge hangi karara dayanıyor?" sorusunu sor. 

---

## Ne zaman kullanılır

- Yatırımlarda Devlet Yardımları Hakkında Karar (9903 sayılı CB Kararı, Türkiye Yüzyılı Kalkınma Hamlesi, Teknoloji/Yerel Kalkınma/Stratejik Hamle, öncelikli ve hedef yatırımlar, bölgesel teşvik).
- Yatırım teşvik belgesi başvurusu, E-TUYS, revize, süre uzatımı, tamamlama vizesi, belge iptali ve 6183 ile geri alma.
- Gümrük muafiyeti, KDV istisnası (3065 m.13/d), vergi indirimi (KVK 32/A), faiz/kâr payı ve makine desteği, sigorta primi işveren hissesi desteği, yatırım yeri tahsisi.
- Ar-Ge ve tasarım merkezi (5746), teknopark (4691), KOSGEB ve kalkınma ajansı, proje bazlı destek.
- Fizibilite ve teşvikli nakit akışı.
- Tipik cümleler: "hangi bölge", "Ar-Ge merkezi", "KOSGEB hibesi", "teşvikli IRR".

## Kapsam

**Kapsar:** 9903 sayılı Karar kapsamındaki teşvik sistemleri ve uygunluk taraması; teşvik belgesi başvurusu, eksik tamamlama, makine-teçhizat listeleri, revize, yatırım konusu/yer değişikliği, devir, sabit kıymet satışı ve kiralanması, süre ve ek süre, mücbir sebep, tamamlama vizesi; destek unsurları (gümrük vergisi muafiyeti, KDV istisnası, vergi indirimi, faiz veya kâr payı desteği, makine desteği, sigorta primi işveren hissesi ve sigorta primi desteği, yatırım yeri tahsisi) ve birbirleriyle/diğer kamu destekleriyle birleşme yasağı; belge iptali ve kısmi müeyyide, desteklerin 6183 ile geri alınması; Ar-Ge ve tasarım merkezi (5746), teknoloji geliştirme bölgesi (4691) teşvikleri; KOSGEB, kalkınma ajansı, proje bazlı destek ve finansman programları (kısa); teşvikli yatırımın fizibilitesi ve nakit akışına teşvik etkisi; teşvik mevzuatı değişiklik takibi. **İdare tarafı:** Bakanlık/ekspertiz görevlisi, vergi dairesi ve SGK görevlisinin bakışı her referansta ayrı başlıkla yazılıdır.

**Kapsamaz ya da yönlendirir:**
- İstihdama bağlı **SGK prim teşvikleri** (4447 geçici maddeleri, 5510 m.81/ı, kadın-genç-engelli teşvikleri), yersiz teşvik geri alımı ve SGK itirazı → `../sosyal-guvenlik-sgk/SKILL.md` (`references/sgk-uyum-ve-itiraz.md`). Teşvik belgesine bağlı **sigorta primi işveren hissesi desteği** (9903 m.18, 5510 ek m.2) bu becerinin konusudur; SGK'daki uygulama ve itiraz yönü orada.
- Teşvik ihlali nedeniyle yapılan **vergi tarhiyatı** (KDV, kurumlar vergisi), uzlaşma, vergi davası, ödeme emri → `../vergi/SKILL.md`. Bu beceri tarhiyatın dayanağını (belge iptal edildi mi, geri alındı mı, vize yapıldı mı) çıkarır, vergi yolunu orası yürütür.
- Gümrük vergisi muafiyetinin gümrük usulü, teminat ve gümrük uyuşmazlığı → `../gumruk-dis-ticaret/SKILL.md` (`references/gumruk-rejimleri-ve-serbest-bolge.md`).
- Bakanlık işlemine karşı **iptal davası dilekçesi** → `../idare-davalari-imar/references/idari-dava-dilekcesi.md`; esas ve süre bu becerinin `references/iptal-muyyide-ve-geri-alma.md` dosyasında.
- Bakanlığa başvuru yazısı, revize/süre uzatımı/mücbir sebep talebi, cevap yazısı → `../idari-ve-kurum-basvurulari/SKILL.md` (`references/resmi-yazi-ve-olur.md` biçimi).
- **Fizibilite raporu metni** (yönetici özeti, pazar, teknik analiz, SWOT) → `../idari-ve-kurum-basvurulari/references/yatirim-fizibilite-raporu.md`; teşvik bölümü ve finansal model bu becerinin `references/fizibilite-ve-tesvikli-nakit-akisi.md` dosyasında.
- Yatırım şirketinin kuruluşu, sermaye, birleşme-bölünme (teşvik belgesinin devriyle kesişir) → `../sirketler-ticaret/SKILL.md`.
- Yatırım yeri tahsisi sonrası imar, ruhsat, kamulaştırma → `../idare-davalari-imar/SKILL.md`.
- Teşvik belgesiyle kurulan yatırımda sahte belge, resmî belgede sahtecilik, nitelikli dolandırıcılık iddiası → `../ceza-hukuku-suclar/SKILL.md` (`references/bilisim-sahtecilik-ve-kamu-idaresi-suclari.md`, `references/malvarligi-suclari.md`); savunma metni `../ceza-ve-infaz-dilekce/SKILL.md`.
- Kamu kurumunun yatırım harcaması, Sayıştay denetimi → `../kamu-mali-denetim-sayistay/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil

`legal_get_statute_article` (`law_no: "5746"`, `law_type: "Kanun"`, `article_no: "6"`) çağır. Yanıt gelirse `soorgla ✓`. 

Profili oku: rol (avukat / mali müşavir-YMM / teşvik danışmanı / yatırımcı / Bakanlık veya vergi dairesi görevlisi), taraf (yatırımcı, finansal kiralama şirketi, devralan, idare).

**9903 sayılı Karar madde aracıyla çekilemez.** Katalogda kaydı var ama bölütlenmemiş (`article_count: 0`, `parse_success: false`); metni yalnız Resmî Gazete belgesinden okunur (PDF, OCR'lı; Türkçe karakterler bozuk gelir, ~105 bin karakter, `offset` ile parça parça). Uygulama Tebliği 2025/1 de katalogda tek madde; tam metni RG'den (`.htm`, temiz). 

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Hangi teşvikten yararlanırım; sistem, bölge, sektör, asgari yatırım uygunluğu | teşvik alabilir miyiz, hangi bölge, öncelikli yatırım, hedef yatırım, Teknoloji Hamlesi, Stratejik Hamle, NACE, asgari sabit yatırım | `references/tesvik-sistemi-ve-uygunluk.md` |
| B. Teşvik belgesinin hayat döngüsü: başvuru, eksik, revize, süre, ek süre, devir, satış, kiralama, yer değişikliği, tamamlama vizesi, yükümlülük takvimi | E-TUYS, müracaat, revize, süre uzatımı, tamamlama vizesi, ekspertiz, YMM raporu, devir, makine satışı, ilerleme raporu | `references/tesvik-belgesi-sureci-ve-yukumlulukler.md` |
| C. Destek unsurlarının içeriği, vergi/SGK/gümrük yönü, birleşme yasağı | KDV istisna belgesi, gümrük muafiyeti, indirimli kurumlar vergisi, yatırıma katkı, faiz desteği, makine desteği, SGK işveren hissesi, yatırım yeri tahsisi, hibe ile birlikte | `references/destek-unsurlari-vergi-sgk-gumruk.md` |
| D. Belge iptali, kısmi müeyyide, desteklerin geri alınması, dava yolu; idare tarafı | teşvik belgesi iptal edildi, müeyyide, geri alma, 6183, gecikme zammı, tarhiyat, iptal davası, ekspertiz raporu | `references/iptal-muyyide-ve-geri-alma.md` |
| E. Ar-Ge/tasarım merkezi ve teknopark teşvikleri | Ar-Ge merkezi, tasarım merkezi, Ar-Ge indirimi, stopaj teşviki, teknokent, TGB kazanç istisnası, merkez dışı çalışma, 13/m KDV | `references/ar-ge-tasarim-ve-teknopark.md` |
| F. KOSGEB, kalkınma ajansı, proje bazlı destek, finansman programları, nitelikli hizmet merkezi | KOSGEB, hibe, kalkınma ajansı çağrısı, proje bazlı, TSP belgesi, öncelikli finansman belgesi | `references/kosgeb-ajans-ve-diger-destekler.md` |
| G. Fizibilite, IRR/NPV, geri ödeme, teşvikin nakit akışına etkisi | fizibilite, IRR, NPV, geri ödeme süresi, hassasiyet, teşvikli/teşviksiz karşılaştırma | `references/fizibilite-ve-tesvikli-nakit-akisi.md` |
| H. "Yeni karar/tebliğ bizi etkiler mi", değişiklik takibi | yeni teşvik kararı, tebliğ değişti, öncelikli ürün listesi, 7555, 7582, yürürlük | `references/tesvik-mevzuati-degisiklik-takibi.md` |

Bir olay birden fazla tipe giriyorsa (ör. tamamlama vizesi yapılmadı, belge iptal edildi, vergi dairesi KDV tarh etti: B + D + C ve `vergi`) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa): yatırımcı mı, finansal kiralama şirketi mi, belgeyi devralan mı, yoksa Bakanlık/ekspertiz görevlisi, vergi dairesi ya da SGK görevlisi mi? İdare tarafında amaç işlemin hukuka uygun kurulması ve dava riskinin azaltılmasıdır; yatırımcı savunması kurma.

**Ad-hoc soru** (ör. "teşvik belgesi almadan aldığımız makine kapsama girer mi?") geldiyse görüşme akışını atla: hükmü çek, kısa cevap ver, etiketle. (Cevap: girmez — müracaat tarihinden önceki harcama kapsama alınmaz.) 

### Adım 2 — Hangi karar, hangi tarih?

1. Belgenin dayandığı kararı belirle: 9903 (müracaat 30.05.2025 ve sonrası) mı, 2012/3305 mü, 2018/11201 Cazibe Merkezleri mi, proje bazlı (2016/9495) mı? Sonuçlandırılmamış eski müracaatlar müracaat tarihindeki karara göre sonuçlanır; yatırımcı yeni karara göre değerlendirme isteyebilir. 
2. Vergi indiriminde **belge alım tarihine** bak: KVK 32/A'nın 7555 ile değişen metni, 16.06.2025'ten önce başvurusu yapılmış ve reddedilmemiş olanlar hariç, 24.07.2025'ten itibaren alınan belgelere uygulanır. 
3. Tutar, oran, tavan, asgari yatırım ve destek süreleri **beceri metninde yoktur**: Karardan (EK-2 bölgeler, EK-3 sektör şartları, m.15-20 oran ve tavanlar, m.18 süre tablosu) ve Bakanlığın yeniden değerleme ilanından çek. Karardaki TL tutarları her yıl yeniden değerleme oranıyla güncellenir ve Bakanlık internet sitesinde ilan edilir; RG'de ayrı ilan olmayabilir `[doğrula]`. 

### Adım 3 — Süreleri en başta çek

Teşvikte kayıp çoğu zaman süreden gelir: tamamlama vizesi müracaatı, teminatla ithalatta belge ibrazı, sabit kıymet satış yasağı, ilerleme raporu. Her referansta **süre tablosu** vardır.

- `legal_calculate_deadline` teşvik sürelerini tanımaz (kural seti yok; idari dava için `iyuk_lawsuit`, `iyuk_tax_lawsuit`, `iyuk_implicit_rejection_*` kodları var); teşvik süresini madde metninden hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle. 
- Bakanlık işlemine karşı iptal davası: idare mahkemesinde 60 gün, yazılı bildirimi izleyen günden; teşvik ihlaline dayalı vergi tarhiyatına karşı vergi mahkemesinde 30 gün. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.

### Adım 4 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarındaki hayalî indeks filtrelerinin (`YATIRIM_TEŞVIK_KARARI`, `KOSGEB_DESTEK`, `KALKINMA_AJANSI_GUIDE`, `IHRACAT_DESTELERI`, `mevzuat_vector`) karşılığı aşağıdaki çağrılardır. Eski YAML'lar yargı kararı aramayı kapatmıştı (`karar_danistay: enabled: false`); bu beceride **iptal, geri alma ve tarhiyat** sorularında Danıştay araması zorunludur.

**Karar ve tebliğ (RG):**
```
legal_search_official_gazette  query: "Yatırımlarda Devlet Yardımları Hakkında Karar"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "Yatırımlarda Devlet Yardımları Hakkında Kararın Uygulanmasına İlişkin Tebliğ"  search_in: "title"  sort_by: "date_desc"
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2025/05/20250530-2.pdf"  offset: 0 | 50000 | 80000  max_chars: 30000   # 9903 tam metin (OCR)
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2025/06/20250621-14.htm"   # Tebliğ 2025/1
legal_search_official_gazette  query: "Öncelikli Ürün Listesi Tebliği"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "9903 sayılı Cumhurbaşkanı Kararı"  date_from: "<son tarama>"  sort_by: "date_desc"   # Karara atıf yapan yeni tebliğ/yönetmelikler
```
9903 sonrası Karar'ı değiştiren bir CB kararı RG başlık aramasında bulunmadı (yalnız Tebliğ 2025/1'i değiştiren Tebliğ 2026/1). Her dosyada bunu yeniden ara. 

**Kanun maddeleri** (`legal_get_statute_article`, `law_type: "Kanun"`): 5746 (m.2-4, 6), 4691 (m.3, 8, 10, ek m.2-3; geçici maddeler), 3065 m.13/d ve 13/m, geçici m.37, 5510 ek m.2, 6745, 6015, 4875 ek m.1, 2577 m.7. **Harfli ve geçici maddeler boş dönebilir:** KVK 32/A ve 4691 geçici m.2 `legal_get_statute_article` ile boş; 32/A `legal_search_statute_semantic` (`mevzuat_no: "5520"`) ile, 4691 geçici m.2 `legal_list_statute_articles` (`statute_id: 69468`, `article_kind: "gecici"`, `article_no: "1"`, `include_content: true`) ile geliyor (geçici m.1 kaydının içinde). 6745 m.80 da boş. 

**Kararlar** — `legal_search_cases` `mahkeme: "danistay"`. Teşvik belgesine dayalı vergi ve gümrük uyuşmazlıkları vergi dava dairelerinde (dönen kararlarda 3., 7., 9. Daire), Bakanlık işlemine karşı iptal davaları idari dava dairelerinde görülür; **daireyi sabit yazma**, dönen kararın dairesine bak. Danıştay 2026 kapsamı çok seyrek; "son 3 yıl" emsalini 2023-2025'ten seç.  Zorunlu adım: son 3 yıldan en az bir Danıştay kararının tam metnini `legal_get_case_document` ile oku, alıntı-önerme kontrolü yap (ORTAK-KURALLAR.md §7).

**İdari görüş** — `legal_search_admin_guidance`:
- **GİB özelgeleri bu alanda zengin.** `kurum` filtresi TAM ADLA ve özelgeyi veren birime göre: `"Gelir İdaresi Başkanlığı"` (merkez; teşvik/32/A özelgeleri ağırlıkla 2011-2018), `"İstanbul Defterdarlığı"`, `"Ankara Defterdarlığı"`, `"Ankara Vergi Dairesi Başkanlığı"`, `"İzmir Vergi Dairesi Başkanlığı"`, `"Konya Defterdarlığı"` (2023-2026 özelgeleri). Yeni özelge için `kurum` vermeden `tarih_baslangic: "2024-01-01"` kullan; `belge_tur: "ozelge"`. 
- **Sanayi ve Teknoloji Bakanlığı görüşü, Teşvik Uygulama GM yazıları, KOSGEB ve kalkınma ajansı kararları yok** (`kurum: "Sanayi ve Teknoloji Bakanlığı"` → 0). Bakanlık yazısını kullanıcıdan iste `[kullanıcı verdi]`. 
- Rekabet Kurulu kararları teşvik/devlet yardımı konusunda sonuç vermiyor (yalnız 4054 ihlal kararları). 

**Sayısal parametreler** — beceri metnine hiçbir tutar, oran, tavan, asgari yatırım, destek süresi yazılmaz:
- Karar tutarları: Karar metni + Bakanlığın yıllık yeniden değerleme ilanı `[doğrula]`; `legal_get_social_parameters` bunları **döndürmez** (teşvik kalemi yok). 
- Faiz/kâr payı desteği TCMB bir hafta vadeli repo ihale faiz oranına bağlı; oranı `legal_get_legal_interest_rates` (politika faizi) ile çek (`politika_faizi` satırı başlangıç tarihiyle geliyor; destek dönemine uyduğunu kontrol et) `[doğrula]`.
- Geri almada 6183 m.51 gecikme zammı oranı: güncel oran `legal_get_legal_interest_rates` → `gecikme_zammi_aylik` (dayanak CBK ile); geçmiş dönem oranları için RG'den çek (`legal_search_official_gazette` "gecikme zammı oranı", `sort_by: "date_desc"`).
- Döviz cinsinden makine ve döviz kredisi → `legal_get_exchange_rate`; yeniden değerleme ve TÜFE karşılaştırması → `legal_calculate_cpi_change` (yeniden değerleme oranı ÜFE bazlıdır, araç yalnız TÜFE verir `[doğrula]`).

### Adım 5 — Analiz

İlgili referans dosyasındaki kontrol listesini sırayla yürüt; her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

**Sıra (eski YAML'lardaki "teşvik filtreleri" ve "finansal model" mantığı, 9903'e göre yeniden kuruldu):** (1) belgenin dayandığı karar ve tarih, (2) yatırım konusu desteklenebilir mi (EK-3, hariç tutulan konular, il/bölge), (3) hangi sistem/program, (4) destek unsurları ve birleşme yasağı, (5) süreler ve yükümlülük takvimi, (6) risk: iptal/müeyyide/geri alma, (7) parasal etki — kullanıcının verdiği rakamla `[incele]`.

**Orantılılık:** "Tamamlama vizesine ne zamana kadar başvurmalıyız?" iki cümle ister; tam teşvik raporu değil.

### Adım 6 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8; Güncellik satırına: "9903 metni RG'den okundu, son değişiklik araması AAAA-AA-GG")

## [Konu]: [yatırımcı / idare] — [tarih]

### Sonuç (tek paragraf)

### Belgenin dayanağı
| Belge no / tarih | Dayandığı karar | Sistem/program | Yatırım cinsi | Yer (il/ilçe/OSB) | Vize durumu |

### Kritik süreler ve yükümlülükler
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |

### Destek unsurları
| Unsur | Var mı | Şart | Risk | Dayanak |

### Bulgular
### Dayanaklar (Karar maddesi, tebliğ, kanun, Danıştay kararı, özelge — etiketli)
### Eksik bilgi

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 7 — "Taslaktır" kapısı

Avukat, YMM ya da teşvik danışmanı olmayan kullanıcı şunları yapmadan önce ORTAK-KURALLAR.md §1 kapısını uygula: teşvik belgesi müracaatını göndermek, revize/süre uzatımı/yatırım konusu değişikliği istemek, tamamlama vizesi müracaatı yapmak, belge kapsamı makineyi satmak/kiralamak/devretmek, belge devrini imzalamak, iptal işlemine dava açmak, indirimli kurumlar vergisini beyannameye yansıtmak.

**Tek yönlü kapılar:** tamamlama vizesi yapılmış belgenin bütün olarak devri uygun görülmez; vize müracaatından itibaren iki yıl dolmadan sabit kıymet satışı izne tabidir ve izinle satışta destekler geri alınır; belge müracaatından önceki harcama sonradan kapsama alınamaz. Bunlarda her zaman `[incele]`. 

### Adım 8 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Bakanlığa revize, süre uzatımı, mücbir sebep, devir izni, satış/kiralama izni, yatırım yeri değişikliği talebi; müeyyide yazısına cevap | `../idari-ve-kurum-basvurulari/SKILL.md` (`references/resmi-yazi-ve-olur.md` biçimi) — içerik bu becerinin referansından |
| Belge iptali / kısmi müeyyide / geri alma işlemine karşı iptal davası | `../idare-davalari-imar/references/idari-dava-dilekcesi.md` + `references/iptal-muyyide-ve-geri-alma.md` ek unsurları; istinaf/temyiz → `../kanun-yollari-dilekce/SKILL.md` |
| Teşvik ihlaline dayalı KDV/kurumlar vergisi tarhiyatı, uzlaşma, vergi davası | Esas `../vergi/SKILL.md`; dilekçe orada gösterilen yollardan |
| Özelge talebi (KDV istisnası, 32/A, Ar-Ge indirimi) | `../idari-ve-kurum-basvurulari/SKILL.md` (`references/ozelge-talebi.md`) |
| Fizibilite raporu metni | `../idari-ve-kurum-basvurulari/references/yatirim-fizibilite-raporu.md` |
| SGK işveren hissesi desteğinin uygulanmaması / yersiz teşvik geri alımı itirazı | Esas `../sosyal-guvenlik-sgk/SKILL.md`; dilekçe `../idari-ve-kurum-basvurulari/references/sgk-itiraz-dilekcesi.md` |

Devrederken taşı: taraf ve rolü, belge no/tarih ve dayandığı karar, işlem/tebliğ tarihi, süre tablosu, destek unsurları tablosu, çekilmiş madde/karar/özelge künyeleri (etiketleriyle), istem önerisi, açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** belge, tamamlama vizesi ve yükümlülük süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Genel mevzuat taraması, takip listesi, boşluk tablosu:** teşvik dışı alanlarla birlikte genel tarama (alana özgü takip `references/tesvik-mevzuati-degisiklik-takibi.md`'de kalır) → [mevzuat-takibi](../mevzuat-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Teşvik belgesi müracaatını E-TUYS'a girmez; Bakanlığa, KOSGEB'e, ajansa başvuru göndermez.
- Destek oranını, tavanını, asgari yatırım tutarını, bölgesini ve süresini ezberden söylemez; Karar metninden ya da Bakanlık ilanından çeker veya `[doğrula]` der.
- Finansal projeksiyon uydurmaz; kullanıcının rakamıyla hesaplar, rakam yoksa tabloyu `[___]` bırakır.
- YMM tasdik raporu, tamamlama ekspertiz raporu ya da yatırım ilerleme raporu düzenlemez; yalnız kontrol listesi ve taslak yapı verir.

---

