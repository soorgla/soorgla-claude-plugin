# Madde farkı: eski metin, yeni metin, yürürlük

## Ne zaman kullanılır
- 🔴 ve 🟠 kalemlerde (SKILL.md Adım 4).
- "7594 hangi maddeleri değiştirdi?", "6698 m.9'un eski hâli neydi?", "bu madde ne zaman değişti?"

Upstream `policy-diff` "Step 1: Extract the new requirements" adımının ilk yarısıdır (kuralın metni). İkinci yarısı (politikayla karşılaştırma) `etki-ve-bosluk.md`'dedir.

---

## 1. Önce bilinen sınır: sürüm araçları yakın tarihli değişikliği göstermez

soorgla'nın üç sürüm aracı (`legal_list_statute_versions`, `legal_compare_statute_versions`, `legal_get_statute_article_history`) 31.10.2026 itibarıyla **2014-2015 civarında duruyor**. Son haftaların, hatta son on yılın değişiklikleri bu araçlarda yoktur. "Bu hafta ne değişti" sorusunun cevabı bu araçlardan **çıkmaz**.

| Araç | Denenen | Sonuç |
|---|---|---|
| `legal_list_statute_versions` | 4857 (`law_type: "Kanun"`) | 17 sürüm; en yenisi 2014-09-10 (6552). Sonraki değişiklikler (ör. 7036 ile m.20) yok |
| `legal_list_statute_versions` | 6698 | 0 sürüm (7499 ile 2024 değişikliği yok) |
| `legal_list_statute_versions` | 5271 CMK | 16 sürüm; en yenisi 2014-06-18 (6545) |
| `legal_get_statute_article_history` | 5237 TCK m.31 | 9 kayıt; en yenisi 2015-03-27 (6638). Güncel metin ise 7593 sonrası metni gösteriyor |
| `legal_compare_statute_versions` | 4857, sürüm 1046 → 1045 | 38 "modified"; ilk beşinin `similarity_ratio` değeri 1 (yalnız boşluk/biçim farkı) |
| `legal_search_statute_versions` | 6698, "yurt dışına aktarılması açık rıza" | 0 sonuç |

Sonuçlar:
- Sürüm listesinin boş ya da eski dönmesi **"değişiklik yok" anlamına gelmez**.
- `legal_compare_statute_versions` `change_type: "modified"` dediğinde `similarity_ratio` 1 ise içerik değişmemiş, yalnız biçim değişmiştir: bunu değişiklik diye raporlama.
- Sürüm araçları yalnız **2014 öncesi olay tarihleri** için eski metin bulmaya yarar (ör. eski bir işçilik alacağında olay tarihindeki metin). Bu ihtiyaç alan becerisinindir.

## 2. Doğru yol: RG metni + güncel madde metni

Her değişen madde için:

1. **Değiştiren hükmü RG'den alıntıla.** `legal_get_official_gazette_document` ile değiştiren kanun / yönetmelik metnini oku; ilgili "MADDE N-" bloğunu aynen al. Değişiklik türünü sınıfla:
   - *İbare değişikliği:* "… yer alan '…' ibaresi '…' şeklinde değiştirilmiştir" → eski ve yeni ibare doğrudan RG metninde.
   - *Madde / fıkra değişikliği:* "… aşağıdaki şekilde değiştirilmiştir" → yeni metin RG'de; eski metin için 3. adım.
   - *Ekleme:* "… fıkradan sonra gelmek üzere aşağıdaki fıkra eklenmiştir" → eski metin yok, yeni hüküm RG'de.
   - *Yürürlükten kaldırma:* "… yürürlükten kaldırılmıştır" → yeni metin yok.
   
2. **Güncel metni çek.** `legal_get_statute_article` (`law_no`, `article_no`, `law_type: "Kanun"`). Metindeki "(Değişik: GG/AA/YYYY-KanunNo/madde md.)", "(Ek: …)", "(Mülga: …)" notunu oku:
   - Not değiştiren düzenlemeyi gösteriyorsa: araç güncel → yeni metin buradan alınabilir. 
   - Not yoksa ya da daha eski bir değişikliği gösteriyorsa: araç **henüz güncellenmemiş**. Yeni metni RG'den kur ve satıra `[soorgla madde metni RG değişikliğini henüz yansıtmıyor — RG metninden kuruldu]` yaz (Eski örnek: VUK kaydı 31.10.2026'da 7587'yi yansıtmıyordu; 01.11.2026 yeniden ayrıştırmasından sonra 213 m.107/A "(Değişik:24/6/2026-7587/9 md.)" notuyla güncel dönüyor.) 
   - Harfli ve mükerrer maddeler: `legal_get_statute_article` (`article_no: "107/A"` ya da `"mükerrer 257"`) ya da `legal_get_statute_article_by_id` ile çek; boş dönerse `legal_list_statute_articles` (`article_no` ana numara, `include_content: true`). 
   - Numara çakışması olan kanunlarda yanıttaki `statute.title`'ı takip listesindeki adla karşılaştır; aynı numaralı diğer kayıtlar `other_candidates`'ta gelir, doğrusunu `legal_get_statute_article_by_id` ile çek.
3. **Eski metni kur.**
   - İbare değişikliğinde: güncel metinde yeni ibareyi eskisiyle yer değiştir.
   - Tüm fıkra / madde değişikliğinde: önce `legal_get_statute_article` ile `effective_date` = değişiklikten bir gün öncesi dene; araç eski sürümü vermezse (çoğunlukla vermez) eski metni **önceki değiştiren düzenlemenin RG metninden** ya da kullanıcının elindeki metinden kur ve `[incele — eski metin yeniden kuruldu]` işaretle. Kuramıyorsan "eski metin soorgla'da yok" de; uydurma.
4. **Yürürlük ve geçiş** (`onem-suzgeci.md` §4).
5. **AYM iptali:** iptal edilen ibareyi karar metninin HÜKÜM bölümünden alıntıla; madde metninin araçtaki hâlinin iptali yansıtıp yansıtmadığını not et.

## 3. Çıktı biçimi (her değişen hüküm için)

```markdown
#### [Kanun adı] ([no]) m.[X]/[fıkra] — [değişiklik türü]
- **Değiştiren:** [düzenleme adı, no], m.[N] — RG [GG.AA.YYYY], sayı [—] [soorgla]
- **Yürürlük:** [tarih / kural] · **Geçiş:** [geçici madde özeti ya da "yok"]
- **Eski:** "[alıntı]" [kaynak etiketi]
- **Yeni:** "[alıntı]" [kaynak etiketi]
- **Ne değişti (tek cümle):** [ör. "bildirim süresi 30 günden 15 güne indi"]
- **Araç durumu:** [güncel metin değişikliği yansıtıyor | yansıtmıyor — RG'den kuruldu]
- **Önem:** 🔴/🟠 — [gerekçe]
```

Uzun maddede yalnız değişen fıkrayı alıntıla; tamamını değil. Tutar ve oran içeren fıkrada tutarı alıntıla ama "güncel değer için ilgili araç" notu düş; değişiklik metnindeki tutar ileride yeniden değerlemeyle değişebilir.

## 4. Kendi kendine kontrol

- Her "Yeni" alıntısı RG'den ya da `legal_get_statute_article`'dan mı? Değilse etiketi `[model bilgisi — doğrulayın]`.
- Eski ve yeni metin aynı fıkrayı mı gösteriyor (fıkra numaraları kaymış olabilir)?
- Yürürlük maddesi okundu mu? Okunmadıysa `` niteliğinde `[yürürlük maddesi okunmadı — doğrulayın]`.
- Karşı oy ya da gerekçe metni hüküm diye alıntılanmadı mı?

---

## Kaynak
- Upstream `policy-diff` Step 0-1 ("Verify rule status", "Extract the new requirements": "'Enhanced disclosure requirements' is not a requirement") ve CLAUDE.md "When disagreeing with a cited statute, quote the text or decline to characterize it".
