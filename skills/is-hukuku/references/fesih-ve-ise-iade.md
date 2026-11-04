# Fesih, iş güvencesi ve işe iade

İşçi tarafında: fesih bildirimini incele, işe iade yolunun açık olup olmadığını ve sürelerini belirle.
İşveren tarafında: fesihten **önce** kontrol et ("bu işçiyi çıkarabilir miyiz?") ya da açılmış işe iade davasında savunma kur.

Temel ilke: fesih son çaredir (ultima ratio). İşletme gereklerine dayanan fesihte 9. HD, işletmesel kararın tutarlı uygulanıp uygulanmadığını, keyfîlik olup olmadığını ve feshin kaçınılmazlığını (ölçülülük — son çare ilkesi) denetler: işveren feshe oranla daha hafif tedbir ya da işçiye teklif edilebilecek başka iş bulunmadığını göstermelidir. Davranış nedenli fesihlerde de bölge adliye mahkemeleri ilkeyi uyguluyor (uyarı/kınama gibi hafif yollar denenmeden fesih); somut olaya göre güncel 9. HD kararını `legal_search_cases` ile çek. 

---

## Süre tablosu (önce bunu doldur)

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| İşe iade için arabulucuya başvuru: **1 ay** | Fesih bildiriminin **tebliği** | 4857 m.20/1  | Hak düşürücü. Kaçarsa işe iade yolu kapanır. Arabuluculuk süresince hak düşürücü süre işlemez (7036 m.3/17). |
| Anlaşamama tutanağından sonra dava: **2 hafta** | Son tutanağın düzenlendiği tarih | 4857 m.20/1  | Hak düşürücü. Taraflar anlaşırsa aynı sürede özel hakeme de gidilebilir. |
| Haklı nedenle derhal fesih: **6 iş günü / 1 yıl** | Fesih hakkı olan tarafın olayı öğrenmesi / olayın gerçekleşmesi | 4857 m.26 (m.25'te değil)  | Kaçarsa haklı nedenle fesih imkânı düşer. Sonuç feshin "geçersizliği" değil, **haksız fesih** sonuçlarıdır (kıdem ve ihbar doğar). Geçersizlik ve işe iade ayrı bir testtir (m.18-21). İki süre de hak düşürücüdür, re'sen gözetilir.  |
| Kesinleşen işe iade kararından sonra işe başlatma başvurusu: **10 iş günü** | Kesinleşmiş kararın tebliği | 4857 m.21  | İşçi başvurmazsa fesih geçerli sayılır. |
| İşverenin işe başlatma süresi: **1 ay** | İşçinin başvurusu | 4857 m.21/1  | Başlatmazsa işe başlatmama tazminatı + boşta geçen süre. |
| Arabuluculuk görüşme süresi | Arabulucunun görevlendirilmesi | 7036 m.3/10  | İlk toplantıya mazeretsiz katılmayan taraf davada haklı çıksa bile yargılama giderlerinin yarısından sorumlu olur, lehine vekâlet ücretinin yarısına hükmedilir (m.3/12, 7531 ile değişik).  |

`legal_calculate_deadline` işe iade sürelerini hesaplar (`labor_reinstatement_mediation`, `labor_reinstatement_lawsuit`, `labor_reinstatement_notification`); sonucu madde metniyle karşılaştır. Kodu olmayan süreleri elle hesapla, son günün resmî tatile denk gelip gelmediğini `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle.

**Her seferinde çek (atlanmaz):** tablodaki arabuluculuk satırlarını yazmadan önce `legal_get_statute_article` `law_no: "7036"` `article_no: "3"` çağır ve başvuru, görüşme süresi, uzatma ve son tutanak kurallarını bu metinden al. Tablodaki ifadeler yön gösterir; çıktıya giren süre araçtan gelen metindir.

---

## Kontrol listesi

### 1. İş güvencesinin ön şartları (biri yoksa işe iade açılamaz) 🔴
Hepsini `legal_get_statute_article(law_no: "4857", article_no: "18")` ile çek ve metne göre kontrol et.
- **Otuz işçi:** İşyerinde (işverenin aynı iş kolundaki tüm işyerleri birlikte) otuz veya daha fazla işçi var mı? 
- **Altı ay kıdem:** İşçinin kıdemi en az altı ay mı? Hesapta m.66 süreleri sayılır; aynı işverenin farklı işyerlerindeki süreler birleştirilir. Yer altı işlerinde kıdem şartı aranmaz (6552 ile eklendi). 
- **Belirsiz süreli sözleşme:** Belirli süreli sözleşmede işe iade yoktur; ancak zincirleme belirli süreli sözleşme belirsiz süreliye dönüşmüş olabilir (4857 m.11) `[incele]`.
- **İşveren vekili değil:** İşletmenin bütününü sevk ve idare eden işveren vekili ve yardımcıları ile işçi alma ve çıkarma yetkisi olan işveren vekilleri kapsam dışıdır (4857 m.18/son). `[incele]`
- Şartlar yoksa: işe iade yerine **kötüniyet tazminatı** (4857 m.17/6: iş güvencesi dışındaki işçiye fesih hakkının kötüye kullanılmasında bildirim süresinin üç katı; bildirim şartına da uyulmadıysa ayrıca ihbar tazminatı) ve TBK genel hükümler değerlendirilir. 

### 2. Fesih türü
- **Geçerli neden (m.18):** işçinin yeterliliği (performans), davranışı ya da işletme/işyeri/iş gerekleri. Kıdem ve ihbar tazminatı ödenir.
- **Haklı neden (m.25):** sağlık sebepleri (I), ahlak ve iyiniyet kurallarına uymayan haller (II), zorlayıcı sebepler (III), gözaltı/tutukluluk (IV). Bildirimsiz fesih olduğu için ihbar tazminatı ödenmez. Kıdem tazminatı **yalnız m.25/II** hallerinde ödenmez; I, III ve IV bentlerine dayanan fesihte en az 1 yıl kıdemi olan işçiye ödenir (1475 m.14/1-1: işveren feshi "17 nci maddenin II numaralı bendinde gösterilen sebepler dışında" — eski 1475 m.17/II'nin karşılığı 4857 m.25/II). 
- **Fesih bildirimi yazılı ve gerekçe açık ve kesin mi?** (4857 m.19/1) Gerekçesiz ya da belirsiz bildirim işveren için ciddi risktir. 🟠 
- **Bildirimin şekli:** fesih sonucu doğuran bildirimler her hâlde yazılıdır; diğer bildirimler imza karşılığı ya da işçinin yazılı kabulüyle KEP üzerinden yapılabilir; imzadan kaçınma tutanakla tespit edilir. Tebliğe bağlı sürelerin başlangıcı buna göre belirlenir. 
- Bildirimdeki neden ile davada ileri sürülen neden aynı mı? İşveren sonradan neden değiştiremez. 

### 3. Usul
- **Savunma alındı mı?** Savunma şartı yalnız **işçinin davranışı ya da verimi** ile ilgili nedenlere dayanan geçerli fesihte aranır (4857 m.19/2); işletme gereklerine dayanan fesihte bu şart yoktur. m.25/II şartlarına uygun haklı fesih hakkı saklıdır. Davranış/verim feshinde savunma alınmaması feshi geçersiz kılar. 🔴  Savunma için tanınacak sürenin ölçütü Kanunda yazmaz; somut dosyada güncel 9. HD kararlarını `legal_search_cases` (`daire: "9. Hukuk Dairesi"`, `sorgu: "savunma için süre verilmeden fesih geçersiz"`) ile ara, en az birinin tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: savunma süresi ölçütü]` yaz, gün sayısı uydurma. 
- Savunma için makul süre verildi mi, çağrı yazılı mı?
- Performans feshinde: objektif ölçüt, önceden bildirilmiş hedefler, karşılaştırma grubu, uyarı ve iyileştirme süresi var mı?
- İşletme gereklerine dayalı fesihte: işletme kararı, kararın tutarlı uygulanması, feshin kaçınılmazlığı, seçimde objektiflik (kıdem, sosyal durum) `[incele]`.
- **Toplu işçi çıkarma** eşiği aşılıyor mu? (4857 m.29 — en az 30 gün önceden yazılı bildirim; eşikler işyerindeki işçi sayısına göre üç kademe, bir aylık süre içinde 17. maddeye göre fesih; fesihler bölge müdürlüğüne bildirimden 30 gün sonra hüküm doğurur) 

### 4. Yasak fesih nedenleri (m.18/3) 🔴
Sendika üyeliği veya faaliyeti, işçi temsilciliği, işverene karşı şikâyet/dava, cinsiyet, medeni hal, aile yükümlülükleri, hamilelik, doğum, din, siyasi görüş, ırk, renk vb., doğum izni sırasında devamsızlık, hastalık/kaza nedeniyle geçici devamsızlık (m.25/I-b süresi içinde).  Bunlardan biri ileri sürülürse **6356 m.25 sendikal tazminat** ve **4857 m.5 ayrımcılık tazminatı** da değerlendirilir. 

### 5. Ultima ratio
- Fesihten önce daha hafif yollar (uyarı, başka iş, eğitim, çalışma koşulu değişikliği) denendi mi? `[incele]`

### 6. İşveren tarafı — ispat
- Feshin geçerli nedene dayandığını ispat yükü **işverendedir** (4857 m.20/2). Bu yük "tamamen" işverende değildir: işçi, feshin başka bir nedene dayandığını iddia ederse bunu ispatla yükümlüdür. 
- Belge izi: yazılı uyarılar, tutanaklar, performans değerlendirmeleri, savunma istem ve savunma metni, işletme kararı. "Neden şimdi?" sorusunun yazılı cevabı var mı?
- Fesihle çelişen belge var mı (yakın tarihli terfi, prim, olumlu değerlendirme)? 🟠

### 7. İşe iade kararının sonuçları
- **İşe başlatmama tazminatı:** işçinin başvurusuna rağmen 1 ay içinde işe başlatılmazsa en az 4, en çok 8 aylık ücret; miktarı mahkeme belirler. 
- **Boşta geçen süre ücreti:** kararın kesinleşmesine kadar en çok 4 aya kadar ücret ve diğer haklar. Her iki kalem dava tarihindeki ücret esas alınarak parasal olarak belirlenir. 
- İşçi işe başlatılırsa peşin ödenen ihbar ücreti ve kıdem tazminatı mahsup edilir.
- **Arabuluculukta anlaşma:** işe başlatma tarihi, boşta geçen süre ücreti ve işe başlatmama tazminatı tutanakta parasal olarak belirlenmezse anlaşma sağlanamamış sayılır; işçi kararlaştırılan tarihte işe başlamazsa fesih geçerli hâle gelir. 
- Tutarlar için ücret bilgisi + `legal_get_social_parameters` (asgari ücret alt sınırı kontrolü).

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4857"  article_no: "18" | "19" | "20" | "21" | "25" | "26" | "17" | "109"
legal_get_statute_article  law_no: "7036"  article_no: "3"
legal_get_statute_article  law_no: "6356"  article_no: "25"      # sendikal fesih iddiası varsa
legal_get_statute_article_history  (4857 m.20, m.21)              # 7036 öncesi/sonrası metin farkı
legal_search_cases  mahkeme: "yargitay"  daire: "9. Hukuk Dairesi"
    sorgu: "<olay cümlesi, ör. savunma alınmadan performans düşüklüğü gerekçesiyle fesih>"
    tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "bam"  sorgu: "<olay>"                   # İŞE İADEDE ÖNCE BU: istinaf kesin (4857 m.20/3)
legal_search_cases  mahkeme: "yargitay"  daire: "22. Hukuk Dairesi"  tarih_bitis: "2020-09-02"   # kapatılan daire, yalnız eski emsal
legal_search_cases  mahkeme: "yargitay"  daire: "Hukuk Genel Kurulu"  # direnme kararları
legal_get_social_parameters  tur: "asgari_ucret_brut"
legal_get_case_document  <son 3 yıldan seçilen en az bir kararın id'si>   # ZORUNLU: tam metni oku, alıntı-önerme kontrolü
```
Akış sırası: (1) 7036 m.3 ve 4857 m.20 metnini çek → süre tablosu; (2) BAM ve 9. HD'de son 3 yıl araması; (3) **en az bir son 3 yıl kararının tam metnini `legal_get_case_document` ile oku** ve neyi desteklediğini yaz; yalnız özetten alınan emsal `[çekildi ama desteği doğrulayın]` etiketi alır.
Eski ES profilinde `mevzuat_turu: içtihadı birleştirme kararı` yüksek öncelikliydi → `legal_search_cases` sorgusuna "içtihadı birleştirme" ekle ya da `legal_search_statute_semantic` kullan.

---

## Görüşme soruları (olgu toplama)

1. Kimin adına? (işçi / işveren)
2. İşe giriş tarihi, fesih bildiriminin tebliğ tarihi ve şekli (yazılı mı, nasıl tebliğ edildi)?
3. İşyerindeki ve işverenin aynı iş kolundaki toplam işçi sayısı?
4. Sözleşme belirsiz süreli mi? Yazılı sözleşme var mı?
5. İşçinin görevi ve yetkileri (işveren vekili mi)?
6. Bildirimde yazan fesih nedeni (aynen)?
7. Savunma istendi mi, ne zaman, ne kadar süre verildi, savunma verildi mi?
8. Uyarı, tutanak, performans kaydı var mı?
9. İşçi son dönemde şikâyet, dava, sendika üyeliği, hamilelik/doğum, rapor/hastalık bildirdi mi?
10. Aynı dönemde başka işçi çıkarıldı mı (kaç kişi)?
11. Arabulucuya başvuruldu mu, tarih, son tutanak tarihi?
12. Brüt ücret ve ek ödemeler (işe iade tazminatı hesabı için)?

## Çıktı iskeleti — fesih/işe iade değerlendirmesi

```markdown
## Fesih değerlendirmesi: [işçi/rol] — [tarih]
**Taraf:** [işçi/işveren] · **Fesih türü (bildirime göre):** [geçerli/haklı m.25/…] · **Tebliğ:** [tarih]

### Sonuç
[İşe iade yolu açık / kapalı (neden) / süre kaçmış — ya da işveren için: devam edilebilir / önce X düzeltilmeli / dur]

### Kritik süreler
| Süre | Başlangıç | Son gün | Dayanak | Durum |

### Ön şartlar
| Şart | Durum | Not |

### Bulgular
- Fesih nedeni ve gerekçe: …
- Savunma: …
- Yasak fesih nedeni işareti: …
- Ultima ratio: …
- Belge izi: …

### Olası sonuçlar ve tutarlar
[iş güvencesi tazminatı aralığı, boşta geçen süre, kıdem/ihbar — formül + [doğrula]]

### Emsal kararlar
### Eksik bilgi
```

## Çıktı iskeleti — işe iade için arabuluculuk başvurusu / dava dilekçesi taslağı
**Önce devir:** arabuluculuk başvurusu ve dava dilekçesi `hukuk-yargilamasi-dilekce` becerisinde (`../../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md`, `../../hukuk-yargilamasi-dilekce/references/dava-dilekcesi.md`), işe iade kararına istinaf `kanun-yollari-dilekce` becerisinde kurulur. Aşağıdaki iskelet yalnız o beceriler yüklü değilse kullanılır.
Eski YAML'da `ui_config` yoktu; aşağıdaki iskelet HMK m.119 unsurlarına göre yazıldı. 
- Arabuluculuk bürosuna başvuru: başvurucu, karşı taraf (işveren unvanı, adresi), uyuşmazlık konusu (feshin geçersizliği ve işe iade, boşta geçen süre, işe başlatmama tazminatı), fesih tarihi, iletişim.
- Dava dilekçesi: mahkeme (iş mahkemesi; yoksa iş mahkemesi sıfatıyla asliye hukuk), taraflar, vekil, dava konusu, arabuluculuk son tutanağı (dava şartı — eklenmeli), açıklamalar (olay sırası), hukuki sebepler, deliller, sonuç ve istem (feshin geçersizliği, işe iade, 4-8 ay tazminat, 4 aya kadar boşta geçen süre ücreti).
- Yetkili mahkeme: davalının yerleşim yeri ya da işin yapıldığı yer (7036 m.6/1); davalı birden çoksa birinin yerleşim yeri de yetkili; aykırı yetki sözleşmesi geçersiz (m.6/5). 

---

