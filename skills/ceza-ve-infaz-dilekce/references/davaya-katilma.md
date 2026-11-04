# Kamu davasına katılma (müdahillik)

## Ne zaman kullanılır
Mağdur, suçtan zarar gören gerçek/tüzel kişi ya da malen sorumlu, açılmış kamu davasına taraf olmak, delil sunmak ve kanun yollarına savcıdan bağımsız başvurmak istiyor.

## Süre ve dayanak
- **İlk derece mahkemesindeki kovuşturmanın her aşamasında, hüküm verilinceye kadar**, şikâyetçi olduğunu bildirerek (CMK 237/1). 
- **Kanun yolu aşamasında katılma istenemez**; ilk derecede ileri sürülüp reddedilen ya da karara bağlanmayan istem, kanun yolu başvurusunda açıkça belirtilirse incelenir (237/2). 🔴 Hüküm yaklaşıyorsa bekleme. 
- Usul: kamu davası açıldıktan sonra dilekçe ya da duruşma tutanağına sözlü beyan; savcı ve sanık dinlendikten sonra karar (CMK 238). 
- Katılan, savcıya bağlı olmadan kanun yollarına başvurabilir (CMK 242/1).  Katılma isteği karara bağlanmamış, reddedilmiş ya da katılan sıfatını alabilecek surette suçtan zarar görmüş olanların istinaf başvurusunda gerekçe gösterilmemesi incelemeye engel değildir (CMK 273/4). 
- İstinaf süresi katılan için de iki hafta (CMK 273/1) — hüküm tebliğ edildiğinde hesapla (`cmk_appeal`).

## Zorunlu unsurlar
1. Kamu davasının açıldığı mahkeme ve esas no.
2. **Şikâyetçi olunduğu beyanı** ve katılma istemi (237/1 "şikâyetçi olduklarını bildirerek").
3. Suçtan **doğrudan** zarar görmenin açıklaması (maddi/manevi). Suç tipine göre "suçtan zarar gören" yorumu değişir (kamu kurumları, dernekler, tüzel kişiler) `[incele]`.
4. Vekil varsa vekâletname.

**Düzeltme:** eski YAML'da "Yargıtay suçtan zarar görmeyi geniş yorumlar; en ufak zarar ihtimali bile belirtilmeli" deniyordu — **yanlış**. CGK'nin yerleşik içtihadında suçtan zarar görme "suçtan **doğrudan doğruya** zarar görmüş bulunma hâli"dir; **dolaylı veya muhtemel zarar davaya katılma hakkı vermez**. Toplumun tamamının mağdur olduğu suçlarda bireyin (geniş anlamda mağdur) katılma hakkı yoktur; mağdurun kim olduğu önce madde metninden, yetmezse hükmün amacı ve suçun kanundaki yerinden belirlenir (Yargıtay CGK, E. 2022/310, K. 2025/121, 12.03.2025; atıf: CGK 08.11.2016, 830-412). Dilekçede zararın **doğrudan** olduğunu somut olgularla göster. 

## Görüşme soruları
1. Mahkeme, esas no, sanık, suç `[___]`
2. Talep eden kim (mağdur, mirasçı, şirket, kurum)? Kimlik/ticaret sicil bilgisi `[___]`
3. Zarar ne (maddi tutar, manevi etki, belge)?
4. Soruşturmada şikâyetçi olundu mu; uzlaştırma teklif edildi mi?
5. Hüküm verildi mi? Sonraki duruşma tarihi?
6. Vekil var mı?

## soorgla adımları
```
legal_get_statute_article  law_no: "5271"  article_no: "237" | "238" | "242" | "273"
legal_search_cases  mahkeme: "yargitay"  daire: "Ceza Genel Kurulu"
    sorgu: "suçtan doğrudan zarar görme katılan sıfatı <suç tipi>"
legal_search_cases  mahkeme: "yargitay"  sorgu: "<suç tipi> katılma talebinin reddi suçtan zarar görmeyen"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti
```
[İL] [N]. [ASLİYE/AĞIR] CEZA MAHKEMESİNE
Esas No              : [___]
KATILMA TALEP EDEN   : [___]   VEKİLİ: [___]
SANIK                : [___]
SUÇ                  : [___]
KONU                 : CMK 237 vd. uyarınca kamu davasına katılma talebimizdir.
AÇIKLAMALAR
1. Sanığın [tarih]'teki eylemi nedeniyle müvekkil doğrudan [zarar] görmüştür.
2. Müvekkil sanıktan şikâyetçidir ve cezalandırılmasını talep etmektedir.
3. [Zarara ilişkin belgeler]
HUKUKİ NEDENLER: CMK m.237, 238, 242 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Müvekkilin davaya KATILAN olarak kabulüne, sanığın cezalandırılmasına karar
                 verilmesini saygıyla talep ederiz.
```

## Sık hatalar
- 🔴 Hükümden sonra katılma istemek (kanun yolunda katılma istenemez).
- Şikâyetçi olunduğunu açıkça yazmamak.
- Katılma kararı verilmeden sonuç beklemek: katılma istemi karara bağlanmadıysa bir sonraki duruşmada hatırlat, tutanağa geçirt.
- Zarar ile suç arasındaki doğrudan bağı göstermemek.

