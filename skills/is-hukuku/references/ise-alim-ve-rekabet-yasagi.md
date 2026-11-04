# İşe alım, rekabet yasağı ve cezai şart

İş sözleşmesi imzalanmadan **önce** işveren tarafına: hangi sözleşme türü, hangi şartlar, rekabet yasağı ve cezai şart geçerli olur mu? Hazır bir sözleşmenin madde madde denetimi için `is-sozlesmesi-denetimi.md`; bu dosya işe alım kararının kendisine odaklanır.

Upstream karşılığı: `employment-legal/skills/hiring-review` (Adım 3 kısıtlayıcı sözleşme hükümleri, Adım 5 yargı çevresi kontrolü). ABD'ye özgü parçalar (eyalet rekabet yasağı yasakları, ücret şeffaflığı yasaları) atıldı; yerine TBK m.444-447 ve 4857 kondu.

**Beceri kuralı söylemez, araçtan çeker:** süre üst sınırları, deneme süresi, bildirim süreleri her seferinde `legal_get_statute_article` ile okunur.

---

## Adım 1 — Olgular

1. Pozisyon, görev tanımı, kıdem düzeyi (yönetici mi, satış mı, Ar-Ge mi?).
2. Çalışma yeri; uzaktan ya da hibrit mi?
3. Planlanan sözleşme türü: belirsiz süreli, belirli süreli, kısmi süreli, çağrı üzerine, deneme süreli, pazarlamacılık?
4. Ücret yapısı: sabit, prim, komisyon, hisse/opsiyon?
5. Rekabet yasağı, gizlilik, cezai şart, eğitim gideri iadesi düşünülüyor mu?
6. Toplu iş sözleşmesi uygulanıyor mu?
7. Aday yabancı mı? (çalışma izni, Turkuaz Kart → `../../yabancilar-vatandaslik/references/calisma-izni-ve-turkuaz-kart.md`)

## Adım 2 — Sözleşme türü

| Konu | Kontrol | Çekilecek dayanak |
|---|---|---|
| Belirli süreli sözleşme | Objektif neden var mı (belirli süreli iş, belirli bir işin tamamlanması, ortaya çıkması gibi)? Zincirleme yenileme belirsiz süreliye dönüşür mü? | `4857/11` |
| Kısmi süreli / çağrı üzerine | Ayrımcılık yasağı ve çağrı üzerine çalışmanın asgari şartları | `4857/13`, `4857/14` |
| Uzaktan çalışma | Yazılı şekil ve sözleşmede bulunması gerekenler; uygulama yönetmeliği | `4857/14`, `legal_search_statute_semantic` "Uzaktan Çalışma Yönetmeliği" |
| Deneme süresi | Kanuni üst sınır ve TİS ile uzatma imkânı; deneme süresinde fesih ve haklar | `4857/15` (TBK karşılığının madde numarasını `legal_list_statute_articles` ile teyit et) |
| Yazılı şekil ve çalışma koşulları belgesi | Bir yıl ve daha uzun sözleşmede yazılılık; yazılı değilse belge verme süresi | `4857/8` |
| Pazarlamacılık | Ücretin yalnız komisyon olamaması, bölge münhasırlığı | `6098/448`-`6098/460` |

## Adım 3 — Rekabet yasağı (TBK m.444-447)

Sırayla kontrol et, her şartı madde metniyle karşılaştır:

1. **Ehliyet ve şekil:** işçinin fiil ehliyeti var mı, yasak yazılı olarak üstlenildi mi? (`6098/444` birinci fıkra)
2. **Haklı menfaat:** hizmet ilişkisi işçiye müşteri çevresi, üretim sırları ya da işverenin işleri hakkında bilgi edinme imkânı veriyor mu ve bu bilgilerin kullanılması işverene önemli zarar verebilecek nitelikte mi? Genel mesleki bilgi bu kapsamda değildir. (`6098/444` ikinci fıkra)
3. **Sınırlar:** yer, zaman ve iş türü bakımından işçinin ekonomik geleceğini hakkaniyete aykırı biçimde tehlikeye atıyor mu? Süre üst sınırını ve hâkimin sınırlama yetkisini `6098/445` ile çek.
4. **Cezai şart ve aynen ifa:** `6098/446`.
5. **Sona erme:** işverenin yasağın sürdürülmesinde gerçek yararı kalmadıysa ya da sözleşmeyi işçi haklı nedene dayanmadan işveren feshettiyse yasak sona erer. (`6098/447`)
6. **Karşılık (ivaz):** Kanunda şart değil; ama süre ve kapsamı geniş yasaklarda hâkimin değerlendirmesinde önemlidir `[incele]`.

**Görevli mahkeme ve daire:** rekabet yasağı uyuşmazlığının iş mahkemesinde mi ticaret mahkemesinde mi görüleceği ve temyiz dairesi tartışmalıdır (bölge adliye mahkemesi daireleri arasında iki yönde karar var; Yargıtay'da 9. HD dışında 11. HD ve 3. HD de bu davalara bakmış) → önce `legal_search_cases` (HGK ve ilgili daireler) ile güncel yaklaşımı çek, en az bir kararın tam metnini oku. 

## Adım 4 — Cezai şart

- **Genel kural:** hizmet sözleşmesine yalnız işçi aleyhine konulan cezai şart geçersizdir. (`6098/420` birinci fıkra) 
- **Rekabet yasağı istisnası:** rekabet yasağına bağlı olarak yalnız işçi aleyhine öngörülen cezai şart, işveren karşı edim üstlenmemiş olsa da geçerlidir.  Bu yaklaşımın güncelliğini her seferinde HGK ve 9. HD'den çek.
- **Eğitim gideri iadesi ve erken ayrılma cezası:** cezai şart mı, gerçek masrafın iadesi mi? Oransal azaltma var mı? İçtihadı çek. `[incele]`
- **Fahiş cezai şartın indirimi:** `6098/182`.

## Adım 5 — Diğer hükümler

- **Gizlilik ve sır saklama:** sözleşme sona erdikten sonra da devam eden borç (`6098/396`).
- **Fikri ürünler:** işçinin eserleri ve buluşları üzerindeki haklar → `5846`, `6769` (ilgili maddeleri `legal_search_statute_semantic` ile bul).
- **KVKK aydınlatması:** işe alım sürecinde aday verisi ve sözleşmede aydınlatma; açık rıza istisnai olmalıdır → ayrıntı `kvkk` becerisinde (`../../kvkk/references/aydinlatma-ve-acik-riza.md`).
- **Ücretten kesme cezası:** sınırları `4857/38`.
- **Fazla çalışmanın ücrete dahil edilmesi:** `4857/41` ve yıllık üst sınır; içtihadı çek.
- **Bildirim (KEP) onayı:** işçinin KEP ile bildirime yazılı kabulü işe alımda alınabilir (`4857/109`).

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4857"  article_no: "8" | "11" | "13" | "14" | "15" | "38" | "41" | "109"
legal_get_statute_article  law_no: "6098"  article_no: "396" | "420" | "444" | "445" | "446" | "447" | "182"
legal_list_statute_articles  (6098, hizmet sözleşmesi bölümü)       # madde numaralarını teyit et
legal_search_cases  mahkeme: "yargitay"  daire: "Hukuk Genel Kurulu"
    sorgu: "<ör. rekabet yasağı süresi ve yer bakımından hakkaniyete aykırılık hâkimin sınırlaması>"
legal_search_cases  mahkeme: "yargitay"  daire: "9. Hukuk Dairesi"
    sorgu: "<ör. eğitim gideri iadesi cezai şart işçi aleyhine geçersizlik>"
    tarih_baslangic: <son 3 yıl>
legal_case_facets  sorgu: "rekabet yasağı cezai şart işçi"   # hangi daireler bakıyor (gürültülü, yalnız ipucu)
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

## İşe alım incelemesi: [pozisyon] — [tarih]
**Sözleşme türü (önerilen):** … · **TİS:** var/yok · **Uzaktan:** evet/hayır

### Sonuç
[Bu şartlarla imzalanabilir / şu hükümler değişmeli / rekabet yasağı geçersiz kalma riski yüksek]

### Sözleşme türü
### Rekabet yasağı
| Şart | Durum | Not | Dayanak [soorgla] |
### Cezai şart ve eğitim gideri
### Diğer hükümler
### Önerilen madde metinleri (taslak)
### Eksik bilgi
```

---

## Kaynak
- Upstream: `claude-for-legal-upstream/employment-legal/skills/hiring-review/SKILL.md` (Apache-2.0), Türk hukukuna uyarlandı.
- Eski YAML: `analysis/service_work/service_contract.yaml` (rekabet yasağı korkuluğu). `analysis/employment_hr_docs/executive_contract_analysis.yaml` boş olduğundan yönetici sözleşmesi için içerik yoktu; bu dosya o boşluğu kısmen doldurur.
