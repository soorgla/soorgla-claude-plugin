# Araç kullanımı — gümrük uygulaması

## Ne zaman kullanılır
Her hesap ve aramada önce bu dosya: hangi araç var, hangi girdiyi ister, yanıtta neye bakılır, araç yanıt vermezse ne yapılır.

---

## Araçların durumu

| Araç | Ne verir | Durum | Araç yanıt vermezse |
|---|---|---|---|
| `legal_calculate_tax` `hesap: "gumruk_maliyet"` | Gümrüklenmiş maliyet: kalem kalem vergi, matrah, oran, tutar, dayanak, uyarı | ✓  | `gumruklenmis-maliyet.md` elle hesap akışı |
| `legal_calculate_tax` `hesap: "gumruk_ceza"` | 4458 m.234-241 idari para cezası: kod, matrah, kat, asgari, %10 öz bildirim, fiil yılının usulsüzlük tutarı ve tebliği | ✓  | `../../gumruk-dis-ticaret/references/ek-tahakkuk-ve-yol-secimi.md` + o yılın Gümrük Genel Tebliği |
| `legal_search_tariff` | Kod öneki ya da serbest metinle TGTC araması, yıl sürümü, kod geçmişi | ✓ | `gtip-tespiti.md` elle akış |
| `legal_search_forms` / `legal_get_form` | Form bankası: beyanname formları, YYS soru formu, rejim ekleri, kılavuzlar | ✓  | `beyanname-kodlari-ve-formlar.md` kaynak listesi |
| `legal_search_admin_guidance` | Gümrük genelgeleri (`kurum: "Ticaret Bakanlığı"`, `belge_tur: "genelge"`) | ✓  | — |
| `legal_get_exchange_rate` | TCMB kuru (`para_birimi`, `tarih`) | ✓  | — |
| `legal_get_statute_article` / `legal_list_statute_articles` | 4458, 4760, 3065 maddeleri; 4458 `statute_id 54479` | ✓ | — |
| `legal_search_official_gazette` | İthalat Rejimi Kararı, İGV, önlem tebliğleri, TGTC değişiklikleri | ✓ | — |
| `legal_calculate_deadline` | Gümrük süreleri (`customs_objection`, `customs_settlement_request`, `customs_payment`, `customs_lawsuit`, `customs_refund_application`…) | ✓ (`customs_*` kodları). Rejim süreleri (DİİB, geçici ithalat, antrepo) kod değil, izin/belgeden | Elle hesap + `legal_check_holiday`, `[doğrula]` |

---

## `gumruk_maliyet` girdileri

| Alan | Zorunlu | Açıklama |
|---|---|---|
| `gtip` | ✓ | 12 haneli güncel TGTC kodu (noktalı ya da noktasız). Kısa kodla oran bulunmaz; araç uyarır |
| `ulke` | ✓ | Menşe ülke adı (Türkçe; "Çin", "Almanya"). Ülke grubu (AB+EFTA+STA, GTS, DÜ…) araçta seçilir |
| `kiymet` | ✓ | Gümrük kıymeti **TL** (CIF + 4458 m.27 ilaveleri), tescil günü kuruyla çevrilmiş |
| `tarih` | önerilir | Beyanname tescil tarihi; oran sürümü buna göre seçilir |
| `miktar` | maktu vergide | Maktu gümrük vergisi birimi cinsinden (ton, kg, adet…); liste dipnotundaki EMY'nin asgari tutarında adet |
| `usd_kur` | dipnot EMY'de | Asgari EMY USD/adet ise tescil günü TCMB kuru |
| `odeme_sekli` | KKDF için | `pesin`, `akreditif`, `kabul_kredili`, `vadeli_akreditif`, `mal_mukabili`. Verilmezse KKDF hesaplanmaz, uyarı döner |
| `ek_gider` | — | Tescile kadarki diğer giderler (3065 m.21/c) |
| `otv` | ÖTV'li eşyada | `motor_tipi` (`icten_yanmali`, `hibrit`, `sarj_edilebilir_hibrit`, `elektrik`), `motor_hacmi`, `elektrik_gucu`, `co2`, `menzil`; (I)/(III) için `otv_miktar`, `otv_asgari_miktar`, `perakende_fiyat`, doğal gazda `kullanim: "tasit"` |

Alan adını bilmiyorsan eksik girdiyle çağır; araç gereken bilgiyi uyarıda söyler (ör. "oran için gerekli bilgi: motor_tipi").

## Yanıtın okunması

- **Vergi adları tam yazılır** (sözleşme §2): `gumruk_vergisi`, `ilave_gumruk_vergisi`, `ek_mali_yukumluluk`, `ek_mali_yukumluluk_liste_dipnotu`, `ek_mali_yukumluluk_karari`, `tarim_payi`, `gumruk_vergisi_askiya_alma`, `gumruk_vergisi_nihai_kullanim`, `anti_damping_vergisi`, `etkisizlestirme_onlemi`, `kaynak_kullanimini_destekleme_fonu`, `ozel_tuketim_vergisi_i`…`_iv`, `katma_deger_vergisi`, `uyari`, `toplam`.
- **Toplama girmeyenler:** damping ve etkisizleştirme (firma oranı tebliğde), koşullu EMY kararı (yalnız A.TR ile AB üzerinden gelirse), askıya alma ve nihai kullanım satırları (eşya tanımı ya da kullanım şartı uyarsa geçerli). Bunları ayrı satırda göster.
- **`dayanak`** sütunu oran satırında "liste / sütun (sürüm)" verir, ör. `II / DÜ (irk-2026-08-27)`: İthalat Rejimi Kararı II sayılı liste, Diğer Ülkeler sütunu, 27.08.2026 konsolide sürümü. Sürümün tescil tarihini kapsadığını kontrol et.
- **Tercihli sütun** seçildiyse açıklamada "menşe ispat belgesi gerekir" yazar → `mense-belgeleri.md`.
- **"GTİP eşlemesi doğrulanmalı"** uyarısı: ÖTV listesindeki eski kod yeni TGTC'ye yorumla eşlendi; listenin metnine bak.
- **"daha dar koşullu satır için bilgi eksik"**: verilmeyen bilgiyle (ör. CO2) oran değişebilir; kullanıcıdan iste.
- **`toplam_vergi: null` ve `eksik_kalemler`**: bir kalem hesaplanamadı (ÖTV için motor bilgisi, maktu vergi için miktar, GTİP oran listesinde yok); `bilinen_vergiler` yalnız hesaplananların toplamıdır, toplam diye sunma — eksik bilgiyi iste.
- **"Ülke adı tanınmadı"**: ad Bakanlığın ülke kod listesinde ve tercihli gruplarda yok; oran Diğer Ülkeler'den geldi. Resmî adı ya da yaygın adı sor ("Kore" → Güney Kore). Tanınan ülkenin kodu `ara_degerler.ulke_kodu`'nda.

## `gumruk_ceza` girdileri

| Alan | Ne zaman | Açıklama |
|---|---|---|
| `kod` | ✓ | Madde_fıkra_bent: `234_1_b`, `235_1_c`, `238_1_a`, `241_3`… ("234/1-b" de olur). Kodsuz ya da tanınmayan kodla çağırınca liste döner |
| `tarih` (araç parametresi) | ✓ | **Fiil tarihi** (5326 m.5/2), karar ya da tebliğ tarihi değil; usulsüzlük tutarının yılı buna göre |
| `vergi_farki`, `beyan_vergi` | m.234 | Fark ve beyana göre vergiler; 234/1-a'da %5 eşiği `beyan_vergi` ile denetlenir |
| `vergiler`, `gumruklenmis_deger`, `cif` / `fob` | maddeye göre | Matrah maddenin metnindeki tutardır (farklı, eksik, fazla eşyanın vergileri…) |
| `ton` / `kap`, `adet`, `faiz` | 235/1-b,d; 241, 237/2; 238/1-c,d | Adet = fiil, kap ya da işlem sayısı; faiz kullanıcıdan (gecikme zammı oranıyla) |
| `oz_bildirim`, `kamu_idaresi`, `yanlis_izahat` | — | Tespitten önce bildirim (%10 ya da 234/5'te ceza yok); genel yönetim kamu idaresi (241/1); idarenin yazılı yanlış izahatı (m.231/5: ceza ve faiz yok) |

Yanıtta `sonuc.ceza`, `ara_degerler` (matrah, kat, hesaplanan, asgari, usulsüzlük tutarı ve tebliği) ve `uyarilar` (koşul notları, peşin ödeme, zamanaşımı) gelir. Ton/kap ve 241/7 işlem tutarları kanun metnindeki tutardır; yeniden değerleme uyarısını çıktıya taşı. **241/1 (tek kat usulsüzlük):** AYM'nin 26.03.2026 tarihli E.2025/269, K.2026/72 kararıyla (RG 02.06.2026) "ikincil düzenlemelere aykırılık" dayanağı iptal edildi; yönetmelik, tebliğ ya da genelge yükümlülüğüne aykırılık için 241/1 cezası kesilemez, aykırı hükmün Kanunda olması gerekir. Araç bunu fiil tarihine göre uyarır.  241/3-6 bentleri kendi fiilini Kanunda saydığı için bu kararın kapsamında değil. Kaçakçılık bağlantılı fiil → `../../gumruk-dis-ticaret/references/kacakcilik-ve-idari-yaptirim-ayrimi.md`.

## Genelge araması

```
legal_search_admin_guidance  sorgu: "<konu>"  kurum: "Ticaret Bakanlığı"  belge_tur: "genelge"
```
Başlıkta "MÜLGA" ya da "… sayılı Genelge ile değişiklik yapılmıştır" ibaresi varsa güncel hâli ayrıca ara. Genelge idareyi bağlar, yükümlüyü bağlamaz; uyuşmazlıkta kanun ve yönetmelik esastır.

## Sık hatalar
- 🔴 Kıymeti döviz olarak vermek (araç TL bekler; kur tescil günü).
- 🟠 Tarih vermemek: yıl başında ve İthalat Rejimi değişikliklerinde oran farklı çıkar.
- 🟠 KKDF uyarısını çıktıdan düşürmek; vadeli ithalatta toplam eksik kalır.
- 🟡 10 haneli ya da eski yıl koduyla çağırmak; önce `gtip-tespiti.md` ile güncel 12 haneli kodu bul.
