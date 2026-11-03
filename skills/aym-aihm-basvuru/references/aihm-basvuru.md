# Avrupa İnsan Hakları Mahkemesi (AİHM) başvurusu

## Ne zaman kullanılır

Türkiye aleyhine, Sözleşme ya da Türkiye'nin taraf olduğu bir protokoldeki hakkın ihlali iddiasıyla bireysel başvuru (Sözleşme m.34) yapılacaksa ve iç hukuk yolları — **AYM bireysel başvurusu dahil** — tüketildiyse kullanılır. AİHM, AYM bireysel başvurusunu Türkiye bakımından tüketilmesi gereken etkili bir iç hukuk yolu sayar.

Önce şunu sor: **AYM süreci nerede?**
- AYM'ye hiç başvurulmadıysa ve 30 günlük süre işliyorsa → önce `aym-bireysel-basvuru.md`.
- AYM'ye başvuruldu, karar bekleniyor → AİHM başvurusu genellikle erken (tüketilmemiş) sayılır `[incele]`.
- AYM süre aşımıyla ya da tüketilmeme nedeniyle kabul edilemez dedi → iç hukuk yolu usulüne uygun tüketilmemiş olabilir; AİHM'de de kabul edilemezlik riski yüksek 🔴 `[incele]`.
- AYM esastan ihlal yok ya da açıkça dayanaktan yoksun dedi → AİHM yolu açık; süre AYM kararının öğrenilmesinden başlar.
- AYM ihlal buldu ama giderim yetersiz → mağdur sıfatının devam edip etmediği `[incele]`.

**Kaynak sınırı:** AİHS, Protokoller ve AİHM İçtüzüğü (Rules of Court) soorgla mevzuat katalogunda **yok**. Hükümleri AİHM kararlarındaki alıntılardan çek (`legal_search_cases mahkeme: "aihm"`); kararda görünmeyen her usul kuralını `[model bilgisi — doğrulayın]` etiketle ve kullanıcıyı Mahkeme'nin resmî sitesindeki güncel İçtüzük ve "Pratik Rehber"e yönlendir.

---

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| **4 ay** | İç hukuktaki nihai kararın (çoğunlukla AYM kararı) öğrenildiği/tebliğ edildiği tarih | Sözleşme m.35/1, 15 No.lu Protokol m.4 ile değişik | `legal_calculate_deadline` hesaplamaz → elle hesapla, `[doğrula]` |
| Geçiş: **6 ay** | Nihai iç karar **1 Şubat 2022'den önce** verildiyse | 15 No.lu Protokol geçiş hükmü | 2026'da pratikte yalnız eski dosyalarda |

**Eski YAML düzeltmesi:** YAML "1 Şubat 2022'den itibaren 6 aydan 4 aya indirildi" diyordu. Doğrusu: Protokol 1 Ağustos 2021'de yürürlüğe girdi; 4 aylık süre **1 Şubat 2022 ve sonrasında verilen nihai iç kararlara** uygulanır (yukarıdaki künyeler).

**Hesap kuralları:**
- Süre, nihai iç kararın tebliğini izleyen günden başlar ve takvim ayı olarak hesaplanır; son gün Türk resmî tatiline, cumartesi ya da pazara denk gelse de **uzamaz**. AİHM süreyi iç hukuka göre değil Sözleşme ölçütlerine göre hesaplar; Türk tatil takvimi geçerli değildir. Bu yüzden `legal_check_holiday` sonucu AİHM süresini değiştirmez. (Kararda son günü pazara denk gelen başvuru, ertesi iş günü yapıldığı için süre aşımı sayıldı.)
- Başvuru tarihi, İçtüzük m.47'deki şartları eksiksiz karşılayan formun **gönderildiği** (posta damgası) tarihtir; eksik form süreyi kesmez. Posta damgası belirlenemezse Mahkeme özel durumlarda formun tarihini ya da kayda giriş tarihini esas alabilir.
- Bu nedenle son güne bırakma; posta süresi ve eksik tamamlama riski için en az **2 hafta** pay bırak `[incele]`.

---

## Kabul edilebilirlik kontrol listesi (Sözleşme m.35)

| # | Ölçüt | Kontrol |
|---|---|---|
| 1 | Süre (4 ay / geçişte 6 ay) | Yukarıdaki tablo; AYM kararının öğrenilme tarihi ve kanıtı |
| 2 | İç hukuk yollarının tüketilmesi (m.35/1) | AYM bireysel başvurusu yapıldı mı ve **usulüne uygun** mu (süresinde, ilgili şikâyet AYM'de ileri sürüldü mü)? AYM'de ileri sürülmeyen şikâyet AİHM'de de tüketilmemiş sayılır `[incele]`. Makul süre şikâyetinde Tazminat Komisyonu (6384) yolu |
| 3 | Kişi bakımından: mağdur sıfatı (m.34) | Doğrudan etkilenme; AYM ihlal bulup yeterli giderim sağladıysa mağdur sıfatı kalkabilir `[incele]` |
| 4 | Konu bakımından | Hak Sözleşme'de ya da **Türkiye'nin onayladığı** protokolde mi? **4 No.lu Protokol:** Türkiye taraf değildir (seyahat/serbest dolaşım şikâyeti bu yüzden AYM'de de konu bakımından yetkisizlikle reddedilir). **7 No.lu Protokol:** onaylanması 6684 sayılı Kanunla uygun bulunmuştur (RG 25.03.2016). **12 No.lu Protokol:** AYM kararlarında "imzalanmış, henüz onaylanmamış" olarak geçer. **16 No.lu Protokol** ve yukarıdakilerin **bugünkü** onay/yürürlük durumu: soorgla'da antlaşma kaydı yok → kullanıcıya Avrupa Konseyi Antlaşma Ofisi'nden (coe.int, "Chart of signatures and ratifications") teyit ettir; teyit yoksa dilekçede `[ARAŞTIRMA GEREKLİ: Protokol onay durumu]` yaz. |
| 5 | Açıkça dayanaktan yoksunluk (m.35/3-a) | Dördüncü derece şikâyeti mi? |
| 6 | Önemli zarar (m.35/3-b) | Başvuranın "önemli bir zarara" uğrayıp uğramadığı ve insan haklarına saygının esastan incelemeyi gerektirip gerektirmediği. 15 No.lu Protokol'den sonra kural **iki ölçütten** oluşur; "iç mahkemece usulünce incelenmemiş olma" güvencesi kaldırıldı |
| 7 | Aynı başvuru / başka uluslararası merci (m.35/2-b) | Aynı şikâyet başka bir uluslararası mercie sunuldu mu? `[model bilgisi — doğrulayın]` |
| 8 | Başvuru hakkının kötüye kullanılması (m.35/3-a) | Olguları gizleme, yanıltıcı bilgi, gizlilik ihlali `[model bilgisi — doğrulayın]` |

---

## Zorunlu unsurlar: resmî başvuru formu (İçtüzük m.47)

**Kural:** Başvuru, Mahkeme Yazı İşlerinin hazırladığı **resmî başvuru formu** ile yapılır; form İçtüzük m.47'deki bilgileri (m.47 § 1 (e)-(f): olayların ve iddia edilen ihlallerin özlü ve okunaklı açıklaması ile ilgili argümanlar dahil) **formun kendi alanlarında** içermelidir. Bu şartlara uyulmaması başvurunun **incelenmemesine** yol açabilir (m.47 § 5.1) ve eksik form süreyi kesmez (m.47 § 6 (a), yukarıda). m.47'nin bugünkü katı biçimi 1 Ocak 2014'ten itibaren uygulanmaktadır. İçtüzük metninin kendisi soorgla'da yok: güncel metni ve formu kullanıcıya AİHM'in resmî sitesinden (echr.coe.int) kontrol ettir.

**Bu beceri resmî formu taklit etmez ve serbest metin form üretmez.** Yapacağı iş: formun her alanına girecek metni hazırlamak ve kullanıcıyı resmî formu (Mahkeme sitesinden, güncel sürüm, Türkçe dahil) indirip doldurmaya yönlendirmek.

Formun ana bölümleri ve doldurma rehberi `[model bilgisi — doğrulayın]` (form sürümüne göre bölüm harfleri değişebilir; kullanıcının indirdiği forma göre eşle):

| Form bölümü | Ne yazılır | Kaynak |
|---|---|---|
| Başvuran (gerçek / tüzel kişi) | Kimlik, adres, uyruk | Görüşme 1 |
| Temsilci | Avukat bilgileri; **formdaki yetki bölümü** başvuran ve avukat tarafından imzalanır (ayrı vekâletname yerine) | Görüşme 2 |
| Olayların açıklaması | Tarih sırasıyla, özlü; formda ayrılan alan sınırlıdır | Aşağıdaki iskelet A |
| İddia edilen ihlaller ve ilgili argümanlar | Her **Sözleşme maddesi** ayrı; hangi olgu hangi hakkı ihlal ediyor | İskelet B |
| m.35/1 kabul edilebilirlik ölçütlerine uygunluk | Her şikâyet için: tüketilen yol, nihai karar ve tarihi, öğrenme tarihi | İskelet C |
| Diğer uluslararası merciler | Var/yok | Görüşme 8 |
| Ekler listesi | Kronolojik, numaralı, sayfa numaralı | İskelet E |
| İmza | Başvuran ya da temsilci | — |

**Ek belge:** Form alanları yetmezse olaylar ve şikâyetleri ayrıntılandıran ek belge sunulabilir (İçtüzük m.47 § 2 (b)); ek belge formun zorunlu alanlarının **yerine geçmez**, Mahkeme şikâyetin kapsamını formdaki özlü açıklamadan belirler. Ek belgenin **azami sayfa sayısı** ve biçim kuralları için sayı yazma: kullanıcıya AİHM'in resmî sitesinden (echr.coe.int, başvuru formu notları / Uygulama Talimatı) güncel sınırı kontrol ettir; soorgla'da bu metin yok.

**Gönderim:** başvuru tarihi formun posta damgasına göre belirlendiğinden (m.47 § 6 (a)), asıl imzalı form ve ekler **posta** ile Strazburg'a gönderilir; yalnız faksla iletilen, aslı süresinde postalanmayan form geçerli başvuru sayılmamıştır. İlk başvurunun e-posta ya da elektronik yolla (eComms vb.) yapılıp yapılamayacağını ve güncel adres/gönderim kurallarını kullanıcıya AİHM'in resmî sitesinden (echr.coe.int) teyit ettir; soorgla'da bu usul metni yok.

**Harç:** AİHM başvurusu harçsızdır `[model bilgisi — doğrulayın]`.

**Dil:** başvuru aşamasında Türkçe yapılabilir; tebliğden sonra Mahkemenin resmî dillerinden biri (İngilizce/Fransızca) istenebilir `[model bilgisi — doğrulayın]`.

**Adil tazmin (m.41):** Başvuru aşamasında talep edilebilir ama **bağlayıcı talep**, başvuru Hükümete tebliğ edildikten sonra Mahkemenin verdiği süre içinde, belgeleriyle yapılır; süresinde talep yapılmazsa tazminata hükmedilmeyebilir. Masraf ve harcamalar yalnız gerçekten ve zorunlu olarak yapıldığı ispatlanırsa ödenir. Bazı dosyalarda ihlal tespiti tek başına yeterli adil tazmin sayılır; müvekkile tutar vaat etme.

---

## Türkiye aleyhine emsal bulma adımı (zorunlu)

1. İhlal edilen her Sözleşme maddesi için `legal_search_cases`:
   `mahkeme: "aihm"`, `sorgu: "<olayın özü> <madde> Türkiye ihlal"`, önce `tarih_baslangic: <bugün - 3 yıl>`, sonra tarihsiz (ilke kararları).
2. Sonuç başlığında "v. TÜRKİYE" / "v. TURKEY" olanları seç. `daire` filtresi işe yaramaz (hepsi "aihm"). Türkçe çevirili kararlar `belge_id`'de `-turkishtranslation` ile biter; tercih et.
3. En az bir güncel Türkiye kararının tam metnini `legal_get_case_document` ile oku (gerekirse `azami_karakter: 60000+`; uzun kararlar parçalı ve çok dilli döner). İlgili paragrafı (§) ve "Mahkeme'nin değerlendirmesi" kısmını teyit et; Hükümet ya da başvuran iddiasını Mahkeme gerekçesi gibi alıntılama (ORTAK-KURALLAR.md §7).
4. Türkiye kararı yoksa diğer devletler aleyhine ilke kararını kullan ve bunu açıkça söyle.
5. Aynı hakta AYM'nin yaklaşımını da `legal_search_cases mahkeme: "anayasa"` ile çek: AYM'nin AİHM içtihadından ayrıldığı nokta, AİHM başvurusunun en güçlü argümanıdır `[incele]`.
6. Eski YAML'daki örnekler (Salduz/Türkiye, Loizidou/Türkiye) yalnız ilgili hak söz konusuysa kullanılır ve **soorgla'dan çekilip künyesi doğrulanmadan** metne yazılmaz.

---

## Görüşme soruları (eski `data_schema` alanlarından)

1. **Başvuran** (`applicant_info`): gerçek / tüzel kişi; uyruk; avukat var mı?
2. **Tüketilen iç yollar** (`domestic_remedies`): AYM başvuru no, karar türü (kabul edilemez / ihlal yok / ihlal var), karar tarihi, **tebliğ ya da UYAP'tan öğrenme tarihi**.
3. AYM'de ileri sürülen şikâyetler nelerdi? AİHM'e götürülecek her şikâyet orada ileri sürüldü mü?
4. **İhlal edilen Sözleşme maddeleri** (`violated_convention_rights`): aday listeyi sen öner (m.2, 3, 5, 6, 8, 10, 11, 13, 14; P1-1 vb.), seçimi avukata bırak `[incele]`.
5. **Kronoloji** (`chronology_of_events`): olaydan AYM kararına kadar.
6. **Adil tazmin** (`just_satisfaction_claim`): maddi zarar belgeleri, manevi zarar, masraf ve avukatlık giderleri (fatura/sözleşme).
7. Mahkemenin ivedi geçici tedbirini (İçtüzük m.39) gerektiren yakın ve ağır tehlike var mı? (sınır dışı, sağlık) `[model bilgisi — doğrulayın]`
8. Aynı şikâyet başka bir uluslararası mercie sunuldu mu?
9. Kimliğin kamuya açık belgelerde gizlenmesi isteniyor mu?

Eski `legal_arguments` ve `relevant_precedents` alanları kullanıcıdan istenmez; beceri MCP'den kurar.

---

## soorgla çağrıları

```
legal_search_cases mahkeme: "aihm" sorgu: "Protocol No. 15 four months final domestic decision" # süre dayanağı
legal_search_cases mahkeme: "aihm" sorgu: "Anayasa Mahkemesine bireysel başvuru tüketilmesi gereken etkili yol Türkiye"
legal_search_cases mahkeme: "aihm" sorgu: "<olay> <Sözleşme maddesi> Türkiye ihlal" tarih_baslangic: "<bugün - 3 yıl>"
legal_get_case_document belge_id: "<seçilen Türkiye kararı>" azami_karakter: 60000
legal_search_cases mahkeme: "anayasa" sorgu: "<aynı hak, aynı olay türü>" # AYM'nin yaklaşımı
legal_get_statute_article law_no: "6216" article_no: "50" # AYM giderimi (mağdur sıfatı)
legal_search_statute_semantic mevzuat_no: "6384" sorgu: "<makul süre / Komisyon>"
```

---

## Dilekçe iskeleti (formun alanlarına girecek metin + ek belge)

Eski `ui_config.blocks` sırası korunmuştur. Bu metin resmî formun **içine** yazılacak ya da ona ek belge olarak eklenecek içeriktir.

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

> ⚠️ Gözden geçiren notu …

### Kısa değerlendirme
[AYM süreci durumu; başvuru yapılabilir mi; en büyük kabul edilebilirlik riski]

### Süre tablosu
| Süre | Başlangıç | Son gün | Dayanak | Durum |
|---|---|---|---|---|
| AİHM başvurusu (4 ay) | [AYM kararının öğrenildiği tarih] | [___] [doğrula — tatil uzatmaz] | Sözleşme m.35/1 (15 No.lu Protokol) [soorgla: karar künyesi] | 🔴/🟠/✅ |
| Önerilen gönderim tarihi | — | [son günden ≥ 2 hafta önce] | — | — |

### Kabul edilebilirlik kontrolü
[8 maddelik liste, işaretli]

### Form doldurma rehberi
[formun her bölümü → aşağıdaki A-E'den hangi metin]

---

AVRUPA İNSAN HAKLARI MAHKEMESİ'NE
(Başvuru Formu Eki — [başvuranın adı] / Türkiye)

BAŞVURAN : [___]
TEMSİLCİ : [___]
TÜKETİLEN SON İÇ HUKUK YOLU : Anayasa Mahkemesi, B. No. [___], karar tarihi [___], öğrenme tarihi [___]

A. OLAYLARIN AÇIKLAMASI
1. [tarih] — [olay]
…
n. Anayasa Mahkemesi [tarih] tarihli kararıyla [sonuç]; karar başvurana [tarih]te [nasıl] tebliğ edildi / öğrenildi.

B. SÖZLEŞME'NİN İHLAL EDİLDİĞİ İDDİALARI VE GEREKÇELERİ — her madde ayrı
B.1. Sözleşme'nin [__]. maddesi — [hakkın adı]
  a) Mahkeme içtihadındaki ilkeler — [AİHM kararı, künye, §] [soorgla]
  b) Somut olay — [olgu → ihlal bağlantısı]
  c) AYM'nin değerlendirmesinin yetersizliği — [AYM kararının ilgili §'ı]
B.2. …

C. MADDE 35 § 1 KABUL EDİLEBİLİRLİK ÖLÇÜTLERİNE UYGUNLUK
- Şikâyet B.1: tüketilen yol [___]; nihai karar [___]; öğrenme tarihi [___]; 4 aylık süre içinde.
- Şikâyet B.2: …
- Başka uluslararası merci: [yok / ___]

D. İLGİLİ AİHM İÇTİHATLARI
- [Karar adı/Türkiye, no., tarih, § — neyi destekliyor] [soorgla]

E. ADİL TAZMİN (Madde 41) — ön bildirim
[maddi / manevi / masraf; bağlayıcı talep tebliğden sonra verilecek sürede yapılacaktır]

EKLER (kronolojik, numaralı): 1. AYM kararı ve tebliğ/öğrenme belgesi 2. AYM başvuru formu 3. Yargıtay/Danıştay/BAM kararı 4. Kanun yolu dilekçeleri 5. …

[tarih] [Başvuran / Temsilci — imza]
```

---

## Sık hatalar

- 🔴 AYM'yi atlayıp doğrudan AİHM'e gitmek (tüketilmeme).
- 🔴 Resmî formun alanlarını boş bırakıp "ekteki dilekçeye bakınız" demek; eksik form süreyi kesmez.
- 🔴 4 aylık süreyi Türk tatilleriyle uzatmak ya da tebliğ beklerken UYAP'tan öğrenme tarihini atlamak.
- 🟠 Yalnız Türk kanun maddelerine atıf yapıp Sözleşme maddesini ve AİHM içtihadını göstermemek.
- 🟠 AYM'de ileri sürülmemiş yeni şikâyet eklemek.
- 🟠 Adil tazmin talebini başvuru formunda yapıp tebliğ sonrası verilen sürede yenilememek.
- 🟡 Eski YAML'daki "6 aydan 4 aya 1 Şubat 2022'den itibaren indirildi" ifadesini aktarmak (bkz. süre bölümündeki düzeltme).

---
