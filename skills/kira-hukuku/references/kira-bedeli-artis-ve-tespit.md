# Kira bedeli: artış, geçici sınırlar ve kira tespiti

**Ne zaman kullanılır:** "kirayı ne kadar artırabilirim / ev sahibi ne kadar artırabilir", "yüzde 25 sınırı hâlâ var mı", "kira tespit davası açmak istiyorum", "beş yıl doldu, rayiç kira", "kira dövizle", "fazla ödediğim kirayı geri alabilir miyim" sorularında.

Temel ilke: kira bedelinin belirlenmesi, kiracı aleyhine değiştirilemeyen hükümlerin **tek istisnasıdır** (TBK m.343) — ama yenilenen dönemlerdeki artış m.344'teki sınıra bağlıdır.

**Hiçbir oran beceri metninden alınmaz.** TÜFE oranı, kesinlik sınırı ve harç her seferinde çekilir ya da kullanıcıdan istenir.

---

## Hangi kural hangi döneme uygulanır

| Dönem / durum | Uygulanacak sınır | Dayanak |
|---|---|---|
| Yenilenen kira dönemi, ilk beş yıl içinde, taraflar anlaşmış | Anlaşma geçerli, ancak **bir önceki kira yılının TÜFE on iki aylık ortalamalara göre değişim oranını** geçmemek koşuluyla | TBK m.344/1 |
| Aynı, taraflar anlaşmamış | Hâkim, aynı TÜFE sınırını geçmemek üzere kiralananın durumuna göre hakkaniyetle belirler | TBK m.344/2 |
| **Konut**, yenilenme tarihi **11.06.2022 - 01.07.2023** | Önceki kira yılı bedelinin **yüzde 25'i**; TÜFE ortalaması bunun altındaysa TÜFE. Fazlası geçersiz; m.344/2 hâkim kararlarına da uygulanır | TBK geçici m.1 (7409/4) |
| **Konut**, yenilenme tarihi **02.07.2023 - 01.07.2024** | Aynı yüzde 25 kuralı | TBK geçici m.2 (7456/23) |
| **Konut**, yenilenme tarihi **02.07.2024 ve sonrası** | Yüzde 25 sınırı **yok**; yeniden m.344/1-2 TÜFE sınırı | Geçici maddelerin süresi bitti; 30.10.2026 itibarıyla yeni geçici sınır bulunamadı `[doğrula — son 12 ayın RG taramasını tekrarla]` |
| Çatılı **işyeri** (2022-2024 dahil) | Yüzde 25 sınırı **hiç uygulanmadı**; m.344 TÜFE sınırı | Geçici m.1-2 metni "Konut kiraları bakımından" |
| **Beş yıldan uzun** süreli ya da **beş yıldan sonra yenilenen** sözleşmeler ve sonraki her beş yılın sonu | Anlaşma olsun olmasın hâkim; TÜFE on iki aylık ortalama değişimi, kiralananın durumu ve **emsal kira bedelleri** gözetilerek hakkaniyete uygun (rayiç) belirler. Sonraki yıllarda bu bedel m.344/1-2'ye göre değişir | TBK m.344/3 |
| Bedel **yabancı para** | Beş yıl geçmedikçe değiştirilemez (aşırı ifa güçlüğü m.138 saklı); beş yıldan sonra döviz değeri de gözetilerek m.344/3 | TBK m.344/4 |

Not: m.344'ün 2019'dan geçerli değişikliği (7161) ÜFE yerine TÜFE'yi getirdi; 2019 öncesi dönemlere ilişkin alacak hesaplarında eski metni `effective_date` ile çek. 2019 öncesi metin: yenilenen dönem anlaşmaları "bir önceki kira yılında **üretici fiyat endeksindeki artış oranını**" geçmemek koşuluyla geçerliydi (tespit ve 5 yıllık hakkaniyet fıkralarında da ÜFE). Not: `legal_get_statute_article` (`effective_date: "2018-06-01"`) bugünkü TÜFE metnini döndürüyor; eski metni karar alıntısından al.

---

## Hesap: TÜFE on iki aylık ortalama

m.344 oranı için `legal_calculate_cpi_12m_average` (`ay`) kullan: verilen ay dahil son 12 ayın endeks ortalamasını önceki 12 ayın ortalamasıyla kıyaslar ve `degisim_yuzdesi` döndürür. `legal_calculate_cpi_change` ise iki tarih arasındaki **noktadan noktaya** değişimdir; m.344 oranı değildir.

1. Kira yılının başlangıç ayını bul (ör. 15 Mart başlayan sözleşme → yenilenme Mart).
2. Uygulanacak oran: yenilenmeden önceki ay itibarıyla TÜİK'in ilan ettiği "TÜFE on iki aylık ortalamalara göre değişim (%)". Oranı `legal_calculate_cpi_12m_average` (`ay`: o ayın herhangi bir günü) ile çek; `bulunan_ay` 24 değilse ya da kullanıcı TÜİK bülteninden farklı bir değer veriyorsa `[doğrula — TÜİK on iki aylık ortalama, AAAA/AA]` yaz. Kanun metni yalnız "bir önceki kira yılında" TÜFE on iki aylık ortalama değişimini söyler; "yenilenmeden önceki ayın" verisinin esas alınması uygulamadaki okumadır ve bu turda bunu açıkça söyleyen 3. HD kararı bulunamadı. Bu yüzden ayı kullanıcıya açıkça söyle ve sonucu `[doğrula]` ile işaretle; uyuşmazlık varsa `legal_search_cases` (`daire: "3. Hukuk Dairesi"`, sorgu "kira artışı hangi ayın TÜFE on iki aylık ortalaması yenilenme tarihinden önceki ay") ile ara.
3. `legal_calculate_cpi_change` sonucunu m.344 oranı yerine kullanma; gösterirsen "noktadan noktaya değişim — m.344 oranı değildir" notuyla göster.
4. Formül: `yeni kira = önceki kira yılı aylık kira × (1 + oran)`. Sözleşmedeki oran daha düşükse sözleşme oranı uygulanır; daha yüksekse fazla kısım geçersiz.
5. Konutta 11.06.2022 - 01.07.2024 arası yenilenmelerde: `min(oran, %25)`.
6. Her sonuç `[doğrula]`.

**Fazla ödenen kira:** sınırı aşan kısım geçersiz olduğundan sebepsiz zenginleşme hükümlerine göre geri istenebilir `[incele]`. İhtirazi kayıtsız ödemenin etkisi ve uygulanacak zamanaşımı (TBK m.82 mi, kira ilişkisi nedeniyle başka süre mi) bu turda doğrulanamadı: çalışma anında `legal_search_cases` (`daire: "3. Hukuk Dairesi"`, sorgu "yasal sınırı aşan kira farkının iadesi ihtirazi kayıt zamanaşımı") ile ara ve tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: fazla kira iadesi zamanaşımı]` yaz ve süreyi kesin söyleme.

---

## Kira tespit davası — süre ve etki

| Durum | Kararın etkisi | Dayanak |
|---|---|---|
| Dava yeni dönemin başlangıcından **en az 30 gün önce** açıldı | Yeni dönem başından itibaren bağlar | TBK m.345/2 |
| Kiraya veren aynı 30 günlük süre içinde (yeni dönemden en geç 30 gün önce) kiracıya **artırım yapılacağını yazılı bildirdi** ve dava **izleyen yeni dönemin sonuna kadar** açıldı | Yeni dönem başından itibaren bağlar | TBK m.345/2 |
| Sözleşmede **artış hükmü var**, dava yeni dönemin sonuna kadar açıldı | Yeni dönem başından itibaren geçerli (ihtar gerekmez) | TBK m.345/3 |
| Bunların dışında | Dava her zaman açılabilir, karar bir sonraki dönemden itibaren etkili | TBK m.345/1 |

- Kira tespit davası **kiracı tarafından da** açılabilir (bedelin indirilmesi) `[incele]`.
- Dava şartı **arabuluculuk** var; arabuluculuk süresince hak düşürücü süre işlemez, ama m.345 "dava tarihi" ile ilgili etkiler için arabuluculuk başvurusunun hangi tarihte yapıldığına dikkat → `usul-arabuluculuk-ve-gorev.md`. m.345'teki 30 günlük sürede arabuluculuk başvuru tarihinin dava tarihi yerine geçip geçmediği bu turda doğrulanamadı; kullanıcıya kesin cevap verme. Çalışma anında `legal_search_cases` (`daire: "3. Hukuk Dairesi"`, sorgu "kira tespit davası otuz gün önce arabuluculuk başvurusu yeni dönem 345") ile ara ve tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: m.345 süresi ve arabuluculuk]` yaz. Güvenli yol: başvuruyu ve davayı süre içinde yapacak şekilde planla.

### Beş yıl sonrası rayiç tespit (m.344/3)
- Beş yıl kira **ilişkisinin başlangıcından** sayılır; yenilenen sözleşmede ilk sözleşme tarihi `[incele]`.
- Beş yıl dolmadan rayiç istenemez; o dönemde yalnız TÜFE sınırı.
- Hâkim emsal kiraları bilirkişiyle tespit eder, **eski kiracılık nedeniyle hakkaniyet indirimi** yapar; indirim oranı takdire bağlıdır, sabit oran yazma. `[incele]`
- Emsaller dava dönemiyle eş zamanlı olmalı; dönemden sonraki emsaller itiraz konusu. `[çekildi ama desteği doğrulayın]`

---

## Kontrol listesi

1. Konut mu, çatılı işyeri mi? (yüzde 25 sınırı yalnız konut)
2. Sözleşme başlangıcı, kira yılı başlangıcı, ilişkinin toplam süresi (beş yıl doldu mu?)
3. Sözleşmede artış maddesi var mı; oranı ne; TÜFE'yi aşıyor mu? 🟠
4. Artış talebi hangi yenilenme tarihine ait — geçici dönem içinde mi?
5. Döviz kaydı var mı? 32 sayılı Karar Tebliği m.8/2 istisnası mı? 🟠
6. Kiraya veren bildirimi/ihtarı yaptı mı, ne zaman? (m.345 etkisi)
7. Arabuluculuk başvurusu yapıldı mı?
8. Kiracı fazla ödeme yaptı mı; hangi dönemler?
9. Tespit davası mı, artış ihtarı mı, ödememe sonrası tahliye mi? (bedel uyuşmazlığı tahliyeye dönüşüyorsa `tahliye-sebepleri.md`)

## Görüşme soruları

1. Kiralanan konut mu işyeri mi? Başlangıç tarihi?
2. Şu an ödenen aylık kira ve son artış tarihi/oranı?
3. Sözleşmedeki artış maddesi (aynen)?
4. İstenen yeni bedel ve bu talebin size nasıl bildirildiği (tarih, yol)?
5. Bölgede benzer yerlerin kirası hakkında bilginiz (beş yıl dolduysa)?
6. Dava ya da arabuluculuk başladı mı?

## soorgla çağrıları

```
legal_get_statute_article law_no: "6098" article_no: "344" | "345" | "343" | "138"
legal_list_statute_articles law_no: "6098" article_kind: "gecici" include_content: true
legal_calculate_cpi_12m_average ay: <YYYY-AA-GG> # m.344 oranı (on iki aylık ortalamalara göre değişim)
legal_calculate_cpi_change baslangic: <YYYY-AA-GG> bitis: <YYYY-AA-GG> # noktadan noktaya; m.344 oranı değildir
legal_search_official_gazette query: "Türk Borçlar Kanunu kira" document_type: "kanun" date_from: <son 12 ay> sort_by: "date_desc" # yeni geçici sınır var mı
legal_search_cases mahkeme: "yargitay" daire: "3. Hukuk Dairesi" sorgu: "<ör. beş yıldan sonra kira tespiti hakkaniyet indirimi emsal>" tarih_baslangic: <son 3 yıl>
legal_search_cases mahkeme: "bam" sorgu: "<olay>" # tespit davaları çoğunlukla istinafta kesinleşir
legal_get_case_document <son 3 yıldan en az bir karar>
legal_get_exchange_rate # dövizli kira
legal_get_social_parameters # kesinlik sınırı
```

## Çıktı iskeleti

```markdown
## Kira bedeli değerlendirmesi: [kiraya veren/kiracı] — [tarih]
**Kiralanan:** [konut/işyeri] · **Başlangıç:** [tarih] · **Yenilenme:** [gg.aa.yyyy] · **İlişki süresi:** [x yıl]

### Uygulanacak kural
[m.344/1 | geçici m.1/2 yüzde 25 | m.344/3 rayiç | m.344/4 döviz] — neden

### Hesap
| Girdi | Değer | Kaynak |
|---|---|---|
| Önceki kira yılı aylık kira | | [kullanıcı verdi] |
| TÜFE 12 aylık ortalama değişim (AAAA/AA) | | [doğrula — TÜİK] |
| Sözleşme oranı | | [kullanıcı verdi] |
| Uygulanan oran | | |
| Yeni kira | | [doğrula] |

### Tespit davası seçeneği ve zamanlaması
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- 🔴 2024 Temmuz sonrası yenilenen konut kirasına yüzde 25 sınırı uygulamak ya da işyerine hiç uygulamak.
- 🔴 `legal_calculate_cpi_change` sonucunu m.344 oranı diye sunmak.
- 🟠 Beş yıl dolmadan rayiç kira istemek.
- 🟠 Yüzde 25 dönemi için tespit davasında hâkimin sınırı aşabileceğini sanmak (geçici maddeler m.344/2 kararlarına da uygulanır).
- 🟠 Dövizli kirada beş yıl dolmadan TL'ye çevirme ya da artış talep etmek (aşırı ifa güçlüğü ayrı tartışma).
- 🟡 Kira yılını takvim yılı sanmak.
