# Yabancının taşınmaz edinimi; yabancı mahkeme ve hakem kararlarının tanınması ve tenfizi

## Ne zaman kullanılır
- "Yabancı biri Türkiye'de ev alabilir mi", "hangi ülke vatandaşları alamaz", "askerî bölgede yabancıya satış", "yabancı şirket taşınmaz edinebilir mi", "mirasla yabancıya kalan taşınmaz tasfiye edilir mi".
- "Yabancı mahkemenin alacak kararını Türkiye'de icra ettirmek istiyorum", "yabancı hakem kararının tenfizi", "tanıma mı tenfiz mi".

**Sınırlar:** tapu iptali, satış vaadi, kat mülkiyeti, ön alım ve ortaklığın giderilmesi → `../../gayrimenkul-insaat/SKILL.md`. Vatandaşlık için taşınmaz alımı → `vatandaslik.md`. Yabancı **boşanma, nafaka, velayet** kararları ve 5490 m.27/A idari tanıma → `../../aile-miras/references/yabancilik-unsuru-ve-tanima.md`. Uygulanacak hukuk soruları (sözleşme, haksız fiil) bu dosyada yalnız işaretlenir; yabancı hukuk içeriği hakkında emin cevap verme (ORTAK-KURALLAR.md §2).

**Bu dosya YAML'sız kuruldu**; eski `citizenship_investment.yaml`'daki tek cümlelik "mütekabiliyet ve Tapu Kanunu" uyarısı genişletildi.

---

## A. Yabancının taşınmaz edinimi (2644 m.35)

| Kural | İçerik | Dayanak |
|---|---|---|
| Kimler edinebilir | **Cumhurbaşkanınca belirlenen ülkelerin** vatandaşı gerçek kişiler, kanuni sınırlamalara uyarak; karşılıklılık şartı 6302 ile kaldırıldı, yerine CB belirlemesi geldi | 2644 m.35/1 (6302, 2012) |
| Alan sınırı | Yabancı gerçek kişilerin toplam edinimi **ilçe özel mülkiyet yüzölçümünün %10'unu** ve kişi başına ülke genelinde **30 hektarı** geçemez; CB kişi başı miktarı iki katına çıkarabilir | 2644 m.35/1 |
| Yabancı şirketler | Kendi ülkesinin kanununa göre kurulmuş tüzel kişiliği haiz ticaret şirketleri ancak **özel kanun** hükümleri çerçevesinde edinebilir; diğer yabancı tüzel kişiler edinemez; **taşınmaz rehninde** bu sınırlamalar uygulanmaz | 2644 m.35/2 |
| CB'nin yetkisi | Ülke, kişi, coğrafi bölge, süre, sayı, oran, tür, nitelik, yüzölçüm ve miktar olarak belirleme, sınırlandırma, durdurma, yasaklama | 2644 m.35/3 |
| Yapısız taşınmaz | Geliştirilecek proje **2 yıl** içinde ilgili Bakanlığın onayına sunulur; proje süresi beyanlar hanesine işlenir | 2644 m.35/4 |
| Askerî yasak ve güvenlik bölgeleri | Harita ve koordinatlar Bakanlığa verilir, tapu işlemleri bunlara göre yürütülür | 2644 m.35/5 |
| Aykırı edinim ve **miras** | Maddeye aykırı edinilen, amacına aykırı kullanılan, süresinde projesi sunulmayan/gerçekleştirilmeyen taşınmazlar ve sınırlama dışında mirasla edinilenler, Maliye Bakanlığının vereceği **1 yılı geçmeyen** sürede malik tarafından tasfiye edilmezse tasfiye edilerek bedele çevrilir, bedel hak sahibine ödenir | 2644 m.35/6 |

**Ülke listesini sabit yazma:** eski YAML'daki "Suriye, Kuzey Kore, Güney Kıbrıs vatandaşları alamaz" ifadesi bir listeye dayanıyor olabilir ama dayanağı CB kararı (ve bazı ülkeler için ayrı mevzuat) olduğundan değişir. Güncel listeyi ve dayanağını (CB kararı, varsa ülkeye özgü mevzuat) Tapu ve Kadastro Genel Müdürlüğü duyurusundan ya da RG'den kullanıcıya teyit ettir — soorgla'da bulunamadı; ülke adı yazma. soorgla'da "Suriye Uyruklu Özel ve Tüzel Kişilerin Hazinece El Konulan Mallarının İdaresi Hakkında Yönetmelik" kaydı var; bu, edinim yasağının değil eski el koyma rejiminin metnidir, dayanak sanma.

**Bağlantılı sonuçlar:**
- Taşınmaz sahipliği **kısa dönem ikamet** gerekçesidir (6458 m.31/1-b); esas olacak taşınmazın niteliği ve değeri 7533 ile Bakanlıkça belirlenir (m.31/6) → `ikamet-izinleri.md`.
- Vatandaşlık için taşınmaz alımında 2023'ten beri yalnız kat mülkiyeti/irtifakı kurulmuş ya da yapılı arsa sayılır → `vatandaslik.md`.
- Yurt dışında yerleşik kişiye konut satışında KDV istisnası, döviz şartı ve bedel iadesinde KKDF gibi vergisel sorular → `../../vergi/SKILL.md`; GİB özelgeleri `legal_search_admin_guidance` (`kurum: "Gelir İdaresi Başkanlığı"`, `belge_tur: "ozelge"`) ile çıkıyor.

### Kontrol listesi — edinim
1. Alıcının uyruğu (çifte vatandaşlık? 5901 m.28 kapsamı → yabancı sayılmayabilir `[doğrula]`) ve güncel CB listesi.
2. Taşınmaz askerî yasak / güvenlik / stratejik bölgede mi? Tapu müdürlüğünün askerî izin yazısı.
3. İlçe %10 ve kişi başı 30 hektar sınırı (tarım arazisi, büyük parsel).
4. Yapısız taşınmazsa 2 yıllık proje yükümlülüğü ve beyanlar hanesi kaydı.
5. Alıcı yabancı şirketse hangi özel kanuna dayanıyor? (Türkiye'de kurulmuş yabancı sermayeli şirket ayrı rejim → `../../sirketler-ticaret/SKILL.md`) `[doğrula]`
6. Mirasla edinimde sınır aşılıyorsa 1 yıllık tasfiye süresi.
7. Bedel ödemesi bankacılık yoluyla ve döviz satışı belgeli mi (ikamet/vatandaşlık başvurusu planlanıyorsa)?

---

## B. Yabancı mahkeme ve hakem kararlarının tanınması ve tenfizi (5718)

| Konu | Kural | Dayanak |
|---|---|---|
| Tenfiz gereği | Yabancı mahkemenin hukuk davalarına ilişkin, o devlet kanunlarına göre **kesinleşmiş** ilamının Türkiye'de icrası yetkili Türk mahkemesinin tenfiz kararına bağlıdır; ceza ilamlarındaki kişisel haklara ilişkin hükümler için de istenebilir | 5718 m.50 |
| Görev ve yetki | **Asliye mahkemesi**; aleyhine tenfiz istenenin Türkiye'deki yerleşim yeri, yoksa sâkin olduğu yer, o da yoksa Ankara, İstanbul ya da İzmir | 5718 m.51 |
| Ekler | Onanmış ilam aslı ya da onaylı örneği ve onaylı tercümesi; **kesinleşme** belgesi ve onaylı tercümesi | 5718 m.53 |
| Şartlar | Karşılıklılık; Türk mahkemelerinin münhasır yetkisine girmeme / aşırı yetki itirazı; kamu düzenine açık aykırılık olmaması; usulüne uygun çağrı, temsil ve savunma hakkı | 5718 m.54 (aile-miras dosyasında DOGRULANDI) |
| Tanıma | Karşılıklılık (m.54/1-a) aranmaz; diğer şartlar aranır | 5718 m.58/1 (aile-miras dosyasında DOGRULANDI) |
| **Yabancı hakem kararı** | Kesinleşmiş ve icra kabiliyeti kazanmış ya da bağlayıcı karar; tarafların yazılı kararlaştırdığı yer **asliye** mahkemesi, yoksa aleyhine karar verilenin yerleşim yeri, sâkin olduğu yer ya da malların bulunduğu yer | 5718 m.60 |
| Hakem kararında ret sebepleri | Tahkim anlaşması yok; genel ahlâk ya da kamu düzenine aykırılık; uyuşmazlık tahkime elverişsiz; usulüne uygun temsil yok; hakem seçiminden haberdar edilmeme ya da savunma imkânından yoksunluk; tahkim anlaşmasının hükümsüzlüğü; usulün anlaşmaya aykırılığı; anlaşmayı aşan karar (o kısım); kesinleşmeme, icra kabiliyeti kazanmama ya da iptal edilme. (ç)-(h) bentlerinde ispat yükü tenfiz istenen taraftadır | 5718 m.62 |

**Ticari dava ve asliye ticaret:** m.51 ve m.60 "asliye mahkemesi" der; uyuşmazlık ticari nitelikteyse asliye ticaret mahkemesinin görevli olup olmadığını TTK m.4-5 ve güncel Yargıtay içtihadıyla kontrol et `[doğrula]`. Uygulamada ticari ilamların tenfizi asliye ticarette görülüp Yargıtay 11. HD'de inceleniyor (ör. 11. HD E.2024/2938 K.2024/5347 — ABD mahkeme kararının tenfizi, ilk derece "Ticaret Mahkemesi"); Ankara BAM 9. HD de özel asliye mahkemelerinin (asliye ticaret, aile, iş) kendi alanlarındaki tanıma/tenfizde görevli olduğunu "yerleşik yargı kararları"na dayanarak kabul etti (Yargıtay 9. HD E.2024/12327 K.2025/346'da aktarılan gerekçe; Yargıtay başka gerekçeyle bozdu). Dava şartı arabuluculuğun (TTK 5/A) tenfiz davasına uygulanıp uygulanmadığını varsayma; güncel kararı ara, bulamazsan `[ARAŞTIRMA GEREKLİ: tenfizde TTK 5/A]` → `../../sirketler-ticaret/SKILL.md`. New York 1958 Sözleşmesi'nin metni ve Türkiye'nin çekinceleri soorgla'da yok; uygulanabilirlik ve çekinceleri RG onay kanunundan ya da UNCITRAL taraf listesinden kullanıcıya teyit ettir, ezberden yazma.

**Temyizde daire:** yabancı mahkeme kararlarının tanınması ve tenfizi istemli davalarda temyiz incelemesi esas davaya ait hükmü incelemekle görevli dairece yapılır (Yargıtay BGK 2026/1 Ortak Hükümler m.12) — daireyi sabit yazma, BGK'dan çek. (aile-miras dosyasında DOGRULANDI)

### Kontrol listesi — tenfiz
1. Karar mahkeme kararı mı, hakem kararı mı, noter/idari karar mı? (Noter ya da idari makam kararı tenfize konu olmayabilir `[incele]`.)
2. Kesinleşme belgesi var mı; apostil ya da konsolosluk onayı; yeminli tercüme?
3. Karşılıklılık: anlaşma, kanun hükmü ya da fiilî uygulama ile kanıtlanabiliyor mu? (Tanımada aranmaz.)
4. Türk mahkemelerinin münhasır yetkisi (ör. Türkiye'deki taşınmazın aynına ilişkin dava) var mı? 🔴
5. Davalıya usulüne uygun tebligat yapılmış mı, savunma hakkı kullanılmış mı (gıyabi karar)?
6. Kamu düzeni: yalnız **açık** aykırılık (ör. cezai nitelikli tazminat, ağır usul ihlali) `[incele]`.
7. Faiz ve döviz: yabancı para alacağında `legal_get_exchange_rate`; faiz hükmünün tenfizi ve Türk faiz hukukuyla ilişkisi `[incele]`.
8. Hakem kararında: tahkim şartı yazılı mı, tahkime elverişlilik (ör. kira tahliyesi, tüketici, iş uyuşmazlığı), kararın iptal edilip edilmediği.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| (Edinim) Alıcının uyruğu ve diğer vatandaşlıkları; taşınmazın ili, ilçesi, niteliği, yüzölçümü? | CB listesi, %10/30 ha |
| (Edinim) Taşınmaz askerî bölgede mi; yapısız mı? | m.35/4-5 |
| (Edinim) Amaç: oturma, ikamet izni, vatandaşlık, yatırım? | Bağlantılı rejimler |
| (Tenfiz) Kararı hangi ülkede hangi makam verdi, ne zaman kesinleşti? | m.50, m.53 |
| (Tenfiz) Karşı taraf yargılamaya katıldı mı, nasıl tebliğ edildi? | m.54 savunma hakkı |
| (Tenfiz) Karşı tarafın Türkiye'de yerleşim yeri ya da malı nerede? | m.51, m.60 yetki |
| (Hakem) Tahkim şartının metni, kurum ve yer? | m.62 |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "2644" law_type: "Kanun" article_no: "35"
legal_get_statute_article law_no: "5718" law_type: "Kanun" article_no: "50" | "51" | "53" | "54" | "58" | "60" | "61" | "62" | "63"
legal_search_official_gazette query: "yabancı uyruklu gerçek kişilerin taşınmaz edinimi Cumhurbaşkanı Kararı" sort_by: "date_desc"
legal_search_cases mahkeme: "yargitay" sorgu: "<ör. yabancı hakem kararının tenfizi kamu düzeni savunma hakkı>" tarih_baslangic: "2023-01-01"
legal_search_admin_guidance sorgu: "yurt dışında yerleşik kişilere konut satışı döviz KDV" kurum: "Gelir İdaresi Başkanlığı" belge_tur: "ozelge"
```

---

## Çıktı iskeleti

```markdown
## [Taşınmaz edinimi / Tenfiz] değerlendirmesi — [taraf] — [tarih]
### Sonuç
### Şart kontrolü
| Şart | Var/Yok | Belge | Not |
### Yetkili merci ve belgeler
### Yabancı hukuk uyarısı (ORTAK-KURALLAR.md §2)
### Eksik bilgi
```

Tenfiz dava dilekçesi → `../../hukuk-yargilamasi-dilekce/SKILL.md` (`references/dava-dilekcesi.md`).

---

## Sık hatalar

- 🟠 Karşılıklılığı taşınmaz ediniminde hâlâ şart sanmak (6302 ile CB belirlemesine geçildi).
- 🟠 Tanımada karşılıklılık aramak.
- 🟠 Kesinleşme belgesi olmadan tenfiz davası açmak.
- 🟡 Ülke yasak listesini sabit yazmak.
- 🟡 Yabancı boşanma kararını bu dosyayla çözmeye çalışmak (aile-miras; idari tanıma yolu var).

---
