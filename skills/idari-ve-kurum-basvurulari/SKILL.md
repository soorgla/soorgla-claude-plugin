---
name: idari-ve-kurum-basvurulari
description: >
  İdareye ve kurumlara verilecek başvuru, itiraz ve resmî yazıların metnini
  yazar: KİK başvuruları, vergi uzlaşma ve özelge talebi, SGK itirazı,
  Sayıştay savunması, makam oluru, tutanak, şirket kurul kararları. Konunun
  esasını çözmek için değil, esas alan becerisinde belirlendikten sonra
  dilekçeyi ya da yazıyı kaleme almak için; idari dava dilekçesi
  idare-davalari-imar'dadır. Kullanıcı "KİK'e başvuru dilekçesi yaz", "vergi
  cezasına uzlaşma talebi", "Sayıştay sorgusuna cevap yaz", "olur yazısı
  hazırla" dediğinde kullan.
argument-hint: "[belge türü ve olay: ör. 'KİK itirazen şikâyet — idare kararı 20.10.2026'da tebliğ', 'vergi ziyaı cezasına uzlaşma', 'makam oluru — görevlendirme']"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /idari-ve-kurum-basvurulari

İdareye ve kurumlara verilen dilekçeler ile kamu ve şirket belgelerinin taslağı. Bu bir **dilekçe/belge katmanıdır**: esas hukuki değerlendirme gerekiyorsa ilgili alan becerisi önce çalışır, bu beceri metni yazar. Ayrıntılı kurallar `references/` altındadır; her belge türünde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- Kamu ihalesi: idareye şikâyet ve KİK'e itirazen şikâyet metni (4734 m.54-56), idarenin şikâyete cevabı, ihale komisyonu kararı
- Vergi: ceza ihbarnamesine uzlaşma, cezada indirim, düzeltme ve şikâyet, özelge talebi (VUK)
- SGK idari para cezası ve prim borcu itiraz dilekçesinin metni
- Sayıştay sorgusuna ve kamu zararına savunma
- Resmî yazı, makam oluru, tutanak
- Şirket: yönetim kurulu, müdürler kurulu, genel kurul kararı, limited şirket pay devri; yatırım fizibilite raporu
- Tipik cümleler: "ihaleye itiraz", "şikâyete cevap yaz", "komisyon kararı", "özelge iste", "SGK itiraz dilekçesini yaz", "resmî yazı", "tutanak tut", "hisse devri", "fizibilite raporu"
- Devir: esas analiz önce alan becerisinde (sosyal-guvenlik-sgk, kamu-ihale, hakedis, vergi, sirketler-ticaret); idari dava dilekçesi → idare-davalari-imar; istinaf/temyiz → kanun-yollari-dilekce

## Kapsam

**Kapsar:** üç alt grup.

1. **İtiraz ve başvurular** (dışarıya, bir makama sunulan): ihale şikâyeti ve itirazen şikâyet, vergi uzlaşma / cezada indirim / düzeltme-şikâyet, özelge talebi, SGK itiraz dilekçesi.
2. **Kurumsal belgeler** (şirket içi, sicile ya da bankaya giden): yönetim kurulu, müdürler kurulu ve genel kurul kararı, limited şirket pay devri seti, yatırım fizibilite raporu.
3. **Kamu yazışmaları** (idarenin kendi belgesi): resmî yazı, makam oluru, tutanak, ihale komisyonu kararı, şikâyete cevap (idare kararı), Sayıştay/denetim savunması.

**Kapsamaz ya da yönlendirir:**
- SGK işleminin **esas analizi** (İPC hesabı, prim borcu, teşvik, statü) → `sosyal-guvenlik-sgk` becerisi, `../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md`. Bu beceri yalnızca dilekçe metnini yazar.
- İdari yargıda **dava dilekçesi** (iptal, tam yargı, vergi davası) → `../idare-davalari-imar/references/idari-dava-dilekcesi.md` (vergi davasına özgü unsurlar `../vergi/references/vergi-davasi.md`); burada yalnızca dava süresini hatırlatırız. Esas: ihale → `../kamu-ihale/SKILL.md`, hakediş → `../hakedis/SKILL.md`, vergi → `../vergi/SKILL.md`, şirket → `../sirketler-ticaret/SKILL.md`. İdari yargıda istinaf ve temyiz → `kanun-yollari-dilekce`.
- Kamu personeli disiplin savunması (657 DMK) → esas ve iskelet `../kamu-personeli/SKILL.md`; savunma istem yazısı, soruşturma raporu ve olurun biçimi bu becerideki `references/resmi-yazi-ve-olur.md`.
- Ceza soruşturması gerektiren tutanaklar (suç tespiti, kolluk tutanağı) → yalnızca işaret.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
Hedef belgenin dayanak maddesine bir `legal_get_statute_article` çağrısı yap (ör. ihale için 4734 m.55). Yanıt gelirse `soorgla ✓`. Profili oku: rol (avukat / değil), kullanıcı kamu görevlisi mi, istekli/mükellef mi?

### Adım 1 — Belge türünü sınıfla

| Belge türü | İpucu sözcükler | Oku |
|---|---|---|
| **A. İtiraz ve başvurular** | | |
| A1. İdareye şikâyet / KİK'e itirazen şikâyet | ihaleye itiraz, şartname, elendim, aşırı düşük, iş deneyim, EKAP, İKN, KİK | `references/ihale-sikayet-ve-itirazen-sikayet.md` |
| A2. Vergi: uzlaşma, cezada indirim, düzeltme-şikâyet | ihbarname, vergi ziyaı, usulsüzlük, uzlaşma, 376, düzeltme, tarhiyat | `references/vergi-uzlasma-indirim-duzeltme.md` |
| A3. Özelge talebi | özelge, mukteza, GİB görüşü, tereddüt | `references/ozelge-talebi.md` |
| A4. SGK itiraz dilekçesi (metin) | SGK cezası, İPC, prim borcu tebligatı | `references/sgk-itiraz-dilekcesi.md` → analiz için `sosyal-guvenlik-sgk` |
| **B. Kurumsal belgeler** | | |
| B1. Şirket kararı ve limited şirket pay devri | karar defteri, yönetim kurulu, müdürler kurulu, genel kurul, adres değişikliği, imza yetkisi, hisse devri | `references/sirket-kararlari-ve-pay-devri.md` |
| B2. Yatırım fizibilite raporu | fizibilite, teşvik belgesi, banka kredisi, yatırım projesi | `references/yatirim-fizibilite-raporu.md` |
| **C. Kamu yazışmaları** | | |
| C1. Resmî yazı ve makam oluru | üst yazı, arz ederim, rica ederim, olur, uygun görüşle arz | `references/resmi-yazi-ve-olur.md` |
| C2. Tutanak | olay tutanağı, tespit, teslim-tesellüm, zabıt | `references/tutanak.md` |
| C3. İhale komisyonu kararı ve şikâyete cevap | komisyon kararı, en avantajlı teklif, yasaklılık teyidi, şikâyete cevap, düzeltici işlem | `references/ihale-idare-kararlari.md` |
| C4. Sayıştay / denetim savunması | sorgu, yargılamaya esas rapor, kamu zararı, harcama yetkilisi | `references/sayistay-savunmasi.md` |

Bir olay birden fazla türe giriyorsa (ör. idare şikâyeti reddetti, istekli KİK'e gidecek: A1; idare tarafı cevap yazacak: C3) kullanıcının hangi tarafta olduğunu sor ve yalnızca o tarafın belgesini yaz.

### Adım 2 — Süreyi en başta belirle
Dilekçe türlerinde (A1-A4, C4) **ilk iş süredir**. Süreyi referans dosyasındaki tablodan değil, dayanak maddeyi `legal_get_statute_article` ile çekerek doğrula; son günü hesapla.

- `legal_calculate_deadline` ihale (`kik_complaint`, `kik_lawsuit`), vergi (`iyuk_tax_lawsuit`, `tax_settlement_request`, `tax_penalty_reduction_376`, `tax_payment_order_objection`), SGK (`sgk_ipc_objection`, `sgk_ipc_lawsuit`) ve idari dava (`iyuk_lawsuit`) kodlarını da tanır; bilinmeyen kodda geçerli kod listesini döndürür. Kodun süresini ve dayanağını madde metniyle karşılaştır.  Sayıştay ve listede olmayan süreler için **elle hesapla**: olay günü sayılmaz, süre ertesi gün başlar; son gün tatile denk gelirse `legal_check_holiday` ile kontrol et ve izleyen ilk iş gününe kaydır; sonucu `[doğrula]` diye işaretle.
- "Gün" ile "iş günü" ayrımını madde metninden al (ör. 4734 m.55'te ihale dokümanına şikâyet için ihale tarihinden **üç iş günü** öncesi sınırı). 
- Süre geçmişse ya da 3 günden az kaldıysa çıktının en üstüne 🔴 koy.

### Adım 3 — Eksik bilgiyi sor, uydurma
Referans dosyasındaki **görüşme sorularını** (eski `data_schema` alanları) sor. Taraf adı, unvan, vergi/sicil numarası, İKN, tebliğ tarihi, tutar, karar numarası gibi bilgileri **asla uydurma**; cevap yoksa metinde `[___]` boşluğu bırak. Görüşme sorusu sayısı az tutulur: önce süreyi etkileyenler (tebliğ/farkına varma tarihi), sonra makam ve taraf bilgileri, en son içerik.

### Adım 4 — soorgla'dan kaynak çek
Eski `search_profile` ve `dependencies.research_agent` tanımlarının karşılığı aşağıdaki çağrılardır; her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

- **Mevzuat:** madde numarası belliyse `legal_get_statute_article` (`law_no`, `article_no`; ek madde için `article_no: "ek 1"`). Belli değilse `legal_search_statute_semantic`. Yönetmelik/tebliğ numarası belirsizse `legal_resolve_statute` (ör. Resmî Yazışma Yönetmeliği soorgla'da `law_no: "2646"` altında; İhalelere Yönelik Başvurular Hakkında Yönetmelik `law_no: "12766"`). 
- **Kararlar:** `legal_search_cases`. İhale uyuşmazlıklarında `mahkeme: "danistay"`, `mahkeme: "kik"` (Kurul kararları); vergi için `mahkeme: "danistay"`; Sayıştay için `mahkeme: "sayistay"`. Olayı serbest cümleyle yaz. `tarih_baslangic` ile son 3 yılı iste. Danıştay iş bölümü: 2026 için **Danıştay Başkanlık Kurulu 2026/6 (RG 25.02.2026)** — ihale (4734, 4735, 2886) → **13. Daire**; vergi dairelerinden **9. Daire** gelir, kurumlar ve KDV'de yalnız belirli bölge idare mahkemelerinin (Adana, Ankara, Antalya, Bursa, Diyarbakır, Erzurum, Gaziantep, İzmir, Kayseri, Konya, Samsun) vergi dava dairesi kararlarına karşı temyizlere ve damga, emlak, yerel vergiler ile Harçlar Kanunu uyuşmazlıklarına bakar; diğer bölgeler ve vergi türleri için görevli daire RG'deki OCR metninde okunamadı → `legal_search_official_gazette(query: "Danıştay Başkanlık Kurulu", search_in: "title", sort_by: "date_desc")` ile güncel kararı bul, gerekirse `legal_case_facets(mahkeme: "danistay")` ile son kararların dairesine bak. Daire adı her yıl değişebilir; sabit sayma. 
- **Güncel emsal:** dilekçe gövdesinde en az bir **son 3 yıl** kararının tam metnini `legal_get_case_document` ile oku ve ORTAK-KURALLAR.md §7 alıntı-önerme kontrolünü yap.
- **İdari görüş:** `legal_search_admin_guidance` (KİK kurul kararları, ilke kararları). Mahkeme kararı değildir; ağırlığını ayrı belirt.
- **Resmî Gazete:** yıllık güncellenen parasal sınırlar ve tebliğ değişiklikleri için `legal_search_official_gazette` (`search_in: "title"`, `sort_by: "date_desc"`).
- **Harç ve sayısal değerler:** dava açılacaksa harç `legal_calculate_court_fee`; parasal sınır, bedel, oran ve tutarlar **beceri metnine yazılmaz**, her seferinde araçtan ya da Resmî Gazete'den çekilir. Kanun metnindeki tutarlar çoğu zaman yeniden değerlenmemiş taban tutarlardır; güncel tutar yıllık tebliğdedir.

### Adım 5 — Çıktı
Önce kısa değerlendirme ve süre tablosu, sonra belge metni. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Belge türü] — [taraf] — [tarih]

### Değerlendirme (en fazla bir paragraf)
[Başvuru yolu doğru mu, süre içinde mi, en güçlü 1-3 iddia, en büyük risk]

### Süre tablosu
| İşlem | Başlangıç (tebliğ / farkına varma) | Süre | Son gün | Dayanak | Durum |

### Eksik bilgi
[metinde [___] bırakılan alanlar]

---
[BELGE METNİ — referans dosyasındaki iskelet]
---

Dipnot — kaynaklar: [her atıf için soorgla etiketi / model bilgisi etiketi]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

- Belge metninin içinde iç anlatım ve kaynak etiketi bulunmaz; etiketler dipnotta toplanır (ORTAK-KURALLAR.md §8).
- **Word (.docx) çıktı:** hazır `.docx` şablonu yoktur (eski YAML'lardaki `templates/*.docx` dosyalarının hiçbiri mevcut değil). Kullanıcı Word isterse ortamda bir docx becerisi ya da aracı varsa onu kullanarak bu metinden belge üret; yoksa markdown metni ver ve bunu söyle.

### Adım 6 — "Dosyalama / gönderme" kapısı
Hiçbir dilekçe, karar ya da resmî yazı **avukat (kamu belgesinde yetkili amir) onayı olmadan sunulmaz, imzaya açılmaz, EKAP'a yüklenmez, KEP'le gönderilmez.** Kullanıcı "gönder", "yükle", "sun" derse ORTAK-KURALLAR.md §1 kapısını uygula ve şunu sor: "Bu metni bir avukat (ya da imza yetkilisi) gözden geçirdi mi?" Açık "evet" olmadan "sunulmaya hazır" ibaresi koyma; çıktı her zaman `TASLAK — inceleme bekliyor` işaretlidir.

Kamu belgeleri (C grubu) idarenin kendi işlemidir: metni hazırlayan kullanıcı imza yetkilisi değilse, yetki zincirini (teklif eden, uygun görüş veren, onaylayan) belgede boş bırak.

---

## İş akışı becerilerine bağlantı

Usul ve dilekçe metni bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** şikâyet, itiraz, uzlaşma ve savunma süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Başvurunun kazanılacağını garanti etmez; dilekçenin süre ve şekil yönünden reddedilmemesine odaklanır.
- Parasal sınırları, başvuru bedelini, oranları ve süreleri ezberden yazmaz; her birini çeker ya da `[doğrula]` diye işaretler.
- Olgu uydurmaz: tutanakta görülmemiş bir şeyi "tespit edilmiştir" diye yazmaz.
- Fizibilite raporunda finansal tahmin üretmez; kullanıcının verdiği rakamları düzenler, eksikleri işaretler.

---

