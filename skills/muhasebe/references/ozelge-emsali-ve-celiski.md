# Özelge emsali bulma ve çelişen özelgeler

## Ne zaman
- "Bu konuda GİB'in özelgesi var mı?", "idare ne diyor?", "sirküler çıktı mı?".
- İki özelge birbirini tutmuyor; hangisine göre beyan edilecek?
- Müşteri için işlem öncesi kendi özelgesini almak gerekir mi?

Bu dosya meslek alanındaki **araştırma ve uygulama kararı** içindir. Özelgeye uyulmasına rağmen ceza kesilmiş, inceleme ya da dava varsa → `../../vergi/references/ozelge-ve-idari-gorus.md` ve `../../vergi/SKILL.md` (uyuşmazlık kapısı).

---

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Somut olay (işlem, taraflar, tutar türü, tarih) | Özelge olaya bağlıdır; teorik soruya özelge verilmez | Sor; olay yoksa yalnız tebliğ/sirküler araştır |
| İşlem tarihi / dönem | Hangi tebliğ ve görüşün yürürlükte olduğu (m.369/2) | Bugünü varsay, yaz |
| Vergi türü ve madde (KDV, GV, KV, damga…) | Arama sorgusu ve tebliğ bölümü | Sorudan çıkar, teyit et |
| Müşterinin kendisine verilmiş özelge var mı (sayı, tarih) | Koruma yalnız ona (m.369/1) | Sor |
| İnceleme başladı mı, olay yargıda mı? | Bu durumda özelge talebi kapsam dışı | Sor; evetse kapıyı aç |

---

## Araç çağrıları

```json
{ "sorgu": "<konu cümlesi>", "belge_tur": "ozelge", "tarih_baslangic": "2023-01-01", "adet": 10 }
{ "sorgu": "<konu>", "belge_tur": "ozelge", "kurum": "İstanbul Vergi Dairesi Başkanlığı" }
{ "sorgu": "<konu>", "belge_tur": "ozelge", "kurum": "Gelir İdaresi Başkanlığı" }
{ "sorgu": "<konu>", "kurum": "Gelir İdaresi Başkanlığı", "belge_tur": "sirkuler" }
```
(`legal_search_admin_guidance`)

```
legal_search_statute_semantic  sorgu: "<konu>"  mevzuat_tur: "teblig"          # genel tebliğ bölümü
legal_search_official_gazette  query: "<tebliğ adı>"  search_in: "title"  sort_by: "date_desc"   # sonraki tebliğ değişikliği
legal_search_cases  mahkeme: "danistay"  sorgu: "<konu>"  tarih_baslangic: "<son 5 yıl>"
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "369" | "413"
legal_get_statute_article  law_no: "14245"  article_no: "8"                    # özelge talebinin kapsamı
```

**Aracın davranışı (2026-11-02 sınandı):**
- `belge_tur: "ozelge"` + `tarih_baslangic` güncel özelgeleri getirir; sonuçta `kurum` özelgeyi veren **birimdir**: "İzmir Vergi Dairesi Başkanlığı", "İstanbul Vergi Dairesi Başkanlığı", "Samsun Defterdarlığı", "Bursa Defterdarlığı" gibi. "Gelir İdaresi Başkanlığı" adıyla gelenler ağırlıkla eski (merkez) özelgelerdir.
- `kurum` **tam eşleşme** ister; birim adını bilmiyorsan `kurum` verme, tarih filtresiyle ara.
- Her sonuçta `belge_no`, `belge_tarihi`, `kaynak.markdown` (gib.gov.tr bağlantısı) gelir; tabloya bunları aynen yaz.
- Sirkülerde `belge_tarihi` boş gelebilir; sirküler aramasında tarih filtresi verme.

🟠 "Bulunamadı" ≠ "özelge yok": kapsam tam değildir, sorguyu farklı sözcüklerle ve filtresiz tekrarla; yine yoksa "soorgla'da bulunamadı" yaz.

---

## Hukuki çerçeve

- **İzahat talebi:** mükellef, vergi durumu ve uygulaması bakımından müphem ve tereddütlü gördüğü hususlarda GİB'den ya da yetkili kıldığı makamdan yazıyla izahat isteyebilir; GİB özelgeyle cevaplar ya da aynı durumdakiler için sirküler yayımlar; aynı mahiyetteki taleplere taşra teşkilatı da özelge verebilir; özelgeler mahremiyet gözetilerek internette yayımlanır. [Vergi Usul Kanunu m. 413](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Koruma ve görüş değişikliği:** yetkili makamın **mükellefin kendisine** yazıyla yanlış izahat vermesi ya da içtihat değişmesi hâlinde **vergi cezası kesilmez ve gecikme faizi hesaplanmaz** (vergi aslı ayrı); genel tebliğ veya sirkülerle görüş değişikliği yayım tarihinden itibaren geçerlidir, geriye yürümez; yargıca iptal edilen tebliğ/sirkülerde bu kural uygulanmaz. [Vergi Usul Kanunu m. 369](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Özelge talebinin kapsamı dışı:** başkasının vergi durumu, yargıya intikal etmiş olay, inceleme konusu işlem, somut olaya dayanmayan teorik soru, işlem gerçekleştikten sonraki başvuru ve bazı yetki konuları. [Mükelleflerin İzahat Taleplerinin Cevaplandırılmasına Dair Yönetmelik m. 8](https://soorgla.com/mevzuat/14245-mukelleflerin-izahat-taleplerinin-cevaplandirilmasina-dair-yonetmelik/) [soorgla]

**Sonuç:** başka mükellefe verilmiş özelge müşteriyi korumaz ve idareyi bağlamaz; idarenin görüşünün göstergesidir. Mahkemeyi de bağlamaz. 🔴 Emsal özelgeye dayanılarak yapılan uygulama müşteri için m.369 korumasından yararlanmaz.

---

## Çelişen özelgeler — karşılaştırma

Aynı soruya farklı cevap varsa her biri için bir satır kur ve şu sırayla tart:

| Özelge (sayı, `kaynak.markdown`) | Veren birim | Tarih | Olay ne (fark var mı) | Dayandığı tebliğ bölümü | Sonraki tebliğ / sirküler değişikliği | Danıştay kararı | Ağırlık |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

1. **Olay aynı mı?** Çoğu "çelişki" olay farkıdır (taraf sıfatı, belge türü, süre). Fark varsa çelişki yok; uyanı seç.
2. **Tarih ve sonraki düzenleme:** özelgeden **sonra** genel tebliğ ya da sirküler değiştiyse eski özelge düşer (m.369/2). RG'de tebliğ değişikliğini `legal_search_official_gazette` ile, tebliğ metnini `legal_search_statute_semantic` ile kontrol et.
3. **Birim:** merkez (GİB komisyonu) özelgesi ile taşra özelgesi çelişiyorsa taşranın merkez görüşüne uygun olması gerekir (m.413/4); uymuyorsa `[incele]`.
4. **Danıştay:** konuyla ilgili Danıştay kararı varsa ikisini yan yana göster; karar idarenin görüşüne aykırıysa uygulama riski ve uyuşmazlık ihtimali yazılır (ORTAK-KURALLAR.md §7).
5. **Hâlâ çelişkiliyse:** ihtiyatlı uygulama + müşterinin **kendi özelgesini** alma önerisi.

---

## Müşterinin kendi özelgesini alması

- Ancak **işlem öncesinde**, somut olayla ve inceleme / yargı yokken (yönetmelik m.8).
- Dilekçe: `../../idari-ve-kurum-basvurulari/references/ozelge-talebi.md`. Olay anlatımı gerçek işlemle birebir olmalı; farklılık korumayı kaldırır.
- Olumsuz özelge riski: idarenin görüşü müşteri için yazılı hâle gelir; talep kararı meslek mensubu ve müşterinindir `[incele]`.
- Beklenen cevap süresi ve işlem takvimi `[doğrula]`.

---

## Kontrol listesi

- ✅ Her özelgenin sayısı, tarihi, veren birimi ve bağlantısı `kaynak.markdown`'dan aynen yazıldı.
- ✅ Özelgenin dayandığı tebliğ bölümü çekildi, sonraki değişiklik arandı.
- 🔴 Müşteriye verilmemiş özelgeyi "bizi korur" diye sunmadım.
- 🟠 Olay farkları satır satır karşılaştırıldı.
- 🟠 Danıştay araması yapıldı; sonuç yoksa "bulunamadı" yazıldı.
- 🟡 Sirküler ve iç genelge araması ayrıca yapıldı.
- [incele] Çelişkide hangi görüşle beyan edileceği; kendi özelge talebi.

## Sık hatalar

- 🔴 Başkasına verilmiş özelgeyi bağlayıcı saymak.
- 🔴 "Özelgeye uyduk, vergi de istenemez" demek (koruma ceza ve gecikme faizi içindir).
- 🟠 Eski özelgeyi sonraki tebliğ değişikliğine bakmadan uygulamak.
- 🟠 Araçta çıkmayan özelgeyi "yok" diye raporlamak; ya da özelge sayısı/içeriği uydurmak.
- 🟡 `kurum` filtresine kısaltma ya da eksik ad yazıp sıfır sonuç almak.

## Uyuşmazlığa dönüş işareti

Özelgeye uyulmasına rağmen tarhiyat/ceza, inceleme raporunda özelgeye aykırı tespit, idarenin özelgeden dönmesi üzerine ihbarname, Danıştay kararıyla çelişen idari uygulamaya karşı dava düşünülmesi → başlığı değiştir, `../../vergi/references/ozelge-ve-idari-gorus.md` ve `../../vergi/SKILL.md`'ye devret.

## Çıktı iskeleti

```markdown
[BAŞLIK]
> ⚠️ Gözden geçiren notu …
## İdari görüş araştırması — [konu] — [dönem]
### Sonuç (idarenin görüşü, ihtiyatlı uygulama önerisi)
### Bulunan belgeler
| Kaynak | Tür | Birim | Tarih | Ne diyor | Müşteriyi bağlar mı | Etiket |
### Çelişki analizi (varsa yukarıdaki tablo)
### Dayanak (VUK m.369, m.413; tebliğ bölümü)
### Öneri: kendi özelge talebi? → idari-ve-kurum-basvurulari/references/ozelge-talebi.md
```
