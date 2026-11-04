# Vergi davası: açma, yürütmenin durdurulması, tahsilin durması, kanun yolları

## Ne zaman kullanılır
- Tarhiyata, cezaya, ödeme emrine, hacze, düzeltme-şikâyet reddine, iade reddine karşı **vergi mahkemesinde dava** açılıp açılmayacağı ve nasıl açılacağı.
- Dava açılırsa tahsil durur mu, yürütmenin durdurulması (YD) gerekir mi?
- Vergi mahkemesi kararına istinaf, bölge idare mahkemesi (BİM) kararına temyiz mümkün mü (parasal sınırlar, 7524 ve 7589 değişiklikleri)?

**Dilekçe metni:** idari dava dilekçesi iskeleti `../../idare-davalari-imar/references/idari-dava-dilekcesi.md` (İYUK m.3 zorunlu unsurları) + aşağıdaki "Vergiye özgü ek unsurlar". İstinaf/temyiz dilekçesi → `../../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`.

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Dayanak |
|---|---|---|
| Vergi mahkemesinde dava | **30 gün**; tebliğ yapılan hâllerde tebliği, tahakkuku tahsile bağlı vergilerde tahsilatı, tevkif yoluyla alınanlarda istihkak sahibine ödemeyi, tescile bağlı vergilerde tescili **izleyen günden** | 2577 m.7/1, 7/2-b  |
| Ödeme emrine karşı dava | Tebliğden itibaren **15 gün** (→ `amme-alacagi-tahsili-6183.md`) | 6183 m.58  |
| Uzlaşma vaki olmazsa cezaya dava | Tutanak tebliğinden; süre bitmiş/15 günden az kalmışsa 15 gün | VUK ek m.7  |
| YD kararına itiraz | Tebliği izleyen günden itibaren **7 gün**, bir defaya mahsus; vergi/idare mahkemesi kararına karşı BİM'e | 2577 m.27/7  |
| İstinaf | Kararın tebliğinden itibaren **30 gün**; parasal sınırı geçmeyen vergi davası kararları **kesin** | 2577 m.45/1 (7524/52 ile değişik cümle)  |
| Temyiz (BİM kararına) | Tebliğden itibaren **30 gün**; vergi davalarında konusu kanundaki sınırı aşanlar (m.46/1-b) | 2577 m.46/1-b (7524/53 ile yeniden düzenleme)  |
| Temyiz — 7589 ile yeni yol | m.46/1 kapsamı dışındaki davalarda BİM ilk derece kararını **kaldırıp yeniden karar verdiyse** 30 gün içinde temyiz; ancak tek hâkimle görülen davalar, sınır altı farklar ve yalnız vekâlet ücreti/yargılama gideri kararları hariç | 2577 m.46/2 "(Ek:16/7/2026-7589/6 md.)"  |

**Parasal sınırları bu dosyaya yazma.** m.45 ve m.46'daki sınırlar her yıl VUK mük.298 yeniden değerleme oranıyla takvim yılı başından artırılır; istinaf/temyiz edilebilirlikte **davanın açıldığı tarihteki** sınır esas alınır (İYUK ek m.1). Güncel yılın tutarını `legal_get_social_parameters` (`tur: "iyuk_istinaf_siniri"` / `"iyuk_temyiz_siniri"`) verir; dava başka bir yılda açıldıysa o yılın tutarını RG'den çek `[doğrula]`. 

`legal_calculate_deadline` `iyuk_tax_lawsuit` (İYUK m.7, 30 gün), `iyuk_appeal`, `iyuk_cassation` kodlarını tanır; sonucu elle sayımla sağla, `legal_check_holiday`. 

---

## Tahsilin durması ve YD — en çok karıştırılan nokta

- İdari yargıda kural: dava açmak işlemin yürütülmesini **durdurmaz** (m.27/1). 
- **Vergi davası istisnası:** vergi mahkemelerinde vergi uyuşmazlıklarından doğan davaların açılması, tarh edilen vergi, resim, harç ve benzeri mali yükümler ile zam ve cezalarının **dava konusu edilen bölümünün** tahsilini durdurur; YD istemine gerek yoktur. 
- **İstisnanın istisnası** — şu davalar tahsili durdurmaz, YD istenmelidir: (a) m.26/3 uyarınca işlemden kaldırılan dosyanın yenilenmesi, (b) **ihtirazi kayıtla verilen beyanname** üzerine yapılan işlemlere karşı davalar, (c) **tahsilat işlemlerine** (ödeme emri, haciz) karşı davalar.  Ödeme emri davasında YD istemeyi unutmak 🔴.
- YD şartları birlikte: **telafisi güç veya imkânsız zarar** ve **açıkça hukuka aykırılık**; karar gerekçeli olmalı.  Kural olarak teminat karşılığı verilir; durumun gereğine göre teminat aranmayabilir; idareden ve adli yardımdan yararlananlardan alınmaz.  Aynı sebeplerle ikinci kez YD istenemez. 
- Davayı kaybetme hâlinde gecikme faizi: dava konusu yapılan vergilerin ödenmemiş kısmına normal vade tarihinden yargı kararının tebliğine kadar gecikme faizi uygulanır; dava sırasında kısmen ya da tamamen ödeme yapılabilir (faiz yükünü azaltır `[incele]`).  7524 ile uzlaşılan vergilerde gecikme faizine ilişkin cümle kaldırıldı. 

---

## Kontrol listesi — dava açmadan önce

1. **Dava edilebilir işlem mi?** İhbarname, ödeme emri, haciz, düzeltme/şikâyet reddi, iade reddi, ihtirazi kayıtla beyan üzerine tahakkuk — hangisi? Ön işlem (ör. rapor tek başına) dava konusu olmaz `[incele]`.
2. **Süre** (yukarıdaki tablo) ve **tebliğ tarihinin** belgesi (e-tebligatta iletim tarihi + 5 gün).
3. **Uzlaşma / indirim çatışması**: uzlaşma talep edilen ceza için dava ancak uzlaşma vaki olmazsa; m.376 başvurusu varsa dava indirimi düşürür. → `ihbarname-ve-yol-secimi.md`
4. **Kısmi dava**: vergi aslını kabul edip yalnız cezaya ya da tersi; tahsil durması yalnız dava konusu kısım için.
5. **Görevli ve yetkili mahkeme**: vergi mahkemesi; yetki, vergiyi tarh ve tahakkuk ettiren / cezayı kesen dairenin, 6183 uygulamasında **ödeme emrini düzenleyen** dairenin, diğer uyuşmazlıklarda işlemi yapan dairenin bulunduğu yer (İYUK m.37). 
6. **İptal sebepleri** — usul önce: tebliğ, zamanaşımı (VUK m.114, m.374), yetkisiz inceleme, raporun tebliğ edilmemesi, inceleme tutanağı ve **somut tespit** eksikliği; sonra esas: hukuki yorum, matrah, istisna şartları, ceza katı.
7. **Delil**: vergi inceleme raporu ve vergi tekniği raporu, tutanaklar, defter ve belgeler, banka kayıtları, Ba-Bs, sevk irsaliyeleri, ödeme kanıtları. Rapor dosyada yoksa mahkemeden getirtilmesini iste.
8. **Emsal**: son 3 yıldan en az bir Danıştay / VDDK kararı tam metin okunarak (ORTAK-KURALLAR.md §7). Danıştay 2026 kapsamı seyrek; 2024-2025 kullan.
9. **Harç**: başvurma harcı ve YD harcı → `legal_get_social_parameters` (`harc_basvurma_asliye`), nispi karar harcı uygulaması `[doğrula]`.
10. **Kanun yolu stratejisi**: miktar istinaf/temyiz sınırının altındaysa ilk derece kararı kesin olabilir → ilk derecede eksiksiz dilekçe kritik. 🟠

---

## Vergiye özgü dilekçe ek unsurları (iskelet `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`'de)

- **Davalı:** ihbarnameyi düzenleyen vergi dairesi müdürlüğü / başkanlığı (belediye vergilerinde belediye başkanlığı) `[doğrula]`.
- **Dava konusu:** ihbarname tarihi, sayısı, vergi türü, dönem; vergi aslı, vergi ziyaı cezası, usulsüzlük cezası **ayrı ayrı tutarlarıyla**; hangisinin dava konusu olduğu (kısmi ise açıkça).
- **Tebliğ tarihi** ve tebliğ şekli (e-tebliğse iletim tarihi + "beşinci günün sonu").
- **YD istemi**: yalnız tahsili kendiliğinden durmayan davalarda (ödeme emri, haciz, ihtirazi kayıt) ya da başka bir yürütme gereken işlemde; telafisi güç zarar somutlanmalı.
- **Uzlaşma durumu**: uzlaşma talep edildi mi, tutanak tarihi.
- **İstem:** "… ihbarnamesiyle tarh edilen … vergi ile kesilen … cezanın kaldırılmasına" (vergi davalarında yerleşik ifade "terkin / kaldırılması"); ödeme emrinde "ödeme emrinin iptaline".
- Ekler: ihbarname, tebliğ belgesi, raporlar, vekâletname.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Hangi işleme dava açılacak; tebliğ tarihi ve şekli? | Süre, tahsilin durması |
| Uzlaşma ya da m.376 başvurusu yaptınız mı? | Dava hakkı |
| Dava konusu tutar (vergi + ceza) ne kadar? | Kesinlik / temyiz sınırı |
| Tahsilat başladı mı, haciz var mı? | YD gereği |
| Vergi inceleme raporu ve eki vergi tekniği raporu elinizde mi? | Delil |
| Aynı konuda önceki dönemler için dava / karar var mı? | Emsal ve tutarlılık |

---

## İdare tarafı (davalı vergi dairesi)

- Savunmada tebliğ zinciri, zamanaşımı hesabı ve raporun somut tespitlerini belgeyle göster; yalnız "rapora dayanılmıştır" deme.
- Tahsili kendiliğinden durmayan davalarda YD istemine karşı kamu alacağının tehlikeye düşeceğini somutla.
- Lehine olmayan VDDK kararlarını da değerlendir; ısrar riski ve faiz yükünü yönetime raporla.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "2577"  article_no: "7" | "27" | "45" | "46"
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "112" | "ek 7"
legal_search_cases  mahkeme: "danistay"  daire: "Vergi Dava Daireleri Kurulu"  sorgu: "<uyuşmazlık>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "danistay"  sorgu: "<uyuşmazlık>"   # daire filtresiz; dönen kararın dairesine bak
legal_get_case_document  belge_id: "<seçilen karar>"
legal_get_social_parameters  tur: "harc_basvurma_asliye" | "harc_temyiz_danistay" | "harc_istinaf_bam"
legal_search_official_gazette  query: "İdari Yargılama Usulü Kanunu parasal sınır yeniden değerleme"  sort_by: "date_desc"
```

---

## Çıktı iskeleti

```markdown
## Vergi davası değerlendirmesi — [işlem / tebliğ tarihi]
### Sonuç
### Süre ve tahsil
| İşlem | Son gün | Tahsil kendiliğinden duruyor mu? | YD gerekli mi? |
### İptal sebepleri (usul → esas), güç sırasıyla
### Kanun yolu öngörüsü (sınır: [madde metninden], dava tarihi esas) [doğrula]
### Emsal (tam metin okunanlar)
### Dilekçe için devir özeti
```

---

## Sık hatalar

- 🔴 Ödeme emri / haciz davasında YD istememek (tahsil durmaz).
- 🔴 Ödeme emrine 30 gün sanmak (15 gün).
- 🟠 İstinaf/temyiz sınırını eski tutardan okumak; 7524 ve 7589 değişikliklerini atlamak.
- 🟠 Daireyi sabit yazmak ("gelir vergisi = 4. Daire" gibi); YAML'lar kendi içinde çelişiyordu.
- 🟡 Davanın yalnız dava konusu kısmın tahsilini durdurduğunu unutmak.

---

