# Değerlendirme: ilk oturum, bilgi eksikliği, aşırı düşük teklif, numune, karar ve sözleşmeye davet

İdare: "Doğru değerlendirdim mi, şikâyete dayanır mı?" · İstekli: "Neden elendim, rakip neden elenmedi, sorguya
nasıl cevap veririm?" Şikâyet kararı verilirse numaralı iddia listesiyle `../../ihale-sikayet/SKILL.md`.

---

## A. İlk oturum ve belge kontrolü (Mal Yön. m.55; tip idari Ş. m.29)
- [ ] Teklifler EKAP'ta ihale saatinde açılır; YM, teklif verenler ve fiyatlar açıklanır.
- [ ] Geçici teminat uygunluğu, yasaklılık ve kesinleşmiş vergi/SGK borcu EKAP sorgusuyla kontrol edilir; uygun
  olmayan teklif değerlendirme dışı (idari Ş. 29.2-29.3).
- [ ] **Belge eksikliği tamamlatılamaz** (m.55/4). **Bilgi eksikliği**, teklifin esasını değiştirmiyorsa yazılı istenir;
  süre **iki iş gününden az olamaz**; tamamlamayanın teklifi dışlanır ve geçici teminatı gelir kaydedilir (m.55/5).
- [ ] Tamamlama için sunulan belge ihale tarihinden sonra düzenlenmişse, ihale tarihi itibarıyla şartı sağladığını
  göstermeli (m.55/6).
- [ ] Birim fiyat teklif cetvelinde **aritmetik hata** → teklif değerlendirme dışı (m.55/7). Düzeltme yapılamaz.
- [ ] Açıklama istemi (idari Ş. 30) fiyat değişikliği ya da uygunsuz teklifi uygun hale getirme için kullanılamaz.
  

**İstekli bakışı:** "eksik belge" ile "bilgi eksikliği" ayrımı en sık uyuşmazlıktır. Belge sunulmuş ama içindeki bir
bilgi (tarih, imza, tutar dökümü) eksikse tamamlatılmalıydı → şikâyet iddiası. KİK emsali: `legal_search_cases`
`mahkeme: "kik"` sorgu "mal alımı bilgi eksikliği tamamlatılmadan değerlendirme dışı bırakılma" (son 3 yıl, MK etkisi).

## B. Yeterlik değerlendirmesi
- [ ] Yalnız idari Ş. m.7'deki belgeler ve kriterler (7.5). Teknik şartnamede yazıp m.7'ye konmamış belge eleme gerekçesi olamaz 🔴 (istekli için iddia).
- [ ] EKAP'tan/entegrasyonla teyit edilenler dışında belgeler yüklendiği haliyle esas alınır; fiziki sunum istenip
  sunulmazsa ya da farklı belge sunulursa dışlama + teminat gelir kaydı + 4734 m.17 (idari Ş. 29.6, 29.12-29.13).
- [ ] İş deneyimi: tek sözleşme, son 5 yıl, benzer iş, güncellenmiş tutar ≥ istenen oran × teklif bedeli
  (`istekli-dokuman-ve-teklif.md` §3). İdare kontrolü için `tutar_guncelle`; araç yoksa elle `[incele]`.
- [ ] Değerlendirme, en avantajlı birinci ve ikinci teklif olması öngörülenler için yapılır; aşırı düşük açıklaması
  istenen ihalede aşırı düşüklerin tamamı değerlendirilir (idari Ş. 29.5).

## C. Aşırı düşük teklif (4734 m.38; Mal Yön. m.58; idari Ş. m.31)
- [ ] **Mal alımında Kurumca belirlenmiş sınır değer formülü yoktur.** Komisyon "diğer tekliflere veya yaklaşık maliyete
  göre" aşırı düşük olanları kendisi tespit eder; gerekçeyi karar ekine yazmalı. `sinir_deger_yapim` /
  `sinir_deger_hizmet`'i mala kendiliğinden uygulama.
- [ ] **KİGT 62/A.1 (Değişik RG-9/4/2026):** mal alımında aşırı düşük tekliflerin değerlendirilmesinde **KİGT 79**
  uygulanır. Buna göre sorgu **e-formla**, önemli bileşenler tek tek ve açık sayılarak ("ve diğer giderler", "vb."
  yasak), 79.2.2 yöntemlerini daraltmadan; açıklama süresi KİGT 79.2.1-c'de "en az 3 iş günü". 79.1 (sınır değer)
  başlıkta hizmete özgü; malda sınır değer formülü ve 3 iş günü alt sınırı uygulanır mı `[incele]` — ilan
  9/4/2026'dan önceyse o tarihteki metin. 
- [ ] **Reddetmeden önce yazılı açıklama istenir**; komisyon "teklifte önemli olduğunu tespit ettiği bileşenleri"
  sorgu yazısında belirtir ve süre verir (m.58/1). Sorgusuz ret mal alımında yok (4734 m.38/3 sorgusuz ret yetkisi
  yalnız hizmet ve yapım için).
- [ ] Değerlendirme ölçütleri: (a) imalat sürecinin ekonomik olması, (b) seçilen teknik çözümler ve mal teminindeki
  avantajlı koşullar, (c) malın özgünlüğü (m.58/2). Açıklama yetersiz ya da hiç yoksa teklif reddedilir.
- [ ] Açıklama EKAP'tan e-imzayla; yüklenen belgeler esas alınır (idari Ş. 29.8).
  

**İdare:** sorgu yazısında bileşenleri ve beklenen belgeyi açık yaz (ör. "1, 2, 7. kalemler için tedarik fiyatı");
belirsiz sorgu, açıklamayı reddetmeyi zorlaştırır. Açıklamayı kabul/ret gerekçesini kalem bazında karara geçir.

**İstekli — açıklama yazısının omurgası** (metin `ihale-belgeleri`'nde):
1. Sorgulanan her bileşen ayrı başlıkta; birim fiyat = tedarik/üretim maliyeti + nakliye + ambalaj + analiz + genel
   gider + kâr.
2. Kanıt: üretici/toptancı fiyat teklifi, stok ve fatura (stoktan satışta alış faturası), maliyet tespit ya da satış
   tutarı tespit tutanağı (YMM/SMMM), avantajlı koşul (kendi üretim, depo, lojistik, kampanya).
3. Teknik şartnamedeki her maliyet doğurucu yükümlülüğün (raf ömrü, numune, test, 48 saatte değişim) karşılandığını göster.
4. Hesap tutarlılığı: açıklanan maliyet ≤ teklif fiyatı; kâr negatif olamaz `[incele]`.
Kanıt biçimi ve tutanak kuralları malda da **KİGT 79.2.2** ile (62/A.1 atfı): üçüncü kişiden fiyat teklifi + meslek
mensubunun maliyet/satış tutarı tespit tutanağı ve beyanı (satışta ağırlıklı ortalama birim satış tutarının %80'inin
altında olmamak), kamu tarifesi, borsa ve hal fiyatı (son 12 ay), isteklinin kendi ürettiği/aldığı/sattığı mal
(ilan ayından önceki 3 ay ya da ondan önceki 3 ay; alımda kullanılacak miktarın en az yarısı, satışta en az 1/20'si);
tutanak dönemi 79.2.4; yöntemlerle açıklama fiilen mümkün değilse son 12 ayın belgeleri (79.3.2); usulüne uygun açıklama
"hayatın olağan akışı" gerekçesiyle reddedilemez (79.3.1). Genel iskelet: `../../kamu-ihale/references/asiri-dusuk-teklif.md`.

## D. Numune ve demonstrasyon değerlendirmesi (Mal Yön. m.43; idari Ş. 29.9, 29.11)
- [ ] Yalnız en avantajlı birinci ve ikinci olması öngörülenlerin numunesi değerlendirilir.
- [ ] Yöntem idari şartnamede yazılı yöntem mi (komisyon / uzman üyeler / uzman + kullanıcı personel)?
- [ ] Numune inceleme raporunda teknik kriter bazında uygunluk ve **ret gerekçesi** yazılı mı? Nihai karar komisyonun.
- [ ] Numune teslimi tutanakla alındı mı, en az biri muhafaza ediliyor mu? (Kurul/yargı kararı sonrası yeniden
  değerlendirme muhafaza edilen numune üzerinden.)
- [ ] Numune yükümlülüğünü yerine getirmeyen: dışlama + teminat gelir kaydı + 4734 m.17 (idari Ş. 29.9, 29.13);
  numunesi başarısız olan: yalnız dışlama (29.11) — ikisini karıştırma 🟠.

**İstekli:** ret gerekçesi teknik şartnamede olmayan bir kritere dayanıyorsa ya da ölçüm yöntemi belirsizse şikâyet
iddiası; muhafaza edilen numunenin yeniden incelenmesini iste.

## E. En avantajlı teklif, eşitlik, yerli malı
- [ ] En düşük fiyat mı, fiyat + fiyat dışı unsur mu (idari Ş. 33; Mal Yön. m.60 — iş deneyimi ve mali yeterlik fiyat
  dışı unsur olamaz, unsur markaya göre belirlenemez).
- [ ] Yerli malı avantajı uygulanacaksa önce avantaj, sonra sıralama: yerli malı teklif etmeyenin bedeline **kendi
  bedeli × oran** eklenir; FDU'lu ihalede önce değerlendirilmiş teklif bedeli (m.61/4-5) → `yerli_mali` ya da (araç
  yanıt vermezse) elle.
- [ ] **Eşit teklifte** sıralama ölçütü idari şartnamede yazılı; iş deneyim belgesi tutarı her ihalede zorunlu ölçüt;
  öncelik: fiyat dışı unsur → yerli malı → iş deneyim tutarı (m.62/1-a, b). 

## F. Karar, kesinleşme, bekleme, davet, imza
| Adım | Süre | Kod (canlı) | Dayanak |
|---|---|---|---|
| İhale yetkilisi onayı / iptali | karar tarihini izleyen 5 iş günü; onay günü yasaklılık teyidi | `kik_tender_approval` | 4734 m.40; idari Ş. 34 |
| Kesinleşen karar bildirimi | onayı izleyen 3 gün | `kik_result_notice` | 4734 m.41; idari Ş. 35 |
| Bekleme (imza yasağı) | bildirimden 10 gün (21/b-c 5) | `kik_standstill` | 4734 m.41; idari Ş. 35.3 |
| Sözleşmeye davet | bekleme bitimi / ön mali kontrolden sonra 3 gün | `kik_contract_invitation` | 4734 m.42; idari Ş. 36 |
| Kesin teminat (%6) + belgeler + imza | davetin tebliğinden 10 gün (yabancı +12) | `kik_contract_signing`, `_foreign` | 4734 m.42-43; idari Ş. 37-38 |
| KİK payı | eşik aşılırsa bedelin on binde beşi, imzadan önce | `usul_kontrol` | 4734 m.53/j; idari Ş. 41.1 |
| İmzalamama | geçici teminat gelir + 4734 m.58 yasaklama (mücbir sebep hariç); m.10 beyanına aykırı belgede yasaklama yok | — | 4734 m.44; idari Ş. 38.6 |
| İkinci teklif sahibi | m.42 süresinin bitiminden 3 gün içinde davet | — | 4734 m.44; idari Ş. 39 |
| İdare imzalamazsa | sürelerin bitiminden 5 gün içinde 10 gün süreli noter ihbarıyla taahhütten vazgeçme | `kik_contract_withdrawal_notice` (5), `kik_contract_withdrawal_period` (10) | 4734 m.45; idari Ş. 40 |

Bu kodlar canlı: `legal_calculate_deadline` ile hesapla, yanıttaki `kural_adi`'yi satırla karşılaştır; araç yanıt
vermez ya da uyuşmazsa elle hesapla, `legal_check_holiday`, `[incele]`.  Yasaklama sonuçları
`../../kamu-ihale/references/yasak-fiil-ve-yasaklama.md`.

**Örnek (İKN 2026/1824919):** ihale 12.01.2027 → onay en geç 19.01.2027 civarı (5 iş günü, tatil kontrolü) →
bildirim + 3 gün → bekleme 10 gün → davet 3 gün → imza 10 gün. Sözleşme tasarısındaki **işe başlama 01.01.2027**
bu takvimle imkânsız; istekli açıklama talebi, idare zeyilname 🟠. Tarihleri araçla hesapla, buradaki sayım tahmindir `[HESAPLANACAK]`.
