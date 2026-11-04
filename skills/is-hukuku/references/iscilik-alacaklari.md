# İşçilik alacakları ve hesap

Kıdem, ihbar, kötüniyet, fazla çalışma, ulusal bayram ve genel tatil (UBGT), hafta tatili, yıllık izin ve ücret alacaklarının hesabı; zamanaşımı; ibraname; zorunlu arabuluculuk başvurusu.

**Kural:** hiçbir tutar (asgari ücret, kıdem tavanı, faiz oranı) bu dosyadan alınmaz. Hepsi soorgla araçlarından, fesih tarihinin dönemine göre çekilir. Her sonuç `[doğrula — bilirkişi/bordro uzmanıyla teyit edin]` taşır.

**Hesap bilirkişisi raporu geldiyse** (fazla çalışma haftalık mı, tablo ile hesap tutarlı mı, bilirkişi hukuki değerlendirme yapmış mı): denetim ve fark tablosu → `../../tazminat-haksiz-fiil/references/bilirkisi-raporu-denetimi.md` §3 ve §4.6. Yeniden hesap aracı `legal_calculate_employment_claims` (aşağıda); araç yanıt vermezse ya da hata dönerse yalnız yöntem denetimi yapılır.

### Hesap aracı: `legal_calculate_employment_claims`
**Durum:** araç yanıt vermezse, hata dönerse ya da "parametre tabloları yüklü değil" derse **tutar elle hesaplanmaz**: aşağıdaki kontrol listesiyle yöntem ve girdiler gösterilir, tablo tutar sütunu boş kalır.

Araç varsa:
- `islem: "alacaklar"` → `alacak{}`: `giris`, `cikis`, `fesih_turu` (`isveren_gecerli_neden`, `isveren_25_2`, `isveren_25_1_3_4`, `isci_hakli_24`, `isci_istifa`, `emeklilik_yas_disi`, `askerlik`, `kadin_evlilik`, `olum`, `belirli_sure_bitimi`), `son_ciplak_brut`, `aylik_duzenli_menfaatler`, `son_yil_yillik_odemeler`, `ucret_donemleri[]`, `fazla_calisma{haftalik_plan[] | haftalik_fazla_saat, gece_calismasi}`, `hafta_tatili_ayda_gun`, `ubgt_yilda_gun`, `kullanilan_izin_gun`, `dogum_tarihi`, `bordro[]` (aylık fazla mesai tahakkuku), `hakkaniyet_indirimi` (varsayılan 0 ve %30 seçenekli), `zamanasimi_basvuru_tarihi`, `net_hesapla`.
- `islem: "brutten_nete"` (ay ay brüt, aynı yıl içinde kümülatif matrah) ve `"netten_brute"` (tek ay); `kalem` kesinti kuralını seçer (kıdemde yalnız damga; ihbar ve kötüniyette SGK yok).
- Aracın verdiği **fesih türüne göre hak kazanma** bir varsayımdır; haklı/geçerli neden değerlendirmesi bu becerinin kontrol listesinde (`fesih-ve-ise-iade.md`) yapılır ve tabloya o sonuç yazılır.
- Kullanıcının bilmediği girdi uydurulmaz: ücret dönemi yoksa araç asgari ücret oranlaması yapar ve uyarır; bu uyarı tabloda "Not" sütununa taşınır.
- Aracın `uyarilar[]` listesi kısaltılmadan "Risk notları"na aktarılır.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| Yıllık izin ücreti ile kıdem, ihbar, kötüniyet ve eşit davranma ilkesine aykırı fesih tazminatı: **5 yıl** zamanaşımı | 4857 ek m.3 (a)-(d) (7036/15 ile eklendi). Milat **25.10.2017** (7036'nın RG'de yayımı); eski YAML'daki 12.10.2017 kabul tarihidir.  | Geçiş kuralı 4857 geçici m.8: ek m.3, 25.10.2017'den **sonra sona eren** sözleşmelerden doğan izin ücreti ve tazminatlara uygulanır. Daha önce sona erenlerde TBK m.146 (10 yıl) işlemeye devam eder; ancak kalan süre 5 yıldan uzunsa 25.10.2017'den itibaren 5 yılın geçmesiyle zamanaşımı dolar.  |
| Ücret, fazla çalışma, UBGT, hafta tatili alacakları: **5 yıl** | TBK m.147/1 ("ücret gibi diğer dönemsel edimler"); dayanak ek m.3 değil  | Her ayın alacağı kendi muacceliyetinden işler. |
| Zamanaşımı iş sözleşmesi devam ederken **da işler** | TBK m.153 durma sebeplerini sayar; hizmet ilişkisi süresince durma yalnız **ev hizmetlilerinin** çalıştıranlardan alacakları için öngörülmüş (m.153/4)  | Dönemsel ücret alacaklarında her ayın alacağı kendi muacceliyetinden işler (yukarıdaki satır). |
| İbraname geçerliliği: sözleşmenin sona ermesinden itibaren **1 ay** geçmeden yapılan ibra kesin hükümsüz | TBK m.420/2  | Ayrıntı: `fesih-oncesi-kontrol.md` §5. |
| Zorunlu arabuluculuk (dava şartı) | 7036 m.3/1; 7445 ile (28.3.2023) bu alacaklara ilişkin itirazın iptali, menfi tespit ve istirdat davaları da kapsamda  | Başvurmadan açılan dava usulden reddedilir; son tutanak eklenmemişse 1 haftalık kesin süre verilir (m.3/2). İş kazası ve meslek hastalığı tazminatı ile bunlarla ilgili tespit ve rücu davalarında arabuluculuk şartı **yoktur** (m.3/3). m.3/15, AYM'nin 03.06.2025 t. E.2024/157 K.2025/121 kararıyla iptal edildi.  |

---

## Kontrol listesi

### 1. Ücret türü (en kritik ayrım)
- **Giydirilmiş brüt ücret:** kıdem ve ihbar tazminatında kullanılır — çıplak brüt ücrete düzenli ödenen yemek, yol, ikramiye, yakacak vb. eklenir. 
- **Çıplak brüt ücret:** fazla çalışma, UBGT, hafta tatili ve yıllık izin ücretinde kullanılır.
- Ücret belirsizse: emsal ücret araştırması (meslek kuruluşu, SGK kaydı), en azından asgari ücret → `legal_get_social_parameters tur: "asgari_ucret_brut"`.
- Not: Eski görev tanımında "AGİ" geçiyordu; asgari geçim indirimi kaldırıldı, yerine asgari ücret istisnası geldi. AGİ'yi hesaba katma. 

### 2. Kıdem tazminatı (1475 m.14)
- Şartlar: en az 1 yıl kıdem + tazminata hak kazandıran sona erme hali: işveren feshi (ahlak ve iyiniyet kurallarına uymayan hâller dışında), işçinin haklı feshi, muvazzaf askerlik, yaşlılık, emeklilik ya da malullük aylığı veya toptan ödeme için ayrılma, yaş dışındaki sigortalılık süresi ve prim günü şartlarını tamamlayıp kendi isteğiyle ayrılma, kadın işçinin evlilikten itibaren 1 yıl içinde ayrılması, ölüm. 
- Hesap: her tam yıl için 30 günlük giydirilmiş brüt ücret; artan süre orantılı.
- **Tavan:** dayanağı memur maaş katsayısı değil, en yüksek devlet memuruna 5434'e göre bir hizmet yılı için ödenecek azami emeklilik ikramiyesidir.  Tutarı `legal_get_social_parameters tur: "kidem_tazminati_tavani"` ile çek. Araç şu an yalnız güncel dönemi döndürüyor; fesih tarihi başka döneme düşüyorsa bunu açıkça yaz, tavanı kullanıcıdan ya da `legal_search_official_gazette` ile ilgili mali haklar genelgesinden iste `[doğrula]`. Giydirilmiş ücret tavanı aşıyorsa tavan esas alınır.
- Kesinti: yalnızca damga vergisi (gelir vergisinden istisna); damga vergisinin dayanağı 488 sayılı Kanuna ekli (1) sayılı tablo IV-1-b, oranı her seferinde tablodan çek `[incele]`. 
- **Faiz:** fesih tarihinden itibaren mevduata uygulanan en yüksek faiz (1475 m.14/11). Bu oran soorgla'da yok → kullanıcıdan banka oranı iste ya da `[doğrula]` bırak. 

### 3. İhbar tazminatı (4857 m.17)
- Bildirim süreleri kıdeme göre: 6 aydan az → 2 hafta; 6 ay–1,5 yıl → 4 hafta; 1,5–3 yıl → 6 hafta; 3 yıldan fazla → 8 hafta. Süreler asgaridir, sözleşmeyle artırılabilir. 
- Giydirilmiş brüt ücret × bildirim süresi. Gelir ve damga vergisi kesilir `[doğrula]`.
- Faiz: yasal faiz ya da temerrüt faizi → `legal_get_legal_interest_rates`.

### 4. Kötüniyet tazminatı (4857 m.17/6)
- İş güvencesi kapsamı dışındaki işçi için; fesih hakkının kötüye kullanılmasında bildirim süresinin 3 katı. Bildirim şartına da uyulmadıysa ayrıca ihbar tazminatı. 

### 5. Fazla çalışma (4857 m.41)
- Haftalık 45 saati aşan çalışma; saat ücretinin %50 fazlası. Yıllık üst sınır 270 saat. 
- Fazla sürelerle çalışma (haftalık 45 saatin altında kalan sözleşmelerde) %25 `[doğrula]`.
- **İspat:** imzalı bordroda fazla çalışma tahakkuku varsa ve işçi ihtirazi kayıtsız imzaladıysa, bordrodakinden fazla çalışma **yalnız yazılı belgeyle** ispatlanabilir (tanık yetmez); ihtirazi kayıt varsa her türlü delil serbesttir. Bordro imzalatılmadan değişken tutarlar bankadan ödenmişse işçiden ihtirazi kayıt beklenmez, her türlü delille ispat mümkündür. 
- **Hakkaniyet indirimi:** fazla çalışma yalnızca tanıkla ispatlanıyorsa 9. HD takdiri bir indirim uygular. Bu kanuni bir oran değil, içtihattır: yerleşik uygulamada indirim %30 ile sınırlı tutulur, daha yüksek oran hakkın özüne dokunduğu için bozma sebebi sayılır. Müvekkile risk olarak bildir; güncel kararı her seferinde çek. 
- Ücretine fazla mesai dahil edilmiş sözleşme: yıllık 270 saatle sınırlı geçerlilik `[incele]`.

### 6. UBGT ve hafta tatili
- UBGT günü çalışılırsa ilave bir günlük ücret (4857 m.47). 
- Hafta tatili: 7 günlük dönemde kesintisiz 24 saat dinlenme (m.46). m.46 2025'te değişti (7553: turizm işletme belgeli konaklama tesislerinde işçinin yazılı talebi ya da onayıyla, hak kazandığı günü izleyen dört gün içinde kullandırma; onay 30 gün önceden yazılı bildirimle geri alınabilir); maddeyi her seferinde çek. 
- Çıplak ücretle hesapla.

### 7. Yıllık izin ücreti (4857 m.53-59)
- İzin süreleri kıdeme göre: 1-5 yıl (5 dahil) → 14 gün; 5 yıldan fazla 15 yıldan az → 20 gün; 15 yıl (dahil) ve üstü → 26 gün; yer altı işlerinde dörder gün fazlası; 18 ve daha küçük yaştakiler ile 50 ve daha büyük yaştakiler en az 20 gün. 
- Kullanılmayan izin sözleşme sona erince son ücret üzerinden ödenir (m.59). İspat yükü işverende (imzalı izin defteri) `[doğrula]`.

### 8. İbraname ve ödeme belgeleri
- TBK m.420 şartlarını kontrol et: yazılı, sona ermeden 1 ay sonra, alacak türü ve miktarı açık, ödeme banka aracılığıyla ve gerçek miktarda.
- Bordro imzalı mı, banka kayıtları ile uyumlu mu?

### 9. Faiz türleri
- Kıdem → en yüksek mevduat faizi (fesihten itibaren).
- Diğer alacaklar → yasal faiz ya da (ticari iş varsayımı yoksa) temerrüt faizi; temerrüt tarihi (ihtar, arabuluculuk başvurusu, dava) `[incele]`.
- Oranlar → `legal_get_legal_interest_rates`.

---

## soorgla çağrıları

```
legal_get_social_parameters  tur: "kidem_tazminati_tavani"      # fesih tarihinin dönemine bak
legal_get_social_parameters  tur: "asgari_ucret_brut" | "asgari_ucret_net"
legal_get_legal_interest_rates
legal_get_statute_article  law_no: "1475"  article_no: "14"
legal_get_statute_article  law_no: "4857"  article_no: "17" | "41" | "46" | "47" | "53" | "59" | "ek 3"
legal_get_statute_article  law_no: "6098"  article_no: "420" | "147"
legal_get_statute_article  law_no: "7036"  article_no: "3"
legal_search_cases  mahkeme: "yargitay"  daire: "9. Hukuk Dairesi"
    sorgu: "<ör. fazla çalışmanın yalnızca tanık beyanıyla ispatı hakkaniyet indirimi>"
legal_search_cases  mahkeme: "yargitay"  daire: "22. Hukuk Dairesi"  tarih_bitis: "2020-09-02"   # kapatılan daire, eski emsal
legal_search_cases  mahkeme: "bam"  sorgu: "<olay>"                      # hakkaniyet indirimi uygulaması
legal_calculate_employment_claims  islem: "alacaklar" | "brutten_nete" | "netten_brute"
legal_calculate_court_fee                                               # dava harcı
legal_get_social_parameters  tur: "harc_arabuluculuk_karar"
legal_calculate_cpi_change                                              # gerekirse güncelleme
```
Eski profildeki `mevzuat_turu: tebliğ` (kıdem tavanı tebliğleri) → tavan artık doğrudan `legal_get_social_parameters`'tan gelir; dayanak genelge `aciklama` alanında yazar.

---

## Görüşme soruları

1. Kimin adına? (işçi / işveren)
2. İşe giriş ve çıkış tarihleri; çıkışın şekli ve nedeni (kim feshetti, hangi gerekçeyle)?
3. Son brüt ücret; düzenli ek ödemeler (yemek, yol, ikramiye, prim, yakacak) ve tutarları?
4. Haftalık çalışma düzeni (günler, giriş-çıkış saatleri, ara dinlenmesi)?
5. UBGT günlerinde çalışma oldu mu?
6. Kullanılan yıllık izinler; izin defteri imzalı mı?
7. Bordrolar imzalı mı, fazla mesai tahakkuku var mı, ihtirazi kayıt var mı?
8. Ödemeler banka ile mi, elden mi?
9. İbraname imzalandı mı, tarihi ve içeriği?
10. Arabulucuya başvuruldu mu?
11. Tanıklar (aynı dönemde çalışmış, bordro kaydı olan)?

## Çıktı iskeleti — alacak hesap tablosu

```markdown
## İşçilik alacakları hesabı: [işçi] — [tarih]
**Giriş:** … · **Çıkış:** … · **Kıdem:** … yıl … ay … gün · **Fesih şekli:** …
**Çıplak brüt ücret:** … `[kullanıcı verdi]` · **Giydirilmiş brüt ücret:** … (kalemler: …)
**Kıdem tavanı (dönem):** … `[soorgla]`

**Hesap:** `legal_calculate_employment_claims` ✓ | araç yok — yalnız yöntem (tutar sütunları boş)

| Kalem | Formül | Girdiler | Brüt — indirimsiz | Brüt — %__ indirimli | Net (bilgi) | Zamanaşımı | Faiz türü ve başlangıcı | Not |
|---|---|---|---|---|---|---|---|---|
| Kıdem | min(giydirilmiş, tavan) × gün / 365 | gün, giydirilmiş, tavan dönemi | | — | | 5 yıl | en yüksek mevduat, fesihten | tavan uygulandı mı |
| İhbar | giydirilmiş günlük × 7 × hafta | hafta | | — | | 5 yıl | yasal, temerrütten | |
| Kötüniyet | ihbarın 3 katı | | | — | | 5 yıl | yasal | iş güvencesi dışı |
| Fazla çalışma | çıplak / 225 × 1,5 × haftalık saat × hafta | haftalık plan, dönem | | | | aylık, 5 yıl | yasal | bordro mahsubu, tanık [incele] |
| Hafta tatili | günlük × 1,5 × gün | ayda gün | | | | aylık, 5 yıl | yasal | |
| UBGT | günlük × gün | yılda gün | | | | aylık, 5 yıl | yasal | |
| Yıllık izin | son çıplak günlük × kullanılmayan gün | hak / kullanılan gün | | — | | sona ermeden 5 yıl | yasal | |

**Toplam (brüt, faizsiz):** indirimsiz … / indirimli … `[doğrula]` — arabuluculuk başvurusunda yaklaşık tutar olarak indirimsiz toplam
**Aylık döküm:** aracın `aylik_dokum` listesi ek tablo olarak (ay, çıplak ücret, gün, fazla çalışma, hafta tatili, UBGT)
**Risk notları:** zamanaşımı, ispat, ibraname, hakkaniyet indirimi; aracın uyarıları
```

## Çıktı iskeleti — zorunlu arabuluculuk başvurusu (işçi alacakları)
**Önce devir:** başvuru ve dava dilekçesi `hukuk-yargilamasi-dilekce` becerisinde (`../../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md`) kurulur; aşağıdaki iskelet yalnız o beceri yüklü değilse kullanılır. Arabuluculuk sürelerini her durumda `legal_get_statute_article` 7036 m.3'ten çek.
Başvurucu bilgileri (ad, TC kimlik no, adres, telefon), karşı taraf (işveren unvanı, adres, varsa vergi/SGK sicil no), uyuşmazlık konusu (alacak kalemleri listesi), işe giriş-çıkış tarihleri, son ücret, talep edilen kalemler ve yaklaşık tutar, vekil bilgileri. Başvuru, karşı tarafın (birden fazlaysa birinin) yerleşim yeri ya da işin yapıldığı yerdeki arabuluculuk bürosuna, büro yoksa görevlendirilen yazı işleri müdürlüğüne yapılır. Yetki itirazı en geç ilk toplantıda yapılır. 

**Yargı çevresi uyarısı:** işçilik alacağı tek başına açılırsa temyizde 9. HD; hizmet tespitiyle ya da iş kazası tazminatıyla birlikte açılırsa 10. HD görevlidir. 

---

