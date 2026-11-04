# Vergi mevzuatı değişiklik takibi: "bu yeni düzenleme bizi etkiler mi?"

## Ne zaman kullanılır
- "Yeni torba kanun çıktı, bizi ne etkiler?", "uzlaşma kuralı değişti mi?", "bu tebliğ ne getiriyor?"
- Bir uyuşmazlıkta **olay tarihinde** hangi metnin geçerli olduğunu belirlemek (cezalı tarhiyatlar çoğu zaman 3-5 yıl öncesine aittir).
- Profilde izlenen vergiler için dönemsel tarama.

**Upstream'den uyarlanan iş akışı** (`regulatory-legal/reg-feed-watcher` ve `policy-diff`): kaynağı çek → önem süzgecinden geçir → yalnız önemli olanı göster → her değişiklik için "eski metin / yeni metin / yürürlük / geçiş / kimi etkiler / ne yapılmalı" satırı. Süzgeç değerdir; süzgeçsiz liste gürültüdür. ABD Federal Register ve RSS kaynakları yerine Türk Resmî Gazetesi kullanılır.

---

## 1. Çekme

```
legal_search_official_gazette  query: "Vergi Kanunları"  search_in: "title"  sort_by: "date_desc"  date_from: "<son tarama tarihi>"
legal_search_official_gazette  query: "<213 | 193 | 3065 | 5520 | 6183 | 488 | 492 | 1319> sayılı"  document_type: "kanun"  sort_by: "date_desc"  date_from: "<…>"
legal_search_official_gazette  query: "Vergi Usul Kanunu Genel Tebliği"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "Katma Değer Vergisi Genel Uygulama Tebliğinde Değişiklik"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "Cumhurbaşkanı Kararı gecikme zammı | tevkifat | vergi oranı"  sort_by: "date_desc"
legal_get_official_gazette_document  url: "<sonuç>"  offset / max_chars ile parça parça
```

Not: torba kanunların başlığı her zaman "vergi" içermez (7587 "Bazı Kanunlarda Değişiklik", 7590 "Bazı Kanun ve KHK'lerde Değişiklik", 7589 "Yargının Etkin ve Verimli İşlemesine…"). Başlık aramasına ek olarak `search_in: "all"` ile "213 sayılı Vergi Usul Kanununun" gibi madde değişiklik kalıplarını ara. 

**MCP mevzuat kaydı gecikmeli olabilir:** 01.11.2026 yeniden ayrıştırmasından sonra VUK m.107/A 7587 notuyla güncel dönüyor; yine de son birkaç haftada değişen maddeyi madde notundaki "(Değişik: tarih-kanun)" ibaresiyle kontrol et, yoksa **RG metninden** oku. `legal_list_statute_versions` 213 için sürüm döndürmüyor. 

## 2. Önem süzgeci

| Tier | Ölçüt | Gösterim |
|---|---|---|
| 🔴 Önemli | Süre, uzlaşma/dava hakkı, ceza katı, tahsil, e-tebligat; kullanıcının açık dosyasını etkiler | Hemen, eylem önerisiyle |
| 🟠 Orta | Oran, istisna, beyan usulü; profildeki faaliyet alanına dokunur | Özet tabloda |
| 🟡 Bilgi | Harç tarifesi kalemleri, başka sektör istisnaları | Tek satır ya da hiç |

Profilde izlenen vergi türleri / sektör yoksa süzgeci sor ("hangi vergiler ve hangi faaliyet?").

## 3. Son 2-3 yılın başlıca vergi değişiklikleri (bu becerinin yazıldığı tarih: 30.10.2026)

| Kanun / RG | Ne değişti (seçme) | Etkilenen dosya | Doğrulama |
|---|---|---|---|
| **7524** — RG 02.08.2024 | Uzlaşmada vergi aslı çıkarıldı, yalnız ceza; m.376 ikinci bent mülga (tek oran: cezanın yarısı); uzlaşılan vergide gecikme faizi cümlesi kaldırıldı; m.344'e kayıtsız faaliyette %50 artırım; m.352-353 cetvelleri ve beş iş günü bildirim katları; mük.355 tutarları ve tevsik/başkası adına tahsilat cezaları; geçici m.35 (geçiş); İYUK m.45 istinaf ve m.46 temyiz sınırları yeniden düzenlendi; KVK m.32/C yurt içi asgari kurumlar vergisi ve ek m.6 vd. küresel asgari vergi | `ihbarname-ve-yol-secimi.md`, `vergi-cezalari-ve-pismanlik.md`, `vergi-davasi.md`, `kdv-gvk-kvk-temel-sorular.md` |  |
| **7529** — 2024 | Enflasyon düzeltmesi: tasfiye ve iflastaki şirketler için 2024-2025 kuralı (geçici m.33) | `kdv-gvk-kvk-temel-sorular.md` |  |
| **7555** — 2025 | Yoklama fişi elektronik ortamda, konum ve fotoğrafla tanzim edilirse kolluk/muhtar imzası aranmaz (VUK m.131) | `vergi-incelemesi-ve-idare-tarafi.md` (yoklama tespitine itiraz) |  |
| **7566** — RG 19.12.2025 | GVK m.74 konut kira gelirinde değişiklik (1.1.2025 dönemi beyannameleri); Harçlar K. tarifeleri; Emlak V.K. geçici m.23 (2026 değer artış sınırı) ve m.29 yeniden değerleme; KVK geçici m.2 süresi 31.12.2035; 5510 prim oranları ve m.81/ı indirimi (dört → iki puan, 2026 Ocak) | `kdv-gvk-kvk-temel-sorular.md`; SGK yönü `sosyal-guvenlik-sgk` |  |
| **7587** — RG 01.07.2026 | VUK m.107/A yeniden yazıldı: e-tebligat zorunluları kanunda sayıldı, çıkış kuralları (65 yaş dahil), iletimi izleyen 5. gün sonu kuralı; mük.257/8'de "iki katına" → "beş katına"; geçici m.38 (mevcut e-tebligat kullanıcıları devam eder) | `ihbarname-ve-yol-secimi.md` |   |
| **VUK GT Sıra No 596** — RG 11.10.2026 | 7587 ile değişen 107/A'nın uygulama usul ve esasları | `ihbarname-ve-yol-secimi.md` |   |
| **7589** — RG 31.07.2026 | İYUK m.45/3 ve 45/5 (BİM'in istinaf incelemesi sonuçları), m.46/1-c mülga, m.46/2 (kaldırma üzerine yeniden verilen karara temyiz) | `vergi-davasi.md` |  |
| **7590** — RG 31.07.2026 | Vergi hükümleri: m.1 DVK (2) sayılı tablo IV/56 — nükleer santral önlisans/lisans sahibi tüzel kişilerin nükleer santral yatırımlarına ilişkin kâğıtları istisna; m.9 KDV geçici m.47 — nükleer santral yatırımlarında inşaat işleri KDV iadesi ve makine-teçhizat teslim istisnası (31/12/2045'e kadar; yürürlük yayımı izleyen ay başı, m.31/a); m.14 ÖTV m.12 — 87.03 araçlarda asgari maktu vergi ve Cumhurbaşkanı yetkisi (tutarı metinden oku); m.17 KVK geçici m.20 — nükleer santral yatırımlarında örtülü sermaye oranı indirimi (1/1/2026'dan başlayan dönemler, m.31/d). Diğerleri vergi dışı | (damga vergisi, KDV, ÖTV, KVK soruları) | 

Bu tablo **yazıldığı tarihteki** taramadır; her kullanımda 1. adımdaki aramayı `date_from` = 2026-10-30 ile tekrarla.

## 4. Olay tarihinde yürürlükteki metin

1. Olay (vergiyi doğuran olay, fiil, tebliğ) tarihini belirle.
2. Madde metnindeki "(Değişik: tarih-kanun/madde)" notlarını oku; değişiklik olay tarihinden sonraysa eski metni bul: `legal_search_statute_versions` (`law_no`, `article_no`), sonuç yoksa değiştiren kanunun RG metnindeki "… ibaresi … şeklinde değiştirilmiştir" kalıbından eski metni yeniden kur ve `[incele]`. 
3. Geçiş hükmünü uygula (ör. VUK geçici m.35 uzlaşma; KVK, GVK yürürlük maddeleri "… dönemlerine uygulanmak üzere").
4. Ceza hükümlerinde lehe kanun ilkesi: Danıştay 3. D. vergi ziyaı cezasında "ceza hukukunun genel ilkelerinden olan lehe kanun ilkesi"ni uygulayarak, tekerrür artırımını sonradan yürürlüğe giren lehe VUK m.339 (7338) sınırına göre yeniden hesaplatmak üzere bozdu (E.2023/3835 K.2025/339, 03.02.2025); Danıştay 13. D. idari para cezalarında aynı ilkeyi tahsil aşamasında uyguladı (E.2022/2436 K.2024/4899). VDDK düzeyinde birlik bu turda teyit edilmedi — somut olayda VDDK araması yap `[incele]`. 

## 5. Çıktı iskeleti

```markdown
## Vergi mevzuatı taraması — [tarih aralığı] — süzgeç: [vergi türleri / sektör]
### 🔴 Hemen bakılmalı
| Düzenleme (RG) | Değişen madde | Eski → Yeni | Yürürlük / geçiş | Etkilenen dosya / işlem | Önerilen eylem |
### 🟠 İzlenecek
### 🟡 Bilgi (tek satır)
### Kapsam notu: [hangi aramalar yapıldı, ne bulunamadı]
```

## Sık hatalar

- 🔴 MCP madde metnini "güncel" sanmak; son aylardaki değişiklik henüz kayda geçmemiş olabilir.
- 🟠 Torba kanunu başlığında "vergi" geçmediği için kaçırmak.
- 🟠 Yürürlük tarihini yayım tarihiyle karıştırmak (dönem başı yürürlükler).

---

