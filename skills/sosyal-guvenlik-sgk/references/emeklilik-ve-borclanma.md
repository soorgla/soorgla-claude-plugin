# Emeklilik, aylıklar, statü ve yurt içi borçlanma

**Ne zaman kullanılır:** "ne zaman emekli olurum", EYT'den yararlanma, yaşlılık/malullük/ölüm aylığı şartları, 4A/4B/4C statü çakışması, askerlik-doğum-staj gibi yurt içi borçlanmalar, aylığın kesilmesi ya da Kurumun "yersiz ödeme" borcu çıkarması. Yurt dışı hizmet → `yurtdisi-borclanma.md`; eksik/kayıt dışı hizmet → `hizmet-tespiti.md`.

**Temel ilke:** hangi rejimin uygulandığını önce belirle. Sonuç; ilk sigorta giriş tarihine, statüye (4/1-a, b, c), prim gün sayısına ve yaşa bağlıdır. Bu becerinin çıktısı **şart tablosudur**, kesin emeklilik tarihi değildir: her sonuç `[doğrula — SGK hizmet dökümü ile]`.

---

## Süre ve yol tablosu

| Konu | Kural | Dayanak |
|---|---|---|
| Kuruma karşı her talep (aylık bağlanması, statü, borçlanma, başlangıç tarihi, yersiz ödeme itirazı) | Önce Kuruma yazılı başvuru; 60 gün cevapsızlık = ret; sonra iş mahkemesi | 7036 m.4/1; 5510 m.101 |
| Yurt içi borçlanma bedelinin ödenmesi | Borcun tebliğinden itibaren **1 ay**; ödenmezse yeni başvuru gerekir, ödenmeyen süre hizmetten sayılmaz | 5510 m.41 |
| Borçlanmayla aylığa hak kazanılırsa aylık başlangıcı | Borcun ödendiği tarihi takip eden ay başı | 5510 m.41 |
| Yersiz ödemenin geri alınması | Kişinin kast/kusurundan doğduysa tespit tarihinden geriye **en fazla 10 yıl**, ödeme tarihlerinden kanuni faizle; Kurum hatasından doğduysa geriye **en fazla 5 yıl**, tebliğden itibaren 24 ay içinde ödenirse faizsiz; aylıktan kesinti oranı maddede | 5510 m.96 |

`legal_calculate_deadline` bu süreleri hesaplamaz; elle hesapla, `[doğrula]`.

---

## Kontrol listesi

### 1. Rejim ve statü 🔴
- **İlk sigorta giriş tarihi** (hizmet dökümünden; yurt dışı/askerlik borçlanması başlangıcı geri çekmiş olabilir — aşağıda 4).
  - 01.10.2008 (5510'un yürürlüğü) sonrası ilk giriş → 5510 m.28.
  - Öncesi giriş → 506 geçici m.81 (4/1-a), 1479 geçici m.10 (4/1-b), 5434 (4/1-c) ile 5510 geçici maddeleri.
- **Statü çakışması (5510 m.53):** 4/1-c ile (a) ya da (b) çakışırsa önce **(c)**; (a) ile (b) çakışırsa **(a)** esas alınır. (a) esas alınan kişi yazılı talepte bulunup diğer statüde de prim ödeyebilir. Eski `social_security_sgk` tanımındaki "4A önceliklidir" ifadesi eksikti: (c) hepsinden önce gelir.
- **Şirket ortağı:** 4/1-b kapsamındakiler kendilerine ait ya da ortak oldukları işyerlerinden 4/1-a sigortalı bildirilemez. Hangi ortakların 4/1-b sayıldığı (limited/anonim ortaklık, yönetim kurulu üyeliği) `[incele]`.
- **Aylık bağlamada esas statü:** 5510 sonrası ilk girişlilerde birden fazla statüde çalışılmışsa en fazla sigortalılığın geçtiği statü; eşitlikte ve bazı hâllerde son statü. 5510 öncesi girişlilerde (5510 yürürlüğünden önce sigortalı/iştirakçi olup sonra aylık isteyenler) birden fazla statü varsa aylığa esas kanun **mülga 2829 sayılı Kanun** hükümlerine göre belirlenir (5510 geçici m.2, sondan bir önceki fıkra); 2829'un kuralını (ör. son yedi yıl ölçütü) bu beceride ezberden uygulama — 2829 soorgla madde kaydında yok, kuralı kullanıcı belgesi, SGK genelgesi (`legal_search_admin_guidance` `kurum: "Sosyal Güvenlik Kurumu"`, `sorgu: "2829 hizmet birleştirme son yedi yıl"`) ya da 10. HD kararından teyit et; bulamazsan `[ARAŞTIRMA GEREKLİ: 2829 statü kuralı]`.

### 2. Yaşlılık aylığı şartları
- **5510 sonrası ilk giriş (m.28/2):** kadın 58, erkek 60 yaş ve 9.000 gün; 4/1-a için 7.200 gün. Yaş hadleri 2036'dan itibaren kademeli artıp 2048'de 65'e ulaşır; kişinin **prim gün şartını doldurduğu tarihteki** yaş haddi uygulanır.
- **Kısmi aylık (m.28/3):** yaş hadlerine 3 yıl eklenmek (en fazla 65) ve en az 5.400 gün.
- **Engelli, ağır engelli çocuk annesi, yer altı maden, erken yaşlanma:** m.28'in diğer fıkraları (ör. %50-59 kayıp oranında 16 yıl/4.320 gün; %40-49'da 18 yıl/4.680 gün; ağır engelli çocuğu olan kadına prim gününün dörtte biri eklenir).
- **Talep şartları:** 4/1-a sigortalının işten ayrılması, 4/1-b'nin faaliyete son verip vermeyeceğini beyan etmesi ve **GSS dahil prim borcunun olmaması**. 4/1-b'de borç → aylık bağlanmaz 🔴 (borç yapılandırma/ödeme planı çıkar).
- **5510 öncesi girişli 4/1-a (506 geçici m.81):** 23.05.2002 tarihindeki sigortalılık süresine göre kademeli yaş, sigortalılık süresi (kadın 20, erkek 25 yıl) ve 5.000-5.975 gün; (C) bendinde 15 yıl + 3.600 gün + yaş seçeneği. Tablo çok satırlı: maddeyi çek, kişinin satırını alıntıla, hesabı tablo hâlinde göster.

### 3. EYT — 5510 geçici m.95 (7438 s. Kanun, RG 03.03.2023)
- 506 geçici m.81/B, 1479 geçici m.10/2, 2925 geçici m.2/1-B ve 5434 geçici m.205 hükümlerine göre aylık bağlanacak olanlar, bu hükümlerdeki **yaş dışındaki şartları** (sigortalılık süresi ve prim günü) taşıyorlarsa yaş şartı aranmadan aylık alır.
- **Pratikte kapsam:** 08.09.1999 (4447'nin yürürlüğü) öncesi ilk girişliler. "08.09.1999" eşiği maddenin kendisinde yazmaz; atıf yapılan geçici maddelerden gelir — çıktıda bunu böyle açıkla.
- **Geriye dönük hak yok:** madde esas alınarak geriye dönük ödeme yapılmaz, geriye dönük hak talep edilemez.
- **(C) bendi (yaş + 15 yıl + 3.600 gün) EYT kapsamında değildir**; madde yalnız (B) bendini sayar. 🟠
- EYT ile emekli olup 30 gün içinde aynı özel sektör işyerinde SGDP'ye tabi çalışmaya başlayan için işverene 5 puan SGDP indirimi (geçici m.95/2) → `sgk-uyum-ve-itiraz.md`.
- Eski görev tanımlarındaki "EYT kapsamı" anlatımı 7438 öncesi tartışmalara dayanıyordu; yalnız bu madde metnini esas al.

### 4. Yurt içi borçlanma (5510 m.41)
- Borçlanılabilen süreler: doğum/analık (3 doğuma kadar, her doğum için doğumdan sonraki en fazla 2 yıl; kadının o sürede uzun vadeli sigortalı olmaması ve çocuğun yaşaması şartı), askerlik (er/erbaş, yedek subay okulu), 4/1-c'nin aylıksız izni, doktora/tıpta uzmanlık, avukatlık stajı, beraatla sonuçlanan tutukluluk/gözaltı, grev-lokavt, kısmi süreli çalışmanın eksik süreleri ve diğerleri.
- Bedel: talep tarihindeki prime esas günlük kazanç alt ve üst sınırı arasında kişinin seçtiği kazancın, doğum borçlanmasında %32'si, diğerlerinde %45'i. Tutarı hesaplarken asgari ücreti `legal_get_social_parameters` ile çek; üst sınır katı m.82'den.
- **Başlangıç tarihine etkisi:** sigortalılık başlangıcından önceki süreler borçlanılırsa başlangıç, borçlanılan gün sayısı kadar geriye götürülür. Bu, 5510 öncesi girişli sayılmayı ve EYT'yi etkileyebilir 🟠; askerlik borçlanmasının, özellikle 5510 öncesi (506 dönemi) borçlanmalarda başlangıç tarihini geri çekip çekmediğini kesin bilgi gibi yazma: güncel 10. HD kararını `legal_search_cases` (`daire: "10. Hukuk Dairesi"`, `sorgu: "askerlik borçlanması sigortalılık başlangıç tarihi geriye gitmesi"`) ile ara, en az birinin tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: askerlik borçlanmasının başlangıca etkisi]` yaz.
- Borçlanılan sürenin hangi statüde sayılacağı m.41 dördüncü fıkrada (doğum ve askerlik: borçlanma tarihindeki statü).

### 5. Malullük ve ölüm aylığı
- **Malullük (m.26):** malul sayılma (m.25), en az 10 yıl sigortalılık + 1.800 gün (başkasının bakımına muhtaç malulde süre aranmaz, 1.800 gün yeter), işten ayrılma ve yazılı istek; 4/1-b'de prim borcu olmaması.
- **Ölüm aylığı (m.32):** ölen sigortalının en az 1.800 gün **ya da** 4/1-a için (borçlanmalar hariç) en az 5 yıl sigortalılık + 900 gün; ya da aylık alırken/hak kazanmışken ölmesi; 4/1-b'de prim borcu olmaması şartı hak sahipleri için de geçerli. Hak sahiplerinin payları ile çocuk şartları (yaş/öğrenim sınırı, malullük, evli olmayan kız çocuğu) `legal_get_statute_article 5510 m.34`'ten çekilir, oranları ezberden yazma. Hak sahibinin 5510 öncesi mevzuata tabi olduğu durumlarda geçici maddelerdeki farklı kurallar ve son yıllarda yetim aylığına ilişkin değişiklik olup olmadığı `legal_search_official_gazette` (`query: "5510 sayılı yetim aylığı"`, `document_type: "kanun"`, `date_from`) ile kontrol edilir `[doğrula]`.
- İş kazası kaynaklı maluliyet → `is-kazasi-ve-rucu.md` (gelir ve aylık birleşmesi `[incele]`).

### 6. Aylık bağlandıktan sonra
- **Yeniden çalışma:** önce ilk giriş tarihine bak. **5510 sonrası ilk girişli** yaşlılık aylığı alan, 4/1-a (ya da yabancı ülke mevzuatı) kapsamında çalışmaya başlarsa aylığı izleyen ödeme dönemi başında **kesilir** ve tüm sigorta kollarına prim alınır (m.30/3-a); 4/1-b kapsamında başlarsa aylık yalnız yazılı talep üzerine kesilir (m.30/3-b). **5510 öncesi girişli** aylık sahiplerinde aylık kesilmeden **sosyal güvenlik destek primi (SGDP)** ödenerek çalışma geçici m.14'te düzenli; ayrıntı ve 4/1-b istisnası için maddeyi çek `[incele]`.
- **En düşük aylık ve ikramiye tutarları** kanunla sık değişir (5510 ek m.19: 7539 ile 14.469 TL, 7590 ile 23.552 TL; ek m.18 bayram ikramiyesi 7546 ile değişti). Tutarı beceriye yazma; her seferinde `legal_search_official_gazette` (`query: "5510 sayılı Kanunun ek 19"`, `date_from`) ile son değişikliği çek.
- **Yersiz ödeme / borç çıkarılması:** borcun kaynağı kişinin kusuru mu Kurum hatası mı? Geriye gidiş süresi ve faiz buna göre değişir (m.96). Kurum hatasıysa 5 yıl sınırı ve 24 ay faizsiz ödeme imkânı 🟠. 7036 m.4 başvurusu ve iş mahkemesi.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "5510" article_no: "28" | "25" | "26" | "32" | "34" | "41" | "53" | "82" | "96"
legal_get_statute_article law_no: "5510" article_no: "geçici 95" # EYT
legal_get_statute_article law_no: "506" article_no: "geçici 81" # 5510 öncesi 4/1-a kademeleri
legal_get_statute_article law_no: "1479" article_no: "geçici 10" # 5510 öncesi 4/1-b
legal_get_statute_article law_no: "7036" article_no: "4"
legal_search_statute_semantic sorgu: "<ör. 5510 öncesi girişlilerin aylık bağlanmasında son statü>" mevzuat_no: "5510"
legal_search_official_gazette query: "5510 sayılı" document_type: "kanun" date_from: "<son 2 yıl>" sort_by: "date_desc"
legal_search_cases mahkeme: "yargitay" daire: "10. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. askerlik borçlanması sigorta başlangıç tarihi geriye götürülmesi yaşlılık aylığı>"
legal_get_case_document belge_id: "<seçilen karar>"
legal_get_social_parameters tur: "asgari_ucret_brut"
```

---

## Görüşme soruları

1. Doğum tarihi ve cinsiyet?
2. İlk sigorta giriş tarihi (hizmet dökümüne göre) ve statüsü?
3. Statü bazında toplam prim günü (4/1-a, 4/1-b, 4/1-c ayrı ayrı)?
4. Askerlik, doğum, yurt dışı ya da başka borçlanma yapıldı mı / yapılabilir mi?
5. Şu anda çalışıyor mu, hangi statüde? Şirket ortaklığı var mı?
6. 4/1-b ise prim ve GSS borcu var mı?
7. Engellilik oranı, ağır engelli çocuk, yer altı madenciliği gibi özel durum?
8. Kurumdan gelen bir ret ya da borç yazısı var mı; tebliğ tarihi?
9. Hedef: en erken emeklilik tarihi mi, aylık tutarı mı, borçlanmaya değer mi?

## Çıktı iskeleti

```markdown
## Emeklilik değerlendirmesi: [kişi] — [tarih]
### Sonuç (şart tablosu; kesin tarih değildir)
### Uygulanan rejim
[5510 m.28 / 506 geçici m.81 bendi / EYT geçici m.95 — gerekçesiyle]
### Şart tablosu
| Şart | Gereken | Mevcut | Eksik | Kaynak |
| Yaş | | | | |
| Sigortalılık süresi | | | | |
| Prim günü | | | | |
| Borç yokluğu (4/1-b) | | | | |
### Borçlanma seçenekleri ve etkisi [doğrula]
### Riskler (statü, borç, işten ayrılma zamanı)
### Kuruma başvuru ve yol
### Eksik bilgi
```

## Sık hatalar

- 🔴 5510 sonrası girişliye 506 geçici m.81 tablosunu uygulamak ya da tersi.
- 🔴 4/1-b sigortalıda prim/GSS borcunu kontrol etmeden "emekli olabilirsiniz" demek.
- 🔴 Hizmet dökümünü görmeden işten ayrılmayı önermek.
- 🟠 506 geçici m.81/C (15 yıl + 3.600 gün) kişisini EYT'li saymak.
- 🟠 Statü çakışmasında 4/1-c önceliğini atlamak.
- 🟡 Borçlanma bedelinin 1 ay içinde ödenmesi gerektiğini söylememek.

---
