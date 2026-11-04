# İhale dokümanı incelemesi: idari şartname, teknik şartname, sözleşme tasarısı

İhale dokümanının hukuka uygunluk ve risk incelemesi. Aynı belge iki ayrı amaçla okunur:
- **İstekli — uyum modu (eski "defense"):** "Teklifim elenir mi, teminatım yanar mı, fiyata neyi katmalıyım?"
- **İstekli — itiraz modu (eski "offense"):** "Doküman rekabeti engelliyor mu, şikâyet edilebilir mi?" (süre kısa: aşağıya bak)
- **İdare — ön kontrol:** "İlana çıkmadan önce şikâyet ve iptal riski taşıyan hüküm var mı?"

Yeterlik kriterlerinin ayrıntılı oranları ve belge kuralları `yeterlik-ve-teklif-degerlendirme.md`'de; sözleşme imzalandıktan sonraki 4735 kuralları (iş artışı, fiyat farkı hesabı, gecikme cezası, fesih) `../../hakedis/SKILL.md`'de.

---

## Ne zaman kullanılır

| Durum | Mod |
|---|---|
| İstekli dokümanı EKAP'tan indirdi, teklif vermeden önce risk listesi istiyor | Uyum |
| Teknik şartnamede marka, model ya da tek ürünü işaret eden ölçü var | İtiraz |
| Benzer iş tanımı, yeterlik kriteri ya da istenen belge rekabeti daraltıyor | İtiraz |
| İdare dokümanı ilana çıkmadan önce kontrol ettiriyor | İdare ön kontrolü |
| Sözleşme tasarısı ile idari şartname arasında çelişki | Üçü de |

**Süre uyarısı (itiraz modu):** dokümana yönelik şikâyet, dokümanın satın alındığı (EKAP'tan indirildiği) tarihten itibaren 10 gün (21/b-c'de 5) içinde ve **her durumda ihale tarihinden üç iş günü öncesine kadar** yapılır; **ilanda da yer alan hususlara** (benzer iş, iş deneyimi oranı, yeterlik kriterleri) süre **ilk ilan tarihinden** başlar — ilk ilan tarihini mutlaka sor; ilan eskiyse süre indirmeden önce dolmuş olabilir 🔴. Açıklama talebi (ihaleden 20 gün önce, 4734 m.29) bu süreyi **durdurmaz**; iki son günü birlikte yaz. Dokümana zamanında itiraz etmeyen istekli, ihale sonrasında aynı hususu ileri süremeyebilir `[incele]`.  İncelemeye başlarken bu son günü hesapla ve en üste yaz.

---

## Kontrol listesi

### A. Teknik şartname (4734 m.12)
- [ ] **Marka, model, patent, menşei, kaynak veya ürün** belirtilmiş mi, ya da belirli bir marka/modele yönelik özellik ve tanımlama var mı? Kural yasak; istisna: ulusal/uluslararası standart yoksa veya teknik özellik belirlenemiyorsa **"veya dengi"** ibaresiyle marka/model yazılabilir. "Veya dengi" yoksa güçlü şikâyet konusu (🔴 idare için). 
- [ ] Teknik kriterler **verimlilik ve fonksiyonellik** sağlamaya yönelik mi, rekabeti engelleyici husus içeriyor mu, fırsat eşitliği sağlanmış mı? İşin gereği olmayan aşırı özellikler (ofis işine askeri standart) 🟠. 
- [ ] Ölçüler aralık yerine tek nokta değer mi ("tam 154 cm")? Tek ürün kataloğundan kopyalanmış izlenimi var mı? → "adrese teslim" şüphesi `[incele]`; somut kanıt (katalog karşılaştırması) olmadan iddia yazma.
- [ ] Ulusal/uluslararası standartlara uygunluk düzenlemesi var mı? Yalnız tek ülkeye özgü ya da yürürlükten kalkmış standart zorunlu tutulmuş mu? 🟡 
- [ ] Teknik şartname ile idari şartname arasında çelişki (teslim süresi, miktar, yer) var mı? Çelişki zeyilname (m.29) ya da şikâyet konusudur. 
- [ ] Mal alımında montaj, satış sonrası servis, yedek parça hükümleri var mı? (Mal Alımı Uygulama Yönetmeliği m.14/5: teknik şartnamede montaj, satış sonrası servis ve yedek parça düzenlenebilir; `law_no: "12917"`, `law_type: "Yönetmelik"`) 
- [ ] Belge isteniyorsa (TSE, ISO, CE, test raporu) akredite kuruluştan mı, teklifle mi sözleşmeden sonra mı sunulacak? Yeterlik kriteri mi, teknik uygunluk belgesi mi? `[incele]`

### B. İdari şartname
- [ ] **Benzer iş tanımı** işin niteliğine uygun mu; rekabeti daraltacak kadar dar (yalnız belli bir kurumda yapılmış iş, belli bir alt kalem) ya da ilgisiz işleri kapsayacak kadar geniş mi? "Dar benzer iş" iptal emsalleri yalnız tanım ihale konusundan **dar** olduğunda işler; tanım ihale konusuyla aynı ya da daha genişse uygulanmaz (`../../ihale-sikayet/references/kik-emsal-arama.md` adım 8). Yapım işlerinde Benzer İş Grupları Tebliği'ndeki gruptan alt kalem seçerek "ayrıştırma" yapılmış mı? `[incele]` Yapım İşlerinde Benzer İş Grupları Tebliği araçta `law_no: "15043"`, `law_type: "Tebliğ"`: grup içinden iş seçerek **ayrıştırma yapılamaz** (m.2.1); birden fazla gruba atıf yapılabilir (m.2.2); farklı uzmanlık gerektiren çok gruplu deneyim aranıyorsa ihale **konsorsiyumlara açık** yapılmalı (m.2.3); BII grubunda belirtilen yapı inşaat alanından küçük işlerde tek başına BII benzer iş olarak belirlenemez (m.2.10); onarım ve tamamlama işlerinde "grup veya o gruptaki işin onarım işi" kalıbı (m.2.4). Metraj eşiklerini Tebliğ ekindeki listeden çek, metne yazma. 
- [ ] Yeterlik kriterleri yönetmelikteki **sabit oranlara** uyuyor mu (iş hacmi, bilanço rasyoları)? İdare bu oranları değiştiremez; ayrıntı `yeterlik-ve-teklif-degerlendirme.md`. 
- [ ] **Makine/ekipman özmal şartı** yeterlik kriteri olarak istenmiş mi? Kanun makine, teçhizat ve ekipmana ilişkin belge istenebileceğini söyler; özmal (sahiplik) şartının yeterlik kriteri yapılması yönetmelik ve KİK kararlarına göre sorunlu `[incele]`.  Yönetmelikler bunu açıkça yasaklar: makine, teçhizat ve diğer ekipman **yeterlik kriteri olarak belirlenemez** (Yapım 12916 m.41/1, Hizmet 12918 m.41, Mal 12917 m.40/1); hizmette işin niteliği gerektiriyorsa kendi malı olması gereken ekipman **fiyat dışı unsur** olarak belirlenebilir (12918 m.41). 
- [ ] **Geçici teminat** "teklif edilen bedelin %3'ünden az olmamak üzere istekli tarafından belirlenecek tutar" olarak mı yazılmış? Sabit tutar ya da %3'ten yüksek zorunlu oran kanuna aykırı. Danışmanlıkta dokümanda belirtilirse geçici teminat istenmeyebilir. 
- [ ] **Kesin teminat** %6 (sınır değerin altındaki tekliflerde Kurum düzenlemesiyle %6-%15 arası); danışmanlıkta dokümanda belirtilirse hakedişten %6 kesinti. 
- [ ] **Yerli istekli / yerli malı avantajı**: eşik altında yalnız yerli istekli düzenlemesi yapılabilir; hizmet ve yapımda yerli istekliye, malda yerli malına %15'e kadar fiyat avantajı; listede yer alan orta-yüksek teknolojili mallar ve yerli yazılımda %15 **zorunlu**; ortak girişimin yerli sayılması için bütün ortaklar yerli olmalı. 
- [ ] İhale dışı bırakılma halleri (m.10/4) "kesinleşmiş" vergi ve SGK borcu ifadesiyle doğru aktarılmış mı? Kanunda olmayan yeni dışlama sebebi eklenmiş mi ("idareyle davalı olanlar" gibi)? 🟠 
- [ ] İhaleye katılamayacaklar (m.11) eksiksiz ve kanuna uygun sayılmış mı? Kanunda olmayan yasak eklenmiş mi? 
- [ ] Aşırı düşük teklif yöntemi (açıklama istenerek mi, sorgusuz ret mi) dokümanda belirtilmiş mi; sorgusuz ret yalnız Kurum düzenlemesinin izin verdiği işlerde ve eşik değerin yarısına kadar olan hizmet ve yapımlarda mümkün. 
- [ ] Ortak girişim ve konsorsiyum: işin farklı uzmanlıklar gerektirmesine rağmen konsorsiyum yasaklanmış mı? Konsorsiyumun katılıp katılamayacağı ilanda ve dokümanda belirtilmek zorunda. 
- [ ] **Teklif fiyatına dahil giderler** (uyum modu): sigorta, vergi, resim, harç, nakliye, damga vergisi, karar pulu, KİK payı vb. listele; teklif fiyatına yansıtılmayan maliyet zarar demektir. KİK payı: 4734 m.53/j-1'deki tutarı aşan sözleşmelerde sözleşme bedelinin onbinde beşi (personel çalıştırılmasına dayalı olmayan hizmette açıklama hesabında da ayrıca hesaplanır, KİGT 79.3.5); eşik tutarı `legal_get_social_parameters` (`ihale_kik_payi_sozlesme_esigi`).  
- [ ] Teminatın gelir kaydedileceği haller kanunda sayılanlarla mı sınırlı (m.10 son fıkra, m.11, m.37, m.44)? 🟡 

### C. Sözleşme tasarısı (yalnız doküman tutarlılığı)
- [ ] Sözleşme tasarısı idari şartnameyle **çelişiyor mu** (ceza oranı, süre, ödeme, fiyat farkı verilip verilmeyeceği, teslim yeri)? İhale dokümanına aykırı sözleşme düzenlenemez; çelişki dokümana yönelik şikâyet ya da zeyilname konusudur. 
- [ ] Taraflar arasında eşitliği bozan tek taraflı hükümler ("yüklenici her talimata itirazsız uyar", "idarenin nakit durumu uygun olduğunda ödenir") → 4735 m.4 eşit hak ilkesine aykırı olabilir 🟠. 
- [ ] Noter onayı zorunlu tutulmuş mu? Dokümanda aksi belirtilmedikçe zorunlu değildir; zorunluysa maliyet olarak fiyata yansıt. 
- [ ] Sözleşme türü işle uyumlu mu? Uygulama projesi olan yapım işi **anahtar teslimi götürü bedel** olmak zorunda.  (Eski YAML bunu "4735 m.6" diye gösteriyordu; zorunluluk 4734 m.62/c'dedir.)
- [ ] Tip sözleşmede dipnotla doldurulması gereken alanlar doldurulmuş mu; idare tip metinden yetkisiz çıkarma yapmış mı? `[incele]`
- [ ] İş artışı oranı, gecikme cezası aralığı, fiyat farkı, mücbir sebep, kesin teminatın iadesi → kuralları `../../hakedis/SKILL.md`'den kontrol et; bu dosya yalnız "doküman kendi içinde tutarlı mı" sorusuna bakar. İş artışı sınırı: anahtar teslimi götürü bedel yapımda sözleşme bedelinin %10'u, birim fiyatlı mal, hizmet ve yapımda %20'si; birim fiyatlı yapımda Cumhurbaşkanı sözleşme bazında %40'a kadar artırabilir (4735 m.24).  Günlük gecikme cezası oranı sözleşmede yazılıdır (ör. örnek ihale 2026/1776751 sözleşme tasarısı m.25.2: ilk sözleşme bedelinin on binde beşi); Tip Sözleşme dipnotundaki aralık kanunda değildir. 

---

## Süreler ve dayanakları

| Süre | Kural | Dayanak |
|---|---|---|
| Dokümana şikâyet | Satın alma/indirme tarihini izleyen günden 10 gün (21/b-c: 5); ihale tarihinden 3 iş günü öncesine kadar | 4734 m.55/1-2  |
| İlana ve dokümanın ilana yansıyan hükümlerine şikâyet (benzer iş, iş deneyimi oranı, yeterlik) | İlk ilan tarihinden 10 gün; ihaleden 3 iş günü öncesine kadar | 4734 m.55/1  |
| Açıklama talebi | Son teklif gününden 20 gün öncesine kadar; **şikâyet süresini durdurmaz** (ayrı yol, ayrı son gün) | 4734 m.29/3  |
| Zeyilname | Son teklif gününden en az 10 gün önce; erteleme en fazla 20 gün, bir defa | 4734 m.29/2  |

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Dokümanı EKAP'tan hangi tarihte indirdiniz? İhale tarihi? | Şikâyet süresinin son günü |
| Taraf: teklif verecek istekli mi, idare mi? | Mod |
| İşin türü ve yaklaşık maliyet bandı (biliniyorsa)? | Hangi yönetmelik, hangi belge zorunlu |
| İdari şartname, teknik şartname ve sözleşme tasarısının tamamı elinizde mi? | Çapraz kontrol |
| (İtiraz modu) Hangi rakip ya da ürün işaret ediliyor; kataloğu var mı? | Adrese teslim iddiasının delili |
| (Uyum modu) İş deneyim belgeniz, ciro ve bilanço değerleriniz neler? | Elenme riski |

---

## MCP adımları

```
legal_get_statute_article  law_no: "4734"  law_type: "Kanun"  article_no: "5" | "10" | "11" | "12" | "29" | "33" | "38" | "43" | "46" | "55" | "62" | "63"
legal_get_statute_article  law_no: "4735"  law_type: "Kanun"  article_no: "4"
legal_get_statute_article  law_no: "12918"  law_type: "Yönetmelik"  article_no: "<28 | 29 | 35 | 36 | 39 ...>"     # hizmet alımı
legal_get_statute_article  law_no: "12916"  law_type: "Yönetmelik"  article_no: "<madde>"      # yapım yönetmeliği; madde metinleri tam
legal_get_statute_article  law_no: "15043"  law_type: "Tebliğ"  article_no: "2"      # Benzer İş Grupları Tebliği
legal_search_official_gazette  query: "Benzer İş Grupları"  search_in: "title"  sort_by: "date_desc"
legal_search_cases  mahkeme: "kik"  sorgu: "<ör. teknik şartnamede veya dengi ibaresi olmadan marka belirtilmesi>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "danistay"  sorgu: "<ör. benzer iş tanımının rekabeti daraltması ihale dokümanına yönelik şikâyet>"
legal_get_case_document  belge_id: "<seçilen karar>"
```

---

## Çıktı iskeleti

```markdown
### Doküman incelemesi — İKN [___] — [mod: uyum / itiraz / idare ön kontrolü]
**Dokümana şikâyet için son gün:** [tarih] ([hesap]) [🔴 7 günden az kaldıysa]

| # | Belge / madde | Tespit (metinden alıntı) | Dayanak | Önem | Öneri |
|---|---|---|---|---|---|
| 1 | Teknik Şartname m.[__] | "[...]" | 4734 m.12 | 🔴 | "veya dengi" eklenmeli / şikâyet iddiası 1 |

### Teklif fiyatına yansıtılacak maliyetler (uyum modu)
### Şikâyet edilebilecek iddialar — her biri ayrı numarada (itiraz modu)
[Bu liste dilekçe becerisine aynen devredilir; sonradan iddia eklenemez.]
```

---

## Sık hatalar

- 🔴 Doküman şikâyetini ihale sonrasına bırakmak (3 iş günü sınırı geçer).
- 🔴 "Veya dengi" ibaresi olmadan marka belirtmek (idare).
- 🟠 Somut kanıt olmadan "adrese teslim" iddiası yazmak; KİK iddianın ispatını bekler.
- 🟠 Sözleşme tasarısı ile idari şartname çelişkisini teklif sonrasına bırakmak.
- 🟡 Teklif fiyatına damga vergisi, KİK payı ve sigorta gibi giderleri katmamak.

---

