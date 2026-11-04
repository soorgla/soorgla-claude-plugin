# Gümrük davası: ön şart, süre, yetki, tahsil, emsal; önlem tebliğine karşı dava

## Ne zaman kullanılır
- İtiraz reddedildi (açık ya da zımni); vergi mahkemesinde dava açılacak.
- İtiraz yapılmadan dava açılmış; ne olur?
- Geri verme talebinin reddine karşı dava.
- Dampinge karşı önlem, ilave gümrük vergisi ya da ek mali yükümlülük getiren düzenleyici işleme (tebliğ/karar) karşı iptal davası.

**Dilekçe:** iskelet `../../idare-davalari-imar/references/idari-dava-dilekcesi.md` + aşağıdaki gümrüğe özgü ek unsurlar; vergi davasının ortak unsurları (tahsilin durması, YD, istinaf/temyiz sınırları) `../../vergi/references/vergi-davasi.md`. İstinaf/temyiz → `../../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`.

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Dayanak |
|---|---|---|
| İtirazın reddine karşı dava | Ret kararının tebliğini izleyen günden **30 gün**, vergi mahkemesinde | 4458 m.242/4; 2577 m.7/1, 7/2-b  |
| İtiraza 30 günde cevap verilmezse | Danıştay 7. D.: itiraz 30 gün içinde karara bağlanmazsa **zımnen reddedilmiş** sayılır ve bunu izleyen **30 gün** (vergi mahkemesi genel süresi) içinde dava açılmalı; geç açılan dava süre aşımından reddedilir (E.2025/2007 K.2025/2961, 25.09.2025 — DİBK E.2021/2 K.2022/1 gerekçesine dayanarak). **Karşı görüş** aynı kararın karşı oyunda: idare itirazı karara bağlamadıkça alacak kesinleşmez, süre işletilmemeli. Güvenli yol: 30. günü izleyen 30 gün içinde dava aç | m.242/2; Danıştay 7. D. E.2022/2870 K.2024/29, E.2022/466 K.2024/1975   |
| Geri verme reddine karşı | Ret kararına önce m.242 itirazı; itirazın reddine dava (aşağıdaki emsalde bu sıra izlenmiş) | m.211, 242; Danıştay 7. D. E.2024/3226 K.2025/3222  |
| Önlem tebliğine (düzenleyici işlem) karşı iptal davası | İlan tarihini izleyen günden; düzenleyici işlem ya da uygulama işlemi ya da ikisi birden dava edilebilir | 2577 m.7/4  |
| YD kararına itiraz, istinaf, temyiz | → `../../vergi/references/vergi-davasi.md` (7 gün; 30 gün; parasal sınırlar araçta yok) | 2577 m.27, 45, 46 |

`legal_calculate_deadline`: genel vergi davası `iyuk_tax_lawsuit` (30 gün) canlıda; gümrük açıklamalı `customs_lawsuit` ve zımni ret için `customs_lawsuit_implicit_rejection` da tanımlı; araç yanıt vermezse ya da "Süre kodu bulunamadı" dönerse elle hesapla (tebliğ günü sayılmaz), son günü `legal_check_holiday` ile kontrol et, `[doğrula]`. Uzlaşma talebinin itiraz/dava süresini durdurmasını (m.244/1) araç hesaplamaz. 

---

## Dava ön şartı: m.242 itirazı

- Danıştay 7. Daire: gümrük vergileri tahakkuklarına karşı dava açılabilmesi için m.242'deki süre içinde idari itiraza başvurulmuş ve başvurunun reddedilmiş olması gerekir; itiraz yoluna başvurulabilmesi için de idarece yapılmış bir ek tahakkuk ya da **ihtirazi kayıtla** verilmiş beyannameye dayalı tahakkuk bulunmalıdır. 
- İtiraz yapılmadan doğrudan açılan dava **idari merci tecavüzü** sayılır ve dilekçe "merciine tevdi" edilir; ilk derece kararı bu yönüyle Danıştay'ca yerinde bulundu (somut olayda usul ekonomisi nedeniyle başka gerekçeyle bozuldu).  Merciine tevdide itiraz süresi kaçmışsa işlem kesinleşmiş olabilir 🔴 `[incele]`.
- Eski YAML'daki "süre geçtiyse doğrudan dava yolu kalır" yanlıştır.

---

## Görev, yetki, taraf

- **Görevli mahkeme:** gümrük vergileri ve cezalarına ilişkin uyuşmazlıklar vergi mahkemesinde; antidamping/ilave vergi tebliği gibi düzenleyici işlemler Danıştay'da ilk derece olarak görülebiliyor (2018-2019 tebliğlerine karşı Danıştay 7. D. ilk derece kararları).  Güncel Danıştay ilk derece görev ve daire dağılımı `[doğrula]`.
- **Yetkili mahkeme:** itirazın reddine karşı "işlemin yapıldığı yerdeki" idari yargı mercii. 
- **Davalı:** Ticaret Bakanlığı adına ilgili gümrük müdürlüğü (emsallerde "… Bakanlığı adına … Gümrük Müdürlüğü").  İtirazı reddeden bölge müdürlüğü mü davalı gösterilmeli `[incele]`.
- **Vergi dışı gümrük işlemleri** (gümrük müşavirliği izni, antrepo izni, yetkilendirilmiş yükümlü statüsü) idare mahkemesinde 60 günlük genel süreye tabidir → `../../idare-davalari-imar/SKILL.md`. 

---

## Tahsil ve yürütmenin durdurulması

- Dava açılması hâlinde gümrük vergileri mahkemece yükümlü aleyhine verilen kararın gümrük idaresine tebliğ edildiği tarihte tahsil edilebilir hâle gelir.  Vergi davalarında dava açılmasının tahsili durdurduğu genel kural (İYUK m.27/4) ve istisnaları (ihtirazi kayıtlı beyana dayalı işlemler, tahsilat işlemleri) için → `../../vergi/references/vergi-davasi.md`. İhtirazi kayıtlı beyana dayalı tahakkukta YD istemi gerekebilir `[incele]`.
- Ödeme süresi itirazla kesilmişti; yargı kararının tebliğinden yeniden başlar (m.198/2). 

---

## Emsal araması ve okunması

1. `legal_search_cases mahkeme: "danistay"` — uyuşmazlık kaynağını cümleyle yaz (ör. "royalti ödemesinin gümrük kıymetine ilavesi satış koşulu"). 2024-2025'te 7. Daire'nin seri kararları var (ör. royalti: E.2022/411 K.2024/709 ve aynı gün verilen benzerleri). 
2. Aynı gün verilmiş seri kararlarda tek kararı oku, diğerlerini "aynı yönde" diye an; birbirinin kopyası olmayabilir `[incele]`.
3. **Karşı oy** sık; çoğunluk gerekçesini ayır (K.2024/29'da karşı oy var).
4. Danıştay 2026 kapsamı seyrek; 2024-2025 kullan, notta yaz.

---

## Kontrol listesi — dava açmadan önce

1. m.242 itirazı süresinde yapıldı mı, sonucu ne (açık ret / zımni ret / kısmi kabul)? Kısmi kabulde yeniden alınan kararlara yeniden itiraz gerekebilir (K.2024/29 olayı) `[incele]`.
2. Uzlaşma talep edildi mi; tutanakla uzlaşılan kısım dava dışı (m.244/4).
3. Süre: ret tebliği + 30 gün; cevap yoksa itirazın idareye intikalinden 30 gün sonra zımni ret + 30 gün (Danıştay 7. D. E.2025/2007 K.2025/2961; karşı oy var) — güvenli tarihi esas al.
4. Yetkili mahkeme: işlemin yapıldığı yer.
5. Kalemler: vergi aslı ile ceza ayrı; KDV/ÖTV ve damping vergisi ayrı istem.
6. Usul sebepleri önce: tebliğ zamanaşımı (m.197/2), yetkisiz merci, gerekçesizlik, laboratuvar ve ikinci tahlil, yurt dışı doğrulama yazısının dosyada olmaması.
7. Esas: tarife (GYK), kıymet (m.24-31), menşe (m.17-22, 198/4), rejim şartları.
8. Emsal: son 3 yıldan en az bir Danıştay kararı tam metin.
9. Harç ve kanun yolu sınırları → vergi-davasi.md.

---

## Gümrüğe özgü dilekçe ek unsurları

- **Dava konusu:** ek tahakkuk ve ceza kararının tarih/sayısı, beyanname sayısı ve tescil tarihi, itiraz dilekçesinin tarihi, itirazın ret (ya da zımni ret) tarihi; vergi kalemleri ve ceza ayrı tutarlarıyla.
- **Ön şartın karşılandığı** açıkça yazılır (m.242 itirazı, tarih, sonuç).
- **Ekler:** beyanname, fatura, menşe/dolaşım belgesi, BTB/BMB, laboratuvar raporu, itiraz dilekçesi ve cevabı, varsa uzlaşma tutanağı ("uzlaşma vaki olmadı").
- **Önlem tebliğine karşı davada:** tebliğin RG tarihi ve sayısı, davacının soruşturmaya katılımı ve hakkındaki oran, uygulama işlemi de dava ediliyorsa künyesi.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| İtirazı ne zaman verdiniz, cevap geldi mi, ne zaman tebliğ edildi? | Ön şart ve süre |
| İtiraz kısmen kabul edildi mi, yeni karar düzenlendi mi? | Yeni itiraz gerekip gerekmediği |
| Uzlaşmaya gittiniz mi, tutanak var mı? | Dava edilemez kısım |
| Eşya hangi gümrük müdürlüğünde işlem gördü? | Yetki |
| Aynı konuda başka dosyalarınız (aynı eşya, farklı beyanname) derdest mi? | Usul ekonomisi, birleştirme |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4458"  law_type: "Kanun"  article_no: "242" | "197" | "198" | "211"
legal_get_statute_article  law_no: "2577"  law_type: "Kanun"  article_no: "7" | "27"
legal_search_cases  mahkeme: "danistay"  sorgu: "<uyuşmazlık> gümrük ek tahakkuk itirazın reddi"  tarih_baslangic: "2023-01-01"
legal_search_cases  mahkeme: "danistay"  sorgu: "İthalatta Haksız Rekabetin Önlenmesine İlişkin Tebliğin iptali <ürün>"
legal_get_case_document  belge_id: "<seçilen karar>"
```

---

## Sık hatalar

- 🔴 İtirazsız dava (merci tecavüzü).
- 🔴 Kendi beyanına dayalı tahakkuka ihtirazi kayıt olmadan itiraz ve dava (önce m.211 geri verme yolu düşünülmeli).
- 🟠 Önlem tebliğine karşı davayı vergi mahkemesinde açmak ya da uygulama işlemini dava etmeyi unutmak `[incele]`.
- 🟠 Davalıyı yanlış göstermek.
- 🟡 Seri kararları ayrı ayrı emsal diye saymak.

---

## İdare tarafı
- İtiraz 30 günde karara bağlanmazsa zımni ret davası ve yargılama gideri riski doğar; gerekçeli karar ver.
- Kısmi kabulde yeni karar düzenleniyorsa itiraz yolunu ve süresini kararda göster.
→ `gumruk-idaresi-tarafi.md`

---

