---
name: ihale-teminat-yasaklama
description: >
  Kamu ihalesinde teminatın gelir kaydı ve ihalelere katılmaktan yasaklama
  sürecini, adım adım yazışma takvimiyle idare ve istekli için yürütür: gelir
  kaydı yazısı, bankaya tazmin talebi, yasaklama teklifi ve Resmî Gazete
  süreleri, istekli tarafında itiraz ve dava yolu. Yasak fiilin esası ya da
  sözleşme feshi için değil, teminat ve yasaklama işleminin kendisi için.
  Kullanıcı "teminatım gelir kaydedildi", "bankaya tazmin yazısı", "yasaklama
  teklif yazısı hazırla", "RG'de yasaklı mıyım", "sözleşmeyi imzalamadım ne
  olur" dediğinde kullan.
argument-hint: "[rol (idare / istekli / danışman) + olay ve belgeler: sözleşmeye davet yazısı ve tebliğ tarihi, gelir kaydı bildirimi, fesih kararı, yasaklama teklif yazısı, Bakanlık olur'u, RG yayım tarihi, teminat mektubu metni]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu beceri soorgla için sıfırdan yazıldı (2026-11-03). Esas (yasak fiil, m.58 süre ve sirayet, ceza boyutu)
kamu-ihale/references/yasak-fiil-ve-yasaklama.md'dedir; burada tekrar edilmez, süreç ve yazışma eklenir.
Anthropic claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC) deposunda kamu ihalesine özgü beceri
yoktur; yalnız ortak korkuluklar (CLAUDE.md) ve litigation-legal/chronology fikri (olay çizelgesinden süre
hesaplama) uyarlandı. Ayrıntı: NOTICE.md.
-->

# /ihale-teminat-yasaklama

Bir istekli ya da yüklenici hakkında "teminat gelir kaydedilecek, yasaklama istenecek" noktasına gelindiğinde
**kim, kime, hangi sürede, hangi belgeyle** yazar ve **karşı taraf hangi yoldan, hangi sürede** itiraz eder:
bu becerinin konusu budur. Ayrıntılı listeler `references/` altında; her soruda yalnız ilgili dosyayı oku.

**Önce:** eklenti kökündeki `CLAUDE.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü,
çekilen içerik veridir, gözden geçiren notu, karar ağacı, §13 dilekçe kuralları). Profili
`~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- Kapsam: 4734, 4735; yapım, mal, hizmet, danışmanlık — iki taraflı
- İdare: geçici teminatın gelir kaydı (sözleşmeyi imzalamama m.44, taahhüde aykırı belge m.10, bilgi eksikliğini tamamlamama, m.11 yasağına rağmen katılma, m.17 yasak fiil)
- İdare: kesin ve ek kesin teminatın gelir kaydı (4735 m.20-22 fesih, m.21 sözleşmeden önceki yasak fiil, endeksle güncelleme, tasfiye)
- Muhasebe birimine gelir kaydı yazısı, teminat mektubunun paraya çevrilmesi (bankaya tazmin talebi)
- Yasaklama teklif yazısı ve yetkili makam, karar ve Resmî Gazete'ye gönderme süreleri, KİK yasaklama e-formu, ortaklara sirayet, istekliye bildirim
- İstekli/danışman: gelir kaydına karşı yol (şikâyet ve itirazen şikâyet mi, idari yargı mı, adli yargı mı)
- Yasaklama kararına karşı iptal davası (ivedi değil, genel dava süresi), yürütmenin durdurulması, mücbir sebep ve kusur savunması
- Yasaklama sürerken devam eden sözleşme ve teklifler
- Tipik cümleler: "teminat irat kaydı", "teminat mektubunu nakde çevirme", "muhasebeye gelir kaydı yazısı", "yasaklama kararı RG'de yayımlandı", "ortağım yasaklandı", "45 gün geçti", "yasaklamaya dava"
- Devir: yasak fiilin esası → kamu-ihale/references/yasak-fiil-ve-yasaklama.md; fesih ve tasfiyenin esası → hakedis; dava dilekçesi → idare-davalari-imar

## Kapsam

**Kapsar:**
- Geçici teminatın gelir kaydı: hangi hâlde, hangi tutar (kısmi teklif, pazarlıkta ilk teklif), kim karar verir,
  muhasebe birimine bildirim ve mektubun paraya çevrilmesi, iş ortaklığı → `references/gecici-teminat-gelir-kaydi.md`
- Kesin ve ek kesin teminatın gelir kaydı: 4735 m.19-22 fesih hâlleri, güncelleme, mahsup yasağı, tasfiye ile
  ilişkisi (yalnız teminat yönü) → `references/kesin-teminat-gelir-kaydi.md`
- Yasaklama süreci adım adım: tespit → idarenin bildirimi → yetkili makam → 45 gün → 15 gün → RG ve KİK sicili →
  ortaklar → yasaklama süresince ihaleler; yazışma takvimi ve örnek hesap → `references/yasaklama-sureci-ve-takvim.md`
- Kısa yazı iskeletleri (muhasebeye talimat, bankaya tazmin, yasaklama teklif yazısı, istekliye bildirim, Bakanlık
  olur'u) → `references/yazi-iskeletleri.md`
- İstekli tarafı: gelir kaydına karşı yol ve yargı yeri, yasaklamaya karşı iptal davası ve YD, savunma başlıkları,
  yasaklı dönemde sözleşme ve teklif → `references/istekli-itiraz-ve-dava.md`

**Kapsamaz ya da yönlendirir:**
- 4734 m.17 fiilinin esası, m.58 süre aralığı (1-2 yıl / 6 ay-1 yıl), sirayetin esası, TCK 235 →
  `../kamu-ihale/references/yasak-fiil-ve-yasaklama.md` (bu beceri onu **okur ve bağlanır**, yeniden yazmaz).
  O dosya 4735'i kapsamaz: **4735 m.26 yasaklaması** (m.25 fiili; süre 1-2 yıl; m.19-21 feshinde m.22/5 gereği)
  ve iki kanunun 45/15 gün takvimi **bu becerinin içindedir** → `references/kesin-teminat-gelir-kaydi.md`,
  `references/yasaklama-sureci-ve-takvim.md`. 
- Fesih ihtarı, fesih şartları, tasfiye hesabı, kabul ve teminat iadesi (4735 m.13-14) → `../hakedis/SKILL.md`
  (`references/fesih-tasfiye-ve-kabul.md`); mal/hizmet/danışmanlıkta ilgili tür becerisi.
- Şikâyet ve itirazen şikâyet zinciri, süre kodları → `../ihale-sikayet/SKILL.md` (`references/sure-zinciri.md`).
- Uzun yazı ve dilekçe metinleri → resmî yazı biçimi `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md`;
  ihale e-form ve teminat mektubu metni `../ihale-belgeleri/SKILL.md`; iptal davası dilekçesi
  `../idare-davalari-imar/references/idari-dava-dilekcesi.md`; adli yargıda teminat alacağı davası
  `../hukuk-yargilamasi-dilekce/SKILL.md`; temyiz `../kanun-yollari-dilekce/SKILL.md`.
- 2886 ihalelerinde teminat ve yasaklama → `../kamu-ihale/references/devlet-ihale-2886.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü, profil, rol
`legal_get_statute_article` (`law_no: "4734"`, `article_no: "58"`, `law_type: "Kanun"`) çağır; metin gelirse
`soorgla ✓`. Profilde ihale rolü yoksa tek soruyla sor: **idare** (ihale birimi, harcama yetkilisi, hukuk
müşaviri, bakanlık strateji/hukuk birimi) mı, **istekli/yüklenici** mi, **ihale danışmanı** mı? Aynı takvim iki
yönden okunur: idare "son günü kaçırırsam yetkim düşer", istekli "süre geçtiyse karar sakat".

### Adım 1 — Olay hangi aşamada? Soru tipini seç

| Soru tipi | İpucu | Oku |
|---|---|---|
| A. İhale aşamasında (sözleşme imzalanmadan önce) geçici teminat | imzalamadı, davet, belge getirmedi, vergi/SGK borcu çıktı, eksik bilgi, yasaklı katıldı, sahte belge | `references/gecici-teminat-gelir-kaydi.md` |
| B. Sözleşme imzalandıktan sonra kesin/ek kesin teminat | fesih, ihtar, sözleşme sonrası sahte belge, mali acz, güncelleme | `references/kesin-teminat-gelir-kaydi.md` (+ `hakedis`) |
| C. Yasaklama süreci, takvim, yetkili makam, RG | yasaklama teklifi, Bakanlığa yazı, 45 gün, RG'ye gönderme, e-form, ortak | `references/yasaklama-sureci-ve-takvim.md` |
| D. Yazı taslağı (kısa) | muhasebeye yazı, bankaya tazmin, teklif yazısı, istekliye bildirim, olur | `references/yazi-iskeletleri.md` |
| E. İstekli: itiraz, dava, savunma, yasaklı dönem | gelir kaydına itiraz, yasaklamaya dava, YD, mücbir sebep, yasaklıyken sözleşmem | `references/istekli-itiraz-ve-dava.md` |

Bir olay çoğu zaman A + C (imzalamama → gelir kaydı → yasaklama) ya da B + C (fesih → gelir kaydı → 4735 m.26)
birlikteliğidir; ikisini de oku. **Gelir kaydı ile yasaklama iki ayrı işlemdir:** farklı makam, farklı süre,
farklı yargı yolu (`istekli-itiraz-ve-dava.md` §1).

### Adım 2 — Tarih çizelgesini kur, süreleri ondan hesapla
Çizelge: sözleşmeye davet tebliği → imza son günü → tespit (imzalamama / fesih / sahte belge tespiti) → gelir kaydı
bildirimi → idarenin bakanlığa (ya da yetkili makama) **bildirim** tarihi (yazının çıkışı ve ulaşması ayrı ayrı) → yasaklama olur'u → RG'ye
gönderme → RG yayımı → istekliye tebliğ / öğrenme → dava.

- Kodlu süreler (`legal_calculate_deadline`): `kik_contract_invitation` (3 gün), `kik_contract_signing` (10 gün),
  `kik_contract_signing_foreign` (22 gün), `kik_complaint` / `kik_complaint_21bc`, `kik_objection`, `kik_lawsuit`
  (30 gün, ivedi), `iyuk_lawsuit` (60 gün, yasaklama davası), `kik_4735_default_notice` (10 gün ihtar),
  `kik_4735_force_majeure_notice` (20 gün). 
- 🟠 **`kik_4735_default_notice` tuzağı:** araç 10 günü dava süresi gibi sayıp son günü tatile göre kaydırıyor
  (2026-11-04 tebliğ → ham 14.11.2026 Cumartesi → araç 16.11.2026). Oysa 10 gün idarenin vereceği **asgari** süredir
  ve sözleşme "20/a'ya göre **belirlenen** sürenin bitimi" itibarıyla feshedilmiş sayılır (4735 m.22/1) `[soorgla]`.
  Kural: ihtarda bitişi **tam tarih** olarak yaz; 7 günlük fesih kararı süresini **ihtarda belirlenen bitiş
  gününden** (örnekte 14.11) say → son gün 21.11.2026 (Cumartesi; uzamamış say, kararı 20.11 Cuma'ya kadar al)
  `[incele]`; 5 günlük bildirim fesih karar tarihinden. Araç sonucunu yalnız "ihtar süresi 10 günden kısa mı"
  kontrolü için kullan. 
- **Yasaklama ve fesih süre kodları:** `kik_second_bidder_notice` (3 gün, 4734 m.44/2),
  `kik_debarment_decision` (45 gün, 4734 m.58/4, 4735 m.26/4), `kik_debarment_gazette_submission` (15 gün),
  `kik_4735_termination_decision` (7 gün, 4735 m.22/1), `kik_4735_termination_notice` (5 gün). Araç yanıt vermezse ya da "Süre kodu bulunamadı"
  dönerse **elle say** (`legal_check_holiday`, `[incele]`). Başlangıç olarak güvenli
  (erken) tarihi ver: 45 günde tespit tarihi, 7 günde ihtarda belirlenen ham bitiş günü. YD kararına itiraz
  **7 gün** (2577 m.27/7) kodsuz kalır, elle say. Ayrıntı `references/yasaklama-sureci-ve-takvim.md` §5. 
- İki hesap ayrışırsa erken tarih son gündür (ORTAK-KURALLAR.md §15). 45 günlük sürenin son günü tatile denk gelirse
  uzayıp uzamadığı açık değildir: **idare için uzamamış say** `[incele]`.
- Süre geçmiş ya da 7 günden az kalmışsa çıktının en üstüne 🔴. **Olay geçmişteyse** (kullanıcı süreler
  geçtikten sonra geldiyse) önce geçen süreleri 🔴 ile tek tek listele, sonra hâlâ açık olanları yaz → akış
  `references/gecici-teminat-gelir-kaydi.md` §4a. Son gün hesaplanınca "Bu süreyi süre defterine
  ekleyeyim mi?" diye sor (`sure-takibi`).

### Adım 3 — Kaynakları çek
- 4734 m.10, 11, 17, 33, 34, 43, 44, 58, 59 ve 4735 m.4, 7, 10, 11, 19-26 → `legal_get_statute_article`
  (`law_type: "Kanun"`).
- Kamu İhale Genel Tebliği (`13354`, `law_type: "Tebliğ"`): **m.28** (yasaklamaya ilişkin açıklamalar: yetkili
  makam, 45 günün başlangıcı ve niteliği, e-form, ortak girişim, teminat gelir kaydı aşamaları, ortaklar) ve
  **m.17.6** (gelir kaydı + yasaklama / yalnız gelir kaydı ayrımı). 
- Uygulama yönetmelikleri: Mal `12917`, Hizmet `12918`, Yapım `12916`, Danışmanlık `12911` → teminat, eksik bilgi,
  sözleşmeye davet maddeleri `legal_search_statute_semantic` (`mevzuat_no` ile).
- Muhasebe: Merkezî Yönetim Muhasebe Yönetmeliği `20357` m.458; mahalli idarede Mahalli İdareler Bütçe ve Muhasebe
  Yönetmeliği `21552` m.435. 
- Kararlar: `legal_search_cases` `mahkeme: "danistay"` (yasaklama, gelir kaydı, görev), `mahkeme: "kik"`
  (imzalamama, yasaklılık teyidi). En az bir son 3 yıl kararının tam metnini `legal_get_case_document` ile oku.
- **Resmî Gazete araç notu:** `legal_search_official_gazette` RG'nin **ilan bölümündeki** yasaklama kararlarını
  döndürmüyor (2026-11-03 denemesinde "ihalelere katılmaktan yasaklama" başlık araması 0, tam metin araması yalnız
  mevzuat). "Yasaklı mı?" sorusu bu araçla cevaplanamaz → EKAP yasaklı sorgusu / İhale Kontrol Sistemi (KİGT 28.3)
  ve kullanıcının RG ilan sureti `[incele]`.

### Adım 4 — Analiz
İlgili referanstaki kontrol listesini sırayla yürüt; her satırı ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Sıra her
iki rolde aynıdır: **olay ve dayanak** (hangi madde, gelir kaydı mı, yasaklama mı, ikisi mi) → **yetki ve süre**
(kim, hangi tarihten, kaç gün) → **tutar** (hangi teminat, hangi oran, güncelleme) → **belge ve yazışma** → **yol**
(istekli için itiraz/dava; idare için savunma riski).

### Adım 5 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Teminat ve yasaklama — İKN [___] — [idare / istekli] — [tür, ihale/sözleşme aşaması]

### Sonuç (tek paragraf)
[Gelir kaydı dayanağı var mı, yasaklama gerekir mi / verilebilir mi (süre ve yetki), istekli için en güçlü yol]

### Tarih çizelgesi ve yazışma takvimi
| # | Adım | Kim → kime | Başlangıç olayı (tarih) | Süre ve dayanak | Son gün | Hesap (kod / elle) | Ek belge | Durum |

### Kontrol listesi
| Kontrol | Sonuç | Dayanak |

### Tutar (gelir kaydedilecek teminat)
[teminat türü, oran, kısım, güncelleme; tutar kullanıcının verdiği belgeden — uydurulmaz]

### Yazılar (kısa iskelet) / İstekli için yol haritası
[yazi-iskeletleri.md'den ilgili iskelet; uzun metin → devir tablosu]

### Dayanaklar · Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı — ORTAK-KURALLAR.md §8]
```

### Adım 6 — "Taslaktır" kapısı
Avukat olmayan kullanıcıda şu adımlardan önce ORTAK-KURALLAR.md §1 kapısı: sözleşmeyi imzalamama kararı (gelir kaydı +
yasaklama riski), şikâyet / itirazen şikâyet, dava açmak, yasaklıyken teklif vermek. **İdare tarafında:** gelir kaydı
talimatını muhasebeye göndermek, yasaklama teklif yazısını bakanlığa göndermek, olur'a sunmak, RG'ye göndermek —
imza zinciri `[Ad SOYADI — unvan]` yer tutucusu olarak kalır. Hiçbir yazı "gönderilebilir" diye işaretlenmez.

**Gizlilik:** istekliye ve üçüncü kişilere gidecek yazıda yaklaşık maliyet, diğer isteklilerin teklifleri ve iç
yazışma (hukuk müşavirliği görüşü) yer almaz; banka yazısına yalnız mektup künyesi ve tutar girer.

---

## Devir

| İstenen | Nereye | Taşınacak özet |
|---|---|---|
| Fiil 4734 m.17'ye giriyor mu, m.58 süresi ve gerekçesi (4735 m.25-26 burada kalır) | `../kamu-ihale/references/yasak-fiil-ve-yasaklama.md` | olay, belgeler, tespit tarihi |
| Fesih şartları (ihtar, %80, mücbir sebep), tasfiye hesabı, teminat iadesi | `../hakedis/SKILL.md` | sözleşme, ihtar ve fesih tarihleri |
| Gelir kaydına karşı şikâyet / itirazen şikâyet | `../ihale-sikayet/SKILL.md` → metin `../idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md` | gelir kaydı bildirimi tarihi, numaralı iddia listesi |
| Yasaklama kararına iptal davası + YD | `../idare-davalari-imar/references/idari-dava-dilekcesi.md` | RG tarih/sayı, tebliğ/öğrenme tarihi, iptal sebepleri (yetki → süre → sebep → orantılılık) |
| Sözleşme sonrası kesin teminat alacağı (adli yargı) | `../hukuk-yargilamasi-dilekce/SKILL.md` | fesih kararı, gelir kaydı tutarı, güncelleme farkı |
| Uzun resmî yazı ve olur biçimi | `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` | iskelet + alan değerleri |
| Teminat mektubu metni / e-form | `../ihale-belgeleri/SKILL.md` | mektup künyesi, sürüm |

Süre hesaplandıysa → `../sure-takibi/SKILL.md`; çok belgeli dosya → `../dava-kronolojisi/SKILL.md`.

## Sık hatalar (özet; ayrıntı her referansın sonunda)

- 🔴 (İdare) Yasaklamayı ihaleyi yapan idarenin kendisinin vermesi; belediye ve bağlı kuruluşunda Çevre ve
  Şehircilik Bakanlığı, il özel idaresinde İçişleri Bakanlığı yetkilidir (4734 m.58/1) `[soorgla]`.
- 🔴 (İdare) 45 günü kaçırmak: süre geçince yasaklama kararı verilemez (KİGT 28.1.5.1.2; Danıştay 13. D.
  E.2023/3840 K.2024/1299, oyçokluğu — başlangıç idarenin bakanlığa bildirdiği tarih) `[soorgla]`. Güvenli yön:
  tespit tarihinden say (`references/yasaklama-sureci-ve-takvim.md` §4).
- 🔴 (İstekli) Yasaklama davasına ivedi usulün 30 gününü, gelir kaydı/imzalamama işlemine doğrudan dava yolunu
  uygulamak; ikisi ayrı yoldur, ayrı dilekçe ister (Danıştay 13. D. E.2020/65 K.2020/273) `[soorgla]`.
- 🔴 (İstekli) Sözleşme sonrası fesih ve kesin teminat gelir kaydına idare mahkemesinde iptal davası açmak; yargı
  yeri adli yargıdır (Danıştay 13. D. E.2023/497 K.2023/1152) `[soorgla]`.
- 🟠 Taahhüde aykırı belge (vergi/SGK borcu) ile süresinde belge getirmemeyi karıştırmak: birincisinde yalnız gelir
  kaydı, ikincisinde gelir kaydı **ve** yasaklama (KİGT 17.6.3-17.6.4) `[soorgla]`.
- 🟠 Kesin teminatı güncellemeden gelir kaydetmek ya da gelir kaydedilen teminatı yüklenici borcuna mahsup etmek
  (4735 m.22) `[soorgla]`.
- 🟡 Yasaklama kararının kaldırılması/değiştirilmesini RG'de yayımlatmamak; YD/iptal kararını Kuruma göndermemek
  (KİGT 28.1.1.3 c-d) `[soorgla]`.

## Bu beceri ne yapmaz
- Gelir kaydedilecek tutarı, teminat mektubu künyesini, banka adını, karar sayısını uydurmaz; belgeden alır.
- EKAP'a giriş yapmaz, yasaklılık sorgulamaz, muhasebe fişi kesmez, bankaya yazı göndermez.
- Yasak fiilin esasını yeniden değerlendirmez; `kamu-ihale` referansına bağlanır.
- Kodu olmayan süreyi "araç hesapladı" diye sunmaz; elle hesaplar, `[incele]` işaretler.
