# İstekli: ön yeterlik başvurusu ve teklif hazırlama

Aday/istekli gözüyle iki dosya: (1) ön yeterlik başvuru zarfı, (2) kısa listeye girildikten sonra teknik + mali teklif. Amaç elenmemek ve puanı en yükseğe çıkarmak; ikincil amaç, dokümanda aykırılık varsa süresinde şikâyet kararını vermek. Liste örnek dokümanın (İKN 2026/1765031) Ö.Y.Ş. m.7-8 ve İ.Ş. m.6, 21-25 yapısını izler.

İdare bu listeyi "başvuru/teklif kontrol tutanağı" olarak tersinden kullanır.

---

## 1. Önce dokümanı oku (son başvurudan önce)

- [ ] Ön yeterlik dokümanını **EKAP hesabıyla indir**; ortak girişimde bütün ortaklar EKAP'a kayıtlı olmalı. İndirme tarihi doküman şikâyeti süresini başlatır (Ö.Y.Ş. 4.1, 4.6).
- [ ] Aykırılık şüphesi varsa iki **ayrı** yol: **açıklama talebi** (son başvurudan 20 gün öncesine kadar; Ö.Y.Ş. 13.1) ve **doküman şikâyeti** (indirmeden 10 gün ve son başvurudan en az 3 iş günü önce; erken olan). Açıklama talebi şikâyet süresini **durdurmaz, uzatmaz** — aykırılıkta şikâyeti süresinde ver, açıklama talebini paralel yap; iki son günü birlikte göster. İlanda yer alan hususlarda (benzer iş, iş deneyimi, yeterlik kriterleri) şikâyet süresi **ilk ilan tarihinden** işler — ilk ilan tarihini sor (4734 m.55/1). `kik_complaint_before_tender` canlı (10 gün); 3 iş günü sınırını `legal_check_holiday` ile elle say.   Doküman hükmüne sonuç aşamasında itiraz kural olarak geç kalmıştır 🔴.
- [ ] Kontrol: anahtar personel sayısı ve yılları (en fazla 4 kişi; 10/5 yıl), puan aralıkları (mali 10-30, teknik 70-90), asgari iş deneyimi ve ciro tutarlarının makullüğü, benzer iş tanımının darlığı ("dar tanım" iptal emsalleri yalnız tanım ihale konusundan **dar** ise işler; aynı ya da daha geniş tanımda uygulanmaz — `../../ihale-sikayet/references/kik-emsal-arama.md`), KT katsayısı (%70-80), asgari teknik puan, yerli avantajı oranı. Ayrıntı: `on-yeterlik-ve-kisa-liste.md` §3-4, `teknik-ve-mali-degerlendirme.md` §4.

## 2. Ön yeterlik başvuru zarfı

| Belge | Dikkat | Dayanak |
|---|---|---|
| Başvuru mektubu (e-form), imza beyannamesi | yetkili kişi, noter tasdiki | Ö.Y.Ş. 7.1-a, c |
| Oda kayıt belgesi | ilan/son başvuru **yılında** alınmış | Ö.Y.Ş. 7.1-b |
| İş ortaklığı beyannamesi | pilot ortak = en çok hisseli | Ö.Y.Ş. 7.1-f, 16.2 |
| Ortaklık tespit belgesi | %50+ hisseli ortağın belgesi kullanılıyorsa; ilk ilan/davet tarihinden sonra düzenlenmiş, son 1 yıl kesintisiz | 12911 m.38/7 |
| Bilanço / eşdeğer belge | YMM/SMMM ya da vergi dairesi onaylı; üç oran birlikte; son başvuru yılın ilk 4 ayındaysa iki önceki yıl | 12911 m.34 |
| Gelir tablosu **veya** danışmanlık cirosu belgesi | biri yeter; danışmanlık cirosunda YMM/SMMM e-formu | 12911 m.35/2-3 |
| İş deneyim belgesi | **tek sözleşme**; yapımla ilgili danışmanlıkta 15 yıl; ihale konusu ya da benzer iş; güncellenmiş tutar | 12911 m.38, 48, 49 |
| Anahtar teknik personel | diploma, oda kaydı / hizmet çizelgesi, özgeçmiş, son başvurudan **bir veya iki önceki aya ait SGK onaylı hizmet bildirimi**, personelin bünyede çalıştığına dair yazılı beyanı | 12911 m.39/1, 3, 6 |
| Kalite belgesi | TÜRKAK teyidi ya da TÜRKAK markası | Ö.Y.Ş. 8.2.4 |
| Sunulmayacak belgeler tablosu | EKAP'tan teyit edilebilen belgeler zarfa konmaz ama tablo eksiksiz doldurulur | Ö.Y.Ş. 8.7.1.2 |

**Hesaplar:**
- Bilanço: `legal_calculate_tender` `hesap: "bilanco_kontrol"`; yoksa elle (cari = dönen varlıklar − yıllara yaygın inşaat maliyetleri / KVB − yıllara yaygın hakediş gelirleri; öz kaynak / (toplam aktif − yıllara yaygın inşaat maliyetleri); KV banka borcu / öz kaynak). `[incele]`
- İş deneyimi güncelleme: `hesap: "tutar_guncelle"` (`belge: is_deneyim_4734` — belgeye konu işin **ihale tarihi** ayından bir önceki ay → ilk ilan/davet ayından bir önceki ay; `is_deneyim_diger` — sözleşme ayından bir önceki ay; `is_deneyim_kesif_yillik` — birim fiyat yılından bir önceki yılın Aralık'ı). Yoksa Yİ-ÜFE ile elle.  Yapım Yönetmeliği m.49/1-a 13/05/2026'da değişti (Danıştay YD sonrası); danışmanlık m.49/1-a araçta hâlâ 13/8/2018 metni (birim fiyat yılından bir önceki yılın Aralık endeksi); son değişiklik RG 09.04.2026 m.49'a dokunmuyor. 
- Ciro güncelleme (Yön. m.36): yıllık toplam ciro gelirin elde edildiği yılın **Haziran** endeksiyle, danışmanlık cirosu **fatura ayından önceki ayın** endeksiyle, ilk ilan ayından önceki ayın endeksine oranlanarak güncellenir.  `hesap: "tutar_guncelle"` `belge: toplam_ciro` / `fatura`.

**Sık eleme nedenleri:**
- 🔴 Birden fazla sözleşmeyi toplayarak deneyim tutarına ulaşmak (m.48/1 yasak).
- 🔴 Kontrollük ihalesinde gerçek kişi denetim/yönetim belgesini 1/50 yerine tam ya da 1/5 saymak (m.48/8).
- 🟠 Pilot ortağın %70'i, diğer ortağın %10'u sağlamaması (m.38/5).
- 🟠 SGK hizmet bildiriminin yanlış aya ait olması; anahtar personelin başka firmada da görünmesi (m.39/3, 7).
- 🟠 Bilançonun yanlış yıla ait olması (ilk dört ay kuralı, 9/4/2026).

**Puanı yükseltmek (kısa liste rekabeti varsa):** tam puan tutarına en yakın **tek** iş deneyimini seç; ortalama ciro hesabında hangi yılların sunulacağını puan tablosuna göre seç; tam puan için gereken toplam/benzer yılı sağlayan personeli öner; şartname puan veriyorsa kalite belgesini ekle.

## 3. Teknik teklif (kısa listeden sonra; İ.Ş. m.6.4)

- [ ] **Teknik Teklif Formları:** özel hizmet deneyimi belgeleri (ortak girişimde her ortak ayrı), metodoloji ve çalışma planı raporu, organizasyon planı, teknik personel zaman çizelgesi ve iş programı, yönetici kadrosu ve teknik personel listesi + özgeçmiş, diploma, deneyim ve bünyede çalışma belgeleri. **Taahhüt edilen** personel özet tabloda gösterilir, bünyede çalışma belgesi gerekmez; ama "istihdam durumu" kaleminde puan düşer (örnekte bünye 10, taahhüt 0). 
- [ ] Teknik personel olarak gösterilen kişi, işte çalışacağına dair yazılı beyan verir; anahtar personel aynı zamanda teknik personel olabilir. 
- [ ] Metodolojide şartnamedeki her alt kriterin başlığına ayrı bölüm aç (işin nasıl yapılacağı, iş programı, organizasyon, kalite kontrol). Puan kırma kararları genellikle "şu konudan detaylı bahsedilmemiş" gerekçesine dayanır; teknik/özel şartnamedeki görev listesini (örnekte Ö.İ.T.Ş. 3.1-3.2 kontrollük görevleri) madde madde karşıla.
- [ ] Belge eksikliği tamamlatılamaz; teknik zarf ihale saatinde açılır, sonradan belge eklenemez (4734 m.52/1).

## 4. Mali teklif

- [ ] E-forma uygun teklif mektubu: dokümanı okuduğunu kabul, bedelin rakam ve yazıyla uyumu, kazıntı/silinti yok, T.C./vergi kimlik no, yetkili imza; iş ortaklığında bütün ortakların imzası (İ.Ş. 22).
- [ ] Birim fiyat teklif cetveli: adam-ay × birim fiyat ve genel gider kalemi (örnek cetvel); **aritmetik hata eleme sebebidir** (Yön. m.65/4).
- [ ] Geçici teminat ≥ teklif bedelinin %3'ü; teminat mektubu süresi teklif geçerlilik süresinden en az 30 gün fazla (örnekte teklif geçerliliği 150 takvim günü) (İ.Ş. 23, 25).
- [ ] Fiyat stratejisi: PM = 100 × Mmin/M ve KM genellikle %20-30 olduğundan fiyat kırmanın toplam puana etkisi sınırlı; teknik puandaki 1 puan çoğu zaman fiyattaki birkaç yüzdeye denktir — `teknik-ve-mali-degerlendirme.md` §4 tablosuyla senaryo hesapla. Yabancı istekliyle rekabette yerli avantajını hesaba kat; yabancı ortaklı ortak girişim avantajdan yararlanamaz.
- [ ] Teklif fiyatına dahil giderler (İ.Ş. 24): ofis, araç, seyahat, sigorta, personel giderleri; örnek Ö.İ.T.Ş. 5.4'e göre şantiye ofisi ve giderleri ayrıca ödenmez.

## 5. Eksik bilgi ve açıklama talebine cevap

- [ ] İdarenin bilgi eksikliği yazısına **verilen süre içinde** (en az 2 iş günü) cevap; sonradan düzenlenen belge ihale/son başvuru tarihi itibarıyla durumu göstermeli; cevap verilmezse teklif dışarıda ve geçici teminat gelir kaydı. 
- [ ] Açıklama talebi fiyatı değiştirmeye ya da uygun olmayan teklifi uygun hale getirmeye yönelik olamaz (İ.Ş. 30.2) — cevapta yeni taahhüt ya da fiyat değişikliği yazma.

## Görüşme soruları

| Soru | Neden |
|---|---|
| Doküman ne zaman indirildi, son başvuru/ihale tarihi? | doküman şikâyeti süresi |
| Ortak girişim mi, hisse oranları, pilot kim, yabancı ortak var mı? | %70/%10/%30, yerli avantajı |
| Kullanılacak iş deneyim belgesi: türü, konusu, kabul tarihi, tutarı, gerçek kişi denetim belgesi mi? | tek sözleşme, 15 yıl, 1/50 |
| Bilanço ve gelir tablosu yılı; serbest meslek erbabı mı? | m.34-35 |
| Anahtar personelin SGK kaydı hangi firmada, son iki ayda? | m.39/3, 7 |
| Teknik personelin kaçı bünyede, kaçı taahhüt? | istihdam puanı |
