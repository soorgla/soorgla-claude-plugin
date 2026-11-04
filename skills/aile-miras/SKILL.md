---
name: aile-miras
description: >
  Aile ve miras uyuşmazlıklarını değerlendirir (TMK): anlaşmalı ve çekişmeli
  boşanma, protokol kontrolü, nafaka, velayet, soybağı, mal rejimi tasfiyesi,
  6284 koruma kararı, yabancı boşanma kararının tanınması; mirasçılık, saklı
  pay ve tenkis, muris muvazaası, vasiyetname, mirasın reddi. Eşler,
  mirasçılar ve avukatlar için. Kullanıcı "boşanmak istiyorum", "nafaka ne
  kadar", "kardeşim tapuyu üstüne almış", "mirası reddetmek istiyorum"
  dediğinde kullan. Tapu iptali ve ortaklığın giderilmesi
  gayrimenkul-insaat'ta; önce değerlendirir, dilekçe metni
  hukuk-yargilamasi-dilekce ve kanun-yollari-dilekce'de yazılır.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: evlilik ve çocuk bilgileri, mahkeme kararı, tapu, vasiyetname, nüfus kaydı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /aile-miras

Türk aile hukuku (TMK İkinci Kitap, 6284, 4787) ve miras hukuku (TMK Üçüncü Kitap) için birleşik beceri. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula: taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri sayılması, gözden geçiren notu, karar ağacı. Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- **Konular ve mevzuat:** Türk aile ve miras hukuku: boşanma (anlaşmalı boşanma protokolü TMK 166/3, çekişmeli boşanma, zina, terk, kusur), maddi ve manevi tazminat, tedbir, yoksulluk ve iştirak nafakası (süresiz nafaka, artırım, kaldırma), velayet ve kişisel ilişki, ortak velayet, soybağı ve babalık, Lahey çocuk kaçırma, mal rejimi tasfiyesi (katılma alacağı, değer artış payı, katkı payı, 2002 öncesi mallar), 6284 koruma ve uzaklaştırma kararı, aile mahkemesi, yabancı boşanma kararının tanınması ve tenfizi (MÖHUK). Miras: yasal mirasçılık, saklı pay, tenkis davası, muris muvazaası, mirasçılık belgesi (veraset ilamı), mirasın reddi, vasiyetname şekli ve iptali, tereke paylaşımı.
- **Tipik kullanıcı ifadeleri:** "boşanmak istiyorum", "protokol hazırla", "nafaka ne kadar", "velayet kime", "eşim şiddet uyguluyor", "mal paylaşımı", "babamdan kalan ev", "kardeşim tapuyu üstüne almış", "mirası reddetmek istiyorum", "vasiyetname geçerli mi".
- **Komşu beceriler:** Önce değerlendirir; dilekçe hukuk-yargilamasi-dilekce ve kanun-yollari-dilekce becerilerine devredilir.

## Kapsam

**Kapsar:**
- Boşanma: anlaşmalı ve çekişmeli boşanma, ayrılık, kusur, boşanmanın mali sonuçları (TMK 161-184).
- Nafaka: tedbir, yoksulluk ve iştirak nafakası; nafakanın artırılması ve kaldırılması.
- Çocuk: velayet, kişisel ilişki, soybağı ve babalık, uluslararası çocuk kaçırma.
- Mal rejimi tasfiyesi (TMK 202-281).
- 6284 sayılı Kanun kapsamındaki koruyucu ve önleyici tedbirler.
- Yabancılık unsurlu aile uyuşmazlıkları: kısa MÖHUK çerçevesi, tanıma ve tenfiz.
- Miras: yasal mirasçılık, saklı pay, tenkis, muris muvazaası, mirasçılık belgesi, mirasın reddi, vasiyetname ve miras sözleşmesi, mirasçılar arası ortaklığın giderilmesi.

**Kapsamaz ya da yönlendirir:**
- Nafaka alacağının icra takibi, nafaka borcunun ödenmemesinden doğan şikâyet, kiralanan ya da tereke malı için icra yolu → `icra-iflas` becerisi (`../icra-iflas/SKILL.md`). Vatandaşın kendi yazacağı basit ödeme emrine itiraz → [../vatandas-basvurulari/references/icra-itirazi.md](../vatandas-basvurulari/references/icra-itirazi.md).
- Aile içi şiddetin ceza boyutu (kasten yaralama, tehdit, 6284 m.13 zorlama hapsi dışındaki suçlar) → yalnız işaret; ceza dilekçesi `ceza-ve-infaz-dilekce`.
- Eşler arasında haksız fiil tazminatı (boşanmadan bağımsız) ve trafik kazasında destekten yoksun kalma → `tazminat-haksiz-fiil`.
- Tapulu taşınmazda bağışlama, ölünceye kadar bakma ve diğer sözleşme incelemesi (sözleşme metni) → `sozlesme-incelemesi-tbk`. Bu sözleşmelerin **miras payına etkisi** (tenkis, muris muvazaası) bu becerideki işlerdir.
- Vesayet, kısıtlama ve kayyımlık (TMK 396-494) → yalnız genel çerçeve ve `[incele]`. Vesayet işlerinde görevli mahkeme sulh hukuktur; aile mahkemesi değildir (4787 m.4/1). 
- Mirasçıların vergi yükümlülüğü (veraset ve intikal vergisi) → oran ve tutar uydurma; veraset ve intikal vergisinin usulü, beyanı ve ihtilafı → `../vergi/SKILL.md`.
- Mirasçı olmayan paydaşlar arasında ortaklığın giderilmesi, tapu iptali ve tescil (muris muvazaası dışında), önalım (7571 ile değişen TMK m.733-734), ecrimisil, kat mülkiyeti → `../gayrimenkul-insaat/SKILL.md`. Yabancı unsurlu mirasta yabancının taşınmaz edinimi → `../yabancilar-vatandaslik/references/tasinmaz-edinimi-ve-tenfiz.md`.
- Kamu personeline ilişkin aile yardımı ve benzeri idari konular → `../kamu-personeli/SKILL.md`; idari dava dilekçesi → `../idare-davalari-imar/references/idari-dava-dilekcesi.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü, güvenlik taraması ve profil

1. Hedef maddeye bir `legal_get_statute_article` çağrısı yap (ör. `law_no: "4721"`, `article_no: "166"`). Yanıt gelirse `soorgla ✓`.
2. **Güvenlik taraması (her aile sorusunda, kullanıcı sormasa bile):** anlatımda şiddet, tehdit, ısrarlı takip, çocuğun zarar görme ya da yurt dışına götürülme riski var mı? Varsa:
   - Çıktının **en üstüne** 🔴 ve `references/aile-ici-siddet-6284.md` adımlarını koy. Tedbir kararı en yakın hâkimden, mülki amirden ya da kolluktan istenebilir ve koruyucu tedbir için delil aranmaz. 
   - Acil tehlikede 112'yi ve 6284'teki başvuru yerlerini (kolluk, mülki amir, hâkim) hatırlat. Destek hatları ve uygulamaları (ör. ALO 183, KADES) anılacaksa adlarının ve işleyişinin güncelliğini resmî kaynaktan kontrol etmesini söyle; soorgla bunları doğrulamıyor. 
   - **Gizlilik:** korunan kişinin adresi ve iletişim bilgisi çıktıya yazılmaz; karşı tarafa gidecek metinde yer almaz (6284 m.8/6). 
   - Aile içi şiddet iddiası içeren uyuşmazlık **arabuluculuğa elverişli değildir**. Arabuluculuk ya da uzlaştırıcı görüşme önerme. 
3. Profili oku: rol (avukat ya da değil), temsil edilen taraf (kadın/erkek eş, mirasçı, vasiyet alacaklısı).

> Upstream `legal-clinic/client-intake` becerisinden uyarlandı: aile görüşmesinde güvenlik sorusu şablonun parçasıdır; başka bir alandan gelen soruda bile şiddet ipucu aile/koruma alanını işaretler. Bu taramayı atlamak tek yönlü bir kapıdır.

### Adım 1 — Soru tipini sınıfla

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Boşanma: dava türü seçimi, sebepler, kusur, tazminat, anlaşmalı boşanma protokolü | boşanmak, protokol, aldatma, terk, şiddet, kusur, tazminat, anlaşmalı | `references/bosanma.md` |
| B. Nafaka: tedbir, yoksulluk, iştirak; artırım, azaltma, kaldırma | nafaka, süresiz nafaka, nafaka artırımı, nafakayı kaldırmak, çocuk masrafı | `references/nafaka.md` |
| C. Velayet, kişisel ilişki, soybağı, çocuk kaçırma | velayet, çocuğu görememek, ortak velayet, babalık, soybağı, Lahey, çocuğu yurt dışına götürdü | `references/velayet-cocuk-ve-soybagi.md` |
| D. Mal rejimi tasfiyesi | mal paylaşımı, katılma alacağı, ev kimin, kredi, 2002 öncesi, değer artış payı, katkı payı, mal kaçırma | `references/mal-rejimi-tasfiyesi.md` |
| E. Aile içi şiddet ve 6284 tedbirleri | şiddet, uzaklaştırma, koruma kararı, tehdit, ısrarlı takip, tedbir kararına itiraz | `references/aile-ici-siddet-6284.md` |
| F. Yabancılık unsuru | yurt dışında boşandım, tanıma, tenfiz, yabancı eş, apostil, MÖHUK, nüfusa tescil | `references/yabancilik-unsuru-ve-tanima.md` |
| G. Yasal mirasçılık, saklı pay, tenkis, muris muvazaası, paylaşım | mirasçılar kim, pay oranı, saklı pay, tenkis, babam evi kardeşime sattı göstermiş, ortaklığın giderilmesi | `references/mirascilik-sakli-pay-ve-tenkis.md` |
| H. Vasiyetname, mirasçılık belgesi, mirasın reddi, tereke işlemleri | vasiyetname, el yazılı vasiyet, veraset ilamı, mirasçılık belgesi, mirası reddetmek, borçlu öldü | `references/vasiyetname-ve-miras-islemleri.md` |

Bir olay birden fazla tipe girebilir. Örnek: şiddet + boşanma + velayet → E + A + C; boşanma + ev ve kredi → A + D. Bu durumda hepsini oku ve çıktıyı tek belgede birleştir. Öncelik sırası her zaman **güvenlik → süre → esas**.

**Tarafı sor** (profilde yoksa): hangi eş, hangi mirasçı ya da vasiyet alacaklısı adına çalışılıyor? Kontrol listesi aynıdır, vurgu değişir. Örnek: davacı eş için kusur ispatı ve sürelerin kaçırılması öne çıkar; davalı eş için affetme ve hak düşürücü süre def'ileri.

**Ad-hoc doktrin sorusu** (ör. "kardeşlerin saklı payı var mı?") geldiyse görüşme akışını atla. İlgili maddeyi çek, kısa cevap ver, etiketle (ORTAK-KURALLAR.md §9).

### Adım 2 — Kritik süreleri en başta hesapla

Aile ve miras hukukunda sürelerin çoğu **hak düşürücüdür**; hâkim kendiliğinden dikkate alır. Her referans dosyasındaki süre tablosunu olayın tarihleriyle doldur. Her sürenin dayanağını `legal_get_statute_article` ile çek.

- `legal_calculate_deadline` yalnız kanun yolu sürelerini hesaplar (`hmk_appeal`, `hmk_cassation`). Aile ve miras sürelerini (6 ay/5 yıl, 1 yıl/10 yıl, 3 ay ret) tanımaz; bunları **elle hesapla**, son günü `legal_check_holiday` ile kontrol et ve `[doğrula]` işaretle. 
- **Adli tatil:** her çeşit nafaka davası ile soybağı, velayet ve vesayete ilişkin dava ve işler adli tatilde de görülür. Boşanma davasının kendisi bu listede yoktur; ama nafaka ve velayet içerdiği ölçüde ivedilik `[incele]`.  Adli tatilin kanun yolu sürelerine etkisi için `legal_calculate_deadline` sonucundaki `adli_tatil_etkisi` alanına bak; nafaka ve velayet hükümlerinde sürenin uzamadığını varsayarak hesapla: HMK 104'teki bir haftalık uzama yalnız "adli tatile tabi olan dava ve işlerde" işler. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴 koy.

### Adım 3 — soorgla'dan kaynak çek

Eski YAML'lardaki `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Kararlar** — `legal_search_cases`:
- Olayı serbest cümleyle yaz. Ör. `sorgu: "kısa süreli evlilikte yoksulluk nafakasının belirli süreyle sınırlandırılması"`.
- `mahkeme: "yargitay"` + `daire` (2026 iş bölümüne göre):
  - Boşanma, ayrılık, nafaka (bağımsız nafaka davaları dahil), velayet, soybağı, evlat edinme, **mal rejimi**, 6284 tedbirleri, Lahey çocuk iadesi, vesayet → `"2. Hukuk Dairesi"`. 
  - **Miras hukuku davaları** (tenkis, vasiyetnamenin iptali, mirasçılık belgesinin iptali, miras sözleşmesi) ile mirasçılar arasında ortaklığın giderilmesi → `"7. Hukuk Dairesi"`.  `[doğrula]`
  - **Muris muvazaasına** (1974/1-2 İBK) dayalı tapu iptali ve tescil → `"1. Hukuk Dairesi"`. 
  - Ölünceye kadar bakma sözleşmesine dayalı temliklerin iptali → 7. HD; genel muvazaa (TBK 19) → 12. HD. 
  - Direnme kararları → `"Hukuk Genel Kurulu"`.
  - **Daire iş bölümü her yıl Yargıtay Büyük Genel Kurulu kararıyla değişebilir.** Bu listeyi sabit sayma. Şüphede güncel kararı `legal_search_official_gazette` (`query: "Büyük Genel Kurulu"`, `search_in: "title"`) ile bul.
  - Hangi dairenin baktığından emin değilsen `legal_case_facets` (`mahkeme: "yargitay"`) ile dağılıma bak. Bu dağılım sözcük eşleşmesine dayanır, kesin görev dağılımını göstermez.
- Kapatıldığı sanılan daireler için uyarı: eski YAML "8. HD kapatıldı, mal rejimi arşivi altın değerinde" diyordu. 8. HD hâlâ kurulu; 2026 iş bölümünde kadastro ve tüzel kişiler dairesi. Mal rejimi kararları 2. HD'dedir. Mal rejimine ilişkin eski 8. HD kararlarını yalnız eski emsal olarak ve `tarih_bitis` ile tara.  Geçiş Yargıtay Birinci Başkanlık Kurulunun 02.07.2021 t. 211 s. kararıyla (RG 09.07.2021) oldu; 8. HD'de mal rejimi kararları için `tarih_bitis: "2021-12-31"` civarını kullan, 2022'de de seyrek 8. HD kararı çıkabildiği için sonuç azsa sınırı genişlet. 
- **İstinaf:** aile mahkemesi kararlarına istinaf; BAM kararı temyize açıktır. Kesinlik ve temyiz sınırı → `legal_get_social_parameters`. Velayet ve kişisel ilişki gibi parayla ölçülemeyen kalemlerde parasal sınır yoktur: HMK 341/2 kesinlik sınırı "malvarlığı davalarına", 362/1-a temyiz sınırı "miktar veya değeri" olan davalara ilişkindir. 
- **Zorunlu adım:** her analizde son 3 yıldan en az bir kararın tam metnini `legal_get_case_document` ile oku ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7). Yalnız arama özetine dayanan emsal `[çekildi ama desteği doğrulayın]` etiketi alır.
- AYM norm denetimi kararları (ör. süresiz nafaka itirazları) için `mahkeme: "anayasa"`. Bireysel başvuru kararları da aynı mahkeme altında gelir; `daire` alanında "Birinci Bölüm" gibi bölüm adı görünür.

**Mevzuat** — madde numarası belliyse `legal_get_statute_article` (`law_no`, `article_no`); belli değilse `legal_search_statute_semantic` (`mevzuat_no: "4721"`). Harfli maddeler (ör. 6325 m.18/B, 5490 m.27/A) `legal_get_statute_article` ile doğrudan gelir; madde numarası belli değilse `legal_list_statute_articles` (`statute_id` ile, `article_query`) kullan. 

Temel mevzuat:
- 4721 TMK. Aile: m.118-395; vesayet: m.396-494; miras: m.495-682.
- 4722 TMK'nın Yürürlüğü ve Uygulama Şekli Hakkında Kanun (mal rejimi geçişi m.10).
- 6284 Ailenin Korunması ve Kadına Karşı Şiddetin Önlenmesine Dair Kanun.
- 4787 Aile Mahkemelerinin Kuruluş, Görev ve Yargılama Usullerine Dair Kanun.
- 5718 MÖHUK, 5490 Nüfus Hizmetleri Kanunu (m.27/A).
- 5717 Uluslararası Çocuk Kaçırmanın Hukuki Yönlerine Dair Kanun.
- 6325 Hukuk Uyuşmazlıklarında Arabuluculuk Kanunu (m.1/2, m.18/B).
- 6100 HMK.
- 1512 Noterlik Kanunu (mirasçılık belgesi ve vasiyetname işlemleri).

`legal_get_statute_article_history` bu kanunlarda belirsiz sonuç döndürebilir; 4721 numarası başka bir kayıtla çakışıyor. `statute_id` ver ya da değişikliği `legal_search_official_gazette` ile ara. 

**Sayısal parametreler** — beceri metnine hiçbir tutar yazılmaz:
- Harç (boşanma, nafaka, tenkis, katılma alacağı, ortaklığın giderilmesi) → `legal_calculate_court_fee`; tanınmayan tür için `legal_get_social_parameters`.
- Yasal faiz (katılma alacağı, tazminat) → `legal_get_legal_interest_rates`.
- Nafaka artırımında enflasyon (TÜFE) → `legal_calculate_cpi_change`. Bu yalnız bir göstergedir; hâkim hakkaniyete göre takdir eder `[incele]`.
- Yabancı para nafaka veya tenfiz → `legal_get_exchange_rate`.
- Bakiye ömür (peşin sermaye yoksulluk nafakası, irat hesabı) → `legal_get_life_expectancy`.

**Resmî Gazete takibi** — son değişiklikleri `legal_search_official_gazette` ile ara (`query: "4721 sayılı Türk Medeni Kanununun"`, `date_from` son 2 yıl). Bu taramada bulunan önemli değişiklikler:
- 7532 sayılı Kanun m.13: TMK 166/4'teki "üç yıl" süresi **bir yıl** oldu (RG 27.11.2024, yayımı tarihinde yürürlükte). Değişiklikten önce AYM 166/4'ü E.2023/116 K.2024/56 ile incelemişti (RG 19.04.2024). Ayrıntı ve geçiş sorusu `references/bosanma.md`'de. 
- 7499 sayılı Kanun (RG 12.03.2024): vesayet hükümlerinde (TMK 407, 409, 436, 471) değişiklik. Hükümlü kısıtlamasında güncel metni çek. 
- 7445 sayılı Kanun m.37 (2023): taşınır ve taşınmazların paylaştırılması ve ortaklığın giderilmesi davalarında **dava şartı arabuluculuk** getirildi. Bu, mirasçılar arası ortaklığın giderilmesini doğrudan etkiler.  Yürürlük: **1.9.2023** (7445 m.43/1-a). 
- TMK 187 (kadının soyadı): AYM E.2022/155 K.2023/38 ile cümleler iptal edildi. soorgla maddeyi yalnız iptal notuyla ve mülga uyarısıyla döndürüyor; yasal boşluğun nasıl doldurulduğunu ara.  İptalin yürürlük tarihi ve sonrasında yeni yasal düzenleme yapılıp yapılmadığı bu taramada doğrulanamadı: soyadı sorusunda `legal_search_official_gazette` (`query: "Anayasa Mahkemesi 2022/155"`) ve `legal_search_cases` (`daire: "2. Hukuk Dairesi"`, sorgu "kadının evlenmeden önceki soyadını tek başına kullanması AYM iptal") ile ara, bir kararın tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: TMK 187 iptal sonrası durum]` yaz. Soyadı davası aile mahkemesinde görülür. 

**İdari görüş** — `legal_search_admin_guidance` aile ve miras alanında zayıftır. Tapu ve nüfus genelgeleri gerekiyorsa `legal_search_official_gazette` dene; bulunamazsa ORTAK-KURALLAR.md §5'i uygula.

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır; listede olmayan ilgili bir nokta görürsen ekle.

**Olay kronolojisi** (upstream `litigation-legal/chronology` becerisinden uyarlandı): çekişmeli boşanma, 6284 ve muris muvazaası dosyalarında, olayları tarih sırasıyla bir tabloya dök (tarih | olay | kaynak/delil | önem). Önemi temsil edilen tarafın bakışıyla işaretle: 🔴 kusur unsurunu, hak düşürücü süre başlangıcını ya da affetmeyi gösteren olay; 🟡 desteklenen ama çürütülebilir olay; ⚪ arka plan. Tablonun başına "Önem işaretleri [davacı/davalı] bakışıyla verildi" yaz. Boşanmada kusur ve affetme, tarihlere bakılmadan doğru değerlendirilemez.

### Adım 5 — Çıktı

Referans dosyasındaki çıktı iskeletini kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

[Güvenlik işareti varsa: 🔴 Güvenlik — ilk yapılacaklar]

## [Konu]: [temsil edilen taraf] — [tarih]

### Sonuç (tek paragraf)
### Kritik süreler
| Süre | Başlangıç | Son gün | Dayanak | Durum |
### Kontrol listesi bulguları
### Hesap (varsa: pay oranı, katılma alacağı, nafaka göstergesi)
[formül + girdiler + kaynak; her tutar ve oran [doğrula]]
### Emsal kararlar
### Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

**Süre devri** (upstream `legal-clinic/client-intake` "deadline handoff" fikrinden uyarlandı): değerlendirmede ortaya çıkan her süreyi ayrı satırda, kopyalanabilir biçimde ver: `süre | başlatan olay ve tarihi | dayanak | son gün ([doğrula] — avukat hesaplasın)`. Tarih belgede yazılıysa (duruşma günü, tedbir bitişi) onu yaz. Hesaplanan sürelerde `[doğrula]` bırak.

### Adım 6 — "Taslaktır" kapısı
Kullanıcı avukat değilse ve çıktı şunlardan biriyse ORTAK-KURALLAR.md §1'deki kapıyı uygula: anlaşmalı boşanma protokolü, dava dilekçesi, mirasın reddi beyanı, vasiyetname metni, tenkis ya da iptal davası, 6284 başvurusu. **İstisna:** 6284 tedbir başvurusu ve acil güvenlik adımları için avukat beklenmez. Kullanıcıya doğrudan başvuru yerlerini söyle (aile mahkemesi, kolluk, mülki amir); avukat incelemesini sonraya bırak. 

### Adım 7 — Dilekçe aşamasında devir
Değerlendirme bitip dilekçe istendiğinde metni bu becerinin içinde değil dilekçe becerisinde kur (ORTAK-KURALLAR.md §14). Devirde taşınacak özet: taraflar ve rolleri, kritik tarihler ve süre tablosu, çekilmiş madde ve karar künyeleri, sonuç ve istem önerisi, açık sorular.

| İstenen belge | Beceri |
|---|---|
| Boşanma, nafaka, velayet, tenkis, iptal, katılma alacağı, babalık **dava dilekçesi**; cevap; ıslah; tanık listesi | `hukuk-yargilamasi-dilekce` ([dava-dilekcesi.md](../hukuk-yargilamasi-dilekce/references/dava-dilekcesi.md), [delil-ve-tanik-listesi.md](../hukuk-yargilamasi-dilekce/references/delil-ve-tanik-listesi.md)) |
| Boşanma davasında tedbir (TMK 169) ya da mal kaçırmaya karşı ihtiyati tedbir talebi | `hukuk-yargilamasi-dilekce` ([ihtiyati-tedbir.md](../hukuk-yargilamasi-dilekce/references/ihtiyati-tedbir.md)) |
| Terk ihtarı (TMK 164) için noter ya da mahkeme ihtarı | `hukuk-yargilamasi-dilekce` ([ihtarname.md](../hukuk-yargilamasi-dilekce/references/ihtarname.md)); ihtar talebinin içeriği `references/bosanma.md`'de |
| Mirasçılar arası ortaklığın giderilmesi için **zorunlu arabuluculuk başvurusu** | `hukuk-yargilamasi-dilekce` ([arabuluculuk-basvurusu.md](../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md)) — bu dosyanın 6325 m.18/B'yi kapsadığını kontrol et |
| Aile mahkemesi kararına **istinaf**, BAM kararına **temyiz** | `kanun-yollari-dilekce` ([hukuk-istinaf.md](../kanun-yollari-dilekce/references/hukuk-istinaf.md), [hukuk-temyiz.md](../kanun-yollari-dilekce/references/hukuk-temyiz.md)) |
| 6284 tedbir talebi ve tedbir kararına itiraz | Bu becerideki `references/aile-ici-siddet-6284.md` iskeleti. Ayrı dilekçe referansı yok; itiraz için `kanun-yollari-dilekce` **kullanılmaz** (6284 m.9 itirazı kanun yolu değildir).  |
| Mirasın reddi beyanı (sulh hukuk), mirasçılık belgesi talebi | Bu becerideki `references/vasiyetname-ve-miras-islemleri.md` iskeleti; dava değil çekişmesiz yargı işi |
| Kesinleşmiş karardan sonra AYM bireysel başvurusu | `aym-aihm-basvuru` |

Dilekçe becerisi yüklü değilse taslağı referans iskeletiyle yaz ve süreyi yine madde metninden çek. Hazır `.docx` şablonu yoktur.

---

## Hesaplarda kurallar

- **Miras payı:** pay ve paydayı göster (ör. eş 1/4, kalan 3/4 çocuklar arasında eşit). Önce zümreyi belirle, sonra eşin payını uygula (TMK 495-499).  Ölüm tarihini her zaman sor: **10.05.2007** öncesi ölümlerde kardeşlerin saklı payı vardı (5650 ile mülga; kabul 4.5.2007, RG ve yürürlük 10.05.2007; mirasçılık ölüm tarihindeki hükme tabi, 4722 m.17).  
- **Katılma alacağı:** artık değer = (edinilmiş mallar + eklenecek değerler + denkleştirme) − borçlar; her eş diğerinin artık değerinin yarısına hak kazanır; alacaklar takas edilir (TMK 231, 236). Bu bir formüldür, sonuç değildir. Mevcut edinilmiş mallar **tasfiye anındaki** değerleriyle, eklenecek değerler devir tarihindeki değerleriyle hesaba katılır (TMK 235); uygulamada sürüm değeri bilirkişiyle karar tarihine en yakın tarihte belirlenir `[incele]`. 
- **Nafaka:** tutar önermek bir takdir işidir. Yalnız göstergeleri ver: tarafların gelirleri, çocuğun ihtiyaçları, TÜFE değişimi. Hepsini `[incele]` işaretle.
- Her tutarın yanına `[doğrula — bilirkişi/avukat teyit etsin]` yaz.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Kronoloji / unsur-delil tablosu:** kusur ve olay kronolojisi belge çoksa → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).
- **Süreyi kaydet:** dava, itiraz ve mirasın reddi süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Boşanma, velayet ya da miras paylaşımı kararını vermez; seçenekleri ve riskleri gösterir.
- Kusur oranını kesin olarak belirlemez; delile göre olasılık ve `[incele]` verir.
- Nafaka ve tazminat tutarını kesinleştirmez.
- Süreleri, harçları, daire iş bölümünü ezberden söylemez; çeker ya da `[doğrula]` diye işaretler.
- Şiddet anlatımında taraf tutmaz ama güvenliği her şeyin önüne koyar.
- Çocuğun psikolojik durumunu değerlendirmez; sosyal inceleme raporunu (SİR) okur ve eksiklerini işaretler.

---

