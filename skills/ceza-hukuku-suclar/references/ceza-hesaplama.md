# Ceza hesabı — temel cezadan sonuç cezaya

## Ne zaman kullanılır
- "Ne kadar ceza çıkar?", "kaç yıl yatarım?", "mahkeme cezayı doğru hesapladı mı?" soruları.
- Gerekçeli kararın ya da istinaf/temyiz dilekçesinin hazırlığında ceza hesabının denetimi (eski `appellate_remedies` YAML'ındaki "TCK 61'deki zincirleme suç, takdiri indirim ve tekerrür kurallarına uygun hesaplanmış mı" maddesi).
- HAGB, erteleme, seçenek yaptırım ve önödeme eşiklerine **sonuç cezanın** düşüp düşmediğini görmek için (→ `yaptirimlar-hagb-erteleme.md`).

**MCP uyarısı:** TCK m.61 (cezanın belirlenmesi) soorgla'da **yok**. Aşağıdaki sıra Yargıtay uygulamasının ve madde metninin bilinen yapısıdır; her kullanımda `[madde çekilemedi — doğrulayın]` etiketiyle ver ve son 3 yıldan bir Yargıtay kararıyla teyit et. m.61/1 ölçütleri (a-g bentleri) Yargıtay CGK'nin tam metin alıntısıyla doğrulandı (CGK, E. 2024/131, K. 2024/226, 10.07.2024). m.61/2 ve sonrası (artırım-indirim **sırası**) doğrulanmadı: hesabı kullanıcıya vermeden önce **TCK m.61 metnini Resmî Gazete / mevzuat.gov.tr'den teyit et** (ya da m.61/2-5'i aynen alıntılayan güncel bir CGK kararını `legal_search_cases` ile bulup tam metnini oku); teyit edemezsen 2. adımdan sonraki sırayı `[ARAŞTIRMA GEREKLİ: TCK m.61/2-5 metni]` etiketiyle ver.

Bu dosyaya hiçbir suçun ceza aralığı yazılmaz; aralık her seferinde suç maddesinden çekilir.

---

## Hesap sırası (iskelet)

| Adım | İşlem | Dayanak | Not |
|---|---|---|---|
| 0 | Suç tarihindeki madde metnini ve **lehe kanunu** belirle | TCK m.7 | Lehe olan kanun bütün olarak uygulanır `[incele]` |
| 1 | **Temel ceza:** alt-üst sınır arasında; işleniş biçimi, kullanılan araçlar, zaman ve yer, suçun konusunun önem ve değeri, zararın ağırlığı, kast veya taksirin ağırlığı, güdülen amaç ve saik ölçütleriyle. Alt sınırdan uzaklaşma **gerekçe** ister | TCK m.61/1 (metin: Yargıtay CGK E. 2024/131, K. 2024/226 alıntısı) | Gerekçesiz üst sınırdan uzaklaşma bozma nedenidir `[incele]` |
| 1a | Olası kast varsa indirim **temel ceza üzerinden** | TCK m.21/2 | |
| 2 | **Nitelikli hâller** (artırım ve indirim gerektiren unsurlar): önce artırım, sonra indirim | TCK m.61/3-4 `[madde çekilemedi]` | Birden fazla nitelikli hâl varsa her biri ayrı değil; temel cezaya bir kez `[incele]` |
| 3 | **Teşebbüs** | TCK m.35 | |
| 4 | **İştirak** (yardım etme indirimi) | TCK m.39 | |
| 5 | **Zincirleme suç** artırımı | TCK m.43 | Kasten öldürme, kasten yaralama, işkence, yağmada yok |
| 6 | **Haksız tahrik** | TCK m.29 | |
| 7 | **Yaş küçüklüğü** | TCK m.31 | 7593 sonrası aralıklar değişti; olay tarihine bak |
| 8 | **Akıl hastalığı** (azalmış kusur) | TCK m.32/2 | |
| 9 | **Takdiri indirim**: ağırlaştırılmış müebbet ve müebbette belirli süreli cezaya; diğer cezalarda altıda birine kadar | TCK m.62 | Gerekçe: "sanığın geçmişi, yargılama sürecindeki davranışı" somut yazılmalı |
| 10 | **Özel indirimler**: etkin pişmanlık (TCK 168, 192, 221, 248, 254 vb.), suça özgü indirimler (ör. TCK 145 değer azlığı) | ilgili madde | Uygulama sırası kararlarda tartışmalı; özel hükmün kendi sırası varsa ona uy `[incele]` |
| 11 | **Adli para cezası**: gün sayısı ayrı belirlenir, sonra gün başına miktar (TCK m.52) | TCK m.52 | Gün başına miktar sınırları metinden, `[doğrula]` |
| 12 | Sonuç ceza → **seçenek yaptırım / erteleme / HAGB** uygunluğu | TCK m.50, 51; CMK m.231 | → `yaptirimlar-hagb-erteleme.md` |
| 13 | **Tekerrür**: cezayı artırmaz; mükerrirlere özgü infaz rejimi ve cezanın infazından sonra denetim | TCK m.58 | Önceki hükmün kesinleşme ve infaz tarihleri, süre penceresi |
| 14 | **Hak yoksunlukları ve güvenlik tedbirleri** (TCK m.53, 54 müsadere, 57 akıl hastası) | TCK m.53-60 | AYM iptal kararlarıyla şekillendi, metinden çek `[doğrula]` |

**Gün/ay/yıl hesabı:** hapis cezası yıl-ay-gün olarak yazılır. Kesirli indirim/artırımda gün küsurunun nasıl ele alınacağı ve ayın kaç gün sayılacağı kuralını hesaptan önce kanun metninden teyit et: TCK m.61'in son fıkraları MCP'de yok → Resmî Gazete / mevzuat.gov.tr'den oku; adli para cezası için TCK m.52'yi `legal_get_statute_article` (5237, 52) ile çek. Teyit edemezsen sonucu `[ARAŞTIRMA GEREKLİ: gün küsuru kuralı]` etiketiyle ver.

---

## Kontrol listesi — mahkemenin hesabını denetleme

1. Temel ceza alt sınırdan uzaklaştırıldıysa gerekçe **somut** mu (aynı olgu hem temel cezada hem nitelikli hâlde iki kez kullanılmış mı)? 🟠
2. Sıra doğru mu (ör. takdiri indirim haksız tahrikten önce yapılmış mı)? Yanlış sıra çoğu zaman farklı sonuç verir. 🔴
3. Zincirleme suç artırımı uygulanamayacak bir suça uygulanmış mı (m.43/3)? 🔴
4. Etkin pişmanlık şartları (zararın tamamen giderilmesi, zamanı, kısmi iadede mağdur rızası) dosyada var mı ve uygulanmış mı?
5. Suç tarihinden sonra ceza aralığı değiştiyse lehe olan uygulanmış mı (7571, 7593, 7589 sonrası)?
6. Adli para cezasında gün sayısı ile gün başına miktar ayrı ayrı gerekçelendirilmiş mi?
7. Çocuk sanıkta 7593 ile eklenen m.31/4 (kasten öldürme ve m.87/2-4'te indirimin uygulanmayabilmesi) gerekçesi yazılmış mı ve suç tarihi 18.08.2026'dan sonra mı?
8. Tekerrür hükmüne esas alınan ilam yargılamanın yenilenmesi ya da kanun değişikliği nedeniyle etkisini yitirmiş mi?

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Suç tarihi? | Uygulanacak ceza aralığı |
| Adli sicil kaydı (kasıtlı suçtan mahkûmiyet, tarih, ceza, infaz tarihi)? | Tekerrür, HAGB, erteleme |
| Zarar giderildi mi, ne zaman (soruşturma / kovuşturma / hükümden sonra)? | Etkin pişmanlık oranı |
| Olay anında yaş? | m.31 |
| Mağdurdan gelen haksız bir hareket var mı? | m.29 |
| Mahkemenin hüküm fıkrası (varsa) — her adımın oranı | Hesap denetimi |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "5237" law_type: "Kanun" article_no: "<suç maddesi>" # ceza aralığı
legal_get_statute_article law_no: "5237" law_type: "Kanun" article_no: "21" | "29" | "31" | "43" | "50" | "51" | "62" | "168"
legal_search_statute_semantic mevzuat_no: "5237" sorgu: "takdiri indirim nedenleri" # m.62 (m.61 dönmüyor)
legal_search_cases mahkeme: "yargitay" daire: "Ceza Genel Kurulu" sorgu: "TCK 61 uyarınca cezanın belirlenmesinde uygulama sırası temel cezanın alt sınırdan uzaklaşılması gerekçesi"
```

---

## Çıktı iskeleti

```markdown
## Muhtemel ceza hesabı — [suç, madde] (suç tarihi [GG.AA.YYYY])
> Bu tablo bir senaryodur; temel cezanın belirlenmesi ve indirim oranları hâkimin takdirindedir [incele].

| Adım | İşlem | Oran / gerekçe | Ara sonuç | Dayanak |
| 1 | Temel ceza (alt sınır senaryosu) | — | … | [suç maddesi] |
| … | … | … | … | … |
| Sonuç | Hapis / adli para | | … | |

### Senaryolar
| Senaryo | Varsayım | Sonuç ceza | HAGB | Erteleme | Seçenek yaptırım |
| İyimser | alt sınır, tahrik 3/4, takdiri 1/6 | … | … | … | … |
| Kötümser | … | … | … | … | … |
```

---

## Sık hatalar

- 🔴 Sonuç cezayı "kesin" diye sunmak; her hesap senaryodur.
- 🔴 TCK m.61'i "soorgla'dan çekildi" diye etiketlemek — araçta yok.
- 🟠 Tekerrürü ceza artırımı gibi hesaba katmak.
- 🟠 Takdiri indirimi (m.62) haksız tahrikten önce uygulamak.
- 🟡 Adli para cezasında gün sayısını ve gün başına miktarı tek kalemde göstermek.

---
