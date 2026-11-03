# İptal davası, dava şartları, idareye başvuru ve yürütmenin durdurulması

## Ne zaman kullanılır
- Kullanıcıya bir idari işlem tebliğ edildi (ret, iptal, ceza, atama dışı her türlü bireysel işlem; düzenleyici işlem) ve "dava açabilir miyim, süre ne zaman doluyor" diye soruyor.
- İdareye bir istemle başvurulmuş, cevap gelmemiş ya da kesin olmayan cevap gelmiş (zımni ret).
- İşlem uygulanırsa telafisi güç zarar doğacak; yürütmenin durdurulması (YD) isteniyor.
- İdare tarafı: işlemin dava şartları ve beş unsur yönünden sağlam kurulup kurulmadığını görmek, savunma vermek, mahkeme kararını uygulamak istiyor.

İmar, kamulaştırma ve tam yargı özel kuralları ayrı dosyalardadır; bu dosya bütün idari davalara ortak usulü verir.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| İptal davası: Danıştay ve idare mahkemesinde **altmış gün** (özel kanunda ayrı süre yoksa) | Yazılı bildirimi izleyen gün | İYUK m.7/1-2(a) | Önce özel süre ara (aşağıdaki tablo). Vergi mahkemesinde 30 gün → vergi becerisi. |
| İlanı gereken düzenleyici işlem | İlan tarihini izleyen gün | İYUK m.7/4 | Uygulama işlemiyle birlikte ya da ayrı dava açılabilir; düzenleyici işlemin iptal edilmemiş olması uygulama işleminin iptaline engel değil. |
| Adresi belli olmayana ilanla bildirim | Son ilanı izleyen günden itibaren **on beş gün sonra** | İYUK m.7/3 | Özel kanunda aksine hüküm yoksa. |
| İdareye istem — cevap verilmezse ret sayılır: **otuz gün** | Başvuru | İYUK m.10/2 | Ret sayıldığı günden itibaren dava süresi içinde dava. Kesin olmayan cevapta kesin cevap beklenebilir ama bekleme başvurudan itibaren **dört ayı** geçemez. Sonradan gelen cevap: dava açılmamış ya da süreden reddedilmişse cevabın tebliğinden itibaren altmış gün. |
| Üst makama (yoksa işlemi yapana) itiraz — **dava süresi içinde** yapılır, süreyi **durdurur**; otuz gün cevapsızlık ret | İtiraz tarihi | İYUK m.11 | Ret ya da zımni retle süre **kaldığı yerden** işler: başvuruya kadar geçen süre hesaba katılır. İvedi yargılama ve sınav davalarında m.11 **uygulanmaz** (m.20/A-2/b, m.20/B-1/b). |
| Görevsiz **adli** yargıda açılıp görevsizlikle reddedilen dava | Görevsizlik kararının kesinleşmesini izleyen gün: **otuz gün** | İYUK m.9 | Adli yargıya başvuru tarihi idari yargıya başvuru tarihi sayılır; idari dava süresi henüz dolmamışsa o süre de kullanılabilir. |
| Dilekçe reddi (m.3/m.5'e aykırılık) sonrası yeni dilekçe: **otuz gün** | Ret kararının tebliği | İYUK m.15/1-d | Aynı yanlışlık tekrarlanırsa dava reddedilir (m.15/5). |
| Savunmaya / ikinci dilekçeye cevap: **otuz gün** (bir defa, en çok 30 gün uzatma) | Tebliğ | İYUK m.16/3 | Süre geçtikten sonra verilen dilekçeye dayanarak hak iddia edilemez (m.16/4). |
| YD kararına itiraz: **yedi gün**, bir defa | Tebliği izleyen gün | İYUK m.27/7 | İdare/vergi mahkemesi kararına → bölge idare mahkemesi; Danıştay dairesi kararına → İDDK/VDDK. İtiraz üzerine verilen karar kesin. İvedi yargılamada ve sınav davalarında YD kararına itiraz **yok**. |
| İdarenin kararı uygulaması: gecikmeksizin, **en geç otuz gün** | Kararın idareye tebliği | İYUK m.28/1 | Uygulanmazsa idare aleyhine maddi ve manevi tazminat davası (m.28/3-4). 7588 ile (RG 11.07.2026) güvenlik/terör gerekçeli kamu görevinden çıkarma davalarında göreve iade sonucu doğuran kararlar ancak **kesinleşmeden sonra** uygulanır → `kamu-personeli`. |

### Özel dava süreleri (genel 60 günü değiştirenler — ilk bakılacaklar)

| Konu | Süre | Dayanak |
|---|---|---|
| İvedi yargılama: ihale işlemleri (yasaklama hariç), acele kamulaştırma, ÖYK kararları, 2634 turizm tahsisleri, ÇED kararları, 6306 Cumhurbaşkanı kararları | **30 gün**; savunma 15 gün; temyiz 15 gün; istinaf yok | İYUK m.20/A |
| MEB ve ÖSYM merkezî sınavları | **10 gün** | İYUK m.20/B |
| Kamulaştırma işleminin iptali | **30 gün** (asliye hukukun tebligatından / ilandan) | 2942 m.14 → `kamulastirma.md` |
| 6306 kapsamındaki idari işlemler | **30 gün** (tebliğden) | 6306 m.6/9 → `imar-plani-ruhsat-ve-donusum.md` |
| SGK İPC (Kurum itirazı reddedildikten sonra) | **30 gün** | 5510 m.102 |
| KVKK İPC | Özel süre yok → 60 gün | 6698 m.18/3 + İYUK m.7 (kvkk becerisi) |
| Askerî hizmet uyuşmazlıkları | Yetki: görev yerinin bağlı olduğu BİM'in bulunduğu yer idare mahkemesi | İYUK m.20/C |

`legal_calculate_deadline` bu süreleri tanımıyor; elle hesapla, `legal_check_holiday`, `[doğrula]`. Süre hesabı İYUK m.8: süre tebliğ/yayın/ilanı izleyen gün başlar; tatiller süreye dahildir, son gün tatilse izleyen ilk çalışma günü; süre **adli tatile (çalışmaya ara verme)** rastlarsa ara vermenin bittiği günü izleyen tarihten itibaren **yedi gün** uzar.

---

## Dava şartları — ilk inceleme sırası (İYUK m.14/3)

İdari yargıda mahkeme şu sırayla bakar; analizi de bu sırayla kur:

1. **Görev ve yetki** — işlem idari mi (adli yargı ayrımı), Danıştay mı (2575 m.24: Cumhurbaşkanı kararları, ülke çapındaki düzenleyici işlemler, birden çok mahkemenin yetki alanına giren işler) yoksa idare mahkemesi mi? Yetki **kamu düzenindendir**; genel kural işlemi yapan merciin bulunduğu yer idare mahkemesi (İYUK m.32). Kamu görevlilerinde m.33; **imar, kamulaştırma, yıkım, işgal, tahsis, ruhsat ve iskân** gibi taşınmaza ilişkin davalarda taşınmazın bulunduğu yer idare mahkemesi (m.34/1); köy/belediye/özel idare mevzuatının uygulanmasında ilgili birimin bulunduğu yer (m.34/2). Taşınır mallarda malın bulunduğu yer (m.35); idari sözleşme dışındaki tam yargıda sırasıyla zararı doğuran uyuşmazlığı çözmeye yetkili mahkeme, hizmetin görüldüğü/eylemin yapıldığı yer, diğer hâllerde davacının ikametgâhı (m.36); vergi uyuşmazlıkları m.37; bağlantılı davalar m.38.
2. **İdari merci tecavüzü** — dava yerine idareye başvurulmuşsa dilekçe görevli idari mercie tevdi edilir (m.15/1-e).
3. **Ehliyet** — iptal davasında **menfaat ihlali** (m.2/1-a), tam yargıda **kişisel hakkın doğrudan ihlali** (m.2/1-b). Dernek, oda, komşu malik, plan alanında oturanlar için menfaat ilişkisini somutlaştır `[incele]`.
4. **Kesin ve yürütülmesi gereken işlem** — hazırlık işlemi, görüş, iç yazı, bilgi notu, tekrar niteliğindeki işlem davaya konu olmaz. Yapı tatil tutanağı ayrıca dava edilebilir mi? → `kacak-yapi-yikim-ve-imar-cezasi.md`.
5. **Süre aşımı** — yukarıdaki tablolar.
6. **Husumet** — işlemi yapan idare; yanlış hasım dava reddi değil, gerçek hasma tebliğ sebebi (m.15/1-c).
7. **Dilekçenin m.3 ve m.5'e uygunluğu** → `idari-dava-dilekcesi.md`.

## Esas: beş unsur (İYUK m.2/1-a) ve yerindelik yasağı

| Unsur | Soru | Tipik aykırılık |
|---|---|---|
| Yetki | İşlemi yapan makam kanunen yetkili mi? Yetki devri yazılı ve usulüne uygun mu? | Encümen yerine başkanlık oluru; il müdürlüğü yerine ilçe; kurul yerine başkan |
| Şekil/usul | Savunma, görüş, ilan, tebliğ, gerekçe, toplantı ve karar yeter sayısı | Savunma alınmadan ceza; askı ilanı eksik plan; gerekçesiz ret |
| Sebep | Dayanılan maddi olgu gerçekten var mı, hukuki nitelendirme doğru mu? | Ölçümsüz tutanağa dayalı ceza; yanlış bent |
| Konu | İşlemin doğurduğu sonuç hukuka uygun mu, ölçülü mü? | Yasal alt/üst sınır dışında ceza; tamamı yerine kısmi yıkım gereken hâl |
| Maksat | Kamu yararı dışında amaç (husumet, kayırma) var mı? | İspatı güç; somut belge yoksa `[incele]`, öne çıkarma |

İdari yargı **yerindelik denetimi yapamaz**, idarenin takdir yetkisini kaldıracak ya da idari işlem niteliğinde karar veremez (m.2/2). Dilekçede "işlem yerinde değil" yerine "işlem şu unsur yönünden hukuka aykırı" de; takdir yetkisinde **kamu yararı ve hizmet gereklerine uygun kullanım** ölçütüne bağla.

## Yürütmenin durdurulması (İYUK m.27)

- Dava açmak işlemi durdurmaz (m.27/1). YD için **iki şart birlikte**: (1) uygulanması hâlinde **telafisi güç veya imkânsız zarar**, (2) işlemin **açıkça hukuka aykırı** olması. Kural olarak idarenin savunması alındıktan ya da savunma süresi geçtikten sonra, gerekçeli karar.
- **Uygulanmakla etkisi tükenecek** işlemlerde (ör. yıkımın icrası, ihaleden çıkarma) savunma alınmadan YD verilebilir — dilekçede bunu ayrı başlıkla iste. Kamu görevlilerinin atama/nakil/görevlendirme işlemleri bu kapsamda sayılmaz (m.27/2, 6526).
- Yalnız "kanun hükmü için AYM'ye başvurulduğu" gerekçesiyle YD verilemez (m.27/2 son cümle).
- **Teminat** kural olarak aranır; durumun gereğine göre aranmayabilir; idare ve adli yardımdan yararlanan teminattan muaftır (m.27/6). Dilekçede teminatsız YD gerekçesi yaz (ekonomik durum, kamu yararı, açık aykırılık) `[incele]`.
- YD istemi dilekçe ve eklerinden yerinde görülmezse savunma alınmadan reddedilebilir (m.27/3). **Aynı sebeplerle ikinci kez YD istenemez** (m.27/10) — ilk istemi güçlü kur; yeni olgu varsa yeni sebep olarak sun.
- YD kararlarının idarece uygulanması zorunlu (m.28/1).

## Kontrol listesi — ilgili / davacı tarafı

1. İşlemin tarihi, sayısı, makamı; tebliğ tarihi ve şekli (e-Tebligat, posta, memur eliyle, ilan) — kronoloji tablosu.
2. Özel süre var mı (yukarıdaki tablo)? İvedi yargılama mı?
3. m.11 itirazı yapılmış mı, yapılacaksa süreye etkisi (durdurma, kalan süre) hesaplandı mı? İvedi yargılamada m.11 yok.
4. Zımni ret: başvuru tarihi + 30 gün (2021 öncesi başvuruda 60 gün) + dava süresi.
5. Görev (adli/idari; Danıştay ilk derece mi), yetki (m.32-38), husumet.
6. Ehliyet ve menfaat ilişkisi; birden fazla işlem tek dilekçeyle ancak aralarında maddi/hukuki bağlılık ya da sebep-sonuç ilişkisi varsa; birden fazla davacı ancak hak/menfaat iştiraki ve aynı olay/sebep varsa (m.5). Aksi hâlde dilekçe reddi (m.15/1-d).
7. Beş unsur tablosu; her iddiaya belge.
8. YD gerekli mi? Telafisi güç zarar somut mu? Uygulanmakla etkisi tükenecek mi?
9. İptal + tam yargı birlikte mi açılacak (m.12)? Zarar şimdiden belli mi? → `tam-yargi-ve-hizmet-kusuru.md`.
10. Emsal: son 3 yıldan en az bir Danıştay kararı tam metin.
11. Kesinlik / kanun yolu öngörüsü (davanın açıldığı tarihteki parasal sınır — ek m.1/2, 7550).

## Kontrol listesi — idare / kamu görevlisi tarafı

1. **İşlemi kurarken:** yetkili makam ve yetki devri belgesi; dayanak mevzuat maddesi işlem metninde; olgu tespiti (tutanak, rapor) işlemle tutarlı; ilgiliye savunma/görüş hakkı (öngörülmüşse); gerekçe; **dava yolu, süre ve merci** bildirimi (Anayasa m.40/2 ve kurum mevzuatı — eksikliği süreyi tartışmalı hâle getirir `[incele]`). Danıştay 8. D.'ye göre bildirim eksikliği genel 60 günlük süreyi ortadan kaldırmaz (usulüne uygun tebliğ ya da tüm unsurlarıyla öğrenme tarihinden işler); ancak işlem **özel (kısa) bir dava süresine** tabiyse ve bu işlemde gösterilmemişse özel süre değil **60 günlük genel süre** uygulanır. İdare tarafı için sonuç: bildirim yapılmazsa kısa özel sürelerden yararlanılamaz; tebliğ (Tebligat K., e-Tebligat).
2. **Başvuruya cevap:** m.10 başvurularını 30 gün içinde kesin cevapla; kesin olmayan cevap ilgiliye dört aya kadar bekleme hakkı verir.
3. **Savunma (m.16):** dilekçenin tebliğinden 30 gün; işlem dosyasının aslı ya da onaylı örneği savunmayla gönderilir (m.16/5). İlk inceleme itirazlarını (süre, ehliyet, kesin işlem, husumet) savunmanın başına koy.
4. **YD kararı gelince:** gecikmeksizin, en geç 30 gün içinde uygula (m.28/1); itiraz (7 gün) uygulamayı durdurmaz `[incele]`. Uygulamamak idare aleyhine tazminat ve kamu görevlisi için disiplin/ceza riski (m.28/3-4).
5. **Mahkeme bilgi-belge istediğinde** belirlenen sürede gönder (m.20/1); gönderilmemesinin etkisi ara kararda önceden takdir edilir (m.20/2).

## Görüşme soruları

| Alan | Soru |
|---|---|
| İşlem | İşlemin tarihi, sayısı, hangi makam? Metni var mı? |
| Tebliğ | Ne zaman, nasıl tebliğ edildi (e-Tebligat, posta, ilan, öğrenme)? Zarf/tebliğ mazbatası var mı? |
| Önceki başvurular | İdareye başvuru/itiraz yapıldı mı, tarih ve cevap? |
| Etki | İşlem uygulanırsa ne olur (yıkım, kapatma, ihraç, para)? Ne zaman uygulanacak? |
| Taraf | Davacı gerçek/tüzel kişi; T.C. kimlik/vergi no; vekil? |
| Değer | Parasal sonuç (tam yargı, İPC) — kesinlik ve harç için |
| İdare tarafı | Dosyada hangi tutanak, rapor, görüş var? Savunma alındı mı? Dava yolu bildirildi mi? |

## soorgla çağrıları

```
legal_get_statute_article law_no: "2577" article_no: "2" | "3" | "7" | "9" | "10" | "11" | "12" | "13" | "14" | "15" | "16" | "27" | "28" | "32" | "33"
legal_list_statute_articles law_no: "2577" article_no: "20" include_content: true # 20/A, 20/B, 20/C
legal_get_statute_article law_no: "2577" article_no: "ek 1" # parasal sınır artışı
legal_get_statute_article law_no: "2575" article_no: "24" law_type: "Kanun"
legal_search_statute_versions law_no: "2577" query: "<eski metin ibaresi>" # başvuru tarihindeki metin
legal_search_official_gazette query: "2577 sayılı İdari Yargılama Usulü Kanununun" document_type: "kanun" sort_by: "date_desc"
legal_search_cases sorgu: "<olay — ör. savunma alınmadan tesis edilen işlemin şekil yönünden hukuka aykırılığı>" mahkeme: "danistay" tarih_baslangic: "<3 yıl önce>"
legal_case_facets sorgu: "<konu>" mahkeme: "danistay"
legal_get_case_document belge_id: "<seçilen karar>"
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## İdari işlem değerlendirmesi — [makam, tarih, sayı]
### Sonuç
### Kronoloji ve süre tablosu
| Olay | Tarih | Süre | Son gün | Dayanak | Durum |
### Dava şartları (m.14/3 sırasıyla)
| Şart | Durum | Not |
### Hukuka aykırılık — beş unsur
| Unsur | İddia | Dayanak | Güç |
### Yürütmenin durdurulması
[iki şart + uygulanmakla etkisi tükenecek mi + teminat]
### Emsal (okunan tam metin)
### Eksik bilgi / Şimdi ne yapalım?
```

## Sık hatalar
- 60 günü her işleme uygulamak; özel süreyi (2942, 6306, 5510, ivedi yargılama, sınav) atlamak.
- Zımni retti hâlâ 60 gün saymak (7331, 2021 sonrası başvurularda 30 gün) ya da tersine 2021 öncesi başvuruya yeni süreyi uygulamak.
- m.11 itirazını dava süresi geçtikten sonra yapıp süreyi "yeniden başlatmak" sanmak; m.11 başvurusu süreyi yalnız durdurur, kalan süre işler.
- İvedi yargılama işinde m.11 itirazına güvenmek (uygulanmaz) ya da YD reddine itiraz etmek (yok).
- Hazırlık işlemine (görüş, iç yazı) dava açmak; kesin işlemi beklemeden süre kaçırmak.
- Aynı sebeplerle ikinci YD istemek.
- Yerindelik argümanı kurmak ("daha uygun bir yer vardı").
- Daireyi eski YAML eşlemesiyle sabitleyip arama yapmak.
