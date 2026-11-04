---
name: ihale-sikayet
description: >
  Kamu ihalesinde başvuru ve yargı zincirini idare ve istekli için yürütür:
  idareye şikâyet, KİK'e itirazen şikâyet, Kurul kararına karşı ivedi dava ve
  temyiz; süreler, ehliyet, iddia kurgusu, başvuru bedeli iadesi ve KİK emsal
  karar araması. İhalenin esasını değerlendirmek için değil, itiraz yolunu ve
  süreleri yönetmek için; ihale danışmanının çok firmalı süre takibini de
  kapsar. Kullanıcı "ihaleden elendim, şikâyet edeceğim", "KİK'e itirazen
  şikâyet", "idare şikâyete cevap vermedi", "Kurul kararına dava" dediğinde
  kullan.
argument-hint: "[olayı ve rolünüzü anlatın (istekli mi idare mi) ya da belgeyi ekleyin: ilan, doküman indirme tarihi, kesinleşen ihale kararı, şikâyet dilekçesi, idare kararı, itirazen şikâyet dilekçesi, KİK bilgi-belge yazısı, Kurul kararı, mahkeme kararı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu beceri soorgla için sıfırdan yazıldı (2026-11-01). Omurgası ihale/IHALE-SERUVENI.md §8 (şikâyet → KİK → yargı
zinciri); önceki içerik kamu-ihale/references/sikayet-kik-ve-dava.md ve
idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md'den devralındı ve madde metinleriyle
yeniden doğrulandı. Anthropic claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC) deposundan yalnız genel
fikir uyarlandı: litigation-legal/chronology (olay çizelgesini çıkarıp süreleri ondan hesaplama). Ayrıntı: NOTICE.md.
-->

# /ihale-sikayet

Dört ihale türünde (yapım, mal, hizmet, danışmanlık) **birebir aynı** olan başvuru zincirinin ortak becerisi:
şikâyet → idare kararı → itirazen şikâyet → Kurul kararı → ivedi dava → Danıştay temyizi → kararın uygulanması.
Tür becerileri (`ihale-yapim`, `ihale-mal`, `ihale-hizmet`, `ihale-danismanlik`) esas iddianın içeriğini (yeterlik,
aşırı düşük, benzer iş) bilir; bu beceri **yolu, süreyi, ehliyeti, iddia kurgusunu, bedeli ve emsali** verir.

**Önce:** eklenti kökündeki `CLAUDE.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü,
çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı, §13 dilekçe kuralları). Profili
`~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- Kapsam: 4734; yapım, mal, hizmet, danışmanlık — iki taraflı
- İdareye şikâyet: ilan/doküman şikâyeti, ihale sonucu şikâyeti, m.21/b-c pazarlıkta kısa süre; ehliyet ve hak kaybı
- Dilekçe unsurları ve iddia kurgusu; idarenin gerekçeli kararı ve bildirimi
- İdare kararına ya da süresinde karar verilmemesine karşı KİK'e itirazen şikâyet; iptal kararına karşı başvuru
- İtirazen şikâyet başvuru bedeli ve haklılık oranına göre iadesi (iddia sayımı)
- Kurumun bilgi-belge istemi ve ihale işlem dosyası; Kurul kararı ve uygulanması
- Kurul kararına karşı ivedi yargılama (istinaf yok, Danıştay temyizi kesin), yürütmenin durdurulması
- KİK emsal kararı arama ve mahkeme etkisi (MK) kontrolü
- İhale danışmanı için çok dosyalı süre tablosu ve "şikâyete dayanak" doküman tarama listesi
- Tipik cümleler: "şartnameye itiraz", "başvuru bedeli iade olur mu", "şikâyete nasıl karar verelim", "KİK dosya istedi", "temyiz süresi", "bu KİK kararı emsal olur mu", "müvekkil firmaların ihaleleri", "bu hafta hangi süreler doluyor", "dokümanı şikâyet için tara"
- Devir: yasaklama ve sözleşme sonrası uyuşmazlık → kamu-ihale / ihale-teminat-yasaklama / hakedis; dilekçe metni → ihale-belgeleri

## Kapsam

**Kapsar:** 4734 m.54–57 ve İhalelere Yönelik Başvurular Hakkında Yönetmelik (soorgla no `12766`) kapsamındaki bütün
başvurular; İYUK m.20/A ivedi yargılama; Kurul kararının ve mahkeme kararının uygulanması; KİK emsal kararı araştırması.

**İki rol, aynı zincir.** Her soruda önce rolü belirle; belirsizse **sor**:
- **İstekli** (aday, istekli, istekli olabilecek, vekili): "Gidelim mi, son gün ne, hangi iddialarla, bedel ne kadar,
  ne kadarı geri gelir, dava açarsak ne olur?"
- **İdare** (ihale yetkilisi, raportör, komisyon, hukuk müşaviri): "Başvuru süre, ehliyet, şekil yönünden reddedilir
  mi? Esasta haklı mı? Ret, düzeltici işlem mi, iptal mi? KİK'e hangi belgeyi, hangi sürede, hangi görüşle gönderelim?
  Kurul kararını nasıl uygularız? Davada ne olur?"
- **İhale danışmanı** (birden çok istekli firma adına; hukuken istekli tarafı, başvuruyu firma kendi adına yapar):
  "Hangi dosyada hangi süre doluyor, hangi dokümanda şikâyete dayanak var, bedel ve iade ne?" → istekli modu +
  `references/danisman-cok-dosya.md` (ihale × firma başına dosya, çok dosyalı süre tablosu, tarama listesi).

**Kapsamaz ya da yönlendirir:**
- **İhalelere katılmaktan yasaklama** (4734 m.58, 4735 m.26): ivedi usul **dışında** (İYUK m.20/A-1-a), genel dava
  süresi ve istinaf → `../kamu-ihale/SKILL.md` (`references/yasak-fiil-ve-yasaklama.md`).
- **Sözleşme imzalandıktan sonraki uyuşmazlıklar** (hakediş, fiyat farkı, süre uzatımı, fesih, kabul): şikâyet yolu
  yoktur → yapımda `../hakedis/SKILL.md`; mal/hizmet/danışmanlıkta ilgili tür becerisi.
- **4735 ek m.2 Yüksek Fen Kurulu itirazı:** sözleşme uygulamasındaki uyuşmazlıkta, kesin kabule kadar idareye yazılı
  itiraz; KİK zinciri değildir, ivedi usul uygulanmaz → `../hakedis/references/uyusmazlik-ve-yargi-yolu.md`. Sınır:
  **sözleşmenin imzası**. İmzadan önceki ihale işlemi buradadır, sonraki uygulama işlemi `hakedis`'tedir.
- **2886 ihaleleri:** KİK yolu yoktur → `../kamu-ihale/references/devlet-ihale-2886.md`.
- **Dilekçe ve karar metinleri** (şikâyet, itirazen şikâyet, idarenin gerekçeli kararı, Kuruma görüş yazısı) →
  `../ihale-belgeleri/SKILL.md` (ve `../idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md`,
  `ihale-idare-kararlari.md`, `resmi-yazi-ve-olur.md`). Bu beceri metni değil, **iddia listesini, süre tablosunu ve
  emsali** hazırlayıp devreder.
- **Kurul kararına karşı dava dilekçesi** → `../idare-davalari-imar/references/idari-dava-dilekcesi.md`;
  **Danıştay temyiz dilekçesi** → `../kanun-yollari-dilekce/SKILL.md`.
- Usul, eşik, ilan, yaklaşık maliyet genel kuralları → `../kamu-ihale/SKILL.md`; iddianın türe özgü esası (benzer iş,
  aşırı düşük, iş deneyimi) → ilgili tür becerisi.

---

## İş akışı

### Adım 0 — MCP ön kontrolü, profil, rol
`legal_get_statute_article` (`law_no: "4734"`, `article_no: "55"`, `law_type: "Kanun"`) çağır. Metin gelirse
`soorgla ✓`. Profilden rolü (avukat / değil) ve ihale rolünü (idare / istekli firma / ihale danışmanı) oku; bu
soruda kullanıcının söylediği taraf profili ezer. Profilde ihale rolü yoksa tek soruyla sor (CLAUDE.md "İhale
sorusunda rol önce"). Danışmanda hangi firma ve hangi İKN için konuşulduğunu netleştir (müvekkil adı profile yazılmaz). İhale türünü (yapım/mal/hizmet/danışmanlık) ve usulünü (özellikle **21/b-c pazarlık** mı) sor:
şikâyet süresi ve Kurul karar süresi buna göre değişir.

### Adım 1 — Zincirde nerede? Soru tipini seç

| Soru tipi | İpucu | Oku |
|---|---|---|
| A. Son gün ne, süre geçti mi, hangi tarihten sayılır | "kaç günüm var", "ne zaman öğrendik", "zeyilname", "sözleşme imzalandı mı" | `references/sure-zinciri.md` |
| B. İstekli: şikâyet ve itirazen şikâyet kurgusu, ehliyet, iddia listesi, bedel ve iade | "elendim", "rakip kazandı", "şartname aykırı", "bedel ne kadar", "iade" | `references/istekli-sikayet-itirazen.md` (+ A) |
| C. İdare: şikâyeti inceleme, 10 gün içinde karar, bildirim, Kuruma dosya ve görüş, Kurul kararını uygulama | "şikâyet geldi", "nasıl karar verelim", "KİK belge istedi", "düzeltici işlem" | `references/idare-cevap-ve-dosya.md` (+ A) |
| D. Kurul kararına dava, yürütmenin durdurulması, savunma, temyiz | "Kurul reddetti", "dava açacağız", "Kurum davalı", "temyiz" | `references/ivedi-dava-ve-temyiz.md` (+ A) |
| E. KİK emsali, Danıştay içtihadı, "bu karar hâlâ geçerli mi" | "emsal KİK kararı", "Kurul ne diyor", "mahkeme iptal etti mi" | `references/kik-emsal-arama.md` |
| F. Danışman: çok dosya, toplu süre takibi, doküman taraması | "müvekkil firmalar", "bu hafta dolan süreler", "dokümanı şikâyet için tara", profilde rol "İhale danışmanı" | `references/danisman-cok-dosya.md` (+ A, B, E) |

Olay birden çok tipe giriyorsa hepsini oku, tek çıktıda birleştir. **Süre (A) her esaslı soruda okunur.**

**Ad-hoc doktrin sorusu** (ör. "itirazen şikâyete yeni iddia eklenebilir mi?") geldiyse akışı atla: maddeyi çek,
kısa cevap ver, etiketle.

### Adım 2 — Tarih çizelgesini çıkar, süreleri ondan hesapla
İhale hukukunda hak kaybının çoğu süreden gelir. Önce olayın çizelgesini kur: ilk ilan, doküman EKAP'tan indirme,
zeyilname bildirimi, ihale tarihi, komisyon kararı, kesinleşen ihale kararının bildirimi, şikâyetin idare kaydına
girişi, idare kararı ve bildirimi, itirazen şikâyetin Kurum kaydına girişi, Kurul kararı tebliği, mahkeme kararı
tebliği. Sonra `references/sure-zinciri.md` tablosuyla her son günü hesapla.

- `legal_calculate_deadline` ile süre kodu kullan (`kik_complaint`, `kik_complaint_before_tender`, `kik_objection`,
  `kik_lawsuit` …). Bütün `kik_*` kodları 2026-11-02'den beri **canlı** (ayrıntı ve tek doğru liste `sure-zinciri.md`
  §3). `kik_complaint_before_tender` 10 günü doğru döndürür ama ihaleden geriye **3 iş günü sınırını hesaplamaz** —
  o sınırı `legal_check_holiday` ile elle say, erken olan son gündür. **Araç yanıt vermez, hata döner ya da `kural_adi`
  halkayla uyuşmazsa:** madde metninden elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[incele]` işaretle.
  
- **İlan / doküman şikâyetinde ilk ilan tarihini mutlaka sor.** İlana yansıyan hususlarda (iş deneyimi oranı, benzer
  iş, yeterlik kriterleri, FDU, aşırı düşük seçeneği) süre doküman indirmeden değil ilk ilan tarihinden işler (4734
  m.55/1; `sure-zinciri.md` halka 1).
- **Açıklama talebi şikâyet süresini durdurmaz.** Açıklama talebi (4734 m.29; ihaleden 20 gün önce) ile doküman
  şikâyeti iki ayrı yoldur; çıktıda iki son gün ayrı satırda, birlikte gösterilir.
- Araç ile elle hesap ayrışırsa **erken tarih** son gündür (ORTAK-KURALLAR.md §15).
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴. Sözleşme imzalandıysa şikâyet yolu kapanmıştır
  (4734 m.55/1 "sözleşmenin imzalanmasından önce") `[soorgla]`; ama süre ve usule aykırı imza itirazen şikâyetin
  incelenmesine engel değildir (m.56/3) `[soorgla]`.
- Son gün hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor (`sure-takibi`).

### Adım 3 — Yürürlükteki metni araçtan çek
Başvurular Yönetmeliği ve Tebliği sık değişiyor (son büyük değişiklik RG 9/4/2026-33219: iddia sayımı ve bedel
iadesi). Her akışta:
- 4734 m.53–57, 65 → `legal_get_statute_article` (`law_type: "Kanun"`).
- Yönetmelik → `legal_get_statute_article` (`law_no: "12766"`, `law_type: "Yönetmelik"`); harfli maddelerde
  (18/A, 20/A) boş dönerse `legal_list_statute_articles` (`article_no: "18/A"`, `include_content: true`).
- İYUK m.20/A → `legal_list_statute_articles` (`law_no: "2577"`, `article_query: "İvedi yargılama usulü"`,
  `include_content: true`).
- Başvurular Tebliği ve yıllık Kamu İhale Tebliği → `legal_search_official_gazette` (`search_in: "title"`,
  `sort_by: "date_desc"`), `legal_get_official_gazette_document`.
- **Geçiş kuralı:** Yönetmeliğin geçiş maddeleri ilan ya da duyuru tarihinde yürürlükte olan hükmü uygular
  (12766 geçici m.4, 6, 7, 9) `[soorgla]`; başvuru tarihini esas alan geçiş hükümleri de var (geçici m.5) `[soorgla]`.
  İlan tarihi ile son değişiklik tarihini karşılaştır, hangi metni uyguladığını yaz.

### Adım 4 — Analiz
İlgili referanstaki kontrol listesini sırayla yürüt; her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle.
Liste tabandır. Sıra her iki rolde aynıdır: **usul süzgeci** (görev alanı, ehliyet, süre, şekil, bedel, tek dilekçe,
iddia sınırı) → **esas** (her iddia ayrı: olgu → doküman maddesi → mevzuat → emsal → sonuç) → **karar türü**
(iptal / düzeltici işlem / ret; 4734 m.54) → **sonraki halka** (itirazen şikâyet, dava, uygulama).

**Orantılılık:** "Bedel ne kadar?" tek satır ister (araçtan çek, söyle); "şikâyet edelim mi?" tam süzgeç ister.

**Emsal:** her esaslı analizde son 3 yıldan en az bir KİK ya da Danıştay kararının tam metnini
`legal_get_case_document` ile oku; KİK kararını emsal göstermeden önce **mahkeme etkisi (MK) kontrolü zorunlu**
(`references/kik-emsal-arama.md`). İptal edilmiş Kurul kararı emsal değildir.

### Adım 5 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Başvuru zinciri — İKN [___] — [istekli / idare] — [tür, usul]

### Sonuç (tek paragraf)
[Yol açık mı, son gün ne, en güçlü iddia hangisi / idare için önerilen karar türü]

### Süre tablosu
| Halka | Başlangıç olayı (tarih) | Süre ve dayanak | Son gün | Hesap yolu (araç kodu / elle) | Durum |

### Usul süzgeci
| Kontrol | Sonuç | Dayanak |

### İddia listesi (ihale-belgeleri'ne aynen devredilecek)
| No | Husus (tek) | Aykırılık sebepleri | Dayanak | Emsal (MK kontrolü) | Risk | Bedel iadesine etkisi |

### Bedel (yalnız itirazen şikâyette)
[dilim, dönem, kaynak; iddia sayısı ve olası iade senaryosu]

### Dayanaklar · Eksik bilgi
**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Avukat olmayan kullanıcı şunlardan önce ORTAK-KURALLAR.md §1 kapısını uygula: şikâyet ya da itirazen şikâyet vermek, başvuru
bedelini yatırmak, başvurudan feragat etmek, dava açmak, temyiz etmek. **İdare tarafında:** şikâyete karar vermek,
ihaleyi iptal etmek, Kuruma görüş göndermek, sözleşmeyi imzalamak (bekleme ve sorgulama yapılmadan imza yasak).

**Gizlilik:** rakip teklifleri, yaklaşık maliyet ve ihale işlem dosyası hassastır. İdare personeline dışa gidecek
metne yaklaşık maliyeti koyma; istekliye rakip belgelerini yalnız erişim hakkı çerçevesinde kullan `[incele]`.

### Adım 7 — Devir

| İstenen | Beceri |
|---|---|
| Şikâyet / itirazen şikâyet dilekçesi metni | `../ihale-belgeleri/SKILL.md` (yoksa `../idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md`) |
| İdarenin gerekçeli şikâyet kararı, Kuruma görüş / bilgi-belge yazısı | `../ihale-belgeleri/SKILL.md` (yoksa `../idari-ve-kurum-basvurulari/references/ihale-idare-kararlari.md`, `resmi-yazi-ve-olur.md`) |
| Kurul kararına karşı iptal davası (+ YD) dilekçesi | `../idare-davalari-imar/references/idari-dava-dilekcesi.md` |
| Danıştay temyizi (ivedi usul, 15 gün) | `../kanun-yollari-dilekce/SKILL.md` |
| İddianın türe özgü esası | `ihale-yapim` / `ihale-mal` / `ihale-hizmet` / `ihale-danismanlik` |
| Yasaklama; usul-eşik-ilan; 2886 | `../kamu-ihale/SKILL.md` |
| Sözleşme sonrası, YFK | `../hakedis/SKILL.md` (yapım) / tür becerisi |

Devirde taşı: rol, İKN, tür ve usul, tarih çizelgesi ve süre tablosu, **numaralı iddia listesi** (itirazen şikâyette
yeni iddia eklenemez), bedel hesabı ve dönemi, çekilmiş madde ve karar künyeleri (MK durumuyla), istem önerisi, açık
sorular.

---

## İş akışı becerilerine bağlantı
- Son gün hesaplandı → `../sure-takibi/SKILL.md` (her halka ayrı satır; "güvenli son gün" esas).
- Belgeler dağınık, olay uzun → `../dava-kronolojisi/SKILL.md`; uzun ihale dokümanı →
  `../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md`.
- Müvekkile ya da yönetime sonuç anlatılacak → `../muvekkil-iletisimi/SKILL.md` (sonuç vaadi yok).

## Bu beceri ne yapmaz
- Başvuru bedelini, eşik ya da parasal limiti metinden söylemez; her seferinde araçtan ve **ilan döneminden** çeker.
- KİK karar numarası, Danıştay künyesi uydurmaz; araçta bulamadığını söyler.
- MK kontrolü yapılmamış Kurul kararını "emsal" diye sunmaz.
- EKAP'a giriş yapmaz, e-şikâyet göndermez, bedel yatırmaz, sorgulama yapmaz.
