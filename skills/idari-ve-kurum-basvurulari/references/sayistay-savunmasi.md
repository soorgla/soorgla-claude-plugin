# Sayıştay sorgusuna ve denetim raporuna savunma (kamu zararı)

Harcama yetkilisi, gerçekleştirme görevlisi, muhasebe yetkilisi gibi sorumluların Sayıştay denetçisinin tespitine (sorgu / yargılamaya esas rapor öncesi savunma istemi) ya da iç denetim/müfettiş raporuna karşı yazdığı savunma. Amaç: işlemin **mevzuata uygun** olduğunu ya da **kamu zararının unsurlarının oluşmadığını** göstermek.

Kamu personeli disiplin savunması (657) bu dosyanın konusu değildir.

---

## Süre ve dayanak

| İşlem | Kural | Dayanak |
|---|---|---|
| Savunma süresi | Kamu zararına yol açan husus tespit edildiğinde sorumluların **savunması alınır**; **tebliğ tarihinden itibaren 30 gün** içinde cevap vermeyen sorumluların savunmaları yargılamaya esas raporun düzenlenmesinde **dikkate alınmaz** | 6085 m.48/1 |
| Rapor akışı | Yargılamaya esas rapor mali yıl sonu itibarıyla düzenlenir (m.6/4 halleri hariç); Başkanlık en geç 15 gün içinde hesap yargılaması yapacak daireye gönderir | 6085 m.48/1-2 |
| İç denetim / müfettiş raporu → kamu zararı tebliği | Kontrol, denetim veya inceleme (ya da Sayıştay sorgusu üzerine yapılan değerlendirme) sonucu tespit edilen kamu zararı alacağı sorumluya tebliğ edilir; tebliğde **ödeme, itiraz veya sulh teklifi için 30 gün** verilir; itiraz merkezde üst yönetici, taşrada en üst yönetici tarafından **15 gün** içinde sonuçlandırılır, sonuçlanmazsa **reddedilmiş sayılır**; ödenmezse dosya hukuk birimine gönderilir. Raporun kendisine savunma süresi kurumun teftiş/denetim yönetmeliğindedir — o yönetmeliği ayrıca çek | Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmelik m.10/2-4 (Değişik: RG 15.06.2019, CK 1147) |
| Hesap yargılaması sonrası | Daire ilamına karşı **Sayıştay Temyiz Kurulu**na temyiz: ilamın ilgiliye **tebliğinden itibaren 60 gün**; sebepler kanuna aykırılık, yetki aşımı, usule uymama vb.; Temyiz Kurulu kararları kesindir | 6085 m.55/1-3 |

Eski YAML "sorgu tebliğinden itibaren 30 gün içinde cevap verilmelidir" diyordu; kanunun sonucu "cevap verilmezse savunma **dikkate alınmaz**"dır — süre geçince savunma yapılamaz değil, rapor savunmasız düzenlenebilir. Yine de süreyi kaçırmamak esastır (🔴).

`legal_calculate_deadline` bu süreyi tanımaz; elle hesapla, `legal_check_holiday`, `[doğrula]`.

## Kamu zararının unsurları — savunmanın iskeleti

5018 m.71'e göre kamu zararı: kamu görevlilerinin **kasıt, kusur veya ihmalinden** kaynaklanan **mevzuata aykırı** karar, işlem veya eylem sonucunda kamu kaynağında **artışa engel olunması veya eksilmeye neden olunması**dır. Belirlenmesinde esas alınan hâller: fazla ödeme, iş/mal/hizmet alınmadan ödeme, transfer giderlerinde fazla/yersiz ödeme, rayiç bedelden yüksek alım, gelirlerin tarh-tahakkuk-tahsilinin mevzuata aykırılığı, mevzuatta öngörülmediği hâlde ödeme. Zarar, oluştuğu tarihten itibaren faiziyle tahsil edilir.

Savunmayı unsur unsur kur (eski YAML yalnız ilk iki unsuru anıyordu):
1. **Mevzuata aykırılık yok:** işlemin dayanağı olan madde (4734, 657, 6245, ek ders mevzuatı vb.) — çek ve alıntıla.
2. **Kaynakta eksilme/artışa engel yok:** iş yapıldı, mal alındı, hizmet sağlandı; bedel rayice uygun; kamu yararı.
3. **Kusur yok / sorumluluk başkasında:** harcama yetkilisi, gerçekleştirme görevlisi ve muhasebe yetkilisinin görev sınırları; talimat, onay zinciri.
4. **Tutar:** hesaplama hatası, mahsup, iade edilmiş tutar.
5. Lehe **Sayıştay daire / Temyiz Kurulu / Daireler Kurulu** kararları.

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `authority_name` | Savunma kime sunulacak? (Sayıştay denetçisi aracılığıyla Başkanlık, ilgili daire, müfettişlik) Belgede bu nasıl yazıyor? |
| `query_reference` | Sorgu / rapor / savunma istem yazısının tarih ve sayısı? **Tebliğ tarihi?** |
| `defendant_info` | Savunma yapan: ad-soyad, unvan, işlem tarihindeki görevi (harcama yetkilisi mi, gerçekleştirme görevlisi mi, muhasebe yetkilisi mi)? |
| `subject_summary` | Hangi maddeye/bulguya savunma? |
| `allegation_details` | Denetçinin tespiti ve hesapladığı tutar? (belgeyi isteyin) |
| `defense_arguments` | İşlem neden yapıldı, dayanağı ne, iş/mal/hizmet alındı mı, kim onayladı? |
| (yeni) | Tutar iade edildi ya da mahsup edildi mi? |
| `relevant_precedents` / `legal_reasons` | (Araştırma adımında doldurulur.) |
| `conclusion_request` | Talep: kamu zararı oluşmadığından ilişiğin kesilmesi / tazmin hükmü verilmemesi? |

## soorgla çağrıları

```
legal_get_statute_article law_no: "6085" article_no: "48" | "6" | "55"
legal_get_statute_article law_no: "5018" article_no: "71" | "32" | "33" | "61"
legal_get_statute_article law_no: "<4734 | 657 | 6245 | …>" article_no: "<işlemin dayanağı>"
legal_search_cases mahkeme: "sayistay" sorgu: "<ör. ek ders ücretinin mevzuata aykırı ödenmesi kamu zararı oluşmadığı>" tarih_baslangic: "<son 3 yıl>"
legal_get_case_document belge_id: "<seçilen karar>"
legal_resolve_statute query: "Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmelik"
```
Ek kaynak: `bureaucrat.audit_accountability.audit_query_defense` ajanı yoktur; karşılığı yukarıdaki çağrılardır.

## Savunma iskeleti

```markdown
[SAYIŞTAY BAŞKANLIĞINA / … DENETİM GRUBU BAŞKANLIĞINA / … MÜFETTİŞLİĞİNE]
([Denetçi aracılığıyla])

SORGU / RAPOR TARİH-SAYISI : [___] TEBLİĞ TARİHİ: [___]
SAVUNMA YAPAN : [Ad SOYAD — işlem tarihindeki unvanı ve sıfatı]
KONU : [___] tarihli ve [___] sayılı [sorgu / rapor]un [___] maddesine ilişkin savunmamdır.

1. İDDİA / BULGU
[Denetçinin tespitinin tarafsız özeti ve tutar]

2. SAVUNMAM VE HUKUKİ AÇIKLAMALAR
a) İşlemin dayanağı ve mevzuata uygunluğu: [madde alıntılarıyla]
b) Kamu kaynağında eksilme / artışa engel olunmadığı: [iş/mal/hizmetin alındığı, rayiç bedel]
c) Kusur ve sorumluluk: [görev sınırları, onay zinciri]
d) Tutar yönünden: [hesap hatası, iade, mahsup]

3. EMSAL KARARLAR
[Sayıştay daire / Temyiz Kurulu / Daireler Kurulu kararları — her biri neyi desteklediğiyle]

HUKUKİ DAYANAK: 5018 sayılı Kanun m.71; 6085 sayılı Kanun m.48; [işlemin dayanağı mevzuat]

SONUÇ VE İSTEM: Açıklanan nedenlerle anılan işlemde kamu zararı oluşmadığından hakkımda tazmin hükmü
verilmemesini / ilişiğimin kesilmesini saygılarımla arz ederim.

[Tarih] [Ad SOYAD]
                                                           [Unvan — imza]
EKLER: [ödeme belgeleri, hakediş, muayene-kabul tutanağı, olur, yazışmalar]
```

## Sık hatalar

- 🔴 30 günü kaçırmak (savunma rapora girmez).
- 🟠 Yalnız "mevzuata uygun" demek; zararın ve kusurun yokluğunu ayrıca göstermemek.
- 🟠 Sorumluluk sıfatını (harcama yetkilisi / gerçekleştirme görevlisi / muhasebe yetkilisi) karıştırmak.
- 🟡 Emsal kararı tam metnini okumadan, yalnız özetinden aktarmak.

---
