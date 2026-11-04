---
name: hukuk-yargilamasi-dilekce
description: >
  Hukuk davasında ilk derece mahkemesine verilecek dilekçenin metnini kurar:
  dava, cevap, replik, düplik, ıslah, delil ve tanık listesi, bilirkişi
  raporuna itiraz, ihtiyati tedbir, delil tespiti, mazeret; ayrıca dava öncesi
  zorunlu arabuluculuk başvurusu ve noter ihtarnamesi. Süreyi madde metninden
  çeker, eksik bilgiyi sorar, harcı hesaplar. Kullanıcı "dava dilekçesi yaz",
  "cevap dilekçesi hazırla", "bilirkişi raporuna itiraz", "noterden ihtarname
  çek" dediğinde kullan. İstinaf ve temyiz kanun-yollari-dilekce'de, ceza
  dilekçeleri ceza-ve-infaz-dilekce'de, avukatsız vatandaş başvurusu
  vatandas-basvurulari'nda yazılır.
argument-hint: "[dilekçe türü + olay ya da dosya bilgisi: mahkeme, esas no, tebliğ tarihi, taraflar; varsa karşı tarafın dilekçesi / bilirkişi raporu]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /hukuk-yargilamasi-dilekce

Hukuk yargılamasında (HMK) sunulacak dilekçelerin taslağını kuran **dilekçe katmanı**. Hukuki değerlendirme (hak var mı, tazminat ne kadar) ilgili alan becerisinin işidir; bu beceri o değerlendirmeyi **usule uygun, süresi hesaplanmış, atıfları çekilmiş** bir dilekçeye çevirir. Ayrıntılı kontrol listeleri `references/` altındadır; her dilekçe türünde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı, "taslaktır" kapısı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- HMK 6100 ilk derece dilekçeleri: dava dilekçesi, cevap, replik, düplik, ıslah, delil ve tanık listesi, bilirkişi raporuna itiraz, esasa ilişkin beyan.
- İhtiyati tedbir ve tedbire itiraz, delil tespiti, HMK'ya göre eski hâle getirme, mazeret, bekletici mesele, kısmi dava (HMK 109/4).
- Dava şartı arabuluculuk başvurusu: iş (7036 m.3), ticari (TTK 5/A), tüketici (6502 m.73/A), kira, ortaklığın giderilmesi, kat mülkiyeti, komşuluk.
- Noter ihtarnamesi: temerrüt, kira ödeme, tacirler arası.
- Tipik cümleler: "cevap süresi", "ıslah", "tanık listesi", "ihtiyati tedbir", "delil tespiti", "mazeret dilekçesi", "arabuluculuk başvurusunu yaz".
- Hak ve tutar değerlendirmesi önce alan becerisinde yapılır (ör. işe iade → is-hukuku, sonra bu beceri).

## Kapsam

**Kapsar:** asliye hukuk, asliye ticaret, sulh hukuk, tüketici, iş, aile mahkemelerinde HMK'ya tabi ilk derece dilekçeleri; dava öncesi zorunlu arabuluculuk başvurusu; noter ihtarnamesi.

**Kapsamaz ya da yönlendirir:**
- İstinaf ve temyiz dilekçeleri → `kanun-yollari-dilekce` becerisi (yüklü değilse yalnız süre tablosu: `legal_calculate_deadline` `hmk_appeal` / `hmk_cassation`).
- Ceza muhakemesi ve infaz (CMK, 5275) dilekçeleri, CMK'ya göre eski hâle getirme → `ceza-ve-infaz-dilekce`. **CMK sürelerini bu beceriden verme.**
- SGK/vergi/KİK itirazları, resmî yazı ve kurum başvuruları → `idari-ve-kurum-basvurulari`. İdari yargıda dava dilekçesi → `../idare-davalari-imar/references/idari-dava-dilekcesi.md`; idari yargıda istinaf/temyiz → `kanun-yollari-dilekce`.
- Ödeme emrine itiraz (İİK 62, 168): avukatsız vatandaş → `vatandas-basvurulari`; takip yolu, itirazın kaldırılması, icra mahkemesine şikâyet, ihalenin feshi, sıra cetveli, iflas ve konkordato değerlendirmesi ve iskeletleri → `icra-iflas`. İtirazın iptali / menfi tespit / istirdat / tasarrufun iptali davası dilekçesi ve ihtiyati haciz talebi buradadır (esas `icra-iflas`'tan devralınır).
- AYM bireysel başvurusu ve AİHM → `aym-aihm-basvuru`.
- Esasa ilişkin hukuki değerlendirme → alan becerisi (ör. `is-hukuku`). Alan becerisi yüklü değilse esas sorusunu `[incele]` ile işaretle; dilekçeyi kurmaya devam et.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
Dilekçe türüne ait ana maddeyi `legal_get_statute_article` ile çek (ör. dava dilekçesi için `law_no: "6100"`, `article_no: "119"`). Yanıt gelirse `soorgla ✓`. Profili oku: rol (avukat / değil), vekil bilgisi.

### Adım 1 — Hangi dilekçe? Yönlendir

| Dilekçe türü | İpucu sözcükler | Oku |
|---|---|---|
| A. Dava dilekçesi (kısmi dava; 31.07.2026 öncesi belirsiz alacak) | dava açmak, dava dilekçesi, alacak davası, tapu iptal, itirazın iptali, menfi tespit, kısmi dava, belirsiz alacak | `references/dava-dilekcesi.md` |
| B. Cevap, cevaba cevap, ikinci cevap | cevap dilekçesi, cevap süresi, ek süre, ilk itiraz, zamanaşımı def'i, replik, düplik, iddianın genişletilmesi | `references/cevap-ve-ikinci-dilekceler.md` |
| C. Islah | ıslah, dava değerini artırma, bilirkişi raporundan sonra harç tamamlama, tamamen ıslah | `references/islah.md` |
| D. Delil ve tanık listesi | tanık listesi, delil listesi, celp, müzekkere, senetle ispat | `references/delil-ve-tanik-listesi.md` |
| E. Bilirkişi raporuna itiraz ve esasa ilişkin beyan | bilirkişi itiraz, ek rapor, yeni bilirkişi, rapora beyan, esas hakkında beyan, son beyan | `references/bilirkisi-itirazi-ve-esasa-beyan.md` |
| F. İhtiyati tedbir (ve tedbire itiraz) | ihtiyati tedbir, satış yasağı şerhi, tedbirli dava, teminatsız tedbir, tedbire itiraz | `references/ihtiyati-tedbir.md` |
| G. Delil tespiti | delil tespiti, değişik iş, hasar tespiti, seviye tespiti, keşif talebi | `references/delil-tespiti.md` |
| H. Eski hâle getirme | süreyi kaçırdım, eski hâle getirme, hastalık nedeniyle süre | `references/eski-hale-getirme.md` |
| I. Mazeret ve bekletici mesele | duruşmaya gidemiyorum, mazeret dilekçesi, işlemden kaldırma, yenileme, bekletici mesele, ceza davasının beklenmesi | `references/mazeret-ve-bekletici-mesele.md` |
| J. **Zorunlu arabuluculuk başvurusu** (yeni) | arabulucuya başvuru, dava şartı arabuluculuk, son tutanak, ticari alacak, kira uyuşmazlığı, ortaklığın giderilmesi, tüketici | `references/arabuluculuk-basvurusu.md` |
| K. **Noter ihtarnamesi** (yeni) | ihtarname, temerrüt ihtarı, kira ödeme ihtarı, fesih bildirimi, ihbarname | `references/ihtarname.md` |

Bir iş birden çok türe giriyorsa (ör. ihtiyati tedbir talepli dava dilekçesi: A + F; arabuluculuk sonrası dava: J → A) hepsini oku, sırayı kronolojik kur.

### Adım 2 — Süreyi en başta belirle

Dilekçede en büyük risk süre kaçırmaktır. Her dilekçe türünün referans dosyasındaki **süre tablosunu** doldurmadan metne geçme.

1. Süreyi **madde metninden** çek (`legal_get_statute_article`). Beceri metnindeki süre ifadesi yalnız yön gösterir; çıktıya giren süre araçtan gelen metindir.
2. Son günü hesapla:
   - `legal_calculate_deadline` kanun yolu (`hmk_appeal`, `hmk_cassation`, `hmk_objection`), icra (`iik_complaint`, `iik_objection_payment_order`), kira, iş, idari yargı gibi ~70 kodu tanır; bilinmeyen kodda geçerli kod listesini döndürür. Cevap süresi ve bilirkişi raporuna itiraz için kod yok; bunları elle say. 
   - Diğer bütün süreleri (cevap, ikinci dilekçe, bilirkişi itirazı, eski hâle getirme, tedbir sonrası dava, arabuluculuk) **elle hesapla**: tebliğ günü sayılmaz, süre ertesi gün başlar; haftalık sürede aynı adlı günde, aylık sürede aynı sayılı günde biter. Son gün `legal_check_holiday` ile resmî tatil / hafta sonu ise sonraki ilk iş gününe kayar. Sonucu `[doğrula]` ve hesap adımlarıyla yaz. Resmî tatil günleri süreye dâhildir; yalnız son gün tatile rastlarsa süre ilk iş günü biter.  
   - **Adli tatil:** adli tatile tabi işlerde süre tatil içinde biterse tatilin bittiği günden itibaren bir hafta uzar (HMK m.104). İhtiyati tedbir, delil tespiti, işçinin açtığı iş davaları, nafaka, çekişmesiz yargı gibi işler adli tatilde de görülür; bunlarda uzama yoktur (HMK m.103). Adli tatil tarihlerini `legal_get_statute_article` 6100/102 ile çek. 
3. Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴 koy. Süre kaçmışsa `eski-hale-getirme.md` yolunu değerlendir.

### Adım 3 — Eksik zorunlu bilgileri sor

Referans dosyasındaki **görüşme sorularını** sor. Kurallar:
- Taraf adı, T.C. kimlik no, adres, esas numarası, tebliğ tarihi, dava değeri **uydurulmaz**. Bilinmeyen her alan `[___]` olarak kalır ve **Eksik bilgi** listesine girer.
- Kullanıcı "örnek dilekçe" istiyorsa kişisel veri yerine `[DAVACI AD SOYAD]` gibi yer tutucu kullan.
- Kullanıcının verdiği süre, madde ya da tutar çekilen metinle çelişiyorsa ilk cümlede söyle (ORTAK-KURALLAR.md §6).

### Adım 4 — Harç ve masraf
Nispi ya da maktu harç gerekiyorsa `legal_calculate_court_fee` ile hesapla. Tanınan kodlar örneği: `basvurma_asliye`, `basvurma_sulh`, `karar_ilam_nispi`, `pesin_harc`, `dava_masrafi_asliye`. Araç tarife dönemini döndürmüyor: tutarı `[doğrula — harç tarifesi dönemi]` diye işaretle. Harç tutarını beceri metnine yazma. 

### Adım 5 — Kaynak çek (gövdedeki her atıf MCP'den)

- **Mevzuat:** gövdede atıf yapılan her madde `legal_get_statute_article` ile çekilmiş olmalı. `18/A`, `5/A`, `73/A` gibi harfli maddelerde `legal_get_statute_article` boş dönüyor; bunları `legal_list_statute_articles` (`law_no`, `law_type: "Kanun"`, `article_no: "18"`, `include_content: true`) ile çek. 
- Değişiklik şüphesinde `legal_get_statute_article_history` ya da madde metnindeki "(Değişik: …)" notlarına bak. HMK'da 7251 (2020) değişiklikleri birçok süreyi ve kurumu etkiledi (m.107, 116, 141, 177, 281, 394, 402).
- **Kararlar:** `legal_search_cases` ile olayı serbest cümleyle ara; **en az bir güncel (son 3 yıl, `tarih_baslangic`) emsal kararın tam metnini `legal_get_case_document` ile oku** ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7): önermen çoğunluk gerekçesinde mi, karşı oyda mı? Karşı oydaki görüşü çoğunluk gerekçesi gibi yazma.
- Daire iş bölümünü sabit sayma; emin değilsen `legal_case_facets` ve güncel Yargıtay BGK kararı (`legal_search_official_gazette`, `search_in: "title"`, `query: "Büyük Genel Kurulu"`).
- Parasal sınırlar (senetle ispat, kesinlik, istinaf/temyiz sınırı) her yıl yeniden değerleme oranıyla artar (HMK ek m.1); beceriye tutar yazma. Senetle ispatta **işlemin yapıldığı tarih**, kesinlik sınırlarında **dava tarihi** esas alınır. 

### Adım 6 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Değerlendirme: [dilekçe türü] — [dosya / taraf] — [tarih]
[3-5 cümle: bu dilekçe neden ve hangi aşamada; en büyük risk; hangi bilgi eksik]

### Süre tablosu
| İşlem | Başlangıç (tebliğ/olay) | Süre ve dayanak | Son gün | Durum |
|---|---|---|---|---|

### Harç / masraf (varsa)
[araç sonucu + [doğrula]]

### Eksik bilgi
[[___] bırakılan her alan için tek satır soru]

---

## DİLEKÇE METNİ
[referans dosyasındaki iskelet: mahkeme başlığı, esas no, taraflar, vekil, konu, açıklamalar (numaralı), hukuki sebepler, deliller, sonuç ve istem, tarih, imza, ekler]

---
**Kaynaklar (dilekçeden çıkarılacak iç not):** [her atıf için soorgla etiketi]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

- Dilekçe metninin içinde iç anlatım ("şu aracı kullandım") ve kaynak etiketi bulunmaz; etiketler alttaki iç notta toplanır (ORTAK-KURALLAR.md §8).
- Mahkemeye hitap ve taraf bloğu büyük harfle; açıklamalar numaralı; her vakıanın yanında dayandığı delil (HMK m.119/1-f, m.194/2). 
- **Word (docx) çıktısı:** kullanıcı Word belgesi isterse ortamda bir docx becerisi ya da aracı varsa onunla üretmesini söyle (ör. `anthropic-skills:docx`). Eski sistemdeki `.docx` şablonları yoktur; şablon arama, uydurma.

### Adım 7 — Sunma / gönderme kapısı
Dilekçe, arabuluculuk başvurusu ya da ihtarname **avukat onayı olmadan sunulmaz, gönderilmez.** Kullanıcı avukat değilse ORTAK-KURALLAR.md §1 kapısını uygula; avukatsa bile çıktıya "TASLAK — avukat incelemesi bekliyor" işaretini koy, "UYAP'a yüklenebilir / gönderilebilir" yazma. Kullanıcı açıkça "inceledim, onaylıyorum" demeden işaret kalkmaz.

---

## Ortak dilekçe kuralları

- **Somutlaştırma:** her vakıa ispata elverişli şekilde somut; her delilin hangi vakıa için gösterildiği yazılı (HMK m.194). Genel "her türlü delil" ibaresi yetmez; yine de sonuna eklenebilir.
- **Belgeler:** elde olan belgeler dilekçeye eklenir; başka yerden getirtilecekler için bulunmasını sağlayacak açıklama (kurum, tarih, sayı) yazılır (HMK m.121). 
- **Talep sonucu açık:** ne istendiği, tutar, faiz türü ve başlangıcı, yargılama gideri ve vekâlet ücreti. Karşı vekâlet ücretinin tarife tutarı gerekiyorsa (masraf bilgisi, sulh hesabı, ıslah sonrası) `legal_calculate_attorney_fee`; araç yanıt vermezse ya da hata dönerse tutar yazma, `[___]` bırak ya da `hesaplamalar/references/harc.md` yolunu izle.
- **İçtihat alıntısı:** yalnız tam metni okunmuş kararın gerekçesinden; tırnak içindeki her cümle kelimesi kelimesine. Okunmamış kararı "Yargıtay … kararında da vurgulandığı üzere" kalıbıyla yazma (eski YAML'ın önerdiği kalıp budur; doğrulanmamış atıf için kullanılmaz).
- **Zayıf argüman açıklığı:** bir iddia hukuken zayıfsa avukata söyle: "(a) yine ileri sür, (b) çıkar, (c) terditli/ikincil talep yap `[incele]`".

---

## İş akışı becerilerine bağlantı

Usul ve dilekçe metni bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Uzun ya da çok belgeli dosya** (bilirkişi raporu, dosya evrakı, uzun sözleşme): okuma [uzun belge protokolüyle](../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md).
- **Kronoloji / unsur-delil tablosu:** dava dilekçesinin açıklamalar bölümü ve bilirkişi raporuna itiraz için olay anlatımı → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).
- **Hesap araçları** (süre kodları ve harç türleri): araç kullanımı ve bilinen eksikler → [hesaplamalar/sure](../hesaplamalar/references/sure.md), [hesaplamalar/harc](../hesaplamalar/references/harc.md); tutarlar araçtan çekilir.

## Bu beceri ne yapmaz

- Davanın kazanılıp kazanılmayacağını söylemez; esas değerlendirmesi alan becerisindedir.
- Süreyi, harcı, parasal sınırı ezberden yazmaz; çeker ya da `[doğrula]` der.
- Taraf, dosya, tarih, tutar uydurmaz.
- Dilekçeyi UYAP'a yüklemez, noterden ihtarname çekmez, arabuluculuk bürosuna başvurmaz.

---

