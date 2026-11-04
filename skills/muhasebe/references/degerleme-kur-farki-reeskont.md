# Değerleme: kur farkı, reeskont, şüpheli alacak (VUK 280, 281, 285, 323)

Dönem sonunda (geçici vergi dönemleri dahil) yabancı paralı kalemlerin değerlemesi, vadesi gelmemiş senetlerin reeskontu ve şüpheli alacak karşılığı. Kur, oran ve tutar sınırı bu metne yazılmaz: kur `legal_get_exchange_rate`, reeskont oranı `legal_calculate_tax` `kur_farki_reeskont` (iç tablo) ve `legal_get_legal_interest_rates` (`tcmb_reeskont`), şüpheli alacak sınırı `had` `vuk_323_supheli_alacak`.

## Ne zaman
- "31 Aralık kur değerlemesini hangi kurla yapacağım, kur farkı ne?"
- "Alacak/borç senetlerini reeskonta tabi tutmalı mıyım, oran ne?"
- "Dava/icradaki alacak için karşılık ayırabilir miyim?"

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Değerleme günü (dönem sonu) | Kur ve oran o günün | Sor |
| Kalem türü: döviz kasa/mevduat, döviz alacak/borç, senet, kredi | Madde seçimi | Mizan / alt hesaplar |
| Döviz tutarı ve defterdeki TL karşılığı | Kur farkı | Sor |
| Efektif mi döviz mi | Efektif alış / döviz alış kuru | Sor |
| Senet nominali, vadesi, senette faiz yazılı mı | Reeskont oranı | Sor |
| Reeskont alacakta uygulandıysa borçta da uygulanıyor mu | m.285 son fıkra zorunluluğu | Sor |
| Şüpheli alacakta: dava/icra belgesi ya da protesto/yazılı istem, teminat, tutar | m.323 şartları | Sor |

## Araç çağrıları

```json
legal_get_exchange_rate  { "para_birimi": "USD", "tarih": "2025-12-31" }
{ "hesap": "kur_farki_reeskont", "kur_farki_reeskont": { "mod": "kur_farki", "doviz_tutar": 50000, "kayitli_tl": 2050000, "degerleme_kuru": "<alis>" }, "tarih": "2025-12-31" }
{ "hesap": "kur_farki_reeskont", "kur_farki_reeskont": { "mod": "reeskont", "nominal": 400000, "vade": "2026-03-15", "degerleme_tarihi": "2025-12-31" }, "tarih": "2025-12-31" }
legal_get_legal_interest_rates
{ "hesap": "had", "had": { "kod": "vuk_323_supheli_alacak" }, "tarih": "2025-12-31" }
```

- `legal_get_exchange_rate` `alis` ve `satis` döndürür; döviz cinsinden kalemde `alis`ı `degerleme_kuru`'na koy. Efektif alış kuru bu araçta yok `[doğrula]`.
- `kur_farki` modunda kur **kullanıcıdan alınır**; araç kuru kendisi çekmez. Sonucun işaretini kalemin yönüne göre yorumla (alacakta + gelir, borçta + gider).
- `reeskont` modunda `faiz_orani` verilmezse araç kendi `tcmb_yari_yil_oran` tablosundan değerleme gününe kadarki son TCMB reeskont oranını alır ve `oran_kaynagi`nda tarihini yazar. Bunu `legal_get_legal_interest_rates` → `tcmb_reeskont` (yürürlük tarihli) ile karşılaştır; tutmuyorsa `[doğrula]`. Bu araç yalnız **güncel** oranı verir; geçmiş dönem oranı için `../../hesaplamalar/references/faiz.md` "geçici yol" (RG'de "Reeskont ve Avans İşlemlerinde Uygulanacak Faiz Oranlarının Tespiti").
- Araç 365 ve 360 gün tabanıyla iki sonuç döndürür; birini seç ve tutarlı uygula.

## Hukuki çerçeve

- **Yabancı paralar:** borsa rayici ile değerlenir; rayiç yoksa kur Bakanlıkça tespit olunur; hüküm yabancı paralı senetli/senetsiz alacak ve borçlara da uygulanır; vadesi gelmemiş yabancı paralı senetler 281/285'e göre reeskonta tabi tutulabilir, senette faiz yoksa madde LİBOR'u gösterir. [Vergi Usul Kanunu m. 280](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] LİBOR yayımı sona erdiği için yerine ne kullanılacağı `[incele]` (özelge: `legal_search_admin_guidance`).
- **Kur:** her yıl sonu yayımlanan VUK genel tebliğlerinde borsa rayici bulunmayan yabancı paralar için TCMB kurlarının esas alınacağı; döviz cinsinden döviz alış, efektifte efektif alış kuru (yoksa döviz alış). [VUK GT 445](https://soorgla.com/mevzuat/20498-vergi-usul-kanunu-genel-tebligi-sira-no-445/) [soorgla] İlgili yılın tebliğini RG'de ara `[doğrula]`.
- **Alacaklar / borçlar:** mukayyet değerle; mevduat ve kredi sözleşmesine dayananlar değerleme gününe kadarki faiziyle; vadesi gelmemiş senede bağlı olanlar değerleme günü kıymetine irca **olunabilir** — senette faiz yazılıysa o, yoksa TCMB resmi iskonto haddi. [Vergi Usul Kanunu m. 281](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/), [m. 285](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Tutarlılık:** alacak senetlerini reeskonta tabi tutan, borç senetlerini de tutmak zorundadır. [Vergi Usul Kanunu m. 285](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Şüpheli alacak:** ticari/zirai kazançla ilgili olmak şartıyla (1) dava veya icra safhasındaki alacaklar, (2) protestoya ya da birden fazla yazılı isteme rağmen ödenmeyen ve haddi aşmayan alacaklar; tasarruf değerine göre karşılık ayrılabilir, teminatlı alacakta teminattan kalan kısma inhisar eder, sonradan tahsilat o dönemin gelirine; işletme esasında gider/gelir kaydı (7338/35). Had: `vuk_323_supheli_alacak`. [Vergi Usul Kanunu m. 323](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- Değersiz alacak (VUK 322) ve karşılığın hangi dönemde ayrılması gerektiği (dava açıldığı yıl kuralı) madde metninden doğrulanmalı `[doğrula]`.

## Kontrol listesi
- ✅ Kur değerleme gününe ait ve kaynağı TCMB (araç yanıtı).
- 🔴 Alacak senetleri reeskont edildi, borç senetleri edilmedi → m.285 son fıkra ihlali.
- 🔴 Dava/icra belgesi olmadan şüpheli alacak karşılığı → KKEG riski.
- 🟠 Kredi ve mevduatta reeskont değil, değerleme gününe kadar faiz tahakkuku (m.281/1, 285/1).
- 🟠 Yabancı paralı senette oran: senette yoksa madde LİBOR diyor `[incele]`.
- 🟠 Teminatlı alacakta karşılık yalnız teminattan kalan kısım.
- 🟡 Reeskont oranı yarıyıl ortasında değiştiyse değerleme günündeki oran.
- 🟡 Geçici vergi dönem sonlarında da aynı değerleme (GVK mük.120/1 "değerlemeye ait hükümler").
- [incele] Ortaklardan/ilişkili kişilerden döviz borcunda kur farkı ve örtülü sermaye (5520 m.12) → `gelir-ve-kurumlar-uygulamalari.md`.

## Sık hatalar
- Satış kuruyla değerleme; efektif kalemde döviz alış kuru (tebliğde efektif alış öncelikli).
- Reeskontu "ihtiyari" diye bir yıl yapıp bir yıl yapmamak — tutarlılık ve dönemsellik `[incele]`.
- Bir önceki yıl ayrılan reeskontu yeni yılın başında iptal etmemek `[doğrula]` (MSUGT ters kayıt uygulaması).
- Şüpheli alacağı tahsil edilince karşılığı kapatıp geliri unutmak.

## Yevmiye kaydı önerisi

```
Kur farkı (döviz alacak, kur arttı):   120/102 …      / 646 Kambiyo Kârları
Kur farkı (döviz borç, kur arttı):     656 Kambiyo Zararları / 300/320 …
Alacak senedi reeskontu:               657 Reeskont Faiz Giderleri / 122 Alacak Senetleri Reeskontu (-)
Borç senedi reeskontu:                 322 Borç Senetleri Reeskontu (-) / 647 Reeskont Faiz Gelirleri
Şüpheli alacak:                        128 Şüpheli Ticari Alacaklar / 120 Alıcılar
                                       654 Karşılık Giderleri / 129 Şüpheli Ticari Alacaklar Karşılığı (-)
```
Hesap kodlarını MSUGT metninden doğrula `[doğrula]`.

## Uyuşmazlığa dönüş
Kur farkı, reeskont ya da karşılık için ihbarname / inceleme raporu → `../../vergi/SKILL.md`. Taşı: kur ve oran kaynakları, değerleme günü, belge durumu (dava/icra/protesto).

## Çıktı
SKILL.md Adım 4. Her kalem bir satır: kalem → yöntem (madde) → kur/oran (kaynak, tarih) → fark → kayıt.
