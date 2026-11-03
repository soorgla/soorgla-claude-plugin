# Süre hesabı ve son gün

Araçlar: `legal_calculate_deadline` (`baslangic_tarihi`, `kural_kodu`), `legal_check_holiday` (`tarih`).

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Sürenin başladığı olay ve tarihi (tebliğ, tefhim, öğrenme, işlem) | Başlangıç | `[___]`; tahmin etme |
| Süre türü ve dayanağı (hangi kanun, hangi madde) | Kural seçimi | Alan becerisi belirler |
| Dava/iş adli tatile tabi mi (HMK m.103 istisnaları, ivedi işler) | Adli tatil uzaması | Sor `[incele]` |
| Tutukluluk (ceza işlerinde) | CMK m.331 | Sor |

## Aracın tanıdığı kodlar

| `kural_kodu` | Aracın kural adı | Dayanak (araç) | Sınama sonucu (başlangıç 20.10.2026) |
|---|---|---|---|
| `hmk_appeal` | İstinaf Başvurusu (Hukuk) | HMK md.345 | 03.11.2026 (2 hafta; 29 Ekim araya girdi, son gün iş günü) |
| `hmk_cassation` | Temyiz Başvurusu (Hukuk) | HMK md.361 | 03.11.2026 |
| `cmk_appeal` | İstinaf (Ceza) | CMK md.273 | 03.11.2026 |
| `cmk_cassation` | Temyiz (Ceza) | CMK md.291 | 03.11.2026 |
| `iik_complaint` | İcra Müdürü İşlemine Şikâyet | İİK md.16, 366 | 27.10.2026 (7 gün) |
| `iyuk_appeal` | İstinaf (İdari) | İYUK md.45 | 19.11.2026 (30 gün) |
| `iyuk_cassation` | Temyiz (İdari) | İYUK md.46 | 19.11.2026 |

**Genişleyen kod listesi (01.11.2026):** araç ~70 kod tanıyor (iş, kira, SGK, KVKK, ihale, vergi, idari dava, AYM bireysel başvuru, zamanaşımı, ceza itirazları). Bilinmeyen kod verilirse "Kural bulunamadı" yerine **geçerli kod listesini** (kod, ad, kanun, madde, süre, birim) döndürür; uygun kodu oradan seç (ör. `iik_objection` yerine `iik_objection_payment_order`, `iyuk_dava` yerine `iyuk_lawsuit`, `ise_iade` yerine `labor_reinstatement_lawsuit`). Listede yoksa (cevap, bilirkişi, kesin süre, aile, gümrük, 6458) elle yola geç.

## Araç çıktısını okuma

| Alan | Anlamı | Kontrol |
|---|---|---|
| `baslangic_gun` | Olay gününün ertesi | Olay günü sayılmaz |
| `ham_bitis` | Tatil uzaması öncesi bitiş | |
| `adli_tatil_etkisi` | Son gün adli tatile denk gelirse uzama | Aşağıdaki uyarıya bak |
| `son_gun_tatil_mi` | Hafta sonu/resmî tatil kaydırması | |
| `kalan_gun` | **Bugüne** göre kalan gün (negatifse geçmiş) | Negatif ya da < 7 ise 🔴 (ORTAK-KURALLAR.md §13) |
| `kanun_maddesi` | Aracın dayanak alanı | Madde metnini ayrıca çek; araç atıf vermez |

## Bilinen tuzaklar

1. **Adli tatil iş türüne bakılmadan uygulanıyor.** `hmk_appeal` başlangıç 10.07.2026 → ham bitiş 24.07.2026 → "adli tatilin bittiği günden itibaren 7 gün" → **07.09.2026**. Bu yalnız **adli tatile tabi** dava ve işlerde doğrudur (HMK m.104); ivedi işler ve HMK m.103'teki istisnalarda süre uzamaz. Araç dava türünü sormaz → adli tatil uzaması çıktıysa iş türünü sor ve `[incele]`.
2. **Ceza işlerinde** araç "Adli tatil bu süreyi ETKİLEMEZ" ve "tutuksuz işlerde son gün adli tatile rastlarsa 3 Eylül'e uzar (CMK m.331/4)" notunu yazıyor; tutukluluğu sor. CMK m.331/4 numarası `[model bilgisi — doğrulayın]`.
3. **Arife yarım günü.** `legal_check_holiday` arifeyi `tatil: false`, `yarim: true`, "13.00'ten sonra tatil" diye işaretler; `legal_calculate_deadline` son gün arifeyse "başvuruyu saat 13.00'ten önce yapın" uyarısı yazar. Yarım günün sürenin bitimine etkisi `[model bilgisi — doğrulayın]`.
4. **Adli tatil iş günüdür.** `legal_check_holiday` adli tatil gününü `tatil: false`, `tatil_turu: "adli_tatil"` döndürür. Adli tatil süre işlemesini durdurmaz; yalnız son gün kuralını etkiler (uzama `legal_calculate_deadline`'da).
5. **Süre metinden değişmiş olabilir.** Araç kuralı sabit tutar; madde değişikliği (ör. 7499) araca işlenmemiş olabilir. Her son günde dayanak maddeyi `legal_get_statute_article` ile çek ve süre ifadesini karşılaştır; çelişirse ikisini de yaz (ORTAK-KURALLAR.md §7).
6. **Tebliğ tarihi:** e-tebligatta tebliğ, muhatabın adresine ulaştığı tarihi izleyen beşinci günün sonunda yapılmış sayılır `[model bilgisi — doğrulayın]`; kullanıcı "tebliğ" dediğinde hangi tarih olduğunu sor.

## Araç tanımadığında elle hesap

1. Dayanak maddeyi çek: `legal_get_statute_article` (harfli maddede boş dönerse `legal_list_statute_articles` ya da `legal_search_statute_semantic`).
2. Süreyi birimine göre say:
   - **Gün:** olay günü sayılmaz, ertesi günden başla, son gün dahil.
   - **Hafta:** başladığı günün ertesi haftadaki aynı adlı gününde biter (ör. salı tebliğ → iki hafta sonraki salı).
   - **Ay / yıl:** başladığı günün karşılık gelen ayındaki aynı sayılı günde biter; o ayda bu gün yoksa ayın son günü `[model bilgisi — doğrulayın]`.
   - **İş günü** (ör. 4857 m.26): her günü `legal_check_holiday` ile kontrol ederek say.
3. Son günü `legal_check_holiday` ile kontrol et; hafta sonu ya da resmî tatilse izleyen ilk iş gününe kaydır.
4. Adli tatile tabi hukuk işinde son gün 20 Temmuz–31 Ağustos arasındaysa HMK m.104 uzaması `[incele]`.
5. Sonucu tabloya `[doğrula]` ve "araç bu kuralı tanımıyor, elle hesaplandı" notuyla yaz.

## Süre tablosu iskeleti

| Süre | Olay ve tarihi | Dayanak | Hesap yolu | Son gün | Kalan | Durum |
|---|---|---|---|---|---|---|
| İstinaf | Gerekçeli karar tebliği 20.10.2026 | [HMK m.345] [soorgla] | `legal_calculate_deadline hmk_appeal` | 03.11.2026 | 4 gün | 🔴 < 7 gün |
| … | … | … | elle + `legal_check_holiday` | … | … | `[doğrula]` |

## Teyit eşiği

Son gün 7 günden yakınsa ya da geçmişse 🔴; adli tatil uzaması, arife, tebliğ tarihi belirsizliği, eski/yeni metin geçişi → `[incele]` ve avukat teyidi.

## Örnek çağrılar

```
legal_calculate_deadline baslangic_tarihi: "2026-10-20" kural_kodu: "hmk_appeal"
legal_check_holiday tarih: "2026-11-03"
legal_get_statute_article law_no: "6100" article_no: "104" law_type: "Kanun"
```
