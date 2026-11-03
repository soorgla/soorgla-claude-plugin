# İhale: idare tarafının kararları — ihale komisyonu kararı ve şikâyete cevap (gerekçeli karar)

İhaleyi yapan idarenin iki belgesi. Kullanıcı genellikle idare personeli (komisyon üyesi, ihale birimi) ya da idareye danışmanlık yapan avukattır. İsteklinin dilekçesi bu dosyada değil: `ihale-sikayet-ve-itirazen-sikayet.md`.

Bu belgeler idarenin işlemidir; **imza yetkisi olmayan kullanıcı adına imza satırı doldurulmaz**, komisyon üyeleri ve ihale yetkilisi `[___]` kalır.

---

## 1. İhale komisyonu kararı (4734 m.40)

### Süre ve dayanak

| İşlem | Kural | Dayanak |
|---|---|---|
| Karar içeriği | Komisyon **gerekçeli kararını** belirleyip ihale yetkilisinin onayına sunar. Kararda **isteklilerin adları/unvanları, teklif edilen bedeller, ihalenin tarihi, hangi istekli üzerine hangi gerekçeyle** yapıldığı, ihale yapılmamışsa **nedenleri** yazılır. | 4734 m.40/5 |
| Onay süresi | İhale yetkilisi karar tarihini izleyen **en geç 5 iş günü** içinde onaylar ya da gerekçesini açıkça belirterek iptal eder; onaylanırsa geçerli, iptal edilirse hükümsüz | 4734 m.40/6-7 |
| Yasaklılık teyidi | Onaydan **önce** idare, ihale üzerinde kalan ve varsa ekonomik açıdan en avantajlı **ikinci** teklif sahibinin yasaklı olup olmadığını teyit ettirip belgeyi karara **ekler**; ikisi de yasaklıysa ihale iptal edilir | 4734 m.40 son fıkra |
| Ekonomik açıdan en avantajlı teklif | Yalnız fiyat ya da fiyat + fiyat dışı unsurlar (dokümanda parasal değer/nispi ağırlık belirlenmiş olmalı); yerli istekli fiyat avantajı (m.63) uygulanır; eşit fiyatta fiyat dışı unsurlar | 4734 m.40/1-4 |
| Değerlendirme sırası | Belgelerin kontrolü, yeterlik, aritmetik hata, aşırı düşük teklif sorgulaması | 4734 m.37, m.38 |
| Komisyon ve karar nisabı | En az beş ve tek sayıda üye (biri başkan; ikisi işin uzmanı; muhasebe/mali işlerden bir personel). Komisyon **eksiksiz toplanır**, **çoğunlukla** karar alır, **çekimser kalınamaz**; karşı oy kullanan üye gerekçesini karara yazıp imzalamak zorundadır. Kararlar başkan ve üyelerin ad, soyad ve unvanlarıyla imzalanır. | 4734 m.6 |

Onaylanan ihale kararı, onay gününü izleyen **en geç 3 gün** içinde teklif veren **bütün isteklilere** bildirilir; bildirimde değerlendirme dışı bırakılma gerekçeleri de yazılır; iptalde de gerekçeli bildirim yapılır. Bildirimden itibaren 21/(b)-(c)'de 5 gün, diğer hâllerde 10 gün geçmeden sözleşme imzalanamaz. Bu bildirim çoğu olayda isteklinin şikâyet süresi bakımından "farkına varma" tarihidir (m.55).

### Görüşme soruları
| Alan | Soru |
|---|---|
| `administration_name` | İdarenin adı? |
| `tender_name` / `tender_registration_number` | İşin adı ve İKN? |
| `tender_date_method` | İhale tarihi ve usulü? |
| `approximate_cost` | Yaklaşık maliyet? (karar metnine yazılıp yazılmayacağı idarenin uygulamasına göre `[incele]`) |
| `commission_members` | Komisyon başkanı ve üyeleri (ad, unvan)? Karşı oy var mı? |
| `bidders_evaluation[]` | Her istekli: ad/unvan, teklif tutarı, geçerli mi, değerlendirme dışıysa **somut** gerekçe (hangi belge, hangi doküman maddesi)? |
| (yeni) | Aşırı düşük teklif sorgulaması yapıldı mı? Açıklama istenen ve reddedilenler? |
| (yeni) | Fiyat dışı unsur ya da yerli malı avantajı var mı? |
| `winning_bidder` / `second_best_bidder` | En avantajlı ve ikinci teklif sahibi? |
| `ban_check_statement` | Yasaklılık teyidi yapıldı mı, tarihi? (yapılmadıysa karar "onaya hazır" değildir) |
| `decision_rationale` | Gerekçe? |

### İskelet
```markdown
                              İHALE KOMİSYONU KARARI

İdarenin adı : [___]
İşin adı : [___]
İKN : [___]
İhale usulü / tarihi : [___]
[Yaklaşık maliyet : ___] (idare uygulamasına göre)

1. TEKLİFLERİN DEĞERLENDİRİLMESİ
İhale komisyonu [tarih] tarihinde saat [__:__]'da toplanarak teklifleri 4734 sayılı Kanun'un 37 ve 38. maddeleri
ile ihale dokümanı hükümleri çerçevesinde değerlendirmiştir.
a) Belge kontrolü ve yeterlik değerlendirmesi: [___]
b) Aritmetik hata kontrolü: [___]
c) Aşırı düşük teklif sorgulaması: [yapıldı/yapılmadı — sonuç]

| İstekli | Teklif tutarı (TL) | Durumu | Değerlendirme dışı bırakılma gerekçesi (doküman maddesiyle) |
|---|---|---|---|

2. KARAR VE GEREKÇE
[Ekonomik açıdan en avantajlı teklifin hangi esasla belirlendiği; ikinci teklif]

3. YASAKLILIK TEYİDİ
İhale üzerinde bırakılan istekli ile ekonomik açıdan en avantajlı ikinci teklif sahibinin ihalelere katılmaktan
yasaklı olup olmadığı [tarih]'de teyit edilmiş, teyit belgesi karara eklenmiştir. (4734 m.40 son fıkra)

SONUÇ: İhalenin [___] üzerinde bırakılmasına, [___]'in ekonomik açıdan en avantajlı ikinci teklif sahibi olarak
belirlenmesine ve kararın ihale yetkilisinin onayına sunulmasına [oy birliği / oy çokluğu] ile karar verilmiştir.
[Karşı oy gerekçesi: ___]

İHALE KOMİSYONU
Başkan [Ad SOYAD — imza] Üye [___] Üye [___] …

İHALE YETKİLİSİ ONAYI: [ONAYLANMIŞTIR / gerekçeli İPTAL] — [tarih] — [Ad SOYAD, unvan, imza]
```

---

## 2. Şikâyete cevap — idarenin gerekçeli kararı (4734 m.55/3, m.54)

### Süre ve dayanak
| İşlem | Kural | Dayanak |
|---|---|---|
| Karar süresi | Şikâyet üzerine gerekli inceleme yapılarak **10 gün** içinde **gerekçeli** karar | 4734 m.55/3 |
| Bildirim | Karar tarihini izleyen **3 gün** içinde şikâyetçiye, diğer aday/isteklilere ve (yalnız ilan ve dokümana yönelik başvurularda) istekli olabileceklere | 4734 m.55/3 |
| Karar türleri | (a) düzeltici işlemle giderilemeyecek aykırılık → **ihalenin iptali**; (b) düzeltmeyle giderilebilecek → **düzeltici işlem**; (c) süre/usul/şekil eksikliği, usulüne uygun imzalanmış sözleşme, aykırılık tespit edilememesi → **başvurunun reddi** | 4734 m.54 (karar türleri fıkrası) Eski YAML bunu "m.55/4" diye gösteriyordu; karar türleri m.54'tedir. |
| Doküman şikâyeti ve erteleme | Dokümanda düzeltme kararı verilirse son başvuru/ihale tarihi m.29'a göre **bir defaya mahsus** ertelenir; hata ilanda da varsa m.26 uygulanır. Doküman şikâyetlerinin ihale tarihinden önce sonuçlandırılması esastır. | 4734 m.55/2 |
| Kanun yolu bilgisi | Kararın bildirimini izleyen **10 gün** içinde Kuruma itirazen şikâyet; iptal kararına karşı 5 gün | 4734 m.55/4, m.56/1 |
| Sözleşme yasağı | Kararın son bildirim tarihini izleyen 10 gün geçmeden ve itirazen şikâyet sorgulaması yapılmadan (başvuru varsa Kurum nihai kararı verilmeden) sözleşme imzalanamaz | 4734 m.55 son fıkra |

Karar süresi kaçarsa istekli doğrudan Kuruma gider (m.55/4); idare açısından 🔴.

### Görüşme soruları
| Alan | Soru |
|---|---|
| `administration_name` / `tender_registration_number` | İdare ve İKN? |
| `complainant_name` | Şikâyet eden? |
| `complaint_date_number` | Şikâyetin idare kayıtlarına giriş tarihi ve sayısı? (10 günlük süre buradan) |
| `complaint_claims[]` | Şikâyet dilekçesindeki iddialar, numaralarıyla? (dilekçeyi isteyin) |
| `administration_evaluation[]` | Her iddia için idarenin teknik/hukuki değerlendirmesi ve dayandığı doküman/mevzuat maddesi? |
| (yeni) | Başvuru süre, ehliyet, şekil yönünden uygun mu? (önce bunu incele) |
| `decision_type` | Ret / düzeltici işlem / iptal? |
| `appeal_info` | (Standart kanun yolu ibaresi; m.55/4 ve m.56'ya göre otomatik.) |

### İskelet
```markdown
                                   T.C.
                             [İDARENİN ADI]
                              [Birimin Adı]

Sayı : E-[___] [gg.aa.yyyy]
Konu : [İKN] İKN'li ihaleye ilişkin şikâyet başvurusu hk.

                                GEREKÇELİ KARAR

İdarenin adı : [___]
İKN / İşin adı : [___]
Başvuru sahibi : [___]
Başvuru tarihi ve sayısı : [___]

1. BAŞVURUNUN SÜRE, USUL VE ŞEKİL YÖNÜNDEN İNCELENMESİ
[4734 m.54 ve m.55/1 — farkına varma tarihi, süre, imza, ehliyet]

2. BAŞVURU SAHİBİNİN İDDİALARI
1) [___]
2) [___]

3. İDARENİN DEĞERLENDİRMESİ
İddia 1: [iddia özeti] — [ilgili doküman maddesi] — [mevzuat] — [değerlendirme] — [sonuç: yerinde görülmüştür /
görülmemiştir]
İddia 2: [___]

4. SONUÇ VE KARAR
Yukarıda belirtilen gerekçelerle 4734 sayılı Kanun'un 54 ve 55. maddeleri uyarınca başvurunun
[REDDİNE / … yönünde DÜZELTİCİ İŞLEM BELİRLENMESİNE / İHALENİN İPTALİNE] karar verilmiştir.
İşbu kararın bildirimini izleyen on gün içinde Kamu İhale Kurumuna itirazen şikâyet başvurusunda bulunulabilir.
[İptal kararında: 4734 m.56/1 uyarınca beş gün]

                                                              [Ad SOYAD]
                                                              [İhale Yetkilisi]
Dağıtım: [şikâyetçi, diğer istekliler — m.55/3]
```

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4734" article_no: "6" | "37" | "38" | "40" | "41" | "54" | "55" | "56"
legal_get_statute_article law_no: "12766" article_no: "<ilgili madde>" # İhalelere Yönelik Başvurular Hakkında Yönetmelik
legal_search_statute_semantic sorgu: "aşırı düşük teklif sınır değer hesaplanması" mevzuat_tur: "kurum_yonetmeligi" # uygulama yönetmelikleri
legal_search_cases mahkeme: "kik" sorgu: "<ör. yasaklılık teyidi yapılmadan onaylanan ihale kararı>"
legal_search_cases mahkeme: "danistay" sorgu: "<…>" tarih_baslangic: "<son 3 yıl>"
legal_get_case_document belge_id: "<seçilen karar>"
```

## Sık hatalar

- 🔴 Yasaklılık teyidini onaydan sonra yapmak ya da ikinci teklif sahibini atlamak.
- 🔴 Şikâyete 10 gün içinde karar vermemek; kararı 3 gün içinde bildirmemek.
- 🟠 Değerlendirme dışı bırakma gerekçesini soyut yazmak ("belgeler uygun değil"); doküman maddesini göstermemek.
- 🟠 Gerekçeli kararda iddiaları tek tek cevaplamamak.
- 🟡 Kanun yolu bilgisini eksik yazmak (iptal kararında 5 gün).

---
