# Yurt dışına aktarım (6698 m.9 — 7499 sonrası)

## Ne zaman kullanılır
- Veri, yedek ya da alt işleyen Türkiye dışında: yabancı bulut, e-posta, CRM, analitik/reklam aracı, yapay zekâ API'si, grup şirketi, yurt dışı müşteri hizmetleri.
- Standart sözleşme imzalanacak ya da Kuruma bildirilecek; bağlayıcı şirket kuralları (BCR) ya da taahhütname düşünülüyor.
- Eski bir "yurt dışına aktarım açık rızası" metni denetleniyor.

**Büyük değişiklik:** 7499 sayılı Kanunla m.9 tamamen değişti; yeni metin **1/6/2024**'te yürürlüğe girdi. Eski birinci fıkra (açık rızayı ana yol sayan düzen) yeni metinle birlikte **1/9/2024'e kadar** uygulandı; o tarihten sonra yalnız yeni sistem geçerli. Uygulama yönetmeliği RG 10.07.2024'te yayımlandı.

---

## Üç kademe (sırayla uygulanır)

1. **Yeterlilik kararı** — m.5/m.6 şartlarından biri + aktarılacak ülke, ülkedeki sektör ya da uluslararası kuruluş hakkında Kurulun yeterlilik kararı (RG'de yayımlanır, en geç 4 yılda bir değerlendirilir). Güncel yeterlilik kararı var mı: `legal_search_official_gazette` (`query: "yeterlilik kararı kişisel veri"`). Bu becerinin yazıldığı tarihte araçta bir yeterlilik kararı bulunamadı; sonuç yoksa "yeterlilik kararı bulunamadı" yaz; araçta bulunamaması kararın olmadığını kanıtlamaz, kullanıcıya Kurum sitesinden teyit etmesini söyle `[doğrula]`.
2. **Uygun güvenceler** (yeterlilik kararı yoksa) — m.5/m.6 şartı + ilgili kişinin aktarılan ülkede de haklarını kullanabilmesi ve etkili kanun yolu imkânı + şunlardan biri:
   - (a) kamu kurumları/uluslararası kuruluşlar arası, uluslararası sözleşme niteliğinde olmayan anlaşma + **Kurul izni**;
   - (b) teşebbüs grubu için **Kurulca onaylanan** bağlayıcı şirket kuralları;
   - (c) **Kurulca ilan edilen standart sözleşme** — izin gerekmez, **bildirim** gerekir;
   - (ç) yazılı taahhütname + **Kurul izni**.
3. **Arızi aktarım** (yeterlilik kararı yok ve uygun güvence sağlanamıyor) — yalnız **arızi** olmak kaydıyla: (a) riskler hakkında bilgilendirilmiş açık rıza; (b) ilgili kişiyle sözleşmenin ifası; (c) ilgili kişi yararına sözleşme; (ç) üstün kamu yararı; (d) hakkın tesisi; (e) hayati menfaat; (f) kamuya açık sicilden aktarım. (a)-(c) kamu kurumlarının kamu hukukuna tabi faaliyetlerine uygulanmaz.

**Sonraki aktarımlar** ve uluslararası kuruluşlara aktarımlarda da aynı güvenceler sağlanır. Veri **işleyenler** de m.9 kapsamındadır (madde metni "veri sorumluları ve veri işleyenler" diyor).

Düzenli, sürekli bir aktarım (ör. tüm müşteri verisinin yabancı bulutta tutulması) **arızi değildir**; açık rızaya dayandırılamaz. 🔴 Yönetmelik m.16/1: düzenli olmayan, tek ya da birkaç sefer gerçekleşen, süreklilik arz etmeyen ve olağan faaliyet akışı içinde bulunmayan aktarımlar arızidir; istisnai hâller yalnız yeterlilik kararı ve uygun güvence yokken uygulanır (m.6/2). `[incele]`

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Standart sözleşmenin Kuruma bildirimi: **5 iş günü** | İmzaların **tamamlanması** | 6698 m.9/5; Yönetmelik (40863) m.14/5 | Fiziken, KEP ya da Kurulun belirlediği yöntemle. Bildirimi kimin yapacağı sözleşmede yazmıyorsa **veri aktaran** bildirir. Ekler: imzalayanların yetki belgeleri + yabancı dildeki her belgenin **noter onaylı** çevirisi (m.14/6). |
| Değişiklik ya da sona erme bildirimi | Değişikliğin/sona ermenin gerçekleşmesi | 40863 m.14/8 | Taraflar ya da içerikteki bilgiler değişirse aynı usulle. Süre ifadesi m.14/5'e yollama — `[incele]` |
| Bildirim yapmamanın yaptırımı | — | 6698 m.18/1-(d) | İdari para cezası **veri sorumlusu ya da veri işleyen** hakkında uygulanır (m.18/2). Tutar → `kurul-sureci-ve-yaptirimlar.md`. |

`legal_calculate_deadline` "iş günü" hesabı yapmıyor; iş günlerini elle say, her günü `legal_check_holiday` ile kontrol et (yarım gün arifeleri dahil `[incele]`).

---

## Kontrol listesi

1. **Aktarım var mı?** Yurt dışından erişim (uzaktan destek), yabancı SaaS, yedek, alt işleyen dahil haritala. "Veri Türkiye'de" denmesi yeterli değil; yedek ve destek erişimini sor.
2. **Hukuki sebep** (m.5/m.6) aktarımın kendisi için ayrıca var mı? Yurt dışı dayanağı, işleme şartının yerine geçmez.
3. **Kademe 1** — yeterlilik kararı aradın mı? Sonucu yaz.
4. **Kademe 2** — standart sözleşme:
   - Kurulun ilan ettiği metin **hiç değiştirilmeden** kullanılıyor mu? Yabancı dilde de imzalanırsa Türkçe metin esastır.
   - Aktarımın tarafları ve rollerine (veri sorumlusu / veri işleyen) uygun standart sözleşme metni mi seçildi? Kurulca ilan edilen metinlerin sayısını ve adlarını ezberden yazma; ilan metni araçta yok — kullanıcıdan Kurum sitesindeki güncel metni iste, seçilen metnin taraf rolleriyle uyumunu kontrol et `[doğrula]`.
   - Aktarımın taraflarınca ya da yetkili temsilcilerce imzalandı mı? Yetki belgesi var mı?
   - Bildirim takvimi (5 iş günü) ve sorumlusu belirlendi mi? Metin değiştirilmiş ya da imza eksikse Kurul m.15 incelemesi başlatır.
5. **BCR / taahhütname** — Kurul onayı/izni alınmadan aktarım başlamış mı? 🔴
6. **Kademe 3** — arızi mi gerçekten? Açık rıza seçildiyse riskler (yeterli koruma olmaması, hak arama güçlüğü) açıkça anlatıldı mı? 🟠
7. **Aydınlatma metni** yurt dışı aktarımı, alıcı grubunu ve dayanağı yazıyor mu? → `aydinlatma-ve-acik-riza.md`.
8. **VERBİS** kaydında "yabancı ülkelere aktarımı öngörülen veriler" güncel mi?
9. **Sektörel yasaklar**: bankacılık, ödeme, sağlık, kamu, elektronik haberleşme gibi alanlarda verinin yurt içinde tutulması zorunluluğu olabilir; KVKK m.9/10 diğer kanunları saklı tutar. `[incele]`
10. **Kurulun durdurma yetkisi**: telafisi güç zarar ve açık hukuka aykırılıkta Kurul aktarımı durdurabilir.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Alıcı | Kim, hangi ülkede? Grup şirketi mi, tedarikçi mi? Rolü (sorumlu/işleyen)? |
| Veri | Hangi kategoriler, özel nitelikli var mı, kaç kişi? |
| Sıklık | Tek seferlik mi, sürekli mi? |
| Mevcut dayanak | Bugüne kadar neye dayanıldı? (açık rıza, taahhütname, hiçbir şey) 1/9/2024 öncesi düzen mi sürdürülüyor? |
| Standart sözleşme | İmzalandı mı, hangi tarihte imzalar tamamlandı, Kuruma bildirildi mi? |
| Sektör | Faaliyet alanı yurt içinde tutma yükümlülüğü getiriyor mu? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "9" | "16" | "18"
legal_list_statute_articles law_no: "6698" article_kind: "gecici" include_content: true # geçici m.3
legal_get_statute_article law_no: "40863" article_no: "<1-…; 14 standart sözleşme>" # Yurt Dışı Aktarım Yönetmeliği
legal_search_statute law_no: "7499" query: "yürürlük" # m.40
legal_search_official_gazette query: "yeterlilik kararı kişisel veri" sort_by: "date_desc"
legal_search_official_gazette query: "standart sözleşme kişisel verilerin yurt dışına aktarılması" sort_by: "date_desc"
legal_check_holiday tarih: "<her iş günü>"
```

---

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Yurt dışı aktarım değerlendirmesi — [faaliyet / alıcı]

### Sonuç
[Hangi kademe uygun; eksik ne; dur/düzelt]

### Aktarım haritası
| Veri | Aktaran | Alıcı (ülke, rol) | Sıklık | m.5/6 şartı | m.9 dayanağı | Durum |

### Süre tablosu
| İşlem | Başlangıç | Son gün (iş günü) | Dayanak | Sorumlu |

### Yapılacaklar
- [ ] Standart sözleşme (modül …) — değişiklik yapılmadan
- [ ] Kurum bildirimi — [tarih], ekler: yetki belgesi, noter onaylı çeviri
- [ ] Aydınlatma metni ve VERBİS güncellemesi
```

---

## Sık hatalar
- 1/9/2024'ten sonra hâlâ "yurt dışına aktarım açık rızası" ile sürekli aktarım yapmak.
- Standart sözleşme metnini "uyarlamak" (değişiklik yasak).
- 5 iş gününü takvim günü saymak ya da imzanın tamamlanması yerine sözleşme tarihinden başlatmak.
- Noter onaylı çeviriyi ve yetki belgesini eklememek.
- Bildirim yükümlüsünü belirlememek; veri işleyenin de m.18/1-(d) muhatabı olduğunu unutmak.
- Uzaktan erişim ve yedekleri aktarım saymamak.
- Aydınlatma metni ve VERBİS kaydını güncellememek.
