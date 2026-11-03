# Ceza istinafı ve temyizi (CMK m.272-307)

İlk derece ceza mahkemesi hükmüne karşı bölge adliye mahkemesi (BAM) ceza dairesine istinaf; BAM ceza dairesi kararına (ve ilk derece sıfatıyla BAM/Yargıtay kararlarına) karşı Yargıtay'a temyiz. Hükmün açıklanmasının geri bırakılması (HAGB) kararına karşı istinaf da buradadır.

**Önce tarih:** 7499 sayılı Kanun (RG 12.03.2024) süreleri ve başlangıç anını değiştirdi; yeni kurallar **1.6.2024 ve sonrasında verilen kararlar** hakkında uygulanır, öncekilere eski hükümler uygulanmaya devam eder. Her işte önce hükmün tarihini öğren.

## Ne zaman kullanılır

### İstinaf (CMK m.272)

- İlk derece hükümlerine karşı istinaf açıktır; hükme esas teşkil eden ya da başka kanun yolu öngörülmemiş ara kararlar hükümle birlikte istinaf edilir (m.272/2).
- **Resen inceleme:** madde metnindeki ağır hapis eşiğini aşan hükümler BAM'ca resen incelenir (m.272/1) — eşiği metinden oku.
- **Kesin hükümler (m.272/3):** madde metnindeki tutarı geçmeyen adli para cezasına mahkûmiyet (hapisten çevrilenler hariç), metindeki gün sınırını geçmeyen adli para cezası gerektiren suçlardan beraat, kanunda kesin olduğu yazılı hükümler. Tutarı ve sınırı beceri metnine yazma; maddeyi çek, eski tarihli hükümlerde değişikliği `legal_get_statute_article_history` ile kontrol et (`effective_date` parametresi şu an eski metni döndürmüyor, aşağıya bak).
- **HAGB:** 1.6.2024 ve sonrasında verilen HAGB kararlarına karşı yol **istinaftır** (m.272/3 saklı); ilk derece sıfatıyla BAM veya Yargıtay verdiyse temyiz. 1.6.2024 öncesi HAGB kararlarında **itiraz** yolu devam eder.
  - **İstisna:** dosya daha önce Yargıtay'ca bozulmuş ve bozmadan sonra HAGB kurulmuşsa yol temyiz olabilir (CMK m.307/3 ve CGK kararı). `[incele]`
  - "HAGB'ye istinaf yolu kapalı" yönündeki eski görüş **yanlıştır** (yukarıdaki dayanaklar).

### Temyiz (CMK m.286)

- BAM ceza dairelerinin **bozma dışında kalan** hükümleri temyiz edilebilir (m.286/1).
- **Temyiz edilemeyenler (m.286/2):** belirli hapis süresinin altındaki cezalarda istinafın esastan reddi ya da cezayı artırmayan kararlar, adli para cezaları, seçenek yaptırımlar, üst sınırı belirli süreye kadar olan suçlar, metindeki süreyi aşmayan suçlardan beraatin onanması, düşme/CVYO/güvenlik tedbiri kararları vb. Her bendi metinden oku; süreleri beceriye yazma.
- **Bentlere rağmen temyiz edilebilenler (m.286/3):** TCK'daki sayılı ifade ve örgüt suçları (ör. m.125/3, 213-217/A, 299-301, 314, 318), TMK m.6/2-4 ve m.7/2, 2911 m.28/1, 31, 32. Listeyi metinden kontrol et.
- Yargıtay bozmasına uyulduktan sonra ilk derece mahkemesinin verdiği karara karşı, istinaf ve temyiz sınırlarına bakılmaksızın yalnız temyiz yoluna gidilir (m.307/3).

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | MCP |
|---|---|---|---|
| İstinaf: **iki hafta** | Hükmün **gerekçesiyle birlikte tebliği** | CMK m.273/1 | `legal_calculate_deadline` `cmk_appeal` |
| Savcının asliye hükümlerine karşı istinafı: **iki hafta** | Kararın başsavcılığa geliş tarihi | CMK m.273/3 | `cmk_appeal` (başlangıcı sen ver) |
| Savcının istinaf istemine cevap: **iki hafta** | İstemin tebliği | CMK m.273/5 | elle |
| Temyiz: **iki hafta** | Hükmün **gerekçesiyle birlikte tebliği** | CMK m.291/1 | `legal_calculate_deadline` `cmk_cassation` |
| Gerekçenin dosyaya konması: en geç **on beş gün** | Hükmün açıklanması | CMK m.232/3 | — (bilgi) |
| Adli tatil | 20 Temmuz–31 Ağustos'a rastlayan süreler işlemez; tatil bitiminden itibaren **üç gün** uzar | CMK m.331/1, 4 | araç yalnız uyarı veriyor; tutuklu işlerde ayrıca kontrol et `[incele]` |

**Eski iddialar ve düzeltmeler:**
- Eski YAML: "Ceza istinafı (CMK 273) — tefhimden veya tebliğden itibaren **7 gün**." → **Yanlış (1.6.2024 ve sonrası kararlar için).** Güncel metin: gerekçeli hükmün tebliğinden itibaren **iki hafta**; "yokluğunda açıklanmışsa tebliğden" diyen eski 2. fıkra mülga. 1.6.2024 öncesi kararlarda eski metin (açıklamadan itibaren yedi gün) uygulanır.
- Eski YAML: "Ceza temyizi (CMK 291) — tefhimden veya tebliğden itibaren **15 gün**." → **Yanlış (1.6.2024 ve sonrası).** Güncel metin: gerekçeli hükmün tebliğinden itibaren **iki hafta**. 1.6.2024 öncesi kararlarda eski metin uygulanır: "hükmün açıklanmasından itibaren on beş gün", yokluğunda açıklanmışsa tebliğden (eski 291/2) — 7499 md.19 ve CMK geçici m.6/1-c. Eski metni tarihçeden çekme: `legal_get_statute_article_history 5271 291` 2014'te duruyor ve 2017 öncesi "yedi gün" metnini veriyor (on beş günlük 2017-2024 metni yok); `effective_date: 2024-01-01` de güncel metni döndürüyor. Eski metin için RG 12.03.2024 sayı 32487'deki 7499 md.19'u `legal_get_official_gazette_document` ile oku.
- `legal_calculate_deadline` `cmk_appeal` ve `cmk_cassation` 14 gün hesaplıyor; 1.6.2024 öncesi kararlar için **kullanma**, elle hesapla.
- Tutuklu sanık zabıt kâtibine ya da ceza infaz kurumu müdürüne beyan veya dilekçeyle başvurabilir; tutanak düzenlendiği an kanun yolu süresi kesilmiş sayılır (m.273/1, m.291/1 → m.263).

## Zorunlu unsurlar ve şekil
- Başvuru, hükmü veren mahkemeye **dilekçe** ya da **zabıt kâtibine beyan** ile yapılır (m.273/1, m.291/1).
- **İstinafta** sanık, katılan ve katılma hakkı olan suçtan zarar görenin dilekçesinde **sebep gösterilmemesi incelemeye engel değildir** (m.273/4); savcı ise sebepleri gerekçeleriyle göstermek zorundadır (m.273/5). Yine de sebep yazmak inceleme kapsamını yönlendirir.
- **Temyizde** temyiz eden hükmün neden bozulmasını istediğini göstermek **zorundadır**; savcı isteğin sanık lehine mi aleyhine mi olduğunu belirtir (m.294/1). Temyiz sebebi yalnız hükmün **hukuki yönüne** ilişkin olabilir (m.294/2).
- Temyiz nedeni: hükmün hukuka aykırılığı; bir hukuk kuralının uygulanmaması veya yanlış uygulanması (m.288). **Hukuka kesin aykırılık hâlleri** dilekçede gösterilmese de var sayılır (m.289/1 a-i: mahkemenin teşekkülü, yasaklı/reddedilen hâkim, görev-yetki, zorunlu kişilerin yokluğu, açıklık ihlali, gerekçesizlik, savunma hakkının sınırlanması, hukuka aykırı delil).

## BAM'ın verebileceği kararlar (talep sonucunu buna göre yaz)
CMK m.280/1: esastan ret; hukuka aykırılığı düzelterek esastan ret (a-d); m.289 hâllerinde ya da kovuşturma şartı/önödeme/uzlaştırma eksikliğinde **bozma ve ilk dereceye gönderme** (e, f); diğer hâllerde **davanın yeniden görülmesi** ve duruşma sonunda esastan ret ya da **kaldırarak yeniden hüküm** (g, m.280/2).
- Eski YAML "cezada kararın bozulması veya beraat istenir" diyordu → ceza istinafında asıl talep "ilk derece hükmünün **kaldırılarak** yeniden hüküm kurulması (beraat / daha az ceza)"dır; "bozma" yalnız m.280/1-e, f hâllerine dayanıyorsan istenir.

## Duruşmalı temyiz (CMK m.299)
Madde metnindeki hapis süresini aşan hükümlerde Yargıtay **uygun görürse** duruşmalı inceler; tutuklu sanık duruşmaya katılma isteminde bulunamaz. Talep hakkı değil, istem/öneridir. Eski YAML'daki "10 yıl ve üzeri" eşiği teyit edildi; ama "şartlar varsa mutlaka talep et" ifadesi yanıltıcıdır: duruşma Yargıtay'ın takdirindedir.

## Görüşme soruları (data_schema → sorular)
1. Hükmü veren mahkeme, esas/karar no, **hüküm tarihi** (1.6.2024 öncesi mi sonrası mı)?
2. Gerekçeli hüküm size (sanık/müdafi/katılan vekili) hangi tarihte tebliğ edildi? Tefhim tarihi?
3. Başvuran sıfatı: sanık, müdafi, katılan, katılma hakkı olan suçtan zarar gören, savcı?
4. Sanık tutuklu mu?
5. Hüküm: mahkûmiyet (suç, ceza türü ve miktarı, erteleme/seçenek yaptırım/HAGB), beraat, düşme, CVYO?
6. Kesinlik kontrolü için: adli para cezası tutarı, hapis süresi, suçun kanundaki üst sınırı?
7. Usul itirazları: savunma hakkı, delil yasağı, hâkimin reddi, görev/yetki, eksik soruşturma, tanık dinlenmemesi?
8. Esas itirazları: eylemin sübutu, suç vasfı, kast/taksir, indirimler, takdiri indirim, HAGB/erteleme koşulları?
9. (Temyiz için) BAM ne karar verdi: esastan ret, düzelterek ret, yeniden hüküm? Duruşma eşiği aşılıyor mu?
10. Daha önce Yargıtay bozması var mı (m.307/3)?

## soorgla çağrıları
```
legal_get_statute_article law_no: "5271" article_no: "272" | "273" | "280" | "286" | "288" | "289" | "291" | "294" | "299" | "231" | "geçici 6" | "331" | "263" | "307"
legal_get_statute_article_history law_no: "5271" article_no: "273" | "291" include_content: true # 1.6.2024 öncesi kararlar; tarihçe 7499 sürümünü göstermeyebilir
legal_calculate_deadline kural_kodu: "cmk_appeal" | "cmk_cassation" baslangic_tarihi: <gerekçeli hükmün tebliği>
legal_search_cases mahkeme: "yargitay" daire: "Ceza Genel Kurulu" sorgu: "<ilke>"
legal_search_cases mahkeme: "yargitay" sorgu: "<suç + hukuka aykırılık>" tarih_baslangic: <son 3 yıl>
legal_search_cases mahkeme: "bam" sorgu: "<suç + istinaf sebebi>"
legal_get_case_document belge_id: <seçilen güncel karar>
```
Ceza dairelerinin suç türlerine göre iş bölümü değişkendir; "Yargıtay İlgili Ceza Dairesine" yaz, numarayı sabitleme. Kapatıldığı söylenen daireler için kararın tarihine bak ve güncel iş bölümünü `legal_search_official_gazette` ile kontrol et (`query: "Yargıtay Büyük Genel Kurulu Kararı"`, `search_in: "title"`, `sort_by: "date_desc"`; metin uzun, ceza daireleri bölümüne `offset` ile ilerle). Yürürlükteki karar: Yargıtay Büyük Genel Kurulu 29.06.2026 tarihli ve 2026/1 sayılı iş bölümü kararı (RG 30.06.2026, sayı 33296); Resmî Gazete'de yayımını izleyen ayın başından, yani 1 Temmuz 2026'dan itibaren uygulanır ve 12 ceza dairesine (1.-12.) iş dağıtır. Bu karar yıl içinde de bazı işleri daireler arasında devretti (ör. 5464 sayılı Kanun işleri 8. Ceza Dairesinden 11. Ceza Dairesine); bu yüzden dilekçede yine "İlgili Ceza Dairesi" yaz.

## Dilekçe iskeleti
```markdown
[___] BÖLGE ADLİYE MAHKEMESİ İLGİLİ CEZA DAİRESİNE ← istinafta
  (temyizde: YARGITAY İLGİLİ CEZA DAİRESİNE)
Gönderilmek üzere
[___] [___]. [ASLİYE / AĞIR] CEZA MAHKEMESİNE ← temyizde: [___] BAM [___]. CEZA DAİRESİNE

DOSYA NO : [___] Esas — [___] Karar
[İSTİNAF / TEMYİZ] EDEN : [sanık / katılan] [ad soyad], T.C. [___]
MÜDAFİİ / VEKİLİ : Av. [___]
KARŞI TARAF : K.H. / [katılan / sanık] [___]
SUÇ : [___]
HÜKÜM TARİHİ : [___] GEREKÇELİ HÜKMÜN TEBLİĞİ: [___]

KONU : [___] tarihli hükmün [istinaf yoluyla incelenerek KALDIRILMASI ve
                    sanığın BERAATİNE / yeniden hüküm kurulmasına]
                    [temyizde: hukuka aykırılık nedeniyle BOZULMASI] talebidir.

AÇIKLAMALAR
A. Usule ilişkin aykırılıklar [ör. CMK m.289/1-(…) — hukuka kesin aykırılık]
B. Esasa ilişkin aykırılıklar [istinafta: sübut, delil değerlendirmesi, vasıf, yaptırım;
                                 temyizde: yalnız hukuki yön — CMK m.288, m.294/2]
C. Yargıtay / BAM içtihatları [soorgla'dan, en az bir güncel karar tam metni okunmuş]

[DURUŞMA İSTEMİ — yalnız temyizde ve CMK m.299 eşiği aşılıyorsa; tutuklu sanık için değil]

HUKUKİ NEDENLER : CMK m.272 vd. / m.286 vd., [TCK maddeleri]
SONUÇ VE İSTEM : Açıklanan nedenlerle [___] tarihli hükmün [KALDIRILARAK sanığın BERAATİNE /
                    BOZULMASINA], [tutukluluğun değerlendirilmesine] karar verilmesini saygıyla
                    arz ve talep ederim.
                                         [tarih] — Sanık müdafii Av. [___] (e-imza)
```

## Sık hatalar
- 🔴 1.6.2024 öncesi bir hükümde yeni "iki hafta, gerekçeli tebliğden" kuralını uygulamak (ya da tersi).
- 🔴 Kesin hükme (m.272/3) istinaf, temyiz edilemeyen BAM kararına (m.286/2) temyiz dilekçesi yazmak.
- 🔴 1.6.2024 sonrası HAGB'ye "itiraz" dilekçesi vermek; ya da bozma sonrası HAGB'de istinaf/temyiz ayrımını kontrol etmemek.
- 🟠 Temyiz dilekçesinde sebep göstermemek (m.294/1 zorunlu) ya da olay tartışmasıyla doldurmak.
- 🟡 Adli tatil hesabını HMK'nın "bir hafta" kuralıyla yapmak; cezada üç gündür.
