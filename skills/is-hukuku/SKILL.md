---
name: is-hukuku
description: >
  Özel sektör iş ilişkisini değerlendirir: fesih ve işe iade, kıdem, ihbar ve
  diğer işçilik alacakları, ibraname ve ikale, iş sözleşmesi denetimi, rekabet
  yasağı, alt işveren ve iç soruşturma (4857, TBK hizmet sözleşmesi). İşçi,
  işveren ve avukatlar için; fesih öncesi risk kontrolünde ve arabuluculuk
  hazırlığında kullan. Kullanıcı "işten çıkarıldım", "işçiyi çıkarabilir
  miyiz", "kıdem hesapla", "ibraname imzalatabilir miyiz" dediğinde. SGK,
  hizmet tespiti, iş kazası ve emeklilik sosyal-guvenlik-sgk'da; dilekçe metni
  hukuk-yargilamasi-dilekce ve kanun-yollari-dilekce becerilerinde yazılır.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: fesih bildirimi, iş sözleşmesi, bordro, SGK tebligatı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /is-hukuku

Türk iş ve sosyal güvenlik hukuku için tek birleşik beceri. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- **Konular ve mevzuat:** Türk iş hukuku: iş sözleşmesinin feshi, haklı/geçerli neden, işe iade davası, iş güvencesi, savunma alma, kıdem, ihbar ve kötüniyet tazminatı, fazla mesai, yıllık izin, UBGT, ücret alacağı, giydirilmiş ücret, zamanaşımı, ibraname, ikale, zorunlu arabuluculuk, iş mahkemesi, Yargıtay 9. Hukuk Dairesi, iş sözleşmesi denetimi, deneme süresi, rekabet yasağı, cezai şart, işe alım, fesih öncesi risk kontrolü, alt işveren (taşeron), muvazaa, geçici iş ilişkisi, serbest çalışan mı işçi mi, iç soruşturma, taciz ve mobbing şikâyeti. 4857, 1475 m.14, 7036, TBK hizmet sözleşmesi.
- **Tipik kullanıcı ifadeleri:** "işten çıkarıldım", "işçiyi çıkarabilir miyiz", "kıdem hesapla", "işe iade süresi", "arabuluculuk başvurusu", "iş sözleşmesini incele", "ibraname imzalatabilir miyiz", "rekabet yasağı geçerli mi", "taşerona verebilir miyiz", "işyerinde soruşturma başlattık".
- **Komşu beceriler:** SGK, hizmet tespiti, iş kazası ve emeklilik sosyal-guvenlik-sgk'da; dilekçe metni hukuk-yargilamasi-dilekce ve kanun-yollari-dilekce becerilerine devredilir.

## Kapsam

**Kapsar:** özel sektör iş ilişkisi (4857 sayılı İş Kanunu, TBK hizmet sözleşmesi hükümleri), fesih öncesi kontrol, ibra ve ikale, işe alım ve rekabet yasağı, işçi statüsü ve alt işverenlik, özel sektör iç soruşturması, işçilik alacakları, işe iade, zorunlu arabuluculuk, iş sözleşmesi denetimi.

**Kapsamaz ya da yönlendirir:**
- Sosyal güvenlik (5510): hizmet tespiti, iş kazası ve meslek hastalığı, SGK rücu, idari para cezaları ve prim itirazı, prim teşvikleri, emeklilik ve EYT, borçlanmalar, GSS → `sosyal-guvenlik-sgk` becerisi (`../sosyal-guvenlik-sgk/SKILL.md`). Olay hem iş hem SGK yönü taşıyorsa (ör. iş kazası sonrası fesih) iki beceri birlikte çalışır.
- Kamu personeli (657 DMK memur, sözleşmeli personel) → `../kamu-personeli/SKILL.md`; işçi statüsündeki kamu çalışanı bu beceride kalır.
- Basın İş Kanunu (5953), Deniz İş Kanunu (854), sendika ve toplu iş sözleşmesi (6356) uyuşmazlıkları → yalnızca genel çerçeve, `[incele]` işaretiyle; ayrıntılı kontrol listesi yok.
- Ceza hukuku yönü (iş kazasında taksirle yaralama/öldürme) → yalnızca işaret.
- Vergi hesabı (gelir vergisi dilimi, damga vergisi tutarı) → oran ve tutar uydurma; "bordro uzmanıyla teyit" de.

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_social_parameters` çağır (sonucu sonraki adımlarda da kullanılacak). Yanıt gelirse `soorgla ✓`. Profili oku: rol (avukat / değil), ağırlıklı taraf (işçi / işveren).

### Adım 1 — Soru tipini sınıfla ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Fesih yapılmış: işe iade, fesih bildirimine itiraz, açılmış davada savunma | işten çıkarıldım, fesih bildirimi, işe iade, haklı neden, son tutanak | `references/fesih-ve-ise-iade.md` |
| H. Fesih henüz yapılmadı: işveren "çıkarabilir miyiz?" kontrolü, ibra, ikale, arabuluculukta anlaşma | çıkarmak istiyoruz, fesih öncesi, ibraname, bozma sözleşmesi, ikale, anlaşarak ayrılma, savunma isteyelim mi | `references/fesih-oncesi-kontrol.md` (fesih yapılınca A'ya geç) |
| B. İşçilik alacakları ve hesap | kıdem, ihbar, fazla mesai, yıllık izin, UBGT, ücret, ibraname, zamanaşımı, arabuluculuk başvurusu | `references/iscilik-alacaklari.md` |
| C. Hizmet tespiti | sigortasız çalıştım, eksik gün, kayıt dışı, prim günü eksik | → `sosyal-guvenlik-sgk` becerisi (`../sosyal-guvenlik-sgk/references/hizmet-tespiti.md`) |
| D. İş kazası, meslek hastalığı, rücu | kaza, maluliyet, kusur raporu, PSD, rücu, destekten yoksun kalma | → `sosyal-guvenlik-sgk` becerisi (`../sosyal-guvenlik-sgk/references/is-kazasi-ve-rucu.md`) |
| E. SGK işlemleri, İPC ve prim itirazı, teşvik, statü, emeklilik | SGK cezası, idari para cezası, prim borcu, teşvik kodu, 4A/4B, EYT, emeklilik | → `sosyal-guvenlik-sgk` becerisi (`../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md`, `../sosyal-guvenlik-sgk/references/emeklilik-ve-borclanma.md`) |
| F. Yurt dışı hizmet ve borçlanma | yurt dışında çalıştım, 3201, borçlanma, ikili sözleşme, Almanya hizmeti | → `sosyal-guvenlik-sgk` becerisi (`../sosyal-guvenlik-sgk/references/yurtdisi-borclanma.md`) |
| G. İş sözleşmesi denetimi (hazır metin) | sözleşmeyi incele, madde madde kontrol, pazarlamacı | `references/is-sozlesmesi-denetimi.md` |
| I. İşe alım, rekabet yasağı, cezai şart, eğitim gideri | işe alacağız, hangi sözleşme türü, rekabet yasağı geçerli mi, cezai şart, eğitim masrafı iadesi | `references/ise-alim-ve-rekabet-yasagi.md` |
| J. İşçi statüsü, alt işveren, muvazaa, ödünç iş ilişkisi | freelance, serbest çalışan, fatura keserek çalışıyor, taşeron, alt işveren, muvazaa, grup şirketine geçici devir | `references/isci-statusu-ve-alt-isveren.md` |
| K. Özel sektör iç soruşturması | şikâyet geldi, soruşturma başlattık, taciz, mobbing, hırsızlık, tanık beyanı, savunma istemi | `references/ic-sorusturma.md` (fesih önerisi çıkarsa H'ye geç) |

Bir olay birden fazla tipe giriyorsa (ör. iş kazası sonrası fesih: D + A + B; soruşturma sonrası fesih: K + H) hepsini oku, çıktıyı tek belgede birleştir.

**Tarafı sor** (profilde yoksa): işçi adına mı, işveren adına mı? Kontrol listesi aynıdır; vurgu değişir. İşçi tarafında hak ve süre kaçırma riski, işveren tarafında ispat yükü ve usul hatası öne çıkar.

**Ad-hoc doktrin sorusu** (ör. "deneme süresi en fazla kaç ay?") geldiyse görüşme akışını atla: ilgili maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Kritik süreleri en başta hesapla

İş hukukunda en büyük risk süre kaçırmaktır. Herhangi bir analizden önce olayın tarihlerini topla ve ilgili referans dosyasındaki **süre tablosunu** doldur. Her sürenin dayanağını `legal_get_statute_article` ile çek. Madde tarihçesi araçları (`legal_get_statute_article_history`, `legal_list_statute_versions`) 4857, 7036 ve 5510 için 2014 sonrası değişiklikleri eksik gösterebilir; değişiklik şüphesinde `legal_search_official_gazette` (`document_type: "kanun"`) ile değiştiren kanunu ara ve güncel metindeki "(Değişik: …)" notlarına bak.

- `legal_calculate_deadline` iş hukuku sürelerini de hesaplar (İngilizce kodlar): `labor_reinstatement_mediation` (işe iade için arabulucuya başvuru, fesih tebliğinden), `labor_reinstatement_lawsuit` (son tutanaktan dava), `labor_reinstatement_notification` (kesinleşmeden sonra işverene başvuru, iş günü), `labor_mediation_duration` / `labor_mediation_extension`, `labor_sgk_application`, `hmk_appeal`, `hmk_cassation`. Bilinmeyen kod verilirse araç geçerli kod listesini döndürür. Sonucu madde metniyle karşılaştır; araçta kodu olmayan süreleri (ör. m.25/II'deki 6 iş günü) elle hesapla, `legal_check_holiday` ile kontrol et, `[doğrula]`. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴 koy.
- **Arabuluculuk süresini her zaman MCP'den çek.** Fesih, işe iade ya da işçilik alacağı sorusunda — kullanıcı arabuluculuk sormasa bile — `legal_get_statute_article` (`law_no: "7036"`, `article_no: "3"`) çağır; başvuru, görüşme (3 hafta + uzatma) ve son tutanaktan sonra dava süresini bu metinden ve 4857 m.20/1'den yaz. Beceri ya da referans metnindeki süre ifadesi yalnız yön gösterir. 

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Kararlar** — `legal_search_cases`:
- Olayı serbest cümleyle yaz (anahtar kelime listesi değil). Ör. `sorgu: "performans düşüklüğü nedeniyle savunma alınmadan yapılan fesih geçersizdir"`.
- `mahkeme: "yargitay"` + `daire`:
  - İş sözleşmesi, fesih, işe iade, işçilik alacakları, 6356 sendikal uyuşmazlıklar, işsizlik ödeneği → `"9. Hukuk Dairesi"`. Kapatılan 22. HD'nin kararları yalnız eski emsal olarak taranır (`daire: "22. Hukuk Dairesi"`, `tarih_bitis: "2020-09-02"`). 
  - Hizmet tespiti, iş kazası ve meslek hastalığı tazminatı, SGK rücu, prim, emeklilik, 3201 borçlanma, 4447 (işsizlik ödeneği hariç) → `"10. Hukuk Dairesi"`. Kapatılan 21. HD yalnız eski emsal (`tarih_bitis: "2020-09-02"`). 
  - **Yargı çevresi uyarısı:** hizmet tespitiyle birlikte ya da iş kazası tazminatıyla birlikte açılan işçilik alacakları 10. HD'ye gider; tek başına açılan işçilik alacağı 9. HD'dedir. Daireler arası iş bölümü her yıl Yargıtay Büyük Genel Kurulu kararıyla değişebilir: bu listeyi sabit sayma, şüphede güncel BGK kararını `legal_search_official_gazette` (`query: "Büyük Genel Kurulu"`, `search_in: "title"`) ile bul. 
  - Direnme kararları → `daire: "Hukuk Genel Kurulu"`
- **İşe iade davalarında son merci BAM'dır:** istinaf yoluna gidilirse bölge adliye mahkemesi ivedilikle ve kesin olarak karar verir. İşe iadede önce `mahkeme: "bam"` ile ara; Yargıtay 9. HD ve HGK yalnız ilke için. Düşük değerli alacaklarda kesinlik sınırını `legal_get_social_parameters` ile kontrol et. 
- Güncel içtihat için `tarih_baslangic` ver (ör. son 3 yıl). Eski ilke kararları için tarihi kaldır.
- Hangi dairenin baktığından emin değilsen önce `legal_case_facets` (`mahkeme: "yargitay"`) ile dağılıma bak. Not: dağılım sözcük eşleşmesine dayanır, kesin görev dağılımı değildir.
- Bir karar seçildiyse tam metni `legal_get_case_document` ile oku ve **alıntı-önerme kontrolünü** yap (ORTAK-KURALLAR.md §7). Esas/karar numarası verilmişse `legal_get_case_by_number`.
- **Zorunlu adım:** her analizde **son 3 yıldan en az bir kararın tam metnini** `legal_get_case_document` ile oku (`tarih_baslangic` ile süz). Yalnız arama özetine dayanan emsal, "Emsal kararlar" bölümüne `[çekildi ama desteği doğrulayın]` etiketiyle girer. Okunan kararı gözden geçiren notunun **Okunan** satırına yaz.
- Danıştay ve Sayıştay kararları iş hukuku sorularında kullanılmaz (SGK İPC'nin idari yargı aşaması → `sosyal-guvenlik-sgk` becerisi).

**Mevzuat** — madde numarası belliyse `legal_get_statute_article` (`law_no`, `article_no`); belli değilse `legal_search_statute_semantic`; kanun numarasından emin değilsen `legal_resolve_statute`. Temel kanunlar:
- 4857 İş Kanunu · 1475 eski İş Kanunu (yalnız m.14 kıdem tazminatı; araç atıf başlığını "İş Kanunu m. 14" diye verir, çıktıda "1475 s. (eski) İş Kanunu m.14" yaz)  · 7036 İş Mahkemeleri Kanunu · 6098 TBK (m.393-447 hizmet sözleşmesi, m.420 ibra) · 5510 Sosyal Sigortalar ve GSS Kanunu · 6331 İSG Kanunu · 3201 Yurt dışı borçlanma · 4447 İşsizlik Sigortası Kanunu · 6356 Sendikalar ve TİS Kanunu · 506 ve 1479 (eski sigortalılar için)
- Yönetmelik, tebliğ ve genelge için `law_type` ver (ör. `"Yönetmelik"`, `"Tebliğ"`).
- Olay tarihinde yürürlükte olan metin farklı olabilir: `effective_date` ile o tarihteki metni iste ya da `legal_compare_statute_versions` ile karşılaştır.

**İdari görüş ve genelgeler** — `legal_search_admin_guidance` (`belge_tur: "genelge"`, `kurum` ile SGK). Bu belgeler mahkeme kararı değildir; ağırlıklarını ayrı belirt. Kapsam dar olabilir (araç ~4 bin belge içeriyor); bulunamazsa §5 "sessiz tamamlama yok" kuralını uygula. Yeni genelge ve tebliğler için `legal_search_official_gazette`.

**Sayısal parametreler** — beceri metnine hiçbir tutar gömülmez:
- Kıdem tazminatı tavanı → `legal_get_social_parameters` (`tur: "kidem_tazminati_tavani"`); fesih tarihinin dönemine denk gelen değeri kullan, döneme denk gelmiyorsa söyle.
- Asgari ücret → `tur: "asgari_ucret_brut"` / `"asgari_ucret_net"`.
- Yasal faiz → `legal_get_legal_interest_rates`. Mevduat faizi (kıdem tazminatı için) bu araçta yok → `[doğrula]` ve kullanıcıdan banka oranını iste.
- Bakiye ömür (iş kazası, destekten yoksun kalma) → `legal_get_life_expectancy`.
- Harç ve masraf → `legal_calculate_court_fee`; arabuluculuk karar harcı `tur: "harc_arabuluculuk_karar"`.
- Enflasyon güncellemesi → `legal_calculate_cpi_change`.

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır: listede olmayan ilgili bir nokta görürsen ekle.

### Adım 5 — Çıktı
Referans dosyasındaki çıktı iskeletini kullan. Genel kalıp:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [işçi/işveren] — [tarih]

### Sonuç (tek paragraf)
[Ne yapılabilir / önce ne düzeltilmeli / dur — tek cümle neden]

### Kritik süreler
| Süre | Başlangıç | Son gün | Dayanak | Durum |

### Kontrol listesi bulguları
[her madde: işaret + kısa açıklama + atıf etiketi]

### Hesap (varsa)
[formül + girdiler + kaynak; her tutar [doğrula]]

### Emsal kararlar
[en fazla 3-5; her biri soorgla atfı ve kararın neyi desteklediği]

### Eksik bilgi
[açık sorular]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

Dilekçe ya da başvuru taslağı istendiyse Adım 7'deki devir tablosuna göre ilgili dilekçe becerisine geç; o beceri yüklü değilse ilgili referans dosyasındaki görüşme sorularını sor, cevapları al, sonra taslağı yaz. Hazır `.docx` şablonu yoktur; taslağı metin olarak üret.

### Adım 6 — "Taslaktır" kapısı
Kullanıcı avukat değilse ve çıktı fesih bildirimi, arabuluculuk başvurusu, dava ya da itiraz dilekçesi, ibraname ise ORTAK-KURALLAR.md §1'deki kapıyı uygula.

### Adım 7 — Dilekçe aşamasında devir
Değerlendirme bitip kullanıcı (ya da karar ağacındaki seçim) bir dilekçe istediğinde dilekçeyi bu becerinin içinde değil, dilekçe becerisinde kur (ORTAK-KURALLAR.md "Alan becerisi → dilekçe becerisi devri"). Devrederken şu özeti taşı: taraflar ve rolleri, kritik tarihler ve süre tablosu, çekilmiş madde ve karar künyeleri, sonuç ve istem önerisi, açık sorular.

| İstenen belge | Beceri |
|---|---|
| İşe iade ya da işçilik alacağı için **zorunlu arabuluculuk başvurusu**, iş mahkemesinde **dava dilekçesi**, cevap, ıslah (alacak), bilirkişi raporuna itiraz, delil/tanık listesi, ihtarname | `hukuk-yargilamasi-dilekce` |
| İş mahkemesi kararına **istinaf**, BAM kararına **temyiz**, istinafa/temyize cevap | `kanun-yollari-dilekce` |
| SGK idari para cezası / prim borcu **itiraz dilekçesinin metni** | `idari-ve-kurum-basvurulari` (`../idari-ve-kurum-basvurulari/references/sgk-itiraz-dilekcesi.md`) |
| Kesinleşmiş karardan sonra AYM bireysel başvurusu | `aym-aihm-basvuru` |

Dilekçe becerisi yüklü değilse taslağı bu becerideki referans iskeletiyle yaz ve süreyi yine madde metninden çek.

---

## Hesaplarda kurallar

- Hesabı **formül + girdiler** olarak göster; yalnızca sonuç yazma.
- Brüt ile neti ayır; vergi ve kesintileri tahmin etme, `[doğrula]` de.
- Ücret türünü baştan belirt: kıdem ve ihbar için **giydirilmiş brüt ücret** , fazla mesai/UBGT/izin için **çıplak ücret** .
- Her tutarın yanında `[doğrula — bilirkişi/bordro uzmanıyla teyit edin]`. Temiz görünen yanlış bir sayı bu becerinin önlemeye çalıştığı asıl hatadır.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** Adım 2'deki süreler (arabuluculuk, işe iade, zamanaşımı) hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).
- **Hesap araçları** (işçilik alacağı faizi, asgari ücret, kıdem tavanı): araç kullanımı ve bilinen eksikler → [hesaplamalar/faiz](../hesaplamalar/references/faiz.md), [hesaplamalar/parametre-ve-kur](../hesaplamalar/references/parametre-ve-kur.md); tutarlar araçtan çekilir.
- **Kronoloji / unsur-delil tablosu:** fesih ve işe iade dosyasında unsur-delil tablosu ([dava-kronolojisi/unsur-delil-tablosu](../dava-kronolojisi/references/unsur-delil-tablosu.md)) → [dava-kronolojisi](../dava-kronolojisi/SKILL.md).
- **İş sözleşmesi seti taraması** (durum tespiti, iç denetim): [tablolu-belge-incelemesi/sutun-sablonlari](../tablolu-belge-incelemesi/references/sutun-sablonlari.md) §3.

## Bu beceri ne yapmaz

- Fesih kararını vermez; kararı kontrol eder.
- Süreleri, tutarları ve daire görev dağılımını ezberden söylemez; her birini çeker ya da `[doğrula]` diye işaretler.
- Dava sonucunu garanti etmez.
- Bilirkişi raporunun yerine geçmez.

---

