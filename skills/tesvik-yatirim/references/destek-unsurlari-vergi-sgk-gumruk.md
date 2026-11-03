# Destek unsurları: gümrük, KDV, vergi indirimi, faiz, makine, SGK, yer tahsisi

## Ne zaman kullanılır
- "KDV istisna belgesi nasıl alınır, neleri kapsar?", "indirimli kurumlar vergisini diğer kazançlara uygulayabilir miyiz?", "faiz desteği ile makine desteği birlikte olur mu?", "SGK işveren hissesi desteği ne zaman başlar?", "KOSGEB hibesi aldık, teşvik belgesi de alabilir miyiz?"
- Teşvik ihlaline bağlı vergi riskinin ön değerlendirmesi (tarhiyat geldiyse esas yol `../../vergi/SKILL.md`).

**Kural:** her unsurun oranı, tavanı, süresi ve asgari tutarı **Karar metninden** (9903 m.13-21) ya da ilgili kanundan çekilir; bu dosyada sayı yoktur. Unsurların hangi sistemde bulunduğu: Hamle programlarında gümrük, KDV, vergi indirimi, faiz/kâr payı, makine desteği, yer tahsisi; Sektörel sistemde makine desteği hariç aynısı; bölgesel teşvik olarak SGK primi desteği.

---

## 1. Unsur unsur kontrol listesi

### 1.1 Gümrük vergisi muafiyeti (9903 m.13)
- Belge kapsamındaki **ithal** makine-teçhizat için gümrük vergisi %0 uygulanır (muafiyetin tanımı Karar m.2'de). EK-4'teki makineler muafiyetsiz ithal edilip sabit yatırıma dahil edilebilir.
- Kullanılmış komple tesis ithali Bakanlık ekspertiziyle; serbest bölgeden kullanılmış komple tesis alınamaz; kullanılmış makine vergi indirimi, makine ve faiz desteğinden yararlanamaz.
- Gümrük işlemleri ve uyuşmazlıkları → `gumruk-dis-ticaret` (3. dalga; yoksa `[incele]`).

### 1.2 KDV istisnası (3065 m.13/d; 9903 m.14)
- Belge sahibine **belge kapsamındaki** makine-teçhizat teslimi ile belge kapsamındaki yazılım ve gayri maddi hak satış ve kiralamaları KDV'den istisna; aynı hüküm belge kapsamı yatırımın devrinde ve set/ünite halindeki malların kısmi teslimlerinde uygulanır.
- **Gerçekleşmezse:** yatırım belgede öngörüldüğü şekilde gerçekleşmezse zamanında alınmayan KDV **alıcıdan** (yatırımcıdan) vergi ziyaı cezası ve gecikme faiziyle alınır; zamanaşımı, tarhı gerektiren durumun meydana geldiği tarihi izleyen takvim yılı başında başlar.
- İstisna için vergi dairesinden **KDV istisna belgesi** alınır; makinenin belge eki listede bulunması ve makine-teçhizat niteliği taşıması gerekir; aksam/parça kapsam dışıdır. Bu ayrıntılar KDV Genel Uygulama Tebliği (II/B-5) bölümündedir; özelgelerle teyit et.
- **Bina-inşaat KDV istisnası (geçici m.37):** imalat sanayii ve turizm yatırımlarında belge kapsamı inşaat işlerine tanınan istisna kanun metninde 31.12.2025'e kadardı; Cumhurbaşkanı m.37/4 yetkisiyle süreyi **31.12.2028'e** uzattı (CB Kararı 9770 (RG 01.05.2025, 32887)). soorgla madde metni hâlâ 31/12/2025 gösteriyor — tarihi madde metninden değil bu karardan al; sonraki değişikliği `legal_search_official_gazette` (`query: "Katma Değer Vergisi Kanununun Geçici 37"`, `search_in: "title"`, `sort_by: "date_desc"`) ile kontrol et.
- Ar-Ge/teknopark makine istisnası (3065 m.13/m) ayrı rejimdir → `ar-ge-tasarim-ve-teknopark.md`.

### 1.3 Vergi indirimi (KVK 32/A; 9903 m.20)
- Gelir/kurumlar vergisi, Karar'daki **yatırıma katkı oranı** üzerinden hesaplanan katkı tutarına ulaşıncaya kadar indirimli uygulanır; oran program/sisteme göre (m.20/1) — oranı Karardan çek. Diğer faaliyet kazançlarına da katkı tutarının belirli bir kısmına kadar indirim uygulanabilir (m.20/2).
- **7555 değişikliği (KVK 32/A):** indirim, **indirim hakkının kullanılabileceği ilk hesap dönemi dahil en fazla on hesap dönemi** uygulanır; **kazanç olduğu halde yararlanılmayan katkı tutarı sonraki dönemlerde dikkate alınmaz**; yatırım tamamlanınca kalan katkı tutarı yeniden değerleme oranıyla artırılır; CB'nin oran ve dönem yetkileri yeniden yazıldı. Yeni metin, 16.06.2025'ten önce başvurusu yapılıp reddedilmemiş olanlar hariç, **24.07.2025'ten itibaren alınan belgelere** uygulanır. Eski belgede eski 32/A metni.
- **Yatırım döneminde terkin:** belge bazında yatırım harcamasına katkı oranı uygulanarak bulunan tutarın bir kısmı için kurumlar vergisi beyannamesinde terkin talebi (32/A(8), 7338 ile eklendi) — kapsamı ve oranı maddeden oku.
- Vergi indirimi **alamayanlar**: arazi-arsa, royalti, yedek parça, amortismana tabi olmayan harcamalar; finans ve sigorta kurumları, iş ortaklıkları; Yap-İşlet ve Yap-İşlet-Devret yatırımları; rödovanslı yatırımlar; ayrıca m.9/3 ve m.10/2'deki enerji ve İstanbul hedef yatırımları.
- **Yeni kurulmuş firma seçeneği:** tescili müracaattan en çok bir yıl önce olan yatırımcı, vergi indiriminden vazgeçerek komple yeni yatırımda faiz/makine desteği oranına ve tavanına ek alabilir (m.20/4) — rakamlar Karardan.
- **2027'den üretim kazancı indirimi (7582):** sanayi sicil belgeli ve fiilen üretim yapan kurumların münhasıran üretim kazancına indirimli kurumlar vergisi oranı uygulanacak (KVK 32/8 yeniden yazıldı; 2027 ve sonrası kazançlar); 32/A ile birlikte uygulanırken çifte indirim yapılıp yapılamayacağını madde metninden ve tebliğden kontrol et `[incele]`. Birlikte uygulama için 7582 sonrası tebliğ/özelgeyi `legal_search_admin_guidance` (`kurum: "Gelir İdaresi Başkanlığı"`, `sorgu: "32 nci maddenin sekizinci fıkrası 32/A birlikte"`, `tarih_baslangic: "2026-06-04"`) ile ara; bulamazsan `[ARAŞTIRMA GEREKLİ: KVK 32/8 (7582) + 32/A birleşmesi]`.
- Uygulama özelgeleri (diğer faaliyet kazancı, iki belge önceliği, yatırım dönemi): `legal_search_admin_guidance` `kurum: "Gelir İdaresi Başkanlığı"` — çoğu 2012/3305 ve eski 32/A dönemine ait; 7555 sonrası belgede geçerliliğini sınırla `[incele]`.

### 1.4 Faiz veya kâr payı desteği (9903 m.15)
- TL yatırım kredisinin belgedeki sabit yatırımın belirli oranına kadar kısmı için, TCMB bir hafta vadeli repo faiz oranına bağlı puan desteği; program/sisteme göre oran ve tavan; ilk kredi kullanımından itibaren azami süre; döviz kredisinde ayrı puan. Rakamlar Karardan.
- Hamle programlarında faiz desteği alan yatırıma **makine desteği verilmez** (ve tersi).
- Belge iptali/kısmi müeyyidede fazla ödenen destek, her ödemenin yapıldığı tarihten itibaren **6183 m.51 gecikme zammı** ile geri alınır; bu kural önceki kararlara göre düzenlenen belgelere de uygulanır.
- Kredi amacı dışında kullandırılırsa aracı kurumdan geri alınır (beş iş günü).
- Bakanlığın Stratejik Öncelikli Proje (TSP) / Öncelikli Finansman programlarından kredi kullanana o kredi için faiz desteği verilmez → `kosgeb-ajans-ve-diger-destekler.md`.

### 1.5 Makine desteği (9903 m.16-17)
- Yalnız Türkiye Yüzyılı Kalkınma Hamlesi yatırımlarında; birim fiyatı Karar'daki eşiğin üzerindeki makine bedelinin bir oranı bütçeden ödenir; tavan programa göre. Ödeme, harcama yılını izleyen yıl verilen **yatırım ilerleme raporuna** göre "destek hak ediş tutarı" kadar; yalnız arazi-arsa veya "diğer" kalemlerinden oluşan raporla ödeme yapılmaz.
- EK-4'teki makine için makine desteği yalnız yurt içinde üretilmişse.

### 1.6 Sigorta primi işveren hissesi ve sigorta primi desteği (9903 m.18-19, m.22; 5510 ek m.2)
- Vizesi yapılmış belgedeki istihdamı aşmamak kaydıyla, komple yeni yatırımda yatırımla sağlanan, diğer cinslerde **yatırım öncesi son altı ay APHB ortalamasına** ilave edilen istihdam için, asgari ücrete isabet eden işveren hissesinin bölgeye göre bir kısmı veya tamamı Bakanlık bütçesinden karşılanır; süre bölge tablosundan (Hamle yatırımlarında ayrı süre). 6. bölgede ayrıca işçi hissesi desteği. OSB/EK-5 ilçe → alt bölge.
- Şart: APHB'nin ve sigortalı hissesi ile karşılanmayan işveren hissesinin **yasal süresinde** verilmesi/ödenmesi; geç ödemede gecikme zammı işverenden; aynı sicildeki birden çok belge birleştirilmez; alt işveren işçileri dikkate alınabilir.
- Muhtelif illerde gerçekleştirilen sektörel yatırımlara SGK primi desteği yok; 1. bölgeden 4-6. bölgeye taşınan imalat yatırımlarına (nakil belgesi) asgari istihdam ve makinenin firma aktifinde bulunma şartıyla yalnız bölgesel destek.
- 5510 ek m.2: karşılanan prim gider yazılamaz; fiilen çalışmayan sigortalı bildirimi tespitinde **bir yıl** destekten yararlanılamaz; yersiz yararlanma gecikme cezası ve zammıyla tahsil; suç duyurusu.
- İstihdama bağlı **diğer** SGK teşvikleri ve SGK itirazı → `../../sosyal-guvenlik-sgk/SKILL.md`. 4447/5510 teşvikleriyle aynı sigortalı için birlikte uygulama (çakışma) kuralını orada kontrol et `[incele]`.

### 1.7 Yatırım yeri tahsisi (9903 m.21)
- 4706 ek m.3 çerçevesinde Hazine taşınmazı; Hamle yatırımlarında Sanayi Bölgeleri GM usulüyle; vergi indirimi öngörülmeyen yatırımlar ve elektrik üretimi tahsis alamaz. Tahsis sonrası imar/ruhsat → `../../idare-davalari-imar/SKILL.md`.

---

## 2. Birleşme (kümülasyon) yasağı — 9903 m.33

- Karar kapsamındaki desteklerden yararlanan yatırım **diğer kamu kurum ve kuruluşlarının desteklerinden yararlanamaz**; başka kamu desteği alınan/alınacak yatırım için Karar desteklerine müracaat edilemez; aykırılıkta Karar destekleri geri alınır.
- **İstisna:** başka kurumdan yalnız sübvansiyonlu kredi ya da krediyle ilgili başka destek alınmışsa, o krediye Karar'ın faiz/makine desteği verilmemek kaydıyla diğer Karar desteklerinden yararlanılır; bu imkân vizesi yapılmamış eski belgelere de uygulanır.
- **Teknoloji Hamlesi:** KOSGEB ve/veya TÜBİTAK doğrudan destek verebilir; bu desteklerle yapılan harcama yatırım bütünlüğü kapsamında değerlendirilebilir.
- **Toplam destek üst sınırı:** KDV, gümrük, vergi indirimi, faiz ve makine desteklerinin yeniden değerlenmiş toplamı, yeniden değerlenmiş gerçekleşen sabit yatırımı geçemez (1.1.2026'dan).
- 5746 Ar-Ge teşvikleri ile 4691 TGB istisnası birbirini dışlar → `ar-ge-tasarim-ve-teknopark.md`.

Eski YAML'daki "birbiriyle çakışmayan (non-stacking) maksimum fayda yol haritası" fikri korunur, ama kural artık açık yasaktır: KOSGEB/ajans hibesi ile teşvik belgesini aynı yatırımda birleştirmeden önce m.33'ü uygula `[incele]`.

---

## 3. Süreler ve dayanakları

| Konu | Süre | Dayanak |
|---|---|---|
| Vergi indirimi (7555 sonrası belgeler) | İlk indirim dönemi dahil en fazla on hesap dönemi | KVK 32/A (7555 m.18) |
| KDV 13/d zamanaşımı | Gerektiren durumun meydana geldiği tarihi izleyen takvim yılı başından | 3065 m.13/d |
| Faiz/kâr payı desteği | Karar'daki azami süre, ilk kredi kullanımından | 9903 m.15/1 |
| SGK desteği | Karar m.18 tablosu; vize sonrası bildirimi izleyen aydan | 9903 m.18/2-3; Tebliğ m.17/3 |
| 5510 ek m.2 yaptırımı | Bir yıl destekten yoksunluk | 5510 ek m.2 |
| Geri alınan faiz desteği | Her ödeme tarihinden 6183 m.51 gecikme zammı | 9903 m.15/8, m.17/5 |

---

## 4. Görüşme soruları

| Soru | Neden |
|---|---|
| Belge alım tarihi ve müracaat tarihi (16.06.2025 öncesi mi)? | 32/A eski/yeni metin |
| Hangi unsurlar belgede kayıtlı? Belgenin "destek unsurları" sayfasını paylaşır mısınız? | Unsur yoksa uygulanmaz |
| KDV istisna belgesi alındı mı; istisnalı alınan makine listede mi, yeni mi? | 13/d |
| Yatırımdan kazanç elde edilmeye başlandı mı, hangi dönemde? | On dönem sınırı, kullanılmayan katkı |
| Faiz desteği mi makine desteği mi talep edildi? | Birbirini dışlar |
| SGK APHB'leri ve primler süresinde mi? Fiilen çalışmayan bildirimi tespiti var mı? | SGK desteği kaybı |
| Başka kurumdan hibe/kredi desteği var mı? | m.33 |

---

## 5. soorgla çağrıları

```
legal_get_statute_article law_no: "3065" law_type: "Kanun" article_no: "13"
legal_list_statute_articles law_no: "3065" law_type: "Kanun" article_query: "teşvik belgesi" # geçici m.30, 37, 42
legal_search_statute_semantic sorgu: "indirimli kurumlar vergisi yatırım teşvik belgesi yatırıma katkı" mevzuat_no: "5520"
legal_get_statute_article law_no: "5510" law_type: "Kanun" article_no: "ek 2"
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/07/20250724-2.htm" # 7555 (32/A, 5746, 4691)
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2026/06/20260604-1.htm" # 7582 (KVK 32/8)
legal_search_admin_guidance sorgu: "<unsur> yatırım teşvik belgesi" tarih_baslangic: "2024-01-01" belge_tur: "ozelge"
legal_search_admin_guidance sorgu: "<unsur> yatırım teşvik belgesi" kurum: "Gelir İdaresi Başkanlığı"
legal_search_cases mahkeme: "danistay" sorgu: "yatırım teşvik belgesi kapsamında KDV istisnası makine teçhizat belge eki liste tarhiyat" tarih_baslangic: "2023-01-01"
legal_get_legal_interest_rates # politika_faizi (faiz desteği hesabı için; baslangic_tarihi ile dönemi kontrol et)
legal_get_exchange_rate # döviz kredisi / ithal makine
```

---

## 6. İdare tarafı

- **Vergi dairesi:** KDV istisna belgesi verirken belge eki listeyi ve makine niteliğini kontrol et; teşvik belgesi iptalini öğrenince tarhiyattan önce iptalin kesinleşip kesinleşmediğini, geri alınıp alınmadığını ve vize durumunu Bakanlıktan sor (Danıştay 3. D. E.2023/5837 K.2024/6305: iptal geri alınıp vize yapılınca tarhiyatın dayanağı kalmaz).
- **SGK:** Bakanlık bildirimini, APHB ve ödeme şartlarını, aynı sicilde birden çok belgeyi ayrı ayrı uygula.
- **Teşvik Uygulama GM:** faiz/makine desteği hak edişini ilerleme raporu ve aracı kurum bildirimleriyle kümülatif hesapla; fazla ödemeyi m.17/4-5'e göre geri al.

---

## 7. Çıktı iskeleti

```markdown
## Destek unsurları değerlendirmesi — [belge no] — [tarih]
| Unsur | Belgede var mı | Şart | Durum | Risk | Dayanak |
| Gümrük vergisi muafiyeti | | | | | 9903 m.13 |
| KDV istisnası | | | | | 3065 m.13/d |
| Vergi indirimi | | | | | KVK 32/A; 9903 m.20 |
| Faiz/kâr payı | | | | | 9903 m.15 |
| Makine desteği | | | | | 9903 m.16 |
| SGK işveren hissesi / prim | | | | | 9903 m.18-19; 5510 ek m.2 |
| Yer tahsisi | | | | | 9903 m.21 |
### Birleşme yasağı kontrolü (m.33)
### Parasal etki — kullanıcı rakamıyla [incele]
```

---

## 8. Sık hatalar

- 🔴 7555 sonrası belgede yatırıma katkı tutarını sınırsız süre devrettirmek; kazanç varken kullanılmayan katkı sonraki döneme geçmez.
- 🔴 KDV geçici m.37 süresini madde metnindeki 31.12.2025'e göre hesaplamak (CB Kararı 9770 ile 31.12.2028'e uzatıldı).
- 🟠 Faiz desteği ile makine desteğini aynı Hamle yatırımında birlikte planlamak.
- 🟠 KOSGEB/ajans hibesi alınmış yatırıma ayrıca teşvik belgesi istemek (m.33).
- 🟠 Belge eki listede olmayan ya da makine niteliği taşımayan kalemi istisnalı almak.
- 🟡 SGK desteğinin vizeden önce başlayacağını sanmak.

---
