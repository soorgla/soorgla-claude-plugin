# Ek tahakkuk ve ceza kararı: triyaj ve yol seçimi (itiraz / uzlaşma / dava)

## Ne zaman kullanılır
- Gümrük müdürlüğünden "ek tahakkuk ve ceza kararı" tebliğ edildi; ne yapılmalı, son gün ne?
- İtiraz mı, uzlaşma mı? İkisi birlikte mi? İtiraz reddedildi, şimdi ne?
- Gümrük vergileri ne zaman zamanaşımına uğrar, ne zaman ödenmeli, itiraz ödeme süresini durdurur mu?

**Dilekçe metni:** itiraz ve uzlaşma talebi → `../../idari-ve-kurum-basvurulari/SKILL.md` (aşağıdaki iskeletle). Dava → `gumruk-davasi.md`.

---

## Triyaj — gelen kararı alan alan ayrıştır (upstream `demand-received` uyarlaması)

Karar elindeyse önce şu alanları çıkar; eksik olanı görüşme sorusuna çevir:

| Alan | Neden önemli |
|---|---|
| Kararı veren gümrük müdürlüğü, karar tarihi ve sayısı | İtirazın hangi üst makama yapılacağı (m.242/1) |
| **Tebliğ tarihi ve şekli** (elden, posta, e-tebligat) | 15 günlük itiraz ve uzlaşma süresinin başlangıcı |
| Beyanname sayısı, tescil tarihi, rejim (serbest dolaşım, DİR, geçici ithalat…) | Yükümlülüğün doğduğu tarih → 3 yıllık tebliğ zamanaşımı (m.197/2) |
| Uyuşmazlık kaynağı: tarife (GTİP), kıymet, menşe, ticaret politikası önlemi, rejim ihlali, yasak/izinli eşya | Hangi referans dosyası ve hangi emsal |
| Tahakkuk kalemleri ayrı ayrı: gümrük vergisi, ilave gümrük vergisi, damping vergisi, EMY, KDV, ÖTV | Uzlaşma ve dava kısmi yapılabilir |
| Ceza maddesi ve kat (m.234, 235, 236, 238, 239, 241) | Ceza hesabı ve indirim imkânı |
| Kaçakçılık bildirimi / savcılık süreci var mı | Varsa uzlaşma yok (m.244/2) → `kacakcilik-ve-idari-yaptirim-ayrimi.md` |
| Beyannamede ihtirazi kayıt var mı | Kendi beyanına dayalı tahakkukta itiraz ve dava imkânı |

Sonra seçenekleri tabloyla sun ve **bir öneri** yap; karar avukatın `[incele]`.

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Dayanak |
|---|---|---|
| İdari itiraz | Tebliğden itibaren **15 gün**; bir üst makama, üst makam yoksa aynı makama dilekçe | 4458 m.242/1 |
| İtirazın karara bağlanması | İdareye intikalinden itibaren **30 gün** içinde karara bağlanıp tebliğ edilir | m.242/2 |
| Yanlış makama itiraz | Süresinde yanlış makama verilen itiraz süresinde yapılmış sayılır, idarece yetkili makama ulaştırılır | m.242/3 |
| Uzlaşma talebi | Henüz itiraz edilmemiş ya da itirazı sonuçlanmamış vergi ve cezalar için tebliğden itibaren **15 gün** | m.244/1 son paragraf |
| Uzlaşmanın süreye etkisi | Uzlaşma talebi itiraz ya da dava süresini **durdurur**; uzlaşma vaki olmaz ya da temin edilemezse süre kaldığı yerden işler; 5 günden az kalmışsa 5 güne tamamlanır | m.244/1 |
| Uzlaşılan tutarın ödenmesi | Uzlaşma tutanağının tebliğinden itibaren **1 ay**; uzlaşılan vergilere yükümlülüğün başladığı tarihten tutanak imzasına kadar gecikme zammı oranında gecikme faizi | m.244/5 |
| Uzlaşma işlemlerinin süresi | Talebin komisyon kaydına girdiği tarihten itibaren azami 30 gün içinde sonuçlandırılması esastır | Gümrük Uzlaşma Yönetmeliği m.18/1 |
| Ek tahakkukun ödenmesi | Tebliğden itibaren **15 gün**; süre bitmeden yazılı istem ve teminatla 30 gün uzatılabilir (tecil faiziyle) | m.198/1 |
| İtirazın ödemeye etkisi | m.242 itirazı ödeme süresini **keser**; süre idarenin ya da yargı merciinin kararının tebliğinden yeniden başlar | m.198/2 |
| Dava | İtirazın reddinin tebliğinden itibaren vergi mahkemesinde **30 gün** (→ `gumruk-davasi.md`) | m.242/4; 2577 m.7/1 |
| Tebliğ zamanaşımı | Hiç alınmadığı ya da noksan alındığı belirlenen vergilerin tebliği, gümrük yükümlülüğünün doğduğu tarihten itibaren **3 yıl** içinde; olayla ilgili dava açılması zamanaşımını durdurur | m.197/2 |
| Kaçakçılık bağlantısında zamanaşımı | Ceza davası açılmışsa ve fiilin zamanaşımı daha uzunsa TCK'daki dava ve ceza zamanaşımı süreleri | m.197/4, m.231/1 |
| İdari para cezasının zamanaşımı | Gümrük vergisi alacağına bağlı idari para cezaları o vergilerin zamanaşımına tabi | m.231/2 |
| Kesinleşme | Süresinde itiraz edilmez ya da dava açılmazsa sürelerin bittiği tarihte kesinleşir; dava açılırsa aleyhe kararın gümrük idaresine tebliğinde tahsil edilebilir hâle gelir | m.197/5 |

`legal_calculate_deadline`: `customs_objection`, `customs_settlement_request`, `customs_payment`, `customs_lab_objection`. Araç yanıt vermezse ya da "Süre kodu bulunamadı" dönerse elle hesapla (tebliğ günü sayılmaz), son günü `legal_check_holiday` ile kontrol et, `[doğrula]`. Uzlaşma talebinin itiraz/dava süresini durdurmasını (m.244/1) araç hesaplamaz.

---

## Uzlaşma — neye girer, neye girmez

- **Kapsam:** (a) beyan ile idare tespiti arasındaki farklara ilişkin tebliğ edilen gümrük vergileri, (b) idare tespitinden önce beyan sahibinin bildirdiği farklara ilişkin vergiler, (c) **4458 ve ilgili diğer kanunlar uyarınca gümrük idaresince düzenlenen idari para cezaları**. Eski YAML'daki "gümrük cezaları uzlaşmaya dahil değildir" ifadesi **yanlıştır**.
- **Kaçakçılık bağlantısı:** vergi ve cezaya ilişkin fiil 5607'deki kaçakçılık suçlarıyla ilişkiliyse uzlaşma uygulanmaz.
- **Sonuç:** tutanak kesindir; yükümlü uzlaşılan hususlarda dava açamaz, şikâyette bulunamaz. Uzlaşma vaki olmazsa yeniden talep edilemez.
- **Peşin ödeme indirimi:** uzlaşılan cezalarda Kabahatler Kanunu m.17 peşin ödeme indirimi ayrıca uygulanmaz. Uzlaşma yapılmayan idari para cezalarında genel kural: kanununda ödeme süresi yoksa tebliğden itibaren **1 ay** içinde ödeme ve bu sürede ödenirse kanuni oranda indirim (oranı maddeden oku); ödeme dava hakkını etkilemez (5326 m.17/6, 7417 ile değişik). 4458'de vergi aslına bağlı cezalar vergiyle aynı zamanda tebliğ edilir ve **aynı zamanda ödenir** (m.232/1); ek tahakkuk edilen vergilerin ödeme süresi tebliğden itibaren 15 gün, teminatla 30 gün uzatılabilir, itiraz ödeme süresini keser (m.198/1-2). 4458'de ayrı bir peşin ödeme indirimi hükmü madde aramasında bulunamadı; vergi aslına bağlı olmayan cezalarda 5326 m.17/6'nın uygulanıp uygulanmadığını ceza kararındaki açıklamadan teyit et `[doğrula]`.
- **Yetkili komisyon:** tutara göre Gümrük ve Dış Ticaret Bölge Müdürlüğü Uzlaşma Komisyonu ya da Merkezi Uzlaşma Komisyonu; sınır Yönetmelik m.9'da ve 18.06.2026'da değişti — tutarı maddeden çek, başvuru tarihinde yürürlükteki metin uygulanır (geçici m.4). Tutarın hesabında kalem bazında vergi + vergi aslına bağlı ceza toplamı, vergi aslına bağlı olmayan cezalar ayrı ayrı esas alınır, fer'iler dikkate alınmaz.
- **Başvuru süresi:** gümrük vergileri ve vergi aslına bağlı olsun olmasın tüm para cezalarının tebliğinden itibaren 4458 m.242'deki **15 günlük itiraz süresi** içinde (Yönetmelik m.11/1). **Şekli:** BİLGE şifresiyle kurumsal internet sayfasından; şifre temin edilemezse EK-3 formuyla — sürede formun evrak kaydına girdiği ya da taahhütlü postaya verildiği tarih esas (m.10/1); iştirak hâlinde her ceza muhatabı ayrı başvurabilir, uzlaşma yalnız başvurana hüküm ifade eder (m.10/2); yetkisiz idareye yapılan başvuru yetkili komisyona iletilir (m.10/3).

---

## Yol seçimi — karar tablosu

| Durum | Öneri | Gerekçe |
|---|---|---|
| Kaynak hukuki yorum (GTİP, kıymet yöntemi), güçlü emsal var | İtiraz → ret hâlinde dava | Uzlaşma tutanağı davayı kapatır |
| Olgu tartışmalı ama ceza katı ağır, emsal belirsiz | Önce uzlaşma (süreyi durdurur), olmazsa kalan sürede itiraz | Uzlaşma süresi itiraz süresini yemez (m.244/1) |
| Vergi kabul, yalnız ceza tartışmalı | Ceza için uzlaşma ya da kısmi itiraz | Kısmi işlem mümkün `[incele]` |
| 5607 soruşturması var | Uzlaşma yok; itiraz ve dava + ceza yargılaması koordinasyonu | m.244/2 |
| 15 gün geçti | İtiraz yolu kapandı; dava için idari başvuru ön şartı karşılanmadığından dava da büyük ihtimalle usulden düşer 🔴 | m.242; Danıştay 7. D. (→ `gumruk-davasi.md`) |
| Kendi beyanına dayalı tahakkuk, ihtirazi kayıt yok | Geri verme (m.211, 3 yıl) dene; ticaret politikası önlemine tabi eşyada kıymet artırımı geri verilmez | → `gumruk-kiymeti-ve-geri-verme.md` |

---

## Kontrol listesi

1. Tebliğ tarihi belgeli mi? 15. gün hangi tarih; tatile denk geliyor mu? 🔴 süre
2. Tebliğ, yükümlülüğün doğduğu tarihten (genellikle beyanname tescili, m.181/1) itibaren 3 yıl içinde mi yapılmış? Değilse zamanaşımı iddiası.
3. Kararın gerekçesi somut mu: hangi GTİP, hangi kıymet unsuru, hangi menşe kuralı, hangi laboratuvar sonucu?
4. Kimyevi tahlile dayanıyorsa tahlile **ayrıca 15 gün içinde** gümrük ve muhafaza başmüdürlüğüne itiraz ve ikinci tahlil imkânı. Teşkilat adı güncel değil; bugünkü merci `[doğrula]`.
5. Ceza maddesi doğru mu, kat ve eşik (ör. m.234/1-a'da beyan ile tespit arasındaki vergi farkı yüzde beşi aşmadıkça bu ceza yok) uygulanmış mı? Katlar 2014 sonrası tarihçede izlenemiyor `[doğrula]`. Karardaki tutarı `legal_calculate_tax` `hesap: "gumruk_ceza"` ile yeniden hesapla (fiil tarihi, kod, matrah, tespitten önce bildirim); fark varsa kat, asgari tutar ve %10 indirimini karşılaştır. 241/1 cezasında aykırı yükümlülük yalnız yönetmelik, tebliğ ya da genelgedeyse AYM iptalini ileri sür (E.2025/269, K.2026/72, RG 02.06.2026); fiil öncesiyse ve ceza kesinleşmemişse lehe hüküm `[doğrula]`. İdarenin yazılı yanlış izahatına dayanan hatada ceza ve faiz yok (m.231/5).
6. Birden fazla beyanname için tek karar düzenlenmiş mi (konu ve yükümlü aynı, bağlılık varsa mümkün)?
7. Dolaylı temsilci (gümrük müşaviri) de muhatap mı? Sorumluluğu bilme/bilmesi gereken hâllerle sınırlı (m.181/2).
8. Kaçakçılık bağlantısı var mı?
9. İtiraz mı, uzlaşma mı — tablo + parasal karşılaştırma `[incele]`.
10. Ödeme süresi: itiraz ödeme süresini keser; uzlaşmada 1 ay; teminat gerekir mi?

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Karar size ne zaman ve nasıl tebliğ edildi? Zarfı/e-tebligat kaydını paylaşır mısınız? | Süre |
| Beyanname ne zaman tescil edildi, hangi rejim? | Zamanaşımı, rejim |
| İdare neye dayanıyor: GTİP, kıymet, menşe belgesi, laboratuvar, yurt dışı doğrulama? | Referans dosyası |
| Beyannameye ihtirazi kayıt koydunuz mu? | Kendi beyanına itiraz |
| Savcılık bildirimi, el koyma ya da kaçakçılık tutanağı var mı? | Uzlaşma yasağı |
| Daha önce aynı eşya için BTB, BMB ya da emsal karar aldınız mı? | Savunma delili |
| Tutar ne kadar (vergi + ceza ayrı ayrı)? | Komisyon yetkisi, harç, kanun yolu sınırı |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4458" law_type: "Kanun" article_no: "242" | "244" | "197" | "198" | "231" | "232" | "234" | "243"
legal_get_statute_article law_no: "15261" article_no: "9" | "10" | "11" | "18" # Gümrük Uzlaşma Yönetmeliği
legal_search_official_gazette query: "Gümrük Uzlaşma Yönetmeliği" search_in: "title" sort_by: "date_desc"
legal_search_cases mahkeme: "danistay" sorgu: "<uyuşmazlık kaynağı> ek tahakkuk 4458 itiraz" tarih_baslangic: "<son 3 yıl>"
legal_check_holiday tarih: "<15. gün>"
```

---

## Çıktı iskeleti

```markdown
## Ek tahakkuk ve ceza kararı — [beyanname/karar no]
### Son gün: [tarih] (itiraz ve uzlaşma, m.242/1 ve m.244/1)
| Kalem | Tutar | Dayanak | Tartışma noktası | Önerilen yol |
### Seçenekler ve sonuçları (itiraz / uzlaşma / ikisi sırayla / ödeme)
### İtiraz dilekçesi unsurları (devir için)
- Merci: [kararı veren müdürlüğün bağlı olduğu Gümrük ve Dış Ticaret Bölge Müdürlüğü]
- Karar künyesi, tebliğ tarihi, beyanname künyesi
- İtiraz gerekçeleri (usul → esas), deliller, istem: kararın kaldırılması / kısmen kaldırılması
```

---

## Sık hatalar

- 🔴 "İtiraz süresi geçti, doğrudan dava açarız" demek (itiraz dava ön şartı; → `gumruk-davasi.md`).
- 🔴 Uzlaşma ve itiraz sürelerini ayrı ayrı 15'er gün sanmak; ikisi de tebliğden işler, uzlaşma talebi itiraz süresini durdurur.
- 🟠 "Gümrük cezaları uzlaşmaya girmez" demek (m.244/1-c).
- 🟠 Kaçakçılıkla ilişkili fiilde uzlaşma önermek (m.244/2).
- 🟠 Ödeme süresi ile itiraz süresini karıştırmak (itiraz ödeme süresini keser, m.198/2).
- 🟡 Kimyevi tahlile ayrı itirazı atlamak (m.243).

---

## İdare tarafı
→ `gumruk-idaresi-tarafi.md` (itirazın 30 günde karara bağlanması, gerekçe, uzlaşma komisyonu).

---
