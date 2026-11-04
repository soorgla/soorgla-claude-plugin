# İş kazası, meslek hastalığı ve rücu

**Ne zaman kullanılır:** iş kazası ya da meslek hastalığının tespiti, sigortalının veya hak sahiplerinin işverene karşı maddi/manevi tazminatı, SGK'nın işverene ya da üçüncü kişiye rücu davası, kusur ve maluliyet raporlarına itiraz.

İki taraf, aynı olay:
- **İşçi / hak sahipleri tarafı:** iş kazası tespiti, maddi tazminat (sürekli iş göremezlik, destekten yoksun kalma), manevi tazminat.
- **İşveren tarafı:** SGK'nın 5510 m.21 rücu davası, kusur raporuna itiraz, tazminatı azaltma.

İş kazası sonrası fesih ya da işçilik alacağı varsa `is-hukuku`; olay aynı zamanda trafik kazasıysa (servis aracı) ZMSS yönü için `tazminat-haksiz-fiil` (`../../tazminat-haksiz-fiil/references/trafik-kazasi-ve-zmss.md`); iş kazası tazminatı bu dosyada kalır.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| İşverenin kazayı bildirmesi: kolluğa **derhal**, Kuruma kazadan sonra en geç **3 iş günü** | 5510 m.13/2-a  | Kaza işverenin kontrolü dışındaki yerde olduysa süre öğrenmeden başlar. Süresinde bildirilmezse bildirime kadarki geçici iş göremezlik ödeneği işverenden tahsil edilir (m.21/2).  |
| Meslek hastalığı bildirimi: işverenin (4/1-b'lide sigortalının kendisinin) öğrendiği günden itibaren **3 iş günü** | 5510 m.14  | Bildirmeyen ya da kasten eksik bildiren işverene Kurum masrafları ve ödenmiş geçici iş göremezlik ödenekleri rücu edilir. Meslek hastalığının Kurum Sağlık Kurulunca tespiti zorunludur; yükümlülük süresi aşılmış olsa da Sosyal Sigorta Yüksek Sağlık Kurulu onayıyla kabul edilebilir. |
| İşçinin işverene karşı maddi/manevi tazminat davası: **10 yıl** | TBK m.146 (sözleşmeye aykırılık; TBK m.72'deki 2 yıl uygulanmaz)  | **Başlangıç olay tarihi değil:** zararın öğrenildiği, sürekli iş göremezlik oranının kesin olarak belirlendiği tarih. Olayın Kurumca iş kazası sayılması ve oranın belirlenmesi beklenir.  Eski referanstaki "TBK m.72 / m.146" ikircikliği giderildi. Destekten yoksun kalma ve üçüncü kişiye karşı (haksız fiil) davada TBK m.72 `[incele]`. |
| SGK rücu davası: **10 yıl** (özel hüküm) | 5510 m.93/3  | Başlangıç olay tarihi değil: gelirler için Kurum onay tarihi, masraf ve ödemeler için masraf/ödeme tarihi. |
| Zorunlu arabuluculuk | 7036 m.3/3 | İş kazası ve meslek hastalığından doğan maddi/manevi tazminat ile bunlarla ilgili tespit, itiraz ve rücu davalarında **uygulanmaz**. Korkuluk: bu davalarda arabuluculuk son tutanağı isteme ya da süre hesabına arabuluculuğu katma.  |
| Kurumun iş kazası saymadığı olayın tespiti (Kuruma karşı) | 7036 m.4/1 | Önce Kuruma başvuru; 60 gün cevapsızlık = ret.  |

---

## Kontrol listesi

### 1. Olay iş kazası mı? (5510 m.13)
`legal_get_statute_article(law_no: "5510", article_no: "13")` ile çek; maddedeki hâllerden hangisi:
- İşyerinde bulunduğu sırada,
- İşveren tarafından yürütülen iş nedeniyle (işyeri dışında da),
- Görevle başka yere gönderilme,
- Emziren kadın işçinin süt izni sırasında,
- İşverence sağlanan taşıtla işin yapıldığı yere gidiş-geliş (servis kazası).
- **İlliyet bağı:** iç nedenli olaylarda (kalp krizi, beyin kanaması) 10. HD işyerinde meydana gelen kalp krizini iş kazası sayma eğiliminde; ancak olayın gerçekten kalp krizi olup olmadığının tıbbi tespiti için kardiyolog bilirkişi raporu istiyor. Daire içinde karşı görüş var: karşı oya göre işyerinde olmak yeterli, illiyet yalnız gelir/tazminat miktarını etkiler. Tazminat davasında (işveren sorumluluğu) çalışma koşullarının krizi tetikleyip tetiklemediği ayrıca araştırılır. `[incele]` 
- Kurum olayı iş kazası saymadıysa önce **iş kazası tespiti** (Kuruma başvuru + dava); tazminat davasında bu sonuç beklenir (bekletici mesele) `[incele]`.

### 2. Kusur
- İşverenin İSG yükümlülükleri (6331): risk değerlendirmesi, eğitim, kişisel koruyucu donanım, denetim, iş güvenliği uzmanı/işyeri hekimi. 2025'te 6331'de ÇASMER ve yetkilendirme hükümleri değişti; kusur raporunda atıf yapılan yükümlülüğün olay tarihindeki metnini çek. 
- **İşçinin müterafik kusuru** → tazminattan indirim (TBK m.52/1 — zarar görenin zararın doğmasında ya da artmasında etkisi). 
- Üçüncü kişi kusuru, kaçınılmazlık.
- Kusur raporu: SGK müfettişi, ceza dosyası bilirkişisi, hukuk mahkemesi bilirkişisi — raporlar arası çelişki varsa 🟠. Bilirkişinin alanında uzman (İSG uzmanı + teknik uzman) olup olmadığı `[incele]`. Rapor geldiyse denetim listesi (heyet uzmanlığı, oransal tespit, rücuda kusurun uygulanacağı tutar) → `../../tazminat-haksiz-fiil/references/bilirkisi-raporu-denetimi.md` §4.4; maluliyet ve aktüerya raporu için aynı dosyanın §4.1-4.2'si.

### 3. Maluliyet
- Sürekli iş göremezlik oranı (SGK Sağlık Kurulu / Adli Tıp). Oran "sabit ve net" değilse zamanaşımı başlamamış olabilir (HGK 2024/104). İtiraz yolu `[incele]`.
- Oran yüksekse malullük aylığı ihtimali → `emeklilik-ve-borclanma.md` (5510 m.25-26).

### 4. Maddi tazminat (işçi tarafı)
- Gerçek zarar: kazanç kaybı × maluliyet oranı × kusur oranı, aktif ve pasif dönem; bakiye ömür → `legal_get_life_expectancy`.
- **Tenkis:** SGK'nın bağladığı gelirin ilk peşin sermaye değerinin (PSD) yalnız **rücuya tabi kısmı** gerçek zarardan düşülür; aynı zarar iki kez ödenmez. Rücu edilemeyen sosyal güvenlik ödemeleri (işçinin kusuruna düşen kısım, kaçınılmazlık/teknik arıza hâlleri, tahsisten sonraki artışlar) indirilmez (TBK m.55/1). Mahkeme Kurumdan gelir bağlanıp bağlanmadığını sormalıdır.  7589 s. Kanunla TBK m.55'e iki fıkra eklendi: kazancı bilinen döneme ait tazminata olay tarihinden, bilinmeyen döneme ait tazminata karar tarihinden kanuni faiz; tahkikat başlayıncaya kadar ifa amacıyla ödenen bedel ödeme tarihine göre oransal mahsup. Yalnız yürürlükten (31.07.2026) sonra meydana gelen olaylara uygulanır (7589 geçici m.1/9). 
- Destekten yoksun kalma (ölüm hâlinde): TBK m.53/3 (cenaze ve tedavi giderleri m.53/1-2). 
- Asgari ücret alt sınırı → `legal_get_social_parameters tur: "asgari_ucret_net"`.
- Hesap aktüerya bilirkişisi işidir; burada yalnızca yöntem ve girdiler gösterilir, her tutar `[doğrula]`. Yeniden hesap `legal_calculate_actuarial_present_value` (`islem: tazminat`; maluliyette `islem: maluliyet_birlestir`, `kip: "sgk_meslekte_kazanma"`) ile yapılır. Araç SGK rücu kipini ayrıca hesaplamaz: rücuda kusur oranının uygulanacağı tutar (gerçek zarar ile peşin sermayeli gelirden düşük olanı) elle karşılaştırılır `[incele]`.

### 5. Manevi tazminat
- TBK m.56: olayın ağırlığı, kusur oranları, tarafların ekonomik durumu; zenginleşme aracı olmamalı. Tutar önermeyi `[incele]` ile sınırla, emsal kararlardan aralık çıkar (BAM ve 10. HD).

### 6. Rücu (işveren tarafı) — 5510 m.21
- SGK'nın rücu edebilmesi için işverenin **kastı ya da İSG mevzuatına aykırı hareketi** gerekir; kusursuz işverene rücu edilemez. Sorumluluğun tespitinde kaçınılmazlık ilkesi dikkate alınır. 
- Rücu tutarı: yapılan ve yapılacak ödemeler ile gelirin başladığı tarihteki ilk peşin sermaye değeri toplamı; **sigortalının ya da hak sahiplerinin işverenden isteyebileceği tutarla sınırlı**. Üçüncü kişi kusurunda PSD'nin yarısı üçüncü kişiye ve kusurlu çalıştıranına rücu edilir (m.21/4). 
- SGK'nın hesapladığı gelir ve masraf kalemleri doğru mu?
- Bildirim süresine uyulmuş mu (uyulmadıysa m.21/2 ve m.14 rücuları)?

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "5510"  article_no: "13" | "14" | "21" | "93"
legal_get_statute_article  law_no: "6331"  article_no: "4"          # işverenin genel yükümlülüğü
legal_get_statute_article  law_no: "6098"  article_no: "52" | "53" | "56" | "146" | "149"
legal_get_statute_article  law_no: "7036"  article_no: "3" | "4"
legal_search_statute_semantic  sorgu: "iş kazası ve meslek hastalığı bildirimi yönetmelik"   mevzuat_tur: "kurum_yonetmeligi"
legal_search_cases  mahkeme: "yargitay"  daire: "10. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. servis aracında meydana gelen kaza iş kazası işverenin kusuru rücu>"
legal_search_cases  mahkeme: "yargitay"  daire: "10. Hukuk Dairesi"
    sorgu: "iş kazası tazminat zamanaşımı sürekli iş göremezlik oranının kesinleşmesi"
legal_search_cases  mahkeme: "yargitay"  daire: "21. Hukuk Dairesi"  tarih_bitis: "2020-09-02"   # kapatılan daire, eski emsal
legal_search_cases  mahkeme: "yargitay"  daire: "Hukuk Genel Kurulu"
legal_search_cases  mahkeme: "bam"  sorgu: "<olay> manevi tazminat miktarı"
legal_get_case_document  belge_id: "<seçilen karar>"
legal_get_life_expectancy  cinsiyet: …  yas: …
legal_get_social_parameters  tur: "asgari_ucret_net"
legal_get_legal_interest_rates
```
Eski profildeki `mevzuat_turu: yönetmelik` (İSG ve bildirim yönetmelikleri) → `legal_search_statute_semantic` (`mevzuat_tur: "kurum_yonetmeligi"`).

Yargı yeri: iş mahkemesi; temyizde 10. HD (SGK rücu ve işçi-işveren arasındaki iş kazası/meslek hastalığı tazminatı; 4857 m.77'ye dayalı tazminat da). Kapatılan 21. HD'nin kararları yalnız eski emsal. Daire görevi BGK kararıyla yıllık değişebilir; tarihli atıf kullan. 

---

## Görüşme soruları

1. Kimin adına? (kazalı işçi / hak sahipleri / işveren)
2. Kaza tarihi, yeri, nasıl oldu (ayrıntılı)?
3. İşçinin görevi; kaza anında ne yapıyordu?
4. SGK'ya ve kolluğa bildirim yapıldı mı, ne zaman?
5. Kurum olayı iş kazası saydı mı? Sürekli iş göremezlik oranı kesinleşti mi, hangi tarihte?
6. Müfettiş raporu, ceza soruşturması, bilirkişi raporu var mı; kusur oranları?
7. SGK gelir bağladı mı, PSD tutarı?
8. İşçinin yaşı, cinsiyeti, ücreti, bakmakla yükümlü olduğu kişiler?
9. İSG belgeleri: eğitim kayıtları, KKD zimmet tutanağı, risk değerlendirmesi?
10. (Rücu) SGK'nın talep ettiği tutar ve kalemleri, tebliğ tarihi; gelirin onay tarihi?

## Çıktı iskeleti

```markdown
## İş kazası değerlendirmesi: [olay] — [tarih]
### Sonuç
### İş kazası niteliği (5510 m.13) ve Kurum tespiti
### Kusur dağılımı
| Taraf | Oran | Kaynak (rapor) | İtiraz noktası |
### Maluliyet ve SGK gelirleri
### Tazminat / rücu kalemleri
| Kalem | Yöntem | Girdiler | Tutar [doğrula] |
### Süreler (zamanaşımı başlangıcı ayrı satırda)
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- 🔴 İşçinin tazminat davasında TBK m.72'deki 2 yıllık süreyi uygulamak ya da 10 yılı olay tarihinden saymak.
- 🔴 Bu davalar için arabuluculuk son tutanağı aramak.
- 🟠 Rücuda işverenin kusursuzluğunu (kaçınılmazlık) ve "işçinin isteyebileceği tutarla sınır" kuralını tartışmamak.
- 🟠 PSD tenkisini atlamak.
- 🟡 Kusur raporları arasındaki çelişkiyi itiraz konusu yapmamak.

---

