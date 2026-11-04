---
name: ihale-yapim
description: >
  4734'e göre yapım işi ihalesini ilan öncesinden sözleşme imzasına kadar
  idare ve istekli için yürütür: yaklaşık maliyet, iş deneyimi ve benzer iş
  grupları, bilanço ve iş hacmi, sınır değer, aşırı düşük teklif açıklaması,
  fiyat farkı katsayıları ve sözleşmeye davet. Mal, hizmet ya da danışmanlık
  için değil, yalnız yapım işi için; şikâyet zinciri ihale-sikayet'e, hakediş
  hakedis'e gider. Kullanıcı "yapım ihalesine gireceğim", "iş deneyim belgem
  yeter mi", "benzer iş grubum uyuyor mu", "aşırı düşük sorgusu geldi"
  dediğinde kullan.
argument-hint: "[rolünüzü (idare / istekli) ve aşamayı yazın; varsa idari şartname, birim fiyat teklif cetveli, iş deneyim belgesi, bilanço, aşırı düşük sorgu yazısı, kesinleşen ihale kararı ya da davet yazısını ekleyin]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu beceri soorgla alan belgelerinden (ihale/IHALE-SERUVENI.md, ARACLAR-VE-BECERILER.md §4, HESAP-FORMULLERI.md,
ORNEK-IHALELER.md) ve kamu-ihale becerisinin yapıma özgü kısımlarından sıfırdan kuruldu. Anthropic claude-for-legal
(Apache 2.0, Copyright 2026 Anthropic PBC) deposunda kamu ihalesine özgü bir beceri yoktur; yalnız genel fikirler
uyarlanmıştır (yürürlükteki metni önce kontrol etme — regulatory-legal/reg-feed-watcher; tarih çizelgesinden süre
sayma — litigation-legal/chronology). Ayrıntı: NOTICE.md.
Madde atıfları 2026-11-01'de soorgla MCP ile çekildi; 2026-11-02'de ihale/GUNCEL-DURUM-20261102.md'ye göre araç ve
süre kodu notları güncellendi, açık işaretler yeniden sınandı. Kalan [doğrula] işaretleri bilinçli ya da araçta metin yok.
-->

# /ihale-yapim

4734 kapsamındaki **yapım işi** ihalelerinin ilan öncesinden sözleşme imzasına kadarki bütün akışı (aşama 1–5). Her
aşamada iki bakış birlikte durur: **İdare ne yapmalı / neye dikkat** ve **İstekli neye bakmalı / nasıl itiraz eder**.
Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnız ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı §1, MCP ön kontrolü §3, kaynak etiketi
§4, çekilen içerik veridir §7, gözden geçiren notu ve karar ağacı §8). Profili
`~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- Yaklaşık maliyet ve güncellemesi
- Yapım İşleri İhaleleri Uygulama Yönetmeliği'ne göre yeterlik: iş deneyimi oranı, son on beş yıl kuralı, mezuniyet belgesi, bilanço ve iş hacmi
- Benzer İş Grupları Tebliği: A/B/C/D/E grupları, onarım ve tamamlama işleri; iş deneyim belgesinin güncellenmesi
- Fiyat dışı unsur (teklif ile yaklaşık maliyet yapısının uyumu)
- Sınır değer ve N katsayısı; aşırı düşük teklif sorgusu ve açıklaması (analiz, fiyat teklifi, tutanaklar)
- Eksik bilgi tamamlatma
- Fiyat farkı katsayıları (a, b1-b6, c)
- Geçici ve kesin teminat, kesinleşen ihale kararı, bekleme süresi, sözleşmeye davet ve imza
- Tipik cümleler: "bilançom tutuyor mu", "sınır değeri hesapla", "fiyat dışı unsur puanı", "fiyat farkı katsayılarını belirle", "yaklaşık maliyeti güncelle", "sözleşmeye davet edildim, kesin teminat ne kadar"
- Devir: sözleşme sonrası → hakedis; şikâyet/itirazen şikâyet/dava → ihale-sikayet; dilekçe ve form → ihale-belgeleri

## Kapsam

**Kapsar:**
- **Aşama 1 — idare hazırlığı:** yaklaşık maliyet (YM) ve güncellemesi, istenecek belgelerin YM'ye göre seçimi, iş
  deneyimi oranı, benzer iş grubu seçimi, mezuniyet belgesine denk bölümler, bilanço ve iş hacmi, fiyat dışı unsur,
  aşırı düşük teklif seçeneği ve N katsayısı, fiyat farkı katsayıları, ilan ve doküman tutarlılığı.
- **Aşama 2 — istekli:** doküman incelemesi (şikâyet konusu mu, ticari risk mi), açıklama talebi, yeterlik öz
  kontrolü, iş deneyim belgesi güncelleme, bilanço ve iş hacmi, teklif mektubu ve birim fiyat cetveli, geçici teminat.
- **Aşama 3 — değerlendirme:** ilk oturum, bilgi eksikliği tamamlatma, açıklama isteme, ayrıntılı değerlendirme ve
  aritmetik hata, sınır değer, aşırı düşük sorgusu ve istekli açıklaması, fiyat dışı unsur puanı, ihale kararı ve onay.
- **Aşama 4–5:** kesinleşen ihale kararının bildirimi, bekleme süresi, sözleşmeye davet, kesin teminat (%6 / sınır
  değer altında YM'nin %9'u), sözleşme öncesi belgeler, KİK payı, imza; imzalamamanın sonuçları.

**Kapsamaz ya da yönlendirir:**
- Sözleşme imzalandıktan sonrası (yer teslimi, hakediş, fiyat farkı **hesabının uygulanması**, süre uzatımı, iş
  artışı, kabul, fesih, YFK) → `../hakedis/SKILL.md`. Bu beceri fiyat farkı katsayılarının **dokümanda doğru
  belirlenmesine** bakar.
- Şikâyet, itirazen şikâyet, başvuru bedeli, Kurul kararı ve ivedi dava → `../ihale-sikayet/SKILL.md` (genel çerçeve
  `../kamu-ihale/references/sikayet-kik-ve-dava.md`). Bu beceri **iddianın esasını** ve süre başlangıcını hazırlar.
- Dilekçe, e-form, teklif mektubu, aşırı düşük açıklama yazısı, komisyon kararı, davet yazısı metni →
  `../ihale-belgeleri/SKILL.md` (resmî yazı biçimi `../idari-ve-kurum-basvurulari/SKILL.md`; aşırı düşük açıklama
  iskeleti `../kamu-ihale/references/asiri-dusuk-teklif.md`).
- Usul seçimi, eşik değer, ilan süreleri genel kuralları, yasak fiil ve yasaklama, 2886 → `../kamu-ihale/SKILL.md`.
- Mal, hizmet, danışmanlık ihaleleri → `ihale-mal`, `ihale-hizmet`, `ihale-danismanlik`. Yapımla ilgili **hizmet**
  belgeleri yapım ihalesinde kullanılamaz (Yapım Yön. m.48/9). 
- Sayıştay ve kamu zararı → `../kamu-mali-denetim-sayistay/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü, tür ve rol

1. `legal_get_statute_article` (`law_no: "12916"`, `article_no: "39"`, `law_type: "Yönetmelik"`) çağır. Metin
   gelirse `soorgla ✓`. Yapım Yönetmeliği maddeleri bu çağrıyla tam metin dönüyor; `legal_search_statute_semantic`
   (`mevzuat_no: "12916"`) 124 madde üzerinde arıyor. 
2. **Tür:** yapım işi mi? (İdari şartname m.2.1-b "Türü: Yapım işi", m.2.1-c "Yapım İşleri İhaleleri Uygulama
   Yönetmeliği".) Değilse ilgili tür becerisine geç.
3. **Rol:** idare (ihale yetkilisi, komisyon, hazırlayan birim, hukuk müşaviri) mi, istekli (teklif veren, ona danışan
   avukat) mı? Profilde yoksa **sor**; rol yanlışsa tavsiye tersine döner.
4. **Aşama:** ilan öncesi / ilan ile ihale tarihi arası / ihale sonrası değerlendirme / kesinleşen karar sonrası.

### Adım 1 — Soru tipi

| Soru tipi | İpucu | Oku |
|---|---|---|
| A. İdare hazırlığı: YM, istenecek belgeler, iş deneyimi oranı, benzer iş, FDU, N, fiyat farkı katsayıları | "şartnameyi hazırlıyoruz", "hangi grubu yazalım", "katsayılar", "YM güncelle" | `references/idare-hazirlik.md` |
| B. İstekli: doküman incelemesi, yeterlik öz kontrolü, belge güncelleme, bilanço/iş hacmi, teklif ve geçici teminat | "girebilir miyim", "belgem yeter mi", "bilanço tutuyor mu", "şartname aykırı mı" | `references/istekli-dokuman-ve-teklif.md` |
| C. Değerlendirme: eksik bilgi, sınır değer, aşırı düşük sorgu ve açıklama, FDU puanı, karar | "sınır değer", "aşırı düşük sorgusu", "eksik bilgi istendi", "puanım", "elendim" | `references/degerlendirme-asiri-dusuk.md` |
| D. Kesinleşen karar, bekleme, davet, kesin teminat, imza | "sözleşmeye davet", "kesin teminat", "imzalamazsam", "ikinci teklif" | `references/sozlesme-kurulus.md` |

Bir olay birden fazla tipe giriyorsa (ör. "elendim, şikâyet edeceğim": C + `ihale-sikayet`) hepsini oku, tek çıktıda
birleştir. **Doktrin sorusu** ("mezuniyet belgesi kaç yıl sayılır?") geldiyse maddeyi çek, kısa cevap ver.

### Adım 2 — Tarih çizelgesi ve süreler

Önce olayın çizelgesini çıkar: ilk ilan, doküman indirme, açıklama talebi, zeyilname, ihale, komisyon kararı, onay,
kesinleşen karar bildirimi, davet tebliği. Süreler buradan sayılır; **olay günü sayılmaz**.

| Süre | Dayanak | Süre kodu |
|---|---|---|
| Açıklama talebi: son teklif gününden 20 gün öncesine kadar yazılı; cevap son teklif gününden en az 10 gün önce. **Şikâyet süresini durdurmaz** — ayrı satır, ayrı son gün | idari şartname m.13; 4734 m.29/3 | — (geriye doğru, elle) |
| İlan / doküman şikâyeti: ilana yansıyan hususta (iş deneyimi oranı, benzer iş, yeterlik, FDU, N, aşırı düşük seçeneği) **ilk ilan**, diğerlerinde doküman indirme tarihinden 10 gün **ve** ihaleden en geç 3 iş günü önce — erken olan | 4734 m.55/1-2 | `kik_complaint_before_tender` (10 gün) + 3 iş günü elle |
| Zeyilname: son teklif gününden en az 10 gün önce; bir defaya mahsus en fazla 20 gün erteleme | idari şartname m.14; 4734 m.29/2 | — (geriye doğru, elle) |
| İhale yetkilisinin onayı: karar tarihini izleyen en geç **5 iş günü** | 4734 m.40 | `kik_tender_approval` |
| Kesinleşen ihale kararı bildirimi: onayı izleyen en geç **3 gün** | 4734 m.41 | `kik_result_notice` |
| Bekleme: bildirimden itibaren **10 gün** (21/b-c'de 5) geçmeden imza yok | 4734 m.41 | `kik_standstill`, `kik_standstill_21bc` |
| Davet: bekleme bitiminden (ön mali kontrol varsa tamamlanmasından) **3 gün** içinde | 4734 m.42 | `kik_contract_invitation` |
| İmza ve kesin teminat: davetin tebliğini izleyen **10 gün** (yabancıya +12) | 4734 m.42 | `kik_contract_signing`, `_foreign` |
| İkinci teklif sahibine tebligat: 10 günlük sürenin bitimini izleyen **3 gün** | 4734 m.44 | — |
| Aşırı düşük açıklaması: idarenin verdiği süre, **5 iş gününden az olamaz** | KİGT 45.1.2 | `kik_low_bid_explanation_works_min` (asgari süre denetimi) |
| İdare imzalamazsa istekli: sürelerin bitiminden en geç 5 gün içinde, 10 gün süreli noter ihbarı | 4734 m.45 | `kik_contract_withdrawal_notice`, `_period` |

**Araç notu:** tablodaki bütün `kik_*` kodları (`kik_tender_approval` … `kik_contract_signing_foreign`,
`kik_contract_withdrawal_notice` / `_period`, `kik_low_bid_explanation_works_min`) ve `kik_4735_*` kodları
2026-11-02'den beri **canlı**; `legal_calculate_deadline` ile hesapla, yanıttaki `kural_adi` ve `kanun_maddesi`'ni
satırla karşılaştır. `kik_complaint_before_tender` 10 günü doğru döndürür ama **ihaleden geriye 3 iş günü sınırını
hesaplamaz** — o sınırı `legal_check_holiday` ile elle say, erken olan son gündür. Araç yanıt vermez ya da kural adı
uyuşmazsa madde metninden elle say, `[incele]`. Açıklama talebi ve zeyilname geriye doğru sürelerdir; kodları yok,
her zaman elle (açıklama talebi ihaleden 20 gün önce — 4734 m.29; şikâyet süresini durdurmaz). Süre geçmişse ya da
7 günden az kaldıysa çıktının başına 🔴. Şikâyet süreleri `ihale-sikayet` (`sure-zinciri.md` §3).

### Adım 3 — Kaynakları çek (yürürlükteki metin)

Yönetmelik ve tebliğler sık değişiyor (9/4/2026, 13/5/2026, 16/10/2026 değişiklikleri). **İlk ilan tarihinde
yürürlükte olan** metin uygulanır; değişiklik metinlerindeki geçiş maddesine bak.

- **4734:** `legal_get_statute_article` (`law_type: "Kanun"`).
- **Yapım İşleri İhaleleri Uygulama Yönetmeliği:** `law_no: "12916"`, `law_type: "Yönetmelik"`. Sık maddeler: m.30
  (istenecek belgeler), m.35 (bilanço), m.36 (iş hacmi), m.39 (iş deneyimi), m.48 (değerlendirme), m.49 (güncelleme),
  m.56 (teminat), m.57 (bilgi eksikliği), m.60 (sınır değer, aşırı düşük), m.61–62 (EAAT, FDU).
- **Kamu İhale Genel Tebliği:** `law_no: "13354"`, `law_type: "Tebliğ"` — m.45 (yapımda sınır değer ve aşırı düşük
  açıklama yöntemleri). 
- **Yapım İşlerinde Benzer İş Grupları Tebliği:** `law_no: "15043"`, `law_type: "Tebliğ"` — m.2 esaslar. **Ek-1 grup
  listesi araçta yok**; grup adlarını Resmî Gazete'deki (11.06.2011/27961) ve değişikliklerdeki listeden doğrula.
  
- **Fiyat farkı esasları** (yapım): asıl metin 2013/5217 sayılı BKK eki Esaslar (RG 31.08.2013/28751; 4735 m.8'e
  dayanır); son değişiklik CB Kararı 10132 (RG 30.07.2025/32971, yürürlük 01.09.2025; geçici m.3: ilanı bu tarihten
  önce yapılan ihalelerde ilan tarihindeki esaslar uygulanır). `legal_search_official_gazette` (`search_in: "title"`)
  ile bul, `legal_get_official_gazette_document` ile oku. 2013 kaydı araçta yalnız kapak metniyle dönüyor; ekli
  Esaslar'ın madde metni için RG PDF'ine bak `[doğrula: 2013/5217 ek metni araçta yok]`.
  
- **Parasal tutarlar** (eşik değer, 62/h mezuniyet tutarı, KİK payı eşiği, vergi/SGK borç sınırı) **beceri metnine
  yazılmaz**: `legal_get_social_parameters` (`ihale_` kalemleri; yalnız güncel dönem) ya da `usul_kontrol`; ilan
  01.02.2026'dan önceyse o yılın Kamu İhale Tebliği'ni Resmî Gazete'den çek.
- **KİK kararları:** `legal_search_cases` (`mahkeme: "kik"`). Emsal göstermeden önce **MK etkisi** kontrolü: karar
  metninin başlığındaki "Mahkeme etkisi" satırı; mahkeme kararı üzerine iptal / kısmen iptal edilmiş Kurul kararı emsal
  değildir. Satırın **yokluğu "etkilenmedi" demek değildir**: satır yalnız toplanmış MK kararlarına dayanır (2026
  işlendi, 2024-2025 sırada, öncesi yok); emin olmak için idare mahkemesi / Danıştay kararını ayrıca ara `[incele]`.
  Danıştay kararı aksi yöndeyse o ağır basar. Esaslı analizde son 3 yıldan en az bir kararın tam metnini
  `legal_get_case_document` ile oku (ORTAK-KURALLAR.md §7 alıntı-önerme kontrolü).

### Adım 4 — Hesap aracı

`legal_calculate_tender` (`hesap` alanı; 15 hesap, aşağıda yapımla ilgili olanlar). Araç yanıt vermezse ya da hata dönerse **yedek yol zorunludur:** formülü madde metninden elle uygula, ara adımları tabloyla göster, sonucu `[incele]`
işaretle.

| Hesap | Ne için | Araç yoksa |
|---|---|---|
| `usul_kontrol` | eşik altı/üstü, ilan süresi, KİK payı, vergi/SGK borç sınırı | `legal_get_social_parameters` + 4734 m.8, 13 |
| `tutar_guncelle` (`is_deneyim_4734`, `is_deneyim_diger`, `is_deneyim_kesif_aylik`, `is_deneyim_kesif_yillik`, `alt_yuklenici`, `toplam_ciro`, `fatura`, `yaklasik_maliyet`) | belge ve YM güncelleme | Yapım Yön. m.49 (iş deneyimi), m.37 (ciro: toplam ciro gelir yılının Haziran endeksiyle, yapım cirosu fatura ayından önceki ay endeksiyle), m.10/5 ve m.11 (YM); Yİ-ÜFE'yi kullanıcıdan ya da TÜİK'ten iste  |
| `mezuniyet_is_deneyimi` | mezuniyet belgesi karşılığı deneyim | 4734 m.62/1-h; Yapım Yön. m.48/8 |
| `bilanco_kontrol` | cari oran, öz kaynak, kısa vadeli banka borcu | Yapım Yön. m.35/3 |
| `is_hacmi_kontrol` | toplam ciro / yapım işleri cirosu | Yapım Yön. m.36/3-5 |
| `sinir_deger_yapim` | sınır değer | KİGT 45.1.1 (adım adım örnek tebliğde) |
| `fiyat_disi_unsur` | teklif fiyatı puanı + FDU | idari şartname m.33; Yapım Yön. m.61/3 |
| `fiyat_farki_yapim` | katsayı toplamı ve örnek ay | fiyat farkı esasları (2013/5217 eki) m.5 `[doğrula: ek metni araçta yok]`; imzadan sonra esaslar değiştirilemez (4735 m.8/2) |

**Sonuç kontrolü:** araç 0, `null` ya da boş döndürdüyse "yok" diye kullanma; dönen dönemi ilan tarihiyle karşılaştır
(ORTAK-KURALLAR.md §15).

### Adım 5 — Analiz

İlgili referanstaki kontrol listesini **idari şartnamenin madde sırasıyla** yürüt (m.7 yeterlik, m.19 sözleşme türü,
m.24 geçerlilik, m.26 geçici teminat, m.29–31 değerlendirme ve aşırı düşük, m.33 EAAT, m.34–41 karar, davet, kesin
teminat, m.43 fiyat farkı, m.45 N). Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle; liste tabandır.

Her bulguda önce ayır: **mevzuata aykırı** (şikâyet konusu; süre işliyor) mı, yalnız **ticari risk** (fiyata yansıt)
mı? İdare için soru "bu hüküm şikâyete dayanır mı?"; istekli için "aykırı mı, ne zamana kadar itiraz edebilirim?".

### Adım 6 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Yapım ihalesi — [idare / istekli] — İKN [___] — aşama [1–5] — [tarih]

### Sonuç (tek paragraf)
### Tarih çizelgesi ve kritik süreler
| Olay / süre | Tarih | Son gün | Dayanak | Durum |
### Bulgular (idari şartname madde sırasıyla)
| Şartname md. | Konu | İşaret | Açıklama | Dayanak (etiketli) |
### Hesaplar (araç çıktısı ya da elle — ara adımlarıyla)
### Önerilen düzeltme / açıklama talebi / iddia listesi
### Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [ORTAK-KURALLAR.md §8 karar ağacı]
```

### Adım 7 — "Taslaktır" kapısı ve gizlilik

Avukat olmayan kullanıcı için şu adımlardan önce ORTAK-KURALLAR.md §1 kapısını uygula: açıklama talebi ya da şikâyet vermek,
aşırı düşük açıklamasını EKAP'tan göndermek, kesin teminatı yatırıp imzalamak ya da **imzalamamaya karar vermek**
(geçici teminat gelir kaydı ve 4734 m.58 riski). İdare tarafında: ihale kararını onaylamak/iptal etmek, aşırı düşük
açıklamasını reddetmek, sözleşmeye davet etmemek.

**Yaklaşık maliyet isteklilere duyurulmaz** (4734 m.62/d); idare kullanıcısında dışa gidecek metne YM'yi koyma. YM
ilk oturumda isteklilerin erişimine açılır (idari şartname m.29.1); ondan önce istekliye YM "tahmini" verme.

### Adım 8 — Devir

| İstenen | Beceri |
|---|---|
| Hakediş, fiyat farkı uygulaması, süre uzatımı, iş artışı, kabul, fesih | `../hakedis/SKILL.md` |
| Doküman ya da sonuç şikâyeti, itirazen şikâyet, Kurul kararına dava | `../ihale-sikayet/SKILL.md` |
| Açıklama talebi, aşırı düşük açıklama yazısı, şikâyet dilekçesi, komisyon kararı, davet yazısı, e-form | `../ihale-belgeleri/SKILL.md` |
| Usul, eşik, ilan süreleri; yasak fiil ve yasaklama | `../kamu-ihale/SKILL.md` |

Devrederken taşı: rol, İKN, usul, YM bilgisi (yalnız idare içinde), tarih çizelgesi ve süre tablosu, şartname madde
numarasıyla bulgular, hesap çıktıları, çekilmiş künyeler (etiketleriyle), açık sorular. Süre hesaplanınca "Bu süreleri
süre defterine ekleyeyim mi?" diye sor (`../sure-takibi/SKILL.md`). Uzun ihale dokümanı (CD'deki şartnameler)
[uzun belge protokolüyle](../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md) okunur.

---

## Çalışılmış örnek (kısa)

İKN 2026/1776751 — bir su ve kanalizasyon idaresinin açık ihaleyle yapım işi (kırsal içme suyu depolarının tadilatı ve
temizliği; teklif birim fiyat). İhale tarihi Aralık 2026; devam eden ihale, KİK kararı yok. Dokümandan çıkanlar:
iş deneyimi teklif bedelinin **%70**'i, son **15 yıl**; benzer iş "A/IV ve A/XI grubu işler"; mezuniyette inşaat
mühendisliği; ekonomik ve mali yeterlik (m.7.2) **boş**; EAAT fiyat 60 + FDU 40 ("teklif ile YM yapısının uyumu",
31 kalem); aşırı düşükte açıklama istenecek (m.31); N = 1,2; kesin teminat %6 / sınır değer altında YM'nin %9'u;
fiyat farkı var (7 katsayı, Σ = 1, b4 = 0). Her referansta bu örneğin ilgili bulgusu ayrı kutuda.

## Bu beceri ne yapmaz

- Eşik değer, parasal limit, 62/h tutarı, KİK payı ve borç sınırını metinden söylemez; araçtan ya da tebliğden çeker.
- Gizli YM'yi tahmin etmez; aşırı düşük ve sınır değeri gerçek teklif listesi olmadan "kesin" hesaplamaz.
- EKAP'a giriş yapmaz, teklif ya da açıklama göndermez, teminat yatırmaz, yasaklılık sorgusu yapmaz.
