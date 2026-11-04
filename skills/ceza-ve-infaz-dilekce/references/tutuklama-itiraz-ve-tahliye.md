# Tutuklamaya / adli kontrole itiraz ve tahliye talebi

İki ayrı dilekçe aynı dosyada:
- **Tutuklamaya itiraz:** tutuklama (ya da tutukluluğun devamı, tahliye isteminin reddi, adli kontrol) kararına karşı **kanun yolu**. Süreye bağlıdır.
- **Tahliye talebi (salıverilme istemi):** her aşamada yapılabilen **istem**; reddi üzerine ayrıca itiraz edilir.

## Ne zaman kullanılır
- Sulh ceza hâkimliği soruşturmada tutuklama ya da adli kontrol kararı verdi → itiraz.
- Kovuşturmada mahkeme tutukluluğun devamına karar verdi → itiraz ya da yeni tahliye talebi.
- Delil durumu değişti, tutukluluk uzadı, sağlık durumu kötüleşti → tahliye talebi (CMK 104).
- Ağır adli kontrol (konutu terk etmeme vb.) ölçüsüz → itiraz ya da kaldırılması talebi.

## Süre ve dayanak

| Dilekçe | Süre | Başlangıç | Dayanak |
|---|---|---|---|
| İtiraz (tutuklama, devam, tahliye reddi, adli kontrol) | **İki hafta** | Kararın öğrenilmesi (CMK 35'e göre tefhim ya da tebliğ) | CMK 268/1  ; itiraz edilebilirlik CMK 101/5 ve 104/2  |
| Tahliye talebi | Süre yok; soruşturma ve kovuşturmanın her aşamasında | — | CMK 104/1  |
| Soruşturmada tutukluluğun incelenmesi | En geç **otuzar gün**de bir sulh ceza hâkimince; şüpheli de bu süre içinde isteyebilir | Tutuklama | CMK 108/1-2  |
| Kovuşturmada inceleme | Her oturumda, oturumlar arasında ya da otuz günlük süre içinde re'sen | — | CMK 108/3  |
| Azami tutukluluk | Ağır ceza görevi dışı 1 yıl (+6 ay); ağır ceza 2 yıl (uzatma toplam 3 yıl; TCK İkinci Kitap Dördüncü Kısım 4-7. bölüm ve TMK suçlarında 5 yıl); soruşturma evresinde 6 ay / 1 yıl (bazı suçlarda 1,5 yıl + 6 ay); çocuklarda yarı ve dörtte üç | Tutuklama | CMK 102  |

**Eski bilgi düzeltildi:** eski YAML "tefhimden itibaren 7 gün (CMK 268)" diyordu. Güncel metin **iki hafta**. Süreleri yine her seferinde maddeden çek.

`legal_calculate_deadline` itiraz süresini hesaplamaz (`cmk_objection` kodu yok); elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]` işaretle.

## Merci

- Kararı veren merciye verilir; o merci yerinde görmezse en çok **üç gün** içinde inceleme merciine gönderir (CMK 268/2). 
- **Sulh ceza hâkimliğinin tutuklama ve adli kontrol kararlarına itiraz → yargı çevresindeki asliye ceza mahkemesi hâkimi**; sulh ceza işlerine asliye ceza hâkimi bakıyorsa ağır ceza mahkemesi başkanı (CMK 268/3-b, 7331 ile değişik).  Başlık: "… SULH CEZA HÂKİMLİĞİNE — Gönderilmek üzere … ASLİYE CEZA MAHKEMESİ HÂKİMLİĞİNE" `[incele]`.
- Asliye ceza kararları → ağır ceza mahkemesi; ağır ceza kararları → numara olarak izleyen daire ya da en yakın ağır ceza (CMK 268/3-c). 
- Dosya BAM ya da Yargıtay'da ise salıverilme istemi hakkında o daire karar verir (CMK 104/3). 

## Zorunlu unsurlar (dilekçede mutlaka)

Tutuklama kararında **şunlar somut olgularla gösterilmiş mi?** (CMK 101/2) 
1. Kuvvetli suç şüphesi,
2. Tutuklama nedeninin varlığı,
3. Tedbirin ölçülülüğü,
4. Adli kontrolün yetersiz kalacağı.

Her biri için "kararda gösterilmemiş / basmakalıp" itirazını ayrı başlıkta yaz.

Diğer kontrol noktaları:
- **Kuvvetli şüphe + somut delil:** CMK 100/1. Tutuklama nedenleri kaçma şüphesi ve delil karartma (100/2). 
- **Katalog suç:** CMK 100/3'te sayılan suçlarda tutuklama nedeni "var sayılabilir"; ama kuvvetli şüphenin somut delillere dayanması yine şarttır ("somut delillere dayanan kuvvetli şüphe sebeplerinin varlığı halinde"). Liste 7406 (2022) ve 7528 (2024) ile genişledi; suçun listede olup olmadığını her seferinde maddeden kontrol et. 
- **Tutuklama yasağı:** sadece adli para cezası gerektiren suçlarda ya da üst sınırı iki yılı geçmeyen hapis cezası gerektiren suçlarda (vücut dokunulmazlığına karşı kasten işlenenler hariç) tutuklama kararı verilemez (CMK 100/4). 🔴 Bu durumda itirazın ilk gerekçesi budur. 
- **Adli kontrol alternatifleri** (CMK 109/3): yurt dışı yasağı, imza, konutu terk etmeme, belirli yere gitmeme, güvence vb. Talep edilen yükümlülüğü somut olarak yaz. Konutu terk etmeme yükümlülüğünde her iki gün cezadan bir gün mahsup edilir (109/6). 
- **Ağır hasta, engelli, gebe ya da doğumdan itibaren altı ay geçmemiş kadın** şüpheli için tutuklama yerine adli kontrol (CMK 109/4). Bu durum varsa ayrı başlık aç. 
- **Azami süre aşımı** (CMK 102) ve süre dolduğu için salıverilen hakkında adli kontrol (109/7).

## Görüşme soruları

1. Kim adına? (şüpheli/sanık, müdafi; tutuklu mu, adli kontrolde mi)
2. Kararı veren merci, karar tarihi, sorgu/değişik iş/esas numarası? `[___]`
3. Karar yüze karşı mı açıklandı (tefhim) yoksa tebliğ mi edildi; hangi tarihte?
4. İsnat edilen suç ve TCK maddesi (iddia/sevk yazısına göre)?
5. Kararda hangi tutuklama nedeni yazıyor (aynen)? Kararın bir örneği var mı?
6. Dosyadaki deliller neler; hangileri şüpheliyi doğrudan gösteriyor? Kısıtlama kararı var mı?
7. Kişisel durum: sabit ikamet, iş, aile, çocuk, sağlık sorunu, gebelik, yaş, sabıka.
8. Daha önce itiraz ya da tahliye talebi yapıldı mı, sonucu?
9. Ne kadar süredir tutuklu; iddianame düzenlendi mi; duruşma tarihi?
10. Önerilecek adli kontrol türü (imza, yurt dışı yasağı, konut)?

## soorgla adımları

```
legal_get_statute_article  law_no: "5271"  article_no: "100" | "101" | "102" | "104" | "108" | "109" | "268" | "35"
legal_search_cases  mahkeme: "anayasa"
    sorgu: "tutuklama kararında kuvvetli suç şüphesini gösteren somut delillerin ve adli kontrolün yetersizliğinin gösterilmemesi"
    tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "aihm"  sorgu: "<olay; gerekçesiz tutuklama, uzun tutukluluk>"
legal_get_case_document  belge_id: <seçilen güncel karar>     # alıntı-önerme kontrolü
```
Not: AYM bireysel başvuru kararları bu konuda en zengin kaynaktır (ör. 2026 tarihli Birinci Bölüm kararları aramada çıktı). Tam metni okumadan dilekçeye alıntılama. 

## Dilekçe iskeleti — tutuklamaya itiraz

```
[İL] [N]. SULH CEZA HÂKİMLİĞİNE
Gönderilmek üzere
[İL] ASLİYE CEZA MAHKEMESİ HÂKİMLİĞİNE (CMK 268/3-b)

Değişik İş / Sorgu No : [___]
İTİRAZ EDEN (ŞÜPHELİ) : [Ad Soyad], T.C. [___], [cezaevi]
MÜDAFİİ               : [Av. ___]
SUÇ                   : [___] (iddiaya göre)
TUTUKLAMA TARİHİ      : [___]  ·  ÖĞRENME/TEFHİM: [___]
KONU                  : [Merci]'nin [tarih] tarihli ve [sayı] sayılı tutuklama kararına itirazlarımızın sunulmasıdır.

AÇIKLAMALAR
1. Olay ve kararın özeti
2. Kuvvetli suç şüphesini gösteren somut delil yoktur / gösterilmemiştir (CMK 100/1, 101/2-a)
3. Tutuklama nedeni somut olgulara dayanmıyor (kaçma şüphesi yok: ikamet, iş, aile; delil karartma yok: deliller toplanmış) (CMK 100/2, 101/2-b)
4. Tedbir ölçüsüzdür (beklenen ceza, tutuklulukta geçen süre) (CMK 100/1 ikinci cümle, 101/2-c)
5. Adli kontrol yeterlidir; önerilen yükümlülükler: [___] (CMK 101/1, 101/2-d, 109)
6. [Varsa] Tutuklama yasağı / CMK 109/4 kapsamı / azami süre
7. Emsal kararlar (yalnız tam metni okunanlar)

HUKUKİ NEDENLER : CMK m.100, 101, 109, 267 vd., 268; Anayasa m.19; AİHS m.5 [her biri MCP'den çekilmiş olmalı]
DELİLLER        : Soruşturma dosyası, ikametgâh, SGK/iş belgesi, sağlık raporu [___]

SONUÇ VE İSTEM  : İtirazımızın kabulü ile tutuklama kararının kaldırılarak şüphelinin TAHLİYESİNE,
                  mümkün görülmezse CMK 109 uyarınca [___] adli kontrol tedbirinin uygulanmasına,
                  itiraz yerinde görülmezse dosyanın inceleme merciine gönderilmesine karar verilmesini
                  saygıyla talep ederiz.
[Tarih] — [Ad Soyad / Av.] — [İmza]
EKLER: [___]
```

## Dilekçe iskeleti — tahliye talebi

Aynı iskelet; başlık davanın görüldüğü mahkeme, "KONU: Tutukluluk hâlinin kaldırılarak sanığın tahliyesine, olmazsa adli kontrol uygulanmasına karar verilmesi talebidir (CMK 104)". Açıklamalarda **son kararlardan bu yana ne değişti** sorusu öne çıkar: toplanan deliller, tanık beyanları, tutuklulukta geçen süre, sağlık, suç vasfının değişme ihtimali.

## Sık hatalar

- 🔴 Eski "7 gün" bilgisiyle süre hesabı (artık iki hafta) — ya da tersine, "iki hafta var" diye beklemek: itiraz ne kadar erken verilirse o kadar iyi.
- İtirazı inceleme merciine doğrudan vermek: dilekçe **kararı veren mercie** verilir.
- Tahliye talebini itiraz yerine kullanmak ya da tersi; ikisi ayrı yollardır.
- Katalog suçta "tutuklama zorunludur" kabulü: 100/3 bir karine, otomatik tutuklama değildir; somut delil şartı ve ölçülülük yine aranır.
- Basmakalıp "kaçma şüphesi yoktur" cümlesi: somut olguyla (tapu, kira sözleşmesi, SGK kaydı, çocuk okul belgesi) destekle.
- Adli kontrolü yalnız "yeterlidir" diye geçmek: **hangi** yükümlülüğün neden yeterli olduğunu yaz.
- AYM/AİHM kararını tam metnini okumadan alıntılamak.

