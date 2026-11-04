---
name: kamu-mali-denetim-sayistay
description: >
  Kamu mali yönetimi ve Sayıştay denetimini 6085 ve 5018'e göre ele alır: kamu
  zararı var mı, harcama öncesi ön kontrol, harcama ve muhasebe yetkililerinin
  sorumluluğu, Sayıştay sorgusu, hesap yargılaması, ilam ve temyiz, kamu
  zararının tahsili. Sözleşmenin yürütülmesi için değil, harcamanın denetimi
  ve sorumluluk için; savunma metni idari-ve-kurum-basvurulari'na gider.
  Kullanıcı "Sayıştay sorgusu geldi", "bu harcama Sayıştay'a takılır mı",
  "tazmin hükmü", "kişi borcu çıkarıldı" dediğinde kullan.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: Sayıştay sorgusu, taslak denetim raporu, ilam, kamu zararı tebliğ yazısı, ödeme emri belgesi, harcama talimatı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /kamu-mali-denetim-sayistay

6085 sayılı Sayıştay Kanunu, 5018 sayılı Kamu Malî Yönetimi ve Kontrol Kanunu (KMYKK), Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmelik ve Sayıştay Denetim Yönetmeliği için birleşik alan becerisi. İki bakış vardır: **kamu görevlisi / idare tarafı** (harcama yetkilisi, gerçekleştirme görevlisi, muhasebe yetkilisi, strateji geliştirme birimi, üst yönetici, iç denetçi) ve **sorumlunun avukatı** (sorgu, ilam, kişi borcu). Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- 6085 Sayıştay Kanunu, 5018 Kamu Mali Yönetimi ve Kontrol Kanunu
- Kamu zararı var mı; harcama öncesi ön kontrol ("bu ödemeyi imzalayayım mı")
- Harcama yetkilisi, gerçekleştirme görevlisi ve muhasebe yetkilisinin sorumluluğu
- Sayıştay sorgusu ve savunma süresi, taslak denetim raporuna idare cevabı, yargılamaya esas rapor
- Hesap yargılaması, ilam, tazmin hükmü, Temyiz Kurulu'na temyiz, karar düzeltme, yargılamanın iadesi
- İlamın infazı ve faiz, kişi borcu, kamu zararının tahsili ve taksitlendirme, zamanaşımı
- İç kontrol, ön mali kontrol, iç denetim
- Ödenek aktarma, ödenek üstü harcama, tasarruf tedbirleri, stratejik plan ve faaliyet raporu
- Tipik cümleler: "kamu zararı çıktı", "ilamı temyiz edelim"
- Devir: savunma ve temyiz dilekçesi metni → idari-ve-kurum-basvurulari

## Kapsam

**Kapsar:** kamu zararının unsurları ve belirlenmesi, sorumluluk sıfatları ve sorumluluk haritası, harcama öncesi "kamu zararı doğurur mu" ön kontrolü, Sayıştay düzenlilik ve performans denetimi süreci, taslak denetim raporuna idare cevabı, sorgu ve savunma süresi, yargılamaya esas rapor, hesap yargılaması ve ilam, Temyiz Kurulu, karar düzeltme, yargılamanın iadesi, tavzih ve düzeltme, ilamın infazı ve faiz, idarece tespit edilen kamu zararının değerlendirilmesi, tebliği, itirazı, sulhu, taksitlendirmesi ve tahsili, zamanaşımı, iç kontrol, ön mali kontrol, iç denetim, bütçe ödeneklerinin kullanılması ve aktarılması, ödenek üstü harcama, tasarruf tedbirleri, stratejik plan ve faaliyet raporu.

**Kapsamaz ya da yönlendirir:**
- Sayıştay sorgusuna **savunma metni** ve ilama karşı **temyiz / karar düzeltme dilekçesi** → `../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`. Bu beceri esası (kamu zararı oluştu mu, tutar doğru mu, sorumluluk kimde, süre ne) değerlendirir; metni orası yazar.
- **Yapım işi, hakediş, fiyat farkı, iş artışı, YBF** kaynaklı kamu zararı → `../hakedis/references/sayistay-denetim-riski.md` (bulgu kodları orada). İhale usulü, doğrudan temin, yaklaşık maliyet → `../kamu-ihale/SKILL.md`. Bu beceri genel çerçeveyi verir, hakediş hesabını yapmaz.
- **Memur mali hakları, harcırah, ek ödeme, yersiz ödeme bildirimine karşı memurun davası** → `../kamu-personeli/references/mali-haklar-harcirah-ve-kamu-zarari.md`. Kamu zararı alacağının idarece tespit ve tahsil usulü bu becerinin `references/kamu-zarari-tahsili-ve-idari-tespit.md` dosyasında.
- **Disiplin** (tasarruf tedbirlerine aykırılık dahil) → `../kamu-personeli/SKILL.md`.
- **Ceza boyutu** (gerçek dışı belge, zimmet, görevi kötüye kullanma, ihaleye fesat; 5018 m.71/4 atfı) → `../ceza-hukuku-suclar/SKILL.md` (`references/bilisim-sahtecilik-ve-kamu-idaresi-suclari.md`: zimmet, görevi kötüye kullanma, resmî belgede sahtecilik, ihaleye fesat); savunma dilekçesi `../ceza-ve-infaz-dilekce/SKILL.md`. Kamu görevlisi hakkında soruşturma izni (4483) → `../kamu-personeli/SKILL.md`.
- **Vergi gelirlerinin tarh-tahakkuk-tahsilindeki** usul soruları → `../vergi/SKILL.md`; bunun kamu zararı (5018 m.71/2-e) yönü burada.
- Kamu zararından doğan alacağın **icra takibi** ayrıntısı → `../icra-iflas/SKILL.md`; idarenin **alacak davası** dilekçesi → `../hukuk-yargilamasi-dilekce/SKILL.md`.
- Resmî yazı, olur, iç denetim raporu cevabı biçimi → `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "6085"`, `law_type: "Kanun"`, `article_no: "48"`) çağır. Yanıt "Yargılamaya esas rapor" başlığıyla gelirse `soorgla ✓`. 

Profili oku: rol (avukat / kamu görevlisi / iç denetçi / strateji birimi), sıfat (harcama yetkilisi, gerçekleştirme görevlisi, muhasebe yetkilisi, kurul üyesi, üst yönetici, ilgili kişi), idare türü (belediye, üniversite, genel bütçeli, özel bütçeli, SGK, düzenleyici kurum, KİT).

**Numara ve kayıt tuzakları:**
- Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmelik hâlâ iki kayıtla dönüyor (`statute_id` 33885 ve 40508, ikisi de "200611058", ikisi de 29 madde); RG künyesi olan kayıt 40508, maddeleri `statute_id: 40508` ile çek. 
- Sayıştay Denetim Yönetmeliği `law_no: "15612"` ile çözülüyor (statute_id 42848). 

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Harcama/ödeme öncesi ön kontrol (idare tarafı) | imzalayayım mı, Sayıştay'a takılır mı, ödeme emri, temsil-ağırlama, tasarruf tedbiri, yolluk, ikramiye, yardım | `references/harcama-oncesi-kamu-zarari-kontrolu.md` |
| B. Kamu zararı oluşmuş mu; unsurlar, tutar, faiz başlangıcı, zamanaşımı, kim sorumlu | kamu zararı, illiyet, kusur, mevzuata aykırı, rayiç bedel, müteselsil, zamanaşımı | `references/kamu-zarari-unsurlari-ve-sorumluluk.md` |
| C. Sayıştay denetimi sürüyor: taslak rapor, sorgu, savunma, yargılamaya esas rapor | denetçi geldi, taslak rapor, idare cevabı, sorgu tebliğ edildi, 30 gün, savunma | `references/sayistay-denetim-sureci-ve-sorgu.md` |
| D. İlam çıktı: temyiz, karar düzeltme, yargılamanın iadesi, tavzih, infaz | ilam, tazmin hükmü, Temyiz Kurulu, 60 gün, karar düzeltme, tashih, ilamın infazı | `references/ilam-temyiz-ve-kanun-yollari.md` |
| E. İdare (müfettiş, iç denetim, kontrol) kamu zararı tespit etti; kişi borcu, itiraz, sulh, taksit, tahsil, dava yolu | kişi borcu çıkarıldı, borç bildirimi, değerlendirme formu, taksit, maaştan kesinti, alacak davası | `references/kamu-zarari-tahsili-ve-idari-tespit.md` |
| F. İç kontrol, iç denetim, bütçe uygulaması, ödenek aktarma, ödenek üstü harcama, stratejik plan ve faaliyet raporu | iç denetim raporu, ön mali kontrol, virman, ödenek aktarma, tertip, faaliyet raporu, performans programı, bulgu takibi | `references/ic-kontrol-ic-denetim-ve-butce.md` |

Bir olay birden fazla tipe giriyorsa (ör. sorgu konusu harcamada sorumluluk sorusu: C + B; ilam sonrası tahsil: D + E; yapım işi bulgusu: C + `../hakedis/references/sayistay-denetim-riski.md`) hepsini oku, tek belgede birleştir.

**Tarafı sor** (profilde yoksa): sorumlu (ya da avukatı) mı, idare (üst yönetici, strateji birimi, takibe yetkili birim) mi, iç denetçi mi? İdare tarafında amaç işlemi mevzuata uygun kurmak, belge zincirini tamamlamak ve tahsil usulünü doğru işletmektir; sorumlu tarafında amaç unsurlardan en az birinin yokluğunu ve süreleri korumaktır. İki taraf aynı olayda çelişebilir (üst yönetici hem sorumlu hem değerlendirici olabilir): çıkar çatışmasını `[incele]` ile işaretle.

**Ad-hoc doktrin sorusu** (ör. "muhasebe yetkilisi neyden sorumlu?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Süreleri en başta çek

Sayıştay süreleri kısadır ve sonuçları farklıdır (savunma süresi kaçarsa savunma dikkate alınmaz; temyiz süresi kaçarsa ilam kesinleşir). Her referans dosyasında **süre tablosu** vardır; her satırı madde metninden çek.

- `legal_calculate_deadline` Sayıştay sürelerini tanımıyor; elle hesapla (tebliğ günü sayılmaz), son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle. 
- Sorgular esas olarak **elektronik ortamda** tebliğ edilir; tebliğ anını sistem kaydından ve tebligat kurallarından belirle `[incele]`. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat** — `legal_get_statute_article` (`law_type: "Kanun"`):
- 6085: m.6 (yetkiler, m.6/4 konu bazlı denetim), m.7 (sorumlular), m.35 (yerindelik denetimi yasağı), m.36 (düzenlilik/performans), m.48-57 (rapor, yargılama, ilam, kanun yolları), m.58-60 (içtihat birleştirme, Danıştay uyuşmazlığı), m.78 (suç teşkil eden fiiller).
- 5018: m.8, 11, 20, 21, 26, 31-33, 41, 55-58, 60-61, 63-64, 68, 70-74, ek m.9.
- Anayasa (`law_no: "2709"`) m.160 (karar düzeltme ve idari yargı yolunun kapalılığı).
- Yönetmelikler: Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmelik (`legal_list_statute_articles` `statute_id: 40508`, `include_content: true`); Sayıştay Denetim Yönetmeliği (`law_no: "15612"`, `article_query` ile).
- Madde tarihçesi: `legal_get_statute_article_history` 6085 ve 5018 için güvenilir değil; değişikliği madde içindeki "(Değişik: …)" notlarından ve RG'den oku.

**Kararlar** — `legal_search_cases`:
- `mahkeme: "sayistay"`; olayı serbest cümleyle yaz ve idare türünü cümleye kat (ör. "belediye temsil ağırlama gideri görevle ilgili olmayan harcama kamu zararı"). Eski YAML'lardaki `konu` / `idare` filtreleri araçta yok.
- **Kapsam:** Sayıştay kararları 2006-2024 arası var; 2025 ve sonrası **sıfır**. Yıllık yoğunluk 2022'den sonra düşüyor. 
- **Temyiz Kurulu kararları ayrı daire etiketi taşımıyor:** `daire: "Temyiz Kurulu"` 0 sonuç veriyor; Temyiz Kurulu kararları ilamı veren dairenin etiketiyle ("5. Daire", "6. Daire") ve künyede "Temyiz Karar Detayı" ibaresiyle dönüyor. Temyiz Kurulu kararını metindeki "Kurulumuza", "temyiz dilekçesi", "Karar Düzeltme" ifadelerinden tanı. 
- Aynı karar birden çok kopya (farklı `belge_id`, aynı dosya no) dönebilir; tekilleştir (ör. 5. Daire 46225 altı kez). 
- Danıştay (kamu zararı borç bildiriminin niteliği, yersiz ödeme, tahsil yolu) → `mahkeme: "danistay"`; AYM (karar düzeltme, mülkiyet) → `mahkeme: "anayasa"`.
- **Zorunlu adım:** her analizde en az bir Sayıştay kararının tam metnini `legal_get_case_document` ile oku; daire ilamı, Temyiz Kurulu kararı ve Başsavcılık mütalaasını ayır (mütalaa karar değildir). "Son 3 yıl" pratikte 2022-2024'tür; 2025+ boşluğunu notta yaz.

**İdari görüş ve kurul kararları** — `legal_search_admin_guidance`:
- `kurum: "Sayıştay Genel Kurulu"` → yalnız RG'de yayımlanmış birkaç İçtihadı Birleştirme Kararı (2006, 2011, 2013; toplam 28 parça). Sayıştay İBK'ları bağlayıcıdır (6085 m.58/3); güncel İBK için RG'yi ayrıca tara (`legal_search_official_gazette` `query: "Sayıştay Genel Kurulu İçtihadı Birleştirme Kararı"`, `sort_by: "date_desc"`). 
- Gelir kaybı türü kamu zararında (5018 m.71/2-e) GİB iç genelgeleri artık var: `kurum: "Gelir İdaresi Başkanlığı"`, `belge_tur: "ic_genelge"` (ör. Tahsilat İç Genelgesi 2022/2). 
- Kamu alımlarında danışıklı teklif ve yaklaşık maliyetin şişirilmesi (rayiç bedel üstü alım, m.71/2-d) için `kurum: "Rekabet Kurulu"`, `sorgu: "kamu alımlarında fiyat teklifleri yaklaşık maliyet danışıklı hareket"`, `tarih_baslangic` ile. 
- **Yok:** Hazine ve Maliye Bakanlığı (BÜMKO) görüşleri, İç Denetim Koordinasyon Kurulu kararları, Strateji ve Bütçe Başkanlığı rehberleri. `kurum: "Hazine ve Maliye Bakanlığı"` 0 dönüyor; filtresiz "iç denetim" sorgusu ilgisiz Rekabet/BDDK kararları getiriyor. Bu görüşleri kullanıcıdan iste `[incele]`. 

**Resmî Gazete** — `legal_search_official_gazette`: tasarruf tedbirleri genelgeleri (`search_in: "title"`, `query: "Tasarruf Tedbirleri"`, `sort_by: "date_desc"`), yılı merkezi yönetim bütçe kanunu (ödenek, silme ve avans tutarları; tutar beceriye yazılmaz), Sayıştay İBK'ları, yönetmelik değişiklikleri.

**Sayısal parametreler** — beceri metnine hiçbir tutar, oran ya da sınır yazılmaz:
- Kamu zararı faizi: Kamu Zararlarının Tahsili Yönetmeliği m.18/6 aksine hüküm yoksa 3095'e yollar; `legal_get_legal_interest_rates` 7589 sonrası kanuni faizi yanlış verebilir. Oranı RG ve madde metninden kontrol et `[doğrula]`. Taksitte muacceliyet faizi 6183 m.51 gecikme zammı oranına bağlı (yönetmelik m.16/6); bu oran araçta yok, RG'den çek. 
- Ödenek aktarma yüzdeleri, avans üst sınırları, silinebilecek alacak tutarları, para cezası çarpanları: madde metninden ve yılı bütçe kanunundan oku, `[doğrula]`.

### Adım 4 — Analiz

İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

**Sıra (eski YAML'lardaki "denetim mantığı", doğrulanarak korundu):** (1) süre ve tebliğ, (2) işlemin dayanağı olan mevzuat (işlem tarihindeki metin), (3) kamu zararının dört unsuru (mevzuata aykırılık, kaynakta eksilme/artışa engel, kasıt-kusur-ihmal, illiyet), (4) yerindelik / takdir yetkisi itirazı (6085 m.35/1-a), (5) tutar, oluşma tarihi, faiz başlangıcı, (6) sorumluluk sıfatı ve paylaşımı, (7) yol seçimi ve sonraki adım `[incele]`.

**Orantılılık:** "Temyiz süresi kaç gün?" iki cümle ister.

### Adım 5 — Çıktı

Referans dosyasındaki iskeleti kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (Kaynaklar satırına: "Sayıştay kararları araçta 2024 sonuna kadar")

## [Konu]: [sorumlu / idare / iç denetim] — [idare türü] — [tarih]

### Sonuç (tek paragraf)
[✅ imzalanabilir / ⚠️ şu tamamlanmadan imzalama / 🛑 dur — ya da: kamu zararı unsurları oluşmuş/oluşmamış görünüyor; önerilen yol ve son gün]

### Kritik süreler
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |

### Kamu zararı unsurları
| Unsur | Var mı | Gerekçe | Atıf |

### Sorumluluk haritası
| Sıfat | Kişi | İmzaladığı belge | Sorumluluk dayanağı | Risk |

### Bulgular
[her madde: işaret + kısa açıklama + atıf etiketi]

### Dayanaklar
[madde, Sayıştay daire/Temyiz Kurulu kararı, İBK, Danıştay — her biri etiketli]

### Eksik bilgi
[açık sorular]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı

Avukat olmayan kullanıcı şunları yapmadan önce ORTAK-KURALLAR.md §1 kapısını uygula: sorguya savunma göndermek, ilamı temyiz etmek ya da karar düzeltme istemek, kamu zararı borcunu kabul edip taahhüt ya da sulh imzalamak, maaştan kesintiye muvafakat vermek, taksit planı ve borç senedi imzalamak.

Borcu yazılı taahhüt etmek ya da sulh imzalamak geri dönüşü zor kapıdır: taahhüt hâlinde değerlendirme aşaması atlanarak borç tahakkuk ettirilir (yönetmelik m.7/A-5).  Her zaman `[incele]`.

**İdare tarafı:** üst yönetici, takibe yetkili birim ya da iç denetçiye "bu zarar sorumludan istenir mi" sorusunda sorumlu lehine savunma yazma; dosyanın eksiklerini (dayanak, illiyet, sorumlu tespiti, oluşma tarihi, tebliğ) ve itiraz/dava riskini çıkar. İç değerlendirme ile sorumluya gidecek yazıyı ayır (ORTAK-KURALLAR.md §1 gönderim yeri kontrolü). Üst yönetici aynı zamanda harcama yetkilisiyse değerlendirmenin kimde olacağını yönetmelik m.7/A-2'den kontrol et.

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Sayıştay sorgusuna savunma; ilama karşı temyiz, karar düzeltme, yargılamanın iadesi, tavzih dilekçesi | `../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md` (temyiz dilekçesi unsurları 6085 m.54 — `references/ilam-temyiz-ve-kanun-yollari.md`) |
| Taslak denetim raporuna idare cevabı, iç denetim raporuna cevap, değerlendirme formu, olur, kamu zararı tebliğ yazısı | İçerik bu becerinin referansları; biçim `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` |
| Sorumlunun kamu zararı borç bildirimine itiraz ve sulh/taksit dilekçesi | İskelet `references/kamu-zarari-tahsili-ve-idari-tespit.md`; avukatsız memur → `../vatandas-basvurulari/SKILL.md` |
| İdarenin sorumludan alacak davası, ihtiyati haciz talebi | `../hukuk-yargilamasi-dilekce/SKILL.md`; takip → `../icra-iflas/SKILL.md` |
| Yersiz ödemeye ilişkin memur davası (aylıktan kesinti, kesin işlem niteliğindeyse) | `../kamu-personeli/SKILL.md` + `../idare-davalari-imar/references/idari-dava-dilekcesi.md` |
| Yapım işi / hakediş bulgusuna savunma | Esas `../hakedis/references/sayistay-denetim-riski.md`; metin `../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md` |
| AYM bireysel başvuru (Temyiz Kurulu kararı sonrası) | `../aym-aihm-basvuru/SKILL.md` `[incele]` |

Devrederken taşı: sorumlunun sıfatı ve işlem tarihindeki görevi, sorgu/ilam künyesi ve tebliğ tarihi, süre tablosu, unsur tablosu, sorumluluk haritası, çekilmiş madde ve karar künyeleri (etiketleriyle), istem önerisi, açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** savunma, temyiz ve karar düzeltme süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Bütçe tertibi kodlaması (ABS ekonomik kod) ya da muhasebe kaydı üretmez; strateji/mali hizmetler biriminin işinin yerine geçmez.
- Faiz oranını, ödenek aktarma yüzdesini, silinebilecek alacak tutarını, para cezası tutarını metinden söylemez; madde metninden, RG'den ya da araçtan çeker veya `[doğrula]` der.
- Sayıştay'a, idareye ya da mahkemeye başvuru göndermez; e-sorgu sistemine erişmez.
- 2025 ve sonrası Sayıştay kararlarını bulamaz; bu boşluğu her çıktıda söyler.

---

