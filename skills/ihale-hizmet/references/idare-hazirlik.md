# İdare hazırlığı — hizmet alımı ihalesi (aşama 1)

İhtiyaçtan ilana kadar: yaklaşık maliyet, yeterlik kriterleri, iş deneyimi oranı, benzer iş tanımı, kalite ve diğer belgeler, sınır değer seçeneği, fiyat farkı maddesi. Amaç: **dokümanı şikâyette ayakta kalacak şekilde hazırlamak.** Aynı liste istekli için "itiraz edilebilir mi" listesidir (`istekli-dokuman-ve-teklif.md`).

- **İdare ne yapmalı:** her kriteri "ihale konusu işle orantılı mı, rekabeti daraltıyor mu" sorusuyla gerekçelendir, gerekçeyi ihale işlem dosyasına koy.
- **İstekli neye bakar:** aynı kriterin mevzuattaki alt-üst sınırına ve emsal KİK kararlarına.

---

## 1. Hizmetin niteliği ve yaklaşık maliyet

- [ ] Danışmanlık mı, personel çalıştırılmasına dayalı mı, dayalı değil mi? (SKILL.md Adım 1). Personele dayalıysa 4734 m.62/e-1 yasağı idare türü için kontrol edildi mi? 🔴 `[incele]`
- [ ] Mal, hizmet ve yapım arasında **kabul edilebilir doğal bağlantı** yoksa bir arada ihale edilmez. Örnek dosyada 31 kalemin bir kısmı parça değişimi (enkoder, röle, şalter, valf): ağırlık maldaysa tür seçimi sorgulanabilir `[incele]`.
- [ ] **Personele dayalı işte YM:** personel maliyeti, tarım dışı 16 yaş üstü brüt asgari ücret + işveren payından az olamaz; nakdi yemek/yol brüt tutarları ve aylık gün sayısı şartnamede; kısa vadeli sigorta kolları prim oranı şartnamede; asgari ücretin üstü ödenecekse "% fazlası" oranı şartnamede. "Brüt asgari ücretin işverene maliyetinin % fazlası" biçiminde belirleme yapılamaz.
- [ ] YM hesap ve güncelleme yöntemi Hizmet Yön. m.7-9'a göre (piyasa fiyat araştırması, kamu fiyatları); güncelleme gerekiyorsa `legal_calculate_tender` `tutar_guncelle` (`belge: yaklasik_maliyet`) — araç yoksa Yİ-ÜFE oranıyla elle, `[incele]`. Metin: fiyat kaynakları (kamu fiyatları, idarelerin aynı/benzer iş fiyatları, oda fiyatları, piyasa fiyat teklifleri ortalaması, BUT/SUT) öncelik sırası olmadan kullanılır, rayici yansıtmayan teklif gerekçesiyle dışarıda kalır (m.8/2-4); kâr en fazla %7 ve cetvelde gösterilir (m.9/3); ilk ilan tarihine kadar endeksle güncellenir (m.9/4); asgari ücret değişiminde ihale komisyonu ihale tarihine kadar günceller (m.9/5); fiyat farkı öngörülen işte güncelleme Pn ile (m.9/6, RG 30/7/2025).
- [ ] YM isteklilere duyurulmaz (4734 m.62/d).

## 2. Yeterlik kriterlerinde genel ilke

- [ ] Yeterlik kriterleri ve belgeler **rekabeti engelleyecek şekilde belirlenemez**; ilanda ve idari şartnamede yazılmamış belge sonradan istenemez. İdari şartname m.7 dışındaki belgeler değerlendirmede dikkate alınmaz (örnek şartname m.7.5) `[kullanıcı verdi]`.
- [ ] Kısmi teklife açıksa her kısım için kriterler ayrı ayrı gösterilir. **Örnek dosyada çelişki:** m.2.1-ç "2 Kısım (31 Kalem)" ama m.20.1 "işin tamamı için teklif verilecektir" — kısım ibaresi zeyilnameyle düzeltilmeli 🟡 `[incele]`.
- [ ] İş deneyimi belgesinin istenmesi: YM'si 13/b-2 hizmet üst limiti ile eşik arasında olan işlerde zorunlu; altında idarenin takdirinde; hizmet alımı ihalesiyle yapılan danışmanlıkta altında da zorunlu. Limitleri `usul_kontrol` / `legal_get_social_parameters` (`ihale_ilan_13b_mal_hizmet_ust`, `ihale_esik_mal_hizmet_*`) ile ilan dönemine göre çek.

## 3. İş deneyimi oranı (Hizmet Yön. m.39)

- [ ] Belge: **son beş yıl** içinde kabulü tamamlanan, kamu veya özel sektörde **bedel içeren tek sözleşme**; devredilen işlerde %80 gerçekleşme şartı; teknolojik ürün deneyim belgesi de kabul.
- [ ] **Oran:** açık ihale ve 21/b, c, f'de teklif edilen bedelin **%25-%50** aralığında idarece belirlenen oran; belli istekliler ve 21/a, d, e'de YM'nin %25-%50'si aralığında parasal tutar. Çok yıllı işte oran bir yıldan fazla süreli işte 4/5, iki yıldan fazlada 3/5, üç yıldan fazlada 2/5 alınır.
- [ ] İş ortaklığı: pilot ortak en az %70, diğer her ortak en az %10, diğerlerinin toplamı en az %30.
- [ ] Örnek: %25 seçilmiş (alt sınır) ✅ — oran yönünden şikâyet zayıf; daraltma riski benzer iş tanımında.

## 4. Benzer iş tanımı — dar tanımın rekabete etkisi

- [ ] **Tanım:** benzer iş, ihale konusu iş veya bölümleriyle nitelik ve büyüklük bakımından benzerlik gösteren, aynı veya benzer usullerle gerçekleştirilen; teçhizat, ekipman, mali güç, uzmanlık, personel ve organizasyon gerekleri bakımından benzer özellik taşıyan işlerdir.
- [ ] Birden fazla iş benzer iş sayıldıysa "birlikte mi ayrı ayrı mı" yazılmalı; yazılmamışsa her biri ayrı ayrı benzer iş sayılır (KİGT 72.3). Örnek m.7.3.1.1 "birlikte veya ayrı ayrı" diyor ✅.
- [ ] **Test (idare öz denetimi):** (a) Benzer iş, ihale konusu işten **daha dar** mı? (b) Belirli bir makine markası/modeli, tek idare ya da tek tesis deneyimine mi bağlanmış? (c) Aynı teçhizat ve uzmanlığı gerektiren yakın işler (ör. demiryolu araç bakım tezgâhları, CNC takım tezgâhı bakım-onarımı, raylı sistem bakım atölyesi) dışarıda mı kalıyor? (d) Önceki yıl ihalesinde daha geniş tanım kullanılıp kullanılmadığı.
- [ ] **Emsal:** KİK, benzer iş tanımının ihale konusu işten de dar belirlenmesini katılımı engelleyici bulup ihaleyi iptal etmiştir (raylı sistem idaresinin toplu taşıma aracı bakım-onarım ihalesi; tanım "mobil yol yardım ve manevra ile birlikte şehir içi otobüs bakım-onarımı" idi; Kurul 4734 m.54/11-a ile iptal). Ters yönde: başvuranın önerdiği tanımın idareninkinden **daha dar** olduğu, idarenin tanımının uygun bulunduğu karar var.
- [ ] **Emsal uygulanabilirlik ölçütü:** "dar benzer iş" iptal emsalleri (KİK 2025/UH.I-296; KİK 2026/UH.I-567 — ihale konusunun üç ana kaleminden yalnız birini kapsayan tanım) yalnız tanım ihale konusu işten **dar** olduğunda işler. Tanım ihale konusuyla aynı ya da daha genişse bu emsaller uygulanmaz; şikâyet riski tanımın kapsam belirsizliğindedir (açıklama/zeyilname).
- [ ] Benzer iş ilanda da yer aldığından ona yönelik şikâyet süresi **ilk ilan tarihinden** işler (4734 m.55/1); idare ilk ilan tarihini kayıtta tutmalı.
- [ ] **Örnek dosya:** "tren teker tornası ağır bakım işleri, torna bakım işleri" (m.7.3.1.1). "Torna bakım işleri" ibaresi genel torna tezgâhı bakımını da kapsıyor gibi okunabilir; idare bunun kapsamını (yalnız teker tornası mı, her türlü CNC torna mı) açıklama ya da zeyilnameyle netleştirmeli 🟠 `[incele]`. Yalnız "zemin altı teker tornası" diye okunursa dar tanım riski 🔴 (Türkiye'de bu tezgâhları bakımı yapmış firma sayısı sınırlı — olgu araştırması gerekir `[OLGU GEREKLİ]`).

## 5. Kalite, standart ve diğer belgeler

- [ ] Kalite ve standart belgeleri (Hizmet Yön. m.42) işin niteliğiyle ilgili ve orantılı mı? m.42/1 dokümanda düzenlenebilecek belgeleri sayar: kalite yönetim sistem belgesi, çevre yönetim sistem belgesi, hizmet yeterlilik belgesi, deney-analiz-kalibrasyon laboratuvarı ve muayene kuruluşu kalite yeterliği. Belgelendirme kuruluşu TÜRKAK ya da IAF karşılıklı tanıma antlaşmasındaki bir kurumca akredite olmalı; TÜRKAK teyidi gerekir (TÜRKAK markalı belgede gerekmez); belge ihale tarihinde geçerli olmalı; iş ortaklığında bir ortağın sunması yeterli (m.42/2, 4, 5).
- [ ] **Örnek dosyada orantılılık riski** (m.7.3.3 tablosu): ISO 9001 (olağan), **TS EN ISO/IEC 27001** bilgi güvenliği ve **ISO/IEC 20000-1** BT hizmet yönetimi (tezgâh bakımında bağlantısı açıklanmalı), **CE uygunluk belgesi** (hizmet için değil ürün için düzenlenir; hangi ürün?), **ECM** (demiryolu araçları bakımından sorumlu kuruluş sertifikası; tezgâh bakımında gerekliliği tartışmalı), **üretici yetki belgesi** ("1 adet zemin altı tekerlek torna makinesi üreticisinden"; tek üreticiye bağlılık ve yerli istekliyi dışlama riski). Her biri için idare gerekçe yazmalı; gerekçesizse 🟠-🔴 `[incele]`. ISO/IEC 27001 ve 20000-1'in m.42/1'deki belge türlerinden hangisine girdiği de ayrıca tartışılabilir `[incele]`.
- [ ] Alt yüklenici yasağı (m.18.1) ve konsorsiyum yasağı (m.17.1) işin niteliğiyle tutarlı mı? `[incele]`

## 6. Değerlendirme, sınır değer ve teminat maddeleri

- [ ] EAAT: yalnız fiyat mı, fiyat dışı unsur mu? Fiyat dışı unsur seçildiyse Hizmet Yön. m.61 ve şartname 33.1'de puanlama.
- [ ] **Sınır değer seçeneği:** YM eşik değerin yarısına eşit veya üstündeyse açıklama isteme (59/2-a) zorunlu; yarısına kadarsa (a) veya (b) — açıklama istemeden ret — seçilir; Kurum listesindeki işlerde (b) zorunlu. Seçenek ilanda ve dokümanda yazılmalı.
- [ ] Personele dayalı olmayan işte **R katsayısı** iş türüne göre ve ilgili dönem için şartnameye yazılır (örnek m.45.1: "Diğer Hizmetler/0,78"). R'yi beceri metninden alma; Kurumun ilan ettiği tabloyu ilan tarihine göre kontrol et (KİGT 79.1.3: her yıl 1 Şubat'tan geçerli) `[doğrula]`.
- [ ] Yerli istekli fiyat avantajı (örnek m.33.3.1: %15): hizmet alımında yerli istekliler lehine **%15'e kadar** fiyat avantajı idarenin takdiridir; Kanun bunu eşik değerin üstüyle sınırlamaz. Eşik altında ayrıca yalnız yerli isteklilerin katılması öngörülebilir; ortak girişimin yerli sayılması için bütün ortaklar yerli olmalı (4734 m.63/a, b, f).
- [ ] Geçici teminat teklif bedelinin en az %3'ü (örnek m.26.1); kesin teminat sınır değerin üstünde/eşitte teklif fiyatının %6'sı, altında **YM'nin %9'u** (örnek m.37.1; Hizmet Yön. m.55/1-2; Kuruma yetki 4734 m.43/3: YM'nin %6-15'i).

## 7. Fiyat farkı ve sözleşme maddeleri

- [ ] Fiyat farkı verilecek mi? Verilmeyecekse bile tip şartname, **mücbir sebep veya idareden kaynaklanan süre uzatımında** yürürlükteki esaslara göre fiyat farkı hesaplanacağını yazar (örnek m.43.1, sözleşme m.14.2). Personele dayalı işte işçilik fiyat farkı esasları ayrıca → `personel-calistirma-ve-fiyat-farki.md`.
- [ ] Sözleşme tasarısı: süre (örnek 6 ay), işyeri teslimi (imzadan 10 gün), ceza oranı (örnek ilk sözleşme bedelinin on binde 2'si; toplam %30 sınırı), iş artışı (%20, 4735 m.24), garanti (2 yıl), eğitim yükümlülüğü. Özel ve ağır aykırılık maddeleri boş bırakılmışsa yalnız genel oran uygulanır (örnek m.16.1.5) `[kullanıcı verdi]`.

## 8. İlan ve doküman değişikliği

- [ ] Açıklama talebi ihale tarihinden 20 gün öncesine kadar; cevap ve zeyilname en geç 10 gün önce bilgi sahibi olunacak şekilde; zeyilnameyle bir defa en fazla 20 gün erteleme; zeyilnameden önce teklif verene geri çekip yeniden verme imkânı (örnek m.13-14; 4734 m.29).
- [ ] İlanda da bulunan hata → 4734 m.26 düzeltme ilanı; süre yetmezse iptal (örnek m.14.5).

---

## Görüşme soruları (idare)

1. İşin yaklaşık maliyeti eşik değerin yarısının üstünde mi? (sınır değer seçeneği)
2. Personel sayısı dokümanda belirli mi, YM'nin ne kadarı işçilik? (personele dayalılık)
3. Benzer iş tanımını kaç firmanın karşılayabildiğini araştırdınız mı? Önceki ihalelerde kaç teklif geldi?
4. Her kalite belgesinin işle bağlantısı nedir?
5. Kalemlerin ne kadarı parça değişimi (mal) ne kadarı işçilik/hizmet?

## Çıktı

SKILL.md Adım 7 iskeleti; "Önerilen düzeltme" bölümünde her bulgu için **zeyilname metni önerisi** ve gerekçe. Zeyilname ya da açıklama yazısı metni → `ihale-belgeleri`.
