# İhale: idareye şikâyet ve KİK'e itirazen şikâyet dilekçesi

İstekli, aday ya da istekli olabilecek kişinin kamu ihalesindeki hukuka aykırılığa karşı iki aşamalı idari başvurusu. Şikâyet ve itirazen şikâyet **dava açılmadan önce tüketilmesi zorunlu idari başvuru yollarıdır**.

İdarenin şikâyete vereceği cevap (gerekçeli karar) bu dosyada değil: `ihale-idare-kararlari.md`.

---

## Ne zaman kullanılır

| Durum | Başvuru | Merci |
|---|---|---|
| İlan, ön yeterlik ya da ihale dokümanında (şartname, yaklaşık maliyet yöntemi, yeterlik kriteri, marka işaret etme) hukuka aykırılık | Şikâyet (dokümana) | İhaleyi yapan idare |
| Teklif değerlendirmesi, elenme, aşırı düşük teklif sorgulaması, kesinleşen ihale kararı | Şikâyet (değerlendirme/sonuç) | İhaleyi yapan idare |
| İdare şikâyeti reddetti, uygun olmayan karar aldı ya da süresinde karar vermedi | İtirazen şikâyet | Kamu İhale Kurumu |
| Şikâyet veya itirazen şikâyet üzerine idarenin aldığı **ihalenin iptali** kararı | Doğrudan Kuruma itirazen şikâyet | Kamu İhale Kurumu |

**Doğrudan KİK'e gidilemez** (iptal istisnası hariç): önce idareye şikâyet şarttır. Şikâyette ileri sürülmeyen iddia itirazen şikâyette ileri sürülemez; ileri sürülürse Kurul o iddiayı şekil yönünden reddeder. Bu yüzden **şikâyet dilekçesi yazılırken bütün iddialar eksiksiz yazılmalıdır**; sonradan eklenemez.

---

## Süre tablosu

| İşlem | Süre ve başlangıç | Dayanak | Not |
|---|---|---|---|
| İdareye şikâyet (genel) | İşlem/eylemin **farkına varıldığı veya varılmış olması gereken tarihi izleyen günden** itibaren **10 gün**; sözleşme imzalanmadan önce | 4734 m.55/1 | Eski YAML "kesinleşen ihale kararının tebliğinden itibaren 10 gün" diyordu; ölçüt tebliğ değil **farkına varma**dır. Kesinleşen ihale kararı bildirimi çoğu olayda farkına varma tarihidir ama her zaman değil `[incele]`. |
| İdareye şikâyet — 4734 m.21/(b) ve (c) pazarlık usulü | **5 gün** | 4734 m.55/1 | |
| İlana yönelik şikâyet | Süre **ilk ilan tarihinden** başlar | 4734 m.55/1 | |
| Ön yeterlik / ihale dokümanına yönelik şikâyet | Süre **dokümanın satın alındığı (EKAP'tan indirildiği) tarihte** başlar; her durumda **ihale veya son başvuru tarihinden üç iş günü öncesine kadar** | 4734 m.55/1-2 | 10 günlük süre ile 3 iş günü sınırından **hangisi önce dolarsa** o. Tebliğ'e göre ilana yansımayan doküman hükümleri için süre, dokümanın **EKAP hesabına giriş yapılarak indirildiği** tarihi izleyen gün başlar; dokümana karşı başvuru için istekli olabilecek sıfatı da bu indirmeyle kazanılır (İhalelere Yönelik Başvurular Hakkında Tebliğ m.3/2, m.4/2-b; değişik ibare RG 18.05.2024). |
| İdarenin karar süresi | Şikâyet üzerine **10 gün** içinde gerekçeli karar; karar tarihini izleyen **3 gün** içinde bildirim | 4734 m.55/3 | |
| KİK'e itirazen şikâyet | İdare kararının **bildirimini izleyen 10 gün**; idare süresinde karar vermezse **karar süresinin bitimini izleyen 10 gün**; sözleşme imzalanmadan önce | 4734 m.55/4, m.56/1 | Eski YAML "zımni ret" diyordu; kanun "karar alınmaması" der. Pazarlık usulünde de itirazen şikâyet süresi 10 gündür (5 gün kuralı yalnız ilk şikâyet için). |
| İdarenin şikâyet/itirazen şikâyet üzerine aldığı **iptal kararına** karşı | **5 gün** içinde **doğrudan Kuruma** | 4734 m.56/1 | Bu durumda inceleme idarenin iptal gerekçeleriyle sınırlıdır (m.56/2). |
| Kurul kararı süresi | Bilgi/belgenin kayda alındığı tarihi izleyen **20 gün**; pazarlık (21/b-c) ve iptal kararına karşı başvurularda **10 iş günü** | 4734 m.56/5 | |
| Kurul kararına karşı dava | İhale işlemleri (ihaleden yasaklama hariç) **ivedi yargılama usulüne** tabidir: dava açma süresi **30 gün** (genel 60 gün değil); 2577 m.11 (üst makama başvuru) uygulanmaz | 4734 m.57; 2577 m.20/A | Dava dilekçesi bu becerinin kapsamında değil; süreyi yalnızca hatırlat. |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, son gün için `legal_check_holiday`. "Gün" takvim günüdür; yalnızca doküman sınırı "iş günü"dür.

**Başvuru tarihi:** dilekçe idare veya Kurum dışındaki bir mercie verilip oradan gönderilirse **kayda girdiği tarih** başvuru tarihidir; postaya vermek süreyi korumaz. Süre son günlerindeyse elden ya da EKAP üzerinden başvuru öner `[doğrula — EKAP başvuru imkânı Tebliğ'de]`.

---

## Zorunlu unsurlar (4734 m.54)

Şikâyet idareye, itirazen şikâyet Kuruma **hitaben yazılmış imzalı dilekçe** ile yapılır ve şunları içerir:

a) Başvuru sahibinin, varsa vekil/temsilcinin adı, soyadı veya unvanı ve adresi
b) İhaleyi yapan idarenin ve ihalenin adı veya **İhale Kayıt Numarası (İKN)**
c) Başvuruya konu durumun **farkına varıldığı veya bildirildiği tarih**
d) Başvurunun konusu, sebepleri ve dayandığı deliller
e) (Yalnız itirazen şikâyette) idareye yapılan **şikâyetin tarihi** ve varsa idare kararının **bildirim tarihi**

Ek kurallar:
- Dilekçeye eklenecek belgeler (vekâletname, imza sirküleri, başvuru bedeli dekontu vb.) ve elektronik başvuru usulü **Kurumun düzenlemesindedir** (Yönetmelik ve Tebliğ). Listeyi oradan çek.
- **Tek dilekçe kuralı:** aynı kişi birden fazla ihaleye, birden fazla kişi aynı ihaleye tek dilekçe ile başvuramaz.
- Süresi dolmamış başvurudaki eksiklik, idare/Kurum bildirmese de **süre sonuna kadar** giderilebilir.
- **İddiaları ayrı ayrı numaralandır (itirazen şikâyet).** 09.04.2026 Tebliğ değişikliğiyle hangi hususun ayrı iddia, hangisinin tek iddia sayılacağı örneklerle düzenlendi: dokümanda her kriter/madde ayrı iddia; aynı sonuca (ör. tek markayı işaret etme) yönelen birden fazla madde tek iddia; her istekliye yönelik her husus ayrı iddia; bir belgenin birden fazla sebeple aykırılığı tek iddia; aşırı düşük açıklamanın birden fazla sebeple reddi tek iddia. Bu ayrım **başvuru bedelinin iadesini** doğrudan etkiler (aşağıda).

## İtirazen şikâyet başvuru bedeli

- Bedel **yaklaşık maliyete göre kademelidir** ve Kurum hesaplarına yatırılır; dekont dilekçeye eklenir. Kanun metnindeki (4734 m.53/j-2) tutarlar **taban tutarlardır**; her yıl 4734 m.67 uyarınca Kamu İhale Tebliği ile güncellenir. **Tutarı bu dosyadan ya da kanun metninden alma.**
  - Çağrı: `legal_search_official_gazette` `query: "Kamu İhale Tebliği"` `search_in: "title"` `sort_by: "date_desc"` → başvuru tarihinde yürürlükte olan yılın tebliğini aç (`legal_get_official_gazette_document`) ve m.53/(j)-(2) satırını oku.
  - Yaklaşık maliyet bilinmiyorsa kullanıcıya sor (ihale ilanında/EKAP'ta yazar); bilinmiyorsa en üst kademeyi yatırma önerisi `[incele]`.
- **İade:** 7571 sayılı Kanunla (24.12.2025) bedelin, dilekçedeki iddialara göre belirlenecek **haklılık oranına** karşılık gelen kısmı iade edilir; ret ya da eşit muamele incelemesiyle verilen iptal/düzeltici işlem kararlarında iade yoktur. İade, Kurul kararının bildirimini izleyen **30 gün** içinde yazılı talep üzerine yapılır. Dilekçeyi yazarken iddiaları Tebliğ'e uygun ayırmak bu yüzden para kaybını önler.
- Başvuru teminatı: itirazen şikâyette m.53/j-2'deki bedelin dört katına kadar teminat alınmasına Cumhurbaşkanınca karar verilebilir; ret hâlinde teminat gelir kaydedilir (4734 m.54). Yürürlükte böyle bir karar olup olmadığı doğrulanamadı; Tebliğ m.11/2 de teminatı yalnız "karar verilmesi durumunda" arar. Başvurudan önce `legal_search_official_gazette` ile ("başvuru teminatı" + "Kamu İhale", `category: "YÜRÜTME"`) ve KİK'in güncel başvuru bedeli duyurusundan kontrol et; karar bulunamazsa teminat yatırma, dilekçeye "yürürlükte teminat kararı tespit edilemedi" notunu düş.

---

## Görüşme soruları (eski `data_schema` alanlarından)

**Her iki dilekçe için:**
| Alan | Soru |
|---|---|
| `applicant_info.title` | Başvuru sahibinin (istekli/aday) tam unvanı ya da adı soyadı? Vekil var mı? |
| `applicant_info.address` | Tebligat adresi? (KEP adresi varsa onu da) |
| `applicant_info.tax_id` / `tc_kimlik` / `mersis_no` | Vergi kimlik no ya da TC kimlik no; tüzel kişide MERSİS no? |
| `tender_info.administration` / `administration_name` | İhaleyi yapan idarenin tam adı? |
| `tender_info.tender_name` | İşin adı (ilandaki gibi)? |
| `tender_info.ikn` | İKN? |
| (yeni) | İhale usulü: açık, belli istekliler arası, pazarlık 21/(b)-(c), 21/(diğer), doğrudan temin? (süreyi değiştirir) |
| (yeni) | İhale tarihi ve sözleşme imzalandı mı? (imzalandıysa başvuru yolu kapanmış olabilir) |
| `complaint_type` | Başvuru dokümana mı, değerlendirmeye/sonuca mı? |

**İdareye şikâyet:**
| Alan | Soru |
|---|---|
| `notification_date` | Aykırılığı ne zaman fark ettiniz ya da öğrendiniz? Belge nedir (kesinleşen ihale kararı bildirimi, EKAP indirme tarihi, ilan tarihi)? |
| `complaint_claims` | İddialarınız nelerdir? (her birini ayrı yazın; sonradan ekleme yapılamaz) |
| `legal_arguments` | (Araştırma adımında doldurulur — kullanıcıya sorma.) |
| `conclusion_request` | Talep: düzeltici işlem mi, ihalenin iptali mi? |

**KİK'e itirazen şikâyet:**
| Alan | Soru |
|---|---|
| `procedural_dates.ekap_download_date` | Doküman EKAP'tan ne zaman indirildi/satın alındı? |
| `procedural_dates.complaint_date` | İdareye şikâyet hangi tarihte, hangi kayıt numarasıyla yapıldı? (şikâyet dilekçesini isteyin) |
| `procedural_dates.response_date` | İdare kararı ne zaman bildirildi? Karar hiç gelmediyse şikâyetin kayda giriş tarihi? |
| `objection_claims` | Hangi iddialar? (yalnız şikâyette ileri sürülenler ve idare kararında belirlenen hususlar) |
| `payment_info` | Başvuru bedeli yatırıldı mı? Dekont tarihi ve tutarı? Yaklaşık maliyet? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4734" article_no: "54" | "55" | "56" | "57" | "53"
legal_get_statute_article law_no: "4734" article_no: "<şikâyet konusu madde: 5 temel ilkeler, 10 yeterlik, 12 teknik şartname, 38 aşırı düşük, 40 karar>"
legal_get_statute_article law_no: "12766" article_no: "8" # İhalelere Yönelik Başvurular Hakkında Yönetmelik, başvuru şekil unsurları
legal_search_official_gazette query: "İhalelere Yönelik Başvurular Hakkında Tebliğ" search_in: "title" sort_by: "date_desc"
legal_search_official_gazette query: "Kamu İhale Tebliği" search_in: "title" sort_by: "date_desc" # yıllık bedel güncellemesi
legal_search_cases mahkeme: "kik" sorgu: "<ör. benzer iş tanımına uymayan iş deneyim belgesi kabul edilemez>"
legal_search_cases mahkeme: "danistay" sorgu: "<…>" tarih_baslangic: "<son 3 yıl>" # ihale davaları bu turda 13. Daire kararlarında görüldü
legal_get_case_document belge_id: "<seçilen karar>"
legal_search_admin_guidance sorgu: "<konu>" belge_tur: "kurul_karar" # KİK düzenleyici/ilke kararları; kapsam dar olabilir
legal_check_holiday tarih: "<son gün>"
```
Ek kaynak: ES adları ve `bureaucrat/consultant.procurement_tender.legal_remedies_master` araştırma ajanı yoktur; karşılığı yukarıdaki çağrılardır. Danıştay'da 4734, 4735 ve 2886 sayılı Kanunlardan (ecrimisil ve tahliye hariç) ve bu Kanunlara tabi olmayan diğer kamu ihalelerinden doğan davalar ile temyiz başvuruları 2026'da da **Onüçüncü Daire**dedir (Danıştay Başkanlık Kurulu 2026/6, RG 25.02.2026, 33179).

---

## Dilekçe iskeleti — idareye şikâyet

```markdown
[İHALEYİ YAPAN İDARENİN ADI — büyük harf, ortalı]
[İHALE YETKİLİSİNE / ŞİKÂYET İNCELEME BİRİMİNE] [___]

BAŞVURU SAHİBİ : [unvan] — VKN/TCKN: [___] — MERSİS: [___]
ADRES / KEP : [___]
VEKİLİ : [varsa ad-soyad, baro sicil, adres]

İHALENİN ADI : [___]
İKN : [___]
İHALE USULÜ / TARİHİ: [___]

FARKINA VARMA / BİLDİRİM TARİHİ: [___] ([kaynak: kesinleşen ihale kararı bildirimi / EKAP indirme / ilan])

KONU: [İKN] sayılı ihalede [ihale dokümanına / tekliflerin değerlendirilmesine / ihale kararına] yönelik
      4734 sayılı Kanun'un 54 ve 55. maddeleri uyarınca şikâyet başvurusudur.

ŞİKÂYET KONUSU İDDİALAR:
1. [İddia 1 — tek husus]
2. [İddia 2 — tek husus]

AÇIKLAMALAR VE HUKUKİ GEREKÇELER:
[Her iddia için: olgu → ilgili doküman maddesi → mevzuat (4734, uygulama yönetmeliği, tebliğ) → KİK/Danıştay kararı → sonuç]

DELİLLER: [ihale dokümanı, EKAP çıktıları, teklif belgeleri, kesinleşen ihale kararı …]

SONUÇ VE İSTEM: Yukarıda açıklanan nedenlerle [düzeltici işlem belirlenmesine / ihalenin iptaline]
karar verilmesini saygılarımla arz ve talep ederim.

[Tarih] BAŞVURU SAHİBİ / VEKİLİ
                                                           [ad-soyad / unvan, imza]
EKLER: [vekâletname, imza sirküleri, belgeler]
```

## Dilekçe iskeleti — KİK'e itirazen şikâyet

```markdown
KAMU İHALE KURUMUNA
ANKARA

BAŞVURU SAHİBİ : [unvan] — VKN/TCKN: [___] — MERSİS: [___]
ADRES / KEP : [___]
VEKİLİ : [___]

İHALEYİ YAPAN İDARE: [___]
İHALENİN ADI : [___]
İKN : [___]

SÜREÇ BİLGİLERİ:
- Dokümanın EKAP'tan indirilme tarihi : [___]
- Farkına varma tarihi : [___]
- İdareye şikâyet tarihi / sayısı : [___]
- İdare kararının bildirim tarihi : [___] (karar alınmadıysa: "10 günlük karar süresi [___] tarihinde dolmuştur")

KONU: İdarenin [tarih/sayı] şikâyet kararının uygun bulunmaması üzerine 4734 sayılı Kanun'un 56. maddesi
      uyarınca itirazen şikâyet başvurusudur.

İTİRAZEN ŞİKÂYET KONUSU İDDİALAR (Tebliğ m.11/9 uyarınca ayrı ayrı):
1. [Şikâyette ileri sürülen iddia 1]
2. [Şikâyette ileri sürülen iddia 2]

AÇIKLAMALAR VE HUKUKİ GEREKÇELER:
[Her iddia: idarenin şikâyet kararındaki gerekçesi → neden hukuka aykırı → mevzuat → emsal Kurul / Danıştay kararı]

BAŞVURU BEDELİ: [tarih] tarihli [tutar — yıllık tebliğden] TL tutarındaki başvuru bedeli Kurum hesabına yatırılmış,
                dekontu ekte sunulmuştur.

SONUÇ VE İSTEM: İdarenin şikâyet kararının iptali ile [düzeltici işlem belirlenmesine / ihalenin iptaline]
karar verilmesini saygılarımla arz ve talep ederim.

[Tarih] BAŞVURU SAHİBİ / VEKİLİ
                                                           [ad-soyad / unvan, imza]
EKLER: [şikâyet dilekçesi sureti, idare kararı, bedel dekontu, vekâletname, imza sirküleri, belgeler]
```
Eski `ui_config` blok sırası (başlık → başvuru sahibi → ihale bilgileri → süreç tarihleri → iddialar → gerekçe → bedel → sonuç → imza) bu iskelete taşındı; eski "Tebliğ Ek-1 / Ek-2 formatı" atfı **kullanılmaz**: Tebliğ dilekçenin şekil unsurlarını Kanun m.54 ve Yönetmelik m.8'e gönderir (şikâyet: m.5; itirazen şikâyet: m.11 — asgari bilgiler, zorunlu ekler, içerik kuralları), madde metinlerinde ek dilekçe formuna atıf yok. Tebliğ ek m.1 (RG 1.4.2023 ile eklendi; yürürlük tarihini madde metninden kontrol et) başvuruların **EKAP üzerinden e-imzayla** yapılmasını zorunlu kılıyor; EKAP'taki e-başvuru ekranının alanlarını esas al.

---

## Sık hatalar

- 🔴 Süreyi tebliğden saymak; ölçüt **farkına varma** tarihidir. Dokümana yönelik şikâyette 3 iş günü sınırını kaçırmak.
- 🔴 Şikâyette yazılmayan iddiayı KİK aşamasında eklemek (şekil yönünden ret; Danıştay 13. D. E.2024/3176).
- 🔴 Doğrudan KİK'e başvurmak (iptal kararı istisnası dışında Kurum başvuruyu idareye gönderir, süre kaçabilir).
- 🟠 Başvuru bedelini kanun metnindeki taban tutardan yatırmak; güncel yıllık tebliği kullanmamak.
- 🟠 Birden fazla isteklinin aynı dilekçeyle başvurması ya da tek dilekçede birden fazla ihale.
- 🟠 İddiaları Tebliğ'deki "ayrı iddia / tek iddia" ayrımına uymadan yazmak (bedel iadesi kaybı).
- 🟡 Vekâletname ve imza sirkülerinin eklenmemesi; dilekçenin imzasız (e-imzasız) olması.

---
