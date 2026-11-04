# Kira sözleşmesi incelemesi

**Ne zaman kullanılır:** kullanıcı imzalanmış ya da imzalanacak bir kira sözleşmesini, ek protokolü, tahliye taahhütnamesini ya da özel şartlar sayfasını getirdiğinde; "bu sözleşmede benim aleyhime ne var", "bu maddeyi koyabilir miyiz" sorularında.

Temel ilke: konut ve çatılı işyeri kirasında hükümlerin çoğu **kiracı lehine emredicidir**. Kira bedelinin belirlenmesi dışında kiracı aleyhine değişiklik yapılamaz (TBK m.343); dava yoluyla sona erdirmeye ilişkin hükümler kiracı aleyhine değiştirilemez (m.354). Aykırı madde sözleşmenin tamamını değil, yalnız o maddeyi (ya da fazla kısmı) geçersiz kılar. 

---

## Adım 0 — Önce yapı, sonra metin (upstream `commercial-legal/review` uyarlaması)

Metni okumadan önce belgelerin listesini çıkar: ana sözleşme (matbu form mu, özel metin mi), "özel şartlar" sayfası, ek protokoller, tahliye taahhütnamesi (ayrı belge mi, sözleşmenin içinde mi, eki mi), demirbaş/teslim tutanağı, depozito makbuzu, kefalet. Her belgenin **tarihini** ayrı yaz: tahliye taahhüdünün geçerliliği, sözleşme ve teslim tarihlerine göre değerlendirilir.

Sonra kiralananı sınıflandır: konut / çatılı işyeri / çatısız alan / taşınır / ürün kirası / altı ay ve daha kısa geçici kullanım. Konut ve çatılı işyeri değilse aşağıdaki listenin 🔴 maddelerinin çoğu uygulanmaz; genel hükümler ve GİK denetimi için `../../sozlesme-incelemesi-tbk/SKILL.md`. 

---

## Kontrol listesi

### 1. Taraflar ve kiralanan
- Kiraya veren malik mi? Değilse (intifa hakkı sahibi, kiracı-alt kiraya veren, vekil) yetki belgesi var mı? Paylı mülkiyette paydaşların çoğunluğu/oybirliği `[incele]`.
- Kiracı tacir ya da tüzel kişi mi? Tacir kiracı için 2012-2020 arasındaki erteleme **sona ermiştir**; bugün konut ve çatılı işyeri hükümleri tacir kiracıya da uygulanır.  
- Kiralanan **aile konutu** mu? Öyleyse kiracı eşin açık rızası olmadan feshedemez; kiracı olmayan eş bildirimle sözleşmenin tarafı olabilir ve o zaman ihtar ve fesih bildirimleri **iki eşe ayrı ayrı** yapılır. 🟠 
- Demirbaş ve eşya listesi var mı? Konut ve çatılı işyeri hükümleri kiracıya bırakılan eşyaya da uygulanır (m.339/1).

### 2. Süre ve yenileme
- Belirli süreli mi, belirsiz süreli mi? Kira yılı başlangıcı hangi gün?
- Belirli süreli konut/çatılı işyeri kirasında kiracı süre bitiminden en az on beş gün önce bildirmedikçe sözleşme **aynı koşullarla bir yıl uzar**; kiraya veren süre bitimine dayanarak sona erdiremez. "Süre sonunda kiracı çıkar" yazan madde kiracıyı bağlamaz. 🔴 
- "On yıllık uzama" sonunda kiraya verenin sebepsiz fesih hakkı — ayrıntı `tahliye-sebepleri.md`.
- Sözleşmedeki "kiracı X ay önce bildirmezse Y yıl uzar" gibi özel uzama maddeleri kiracı lehine ise geçerlidir `[incele]`.

### 3. Kira bedeli ve artış
- Artış maddesi TBK m.344'teki sınırı (bir önceki kira yılının TÜFE on iki aylık ortalamalara göre değişimi) aşıyor mu? Aşan kısım geçersizdir; madde tümden geçersiz olmaz. 🟠 
- Konutta 11.06.2022 - 01.07.2024 arasında yenilenen dönemler için yüzde 25 sınırı vardı (geçici m.1 ve m.2); o dönemlere ilişkin artış ve alacak hesabında hâlâ önemlidir. Ayrıntı `kira-bedeli-artis-ve-tespit.md`.
- **Dövizle kira:** Türkiye'de yerleşikler arasında konut ve çatılı işyeri kirasında bedelin döviz cinsinden ya da dövize endeksli kararlaştırılması 32 sayılı Karar'a ilişkin Tebliğ m.8/2 ile yasaktır. Gayrimenkul kirasında istisnalar: kiracı Türk vatandaşı olmayan Türkiye'de yerleşik kişi ya da m.8/19'daki (dışarıda yerleşiklerin Türkiye'deki şube/temsilcilik, en az %50 paylı şirketleri, serbest bölge şirketleri) kişiyse (m.8/3); Kültür ve Turizm Bakanlığından belgeli konaklama tesisinin işletilmesi için kiralama (m.8/4); gümrüksüz satış mağazası kiralaması (m.8/5). Kamu kuruluşları istisnası (m.8/15) ve havacılık istisnası (m.8/20) gayrimenkul kiralamayı kapsamaz. Tebliğ sık değişiyor; güncel metni `legal_get_statute_article` (`law_no: "11990"`, `law_type: "Tebliğ"`, `article_no: "8"`) ile çek. Döviz kararlaştırılmışsa beş yıl geçmedikçe bedel değiştirilemez (m.344/4). 🟠  
- Ödeme günü, yeri, yöntemi (banka havalesi ispat kolaylığı sağlar).

### 4. Kiracıya yüklenen ek ödemeler
- Kira bedeli ve yan giderler dışında başka ödeme yükümlülüğü getirilemez. **Gecikmede cezai şart** ve "bir kira geç ödenirse kalan tüm kiralar muaccel olur" maddeleri **geçersizdir**. 🔴 
- Sözleşmenin kurulmasını ya da sürdürülmesini, kiracının yararı olmaksızın kullanımla ilgisi olmayan bir borca (ör. kiraya verenden mal alma, sigorta yaptırma) bağlayan bağlantılı sözleşme geçersizdir. 🟠 
- Sona ermede "sözleşmeye aykırı kullanım zararı dışında" önceden kararlaştırılmış tazminat (ör. "çıkışta X kira bedeli boya-badana tazminatı") geçersizdir. 🟠 
- Vergi, sigorta ve kiralananın sürekli yükleri kural olarak kiraya verene aittir (m.302); temizlik ve olağan bakım giderleri kiracıya (m.317); ısıtma, aydınlatma, su gibi kullanma giderleri sözleşme ya da yerel âdet aksini öngörmedikçe kiracıya (m.341). 

### 5. Güvence (depozito)
- Üç aylık kira bedelini aşamaz; para ise vadeli tasarruf hesabına, kıymetli evrak ise bankaya — kiraya verene elden verilmesi kanunun öngördüğü yol değildir. Ayrıntı `depozito-ayip-ve-sona-erme.md`. 🟠 

### 6. Kullanım, bakım, ayıp
- Kiraya verenin teslim ve kullanıma elverişli bulundurma borcu konut ve çatılı işyerinde kiracı aleyhine değiştirilemez: "kiralanan olduğu gibi teslim edilmiştir, hiçbir ayıptan kiraya veren sorumlu değildir" maddesi bu yönüyle geçersizdir. 🟠 
- Kullanım amacı (konut/işyeri) ve amaç değişikliği yasağı açık mı?
- Özenle kullanma ve komşulara saygı borcu (m.316); aykırılıkta yazılı ihtar ve süre (konut/çatılı işyerinde en az 30 gün) gerekir. 
- Yenilik ve değişiklik (m.321): kiracı ancak kiraya verenin **yazılı rızasıyla** yenilik ve değişiklik yapabilir; eski hâle getirme ve değer artışı talepleri yazılı anlaşmaya bağlıdır. 

### 7. Alt kira, devir, kullanım hakkı
- Konut ve çatılı işyerinde kiracı, kiraya verenin **yazılı rızası** olmadıkça alt kiraya veremez, kullanım hakkını devredemez. 
- Kira ilişkisinin devri her zaman yazılı rızaya bağlıdır; **işyerinde** kiraya veren haklı sebep olmadıkça rızadan kaçınamaz ve devreden kiracı en fazla iki yıl müteselsilen sorumlu kalır. 
- Kısa süreli konaklama amaçlı kiralama (ör. günlük kiralık): konutun 100 güne kadar turizm amaçlı kiralanması Kültür ve Turizm Bakanlığından **izin belgesine** bağlıdır; başvuruda binadaki tüm kat maliklerinin oy birliği kararı gerekir; konutu mesken olarak kiralayan kiracı onu kendi nam ve hesabına turizm amaçlı kiraya veremez (7464 m.1-3). İdari yaptırımlar m.4'te (tutarı oradan çek). 

### 8. Sona erme ve tahliye maddeleri
- Kanunda sayılanlar dışında kiracı aleyhine **yeni tahliye sebebi** yaratılamaz ("kiraya veren dilediğinde 1 ay önceden bildirerek feshedebilir" gibi). 🔴 
- Fesih bildirimi yazılı olmalıdır (m.348). 
- **Tahliye taahhüdü sözleşmeyle birlikte mi alındı?** Kiralananın tesliminden önce, sözleşmeyle aynı anda düzenlenen taahhüt geçersizdir; sözleşmenin eki olarak gösterilmesi ya da "taahhüt verilmeden teslim edilmez" maddesi bunun delilidir. 🔴 Ayrıntı `tahliye-sebepleri.md`. 
- Erken çıkış maddesi: kiracı süreye uymadan çıkarsa borcu "benzer koşullarla yeniden kiraya verilebileceği makul süre" kadar sürer; sabit "kalan sürenin tüm kirası" kaydı bu ölçüyle denetlenir `[incele]`. 

### 9. Kiraya veren tarafı — güvenceyi kanuna uygun kur
Kiraya verenle çalışıyorsan geçersiz maddeleri silmek yerine kanuna uygun karşılıklarını öner: gecikme cezası yerine temerrüt faizi ve m.315 ihtarı; geçersiz önceden tahliye taahhüdü yerine teslimden sonra serbest iradeyle alınacak taahhüt (bkz. `tahliye-sebepleri.md`); m.342'ye uygun depozito; kefalet için TBK kefalet şekil şartları: yazılı şekil, azami miktar ve tarih, bunların ve müteselsillik sıfatının kefilin **el yazısıyla** belirtilmesi (m.583); evli kefilde eşin önceden ya da en geç kurulma anında **yazılı rızası** (m.584; ticari işletme ve esnaf istisnaları) (`../../sozlesme-incelemesi-tbk/SKILL.md`). 

---

## Süreler (sözleşmede kontrol edilecek)

| Süre | Dayanak | Not |
|---|---|---|
| Kiracının belirli süreli sözleşmede sona erdirme bildirimi: süre bitiminden **en az 15 gün önce** | TBK m.347/1  | Bildirmezse bir yıl uzar. |
| Kiracının temerrüdünde ödeme süresi: konut/çatılı işyerinde **en az 30 gün** | TBK m.315  | Sözleşmede daha kısa süre yazılması kiracıyı bağlamaz. |
| Kira bedelinde zamanaşımı: **5 yıl** | TBK m.147/1  | Her dönem kirası ayrı muaccel olur. |
| Depozitonun bankadan iadesi: sona ermeden sonra **3 ay** içinde kiraya veren dava/takip bildirmezse | TBK m.342/3  | |

---

## Görüşme soruları

1. Kimin adına inceliyoruz? (kiraya veren / kiracı)
2. Kiralanan ne? (konut / dükkân, ofis gibi çatılı işyeri / arsa / depo / eşyalı)
3. Sözleşme başlangıç tarihi, süresi, kira yılı başlangıcı? Kiralanan ne zaman teslim edildi?
4. Belgeler: ana sözleşme, özel şartlar, ek protokol, tahliye taahhüdü, teslim tutanağı — her birinin tarihi?
5. Aylık kira, ödeme şekli, artış maddesi, döviz kaydı?
6. Depozito tutarı, nerede tutuluyor (elden / banka)?
7. Taraflardan biri tacir ya da şirket mi? Kiracı evli mi, aile konutu mu?
8. Kefil var mı?
9. Sözleşmede özel tahliye, ceza, erken çıkış maddeleri var mı?

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6098"  article_no: "339" | "343" | "344" | "346" | "340" | "342" | "334" | "322" | "323" | "347" | "348" | "349" | "354"
legal_list_statute_articles  law_no: "6098"  article_kind: "gecici"  include_content: true      # yüzde 25 dönemi
legal_search_statute_semantic  sorgu: "yerleşikler arası kira sözleşmesinde döviz cinsinden bedel"   # dövizli kira
legal_search_cases  mahkeme: "yargitay"  daire: "3. Hukuk Dairesi"  sorgu: "<madde sorunu, ör. kira sözleşmesinde gecikme cezai şartı geçersiz>"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  <son 3 yıldan en az bir karar>
```

## Çıktı iskeleti

```markdown
## Kira sözleşmesi incelemesi: [kiraya veren/kiracı adına] — [tarih]
**Belgeler:** [liste + tarihler] · **Kiralanan:** [konut/çatılı işyeri/diğer] · **Uygulanan rejim:** [TBK m.339-356 / genel hükümler]

### Sonuç
[İmzalanabilir / şu maddeler düzeltilmeli / dur]

### Madde madde bulgular
| Madde | Sorun | İşaret | Dayanak | Önerilen değişiklik |

### Geçersiz ya da kısmen geçersiz maddeler
### Kiracı/kiraya veren için eksik güvenceler
### Takvim (sözleşmeden çıkan bildirim ve uzama tarihleri) → `kira-takvimi-ve-ihtarlar.md`
### Eksik bilgi
```

## Sık hatalar

- 🔴 Gecikme cezası ya da kalan kiraların muacceliyeti maddesini geçerli saymak (m.346).
- 🔴 Sözleşmeyle aynı gün imzalatılan tahliye taahhüdüne güvenmek.
- 🟠 "Süre sonunda kiracı tahliye eder" maddesini kiraya verene tahliye hakkı veriyor sanmak (m.347).
- 🟠 Çatılı işyeri kiracısı tacir diye kira hükümlerinin uygulanmadığını söylemek (erteleme 2020'de bitti).
- 🟠 Depozitonun üç aylık kirayı aşan kısmını "anlaşmayla geçerli" saymak.
- 🟡 Çatısız arsa ya da otopark kirasına konut ve çatılı işyeri korumalarını uygulamak.

