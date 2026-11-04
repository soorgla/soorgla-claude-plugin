# Amme alacağının tahsili (6183): ödeme emri, haciz, tecil, temsilci ve ortak sorumluluğu

## Ne zaman kullanılır
- "Ödeme emri geldi", "hesabıma haciz konuldu", "şirketin vergi borcu bana (müdür / ortak) çıkarıldı", "taksitlendirme (tecil) istiyorum", "borç zamanaşımına uğradı mı?"
- Vergi dairesi ya da belediye tahsil servisi (idare tarafı) ödeme emri / haciz işlemini kuruyor.

SGK prim alacakları da 6183'e göre tahsil edilir ama esas (prim borcu doğru mu) → `../../sosyal-guvenlik-sgk/SKILL.md`. İcra dairesindeki takiple kesişim (sıra cetveli, konkordato) → `../../icra-iflas/SKILL.md`.

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Dayanak |
|---|---|---|
| Ödeme emrinin içeriği | Borçlu **15 gün** içinde borcu ödemeye ya da mal bildiriminde bulunmaya çağrılır | 6183 m.55/1  |
| Ödeme emrine karşı dava | Tebliğden itibaren **15 gün** — vergi mahkemesinde | 6183 m.58/1  |
| Kısmi itiraz | Borcun hangi kısmına itiraz edildiği cihet ve miktarıyla açıkça gösterilmeli, aksi hâlde itiraz edilmemiş sayılır | 6183 m.58/2  |
| Ret sonrası mal bildirimi | Borcun tamamına itirazın reddi kararının tebliğinden itibaren **15 gün** içinde mal bildirimi | 6183 m.58 son fıkralar  |
| Tahsil zamanaşımı | Vadenin rastladığı takvim yılını izleyen yıl başından itibaren **5 yıl**; zamanaşımından sonra rızaen ödeme kabul edilir | 6183 m.102  |
| Tecil | Borçlu yazılı ister, teminat gösterir; **72 ayı** geçmemek üzere faizle; belirli tutara kadar teminat aranmaz (tutar kanunda yazılı, Cumhurbaşkanı değiştirebilir) | 6183 m.48  |
| Tecil reddi | Reddin tebliğinden itibaren idarenin verebileceği **30 güne kadar** ödeme süresi içinde ödenirse ödeme tarihine kadar faizle tecil edilmiş sayılır | 6183 m.48/3  |

`legal_calculate_deadline` `tax_payment_order_objection` (6183 m.58, 15 gün) kodunu tanır; sonucu elle sayımla sağla. 

**Metin–uygulama farkı:** 6183 m.58 metni itirazın "vergi itiraz komisyonu" nezdinde yapılacağını söylüyor; bu komisyonlar vergi mahkemelerinin kurulmasıyla kalktı ve itiraz bugün **vergi mahkemesinde dava** olarak yapılıyor. Metni olduğu gibi aktarıp kullanıcıyı olmayan komisyona yönlendirme. Dayanak: 2576 m.6/b — vergi mahkemeleri, vergi/resim/harç ve benzeri mali yükümler konusunda "6183 sayılı … Kanunun uygulanmasına ilişkin davaları" çözer.  m.58'in bir fıkrası AYM'nin 21.04.2022 tarihli E.2021/119 K.2022/48 kararıyla iptal edildi; iptal edilen fıkrayı uygulama. 

---

## Kontrol listesi — ödeme emri

1. **Ödeme emrine karşı ileri sürülebilecekler sınırlıdır:** borcun olmadığı, kısmen ödendiği, zamanaşımına uğradığı (m.58/1) — ve uygulamada asıl alacağın **kesinleşmediği** (ihbarnamenin usulüne uygun tebliğ edilmediği). Tarhiyatın esasına ödeme emri davasında girilmez `[incele]`. 
2. **Asıl alacak kesinleşmiş mi?** İhbarname tebliğ edildi mi, dava süresi geçti mi, dava açıldıysa sonuçlandı mı? Kesinleşmemiş alacak için ödeme emri 🔴 iptal sebebi.
3. **Tahsil zamanaşımı** (m.102): vadenin rastladığı yılı izleyen yıl başından 5 yıl. Kesen sebepler m.103'te sayılıdır: ödeme, haciz, cebren tahsilat, ödeme emri tebliği, mal bildirimi, teminata bağlama, yargı merciinin bozma ya da icranın tehiri kararı, özel kanunla ödeme başvurusu / ödeme planı; kesilmeyi izleyen yıl başından yeniden işler. Borçlunun yurt dışında olması, hileli iflas, tereke tasfiyesi süresince işlemez (m.104). 
4. **Muhatap doğru mu?** Şirket borcu için temsilciye ödeme emri → aşağıdaki "Sorumluluk" bölümü.
5. **Tahsil durmaz**: ödeme emrine karşı dava tahsili kendiliğinden durdurmaz; **YD iste** (2577 m.27/4). → `vergi-davasi.md`
6. **Mal bildirimi** süresi ve yükümlülüğü: bildirmeme ve gerçeğe aykırı bildirim yaptırımları ödeme emrinde yazılı olmalı (m.55/2). 

## Sorumluluk — kanuni temsilci ve ortak

| Kim | Sorumluluk | Dayanak |
|---|---|---|
| Kanuni temsilci (tüzel kişi, küçük, kısıtlı, tüzel kişiliği olmayan teşekkül) — **vergi ödevleri** yönünden | Ödevleri yerine getirmemeleri yüzünden mükellefin varlığından alınamayan vergi ve bağlı alacaklar temsilcinin varlığından alınır; asıl mükellefe rücu edebilir | VUK m.10/2-3  |
| Tasfiye edilerek sicilden silinmiş şirket | Tasfiye öncesi dönem tarhiyatı ve cezası kanuni temsilcilerden, tasfiye dönemi için tasfiye memurlarından, **müteselsilen** herhangi biri adına; limited ortakları sermaye payları oranında; tasfiye memuru sorumluluğu dağıtılan tutarla sınırlı | VUK m.10/5 (7103/9)  |
| Kanuni temsilci — **tahsil** yönünden | Tüzel kişinin varlığından tamamen veya kısmen tahsil edilemeyen ya da edilemeyeceği anlaşılan amme alacakları temsilcinin şahsi varlığından; tasfiye, tasfiyeden önceki sorumluluğu kaldırmaz; rücu hakkı var | 6183 mükerrer m.35  |
| Limited şirket ortağı | Şirketten tahsil edilemeyen ya da edilemeyeceği anlaşılan amme alacağından **sermaye payı oranında** doğrudan sorumlu; payı devreden ve devralan devir öncesi borçtan müteselsilen | 6183 m.35  |

Kontrol: (1) önce şirket hakkında takip yapılıp **tahsil edilemezlik / edilemeyeceği** belgelenmiş mi (mal varlığı araştırması)? (2) temsilcinin **görev dönemi** ile borcun doğduğu ve ödenmesi gereken dönem örtüşüyor mu? (3) ortaklık payı ve devir tarihleri sicilden teyit edildi mi? (4) "kusur" ve ödevin ihmali gerekçede var mı (VUK m.10)? Her biri iptal sebebi olabilir `[incele]`. Danıştay 13. D.: m.35 sorumluluğu kusursuz sorumluluktur; ancak önce asıl borçluya başvurulmalı ve alacağın ondan tahsil edilemediği/edilemeyeceği anlaşılmalı — asıl borçlu hakkında ödeme emriyle takip yapılmadan temsilciye gidilemez; ayrıca alacak tahsil edilebilir aşamaya gelmeden görevden ayrılan temsilci sorumlu değildir (E.2022/2436 K.2024/4899, 20.11.2024, bozma, oyçokluğu — karşı oy: ceza tebliğinden sonra ödenebilir dönemde görevde olan temsilci sorumlu). Karar idari para cezası kaynaklı alacağa ilişkin; vergi alacağında VUK m.10 ile birlikte uygula ve vergi dairesinden güncel karar ara `[incele]`. 

## Gecikme zammı ve tecil faizi

- Vadesinde ödenmeyen amme alacağına aylık gecikme zammı uygulanır; ay kesirleri günlük hesaplanır; vergi ziyaı cezalarında da uygulanır, diğer ceza mahiyetindeki alacaklarda uygulanmaz. Oranı Cumhurbaşkanı değiştirebilir.  **Oranı metne yazma** — araç döndürmüyor; RG'deki son Cumhurbaşkanı kararından çek `[doğrula]`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Ödeme emrinin tebliğ tarihi ve şekli? | 15 gün |
| Ödeme emrindeki borç hangi ihbarnameye / beyannameye dayanıyor; o ihbarname size tebliğ edildi mi? | Kesinleşme |
| Borç hangi yıla ait, vadesi ne zamandı? | Tahsil zamanaşımı |
| (Temsilci / ortak ise) Görev / ortaklık dönemi; pay devri tarihi; şirket hakkında takip yapıldı mı? | Sorumluluk şartları |
| Haciz uygulandı mı, nereye? | YD ihtiyacı |
| Ödeme gücü, teminat imkânı? | Tecil |

---

## İdare tarafı (tahsil dairesi)

- Ödeme emri düzenlemeden önce: asıl alacak kesinleşti mi, tebliğ belgesi dosyada mı, zamanaşımı hesaplandı mı?
- Temsilci / ortağa gitmeden önce: şirket nezdinde mal varlığı araştırması ve tahsil edilemezlik tespiti yazılı olsun; temsilcinin görev süresiyle borç dönemini eşleştir.
- Ödeme emrinde m.55/2'deki zorunlu ihtarlar eksiksiz yer alsın.
- Tecil taleplerinde teminat eşiği ve taksit koşullarını o tarihteki Cumhurbaşkanı kararı ve tebliğden al.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6183"  law_type: "Kanun"  article_no: "48" | "51" | "55" | "58" | "102" | "103" | "104"
legal_list_statute_articles  law_no: "6183"  law_type: "Kanun"  article_query: "kanuni temsilci"  include_content: true   # m.35 ve mükerrer 35
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "10"
legal_search_cases  mahkeme: "danistay"  sorgu: "<ör. kanuni temsilci adına ödeme emri şirketten tahsil imkânı araştırılmadan>"  tarih_baslangic: "<son 3 yıl>"
legal_search_official_gazette  query: "gecikme zammı oranı"  sort_by: "date_desc"
```

---

## Çıktı iskeleti

```markdown
## Ödeme emri değerlendirmesi — [tebliğ tarihi / tutar]
| İşlem | Son gün | Not |
| Dava (vergi mahkemesi) | +15 gün | YD istenmeli |
| Ödeme / mal bildirimi | +15 gün | |
### Asıl alacak kesinleşmiş mi?
### Zamanaşımı
### (Temsilci/ortak) sorumluluk şartları
### Öneri: dava / ödeme / tecil
```

---

## Sık hatalar

- 🔴 Ödeme emrine 30 günlük dava süresi uygulamak.
- 🔴 Ödeme emri davasında tarhiyatın esasını tartışıp kesinleşme ve tebliğ iddiasını atlamak.
- 🟠 m.58 metnindeki "itiraz komisyonu"na yönlendirmek.
- 🟠 Limited ortağı borcun tamamından sorumlu tutmak (pay oranı).
- 🟡 Gecikme zammı oranını kanun metnindeki dipnotlu orandan okumak.

---

