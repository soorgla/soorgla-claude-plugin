# Sosyal parametreler ve döviz kuru

Araçlar: `legal_get_social_parameters` (`tur` isteğe bağlı), `legal_get_exchange_rate` (`para_birimi`, `tarih`).

## Sosyal parametreler

Parametresiz çağrı bütün **güncel** kalemleri döndürür; `tur` verilirse tek kalem. **Tarih parametresi yoktur**: geçmiş dönem değeri (ör. 2024'te feshedilen işçinin tavanı) araçtan alınamaz.

01.11.2026'da görülen harç dışı kalemler (değerler her seferinde yeniden çekilir):

| `tur` | Ne için | Not |
|---|---|---|
| `asgari_ucret_brut`, `asgari_ucret_net` | İşçilik alacağı tabanı, pasif dönem geliri, kesinlik kontrolü | Açıklamada günlük tutar da var |
| `asgari_ucret_isveren_maliyeti_tam` / `_hizmet` / `_imalat` | İşveren maliyeti | Prim indirimi açıklaması kanunla teyit edilmedi |
| `kidem_tazminati_tavani` | Kıdem tazminatı tavanı | Yarıyıllık dönem; fesih tarihi döneme düşüyor mu bak |
| `istinaf_kesinlik_siniri`, `temyiz_siniri` | HMK kanun yolu sınırları | Açıklama "dava tarihine göre uygulanır" diyor; dava tarihi başka yıldaysa güncel değer yanlış olabilir |
| `thh_parasal_sinir` | Tüketici hakem heyeti sınırı | |
| `iyuk_istinaf_siniri`, `iyuk_temyiz_siniri` | İdari yargı kanun yolu sınırları | Davanın açıldığı tarihteki sınır esas (İYUK ek m.1/2) |
| `icra_kesinlik_siniri`, `icra_temyiz_siniri` | İcra mahkemesi kararlarında istinaf/temyiz sınırı | Açıklama "şikâyet/dava tarihine göre" diyor |
| `en_dusuk_emekli_ayligi`, `prime_esas_kazanc_ust_sinir_kati` | Emekli aylığı alt tutarı; PEK üst sınırı katsayısı (TL değil, kat) | |
| `ihale_*` | 4734 eşik değerleri, doğrudan temin ve pazarlık limitleri, itirazen şikâyet bedelleri | Dönem başı her yıl 1 Şubat (KİK tebliği) |
| `harc_*` | Maktu harçlar | `references/harc.md` |

Araçta **olmayan** kalemler (01.11.2026): mevduat faizi, prime esas kazancın TL alt/üst sınırı, borçlanma tutarı, ZMSS limitleri, memur katsayıları. Bunlarda `[___ — araçta yok, birincil kaynaktan girin]` yaz, değer uydurma.

### Geçmiş dönem için geçici yol
1. Kalemin `dayanak` / `aciklama` alanındaki kaynağı (ör. "HMB Mali ve Sosyal Haklar Genelgesi", "Asgari Ücret Tespit Komisyonu Kararı") `legal_search_official_gazette` ile o dönem için ara (`search_in: "title"`, `date_from`/`date_to`).
2. Bulunursa değer `[soorgla]` (RG kaynağıyla), bulunmazsa kullanıcıdan iste ya da `[model bilgisi — doğrulayın]`.
3. Hesap tablosunda "güncel dönem değeri değildir" notu.

## Döviz kuru

`legal_get_exchange_rate` TCMB `alis` / `satis` ve **`kur_tarihi`** döndürür. Hangi kur türü olduğu (döviz/efektif) yazmaz; döviz alış/satış olduğu `[model bilgisi — doğrulayın]`.

**Her çağrıda `kur_tarihi`'ni istenen tarihle karşılaştır:**
- Hafta sonu ve tatilde önceki iş gününün kurunu vermesi olağandır.
- Veri günlük güncelleniyor. İstenen tarih ile `kur_tarihi` arasında birkaç iş gününden fazla fark varsa kuru **kullanma**; "soorgla kur verisi [kur_tarihi] tarihinde kalmış" yaz, TCMB'den değeri kullanıcıdan iste.
- **XDR (Özel Çekme Hakkı)** `para_birimi: "XDR"` ile döner; yalnız `alis` dolu, `satis` boş. CMR, Montreal, LLMC ve TTK deniz sınırlarında ÖÇH çevirisi için kullan, `kur_tarihi`'ni yaz.

Hangi günün ve hangi kurun (alış/satış, ödeme günü/dava günü/temerrüt günü) uygulanacağı hukuki değerlendirmedir (TBK m.99, döviz alacağında alacaklının seçimlik hakkı `[model bilgisi — doğrulayın]`; harçta dava tarihi) → alan becerisi `[incele]`.

### Kur tablosu iskeleti

| Tutar | Para birimi | İstenen tarih | `kur_tarihi` | Kur (alış/satış) | TL karşılığı | Kaynak |
|---|---|---|---|---|---|---|
| … | USD | … | … | … | … `[doğrula]` | [soorgla] |

## Teyit eşiği

Geçmiş dönem parametresi geçici yolla bulunduysa, kur tarihi istenen tarihten saptıysa, ÖÇH gerekiyorsa ya da sonuç kesinlik/temyiz/THH sınırına ±%10 yakınsa → 🟠.

## Örnek çağrılar

```
legal_get_social_parameters
legal_get_social_parameters tur: "kidem_tazminati_tavani"
legal_get_exchange_rate para_birimi: "USD" tarih: "2025-03-14"
```
