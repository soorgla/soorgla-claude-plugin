# Dosya brifingi (`brifing`)

Kaynak: upstream `litigation-legal/matter-briefing`. Türk usulüne uyarlandı (duruşma ve ara karar, kanun yolu, vekaletname yetkisi; "outside counsel call" yerine duruşma, müvekkil görüşmesi ve karşı taraf vekiliyle görüşme).

Amaç: avukata bir dosyanın güncel resmini duruşma salonuna yürüyene kadar okunacak uzunlukta vermek. Bu adım **yalnız okur, yazmaz.**

---

## 0. Kapı ve bağlam

- `_liste.yaml`'da kısa ad yoksa reddet: "`<kisa-ad>` dizinde yok; önce `ac`. Açılmamış (çıkar çatışması kaydı olmayan) bir dosya için brifing kurmam."
- Okunacaklar: dizindeki satır, `dosya.md`, `_gunluk.md`, gerekirse `notlar.md`. **Başka dosyanın klasörü okunmaz.**
- Kullanıcı amaç verdiyse (duruşma, müvekkil görüşmesi, karşı taraf vekiliyle telefon, ortaklar toplantısı) son bölümü ona göre kur.

## 1. Güncellik kontrolleri

- `son_guncelleme` 30 günden eskiyse en üstte ⚠️ BAYAT ve brifingden sonra `guncelle` öner.
- Açık süreleri yeniden kontrol et: son günü geçmiş ama `durum: acik` olan satır → 🔴 "kaçmış olabilir ya da kayıt güncellenmemiş". Kanun yolu süresi ise `legal_calculate_deadline` ile yeniden hesapla ve kartla karşılaştır; fark varsa ikisini de yaz (ORTAK-KURALLAR.md §7 araç-model çelişkisi).
- Çıkar çatışması `bekliyor`/`yapilmadi` ya da `atlama` doluysa ⚠️ ile ilk satırlarda.
- İsteğe bağlı: dosya kanun yolundaysa ve esas + karar no biliniyorsa `legal_get_case_by_number` ile kararın soorgla'da yayımlanmış metnini bağla; yalnız esas no varsa `legal_list_cases_by_number` + `daire` (esas no tek başına tekil değildir; aynı numara farklı dairelerde başka kararlara denk gelir).  İlk derece kararlarının çoğu soorgla'da yoktur; bulunamaması kararın olmadığı anlamına gelmez.

## 2. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu (ORTAK-KURALLAR.md §8) — Okunan: dosya.md, _gunluk.md (N giriş), [notlar.md] · Güncellik: son güncelleme AAAA-AA-GG [⚠️ BAYAT]

# [Müvekkil ya da kod] — brifing, [bugün]

**Durum:** [durum / aşama] · **Merci:** [mahkeme, E. no] · **Rolümüz:** [___]
**Risk:** [🔴/🟠/🟡/🟢] — [kayıtlı gerekçe] · **Gizlilik:** [sınıf]
**Çıkar çatışması:** [durum — ⚠️ bekliyor/atlandıysa]

## Tek paragraf
[Şu an ne yapıyoruz ve neden; dönüm olgusu kayıtlıysa adı.]

## Son gelişmeler
[Günlüğün son 3–5 girişi, en yenisi üstte. Günlük inceyse bunu söyle.]

## Sıradaki
| Ne | Tarih | Dayanak | Durum |
|---|---|---|---|
[açık süreler ve duruşmalar; 7 günden azsa 🔴]

**Bekleyen kararlar:** [açık sorular ve "Yapılacaklar"daki açık maddeler]

## Yetki ve ekip
[Vekaletnamede HMK m.74 özel yetkileri; sorumlu avukat; dosyaya katılması gereken ama katılmamış biri var mı (ör. bilirkişi raporu geldi, teknik danışman yok)]

## Yeniden değerlendirme soruları
*Soru, cevap değil.*
- Risk [__] hâlâ doğru mu, yoksa dosya hareket etti mi?
- Son gelişme yeni bir süre ya da delil koruma ihtiyacı doğurdu mu?
- Müvekkile en son ne zaman bilgi verildi? (`muvekkil-iletisimi`)

## [Amaca göre: duruşma / müvekkil görüşmesi / karşı vekille görüşme için]
[Sorulacaklar, alınacak kararlar, istenecek belgeler. Amaç verilmediyse bu bölüm yok.]
```

Ardından ORTAK-KURALLAR.md §8 karar ağacı (ör. 1. `guncelle` ile görüşmeden sonra kaydet · 2. `[alan becerisi]` ile şu soruyu derinleştir · 3. `muvekkil-iletisimi` ile bilgilendirme yazısı · 4. Bekle ve izle — [tarih] · 5. Başka bir şey).

## 3. Üslup

Bilineni söyle, bilinmeyeni işaretle. Yeni açılmış ve günlüğü ince bir dosyanın brifingi kısadır; şişirme. Tahmin yürütme, strateji önerme: brifing soruları ortaya koyar, cevabı avukat verir. Yeniden risk ataması gerekiyorsa bu `guncelle`'nin işidir.

## Bu adım ne yapmaz

- Sonuç tahmini yapmaz; risk alanı kayıtlı bir yargıdır.
- Dosyaya yazmaz.
- Başka dosyalarla kıyas yapmaz (dosyalar arası bağlam kuralı).
