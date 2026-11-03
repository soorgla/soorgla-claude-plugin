# Sayıştay denetim süreci, taslak rapor, sorgu ve savunma

## Ne zaman kullanılır
- Sayıştay denetim ekibi idarede; taslak denetim raporu geldi ve **üst yönetici cevabı** hazırlanacak (idare tarafı).
- Sorumluya **sorgu** tebliğ edildi; savunma süresi ve savunmanın esası soruluyor (sorumlu ya da avukatı).
- "Bu bulgu tazmine gider mi, yoksa yalnız raporda mı kalır?" ayrımı.

**Sınır:** savunma **metni** → `../../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`. Bu dosya süreyi, bulgunun türünü ve savunmanın esasını belirler. Hakediş bulguları → `../../hakedis/references/sayistay-denetim-riski.md`.

---

## 1. Süreç haritası

| Aşama | Ne olur | Dayanak |
|---|---|---|
| Denetim türü | Düzenlilik denetimi (hesap ve işlemlerin hukuka uygunluğu, mali rapor güvenilirliği, iç kontrol) ve performans denetimi (hedef ve göstergeler) | 6085 m.36 |
| Zaman | Sayıştay hesap/faaliyet dönemine bağlı olmaksızın yıl içinde, yıllar itibarıyla ya da sektör, program, proje, konu bazında denetleyebilir | 6085 m.6/4 |
| Bilgi-belge | Sorumlular istenen bilgi, kayıt ve belgeyi geciktirmeksizin vermek zorunda; vermeyenlerin aylıkları Sayıştay istemiyle yarım olarak ödenebilir | 6085 m.9 ; 5018 m.76 |
| Taslak denetim raporu | Rapor değerlendirme komisyonundan geçer, idareye gönderilir; **üst yönetici raporun alındığı tarihten itibaren 30 gün içinde** cevaplar; ekip cevabı dikkate alarak raporu düzenler | Sayıştay Denetim Yön. m.17/1, m.35/4 |
| Sorgu | Kamu zararına yol açan husus tespit edilince sorgu düzenlenir, adı-soyadı-unvanı yazılı her sorumluya tebliğ edilir; e-tebliğ esastır; sorguların tamamı üst yöneticiye ve muhasebe birimine bilgi için gönderilir | Denetim Yön. m.45/1, 2, 5 |
| Savunma | Tebliğden itibaren **30 gün** içinde cevap vermeyenin savunması **dikkate alınmaz** | 6085 m.48/1; Denetim Yön. m.45/1 |
| Yargılamaya esas rapor | Mali yıl sonu itibarıyla düzenlenir (m.6/4 konu denetimlerinde beklenmez); Başkanlık en geç 15 gün içinde daireye gönderir | 6085 m.48/1-2 |
| Hesap yargılaması | Başsavcılık yazılı düşüncesi, üye incelemesi, savcı hazır bulunur | 6085 m.49 |
| Hüküm | Hesap ve işlemlerin uygunluğuna ya da kamu zararının sorumlulardan **tazminine** hükmedilir; belgeler yargı/soruşturma nedeniyle yoksa hüküm dışı bırakılabilir | 6085 m.50 → `ilam-temyiz-ve-kanun-yollari.md` |

**İdarenin paralel yükümlülüğü:** Sayıştay sorgusu üst yöneticiye "bilgi amaçlı" gelir; üst yönetici gerek görürse sorguyu **ihbar kabul ederek** kendi kontrol/denetimini başlatır ve yönetmelik m.7/A'ya göre değerlendirir; kamu zararı kararı çıkarsa takip ve tahsil başlar, Sayıştay süreci ayrıca devam eder. → `kamu-zarari-tahsili-ve-idari-tespit.md`.

## 2. Süre tablosu

| İşlem | Başlangıç | Süre | Sonuç | Dayanak |
|---|---|---|---|---|
| Taslak rapora idare cevabı | Raporun alındığı tarih | 30 gün | Cevap rapora eklenir; geç cevap rapora yansımayabilir `[incele]` | Denetim Yön. m.17/1, 35/4 |
| Sorguya savunma | Sorgunun tebliği (e-tebliğde sistem kaydı) | 30 gün | Süre geçerse savunma dikkate alınmaz | 6085 m.48/1 |
| Yargılamaya esas raporun daireye gönderilmesi | Raporun Başkanlığa sunulması | 15 gün | Bilgi | 6085 m.48/2 |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, `legal_check_holiday`, `[doğrula]`. 7 günden az kaldıysa 🔴.

## 3. Sorgu geldi — değerlendirme kontrol listesi

| # | Kontrol | Not |
|---|---|---|
| 1 | Tebliğ tarihi ve yöntemi (e-tebliğ / elden / yazılı); süre tablosu | 🔴 süre |
| 2 | Sorguda adınız ve **sıfatınız** doğru mu (işlem tarihindeki görev)? | Sıfat hatası savunmanın ilk maddesi |
| 3 | Bulgu türü: tazmine giden sorgu mu, yalnız denetim raporu bulgusu mu, performans bulgusu mu? | Performans bulgusu sorumluluk doğurmaz (6085 m.7/6) |
| 4 | İşlemin dayanağı ve işlem tarihindeki metin | `kamu-zarari-unsurlari-ve-sorumluluk.md` §2 |
| 5 | Dört unsur testi (aykırılık, zarar, sorumlu, illiyet) | Aynı dosya |
| 6 | Yerindelik / takdir yetkisi itirazı uygun mu? | 6085 m.35/1-a; tek başına yetmez |
| 7 | Tutar hesabı, oluşma tarihi, iade/mahsup | Belge iste |
| 8 | İBK veya Temyiz Kurulu emsali | Lehe ve aleyhe birlikte göster |
| 9 | Tutar yükleniciden/ilgiliden geri alınabilir mi; idare değerlendirmesi başladı mı? | Sorgu idareye de gitti (Denetim Yön. m.45/5) |
| 10 | Ceza boyutu (gerçek dışı belge, 6085 m.78) | `[incele]`; ceza becerisine işaret |

**Taslak rapor (idare tarafı) kontrol listesi:** bulgu ↔ mevzuat atfı doğru mu; idarenin yetkili kurum görüşüne (HMB, ilgili bakanlık) dayandığı işlemlerde o görüş eklendi mi (rapor değerlendirme komisyonu bu uygunluğa bakar, Denetim Yön. m.35/3); düzeltici eylem ve tarih; bulgunun sorguya dönüşme riski; cevabın üst yönetici imzasıyla 30 gün içinde gitmesi.

## 4. Görüşme soruları (eski `data_schema` ve persona alanlarından)

| Alan | Soru |
|---|---|
| Belge | Sorgu / taslak rapor tarih ve sayısı? Tebliğ tarihi ve yöntemi? |
| Sorumlu | Adınız, işlem tarihindeki unvanınız ve sıfatınız? Başka sorumlular? |
| İdare türü | Belediye ve bağlı idare / üniversite / genel bütçeli / özel idare / SGK / düzenleyici kurum? |
| Konu | Harcırah / ihale / personel / sorumluluk-usul / vergi-harç-gelir / iş mevzuatı / bütçe-muhasebe / çeşitli? (sorgu cümlesine kat) |
| İddia | Denetçinin tespiti ve hesapladığı tutar? |
| Savunma | İşlem neden yapıldı, dayanağı ne, kim onayladı, iş/mal/hizmet alındı mı? |
| İade | Tutar iade/mahsup edildi mi? |

## 5. MCP adımları

```
legal_get_statute_article law_no: "6085" law_type: "Kanun" article_no: "48" | "36" | "35" | "7" | "9" | "50"
legal_list_statute_articles law_no: "15612" article_query: "cevap" | "sorgu" include_content: true
legal_list_statute_articles statute_id: 40508 article_no: "7/B" include_content: true
legal_search_cases mahkeme: "sayistay" sorgu: "<idare türü + konu + aykırılık + 'kamu zararı oluşmadığı' / 'tazmin'>" tarih_baslangic: "2022-01-01"
legal_get_case_document belge_id: "<seçilen>"
legal_search_admin_guidance kurum: "Sayıştay Genel Kurulu" sorgu: "<konu>"
```

Sayıştay karar künyesinde "Kamu İdaresi" (ör. "Belediyeler ve Bağlı İdareler", "Yüksek Öğretim Kurumları") ve "Konu" (ör. "Harcırah Mevzuatı ile İlgili Kararlar", "Personel Mevzuatı ile İlgili Kararlar") alanları var; bunları filtre olarak değil sorgu cümlesinde kullan.

## 6. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Kaynaklar: "Sayıştay kararları araçta 2024 sonuna kadar")
## Sorgu değerlendirmesi — [sorgu no/tarih] — [sorumlu, sıfat]
### Sonuç
[Savunma güçlü/zayıf; ana dayanak; son gün]
### Süre
| İşlem | Tebliğ | Süre | Son gün | Durum |
### Bulgu ve unsurlar
| Unsur | Durum | Savunma argümanı | Atıf |
### Emsal (lehe / aleyhe)
### Eksik belge
### Devir
Savunma metni → idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md (özet: …)
```

## 7. Sık hatalar
- 30 günü "hak düşürücü" sanıp süre geçtikten sonra hiç yazmamak; ya da tersine süreyi önemsiz saymak. Sonuç "savunma dikkate alınmaz"dır; yine de süre içinde vermek esastır 🔴.
- Taslak rapora idare cevabını süresinde vermemek ve bulgunun sorguya dönüşmesini beklemek.
- Performans bulgusunu tazmin riski gibi sunmak.
- Sorgu cevabında yalnız "yerindelik" ve "kamu yararı" demek.

## Eski YAML'dan düzeltilenler
- `audit_query_defense.yaml`: "30 gün (Hak düşürücü süre)" → 6085 m.48/1 sonucu "savunma dikkate alınmaz"dır.
- YAML `karar_sayistay` için `konu.keyword` / `idare.keyword` filtrelerini ve "relax_filters" yeniden deneme stratejisini kullanıyordu → araçta bu filtreler yok; künye alanları sorgu cümlesine yazılır.
- YAML taslak rapor aşamasını hiç anmıyordu → idare cevabı için 30 gün (Denetim Yön. m.17, m.35) eklendi.
