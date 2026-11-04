# Cezaların toplanması (içtima), müddetname ve mahsup

## Ne zaman kullanılır
Bir kişi hakkında **birden fazla kesinleşmiş hüküm** var; koşullu salıverilme hesabı için toplama kararı gerekiyor ya da mevcut toplama/müddetname hatalı.

## Dayanak
- Her ceza diğerinden bağımsızdır; ancak başka başka kesinleşmiş hükümler varsa **107. maddenin uygulanabilmesi için** infaz hâkimliğinden **toplama kararı** istenir (5275 m.99/1). 
- Adli para cezasından çevrilen ve kurumda infaz aşamasına gelen hapis cezaları da toplamaya dâhil edilir (99/1, 7242 ek cümle). 
- **Yetkili merci (101/2):** **en fazla cezaya hükmetmiş mahkemenin bulunduğu yer infaz hâkimliği**; bu durumda birden çok infaz hâkimliği yetkiliyse **son hükmü veren** mahkemenin bulunduğu yer. En fazla ceza Yargıtay'ca ilk derece sıfatıyla verildiyse **Ankara** infaz hâkimliği; BAM ilk derece sıfatıyla verdiyse BAM'ın bulunduğu il; BAM duruşma açarak verdiyse hükmü kaldırılan ilk derece mahkemesinin yeri. 
- Karar **duruşmasız** verilir; savcı ve hükümlünün yazılı görüşü istenebilir (101/1); kararlara **itiraz** açık (101/3). 
- Birden fazla cezada koşullu salıverilme üst sınırları 107/3 ve 107/4'tedir (süreli hapislerde en fazla 28 yıl; örgüt suçlarında 32 yıl vb.). 

Eski YAML'daki merci kuralı ("en fazla cezayı veren; eşitse son hükmü veren") 2020 öncesi metne yakındı; güncel 101/2'de "birden çok infaz hâkimliği yetkili ise son hüküm" kuralı ve Yargıtay/BAM özel hâlleri var.

**Farklı infaz rejimleri:** toplanan cezalar farklı koşullu salıverilme oranlarına (yarı, üçte iki, dörtte üç) ya da farklı suç tarihlerine (geçiş hükümleri) tabiyse, her ceza kendi oranıyla hesaplanmalıdır: 5275 m.99'a göre her ceza bağımsız varlığını korur, toplama kararı 107'nin uygulanması içindir; içtima hükümlünün özgürlüğünü en az kısıtlayacak biçimde yapılır; 1.6.2005 öncesi suçlarda lehe kanun her suç için ayrı belirlenir ve karma uygulama yapılmaz. Yargıtay, iki cezanın "tabi oldukları infaz rejimleri dikkate alınarak" şartla tahliye tarihi belirlenen müddetnameyi hukuka uygun bulmuştur (Yargıtay 1. CD, E. 2023/9573, K. 2024/1567, 08.03.2024, kanun yararına bozma; atıf: CGK 17.04.2007, 32/97) `[incele]`. 

**Mahsup:** hüküm kesinleşmeden önce şahsi hürriyeti sınırlayan bütün hâllerde geçen süreler hapis cezasından indirilir; adli para cezasında gün karşılığı TCK 63'te yazılıdır (tutarı metinden çek) (TCK 63). Konutu terk etmeme adli kontrolünde iki gün bir gün sayılır (CMK 109/6).  **Başka dosyada geçen tutukluluk** (beraatle ya da cezadan fazla tutuklulukla sonuçlanan dosyadaki "artık" süre): bu sürenin başka bir mahkûmiyetten mahsup edilip edilemeyeceği ve hangi suç tarihi koşuluna bağlı olduğu kanun metninde açık değil; dilekçeye yazmadan önce güncel Yargıtay kararlarını `legal_search_cases` ile ara (`mahkeme: "yargitay"`, son 3 yıl; ör. "başka dosyada tutuklu kalınan sürenin mahsubu, TCK 63") ve en az birinin tam metnini oku; bulamazsan talebi `[ARAŞTIRMA GEREKLİ: başka dosyadaki tutukluluğun mahsubu]` etiketiyle, kesin kural gibi değil talep olarak yaz. Mahsup edilmeyen sürenin CMK m.141 tazminatıyla ilişkisini de sor. 

## Süre
- Toplama talebi için süre yok.
- Toplama kararına itiraz (101/3) → CMK 268: öğrenmeden **iki hafta** `[doğrula]`.
- Savcılığın düzenlediği **müddetnameye** itiraz: 4675 m.5 şikâyeti — öğrenmeden 15 gün, her hâlde 30 gün → `infaz-hakimligi-sikayet-ve-disiplin.md`. 
- Ayrım: çektirilecek cezanın **hesabında** duraksama (müddetname hesabı) 7242 sonrası 5275 m.98/1-b ile yine **infaz hâkimliğine** götürülür ve süreye bağlı değildir; hükmün **yorumunda** duraksama ya da sonradan yürürlüğe giren lehe kanun 98/1-a ile **hükmü veren mahkemeye**. Savcılık kararının mevzuata aykırılığı iddiası 4675 m.5 şikâyetidir (süreli). Başvuru infazı kendiliğinden durdurmaz (98/2). 

## Görüşme soruları
1. Hükümlü: ad, T.C., bulunduğu kurum `[___]`
2. Her ceza için: mahkeme, E./K. no, ceza miktarı, suç, **suç tarihi**, kesinleşme tarihi (tablo hâlinde).
3. En fazla ceza hangi mahkemeden; son hüküm hangisi? (merci tespiti)
4. Adli para cezasından çevrilen hapis var mı?
5. Gözaltı/tutukluluk süreleri (her dosya için tarihler) — mahsup edildi mi?
6. Mevcut müddetname var mı; hangi hesabı hatalı buluyorsunuz?

## soorgla adımları
```
legal_get_statute_article  law_no: "5275"  article_no: "99" | "101" | "107" | "98"
legal_get_statute_article  law_no: "5237"  article_no: "63"
legal_get_statute_article  law_no: "4675"  article_no: "5"
legal_search_cases  mahkeme: "yargitay"
    sorgu: "cezaların toplanması koşullu salıverilme oranları farklı suçlarda ayrı hesaplama infaz hâkimliği yetki"
    tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti
```
[İL] İNFAZ HÂKİMLİĞİNE   (5275 m.101/2'ye göre yetkili yer)

HÜKÜMLÜ : [Ad Soyad], T.C. [___], [kurum]
KONU    : 5275 s. Kanun m.99 uyarınca kesinleşmiş cezalarımın TOPLANMASI ve yeni müddetname
          düzenlenmesi talebimdir.

TOPLANMASI TALEP EDİLEN CEZALAR
| Mahkeme | E./K. No | Suç / suç tarihi | Ceza | Kesinleşme |
|---|---|---|---|---|
| [___] | [___] | [___] | [___] | [___] |

AÇIKLAMALAR
1. Cezalar kesinleşmiştir; 107. maddenin uygulanabilmesi için toplanmaları gerekir (m.99/1).
2. Yetki: en fazla ceza [mahkeme] tarafından verilmiştir; Hâkimliğiniz m.101/2 uyarınca yetkilidir.
3. [Farklı infaz rejimleri ve suç tarihleri — her ceza için oran]
MAHSUP TALEBİ: [gözaltı/tutukluluk tarihleri — dosya bazında]
HUKUKİ NEDENLER: 5275 m.99, 101, 107; TCK m.63 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Cezaların toplanmasına, mahsupların yapılmasına ve yeni müddetname
                 düzenlenmesine karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- Merciyi yanlış belirlemek (Yargıtay/BAM ilk derece hâllerini atlamak).
- Suç tarihlerini yazmamak — geçiş hükümleri (31.7.2023, 4.6.2025) suç tarihine göre uygulanır.
- Kesinleşmemiş hükmü toplamaya katmak.
- Müddetnameyi kendi hesabıyla "düzeltip" sunmak; farkı göster, hesabı mercie bırak.

