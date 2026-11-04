# Esasa ilişkin savunma (mütalaaya karşı beyan)

## Ne zaman kullanılır
Kovuşturma evresinde, Cumhuriyet savcısının esas hakkındaki mütalaasından sonra, hükümden önce sanık ya da müdafiinin sunduğu yazılı savunma. Sözlü savunmanın yanında dosyaya konur.

## Süre ve dayanak
- Kanunda sabit bir yazılı savunma süresi yoktur; mahkeme mütalaaya karşı savunma için süre verir. Verilen süreyi ve sonraki duruşma tarihini sor. 
- Deliller tartışılırken söz sırası: katılan/vekili, savcı, sanık/müdafi; **son söz sanığındır** (CMK 216). 
- Hükümden sonra: **istinaf iki hafta**, hükmün gerekçesiyle birlikte tebliğinden (CMK 273/1); temyiz iki hafta (CMK 291/1). Savunma taslağının sonunda bu süreleri hatırlat; hesap için `legal_calculate_deadline(kural_kodu: "cmk_appeal" | "cmk_cassation")`. 

## Zorunlu unsurlar ve savunma kurgusu
1. **Mütalaaya cevap:** mütalaadaki her aleyhe tespiti ayrı ayrı ele al.
2. **Suçun unsurları:** maddi unsurlar (fiil, netice, nedensellik) ve manevi unsur (kast/taksir). TCK'daki suç tanımını `legal_get_statute_article(law_no: "5237", article_no: <suç maddesi>)` ile çek ve unsur unsur karşılaştır.
3. **Hukuka aykırı delil:** hukuka aykırı elde edilen delil reddolunur (CMK 206/2-a); suç ancak hukuka uygun delille ispatlanır (CMK 217/2); hâkim yalnız duruşmada tartışılmış delile dayanabilir (217/1).  Arama, el koyma, iletişimin denetlenmesi gibi işlemlerin kararına ve süresine bak `[incele]`.
4. **Şüpheden sanık yararlanır:** dosyadaki çelişkileri somut olarak listele (tanık beyanları arası çelişki, saat/konum uyumsuzluğu).
5. **Lehe hükümler (ikincil talep):** beraat olmazsa takdiri indirim (TCK 62), HAGB (CMK 231 — bkz. `hagb.md`), hapis cezasının ertelenmesi (TCK 51), seçenek yaptırımlar (TCK 50).  HAGB ile erteleme birlikte uygulanmaz (CMK 231/7). 
6. **Suç vasfının değişmesi:** daha hafif suç tipine dönüşme ihtimali varsa ek savunma hakkı (CMK 226) `[incele]`. 

**Kullanıcı aksini istemedikçe** beraat asıl, lehe hükümler terditli (ikincil) talep olarak yazılır. Sanık lehe hükümleri istemiyorsa (ör. beraat dışında hiçbir şeyi kabul etmiyorsa) bunu not al; HAGB'de artık sanığın kabulü şart değildir, bu yüzden HAGB istenmiyorsa bunun sonuçları ayrıca anlatılmalıdır (bkz. `hagb.md`).

## Görüşme soruları
1. Mahkeme, esas no, sanık bilgisi `[___]`
2. İddianamedeki suç ve madde; mütalaada istenen ceza ve madde?
3. Mütalaanın tarihi ve metni (yapıştırın)?
4. Sanığın daha önceki savunmaları (soruşturma ifadesi, sorgu) — çelişki var mı?
5. Aleyhe deliller: tanık, kamera, HTS, bilirkişi raporu, tutanak — hangileri tartışmalı?
6. Hukuka aykırılık şüphesi olan işlem var mı (arama kararı, iletişim tespiti, ifade sırasında müdafi)?
7. Lehe olgular: zarar giderildi mi, sabıka var mı, pişmanlık, kişisel durum?
8. Sanık lehe hükümleri (HAGB, erteleme) istiyor mu?
9. Sonraki duruşma tarihi ve savunma için verilen süre?

## soorgla adımları
```
legal_get_statute_article  law_no: "5237"  article_no: <suç maddesi>     # unsurlar
legal_get_statute_article  law_no: "5271"  article_no: "206" | "217" | "216" | "231" | "273"
legal_search_cases  mahkeme: "yargitay"  daire: "Ceza Genel Kurulu"
    sorgu: "<suçun unsuru tartışması; ör. dolandırıcılıkta hileli davranışın yeterliliği>"
legal_search_cases  mahkeme: "yargitay"  sorgu: "<olay> beraat şüpheden sanık yararlanır"  tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "bam"  sorgu: "<olay>"            # istinaf aşamasındaki uygulama
legal_get_case_document  belge_id: <seçilen güncel karar>
```
Daire iş bölümü yıllık değişir; suç tipine göre daireyi sabitleme, `legal_case_facets` ile dağılıma bak.

## Dilekçe iskeleti
```
[İL] [N]. [ASLİYE/AĞIR] CEZA MAHKEMESİNE

Esas No      : [___]
SANIK        : [Ad Soyad], T.C. [___]
MÜDAFİİ      : [Av. ___]
SUÇ          : [___]
MÜTALAA TARİHİ: [___]
KONU         : İddia makamının [tarih] tarihli esas hakkındaki mütalaasına karşı savunmalarımız ile BERAAT talebimizin sunulmasıdır.

AÇIKLAMALAR
I.   Olayın gerçek akışı (sanık açısından)
II.  Mütalaaya cevaplarımız (madde madde)
III. Suçun maddi ve manevi unsurları oluşmamıştır
IV.  Hukuka aykırı deliller hükme esas alınamaz (CMK 206/2-a, 217/2) [varsa]
V.   Dosyadaki şüpheler sanık lehine değerlendirilmelidir
VI.  Emsal kararlar [yalnız tam metni okunanlar]
VII. Lehe hükümler (terditli)

HUKUKİ NEDENLER: TCK m.[___]; CMK m.206, 217, 223, 231 [MCP'den çekilenler]; AİHS m.6
SONUÇ VE İSTEM : Öncelikle sanığın BERAATİNE (CMK 223/2-[___]); Mahkemeniz aksi kanaatte ise
                 TCK 62 uyarınca takdiri indirim ile [HAGB / erteleme / seçenek yaptırım]
                 uygulanmasına karar verilmesini saygıyla talep ederiz.
[Tarih — Av. — İmza]
```

## Sık hatalar
- Mütalaayı okumadan genel savunma yazmak.
- "Yüzde bir şüphe bile beraat sebebidir" gibi kanunda olmayan formüller (eski YAML'da vardı) — ilkeyi içtihatla anlat.
- Hukuka aykırı delil itirazını somut işlem göstermeden yazmak.
- Lehe hükümleri asıl talep gibi yazıp beraat talebini zayıflatmak.
- Suç tipinin güncel cezasını kontrol etmemek: 7550 (2025) ve 7571 (2025) birçok TCK maddesinin cezasını artırdı (ör. m.86, 87, 89, 170, 220); lehe kanun karşılaştırması gerekir (TCK 7).  

