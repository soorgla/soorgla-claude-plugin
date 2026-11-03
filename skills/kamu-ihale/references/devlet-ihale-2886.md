# 2886 sayılı Devlet İhale Kanunu: satış, kiralama, trampa, ecrimisil

Kamuya **gelir getiren** işlemler (taşınmaz ve taşınır satışı, kiralama, trampa, sınırlı ayni hak tesisi) ile işgal üzerine ecrimisil. Belediye ve il özel idaresi taşınmazları, kamu binalarındaki kantin/büfe/kafeterya kiralamaları, Hazine taşınmazları tipik konulardır.

**Temel ayrım (eski YAML'daki "The Fork"):** idare **para harcıyorsa** 4734; **para kazanıyorsa** (satış, kira) kural olarak 2886. 4734'ün şikâyet ve itirazen şikâyet yolu ile KİK'in yetkisi 4734'e göre yapılan ihalelerle sınırlıdır; 2886 ihalelerinde KİK yolu yoktur, ihale işlemine karşı doğrudan idari yargıya gidilir.

- **İstekli / müşteri tarafı:** satış ya da kiralama ihalesine katılım, ihalenin iptali, teminat, ecrimisile itiraz.
- **İdare tarafı (emlak ve istimlak birimi):** usul seçimi, tahmin edilen bedel, kıymet takdiri, ihale kararının onayı, kira süresi, ecrimisil, Sayıştay riski.

---

## Ne zaman kullanılır

| Durum | Taraf |
|---|---|
| Belediye/Hazine taşınmazının satış veya kiralama ihalesi | İkisi |
| Kantin, büfe, çay bahçesi kiralaması; 51/g pazarlık | İkisi |
| Tahmin edilen bedel düşük belirlendi (kamu zararı) | İdare |
| İhale kararı ita amirince iptal edildi / onaylanmadı | İstekli |
| İşgal nedeniyle ecrimisil ihbarnamesi | İstekli (işgalci) / idare |
| Kira sözleşmesi bitti, tahliye, kira alacağı | Sözleşme sonrası → özel hukuk |

---

## Kontrol listesi

### 1. Kapsam ve usul
- [ ] İşlem 2886 m.1 kapsamında mı (genel ve özel bütçeli idareler, il özel idareleri, belediyeler vb.); özel kanun (ör. 5393 Belediye K., Hazine Taşınmazlarının İdaresi Hakkında Yönetmelik, 4706) farklı düzen öngörüyor mu? `[incele]` m.1: genel ve katma bütçeli idareler, özel idare ve belediyelerin alım, satım, hizmet, yapım, kira, trampa, gayri ayni hak tesisi ve taşıma işleri bu Kanuna göre yürütülür (alım-yapım tarafını bugün 4734 düzenler). Belediyede taşınmaz satımı, takası, üç yıldan fazla kiralanması ve otuz yılı geçmeyen sınırlı ayni hak tesisi kararı **belediye meclisinindir** (5393 m.18/e); ihale usulü 2886'ya göre yürür.
- [ ] Usuller: **kapalı teklif**, **belli istekliler arasında kapalı teklif**, **açık teklif**, **pazarlık**, **yarışma**; hangisinin uygulanacağını idare kanuna uyarak belirler.
- [ ] **Pazarlık (m.51):** bentler sınırlı sayıdadır. Kiralamada en sık başvurulan (g) bendi: kullanışlarının özelliği, idareye yararlı olması veya ivediliği nedeniyle kapalı/açık teklifle ihalesi uygun görülmeyen kiralama, trampa ve sınırlı ayni hak tesisi. Gerekçe somut olmalı; rekabeti daraltan keyfî 51/g seçimi iptal sebebi `[incele]`. 51/g davası örneği:
- [ ] Pazarlıkta (a), (b), (c), (d), (i), (l), (p) bentlerinde şartname, tahmini bedel, teminat ve sözleşme zorunlu değil; (i), (l), (p)'de Maliye (Hazine ve Maliye) Bakanlığının uygun görüşü alınır.

### 2. Tahmin edilen bedel ve kıymet takdiri
- [ ] Tahmin edilen bedel idarece tespit edilir/ettirilir; gerektiğinde belediye, ticaret ve sanayi odası, borsa veya bilirkişiden fiyat soruşturulur; dayanaklarıyla hesap tutanağında gösterilir; komisyon gerektiğinde tahkik ettirir. 4734'teki yaklaşık maliyetin aksine kanunda "gizlilik" hükmü yok; ilana yazılıp yazılmayacağını şartname ve yönetmelikten kontrol et `[incele]`.
- [ ] Bedel piyasa rayicinin altındaysa Sayıştay kamu zararı riski (idare için 🟠). Sayıştay daire kararlarını `legal_search_cases mahkeme: "sayistay"` ile ara; savunma metni `../../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`.

### 3. Teminat ve yerel yönetimlerde taksitli satış (2026 değişikliği)
- [ ] **7587 ile 2886'ya ek m.1 (RG 01.07.2026):** il özel idareleri, belediyeler ve bunların kurduğu mahalli idare birliklerine ait taşınmazların satış bedeli peşin veya taksitle ödenebilir; taksit ilanda belirtilmiş ve istekli talep etmişse en az %25 peşin, kalanı en fazla 2 yılda ve en fazla 12 taksitte **kanuni faiziyle**; kalan borç için kesin ve süresiz banka teminat mektubu ya da idare lehine kanuni ipotek verilirse tapu devredilir, verilmezse taksitler bitene kadar devir yok; ödenmeyen taksit 6183 m.51 faiziyle tahsil; satış, kira, trampa ve sınırlı ayni hak ihalelerinde tahmin edilen bedelin **%3'ünden az olmamak üzere %30'una kadar** geçici teminat alınabilir; usul ve esaslar Çevre, Şehircilik ve İklim Değişikliği Bakanlığınca belirlenir. Geçici teminat fıkrasının yalnız yerel yönetim taşınmazlarına mı uygulanacağı madde başlığı karşısında `[incele]`. Kanuni faiz oranı için 3095 m.1 (7589 sonrası) madde metnine dayan; `legal_get_legal_interest_rates` bu konuda yanlış oran verebilir. Bakanlığın ek m.1 usul ve esasları Resmî Gazete'de bulunamadı; ilan tarihinde yeniden ara `[doğrula]`.

### 4. İhale kararı ve onay
- [ ] Komisyon kararında başkan ve üyelerin ad, soyad ve esas görevleri; isteklilerin isimleri, adresleri, teklifleri, ihalenin tarihi, kime ve hangi gerekçeyle yapıldığı ya da yapılmama nedenleri yazılır.
- [ ] İta amiri kararı **karar tarihinden itibaren en geç 15 iş günü** içinde onaylar ya da iptal eder; iptal edilirse ihale hükümsüz. İta amirine onay **zorunluluğu** getirilmemiştir; iptal yetkisi takdirîdir ama kamu yararı ve hizmet gerekleriyle sınırlı, gerekçeli olmalı `[incele]`.
- [ ] Onaylanan karar onay gününden itibaren **en geç 5 iş günü** içinde üzerine ihale yapılana imzası alınarak bildirilir ya da iadeli taahhütlü postalanır; iptal de aynı şekilde bildirilir (m.32). m.32'nin ikinci cümlesi AYM'nin 18.06.2013 tarihli E.2013/71 K.2013/77 kararıyla iptal edilmiştir; 15 iş günü içinde onaylanmamanın sonucunu Kanun metni ayrıca düzenlemiyor, istekli bakımından sonuç (teklifle bağlılık, teminatın iadesi) `[incele]`. Teklif verildikten sonra Kanunda yazılı haller dışında zam/indirim teklifi kabul edilmez (m.33).

### 5. Kiralama
- [ ] Kira süresi **10 yılı geçemez** (turistik tesis, enerji ve doğal gaz tesislerinin arazileri istisna); 3 yılı aşan kiralamada Hazine ve Maliye (eski Maliye) Bakanlığı izni (katma bütçelilerde bağlı bakanlık); **özel idare ve belediyelerde kendi kanunları**; 3 yılı aşan kirada bedel her yıl şartname ve sözleşmeye göre yeniden belirlenir. Belediyelerde kiralama süresi ve yetkili organ (meclis/encümen) için 5393'ü çek `[incele]`.
- [ ] Sözleşme imzalandıktan sonraki uyuşmazlık (kira bedeli, tahliye, kira alacağı) özel hukuk niteliğindedir → `../../kira-hukuku/SKILL.md`; görevli mahkeme ve Yargıtay dairesini sabit yazma, güncel BGK iş bölümünden çek. Eski YAML "Yargıtay 3. HD" diyordu; daire bilgisini metne gömme.

### 6. Ecrimisil (m.75)
- [ ] Devletin özel mülkiyetinde veya hüküm ve tasarrufu altındaki taşınmazlar, özel bütçeli idarelerin taşınmazları ve Vakıflar Genel Müdürlüğü/mazbut vakıf taşınmazlarında işgal üzerine; **tespit tarihinden geriye 5 yılı geçmemek** üzere, işin ehli üç kişilik komisyonca takdir edilen ecrimisil istenir; **zarar ve kusur aranmaz**.
- [ ] İtiraz edilmezse **%20**, peşin ödenirse ayrıca **%15** indirim; rızaen ödenmezse 6183'e göre tahsil.
- [ ] Kira sözleşmesi bittiği halde işgal sürerse sözleşmede hüküm varsa ona göre, yoksa ecrimisil.
- [ ] Tahliye: idarenin talebi üzerine mülki amir **en geç 15 gün** içinde tahliye ettirir.
- [ ] Ecrimisile itiraz ve dava yolu (idari yargı mı, adli yargı mı; belediye taşınmazında 2886 mı uygulanır) `[incele]` — Uyuşmazlık Mahkemesi ve Danıştay içtihadını çek. Belediye taşınmazında m.75 uygulanır (5393 m.15: "2886 sayılı Devlet İhale Kanununun 75 inci maddesi hükümleri belediye taşınmazları hakkında da uygulanır"); ecrimisil ihbarnamesinin iptali davaları idari yargıda görülüyor (görülen temyizler Danıştay 4. Dairede).

### 7. Yasak fiil ve yasaklama (2886)
- [ ] m.83 yasak fiiller: fesat karıştırma, açık teklif/pazarlıkta rağbeti kırma, sahte belge/teminat, taahhüdü kötü niyetle yerine getirmeme, hileli malzeme.
- [ ] m.84: ihaleyi yapan veya ilgili bakanlıkça **bir yıla kadar** bütün ihalelere katılmaktan yasaklama; RG'de ilan; sermayesinin çoğunluğuna sahip olunan tüzel kişilere de uygulanır; sözleşme yapmayan ve taahhüdünü yerine getirmeyenlere de; Türkiye genelinde faaliyet gösteren tüzel kişilerde temsilcinin şahsi kusurundan doğan üçüncü fıkra hallerinde bir ay içinde **ihale bedelinin üç katı** tazminat peşin ödenirse yasaklama verilmez. Yasaklama davası ivedi usule tabi değildir (İYUK 20/A-1-a).

### 8. Dava
- [ ] 2886 ihalesine karşı dava: "ihaleden yasaklama kararları hariç ihale işlemleri" ivedi usule tabidir (30 gün, istinaf yok, 15 gün temyiz); 2886 ihalelerinin de bu kapsamda olduğu kabul ediliyor, olay bazında `[incele]`.
- [ ] Dava dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`.

---

## Süreler ve dayanakları

| Süre | Kural | Dayanak |
|---|---|---|
| İhale kararının onayı | Karar tarihinden en geç 15 iş günü | 2886 m.31 |
| Kira süresi | En çok 10 yıl (istisnalar); 3 yılı aşan için izin | 2886 m.64 |
| Ecrimisil dönemi | Tespit tarihinden geriye en çok 5 yıl | 2886 m.75 |
| Tahliye | Mülki amir en geç 15 gün | 2886 m.75 |
| Taksitli satış (yerel yönetim) | En az %25 peşin, en çok 2 yıl / 12 taksit | 2886 ek m.1 |
| Yasaklama süresi | En çok 1 yıl | 2886 m.84 |
| Dava (ihale işlemi) | 30 gün (ivedi); temyiz 15 gün, istinaf yok `[incele]` | 2577 m.20/A |

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Taşınmazın maliki/idaresi (Hazine, belediye, il özel idaresi, vakıf, üniversite)? | Uygulanacak kanun ve izin |
| İşlem türü: satış, kiralama, trampa, ecrimisil? | Akış |
| Usul ve gerekçesi (51/g ise gerekçe)? | Usul denetimi |
| Tahmin edilen bedel nasıl belirlendi; kıymet takdir raporu var mı? | Kamu zararı |
| İhale tarihi, komisyon kararı, ita amiri onay/iptal tarihi? | 15 iş günü |
| (Ecrimisil) İşgal başlangıcı, tespit tarihi, ihbarname tarihi, itiraz edildi mi? | 5 yıl, indirimler |
| (Satış) Taksit ilanda öngörüldü mü, teminat mektubu/ipotek? | Ek m.1 |

---

## MCP adımları

```
legal_get_statute_article law_no: "2886" law_type: "Kanun" article_no: "1" | "9" | "30" | "31" | "35" | "45" | "51" | "64" | "75" | "83" | "84" | "ek 1"
legal_resolve_statute query: "Hazine Taşınmazlarının İdaresi Hakkında Yönetmelik"
legal_get_statute_article law_no: "5393" law_type: "Kanun" article_no: "18" # belediye meclisinin taşınmaz yetkisi
legal_search_official_gazette query: "2886 sayılı Devlet İhale Kanununa" category: "YASAMA BÖLÜMÜ" sort_by: "date_desc"
legal_search_cases mahkeme: "danistay" sorgu: "<ör. 2886 sayılı Kanun 51/g pazarlık kiralama ihalesinin iptali>" tarih_baslangic: "<son 3 yıl>"
legal_search_cases mahkeme: "sayistay" sorgu: "<ör. kiralama tahmin edilen bedel düşük kamu zararı>"
legal_get_case_document belge_id: "<seçilen karar>"
```

---

## Çıktı iskeleti

```markdown
### 2886 değerlendirmesi — [taşınmaz/iş] — [istekli / idare]
| Kontrol | Sonuç | Dayanak |
|---|---|---|
| Uygulanacak kanun (2886 / özel kanun) | | |
| Usul ve gerekçe | ✅/🔴/[incele] | 2886 m.35, 51 |
| Tahmin edilen bedel ve dayanağı | | m.9 |
| Onay süresi (15 iş günü) | | m.31 |
| Kira süresi ve izin | | m.64 |
| Teminat / taksit (yerel yönetim) | | ek m.1 |
| Yargı yolu ve son gün | | İYUK 20/A |

### Sonraki adım
[ihale aşaması → dava / sözleşme sonrası → kira-hukuku / ecrimisil → itiraz ve indirim hesabı]
```

---

## Sık hatalar

- 🔴 2886 ihalesine karşı KİK'e itirazen şikâyet yapmak (yol yok; dava süresi işler).
- 🟠 51/g pazarlığı somut gerekçe olmadan seçmek (idare).
- 🟠 Ecrimisilde 5 yıldan eski dönemi ya da indirim haklarını hesaba katmamak.
- 🟠 Kira sözleşmesi sonrası tahliye uyuşmazlığını idari yargıda açmak.
- 🟡 Yerel yönetim taşınmaz satışında 2026'da gelen taksit ve teminat imkânını ilanda öngörmemek.

---
