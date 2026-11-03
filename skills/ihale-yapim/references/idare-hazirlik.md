# Aşama 1 — İdare hazırlığı (yapım)

Yaklaşık maliyetten ilana kadar idarenin kurduğu her tercih, sonradan şikâyetin hedefidir. Bu dosya iki soruyu birlikte
yürütür: **İdare:** "bu tercih mevzuata uygun ve savunulabilir mi?" — **İstekli:** "bu tercih aykırıysa doküman
şikâyetine konu olur mu?" (doküman şikâyeti süresi ve zinciri `ihale-sikayet`'te).

Tüm madde atıfları 2026-11-01'de çekildi; ilan tarihinde yürürlükteki metinle karşılaştır.

---

## 1. Yaklaşık maliyet (YM)

- [ ] YM KDV hariç; miktarlar proje, metraj ve mahal listesinden (Yapım Yön. m.9); fiyatlar kurum birim fiyatları ve
  piyasa araştırması; yüklenici kârı ve genel gider içermeyen fiyatlarla bulunan tutara kâr ve genel gider eklenir
  (m.10–11). Hesap cetveli ve icmal, hazırlayanlarca imzalanıp **ihale onay belgesine eklenir** (m.11/2).

- [ ] **Fiyat kaynakları (m.10/1):** idarenin benzer işlerdeki sözleşme fiyatları, kamu kurumlarının birim fiyat ve
  rayiçleri, meslek odası/üniversite rayiçleri, deneyimli yüklenicilerden alınan maliyetler, piyasa araştırması. Bunlar
  **öncelik sırası olmaksızın** biri, birkaçı ya da tamamı kullanılır (m.10/2). Güncelliğini kaybetmiş kamu birim
  fiyatı ilgili endeksle güncellenir (m.10/5, Ek: RG-30/7/2025). Piyasa araştırmasında aynı koşullu yazı, KDV hariç
  fiyat; tereddütte oda rayici (m.10/3-4).

- [ ] **Güncelleme:** YM ilandan önceki bir ayda hazırlandıysa güncelle. Fiyat farkı öngörülmeyen işte Yİ-ÜFE oranı;
  öngörülen işte fiyat farkı katsayısı (Pn) (m.11 son fıkra). Araç: `tutar_guncelle` (`belge: yaklasik_maliyet`);
  yoksa `k = E(ilan−1) / E(YM hesap ayı−1)` elle, `[incele]`.
- [ ] YM gizlidir (4734 m.62/d); dışa giden yazıya konmaz. İlk oturumda isteklilere açılır.
- [ ] Yapımda ihaleye çıkmadan önce: arsa, mülkiyet, kamulaştırma, gerekirse imar işlemleri ve **uygulama projesi**
  (4734 m.62/1-c); onarım işlerinde kesin proje üzerinden ve birim fiyat teklif alınabilir; su depoları gibi işlerde
  arsa/kamulaştırma şartı aranmaz. Çok yıllı işte ilk yıl ödeneği proje maliyetinin %10'undan az olamaz (m.62/1-a).

## 2. YM'ye göre istenecek belgeler (Yapım Yön. m.30)

YM'yi eşik değerle karşılaştır — eşik tutarını `legal_get_social_parameters` (`tur: "ihale_esik_yapim"`) ya da
`usul_kontrol`'den ilan döneminin değeriyle al.

| Belge | YM < eşik/10 | eşik/10 ≤ YM < eşik/2 | YM ≥ eşik/2 (ve belli istekliler) |
|---|---|---|---|
| Teklif vermeye yetki + **iş deneyim belgesi** | zorunlu | zorunlu | zorunlu |
| Ekonomik ve mali yeterlik (bilanço, iş hacmi) | **istenemez** | istenebilir | **zorunlu** |
| Kalite ve çevre yönetim sistem belgesi | istenemez | istenemez | istenebilir |

- [ ] Taahhütname istenemez (m.30/1-f). Kısmi teklifte YM işin tamamına göre (m.30/1-g).
- [ ] Bunların dışındaki 4734 m.10 belgeleri (makine-ekipman, teknik personel) işin niteliğiyle orantılı olmalı
  (m.30/1-e). Orantısız kriter doküman şikâyetinin en sık konusudur.

## 3. İş deneyimi oranı (Yapım Yön. m.39)

- [ ] İş deneyim belgesi her ihalede **zorunlu** (m.39/1). Belgeler ilk ilan tarihinden geriye **son 15 yıl** içinde
  geçici kabulü yapılan (ya da %80 gerçekleşen devam eden / devredilen) işler (m.39/2; 4734 m.10/1-b-2).
- [ ] Oran — açık ihale ve 21/b-c'de **teklif edilen bedelin**; belli istekliler ve 21/a-d-e'de **YM'nin**:

| YM | Alt sınır | Üst sınır |
|---|---|---|
| eşiğin iki katına kadar | %50 | %100 |
| eşiğin iki katı ve üzeri | %50 | %80 |

- [ ] İş ortaklığında pilot ortak asgari tutarın en az %80'i, diğerleri her biri en az %20'si; pilot tamamını
  sağlarsa diğerleri en az %40 oranında benzer olmayan yapım işi belgesi sunabilir (m.39/6-7).
- [ ] Mezuniyet belgesi: m.39/11 (tüzel kişinin en az 5 yıldır %51 ortağı), m.39/12 (15 yıldan fazlası için mezuniyet
  sahibine ait yapım işi belgesi). Dokümanda **hangi mühendislik/mimarlık bölümlerinin** denk sayıldığı yazılmalı
  (Benzer İş Grupları Tebliği m.2.14).

## 4. Benzer iş grubu seçimi (Benzer İş Grupları Tebliği m.2)

- [ ] İşin Ek-1 listesindeki **grubunu** tespit et; benzer işi o gruba atıfla belirle. Grup adları ve kapsamı Ek-1'den
  doğrulanır (araçta yok) `[doğrula]`.
- [ ] **Ayrıştırma yasak:** bir grup içinden bazı işleri seçerek benzer iş belirlenemez (m.2.1).
- [ ] Birden fazla gruba **"veya"** ile atıf yapılabilir; istekli herhangi birinin belgesini sunar (m.2.2).
- [ ] Birden fazla grubun **birlikte** aranması zorunluysa ihale **konsorsiyumlara açık** yapılmalıdır (m.2.3).
- [ ] **Onarım** ihalelerinde önce yapının temelden inşasını içeren grup yazılır ve benzer iş "X grubu veya X grubu
  işin onarım işi" şeklinde belirlenir; tamamlamada işin karakteristiğine bakılır (m.2.4).
- [ ] Yapının bir parçası tek başına ihale ediliyorsa, o parçayı **içeren** büyük işin belgesi de kabul edileceği
  yazılmalı (m.2.5, 2.6). Listede olmayan iş: Yönetmelik m.3 tanımıyla, rekabeti engellemeden (m.2.7).

## 5. Ekonomik ve mali yeterlik kriterleri (YM ≥ eşik/10 ise)

- [ ] **Bilanço** (m.35/3): cari oran ≥ 0,75; öz kaynak oranı ≥ 0,15; kısa vadeli banka borcu / öz kaynak < 0,50 —
  üçü birlikte. Kriterler yönetmelikte sabittir; idare bunları değiştiremez.
- [ ] **İş hacmi** (m.36): YM eşiğin üç katına kadarsa toplam ciro **ve** yapım işleri cirosu belgelerinin ikisi de
  istenir, istekli birini sunar; üç katı ve üzerinde yalnız yapım cirosu istenebilir (m.36/2). Açık ihalede toplam ciro
  teklifin ≥ %25'i, yapım cirosu ≥ %15'i (m.36/3-a).

## 6. Ekonomik açıdan en avantajlı teklif ve fiyat dışı unsur

- [ ] YM ≥ eşik/2 olan **birim fiyatlı** işlerde FDU kullanmak **zorunlu**; altında isteğe bağlı (Yapım Yön. m.61/2).
- [ ] Fiyat puanlamasında referans: en düşük geçerli teklif **ya da** sınır değer **ya da** sınır değerin üzerindeki
  ilk geçerli teklif (m.61/3) — hangisi seçildiyse şartname m.33'te formülle yazılır.
- [ ] FDU'nun parasal değeri ya da nispi ağırlığı, hesaplama yöntemi ve istenecek belgeler idari şartnamede **açıkça**;
  marka/modele dayalı olamaz; gerekçeli açıklama belgesi onay belgesine eklenir (m.62/2-4).

- [ ] "Teklif ile YM yapısının uyumu" unsurunda kalem seçimi, asgari–azami oranlar ve kalem puanları; asgari FDU puanı
  ve diğer unsurların üst sınırı Kamu İhale Genel Tebliği'nde: FDU'lu **birim fiyatlı** işte 53.3.4-(ğ) "teklif ile YM
  yapısının uyumu" unsuru **zorunlu** ve asgari puanı toplam FDU puanının **yarısının altında olamaz**; (ç) bendi
  (kendi malı ekipman) Yapım Yön. m.41'e göre puanlanır; diğer unsurların her biri **azami 5 puan**. (ğ) için iş
  kaleminin YM'deki ağırlığına göre dokümanda **asgari ve azami oran** yazılır; "YM ağırlığının %90-110'u" gibi göreli
  aralık yazılamaz (9/4/2026 eki). Teklif fiyatı puanı TP = Ptam − |RD − TF| × Ptam / RD; referans değere en az 50 tam
  puan (53.3.5).

## 7. Aşırı düşük teklif seçeneği ve N katsayısı

- [ ] YM ≥ eşik/2: **açıklama istenmesi zorunlu** (m.60/2-a, 3). YM < eşik/2: (a) açıklama iste ya da (b) aşırı düşük
  teklif sınır değerinin altını **açıklama istemeden reddet** — biri seçilip ilanda ve dokümanda yazılır (m.60/4); Kurum
  listesindeki işlerde (b) zorunlu (m.60/5).
- [ ] **N:** B, C, D, E gruplarındaki işler ve bunların tamamlama, onarım, güçlendirme, montaj işlerinde 1,00; diğer
  yapım işlerinde 1,20; farklı kısımlar varsa YM içindeki ağırlığı en büyük olanınki. Bakanlık ilanıyla 1,00–1,20
  arası farklı N olabilir. N, idari şartnamenin "Diğer hususlar" bölümünde yazılır (KİGT 45.1.1.1–45.1.1.3).

## 8. Fiyat farkı katsayıları

- [ ] Fiyat farkı verilecekse formül, katsayılar ve endeksler dokümanda (idari şartname m.43). Esas ve usulleri
  Cumhurbaşkanı belirler; sözleşmedeki fiyat farkı esasları **imzadan sonra değiştirilemez** (4735 m.8/1-2).

  `F = An × B × (Pn − 1)`, `B = 0,90`; `a + b1 + … + b6 + c = 1`; katsayılar idarece YM yapısına göre belirlenir
  (yapım fiyat farkı esasları — 2013/5217 eki — m.5 `[doğrula: ek metni araçta yok; RG 31.08.2013 PDF'inden]`).
  Ek kesin teminat: fiyat farkı olarak ödenecek bedelin %6'sı (Yapım Yön. m.56/10).
- [ ] Her katsayıya **uygun endeks**: a → TÜFE genel; b1 → CPA 23 ve altı; b2 → CPA 24; b3 → akaryakıt; b4 → CPA 19;
  b5 → CPA 16; b6 → idarenin seçtiği alt endeks; c → CPA 28 (makine-ekipman amortismanı) `[doğrula: esaslar m.5/4
  bentleri; 2013/5217 ek metni araçta yok]`. CB Kararı 10132 (yürürlük 01.09.2025) m.5/4 (b), (c), (d), (e), (g)
  bentlerine "alt endeksleri" ibaresini ekledi ve 2003=100 CPA 2008 seçilmiş sınıflar tablosunu kaynağa kattı.

- [ ] Katsayılar YM'deki girdi ağırlıklarıyla tutarlı mı? `fiyat_farki_yapim` ile toplam = 1 kontrolü; araç yoksa elle.

## 9. İlan ve doküman tutarlılığı

- [ ] İlan ile idari şartname aynı mı (iş deneyimi oranı, benzer iş, N, FDU, aşırı düşük seçeneği)? İlandaki
  m.24-25'e aykırı hata, ilan süresi 25/40 gün olan ihalelerde ilanın yayımını izleyen **15 gün**, diğerlerinde **10
  gün** içinde **düzeltme ilanıyla** giderilebilir; ilan hiç yapılmamışsa ya da ilan süresine uyulmamışsa ilan
  geçersizdir, yenilenir (4734 m.26). Dokümandaki hata zeyilnameyle düzeltilir (4734 m.29/2). Usul, eşik, ilan süresi →
  `kamu-ihale`; `usul_kontrol`.
- [ ] Teklif geçerlilik süresi ile geçici teminat mektubu son geçerlilik tarihi uyumlu mu (şartname m.24, m.26.3)?

---

> **Çalışılmış örnek — İKN 2026/1776751 (idare öz denetimi)**
> - Ekonomik ve mali yeterlik (m.7.2) **boş**, ama EAAT **FDU'lu** (m.33). YM ≥ eşik/2 olsaydı ikisi de zorunluydu
> (m.30/1-b-3, m.61/2). Doküman ancak YM eşiğin yarısının altındaysa tutarlı; FDU orada isteğe bağlı kullanılmış.
> İlk oturumda açıklanan YM ile kontrol et 🟠 `[incele]`.
> - Benzer iş "**A/IV ve A/XI** grubu işler". "ve" iki grubu birlikte istiyor okunursa m.2.3 gereği konsorsiyuma açık
> olmalıydı; şartname m.17.1 konsorsiyumu kapatıyor. "veya" anlamındaysa m.2.2'ye uygun. İş bir **tadilat/onarım**;
> m.2.4'teki "veya o grubun onarım işi" ibaresi yok 🟠 `[incele]`. Grup adları Ek-1'den `[doğrula]`.
> - %70 iş deneyimi her iki YM bandında (%50–100 / %50–80) sınır içinde ✅. N = 1,2: A grubu altyapı işi ✅.
> - Fiyat farkı: Σ = 1,000000 ✅; a = 0,734106 (işçilik ağırlıklı tadilat için makul, YM analizleriyle teyit);
> c için "28.14 Diğer musluk ve valfler" seçilmiş — c amortisman katsayısıdır, valf ise malzemedir 🟡 `[incele]`.
