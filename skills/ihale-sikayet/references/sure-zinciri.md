# Süre zinciri: şikâyetten Danıştay temyizine

Her halkanın başlangıç olayı, süresi, süre kodu ve dayanağı. İki rol aynı tabloyu kullanır: istekli "son gün"ü,
idare "karar ve bildirim" sürelerini ve **sözleşme imza yasağını** izler.

Kaynak: 4734 m.54–57, 65; 12766 m.6, 7, 13, 18; 2577 m.8, 20/A, 45/8, 61–62 — hepsi `legal_get_statute_article` /
`legal_list_statute_articles` ile 2026-11-01'de çekildi `[soorgla]`. Süre kodlarının canlı durumu §3'te.

---

## 1. Zincir tablosu

| # | Halka | Kim | Başlangıç olayı (izleyen günden sayılır) | Süre | Kod | Dayanak |
|---|---|---|---|---|---|---|
| 1 | İlan / doküman şikâyeti | istekli olabilecek | İlana **ve dokümanın ilana yansıyan hükümlerine**: **ilk ilan** tarihi. Dokümanın ilana yansımayan hükümlerine: dokümanın **EKAP hesabına giriş yapılarak indirildiği** tarih. Zeyilnameye: zeyilnamenin **bildirildiği** tarih | 10 gün (21/b-c: 5) **ve** en geç ihale / son başvuru tarihinden **3 iş günü** önce — hangisi önce dolarsa | `kik_complaint_before_tender` (yalnız 10 gün; 3 iş günü elle) | 4734 m.55/1-2; 12766 m.6/2, m.7/1-a,b |
| 1a | Açıklama talebi (şikâyet değildir) | istekli olabilecek | İhale / son başvuru tarihi (geriye doğru) | İhaleden **20 gün** öncesine kadar yazılı; idare cevabı en az 10 gün önce. **Halka 1'in süresini durdurmaz, uzatmaz** | — (kod yok, elle) | 4734 m.29, m.50 (danışmanlık); 12916 m.27/3 |
| 2 | İhale sürecine / sonuca şikâyet | aday, istekli | İşlem/eylemin **farkına varıldığı veya varılmış olması gereken** tarih (çoğu olayda kesinleşen ihale kararının bildirimi; her zaman değil `[incele]`) | 10 gün; 21/b-c: **5 gün**; her durumda sözleşme imzalanmadan önce | `kik_complaint`, `kik_complaint_21bc` | m.55/1; 12766 m.6/1, m.7/1-c |
| 3 | İdarenin kararı | idare | Şikâyetin idare kaydına girişi | **10 gün** gerekçeli karar; ilan/doküman şikâyeti ihaleden önce sonuçlandırılır (esas) | `kik_complaint_decision` | m.55/3; 12766 m.10/3 |
| 4 | Kararın bildirimi | idare | Karar tarihi | **3 gün**; şikâyetçi + aday/istekliler; ilan/doküman şikâyetinde istekli olabileceklere de | `kik_complaint_decision_notice` | m.55/3; 12766 m.13/1 |
| 5a | İtirazen şikâyet (karar var) | başvuru sahibi dahil aday, istekli, istekli olabilecek | İdare kararının **bildirimi** | 10 gün (21/b-c'de de 10) | `kik_objection` | m.55/4; 12766 m.6/3, m.7/1-ç |
| 5b | İtirazen şikâyet (karar yok) | **yalnız** şikâyet sahibi | 10 günlük karar süresinin **bitimi** | 10 gün | `kik_objection_no_decision` | m.55/4 |
| 5c | İptal kararına karşı | aday, istekli | Şikâyet / itirazen şikâyet üzerine alınan **iptal kararının bildirimi** | **5 gün**, doğrudan Kuruma | `kik_objection_cancellation` | m.56/1; 12766 m.4/3-b,c, m.6/3 |
| 5d | İdarenin **kendiliğinden** iptaline karşı | aday, istekli | İptal kararının **bildirimi** | KİK yolu yok → **30 gün** doğrudan dava; şikâyet süreyi durdurmaz | `kik_lawsuit` (başlangıç = iptal bildirimi) | m.56/1; 2577 m.20/A-2(a),(b); KİK 2026/UM.IV-952 |
| 6 | Kurul kararı | Kurum | İhale işlem dosyası ve gerekli bilgi-belgenin **Kurum kaydına alınması** | 20 gün; 21/b-c ve iptal kararına karşı başvuruda **10 iş günü** | `kik_board_decision`, `kik_board_decision_short` | m.56/5; 12766 m.18/5 |
| 7 | Kurul kararının bildirimi ve yayını | Kurum | Karar tarihi | **5 iş günü** içinde tebligata çıkarma; sonraki 5 gün içinde internette yayın | `kik_board_decision_notice` | m.56 (tebligat fıkrası); 12766 m.24/1 |
| 8 | Bedel iadesi talebi | başvuru sahibi | Kurul kararının bildirimi | **30 gün** içinde yazılı talep; Kurum talepten itibaren 15 gün içinde öder | — (kod yok) | 4734 m.53/j 4. paragraf (7571/11) — süre Kanunda; 12766 m.18/A iade usulünü düzenler, süre koymaz |
| 9 | Dava | istekli **ya da** idare `[incele]` | Kurul kararının **tebliği** | **30 gün** (ivedi); İYUK m.11 uygulanmaz | `kik_lawsuit` | 4734 m.57; 2577 m.20/A-2(a,b) |
| 10 | İlk inceleme ve tebliğ | mahkeme | Dava açılması | 7 gün | — | 20/A-2(c) |
| 11 | Savunma | davalı (Kurum) | Dava dilekçesinin tebliği | 15 gün + bir kez en çok 15 gün | `kik_lawsuit_defense` | 20/A-2(d) |
| 12 | Karar | mahkeme | Dosyanın tekemmülü (savunma ya da süresi) | En geç 1 ay; YD kararına **itiraz yok** | — | 20/A-2(e,f) |
| 13 | Temyiz | taraflar | Nihai kararın **tebliği** | **15 gün**, doğrudan Danıştay; **istinaf yok** | `kik_lawsuit_cassation` | 20/A-2(g); 2577 m.45/8 |
| 14 | Temyize cevap | karşı taraf | Temyiz dilekçesinin tebliği | 15 gün | `kik_lawsuit_cassation_response` | 20/A-2(ı) |
| 15 | Danıştay kararı | Danıştay | — | 2 ay içinde karar, 1 ay içinde tebliğ; karar **kesin** | — | 20/A-2(i,j) |
| 16 | Kararın uygulanması | idare / Kurum | Kurul kararı; mahkeme kararı üzerine Kurul kararı (MK) | **İvedilikle**; MK kararı da 5 iş günü içinde bildirime çıkar | — | m.56 son fıkra; 12766 m.23, m.24/1 |

**Halka 1 — ilana yansıyan hususlar (🔴 ilk ilan tarihini mutlaka sor).** 4734 m.55/1: "İlanda yer alan hususlara
yönelik başvuruların süresi ilk ilan tarihinden, ön yeterlik veya ihale dokümanının ilana yansımayan diğer
hükümlerine yönelik başvuruların süresi ise dokümanın satın alındığı tarihte başlar" `[soorgla]`. İlanda zorunlu yer
alan ve bu yüzden süresi **ilk ilandan** işleyen tipik hususlar: iş deneyimi oranı ve süresi, **benzer iş** tanımı,
ekonomik-mali ve mesleki-teknik **yeterlik kriterleri**, kalite/standart belgeleri, fiyat dışı unsurlar, aşırı düşük
teklif seçeneği ve (yapımda) N katsayısı, kısmi teklif ve konsorsiyum durumu — her dosyada ilan metniyle karşılaştır
`[incele]`. İlk ilan, doküman indirme tarihinden 10 günden fazla önce yayımlandıysa bu iddiaların süresi indirmeden
önce dolmuş olabilir. Bir dosyada hem ilana yansıyan hem yansımayan iddia varsa **iki ayrı son gün** hesapla; düzeltme ilanı
varsa düzeltilen husus için başlangıç `[incele]`. İki sınırdan da (ilk ilan/indirme + 10 gün; ihaleden 3 iş günü
önce) erken olan son gündür.

**Halka 1a — açıklama talebi.** Açıklama talebi ile şikâyet iki ayrı yoldur; açıklama talebi şikâyetin ön şartı
değildir ve m.55'te açıklama talebine bağlı bir durma ya da uzama hükmü yoktur `[soorgla]`. Cevap ihaleden 10 gün
öncesine kadar gelebilir; bu tarih çoğu dosyada halka 1'in son gününden sonradır. Aykırılık iddiasında şikâyet süresinde
verilir, açıklama talebi paralel yapılır; çıktıda iki son gün **birlikte** gösterilir.

**Sözleşme imza yasağı (idare için 🔴):** şikâyet varsa, karar son bildiriminden (karar yoksa karar süresinin
bitiminden) itibaren **10 gün geçmeden** ve Kurum internet sayfasından **itirazen şikâyet sorgulaması yapılmadan**;
itirazen şikâyet varsa **nihai Kurul kararı verilmeden** sözleşme imzalanamaz (m.55 son fıkra; 12766 m.13/2)
`[soorgla]`. Kesinleşen ihale kararı sonrası genel bekleme süresi (m.41, `kik_standstill`) ayrıca işler → tür becerisi.

## 2. Hesap kuralları

- **Olay günü sayılmaz;** süre izleyen gün başlar (12766 m.7; 2577 m.8/1) `[soorgla]`.
- "Gün" takvim günüdür; **"iş günü"** yalnız doküman şikâyetindeki 3 iş günü sınırı, Kurul'un 10 iş günü süresi ve
  5 iş günü tebligat süresidir. Yönetmelikte iş günü: ulusal bayram, genel tatil ve hafta tatili dışındaki günler;
  **idari izin günleri iş günü sayılır** (12766 m.3/1-c) `[soorgla]`.
- Tatil günleri süreye dahildir; son gün tatile rastlarsa izleyen ilk iş gününün bitimine uzar — **ama doküman ve
  ilan şikâyetinde 3 iş günü öncesi sınırı uzamaz** (12766 m.7/2; dava ve temyizde 2577 m.8/2) `[soorgla]`.
- **Başvuru tarihi = kayda giriş tarihi.** Yanlış merciye verilip oradan gönderilen dilekçede idare/Kurum kaydına
  giriş tarihi esastır (m.54) `[soorgla]`. Başvurular **EKAP üzerinden e-imzayla** yapılmak zorunda (12766 ek m.1)
  `[soorgla]`; son gün EKAP kesintisi riskine karşı iç hedefi bir iş günü erken koy.
- **Tebligat:** EKAP üzerinden ya da elektronik yapılan bildirimde bildirim tarihi tebliğ tarihidir (4734 m.65/b)
  `[soorgla]`. İadeli taahhütlü mektupla tebligat varsayımı için m.65/a metninde kesik bölüm var `[doğrula]`.
  
- **Aynı mahiyette ikinci şikâyet süreyi yeniden başlatmaz** (12766 m.14/2) `[soorgla]`.
- Şikâyet üzerine alınan idare kararıyla **yeni** bir zarara uğradığını iddia eden, bu konuda doğrudan Kuruma
  itirazen şikâyette bulunur (12766 m.14/3) `[soorgla]`; süre o kararın bildiriminden.

### İvedi usulde adli tatil (İYUK m.8/3) — `[doğrula]`

- Metin: "Bu Kanunda yazılı sürelerin bitmesi çalışmaya ara verme zamanına rastlarsa … yedi gün uzamış sayılır"
  (2577 m.8/3) `[soorgla]`. 20/A'daki 30 ve 15 günlük süreler de "bu Kanunda yazılı" sürelerdir; metinde ivedi usul
  için istisna yok.
- Öte yandan nöbetçi mahkeme "kanunen belli süre içinde karara bağlanması gereken işler"e bakar (2577 m.62/b)
  `[soorgla]`; ivedi davalar ara verme döneminde görülebilir. Uzatmanın ivedi davalarda uygulanıp uygulanmadığına
  ilişkin Danıştay kararı bu turda bulunamadı (`legal_search_cases` danistay, 2026-11-01).
- **Kural:** 20 Temmuz–31 Ağustos arasında biten dava ve temyiz süresinde **uzatmasız son günü** esas al. Araç
  (`kik_lawsuit`) uzatma uygular ama "GÜVENLİ SON GÜN (uzatmasız)" satırını da verir — o satır son gündür.

## 3. Süre kodlarının canlı durumu (2026-11-03)

Süre kodu SQL'i 2026-11-02'de canlıya alındı. 

| Kod | Durum | Ne yap |
|---|---|---|
| `kik_complaint` | Canlı: 10 gün, adli tatil yok | 21/b-c ise `kik_complaint_21bc` |
| `kik_complaint_21bc` | Canlı: 5 gün | — |
| `kik_complaint_before_tender` | Canlı: 10 gün (düzeltildi) | Araç **yalnız 10 günü** hesaplar. İhale ya da son başvuru tarihinden geriye 3 iş günü sınırını ayrıca `legal_check_holiday` ile say; erken olan son gündür 🔴 |
| `kik_complaint_decision`, `kik_complaint_decision_notice`, `kik_objection`, `kik_objection_no_decision`, `kik_objection_cancellation`, `kik_board_decision`, `kik_board_decision_short`, `kik_board_decision_notice` | Canlı | Yanıttaki `kural_adi`'yi halkayla karşılaştır |
| `kik_lawsuit` | Canlı: 30 gün; adli tatil uzatması + güvenli gün | Güvenli günü esas al |
| `kik_lawsuit_defense`, `kik_lawsuit_cassation`, `kik_lawsuit_cassation_response` | Canlı (adli tatil bayrağı açık) | Güvenli günü esas al (§2) |
| `kik_4735_default_notice`, `kik_4735_force_majeure_notice` | Canlı (sözleşme sonrası; bu zincirin dışında) | → `hakedis` / tür becerisi |
| Bedel iadesi talebi (30 gün) | Kod yok | Elle say (4734 m.53/j) |

Araç yanıtında `kural_adi` ve `kanun_maddesi`'ni beklenen halkayla karşılaştır; uyuşmazsa sonucu kullanma.

## 4. Elle hesap örneği (yöntem)

Kesinleşen ihale kararı EKAP'ta 02.11.2026 (Pazartesi) bildirildi, açık ihale:
1. Şikâyet: 03.11 başlar → 10. gün 12.11.2026 (`kik_complaint` aynı sonucu verdi `[soorgla]`).
2. İdare kararı: şikâyet 12.11'de kayda girdiyse karar son günü 22.11 (Pazar) → `legal_check_holiday` → izleyen iş
   günü 23.11.2026 (Pazartesi); bildirim karar tarihinden 3 gün.
   
3. Karar yoksa itirazen şikâyet: karar süresinin bitiminden 10 gün (yalnız şikâyet sahibi).

Her satırın yanına gerekçe yaz: başlangıç olayı, dayanak, tatil kaydırması, araç mı elle mi.

## 5. Sık hatalar
- 🔴 Doküman şikâyetinde yalnız 10 günü saymak; 3 iş günü sınırını kaçırmak (araç bu sınırı hesaplamaz).
- 🔴 İlana yansıyan hususta (benzer iş, iş deneyimi oranı, yeterlik) süreyi doküman indirmeden saymak; doğrusu ilk ilan.
- 🔴 "Önce açıklama talebi, sonra şikâyet" sırası: açıklama talebi şikâyet süresini durdurmaz.
- 🔴 21/b-c ihalesinde şikâyete 10 gün saymak (5 gün); itirazen şikâyete 5 gün saymak (10 gün; 5 gün yalnız iptal
  kararına karşı).
- 🔴 Kurul kararına 60 gün dava süresi ya da istinaf (30 gün, istinaf yok, temyiz 15 gün).
- 🔴 (İdare) Bekleme ve sorgulama yapılmadan sözleşme imzalamak.
- 🟠 Süreyi tebliğden saymak; ölçüt farkına varmadır (bildirim çoğu zaman farkına varma tarihidir ama her zaman değil).
- 🟠 Bedel iadesinin 30 günlük talep süresini kaçırmak.
