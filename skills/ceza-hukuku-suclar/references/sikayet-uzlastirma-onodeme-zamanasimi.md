# Dava şartları ve düşme nedenleri — şikâyet, uzlaştırma, önödeme, zamanaşımı

## Ne zaman kullanılır
- "Şikâyet süresi geçti mi?", "şikâyetimi geri çekersem ne olur?", "uzlaştırmacı aradı, kabul edeyim mi?", "önödeme tebligatı geldi", "zamanaşımı doldu mu?" soruları.
- Her ceza dosyasında **esasa girmeden önce** usul ön kontrolü (SKILL.md Adım 4/2).
- Mağdur ya da kurum adına suç duyurusu / şikâyet hazırlığı.

---

## Süreler ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| Şikâyet süresi | 6 ay; şikâyet hakkı olanın fiili ve faili öğrendiği günden; zamanaşımını geçemez | TCK m.73/1-2 |
| Hakarette mutlak üst sınır | Şikâyete bağlı hakarette şikâyet süresi fiilden itibaren her hâlde **2 yıl** | TCK m.73/2 (7531/14) Geçiş: 14.11.2024'te soruşturma ya da kovuşturma evresine geçilmiş dosyalara uygulanmaz (CMK geçici m.7/1) |
| Uzlaşma teklifine cevap | Teklif tarihinden itibaren **7 gün**; bildirmezse reddetmiş sayılır | CMK m.253/4 (7531 ile 3 günden 7 güne) |
| Uzlaştırma süresi | Belgeler verildikten itibaren 30 gün; büro her defasında 20 günü geçmemek üzere en fazla iki kez uzatır | CMK m.253/12 |
| Önödeme | Savcılık tebliğinden itibaren **10 gün**; 10 gün içinde talep edilirse birer ay ara ile üç eşit taksit | TCK m.75/1 |
| Uzlaşma belgesi (teklif reddedildikten sonra) | En geç iddianamenin düzenlendiği tarihe kadar savcıya başvuru | CMK m.253/16 |
| Dava zamanaşımı | Ağırlaştırılmış müebbet 30, müebbet 25, ≥20 yıl hapis 20, 5-20 yıl arası 15, ≤5 yıl hapis veya adli para 8 yıl; 12-15 yaş yarısı, 15-18 yaş üçte ikisi | TCK m.66/1-2 |
| Zamanaşımının kesilmesi | Savcı huzurunda ifade/sorgu, tutuklama, iddianame, (kısmi de olsa) mahkûmiyet; kesilmede süre en fazla yarısı kadar uzar | TCK m.67/2-4 |
| Zamanaşımının durması | İzin/karar/bekletici mesele, kaçaklık kararı; uzlaştırma süreci (ilk tekliften rapora kadar); HAGB denetim süresi | TCK m.67/1; CMK m.253/21, 231/8 |
| Ceza zamanaşımı | Kesinleşmiş cezanın infazı için ayrı süreler | TCK m.68 |

`legal_calculate_deadline` bu sürelerin hiçbirini tanımıyor; elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]`.

---

## Kontrol listesi — şikâyet

1. Suç **şikâyete bağlı** mı? Madde metninde "şikâyet üzerine" ibaresi ya da ayrı soruşturma-kovuşturma koşulu maddesi (ör. hakarette m.131: kamu görevlisine görevinden dolayı hakaret hariç şikâyete bağlı; tehditte yalnız 106/1 ikinci cümle "sair kötülük" tehdidi).
2. Şikâyet süresi öğrenmeden mi işliyor ve zamanaşımı içinde mi; hakarette 2 yıl üst sınırı ve geçiş?
3. Şikâyet hakkı kimde (mağdur, kanuni temsilci; hakarette mağdurun ölümü hâlinde m.131/2'deki yakınlar)?
4. **Vazgeçme** (m.73/4-7): davayı düşürür; hükmün kesinleşmesinden sonra infazı engellemez; iştirak hâlinde biri için vazgeçme hepsini kapsar; vazgeçmeyi kabul etmeyen sanığı etkilemez; şahsi haklardan da açıkça vazgeçildiyse hukuk mahkemesinde dava açılamaz → **tek yönlü kapı**, `[incele]`.
5. Bir suçun işlenmesi amacıyla işlenen konut dokunulmazlığı ihlali ya da mala zarar vermede şikâyet aranmaz (hırsızlık amaçlı).

## Kontrol listesi — uzlaştırma (CMK m.253-254)

1. **Kapsam** (253/1): (a) soruşturması ve kovuşturması şikâyete bağlı suçlar; (b) şikâyete bağlı olup olmadığına bakılmaksızın sayılan TCK suçları: kasten yaralama (86/3 hariç; 88), taksirle yaralama (89), tehdit (**106/1 — hayata yönelik tehdit dahil**), konut dokunulmazlığının ihlali (116), iş ve çalışma hürriyetinin ihlali (117/1; 119/1-c), hırsızlık (**141 — nitelikli hırsızlık 142 değil**), güveni kötüye kullanma (**155/3 hariç**), dolandırıcılık (**157 — nitelikli dolandırıcılık 158 değil**), suç eşyasının satın alınması (165), çocuğun kaçırılması (234), ticari sır (239/4 hariç); (c) adli süreçteki çocuklarda üst sınırı üç yılı geçmeyen suçlar (mağdur gerçek veya özel hukuk tüzel kişisiyse).
2. **Kapsam dışı** (253/3): cinsel dokunulmazlığa karşı suçlar, ısrarlı takip (123/A) ve **hakaret (125 — bütünüyle, 7571 sonrası)**; uzlaştırma kapsamındaki suç kapsam dışı başka bir suçla **aynı mağdura** karşı birlikte işlenmişse uzlaşma uygulanmaz — **ancak** önödeme kapsamındaki suçla birlikte işlenmişse uzlaştırma kapsamındaki suç için uygulanır (7571).
3. **Hakaretin seyri:** 7531 (14.11.2024) ile yalnız 125/2 (mağduru muhatap alan sesli, yazılı, görüntülü ileti) uzlaştırma dışına alınıp önödemeye bağlandı; 7571 (25.12.2025) ile 125'in tamamı uzlaştırma dışına alındı, önödeme kapsamı "125/3-a (kamu görevlisine görevinden dolayı) hariç" bütün hakarete genişledi. Her iki kanunun geçiş maddesi: yürürlük tarihinde **uzlaşma sağlanmış** (7571) ya da soruşturma/kovuşturma evresinde bulunan (7531) dosyalar eski hükme göre sonuçlandırılır. Suç tarihini, uzlaştırma aşamasını ve yürürlük tarihini karşılaştır `[incele]`.
4. Birden fazla mağdur varsa **hepsinin** kabulü gerekir (253/7). Ulaşılamayan tarafta uzlaştırmasız sonuçlandırılır (253/6).
5. **Sonuç:** soruşturmada edim def'aten yerine getirilirse KYOK; ileri tarihe bırakılırsa kamu davasının açılmasının ertelenmesi (zamanaşımı işlemez); kovuşturmada düşme ya da **durma** (7531 öncesi HAGB). Uzlaşmada tespit edilemeyen ya da sonradan ortaya çıkan zararlar hariç tazminat davası açılamaz.
6. Uzlaştırma müzakerelerindeki açıklamalar hiçbir yargılamada delil olarak kullanılamaz (253/20); sonuçsuz uzlaştırma **tekrarlanamaz** (253/18) → tek yönlü kapı.
7. Uzlaştırma yapılmadan dava açıldıysa: mahkeme dosyayı uzlaştırma bürosuna gönderir (254/1) — eski YAML'daki "uzlaştırmaya gidilmeden dava açıldıysa düşme sebebidir" ifadesi **yanlış**; düşme ancak uzlaşma sağlanır ve edim yerine getirilirse.

## Kontrol listesi — önödeme (TCK m.75)

1. Kapsam: uzlaşma kapsamı dışında kalan, **yalnız adli para cezası** gerektiren ya da **hapis üst sınırı altı ayı aşmayan** suçlar; ayrıca 75/6'da sayılanlar (98/1, hakaret — 125/3-a hariç, 171, 182/1, 264/1, 278/1-2 ve özel kanun suçları). 75/6 kapsamındaki suçların beş yıl içinde tekrarında önödeme uygulanmaz.
2. Miktar: maktu adli para ya da alt sınır; hapiste gün başına kanunda yazılı tutar (metinden çek, `[doğrula]`); soruşturma giderleriyle birlikte.
3. Taksirli suçlar hariç, önödeme kararından itibaren beş yıl içinde yeni önödemeli suçta miktar yarı oranında artar.
4. Önödeme yapılmadan dava açıldıysa ya da vasıf değişikliğiyle önödemeli suça dönüştüyse mahkeme de önödeme önerir (75/2-3).
5. Önödeme yapılırsa KYOK / düşme; kayıt yalnız soruşturma için kullanılabilir (75/7). Malın geri alınması, şahsi hak ve müsadere saklı (75/5).

## Kontrol listesi — zamanaşımı

1. Suçun **kanundaki** cezasının üst sınırı (nitelikli hâller dahil; seçimlikte hapis) hangi kademeye düşüyor?
2. Başlangıç: tamamlanmış suçta suç günü; teşebbüste son hareket; kesintisiz suçta kesintinin gerçekleştiği gün; zincirlemede son suç; çocuğa karşı üstsoy ya da hüküm ve nüfuz sahibinin suçunda çocuğun 18 yaşını bitirdiği gün.
3. Kesme nedenleri ve **olağanüstü zamanaşımı** (kesilmeyle süre en fazla yarısı uzar) — iki süreyi ayrı hesapla.
4. Durma nedenleri: uzlaştırma süreci, HAGB denetimi, kamu davasının ertelenmesi, soruşturma izni (4483), bekletici mesele.
5. Zamanaşımı **re'sen** gözetilir; kanun yolunda da ileri sürülür.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Olay tarihi; fiili ve faili ne zaman öğrendiniz? | Şikâyet süresi başlangıcı |
| Şikâyet ne zaman, nereye yapıldı (kolluk, savcılık, e-Devlet)? | Süre ve geçerlilik |
| Uzlaşma teklifi ne zaman tebliğ edildi? | 7 gün |
| Önödeme tebliği ne zaman geldi? | 10 gün, taksit talebi |
| Mağdur sayısı? | Uzlaşmada hepsinin kabulü |
| Aynı mağdura karşı başka bir suç (ör. hakaret + tehdit) var mı? | 253/3 birlikte işlenme kuralı |
| İfade, tutuklama, iddianame, hüküm tarihleri? | Zamanaşımının kesilmesi |

---

## İdare / kurum tarafı

- Kamu kurumu ya da özel hukuk tüzel kişisi **suçtan zarar gören** sıfatıyla şikâyet eder ve uzlaşabilir (253/1: "gerçek veya özel hukuk tüzel kişisi"); kamu tüzel kişisi uzlaşmanın tarafı olamaz `[incele]`.
- Kurum adına şikâyetten vazgeçme ve uzlaşma için yetki belgesi ve iç onay gerekir; kamu kurumunda kamu zararı varsa vazgeçme kamu zararı sorumluluğu doğurabilir → `../../hakedis/references/sayistay-denetim-riski.md` `[incele]`.

---

## Şikâyet / suç duyurusu dilekçesi iskeleti (ORTAK-KURALLAR.md §13)

```markdown
[TASLAK BAŞLIĞI]
… CUMHURİYET BAŞSAVCILIĞINA
ŞİKÂYETÇİ / MÜŞTEKİ : [ad, T.C. kimlik no, adres] [___]
VEKİLİ : [___]
ŞÜPHELİ : [bilinen bilgiler; bilinmiyorsa "faili meçhul"]
SUÇ : [TCK m.__ — vasıf önerisi; vasfı savcılık belirler]
SUÇ TARİHİ / YERİ : [___]
ÖĞRENME TARİHİ : [şikâyete bağlı suçta zorunlu]
AÇIKLAMALAR : [kronolojik olay; her olgu yanında delil numarası]
DELİLLER : [ekran görüntüsü + URL/tarih tespiti, kamera kaydı (yer/saat — kayıtların silinme süresi kısa), tanık, rapor, banka dökümü]
HUKUKİ NEDENLER : [TCK m.__, CMK m.158]
SONUÇ VE İSTEM : Şüpheli hakkında kamu davası açılmasına; [koruma tedbiri / delil tespiti] talebimizdir. Şahsi haklarımızı saklı tutarız.
[tarih — imza]
```

KYOK kararına itiraz → sulh ceza hâkimliği, süre ve şekil CMK m.173'ten `[doğrula]`; dilekçe biçimi `../../ceza-ve-infaz-dilekce/SKILL.md`.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "5237" law_type: "Kanun" article_no: "66" | "67" | "68" | "73" | "75"
legal_get_statute_article law_no: "5271" law_type: "Kanun" article_no: "253" | "254" | "173"
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2024/11/20241114-1.htm" # 7531 (m.14-18)
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/12/20251225-33.htm" # 7571 (m.16, 24, 26)
legal_search_cases mahkeme: "yargitay" sorgu: "hakaret suçu önödeme kapsamına alındı 7571 geçici madde 8 uzlaşma sağlanmış dosya" tarih_baslangic: "2025-12-25"
```

---

## Çıktı iskeleti

```markdown
## Usul ön kontrolü — [suç, suç tarihi]
| Konu | Durum | Tarih / süre | Dayanak | İşaret |
| Şikâyet | şikâyete bağlı mı / süresinde mi | | TCK 73 | |
| Uzlaştırma | kapsamda mı / yapıldı mı / geçiş | | CMK 253 | |
| Önödeme | kapsamda mı / teklif edildi mi | | TCK 75 | |
| Dava zamanaşımı | olağan / olağanüstü son gün | | TCK 66-67 | |
### Tek yönlü kapılar (vazgeçme, uzlaşma reddi, önödeme) [incele]
```

---

## Sık hatalar

- 🔴 Hayata yönelik tehdidin (106/1 birinci cümle) uzlaştırmaya tabi olmadığını söylemek — 6763'ten beri tabidir.
- 🔴 7571 sonrası hakarette uzlaştırma önermek; ya da geçiş maddesini (uzlaşma sağlanmış dosyalar) atlamak.
- 🔴 Nitelikli hırsızlık (142) ve nitelikli dolandırıcılığı (158) uzlaştırma kapsamında saymak.
- 🟠 "Uzlaştırmaya gidilmeden dava açıldıysa düşme" demek (doğrusu: mahkeme uzlaştırmaya gönderir).
- 🟠 Uzlaşma teklifine cevap süresini 3 gün yazmak (7531 ile 7 gün).
- 🟡 Olağan ve olağanüstü zamanaşımını tek süre gibi hesaplamak.

---
