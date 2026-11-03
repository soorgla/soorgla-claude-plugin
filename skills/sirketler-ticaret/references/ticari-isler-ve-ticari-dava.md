# Ticari işler, tacir yükümlülükleri ve ticari dava

## Ne zaman kullanılır
- "Bu dava ticari dava mı, hangi mahkeme?", "asliye ticaret mi asliye hukuk mu", "arabuluculuk zorunlu mu", "ticari faiz uygulanır mı", "tacirler arasında ihtar nasıl yapılır", "basit yargılama mı".
- Bir uyuşmazlığın usul çerçevesini kurmak (esas sözleşme incelemesi → `../../sozlesme-incelemesi-tbk/SKILL.md`).

---

## 1. Ticari dava — görev

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| NİSPİ | Her iki tarafın da **ticari işletmesiyle ilgili** hukuk davası ticari davadır | TTK m.4/1 | |
| MUTLAK | Tacir olup olmadığına bakılmaksızın: TTK'da düzenlenen hususlar; TMK m.962-969; TBK m.202-203, 444 ve 447, 487-501, 515-519, 532-545, 547-554, 555-560, 561-580; fikri mülkiyet mevzuatı; borsa/sergi/antrepo; banka, kredi kuruluşu, finansal kurum ve ödünç para işleri | TTK m.4/1-a…f | Ticari işletmeyi ilgilendirmeyen havale, vedia ve fikir-sanat eseri hakları istisna |
| GÖREVLİ | Aksine hüküm yoksa değere bakılmaksızın **asliye ticaret mahkemesi**; asliye ticaretle diğer hukuk mahkemeleri arasındaki ilişki **görev** ilişkisidir | TTK m.5/1, 3 | |
| ATM-YOKSA | Asliye ticaret bulunmayan yerde ticari davaya asliye hukuk bakar; görev kuralına dayanılmaması görevsizlik gerektirmez | TTK m.5/4 | |
| BASİT-YARGILAMA | Miktar/değeri kanundaki sınırı aşmayan ticari davalarda basit yargılama; sınır HMK ek m.1'e göre her yıl artırılır | TTK m.4/2 (7445 ile) | **Tutarı metinden yazma** → `legal_get_social_parameters` ya da HMK ek m.1 ilanı `[doğrula]` |
| TÜKETİCİ | Taraflardan biri tüketiciyse 6502 m.73 ile tüketici mahkemesi `[incele]` | 6502 m.73 | `../../tuketici/SKILL.md` |

## 2. Dava şartı ticari arabuluculuk (TTK m.5/A)

| Kontrol | Kural | Dayanak |
|---|---|---|
| Kapsam | TTK m.4'te ve diğer kanunlarda belirtilen ticari davalardan, konusu bir miktar para olan **alacak, tazminat, itirazın iptali, menfi tespit ve istirdat** davaları | TTK m.5/A/1 |
| Sonuç | Dava açılmadan önce arabulucuya başvurmamak dava şartı yokluğu (usulden ret) | TTK m.5/A/1; 6325 m.18/A |
| Süre | Arabulucu görevlendirmeden itibaren **6 hafta**; zorunlu hâlde en fazla **2 hafta** uzatma | TTK m.5/A/2 |
| Kapsam dışı (örnek) | Genel kurul kararının iptali, haklı sebeple fesih, tespit davaları gibi para alacağı olmayan davalar `[incele]` | — |

 Kapsam genişlemesi: 7445 s. Kanun m.31 (RG 05.04.2023) — "alacak ve tazminat talepleri" yerine "alacak, tazminat, itirazın iptali, menfi tespit ve istirdat davalarında"; yürürlük **1/9/2023** (7445 m.43/1-a); menfi tespit ve istirdat davaları için 1/9/2023 ve sonrasında açılan davalara uygulanır (7445 geçici m.1). Başvuru metni → `../../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md`.

## 3. Tacirin yükümlülükleri

| Kontrol | Kural | Dayanak |
|---|---|---|
| Genel | Her borcu için iflasa tabi; ticaret unvanı seçmek, sicile tescil ettirmek, ticari defter tutmak | TTK m.18/1 |
| Basiret | Basiretli iş adamı gibi davranma — tacirin kusuru ve özen ölçütü | TTK m.18/2 |
| İhtar şekli | Tacirler arasında temerrüde düşürme, fesih, dönme ihbar/ihtarları **noter, taahhütlü mektup, telgraf ya da güvenli elektronik imzalı KEP** ile | TTK m.18/3 |
| Cezai şart | Tacir sıfatını haiz borçlu, TBK m.182/3 (ceza), m.121/2 ve m.525'teki aşırı ücret/ceza indirimini isteyemez | TTK m.22 |
| Faturaya itiraz | Faturayı alan 8 gün içinde itiraz etmezse içeriği kabul etmiş sayılır | TTK m.21/2 (teyit mektubu için aynı süre m.21/3) |
| Ticari iş karinesi | Bir tacirin borçları kural olarak ticari sayılır | TTK m.19 (gerçek kişi tacir işin ticari işletmesiyle ilgisiz olduğunu açıkça bildirirse adi; bir taraf için ticari sözleşme diğeri için de ticari, m.19/2) |

Ticari satışta ayıp ihbarı (2 gün / 8 gün), bayilik-acentelik → `../../sozlesme-incelemesi-tbk/SKILL.md`.

## 4. Ticari faiz

| Kalem | Kural | Dayanak |
|---|---|---|
| Kanuni faiz | Sözleşmede belirlenmemişse yıllık, TCMB'nin önceki yılın 31 Aralık'ındaki kısa vadeli kredi **reeskont oranının %80'i**; 30 Haziran'da 5 puan ya da daha fazla fark varsa ikinci yarıda 30 Haziran oranının %80'i | 3095 m.1 (7589 ile, RG 31.07.2026) |
| Ticari temerrüt (avans) faizi | TCMB kısa vadeli avans oranı m.1 oranından fazlaysa ticari işlerde sözleşme olmasa da avans oranı istenebilir; 30 Haziran'da 5 puan kuralı | 3095 m.2/2 |
| Akdi faiz | Temerrüt faizi sözleşmede yoksa ve akdi faiz daha yüksekse temerrüt faizi akdi faizden az olamaz | 3095 m.2/3 |
| Oranlar | `legal_get_legal_interest_rates` — `yasal_faiz` (3095 m.1 / 7589, reeskont oranına bağlı yeni yöntem) ve `ticari_temerut` (3095 m.2, avans) satırlarını `baslangic_tarihi` ile oku; dönem bölünmesinde her dönemi ayrı hesapla | — |

---

## Süreler

| Süre | Başlangıç | Dayanak |
|---|---|---|
| Ticari arabuluculuk: 6 hafta (+2) | Arabulucunun görevlendirilmesi | TTK m.5/A/2 |
| Faturaya itiraz: 8 gün | Faturanın alınması | TTK m.21/2 `[doğrula]` |
| Ticari temerrüt faizinde dönem değişimi | 1 Ocak / 1 Temmuz | 3095 m.1-2 |

## Görüşme soruları
1. Taraflar tacir mi; işlem ticari işletmeleriyle ilgili mi?
2. Uyuşmazlık TTK m.4/1'deki mutlak ticari davalardan mı (ör. acente, kıymetli evrak, haksız rekabet)?
3. İstem para mı; arabuluculuğa başvuruldu mu, son tutanak tarihi?
4. Taraflardan biri tüketici mi?
5. Faiz sözleşmede kararlaştırıldı mı; temerrüt tarihi; ihtar nasıl yapıldı?

## soorgla çağrıları

```
legal_get_statute_article law_no: "6102" article_no: "3" | "4" | "18" | "19" | "20" | "21" | "22"
legal_list_statute_articles law_no: "6102" article_no: "5" include_content: true # m.5 ve m.5/A
legal_get_statute_article law_no: "3095" article_no: "1" | "2" law_type: "Kanun"
legal_get_legal_interest_rates
legal_resolve_statute law_no: "6325" query: "Hukuk Uyuşmazlıklarında Arabuluculuk Kanunu" # numara çakışması
legal_search_cases mahkeme: "yargitay" daire: "11. Hukuk Dairesi" sorgu: "<ör. ticari davada dava şartı arabuluculuğa başvurulmadan açılan itirazın iptali davası>" tarih_baslangic: "<son 3 yıl>"
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Usul çerçevesi — [uyuşmazlık]

| Soru | Cevap | Dayanak |
|---|---|---|
| Ticari dava mı (nispi/mutlak)? | | |
| Görevli mahkeme | | |
| Dava şartı arabuluculuk? | | |
| Yargılama usulü (basit/yazılı) | | |
| Faiz türü ve başlangıcı | | |
| Yargıtay dairesi (kanun yolunda) | | |
```

## Sık hatalar
- Ticari alacak davasını arabuluculuğa gitmeden açmak.
- Asliye hukukla asliye ticaret arasındaki ilişkiyi "iş bölümü" sanmak (görev ilişkisi, m.5/3).
- Kanuni faizi 7589 öncesi sabit oranla hesaplamak.
- Tacirler arası fesih ihtarını e-postayla yapmak (m.18/3 şekli).
