# Duruşma mazeret dilekçesi ve bekletici mesele talebi

İki kısa ara dilekçe. Ortak nokta: davanın esasını değil, **akışını** etkiler.

---

## A. Mazeret dilekçesi

### Ne zaman kullanılır
Taraf ya da vekili duruşmaya katılamayacak. Amaç: dosyanın işlemden kaldırılmasını ya da yokluğunda aleyhe işlem yapılmasını önlemek.

### Gelmemenin sonuçları (HMK m.150)

- Usulüne uygun davet edilen **iki taraf da gelmezse** dosya **işlemden kaldırılır** (m.150/1).
- Biri gelir, diğeri gelmezse gelen tarafın talebiyle yokluğunda devam edilir ya da dosya işlemden kaldırılır; **geçerli özrü olmadan** gelmeyen taraf yokluğunda yapılan işlemlere itiraz edemez (m.150/2).
- İşlemden kaldırılan dava **üç ay** içinde yenilenebilir; bir aydan sonra yenilemede yeniden harç alınır (m.150/4). Üç ayda yenilenmezse dava açılmamış sayılır (m.150/5). İlk yenilemeden sonra bir defadan fazla takipsiz bırakılamaz (m.150/6).
- Bu yüzden mazeret yalnız "ertelensin" değil, aynı zamanda m.150/2 anlamında **geçerli özür** belgesidir.

### Mazeretin kabulü
HMK'da genel bir "mazeret dilekçesi" maddesi bulunmuyor; mazeretin kabulü hâkimin takdirindedir. İstinaf duruşması için ayrı hüküm vardır (HMK m.358/2). Avukatın mesleki mazereti (aynı saatte başka duruşma, şehir dışında olma) içtihatla korunur: mazeretin reddedilip aynı celsede esas hakkında karar verilmesi **hukuki dinlenilme hakkını** (HMK m.27; Anayasa m.36) ihlal eder ve bozma sebebidir; **tarafın başka vekillerinin bulunması mazereti reddetme sebebi değildir** (Yargıtay 9. HD, E. 2025/9409, K. 2026/354, 19.01.2026). Dayanak olarak Avukatlık Kanunu'nda ayrı bir mazeret maddesi doğrulanmadı; dilekçede HMK m.27 ve bu içtihada dayan `[incele]`.

Süre: kanuni süre yok; **duruşmadan önce** UYAP'tan gönder. Belge (rapor, çakışan duruşmanın esas no ve saati) ekle.

### Görüşme soruları (eski `data_schema`)
1. Mahkeme, esas no — `court_name`, `file_number`
2. Duruşma tarihi ve saati — `hearing_date_time`
3. Mazeret bildiren (taraf / vekil) — `party_info`
4. Mazeret: çakışan duruşma (mahkeme, esas no, saat) / sağlık (rapor tarihi, süresi) / diğer — `excuse_reason`
5. Karşı taraf gelecek mi? Yokluğunuzda tanık dinlenmesi, keşif gibi kritik işlem var mı?
6. Yeni günün UYAP'tan öğrenilmesi istenecek mi?

### İskelet
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
MAZERET BİLDİREN : [Davacı/Davalı] Vekili Av. [___]
KONU : [tarih saat] tarihli duruşmaya [mazeret] nedeniyle katılamayacağımdan mazeretli sayılmam talebidir.

AÇIKLAMALAR : [tarih saat] tarihli duruşmaya, [aynı saatte [mahkeme] [esas no] sayılı dosyadaki duruşmam | ekte sunulan [tarih] tarihli sağlık raporu] nedeniyle katılamayacağım.

SONUÇ VE İSTEM : Mazeretimin kabulü ile duruşmanın başka bir güne ertelenmesine, yeni duruşma gününün UYAP üzerinden öğrenilmesine karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
EKLER: [___]
```

### Sık hatalar
- 🟠 Belgesiz mazeret; sağlık raporu duruşma gününü kapsamıyor.
- 🟠 Dosya daha önce işlemden kaldırılıp yenilenmiş — ikinci takipsizlikte dava açılmamış sayılır (m.150/6). 🔴
- 🟡 Duruşmadan sonra gönderilmiş.

---

## B. Bekletici mesele (bekletici sorun) talebi

### Ne zaman kullanılır
Davada hüküm verilebilmesi başka bir davaya, idari makamın tespitine ya da bir hukuki ilişkinin varlığına kısmen veya tamamen bağlı.

### Kurallar
- Mahkeme bekletme kararını **verebilir** (takdir); zorunluluk iddiası içtihada dayanır `[incele]`.
- Başka dava/idari başvuru henüz yapılmamışsa mahkeme ilgili tarafa **uygun süre** verir; süresinde başvurulmazsa o taraf iddiasından vazgeçmiş sayılır (m.165/2). Bu süreyi kullanıcıya ayrıca hatırlat.
- **Ceza davası ilişkisi (eski YAML düzeltildi):** TBK m.74'e göre hukuk hâkimi kusur, ayırt etme gücü, beraat, kusurun değerlendirilmesi ve zararın belirlenmesi konularında ceza hâkiminin kararıyla **bağlı değildir**. Eski YAML "ceza kararı maddi vakıanın tespiti yönünden hukuk davasını etkiler" diyordu; bu kanun metninde yok, içtihat kuralıdır: Yargıtay'ın yerleşik uygulamasına göre **kesinleşmiş ceza hükmüyle saptanan maddi olgu** (ve maddi nedensellik bağı) hukuk hâkimini bağlar; ceza davasındaki **kusur raporu** bağlamaz (Yargıtay HGK, E. 2024/166, K. 2025/396, 25.06.2025; ilke aynı biçimde HGK E. 2022/660, K. 2023/1066'da). Aynı dosyada ilk derece mahkemesi HAGB kararının kesinleşmiş mahkûmiyet gibi bağlayıcı olmadığını kabul etti; HGK'nin bu noktadaki sonucu okunmadı — HAGB'li ceza dosyasına dayanacaksan HGK kararının tam metnini oku. Bekletici mesele talebini bu ayrıma göre kur.

### Görüşme soruları (eski `data_schema`)
1. Mevcut dava: mahkeme, esas no, talep eden taraf — `court_name`, `file_number`, `party_info`
2. Beklenecek dava/işlem: mahkeme veya idari makam, esas/başvuru no, aşaması — `pending_case_info`
3. İki dava arasındaki bağ: hangi sonuç bu davayı nasıl değiştirir? — `connection_details`
4. Beklenecek dava henüz açılmadı mı? (m.165/2 süresi)

### soorgla çağrıları
```
legal_get_statute_article law_no: "6100" article_no: "165" | "150" | "358"
legal_get_statute_article law_no: "6098" article_no: "74"
legal_search_cases sorgu: "<dava türü> davasında <diğer dava> sonucunun bekletici mesele yapılmaması bozma" mahkeme: "yargitay" tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar>
```

### İskelet
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
TALEP EDEN : [___] — VEKİLİ: Av. [___]
KONU : [Mahkeme] [esas no] sayılı dosyanın bekletici mesele yapılması talebidir.

BEKLENMESİ TALEP EDİLEN DOSYA : [mahkeme / idari makam], [esas no], [aşama]

AÇIKLAMALAR VE HUKUKİ BAĞLILIK
1. [Beklenen dosyanın konusu]
2. [O dosyadaki sonucun bu davadaki hükmü nasıl belirleyeceği]

İLGİLİ KARARLAR : [yalnız tam metni okunmuş kararlar]
SONUÇ VE İSTEM : [Dosya] sonucunun HMK m.165 uyarınca bekletici mesele yapılmasına karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```

### Sık hatalar
- 🟠 Bağ soyut; beklenen kararın sonucu bu davayı nasıl etkileyeceği yazılmamış.
- 🟠 Ceza kararının hukuk hâkimini her yönden bağladığı yazılmış (TBK m.74'e aykırı).
- 🟡 m.165/2 süresi verildiği hâlde diğer dava açılmamış.

---
