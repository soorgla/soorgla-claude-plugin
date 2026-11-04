# Nafaka: tedbir, yoksulluk ve iştirak nafakası; artırım, azaltma, kaldırma

**Ne zaman kullanılır:** boşanma davasında nafaka talebi ya da savunması; boşanmadan sonra yoksulluk ya da iştirak nafakasının artırılması, azaltılması ya da kaldırılması; "süresiz nafaka" sorusu; 6284 kapsamında tedbir nafakası. Nafaka alacağının icra yoluyla tahsili → `icra-iflas` becerisi (`../../icra-iflas/SKILL.md`).

---

## Nafaka türleri

| Tür | Dayanak | Kime | Kusur koşulu |
|---|---|---|---|
| Tedbir nafakası (dava süresince) | TMK 169 (boşanma davasında re'sen geçici önlem); ayrı yaşamada TMK 197 | Eş ve çocuklar | Aranmaz `[incele]`   |
| 6284 tedbir nafakası | 6284 m.5/4 | Şiddet mağduru | Hâkim, TMK'ya göre nafakaya hükmedilmemişse talep olmasa bile verebilir  |
| Yoksulluk nafakası | TMK 175 | Boşanma yüzünden yoksulluğa düşecek eş | Kusuru **daha ağır olmamalı**; nafaka yükümlüsünün kusuru aranmaz  |
| İştirak nafakası | TMK 182/3, 327-330 | Velayeti kendisine verilmeyen eşin çocuğun giderine katılması | Kusurdan bağımsız  |
| Yardım nafakası | TMK 364 vd. | Yoksulluğa düşecek üstsoy, altsoy, kardeş | Kardeşe nafaka ancak yükümlü refah içindeyse `[incele]`  |

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| Boşanma davasında istenmeyen yoksulluk nafakası için ayrı dava: boşanma hükmünün kesinleşmesinden **1 yıl** | TMK 178  | Zamanaşımı; def'i olarak ileri sürülür |
| Artırım, azaltma, kaldırma davası | Kanunda süre yok | Koşul değişikliği oldukça açılabilir; geçmişe etkisi `[incele]` |
| Kanun yolu: tebliğden 2 hafta | HMK 345 | Nafaka davaları adli tatilde de görülür (HMK 103/1-b)  |

---

## Kontrol listesi

### 1. Yoksulluk nafakasının koşulları (TMK 175)
- Talep eden boşanma yüzünden **yoksulluğa düşecek** mi? Gelirine, mal varlığına, çalışma gücüne bak. "Yoksulluk" asgari yaşam gereksinimini karşılayamamak olarak yorumlanır; asgari ücretin altında gelir tek başına ölçüt değildir `[incele]`.
- Talep edenin kusuru **daha ağır olmamalı**. Eşit kusur engel değildir. 
- Yükümlünün mali gücü: nafaka "mali gücü oranında" belirlenir.

### 2. "Süresiz" nafaka tartışması — güncel durum
- Kanun metni hâlâ "**süresiz olarak**" demektedir. 
- **AYM:** "süresiz olarak" ibaresine yapılan itirazlar iki kez esastan reddedildi. 2025'teki son itiraz, kural o davada uygulanacak kural olmadığı için yetkisizlik nedeniyle reddedildi. Yani ibare yürürlüktedir.  Yasa değişikliği gündemi için `legal_search_official_gazette` ile son durumu ara. Model bilgisindeki "nafakaya süre sınırı getiriliyor" haberlerini RG'de karşılığı yoksa yazma.
- **Yargıtay 2. HD (2026):** irat biçiminde verilen yoksulluk nafakasını "36 ay" gibi bir süreyle sınırlamak **kanuna açık aykırılıktır**; nafaka alacaklısı açıkça istemedikçe süre konamaz. Kısa evlilikte doğru yol, hâkimin takdiriyle bir defaya mahsus **toptan ödeme** kararını tartışmaktır (TMK 176/1). 
- Toptan nafakada ölçütler: kusurun niteliği, evliliğin süresi, tarafların ekonomik ve sosyal durumu, ödeme gücü, ortak çocuk yokluğu, yaş, yeniden evlenme olasılığı. 

### 3. Nafakanın sona ermesi ve değiştirilmesi (TMK 176)
- **Kendiliğinden kalkar:** alacaklının yeniden evlenmesi, taraflardan birinin ölümü.
- **Mahkeme kararıyla kaldırılır:** alacaklının evlenmeden fiilen evliymiş gibi yaşaması, yoksulluğun ortadan kalkması, haysiyetsiz hayat sürmesi.
- **Artırma/azaltma:** tarafların mali durumunun değişmesi ya da hakkaniyet.
- **Gelecek yıllar için artış:** hâkim, istem hâlinde irat biçimindeki nafakanın gelecek yıllarda ne miktarda ödeneceğini karara bağlayabilir (ör. TÜFE oranında). Bu istem dilekçede açıkça yazılmalıdır. 
- Kaldırma davasında ispat: fiilen evli gibi yaşama için süreklilik, ortak konut, sosyal çevrenin bilgisi; tek fotoğraf yetmez `[incele]`.
- Artırım davasında TÜFE değişimini `legal_calculate_cpi_change` ile göster; ama hâkimin TÜFE ile bağlı olmadığını belirt `[incele]`.

### 4. İştirak nafakası (TMK 182, 327-330)
- Miktar: çocuğun ihtiyaçları, ana ve babanın hayat koşulları ve ödeme güçleri, çocuğun gelirleri. Her ay peşin ödenir. 
- Çocuk ergin olunca iştirak nafakası sona erer. Eğitim devam ediyorsa ergin çocuk için yardım ya da eğitim nafakası ayrıca değerlendirilir (TMK 328/2: ana-baba, durum ve koşullara göre beklenebilecek ölçüde, eğitim bitene kadar bakmakla yükümlü) `[incele]`. 
- Velayet değişirse iştirak nafakasının yönü de değişir.

### 5. Usul
- Bağımsız nafaka davaları aile mahkemesindedir; temyizde 2. HD. 
- Harç → `legal_calculate_court_fee`. Nafaka davasında değer yıllık nafaka üzerinden hesaplanabilir `[doğrula]`.
- Yabancı para nafaka ya da yurt dışındaki borçlu → `yabancilik-unsuru-ve-tanima.md` ve `legal_get_exchange_rate`.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4721"  article_no: "175" | "176" | "178" | "182" | "327" | "328" | "330"
legal_get_statute_article  law_no: "6284"  article_no: "5"
legal_search_cases  mahkeme: "yargitay"  daire: "2. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. yoksulluk nafakasının belirli süreyle sınırlandırılması kanuna aykırıdır toptan nafaka>"
legal_search_cases  mahkeme: "anayasa"  sorgu: "TMK 175 süresiz olarak ibaresi"
legal_search_official_gazette  query: "yoksulluk nafakası"  date_from: "<son 2 yıl>"
legal_calculate_cpi_change   # artırım göstergesi
legal_get_life_expectancy    # toptan nafaka hesabında yardımcı
legal_get_case_document  belge_id: "<seçilen karar>"
```

---

## Görüşme soruları

1. Hangi nafaka? Tedbir, yoksulluk, iştirak; yeni talep mi, artırım mı, kaldırma mı?
2. Boşanma kararının tarihi ve kesinleşme tarihi? Kararda nafaka ve artış kaydı var mı?
3. Tarafların şu anki gelirleri, işleri, mal varlıkları, yeni eş veya birlikte yaşanan kişi?
4. Çocukların yaşları, okulları, özel ihtiyaçları (sağlık, kurs)?
5. Nafaka alacaklısının yeniden evlenmesi ya da fiilen evli gibi yaşaması iddiası var mı? Delil ne?
6. Son ödeme ne zaman yapıldı, birikmiş nafaka var mı? (icra → `icra-iflas`)
7. Taraflardan biri yurt dışında mı?

## Çıktı iskeleti

```markdown
## Nafaka değerlendirmesi: [müvekkil] — [tarih]
### Sonuç
### Talep / savunma tablosu
| Nafaka türü | Koşul | Durum | Dayanak | Not |
### Değişiklik gerekçeleri (artırım/kaldırma)
| Olgu | Delil | Etki | [incele] |
### Göstergeler
[gelirler, TÜFE değişimi — legal_calculate_cpi_change; tutar önerisi yok, [incele]]
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Yoksulluk nafakasını hâkimin takdiriyle belirli süreyle sınırlanabilir saymak (2. HD 2026: kanuna açık aykırılık).
- "AYM süresiz nafakayı iptal etti" demek. İbare yürürlüktedir.
- Eşit kusurlu eşe yoksulluk nafakası verilemez sanmak. Engel yalnız "daha ağır kusur".
- Artırım davasında TÜFE'yi otomatik ölçüt saymak.
- Boşanmada istenmeyen yoksulluk nafakası için 1 yıllık süreyi kaçırmak.

---

