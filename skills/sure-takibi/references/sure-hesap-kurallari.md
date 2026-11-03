# Süre hesap kuralları

**Ne zaman kullanılır:** her `--ekle`, `--cikar` ve `--guncelle` (tarih değişikliği) adımında son günü hesaplarken ya da kullanıcının verdiği son günü sınarken.

Bu dosya süre **uzunluğu** vermez. Uzunluk her seferinde dayanak maddeden çekilir. Burada yalnız **sayım kuralları**, kuralların hangi maddeden çekileceği ve hesap gerekçesinin nasıl yazılacağı vardır. Upstream `legal-clinic/deadlines` "beceri hesap yapmaz, öğrenci yapar" der; bizde araç ve madde metni olduğu için hesap yapılır, ama **gerekçesi her satırda görünür** ve son karar avukatındır.

---

## 1. Hesap gerekçesi (her satırda zorunlu)

Defterdeki ve rapordaki her son gün şu zincirle yazılır; eksik halka `[___]` kalır:

```
Başlangıç olayı: [tebliğ / tefhim / e-tebligat / ilan / öğrenme / sözleşme dönemi sonu] — [tarih] — [kaynak: mazbata, UYAP kaydı, kullanıcı beyanı]
Süre: [uzunluk ve birim, madde metninden aynen] — [dayanak, soorgla atfı]
Sayım: [hangi kanunun sayım kuralı] → işlemeye başladığı gün [tarih] → ham bitiş [tarih]
Tatil: [ham bitiş tatil mi? legal_check_holiday sonucu] → [uzama kuralı ve maddesi]
Adli tatil: [uygulanır / uygulanmaz / araç: "…"] → [uzama kuralı ve maddesi]
Son gün: [tarih, haftanın günü] — [araç / elle] — [sağlama: tuttu / ayrıştı: …]
```

Rapordaki "hesap gerekçesi" sütunu bunun tek satırlık özetidir: `Tebliğ 20.10.2026 → HMK 361 (araç) → 03.11.2026 Salı; tatil yok; sağlama tuttu`.

---

## 2. Başlangıç olayı

Hesap hatalarının çoğu sayımda değil **başlangıçta** olur. Her satırda başlangıç olayının türünü ve kaynağını yaz.

| Olay | Dikkat | Çek |
|---|---|---|
| Fiziki tebliğ (muhatabın kendisine ya da birlikte oturana) | Mazbatadaki tarih; kullanıcının "elime geçtiği gün"ü değil | `[kullanıcı verdi]` mazbata |
| Tebligat Kanunu m.21 (kapıya yapıştırma, muhtara bırakma) | İhbarnamenin kapıya yapıştırıldığı tarih tebliğ tarihidir; muhatabın muhtardan aldığı gün değildir | `legal_get_statute_article` `law_no: "7201"`, `article_no: "21"` |
| Elektronik tebligat (UETS) | Tebliğ, adrese ulaştığı günden sonraki belirli günün sonunda yapılmış sayılır; "okundu" tarihi değildir | `legal_get_statute_article` `law_no: "7201"`, `article_no: "7/a"` |
| Tefhim (yüze karşı karar açıklama) | Gerekçeli karar sonradan tebliğ ediliyorsa sürenin hangisinden başladığı kanuna göre değişir `[incele]` | ilgili kanun yolu maddesi |
| İlan (RG, gazete, ilan panosu) | İlan tarihi; ilan süresinin bitimi değil — maddeye bak | İYUK m.8/1; özel kanun |
| Öğrenme (idari işlem, haksız fiil, ayıp) | Öğrenme tarihi ispat konusudur; en erken savunulabilir tarihi esas al ve `[incele]` | ilgili alan becerisi |
| Sözleşme dönemi sonu (yenileme, fesih bildirimi) | Geriye doğru sayılır, bkz. `sozlesme-yenileme-ve-ihbar.md` | TBK m.92; sözleşme |
| Hâkimin verdiği süre | Ara kararın tefhimi ya da tebliği; süre kesin mi (HMK m.94)? | `[kullanıcı verdi]` tutanak |

Kullanıcı yalnız "geçen hafta tebliğ edildi" diyorsa tarihi uydurma: `son_gun: [HESAPLANACAK]`, eksik bilgi olarak sor. Bir aralık verildiyse (ör. "20-22 Ekim arası") **en erken** tarihle hesapla ve bunu yaz.

---

## 3. Sayım kuralı — hangi kanunun kuralı?

Sürenin dayandığı kanunun kendi sayım maddesi uygulanır. Kuralları ilk kullanımda MCP'den çek ve hesap gerekçesine maddeyi yaz.

| Yargı / alan | Sayım maddesi | Tatil maddesi | Adli tatil |
|---|---|---|---|
| Hukuk yargılaması (HMK) | 6100 m.92 | 6100 m.93 | 6100 m.102-104 |
| Ceza yargılaması (CMK) | 5271 m.39 | 5271 m.39/4 | 5271 m.331 |
| İdari yargı (İYUK) | 2577 m.8/1 | 2577 m.8/2 | 2577 m.8/3 ("çalışmaya ara verme") |
| İcra ve iflas (İİK) | 2004 m.19 | 2004 m.19; takip işlemleri için m.51 | İİK'da adli tatil hükmü yok; icra mahkemesi işleri ivedidir (İİK m.18/1), HMK m.103/1-h ile tatilde görülür, m.104 uzaması uygulanmaz → aşağıda 4. madde `[incele]` |
| Borçlar hukuku (sözleşme, ifa) | 6098 m.92 | 6098 m.93 (aksine anlaşma geçerli) | Uygulanmaz (usul süresi değil) |
| Elektronik işlem (UYAP) | 6100 m.445/4: süre gün sonunda biter | — | — |

Ortak noktalar (maddelerden çekilerek yazılır):
- Gün olarak belirlenen sürede başlangıç günü sayılmaz.
- Hafta, ay ve yıl olarak belirlenen süre, başladığı güne karşılık gelen günde biter; o ayda karşılık gelen gün yoksa ayın son günü.
- Son gün resmî tatile denk gelirse süre tatili izleyen ilk iş gününe uzar. Aradaki tatiller süreye dahildir.
- Fiziki işlemde süre son günün mesai/tatil saatinde, UYAP'ta gün sonunda biter. Son günün **saatini** rapora yaz.

TBK m.92/1'deki "sekiz veya on beş gün, bir veya iki hafta değildir" ayrımına dikkat: sözleşmede "15 gün" ile "2 hafta" farklı son gün verebilir.

---

## 4. Tatil kontrolü

- Ham bitişi ve uzama sonrası son günü `legal_check_holiday` ile kontrol et. Uzama sonrası gün de tatilse bir sonraki iş gününe kadar sürdür.
- **Arife:** dinî bayram arifeleri ve 28 Ekim öğleden sonra tatildir. `legal_check_holiday` arifeyi `yarim: true` ve "13.00'ten sonra tatil" açıklamasıyla işaretler; `legal_calculate_deadline` da son gün arifeyse uyarı yazar. Son gün bir arifeye denk geliyorsa satıra "son gün arife, öğleden sonra tatil; işi sabahtan bitirin" yaz `[incele]`. Fiziki teslimde bu gün fiilen yarım gündür.
- **Hafta sonu:** Cumartesi ve Pazar araçta tatil olarak döner. Mahkemenin ve idarenin çalışmadığı gün olduğu için uygulamada uzama sebebidir; özel bir kanun aksini öngörüyorsa `[incele]`.
- **İdari izin:** resmî tatil değildir, süre işler `[model bilgisi — doğrulayın]`.
- **Bayram tarihleri** (Ramazan, Kurban) her yıl değişir; ezberden yazma, araçtan al.

---

## 5. Adli tatil

Adli tatil her yargı kolunda **farklı** işler; aynı dosyada bile süre türüne göre değişebilir.

1. **Hukuk (HMK m.102-104).** Tatil başlangıç ve bitişini m.102'den çek. Süre işlemeye devam eder; yalnız **bitişi** tatile denk gelirse tatilin bittiği günden itibaren m.104'teki kadar uzar. m.103'te sayılan işler (geçici hukuki koruma, nafaka, işçinin açtığı davalar, ivedi işler vb.) **tatilde görülür; bu işlerde uzama uygulanmaz**. Dosyanın m.103 kapsamında olup olmadığını sor; emin değilsen uzamasız tarihi son gün kabul et ve `[incele]` yaz.
2. **Ceza (CMK m.331).** Tatile rastlayan süreler işlemez; tatilin bitiminden itibaren m.331/4'teki kadar uzamış sayılır. Tutuklu işler ve ivedi işler ayrıdır (m.331/2-3). **Araç (`cmk_appeal`, `cmk_cassation`) bu uzamayı uygulamıyor** (bilinen eksik): ham bitiş tatildeyse uzamayı elle hesapla, tutuklu/tutuksuz ayrımını sor, iki tarihi de yaz ve **erken olanı** son gün kabul et `[incele]`.
3. **İdari yargı (İYUK m.8/3).** "Çalışmaya ara verme" süresine rastlayan bitiş, ara vermenin sona erdiği günü izleyen tarihten itibaren maddedeki kadar uzar. Ara verme tarihlerini ve kapsamını İYUK m.61'den çek. **Dikkat:** m.61/1'e göre bölge idare mahkemesinin bulunduğu il merkezi dışında kalan ve tek idare ya da tek vergi mahkemesi bulunan yerlerdeki mahkemeler çalışmaya ara vermeden yararlanmaz; bu mahkemelerdeki işlerde uzama yoktur. Araç (`iyuk_appeal`) mahkemenin yerini bilmez ve uzamayı her durumda uygular: mahkemenin yerini sor, belirsizse uzamasız tarihi son gün kabul et `[incele]`.
4. **İcra.** İİK'da adli tatile özgü bir hüküm yoktur; İİK m.19 yalnız son günü resmi tatile rastlayan sürenin tatili izleyen günde biteceğini söyler. İcra mahkemesine arz edilen hususlar **ivedi işlerdendir** (İİK m.18/1); HMK m.103/1-h'ye göre kanunlarda ivedi olduğu belirtilen işler adli tatilde görülür ve HMK m.104'teki bir haftalık uzama yalnız "adli tatile tabi olan dava ve işlerde" uygulanır. Bu üç maddenin birlikte okunmasıyla icra mahkemesi işlerinde (şikâyet, itirazın kaldırılması, icra mahkemesine yapılan itirazlar) ve icra dairesi nezdindeki sürelerde (ödeme emrine itiraz vb.) adli tatil uzaması **uygulanmaz**; süreleri uzamamış say. Bu çıkarım kanun metninden; aynı sonucu doğrudan söyleyen içtihat bu turda okunmadı `[incele]`. İtirazın iptali gibi genel mahkemede görülen davalar icra mahkemesi işi değildir; onlar için 1. madde geçerlidir.
5. **Maddi hukuk süreleri** (hak düşürücü süre, zamanaşımı, sözleşme bildirimi) adli tatilden etkilenmez. Dava açma süresinin HMK m.104 kapsamına girip girmediği tartışmalıdır: uzamasız tarihi son gün kabul et, `[incele]`.

**Güvenli yön kuralı:** iki hesap ayrışıyorsa (uzamalı / uzamasız, araç / elle) defterde **erken tarih** son gün, geç tarih "olası uzama" notudur. Hiçbir zaman geç tarihi tek başına yazma.

---

## 6. Sürenin durması, kesilmesi, uzaması

Bunlar **esas değerlendirmesidir**; bu beceri yalnız defterde gösterir ve `[incele]` işaretler:
- **Zorunlu arabuluculuk:** başvurudan son tutanağa kadar zamanaşımı durur, hak düşürücü süre işlemez (iş uyuşmazlığında 7036 m.3/17; diğer dava şartı arabuluculuklarda 6325 sayılı Kanun — numara çakışabilir, `legal_search_statute_semantic` ile çek). Defterde ilgili satırı `durdu` durumuna al, son tutanak tarihi gelince yeniden hesapla.
- **Zamanaşımının kesilmesi** (TBK m.154: ikrar, dava, takip) zamanaşımını yeniden başlatır; yeni başlangıç tarihini alan becerisi belirler.
- **Hâkimin verdiği süre** (HMK m.94/2): kesin olduğu açıkça ihtar edilmemişse ikinci süre istenebilir; bu bir **güvence değildir**, defterde ilk süre son gündür.
- **Eski hâle getirme** ya da süre tutum: süre geçtikten sonra konuşulur; bu becerinin işi değildir.

---

## 7. `legal_calculate_deadline` kural kodları

Araç 01.11.2026'da ~70 kod tanıyor; aşağıdaki tablo sık kullanılan kanun yolu kodlarıdır. Bilinmeyen kod verilirse araç **geçerli kod listesini** (kod, ad, kanun, madde, süre, birim) döndürür; doğru kodu oradan seç, listede yoksa elle hesapla. Listede örneğin `iik_objection_payment_order` (İİK m.62), `iyuk_lawsuit`, `iyuk_tax_lawsuit`, `kik_complaint`, `labor_reinstatement_mediation`, `rent_eviction_notice_residential`, `aym_individual_application`, `statute_of_limitations_general` var; cevap süresi, bilirkişi raporuna itiraz ve kesin süre için kod yok.

| Kod | Araçtaki ad | Dayanak (araç) | Not |
|---|---|---|---|
| `hmk_appeal` | İstinaf Başvurusu (Hukuk) | HMK m.345 | Adli tatil uzaması uygulanıyor; m.103 işlerinde uygulanmaması gerekir — araç bunu bilmez `[incele]` |
| `hmk_cassation` | Temyiz Başvurusu (Hukuk) | HMK m.361 | aynı |
| `cmk_appeal` | İstinaf (Ceza) | CMK m.273 | Adli tatil uzamasını **uygulamıyor** (bkz. §5/2) |
| `cmk_cassation` | Temyiz (Ceza) | CMK m.291 | aynı |
| `iyuk_appeal` | İstinaf (İdari) | İYUK m.45 | Ara verme uzamasını her mahkeme için uyguluyor; İYUK m.61/1 istisnasını bilmez (§5/3). İvedi yargılama usulü ve özel kanun süreleri (ihale, seçim, 6458) farklıdır; araç bilmez `[incele]` |
| `iyuk_cassation` | Temyiz (İdari) | İYUK m.46 | aynı |
| `iik_complaint` | İcra Müdürü İşlemine Şikâyet | İİK m.16, 366 | Adli tatil etkisi yok |

Uzatma uygulandığında `uyarilar` alanı uzatmasız **"GÜVENLİ SON GÜN"**ü de yazar; m.103 işlerinde ve İYUK m.61/1 yerlerinde onu esas al.

**Araç sonucu nasıl okunur:** `baslangic_gun` (işlemeye başladığı gün), `ham_bitis`, `adli_tatil_etkisi`, `son_gun_tatil_mi`, `son_gun`, `kalan_gun`, `uyarilar`. `kalan_gun` aracın kendi "bugün"üne göredir; raporda kendi hesapladığın kalan günle karşılaştır. Araç **başlangıç olayının doğruluğunu, sürenin özel kanunla değişip değişmediğini, dosyanın adli tatilde görülen işlerden olup olmadığını** bilmez.

---

## 8. Sağlama (iki yoldan hesap)

Upstream `deadlines` öğrencinin hesabını "makullük bandı" ile sınar. Biz süre uzunluğunu beceriye yazmadığımız için bandın yerine **çift hesap** koyarız:

1. Araç sonucu (varsa).
2. Madde metninden elle sayım (bu dosyadaki §3-5).
3. Kullanıcı bir son gün verdiyse o da üçüncü hesaptır.

Üçü tutuyorsa sessizce yaz. Biri ayrışırsa dur ve göster:
> "Girdiğiniz son gün [tarih]; benim hesabım [tarih] (gerekçe: …). Fark [N] gün. Olası nedenler: başlangıç olayı (tebliğ türü), sayım kuralı, adli tatil. Hangisini esas alayım? Belirleyene kadar deftere **erken tarihi** yazıyorum `[incele]`."

Kullanıcının verdiği son gün daha geçse, deftere **onu yazma**; erken olanı yaz, kullanıcının tarihini notta tut (`ORTAK-KURALLAR.md` §6).
