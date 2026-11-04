# Önalım (şufa) hakkı

## Ne zaman kullanılır
- "Kardeşim hissesini yabancıya sattı, haberim yok", "önalım davası açmak istiyorum, süre ne?", "önalım bedelini ne kadar yatıracağım?", "aldığım hisse için önalım davası açıldı".
- Sözleşmeden doğan önalım, alım ve geri alım haklarının tapu şerhi ve kullanımı (kısa).
- **Yönlendirmeler:** 6306 kapsamında Başkanlığın önalım hakkı → `kentsel-donusum-ozel-hukuk.md`; sözleşme metni → `../../sozlesme-incelemesi-tbk/references/satis-trampa-bagislama.md`; kamu taşınmazı satışı (2886) → `../../kamu-ihale/references/devlet-ihale-2886.md`.

---

## Hukuki çerçeve — 7571 sonrası (RG 25.12.2025)

| Konu | Kural | Dayanak |
|---|---|---|
| Hak sahibi | Paylı mülkiyette bir paydaş taşınmaz üzerindeki payını tamamen ya da kısmen **üçüncü kişiye satarsa** diğer paydaşlar önalım hakkını kullanabilir | TMK m.732  |
| Kullanılamayacağı satışlar | **2886 sayılı Kanun kapsamındaki satışlar** ile cebrî artırmayla satışlar (2886 ibaresi 7571 ile eklendi) | TMK m.733/1  |
| Feragat ve vazgeçme | Önalımdan feragat resmî şekil ve tapuya şerh; belirli satışta vazgeçme yazılı şekil, satıştan önce ya da sonra | TMK m.733/2  |
| Bildirim | Satış alıcı ya da satıcı tarafından diğer paydaşlara **noter aracılığıyla** bildirilir | TMK m.733/3  |
| Hak düşürücü süre | Bildirimden itibaren **üç ay**, her hâlde satıştan itibaren **bir yıl** (7571 öncesi iki yıl) | TMK m.733/4  |
| Geçiş (süre) | 733'teki değişiklikler 25.12.2025'ten **önce yapılmış satışlara uygulanmaz**; onlarda eski metin (iki yıl, 2886 istisnası yok) | TMK geçici m.1/1 (7571 m.37)  |
| Kullanma | Alıcıya karşı dava açılarak | TMK m.734/1  |
| Bedel | Dava konusu payın **rayiç bedeli** hâkimce gecikmeksizin belirlenir; hak sahibi rayiç bedel + alıcıya düşen tapu giderlerini, hâkimin belirlediği yere, verilen **kesin süre** içinde nakden yatırır; yatırmazsa tescile karar verilemez; bedel kesinleşmede nemasıyla ödenir (eski metinde tapuda gösterilen satış bedeli esastı) | TMK m.734/2 (7571 m.36)  |
| Geçiş (bedel) | 734'teki değişiklik 25.12.2025'ten önce **açılmış davalara da** uygulanır | TMK geçici m.1/2  |
| Görev, yetki, daire | Taşınmazın bulunduğu yer (HMK m.12); temyiz 2026/1'e göre 7. HD |  |

**Rayiç bedelin hangi tarihe göre belirleneceği** kanunda yazılı değil. 7. HD çoğunluğu (2026): 7571 s. Kanun'un yürürlüğünden (25.12.2025) **sonra açılan** davalarda **dava tarihi**, o tarihte **derdest** davalarda **25.12.2025** esas alınır. Gerekçede karşı oy: her iki durumda da **satış tarihi** esas alınmalı. Kararlar "gerekçede oy çokluğu" ile verildi; çalışma anında `legal_search_cases` (7. HD, 2026 sonrası) ile yaklaşımın sürüp sürmediğini kontrol et `[incele]`.  

---

## Kontrol listesi

1. **Satış tarihi** 25.12.2025'ten önce mi sonra mı? Süre ve 2886 istisnası buna göre (geçici m.1/1). Bedel kuralı her durumda yeni metin (geçici m.1/2).
2. **Satış türü:** üçüncü kişiye mi (paydaşa satışta önalım yok `[doğrula]`), satış mı (bağış, trampa, ölünceye kadar bakma görünümünde muvazaalı satış iddiası `[incele]`), cebrî artırma ya da 2886 satışı mı?
3. **Bildirim:** noter aracılığıyla mı yapıldı; bildirimde satış koşulları açık mı? Usulsüz bildirim üç aylık süreyi başlatmayabilir `[incele]`.
4. **Süre:** bildirimden üç ay; her hâlde satıştan bir yıl (eski satışta iki yıl). 🔴 Son gün yakınsa önce davayı aç.
5. **Feragat/vazgeçme:** resmî şekilde ve şerhli feragat ya da yazılı vazgeçme var mı?
6. **Bedel ve depo:** bilirkişiyle rayiç bedel; kesin süre içinde nakden depo — kaçırılırsa tescil kararı verilemez 🔴. Müvekkilin nakit gücünü baştan sor.
7. **Hasım:** alıcı (zincirleme satışta son alıcı ve aradakiler `[incele]`).
8. **Kısmi kullanım:** birden çok paydaş varsa hak paylaşımı `[doğrula]`.

---

## Süre tablosu

| İşlem | Başlangıç | Süre | Dayanak |
|---|---|---|---|
| Önalım davası (25.12.2025 ve sonrası satış) | Noter bildirimi / satış | Üç ay / her hâlde bir yıl | TMK m.733/4 |
| Önalım davası (25.12.2025 öncesi satış) | Noter bildirimi / satış | Üç ay / her hâlde iki yıl | TMK geçici m.1/1; eski m.733/4 |
| Bedelin depo edilmesi | Hâkimin ara kararı | Hâkimin verdiği kesin süre | TMK m.734/2 |
| İstinaf/temyiz | Tebliğ | `hmk_appeal` / `hmk_cassation` | HMK |

`legal_calculate_deadline` önalım süresini tanımıyor (`tmk_onalim` → "Kural bulunamadı"); elle hesapla, `legal_check_holiday`, `[doğrula]`. 

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Satışın tarihi ve yevmiyesi; tapudaki bedel? | Süre, geçiş |
| Noter bildirimi geldi mi, ne zaman tebliğ edildi? | Üç aylık süre |
| Alıcı kim (paydaş mı, üçüncü kişi mi)? Zincirleme satış var mı? | Hak, hasım |
| Daha önce önalımdan feragat ya da vazgeçme yazısı imzaladınız mı? | Engel |
| Rayiç bedeli kesin süre içinde nakden yatırabilir misiniz? | Davanın akıbeti |

---

## İdare tarafı

- Hazine/belediye 2886 kapsamında pay satıyorsa (25.12.2025 sonrası satış) paydaşların önalım hakkı yok; satış ilanında ve sözleşmede bunu belirt. Eski satışlar için geçiş hükmü `[incele]`.
- 6306'da Başkanlığın kanuni önalım hakkı ayrı bir rejimdir → `kentsel-donusum-ozel-hukuk.md`.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4721"  law_type: "Kanun"  article_no: "732" | "733" | "734" | "735" | "736"
legal_list_statute_articles  law_no: "4721"  law_type: "Kanun"  article_kind: "gecici"  include_content: true   # geçici m.1 (7571)
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2025/12/20251225-33.htm"  offset: 36000   # 7571 m.35-37
legal_search_cases  mahkeme: "yargitay"  daire: "7. Hukuk Dairesi"  tarih_baslangic: "2025-12-25"
    sorgu: "<ör. 7571 sonrası önalım davasında rayiç bedelin belirlenmesi ve kesin süre içinde depo>"
legal_get_case_document  belge_id: "<seçilen>"
```

---

## Çıktı iskeleti

```markdown
## Önalım değerlendirmesi — [ada/parsel] — [satış tarihi]
### Sonuç
### Uygulanacak metin: eski / yeni (geçici m.1)
### Süre tablosu
### Bedel: rayiç bedel tahmini (bilirkişi), tapu giderleri, nakit planı
### Riskler (bildirim usulü, muvazaa iddiası, feragat)
```

---

## Sık hatalar

- 🔴 25.12.2025 sonrası satışta "iki yıl" sürecine güvenmek.
- 🔴 Bedeli tapudaki satış bedeli sanıp nakit planı yapmamak; kesin süreyi kaçırmak.
- 🟠 2886 satışında önalım davası açmak (yeni metin) ya da eski satışta 2886 istisnasını uygulamak.
- 🟠 Kat irtifakı/kat mülkiyeti kurulmuş bağımsız bölüm satışında önalım aramak `[doğrula]`.

---

