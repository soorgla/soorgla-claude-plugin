# Boşanma: dava türü, sebepler, kusur ve mali sonuçlar

**Ne zaman kullanılır:** kullanıcı boşanmak istiyor ya da boşanma davası açılmış; anlaşmalı/çekişmeli seçimi, boşanma sebebinin belirlenmesi, kusur değerlendirmesi, maddi/manevi tazminat ya da anlaşmalı boşanma protokolünün kontrolü isteniyor. Nafaka ayrıntısı → `nafaka.md`; velayet → `velayet-cocuk-ve-soybagi.md`; mal paylaşımı → `mal-rejimi-tasfiyesi.md`; şiddet ipucu → önce `aile-ici-siddet-6284.md`.

Temel ilke: boşanma kamu düzenine ilişkindir. Hâkim, tarafların ikrarıyla bağlı değildir; anlaşmalı boşanma bunun tek istisnasıdır (TMK 166/3 son cümle).

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| **Zina:** öğrenmeden **6 ay**, her hâlde eylemden **5 yıl**; affeden eşin dava hakkı yoktur | TMK 161/2-3 | Hak düşürücü. Süre geçtiyse aynı olaylar genel sebebe (166/1) dayanak yapılabilir mi? `[incele]` |
| **Hayata kast, pek kötü veya onur kırıcı davranış:** öğrenmeden **6 ay**, her hâlde sebebin doğumundan **5 yıl**; affeden eşin dava hakkı yoktur | TMK 162/2-3 | Şiddet varsa önce 6284 |
| **Terk:** ayrılık en az **6 ay** sürmüş olmalı; ihtar, sürenin **4. ayı bitmeden** istenemez; ihtardan sonra **2 ay** geçmeden dava açılamaz | TMK 164 | İhtar hâkim ya da noter eliyle yapılır; ihtar talebinin kendisi kötüniyetli olmamalı `[incele]` |
| **Anlaşmalı boşanma:** evlilik en az **1 yıl** sürmüş olmalı | TMK 166/3 | 1 yıl dolmadıysa anlaşma olsa da 166/1 çekişmeli yol |
| **Fiili ayrılık (166/4):** önceki boşanma davasının reddi kararının kesinleşmesinden itibaren **1 yıl** ortak hayat kurulamamışsa | TMK 166/4, 7532 m.13 ile değişik (RG 27.11.2024) | **Eski metin 3 yıldı.** 27.11.2024 öncesinde kesinleşen ret kararlarında 1 yıllık sürenin uygulanıp uygulanmayacağı açık bir sorudur: çalışma anında `legal_search_cases` (`daire: "2. Hukuk Dairesi"`, `tarih_baslangic: "2024-11-27"`, sorgu "166/4 önceki ret kararı kesinleşme bir yıl 7532") ile ara ve en az bir kararın tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: 166/4 geçiş uygulaması]` yaz |
| **Boşanmadan doğan dava hakları** (tazminat, yoksulluk nafakası boşanma davasında istenmediyse): boşanma hükmünün kesinleşmesinden **1 yıl** zamanaşımı | TMK 178 | Mal rejimi tasfiyesine **uygulanmaz** (10 yıl) → `mal-rejimi-tasfiyesi.md` |
| İstinaf: tebliğden **2 hafta** | HMK 345 | `legal_calculate_deadline` `hmk_appeal` |

`legal_calculate_deadline` TMK sürelerini hesaplamaz; elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]` yaz.

---

## Kontrol listesi

### 1. Güvenlik ve acil tedbir 🔴
- Şiddet, tehdit, ısrarlı takip var mı? Varsa önce `aile-ici-siddet-6284.md`.
- Dava açılınca hâkim barınma, geçim, malların yönetimi ve çocukların korunması için geçici önlemleri **re'sen** alır (TMK 169). Tedbir nafakası ve konutun kullanımı talep listesine konur.

### 2. Görev ve yetki
- Görevli mahkeme: **aile mahkemesi** (4787 m.4/1). Aile mahkemesi kurulamayan yerde HSK'nın belirlediği asliye hukuk mahkemesi bakar.
- Yetkili mahkeme: eşlerden birinin yerleşim yeri ya da davadan önce **son 6 aydır** birlikte oturdukları yer (TMK 168). Bu yetkinin kesin olup olmadığı `[incele]`.
- **Arabuluculuk:** boşanmanın kendisi tarafların serbestçe tasarruf edebileceği bir konu değildir. Aile içi şiddet iddiası varsa uyuşmazlık arabuluculuğa hiç elverişli değildir. Boşanma için dava şartı arabuluculuk yoktur: 6325 m.18/A yalnız "ilgili kanunlarda" dava şartı sayılan hâllere uygulanır, m.18/B listesi (kira, paylaştırma ve ortaklığın giderilmesi, kat mülkiyeti, komşu hakkı) boşanmayı içermez, 4787'de arabuluculuk hükmü yoktur. Yeni bir yasal değişiklik ihtimaline karşı `legal_search_official_gazette` ile son değişiklikleri tara.

### 3. Dava türü seçimi
| Yol | Koşul | Dikkat |
|---|---|---|
| Anlaşmalı (166/3) | Evlilik ≥ 1 yıl; birlikte başvuru ya da diğerinin davasını kabul; hâkim tarafları **bizzat** dinler; mali sonuçlar ve çocuklar konusunda anlaşma | Hâkim protokolde değişiklik yapabilir, taraflar kabul ederse boşanır. Protokolde bir kalem eksikse (ör. mal rejimi, nafaka) anlaşmalı boşanma koşulları bozulabilir `[incele]` |
| Genel sebep (166/1-2) | Evlilik birliğinin temelinden sarsılması | Davacının kusuru daha ağırsa davalı itiraz edebilir; itiraz hakkın kötüye kullanılmasıysa ve korunmaya değer yarar kalmadıysa yine boşanır (166/2). |
| Özel sebepler (161-165) | Zina, hayata kast/pek kötü veya onur kırıcı davranış, suç işleme ve haysiyetsiz hayat, terk, akıl hastalığı | Kesin sebeplerde kusur ve sarsılma ayrıca ispat edilmez. Hak düşürücü süre yalnız zina (161) ve hayata kast/pek kötü davranış (162) için vardır (öğrenmeden 6 ay, her hâlde 5 yıl; affeden eşin dava hakkı yok); suç ve haysiyetsiz hayatta (163) dava "her zaman" açılabilir, akıl hastalığında (165) süre yok ama iyileşmezliğin resmî sağlık kurulu raporuyla tespiti şart; terkte (164) ihtar usulü ve bekleme süreleri işler. Özel ve genel sebep birlikte (terditli ya da kümülatif) ileri sürülebilir `[incele]` |
| 166/4 fiili ayrılık | Önceki ret kararının kesinleşmesinden 1 yıl ve ortak hayatın kurulamaması | Kusur incelemesi yapılmaz; ama tazminat ve nafaka için kusur yine önemlidir `[incele]` |

Eski YAML'daki strateji önerisi ("zina yerine genel sebebe dayanalım, ispatı daha kolaydır") bir takdir meselesidir ve `[incele]` olarak sunulmalıdır. Zinanın ispatı ile tazminat ve katılma alacağındaki etkisi (TMK 236/2) birlikte tartılır.

### 4. Kusur değerlendirmesi
- Olay kronolojisini çıkar (SKILL.md Adım 4). Her olay için şunları not et: tarih, delil (tanık, mesaj, HTS, rapor, tutanak), **affetme ya da hoşgörü** (olaydan sonra birlikte yaşamaya devam), karşı tarafın bilgisi.
- Davadan önce affedilen ya da hoşgörüyle karşılanan olaylar kusur olarak yüklenemez (ör. kadın evi terk ettikten sonra ortak konuta dönüp evliliği sürdürmüşse, önceki olaylar affedilmiş, en azından hoşgörüyle karşılanmış sayılır).
- Dava açıldıktan sonraki olayların kusur belirlemesine etkisi ayrı bir sorudur: çalışma anında `legal_search_cases` (`daire: "2. Hukuk Dairesi"`, sorgu "dava tarihinden sonra meydana gelen olaylar kusur belirlemesinde") ile ara, en az bir kararın tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: dava sonrası olayların kusura etkisi]` yaz.
- Delil hukuka uygun mu? Gizli kayıt, telefona erişim, özel yazışma. Hukuka aykırı delil riski 🟠 `[incele]`.
- Kusur sonucu: tam kusurlu / daha ağır kusurlu / eşit kusurlu / daha az kusurlu / kusursuz.

### 5. Tazminat (TMK 174)
- **Maddi tazminat:** mevcut ya da beklenen menfaatleri boşanma yüzünden zedelenen, **kusursuz ya da daha az kusurlu** taraf, kusurlu taraftan isteyebilir (174/1).
- **Manevi tazminat:** boşanmaya yol açan olaylar yüzünden **kişilik hakkı saldırıya uğrayan** taraf, kusurlu diğer taraftan isteyebilir (174/2).
- **Düzeltme:** eski YAML "eşit kusur hâlinde tazminat alınamaz, sadece boşanılır" diyordu. Maddi tazminat için bu, 174/1'deki "kusursuz veya daha az kusurlu" koşulundan çıkar. Manevi tazminatta ölçüt ayrıdır: kişilik hakkı saldırısı ve karşı tarafın kusuru. Eşit kusurda manevi tazminat verilip verilmeyeceği içtihada bırakılır `[incele]`.
- Manevi tazminat irat biçiminde ödenemez; maddi tazminat toptan ya da irat olabilir (TMK 176/1-2).
- Miktar takdire bağlıdır. Faiz başlangıcı ve faiz türü (yasal faiz) → `legal_get_legal_interest_rates` `[incele]`.

### 6. Anlaşmalı boşanma protokolü — kontrol listesi
Protokolde şu kalemlerin her biri **açıkça** yer almalıdır; eksik kalem 🟠:
1. Boşanma iradesi ve tarafların kimliği.
2. Velayet ve kişisel ilişki takvimi: hafta sonu, bayram, yaz tatili, telefon/görüntülü görüşme, teslim yeri.
3. İştirak nafakası (miktar, artış ölçütü, ödeme günü, hesap).
4. Yoksulluk nafakası **ya da açık feragat**.
5. Maddi ve manevi tazminat **ya da açık feragat**.
6. Mal rejimi tasfiyesi: ya ayrıntılı paylaşım ya da açık bir "karşılıklı hiçbir talep yoktur" kaydı. Kapsamı belirsiz feragat, ileride katılma alacağı davasına kapı açar `[incele]`.
7. Ziynet eşyası ve kişisel eşya iadesi.
8. Ortak konut ve kredi borcu.
9. Yargılama giderleri ve vekâlet ücreti.
10. Tarafların bizzat duruşmada hazır olacağı.
- Kullanıcı avukat değilse protokol "TASLAK — avukat incelemesi bekliyor" işaretini taşır (ORTAK-KURALLAR.md §1).

### 7. Ziynet ve kişisel eşya
- **Eskimiş kural uyarısı:** 2. HD'nin önceki içtihadı "düğünde kime ne takılırsa takılsın hepsi kadına ait sayılır" yönündeydi (ör. E.2023/5245 K.2024/3793, 23.05.2024). Daire bu içtihadı **değiştirdi**. Güncel ilke: (1) taraflar arasında paylaşım anlaşması varsa ona göre; (2) yoksa iddia ve ispat edilen yerel örf ve adete göre; (3) o da yoksa erkeğe ve kadına takılan, ekonomik değer taşıyan her şey **kural olarak takılan eşe** aittir. Karşı cinse özgü takı o cinse verilmiş sayılır; her iki cinse özgü olan takılan eşe, takı sandığına/torbasına konulan her iki cinse özgü şey ortak sayılır; özgü olma çekişmeliyse bilirkişi incelemesi yapılır.
- İspat: kadına özgü ziynetlerin kadının himayesinde bulunması olağandır; aksini (ziynetin alındığını, kadında olmadığını) iddia eden kadın ispatla yükümlüdür (HMK 190, TMK 6 ve 222/1). Olayın tarihi eski içtihat dönemine düşüyorsa iki görüşü de göster `[incele]`.
- Ziynet alacağı boşanma davasıyla birlikte ya da ayrı açılabilir. Ayrı açılırsa harç ve görev `[incele]`.

### 8. Ceza boyutu ve diğer alanlar
- Şiddet, tehdit ya da özel hayatın gizliliğinin ihlali varsa ceza yönünü yalnız işaretle. Dilekçe ceza becerisine gider.
- Eşler arasındaki borç ve eşya davaları (TBK kaynaklı) 2026 iş bölümünde 2. HD'dedir.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4721" article_no: "161" | "162" | "164" | "166" | "168" | "169" | "174" | "176" | "178"
legal_get_statute_article law_no: "4787" article_no: "4"
legal_search_official_gazette query: "4721 sayılı Türk Medeni Kanununun" date_from: "<son 2 yıl>"
legal_search_cases mahkeme: "yargitay" daire: "2. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. eşine sürekli hakaret eden ve ekonomik şiddet uygulayan erkek ağır kusurludur>"
legal_search_cases mahkeme: "yargitay" daire: "Hukuk Genel Kurulu" sorgu: "<kusur, affetme, hoşgörü>"
legal_search_cases mahkeme: "bam" sorgu: "<tazminat miktarı>" # tazminat miktarında BAM uygulaması
legal_search_cases mahkeme: "anayasa" sorgu: "TMK 166 dördüncü fıkra" # AYM 2023/116 K.2024/56
legal_get_case_document belge_id: "<seçilen son 3 yıl kararı>"
legal_calculate_court_fee (boşanma harcı)
legal_calculate_deadline kural_kodu: "hmk_appeal"
```
Ek kaynak: `mevzuat_no: 5718` → yabancılık unsuru varsa `yabancilik-unsuru-ve-tanima.md`.

---

## Görüşme soruları

1. Evlilik tarihi? Daha önce boşanma davası açıldı ve reddedildi mi? Reddedildiyse kesinleşme tarihi?
2. Ortak çocuklar: doğum tarihleri, şu an kimin yanında?
3. Şu an birlikte mi yaşıyorsunuz? Ayrıldıysanız ne zaman ve kim ayrıldı?
4. Boşanmaya yol açan olaylar tarih sırasıyla nelerdir? Hangisini ne zaman öğrendiniz? Olaylardan sonra barıştınız mı?
5. Şiddet, tehdit ya da ısrarlı takip var mı? Daha önce 6284 kararı ya da şikâyet oldu mu?
6. Deliller: tanık (kim, neyi gördü), mesaj, fotoğraf, darp raporu, kolluk tutanağı?
7. Karşı taraf anlaşmaya açık mı? Hangi konularda anlaşma var?
8. Gelir durumları: iki tarafın da işi, maaşı, mal varlığı?
9. Evlilik içinde edinilen mallar: konut, araç, birikim, şirket payı, kredi?
10. Taraflardan biri yabancı mı ya da yurt dışında mı yaşıyor?
11. Yerleşim yerleri ve son 6 ay birlikte oturulan yer?

## Çıktı iskeleti

```markdown
## Boşanma değerlendirmesi: [müvekkil] — [tarih]
### Sonuç
[önerilen yol: anlaşmalı / genel sebep / özel sebep + genel sebep; tek cümle neden]
### Güvenlik (varsa)
### Kritik süreler
| Sebep | Öğrenme / olay tarihi | Hak düşürücü süre sonu | Dayanak | Durum |
### Olay kronolojisi
| Tarih | Olay | Delil | Önem (🔴/🟡/⚪) | Affetme? |
### Kusur değerlendirmesi
[taraf bazında; [incele]]
### Mali sonuçlar
| Kalem | Talep edilebilir mi | Dayanak | Not |
### Protokol kontrolü (anlaşmalıysa)
| Kalem | Var/Eksik | Risk |
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- 166/4 için "3 yıl" yazmak. 7532 ile **1 yıl** oldu.
- Anlaşmalı boşanmada evliliğin 1 yılı doldurmadığını kaçırmak.
- Zina ya da hayata kastta 6 aylık sürenin affetme ve öğrenme tarihine göre geçtiğini görmemek.
- Terk ihtarını 4. ay dolmadan istemek.
- Protokolde mal rejimini ya da yoksulluk nafakasını belirsiz bırakmak.
- Mal rejimi alacağına TMK 178'deki 1 yıllık zamanaşımını uygulamak.
- Şiddet anlatılan dosyada arabuluculuk ya da uzlaşma önermek.

---
