# Delil tespiti (değişik iş)

## Ne zaman kullanılır
Görülmekte olan davada inceleme sırası henüz gelmemiş ya da ileride açılacak davada ileri sürülecek bir vakıanın **şimdi** keşif, bilirkişi incelemesi ya da tanık ifadesiyle tespiti: su sızıntısı hasarı, inşaat seviyesi, ayıplı mal, bozulacak ürün, yıkılacak yapı.

Alternatif: noterin vakıa tespiti (1512 s. Noterlik Kanunu) saklıdır — fotoğraflı tespit için daha hızlı olabilir `[incele]`.

---

## Şartlar, merci ve süre tablosu

| Kural | Dayanak | Not |
|---|---|---|
| **Hukuki yarar** şarttır; kanunda açıkça öngörülen hâller dışında, delil hemen tespit edilmezse **kaybolacak** ya da ileri sürülmesi **önemli ölçüde zorlaşacaksa** hukuki yarar var sayılır | HMK m.400/2 | "Neden şimdi?" sorusunun somut cevabı dilekçenin kalbidir. |
| Dava açılmadan önce: **esas davaya bakacak mahkeme** ya da keşif/bilirkişi konusu şeyin bulunduğu veya tanığın oturduğu yer **sulh hukuk mahkemesi** | HMK m.401/1 | Eski YAML "genellikle taşınmazın bulunduğu yer nöbetçi sulh hukuk" diyordu — seçeneklerden biridir, tek seçenek değildir. |
| Esas davada tespit yapan mahkemenin görevsiz/yetkisiz olduğu ileri sürülemez | HMK m.401/3 | |
| Dava açıldıktan sonra: **yalnız davaya bakan mahkeme** | HMK m.401/4 | |
| Dilekçe içeriği: tespiti istenen vakıa; tanık/bilirkişiye sorulacak sorular; kaybolma/zorlaşma kuşkusunun sebepleri; aleyhine tespit istenenin ad, soyad, adresi (koşullar imkân vermiyorsa gösterilmeyebilir) | HMK m.402/1 | |
| Tespit giderleri **avans** olarak ödenmedikçe işlem yapılmaz | HMK m.402/2 | |
| Karar dilekçeyle karşı tarafa tebliğ edilir; karşı taraf itiraz ve ilave sorularını **bir hafta** içinde bildirir | HMK m.402/3 | |
| Tespitten sonra tutanak ve rapor karşı tarafa **re'sen tebliğ** | HMK m.402/4 (7251/44 ile ek, 2020) | |
| **Acele hâlde** karşı tarafa tebligatsız tespit; sonra re'sen tebliğ; karşı taraf tebliğden itibaren **bir hafta** içinde itiraz | HMK m.403 | Zorunluluğu gerekçelendir. |
| Adli tatil | HMK m.103/1-a | Delil tespiti adli tatilde de görülür. |

Delil tespiti sonrası dava açma süresi HMK'da öngörülmemiştir (ihtiyati tedbirdeki m.397 gibi bir süre yok); ama maddi hukuk süreleri (ayıp ihbarı, zamanaşımı) işlemeye devam eder `[incele]`.

**Arama kapsamı uyarısı:** "delil tespitinde hukuki yarar" araması bu turda tespit davası kararları döndürdü (Yargıtay 9. HD 2025 kararları, konu dışı). Delil tespiti kararlarının çoğu değişik iş olarak sulh/asliye mahkemesinde ve itiraz üzerine BAM'da kalır; `mahkeme: "bam"` ve `mahkeme: "mahkeme"` ile ara, zayıf dönerse ORTAK-KURALLAR.md §5 seçeneklerini sun.

---

## Görüşme soruları (eski `data_schema`)
1. Dava açıldı mı? Açılmadıysa hangi mahkeme seçilecek (esas mahkeme / şeyin bulunduğu yer sulh)? — `court_name`
2. Tespit isteyen ve aleyhine tespit istenen (adres bilinmiyor mu?) — `requesting_party`, `opposing_party`
3. Vekil bilgisi — `legal_representatives`
4. Tespiti istenen vakıa tam olarak ne? Adres / ada-parsel / ürün seri no — `subject_summary`, `facts_narrative`
5. Neden şimdi? (onarım başlayacak, inşaat devam ediyor, mal bozulacak, yağmur, tarih) — `urgency_justification`
6. Bilirkişiye sorulacak sorular (maddeler hâlinde, teknik ve ölçülebilir) — `questions_for_expert`
7. Karşı tarafa haber verilmeden mi yapılmalı (m.403)? Neden?
8. Elinizdeki fotoğraf, tapu, sözleşme — `evidence_list`
9. Hangi uzmanlık gerekiyor (inşaat, makine, gıda, bilişim)?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6100" article_no: "400" | "401" | "402" | "403" | "404" | "405" | "406"
legal_search_cases sorgu: "delil tespiti talebi reddi hukuki yarar delilin kaybolma tehlikesi itiraz" mahkeme: "bam" tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar>
legal_calculate_court_fee harc_turu: "basvurma_sulh" # sulh mahkemesine başvuruluyorsa; değilse basvurma_asliye
```

## Dilekçe iskeleti (eski `ui_config`: başlık → taraflar → konu → hukuki yarar ve aciliyet → açıklamalar → bilirkişi soruları → hukuki sebepler/deliller → sonuç)
```markdown
[YER] NÖBETÇİ SULH HUKUK MAHKEMESİ'NE [ya da esas davaya bakacak mahkeme / dava içindeyse: DOSYA NO]

TESPİT İSTEYEN : [___] — VEKİLİ: Av. [___]
ALEYHİNE TESPİT İSTENEN : [___] [adres gösterilemiyorsa nedeni]
KONU : [adres / ada-parsel] [vakıa] ile [zarar/onarım bedeli]'nin bilirkişi marifetiyle keşfen tespiti talebidir.

HUKUKİ YARAR VE ACİLİYET (HMK m.400/2)
[Delil hemen tespit edilmezse neden kaybolacak / zorlaşacak — somut olay ve tarih]

AÇIKLAMALAR
1. [___]

BİLİRKİŞİ TARAFINDAN CEVAPLANMASI İSTENEN HUSUSLAR (HMK m.402/1)
1. [ölçülebilir soru]
2. …

HUKUKİ SEBEPLER : HMK m.400-403, [___]
DELİLLER : [fotoğraf, tapu, sözleşme …]
SONUÇ VE İSTEM : [Karşı tarafa tebligat yapılmaksızın (HMK m.403)] mahallinde keşif yapılarak [uzmanlık] bilirkişi marifetiyle yukarıdaki hususların tespitine, tespit tutanağı ve raporun tarafımıza tebliğine karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```

## Sık hatalar
- 🔴 Aciliyet soyut ("delil kaybolabilir"); somut olay yok.
- 🟠 Bilirkişi soruları hukuki nitelendirme içeriyor ("kusur kimde") — teknik ölçüm sor.
- 🟠 Dava açıldıktan sonra başka mahkemeden tespit istenmiş.
- 🟡 Maddi hukuk süreleri (ayıp ihbarı, zamanaşımı) tespit beklenirken kaçırılmış.
