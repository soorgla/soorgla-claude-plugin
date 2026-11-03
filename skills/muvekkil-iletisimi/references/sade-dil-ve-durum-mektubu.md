# Sade dil ve dosya durum mektubu

Uyarlama: Anthropic `legal-clinic/status` (client ve internal kipleri), `legal-clinic/client-letter` (rutin yazışma şablonları), `legal-clinic/plain-language-letters` (yönlendirme) ve `legal-clinic/CLAUDE.md` sade dil standartları (Apache 2.0). ABD hukuk kliniğine özgü öğeler (öğrenci-avukat imza kuralı, pedagoji kipi, profesör kuyruğu) çıkarıldı; yerine büro içi onay (sorumlu avukat / ortak) kondu.

---

## 1. Okuyucu kimdir?

Müvekkil çoğu zaman tedirgindir, yargılama sürecini bilmez ve mektubu birkaç kez okur. Mektup ona üç şeyi sağlamalıdır: **ne olduğunu anlamak, ne yapacağını bilmek, avukatına güvenmek.**

| Okuyucu | Ne ister | Ne istemez |
|---|---|---|
| Gerçek kişi müvekkil (işçi, kiracı, mirasçı, sanık) | Ne oldu, ne zaman biter, ne yapmalıyım, ne kadar tutar | Madde numarası yığını, içtihat tartışması, Latince |
| Şirket yetkilisi (genel müdür, patron) | Risk, tutar, karar gereken nokta | Usul ayrıntısı → E kipi (`is-birimi-ozeti.md`) |
| Şirket içi hukukçu (müvekkil şirketin) | Usul durumu, sonraki işlem, bütçe | Sadeleştirilmiş dil — hukukçuya hukukçu dili |
| Ortak / kıdemli avukat (iç not) | Usul durumu, karar gereken nokta, stajyerin değerlendirmesi | Müvekkil üslubu → §5 |

Profilde ya da kullanıcı mesajında okuyucu belli değilse **tek soru** sor: "Bu mektup kime gidiyor: müvekkilin kendisine mi, şirket yöneticisine mi, şirketin hukukçusuna mı?"

---

## 2. Sade dil kuralları ve denetim listesi

Hedef: lise mezunu bir okurun tek okumada anlaması. Profilde "okuma düzeyi" ya da "yasaklı ifadeler" tanımlıysa onlar geçerlidir.

**Denetim listesi** (Adım 5'te her mektuba uygulanır; bulgu avukat notuna yazılır):

- [ ] Cümle ortalama 15-20 sözcük; 30 sözcüğü geçen cümle bölünür.
- [ ] Paragraf en fazla 4 cümle.
- [ ] Her hukuki terim ilk geçtiği yerde tek cümleyle açıklanır (aşağıdaki tablo).
- [ ] Edilgen yerine etken çatı: "dilekçe tarafımızca ibraz edilmiştir" değil "dilekçeyi verdik".
- [ ] Tarihler gün adıyla: "**12 Kasım 2026 Perşembe**". "Tebliğden itibaren iki hafta" değil, hesaplanmış son gün.
- [ ] Tutarlar rakamla ve TL ile; "takriben", "cari tarife" yok.
- [ ] Müvekkilden istenen her şey ayrı madde, son tarihiyle.
- [ ] "Sonuç vaadi" taraması: `kotu-haber-ve-sonuc-vaadi.md` §1 listesindeki ifadelerden hiçbiri yok.
- [ ] Madde numarası en fazla birkaç tane ve konusu yazılmış ("Türk Borçlar Kanunu'nun kira artışını düzenleyen 344. maddesi").
- [ ] İç anlatım yok ("X becerisiyle inceledim", "soorgla'dan çektim").
- [ ] Müvekkilin bilmediği üçüncü kişilerin kişisel verisi (tanık adresi, karşı tarafın sağlık bilgisi) gerekmedikçe yok.

**Kaçınılacak kalıplar** (yerine yazılacak):

| Kaçın | Yaz |
|---|---|
| mezkûr, işbu, müracaat, ikame etmek, tevdi | bu, başvuru, açmak, vermek |
| "… hususunun tarafınıza bildirilmesi" | "Size … bildirmek isterim" |
| "dava ikame edilmiş olup …" | "Davayı açtık." |
| "HMK 345 uyarınca istinaf süresi tefhimden itibaren işlemekte olup" | "Karara itiraz etmek (istinaf) için son gün **3 Kasım 2026 Salı**." |
| "lehe/aleyhe" | "sizin lehinize / aleyhinize (sizin isteğinizi kabul eden / reddeden)" |
| "müddeabih", "ıslah", "feragat" | açıklamasıyla: aşağıdaki tablo |

**Terim çeviri tablosu** (ilk geçişte parantez içinde açıklama):

| Terim | Sade açıklama |
|---|---|
| Arabuluculuk | Dava açmadan önce tarafsız bir arabulucu önünde anlaşma görüşmesi; bazı davalarda zorunlu |
| Ön inceleme duruşması | Hâkimin tarafları ve delilleri ilk kez topluca ele aldığı duruşma |
| Bilirkişi raporu | Mahkemenin uzman kişiye hazırlattığı rapor (hesap, kusur, değer); hâkimi bağlamaz ama çok etkilidir |
| Bilirkişi raporuna itiraz | Rapordaki hata ve eksikleri mahkemeye yazılı bildirme; kısa süresi vardır |
| İstinaf | İlk kararın bir üst mahkemede (bölge adliye mahkemesi) yeniden incelenmesi |
| Temyiz | İstinaf kararının Yargıtay'da incelenmesi; her dava için açık değildir |
| Kesinleşme | Karara karşı başvuru yolu kalmaması; bundan sonra karar değişmez |
| Islah | Davadaki talebi (çoğu zaman tutarı) davanın içinde artırma ya da düzeltme |
| Feragat / kabul | Davadan vazgeçme / karşı tarafın isteğini kabul etme |
| Tebligat / tebliğ | Resmî evrakın size ya da avukatınıza usulüne göre ulaştırılması; çoğu süre bu günden başlar |
| İcra takibi / ödeme emri | Alacağın icra dairesi eliyle istenmesi / borçluya gönderilen ödeme talimatı |
| Haciz | Borç için mala ya da hesaba el konulması |
| Vekâlet ücreti (karşı taraf) | Davayı kaybeden tarafın, kazanan tarafın avukatı için ödemeye mahkûm edildiği ücret |
| Yargılama gideri | Harç, tebligat, bilirkişi, tanık giderleri |
| Duruşma ertelendi | Bu duruşmada karar çıkmadı; yeni tarih verildi |
| Gerekçeli karar | Kararın nedenlerinin yazılı olduğu tam metin; çoğu itiraz süresi bunun tebliğinden başlar |
| HAGB (ceza) | Hükmün açıklanmasının geri bırakılması: belli süre suç işlenmezse karar hiç yokmuş gibi olur |
| Tedbir | Dava sürerken mahkemenin verdiği geçici koruma kararı |

Tabloda olmayan bir terim kullanılıyorsa aynı biçimde açıkla; açıklayamıyorsan kullanma.

---

## 3. Durum mektubu (A kipi) — iskelet

**Zorunlu içerik:** ne oldu · sırada ne var ve ne zaman · sizden ne istiyoruz (son tarihli) · süre işliyorsa ilk paragrafta · masraf doğuyorsa tutar ve kimin ödeyeceği · nasıl ulaşırsınız.

**Yazılmayanlar:** hukuki analizin tamamı (müvekkil isterse ayrı görüşme), davanın zayıf yanlarının ilk kez bir durum mektubunda açılması (bu bir **görüşme** konusudur, `kotu-haber-ve-sonuc-vaadi.md` §2), karşı taraf avukatı hakkında kişisel yorum, kesin sonuç ve kesin süre tahmini.

Avukat notu (müvekkile gitmez) ve ardından gidecek metin:

````markdown
### Müvekkile gidecek metin

```
Konu: [Mahkeme adı] [Esas no] — dosyanızdaki son gelişme

Sayın [Ad Soyad],

[SÜRE İŞLİYORSA — İLK PARAGRAF:]
Önemli: [ne için] son gün **[gün ay yıl, gün adı]**. Bu tarihe kadar
[sizden istenen karar / belge / onay] gerekiyor.

**Ne oldu?**
[Tek-iki cümle, etken çatı. Ör.: "12 Ekim'deki duruşmada mahkeme bilirkişiden
ek rapor istedi; karar bu duruşmada çıkmadı."]

**Sırada ne var?**
[Ne ve ne zaman. Ör.: "Bir sonraki duruşma 18 Şubat 2027 Perşembe saat
10.30'da. Bu duruşmaya gelmeniz gerekmiyor; biz katılacağız."
Kesin tarih yoksa: "Mahkemenin yeni tarih vermesini bekliyoruz. Bu genellikle
birkaç hafta sürer; kesin bir süre söylemek mümkün değil."]

**Sizden istediklerimiz**
- [Belge / bilgi / karar] — **[son tarih]** — [neden gerekli, tek cümle]
[Yoksa: "Şu an sizin yapmanız gereken bir şey yok. Gerektiğinde size yazacağız."]

**Masraf** [yalnız masraf doğuyorsa]
[Ne için, yaklaşık ne kadar, kim ödüyor, ne zamana kadar. Ayrıntı:
ucret-ve-masraf-bilgilendirmesi.md]

Sorularınız için [telefon / e-posta / çalışma saatleri] üzerinden bana
ulaşabilirsiniz.

Saygılarımla,
Av. [Ad Soyad]
[Büro adı] | [Baro sicil no — profil] | [Telefon] | [E-posta]
```
````

**Kararın lehe çıktığı durumda** bile şunlar yazılır: kararın henüz kesinleşmediği, karşı tarafın itiraz (istinaf/temyiz) yoluna gidebileceği ve bunun ne zamana kadar belli olacağı; paranın tahsili ayrı bir aşama ise (icra) bunun da süre ve masraf gerektirdiği. "Davayı kazandık, paranız geliyor" yazılmaz.

---

## 4. Rutin yazışma (B kipi)

Rutin yazışma **esasa ilişkin görüş içermez.** Taslak sırasında "bu dosyada şunu yapmalısınız" türü bir tavsiyeye kayarsa A ya da C kipine geç.

### 4.1 Randevu / görüşme teyidi

```
Sayın [Ad Soyad],

[Tarih, gün adı] saat [saat]'te [büro adresi / görüntülü görüşme bağlantısı /
telefon] ile görüşmemizi teyit ederim.

Lütfen yanınızda getirin:
- [Belge 1 — ör. kira sözleşmesinin aslı]
- [Belge 2 — ör. size gelen ihtarname ve zarfı]
- Nüfus cüzdanınız

Görüşmeyi değiştirmeniz gerekirse lütfen en az bir gün önce [telefon] numarasından
haber verin.

Saygılarımla,
Av. [Ad Soyad]
```

### 4.2 Belge isteme

```
Sayın [Ad Soyad],

Dosyanızda ilerleyebilmemiz için aşağıdaki belgelere ihtiyacımız var:

- [Belge] — [neden: ör. "mahkemenin istediği ücret bordroları"]
- [Belge]

**Son tarih: [gün ay yıl, gün adı].** [Varsa neden: "Mahkemenin verdiği
kesin süre [tarih]'te doluyor; belgeleri ondan önce mahkemeye vermemiz gerekiyor.
Süre kaçarsa bu delile dayanma hakkı kaybedilebilir."]

Belgeleri [büroya getirerek / e-posta ile / KEP ile] iletebilirsiniz.
Elinizde olmayan bir belge varsa ya da ne istediğimiz açık değilse lütfen
arayın; nereden alınabileceğini birlikte bulalım.

Saygılarımla,
Av. [Ad Soyad]
```

"Süre kaçarsa hak kaybı" cümlesi yalnız alan becerisi ya da madde metni bunu gösteriyorsa yazılır; dayanağı avukat notunda etiketiyle durur.

### 4.3 Kısa "yapıldı" bildirimi

```
Sayın [Ad Soyad],

Kısa bir bilgi: [tarih] günü [yapılan iş — ör. "işe iade davanızı İstanbul
Anadolu [__]. İş Mahkemesinde açtık"]. Dosya numarası: [___].

Sırada: [tek cümle — ör. "Mahkeme karşı tarafa dilekçemizi gönderecek; onların
cevabını bekliyoruz. Bu genellikle birkaç hafta sürer."]

Şu an sizin yapmanız gereken bir şey yok. Gelişme olduğunda size yazacağım.

Saygılarımla,
Av. [Ad Soyad]
```

### 4.4 Hatırlatma (müvekkil cevap vermediğinde)

İkinci hatırlatmadan sonra yazılı kanal (e-posta + KEP ya da iadeli taahhütlü) önerilir; süre işliyorsa sonucun müvekkile ait olacağı nazik ama açık yazılır. Avukatın işi bırakma kararı C kipidir.

---

## 5. İç durum notu (H kipi) — ortağa / kıdemli avukata

Okuyucu hukukçudur; sade dile çevirme yapılmaz. Başlık: ORTAK-KURALLAR.md §1 avukat başlığı.

````markdown
# Durum: [Müvekkil kısa adı] — [Konu] — [tarih]

**Sorumlu:** [ad] | **Aşama:** [arabuluculuk / dava öncesi / ön inceleme / tahkikat / karar / istinaf / icra]
**Mahkeme ve esas:** [___]

## Son durumdan bu yana
- [yapılan işler, tarihleriyle]

## Yaklaşan
| Tarih | Ne | Dayanak / kaynak | Kimin işi |
|---|---|---|---|

## Karar gereken noktalar
- [somut soru — ör. "Bilirkişi raporuna itiraz mı, ek rapor talebi mi?"]

## Müvekkil iletişimi
- Son temas: [tarih, kanal] · Bekleyen cevap: [var/yok] · Günlükte açık iş: [N]

## Değerlendirmem
[Bu bölümü taslak doldurmaz; stajyerin/avukatın kendi değerlendirmesidir.
Taslak yalnız iskeleti ve olguları hazırlar: "[Değerlendirmenizi yazın]"]
````

"Değerlendirmem" bölümünü model yazmaz; yazarsa iç not, yazanın düşüncesi gibi görünen bir model özeti olur.

---

## 6. Avukatı olan vatandaş için: "avukatınıza soru listesi"

Kullanıcı avukat değilse ve kendi avukatına yazmak istiyorsa ("avukatım bilgi vermiyor"), bu beceri mektup yazmaz; kısa, kibar bir **bilgi isteme e-postası** ve soru listesi hazırlar:

- Dosyanın son durumu ve bir sonraki duruşma / işlem tarihi
- İşleyen bir süre (itiraz, istinaf, belge sunma) var mı, son günü ne
- Sizden beklenen belge ya da karar
- Bugüne kadarki masraf ve beklenen masraf
- Yazılı avukatlık sözleşmesinin bir örneği (Av.K. m.163 `[soorgla]`)

Başlık: `ARAŞTIRMA NOTUDUR — HUKUKİ TAVSİYE DEĞİLDİR — HAREKETE GEÇMEDEN ÖNCE BİR AVUKATA DANIŞIN`. Avukat hakkında şikâyet ya da azil sorusu gelirse: baro başvuru yolunu `[model bilgisi — doğrulayın]` etiketiyle anlat, avukatın kusuru hakkında yargıda bulunma.

---

## 7. MCP adımları

| Adım | Çağrı |
|---|---|
| Kanun yolu son günü | `legal_calculate_deadline` (`hmk_appeal`, `hmk_cassation`, `cmk_appeal`, `iik_complaint`) |
| Diğer süreler | Alan becerisinin süre tablosu; yoksa `legal_get_statute_article` + elle hesap + `legal_check_holiday`, `[incele]` |
| Mektupta anılacak madde | `legal_get_statute_article` (mektupta sade biçimde, avukat notunda `[soorgla]` etiketiyle) |
| Sınır ve tutar (kesinlik sınırı, harç) | `legal_get_social_parameters` |

## Sık hatalar

- Süreyi mektubun ortasına gömmek. Süre her zaman ilk paragrafta.
- "Tebliğden itibaren iki hafta" yazmak; müvekkil tebliğ tarihini bilmez. Hesaplanmış son gün yaz.
- Lehe kararda "kazandık" deyip istinaf ve tahsil aşamasını yazmamak.
- İnceleme etiketini ya da `[soorgla]` etiketini müvekkil metnine bırakmak.
- Durum mektubunda ilk kez kötü haber vermek (önce telefon/görüşme; bkz. `kotu-haber-ve-sonuc-vaadi.md`).
