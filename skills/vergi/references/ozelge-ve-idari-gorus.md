# Özelge araştırması ve idari görüşün ağırlığı

## Ne zaman kullanılır
- "Bu konuda GİB'in özelgesi var mı?", "başka bir şirkete verilen özelge bizi korur mu?", "özelgeye uydum ama ceza kesildi".
- Planlanan işlem için özelge istemenin gerekip gerekmediği.
- Genel tebliğ ya da sirkülerle idarenin görüş değiştirmesinin etkisi.

**Özelge talep dilekçesi** → `../../idari-ve-kurum-basvurulari/references/ozelge-talebi.md`. Bu dosya araştırma ve değerlendirme içindir.

---

## Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| İzahat talebi | Mükellef, vergi durumu ve uygulaması bakımından **müphem ve tereddütlü** gördüğü hususlarda GİB'den ya da yetkili kıldığı makamdan yazıyla izahat isteyebilir | VUK m.413/1  |
| Özelge ve sirküler | GİB izahatı özelgeyle cevaplar ya da aynı durumdakiler için **sirküler** yayımlar; ikisi de Başkanlık bünyesindeki komisyonda oluşturulur; aynı mahiyette taleplere taşra teşkilatı da özelge verebilir | VUK m.413/2-4  |
| Yayım | Sirküler ve vergi mahremiyeti gözetilerek özelgeler internette yayımlanır | VUK m.413/5  |
| Koruyucu etki | Yetkili makamın mükellefin **kendisine** yazıyla yanlış izahat vermesi ya da içtihat değişmesi hâlinde **vergi cezası kesilmez ve gecikme faizi hesaplanmaz**; vergi aslı tarh edilebilir | VUK m.369/1  |
| Görüş değişikliği | Genel tebliğ ya da sirkülerle yapılan görüş değişikliği yayım tarihinden itibaren geçerli, geriye yürümez (yargıca iptal edilenler hariç) | VUK m.369/2  |
| Rapor değerlendirme | Rapor değerlendirme komisyonları bir özelgenin m.369 kapsamında olduğu kanaatine varırsa özel komisyon karar verir; bu karar komisyonu ve incelemeciyi bağlar | VUK m.140 ek fıkra  |

**Başkasına verilen özelge:** m.369'un koruması mükellefin **kendisine** verilen yazılı izahat içindir. Başka mükellefe verilmiş yayımlanmış özelge idareyi bağlamaz; ancak idarenin yerleşik görüşünü gösterir, uzlaşmada "yargı kararları ile idarenin görüş farklılığı" ve kanuna nüfuz edememe gerekçesi olarak kullanılabilir (VUK ek m.1) `[incele]`. Eski YAML'daki "hukuki güven ilkesi gereği emsal teşkil edebilir" ifadesi bu sınırla birlikte kullanılmalı.

**Hiyerarşi:** özelge kanuna, Cumhurbaşkanı kararına ve yargı içtihadına aykırıysa yargı denetiminde ağırlığı düşer; özelge mahkemeyi bağlamaz. İnceleme elemanları ise genel tebliğ ve sirkülere aykırı rapor düzenleyemez (VUK m.140/5) — özelge bu sayımda yok `[incele]`. 

---

## Araştırma adımları — soorgla kapsamı

1. **`legal_search_admin_guidance` GİB belgelerini içeriyor (2026-10-31 canlıya alındı, ~19.500 belge).** Özelge → `belge_tur: "ozelge"` + `tarih_baslangic`/`tarih_bitis`; `kurum` özelgeyi veren birimin tam adı ("Gelir İdaresi Başkanlığı" ağırlıkla 2011-2018; sonrası "<il> Vergi Dairesi Başkanlığı" / "<il> Defterdarlığı"), güncel özelgede `kurum` verme. Sirküler, iç genelge, genel yazı, kanun gerekçesi → `kurum: "Gelir İdaresi Başkanlığı"` + `belge_tur: "sirkuler"` | `"ic_genelge"` | `"genel_yazi"` | `"gerekce"` (sirkülerde `belge_tarihi` boş gelebilir; tarih filtresi kullanma).  Her sonucu `kaynak.markdown` atfıyla (gib.gov.tr bağlantısı) göster; özelgenin **kime** verildiğini ve tarihini tabloya yaz.
2. **Genel tebliğler** RG'de yayımlanır → `legal_search_official_gazette` (`query: "Vergi Usul Kanunu Genel Tebliği"`, `search_in: "title"`, `sort_by: "date_desc"`); son örnekler: VUK GT Sıra No 594 (RG 31.07.2026), 595 (RG 05.09.2026), 596 (RG 11.10.2026, 107/A uygulaması).  Tebliğ maddeleri için `legal_search_statute_semantic` (`mevzuat_tur: "teblig"`).
3. **Özelge araçta çıkmazsa** (araç kapsamı tam değildir): kullanıcıdan özelgenin kendisini iste (`[kullanıcı verdi]`) ya da GİB'in özelge sayfasında web araması yap ve `[web araması — doğrulayın]` etiketle; özelge sayısı, tarihi ve konusu birebir yazılsın, içerik uydurulmaz. 🔴 Bulunan özelge **yalnız talep eden mükellefi bağlar** (m.369); başkasına verilmiş özelge emsal değil, idarenin görüşünün göstergesidir.
4. **Yargı denetimi**: aynı konuda Danıştay/VDDK kararı ara; özelgeyle çelişiyorsa ikisini de göster (ORTAK-KURALLAR.md §7 araç-model çelişkisi).

---

## Kontrol listesi — "özelgeye uydum ama ceza kesildi"

1. Özelge **mükellefin kendisine mi** verildi, yazılı mı? (m.369/1)
2. Özelgede anlatılan olay ile gerçek olay **aynı mı**? Farklılık korumayı kaldırır `[incele]`.
3. Özelge tarihinden sonra işlem yapıldı mı; sonradan görüş değişikliği tebliğ/sirkülerle mi yapıldı (geriye yürümez)?
4. Tarhiyatta ceza ve gecikme faizi kesilmiş mi? Kesildiyse m.369 iptal iddiası; vergi aslı ayrı tartışılır.
5. Uzlaşmada m.369 yanılması açık bir gerekçe olarak sayılır (ek m.1/1). 

## Kontrol listesi — özelge istemeli mi?

- İşlem planlanıyor ve mevzuat gerçekten müphem mi? Yargıya intikal etmiş olaylar ve başkasının vergi durumu kapsam dışı → `../../idari-ve-kurum-basvurulari/references/ozelge-talebi.md`.
- Beklenen süre ile işlem takvimi uyumlu mu? `[doğrula]`
- Olumsuz özelge riski: idare görüşü yazılı hâle gelir; karar avukatın `[incele]`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Özelge size mi verildi, tarih ve sayısı? Metni paylaşabilir misiniz? | m.369 kapsamı |
| Özelgedeki olay anlatımı ile gerçek işlem arasında fark var mı? | Koruma |
| Özelgeden sonra konuyla ilgili tebliğ/sirküler değişti mi? | m.369/2 |
| İşlem henüz yapılmadı mı, yoksa inceleme/dava var mı? | Özelge talebi mümkün mü |

---

## İdare tarafı

- Rapor değerlendirmede mükellefe verilmiş özelgeyi tespit et; m.369 kapsamındaysa ceza ve gecikme faizi kesilmemeli.
- Görüş değişikliğinde yeni tebliğ/sirkülerin yayım tarihini esas al; geriye dönük ceza kesme.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "369" | "413" | "140"
legal_get_statute_article  law_no: "14245"  article_no: "8" | "9" | "10"     # Mükelleflerin İzahat Taleplerinin Cevaplandırılmasına Dair Yönetmelik (idari-ve-kurum-basvurulari'nda doğrulandı)
legal_search_official_gazette  query: "Vergi Usul Kanunu Genel Tebliği"  search_in: "title"  sort_by: "date_desc"
legal_search_statute_semantic  sorgu: "<konu>"  mevzuat_tur: "teblig"
legal_search_admin_guidance  sorgu: "<konu>"  belge_tur: "ozelge"  tarih_baslangic: "<son 3 yıl>"     # güncel özelgeler (birim adıyla gelir)
legal_search_admin_guidance  sorgu: "<konu>"  kurum: "Gelir İdaresi Başkanlığı"  belge_tur: "sirkuler" | "ic_genelge" | "genel_yazi"     # tarih filtresi verme
legal_search_cases  mahkeme: "danistay"  sorgu: "<konu> özelgeye uygun hareket ceza"  tarih_baslangic: "<son 3 yıl>"
```

---

## Çıktı iskeleti

```markdown
## İdari görüş değerlendirmesi — [konu]
| Kaynak | Tür (özelge/sirküler/tebliğ/karar) | Kime | Tarih | Ne diyor | Bağlayıcılık | Etiket |
### Sonuç: korunma var mı (ceza / gecikme faizi / vergi aslı ayrı ayrı)
### Özelge talebi önerisi → idari-ve-kurum-basvurulari/references/ozelge-talebi.md
```

---

## Sık hatalar

- 🔴 "Özelgeye uyan mükellefe tarhiyat yapılamaz" demek (yalnız ceza ve gecikme faizi korunur).
- 🟠 Başkasına verilen özelgeyi bağlayıcı saymak.
- 🟠 soorgla'da özelge "bulunamadı" sonucunu "özelge yok" diye raporlamak (kapsam tam değil; `kurum` filtresi birim adına bağlı).
- 🔴 Araçta bulunan, başka mükellefe verilmiş özelgeyi müvekkil için bağlayıcı saymak.

---

