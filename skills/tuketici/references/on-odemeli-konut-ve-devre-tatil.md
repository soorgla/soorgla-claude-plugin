# Ön ödemeli konut, devre mülk ve devre tatil

## Ne zaman kullanılır
- **Ön ödemeli konut ("maketten satış"):** konut bedelinin teslimden önce peşin ya da taksitle ödendiği satış ve satış vaadi; teslim gecikti, proje durdu, tüketici sözleşmeden dönmek istiyor, satıcı kesinti/tazminat istiyor.
- **Devre mülk / devre tatil / uzun süreli tatil hizmeti:** otel ya da tatil köyü satış ofisinde imzalanan sözleşmelerden kurtulmak, ödenen bedelin iadesi, aidat ve bakım ücreti uyuşmazlığı.
- **İşletme tarafı:** müteahhit/satıcı ya da devre tatil şirketi sözleşme şablonunu, ön bilgilendirme formunu, satış sürecini denetletiyor; Bakanlık yaptırımı riski.
- Konuttaki yapı ayıbı → `ayipli-mal-ve-hizmet.md`; konut kredisi → `tuketici-kredisi-ve-bankacilik.md`; kat karşılığı inşaat sözleşmesi (arsa sahibi–yüklenici) → `../../sozlesme-incelemesi-tbk/references/eser-ve-insaat.md`.

**Dikkat — 7392 (24.3.2022):** ön ödemeli konutta teslim süresi ve devre tatil kuralları bu kanunla değişti. Sözleşme tarihi 2022 öncesiyse hangi metnin uygulanacağını 6502 geçici m.3'ten belirle `[incele]`. 

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Ön bilgilendirme formu: sözleşmeden **en az 1 gün önce** | — | 6502 m.40/2 (konut), m.50/4 (devre tatil)  | Verildiğinin ispatı satıcıda `[doğrula]` |
| Ön ödemeli konutta cayma: **14 gün**, gerekçesiz ve cezasız | Sözleşme | 6502 m.43/1  | Bağlı kredi cayma süresi sonunda yürürlüğe girer; bu sürede kredi masrafı istenemez (m.43/2). Satıcı iadeyi yaptıktan sonra tüketici **10 gün** içinde edinimlerini iade eder (m.43/3). |
| Ön ödemeli konutun teslimi: sözleşmedeki süre, **her hâlde sözleşmeden itibaren 48 ay** | Sözleşme tarihi | 6502 m.44 (7392/6)  | Eski YAML "36 ay" diyordu; 7392 ile değişti. Kat irtifakının tüketici adına tescili + zilyetlik devri teslim sayılır. |
| Ön ödemeli konutta gerekçesiz dönme: sözleşmeden itibaren **24 aya kadar**; satıcı yasal masraflar + kanundaki kademeli oranlarla sınırlı tazminat isteyebilir | Sözleşme tarihi | 6502 m.45/1 (KHK 684, 7074)  | Oranları madde metninden çek; satıcı yükümlülüğünü hiç ya da gereği gibi yerine getirmediyse hiçbir bedel isteyemez (m.45/2). |
| Devre tatil / uzun süreli tatil hizmetinde cayma: **14 gün**; süre dolmadan ödeme ya da borç senedi istenemez | Sözleşme (yönetmelik) | 6502 m.50/6 (7392 ek cümleler)  | Alınan bedel derhâl iade edilir; borç belgesi tüketici yönünden geçersiz; bağlı yeniden satım/değişim sözleşmeleri de kendiliğinden sona erer. |
| Devre tatil sözleşmesinin azami süresi: **10 yıl** (devre mülk hariç) | — | 6502 m.50/9 (7392)  | |
| Şahsi hak sağlayan devre tatilde dönem kullanmama bildirimi: tatilden **en az 90 gün önce** → o dönem bedel istenemez | Tatil başlangıcı | 6502 m.50/10 (7392)  | |
| Konut/tatil taşınmazında ayıp zamanaşımı **5 yıl** | Teslim | 6502 m.12/1 | → `ayipli-mal-ve-hizmet.md` |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, `[doğrula]`.

---

## Kontrol listesi — ön ödemeli konut

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ÖÖK-NİTELİK | Bedel teslimden önce (peşin ya da taksitle) ödeniyor, konut sonra devredilecek mi? | 6502 m.40/1  | Tamamlanmış konutun peşin satışı ön ödemeli değildir |
| ÖÖK-RUHSAT | Yapı ruhsatı alınmadan sözleşme yapılmış mı? (yasak; idari para cezası) | 6502 m.40/3, m.77/5  | |
| ÖÖK-ŞEKİL | Satış tapuda, satış vaadi **noterde düzenleme** şeklinde mi? Değilse satıcı geçersizliği tüketici aleyhine ileri süremez; geçerli sözleşme olmadan ödeme istenemez | 6502 m.41  | Tüketici geçersizliğe dayanıp iade isteyebilir `[incele]` |
| ÖÖK-TEMİNAT | Proje büyüklüğü eşiğini aşıyorsa bina tamamlama sigortası ya da Bakanlık teminatı var mı? Teminat haczedilemez | 6502 m.42  | Eşik yönetmelikte → çek |
| ÖÖK-TESLİM | 48 ay (2022 öncesi sözleşmede eski süre) aşıldı mı? Sözleşmedeki süre daha kısa mı? | 6502 m.44 | Gecikmede kira kaybı (müspet zarar / ifaya eklenen ceza) sözleşme ayaktayken istenir; tüketici sözleşmeden döner ya da bedel iadesini isterse 3. HD aynı sözleşmeye dayanarak geç teslim kira tazminatı istenemeyeceğini kabul etti. Talepler arasında seçim yapmadan önce bunu değerlendir `[incele]`  |
| ÖÖK-DÖNME | 24 ay içinde gerekçesiz dönme; satıcı kusurlu değilse kesinti kanundaki üst oranlarla sınırlı; satıcı kusurluysa kesinti yok | 6502 m.45 | Sözleşmedeki daha ağır cezai şart haksız şart `[incele]` |
| ÖÖK-BAĞLI-KREDİ | Konut bağlı krediyle alındıysa teslim edilmemede banka 1 yıl ve kredi tutarıyla sınırlı müteselsil sorumlu | 6502 m.35/2 | → kredi dosyası |
| ÖÖK-GÖREV | Taşınmazın aynına ilişkin (tapu iptal-tescil) uyuşmazlıkta dava şartı arabuluculuk **yok**; bedel/tazminat davasında var | 6502 m.73/A-1-d  | → `hakem-heyeti-ve-tuketici-davasi.md` |

## Kontrol listesi — devre mülk ve devre tatil

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| DT-NİTELİK | Devre tatil (1 yıldan uzun, birden fazla dönem konaklama), uzun süreli tatil hizmeti (indirim/menfaat hakkı), değişim ya da yeniden satış sözleşmesi mi? | 6502 m.50/1, 50/3-4 | |
| DT-AYNİ-HAK | Devre mülk (634 KMK sekizinci bölüm) dışında tüketiciyle **mülkiyet payına bağlı ayni hak** sağlayan devre tatil sözleşmesi kurulamaz; kooperatif/şirket ortaklığı, dernek/vakıf üyeliğiyle devre tatil verilemez; ayni hak sahibi olmayan satış yapamaz | 6502 m.50/2 (7392)  | Aykırılık **suçtur** (3-6 yıl hapis) → ceza boyutu için yalnız işaret, `../../ceza-ve-infaz-dilekce/SKILL.md`  |
| DT-ÖN-ÖDEME | Devre mülk dahil **ön ödemeli devre tatil sözleşmesi kurulamaz** (inşaatı bitmemiş tesiste ön satış) | 6502 m.50/8 (7392) | Aykırılık suç (m.77/4-b-2). 7392 yayımında ruhsatı alınmış tesisler için geçici m.3/2'deki beş yıllık geçiş istisnası `[incele]` |
| DT-ŞEKİL | Tarih tüketicinin el yazısıyla, imzalı, nüsha verilmiş mi (mesafeli satış hariç)? | 6502 m.50/5 | |
| DM-RESMİ-ŞEKİL | Devre mülk hakkı müşterek mülkiyet payına bağlı ayni hak olduğundan devri ve satış vaadi **resmî şekle** tabidir; satış ofisinde imzalanan adi yazılı sözleşme geçersizdir, taraflar verdiklerinin iadesini isteyebilir. **Ancak** adi sözleşmeye dayanılarak tapuda devir yapılmışsa geçersiz sözleşme geçerli hâle gelir | 634 KMK m.57 vd.; TMK m.706; TBK m.237; Tapu K. m.26; Noterlik K. m.89  | Eski YAML "adi yazılı sözleşme geçersiz (İBK)" diyordu; tapu devri istisnası eksikti, "İBK" künyesi doğrulanamadı |
| DM-CAYMA-TECRÜBE | Tapu devri yapılmış olsa bile, devre mülk fiilen teslim edilmemiş ve tüketici tecrübe/muayene imkânı bulmamışsa cayma hakkının askıda kaldığı kabul ediliyor | Devre Tatil Yönetmeliği; 3. HD aynı karar `[incele]`  | Sonuç kısmını okumadan "Yargıtay onadı" deme |
| DT-ORGANİK-BAĞ | Satış şirketi, tesis şirketi, işletmeci farklı unvanlarda mı? Organik bağ varsa müteselsil sorumluluk tartışılır | Yargıtay 3. HD aynı karar (BAM gerekçesi) `[incele]` | Davalıları geniş seç |
| DT-AİDAT | Kullanılmayan dönem için aidat; 90 gün bildirimi yapıldı mı? | 6502 m.50/10 | |
| DT-KREDİ | Bedel bağlı krediyle ödendiyse caymanın kredi verene de bildirilmesi | 6502 m.50/7 | |

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Sözleşme | Nerede, ne zaman imzalandı (satış ofisi, otel, noter, tapu)? Kaç sözleşme/protokol var? Sözleşmenin adı? |
| Şekil | Noter ya da tapu işlemi yapıldı mı? Tapuda pay devri var mı? |
| Ödeme | Ne kadar, kime, nasıl ödendi (kart, senet, kredi)? Dekontlar? |
| Ön bilgi | Ön bilgilendirme formu bir gün önce verildi mi? Cayma hakkı yazılı mıydı? |
| Teslim / kullanım | Konut teslim edildi mi, kat irtifakı tescil edildi mi? Devre mülkte tatil yapıldı mı, hangi tesiste? |
| Proje | Yapı ruhsatı tarihi, inşaat seviyesi, bina tamamlama sigortası? |
| Talep | İptal ve iade mi, teslim ve gecikme tazminatı mı, aidat itirazı mı? |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6502"  article_no: "35" | "40" | "41" | "42" | "43" | "44" | "45" | "50" | "77"
legal_list_statute_articles  law_no: "6502"  article_kind: "gecici"  include_content: true     # geçici m.3 geçiş
legal_resolve_statute  query: "Ön Ödemeli Konut Satışları Hakkında Yönetmelik"      # → 20238; "Satışı" yazılırsa boş döner
legal_resolve_statute  query: "Devre Tatil ve Uzun Süreli Tatil Hizmeti Sözleşmeleri Yönetmeliği"
legal_search_statute_semantic  mevzuat_no: "634"  sorgu: "devre mülk hakkı kurulması resmi şekil"
legal_search_cases  mahkeme: "yargitay"  sorgu: "devre mülk adi yazılı sözleşme geçersiz tapu devri cayma"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "yargitay"  sorgu: "ön ödemeli konut geç teslim kira kaybı tazminatı"  tarih_baslangic: "<son 3 yıl>"
```

---

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## [Ön ödemeli konut / Devre mülk / Devre tatil] — [tüketici/satıcı] — [tarih]

### Sonuç
[Geçerlilik; cayma/dönme hakkı; iade ve kesinti; teslim gecikmesi tazminatı; yol]

### Sözleşme haritası
| Belge | Tarih | Şekil (adi/noter/tapu) | Taraf şirket | Ödeme |

### Süre tablosu
| Süre | Başlangıç | Son gün | Dayanak | Durum |

### Riskler
[ceza boyutu (m.77/4-b), organik bağ, tapu devri istisnası, 2022 geçişi]

### Dayanaklar · Eksik bilgi · Şimdi ne yapalım?
```

---

## Sık hatalar
- Teslim süresini 36 ay sanmak (7392 sonrası 48 ay).
- Devre mülkte tapu devri yapılmışsa "adi sözleşme geçersiz" argümanını tek başına kullanmak.
- Satıcı kusurluyken m.45 kesintisini kabul etmek.
- Ceza boyutunu (m.77/4-b) atlamak; işletme tarafında bu bir 🔴'dir.
- Tapu iptal-tescil talebinde gereksiz arabuluculuk; bedel talebinde arabuluculuğu atlamak.

