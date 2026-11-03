# Kesinleşme, sözleşme ve uygulama (danışmanlık)

İhale kararından sözleşmenin bitimine kadar: onay, kesinleşen karar, bekleme, davet, kesin teminat, imza, ikinci en yüksek puanlı istekli; sonra danışmanlık sözleşmesine özgü konular — personel onayı ve değişimi, personel bulundurmama ve kontrollük cezaları, hizmet fiyat farkı, sözleşme değişikliği, devir, fesih, kabul ve iş deneyim belgesi. Liste örnek idari şartnamenin (İKN 2026/1765031) m.36-46 ve sözleşme tasarısının m.12-18, 35-51 yapısını izler. Kontrollüğü yapılan **yapım işinin** hakedişi, süre uzatımı ve kabulü `../../hakedis/SKILL.md`'nin konusudur.

---

## 1. Karar, onay ve kesinleşme (İ.Ş. m.36-38)

- [ ] Toplam puanı en yüksek istekli üzerinde bırakılır; komisyonun gerekçeli kararı onaya sunulur; onaydan önce ilk iki istekli için **yasaklılık teyidi** belgesi karara eklenir; ikisi de yasaklıysa iptal.
- [ ] İhale yetkilisi karar tarihini izleyen en geç **5 iş günü** içinde onaylar ya da gerekçeyle iptal eder.
- [ ] Kesinleşen ihale kararı, komisyon kararı ekiyle bütün isteklilere bildirilir; bildirimden itibaren **10 gün** geçmeden sözleşme imzalanmaz (şikâyet varsa nihai karara kadar). Süre kodu: `kik_result_notice`, `kik_standstill` (canlı; araç yanıt vermezse elle).
- [ ] Teknik ya da mali değerlendirmede 3'ten az istekli kaldıysa ihale iptal edilmeliydi (İ.Ş. 35.3; 4734 m.52 son fıkra) — istekli için iptal iddiası, idare için öz denetim.

## 2. Sözleşmeye davet ve imza (İ.Ş. m.39-44)

| Adım | Kural | Dayanak |
|---|---|---|
| Davet | bekleme süresinin (ön mali kontrol varsa tamamlanmasının) bitiminden 3 gün içinde | 4734 m.42; İ.Ş. 39.1 |
| İmza | davetin tebliğinden 10 gün (yabancıya +12); m.10/4 (a)-(e), (g) durumlarında olunmadığına dair belgeler + kesin teminat | 4734 m.42; Yön. m.71/1; İ.Ş. 41.1 |
| Kesin teminat | ihale bedelinin %6'sı; ortak girişimde bir ya da birkaç ortak karşılayabilir. Dokümanda belirtilirse sözleşmeden önce alınmaz, her hakedişten %6 kesilir; o zaman davet kesin teminat istenmeden yapılır | 4734 m.43/1-2, m.42/2; İ.Ş. 40 |
| KİK payı | bedel 53/j-1 eşiğini aşıyorsa onbinde beşi, imzadan önce yatırılır (eşik tutarı `usul_kontrol`'den) | 4734 m.53/j-1; İ.Ş. 44.1 |
| Yasaklılık teyidi | imza tarihinde Kurumdan | İ.Ş. 44.2; Yön. m.71/2 |
| İmzalamazsa | geçici teminat gelir kaydı + m.58 yasaklama; ikinci en yüksek puanlı istekliyle (teklif fiyatı ihale yetkilisince uygun görülürse) görüşülerek sözleşme; o da imzalamazsa iptal. Belgeler taahhüde aykırıysa teminat gelir kaydedilir ama yasaklama uygulanmaz | 4734 m.52/12; Yön. m.71/1, 3; İ.Ş. 41.4, 42 |
| İdare yükümlülüğünü yerine getirmezse | istekli süre bitimini izleyen 5 gün içinde 10 gün süreli noter ihbarnamesiyle taahhütten vazgeçebilir; teminat iade + belgelenmiş teminat giderleri | İ.Ş. 43 (4734 m.45; `kik_contract_withdrawal_notice`, `_period` — canlı) |

İstekli için 🔴: imzalamama kararı yasaklama getirir; mücbir sebep yoksa avukat kapısı (ORTAK-KURALLAR.md §1).

## 3. Personel: onay, değişim ve cezalar (sözleşme m.35-38; Ö.İ.T.Ş. 5.15-5.19)

**Mevzuat çerçevesi:** teklifte önerilen anahtar teknik ve teknik personel zorunlu olmadıkça değiştirilemez; değişirse yeni personel **dengi veya daha nitelikli** olmalı. Sözleşme imzalandıktan sonra değişiklik yalnız 4735 m.15'te sayılan hallerde yapılabilir: işin yapılma yeri; süresinden önce bitirme kaydıyla süre ve buna uygun ödeme şartları — bedel aşılmadan ve karşılıklı anlaşmayla. Örnek sözleşme m.43 de aynı kurguda.

Örnek sözleşmedeki kurgu (tip danışmanlık sözleşmesinden geldiği varsayılır `[doğrula — tip sözleşme madde numaraları]`):
- [ ] **Personel tanımı (m.35):** unvan ve sayılar tabloda; isimler sözleşme aşamasında yazılır → isimler teknik teklifteki kişilerle aynı mı? Farklıysa m.66/4 dengi/daha nitelikli şartı ve teknik puana etkisi `[incele]`.
- [ ] **Onay (m.36):** tabloda isim ve unvanıyla yer alanlar onaylı sayılır; ek personel için özgeçmiş gönderilir, idare **21 takvim günü** içinde gerekçeli itiraz etmezse onaylanmış sayılır. Süre kodu yok — elle hesapla.
- [ ] **Değişim (m.37):** idarenin yazılı onayı olmadan değişiklik yok; danışmanın kontrolü dışındaki nedenle değişimde aynı/üstün nitelikli eleman; idare suistimal, ceza kovuşturması ya da performans nedeniyle gerekçeli bildirimle değişim isteyebilir; yeni personelin ücreti eskisini aşamaz, ek masraf danışmana ait.
- [ ] **Cezalar (m.17.1.2-17.1.3):** personeli iş başında bulundurmama için unvan başına **günlük** ceza; onaysız personel çalıştırma cezası; rapor gecikmesi, hatalı hakediş/kesin hesap, onaysız malzeme, fen kurallarına aykırı imalat, İSG tedbiri alınmadan işe başlatma gibi kontrollük kusurlarına sözleşme bedelinin binde/onbinde oranında ceza; toplam ceza sözleşme bedelinin %30'unu geçemez. Ceza tutarlarını belgeden oku, metne yazma.
- [ ] **Ek yaptırımlar (Ö.İ.T.Ş. 5.9-5.14):** kabule hazır olmayan iş için kabul istemi → günlük gecikme cezası; kusuru giderilmemiş imalatı "giderildi" onaylama → o imalatın %20'si; yapım yüklenicisine nefaset kesintisi yapılırsa danışmana bunun %20'si; kasıtlı fazla ödemede A = B × C / D formülüyle ceza ve tekrarında fesih imkânı; personeli başka işte çalıştırma → personel bulundurmama cezası.

**İdare için:** ceza kesmeden önce olayı tutanağa bağla, ilgili sözleşme maddesini ve ihtar gerekiyorsa ihtarı belgele; cezanın kusurla orantısı ve yapım yüklenicisinin kusurundan ayrımı `[incele]`. **Danışman için:** her personel değişikliğini önceden yazılı onaya bağla; gerekçeli itirazı süresinde yap; ceza kesintisine hakediş üzerinde ihtirazi kayıt koy (`../../hakedis/SKILL.md` itiraz usulü).

## 4. Fiyat farkı (İ.Ş. m.46; sözleşme m.15)

- [ ] Fiyat farkı ancak dokümanda öngörülmüşse ve Cumhurbaşkanınca belirlenen esaslara göre verilir; esas ve usuller sözleşme imzalandıktan sonra değiştirilemez.
- [ ] Danışmanlıkta uygulanan esaslar: **4734'e göre ihale edilen hizmet alımlarında uygulanacak fiyat farkı esasları** (2013/5215 BKK, RG 31.08.2013; değişiklikler RG 24.02.2022, 07.03.2023 ve **30.07.2025** — CB Kararı 10132). Örnek şartname yalnız 2013/5215'e atıf yapıyor; 30.07.2025 değişikliğiyle işlenmiş metnin uygulanacağını kontrol et `[incele — değişikliğin geçiş hükmü ve ilan tarihi]`.
- [ ] Örnek kurgu: adam-ay personel kalemleri esasların **işçilik maliyetlerindeki değişiklik** maddesine (m.6) göre; genel gider/bakım kalemleri m.5 formülüne göre: **F = An × B × (Pn − 1)**, B = 0,90, Pn = a1 + a2·İn/İo + b1·AYn/AYo + b2·Yn/Yo + b3·Gn/Go + c·Mn/Mo. Katsayı toplamı 1 olmalı (örnek: a1 0,85 + b1 0,11 + b3 0,04 = 1,00 ✅).
- [ ] Hesap aracı: `fiyat_farki_hizmet` (KİGT 83.1-83.3); araç yanıt vermezse endeksleri (Yİ-ÜFE alt kalemleri, motorin, TÜFE/asgari ücret değişimi) kullanıcıdan ya da `legal_calculate_cpi_change`'den al, formülle elle hesapla, `[incele]`. Yapım işi formülü (`fiyat_farki_yapim`) danışmanlığa uygulanmaz.

## 5. Devir, fesih, kabul, iş deneyim belgesi

- [ ] **Devir:** zorunlu hallerde ihale yetkilisinin yazılı izniyle; devralanda ilk ihaledeki yeterlik şartları; izinsiz devirde fesih ve 4735 m.20, 22, 26 (sözleşme m.44). Ayrıca isim ve statü değişikliği dışında, devirden sonraki **3 yıl** içinde aynı yüklenici başka sözleşme devredemez ve devralamaz.
- [ ] **İdarenin feshi:** en az 10 gün süreli ihtara rağmen aykırılığın sürmesi (sözleşme m.47; 4735 m.20) → `kik_4735_default_notice` (canlıda var). Fesih ve tasfiye ayrıntısı `../../hakedis/SKILL.md`.
- [ ] **Danışmanın feshi / mali acz:** yazılı bildirim → teminatlar gelir kaydı ve genel hükümlere göre tasfiye (sözleşme m.46).
- [ ] **Mücbir sebep:** 20 gün içinde bildirim (`kik_4735_force_majeure_notice`, 4735 m.10).
- [ ] **Muayene ve kabul:** Danışmanlık Hizmet Alımları Muayene ve Kabul Yönetmeliği (soorgla no `4712`, RG 24968); kontrollük hizmetinde danışmanın kabulü çoğu zaman yapım işinin kesin kabulüne ve kesin hesabına bağlanır (örnek Ö.İ.T.Ş. 4, sözleşme m.41-42) — süre bağlantısını sözleşmeden oku.
- [ ] **İş deneyim belgesi:** düzenlemeye yetkili kurumlar, belge düzenleme koşulları, başvuru ve tutar tespiti Yön. m.42-47; EKAP üzerinden düzenleme ek m.1. Kontrollük danışmanının belgesi "yapımla ilgili danışmanlık" belgesidir (15 yıl, m.38/1). Madde dağılımı: m.42 yetkili kurumlar, m.43 düzenleme koşulları, m.44 başvuru, m.45 tutar tespiti (hakedişteki tutar, güncellenmeden), m.46 belgenin verilmesi (başvurudan 30 gün; iş durum belgesinde ilk sözleşme bedeli + %80), m.47 belge düzenlenemeyen işler (fatura, damga vergisi; m.47/1-a RG 9/4/2026).
- [ ] **Uyuşmazlık yeri:** örnek sözleşmede Ankara mahkemeleri ve icra daireleri (m.54); sözleşme uyuşmazlığı adli yargıdadır, ihale aşaması idari yargıdadır (Ö.Y.Ş. 23).

## MCP adımları

```
legal_get_statute_article law_no: "12911" law_type: "Yönetmelik" article_no: "66" | "68" | "69" | "70" | "71" | "42" | "43" | "44" | "45" | "46"
legal_get_statute_article law_no: "4734" law_type: "Kanun" article_no: "41" | "42" | "43" | "44" | "46" | "52" | "58"
legal_get_statute_article law_no: "4735" law_type: "Kanun" article_no: "8" | "10" | "15" | "16" | "20" | "22"
legal_search_official_gazette query: "Hizmet Alımlarında Uygulanacak Fiyat Farkına İlişkin Esaslar" search_in: "title" sort_by: "date_desc"
legal_calculate_deadline kural_kodu: "kik_4735_default_notice" | "kik_4735_force_majeure_notice"
```
