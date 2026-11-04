# Coğrafi işaret ve geleneksel ürün adı

## Ne zaman kullanılır
- "Yöremizin ürününü tescil ettirmek istiyoruz", "coğrafi işaretli ürünü başkası taklit ediyor", "tescilli coğrafi işareti kullanabilir miyiz", "amblem zorunlu mu", "belediye/oda başvuru sahibi olabilir mi".
- Coğrafi işaretli ürünle çakışan marka başvurusu (m.48 ilişkisi).

Bu dosya kısa tutuldu; eski YAML'larda coğrafi işarete özgü görev tanımı yoktu, içerik madde metinlerinden kuruldu.

---

## Kavramlar

| Tür | Tanım | Dayanak |
|---|---|---|
| Coğrafi işaret | Belirgin niteliği, ünü veya diğer özellikleri bakımından köken yöresiyle özdeşleşmiş ürünü gösteren işaret | SMK m.34/1  |
| Menşe adı | Tüm veya esas özelliklerini yöreye özgü doğal ve beşerî unsurlardan alan; üretim, işleme ve diğer işlemlerin **tümü** yörede | m.34/1-a |
| Mahreç işareti | Yöreyle özdeşleşen; işlemlerden **en az biri** yörede | m.34/1-b |
| Yer adı içermeyen geleneksel ad | Şartları taşıyorsa menşe adı/mahreç işareti olabilir | m.34/2 |
| Geleneksel ürün adı | Menşe/mahreç dışında kalan; piyasada **en az 30 yıl** geleneksel kullanım + geleneksel yöntem/bileşim ya da hammadde | m.34/3 |

---

## Süre tablosu

| İşlem | Başlangıç | Süre | Dayanak |
|---|---|---|---|
| Reddedilen başvuruya itiraz (başvuran) | Kararın bildirimi | 2 ay | SMK m.40/1  |
| Yayımlanan başvuruya itiraz (üçüncü kişi, önceki hak sahibi) | Bülten'de yayım | 3 ay | SMK m.40/2 |
| Ücret | İtiraz süresi içinde ödenmeli ve bilgisi sunulmalı; yoksa itiraz yapılmamış sayılır (kamu kurumları muaf) | — | SMK m.40/3 |
| Tescilli işarette değişikliğe itiraz | Değişikliğin yayımı | 3 ay; kesinleşen değişiklik yayımdan itibaren en geç 1 yıl içinde uygulanır | SMK m.42/2  |

---

## Kontrol listesi

1. **Başvuru hakkı** (m.36): üretici grupları; ürün ya da coğrafi alanla ilgili kamu kurumları ve kamu kurumu niteliğindeki meslek kuruluşları; kamu yararına çalışan ya da üyelerinin ekonomik çıkarını korumaya yetkili dernek, vakıf ve kooperatifler; tek üretici varsa ispat şartıyla o üretici. 
2. **Ürün tanımı ve coğrafi sınır:** menşe mi mahreç mi (işlemlerin tümü mü biri mi yörede)?
3. **Tescil edilmeyecek adlar** (m.35): ürünün öz adı olmuş (jenerik) adlar; gerçek kaynak konusunda halkı yanıltabilecek bitki tür/çeşidi ya da hayvan ırkı adları; kamu düzeni/genel ahlaka aykırı adlar; kendi ülkesinde korunmayan adlar; tescilli ya da başvurusu yapılmış bir coğrafi işaretle eş sesli ve tüketiciyi yanıltabilecek adlar (m.35/1). Geleneksel ürün adı için ayrı liste m.35/2. 
4. **Denetim mekanizması** (m.37 başvuru şartları, m.49 kullanımın denetimi): denetim mercii belirlenmiş mi? `[doğrula]`
5. **Kullanım ve amblem** (m.46): amblem kullanım zorunluluğu SMK yayımından 1 yıl sonra yürürlüğe girdi (m.192/1-b).  Ayrıntı `[doğrula]`.
6. **Marka ilişkisi** (m.48): coğrafi işaretle çakışan marka başvurusu ve önceki iyiniyetli marka kullanımı (m.47) `[doğrula]`.
7. **Tecavüz** (m.53 coğrafi işaret, m.54 geleneksel ürün adı): taklit, "tipi/usulü" gibi ifadelerle kullanım, yanıltıcı sunum `[doğrula]`.
8. **Talepler:** SMK m.149; **manevi tazminat istenemez** (m.149/4) ve yoksun kalınan kazanç hesabına ilişkin m.151 uygulanmaz (m.151/6). 
9. **Sektörel mevzuat:** Türk Gıda Kodeksi tebliğleri coğrafi işaretli ürünün özelliklerine atıf yapıyor (ör. Krema ve Kaymak Tebliği 2025/18).  Tescil kaydı ile gıda mevzuatını birlikte oku.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Başvuru sahibi kim (birlik, oda, belediye, kooperatif)? | Başvuru hakkı |
| Üretimin hangi aşamaları yörede yapılıyor? | Menşe/mahreç |
| Ürün en az 30 yıldır bu adla mı biliniyor? Belge? | Geleneksel ürün adı |
| Aynı adla tescilli marka var mı? | m.47-48 |
| Denetimi kim yapacak? | m.37, m.49 |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6769"  law_type: "Kanun"  article_no: "33" | "34" | "35" | "36" | "37" | "38" | "40" | "42" | "44" | "46" | "47" | "48" | "49" | "50" | "53" | "54"
legal_search_official_gazette  query: "<ürün adı> coğrafi işaret"  sort_by: "date_desc"
legal_search_cases  mahkeme: "yargitay"  sorgu: "coğrafi işarete tecavüz <ürün>"
```

---

## Çıktı iskeleti

```markdown
## Coğrafi işaret — [ürün], [yöre]
| Konu | Durum | Dayanak | İşaret |
### Tür önerisi: menşe adı / mahreç işareti / geleneksel ürün adı — gerekçe
### Süreler ve itiraz yolu
### Açık sorular
```

---

## Sık hatalar

- 🟠 İşlemlerin bir kısmı yöre dışındayken menşe adı istemek (mahreç uygundur).
- 🟠 Coğrafi işaret tecavüzünde manevi tazminat istemek (m.149/4).
- 🟡 3 aylık yayıma itiraz süresini markadaki 2 ayla karıştırmak.

---

