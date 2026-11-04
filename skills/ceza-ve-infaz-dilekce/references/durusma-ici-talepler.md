# Duruşma içi talepler: tevsi-i tahkikat ve vareste tutulma

## 1. Tevsi-i tahkikat (delil toplanması talebi)

### Ne zaman kullanılır
Hükümden önce, maddi gerçeği aydınlatacak bir delilin (kamera kaydı, HTS/baz kaydı, tanık, bilirkişi, keşif, banka kaydı) toplanmasını istemek için. Soruşturma evresinde benzer talep savcılığa yapılır (CMK 160 vd.) `[incele]`.

### Süre ve dayanak
- Sabit süre yok; hükümden önce. Delilin ya da olayın **geç bildirilmiş olması reddi için sebep değildir** (CMK 207). 
- Talep yalnız şu hâllerde reddedilebilir: delil kanuna aykırı elde edilmişse, ispat edilmek istenen olayın karara etkisi yoksa, istem sadece davayı uzatmak amacıyla yapılmışsa (CMK 206/2). Dilekçe bu üç ret sebebinin **hiçbirinin** olmadığını göstermelidir. 
- Eski YAML'da "CMK 177" (sanığın delil getirmesi) ve "CMK 289 eksik inceleme" atıfları vardı. 
- Reddedilen delil talebi istinaf/temyiz sebebi olarak saklı tutulur; ret kararının tutanağa geçirildiğini kontrol et `[incele]`.

### Zorunlu unsurlar
1. Toplanacak delil — **somut** (kurum, tarih aralığı, saat, kamera konumu, hat numarası).
2. Delilin nereden isteneceği (BTK, emniyet, banka, belediye, hastane).
3. Delilin karara etkisi: neyi ispatlayacak, sonucu nasıl değiştirir (beraat, vasıf değişikliği).
4. 206/2 ret sebeplerinin yokluğu.
5. **Kayıt silinme riski:** kamera ve trafik kayıtları kısa sürede silinir; "acil" ibaresi ve ilgili kuruma doğrudan müzekkere talebi.

### Görüşme soruları
1. Mahkeme, esas no, talep eden (sanık/katılan) `[___]`
2. İstenecek her delil için: ne, nerede, hangi tarih/saat aralığı?
3. Bu delil neyi ispatlayacak?
4. Daha önce istendi mi, reddedildi mi?
5. Sonraki duruşma tarihi?

## 2. Duruşmadan vareste (bağışık) tutulma

### Ne zaman kullanılır
Sorgusu yapılmış sanığın sonraki duruşmalara gelme zorunluluğunun kaldırılması.

### Dayanak ve şartlar
- **Mahkemece sorgusu yapılmış** sanık ya da bu konuda yetkili kılınmış müdafi ister; mahkeme bağışık **tutabilir** (takdir) (CMK 196/1).  Eski YAML "sadece sorgu + talep yeterlidir" diyordu; madde "tutabilir" der, karar mahkemenin takdirindedir `[incele]`.
- Müdafiin vareste talebi için vekâletnamede **özel yetki** gerekip gerekmediğini kontrol et ("bu hususta sanık tarafından yetkili kılındığı hâllerde"). 🟠
- Alt sınırı beş yıl ve üzeri hapis gerektiren suçlar dışında sanık **istinabe** yoluyla sorguya çekilebilir (196/2); yurt içindeki sanık için SEGBİS (196/4). Sanık uzakta ve sorgusu yapılmamışsa önce bu yollar talep edilir. 
- Vareste tutulmak hüküm duruşmasına gelmeme ve son söz hakkı açısından sonuç doğurur; hükmün yokluğunda açıklanması, tebliğ ve kanun yolu süresinin tebliğden başlaması konusunda kullanıcıyı uyar `[incele]`. 

### Görüşme soruları
1. Mahkeme, esas no, sanık `[___]`
2. Sorgu hangi duruşmada/tarihte yapıldı (tutanak)? Yapılmadıysa istinabe/SEGBİS mi isteniyor?
3. Gerekçe: ikamet başka il, iş, sağlık, eğitim, yurt dışı?
4. Müdafiin vekâletnamesinde vareste/özel yetki var mı?

## soorgla adımları
```
legal_get_statute_article  law_no: "5271"  article_no: "196" | "206" | "207" | "217"
legal_search_cases  mahkeme: "yargitay"
    sorgu: "sanığın lehine delil toplanması talebinin gerekçesiz reddi eksik araştırma bozma"
    tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti — tevsi-i tahkikat
```
[İL] [N]. [ASLİYE/AĞIR] CEZA MAHKEMESİNE
Esas No     : [___]
TALEP EDEN  : [Sanık/Katılan] [___]   VEKİLİ/MÜDAFİİ: [___]
SUÇ         : [___]
KONU        : Maddi gerçeğin ortaya çıkarılması için aşağıdaki delillerin toplanması talebidir.

TOPLANMASINI TALEP ETTİĞİMİZ DELİLLER
1. [Delil] — [kurum] — [tarih/saat aralığı] — [ACİL: kayıt silinme riski]
GEREKÇELERİMİZ VE DELİLLERİN ESASA ETKİSİ
1. [Delil 1 neyi ispatlar; CMK 206/2 ret sebeplerinin yokluğu]
HUKUKİ NEDENLER: CMK m.206, 207, 217 [MCP'den çekilenler]
SONUÇ VE İSTEM : Taleplerimizin kabulü ile belirtilen delillerin toplanmasına, deliller toplanmadan
                 esas hakkında karar verilmemesine karar verilmesini saygıyla talep ederiz.
```

## Dilekçe iskeleti — vareste
```
[MAHKEME]   Esas No: [___]
SANIK: [___]   MÜDAFİİ: [___]
KONU: Sorgusu tamamlanan sanığın sonraki duruşmalardan vareste tutulması talebidir (CMK 196/1).
AÇIKLAMALAR: Sanığın sorgusu [tarih] tarihli [N]. celsede yapılmıştır. Sanık [gerekçe] nedeniyle
             duruşmalara katılmakta güçlük çekmektedir. Müdafi olarak duruşmaları takip edeceğiz.
SONUÇ VE İSTEM: Sanığın duruşmalardan vareste tutulmasına karar verilmesini saygıyla talep ederiz.
```

## Sık hatalar
- Delili soyut tanımlamak ("kamera kayıtları istensin") — hangi kamera, hangi saat?
- Vareste talebini sorgudan önce yapmak.
- Vareste'yi hak gibi sunmak; takdire bağlıdır.
- Talebin reddini tutanakta itiraz kaydı olmadan geçmek.

