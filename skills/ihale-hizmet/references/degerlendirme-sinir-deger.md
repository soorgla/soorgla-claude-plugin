# Değerlendirme — sınır değer, aşırı düşük teklif, bilgi eksikliği, kesinleşme ve sözleşmeye davet (aşama 3-5)

Tekliflerin açılmasından sözleşmenin imzalanmasına kadar. Örnek idari şartname m.29-41 sırasıyla. Genel 4734 m.37-38 kontrolleri `../../kamu-ihale/references/yeterlik-ve-teklif-degerlendirme.md` ve `asiri-dusuk-teklif.md`'de; burada **hizmete özgü** olanlar.

- **İdare:** sınır değeri doğru hesapla, sorgu yazısını KİGT 79.2.1'e göre kur, açıklamayı yalnız 79.2.2 yöntemleriyle değerlendir, reddi gerekçelendir.
- **İstekli:** sorguya süresinde ve yöntemine uygun cevap ver; rakibin açıklamasını aynı ölçütle denetle.

---

## 1. İlk oturum ve bilgi eksikliği (m.29; 4734 m.37)

- [ ] İlk oturum: geçici teminat, yasaklılık, kesinleşmiş vergi/SGK borcu (EKAP sorgusu); uygun olmayan değerlendirme dışı (örnek m.29.2-29.3). Vergi/SGK borcu sınırını `usul_kontrol` çıktısından ilan dönemine göre al (15.11.2026'dan sonraki ilanlarda değişiyor) `[doğrula]`.
- [ ] **Belge eksikliği tamamlatılmaz; belgede bilgi eksikliği** teklifin esasını değiştirmiyorsa idarenin verdiği sürede tamamlatılır; tamamlamayanın teklifi değerlendirme dışı ve geçici teminatı gelir kaydedilir.  Ayrım `[incele]`. Hizmet Yön. m.56: eksik belge idarece tamamlatılamaz (/4); bilgi eksikliği yazılı istenir, idare **en az 2 iş günü** makul süre verir, tamamlamayanın teklifi değerlendirme dışı ve geçici teminatı gelir kaydedilir (/5); sonradan düzenlenen belge ihale tarihi itibarıyla katılım şartlarının sağlandığını göstermeli (/6); birim fiyat teklif cetvelinde aritmetik hata → değerlendirme dışı (/7). Süre kodu `kik_info_completion_min` canlı; araç yanıt vermezse elle say. 
- [ ] Açıklama (m.30; 4734 m.37/1) fiyatı değiştirme ya da uygunsuz teklifi uygun hale getirme amacıyla istenemez.
- [ ] Fiziki belge istenip verilmezse ya da yüklenenden farklı belge verilirse: değerlendirme dışı + teminat gelir kaydı + 4734 m.17 (örnek m.29.12-29.13) 🔴.

## 2. Sınır değer

- [ ] **Personel çalıştırılmasına dayalı işte:** sınır değer = **kâr hariç yaklaşık maliyet**. 
- [ ] **Dayalı olmayan işte** (örnek dosya): değişkenler SD, YM, R; n ve T1…Tn = ilk oturumda teklif mektubu ve geçici teminatı usulüne uygun olan **ve YM'nin %60'ından düşük ya da YM'den yüksek olanlar dışındaki** teklifler.  Denklem tebliğde görsel; metinde boş. Yaygın kullanılan biçim `SD = R × (YM + T1 + … + Tn) / (n + 1)` — **tebliğ görseliyle doğrulanmadı** `[doğrula]`.
- [ ] R: her yıl 1 Şubat'tan geçerli, iş türüne göre farklı (KİGT 79.1.3) ; şartnamedeki değer (örnek m.45.1 "Diğer Hizmetler/0,78") esas. İlan mı ihale tarihi mi esas — `[doğrula]`.
- [ ] Hesap: `legal_calculate_tender` `hesap: "sinir_deger_hizmet"` (girdi: YM, geçerli teklifler, R, personele dayalı mı). **Araç yoksa:** (1) geçerli teklifleri süz (YM×0,60 ≤ T ≤ YM), (2) n'i say, (3) formülü uygula, (4) sonucu `[incele]` işaretle ve "formül tebliğ görselinden doğrulanmadı" notunu koy. İstekli YM'yi teklifler açıldıktan sonra görür (örnek m.29.1).
- [ ] Seçenek: açıklama isteme (59/2-a) mı, açıklama istemeden ret (59/2-b) mi — ilanda yazanı uygula; eşik yarısı kuralı. 

## 3. Aşırı düşük teklif sorgusu (idare) — KİGT 79.2.1

- [ ] **E-form** kullanıldı mı? 
- [ ] Önemli bileşenler işin mahiyetine uygun, **bütün istekliler için aynı**, tek tek ve açık sayıldı mı? "ve diğer giderler", "vb.", "her türlü gider" gibi ibareler yasak; kullanılırsa o kısım değerlendirmede dikkate alınmaz. 
- [ ] 79.2.2 yöntemlerini daraltan yeni yöntem konmadı mı? Süre **en az 3 iş günü** mü? 
- [ ] Örnek dosya için makul bileşenler: yedek parça kalemleri (enkoder, röle, şalter, valf, hortum, sensör), hidrolik yağ/gres/soğutucu, kalibrasyon, işçilik (varsa ayrı satır), ulaşım. Hangi kalemlerin "önemli" olduğu teklif yapısına göre `[incele]`.

## 4. Açıklamanın hazırlanması (istekli) ve değerlendirilmesi (idare)

- [ ] Kabul edilen yöntemler: üçüncü kişiden fiyat teklifi + meslek mensubunun maliyet ya da satış tutarı tespit tutanağı ve kalıp beyanı; merkezi kamu kurumu fiyatları; kamu kurumlarının ilan ettiği fiyatlar; ticaret borsası; toptancı hal; münhasır hak sahibi fiyatları; isteklinin kendi ürettiği/aldığı/sattığı mal fiyatları; ortağın işletmesinden emsal bedel. 
- [ ] **Fiyat teklifi kuralları:** maliyet tespit tutanağına dayanan hizmet fiyatı tutanaktaki toplam birim maliyetin altında olamaz; satış tutarı tespit tutanağına dayanan fiyat ağırlıklı ortalama birim satış tutarının %80'inin altında olamaz; meslek mensubu kalıp beyanı yazıp imzalar ve kaşeler; fiyat teklifi teklife konu alanda faaliyet gösterenden alınır; ihale tarihinden önce düzenlenmiş olması şart değil.  🔴 Kalıp beyan eksikliği en sık ret nedeni.
- [ ] **Tutanak dönemi:** ilan/davet ayından önceki üç ay ya da ondan önceki üç ay (örn. ilan 10.03.2024 → 01.12.2023-29.02.2024 veya 01.09.2023-30.11.2023). 
- [ ] Kendi malı/stok ile açıklamada: maliyet → alış miktarı ihtiyacın en az yarısı; satış → satış miktarı en az 1/20'si ve %80 kuralı. 
- [ ] **Sözleşme ve genel giderler:** personele dayalı olmayan işte %4 hesaplanmaz; ihale kararı ve sözleşme damga vergisi ile (eşik üstü sözleşmede) KİK payı açıklanır. 
- [ ] Sigorta önemli bileşense: acente poliçe/teklifi + şirket genel/bölge müdürlüğü teyidi, tüm süreyi kapsar.  Akaryakıt: EPDK fiyatlarının %90'ının altı geçersiz. 
- [ ] Yöntemlerle açıklama fiilen mümkün değilse gerekçeli olarak son 12 aydaki elverişli belgelerle açıklama.  (Tek üreticiden ithal yedek parçada bu yol önemli `[incele]`.)
- [ ] **Usulüne uygun açıklama yapan teklif geçerli kabul edilir;** "hayatın olağan akışına aykırı", "ticari gereklere aykırı" gibi gerekçelerle reddedilemez.  İdare reddederken bileşeni, belgeyi ve tebliğ hükmünü tek tek yazmalı.
- [ ] Açıklama EKAP üzerinden e-imzayla; sunmayan veya uygun bulunmayanın teklifi reddedilir (örnek m.29.8; 4734 m.38).
- [ ] Açıklama metni → `ihale-belgeleri` (yoksa `../../kamu-ihale/references/asiri-dusuk-teklif.md` iskeleti).

## 5. İşçilik maliyetinin altında teklif

- [ ] Personele dayalı işte ya da dayalı olmayan işte işçilik satırı açılmışsa: sözleşme gideri ve genel gider dahil asgari işçilik maliyetinin altındaki işçilik bedeli → **dokümana aykırı teklif, değerlendirme dışı** (aşırı düşük sorgusuna gerek yok).  İşçilik Hesaplama Modülü kullanımı zorunlu.  Hesap → `personel-calistirma-ve-fiyat-farki.md` §2.

## 6. Karar, kesinleşme, bekleme, davet (m.34-41)

| Adım | Kural | Kaynak |
|---|---|---|
| Onay | karar tarihini izleyen en geç 5 iş günü; **onaydan önce** ilk iki istekli için yasaklılık teyidi, ikisi de yasaklıysa iptal | örnek m.34.1; 4734 m.40  |
| Bildirim | onayın günü izleyen en geç 3 gün, komisyon kararıyla birlikte; değerlendirme dışı bırakma gerekçeleri yazılır | m.35.1; 4734 m.41  |
| Bekleme | bildirimden 10 gün (21/b-c: 5 gün) imza yok | m.35.3; 4734 m.41 |
| Davet | bekleme (ön mali kontrol varsa onun) bitiminden 3 gün | m.36.1; 4734 m.42 |
| İmza | davetin tebliğinden 10 gün (yabancıya +12); belgeler + kesin teminat | m.36.1, m.38 |
| Kesin teminat | SD'ye eşit/üstü: teklifin %6'sı; SD altı: **YM'nin %9'u**; kısmi teklifte kısım bazında | m.37.1; Hizmet Yön. m.55/2 (yetki: 4734 m.43/3)  |
| KİK payı | eşik üstü sözleşmede bedelin on binde beşi, imzadan önce | m.41.1; `ihale_kik_payi_sozlesme_esigi` |
| İmzalamazsa | geçici teminat gelir kaydı + 4734 m.58; ikinci teklif sahibine geçiş | m.38.6, m.39 |
| İdare imzalamazsa | sürenin bitiminden 5 gün içinde 10 gün süreli noter ihbarı → taahhütten vazgeçme | m.40.1; 4734 m.45 (`kik_contract_withdrawal_notice` / `_period` — canlı) |

Süre kodları (`kik_tender_approval`, `kik_result_notice`, `kik_standstill`, `kik_contract_invitation`, `kik_contract_signing`, `_foreign`, `kik_contract_withdrawal_*`) 2026-11-02'den beri **canlı**; `legal_calculate_deadline` ile hesapla, `kural_adi`'yi satırla karşılaştır; araç yanıt vermezse elle say, `legal_check_holiday`, `[incele]` (SKILL.md Adım 3). Aşırı düşük açıklama süresi (hizmette en az 3 iş günü, KİGT 79) için `kik_low_bid_explanation_services_min` de canlı. 

- [ ] Şikâyet ya da itirazen şikâyet varsa nihai karara kadar imza yok → `ihale-sikayet`.
- [ ] İstekli: sınır değerin altında kazandıysan kesin teminat YM'nin %9'u — nakit akışını teklif aşamasında planla.

## Görüşme soruları

1. Sorgu yazısının tarihi, verilen süre, sayılan bileşenler?
2. Fiyat tekliflerini kimden aldınız; tutanak hangi döneme ait; kalıp beyan var mı?
3. Teklifiniz YM'nin %60'ının altında mı? (sınır değer hesabına girmez)
4. Kesinleşen ihale kararını EKAP'ta hangi gün gördünüz?
