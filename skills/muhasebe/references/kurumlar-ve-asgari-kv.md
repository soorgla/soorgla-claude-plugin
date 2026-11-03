# Kurumlar vergisi ve yurt içi asgari kurumlar vergisi (5520 m.32, 32/C)

Yıllık kurumlar vergisi hesabı: oran (genel / finans), ihracat ve üretim indirimleri, KKEG, yurt içi asgari kurumlar vergisi karşılaştırması, geçici vergi ve kesinti mahsubu, beyan ve ödeme günleri. Oran, puan ve yüzde bu metne yazılmaz; `legal_calculate_tax` `kurumlar` ve `had` ile çekilir, madde metninden okunur.

## Ne zaman
- "Bu yıl ödenecek kurumlar vergisi ne kadar, asgari vergiye takılıyor muyuz?"
- "İhracat kazancına indirimli oran nasıl uygulanır?"
- "Asgari vergiden hangi istisnalar düşülür?"
- "Geçici vergiyi nasıl mahsup ederim, fazlası iade mi?"

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Hesap dönemi (ve özel hesap dönemi) | Oran ve asgari vergi dönemi | Sor |
| Ticari bilanço kârı | Asgari vergi tabanı (32/C/6) | Sor |
| KKEG toplamı ve kalemleri | Matrah ve asgari taban | Mizan / KKEG listesi |
| İndirim ve istisnalar sonrası matrah | Hesaplanan KV | Sor; hesap yolu `[incele]` |
| Münhasıran ihracat kazancı ve üretim kazancı (sanayi sicil belgesi) | 32/7, 32/8 | Sor; ayrıştırma yöntemi `[incele]` |
| 32/C/2 kapsamındaki istisna/indirim tutarları (bent bent) | Asgari tabandan düşülür | Sor |
| Finans sektörü mü (m.32/1 ikinci cümle) | Oran | Sor |
| İlk defa faaliyete başlama yılı | 32/C/5 (ilk üç dönem) | Sor |
| Ödenen geçici vergiler, kaynakta kesilen vergiler | Mahsup (m.34) | Sor |

## Araç çağrıları

```json
{ "hesap": "kurumlar", "girdi": { "yil": 2025, "matrah": 3200000, "ihracat_matrahi": 900000, "ticari_bilanco_kari": 2600000, "kkeg": 450000, "asgari_dusulecek": 300000 }, "tarih": "2025-12-31" }
{ "hesap": "had", "girdi": { "ara": "kv" }, "tarih": "2025-12-31" }
```

- Araç: `hesaplanan_kv`, `asgari_kv`, `odenecek_kv` (büyük olanı), `asgari_uygulandi` döndürür; **geçici vergi ve kesinti mahsubu öncesidir.**
- `asgari_dusulecek` **tek toplam**dır; 32/C/2 bentlerine göre ayrıştırmayı sen yap ve çıktıda bent bent göster.
- `ticari_bilanco_kari` verilmezse asgari vergi hesaplanmaz; `ilk_uc_donem: true` ise uygulanmaz.
- Oranlar `yil-06-30` tarihindeki en son tablo satırından gelir; `dayanak`/`ara_degerler.oran` dönemi doğru göstermiyorsa `[doğrula]`.
- Tutarlar örnektir.

## Hukuki çerçeve

- **Oran:** genel oran ve bankalar, finansal kiralama/faktoring/finansman, ödeme ve e-para kuruluşları, sigorta, emeklilik, YİD/KÖİ şirketleri için ayrı (yüksek) oran maddede. [Kurumlar Vergisi Kanunu m. 32](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]
- **Geçici vergi:** cari dönem KV oranında; GVK esaslarıyla (m.32/2); beyan ve ödeme günleri GVK mük.120/3.
- **İhracat indirimi:** münhasıran ihracattan elde edilen kazanca oran maddedeki puan kadar indirimli; aracılı ihracat sözleşmesiyle DTSŞ/SDŞ üzerinden ihracat yapan imalatçı/tedarikçiye de (7491/62). [Kurumlar Vergisi Kanunu m. 32](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]
- **Üretim kazancı:** sanayi sicil belgeli ve fiilen üretim yapan kurumların münhasıran üretim kazancı ile zirai üretim kazancına maddedeki indirimli oran; bu kazançta ihracat indirimi ayrıca uygulanmaz (m.32/8, **7582/8 ile 21.5.2026'da değişti**); indirimli oranlar diğer indirimlerden sonra uygulanır (m.32/9). Değişikliğin yürürlük ve ilk uygulanacağı dönem `[doğrula]` (7582 yürürlük maddesi okunmadı). Araç üretim kısmını `girdi.uretim_matrahi` ile alır: 2027 öncesi dönemde genel orandan `kv_uretim_indirim` puanı düşer, `kv_uretim_oran` satırının başladığı dönemden itibaren o oran uygulanır; finans kurumunda hata döner. Üretim ve ihracat kısımları çakışmamalı, araç aynı kazanca iki indirim uygulamaz.
- **Halka arz indirimi** (m.32/6) ve **32/5 birleşme** indirimi maddede; araçta yok.
- **Yurt içi asgari KV:** 32 ve 32/A'ya göre hesaplanan vergi, indirim ve istisnalar düşülmeden önceki kurum kazancının maddedeki oranından az olamaz (32/C/1); "indirim ve istisnalar düşülmeden önceki kurum kazancı" = dönem sonu ticari bilanço kârı + KKEG (32/C/6); geçici vergi dönemlerinde de uygulanır (32/C/4); ilk defa faaliyete başlayanlara başladığı dönemden itibaren üç dönem uygulanmaz (32/C/5); Cumhurbaşkanı oranı sektör vb. itibarıyla değiştirebilir (32/C/7). [Kurumlar Vergisi Kanunu m. 32/C](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]
- **32/C/2 — asgari vergi tabanından düşülecekler (madde metni):**
  - a) m.5/1'in (a), (ç), (i), (j), (k) bentleri ile (d) bendindeki istisnalar (sahip olunan taşınmazlardan elde edilen kazançlar hariç),
  - b) m.10/1'in (g), (h), (i), (j) bentlerindeki indirimler,
  - c) 4490 sayılı Türk Uluslararası Gemi Sicili Kanunu ve 3218 sayılı Serbest Bölgeler Kanunu kapsamında istisna kazançlar,
  - ç) 4691 sayılı Kanun kapsamındaki kazanç istisnası ile KV matrahından indirilen Ar-Ge ve tasarım indirimleri,
  - d) 7412 sayılı Kanunun 6/1-a bendindeki kazanç indirimi (Ek: 21.5.2026-7582/9).
- **32/C/3 — asgari vergiden düşülecek:** 32/6-7-8 indirimli oran nedeniyle alınmayan vergi ve madde yürürlüğünden önce alınmış teşvik belgelerinde yatırıma katkı tutarı kullanımı nedeniyle 32/A'ya göre alınmayan vergi. **Araç bunu düşmez.**
- Asgari verginin ilk uygulanacağı dönem: tablo 2025 hesap dönemini gösteriyor; 7524 yürürlük maddesi okunmadı `[doğrula]`.
- **KKEG:** öz sermaye faizi, örtülü sermaye faiz/kur farkı, transfer fiyatlandırmasıyla örtülü kazanç, yedek akçeler, hesaplanan KV ile para ve vergi cezaları, gecikme zammı ve faizleri … [Kurumlar Vergisi Kanunu m. 11](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla] Binek oto KKEG'i → `binek_oto`.
- **Mahsup:** m.15/1 ve 30/1-2'ye göre kesilen vergiler; geçici vergide kesintiler o dönemin geçici vergisinden; yıllık beyannamede geçici verginin **yalnız ödenen kısmı** mahsup edilir; fazlası yazıyla bildirilir, tebliğden itibaren bir yıl içinde başvuruda iade. [Kurumlar Vergisi Kanunu m. 34](https://soorgla.com/mevzuat/5520-kurumlar-vergisi-kanunu/) [soorgla]
- **Beyan ve ödeme:** beyanname hesap döneminin kapandığı ayı izleyen dördüncü ayın 1-25'i (m.14/3); vergi beyannamenin verildiği ayın sonuna kadar (m.21/1). Son gün tatile rastlarsa VUK 18/4 → `musteri-beyan-takvimi.md`.

## Kontrol listesi
- ✅ Hesaplanan KV ile asgari KV karşılaştırıldı, büyük olan seçildi.
- 🔴 İlk üç dönemdeki kuruma asgari vergi uygulamak ya da üç dönemi faaliyete başlama yerine kuruluş tarihinden saymak `[incele]`.
- 🔴 32/C/3 indirimini atlamak → indirimli oran avantajı asgari vergide kaybolur.
- 🟠 32/C/2 dışındaki istisnayı (ör. yalnız 5/1-e taşınmaz satış kazancı) asgari tabandan düşmek.
- 🟠 Üretim kazancı (32/8) varsa `uretim_matrahi` verildi mi; ihracatla çakışan kısım ayrıldı mı?
- 🟠 İhracat ve üretim kazancının ayrıştırma yöntemi belgelendi mi `[incele]`.
- 🟡 Geçici vergi dönemlerinde de asgari vergi kontrolü (32/C/4).
- 🟡 Ödenmemiş geçici vergi mahsup edilmez (m.34/4).
- [incele] Zarar mahsubu, istisna ve indirimlerin sırası ve matraha etkisi.

## Sık hatalar
- Asgari tabanı "matrah"tan hesaplamak (taban ticari kâr + KKEG).
- Tahakkuk eden ama ödenmeyen geçici vergiyi mahsup etmek.
- Finans sektörü oranını yalnız bankaya uygulamak; maddede sayılan diğerlerini atlamak.
- Araç `odenecek_kv` değerini "ödenecek net" sanmak (mahsup öncesi).

## Yevmiye kaydı önerisi

```
31.12.AAAA
691 Dönem Kârı Vergi ve Diğer Yasal Yükümlülük Karşılıkları [odenecek_kv]
        370 Dönem Kârı Vergi ve Diğer Yasal Yükümlülük Karşılıkları [odenecek_kv]
370 … [mahsup edilen]
        371 Dönem Kârının Peşin Ödenen Vergi ve Diğer Yükümlülükleri (-) [mahsup edilen]
(193 Peşin Ödenen Vergiler ve Fonlar → 371'e aktarım)
```
Hesap kodları MSUGT'den okunmadı `[doğrula]`.

## Uyuşmazlığa dönüş
KKEG eleştirisi, istisna reddi, örtülü sermaye/TF tarhiyatı, asgari vergi farkı ihbarnamesi → `../../vergi/SKILL.md`.

## Çıktı
SKILL.md Adım 4. Tablo: ticari kâr → KKEG → istisna/indirim → matrah → hesaplanan KV → asgari taban (bent bent düşülenler) → asgari KV → 32/C/3 → ödenecek → mahsuplar → net.
