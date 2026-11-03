# Depozito, ayıp, yan giderler, alt kira ve devir, sona erme sonrası

**Ne zaman kullanılır:** "depozitomu vermiyor", "evde rutubet/kombi bozuk, kiradan düşebilir miyim", "aidatı kim öder", "alt kiraya verdi", "dükkânı devretmek istiyorum", "sözleşme bitmeden çıkarsam ne olur", "çıkışta boya-badana parası istiyor", "kiralanana hasar verdi" sorularında.

---

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Depozitonun bankadan iadesi: kiraya veren **3 ay** içinde dava/takip bildirmezse banka kiracının istemiyle öder | Kira sözleşmesinin sona ermesi | TBK m.342/3 | Depozito bankadaysa kiracının en hızlı yolu. |
| Kira bedeli ve dönemsel edimler: **5 yıl** zamanaşımı | Her dönemin muacceliyeti | TBK m.147/1 | |
| Kiraya verenin hasar talebi: gözden geçirme ve **hemen yazılı** bildirim | Geri verme | TBK m.335 | Bildirim yapılmazsa kiracı her türlü sorumluluktan kurtulur; olağan incelemeyle anlaşılamayan eksiklikler için sorumluluk sürer, bunlar da fark edilince hemen yazılı bildirilmeli. |
| Ayıp nedeniyle kiracının fesih/indirim hakkı | Ayıbın öğrenilmesi, bildirim | TBK m.305-308 | Bildirim gecikmeksizin (m.318). |

---

## Kontrol listesi

### 1. Depozito (güvence) — TBK m.342
- Tutar: üç aylık kira bedelini aşamaz; aşan kısım geçersiz. 🟠
- Para ise kiracı **vadeli tasarruf hesabına** yatırır, kiraya verenin onayı olmadan çekilemez; kıymetli evrak bankaya depo edilir. Banka ancak iki tarafın rızasıyla, kesinleşmiş icra takibi ya da kesinleşmiş mahkeme kararıyla öder.
- Depozito **elden** kiraya verene verildiyse: kanunun öngördüğü yol değildir; iade borcu yine vardır, ama banka güvencesi yoktur — iade için arabuluculuk ve sulh hukuk davası `[incele]`. Elden verildiği kira sözleşmesiyle ispatlanırsa kiraya veren yemin teklifiyle bundan kurtulamaz; sözleşmede iade süresi (ör. "tahliyeden en geç 1 ay içinde") varsa faiz o sürenin bitiminden işletilir. Sözleşmede süre yoksa faiz başlangıcı ve m.342'ye aykırılığın başka sonuçları için çalışma anında `legal_search_cases` (`daire: "3. Hukuk Dairesi"`, sorgu "elden verilen depozito iadesi faiz başlangıcı temerrüt") ile ara ve tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: depozito faiz başlangıcı]` yaz.
- Kiraya veren depozitodan neyi düşebilir: ödenmemiş kira ve yan giderler, olağan kullanım dışı hasar. **Olağan kullanımdan doğan eskime ve bozulmadan kiracı sorumlu değildir.**
- Tahliye tarihi ispatı: kiracı iddia ettiği tarihi ispatlayamazsa kiraya verenin kabul ettiği tarih esas alınır → **anahtar teslim tutanağı** ya da noter ihtarıyla anahtar teslimi. 🟠
- Depozito "son kiralara mahsup edilir" maddesi yoksa kiracının son ayları ödememesi temerrüt riski taşır `[incele]`.

### 2. Ayıp — TBK m.301, m.304-308, m.318
- Kiraya veren kiralananı kullanıma elverişli teslim ve **sözleşme süresince** bu durumda bulundurmakla yükümlü; konut/çatılı işyerinde kiracı aleyhine değiştirilemez.
- Sonradan ayıp: kiracı **giderilmesini, kiradan orantılı indirimi ya da zararının giderilmesini** isteyebilir; önemli ayıpta fesih hakkı saklı.
- Giderilme istemi: uygun süre verilir; giderilmezse kiraya veren hesabına giderip kiradan düşme ya da fesih (m.306) — **kendi başına kiradan kesmek** kiracıyı temerrüde sokabilir; önce yazılı bildirim ve süre. 🟠
- Kiracının **bildirim borcu**: gidermekle yükümlü olmadığı ayıbı gecikmeksizin bildirmezse doğan zarardan sorumlu (m.318).
- Kiracının küçük bakım ve temizlik borcu (m.317) ile kiraya verenin esaslı onarım borcu ayrımı: kombi bakımı, ampul, conta kiracıda; kombi değişimi, çatı akıntısı, tesisat kiraya verende — yerel âdete de bakılır `[incele]`.
- Delil: fotoğraf, ustadan rapor, gerekirse **delil tespiti** → `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`.

### 3. Yan giderler ve aidat
- Isıtma, aydınlatma, su gibi **kullanma giderleri** sözleşme ya da yerel âdet aksini öngörmedikçe kiracıda; giderlere katlanan taraf belgeleri istem üzerine verir.
- Zorunlu sigorta (DASK), emlak vergisi gibi yükler kural olarak kiraya verende.
- Apartman aidatı (KMK ortak giderler): kiracının yönetime karşı sorumluluğu KMK'dan (m.22/1: kat malikiyle müteselsil, ama **ödemekle yükümlü olduğu kira miktarıyla sınırlı**; ödediği kira borcundan düşülür), kiraya verene karşı sorumluluğu sözleşmeden `[incele]`.
- Yan gider borcunun ödenmemesi de m.315 temerrüt ihtarına konu olabilir (metin "kira bedelini veya yan gideri"). İki haklı ihtar ise yalnız kira bedeli için `[incele]`.

### 4. Alt kira, kullanım hakkı ve devir
- Konut ve çatılı işyerinde alt kira ve kullanım hakkının devri için **yazılı rıza** şart; alt kiracının aykırı kullanımından kiracı sorumlu.
- Kira ilişkisinin devri: yazılı rıza; **işyerinde** kiraya veren haklı sebep olmadan rızadan kaçınamaz; devreden en fazla iki yıl müteselsil sorumlu. Konutta böyle bir zorunluluk yok.
- Rızasız alt kira sözleşmeye aykırılık sayılır → m.316 ihtar ve fesih yolu `[incele]`.
- Kiracının ölümü: ölen kiracıyla aynı konutta oturanlar ve işyerinde ortaklar/aynı mesleği sürdüren mirasçılar sözleşmeyi sürdürebilir.
- Kiralananın satışı: yeni malik sözleşmenin tarafı olur (m.310); tahliye için `tahliye-sebepleri.md` m.351.

### 5. Erken çıkış (sözleşme bitmeden)
- Kiracı süreye uymadan çıkarsa borçları, kiralananın **benzer koşullarla yeniden kiralanabileceği makul süre** boyunca devam eder; kabul edilebilir, ödeme gücü olan ve devralmaya hazır **yeni kiracı** bulursa borç sona erer; kiraya veren kurtulduğu giderleri ve kasten kaçındığı yararları indirmekle yükümlü.
- "Kalan sürenin tüm kirası ödenir" maddesi bu sınırla değerlendirilir `[incele]`; makul süre yer ve piyasaya göre bilirkişi işi.
- Anahtarı tutanakla teslim et; teslim edilmeyen anahtar kiranın işlemeye devam ettiği iddiasını doğurur. 🟠

### 6. Geri verme ve hasar
- Kiracı teslim aldığı durumda geri verir; olağan kullanımdan eskimeden sorumlu değil.
- Sona ermede sözleşmeye aykırı kullanım zararı dışında önceden kararlaştırılmış tazminat (ör. sabit "boya-badana bedeli") **geçersiz**. 🟠
- Kiraya verenin hasar talebi: hasar + kiralanamama süresi kira kaybı; teslim ispatı tartışması. `[çekildi ama desteği doğrulayın]`
- Kiracının yaptığı faydalı ve lüks giderler, yenilikler (m.321) ve sebepsiz zenginleşme `[incele]`. m.321: yenilik için kiraya verenin **yazılı rızası** gerekir; rıza veren kiraya veren, yazılı kararlaştırılmadıkça eski hâle getirmeyi isteyemez; kiracı da aksine yazılı anlaşma yoksa rızayla yaptığı yeniliğin değer artışını isteyemez.

---

## Görüşme soruları
1. Depozito tutarı, nasıl verildi (elden / banka / çek), makbuz var mı?
2. Tahliye ve anahtar teslim tarihi; teslim tutanağı, fotoğraf var mı?
3. Kiraya verenin iddia ettiği hasarlar ve bunların giriş tutanağındaki durumu?
4. Ödenmemiş kira, aidat, fatura var mı?
5. Ayıp: ne zaman ortaya çıktı, ne zaman ve nasıl bildirildi, kiraya veren ne cevap verdi?
6. Alt kira/devir: yazılı rıza var mı; işyeri mi?
7. Erken çıkışta yeni kiracı önerildi mi?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6098" article_no: "301" | "302" | "305" | "306" | "317" | "318" | "322" | "323" | "325" | "334" | "335" | "341" | "342" | "356"
legal_search_cases mahkeme: "yargitay" daire: "3. Hukuk Dairesi" sorgu: "<ör. depozito iadesi olağan kullanım eskime kiracı sorumlu değil>" tarih_baslangic: <son 3 yıl>
legal_get_case_document <son 3 yıldan en az bir karar>
legal_get_legal_interest_rates # depozito/kira alacağına faiz
```

## Çıktı iskeleti
```markdown
## [Depozito iadesi / ayıp / erken çıkış] değerlendirmesi: [kiracı/kiraya veren] — [tarih]
### Sonuç
### Alacak-borç tablosu
| Kalem | Tutar | Dayanak | Not |
|---|---|---|---|
| Depozito | | TBK m.342 | [doğrula] |
| Ödenmemiş kira | | | |
| Hasar (olağan kullanım dışı) | | TBK m.334 | bilirkişi |
| Net | | | [doğrula] |
### Sonraki adım (yazılı talep → arabuluculuk → sulh hukuk)
### Eksik bilgi
```

## Sık hatalar
- 🔴 Ayıp nedeniyle kiracının bildirim ve süre vermeden kirayı kendiliğinden kesmesi.
- 🟠 Olağan eskimeyi (boya solması, normal aşınma) depozitodan düşmek.
- 🟠 Üç aylık kirayı aşan depozitoyu geçerli saymak.
- 🟠 Anahtarı tutanaksız bırakmak.
- 🟡 Konut kirasında devre rıza verilmesini zorunlu saymak (zorunluluk yalnız işyerinde).
