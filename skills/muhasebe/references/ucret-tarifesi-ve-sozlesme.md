# SM/SMMM/YMM asgari ücret tarifesi ve meslek sözleşmesi

Büronun kendi işi: bir müşteri için asgari ücretin tarifeden bulunması (il grubu, işçi sayısı, kademeli kalemler) ve ücret sözleşmesinin kontrolü. Tutar ve oran bu metne yazılmaz; `legal_calculate_tax` `smmm_ucret` ile o yılın tarifesinden çekilir.

## Ne zaman
- "Limited şirketin defter tutma ücreti tarifeye göre en az ne?"
- "Kurumlar vergisi beyannamesi / tasdik ücreti?"
- "Ciroya göre kademeli ücreti hesapla."
- "Sözleşmemizde eksik ne var, müşteri sözleşmeyi feshederse ücret?"

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Yıl (`tarih`) | Tarife yıllık; araç yılı `tarih`ten alır | Bugün varsayılır — yazılı uyar |
| Unvan: SM, SMMM, YMM | Ayrı ekler (EK-1, EK-2, EK-3) | Profil `## Mali müşavirlik` |
| Büronun ili | İl grubu | Profil; yoksa sor |
| Müşteri türü (şahıs / şirket türü, bilanço / işletme) | Kalem seçimi | Sor (müşteri adı **yazılmaz**) |
| Çalışan sayısı | Tablo I işçi sütunu (`iscisiz`, `1-3`, `4-9`, `10-49`, `50+`) | Sor |
| Kademeli kalemde matrah (ciro, aktif toplamı vb.) | Kademeli hesap | Sor |
| Mevcut sözleşme metni | Kontrol listesi | İste |

## Araç çağrıları

```json
{ "hesap": "smmm_ucret", "smmm_ucret": { "ara": "limited", "il": "Bursa", "isci": "4-9" }, "tarih": "2026-01-15" }
{ "hesap": "smmm_ucret", "smmm_ucret": { "ara": "kurumlar vergisi beyannamesi", "il": "Bursa" }, "tarih": "2026-04-01" }
{ "hesap": "smmm_ucret", "smmm_ucret": { "sayfa": "<aramadan>", "sira": "<ilk kademe sırası>", "tutar": 48000000 }, "tarih": "2026-04-01" }
```

- Arama en çok 40 kalem döndürür; `il` ve `isci` ile daralt. Dönen kalemde `kademe` doluysa ücret için `sayfa` + `sira` + `tutar` ile yeniden çağır.
- İl, o yılın il grubu listesinde yoksa araç hata verir; yazımı kontrol et.
- Araç **eklemez:** kalemin "… TL'den az olmamak üzere" alt sınırı, tarife notlarındaki ilave/indirimler, KDV. Kalem metnini (`baglam`, `kalem`) çıktıya aynen koy ve notları tarifeden oku `[doğrula]`.
- KDV ve serbest meslek stopajı kırılımı: `{ "hesap": "fatura_kirilim", ... }` → `stopaj-ve-muhtasar.md`.
- Tablo kaynağı: 2026 tarifesi Resmî Gazete ekinin taranmış görüntüsünden iki bağımsız okumayla alındı; tutarı müşteriye bildirmeden önce RG ekiyle karşılaştır `[doğrula]`.

## Hukuki çerçeve

- **Asgari ücret ve yasak:** ücretin asgari miktarı tarifeyle belirlenir; **tarifedeki asgari miktarın altında ücretle iş kabulü yasaktır, aykırılık disiplin cezası gerektirir**; tarife oda → TÜRMOB → Bakanlık tasdiki → RG'de yayımla yürürlüğe girer; yenisi tasdik edilene kadar mevcut tarife uygulanır. [Serbest Muhasebeci Mali Müşavirlik Ve Yeminli Mali Müşavirlik Kanunu m. 46](https://soorgla.com/mevzuat/3568-serbest-muhasebeci-mali-musavirlik-ve-yeminli-mali-musavirlik-kanunu/) [soorgla]
- **Yönetmelik:** tarifeye uyma zorunlu; altında ücretle çalışmak disiplin cezası gerektirir; **ücretsiz işlem yapılamaz** (m.11). [SM, SMMM ve YMM Ücretlerinin Esasları Hakkında Yönetmelik m. 11](https://soorgla.com/mevzuat/9611-serbest-muhasebeci-serbest-muhasebeci-mali-musavir-ve-yeminli-mali-musavir-ucretlerinin-esaslari-hakkinda-yonetmelik/) [soorgla]
- **2026 tarifesi:** "2026 Yılı Serbest Muhasebecilik, Serbest Muhasebeci Mali Müşavirlik ve Yeminli Mali Müşavirlik Asgari Ücret Tarifesi", RG 17.12.2025, sayı 33110; yürürlük 1.1.2026; tarife RG ekinde. [RG 17.12.2025](https://www.resmigazete.gov.tr/eskiler/2025/12/20251217-2.htm) [soorgla] 2027 tarifesi Aralık'ta: `legal_search_official_gazette` `query: "Serbest Muhasebeci Mali Müşavir Yeminli Mali Müşavir asgari ücret tarifesi"` `date_from: "<yıl>-12-01"` (başlık araması `search_in: "title"` bu tarifeyi **bulmadı**; `all` kullan).
- **Disiplin cezasının türü ve süreci** (TÜRMOB disiplin yönetmeliği) ve tarife altı sözleşmenin **özel hukuk geçerliliği** (TBK m.27 kesin hükümsüzlük mü, yalnız disiplin mi) kaynaktan doğrulanmalı `[doğrula]` `[incele]`.

### Ücret sözleşmesi (Yönetmelik m.12-23)

- Ücret serbestçe kararlaştırılır; iş yapılınca ücretin tümü hak edilir (m.12).
- **Yazılı** ve **belli bir meblağı** kapsamalı; ortaklık payı verilemez; sözlü sözleşme disiplin cezası; yabancı firmayla yabancı dil/para mümkün, asgari ücret kontrolü sözleşme anındaki kurla (m.13).
- Münferit ya da süreli; **süreli sözleşme en az bir yıllık**; sözleşme yalnız kendi işlem ve süresini kapsar (m.14); hangi iş, hangi şart, ne miktar açıkça yazılır (m.15).
- Büroda tek meslek mensubuyla, ortaklıkta yetkililerce imza (m.16).
- **Haklı sebepsiz işi bırakan** meslek mensubu ücret isteyemez, peşin aldığını (avans dahil) iade eder; **iş sahibi feshederse ücretin tamamı** ödenir (meslek mensubunun kusuru hariç); peşin ücret/avans ödenmezse meslek mensubu işe başlamak/sürdürmek zorunda değil; iş devredilir ya da sahibine verilir (m.17).
- İş sahibi başka meslek mensubu katmak isterse onay; bir hafta cevapsız kalırsa sözleşme sona erer; sözleşmeye uymayan meslek mensubuna bir hafta önceden yazılı bildirimle fesih (m.19).
- Sözleşme dışı sonradan doğan işler ayrıca ücrete tabi; vergi, harç, giderler ve seyahat iş sahibinde (m.20); ücret kural olarak peşin, taksit kararlaştırılabilir (m.21).
- Tebligat adresi sözleşmedeki adres; değişiklik üç gün içinde taahhütlü mektupla bildirilir (m.23).

## Sözleşme kontrol listesi
- ✅ Yazılı, imzalı, belli meblağ, unvan ve oda sicil no.
- 🔴 Ücret o yılın tarifesindeki asgari kalemin altında → disiplin riski (m.46).
- 🔴 Ücretsiz iş ya da "ilk yıl ücretsiz" kampanyası (Yönetmelik m.11).
- 🟠 **Kapsam:** defter, beyanname, bordro/SGK, e-defter, yıllık işler (KV/GV, enflasyon/yeniden değerleme), danışmanlık, tasdik ayrı mı — kapsam dışı işler ayrıca ücretli (m.20).
- 🟠 **Süre:** başlangıç–bitiş, yenileme; süreli ise en az bir yıl (m.14).
- 🟠 **Fesih:** bildirim yolu ve süresi, m.17 ve m.19 sonuçları açık yazılmış mı.
- 🟠 **Belge teslimi ve iadesi:** belgelerin teslim tarihi (beyan son gününden önce), teslim tutanağı, sözleşme bitiminde defter/belge iadesi ve devir-teslim tutanağı — iade yükümlülüğünün mevzuat dayanağı `[doğrula]`.
- 🟠 **Sorumluluk:** müşterinin geç/eksik belge vermesinden doğan ceza ve gecikme kimde; meslek mensubunun ceza ve vergiden sorumluluğu (VUK ve 3568'deki dayanak maddeleri metinden doğrula) `[doğrula]` `[incele]`.
- 🟡 Ödeme günü, peşin/taksit (m.21), gecikmede faiz `[incele]`.
- 🟡 Tebligat adresi ve adres değişikliği (m.23); KEP adresi.
- 🟡 Ücret artışı: yıl ortasında tarife değişmez; ertesi yıl tarifesine uyum maddesi.
- [incele] Kişisel veri: müşteri ve çalışan verisinin işlenmesi (KVKK aydınlatma, veri işleyen sözleşmesi).

## Sık hatalar
- Geçen yılın tarifesiyle teklif vermek (`tarih` vermemek).
- Büronun değil müşterinin ilini kullanmak `[doğrula]` — il grubunun hangi ile göre belirlendiğini tarife notundan oku.
- Kademeli kalemde yalnız ilk dilimi uygulamak; alt sınırı unutmak.
- Tarifeyi KDV dahil sanmak.

## Uyuşmazlığa dönüş
Ücret alacağı için ihtar/icra, odaya şikâyet, disiplin soruşturması → kapıyı aç; sözleşme ve alacak yönü `../../sozlesme-incelemesi-tbk/SKILL.md` ve `../../icra-iflas/SKILL.md`; vergi yönü `../../vergi/SKILL.md`.

## Çıktı
SKILL.md Adım 4. Ücret tablosu: kalem (tarife metni) → il grubu / işçi sütunu → tarife tutarı ya da kademe hesabı → alt sınır notu → KDV ve stopaj (`fatura_kirilim`) → dayanak (tarife RG künyesi). Sözleşme incelemesinde yukarıdaki listeyi ✅/🔴/🟠/🟡 ile doldur; müşteri adı yerine `[Müşteri]`.
