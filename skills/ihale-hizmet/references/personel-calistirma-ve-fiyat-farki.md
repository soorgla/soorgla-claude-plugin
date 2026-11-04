# Personel çalıştırılmasına dayalı hizmet, işçilik hesabı ve sözleşme sonrası fiyat farkı, asgari ücret değişimi, iş artışı (aşama 1-6)

Temizlik, güvenlik, yemek dağıtımı, park-bahçe, sürücülü araç gibi işçilik ağırlıklı hizmetler ve her hizmet sözleşmesinin sözleşme sonrası parasal konuları.

- **İdare:** işin personele dayalı olup olmadığını doğru nitele (yasak, sınır değer ve fiyat farkı buna bağlı), işçilik kalemlerini KİGT 78'e göre kur, fiyat farkını esaslara göre öde/kes.
- **İstekli / yüklenici:** işçilik altı teklif vermeden fiyatla, asgari ücret değişiminde fiyat farkı hakkını hesapla, iş artışının sınırını bil.

---

## 1. Personele dayalı mı?

- [ ] Dört koşul birlikte: personel sayısı dokümanda belli; çalışma saatlerinin tamamı idare için; YM'nin **en az %70'i** asgari işçilik (+ayni yemek/yol); iş niteliği gereği sürekli. 
- [ ] Koşula bakılmaksızın personele dayalı sayılanlar: mahalli idare/şirket bütçesinden sürekli park-bahçe, çöp toplama, cadde-sokak temizliği, sürücülü araç/iş makinesi kiralama vb.  Sayılmayanlar: danışmanlık, hastane bilgi yönetim sistemi, çağrı merkezi. 
- [ ] Süreklilik dışındaki koşulları taşıyan işlerde de personele dayalı iş kuralları (asgari işçilik, sınır değer, modül) aynen uygulanır.  Kısmi teklifte kısım kısım bakılır; bir kısım personele dayalıysa ihale öyle sayılır. 
- [ ] 🔴 4734 m.62/e-1: sayılan idareler bu bütçelerden personel çalıştırılmasına dayalı hizmet alımı **yapamaz**. İdare kullanıcısında ilk soru bu; istisna ve özel mevzuat `[incele]`. 
- [ ] Örnek dosya (tezgâh bakım-onarımı): personel sayısı belirtilmemiş, birim fiyatlı iş kalemleri, R "Diğer Hizmetler" → **personele dayalı değil** ✅ (teknik şartname okunamadığı için personel sayısı şartı varsayım `[incele]`).

## 2. Asgari işçilik maliyeti (teklif ve değerlendirme)

Bileşenler (KİGT 78.30): 
- (a) **Asgari işçilik maliyeti:** ihale tarihinde yürürlükteki brüt asgari ücret ya da şartnamedeki "% fazlası" (bayram/genel tatil ve fazla çalışma dahil) + nakdi yemek/yol gibi prime esas ödemeler + işveren sigorta primleri.
- (b) işçilikle bağlantılı ayni giderler; (c) hizmetin yürütülmesine yardımcı unsurlar;
- (ç) **sözleşme giderleri ve genel giderler:** her işçilik birim fiyatı üzerinden **%4**.

Kurallar:
- [ ] Asgari ücret: **ihale tarihinde** yürürlükteki.  `legal_get_social_parameters` `asgari_ucret_brut`; `donem_basi`/`donem_sonu`'nu ihale tarihiyle karşılaştır (araç güncel dönemi verir; geçmiş dönem için kaynağı ayrıca çek `[doğrula]`).
- [ ] İşveren payı: kısa vadeli sigorta kolları prim oranı **şartnamede** yazılı olan (12918 m.10/3; KİGT 78.11).  Araçtaki `asgari_ucret_isveren_maliyeti_*` kalemleri prim **indirimli** maliyetleri veriyor (hizmet %19,75 / tam %21,75 açıklamasıyla); KİGT 78.7'ye göre emekli personel çalıştırılacak olsa bile işveren payı indirimsiz eşit şartta hesaplanır — teşvik/indirim düşülüp düşülmeyeceğini Modülle teyit et `[incele]`. 
- [ ] Teklif (işçi × ay); 30 günden kısa aylar ve kısa Şubat için (işçi × gün). Yemek/yol için ay 30 gün değil şartnamedeki 26 ya da 22 gün; belirtilmemişse 26.  Ücret ve nakdi yemek/yol net yazılamaz; brüt kabul edilir. 
- [ ] Her işçilik maliyeti (farklı ücret grubu, bayram, fazla çalışma, engelli işçi) için ayrı satır; malzeme ayrı kalem.  Aynı ilde 50+ işçide engelli işçi sayısı ve ücret grubu şartnamede. 
- [ ] İşe alma/çıkarmayı idareye bırakan ya da önceki işçilerin çalıştırılmasını şart koşan hüküm konamaz (4857 m.2/9). 
- [ ] **Hesap:** `legal_calculate_tender` `hesap: "iscilik"` (dayanak KİGT 78.6, 78.11, 78.13, 78.29, 78.30). **Araç yanıt vermezse ya da hata dönerse (zorunlu yedek):** her ücret grubu için `aylık brüt ücret + nakdi yemek×gün + nakdi yol×gün` → işveren SGK + işsizlik payı ekle → bayram/fazla çalışma (4857 m.41, 47) satırları → toplam × personel × ay (kıst ay ayrı) → ×1,04 (sözleşme ve genel gider). Asgari ücret değişim tarihinde dönemi böl. Sonucu KİK İşçilik Hesaplama Modülü (ihale.gov.tr) ile karşılaştırmasını kullanıcıdan iste; `[incele]`. Prim oranlarını ve işsizlik payını araçta yoksa kullanıcıdan/SGK kaynağından al, `[doğrula]`.
- [ ] Altında teklif → dokümana aykırı, değerlendirme dışı (78.29). Personele dayalı işte sınır değer = kâr hariç YM (79.1.1) — açıklama, işçilik dışı kalemler ve kâr payı üzerinden yapılır.

## 3. Sözleşme sonrası — fiyat farkı: hangi metin?

- [ ] Dayanak: 4735 m.8 ve **4734'e Göre İhale Edilen Hizmet Alımlarında Uygulanacak Fiyat Farkına İlişkin Esaslar** (BKK 2013/5215, RG 31.08.2013); değişiklikler CB Kararı 5202 (RG 24.02.2022), 6902 (RG 07.03.2023), **10132 (RG 30.07.2025)**.  Esasların madde metni araçta yok: `legal_get_official_gazette_document` 2013/5215 kaydında yalnız BKK kapak metni dönüyor, esaslar eki gelmiyor (2026-11-02 denendi). Madde numaraları ve katsayılar için RG ekini ya da kullanıcının verdiği metni oku `[doğrula]`. Hangi değişikliğin uygulanacağı ilan tarihine ve geçiş hükmüne bağlı.
- [ ] Fiyat farkı **dokümanda öngörülmediyse** ödenmez; ancak tip hükme göre mücbir sebep ya da idareden kaynaklanan süre uzatımında yürürlükteki esaslara göre hesaplanır (örnek m.43.1, sözleşme m.14.2). Esas ve usul sözleşmeden sonra değiştirilemez (sözleşme m.14.3). Vergi/harç artışı fiyat farkı sebebi değildir (sözleşme m.14.1) `[kullanıcı verdi]`.
- [ ] Toplu iş sözleşmesinden doğan artışlar: Personel Çalıştırılmasına Dayalı Hizmet Alımlarında TİS'ten Kaynaklanan Fiyat Farkının Ödenmesine Dair Yönetmelik (soorgla no `20470`). 

## 4. Asgari ücret değişimi ve işçilik fiyat farkı

- [ ] KİGT 83.1: işçiliğe ilişkin brüt maliyet = şartnameye göre asgari ücret (ya da % fazlası; bayram ve fazla çalışma dahil) + işverenin karşıladığı primler. 
- [ ] KİGT 83.2: % fazlası ücret alan personelde fark = (güncel asgari ücretin % fazlası + primler) − (temel asgari ücretin % fazlası + primler). Tebliğ örneği: temel 100, %30 fazla, %5 artış → 160'tan 168'e, fark 8. 
- [ ] KİGT 83.3: esasların m.5 formülü (a1 işçilik katsayısı, artış katsayısı uygulanmaz) ile m.6 işçilik farkı ayrı hesaplanır ve toplanır; a1 ve a2 birlikte belirlenmişse toplam. 
- [ ] **Hesap:** `legal_calculate_tender` `hesap: "fiyat_farki_hizmet"` (KİGT 83.1-83.3: a1'e artış uygulanmaz, asgari ücret farkı brüt ücret + işveren primleri farkı olarak ayrı hesaplanır). **Araç yanıt vermezse ya da hata dönerse (zorunlu yedek):** her ay ve her ücret grubu için `(güncel brüt maliyet − temel brüt maliyet) × fiilen çalışılan işçi×ay`; temel = ihale tarihindeki asgari ücret dönemi, güncel = uygulama ayı. Asgari ücreti `legal_get_social_parameters` ile dönem dönem al; geçmiş dönemi araç vermiyorsa kullanıcıdan/RG'den iste. Endeksli (Pn) kısım: araç `seriler` ile seçilen Yİ-ÜFE alt endeksini (`tcmb_fiyat_endeksleri`) ve TÜFE'yi (2003=100) okur; araç yoksa TÜİK/EVDS'den ya da kullanıcıdan iste. Sonuç `[incele]`.
- [ ] Prim oranı ya da asgari ücret dışı mevzuat değişikliği (ör. işveren prim indirimi kalkması) fiyat farkına girer mi → esas metninden `[incele]`.

## 5. İş artışı, iş eksilişi, değişiklik

- [ ] Öngörülemeyen durumlarla zorunlu artış: sözleşmeye esas iş içinde kalması ve asıl işten ayrılmasının teknik/ekonomik olarak mümkün olmaması şartıyla, birim fiyatlı hizmette sözleşme bedelinin **%20**'sine kadar, süre hariç aynı hükümlerle aynı yükleniciye.  Bu sınırda tamamlanamayacaksa tasfiye.
- [ ] Sözleşme bedelinin %80'inden az tamamlanan işte yükleniciye (%80 tutarı − yapılan iş tutarı) × %5, geçici kabul tarihindeki fiyatlarla. 
- [ ] "İş programından fazla iş, idare imkân bulursa öder" (örnek sözleşme m.12.2) iş artışı onayı yerine geçmez `[incele]`.
- [ ] Sözleşme değişikliği yalnız bedel aşılmadan ve karşılıklı anlaşmayla iş yeri ve (erken bitirmede) süre/ödeme şartlarında (örnek m.23) `[kullanıcı verdi]`.
- [ ] Gecikme ve fesih (4735 m.20, en az 10 gün ihtar) → süre kodu `kik_4735_default_notice` (canlı); mücbir sebep bildirimi 20 gün `kik_4735_force_majeure_notice` (canlı). 
- [ ] Hakediş, muayene-kabul (Hizmet Alımları Muayene ve Kabul Yönetmeliği, soorgla no `4714` ; örnek m.20.3: teslimden 10 iş günü) ve kesin teminat iadesi uyuşmazlığında yapım dışı olduğu için `hakedis` becerisi yalnız benzetme yoluyla kullanılır `[incele]`.

## Görüşme soruları

1. İhale tarihi ve o tarihteki asgari ücret dönemi? Sözleşme süresince asgari ücret kaç kez değişti?
2. Şartnamede asgari ücretin % fazlası, nakdi yemek/yol, prim oranı ne yazıyor?
3. İdari şartname m.43 fiyat farkı öngörüyor mu, hangi katsayılarla?
4. Süre uzatımı verildi mi, sebebi mücbir sebep mi idare mi?
5. İş artışı oluru var mı, oran ne?
