---
name: icra-iflas
description: >
  İcra ve iflas işlemlerini değerlendirir (İİK): ilamlı, ilamsız ve kambiyo
  takibi, ödeme emrine itiraz, itirazın kaldırılması ve iptali, icra
  mahkemesine şikâyet, haciz ve haczedilmezlik, ihalenin feshi, sıra cetveli,
  menfi tespit, ihtiyati haciz, tasarrufun iptali, iflas ve konkordato.
  Alacaklı ya da borçlu vekili avukatlar için. Kullanıcı "icra takibi
  başlatacağız", "itirazın kaldırılması mı iptali mi", "haciz kaldırılsın",
  "konkordato" dediğinde kullan. Avukatsız vatandaşın basit ödeme emri itirazı
  vatandas-basvurulari'nda; dava ve kanun yolu dilekçesi
  hukuk-yargilamasi-dilekce ve kanun-yollari-dilekce'de yazılır.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: ödeme emri, icra emri, haciz tutanağı, kıymet takdiri raporu, sıra cetveli, konkordato kararı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /icra-iflas

Türk icra ve iflas hukuku için birleşik beceri. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- **Konular ve mevzuat:** Türk icra ve iflas hukuku (2004 s. İİK): ilamlı, ilamsız ve kambiyo senedine dayalı takip, takip talebi, ödeme emri ve icra emri, ödeme emrine itiraz (avukat ya da alacaklı tarafı), itirazın kaldırılması, itirazın iptali, inkâr tazminatı, icra mahkemesine şikâyet, usulsüz tebligat ve e-tebligat, icranın geri bırakılması, haciz, maaş haczi, haczedilmezlik, 89 haciz ihbarnamesi, istihkak davası, kıymet takdiri, satış, ihalenin feshi, sıra cetveli, menfi tespit ve istirdat, ihtiyati haciz, tasarrufun iptali, iflas, konkordato, kiralananın icra yoluyla tahliyesi, icra mahkemesi kararına istinaf.
- **Tipik kullanıcı ifadeleri:** "icra takibi başlatacağız", "itirazın kaldırılması mı iptali mi", "icra müdürlüğü işlemini şikâyet", "haciz kaldırılsın", "ihale feshi", "konkordato", "iflas".
- **Komşu beceriler:** Avukatsız vatandaşın basit ödeme emri itirazı vatandas-basvurulari'nda; dava ve kanun yolu dilekçe metni dilekçe becerilerinde.

## Kapsam

**Kapsar:** genel haciz yoluyla ilamsız takip, kambiyo senetlerine özgü haciz yolu, ilamlı takip, rehnin paraya çevrilmesi (yalnız işaret), ödeme emrine itiraz ve sonrası (itirazın kaldırılması, itirazın iptali, inkâr tazminatı), icra mahkemesine şikâyet ve tebligat usulsüzlüğü, icranın geri bırakılması, haciz ve haczedilmezlik, haciz ihbarnamesi, istihkak, kıymet takdiri, satış ve ihalenin feshi, sıra cetveli, menfi tespit ve istirdat, ihtiyati haciz, tasarrufun iptali (çerçeve), iflas yolları ve iflas tasfiyesinde sıra cetveli, konkordato, kiralananın icra yoluyla tahliyesi, icra mahkemesi kararlarına kanun yolu.

**Kapsamaz ya da yönlendirir:**
- Avukatsız vatandaşın kendi ödeme emrine itirazı (Örnek 7, 10, 13 için süre, merci, basit dilekçe) → `vatandas-basvurulari` (`../vatandas-basvurulari/references/icra-itirazi.md`). Bu beceri o dosyayı tekrarlamaz; avukat ya da alacaklı tarafının stratejisini kurar.
- Kira ilişkisinin esası (kira artışı, tespit, tahliye sebepleri, depozito, kira arabuluculuğu) → `kira-hukuku` (`../kira-hukuku/SKILL.md`); bu beceri yalnız İİK 269 vd. icra yolunu ve icra mahkemesi aşamasını alır.
- İşçilik alacağına dayalı itirazın iptali, menfi tespit ve istirdat → esas için `is-hukuku` (`../is-hukuku/SKILL.md`); bu beceri icra usulünü ekler.
- Sözleşmeden doğan alacağın varlığı, cezai şart, temerrüt → `sozlesme-incelemesi-tbk` (`../sozlesme-incelemesi-tbk/SKILL.md`).
- Haksız haciz nedeniyle tazminat → `tazminat-haksiz-fiil` (`../tazminat-haksiz-fiil/SKILL.md`).
- Nafaka ilamının icrası ve nafaka alacağı için haciz önceliği → esas için `aile-miras` (`../aile-miras/SKILL.md`); haciz sırası bu becerinin `haciz-satis-istihkak-ve-sira-cetveli.md` dosyasında.
- Amme alacakları (6183 sayılı Kanun, vergi ve SGK prim takibi), vergi ihtilafı → `../vergi/SKILL.md` (6183 ödeme emri ve haciz: `../vergi/references/amme-alacagi-tahsili-6183.md`); SGK prim borcu için `sosyal-guvenlik-sgk` (`../sosyal-guvenlik-sgk/SKILL.md`). Bu beceri yalnız 6183 takibinin İİK takibiyle kesiştiği yeri (sıra, konkordato mühleti) işaretler.
- İcra suçları (İİK m.331-354) ve hileli/taksirli iflas suçu → yalnız işaret; TCK genel hükümleri `../ceza-hukuku-suclar/SKILL.md`, dilekçe `ceza-ve-infaz-dilekce`.
- Gemi ihtiyati haczi ve gemi alacaklısı hakkı (TTK m.1352 vd.) → `../deniz-tasima/references/gemi-ihtiyati-haczi-ve-gemi-alacaklari.md`; genel ihtiyati haciz usulü burada.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "2004"`, `article_no: "16"`) çağır. Yanıt gelirse `soorgla ✓`. Profili oku: rol (avukat / değil) ve taraf (alacaklı / borçlu / üçüncü kişi / ihale alıcısı / konkordato alacaklısı).

### Adım 1 — Soru tipini sınıfla ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Takip başlatma: yol seçimi, takip talebi, zamanaşımı, faiz | takip açacağız, hangi örnek, ilamlı mı ilamsız mı, çek/senet, fatura, kapak hesabı | `references/takip-yolu-ve-takip-talebi.md` |
| B. Ödeme emri tebliğ edildi ya da itiraz geldi: itiraz stratejisi, itirazın kaldırılması/iptali, inkâr tazminatı, arabuluculuk | itiraz ettiler, itirazın kaldırılması, itirazın iptali, 6 ay, 1 yıl, %20 tazminat | `references/odeme-emri-itiraz-ve-sonrasi.md` |
| C. İcra dairesi işlemine şikâyet, tebligat, icranın geri bırakılması, icra mahkemesi kararına kanun yolu | şikâyet, usulsüz tebligat, e-tebligat, icra emri, zamanaşımı itirazı, istinaf | `references/sikayet-tebligat-ve-icra-mahkemesi.md` |
| D. Haciz, haczedilmezlik, 89 ihbarnamesi, istihkak, kıymet takdiri, satış, ihalenin feshi, sıra cetveli | haciz, maaş haczi, meskeniyet, konutta haciz, istihkak, yediemin, ihale, sıra cetveli | `references/haciz-satis-istihkak-ve-sira-cetveli.md` |
| E. Takip dışı davalar ve geçici hukuki koruma | menfi tespit, istirdat, ihtiyati haciz, tasarrufun iptali, muvazaa | `references/menfi-tespit-istirdat-ve-ihtiyati-haciz.md` |
| F. İflas ve konkordato | iflas, borca batık, konkordato, geçici mühlet, kesin mühlet, kayıt kabul | `references/iflas-ve-konkordato.md` |
| G. Kiralananın icra yoluyla tahliyesi | Örnek 13, Örnek 14, tahliye emri, kira takibi, iki haklı ihtar | `references/kira-tahliye-takibi.md` |

Bir olay birden fazla tipe giriyorsa (ör. kambiyo takibinde itiraz + haciz + istihkak: A + B + D) hepsini oku, çıktıyı tek belgede birleştir.

**Tarafı sor** (profilde yoksa): alacaklı mı, borçlu mu, üçüncü kişi mi? Kontrol listesi aynıdır; vurgu değişir. Alacaklıda süre düşmesi (haciz isteme, satış isteme, itirazın kaldırılması) ve yanlış yol seçimi; borçluda itiraz ve şikâyet sürelerinin kısalığı ve inkâr tazminatı riski öne çıkar.

**Avukat olmayan kullanıcı** ödeme emrine itiraz soruyorsa `vatandas-basvurulari`'na yönlendir; o dosyadaki 🔴 avukat eşiklerinden biri varsa (kambiyo, imza inkârı, tahliye, süre geçmiş) burada değerlendirmeye devam et ve ORTAK-KURALLAR.md §1 kapısını uygula.

**Ad-hoc doktrin sorusu** (ör. "maaşın ne kadarı haczedilir?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Kritik süreleri en başta hesapla

İcra hukukunda süreler çok kısa (3, 5, 7 gün) ve çoğu hak düşürücüdür. Herhangi bir analizden önce olay tarihlerini topla ve ilgili referans dosyasındaki **süre tablosunu** doldur. Her sürenin dayanağını `legal_get_statute_article` (`law_no: "2004"`) ile çek; referans dosyasındaki süre ifadesi yalnız yön gösterir.

- Süre hesabı İİK m.19'a göre: gün olarak belirlenen sürede ilk gün sayılmaz; hafta olarak belirlenen süre son haftanın aynı gününde biter; son gün resmî tatilse süre izleyen iş günü biter. 
- `legal_calculate_deadline` icra hukukunda yalnız `iik_complaint` (İİK m.16 şikâyet, 7 gün) kodunu tanır; `iik_objection` ve `iik_appeal` "Kural bulunamadı" döner. Diğer bütün süreleri madde metninden elle hesapla, son günü `legal_check_holiday` ile kontrol et ve `[doğrula]` diye işaretle. 
- Adli tatil: aracın `iik_complaint` için "etkilemez" demesi İİK m.16 şikâyetiyle sınırlıdır; itiraz, dava ve kanun yolu sürelerinde adli tatilin etkisini her olayda ayrıca kontrol et `[incele]`. İcra mahkemesine getirilen işler ivedidir (İİK 18/1), ivedi işler adli tatilde de görülür (HMK 103/1-h); HMK 104'teki bir haftalık uzama yalnız adli tatile tabi işlerde işler. İİK m.330 adli tatille ilgili değildir (salgın/savaşta takiplerin Cumhurbaşkanı kararıyla durdurulması). 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴 koy.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Kararlar** — `legal_search_cases`:
- Olayı serbest cümleyle yaz. Ör. `sorgu: "usulsüz tebligatta gecikmiş itiraz değil tebliğ tarihinin öğrenme tarihi olarak düzeltilmesi istenir"`.
- `mahkeme: "yargitay"` + `daire` (görev dağılımı Yargıtay Büyük Genel Kurulu kararıyla her yıl değişebilir; aşağıdaki dağılım 2026/1 sayılı karardan okundu, şüphede yeniden çek):
  - İcra mahkemesinin şikâyet, itiraz ve itirazın kaldırılması kararları; ilamların icrası; satış ve satışa hazırlık şikâyetleri; rehnin paraya çevrilmesi; 89 haciz ihbarnamesine karşı şikâyetler; icra suçları; kira alacağı ve tahliyeye ilişkin icra mahkemesi kararları; istihkak davaları; **tasarrufun iptali** ve TBK m.19 muvazaa davaları → `"12. Hukuk Dairesi"`.
  - **Konkordato**, iflas ve iflasın ertelenmesi kararları; icra mahkemesinde ya da genel mahkemede görülen **sıra cetveline** ilişkin şikâyet ve davalar; İİK m.235 kayıt kabul ve terkin davaları; sermaye şirketlerinin uzlaşma yoluyla yeniden yapılandırılması → `"6. Hukuk Dairesi"`.
  - Ticari nitelikteki itirazın iptali (m.67), borçtan kurtulma (m.69), menfi tespit ve istirdat (m.72); tacirler arası 89 menfi tespiti → `"11. Hukuk Dairesi"`. Tacir olmayanlar arasındaki 89 menfi tespiti → `"3. Hukuk Dairesi"`. İşçi-işveren arasındaki itirazın iptali, menfi tespit ve istirdat → `"9. Hukuk Dairesi"`. Diğer itirazın iptali davaları alacağın kaynağı olan ilişkiye bakan daireye gider `[incele]`.
  
  - Kapatılan 19. HD ve eski 8. HD kararları yalnız eski emsal olarak taranır. Kapanış ve görev devri tarihlerini kesin yazma; bu dairelerde ararken `tarih_bitis` koyma ve en yeni kararın tarihine bak (soorgla'da 19. HD'nin ticari menfi tespit/itirazın iptali kararları Haziran 2020'ye kadar görünüyor). 
  - Direnme kararları → `daire: "Hukuk Genel Kurulu"`.
- İcra mahkemesi kararlarının çoğu **istinafta kesinleşir**: önce `mahkeme: "bam"` ile ara; Yargıtay yalnız temyiz sınırını aşan işler ve ilke için. Sınırlar için `sikayet-tebligat-ve-icra-mahkemesi.md` dosyasına bak.
- Hangi dairenin baktığından emin değilsen `legal_case_facets` (`mahkeme: "yargitay"`) ile dağılıma bak; dağılım sözcük eşleşmesine dayanır.
- Bir karar seçildiyse tam metni `legal_get_case_document` ile oku ve **alıntı-önerme kontrolünü** yap (ORTAK-KURALLAR.md §7). Esas/karar numarası verilmişse `legal_get_case_by_number`.
- **Zorunlu adım:** her analizde **son 3 yıldan en az bir kararın tam metnini** oku (`tarih_baslangic` ile süz). Yalnız arama özetine dayanan emsal `[çekildi ama desteği doğrulayın]` etiketi alır.

**Mevzuat** — madde numarası belliyse `legal_get_statute_article`; belli değilse `legal_search_statute_semantic`. Temel mevzuat:
- 2004 İcra ve İflas Kanunu · 7201 Tebligat Kanunu (m.7/a e-tebligat, m.21, m.32, m.35) · 6102 TTK (kambiyo senetleri, m.376 borca batıklık, m.5/A arabuluculuk) · 6098 TBK (kira, temerrüt, m.19 muvazaa) · 3095 Kanuni Faiz ve Temerrüt Faizi Kanunu · 6325 HUAK (m.18/A, m.18/B) · 7036 İş Mahkemeleri Kanunu m.3 · 6183 AATUHK (yalnız kesişme) · 492 Harçlar Kanunu.
- **Harfli maddeler** (ör. 6102 m.5/A, 6325 m.18/B, İİK 68/a, 83/a, 308/a-h) `legal_get_statute_article` ile doğrudan gelir. Madde numarası belli değilse `legal_list_statute_articles` (`article_no` öneki ya da `article_query`) kullan. 
- Olay tarihinde yürürlükte olan metin farklı olabilir: değişiklik şüphesinde `legal_search_official_gazette` (`document_type: "kanun"`, `query: "2004 sayılı İcra ve İflas Kanununun"`) ile değiştiren kanunu bul; madde tarihçesi araçları eksik olabilir.

**Son yıllardaki önemli değişiklikler** (her birini olay tarihine göre uygula, geçiş hükmüne bak):

| Kanun (RG) | Değişiklik | Etkilediği referans |
|---|---|---|
| 7343 (30.11.2021) | Satış isteme süresi taşınır/taşınmaz ayrımı kalkarak hacizden itibaren **bir yıl**; ihalenin feshi talep edebilecekler sınırlandı, üçüncü kişilere nispi harç ve teminat; elektronik satış portalı | haciz-satis | 
| 7445 (05.04.2023) | Konutta haciz için icra mahkemesi onayı (m.79/a); ev eşyasının haczedilmezliği genişledi (m.82/3); haciz alacak ve giderleri aşamaz (m.85); muhafazasına gerek kalmayan malların tasfiyesi (m.88/a); 1.9.2023'ten sonra açılan **ticari ve işçilik** menfi tespit ve istirdat davalarında dava şartı arabuluculuk (TTK m.5/A, 7036 m.3); kira uyuşmazlıklarında dava şartı arabuluculuk (HUAK m.18/B, İİK'ya göre ilamsız tahliye hariç) | haciz-satis, menfi-tespit, odeme-emri, kira-tahliye |
| 7499 (12.03.2024) | İİK m.19'a hafta olarak belirlenen süre kuralı; BAM kararlarına temyiz süresi **iki hafta** (m.364/2) | sikayet-tebligat |
| 7571 (25.12.2025) | İhalenin feshinde ehliyetsiz kişilerin talebinin dosya üzerinden kesin reddi; eksik teminat/harç için iki haftalık kesin süre (m.134); tasarrufun iptalinde bağışlama sayılan işlemler yeniden yazıldı (m.278); m.363-364 parasal sınırlarında **şikâyet ya da dava tarihindeki** miktar esas (ek m.1/2) | haciz-satis, menfi-tespit, sikayet-tebligat |

Ek m.1/2 zinciri: 7550 (RG 04.06.2025, yayımında yürürlük) "hükmün verildiği" yerine "davanın açıldığı veya şikâyet başvurusunun yapıldığı" tarihi getirdi ve üçüncü fıkrayı kaldırdı; 7571 m.3 (25.12.2025) fıkrayı aynı esasla yeniden yazdı. İkisi de İİK'ya geçiş hükmü eklemedi; eski tarihli kararlarda uygulama için `references/sikayet-tebligat-ve-icra-mahkemesi.md`'deki araştırma adımını izle. 

**Sayısal parametreler** — beceri metnine hiçbir tutar, oran ya da sınır gömülmez:
- İcra harçları: `legal_calculate_court_fee` yalnız tahsil harcını hesaplar (`harc_turu: "icra_tahsil_haciz_once"`, `"icra_tahsil_haciz_sonra"`, `"icra_tahsil_satis"`, `deger` ile). İcraya başvurma, peşin harç (takip), haciz-teslim-satış harcı, icra mahkemesi başvurma, iflas/konkordato ve ihtiyati haciz harcı için `legal_get_social_parameters` (`tur: "harc_icra_basvurma"`, `"harc_basvurma_sulh"`, `"harc_haciz_teslim_satis"`, `"harc_iflas_konkordato"`, `"harc_ihtiyati_tedbir_haciz"`, `"harc_icranin_tehiri"`, `"harc_icra_idare"`, `"harc_icra_degersiz"`). Aracın `pesin_harc` kodu **dava** peşin harcıdır (karar ilam harcının dörtte biri), icra takibinin peşin harcı değildir; takip peşin harcını bu kodla hesaplama. 
- İcra mahkemesi istinaf ve temyiz sınırları (İİK m.363, 364): `legal_get_social_parameters` (`tur: "icra_kesinlik_siniri"` → m.363/1 istinaf sınırı; `tur: "icra_temyiz_siniri"` → m.364/1 temyiz sınırı). Tutar ek m.1 uyarınca her yıl yeniden değerleme oranıyla artar ve 7571'den sonra **şikâyet ya da dava tarihindeki** yılın tutarı esas alınır; dönem alanını olay tarihiyle karşılaştır. HMK sınırlarını (`istinaf_kesinlik_siniri`, `temyiz_siniri`) icra mahkemesi kararlarına uygulama. 
- İlamsız takipte itirazın kaldırılması için parasal sınır **yok** (İİK m.68 metninde tutar geçmez); araçtaki dayanaksız `ilamsiz_itirazin_kaldirilmasi_siniri` kalemi 2026-11-03'te kaldırıldı. Böyle bir sınır varsayma. 
- Yasal ve ticari faiz → `legal_get_legal_interest_rates`; döviz alacağında kur → `legal_get_exchange_rate`.

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

### Adım 5 — Çıktı
Referans dosyasındaki çıktı iskeletini kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [alacaklı/borçlu/üçüncü kişi] — [icra dairesi, dosya no, tarih]

### Sonuç (tek paragraf)
### Kritik süreler
| İşlem | Başlangıç (tebliğ/öğrenme) | Son gün | Dayanak | Merci | Durum |
### Yol seçimi ve riskler
### Kontrol listesi bulguları
### Harç ve masraf (araçtan; her tutar [doğrula])
### Emsal kararlar
### Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Kullanıcı avukat değilse ve çıktı itiraz, şikâyet, takip talebi, ihalenin feshi talebi ya da dava dilekçesi ise ORTAK-KURALLAR.md §1'deki kapıyı uygula. Haksız itiraz ve haksız takip tazminatı (İİK m.67, 68, 72, 97, 170) avukat olmayan için 🔴 risk satırıdır.

### Adım 7 — Dilekçe aşamasında devir
Değerlendirme bitince dilekçeyi bu becerinin içinde değil, dilekçe becerisinde kur (ORTAK-KURALLAR.md §14). Taşınacak özet: taraflar ve rolleri, icra dairesi ve dosya no, takip türü (örnek no), kritik tarihler ve süre tablosu, çekilmiş madde ve karar künyeleri, istem önerisi, açık sorular.

| İstenen belge | Beceri |
|---|---|
| Avukatsız vatandaşın Örnek 7 ödeme emrine itirazı | `vatandas-basvurulari` (`../vatandas-basvurulari/references/icra-itirazi.md`) |
| İtirazın iptali, menfi tespit, istirdat, tasarrufun iptali dava dilekçesi; dava şartı arabuluculuk başvurusu; ihtiyati haciz talebi ve ihtiyati haciz kararına itiraz; noter ihtarnamesi (temerrüt, iki haklı ihtar) | `hukuk-yargilamasi-dilekce` |
| İcra mahkemesi kararına **istinaf**, BAM kararına **temyiz** | `kanun-yollari-dilekce` (İİK m.363-364 süre ve sınırları bu beceriden taşınır) |
| İcra mahkemesine şikâyet, itirazın kaldırılması, kambiyo itirazı, icranın geri bırakılması, ihalenin feshi, kıymet takdirine şikâyet, istihkak, konkordato ve iflas talepleri | **Ayrı dilekçe becerisi yok.** Bu becerinin referans iskeletiyle yaz; ORTAK-KURALLAR.md §13 kurallarını (süre, `[___]`, harç araçtan, sunma kapısı) aynen uygula. |

---

## Hesaplarda kurallar

- Takip tutarını **asıl alacak + işlemiş faiz (dönem, oran, dayanak) + masraf** olarak ayrı ayrı göster; faiz oranını araçtan çek, kur farkını `legal_get_exchange_rate` ile göster.
- İnkâr tazminatı, kötüniyet tazminatı ve para cezaları için kanundaki alt sınırı madde metninden aktar; hâkimin takdirine kalan oranı tahmin etme `[incele]`.
- Her tutarın yanında `[doğrula]`. Temiz görünen yanlış bir kapak hesabı bu becerinin önlemeye çalıştığı asıl hatadır.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Uzun ya da çok belgeli dosya** (icra dosyası, ihale ve satış evrakı, sıra cetveli): okuma [uzun belge protokolüyle](../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md).
- **Süreyi kaydet:** itiraz, şikâyet ve dava süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Hesap araçları** (takip faizi, tahsil harcı; başvurma ve icra peşin harcı araçta yok): araç kullanımı ve bilinen eksikler → [hesaplamalar/faiz](../hesaplamalar/references/faiz.md), [hesaplamalar/harc](../hesaplamalar/references/harc.md); tutarlar araçtan çekilir.

## Bu beceri ne yapmaz

- UYAP'ta takip açmaz, harç yatırmaz, haciz istemez.
- Malvarlığı sorgusunun sonucunu tahmin etmez; yalnız hangi sorgunun istenebileceğini söyler (İİK m.78).
- Süreleri, sınırları, harçları ve daire görev dağılımını ezberden söylemez; her birini çeker ya da `[doğrula]` diye işaretler.
- Konkordato projesinin finansal fizibilitesini ya da borca batıklık bilançosunu hazırlamaz; hukuki koşulları ve belge listesini kontrol eder, mali analizi bağımsız denetçiye bırakır.

---

