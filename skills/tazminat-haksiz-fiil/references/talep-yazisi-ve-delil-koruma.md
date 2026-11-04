<!--
Bu dosyadaki iş akışı anthropics/claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC) deposundaki
litigation-legal/skills/demand-intake, demand-received, demand-draft, legal-hold ve chronology becerilerinden
uyarlanmış ve Türk hukukuna göre değiştirilmiştir. Ayrıntı: NOTICE.md.
-->

# Talep yazısı, gelen talep ve delil koruma

## Ne zaman kullanılır
- **Talep göndermeden önce** (zarar gören tarafı): sigortacıya KTK m.97 başvurusu, Sigorta Tahkim'e gitmeden önceki başvuru, sorumluya ihtar/talep yazısı, satıcıya 7223 m.11/3 bilgi talebi, idareye İYUK m.13 başvurusu. Amaç: yazmadan önce **duruş, kaldıraç, ikrar riski ve ibra tuzağı** sorularını sormak.
- **Talep geldiğinde** (sorumlu, işveren, sigortacı tarafı): karşı taraftan gelen tazminat talebini/ihtarnameyi sınıflamak ve cevap seçeneklerini sunmak.
- **Delil kaybolmadan:** kamera kayıtları, hasta dosyası, ürünün kendisi, araç hasarı, sosyal medya içeriği.
- **Kronoloji:** olaydan bugüne tarih çizelgesi; zamanaşımı ve faiz başlangıcı için.

Metin yazımı (noter ihtarnamesi, delil tespiti, ihtiyati tedbir) `hukuk-yargilamasi-dilekce` becerisine devredilir; bu dosya içeriği ve kapıları belirler.

---

## A. Talep göndermeden önce — görüşme

### Duruş (önce sor, varsayılan koyma)
1. **Ton:** ölçülü / kararlı / sert? İlişki sürecek mi (komşu, iş ortağı, hastane)?
2. **Cevap süresi:** kanuni süre varsa onu yaz (KTK m.97: 15 gün; 5684 m.30/13: 15 iş günü; 7223 m.11/3: 10 iş günü; İYUK m.13: 30 gün). Kanuni süre yoksa makul süre öner ve `[incele]`. 
3. **Gönderim yolu:** noter, KEP, iadeli taahhütlü, sigortacının başvuru kanalı (e-posta/portal) — **ispat edilebilir** ve tarihli olmalı.
4. **İmza:** avukat mı, zarar gören mi?

### Çekirdek sorular
1. Talebin türü: ödeme / bilgi / delil koruma / sulh teklifi?
2. Taraflar: gönderen, alıcı (sigortacı unvanı, poliçe no; işleten; hastane tüzel kişiliği; idare).
3. Olay ve tarih (kronoloji, bkz. D).
4. Hukuki dayanak (madde ve sözleşme; kesin değilse `[atıf: ___]` bırak).
5. **İstem:** somut ve kalem kalem (ör. "değer kaybı … TL, ekspertiz ücreti … TL"). Belirsizse "fazlaya ilişkin haklar saklı" kaydı.
6. Ekler: tutanak, rapor, fatura, kimlik/ruhsat, IBAN, vekâletname, maluliyet raporu, veraset ilamı.
7. Önceki temaslar ve cevaplar.
8. Kime bilgi verilecek (kendi kasko/sağlık sigortası, işveren)?

### Stratejik sorular (tutar yüksekse, ölüm/ağır yaralanma varsa ya da karşı taraf tekrar eden bir aktörse)
9. **Kaldıraç ve alternatif:** cevap gelmezse dava mı, tahkim mi? (Bkz. `trafik-kazasi-ve-zmss.md` usul yolu.)
10. **İkrar riski (sorumlu tarafın yazısında):** "kusurumuz yoktur ama iyi niyet göstergesi olarak …" gibi cümleler ikrar sayılabilir ve zamanaşımını keser (TBK m.154/1). 
11. **Kendi aleyhine bilgi:** yazıda kendi kusurunuzu, belirsiz olguları, iç değerlendirmeyi yazmayın; olguyu doğrulanmış olanla sınırlayın.
12. **Sulh/uzlaşma niteliği:** teklif içeren yazıda "sulh amacıyla, ikrar niteliğinde değildir" kaydı. Türk hukukunda ABD FRE 408 benzeri genel bir delil yasağı yoktur; kayıt koruma değil, niyet beyanıdır `[incele]`.

Kullanıcı stratejik soruları atlarsa yazının ilgili kısımlarına `[incele: duruş/ikrar riski konuşulmadı]` işareti koy.

### Gönderim öncesi kapı (geçmeden yazma)
```
1. Olgular doğrulandı mı? Doğrulanmayan her olgu [doğrula: ___] ile işaretli mi?
2. Alıntılar birebir mi? Belgeden alıntı yoksa tırnak kullanma; "[tarih] tarihli yazınızda … belirtilmiştir [alıntıyı doğrula]".
3. Atıf tam önermeyi destekliyor mu? (madde hem yükümlülüğü hem süreyi içeriyor mu?)
4. İkrar ve kendi aleyhine bilgi taraması yapıldı mı?
5. Zayıf kalemler: ileri sürülecek mi, çıkarılacak mı, ihtiyati mi? [incele]
6. Süre: zamanaşımı ve kanuni bekleme süreleri hesaplandı mı?
7. Avukat olmayan kullanıcı: "Bunu bir avukatla gözden geçirdiniz mi?" (ORTAK-KURALLAR.md §1)
```
Her maddeye kullanıcıdan açık cevap al; boş geçilen kapı, hiç kapı olmamasından kötüdür.

### KTK m.97 başvurusunun asgari içeriği (iskelet)
```markdown
[SİGORTA ŞİRKETİ UNVANI] — Hasar/Tazminat Birimi
KONU: 2918 s. KTK m.97 uyarınca yazılı başvuru — [plaka], poliçe no [___]
Başvuran: [ad, T.C. kimlik no, adres, IBAN] / Vekil: [___]
Kaza: [tarih, yer, araçlar, tutanak no]
Zarar kalemleri: [araç hasarı / değer kaybı / sürekli iş göremezlik / destekten yoksun kalma / bakıcı / diğer] — tutar ya da "hesaplanacak"
Ekler: [tutanak, ekspertiz, fotoğraflar, ruhsat, ehliyet, maluliyet raporu, gelir belgesi, veraset ilamı, nüfus kaydı]
İstem: [tutar] tazminatın [faiz başlangıcı] faiziyle ödenmesi; 15 gün içinde yazılı cevap.
Tarih / imza
```
Başvuru tarihini ve teslim kanıtını süre tablosuna yaz; dava/tahkim takvimi buna bağlıdır. Genel Şartlar'ın istediği belge listesi poliçe ve tarife düzenlemesinden kontrol edilmeli `[doğrula]` (KTK m.99/1 "genel şartlarla belirlenen belgeler"). 

### Sigorta Tahkim Komisyonu başvurusu (iskelet)
Ne zaman: sigortacıya başvuru yapılmış ve talep kısmen/tamamen reddedilmiş ya da **15 iş günü** içinde yazılı cevap gelmemiş; uyuşmazlık mahkemeye ya da tüketici hakem heyetine taşınmamış (5684 m.30/13-14). Trafik sigortası zorunlu sigorta olduğu için sigortacı sisteme üye olmasa da başvurulabilir (m.30/1). Dava mı tahkim mi seçimi `trafik-kazasi-ve-zmss.md` "Usul yolu"nda.

**Dosyanın kendisi kritiktir:** hakemler **yalnız kendilerine verilen evrak üzerinden** karar verir (m.30/15). Duruşma ve sonradan delil sunma imkânı sınırlı olduğu için bütün belgeler başvuruyla birlikte verilir; değer kaybı, pert ve bedensel zararda bilirkişi incelemesi isteniyorsa açıkça yazılır. 

```markdown
SİGORTA TAHKİM KOMİSYONU'NA
BAŞVURU SAHİBİ : [ad soyad / unvan, T.C. kimlik / vergi no, adres, telefon, e-posta, IBAN] — Vekil: [___]
SİGORTA KURULUŞU: [unvan] — Poliçe türü: [ZMSS / kasko / İMM] — Poliçe no: [___], başlangıç: [___]
OLAY            : [kaza tarihi, yer, araçlar ve plakalar, tutanak türü ve no]
SİGORTACIYA BAŞVURU: [tarih, yol (KEP / iadeli taahhütlü), teslim kanıtı] — CEVAP: [tarih ve özeti / 15 iş günü içinde cevap yok]
UYUŞMAZLIK KONUSU VE TALEP:
 1. [Araç hasarı / değer kaybı / pert farkı / sürekli iş göremezlik / destekten yoksun kalma] — [tutar] TL
    [belirlenemiyorsa: "bilirkişi incelemesiyle belirlenecek tutar; şimdilik ___ TL"]
 2. Faiz: [tür ve başlangıç — başvuru ve KTK m.99 süresine göre] [incele]
 3. Yargılama giderleri ve vekâlet ücreti
AÇIKLAMALAR     : [olay, kusur dağılımı ve kaynağı, zarar kalemlerinin yöntemi — alan değerlendirmesinden]
DELİLLER        : [tutanak, fotoğraflar, ekspertiz, onarım faturası, TRAMER kaydı, emsal ilanlar, sağlık kurulu raporu,
                   gelir belgeleri, veraset ilamı, nüfus kaydı, sigortacıyla yazışmalar, başvuru ücreti dekontu]
                   Bilirkişi incelemesi talebi: [değer kaybı / aktüerya / kusur]
Tarih / imza
```
- **Başvuru ücreti, parasal eşikler ve form:** başvuru ücreti, hakem heyeti eşiği, itiraz ve temyiz eşikleri Müsteşarlıkça (ÜFE oranında) güncellenir (m.30/12, 18, 22); tutarları beceriye yazma, başvuru günündeki değeri Komisyon duyurusundan ya da yönetmelikten al `[doğrula]`. Başvuru esasları yönetmelikle belirlenir (m.30/21).
- **Vekâlet ücreti:** `legal_calculate_attorney_fee` (`yargi_yeri: sigorta_tahkim`) iki sonuç verir: AAÜT m.17/2 ve 5684 m.30/17 lafzına göre (beşte bir yalnız talebi reddedilen aleyhine) ve İtiraz Hakem Heyeti uygulamasına göre (nisbi → beşte bir → maktunun altındaysa maktu, iki tarafa da). Hangisinin doğru olduğu Yargıtay'ca gerekçeli olarak söylenmedi; talepte ya da itirazda ikisini ve farkı göster, tek tutarı kesin diye sunma. 
- **Kararın ardından:** hakem kararına bildirimden itibaren **on gün** içinde bir defa itiraz (itiraz için başvuru ücreti yatırılır; itiraz icrayı durdurur); eşik altındaki kararlar kesindir; usul hatalarında temyiz her hâlde açık (m.30/12) → `kanun-yollari-dilekce`. Hakemin reddi öğrenmeden itibaren **beş iş günü** içinde (m.30/15). Reddedilen aleyhine vekâlet ücreti tarifenin beşte biri (m.30/17); hesap `legal_calculate_attorney_fee` (`yargi_yeri: "sigorta_tahkim"`). 

---

## B. Talep geldiğinde — sınıflama (sorumlu ya da sigortacı tarafı)

1. **Oku ve çıkar:** gönderen, vekil, alıcı, gönderim yolu ve **tebliğ tarihi**, talep türü, istenen tutar ve süre, ileri sürülen olgular, dayanaklar, tehdit edilen adım (dava, tahkim, ceza şikâyeti).
2. **Dosya taraması:** aynı olay ya da aynı karşı tarafla açık/kapalı dosya var mı (profilde dosya alanı açıksa)?
3. **Esas değerlendirmesi** (görüş değil, yönlendirme için): olgular bizim bildiğimizle uyuşuyor mu; dayanak uygulanabilir mi; karşı tarafın davası ne kadar güçlü; savunmalarımız (zamanaşımı, illiyet, müterafik kusur, kurtuluş kanıtı, ZMSS teminat dışı hâller); istenen tutar makul mü? **Derece:** güçlü / tartışmalı / zayıf / dayanaksız — `[incele]`.
4. **Seçenekler** (birini öner, gerekçesiyle):
   - **A. Esastan cevap** — talep tartışmalı ya da güçlüyse; kayda geçer.
   - **B. Ara cevap** — inceleme için zaman; kabul ya da ret içermez. Kanuni cevap süresi varsa (KTK m.97 15 gün) ara cevap süreyi durdurmaz 🟠.
   - **C. Sulh teklifi** — ikrar içermeyecek biçimde; KTK m.111 gereği açıkça yetersiz tutardaki anlaşma iki yıl içinde iptal edilebilir, bu yüzden "düşük teklif + tam ibra" stratejisinin sınırını yaz. 
   - **D. Cevap vermeme + delil koruma** — dayanaksız talep; ama sessizliğin aleyhe yorumlanabileceği ve sigortacı için m.97 süresi sonrası dava/tahkim yolunun açıldığı unutulmamalı.
5. **Süreler:** karşı tarafın verdiği süre bağlamaz; kanuni süreler bağlar. İç karar tarihi = kanuni son gün − hazırlık/onay süresi.
6. **Sigortaya bildirim:** sorumluluk sigortası (mesleki, işyeri, ZMSS, ihtiyari) varsa sigortacıya **gecikmeden ihbar** — poliçedeki ihbar yükümlülüğü ihlali teminatı etkileyebilir `[incele]`.

---

## C. Ödeme, ibra ve makbuz tuzakları (iki taraf için)
- Sigortacı ya da sorumlu, ödeme karşılığında "**tüm haklarımdan feragat ederek tam ve kesin ibra ederim**" yazılı belge imzalatabilir. Zarar görene: imzadan önce tutarın gerçek zararı karşılayıp karşılamadığını (`bedensel-zarar-ve-destek-hesabi.md`) ve **ihtirazi kayıt** konulabileceğini anlat; KTK kapsamındaki anlaşmalarda m.111 koruması var. Avukat olmayan kullanıcı için §1 kapısı zorunlu. 
- 31.07.2026 sonrası olaylarda, tahkikat başlamadan yapılan ödeme **oransal mahsup** edilir (TBK m.55/4); ödeme tarihini ve tutarını kaydet. 
- Kısmi ödeme borcun ikrarıdır, zamanaşımını keser (TBK m.154/1).

---

## D. Delil koruma (upstream legal-hold'un Türk hukuku karşılığı)
ABD'deki "legal hold" kurumu yoktur; karşılığı, delilin kendi elimizde korunması ve kaybolma riski olan delil için **mahkeme yoluyla tespit** ya da kuruma yazılı saklama talebidir.

| Delil | Kaybolma riski | Önerilen adım |
|---|---|---|
| Şehir/işyeri/araç kamerası | Kısa sürede üzerine kayıt | Kolluk ve savcılığa derhal saklama talebi; gerekirse delil tespiti → `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`; ceza dosyasında → `../../ceza-ve-infaz-dilekce/references/durusma-ici-talepler.md` |
| Hasta dosyası, görüntüleme, laboratuvar kayıtları | Değiştirilme/eksiklik iddiası | Hastaneden yazılı tam dosya talebi (tarih kanıtlı); gerekirse delil tespiti |
| Hasarlı araç | Onarım/satış | Onarımdan önce ekspertiz ve fotoğraf; değer kaybı için onarım faturaları |
| Ürün (patlayan cihaz vb.) | Servise verme, atma | Ürünü olduğu gibi sakla; servise verme; bağımsız uzman |
| Sosyal medya içeriği | Silinme | Tarihli ekran görüntüsü + URL; noter ya da güvenilir zaman damgası `[incele]` |
| Tanık | Unutma, ulaşılamama | İletişim bilgisi ve kısa yazılı anlatım (tarihli) |

Kendi müvekkilimiz (sorumlu taraf, işletme, hastane) için: ilgili kayıtların (kamera, bakım kayıtları, nöbet çizelgesi, hasta dosyası, yazışmalar) **silinmemesi** için iç talimat ver; delilin yok edilmesi hem ispat hem ceza sorumluluğu bakımından ağır risktir 🔴 `[incele]`.

---

## E. Kronoloji
Olaydan bugüne tek tablo. Her satırda kaynak belge; kaynaksız satır `[doğrula]`.

| Tarih | Olay | Kaynak | Hukuki önemi |
|---|---|---|---|
| | Fiil / kaza / müdahale | | Zamanaşımı (10 yıl), temerrüt, TBK m.55 eski/yeni |
| | Zararın ve sorumlunun öğrenilmesi | | Zamanaşımı (2/3 yıl) |
| | Sigortaya/satıcıya/idareye başvuru | | KTK m.97 / 7223 m.11 / İYUK m.13 |
| | Cevap ya da cevapsızlık | | Dava/tahkim yolu açılır |
| | Ödeme / ikrar | | Zamanaşımı kesilir; mahsup |
| | Ceza soruşturması, iddianame, karar | | Uzamış zamanaşımı |
| | Rapor tarihleri (maluliyet, kusur, ATK) | | Hesap dönemi |

Boşlukları ("bu tarih ile şu tarih arasında ne oldu?") ayrıca listele.

---

## Görüşme soruları
Yukarıdaki A ve B bölümlerindeki sorular; ayrıca:
1. Karşı tarafla yazılı/sözlü temas oldu mu; ne söylendi?
2. Herhangi bir belge imzaladınız mı (ibra, makbuz, tutanak)?
3. Hangi deliller elinizde, hangileri başkasında?

## soorgla çağrıları
```
legal_get_statute_article  law_no: "2918"  article_no: "97" | "99" | "111"
legal_get_statute_article  law_no: "5684"  article_no: "30"
legal_get_statute_article  law_no: "6098"  article_no: "154" | "117"
legal_list_statute_articles  law_no: "7223"  article_no: "11"  include_content: true
legal_check_holiday  tarih: "<son gün>"
legal_search_cases  mahkeme: "yargitay"  sorgu: "<ör. sigorta şirketine verilen ibranamenin geçerliliği KTK 111 yetersiz ödeme>"
```

## Çıktı iskeleti
```markdown
## Talep [gönderme | sınıflama] — [olay] — [tarih]
### Duruş (ton, süre, yol, imza)
### Kronoloji
### İstem / gelen talebin özeti
### Gönderim öncesi kapı (7 madde, her biri cevaplı)
### Seçenekler ve öneri (gelen talepte)
### Delil koruma adımları
### Süreler
### Açık sorular
```

## Sık hatalar
- KTK m.97 başvurusunu ispat edilemeyen kanaldan yapmak.
- Karşı tarafın verdiği süreyi kanuni süre sanmak.
- Sorumlu tarafın yazısında ikrar niteliğinde cümle kurmak.
- Ödeme belgesindeki ibrayı incelemeden imzalatmak/imzalamak.
- Delil tespiti için geç kalmak (kamera kayıtları).

