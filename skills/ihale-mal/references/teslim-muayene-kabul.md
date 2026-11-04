# Sözleşme sonrası: teslim, muayene ve kabul, gecikme cezası, süre uzatımı, iş artışı, fiyat farkı

Mal alımı sözleşmesinin yürütülmesi. İdare (muayene kabul komisyonu, gerçekleştirme görevlisi) ve yüklenici için.
Yapım işi sözleşme sonrası `../../hakedis/SKILL.md`'dedir; burada yalnız mal.

Mevzuat: 4735 (`law_type: "Kanun"`); Mal Alımları Denetim, Muayene ve Kabul İşlemlerine Dair Yönetmelik →
`legal_list_statute_articles` `law_no: "4713"` `query: "Mal Alımları Denetim Muayene ve Kabul"` (statute_id 43825)
ya da `legal_search_statute_semantic` `mevzuat_no: "4713"`. Sözleşmenin kendi hükümleri ve teknik şartname önce okunur:
**muayenede aranacak hususlar ihale dokümanında yazılı şartlardır** (MKY m.13).

---

## A. Teslim ve teslim programı
- [ ] Teslim yeri, işe başlama tarihi, teslim programı (peyder pey / sipariş üzerine), sipariş bildirimi biçimi (EKAP,
  e-posta, telefon) sözleşmede açık mı? Telefonla sipariş ispat sorunu doğurur → yazılı teyit iste `[incele]`.
- [ ] Teslim programında değişiklik idarenin uygun görüşüyle; süre uzatımı verilirse yüklenici yeni programı bildirir
  (sözleşme tasarısı; örnekte 5 iş günü).
- [ ] Süresinden önce teslim (MKY m.28) ve kısmi kabul (4735 m.11/3: müstakil kullanıma elverişli bölümler) mümkün mü?
- [ ] Sözleşme sonrası onay numunesi şartı (örnek TŞ 8.12) varsa: numune onay süresi ve "gecikmeler teslim süresine
  dahil" hükmü yükleniciye risk; onay talebini tarihli yaz.

## B. Muayene ve kabul (4735 m.11; MKY)
- [ ] Komisyon en az üç kişi, tek sayı, biri işin uzmanı; günlük teslimli ve çabuk bozulan mallarda kullanıcı
  birimden kurulur (4735 m.11/1; MKY m.6). Mal teslim edilmedikçe muayene yapılamaz.
- [ ] İdare, teslimden ya da teslime hazır bildiriminden itibaren **en geç beş iş günü** içinde muayeneye başlar; yer,
  gün, saat yükleniciye yazılı bildirilir (MKY m.11/a). Süre kodu `mal_inspection_start` canlı (5 iş günü,
  MKY m.11/a); araç yanıt vermezse elle say, `legal_check_holiday`. 
- [ ] Önce **fiziksel muayene**; fiziksel nitelikleri uygun olmayan malın numunesi laboratuvara gönderilmez; muayene
  yarıda bırakılmaz (MKY m.15). Tutanak her safhayı yazar, yüklenici imzalatılır (MKY m.16).
- [ ] Muayene raporu: dokümandaki nitelik ile bulunan nitelik ayrı ayrı yazılır; sonuç "niteliklerine uygundur /
  uygun değildir" (MKY m.20). Karar çoğunlukla; çekimser kalınamaz; karşı oy gerekçeli (MKY m.21).
- [ ] Numune: yeter sayıda alınması ve muhafazası idarenin sorumluluğu; mühürlü, dokümanda belirtilen süre (MKY m.13);
  ilk incelemede kanaat yoksa ikinci, sonuçlar farklıysa üçüncü muayene (MKY m.14).
- [ ] Geçici kabul yalnız dokümanda öngörülmüşse (işletmeye alma ve kapasite gerektiren mallar) (MKY m.22-23);
  kesin kabul zamanı dokümanda; yüklenici dilekçeyle başvurur (MKY m.25).
- [ ] Olumlu rapor ödemeye esas belgedir (MKY m.25); ödeme süresi sözleşmeden (örnekte kabul raporundan 30 gün).
  

### Red ve itiraz (yüklenici)
| Durum | Yol | Dayanak |
|---|---|---|
| Fiziksel muayenede red | usulüne göre itiraz → ilk muayenede bulunmayanlardan en az 3 kişilik **ikinci komisyon**; kararı kesin. Bu hükmün **ihale dokümanında yer alması zorunlu** | MKY m.15 |
| Laboratuvar muayenesinde red | itiraz → saklanan numune üzerinden **dokümanda belirtilen hakem laboratuvar**; raporu kesin; yalnız itiraz edilen noktalar | MKY m.18 |
| Dokümandan farklı ama daha iyi mal | dokümanda hüküm varsa ve komisyon onaylarsa kabul; ilave bedel yok | MKY m.26 |
| Uymayan / kusurlu mal | idarenin verdiği sürede bedelsiz değiştirme; gecikirse gecikme cezası | sözleşme (örnek 33.1, TŞ 8.5: 48 saat) |

- [ ] İtiraz süresi ve biçimi MKY'de gün olarak yazılı değil; sözleşme/teknik şartnameye bak, yoksa **derhal ve yazılı**
  itiraz et, numunenin korunmasını iste `[incele]`.
- [ ] **İdare için:** teknik şartnamede hakem laboratuvar ve ikinci komisyon hükmü yoksa (örnek İKN 2026/1824919 TŞ
  m.8'de hakem laboratuvar adı yok) red işlemi itiraza açık hale gelir 🟡 — dokümana ekle.
- [ ] Test giderinin yükleniciye ait olduğu hükmü (örnek TŞ 8.4) fiyata yansıtılmış olmalı (istekli tarafı).

## C. Gecikme cezası, ihtar, fesih
- [ ] Gecikme cezası oranı **ihale dokümanında** belirlenir (4735 m.20/a); örnekte günlük sözleşme bedelinin on binde ikisi
  (sözleşme T. 34.2). Tip sözleşmedeki izin verilen aralık `[doğrula]` (Mal Alımı Tip Sözleşmesi dipnotu —
  `legal_get_form` yazılmadı; tip sözleşme form bankasına `MEV-<mevzuat_no>-…` kimliğiyle yüklenecek, o zamana kadar
  KİK sitesindeki tip sözleşmeden oku).
- [ ] Ceza için önce **en az on gün süreli, nedenleri açıkça belirtilen ihtar**; ihtara rağmen devam → kesin teminat
  gelir kaydı + fesih + genel hükümlere göre tasfiye (4735 m.20/a). → `legal_calculate_deadline` `kik_4735_default_notice`;
  kod yoksa elle, `[incele]`. 
- [ ] Ceza, ödemelerden ve teminattan kesilir; peyder pey teslimde cezanın **sözleşme bedeli** üzerinden mi geciken
  parti üzerinden mi hesaplandığı sözleşmeden okunur — oransızlık iddiası `[incele]`.
- [ ] Muayene süresi işin süresinden sayılmaz; son teslimden önce uygunsuz mal için sözleşmede tanınan değiştirme hakkı
  (örnek: 2 defa, sözleşme T. 34.6).
- [ ] Fesih sonrası yasaklama (4735 m.26) ve teminatın endeksle güncellenmesi → `../../kamu-ihale/references/yasak-fiil-ve-yasaklama.md`;
  fesih/tasfiye uyuşmazlığı adli yargı (sözleşme yetki maddesi) → `hukuk-yargilamasi-dilekce`.

## D. Mücbir sebep ve süre uzatımı (4735 m.10)
- [ ] Haller: doğal afet, kanuni grev, genel salgın, seferberlik, Kurumca belirlenecek benzerleri.
- [ ] Şartlar birlikte: yükleniciden kaynaklanmayan, ifaya engel, giderilemez; **olayı izleyen 20 gün içinde yazılı
  bildirim**; yetkili mercilerce belgelendirme. → `kik_4735_force_majeure_notice`; kod yoksa elle, `[incele]`.
  
- [ ] İdareden kaynaklanan gecikmede en az gecikilen süre kadar uzatma (sözleşme hükmü); sipariş vermeme, numune onayını
  geciktirme, depo kabul etmeme kayıt altına alınmalı.
- [ ] Süre uzatımında fiyat farkı: sözleşmede "mücbir sebep veya idareden kaynaklanan uzatmada fiyat farkı esaslarına göre"
  hükmü varsa (örnek idari Ş. 43.1) → §F.

## E. İş artışı ve eksilişi (4735 m.24)
- [ ] Birim fiyatlı mal alımında **öngörülemeyen durum** nedeniyle zorunlu artış, sözleşme bedelinin **%20'sine kadar**,
  süre hariç aynı koşullarla aynı yükleniciye. Tamamlanamıyorsa artış yapılmadan tasfiye.
- [ ] Bedelin %80'inden az tamamlanan işte yükleniciye, %80 ile gerçekleşen tutar farkının %5'i (geçici kabul tarihindeki
  fiyatlarla). 
- [ ] Teknik şartnamedeki "idare %20'ye kadar artırır/eksiltir" genel hakkı, m.24'teki "öngörülemeyen durum" şartını
  ortadan kaldırmaz; artış kararının gerekçesi aranır `[incele]`. Artışta ek kesin teminat %6.

## F. Fiyat farkı
- [ ] Fiyat farkı verilecek mi? İdari Ş. m.43 ve sözleşme m.14 aynı mı? Verilmiyorsa yalnız sözleşmede öngörülen
  uzatma hallerinde.
- [ ] Esaslar: "4734 Sayılı Kanuna Göre İhale Edilen Mal Alımlarında Uygulanacak Fiyat Farkına İlişkin Esaslar" — ilan
  tarihinde yürürlükteki metin (son değişiklik CB Kararı 10132, RG 30.07.2025) → `legal_search_official_gazette`
  + `legal_get_official_gazette_document`. 
- [ ] **Mal fiyat farkı formülü** (Mal Alımlarında Uygulanacak Fiyat Farkına İlişkin Esaslar m.5, KİK işlenmiş metni RG 30.07.2025): `F = (M × B) × [(A2/A1) − 1]`. M teslim edilen miktar (götürü bedelde teslim yüzdesi), **B sözleşme (birim) fiyatı**; sabit 0,90 katsayısı ve Pn ağırlıkları **yok**. Kapsam (m.2): elektrik, doğal gaz, ilaç, petrol ve LPG ürünleri; bunlar dışında sözleşme süresi 180 günü aşan alımda yalnız 180. günden sonra teslim edilen kısım (A1/A2 idarenin seçtiği Yİ-ÜFE alt sektör endeksi). A1/A2: petrol/LPG ihale tarihindeki ve teslim tarihindeki EPDK fiyatı, doğal gaz/elektrik EPDK aylık fiyatları, ilaç depocu satış fiyatı. Cezalı teslimde düşük olan, erken teslimde teslim tarihindeki değer (m.6/7-8); avans düşülür (m.6/6). 
- [ ] Hesap → `legal_calculate_tender` `hesap: "fiyat_farki_mal"` (`mal_fiyat_farki`: `mal_turu`, kalem başına miktar,
  sözleşme fiyatı, A1, A2; 180 günü aşanda `seri` + aylar verilirse A1/A2 veritabanından).
  Araç yanıt vermezse ya da hata dönerse formülle elle hesapla, `[incele]`; yapım formülünü (`fiyat_farki_yapim`) mala uygulama.
- [ ] Fiyat farkı ödemesinde ek kesin teminat %6 (sözleşme T. 11.2).

## G. Kesin teminat iadesi, iş deneyim belgesi
- [ ] Piyasadan hazır alınan malda garanti varsa yarısı kabulde, kalanı garanti sonunda; yoksa tamamı; SGK ve idare
  borcu mahsup (sözleşme T. 11.3).
- [ ] Kesin kabul sonrası iş bitirme belgesi EKAP üzerinden (Mal Yön. m.44-45, ek m.1) — yüklenici talep etmeli;
  sonraki ihalelerde iş deneyimi için gerekli.

## Çıktı iskeleti
```markdown
### Mal teslimi / muayene — sözleşme [___] — [idare / yüklenici]
| Olay | Tarih | Süre / son gün | Dayanak | Durum |
| Teslim bildirimi → muayeneye başlama (5 iş günü) | … | … | MKY m.11 | |
### Bulgular · Yapılacaklar (itiraz, bildirim, ihtar cevabı) · Hesaplar (etiketli)
```
