# Dosya açma (`ac`)

Kaynak: upstream `litigation-legal/matter-intake` ve `matter-workspace new`. Türk hukukuna uyarlandı: çıkar çatışması kapısı Av.K. m.38'e bağlandı; ABD'deki "legal hold", "materiality/reserve", "outside counsel budget" adımları yerine delil koruma, vekaletname yetkileri ve (yalnız şirket içi kullanıcıda) karşılık notu kondu.

Amaç: her dosya aynı sorularla açılsın ki portföy karşılaştırılabilir olsun; dizin satırı özeti, kart ise satırın taşıyamadığı anlatıyı tutar.

---

## 0. Hazırlık

- Profili oku: rol, çalışma biçimi, çıkar çatışması satırı, dosya klasörü yeri.
- `_liste.yaml`'ı oku: kısa adın tekil olduğunu doğrula (`_kapali/` dahil). Aynı ad kapalı dosyada varsa yeni ad iste (ör. sonuna `-2`).
- MCP ön kontrolü: `legal_get_statute_article` (`law_no: "1136"`, `article_no: "38"`). Yanıt gelirse `soorgla ✓` ve kapı metnini buradan alıntıla.
- Kullanıcı başlangıç belgesini (dava dilekçesi, tebligat, ödeme emri, ihtarname, arabuluculuk daveti) verdiyse önce onu oku; görüşme sorularının çoğu oradan dolar. Okuduğunu **Okunan** satırına yaz.

## 1. Kimlik

- Müvekkil (ya da kod), karşı taraf(lar), karşı taraf vekili
- Konu (tek satır) ve **alan becerisi** (`is-hukuku`, `kira-hukuku` … ; uymuyorsa "genel")
- **Rolümüz:** davacı / davalı / alacaklı / borçlu / müdafi / katılan vekili / başvurucu / danışmanlık. Profilde ağırlıklı taraf varsa öner, onaylat; yoksa sor. Varsayma.
- Merci ve numaralar: mahkeme ya da birim, esas no, UYAP birimi; dava öncesiyse arabuluculuk bürosu ya da savcılık no.
- Kaynak: `müvekkil başvurusu | tebligat | ödeme emri | ihtarname | arabuluculuk daveti | soruşturma ifadeye çağrı | iç bildirim`

## 2. Çıkar çatışması kapısı

Bu adım beceri bir çatışma olup olmadığına **karar vermek** için değil, kontrolün yapıldığından ve kaydın tutulduğundan emin olmak içindir.

Dayanak: Av.K. m.38 avukatın işi reddetmek zorunda olduğu hâlleri sayar; m.38/b "aynı işte menfaati zıt bir tarafa avukatlık etmiş veya mütalaa vermiş" olmaktır ve zorunluluk "avukatların ortaklarını ve yanlarında çalıştırdıkları avukatları da kapsar" `[soorgla]`.  TBB Meslek Kuralları soorgla'da yok; çıkar çatışması ve karşı tarafla görüşme kurallarını bu becerinin bilgisiyle yazma, barobirlik.org.tr'deki güncel metinden teyit et ve dosya notuna "TBB Meslek Kuralları — elle teyit edildi / edilmedi" diye işle `[incele]`. 

Kaydedilecekler: **durum**, **yöntem**, **kontrol eden**, **tarih**, **kontrol edilen adlar** (karşı taraf, bilinen bağlı şirketler, karşı taraf vekili, temel tanıklar; ince liste olur, boş olmaz), **not**.

Kullanıcı isterse yardımcı adım: yeni dosyadaki adları `_liste.yaml`'daki `taraflar_cc` alanlarıyla karşılaştır ve **olası eşleşmeleri** listele. Yalnız dizini oku; eşleşen dosyanın klasörünü açma. Sonucu "olası eşleşme — karar sizin" diye ver; büronun kendi sistemi varsa asıl kontrol odur.

Duruma göre:

- `temiz` → devam.
- `uygulanmaz` → avukat olmayan kullanıcının kendi işi ya da tek müvekkilli şirket içi kullanım. Gerekçesi tek satır.
- `sorunlu` → **dur.** Av.K. m.38 hâllerinden biri olabilir. Dosya açılmaz; "Bu iş için m.38 kapsamında ret zorunluluğu doğabilir; karar avukatındır `[incele]`" de. Avukat çatışma olmadığını yazılı gerekçeyle belirtirse `temiz` ya da `bekliyor` ile yeniden başla.
- `bekliyor` → yalnız profil "paralel açılışa izin: evet" diyorsa. Kontrolü kim yapıyor, ne zaman dönecek, hangi adlar — üçü de yazılır. Kart ve dizin satırı bayrak taşır; her `guncelle`, `brifing` ve `portfoy`'da yeniden hatırlatılır.
- `yapılmadı` → **KAPI. Kart, günlük ve dizin satırı yazılmaz.** Üç yol:
  1. **Şimdi yap:** açılışı duraklat; kontrol bitince `temiz` ile dön.
  2. **Bekliyor olarak işaretle:** yalnız profil paralel açılışa izin veriyorsa; sorumlu ve tarih zorunlu.
  3. **Gerekçeli atla:** kullanıcı açıkça kabul ederse. `cikar_catismasi.atlama` alanına kim, tarih, gerekçe yazılır. Bu kayıt her portföy özetinde görünür ve beceri onu hiçbir zaman kendiliğinden silmez; ancak kullanıcı kontrol yapıldıktan sonra elle kaldırır.

  "Sonra bakarım" kabul edilmez; üç yoldan biri seçilir ve seçim kayda geçer.

## 3. Gizlilik sınıfı

| Sınıf | Ne zaman | Sonucu |
|---|---|---|
| standart | Olağan ticari, kira, alacak, iş dosyası | Olağan kurallar |
| yüksek | KVKK m.6 özel nitelikli veri (sağlık, cinsel hayat, ceza mahkûmiyeti, sendika üyeliği, biyometrik veri …) içeren dosya; aile, şiddet (6284), çocuk; kamuoyu bilinen kişi | Dizinde müvekkil adı yerine kod; kısa adda ad yok; brifing ve portföy özetinde ad yerine kod; çıktıları paylaşmadan önce sor |
| çok yüksek | Ceza soruşturması ve müdafilik, iç soruşturma, birleşme/satın alma, ihbarcı (whistleblower), aynı büroda birbirine yakın müvekkiller | "yüksek"tekilere ek: dosyalar arası bağlam profilde açık olsa bile bu dosya için kapalı; dosya içeriği alan becerisi dışındaki becerilere (ör. müvekkil mektubu) yalnız kullanıcının açık isteğiyle aktarılır |

Özel nitelikli verinin tanımı KVKK m.6/1'den alınır `[soorgla]`.  Gizlilik sınıfını avukat seçer; beceri yalnız önerir ve gerekçesini yazar.

## 4. Vekaletname ve yetki

- Vekaletname var mı, tarihi, noteri, yevmiye no, genel/özel.
- HMK m.74'teki özel yetkiler vekaletnamede açıkça var mı: sulh, feragat, kabul, ibra, davanın tamamını ıslah, tahkim, alternatif uyuşmazlık çözüm yoluna başvuru, tevkil `[soorgla]`.  Bilinmiyorsa "kontrol edilmedi" yaz; arabuluculuk ve sulh aşamasında `guncelle` bu satıra bakar.
- Ücret sözleşmesi var mı (yalnız varlığı ve yeri; tutarı karta yazma).

## 5. Süreler ve delil koruma

- Bilinen ilk süreyi sor: cevap süresi, itiraz süresi, kanun yolu süresi, arabuluculuk son tutanağından sonra dava süresi, zamanaşımı.
- Son günü `sure-takibi` becerisine hesaplat. Yüklü değilse: kanun yolu ve İİK şikâyeti için `legal_calculate_deadline` (`hmk_appeal`, `hmk_cassation`, `cmk_appeal`, `iik_complaint`); diğerleri için süreyi ilgili madde metninden çek, elle hesapla, `legal_check_holiday` ile kontrol et ve `[doğrula]` işaretle (bilinen eksikler: `dosya-guncelle.md` §4).
- Son güne 7 günden az kaldıysa ya da geçmişse kartın ve özetin en üstüne 🔴.
- **Delil koruma** (ABD "legal hold"un yerine; Türk hukukunda genel bir saklama emri kurumu yoktur `[model bilgisi — doğrulayın]`): müvekkile yazışma, e-posta, mesaj, kamera kaydı, bordro gibi delilleri silmemesini ve saklamasını hatırlat; kaybolma tehlikesi varsa delil tespiti talebini düşün → esas alan becerisi, dilekçe `hukuk-yargilamasi-dilekce` (delil tespiti). Bunu karta "Yapılacaklar" maddesi olarak yaz.

## 6. Risk ve ilk tez

- Risk: avukatın yargısı. Beceri yalnız 🔴/🟠/🟡/🟢 ölçeğini (ORTAK-KURALLAR.md §8) hatırlatır; profilde ölçek tanımı yoksa "kaba değerlendirme" diye not düşer, kesinlik taklidi yapmaz.
- Şirket içi kullanıcıda isteğe bağlı: finans birimine bildirilecek bir karşılık (dava karşılığı) konusu var mı `[incele]`. Tutar uydurulmaz.
- İlk tez: kullanıcının anlattığı; beceri tez kurmaz. Etiket: `[incele] — açılıştaki tez çalışma hipotezidir; dilekçe ya da müvekkil yazışmasında bu çerçeveye dayanmadan önce avukat teyit etsin`.

## 7. Yazma

1. Kartı (`sablonlar.md` §1), günlük tohumunu (§2), boş `notlar.md`'yi ve dizin satırını (§4) hazırla.
2. **Kullanıcıya göster:** "Şunu yazacağım; eksik ya da yanlış olan var mı?"
3. Onay gelince yaz. Klasör yoksa oluştur.
4. Profili değiştirme; sor: "`<kisa-ad>` dosyasına şimdi geçeyim mi?"

## 8. Çıktı ve karar ağacı

Kısa onay mesajı: kısa ad, klasör yolu, çıkar çatışması durumu, ilk süre ve son günü (etiketiyle), gizlilik sınıfı. Ardından ORTAK-KURALLAR.md §8 karar ağacı, bu adıma göre:

> **Şimdi ne yapalım?**
> 1. **Esası değerlendir** — `[alan becerisi]` ile ilk analiz (etkin dosyadan okur)
> 2. **Süreyi kesinleştir** — `sure-takibi` ile son gün ve tatil kontrolü
> 3. **Olay çizelgesi** — elimizdeki belgelerden `dava-kronolojisi`
> 4. **Eksik bilgiyi topla** — müvekkile sorulacaklar listesi
> 5. **Başka bir şey**

## Bu adım ne yapmaz

- Çıkar çatışması kontrolünü kendisi yürütmez; kayıt tutar ve kapı kurar.
- Tez uydurmaz, riski kendisi atamaz.
- Delil saklama talimatını müvekkile göndermez; taslağını önerir.
