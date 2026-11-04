# Yeniden değerleme (VUK mük.298/Ç)

Enflasyon düzeltmesi şartlarının oluşmadığı (ya da kanunla "oluşmamış sayıldığı") hesap dönemlerinde amortismana tabi iktisadi kıymetlerin ve birikmiş amortismanlarının yılın yeniden değerleme oranıyla artırılması; değer artışının pasifte özel fonda izlenmesi. Oran bu metne yazılmaz; `legal_calculate_tax` `yeniden_degerleme` ya da `had` `vuk_yeniden_degerleme_orani` ile o yıl için çekilir.

## Ne zaman
- "Bu yıl yeniden değerleme yapabilir miyim, oran ne?"
- "Makinenin yeniden değerleme sonrası değeri ve fon tutarı?"
- "Fonu sermayeye ekleyebilir miyim / satışta fon ne olur?"
- Geçici vergi döneminde yeniden değerleme (oran farklı, aşağıda).

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Değerleme yılı / geçici dönem | Oran o yılın (ya da dönemin) oranı | Sor |
| Kıymetin yasal defterdeki değeri ve birikmiş amortismanı (dönem sonu) | Ç-2 | Sor; ayrılmamış amortisman varsa "ayrılmış varsay" (Ç-2) |
| Aktife giriş yılı | Aktife girdiği dönemde yapılmaz (Ç-9) | Sor |
| Maliyete eklenmiş kur farkı / kredi faizi var mı, hangi yıl | Ç-1 kapsam dışı | Sor `[incele]` |
| Mükellef niteliği | Tam mükellef + bilanço esası; mük.298/A-9 kapsamı ve yabancı para kayıt izni olanlar hariç | Sor |
| Kıymet sat-kirala-geri al ya da kira sertifikasına konu mu | Kapsam dışı | Sor |
| Özel hesap dönemi var mı | Başladığı takvim yılının oranı (Ç-3) | Sor |

## Araç çağrıları

```json
{ "hesap": "yeniden_degerleme", "yeniden_degerleme": { "yil": 2025, "maliyet": 1200000, "birikmis_amortisman": 480000, "aktife_giris_yili": 2022 }, "tarih": "2025-12-31" }
{ "hesap": "had", "had": { "kod": "vuk_yeniden_degerleme_orani" }, "tarih": "2025-12-31" }
```

- Araç oranı `yil-06-30` tarihindeki **en son** `vuk_yeniden_degerleme_orani` satırından alır. Yılın oranı tabloya henüz girmediyse hesap yapmaz, son kaydı gösteren bir hata döndürür (önceki yılın oranı kullanılmaz). Bu durumda oranı o yılın VUK genel tebliğinden RG'de bul ve kullanıcıya bildir `[doğrula]`.
- `aktife_giris_yili >= yil` ise araç hata döndürür (Ç-9).
- Örnek tutarlar yalnız biçim içindir.

## Hukuki çerçeve

- **Kapsam ve şart:** tam mükellef, bilanço esasına göre defter tutan GV/KV mükellefleri (kollektif, adi komandit, adi şirketler dahil; mük.298/A-9 kapsamındakiler ve kayıtlarını yabancı parayla tutanlar hariç), (A) fıkrasındaki enflasyon düzeltmesi şartlarının gerçekleşmediği dönem sonunda amortismana tabi kıymetlerini ve amortismanlarını yeniden değerleyebilir; sat-kirala-geri al ve kira sertifikasına konu olanlar hariç. [Vergi Usul Kanunu m. mükerrer 298](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Oran:** (B) fıkrasındaki oran; yıl için ilan edilir; özel hesap döneminde dönemin başladığı takvim yılının oranı; **geçici vergi dönemlerinde** ayrı oran (önceki yılın Kasım ayından başlayan 3, 6, 9 aylık dönemlerde Yİ-ÜFE ortalama artışı). [Vergi Usul Kanunu m. mükerrer 298](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla] 2025 oranı VUK GT 585 (RG 27.11.2025, sayı 33090) ile ilan edildi. 2026 oranı bu tarihte RG'de görünmüyor; Kasım-Aralık'ta `legal_search_official_gazette` `query: "yeniden değerleme oranı"` `sort_by: "date_desc"` ile ara `[doğrula]`.
- **Hesap:** değerler ve amortismanlar oranla çarpılır (Ç-3); değer artışı = yeniden değerleme sonrası ve öncesi net bilanço aktif değeri farkı, kıymet bazında pasifte özel fon (Ç-4); amortisman yeni değer üzerinden devam eder (Ç-5). [Vergi Usul Kanunu m. mükerrer 298](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Fonun kullanımı:** sermayeye ilave dışında başka hesaba nakledilen ya da işletmeden çekilen kısım o dönem vergilendirilir; sermaye ilavesi kâr dağıtımı sayılmaz (Ç-6); kıymet elden çıkarılınca fondaki tutar "aynen amortismanlar gibi" işlem görür (Ç-7).
- **Yıl kuralları:** her yılın oranı yalnız o yıla uygulanır, geçmişe dönük yapılamaz (Ç-8); aktife girdiği hesap döneminde yapılmaz (Ç-9); bir yıl yapılmaması sonraki yılları engellemez (Ç-13); enflasyon düzeltmesi şartının oluştuğu dönemde yapılmaz (Ç-11).
- **2025-2027 dönemi:** geçici m.37 ile 2025, 2026 ve 2027 hesap dönemlerinde (geçici dönemler dahil) enflasyon düzeltmesi yapılmaz ve bu dönemler (Ç) bakımından "şartların gerçekleşmediği dönem" sayılır → bu yıllarda yeniden değerleme yolu açıktır; mük.298/A-9 kapsamındakiler hariç. [Vergi Usul Kanunu m. geçici 37](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Usul ve örnek kayıtlar:** VUK GT 537 İkinci Bölüm (sürekli yeniden değerleme), m.10 oran, m.11-12 kayıt örnekleri. [VUK GT 537](https://soorgla.com/mevzuat/39523-vergi-usul-kanunu-genel-tebligi-sira-no-537/) [soorgla]

## Kontrol listesi

- ✅ Yılın oranı araçtan geldi ve `dayanak` o yılın tebliğini gösteriyor.
- 🔴 Aktife giriş yılı = değerleme yılı → yapılmaz (Ç-9).
- 🔴 Enflasyon düzeltmesi yapılan dönem (ya da A-9 kapsamı) → yapılmaz.
- 🟠 Maliyete eklenmiş kur farkı / kredi faizi ayrıştırıldı mı (aktifleştirme yılına ait olanlar hariç kapsam dışı, Ç-1).
- 🟠 Fon kıymet bazında ayrıntılı izleniyor mu (Ç-4); amortisman kayıtlarında değer artışı ve hesap şekli gösterildi mi (Ç-5).
- 🟡 Geçici vergi döneminde yapılacaksa yıllık oran değil dönem oranı kullanıldı mı.
- 🟡 Satış/devirde fon "amortisman gibi" kapatıldı mı (Ç-7).
- [incele] Fonun sermayeye eklenmesi ya da başka hesaba aktarılması planlanıyorsa vergi sonucu.

## Sık hatalar
- Önceki yıl yapılmadı diye o yılın oranını da uygulamak (Ç-8 yasağı).
- Arsa, arazi gibi amortismana tabi olmayan kıymetlere uygulamak.
- Fonu "geçmiş yıl kârı"na aktarmak → o dönem vergilendirilir (Ç-6).
- Yeni yılın oranı yayımlanmadan aracın döndürdüğü eski oranla kapanış yapmak.
- 2023 sonu enflasyon düzeltmesi yapılmış kıymette esas değeri düzeltilmiş son bilançodan almamak (Ç-11 üçüncü cümle).

## Yevmiye kaydı önerisi

```
31.12.AAAA
253 Tesis, Makine ve Cihazlar (ilgili duran varlık)   [yeni maliyet − eski maliyet]
        257 Birikmiş Amortismanlar                         [yeni birikmiş − eski birikmiş]
        522 MDV Yeniden Değerleme Artışları                [deger_artisi_fonu]
              (alt hesap: kıymet bazında, "213 s. K. mük.298")
```

Satışta fonun kapatılması ve gelir hesabı (VUK GT 537 m.12 örneğinde 679 kullanılmış) — örneği tebliğden oku `[doğrula]`.

## Uyuşmazlığa dönüş
İnceleme fonun kullanımını (örtülü dağıtım, başka hesaba nakil) ya da kapsamı eleştirdiyse → `../../vergi/SKILL.md`.

## Çıktı
SKILL.md Adım 4: girdi (yıl, maliyet, birikmiş) → oran (kaynak tebliğiyle) → yeni değerler → fon → dayanak → parametre dönemi.
