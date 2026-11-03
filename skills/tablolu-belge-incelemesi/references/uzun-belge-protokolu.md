# Uzun belge protokolü (onlarca–yüzlerce sayfa)

## Ne zaman kullanılır
- Tek belge ≈50 sayfanın üstündeyse ya da ekleri, şartnameleri, protokolleriyle birlikte okunması gerekiyorsa: bayilik/distribütörlük sözleşmesi, yapım sözleşmesi + idari ve teknik şartname, ihale dokümanı, pay alım sözleşmesi + ekleri, kira portföyünün ana sözleşmesi, icra dosyası, bilirkişi raporu, uzun bir dava dosyası.
- Kullanıcı "baştan sona oku", "hiçbir maddeyi atlama", "eklerle çelişiyor mu bak" dediğinde.
- Diğer beceriler (sozlesme-incelemesi-tbk, kamu-ihale, hakedis, sirketler-ticaret, icra-iflas, hukuk-yargilamasi-dilekce) uzun belgeyle karşılaştığında bu dosyayı çağırır; **okuma** buradaki adımlarla, **değerlendirme** çağıran becerinin kontrol listesiyle yapılır.

Upstream `review` (başlıktan yönlendirme), `tabular-review` (birebir alıntı kuralı) ve commercial-legal `CLAUDE.md` "Large input" bölümünün uyarlamasıdır.

**Temel kural:** özetten bulgu üretilmez. Her bulgu bir madde numarasına ve o maddeden **birebir alıntıya** dayanır. Okunmamış bölüm hakkında hüküm kurulmaz; okunmadığı söylenir.

---

## 1. Harita (gövdeyi okumadan önce)

Belgenin iskeletini çıkar ve kullanıcıya göster:

| # | Bölüm / madde aralığı | Başlık | Sayfa | Tür (ana metin / ek / şartname / protokol / tablo) | Öncelik |
|---|---|---|---|---|---|

Şunları ayrıca işaretle:
- **Ekler, şartnameler, protokoller, zeyilnameler** — adı, tarihi, imzalı mı. Atıf yapılan ama belgede bulunmayan ek → "eksik ek" listesine.
- **Öncelik sırası maddesi** (belgeler arası çelişkide hangisi geçerli: ana sözleşme mi, özel şartname mi, ek protokol mü). Yoksa bunu 🟡 olarak not et: çelişkide yorum kurallarına kalınır `[incele]`.
- **Tanımlar maddesi** ve tanımların başka yerlerde (eklerde) yapılıp yapılmadığı.
- Numaralandırma bozuklukları (atlanan ya da tekrarlanan madde numarası, iki ayrı "Madde 12").
- **Değişiklik izleri**: "Değişik:", "ek protokol ile", tarihli zeyilname — hangi metnin güncel olduğu. Ek protokol geçmişi için → `../../sozlesme-incelemesi-tbk/references/degisiklik-gecmisi-ve-is-birimi-ozeti.md`.

Harita, **kapsam bildiriminin** (§5) temelidir: haritadaki her satır sonunda "okundu / okunmadı / kısmen" işareti alır.

## 2. Önce tanımlar

Tanımlar maddesini (ve eklerdeki tanımları) gövdeden önce oku ve bir **tanım sözlüğü** çıkar: terim → tanım (birebir) → madde no. Gövdeyi bu sözlükle oku:
- "Mücbir Sebep", "Önemli Olumsuz Değişiklik", "Kontrol", "Bağlı Şirket", "Kabul", "İş Günü" gibi tanımlar sonucu değiştirir; genel anlamıyla okuma.
- Tanım bir başka belgeye gönderme yapıyorsa (ör. "Şartnamede tanımlandığı şekilde") o belgeyi haritada işaretle.

## 3. Bölüm bölüm okuma ve YEŞİL / SARI / KIRMIZI

Haritadaki öncelik sırasıyla, **bölüm bölüm** oku. Her bölüm için:

| Madde | Konu | İşaret | Birebir alıntı | Not |
|---|---|---|---|---|
| m.14.2 | Kontrol değişikliği | KIRMIZI | "…" | Karşı tarafa fesih hakkı veriyor |

- **YEŞİL:** olağan, çağıran becerinin standardına uygun.
- **SARI:** müzakere edilebilir sapma, belirsiz ifade, eksik düzenleme.
- **KIRMIZI:** çağıran becerinin kırmızı çizgisi ya da açık risk (sınırsız sorumluluk, tek taraflı fesih, kontrol değişikliğinde fesih, öncelik sırası aleyhe).
- İşaretin ölçütü **çağıran alan becerisinin** kontrol listesi ve profil playbook'udur; bu protokol ölçüt koymaz. Bağımsız çalışıyorsa işareti "ilk okuma işareti" diye adlandır ve değerlendirmeyi devret.
- **Alıntı kuralı:** alıntı belgeden harfi harfine, bitişik metindir. Başlık + "olağan şablon" birleştirilmez, hafızadan yeniden kurulmaz, cümle ortasında "…" ile ayrı yerler birleştirilmez. Kesmek gerekiyorsa cümle sınırında kes ve `[kısaltıldı]` yaz. Alıntı çıkarılamıyorsa (OCR bozuk, sayfa yüklenmedi) bulgu "incelenmeli — alıntı yok: [neden]" olur.
- Bölüm okunduktan sonra haritadaki satıra "okundu" yaz. Bir bölüm bağlama sığmadığı için yarım kaldıysa "kısmen: s.40-52 okunmadı".

**Önce okunacaklar** (her şey okunamayacaksa): tanımlar, konu ve kapsam, bedel ve ödeme, süre ve yenileme, fesih ve sona erme, sorumluluk ve sınırı, cezai şart, tazmin, teminat, devir ve kontrol değişikliği, münhasırlık ve rekabet yasağı, gizlilik ve kişisel veri, fikri mülkiyet, uygulanacak hukuk, yetki/tahkim, bildirim adresleri, öncelik sırası.

## 4. Çapraz kontrol

Bütün bölümler okunduktan sonra ayrı bir geçiş:

1. **İç atıflar:** "Madde 9.3'te belirtilen süre" gerçekten 9.3'e mi gidiyor; atıf yapılan madde var mı; numaralandırma değişikliği atıfları kaydırmış mı?
2. **Ana sözleşme – ek çelişkisi:** aynı konu (süre, bedel, ceza, kabul ölçütü, fesih bildirim süresi) ana metinde ve ekte farklı mı düzenlenmiş? Öncelik sırası maddesi hangisini öne alıyor? Öncelik sırası yoksa `[incele]`.
3. **Tanım tutarlılığı:** tanımlanıp hiç kullanılmayan terim (çoğu zaman silinmiş bir maddenin izidir); büyük harfle kullanılıp tanımlanmamış terim; aynı terimin iki farklı tanımı.
4. **Süre ve tutar tutarlılığı:** rakam ve yazıyla yazılan tutar uyuşuyor mu; para birimi her yerde aynı mı; süreler takvim günü / iş günü olarak tutarlı mı.
5. **Taraf ve imza:** taraf unvanları her yerde aynı mı; imza sayfası ve yetki belgeleri haritada var mı.

Çapraz kontrol bulguları kendi tablosunda verilir: `Tür | Yer 1 (madde + alıntı) | Yer 2 (madde + alıntı) | Etki | İşaret`.

## 5. Kapsam bildirimi (sessiz atlama yok)

Çıktının gözden geçiren notundaki **Okunan** satırı (ORTAK-KURALLAR.md §8, §10) haritadan doldurulur:

> - **Okunan:** Ana sözleşme m.1-42 (s.1-58) tamamı; Ek-1 Teknik Şartname s.1-30 / 64 (s.31-64 okunmadı: ölçüm tabloları); Ek-3 atıf var, belgede yok.

Kural: "baştan sona okudum" yalnız haritadaki her satır "okundu" ise yazılır. Okunmayan bölüm hakkında sonuç cümlesi kurulmaz; gerekirse "s.31-64 okunmadan kabul ölçütü hakkında kesin bir şey söyleyemem" denir.

## 6. Çok büyük ya da çok belgeli işler

- **Öncelik sor:** "Belge [N] sayfa. Tamamını bu turda okuyamam. Seçenekler: (1) §3'teki öncelikli maddeler + tanımlar, (2) sizin seçtiğiniz bölümler, (3) bölüm bölüm, birkaç turda tamamı. Hangisi?" Onaysız başlama (ORTAK-KURALLAR.md §10 büyük çıktı kuralı).
- **Claude Code / Cowork:** bölüm başına bir **alt ajan** çalıştır. Her alt ajana: tanım sözlüğü (§2), kendi bölümünün sınırları, işaret ölçütü (çağıran becerinin kontrol listesi), alıntı kuralı (§3) ve dönüş biçimi (`madde | konu | işaret | birebir alıntı | not`) verilir. Alt ajanlar çapraz kontrol yapmaz; birleştirmeden sonra §4 ana ajan tarafından yapılır. Birleştirmede alt ajanların dönüşlerinden düşen bulgu varsa işaretle.
- **Belge sayısı çoksa** (aynı sorular birçok belgeye): tablolu incelemeye geç → `tablolu-inceleme-akisi.md`.

## 7. Taranmış PDF

- Metin katmanı yoksa (seçilemiyor, okuma boş ya da anlamsız karakter dönüyor) kullanıcıya **hemen** söyle: "Bu belge taranmış görüntü; metni güvenilir okuyamıyorum." Görüntüden okuma yapılabiliyorsa yap ama her alıntıya `[OCR — belgeyle karşılaştırın]` ekle; rakam, tarih ve madde numaraları en sık bozulan yerlerdir.
- Seçenekler: (1) kullanıcı metin katmanlı PDF ya da Word aslını verir, (2) ortamda OCR olanağı varsa (ör. `anthropic-skills:pdf` becerisi) Türkçe OCR ile metne çevrilir, (3) yalnız okunabilen sayfalar incelenir ve kapsam bildirimine "s.X-Y taranmış, okunamadı" yazılır.
- soorgla.com'un kendi sohbetinde belgeler sunucu tarafında Türkçe OCR'lı Tika ile metne çevrilir `[model bilgisi — doğrulayın]`; Claude Code'da bu hat yoktur.
- Taranmış belgede imza, kaşe, el yazısı ek ve paraf okunamaz: "imza ve paraflar görsel olarak doğrulanmalı" notu düş.

## 8. İstemciye göre sınırlar

- **ChatGPT ve benzeri ortamlar:** büyük dosyada model belgenin tamamını bağlama almaz, **arama ile parça parça** okur. Aranmayan madde hiç görülmeyebilir; tanımlar, ekler ve öncelik sırası maddesi en sık kaçırılanlardır. Bu ortamda: haritayı (§1) mutlaka çıkar, her bölümü ayrı ayrı iste ve oku, kapsam bildiriminde "dosya arama ile okundu; tam okuma doğrulanamadı" yaz. Kullanıcıya belgeyi bölümler hâlinde yapıştırmayı öner.
- **claude.ai web:** alt ajan yoktur; bölüm bölüm, birkaç turda ilerle; her turun sonunda haritayı güncel durumuyla yeniden ver (kullanıcı kopyalayıp sonraki tura yapıştırabilsin).
- **Claude Code / Cowork:** alt ajan kullanılabilir (§6); harita ve tanım sözlüğü istenirse çıktı klasörüne yazılır (yer → SKILL.md "Gizlilik ve dosyaların yeri").

## 9. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

> ⚠️ Gözden geçiren notu (ORTAK-KURALLAR.md §8) — **Okunan** satırı §5'e göre

## [Belge adı] — uzun belge incelemesi — [tarih]

### Sonuç
[Tek paragraf: en önemli 3 KIRMIZI, çapraz kontrolde bulunan çelişki, okunmayan bölüm varsa]

### Harita
[§1 tablosu, okundu/okunmadı sütunuyla]

### Tanım sözlüğü (önemli terimler)
| Terim | Tanım (birebir) | Madde |

### Bölüm bölüm bulgular
[§3 tablosu; KIRMIZI ve SARI önce]

### Çapraz kontrol
[§4 tablosu]

### Eksik ekler ve okunamayan sayfalar

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı — değerlendirme için ilgili alan becerisine devir ilk seçenek]
```
