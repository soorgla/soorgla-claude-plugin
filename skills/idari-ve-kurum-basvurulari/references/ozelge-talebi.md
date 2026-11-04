# Özelge (mukteza) talebi

Mükellefin, vergi durumu ve vergi uygulaması bakımından **müphem ve tereddütlü** gördüğü bir konuda Gelir İdaresi Başkanlığından ya da yetkili kıldığı makamdan yazılı izahat istemesi. 

Süreye bağlı bir itiraz değildir; ama değeri **işlemden önce** alınmasındadır.

---

## Ne zaman kullanılır / kullanılmaz

- **Kullanılır:** planlanan ya da süren bir işlemin vergilendirilmesinde (KDV oranı, tevkifat, istisna, gider yazma, stopaj) mevzuat açık değilse.
- **Kullanılmaz:** başkalarının vergi durumu hakkında izahat talepleri ve **yargıya intikal etmiş olaylar** özelge kapsamında değerlendirilmez.  Olay incelemedeyse ya da tarhiyat yapılmışsa özelge yerine `vergi-uzlasma-indirim-duzeltme.md`.

## Koruyucu etki — doğru anlatım

Yetkili makamın mükellefe **yazıyla yanlış izahat vermesi** hâlinde **vergi cezası kesilmez ve gecikme faizi hesaplanmaz**.  Eski YAML'daki "özelgeye uyan mükellefe sonradan aksi yönde **tarhiyat yapılamaz**" ifadesi **yanlış**tır: vergi aslı tarh edilebilir; korunan ceza ve gecikme faizidir. Koruma, özelgede anlatılan olayın gerçek olayla **aynı** olmasına bağlıdır `[incele]`; bu yüzden olay eksiksiz anlatılmalıdır.

## Makam

Özelge, gelir veya kurumlar vergisi mükelleflerince **sürekli mükellefiyetin bulunduğu** vergi dairesi başkanlığından, başkanlık bulunmayan illerde **defterdarlıktan** istenir (m.10/1); diğer mükellef ve vergi sorumluları ikametgâh ya da kanuni merkezlerinin bulunduğu yerdeki vergi dairesi başkanlığına / defterdarlığa, ikametgâhı ya da kanuni merkezi olmayanlar Ankara, İstanbul veya İzmir Vergi Dairesi Başkanlığından birine başvurur (m.10/2).  Eski YAML'daki "413 Seri No.lu Genel Tebliğ" atfı doğrulanmadı; dayanak VUK m.413 ve bu **Yönetmelik**tir. **Form zorunlu:** talep, Gelir İdaresi Başkanlığının internet sitesinde örneği bulunan **Özelge Talep Formu** ile yapılır; form kullanılmadan yapılan talep **kabul edilmez** (m.10/3). Formun güncel hâlini ve elektronik (internet vergi dairesi) başvuru imkânını Başkanlık sitesinden kontrol et — Yönetmelik elektronik başvuruyu düzenlemiyor; dilekçeyi formun eki/açıklaması olarak hazırla. Özelge kapsamı dışında kalanlara (başkasının vergi durumu, yargıya intikal etmiş olay, incelemedeki işlem, teorik soru, işlem gerçekleştikten sonraki başvuru vb.) dikkat (m.8/2). 

Uygulama birliği için Başkanlık sirküler yayımlayabilir; özelgeler vergi mahremiyeti gözetilerek internette yayımlanır.  Bu yüzden yazmadan önce **aynı konuda yayımlanmış özelge ve sirküler** taranır.

---

## Zorunlu unsurlar (eski şablon + Yönetmelik)

1. Mükellef bilgileri: ad-soyad/unvan, VKN/TCKN, bağlı vergi dairesi, adres.
2. Konu: tereddüt edilen hususun tek cümlelik özeti.
3. **Olayın tam anlatımı:** işlem, taraflar, sözleşme, fatura akışı, tutar ve tarihler. (Koruyucu etki buna bağlı.)
4. **Tereddüt edilen husus:** hangi hükmün nasıl uygulanacağı.
5. **Mükellefin görüşü:** "Kanaatimizce …" — gerekçesiyle. Yönetmelik m.8-11 mükellef görüşünü **zorunlu unsur olarak saymıyor** (eski YAML "zorunlu" diyordu); görüş alanı Özelge Talep Formunda yer alıyorsa doldur, yoksa yine de yazmak tavsiye edilir. 
6. Ekler: sözleşme, örnek fatura vb.

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `taxpayer_info.*` | Unvan/ad-soyad, VKN/TCKN, bağlı vergi dairesi, adres? |
| `tax_office_presidency` | İkametgâh/kanuni merkezin bulunduğu il? (makamı belirlemek için) |
| `subject_summary` | Bir cümleyle soru nedir? |
| `event_description` | İşlemi baştan sona anlatın: kim, kime, ne satıyor/veriyor, hangi tarihte, hangi bedelle, sözleşme var mı? |
| `hesitation_point` | Hangi vergi ve hangi madde konusunda tereddüt var? |
| `taxpayer_opinion` | Sizce uygulama nasıl olmalı ve neden? |
| (yeni) | Bu konuda inceleme, tarhiyat ya da dava var mı? (varsa özelge kapsamı dışı olabilir) |
| `attachments` | Hangi belgeler eklenecek? |
| `legal_basis` | (Araştırma adımında doldurulur.) |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "213"  article_no: "413" | "369"
legal_get_statute_article  law_no: "14245"  article_no: "8" | "9" | "10" | "11"     # Mükelleflerin İzahat Taleplerinin Cevaplandırılmasına Dair Yönetmelik
legal_get_statute_article  law_no: "<3065 KDV | 193 GVK | 5520 KVK | …>"  article_no: "<ilgili madde>"
legal_search_statute_semantic  sorgu: "<konu>"  mevzuat_tur: "teblig"           # ilgili genel tebliğ
legal_search_admin_guidance  sorgu: "<konu> özelge"                               # kapsam dar; GİB özelgeleri bulunmayabilir
legal_search_cases  mahkeme: "danistay"  sorgu: "<konu>"  tarih_baslangic: "<son 3 yıl>"
```
GİB özelgeleri 2026-10-31'den beri soorgla'da: `legal_search_admin_guidance` `belge_tur: "ozelge"` + `tarih_baslangic` (`kurum` özelgeyi veren birimin tam adıdır; güncel özelgede verme). Talepten önce aynı konuda verilmiş özelgeleri ara ve dilekçede "benzer konuda verilmiş özelgeler" olarak an; başkasına verilmiş özelge talep edeni bağlamaz. Araç kapsamı tam değildir; bulunamazsa ORTAK-KURALLAR.md §5 (sessiz tamamlama yok) — "yayımlanmış özelgeler tarandı" deme.

---

## Dilekçe iskeleti

```markdown
[… VERGİ DAİRESİ BAŞKANLIĞINA / … DEFTERDARLIĞINA]
([Mükellef Hizmetleri … Grup Müdürlüğü])

MÜKELLEF       : [unvan / ad-soyad]
VKN / TCKN     : [___]
VERGİ DAİRESİ  : [___]
ADRES          : [___]

KONU: [… işleminin … vergisi karşısındaki durumu] hakkında özelge talebidir.

1. OLAYIN ÖZETİ
[Tam ve olgusal anlatım; tarih, taraf, tutar, belge]

2. TEREDDÜT EDİLEN HUSUS
[Hangi hükmün nasıl uygulanacağı]

3. MÜKELLEF GÖRÜŞÜMÜZ
[Kanaatimizce … çünkü … — dayanak maddeler ve varsa yayımlanmış özelge/sirküler]

Yukarıda açıklanan hususta 213 sayılı VUK m.413 uyarınca özelge verilmesini saygılarımla arz ederim.

[Tarih]                                                    MÜKELLEF / VEKİLİ
                                                           [ad-soyad / unvan, imza]
EKLER: [sözleşme, örnek fatura, …]
```

## Sık hatalar

- 🟠 Olayı eksik ya da genel anlatmak: özelge başka bir olay için verilmiş sayılır, m.369 koruması işlemez.
- 🟠 İnceleme başlamışken ya da dava varken özelge istemek.
- 🟡 "Özelge alınırsa vergi çıkmaz" demek: vergi aslı yine tarh edilebilir.
- 🟡 Yayımlanmış özelge ve sirkülerleri taramadan yazmak.

---

