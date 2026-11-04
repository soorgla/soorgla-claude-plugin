# İdare hazırlığı: yaklaşık maliyet, teknik şartname, yeterlik, yerli malı

Mal alımında ilana çıkmadan önceki öz denetim. Aynı liste istekli tarafından "doküman hukuka uygun mu" sorusuyla
okunur (`istekli-dokuman-ve-teklif.md`). Parasal sınırlar metne yazılmaz: `usul_kontrol` ya da
`legal_get_social_parameters` `ihale_` kalemleri, **ilk ilan tarihinin dönemi**.

Mevzuat çağrısı: `legal_get_statute_article` `law_no: "12917"` `law_type: "Yönetmelik"` (Mal Yön.);
4734 / 4735 `law_type: "Kanun"`.

---

## A. Ödenek, kısımlara bölme, usul
- [ ] **Ödenek var mı?** "Ödeneği bulunmayan hiçbir iş için ihaleye çıkılamaz." Sözleşmede "ödenek olduğu takdirde
  ödenir" ibaresi bu kuralı ve 4735 m.4 eşitliğini zayıflatır 🟠. 
- [ ] Eşik değerin altında kalmak için kısımlara bölme yok mu? Aynı yıl içinde aynı kalemler parça parça mı alınıyor? 🔴
  
- [ ] Usul ve ilan süresi → `usul_kontrol`; genel kurallar `../../kamu-ihale/references/usul-esik-ve-ilan.md`.

## B. Yaklaşık maliyet (Mal Yön. m.7-8)
- [ ] KDV hariç, ihale onay belgesinden **önce** hesaplanmış ve dayanaklarıyla hesap cetvelinde mi? (m.7/1)
- [ ] Fiyat kaynakları m.8/3'teki yollardan: (a) kamu kurumları ve meslek kuruluşları, (b) üretici/satıcıdan fiyat
  bildirimi veya proforma, (c) Bütçe Uygulama Talimatı / Sağlık Uygulama Tebliği fiyatları, (ç) önceki alım
  sözleşme bedelleri endeksle güncellenmiş, (d) kamu kurumlarının internetteki fiyatları.
- [ ] Piyasayı yansıtmayan fiyat bildirimi dışlanmış ve gerekçesi cetvele yazılmış mı? (m.8/1-2)
- [ ] Kısmi teklif varsa her kısım için ayrı YM (m.7/3). İhale tarihine kadar değiştiyse komisyon gerekçeli günceller (m.7/7).
- [ ] Önceki sözleşmeden güncelleme → `tutar_guncelle` (`belge: yaklasik_maliyet`); araç yoksa elle endeks oranı, `[incele]`.
- [ ] YM tekliflerle birlikte açıklanana kadar gizli (m.7/5). 

## C. Teknik şartname (Mal Yön. m.14; 4734 m.12)
- [ ] Kriterler **verimlilik ve fonksiyonelliğe** yönelik, rekabeti engellemiyor, fırsat eşitliği sağlıyor mu? **Yerli
  malı teklifini engelleyen** düzenleme yok mu? (m.14/1)
- [ ] **Marka, model, patent, menşei, kaynak, ürün** belirtilmemiş ve belirli markaya yönelik özellik yok mu? İstisna:
  ulusal/uluslararası standart yoksa ya da özellik tanımlanamıyorsa, **"veya dengi"** ibaresiyle marka/model
  yazılabilir (m.14/3). "Veya dengi" yoksa 🔴.
- [ ] Ulusal standart varsa ona, yoksa yalnız uluslararası standarda uygunluk (m.14/2).
- [ ] Ambalaj, etiket, kullanım kılavuzu (m.14/4); montaj, satış sonrası servis, yedek parça (m.14/5).
- [ ] Teknik şartname, idari şartnamedeki yeterlik kriterleri ve belgeleriyle **uyumlu** mu (m.14/7)? Teknik şartnamede
  yazıp idari şartname m.7'ye konmayan belge yeterlik değerlendirmesinde dikkate alınmaz (tip idari şartname m.7.5).
- [ ] Düzenlemeler ihale ve muayene kabul komisyonunda **tereddüt yaratmayacak açıklıkta** mı (m.14/8)? "1. kalite",
  "piyasada kabul görmüş tescilli markalardan" gibi ölçütsüz ifadeler hem belirsiz hem dolaylı marka şartı riski taşır 🟠 `[incele]`.
- [ ] Özel imalatta prototip (m.14/9), uygunluk değerlendirme yükümlülükleri (m.14/11).
  

## D. Numune, katalog, demonstrasyon (Mal Yön. m.43)
- [ ] Numune isteniyorsa **hangi kalem, kaç adet, hangi aşamada, kim sunacak, hangi yöntemle değerlendirilecek**
  idari şartnamede yazılı mı? (m.43/2-a)
- [ ] **İhale tarihinden önce numune teslimi ya da "numunesi uygun olan teklif verebilir" düzenlemesi yapılamaz** 🔴.
- [ ] Değerlendirme yöntemi m.43/2-c'deki üçünden biri (komisyonun tamamı / uzman üyeler / uzman üyeler + kullanıcı personel).
- [ ] En az bir numune idarede **muhafaza** edilecek mi? (yeniden değerlendirme muhafaza edilen numune üzerinden, m.43/2-b)
- [ ] Teknik şartnameye cevap dokümanı isteniyorsa katalog da istenmesi zorunlu (özel imalat hariç, m.43/1).
- [ ] Sözleşme sonrası "ilk teslimden önce onay numunesi" ihale numunesi değildir; sözleşme/teknik şartname ile uyumunu
  ve gecikme etkisini kontrol et (`teslim-muayene-kabul.md`). 

## E. Yeterlik kriterleri (Mal Yön. m.26-27, 33-38, 42)
- [ ] Kriterler rekabeti engellemeyecek şekilde ve ilan + idari şartnamede birlikte yazılı mı? (m.26/1-2)
- [ ] **İş deneyimi istenebilir mi?** YM, 4734 m.13/b(2) mal üst limitine eşit veya altındaysa iş deneyim belgesi
  **istenemez** (belli istekliler hariç) → `ihale_ilan_13b_mal_hizmet_ust` (ilan dönemi) (m.27/1-b) 🔴.
- [ ] **Eşik altı** ihalede ekonomik-mali yeterlik belgesi (bilanço, iş hacmi) istenemez (m.27/1-c) →
  `ihale_esik_mal_hizmet_genel_butce` / `_diger`.
- [ ] Taahhütname yeterlik belgesi olamaz (m.27/1-ı); personel çalıştırma belgesi istenemez (m.27/1-g);
  laboratuvarın istekli bünyesinde olması şartı konamaz (m.27/1-ğ).
- [ ] Piyasaya arz için zorunlu izin (ör. gıdada Tarım ve Orman Bakanlığı **işletme kayıt/onay belgesi**) yeterlik olarak
  istenebilir; istenmezse muayene-kabulde sunulması düzenlenmeli (m.27/1-f). Belge kimde aranıyor: **istekli** mi,
  **üretici** mi? İdari ve teknik şartname aynı şeyi mi söylüyor? `[incele]`
- [ ] **İş deneyimi oranı:** açık ihale ve 21/b-c'de teklif bedelinin **%10'undan az, %40'ından fazla olmamak** üzere
  (m.37/3-a); belli istekliler ve 21/a-d-e'de YM'nin %10-40'ı arasında parasal tutar (m.37/3-b).
- [ ] Son beş yıl içinde **kesin kabulü** tamamlanan tek sözleşme; devredilen işte %80 şartı; ilk ilan ile ihale arası
  kesin kabul de sayılır (m.37/1-2). Teknolojik ürün deneyim belgesi seçeneği yazılı mı?
- [ ] **Benzer iş** tanımı: "ihale konusu alım veya bölümleriyle nitelik ve büyüklük bakımından benzer, aynı veya benzer
  üretim usul ve tekniği, teçhizat, mali güç, uzmanlık ve organizasyon gerekleri bakımından benzer" (m.3/1-b). Çok dar
  (yalnız belli kurum, belli marka) 🔴; çok geniş tanım rekabeti artırır ama yeterliği anlamsızlaştırabilir `[incele]`.
  Birden fazla iş sayılıyorsa "birlikte mi ayrı ayrı mı" yazılmalı. Kural KİGT 72.3'te ve **hizmet** bölümünde
  (açıklık yoksa her biri ayrı ayrı benzer iş sayılır); mal bölümünde (KİGT 54-62/A) karşılığı aramada çıkmadı —
  malda kıyasen kullan, `[incele]` `[doğrula: mal için ayrı hüküm araçta bulunamadı]`.
  
  Öz denetimde emsal ölçütü: "dar tanım" iptal emsalleri yalnız tanım ihale konusundan **dar** ise işler; aynı ya da
  daha geniş tanıma karşı bu emsallerle şikâyet riski düşüktür (`../../ihale-sikayet/references/kik-emsal-arama.md`).
  Benzer iş ilanda da yer aldığından buna yönelik şikâyet süresi **ilk ilan tarihinden** işler (4734 m.55/1).
- [ ] Bilanço istenirse üç oran birlikte ve sabit (m.33/3); iş hacmi istenirse açık ihalede toplam ciro %25 / mal satış
  cirosu %15 (m.34/6-a). İdare bu oranları değiştiremez. İlk dört ay kuralı (9/4/2026 değişikliği: iki önceki yıl,
  m.33/5, m.34/8).
- [ ] Yetkili satıcılık/imalatçılık şartı konduysa imalatçı, yetkili satıcı ve serbest bölge belgelerinin **birlikte**
  sayılması zorunlu (m.38/1).
- [ ] Kalite yönetim / çevre yönetim belgesi **yalnız özel imalatta** (m.42/1); standarda uygunluk belgesi m.42/2.
  

## F. Kısmi teklif, iş ortaklığı, konsorsiyum
- [ ] Çok kalemli alımda kısmi teklif idarenin takdiri; ama **yerli malı avantajı verilecekse kısmi teklif zorunlu ve her
  kısım tek kalem** (birbirini tamamlayan kalemler hariç) (Mal Yön. m.61/4).
- [ ] Kısmi teklifte yeterlik her kısım için ayrı değerlendirilir, belgeler işin tamamının YM'sine göre belirlenir (m.27/2).
- [ ] Konsorsiyum yasağı/izni işin uzmanlık gerektirmesiyle tutarlı mı? (m.26/7)

## G. Yerli malı ve yerli istekli (4734 m.63; Mal Yön. m.5, m.61)
- [ ] Eşik altı ihaleyi yalnız yerli isteklilere açma imkânı (m.61/1); ortak girişimde bütün ortaklar yerli (m.5/3).
- [ ] Yerli malına **%15'e kadar** avantaj; oran ilanda ve idari şartnamede yazılı (m.61/2-3).
- [ ] Orta-yüksek teknolojili ürün listesindeki mallarda ve yerli yazılımda **%15 zorunlu** (4734 m.63/c; m.61/6) — listenin
  ilan tarihindeki sürümü: Sanayi ve Teknoloji Bakanlığı yerli malı sayfası ve KİK duyurusu `[web araması — doğrulayın]`.
- [ ] Yerli malı **yerli malı belgesiyle** belgelenir (Bakanlığın usul ve esasları: Yerli Malı Tebliği SGM-2024/10, son
  değişiklik SGM-2026/3) (m.61/7).
- [ ] İdari şartnamede m.7.1(f) "yerli malı belgesi" satırı var ama m.33.3 "boş bırakılmıştır" ise **avantaj yoktur**;
  tutarsızlık açıklama/zeyilname konusu 🟡.
- [ ] Hesap → `yerli_mali`. Araç yanıt vermezse ya da hata dönerse elle: yerli malı teklif etmeyenin
  bedeline, kendi bedeli × oran eklenir (m.61/4), `[incele]`.
- [ ] Yerli malı listeleri (fiyat avantajı zorunlu ürünler CPV listesi, sürümlü) için
  **arama aracı yok**; yedek yol Sanayi ve Teknoloji Bakanlığı yerli malı sayfası.
  

## H. Sözleşme tasarısı tutarlılığı (idare öz denetimi)
- [ ] İşe başlama ve teslim tarihi, ihale tarihi + bekleme + davet + imza sürelerinden **sonra** mı? 🟠
- [ ] Gecikme cezası oranı, ihtar süresi (en az 10 gün, 4735 m.20/a), kesin teminat %6, fiyat farkı hükmü idari
  şartname m.43 ile aynı mı?
- [ ] "Çelişkide idare lehine hüküm geçerli" gibi ibare, sözleşmedeki belge öncelik sırasıyla ve 4735 m.4 eşitlikle
  çelişir 🟠.
- [ ] Miktar artırma/eksiltme hakkı 4735 m.24 sınırında mı (birim fiyatta %20, "öngörülemeyen durum" şartı)? `[incele]`

---

## Örnek: İKN 2026/1824919 (idare gözüyle, `[kullanıcı verdi]` metin)
| Madde | Tespit | Değerlendirme |
|---|---|---|
| İdari Ş. 7.3.1 | %20 iş deneyimi | %10-40 aralığında ✅ (m.37/3-a); YM 13/b(2) üst limitin üstünde mi → `usul_kontrol` |
| İdari Ş. 7.3.1.1 | "kamu veya özel sektöre yapılmış her türlü gıda satışı" | geniş, rekabet lehine; şikâyet riski düşük 🟢 `[incele]` |
| İdari Ş. 7.2 | ekonomik-mali yeterlik boş | eşik altıysa zorunlu olarak boş (m.27/1-c) ✅ |
| İdari Ş. 7.3.2 | işletme kayıt belgesi "teklif veren firmaya ait" | TŞ 2.2 "üretici firmaların" diyor → kimde aranacağı çelişkili 🟡 |
| İdari Ş. 7.1(f) / 33.3 | yerli malı belgesi satırı / avantaj boş; m.20 kısmi teklif yok | avantaj yok ve verilemez (m.61/4) 🟡 |
| TŞ (bulgur, meyve suyu vb.) | "piyasada kabul görmüş tescilli markalardan" | ölçütsüz, dolaylı marka şartı 🟠 `[incele]` |
| Sözleşme T. 10.2 | işe başlama 01.01.2027; ihale 12.01.2027 | tarih ihaleden önce 🟠 — zeyilname |
| Sözleşme T. 12.2.3, TŞ 2.3 | "ödenek mevcut olduğu takdirde" ödeme | 4734 m.5/5, 4735 m.4 🟠 |
| TŞ 2.4 | çelişkide idare lehine hüküm | Sözleşme T. 8.2 öncelik sırasıyla çelişir 🟠 |
