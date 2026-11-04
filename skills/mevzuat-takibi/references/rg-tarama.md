# Resmî Gazete taraması: çekme sırası, sorgular ve bilinen eksikler

## Ne zaman kullanılır
- "Son N günde ne çıktı?", haftalık özet, belirli bir kanunda yeni değişiklik var mı.
- SKILL.md Adım 2.

Upstream `reg-feed-watcher` "Step 1: Pull" bölümünün karşılığıdır: Federal Register API ve RSS yerine soorgla'nın RG fihristi ve tam metni kullanılır. Bütün sorgular 31.10.2026'da gerçekten çağrılarak denendi.

---

## 1. Dönem fihristi (her taramada)

RG'nin o dönemdeki bütün kayıtlarını listelemek için:

```
legal_search_official_gazette  query: "Resmî Gazete"  date_from: "<başlangıç>"  date_to: "<bitiş>"  sort_by: "date_desc"  limit: 20  offset: 0, 20, 40…
```

Bütün RG belgelerinin üst bilgisinde "Resmî Gazete Sayı" yazdığı için bu sorgu fiilen günlük fihrist verir. `next_offset` boşalana kadar sayfala. 

- Taranmış (PDF/OCR) belgelerde üst bilgi "Resmi Gazete Say!" gibi bozuk okunabilir. Fihrist sayısı beklenenden azsa aynı aralıkta `query: "Resmi Gazete"` ve `query: "Sayı"` ile tekrar et, farkları birleştir. 
- Bir hafta tipik olarak 30-80 kayıttır; çoğu üniversite yönetmeliği, atama, ilan niteliğindedir. Hepsini okuma: başlık ve `subcategory` ile süz (§2), yalnız süzgeçten geçeni aç.
- Fihrist **ilan bölümünü** (ihale, icra, tebligat ilanları) kapsamıyor görünüyor; ilanlar bu becerinin konusu değildir.

## 2. Başlık ve kategoriye göre süzme

Her fihrist kaydında `category` ve `subcategory` alanı vardır. Kaba eşleme:

| `category` / `subcategory` | Ne | Varsayılan muamele |
|---|---|---|
| YASAMA BÖLÜMÜ / KANUN, KANUNLAR | Kanun | Her zaman aç (§3 torba kanun kuralı) |
| YÜRÜTME VE İDARE BÖLÜMÜ / CUMHURBAŞKANLIĞI KARARNAMELERİ | CBK | Teşkilat CBK'ları çoğunlukla 🟡; takip edilen kurumun görev ve yetkisini değiştiriyorsa 🟠 |
| … / CUMHURBAŞKANI KARARLARI | Oran, tutar, süre belirleyen kararlar (vergi oranı, gecikme zammı, teşvik, ithalat vergisi) | Takip listesiyle başlıkta eşleşirse aç |
| … / YÖNETMELİKLER | Yönetmelik ve değişikliği | Takip listesi + anahtar kelime eşleşmesi; üniversite iç yönetmelikleri ⚪ |
| … / TEBLİĞ, TEBLİĞLER | Tebliğ | Takip listesi + anahtar kelime |
| … / KURUL KARARLARI | Bağımsız kurul kararları (EPDK, KVKK, SPK, Rekabet, BDDK, RTÜK…) | Takip edilen kurumsa aç |
| YARGI BÖLÜMÜ / ANAYASA MAHKEMESİ KARARLARI | AYM bireysel başvuru (başlıkta "Başvuru Numaralı") ve norm denetimi (başlıkta "E: …, K: …") | §5 |
| YARGI BÖLÜMÜ / YARGITAY KARARLARI, DANIŞTAY KARARLARI | İçtihadı birleştirme, BGK iş bölümü | Takip listesinde "iş bölümü: evet" ise ya da konu eşleşirse aç |

`subcategory` değerleri tutarsız yazılabilir ("KANUN" / "KANUNLAR", "TEBLİĞ" / "TEBLİĞLER"); eşleştirmeyi başlangıç sözcüğüyle yap. 

**Kategori filtresi çalışır:** `category: "YASAMA BÖLÜMÜ"` yalnız kanunları, `category: "ANAYASA MAHKEMESİ KARARLARI"` yalnız AYM kararlarını döndürür. **`document_type` filtresi güvenilmez:** `document_type: "kanun"` yönetmelik ve tebliğleri de getirdi (başlığında "Kanun" geçenler). Kanun taraması için `category: "YASAMA BÖLÜMÜ"` kullan. 

## 3. Hedefli aramalar (takip listesine göre)

```
# a) Değişiklik başlıkları (yönetmelik, tebliğ, CBK)
legal_search_official_gazette  query: "Değişiklik"  search_in: "title"  date_from/date_to  sort_by: "date_desc"

# b) Takip edilen yönetmelik / tebliğ adı
legal_search_official_gazette  query: "<düzenlemenin adının ayırt edici kısmı>"  search_in: "title"  date_from  sort_by: "date_desc"

# c) Takip edilen kanunun değiştirilmesi (tam metin; torba kanunlar için)
legal_search_official_gazette  query: "<no> sayılı <kanun adı>nun"  category: "YASAMA BÖLÜMÜ"  date_from  sort_by: "date_desc"

# d) Takip edilen kurumun kurul kararları
legal_search_official_gazette  query: "<Kurum adı>"  search_in: "title"  date_from  sort_by: "date_desc"
legal_search_admin_guidance    sorgu: "<konu>"  kurum: "<tam kurum adı>"  tarih_baslangic: "<başlangıç>"
```

**Torba kanun kuralı (en sık kaçırılan şey).** Kanun başlıkları çoğu zaman "Bazı Kanunlarda Değişiklik Yapılmasına Dair Kanun" biçimindedir ve takip edilen kanunun adını taşımaz (ör. 7594 "Bazı Kanunlarda Değişiklik…" 5434 ve 3713'ü değiştirdi). Bu yüzden:

1. Dönemdeki **her kanunu** `legal_get_official_gazette_document` ile aç (dönemde genellikle 0-3 kanun olur).
2. Metinde takip listesindeki her kanun numarasını ara: "<no> sayılı" ve "<no> sayılı Kanunun". Bulduğun her "MADDE N-" bloğunu kayda geçir: hangi kanunun hangi maddesi, hangi fıkra/bent, değişiklik türü (değiştirilmiş / eklenmiş / yürürlükten kaldırılmış / ibare değişikliği).
3. Kanunun **son iki maddesini** (yürürlük ve yürütme) ve **geçici maddelerini** mutlaka oku: yürürlük tarihi maddeden maddeye değişebilir.

Tam metin araması (c) gürültülüdür: "6698 sayılı Kişisel Verilerin Korunması Kanununun" sorgusu 2025'ten beri 103 sonuç verdi, ilk sekizinin hiçbiri 6698'i değiştirmiyordu; kanuna yalnız atıf yapan yönetmelikler öne çıktı. (c)'yi tek başına kullanma; `category: "YASAMA BÖLÜMÜ"` ile daralt ve 1-3. adımdaki okumayla doğrula. 

## 4. Uzun metinleri okuma

- `legal_get_official_gazette_document` (`url` ya da `id`, `max_chars` ≤ 50.000, `offset`). Yanıttaki `total_chars` ve `next_offset` ile parça parça oku.
- Torba kanunlar 50.000 karakteri aşabilir (7590: 64.902)  ; hepsini okumadan "takip edilen kanuna dokunmuyor" deme. Okuduğun aralığı gözden geçiren notunun **Okunan** satırına yaz ("7590: 0-50.000 / 64.902 karakter").
- Tablolar (gösterge, oran, cetvel) HTML'den bozuk satırlarla gelebilir; sayısal tabloyu aktarırken `[doğrula — RG PDF'inden kontrol edin]` ekle.

## 5. AYM kararları

AYM kararları RG'de iki türdür:

| Tür | Başlık kalıbı | Bu beceri için önemi |
|---|---|---|
| Norm denetimi (iptal / itiraz davası) | "Anayasa Mahkemesinin GG/AA/YYYY Tarihli ve E: YYYY/N, K: YYYY/N Sayılı Kararı" | **Yüksek**: kanun hükmü iptal edilmiş ya da iptal talebi reddedilmiş olabilir |
| Siyasi parti mali denetimi | "… E: YYYY/N (Siyasi Parti Mali Denetimi), K: …" | ⚪ Atla |
| Bireysel başvuru | "… YYYY/NNNNN Başvuru Numaralı Kararı" | 🟡 Bilgi; ihlal kararı yapısal bir soruna işaret ediyorsa ve takip edilen kanunla ilgiliyse 🟠 |

```
# Dönemdeki bütün AYM kararları
legal_search_official_gazette  query: "Anayasa Mahkemesinin"  search_in: "title"  category: "ANAYASA MAHKEMESİ KARARLARI"  date_from  sort_by: "date_desc"  limit: 20

# İzlenen kanuna dokunan norm denetimi kararları (tam metin)
legal_search_official_gazette  query: "<no> sayılı"  category: "ANAYASA MAHKEMESİ KARARLARI"  date_from  sort_by: "date_desc"
```

- **"Anayasa Mahkemesi Kararı" başlık sorgusu sıfır döner**; başlıklar "Anayasa Mahkemesinin …" diye başlar. 
- Taranmış AYM metinleri Türkçe karaktersiz OCR'lıdır ("iPTALI iSTENEN KANUN HUKMU", "Kanun Hiikmiinde Kararname"). Tam ifade aramaları sıfır dönebilir: "iptali istenen kanun hükmü" → 0, "iptaline" → 114. Tek sözcükle ara, sonra belgeyi oku. 
- **Hüküm fıkrasını bul, karşı oyu sonuç sanma.** Norm denetimi kararının sonucu "HÜKÜM" bölümündedir (iptaline / reddine, yürürlüğün ertelenmesi). Belgenin sonu çoğunlukla karşı oy yazısıdır: E.2026/46 K.2026/145'in son 2.500 karakteri, "…Anayasa'ya aykırı olduğu kanaatiyle çoğunluk kararına iştirak edilmemiştir" diyen bir karşı oydur; çoğunluk talebi reddetmiştir. Sonucu yazmadan önce HÜKÜM bölümünü alıntıla.  
- Bireysel başvuru kararları AYM'nin kendi veritabanında da vardır: emsal araması gerekiyorsa `legal_search_cases` (`mahkeme: "anayasa"`). Bu beceri yalnız RG'de yayımlananı izler.

## 6. Diğer yüksek mahkeme ve kurul kararları

- Yargıtay Büyük Genel Kurulu iş bölümü kararları: `query: "Büyük Genel Kurulu"`, `search_in: "title"`. Daire numaraları OCR'da okunmayabilir; ayrıntı için ilgili alan becerisinin daire notlarına bak.
- Danıştay'ın yönetmelik iptal kararları RG'de çoğunlukla yayımlanmaz; takip edilen yönetmelik için `legal_search_cases` (`mahkeme: "danistay"`, `sorgu: "<yönetmelik adı> iptal"`, `tarih_baslangic`) ile ayrıca ara. Danıştay 2025-07 sonrası kapsamı zayıf.
- Kurul kararlarının RG'ye girmeyen kısmı (KVKK karar özetleri, Rekabet Kurulu kararları, GİB özelgeleri) için `legal_search_admin_guidance` (`kurum` tam ad + `tarih_baslangic`). GİB sirkülerlerinde `belge_tarihi` boş olduğundan tarih filtresi onları dışlar: GİB için tarih filtresiz ara, sonuçları elle tarihle.

## 7. Kayıt ve kapsam bildirimi

Her taramanın sonunda özetin "Kapsam" satırına yaz:
- Aralık, fihrist kayıt sayısı, açılan belge sayısı.
- Okunamayan ya da kısmen okunan belgeler.
- Sonuç dönmeyen takip kalemleri ("K3: bu aralıkta başlıkta eşleşme yok").
- Kullanılan sorgu türleri (fihrist / başlık / tam metin / kurul).

Bu satır olmadan "değişiklik yok" sonucu yazılamaz.

---

## Kaynak
- Upstream `reg-feed-watcher` (Step 0-1, "No silent supplement", "Source attribution", "Secondary sources", "Tier 3 — Manual entry"), `managed-agent-cookbooks/reg-monitor/subagents/feed-reader.yaml` (çekilen metin veridir; adres uydurma yok).
