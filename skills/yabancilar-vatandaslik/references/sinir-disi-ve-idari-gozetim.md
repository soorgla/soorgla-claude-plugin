# Sınır dışı etme, idari gözetim, giriş yasağı ve tahdit kodu

## Ne zaman kullanılır
- "Deport kararı verildi", "geri gönderme merkezine (GGM) götürüldü", "imza yükümlülüğü / elektronik kelepçe getirildi", "Türkiye'ye giriş yasağım var", "G-87 kodu konmuş", "kırmızı bültenle yakalandı, sınır dışı ediliyor".
- İl göç idaresi ya da valilik görevlisi (idare tarafı) sınır dışı ve idari gözetim kararını kuruyor ya da aylık değerlendirmeyi yapıyor.

İkamet izninin iptali sınır dışının en sık sebebidir (m.54/1-f) → ayrıca `ikamet-izinleri.md`. Uluslararası koruma başvuru sahibi ise → `uluslararasi-koruma.md` (m.68 ayrı idari gözetim rejimi, m.54/2). Kırmızı bülten ve iade → ceza boyutu `../../ceza-hukuku-suclar/SKILL.md`, tutuklama ve CMK itirazı `../../ceza-ve-infaz-dilekce/SKILL.md`.

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Dayanak |
|---|---|---|
| Yakalanan yabancı hakkında sınır dışı değerlendirmesi ve karar | **48 saat** içinde | 6458 m.57/1 |
| İdari gözetim kararı alınan yabancının GGM'ye götürülmesi | **48 saat** içinde | 6458 m.57/2 |
| Sınır dışı kararına **dava** | Kararın **tebliğinden 7 gün** — idare mahkemesi; dava açan kişi kararı veren makama da bildirir | 6458 m.53/3 (7533/36) |
| Mahkemenin karar süresi | Dosya tekemmülünden (savunma ya da savunma süresinin geçmesi) ya da ara karar/duruşma tamamlanmasından itibaren **15 gün**; karar **kesin**; duruşma mahkemenin takdirinde | 6458 m.53/3 |
| Davacının adresine tebligat yapılamazsa | İYUK m.26/3'teki süre **iki ay** olarak uygulanır | 6458 m.53/3 |
| Sınır dışı edilmeme güvencesi | Dava süresi içinde ve yargılama sonuçlanıncaya kadar sınır dışı edilmez — **yabancının rızası saklı** | 6458 m.53/3 son cümle |
| Terke davet (çıkış için süre) | Kararda belirtilmek kaydıyla **15 günden az olmamak üzere 30 güne kadar**; kaçma riski, yasal giriş-çıkış ihlali, sahte belge, kamu düzeni tehdidi varsa süre tanınmaz | 6458 m.56/1 |
| GGM'de idari gözetim süresi | En çok **6 ay**; yabancının iş birliği yapmaması ya da doğru bilgi/belge vermemesi hâlinde en çok **6 ay daha** | 6458 m.57/3 |
| İdari gözetimin devamının değerlendirilmesi | Valilikçe **her ay**; zaruret yoksa derhâl sonlandırılır ve alternatif yükümlülük getirilir | 6458 m.57/4 (7196) |
| İdari gözetime karşı başvuru | Süre yok; sulh ceza hâkimi **5 gün** içinde karar verir; karar **kesin**; başvuru gözetimi **durdurmaz**; şartlar değişince yeniden başvurulabilir | 6458 m.57/6 |
| Alternatif yükümlülük süresi | Toplam **24 ayı** geçemez | 6458 m.57/A-2 |
| Elektronik izlemeye karşı başvuru | Sulh ceza hâkimi, **5 gün**, kesin; başvuru yükümlülüğü durdurmaz | 6458 m.57/A-5 |
| Türkiye'ye giriş yasağı süresi | En çok **5 yıl**; kamu düzeni/güvenliği açısından ciddi tehdit varsa Genel Müdürlükçe en çok **10 yıl daha** | 6458 m.9/3 |
| Giriş yasağına ya da kaldırılması talebinin reddine dava | Özel süre yok → **60 gün** (İYUK) | 2577 m.7 |

`legal_calculate_deadline` bu süreleri tanımıyor ("yukk_sinir_disi" → Kural bulunamadı); 7 günü elle say, son günü `legal_check_holiday` ile kontrol et.

**7533 değişikliği (RG 30.11.2024):** m.53/3 yeniden yazıldı; tekemmül kuralı, iki aylık tebligat süresi ve duruşmanın takdire bağlanması eklendi. Önceki metinde m.54/1-(b), (d), (k) kapsamındakiler için yargılama sürerken sınır dışı edilmeme güvencesine istisna bulunup bulunmadığını ve 7533'ün bunu değiştirip değiştirmediğini RG metninden kontrol et; tarihçe aracı bu madde için boş. Yeni m.53/3'ün son cümlesi istisnasız: "Yabancının rızası saklı kalmak kaydıyla, dava açma süresi içinde veya yargı yoluna başvurulması hâlinde yargılama sonuçlanıncaya kadar yabancı sınır dışı edilmez"; mahkeme 15 günde karar verir, karar kesindir. Geçici m.3: değişiklik 30.11.2024'ten sonra açılan davalara uygulanır.

**Kanun yolu:** sınır dışı davasında idare mahkemesi kararı **kesindir** (m.53/3). Diğer 6458 davalarında bölge idare mahkemesi ilk derece kararını kaldırıp yeniden karar verse bile **temyiz yolu kapalıdır** (7589 ile eklenen 2577 m.46/2-d). Eski YAML'daki "sınır dışı kararları BİM'de kesinleşir" yanlıştır. Kesin karardan sonra yol **AYM bireysel başvuru** (tedbir talepli) → `../../aym-aihm-basvuru/SKILL.md`.

---

## Kontrol listesi — sınır dışı kararı

1. **Tebliğ ve haklar bildirimi:** karar gerekçesiyle yabancıya, yasal temsilcisine ya da avukatına tebliğ edildi mi? Avukatı yoksa kararın sonucu, itiraz usulü ve süreleri hakkında bilgilendirildi mi (m.53/2)? Tebliğ belgesi, tercüman ve imza durumunu iste. Bilgilendirme yoksa süre başlangıcı ve iptal sebebi `[incele]`.
2. **Dayanak bent hangisi?** m.54/1'in 12 bendinden hangisi gösterildi: (a) TCK 59 mahkûmiyet, (b) terör/suç örgütü, (c) sahte belge, (ç) meşru olmayan geçim, (d) kamu düzeni/güvenliği/sağlığı tehdidi, (e) vize ihlali 10 günden fazla, (f) ikamet izninin iptali, (g) ikamet ihlali 10 günden fazla, (ğ) izinsiz çalışma, (h) yasal giriş-çıkış ihlali, (ı) giriş yasağına rağmen giriş, (i) uluslararası koruma sona erdi/reddedildi, (j) uzatma reddinden sonra 10 gün içinde çıkmama, (k) uluslararası kuruluşlarca tanımlanan terör örgütleriyle ilişki. Bent ile olgu örtüşüyor mu?
3. **(b), (d), (k) bentleri — somut olgu var mı?** Karar yalnız bir tahdit kodu ya da istihbari kayda mı dayanıyor? Mahkemeden dayanak bilgi ve belgelerin **celbini** iste. Danıştay 10. Daire, giriş yasağı davasında ara kararla istenen dayanak belgeleri idare sunamayınca ret kararını bozdu; AYM de dayanak bilgi ve belgelerin dosyaya getirilmesini etkili başvuru yönünden değerlendiriyor. "İstihbari bilgi asla delil olamaz" diye mutlak yazma; kural, mahkemenin dayanağı **denetleyebilmesi**dir `[incele]`.
4. **m.55 engelleri (bireysel değerlendirme şart):** sınır dışı edileceği ülkede ölüm cezası, işkence, insanlık dışı muamele riski; ciddi sağlık sorunu, yaş, hamilelik; hayati tedavinin sürmesi ve o ülkede tedavi imkânı olmaması; destek sürecindeki insan ticareti mağduru; tedavisi süren şiddet mağduru. Değerlendirme **herkes için ayrı** yapılır (m.55/2). Kararda m.55 değerlendirmesi yoksa 🔴 iptal sebebi `[incele]`. Hatay 1. İdare Mahkemesi, m.54/1-(b), (d) dayanaklı sınır dışı kararını, idarenin kronik hastalığı bulunan yabancının seyahat riskini hiç değerlendirmediği gerekçesiyle m.55/1-(b)'ye aykırı bularak iptal etti (E.2019/19 K.2019/649, kesin). Danıştay 10. Daire bu kararı **yalnız vekâlet ücreti yönünden** kanun yararına bozdu (E.2019/12748 K.2023/6982, 16.11.2023; RG 15.05.2024, 32547): m.55 gerekçesi Danıştay denetiminden geçmedi; karar, iptalle sonuçlanan davada avukatla temsil edilen davacı lehine vekâlet ücreti hükmedilmesi gerektiğine emsaldir.
5. **Kötü muamele riski ciddi mi?** Ülke raporları, kişinin geçmişi, uluslararası koruma başvurusu (yoksa yapılabilir mi → `uluslararasi-koruma.md`). Risk iddiası varsa AYM'ye **tedbir** talepli başvuru planını idare mahkemesi süreciyle paralel hazırla (başvuru yollarının tüketilmesinden itibaren 30 gün, haklı mazerette mazeretin kalkmasından 15 gün — 6216 m.47/5) `[incele]`. AYM İçtüzüğü m.73: başvurucunun yaşamına ya da maddi veya manevi varlığına yönelik ciddi tehlike anlaşılırsa Bölüm resen ya da talep üzerine tedbire karar verebilir; Komisyon kabul edilebilirliği derhâl inceleyip başvuruyu Bölüme gönderir; tedbirli başvuruda esas hakkındaki karar en geç altı ay içinde verilir, ihlal yokluğu ya da düşme kararıyla tedbir kendiliğinden kalkar.
6. **Aile ve özel hayat bağları:** Türk vatandaşı eş ya da çocuk, uzun süreli yasal ikamet, Türkiye'de eğitim gören çocuk. Ölçülülük ve aile hayatına saygı iddiası `[incele]`.
7. **Terke davet süresi verildi mi?** Verilmediyse m.56/1'deki istisna gerekçesi yazılı mı?
8. **Bağlantılı işlemler:** giriş yasağı (m.9), tahdit kodu, ikamet izninin iptali, vatandaşlığın geri alınması aynı olaydan doğuyorsa her birine **ayrı dava** gerekir; farklı mahkemelerde açılırsa bağlantı kararı için dosya Danıştay'a gider. Yetkili idare mahkemesi: işlemi yapan merciin (valilik; Genel Müdürlük işleminde Ankara) bulunduğu yer (İYUK m.32 genel yetki; m.33-37'deki özel kurallar bu işlemlere uymuyor).
9. **Rıza ve gönüllü geri dönüş:** kişi GGM'de "gönüllü dönüş" ya da "dava açmayacağım" yazılı beyanı imzaladı mı, hangi dilde, tercümanla mı? Rıza güvenceyi ortadan kaldırır (m.53/3) — beyanın geçerliliği `[incele]` 🔴.
10. **Ceza bağlantısı:** sınır dışı TCK 59'a (m.54/1-a) ya da kırmızı bültene dayanıyorsa ceza dosyasının durumu (kesinleşme, iade talebi, 6706 süreci) → ceza becerileri.

## Kontrol listesi — idari gözetim ve alternatifler

1. **Gözetim sebebi m.57/2'de sayılanlardan biri mi?** Kaçma ve kaybolma riski, giriş-çıkış kuralı ihlali, sahte/asılsız belge, tanınan sürede çıkmama, kamu düzeni/güvenliği/sağlığı tehdidi. Gerekçe somut mu, yoksa matbu mu?
2. **Alternatif yükümlülük değerlendirildi mi?** m.57/A: belirli adreste ikamet, bildirim (imza), aile temelli geri dönüş, geri dönüş danışmanlığı, gönüllü kamu hizmeti, teminat, elektronik izleme. m.57/2 kapsamında olup gözetime alınmayana bunlardan en az biri **zorunludur** (m.57/A-3); uymayan gözetime alınabilir (m.57/A-6).
3. **Süre ve aylık değerlendirme:** 6 ay doldu mu? Uzatma gerekçesi yabancının iş birliği yapmaması mı? Aylık değerlendirme kararları tebliğ edildi mi (m.57/5)? Tebliğ edilmeyen değerlendirme → sulh ceza başvurusu gerekçesi.
4. **Sınır dışının fiilen mümkün olmaması:** sınır dışı edilecek ülkeye fiilî imkân yoksa (sefer yok, ülke kabul etmiyor, m.55 engeli) gözetimin amacı kalmamıştır `[incele]`.
5. **GGM koşulları ve kötü muamele:** avukat ve aile görüşü, sağlık, kalabalık. AYM'de idari gözetim nedeniyle kötü muamele ve kişi hürriyeti iddiaları ayrıca incelenir; başvuru yollarının (sulh ceza, tazminat) tüketilmesi aranır.
6. **Uyruk tespiti için cihaz incelemesi** (m.57/8) yapıldıysa verinin amaç dışı kullanılmadığını sor.
7. Uluslararası koruma başvurusu varsa gözetim **m.68** rejimine geçer (en çok 30 gün) → `uluslararasi-koruma.md`.

## Kontrol listesi — giriş yasağı ve tahdit kodu

1. Yasak kim tarafından? Genel Müdürlük (m.9/1, kamu düzeni/güvenliği/sağlığı) mı, sınır dışı sonrası valilik ya da Genel Müdürlük (m.9/2) mi?
2. Süre: en çok 5 yıl; 10 yıl ek uzatmanın "ciddi tehdit" gerekçesi var mı?
3. Vize/ikamet ihlalinde kendiliğinden çıkış için valiliğe başvuran ve cezasını ödeyen yabancıya giriş yasağı konmayabilir (m.9/4); terke davete uyup süresinde çıkana da konmayabilir (m.9/5).
4. **Kaldırma ya da geçici giriş izni:** Genel Müdürlük yasağı kaldırabilir veya belirli süre için girişe izin verebilir (m.9/6) — önce idari başvuru, ret üzerine dava.
5. Kod listesi ve anlamları yayımlanmış bir düzenlemede bulunamadı; kodun anlamını idarenin savunmasından ve ara kararla istenecek belgelerden öğren, kendin anlam yükleme `[incele]`. Danıştay kararlarında geçen örnekler: G-87, "M-67 (INTERPOL/Yer ve Kimlik Tespiti Amaçlıdır)" (Danıştay 10. D. E.2021/3827 K.2025/4243). Eski YAML'daki "Ç-114" kodu doğrulanamadı.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Kararın tam adı, tarihi ve **tebliğ tarihi**; tebliğ kime, hangi dilde yapıldı? | 7 gün; haklar bildirimi |
| Kişi şu an nerede (GGM, karakol, serbest, imza yükümlülüğü)? Hangi il? | Sulh ceza başvurusu, yetki |
| Uyruğu, Türkiye'ye giriş şekli ve tarihi, sahip olduğu izinler (ikamet, çalışma, koruma)? | Dayanak bent |
| Ülkesine dönerse ne olur? Daha önce zulüm, tehdit, yargılama? | m.55, uluslararası koruma |
| Ağır hastalık, hamilelik, yaşlılık, tedavi süreci? | m.55/1-b, c |
| Türkiye'de eş, çocuk, Türk vatandaşı yakın, iş, okul? | Aile hayatı, ölçülülük |
| Hakkında ceza soruşturması, mahkûmiyet, kırmızı bülten var mı? | m.54/1-a, b; iade |
| GGM'de herhangi bir belge imzaladı mı (gönüllü dönüş, feragat)? | Rıza |
| Daha önce sınır dışı, giriş yasağı ya da tahdit kodu? | Bağlantılı davalar |
| Avukatlık ücreti karşılanabiliyor mu? | m.57/7 adli yardım |

---

## İdare tarafı (il göç idaresi / valilik)

- Karar formu: dayanak bent, somut olgu, **m.55 bireysel değerlendirmesi**, terke davet süresi ya da verilmeme gerekçesi, haklar bildirimi, tercüman. Matbu "kamu düzeni" gerekçesi dava riskini en çok artıran eksiktir.
- Tahdit koduna dayanan işlemlerde, mahkemenin ara kararına sunulabilecek dayanak belgeyi önceden dosyaya bağla; Danıştay 10. Daire belge sunulamayan dosyada ret kararını bozdu (E.2020/4631 K.2024/5214).
- İdari gözetimde: 48 saat kuralı, aylık değerlendirme ve tebliğ, alternatif yükümlülük değerlendirmesinin yazılı kaydı, 6 ay sonunda uzatma gerekçesi (iş birliği yapmama tutanağı).
- Dava açıldığı bildirilince sınır dışı işlemini durdur (m.53/3); rıza beyanı alınacaksa tercüman ve avukat erişimini kayıt altına al.
- İç değerlendirme ile yabancıya tebliğ edilecek kararı ayır; gizli istihbari yazıları karar metnine aktarma.

---

## Sulh ceza hâkimine başvuru iskeleti (idari gözetim / elektronik izleme)

Kanun yolu değildir; 6458 m.57/6 ve m.57/A-5 başvurusudur. Dilekçe idareye (GGM) verilirse derhâl hâkime ulaştırılır.

```markdown
[TASLAK — avukat incelemesi bekliyor]

[GGM'nin bağlı olduğu / kararın alındığı yer] NÖBETÇİ SULH CEZA HÂKİMLİĞİNE

BAŞVURAN: [ad, uyruk, yabancı kimlik no / pasaport no, GGM adı]
VEKİLİ: [___]
KARŞI TARAF: [___] Valiliği (İl Göç İdaresi Müdürlüğü)
KONU: [tarih] tarihli idari gözetim kararının (ya da uzatma / aylık değerlendirme kararının) kaldırılması ve serbest bırakılma; gerekirse 6458 m.57/A alternatif yükümlülük uygulanması talebidir.

AÇIKLAMALAR
1. Karar ve tebliğ: [___]
2. m.57/2 sebeplerinin bulunmadığı / somut olmadığı: [___]
3. Alternatif yükümlülüklerin değerlendirilmediği: [adres, imza, teminat önerisi]
4. Sınır dışının fiilen mümkün olmaması / m.55 engeli: [___]
5. (Uzatmada) iş birliği yapmama iddiasının gerçek dışı olduğu: [___]
6. Bekleyen sınır dışı davası: [mahkeme, esas no] — m.53/3

HUKUKİ SEBEPLER: 6458 m.57, m.57/A, m.55; Anayasa m.19; AİHS m.5
DELİLLER: [kira sözleşmesi, ikamet, aile belgeleri, sağlık raporu, dava dilekçesi örneği]
SONUÇ VE İSTEM: İdari gözetimin kaldırılmasına, başvuranın serbest bırakılmasına; olmadığı takdirde m.57/A'daki [___] yükümlülüğünün uygulanmasına karar verilmesini saygıyla arz ederim.
[Tarih — imza]
```

İdare mahkemesindeki sınır dışı davası dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`. Ek unsurlar: (1) başlıkta "6458 m.53/3 uyarınca 7 günlük süre içinde — ivedi", (2) karar veren makama başvurunun bildirildiğinin belgesi, (3) dayanak bilgi ve belgelerin celbi talebi, (4) m.55 değerlendirmesi yapılmadığı iddiası, (5) yürütmenin durdurulması talebi (dava açılması zaten sınır dışını durdurur; YD ayrıca giriş yasağı ve ikamet iptali için önemlidir) `[incele]`.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6458" law_type: "Kanun" article_no: "9" | "53" | "54" | "55" | "56" | "57" | "102"
legal_list_statute_articles statute_id: 69213 article_query: "idari gözetime alternatif" include_content: true # m.57/A
legal_search_statute_semantic mevzuat_no: "21460" sorgu: "idari gözetim altındaki yabancının dava dilekçesi yetkili idare mahkemesine" # Yönetmelik m.59
legal_get_statute_article law_no: "2577" law_type: "Kanun" article_no: "7" | "27" | "46"
legal_search_cases mahkeme: "danistay" sorgu: "<ör. G-87 tahdit kodu somut bilgi belge sunulamadı giriş yasağı>" tarih_baslangic: "2023-01-01"
legal_search_cases mahkeme: "anayasa" sorgu: "<ör. sınır dışı etme kötü muamele yasağı etkili başvuru tedbir>" tarih_baslangic: "2023-01-01"
legal_search_official_gazette query: "6458 sayılı Yabancılar ve Uluslararası Koruma Kanununun 53 üncü maddesi" date_from: "2019-01-01"
```

---

## Çıktı iskeleti

```markdown
## Sınır dışı / idari gözetim değerlendirmesi — [ad, uyruk] — [tarih]
### 🔴 Acil
| İşlem | Tebliğ | Süre | Son gün | Merci |
| Sınır dışı davası | | 7 gün | | İdare mahkemesi |
| İdari gözetime başvuru | — | her zaman | bugün | Sulh ceza hâkimi |
| AYM bireysel başvuru + tedbir (kesin karardan sonra) | | | | AYM |
### Dayanak bent ve olgu
### m.55 engelleri
### İdari gözetim: sebep, süre, alternatif
### Bağlantılı işlemler (giriş yasağı, ikamet iptali, vatandaşlık)
### Öneri
```

---

## Sık hatalar

- 🔴 Sınır dışı kararına 60 günlük genel dava süresini uygulamak (7 gün).
- 🔴 İdari gözetime itirazı idare mahkemesine yapmak (sulh ceza hâkimi); ya da sulh ceza başvurusunun gözetimi durdurduğunu sanmak.
- 🔴 GGM'de imzalatılan "gönüllü dönüş" beyanını sormamak (rıza güvenceyi kaldırır).
- 🟠 Sınır dışı davasında istinaf/temyiz planlamak (karar kesin; sonraki yol AYM).
- 🟠 Giriş yasağına ayrıca dava açmamak (ayrı işlem).
- 🟠 "İstihbari bilgi hiçbir zaman delil olamaz" diye mutlak yazmak; asıl talep dayanak belgenin celbidir.
- 🟡 m.102 para cezası tutarını metinden okumak (yeniden değerlenir).

---
