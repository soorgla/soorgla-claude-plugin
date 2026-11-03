# Ödeme emrine itiraz (icraya itiraz)

Kişiye icra dairesinden **ödeme emri** (icra dairesinin "borcu öde ya da itiraz et" diye gönderdiği resmî kâğıt) gelmiştir. Bu dosya, avukat olmayan kişinin **süresi içinde** ve **doğru yere** itiraz etmesi için yazıldı.

**İlk iş: ödeme emrinin türünü bul.** Kâğıdın üstünde "Örnek No" yazar. Tür, sürenin kaç gün olduğunu ve itirazın nereye yapılacağını değiştirir.

| Ödeme emri | Takip | İtiraz nereye | Süre |
|---|---|---|---|
| **Örnek 7** (genel haciz yoluyla ilamsız takip) | Senetsiz alacak, fatura, sözleşme | **İcra dairesine** (dilekçe ya da sözlü) | **7 gün** (İİK m.62) |
| **Örnek 10** (kambiyo senetlerine özgü haciz yolu) | **Senet (bono), çek, poliçe** | **İcra mahkemesine** dilekçe | **5 gün** (İİK m.168) |
| **Örnek 13** (kira alacağı / tahliye ihtarlı) | Kira borcu | İcra dairesine | **7 gün** itiraz; ödeme süresi ayrıdır `[doğrula]` |

**Kâğıtta "senet", "bono", "çek", "kambiyo" ya da "Örnek 10" yazıyorsa** bu dosyadaki icra dairesi dilekçesi **yetmez**: itiraz 5 gün içinde **icra mahkemesine** yapılır. 🔴 avukat eşiği (aşağıda).

---

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Genel haciz ödeme emrine itiraz: **7 gün** | Ödeme emrinin **tebliği** | İİK m.62/1 | Süresinde itiraz takibi **durdurur** (m.66). Süre geçerse alacaklının talebiyle takip devam eder. |
| Kambiyo senedi takibinde borca, imzaya, yetkiye itiraz ve "senet kambiyo senedi değil" şikâyeti: **5 gün** | Ödeme emrinin tebliği | İİK m.168/3-5, m.170 | Mercii **icra mahkemesi**, icra dairesi değil. İmzaya itiraz satış dışındaki takip işlemlerini **durdurmaz**; mahkeme ciddi görürse geçici durdurma verebilir. |
| Gecikmiş itiraz: **3 gün** | Mazeretin (engelin) kalktığı gün | İİK m.65 | Hastalık, kaza gibi belgeli engel. 🔴 avukat eşiği. |
| Alacaklının itirazın kaldırılmasını isteme süresi: **6 ay** | İtirazın alacaklıya tebliği | İİK m.68/1 | Alacaklının elinde imzası ikrar edilmiş/noter onaylı borç ikrarı ya da resmî belge varsa. |
| Alacaklının itirazın iptali davası süresi: **1 yıl** | İtirazın alacaklıya tebliği | İİK m.67/1 | Süre geçse de alacaklı genel hükümlerle dava açabilir (m.67). |
| Borcu ödedikten sonra **istirdat** (geri alma) davası: **1 yıl** | Ödeme tarihi | İİK m.72/7 | 🔴 avukat eşiği. |

**Hesap:** `legal_calculate_deadline` `iik_objection_payment_order` kodu İİK m.62'ye göre 7 gün hesaplar ("Adli tatil bu süreyi ETKİLEMEZ"); kambiyo senedine dayalı takipteki 5 günlük süre için kod yok. Sağlama için ya da kambiyoda elle hesapla: tebliğ günü sayılmaz, ertesi gün 1. gündür; 7. (kambiyoda 5.) gün hafta sonu ya da resmî tatilse `legal_check_holiday` ile bak ve ilk iş gününe kaydır. `iik_complaint` kodunun dayanağı **İİK m.16 (şikâyet)** dır; itiraz için kullanma.

Adli tatilin itiraz süresine etkisi: **etkilemez.** Yargıtay 12. HD'ye göre icra dairelerinde ve icra mahkemelerinde adli tatil hükümleri (HMK m.102-104) uygulanmaz; İİK'daki bir sürenin son günü adli tatile rastlarsa süre o gün biter, bir hafta uzamaz. Kullanıcıya "20 Temmuz–31 Ağustos arasında da süre işliyor" de; yalnız son gün hafta sonu/resmî tatilse ilk iş gününe kayar.

E-tebligat ya da "tebliğ edilmiş sayılma" (Tebligat Kanunu m.21, e-Devlet adresine bildirim) tarihinin hangisi olduğu belirsizse **en erken tarihi** esas al.

---

## Zorunlu unsurlar ve kurallar (genel haciz, Örnek 7)

- İtiraz **dilekçe ile veya sözlü** olarak yapılır; takibi yapan dairede değilse **başka bir icra dairesine** de verilebilir, o daire itirazı yetkili daireye gönderir.
- Borçlu itirazla birlikte **yurt içinde bir adres** bildirmek zorundadır.
- **Kısmi itiraz:** borcun bir kısmına itiraz ediliyorsa itiraz edilen kısmın **cihet ve miktarı açıkça** gösterilir; gösterilmezse itiraz **edilmemiş sayılır**. Takip kabul edilen kısım için devam eder.
- **İmzaya itiraz:** takip bir senede dayanıyorsa ve imza borçluya ait değilse bu **ayrıca ve açıkça** yazılır; yazılmazsa takip yönünden imza **kabul edilmiş sayılır**.
- Genel haciz takibinde madde metni itiraz sebebi gösterilmesini şart koşmaz; "borcum yoktur" demek takibi durdurur. Ama sebep yazmak sonraki aşamada (itirazın kaldırılması/iptali) borçluya zarar verebilir ya da yarar sağlayabilir `[incele]`.
- **Yetkiye itiraz:** icra dairesinin yetkisizliği ileri sürülecekse yetkili daire gösterilmeli ve esasa ilişkin itirazla birlikte yapılmalıdır.
- İtiraz edildiğine dair **ücretsiz belge** alınır; mutlaka isteyin. İcra işlemleri UYAP üzerinden yürür ve elektronik ortamda yapılan işlemde süre gün sonunda biter (İİK m.8/a). UYAP Vatandaş/e-Devlet ekranında o dosya için itiraz seçeneği açıksa kullanılabilir; ekranı ve gönderim sonrası alındı kaydını kullanıcıya kontrol ettir. Emin değilsen ya da son gündeysen **icra dairesine dilekçeyle** ver ve ücretsiz itiraz belgesini al.
- **Ödeme emri henüz tebliğ edilmeden** (takibi başka yoldan öğrenip) itiraz: Yargıtay 12. HD çoğunluğu kira alacağına ilişkin **Örnek 13** takibinde tebliğden önce yapılan itirazın hukuki sonuç doğurmadığını kabul etti; karşı oy ve genel haciz takibine ilişkin farklı bir 12. HD kararı var. Güvenli yol: **ödeme emri tebliğ edildikten sonra süresi içinde yeniden itiraz edin.**

## 🔴 Avukat eşikleri

Aşağıdakilerden biri varsa kullanıcıya **açıkça** "tek başınıza ilerlemeniz risklidir" de; taslağı yalnızca süreyi kurtarmak için ver ve adli yardım bürosunu hatırlat:

1. **Senet/çek takibi (Örnek 10).** İtiraz icra mahkemesine 5 günde yapılır; imzaya itiraz haksız çıkarsa borçlu takip konusu alacağın **en az %20'si inkâr tazminatı** ve **%10'u para cezasıyla** sorumlu tutulabilir (takip itirazla durdurulmuşsa).
2. **İmzaya itiraz (her takipte).** Sahte imza iddiası bilirkişi incelemesi, ceza boyutu (resmî/özel belgede sahtecilik) ve tazminat riski taşır. Genel haciz takibinde de alacaklı itirazın kaldırılmasını isterse imza incelemesi yapılır; imza borçluya ait çıkarsa tazminat ve para cezası riski vardır.
3. **Haksız itiraz riski.** Borç gerçekten varsa ve itiraz yalnız zaman kazanmak içinse: alacaklı itirazın kaldırılmasını ya da itirazın iptalini kazanırsa borçlu **en az %20 tazminat** ödeyebilir. Kullanıcıya bunu sade dille söyle: "Borcunuz varsa itiraz etmek size ek borç olarak dönebilir."
4. **Menfi tespit / istirdat davası** düşünülüyorsa (borcu ödemek zorunda kaldınız ama borçlu değilsiniz; ya da takip başlamadan önlem almak istiyorsunuz). Teminat ve tedbir koşulları teknik; avukatın değerlendirmesi için `../../icra-iflas/references/menfi-tespit-istirdat-ve-ihtiyati-haciz.md`. 1.9.2023 ve sonrasında açılan ticari (TTK m.5/A) ve işçilik (7036 m.3/1) menfi tespit ve istirdat davalarında arabuluculuk dava şartıdır; kira ilişkisinden doğuyorsa 6325 m.18/B.
5. **Süre geçti** ya da tebliğ tarihi belirsiz (gecikmiş itiraz, tebligat usulsüzlüğü şikâyeti).
6. **Tahliye** istenen kira takibi (Örnek 13/14): ev ya da işyeri kaybı riski.
7. Takip tutarı kullanıcı için **yüksek** ya da birden çok takip var.

## Görüşme soruları

1. Ödeme emrinin üstünde "Örnek" numarası ne yazıyor? (7 / 10 / 13 / bilmiyorum)
2. Ödeme emri size **hangi tarihte** ulaştı? Nasıl? (postacı, e-tebligat, kapıya yapıştırma, komşuya bırakma)
3. İcra dairesinin adı ve **dosya numarası** (Örn. "… İcra Dairesi 2026/____ Esas").
4. Alacaklı kim? Takip tutarı ne kadar?
5. Takip neye dayanıyor? (fatura, sözleşme, senet, çek, kira, kredi kartı, telefon faturası)
6. Borcun **tamamına** mı itiraz ediyorsunuz, bir **kısmına** mı? Kısmi ise kabul ettiğiniz ve itiraz ettiğiniz tutarlar.
7. Senet/çek varsa: üstündeki **imza size mi ait**?
8. Borcu ödediniz mi, ödediyseniz belgesi var mı? Zamanaşımı ya da başka bir neden var mı?
9. İkametgâhınız takibin yapıldığı şehirden farklı mı? (yetki itirazı)
10. Adınız-soyadınız, T.C. kimlik no, **yurt içi tebligat adresiniz**.

## soorgla çağrıları

```
legal_get_statute_article law_no: "2004" article_no: "62" | "66" | "65" | "67" | "68" | "72"
legal_get_statute_article law_no: "2004" article_no: "168" | "170" # senet/çek takibi
legal_get_statute_article law_no: "2004" article_no: "269" # kira takibi (çek ve kontrol et)
legal_check_holiday tarih: <son gün>
legal_search_cases mahkeme: "yargitay" daire: "12. Hukuk Dairesi"
    sorgu: "<olay, ör. kısmi itirazda miktar gösterilmemesi itiraz edilmemiş sayılır>"
    tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar> # alıntı-önerme kontrolü
legal_get_social_parameters tur: "harc_basvurma_sulh" # icra mahkemesine başvuru harcı
```
İcra hukukunda Yargıtay **12. Hukuk Dairesi** çok sayıda karar veriyor (yukarıdaki künyeler). Daire görev dağılımını sabit sayma; şüphede `legal_case_facets` ya da güncel Yargıtay BGK kararıyla kontrol et (sıra cetveli, iflas ve konkordato 6. HD'ye, ticari itirazın iptali/menfi tespit 11. HD'ye gidebilir; ayrıntı `icra-iflas`).

## İskelet — genel haciz ödeme emrine itiraz (Örnek 7)

```
[___] İCRA DAİRESİ MÜDÜRLÜĞÜ'NE

DOSYA NO : [___]/[___] Esas

İTİRAZ EDEN (BORÇLU) : [Ad Soyad], T.C. No: [___]
Adres (tebligat) : [yurt içi adres]

ALACAKLI : [Ad Soyad / Unvan]

KONU : Tarafıma [tebliğ tarihi] tarihinde tebliğ edilen ödeme emrine itirazlarımın
       sunulmasıdır.

AÇIKLAMALAR :
1. Yukarıda numarası yazılı dosyadan tarafıma ödeme emri [tebliğ tarihi] tarihinde
   tebliğ edilmiştir. İtirazım süresindedir.
2. [Tam itiraz:] Alacaklıya takip konusu borcum bulunmamaktadır. Borca, faize, faiz
   oranına, tüm ferilerine ve takibin tamamına itiraz ediyorum.
   [Kısmi itiraz:] Takip konusu [toplam] TL'nin [kabul edilen] TL'lik kısmını kabul,
   [itiraz edilen] TL'lik kısmına ve bu kısma ilişkin faiz ve ferilerine itiraz ediyorum.
3. [Senede dayalı ise ve imza ait değilse — AYRICA VE AÇIKÇA:] Takibe dayanak belgedeki
   imza tarafıma ait değildir; imzaya açıkça itiraz ediyorum.
4. [Yetki itirazı varsa:] İcra dairesi yetkili değildir; yetkili icra dairesi [___]
   İcra Dairesi'dir.

SONUÇ VE İSTEM : Süresinde yaptığım itirazımın kabulü ile İİK m.66 uyarınca takibin
durdurulmasını arz ve talep ederim.

                                                    Tarih : [___]
                                                    Ad Soyad / İmza
```

Kambiyo senedi (Örnek 10) için bu iskelet **kullanılmaz**: başlık "[___] İCRA HUKUK MAHKEMESİ'NE", taraflar "davacı/borçlu – davalı/alacaklı", istem "itirazın kabulü ile takibin durdurulması / iptali". Harç ve masraf yatırılır. Bu dilekçeyi avukatla hazırlamayı öner; avukata ulaşılamıyor ve süre doluyorsa taslağı `[incele]` işaretleriyle ver.

## Sık hatalar

- Senet/çek takibinde icra dairesine itiraz etmek (doğrusu: 5 gün, icra mahkemesi).
- Kısmi itirazda tutarı yazmamak → itiraz edilmemiş sayılır.
- İmzaya itirazı "borca itiraz ediyorum" cümlesinin içine gömmek → imza kabul edilmiş sayılır.
- Tebliğ gününü süreye saymak ya da son günü tatile denk geldiği hâlde kaydırmamak (ya da tersine, tatil olmayan günü kaydırmak).
- İtiraz belgesini almamak.
- Borç varken yalnız zaman kazanmak için itiraz edip %20 tazminat riskini göze almak.
- Eski YAML'daki gibi "Borca itiraz takibi her durumda durdurur" demek: kambiyo takibinde imzaya itiraz satış dışındaki işlemleri durdurmaz (m.170).
