# Kaza tutanağından kusur notu

## Ne zaman kullanılır
Kaza tespit tutanağı, kroki, olay yeri fotoğrafı ya da kamera kaydı geldi ve soru "kim kusurlu", "kusur oranım ne olur", "tutanağa itiraz edebilir miyim". Ayrıca: sigortacı ya da Sigorta Tahkim hakem heyeti kusuru yalnız tutanağa dayanarak belirlemiş; ceza dosyasındaki kusur raporu hukuk dosyasına gelmiş.

**Çıktı kusur oranı değildir.** Çıktı: kaynaklı olay sırası, **en az iki kusur senaryosu**, bilirkişiye sorulacak sorular ve eksik delil listesi. Kusur oranını bilirkişi belirler.

**Kullanılmaz:** kusur oranı belli, yalnız hesap gerekiyor → `trafik-kazasi-ve-zmss.md` ve `bedensel-zarar-ve-destek-hesabi.md`. Kusur **raporu** geldiyse raporun denetimi → `bilirkisi-raporu-denetimi.md` §4.3 (bu dosyanın §4-§6'sını kullanır).

**Yasak ifadeler:** "kusur oranınız %X", "karşı taraf %100 kusurlu", "dava kesin kazanılır". Avukat olmayan kullanıcıya: "Kusur oranını bilirkişi belirler; bu not, bilirkişiden neyi sormanız gerektiğini gösterir." Gerekiyorsa baro adli yardım hatırlatması.

---

## 1. Girdiler ve değeri

| Girdi | Düzenleyen | Dayanak | Değeri ve sınırı |
|---|---|---|---|
| **Kolluk kaza tespit tutanağı** | Trafik zabıtası ya da genel kolluk | Yön. m.156/a | Kaza yeri, iz ve deliller, sürücüler, hasar, saat, kroki. **Görevliler kusur oranı yazmaz**; yalnız kimin hangi kuralı ihlal ettiğini yazar (m.156/a-3). Tutanaktaki "asli kusurlu" ifadesi oran değildir. |
| **Anlaşmalı tutanak** (Maddi Hasarlı Trafik Kazası Tespit Tutanağı) | Sürücüler birlikte | KTK m.81; Yön. m.152 | Yalnız maddi hasarlı kazada. Bu yolla ayrılan taraflar sonradan kolluktan tutanak isteyemez (m.152/c). Tek taraflı kaza, belgesiz sürücü, ZMSS'siz araç, alkol şüphesi, kamu aracı ya da kamu malına zarar varsa kolluk düzenler (m.152/ç). |
| **Kroki** | Tutanağın parçası | Yön. m.156/a | Çarpışma sonrası konum, fren izi, şerit, işaret. Ölçüsüz el çizimiyse `[ölçü yok]`. |
| **Olay yeri fotoğrafı** | Taraflar / kolluk | Yön. m.152/b | Hasar bölgesi, çarpışma noktası, yol durumu. Araçlar çekildikten sonra çekilen fotoğraf ayrıca işaretlenir. |
| **Kamera kaydı** (MOBESE, işyeri, araç içi) | Üçüncü kişi / taraf | — | En güçlü olgusal delil; kısa sürede silinir → `talep-yazisi-ve-delil-koruma.md`, delil tespiti `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`. |
| **Tanık** | — | Yön. m.157/b | Tanık beyanları kusur tespitinde dikkate alınır. Tutanakta adı yazılı tanık ile sonradan bulunan tanık ayrılır. |
| **Ceza dosyası** | Savcılık bilirkişisi, ATK, üniversite | TBK m.74 | Kusur değerlendirmesi hukuk hâkimini bağlamaz; **kesinleşmiş maddi vakıa bağlar** (§5). Dosya mutlaka istenir. |
| **Sigorta araştırma raporu** | Sigortacı | — | Kurgu kaza iddiasının ana delili (§5). |

**Okunan satırı zorunlu** (ORTAK-KURALLAR.md §10). Kroki ya da fotoğrafta okunamayan ölçü, plaka ve yön oku **tahmin edilmez**, `[okunamadı]` yazılır.

---

## 2. Olay sırasını çıkar
1. **Sabitler:** tarih, saat, hava, gün ışığı / gece, yol türü (yerleşim içi / dışı, bölünmüş, şerit sayısı), kavşak tipi (ışıklı, işaretli, işaretsiz), hız sınırı levhası, kaplama.
2. **Aktörler:** her araç için plaka, tür, sürücü, yön, şerit, hız (beyan edilen ve iz/hasardan çıkan **ayrı**), ehliyet ve alkol. Yaya, bisikletli, motosikletli ayrıca.
3. **Zaman çizgisi:** önce – çarpışma anı – sonra; her cümlenin yanında kaynağı (`[tutanak s.1]`, `[kroki]`, `[A beyanı]`, `[kamera 00:12]`).
4. **Çarpışma noktası ve açısı:** hasar bölgeleri, kroki konumu ve fren izi birlikte okunur.
5. **Çelişki taraması** (§4).
6. **Kural eşlemesi** (§3): her aktörün olası ihlali, maddesiyle. Madde metni o an `legal_get_statute_article law_no: "2918"` ile çekilir; çekilemeyen `[model bilgisi — doğrulayın]`.
7. **Senaryolar** (§6): delillerin farklı okunuşuna göre en az iki senaryo; her birinde destekleyen ve çürüten deliller.

---

## 3. Kural eşlemesi: KTK m.84 ve Yönetmelik m.157

KTK m.84 on iki hâli sayar ve bu hâllerde sürücüyü **asli kusurlu** sayar; Yönetmelik m.157/a aynı listeyi tekrarlar.

- **Oran tablosu yok.** Hareket birden fazla sürücüce yapılmışsa ya da kaza bu hâller dışındaki ihlallerden doğmuşsa oran yönetmelik esaslarına göre belirlenir (m.84 son fıkra); Yönetmelik m.157/b oran vermez, yalnız kurallar, iz-deliller, ifadeler ve tanık beyanlarının dikkate alınacağını söyler. Oran uygulamada bilirkişinin takdiridir.
- **Zorunluluk istisnası** (Yön. m.157/a son paragraf): başkasının kural dışı hareketi ya da teknik arıza sürücüyü tehlikeye düşürmüş, sürücü kazayı önlemek için temel kurallardan birini ihlale mecbur kalmış ve bütün tedbirlere rağmen kazaya yol açmışsa **asli kusurlu sayılamaz**. "Arkadan çarpma" gibi otomatik asli kusur hâllerine karşı ana savunma.

| m.84 | Hâl | Sorulacak / istenecek delil |
|---|---|---|
| a | Kırmızı ışıkta ya da memurun dur işaretinde geçme | Sinyal faz kaydı, kavşak kamerası, tanık; ışık arızası |
| b | Taşıt giremez yola / bölünmüş yolda ters yöne girme | Levha fotoğrafı ve görünürlüğü, yol geometrisi |
| c | İkiden fazla şeritli yolda karşı yön şeridine girme | Çarpışma noktasının şeritteki yeri, kroki ölçüsü, sürtünme izi |
| d | **Arkadan çarpma** | Öndeki araç ani / nedensiz fren yaptı mı, önüne kırdı mı, stop lambası çalışıyor muydu; zorunluluk istisnası; takip mesafesi (§7) |
| e | Geçme yasağı olan yerde geçme | Devamlı çizgi, levha, viraj / tepe, görüş mesafesi |
| f | Doğrultu değiştirmeyi yanlış yapma | Sinyal, hasar açısı (yan sürtme) |
| g | Şeride tecavüz | Çarpışma noktası, şerit çizgisi, yol genişliği |
| h | Kavşakta geçiş önceliğine uymama | Kavşak tipi, "Dur" / "Yol ver" levhası, kavşağa önce giren araç, hasar bölgesi |
| i | Dar kaplamada geçiş önceliğine uymama | Yol genişliği ölçüsü, levha |
| j | Manevra genel şartlarına uymama | Manevra türü, görüş, uyarı |
| k | Yerleşim dışında zorunluluk dışı park / duraklama, tedbir almama | Gece / gündüz, ışık ve reflektör, arıza belgesi |
| l | Kurallara uygun park edilmiş araca çarpma | Parkın kurallara uygunluğu |

Tutanakta sık geçen diğer maddeler (m.84 dışı; oran bilirkişinin takdiri): trafiği tehlikeye sokacak şerit değiştirme (m.46/2-c), hızı koşullara uydurmama (m.52/1-b), güvenli takip mesafesi (m.56/1-c), kavşakta geçiş önceliği (m.57), yayanın geçit dışından geçmesi ya da taşıt yolunda trafiği tehlikeye düşürmesi (m.68/1-b, c), yaya ve okul geçidinde yayaya ilk geçiş hakkı (m.74; 2018'den beri bentsiz tek fıkra). Bu maddelerin metnini **her seferinde çek**: m.46, 56 ve 57 7574 ile (yürürlük 27.02.2026) değişti; kaza tarihindeki metni kullan.

---

## 4. Tutanak – kroki – fotoğraf çelişki listesi
- [ ] Kroki konumları anlatımla uyumlu mu (ör. "arkadan çarptı" deniyor, hasar yan tarafta).
- [ ] İki aracın hasar bölgeleri birbirini tamamlıyor mu (yükseklik, açı)? Uyumsuzsa "kaza–hasar uyumu" sorusu (§5).
- [ ] Fren izi var mı, ölçülmüş mü? Ölçü varsa §7.
- [ ] Saat, hava, ışık koşulu tutanağın her yerinde aynı mı.
- [ ] Sürücü kimliği tutarlı mı; sonradan "aracı ben kullanıyordum" diyen var mı.
- [ ] Anlaşmalı tutanakta iki sürücünün el yazısı / imzası aynı elden çıkmış gibi mi; kroki başka kazalardaki krokilerle aynı mı.
- [ ] Fotoğraflar kaza yerinde mi, araçlar çekildikten sonra mı.
- [ ] Tutanaktaki ihlal maddesi anlatılan oluşla örtüşüyor mu (madde metni çekilip karşılaştırılır).
- [ ] Ceza dosyasındaki rapor, tutanak ve hakem / mahkeme raporu arasında fark var mı → çelişki giderilmeden hüküm kurulamaz (§5).
- [ ] Tutanakta kusur **oranı** yazılmış mı? Yazılmışsa Yön. m.156/a-3'e aykırı; oranın delil değeri yok, itiraz noktası olarak not et.

---

## 5. İçtihat çerçevesi

| İlke | Karar | Kaynak durumu |
|---|---|---|
| **Kusur oranı uzmanlık işidir**; tutanağa dayanıp rapor almadan karar verilemez | 4. HD E.2022/13579 K.2024/11578 (25.11.2024): hakem heyeti rapor almadan tutanağa göre tam kusur kabul etmiş; ceza dosyası getirtilip uzman bilirkişiden denetime elverişli, gerekçeli rapor alınması için bozma | |
| **Ceza hâkiminin kusur değerlendirmesi bağlamaz; kesinleşmiş maddi vakıa bağlar** | TBK m.74. 4. HD E.2023/13290 K.2025/8068 (20.05.2025): kesinleşmiş mahkûmiyet varken sürücüyü kusursuz sayan karar bozuldu | |
| Savcılık aşamasındaki kusur raporu bağlamaz | TBK m.74. **4. HD E.2025/7360 K.2025/12662'yi dayanak gösterme:** cümle yalnız karşı oyda, çoğunluk savcılık raporuyla yetinen hakem kararını onadı. Karşı taraf bu kararı "savcılık raporu yeterli" diye kullanabilir; itirazda yeniden rapor ihtiyacını somut çelişkiyle gerekçelendir. | |
| **Çelişkili kusur raporları:** tercih gerekçelendirilmeli ya da çelişkiyi gideren üçüncü rapor alınmalı | 4. HD E.2023/3943 K.2025/4851 (24.03.2025): ceza dosyasındaki ATK raporu iki sürücüyü de asli kusurlu bulmuş, tahkim raporu farklı oran vermiş; üçüncü rapor için bozma | |
| Uzman kurum seçenekleri | ATK, İTÜ, Karayolları Genel Müdürlüğü Trafik Fen Heyeti (4. HD E.2024/3390 K.2024/4176: raporlar çelişince uzman kuruldan denetime açık rapor için bozma) | |
| **Tutanağın ispat gücü — dikkat** | 4. HD E.2022/997 K.2023/7021 (25.05.2023): çoğunluk, tutanak ve fotoğraflarla kazanın varlığını sabit saydı, hasar miktarı için rapor istedi. "Tutanak aksi ispat edilinceye kadar geçerli resmî belgedir" cümlesi **karşı oydadır**; çoğunluk gerekçesi gibi alıntılama | |
| **Kurgu kaza şüphesi** | 4. HD E.2024/3235 K.2024/4692 (14.05.2024, oy çokluğu): anlaşmalı tutanakta el yazısı benzerliği, fotoğraf-yer uyumsuzluğu, krokinin başka dosyalarda tekrarı → hakem heyeti el çekmeli, genel mahkemede tam delil toplanmalı | |
| Hasar–kaza uyumu tespit edilemiyorsa taraflara delil sunma imkânı | 4. HD E.2025/4136 K.2025/8579 (bozma: delil imkânı tanınmalı; hakem heyeti el çekmeli, iş genel mahkemede görülmeli) | |

**Kural:** tutanaktaki "asli kusurlu" tespiti başlangıç noktasıdır, sonuç değildir. Not her zaman "kusur oranı için bilirkişi raporu gerekir" der; ceza dosyası varsa istenmesini önerir; kesinleşmiş ceza kararındaki maddi vakıaları ayrı satırda listeler.

**Müterafik kusur** (kask, emniyet kemeri, alkollü sürücünün aracına binme) kusur oranında değil, **tazminattan indirim** olarak (TBK m.52) değerlendiriliyor. Tutanakta kemer takılmadığı yazılıysa bu sabit sayılır; 4. HD yerleşik uygulamada indirim yapıyor ve müterafik kusuru def'i değil, re'sen gözetilecek hâl sayıyor (4. HD E.2022/12349 K.2024/9969). İndirim oranını tablodan yazma; kararlarda karşı oy ve kemer durumu belirsizse tartışma var `[incele]`. Kaskta takılmamanın maluliyetle illiyeti doktor heyetinden alınacak raporla saptanmalı `[çekildi ama desteği doğrulayın]`.

---

## 6. Senaryolar ve bilirkişi soruları

Her senaryo: oluş anlatımı · destekleyen deliller · çürüten deliller · ilgili kural (m.84 bendi / diğer madde). Sonuç cümlesi en fazla "Senaryo 1 kabul edilirse A'nın asli kusurlu sayılması muhtemeldir `[incele]`" düzeyinde kalır; **oran yazılmaz**.

**Soru bankası** (senaryoya göre seç):
- Çarpışma noktası hangi şeritte / yol bölümündedir; dayanak iz ve ölçü nedir?
- Araçların çarpışma öncesi hızı hasar ve izlerden tahmin edilebiliyor mu; hangi yöntemle?
- Sürücü tehlikeyi hangi mesafeden algılayabilirdi; algılama-reaksiyon ve durma mesafesine göre kazadan kaçınabilir miydi?
- Öndeki araç ani ve nedensiz fren yapmış mıdır; Yön. m.157/a son paragraftaki zorunluluk hâli var mıdır?
- Kavşağa hangi araç önce girmiştir; levha / ışık durumu nedir?
- Hasarlar iddia edilen oluşla teknik olarak uyumlu mudur?
- Ceza dosyasındaki rapor ile bu rapor arasındaki fark nedir; hangi tespit neden tercih edilmiştir?
- Yaya, yolcu ya da motosikletlinin davranışı (kask, kemer, geçiş yeri) zararın artmasına katkıda bulunmuş mudur `[incele]`?

---

## 7. Kaçınılabilirlik aracı

`legal_calculate_stopping_distance` (`mod: durma | izden_hiz | kritik_hiz | yaya | takip`). Araç alt/tipik/üst senaryo verir; reaksiyon süresi ve sürtünme aralıkları model bilgisidir, çıktıdaki `[model bilgisi — doğrulayın]` uyarısı nota taşınır. Hız sınırı: levhadaki sınır biliniyorsa `hiz_siniri_kmh`, bilinmiyorsa `kty_100` (kaza tarihi, araç cinsi, yol türü, römork) verilir; araç Yönetmelik tablosundan kaza tarihindeki genel sınırı bulur. Sınırı elle tablodan okuyup yazma; araç "bilinmiyor" ya da "tablo yüklü değil" dönerse sınır `[___]` kalır ve levha sorulur. Yalnız şu hâllerde ve yalnız **kroki ya da keşif ölçüsü varsa** çağrılır; sonuç senaryonun desteği olarak sunulur, kusur hükmü olarak değil:
- arkadan çarpma: takip mesafesi ve öndeki aracın fren anı (`takip`);
- yaya çarpması: sürücünün yayayı algılayabileceği mesafe (`yaya`);
- ölçülmüş fren izinden hız tahmini (`izden_hiz`);
- "ben önce girdim" iddiasında varış süreleri (`kritik_hiz` / `durma`).

Ölçü yoksa araç çağrılmaz; eksik delil listesine "olay yeri ölçümü / keşif" yazılır. Araç yoksa ya da yanıt vermiyorsa fiziksel hesap **elle yapılmaz**; soru bilirkişi soru bankasına taşınır.

---

## 8. Görüşme soruları
1. Kaza tarihi, saati, yeri; yol ve kavşak tipi; hava ve ışık?
2. Tutanak türü: kolluk mu, anlaşmalı mı? Kim imzaladı, imzalamadan önce okundu mu?
3. Kroki ölçülü mü; fren izi ölçüldü mü?
4. Fotoğraf ve kamera kaydı var mı; kayıt kimde, ne zaman silinir?
5. Tanık var mı; tutanakta adı geçiyor mu?
6. Ceza soruşturması / kovuşturması var mı; dosya no, aşama, kusur raporu alındı mı, karar kesinleşti mi?
7. Sigortacı ya da hakem heyeti kusuru neye dayanarak belirledi?

## soorgla çağrıları
```
legal_get_statute_article law_no: "2918" article_no: "81" | "84" (+ tutanakta anılan her madde)
legal_search_statute sorgu: "Karayolları Trafik Yönetmeliği 156" | "152" | "157"
legal_get_statute_article law_no: "6098" article_no: "74" | "52"
legal_search_cases mahkeme: "yargitay" daire: "4. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. kaza tespit tutanağı ile kusur raporu arasındaki çelişki giderilmeden hüküm kurulamaz>"
legal_get_case_document # en az bir kararın tam metni (SKILL.md Adım 3)
```

## Çıktı iskeleti
```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre; avukat değilse ARAŞTIRMA NOTU]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Kaza tutanağı ve kusur notu — [olay] — [kaza tarihi]
Okunan: [tutanak _ s., kroki _, fotoğraf _ (_ okunamadı), ceza dosyası var/yok]

### 1. Olay özeti (kaynaklı zaman çizgisi)
### 2. Sabitler
| Yol | Kavşak | Hava / ışık | Saat | Hız sınırı | Kaynak |
### 3. Tutanaktaki tespitler
- Görevlinin yazdığı ihlaller: Sürücü A — KTK m.__ [soorgla]; Sürücü B — yok
- Tutanakta oran yazılmış mı: hayır / evet (Yön. m.156/a-3'e aykırı)
### 4. Çelişkiler ve boşluklar
### 5. Kusur senaryoları (oran yok)
### 6. Bilirkişiye sorulacak sorular
### 7. Eksik delil ve nasıl temin edileceği
### 8. Devir
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

## Devir
- Kusur oranı belli olunca zarar ve sigorta yolu → `trafik-kazasi-ve-zmss.md`; araç hasarı → `arac-hasari-deger-kaybi-ve-pert.md`.
- Kusur raporu geldiyse → `bilirkisi-raporu-denetimi.md` §4.3.
- Kamera kaydı ve olay yeri için delil tespiti → `talep-yazisi-ve-delil-koruma.md`; dilekçe `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`.
- Rapora itiraz dilekçesi → `../../hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md`.
- Ceza dosyasında katılma ve belge isteme → `../../ceza-ve-infaz-dilekce/references/davaya-katilma.md`.

## Sık hatalar
- Tutanaktaki "asli kusurlu" ifadesini kusur oranı sanmak.
- Ölçüsüz krokiden hız ya da mesafe hesaplamak.
- 4. HD 2022/997'deki "aksi ispat edilinceye kadar geçerli resmî belge" cümlesini çoğunluk görüşü gibi alıntılamak.
- Ceza mahkemesinin kusur oranına bağlı kalmak; ya da tersine, kesinleşmiş maddi vakıaları yok saymak.
- Arkadan çarpmada zorunluluk istisnasını (Yön. m.157/a son paragraf) hiç sormamak.

## Kaynak
Eski YAML karşılığı yok.
