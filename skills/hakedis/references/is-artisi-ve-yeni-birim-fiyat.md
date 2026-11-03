# İş artışı, iş eksilişi, yeni birim fiyat ve işin tasfiyesi

## Ne zaman kullanılır
- Sözleşme kapsamında ilave iş (keşif artışı) yaptırılacak ya da yaptırıldı; iş artışı oluru, mukayeseli keşif, revize proje.
- Sözleşmede fiyatı bulunmayan bir iş kalemi için **yeni birim fiyat (YBF)** belirlenecek ya da belirlenen fiyat tartışmalı.
- İşin %10 / %20 sınırı içinde bitmeyeceği anlaşıldı (tasfiye) ya da iş %80'in altında bitecek (iş eksilişi).
- İdare tarafı: "Bu artışı onaylarsam Sayıştay sorar mı?"

---

## 1. Kanun metni (4735 m.24)

Öngörülemeyen durumlar nedeniyle iş artışı **zorunlu** olursa, artışa konu iş;
- (a) **sözleşmeye esas proje içinde kalması**,
- (b) idareyi külfete sokmaksızın **asıl işten ayrılmasının teknik veya ekonomik olarak mümkün olmaması**

şartlarıyla, **anahtar teslimi götürü bedel yapım işlerinde sözleşme bedelinin %10'una**, **birim fiyatlı** mal, hizmet ve yapım sözleşmelerinde **%20'sine** kadar, **süre hariç** sözleşme ve ihale dokümanı hükümleri çerçevesinde aynı yükleniciye yaptırılabilir. Birim fiyatlı **yapım** işlerinde Cumhurbaşkanı bu oranı sözleşme bazında **%40'a kadar** artırmaya yetkilidir.

- İş bu şartlar içinde tamamlanamayacaksa **artış yapılmaksızın hesabı genel hükümlere göre tasfiye edilir**; bu durumda işin tamamının ihale dokümanı ve sözleşmeye uygun yapılması zorunludur.
- Sözleşme bedelinin **%80'inden düşük** bedelle tamamlanacağı anlaşılan işlerde yüklenici işi bitirmek zorundadır; yükleniciye gerçek giderleri ve kârı karşılığı olarak, sözleşme bedelinin %80'i ile sözleşme fiyatlarıyla yaptığı iş tutarı arasındaki farkın **%5'i** geçici kabul tarihindeki fiyatlar üzerinden ödenir.

---

## 2. Kontrol listesi — iş artışı

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TÜR-SINIR | Sözleşme türü ve uygulanacak sınır: götürü bedel %10, birim fiyat %20; Cumhurbaşkanı kararıyla artırılmış oran (birim fiyatlı yapım, %40'a kadar) var mı? | 4735 m.24/1-2 | Karma sözleşmede her kısım kendi sınırıyla `[incele]` |
| ÖNGÖRÜLEMEZLİK | Artış ihale öncesinde öngörülemeyen bir durumdan mı (zemin, mevzuat değişikliği, yer koşulu) doğdu, yoksa proje hatası/eksikliği mi? | 4735 m.24/1 | Proje hatası tek başına öngörülemezlik değildir `[incele]`; idare için 🔴 Sayıştay riski |
| PROJE-İÇİ | Artışa konu iş sözleşmeye esas proje içinde mi? Projeden bağımsız yeni yapı → ayrı ihale | 4735 m.24/1-a | Kampüse ayrı bina eklemek iş artışı değildir |
| AYRILMAZLIK | Asıl işten ayrılması teknik/ekonomik olarak mümkün değil mi? | 4735 m.24/1-b | Mümkünse ayrı ihale |
| GÖTÜRÜ-KAPSAM | Götürü bedelde artış diye ödenen imalat zaten götürü bedel kapsamında (poz tarifi, uygulama projesi) mı? | Sözleşme, poz tarifleri | Sayıştay bunu kamu zararı saydı |
| ORAN-HESABI | Oran = toplam artış tutarı / **ilk sözleşme bedeli**; fiyat farkları hesaba katılmaz | 4735 m.24; Genel Şartname m.21/1, 4, 6 | YBF ile yapılan kalemler oran hesabında hangi fiyatla? → §4. Genel Şartname m.21/4: "İşin tamamı ifadesinden ilk sözleşme bedeline karşılık gelen iş miktarı anlaşılır"; m.21/6: YBF'li artış tutarı uygulama ayı Pn'ine bölünerek **ihale tarihi itibarıyla** hesaplanır (fiyat farkı etkisi ayıklanır). |
| ARTIŞ-EKSİLİŞ | Eksilişler artışla mahsup edilerek "net %20" mi hesaplandı? | Genel Şartname m.21 | Eski YAML "mutlak artış esastır, eksiliş kotayı açmaz" diyordu. m.21 artış ile eksilişin **mahsubunu düzenlemiyor**; yalnız götürü bedelde eksilişin ihale tarihi itibarıyla tutarının m.21/6 esaslarıyla hesaplanacağını söylüyor (m.21/7). Mahsup sorusu Sayıştay ve yargı kararından çözülür → `[incele]` |
| OLUR | İhale yetkilisinin iş artışı oluru (gerekçe raporu, mukayeseli keşif, revize proje) artıştan **önce** alındı mı? | Genel Şartname m.12, m.21 | Olursuz yapılan imalat ödeme riski; yüklenici için 🟠 |
| SÜRE | Proje değişikliği varsa değişikliğe konu işin yapılması için gerekli süre hesaplanarak süre uzatımı verildi mi? | Genel Şartname m.12/4 (1.9.2025 sonrası: "süre uzatımı verilir") | "Süre hariç" ifadesi (4735 m.24) artışın eski süreye sıkıştırılması demek değildir `[incele]` |
| PROJE-GÖRÜŞ | Yükleniciye proje değişikliği tebliğ edildiyse görüşlerini tebliğ/bildirimden itibaren **15 gün** içinde bildirdi mi? | Genel Şartname m.12/6 (1.9.2025 sonrası) | |
| UYGULAMA-PROJESİ | Birim fiyatlı işin onaylı uygulama projesi olmayan kısmına başlandı mı? (Başlanamaz; sorumluluk aykırı davranan tarafta) | Genel Şartname m.12/2 (1.9.2025 sonrası) | |
| BAŞKA-YÜKLENİCİ | İdare, proje içinde kalan zorunlu artışı başka yükleniciye de yaptırabilir; yüklenici bundan hak iddia edemez | Genel Şartname m.22/7 (1.9.2025 sonrası) | |
| SINIR-AŞIMI | Sınır aşılacaksa: artış yapılmaksızın **tasfiye** (4735 m.24/3) ya da ayrı ihale; sınırı aşan ödeme | 4735 m.24/3 | Eski YAML "%10,01 aşımda devam ettirmek suçtur" diyordu → kanunda böyle bir hüküm yok; sonuç tasfiye ve kamu zararı/disiplin riski `[incele]` |
| İŞ-DENEYİM | İş artışı iş deneyim belgesi tutarına nasıl yansır? | YİİUY m.46/2: belge tutarı fiyat farkları **hariç**, varsa **yasal keşif artışları dahil** sözleşme fiyatlarıyla yapılan iş üzerinden yazılır (özel sektör işlerinde sözleşmede iş artışı hükmü varsa en çok %10, m.46/4). **Düzeltme:** önceki metin m.46/5'i iş artışı kuralı sanıyordu; m.46/5 idarenin yükleniciye verdiği malzeme bedelinin yarısının belge tutarına eklenmesidir ve 9.4.2026'da "ilk sözleşme bedelinin %20'sini aşmamak üzere" sınırı bu ekleme için getirildi | Ayrıntı `../../kamu-ihale/SKILL.md` |

---

## 3. Yeni birim fiyat (Genel Şartname m.22) — 1.9.2025 sonrası metin

Proje değişikliği şartları gerçekleştiğinde, idarenin gerekli görüp yaptırmak istediği ve ihale dokümanında/teklifte fiyatı bulunmayan iş kalemlerinin ve m.21'e göre yaptırılan ilave işlerin birim fiyatları **yüklenici ile birlikte** tespit edilir. Birim fiyat sözleşmede yeni birim fiyatlar üzerinden; götürü bedelde yeni birim fiyatlarla hesaplanan artış tutarına göre belirlenecek ilerleme yüzdeleriyle ödenir.

**Analiz sırası (m.22/2):**
1. (a) Yüklenicinin **aşırı düşük teklif açıklaması** kapsamında sunduğu ve yeni kaleme benzeyen kalemlerin analizleri,
2. (b) İdarede veya diğer idarelerde mevcut benzer analizler,
3. (c) İdarenin daha önceki benzer işlerinin sözleşmelerinde ortaya çıkan maliyet analizleri,
4. (ç) Yeni kalemin yapımı sırasında tutulacak **puantajla** tespit edilen girdiler.

**Rayiçler (m.22/3):** fiyat farkı öngörülen ve öngörülmeyen işlerde ayrı ayrı düzenlenmiş; aşırı düşük teklif rayiçleri, kamu kurumlarının yayımladığı rayiçler (alt endeksle güncellenerek), idarenin önceki işlerinin rayiçleri, idarece kabul edilen ticaret/sanayi odası onaylı yerel rayiçler.

**Kâr ve genel gider (m.22/4):** sözleşmede önceden belirlenmiş oran varsa o; yoksa kâr ve genel gider hariç analiz tutarına **%10 yüklenici kârı** ile **%15'e kadar** idare ve yüklenicinin anlaştığı oranda genel gider eklenir.

**Üst sınır (m.22/5, oran sözleşmede belirlenmemişse):** benzer kalem varsa, yüklenicinin benzer kalem için teklif ettiği fiyatın resmî analizle hesaplanan fiyata oranı (**%90'ı aşmamak üzere**) ile yeni kalemin resmî analiz fiyatının çarpımını; benzer kalem yoksa resmî analiz fiyatının **%90'ını** geçemez.

**Süre ve anlaşmazlık (m.22/6):** yeni fiyat proje değişikliği onay tarihinden itibaren **30 gün** içinde ve her hâlde imalata başlanmadan tespit edilir; tutanak aynı süre içinde idare onayına sunulur. Uyuşulamazsa **anlaşmazlık tutanağı** düzenlenir ve idare **10 gün** içinde Yüksek Fen Kuruluna intikal ettirir; YFK'nın tespit ettiği fiyatı iki taraf kabul etmek zorundadır; yüklenici kararı beklemeden idarenin tespit ettiği **geçici fiyatla** işe devam eder.

**İş eksilişi (m.22/8):** proje değişikliğine bağlı iş eksilişinde eksilen imalatın fiyatı da yeni fiyat hükümleriyle hesaplanır.

**Ocak ve depo yeri değişikliği (m.30/3) ve sonradan istenen yıkım işleri (m.31/1):** etkilenen kalemler için m.22'ye göre yeni fiyat.

### YBF kontrol listesi

| Kod | Kontrol | Not |
|---|---|---|
| GEREKLİLİK | Kalem gerçekten sözleşmede yok mu, yoksa var olan pozun benzeri/türevi mi? | Benzer poz varsa YBF yerine sözleşme fiyatı ya da m.22/5 sınırı |
| SIRA | m.22/2 sırası izlendi mi? Üst sıradaki analiz varken puantaja ya da faturaya mı gidildi? | 1.9.2025 öncesi sözleşmelerde eski m.22 metni geçerli `[incele]` |
| RAYİÇ | Rayiçler ilgili alt endeksle doğru aya güncellendi/indirgendi mi? | Endeks ayını yaz |
| KÂR | Kâr ve genel gider bir kez mi eklendi (kârlı resmî poza tekrar kâr eklenmesi)? | Çifte kâr klasik Sayıştay bulgusu |
| %90 | Üst sınır (m.22/5) aşıldı mı? | Yalnız sözleşmede oran yoksa |
| SÜRE | 30 gün ve "imalattan önce" şartı; anlaşmazlıkta 10 gün YFK intikali | Yüklenici: anlaşmazlık tutanağını mutlaka iste |
| FİYAT-FARKI | YBF'nin fiyat farkı hesabında hangi aya ilişkin olduğu | Esaslar m.6/8 → `fiyat-farki.md` |
| ORAN-ETKİSİ | YBF ile yapılan kalemin iş artışı oran hesabına etkisi | Genel Şartname m.21/6 → §4 |

---

## 4. YBF'nin iş artışı oranına etkisi (Genel Şartname m.21/6, 1.9.2025 sonrası)

Sözleşmede birim fiyatı bulunmayan kalem için m.22'ye göre YBF yapıldığında, iş artışının yasal sınır içinde olup olmadığı hesaplanırken:
- fiyat farkı öngörülen işlerde bu kalem için **ihale tarihinin içinde bulunduğu aya** ilişkin;
- fiyat farkı öngörülmeyen işlerde proje değişikliği iş bitim tarihinden önceyse **onay ayına** ilişkin, sonraysa onay ayına ilişkin fiyatın iş bitim ayına endeksle **indirgenmiş** hâli

esas alınır.

---

## 5. Süreler

| Süre | Başlangıç | Dayanak |
|---|---|---|
| Proje değişikliğine görüş: 15 gün | Tebliğ/bildirim | Genel Şartname m.12/6 (1.9.2025 sonrası) |
| Yeni fiyatın tespiti ve onaya sunulması: 30 gün, imalattan önce | Proje değişikliği onayı | Genel Şartname m.22/6 |
| Anlaşmazlığın YFK'ya intikali: 10 gün (idare) | Anlaşmazlık tutanağı | Genel Şartname m.22/6 |
| YFK'ya itiraz (genel yol) | Kesin kabul tamamlanıncaya kadar; idare 30 günde gönderir, YFK 60 günde karar verir | 4735 ek m.2 |

`legal_calculate_deadline` Genel Şartname sürelerini tanımaz (canlıdaki 4735 kodları yalnız m.20/a ihtarı ve m.10 mücbir sebep bildirimi); elle hesapla, `legal_check_holiday`, `[doğrula]`.

---

## 6. Görüşme soruları

| Alan | Soru |
|---|---|
| Tür | Sözleşme türü; ilk sözleşme bedeli; Cumhurbaşkanı kararıyla artırılmış oran var mı? |
| Gerekçe | Artışın sebebi ne; ihale öncesi etüt ve proje bunu öngörebilir miydi? |
| Belgeler | Mukayeseli keşif, revize proje, gerekçe raporu, iş artışı oluru, saha tutanakları, idarenin yazılı talimatı? |
| YBF | Hangi kalemler için YBF yapıldı; hangi analiz ve rayiçlerle; tutanak tarihi; anlaşmazlık tutanağı? |
| Eksiliş | Eksilen kalemler ve tutarları; net mi mutlak mı hesaplandı? |
| Süre | Artış için süre uzatımı istendi/verildi mi? |

---

## 7. MCP adımları

```
legal_get_statute_article law_no: "4735" law_type: "Kanun" article_no: "24"
legal_get_statute_article_history law_no: "4735" law_type: "Kanun" article_no: "24"
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/07/20250730-16.htm" # Genel Şartname m.12, 21, 22 yeni metni
legal_search_official_gazette query: "iş artışı oranı Cumhurbaşkanı Kararı birim fiyat yapım" sort_by: "date_desc"
legal_search_cases mahkeme: "sayistay" sorgu: "<ör. anahtar teslimi götürü bedel kapsamındaki imalata iş artışı yoluyla ödeme kamu zararı>"
legal_search_cases mahkeme: "yargitay" daire: "6. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "kamu ihale yapım işi yeni birim fiyat yüklenici ile anlaşılamaması Yüksek Fen Kurulu fiyatı"
legal_get_case_document belge_id: "<seçilen>"
```

---

## 8. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …
## İş artışı / YBF denetimi — [işin adı] — [yüklenici / idare]
### Sonuç
[Uygun / sınır aşımı / gerekçe yetersiz — tek cümle]
### Sınır hesabı
| Sözleşme türü | İlk sözleşme bedeli | Toplam artış | Oran | Kanuni sınır | Durum |
### Şart kontrolü (4735 m.24)
| Öngörülemezlik | Proje içinde | Ayrılamazlık | Olur tarihi | Süre uzatımı |
### YBF tablosu
| Kalem | Analiz yöntemi (m.22/2 a-ç) | Rayiç ve güncelleme ayı | Kâr+GG | %90 sınırı | Tutanak tarihi | İşaret |
### Riskli bulgular
[ör. eksiliş mahsubuyla gizlenen aşım; götürü kapsamındaki imalata artış ödemesi]
### Aksiyon
[tasfiye / ayrı ihale / tutanak revizyonu / YFK]
```

---

## 9. Sık hatalar
- Proje hatasını "öngörülemeyen durum" saymak.
- Götürü bedel kapsamındaki işi iş artışı olarak ödemek.
- Oranı güncel (fiyat farklı) bedel üzerinden hesaplamak.
- YBF'yi imalattan sonra belirlemek ya da anlaşmazlık tutanağı düzenlemeden yükleniciye fiyat dayatmak.
- Kârlı resmî poza ikinci kez kâr eklemek.
- Sınırı aşan işte tasfiye yerine "ek sözleşme" yapmak (4735 m.4: kanundaki haller dışında ek sözleşme düzenlenemez).

## Eski YAML'dan düzeltilenler
- **YBF analiz sırası:** YAML "(a) yüklenicinin sözleşmedeki diğer birim fiyatları, (b) resmî kurum analizleri, (c) meslek odası/üniversite rayiçleri, (ç) faturalar" diyordu → 1.9.2025 sonrası sıra: aşırı düşük teklif analizleri, idarelerin benzer analizleri, idarenin önceki işleri, puantaj.
- **Kâr oranı:** YAML "%25 yüklenici kârı ve genel gider" diyordu → sözleşmede oran yoksa %10 kâr + %15'e kadar anlaşılan genel gider, ayrıca %90 üst sınır.
- **Götürü bedelde 0,90 katsayısı:** YAML "YBF'de 0,90 katsayısı uygulanmalı" diyordu → güncel kural m.22/5'teki %90'ı aşmayan oran sınırıdır.
- **%10 aşımı "suçtur":** kanunda karşılığı yok; sonuç tasfiye (4735 m.24/3).
- **Birim fiyatta %20:** YAML Cumhurbaşkanının birim fiyatlı yapım işlerinde %40'a kadar artırma yetkisini anmıyordu.
