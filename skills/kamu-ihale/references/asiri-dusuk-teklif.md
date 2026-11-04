# Aşırı düşük teklif ve sınır değer

4734 m.38'e göre aşırı düşük teklif tespiti, açıklama istenmesi, açıklamanın değerlendirilmesi ve sorgusuz ret. Kamu ihale uyuşmazlıklarının en büyük kümelerinden biridir ve açıklamada sunulan belge (fiyat teklifi, satış tutarı tespit tutanağı, maliyet tespit tutanağı) yüzünden **yasak fiil ve yasaklama** riskine dönüşebilir.

- **İstekli tarafı (açıklama yapan):** sorgu yazısı geldi; neyi, hangi belgeyle, hangi sürede açıklamalı?
- **İstekli tarafı (rakibe itiraz eden):** rakibin açıklaması mevzuata uygun mu?
- **İdare tarafı:** sınır değer doğru hesaplandı mı, kimden açıklama istenmeli, açıklama nasıl değerlendirilir?

---

## Ne zaman kullanılır

| Durum | Taraf |
|---|---|
| "Aşırı düşük teklif açıklaması istendi" yazısı geldi | İstekli |
| Açıklamam reddedildi, teklifim değerlendirme dışı | İstekli |
| Rakibin açıklamasında fiyat teklifi/tutanak usulsüz | İstekli (şikâyet) |
| Sınır değer hesabı, sorgusuz ret seçeneği, açıklamanın değerlendirmesi | İdare |

---

## Kontrol listesi

### 1. Hukuki çerçeve (m.38)
- [ ] Komisyon teklifleri değerlendirdikten sonra diğer tekliflere veya yaklaşık maliyete göre aşırı düşük olanları tespit eder; reddetmeden önce **önemli bileşenlerle ilgili ayrıntıları yazılı ister**. 
- [ ] Açıklamada dikkate alınacak hususlar: imalat sürecinin/hizmetin/yapım yönteminin ekonomik olması; seçilen teknik çözümler ve isteklinin avantajlı koşulları; teklifin özgünlüğü. Açıklaması yeterli görülmeyen ya da açıklama yapmayanın teklifi **reddedilir**. 
- [ ] **Kurum düzenlemesi esastır:** sınır değer, sorgulama kriterleri, açıklama istenmeden sonuçlandırma ve eşik değerin **yarısına kadar** hizmet ve yapım ihalelerinde sınır değer altındaki tekliflerin açıklama istenmeden reddi Kurum düzenlemesine bağlıdır; komisyon Kurum düzenlemelerini esas alır. 
- [ ] Yapım işlerinde sınır değeri komisyon **Kurum'un belirlediği yönteme göre** hesaplar; ilanda ve dokümanda belirtilmek kaydıyla seçenekler (açıklama isteme / açıklama istemeden ret vb.) uygulanır.  Sınır değer formülü ve **N katsayısı** Kamu İhale Genel Tebliği'nde ve yönetmelikte; beceriye yazılmaz, güncel metinden çekilir. Yapımda formül KİGT 45.1.1 (YM'nin %40-%120 bandı dışındaki teklifler ortalamaya girmez; Tort1 ± σ, Tort2, C, K), N katsayısı 45.1.1.1 (Benzer İş Grupları Tebliği'ndeki B, C, D, E gruplarında 1,00, diğer yapım işlerinde 1,20; Bakanlıklar 45.1.1.2'ye göre farklı katsayı belirleyebilir), uygulanacak katsayı ilan ve idari şartnamede yazılır (45.1.1.3). Hizmette personel çalıştırılmasına dayalı işlerde kâr hariç yaklaşık maliyet sınır değerdir (79.1.1); diğerlerinde SD = R × (YM + ΣT)/(n+1) ve R her yıl 1 Şubat'tan geçerli olarak Kurumca ilan edilir (79.1.2-79.1.3). Hesap için `legal_calculate_tender` (`sinir_deger_yapim`, `sinir_deger_hizmet`) kullanılır; araç yanıt vermezse ya da hata dönerse elle hesapla (hizmet formülü EKAP modülüyle karşılaştırılmadı). 
- [ ] Yaklaşık maliyetin üzerindeki tekliflerden açıklama istenmesi KİK kararlarında mevzuata aykırı bulunmuştur `[incele]` — güncel tebliğle teyit et. 

### 2. Açıklamanın hazırlanması (istekli)
- [ ] Sorgu yazısındaki **önemli bileşenleri** tek tek listele; yazıda istenmeyen kalem açıklanmak zorunda değildir, istenen her kalem açıklanmalıdır.
- [ ] Süre: idarenin yazıda verdiği süre; asgarisi yapımda **5 iş günü** (KİGT 45.1.2), hizmette **3 iş günü** (KİGT 79.2.1-c); malda KİGT 62/A.1 atfıyla 79 uygulanır (3 iş günü alt sınırının mala uygulanması `[incele]`); danışmanlıkta süreyi komisyon belirler; daha kısa süre verilmişse bu da şikâyet konusudur . Kaçırılırsa açıklama yapılmamış sayılır ve teklif reddedilir. 🔴 
- [ ] Kullanılan yöntemler (Kamu İhale Genel Tebliği'ndeki liste): üçüncü kişiden **fiyat teklifi** (SMMM/YMM onaylı satış tutarı veya maliyet tespit tutanağıyla), resmî fiyatlar, kamu kurumlarından alınan fiyatlar, isteklinin kendi stokları ve üretim maliyeti vb. Hangi yöntemin hangi bileşen için kabul edildiğini güncel tebliğden çek: yapımda KİGT 45.1.13 (fiyat teklifi, çimento-demir üretici tarifeleri, kamu tarifeleri, asgari fiyatlar, maliyet/satış tutarı tespit tutanağı, stok tespit tutanağı; yalnız alış faturası geçerli açıklama değildir, 45.1.13.9), kamu birim fiyatı ve rayiçte analiz/belge muafiyeti 45.1.5-45.1.6; hizmette 79.2.2.1-79.2.2.8 (fiyat teklifi, merkezi kamu fiyatları, kamu ilan fiyatları, borsa, hal, özel/münhasır hak sahibi fiyatları, kendi ürettiği/aldığı/sattığı mal, emsal bedel) ve fiilen imkânsızlıkta 79.3.2. 
- [ ] **Satış tutarı tespit tutanağı (Ek-O.6) tarih kuralı:** tutanak ilan/davet tarihinin içinde bulunduğu aydan önceki üç ay (veya ondan önceki üç ay) bilgileriyle düzenlenir; dayanak faturalar o dönemde **işlem görmüş** olmalıdır. Faturası sorgu yazısından **sonra** GİB sistemine gönderilen tutanak açıklamada dikkate alınamaz; KİK ve Danıştay bunu "ihale kararını etkileyecek davranış" (m.17/b) sayıp isteklinin **bütün kısımlarda** değerlendirme dışı bırakılmasını onadı. 🔴  Bu yüzden açıklamada kullanılacak her fiyat teklifinin dayanağını, tarihini ve imzalayan meslek mensubunu ihale öncesinde kontrol et.
- [ ] Belgelerin aslı ya da onaylı sureti; fotokopi sunmanın gerekçesi yoksa açıklama mevzuata uygun sayılmayabilir. 
- [ ] Fiyat teklifindeki tutar ile teklif cetveline yansıtılan tutar uyumlu mu? Daha düşük gösterilmesi ret sebebi olmuştur. 
- [ ] İşçilik ağırlıklı hizmetlerde asgari işçilik maliyetinin altına inilemez; güncel asgari ücreti `legal_get_social_parameters` ile çek. Personel çalıştırılmasına dayalı hizmette asgari işçilik maliyeti hesabında KİK İşçilik Hesaplama Modülü zorunludur (KİGT 79.3.3); sözleşme ve genel gider dahil asgari işçiliğin altındaki teklif değerlendirme dışıdır (KİGT 78.29). Yapımda analizlerdeki işçilik fiyatı ihale tarihindeki saatlik asgari ücretin altında olamaz (KİGT 45.1.9). İşçilik hesabı için `legal_calculate_tender` (`iscilik`) kullanılır. 

### 3. Değerlendirme (idare) ve rakibe itiraz (istekli)
- [ ] Sınır değer ilanda/dokümanda belirtilen yönteme göre doğru hesaplandı mı? Hesap tablosunu iste.
- [ ] Açıklama istenenler doğru belirlendi mi (sınır değerin altındakiler; yaklaşık maliyetin üzerindekiler değil)?
- [ ] Sorgu yazısı önemli bileşenleri ve açıklama yöntemlerini açıkça gösteriyor mu? Belirsiz yazıya dayanan ret sakat olabilir `[incele]`.
- [ ] Açıklamanın reddi **gerekçeli** mi; hangi bileşen, hangi belge, hangi tebliğ hükmü? (Kesinleşen ihale kararında gerekçe yazılmalı.)
- [ ] Kurul, aşırı düşük değerlendirmesini kendisi yapmak yerine idareye bırakmışsa (ya da tersi) Danıştay kararlarına bak. 

---

## Süreler ve dayanakları

| Süre | Kural | Dayanak |
|---|---|---|
| Açıklama | Komisyonun sorgu yazısında belirlediği süre; asgari yapımda 5 iş günü (KİGT 45.1.2), hizmette 3 iş günü (KİGT 79.2.1-c); malda KİGT 62/A.1 (Değişik RG-9/4/2026) atfıyla 79 uygulanır, 3 iş günü alt sınırının mala uygulanması `[incele]`; danışmanlıkta yönetmelikte hüküm yok, komisyon belirler | 4734 m.38/1  |
| Rete karşı şikâyet | Kesinleşen ihale kararının farkına varıldığı tarihi izleyen günden 10 gün (21/b-c: 5) | 4734 m.55/1  |
| Tutanak dönemi | İlan/davet ayından önceki üç ay ya da ondan önceki üç ay | Kamu İhale Genel Tebliği 79.2.4  |

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Sorgu yazısının tarihi, verilen süre ve istenen önemli bileşen listesi? | Süre ve kapsam |
| İhale türü (yapım/hizmet/mal) ve ilan tarihi? | Yöntem ve tutanak dönemi |
| Her bileşen için hangi belgeyle açıklayacaksınız (fiyat teklifi, kendi üretim, resmî fiyat)? | Yöntem uygunluğu |
| Fiyat teklifi veren firma kim, tutanağı hangi meslek mensubu düzenledi, dayanak faturaların tarihleri? | Tarih ve sahtelik riski |
| (Rakibe itiraz) Rakibin açıklamasını gördünüz mü, nasıl eriştiniz? | Delil |

---

## MCP adımları

```
legal_get_statute_article  law_no: "4734"  law_type: "Kanun"  article_no: "38" | "17" | "10"
legal_list_statute_articles  statute_id: 43184  article_no: "60"  include_content: true     # yapım yönetmeliği m.60 (birleşik kayıt)
legal_get_statute_article  law_no: "12918"  law_type: "Yönetmelik"  article_no: "<aşırı düşük maddesi>"
legal_search_official_gazette  query: "Kamu İhale Genel Tebliğinde Değişiklik"  search_in: "title"  sort_by: "date_desc"
legal_search_cases  mahkeme: "kik"  sorgu: "<ör. satış tutarı tespit tutanağı fatura tarihi aşırı düşük açıklama>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "danistay"  sorgu: "aşırı düşük teklif açıklaması tutanak fatura Kurul kararı iptali"  tarih_baslangic: "<son 3 yıl>"
legal_get_case_document  belge_id: "<seçilen karar>"
legal_get_social_parameters  tur: "asgari_ucret_brut"        # işçilik ağırlıklı hizmet
legal_get_statute_article  law_no: "13354"  law_type: "Tebliğ"  article_no: "45" | "79" | "78"   # KİGT sınır değer ve açıklama
legal_calculate_tender  sinir_deger_yapim | sinir_deger_hizmet | iscilik   # parametre adlarını araç tanımından al; hata dönerse elle
```

---

## Çıktı iskeleti

### İç değerlendirme
```markdown
### Aşırı düşük teklif — İKN [___] — [istekli: açıklama / istekli: itiraz / idare]
**Açıklama son günü:** [tarih] 🔴/🟠
| Bileşen | Teklifteki tutar | Açıklama yöntemi | Belge ve tarihi | Risk |
|---|---|---|---|---|
```

### Açıklama yazısı iskeleti (istekliden idareye)
```markdown
[İDARENİN ADI]
[İHALE KOMİSYONU BAŞKANLIĞINA]

İKN: [___]   İşin adı: [___]
Konu: [tarih/sayı] sayılı yazınız ile istenen aşırı düşük teklif açıklamamızdır.

1. Açıklama istenen önemli bileşenler ve açıklamalar
   1.1 [Bileşen] — teklif edilen birim fiyat [___] — açıklama yöntemi: [___] — ek: [belge no]
   1.2 ...
2. Teklifimizin ekonomik olmasını sağlayan hususlar (4734 m.38/2-a,b,c)
   [üretim/hizmet yönteminin ekonomikliği, avantajlı koşullar, özgünlük]
3. Ekler listesi
   [fiyat teklifleri, satış tutarı/maliyet tespit tutanakları (dönem: ___), faturalar, analizler]

Bilgilerinize arz ederiz.                    [Tarih] [İstekli unvanı, yetkili, imza]
```
Yazı "TASLAK — avukat incelemesi bekliyor" işaretiyle verilir; iç notlar ve etiketler dış metne girmez.

---

## Sık hatalar

- 🔴 Sorgu yazısından sonra düzenlenmiş/GİB'e gönderilmiş faturaya dayanan tutanak sunmak (yasak fiil, bütün kısımlarda eleme, yasaklama riski).
- 🔴 Açıklama süresini kaçırmak.
- 🟠 Sorguda istenen bir bileşeni atlamak.
- 🟠 Fiyat teklifindeki tutar ile teklif cetvelindeki tutarı uyumsuz bırakmak.
- 🟡 Belgelerin fotokopisini gerekçesiz sunmak.

---

