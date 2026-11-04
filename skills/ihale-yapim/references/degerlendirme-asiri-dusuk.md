# Aşama 3 — Değerlendirme, sınır değer ve aşırı düşük teklif (yapım)

İhale saatinden onaya kadar. **İdare:** ilk oturumdan karara kadar her adım gerekçeli ve sırasıyla mı? **İstekli:**
elendiysem gerekçe ne, eksik bilgiyi süresinde tamamladım mı, aşırı düşük açıklamam mevzuata uygun mu, rakibin teklifi
neden geçerli sayıldı? Sonuca şikâyet → `ihale-sikayet`; açıklama yazısının metni → `ihale-belgeleri`
(iskelet: `../../kamu-ihale/references/asiri-dusuk-teklif.md`).

---

## 1. İlk oturum ve eksik bilgi

- [ ] Teklifler EKAP'ta açılır; YM, teklif verenler ve fiyatlar isteklilere açılır (şartname m.29.1). Geçici teminat,
  yasaklılık ve kesinleşmiş vergi/SGK borcu kontrolü; uygun olmayan değerlendirme dışı (m.29.2-3).
- [ ] **Belge eksikliği tamamlatılmaz; bilgi eksikliği tamamlatılır:** teklifin esasını değiştirmeyecek bilgi eksikliği
  idarenin belirlediği sürede yazılı istenir; tamamlamayan değerlendirme dışı, geçici teminatı **gelir kaydedilir**
  (4734 m.37/2; Yapım Yön. m.57/5). 🔴 
- [ ] **Açıklama isteme** (m.37/1, şartname m.30): net olmayan husus için; teklif fiyatı değiştirilemez, uygun olmayan
  teklif uygun hale getirilemez.
- [ ] Ayrıntılı değerlendirme: yeterlik kriterleri, dokümana uygunluk, birim fiyat cetvelinde **aritmetik hata** —
  hata varsa değerlendirme dışı (m.37/2). Değerlendirme EAAT birinci ve ikinci olması öngörülenlerle yapılır; aşırı
  düşük sorgusunda aşırı düşüklerin tamamı (şartname m.29.5).
- [ ] **İstekli:** "bilgi mi belge mi?" ayrımı en sık uyuşmazlıktır; KİK kararı ararken `legal_search_cases`
  (`mahkeme: "kik"`, sorgu "yapım iş deneyim belgesi bilgi eksikliği tamamlatma") + MK etkisi kontrolü.

## 2. Sınır değer (KİGT 45.1.1)

Hesap `sinir_deger_yapim`; yoksa elle:

1. Geçerli teklif: ilk oturumda teklif mektubu ve geçici teminatı usulüne uygun olanlar (45.1.1.5).
2. YM'nin %40'ının altı ve %120'sinin üstü hesaba girmez.
3. `Tort1` = ortalama; `σ` = standart sapma (n−1); `Tort2` = `Tort1 ± σ` aralığındakilerin ortalaması (2 ondalık).
4. `C = Tort2 / YM` (3 ondalık). `K`: C < 0,60 → K = C; 0,60 ≤ C ≤ 1,00 → K = (3,2C − C² − 0,6) / (C + 1);
   C > 1,00 → K = 1 (3 ondalık).
5. `SD = (K × Tort2) / (C × N)`.
6. Tek geçerli teklif → `Tort2` = o teklif; %40–%120 aralığında teklif yoksa ya da SD YM'nin %40'ının altına düşerse
   **SD = YM × %40** (45.1.1.4).

- [ ] Test: tebliğin 45.2 örneğini araca ver; SD 52.281,00 çıkmalı. Çıkmazsa araç sonucunu kullanma, `[incele]`.
- [ ] **İstekli:** SD'yi hesaplarken "geçerli teklif" listesine kim girdi? Geçersiz bir teklifin hesaba katılması ya da
  geçerli birinin dışlanması SD'yi ve sıralamayı değiştirir — şikâyet konusu.

## 3. Aşırı düşük sorgusu (idare)

- [ ] Seçenek ilanda/dokümanda yazılı olan: (a) açıklama iste ya da (b) aşırı düşük teklif sınır değerinin altını
  sorgusuz reddet; YM ≥ eşik/2'de (a) zorunlu (Yapım Yön. m.60). 
- [ ] Sorgulanacak kalemler: idarenin **sıralı iş kalemleri listesinde** YM'nin kümülatif %80'ine kadar olanlar + %80'i
  aşmaya yol açan kalem (45.1.2.1).
- [ ] Açıklama istenmeyecek analiz girdileri: kâr ve genel gider hariç analiz toplamının **%3'üne eşit/altında** olanlar;
  bunların toplamı %15'i aşarsa en küçükten %15'i aşmaya yol açana kadar; **işçilik girdisi her zaman açıklanır**
  (45.1.2.2). Bunlar sorgu yazısında belirtilir (45.1.2.3).
- [ ] Süre: **en az 5 iş günü** makul süre; nakliye mesafeleri ve hazır beton azami mesafesi yazıda (45.1.2, 45.1.13.16).
- [ ] Analiz formatı (malzeme, işçilik, makine, diğer — girdi cinsleri) dokümanda ya da yazı ekinde (45.1.4); özel ve
  paçal kalemler için girdileri gösteren format.

## 4. İstekli açıklaması — kontrol listesi

- [ ] Yalnız **sorgulanan** kalemler için analiz; teklif kapsamında analiz istenmez (45.1.3). Analizde kâr ve genel
  gider **en az %10** (45.1.3). Açıklanmayan girdiye bir kuruşun altında bedel konamaz; yuvarlama iki ondalık.
- [ ] Kamu birim fiyatı ya da daha yüksek fiyat teklif edilen kalemde poz numarasıyla liste yeterli, analiz zorunlu
  değil; ilan ayına ait güncel fiyat yoksa son yayımlanan (45.1.5, 9/4/2026). Bakanlık rayici poz numarasıyla
  listelenirse belge gerekmez (45.1.6).
- [ ] Analiz tutarı teklif birim fiyatını aşarsa ya da analiz formatına, birim fiyat tarifine, teknik şartnameye
  uymazsa teklif **reddedilir**; hesap hatası komisyonca re'sen düzeltilir (45.1.8). İşçilik saatlik asgari ücretin
  altında olamaz (45.1.9) — güncel asgari ücret `legal_get_social_parameters`.
- [ ] Dayanak belgeler (45.1.13): üçüncü kişi fiyat teklifi; çimento/demir üretici tarifesi; kamu kurumu tarifesi ya
  da fiyat teklifi; asgari fiyatlar; **maliyet/satış tutarı tespit tutanağı**; stok tespit tutanağı. Yalnız alış
  faturası geçerli değildir (45.1.13.9).
- [ ] Fiyat teklifi + tutanak: meslek mensubunun (YMM/SMMM) beyan şerhi; ilan ayından önceki **üç ay** (ya da ondan
  önceki üç ay) verisi; o dönemde sorgulanan miktarın **en az 1/20'si** kadar alım/satış; satışta teklif fiyatı
  ağırlıklı ortalamanın **%80'inin** altında olamaz (45.1.13.1, 45.1.13.11). 🔴 Tutanaktaki sahte ya da sonradan
  düzenlenmiş fatura 4734 m.17 → yasaklama (`kamu-ihale`).
- [ ] Akaryakıt: EPDK raporundaki fiyatların %90'ının altı geçersiz (45.1.13.14). İş makinesi: resmî rayiç ya da
  kendi malıysa satın alma bedeli + belgeler (45.1.13.17). Nakliyede idarenin mesafesinden kısa mesafe yalnız kamu
  belgesiyle (45.1.13.15).
- [ ] Ekonomik yapım yöntemi, teknik çözüm, avantajlı koşul, özgünlük iddiası **maliyet avantajını** açıklamalı
  (45.1.10–45.1.12; 4734 m.38).
- [ ] Ret gerekçesi kesinleşen kararda **hangi düzenlemeye aykırı** olduğu yazılarak bildirilir; yalnız madde atfı
  yetmez (45.1.16) — eksikse şikâyet konusu.
  

## 5. Fiyat dışı unsur puanı ve EAAT

- [ ] Teklif fiyatı puanı şartname m.33 formülüyle: ör. `TP = Ptam − |RD − TF| × Ptam / RD`; RD = şartnamede seçilen
  referans (en düşük geçerli teklif / SD / SD üstü ilk geçerli teklif — Yapım Yön. m.61/3). Araç: `fiyat_disi_unsur`.
- [ ] "Teklif ile YM yapısının uyumu": her seçili kalemin (ya da grubun) teklif tutarı / toplam teklif × 100 oranı
  asgari–azami aralıktaysa kalem puanı; **yuvarlama yok**; EKAP otomatik hesaplar — itirazda EKAP çıktısını elle
  yeniden hesapla.
- [ ] Eşitlikte şartname m.33.2 sırası (önce düşük fiyat). İş ortaklığında ortaklık oranına bakılmaz.

## 6. Karar ve onay

- [ ] Komisyon gerekçeli kararı (adlar, bedeller, gerekçe); ihale yetkilisi karar tarihini izleyen **5 iş günü** içinde
  onaylar ya da gerekçeyle iptal eder; onay öncesi birinci ve ikinci için **yasaklılık teyidi** (4734 m.40). Bütün
  tekliflerin reddi ve iptal: m.39, gerekçe bildirimi (şartname m.32). 

---

> **Çalışılmış örnek — İKN 2026/1776751**
> - Şartname m.31: sınır değerin altındakilerden **açıklama istenecek** (seçenek a); N = 1,2 (m.45). Sorgu yazısı
>   geldiğinde: hangi kalemler %80'e giriyor, hangi girdiler muaf, süre en az 5 iş günü mü?
> - FDU (m.33): RD = en düşük geçerli teklif, Ptam 60. Örnek: RD 1.000, TF 1.100 → Pfark = 100 × 60 / 1.000 = 6,
>   TP = 54; FDU puanı (≤ 40) eklenir. Gerçek tutarlarla `fiyat_disi_unsur` ile tekrarla.
> - Tadilat kalemlerinde (boya, sıva, seramik) işçilik girdisi her zaman açıklanır; saatlik asgari ücret altı ret sebebi.
