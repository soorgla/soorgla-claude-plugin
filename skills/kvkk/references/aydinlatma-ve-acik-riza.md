# Aydınlatma metni ve açık rıza metni

## Ne zaman kullanılır
- Kullanıcı aydınlatma metni, açık rıza metni, çerez bildirimi ya da pazarlama izni metni yazdırmak ya da mevcut metni denetletmek istiyor.
- "Açık rıza almamız gerekir mi?", "okudum onaylıyorum kutusu yeterli mi?", "SMS kampanyası için ne lazım?" soruları.
- Yeni bir veri işleme faaliyeti başlıyorsa önce `on-inceleme-ve-etki-degerlendirmesi.md` ile hukuki sebebi belirle, sonra buraya gel.

Temel ayrım: **aydınlatma** her veri işlemede yapılan tek taraflı bilgilendirmedir, onaya bağlanmaz; **açık rıza** yalnız başka işleme şartı yoksa başvurulan, ayrı alınan bir irade beyanıdır. İkisini tek metinde ve tek onayda birleştirmek bu alandaki en yaygın hatadır.

---

## Süreler ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| Aydınlatma zamanı | Kişisel veri **elde edilirken** | 6698 m.10/1 |
| Veri ilgili kişiden alınmadıysa | Elde edilmesinden itibaren makul sürede; iletişim için kullanılacaksa ilk iletişimde; aktarılacaksa en geç ilk aktarımda | Aydınlatma Tebliği m.6 |
| Amaç değişirse | Yeni amaç için veri işlemeden **önce** ayrıca aydınlatma | Aydınlatma Tebliği m.5/1-(b) |
| 2016 öncesi alınmış rızalar | Geçiş dönemi kuralı (1 yıl) çoktan bitti; eski rıza metinleri bugünkü ölçüyle yeniden değerlendirilir | 6698 geçici m.1/3 |

---

## Kontrol listesi — aydınlatma metni

1. **Asgari unsurlar** (m.10/1 ve Tebliğ m.4): (a) veri sorumlusunun ve varsa temsilcisinin kimliği; (b) işleme amaçları; (c) kimlere ve hangi amaçla aktarılabileceği; (ç) toplama yöntemi ve **hukuki sebebi**; (d) m.11 hakları. Biri eksikse 🔴.
2. **Hukuki sebep tek tek yazılmış mı?** "Kanun'un 5 ve 6. maddeleri kapsamında" gibi toplu ifade yetmez; her amaç için m.5/2 ya da m.6/3'teki hangi bendin dayanıldığı açıkça belirtilmeli. Kurul 2026/347 sayılı kararının ekindeki örnek hatalı metin tam olarak bu ifadeyi eleştiriyor.
3. **Amaçlar belirli mi?** "vb.", "ve benzeri amaçlarla", "ileride doğabilecek" gibi genel ve muğlak ifadeler yasak. 🟠
4. **Alıcı grupları ve aktarım amacı** yazılmış mı? "İlgilisi ile paylaşılır" yetmez.
5. **Toplama yöntemi**: otomatik / kısmen otomatik / veri kayıt sisteminin parçası olarak otomatik olmayan — hangisi?
6. **Onaya bağlanmış mı?** Metnin sonunda "okudum ve kabul ediyorum / onaylıyorum / açık rıza veriyorum" varsa 🔴: aydınlatma onaya bağlanamaz; Kurul'un önerdiği ifade "okudum ve anladım" yönündedir. Aydınlatmanın ispat yükü veri sorumlusundadır; okunduğunu gösteren kayıt saklanmalı.
7. **VERBİS ile tutarlılık**: kayıt yükümlüsü ise aydınlatmadaki kategoriler, amaçlar, alıcılar Sicile bildirilenlerle uyumlu mu?
8. **Dil**: anlaşılır, açık, sade; yanıltıcı ya da eksik bilgi yok.
9. **Katmanlı sunum** (kısa ilk katman + tam metin bağlantısı) uygulamada kabul görür ama tam metin erişilebilir olmalı. `[model bilgisi — doğrulayın]`
10. **Yurt dışı aktarım** varsa ayrıca yazılmalı; arızi aktarıma açık rızada "muhtemel riskler" bilgisi şart → `yurt-disi-aktarim.md`.

## Kontrol listesi — açık rıza

1. **Önce başka şart var mı?** m.5/2'deki şartlardan biri (kanunda öngörülme, sözleşmenin kurulması/ifası, hukuki yükümlülük, hakkın tesisi, meşru menfaat…) varsa açık rıza **istenmez**; gereksiz rıza istemek hem yanıltıcıdır hem rıza geri alınınca faaliyeti kilitler. 🟠
2. **Tanım unsurları**: belirli bir konuya ilişkin, bilgilendirmeye dayanan, özgür iradeyle açıklanan. Her biri ayrı test edilir.
3. **Hizmet şartına bağlanmış mı?** ("Rıza vermezseniz üyelik açılmaz") → özgür irade sorgulanır; "battaniye rıza" (tek onayla her amaca rıza) 🔴. `[incele]`
4. **Ayrı mı alınıyor?** Aydınlatma ile açık rıza ayrı ayrı yerine getirilmeli; aynı sayfada olsalar bile ayrı metin ve ayrı beyan.
5. **Güç dengesizliği**: işçi–işveren ilişkisinde açık rıza özgür irade bakımından şüphelidir; Kurul biyometrik mesai takibinde ve e-posta denetiminde rızayı birincil dayanak saymıyor. → `on-inceleme-ve-etki-degerlendirmesi.md`.
6. **Özel nitelikli veri**: 7499 sonrası m.6/3'te açık rıza dışında da şartlar var (ör. istihdam ve İSG'deki hukuki yükümlülük, sağlık hizmeti, hakkın tesisi). Eski metinlerdeki "sağlık verisi yalnız açık rızayla" kabulü bayattır. Her durumda Kurulun belirlediği yeterli önlemler şart (m.6/4). Hangi Kurul kararının yürürlükte olduğunu (2018/10 sayılı karar ya da 7499 sonrası yeni karar) ezberden yazma: `legal_search_official_gazette` (`query: "özel nitelikli kişisel veri yeterli önlemler"`, `institution: "Kişisel Verileri Koruma Kurulu"`, `sort_by: "date_desc"`) ve `legal_search_admin_guidance` (`kurum: "Kişisel Verileri Koruma Kurulu"`) ile en yeni kararı bul; bulamazsan `[ARAŞTIRMA GEREKLİ: yürürlükteki yeterli önlemler kararı]` yaz.
7. **Geri alma**: rızanın geri alınabileceği ve yolu yazılmış mı? `[model bilgisi — doğrulayın]`
8. **Kayıt**: rızanın ne zaman, hangi metinle, hangi kanaldan alındığı saklanıyor mu?

## Kontrol listesi — ticari elektronik ileti (SMS, e-posta, arama)

- Ticari elektronik ileti için **önceden onay** 6563 m.6'dan gelir; KVKK açık rızasından ayrı bir rejimdir. Esnaf ve tacirlere onaysız gönderilebilir; mevcut mal/hizmetin değişiklik, kullanım ve bakımına ilişkin iletiler için ayrıca onay gerekmez.
- Ödeme/üyelik sırasında "doğrulama kodu" bahanesiyle SMS kodu alıp bunu ticari ileti onayı ya da açık rıza saymak hukuka aykırı bulunmuştur. 🔴
- İYS (İleti Yönetim Sistemi) kaydı ve ret hakkı 6563 ikincil düzenlemesindedir `[model bilgisi — doğrulayın]`; ayrıntı için `legal_search_statute_semantic` (`sorgu: "ticari iletişim ve ticari elektronik iletiler yönetmelik ileti yönetim sistemi"`).

## Kontrol listesi — çerez

- Kesinlikle gerekli çerezler dışındaki (işlevsel, performans-analitik, reklam/pazarlama) çerezler için, açık rıza dışında bir işleme şartı yoksa açık rıza gerekir; rıza **opt-in** alınır — varsayılan ayar çerezlerin çalışmaması, ziyaretçinin onayıyla çalışmasıdır (önceden işaretli kutu olmaz). Kurumun çerez rehberi araçta yok; güncel rehberi kullanıcıdan ya da Kurum sitesinden iste `[doğrula]`.
- Çerezle yurt dışına aktarım (yabancı reklam/analitik sağlayıcı) → `yurt-disi-aktarim.md`.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Veri sorumlusu | Unvan, MERSİS/vergi no, adres, iletişim (KEP, e-posta); Türkiye'de yerleşik değilse temsilci? |
| Faaliyet | Metin hangi süreç için? (üyelik, e-ticaret, işe alım, çalışan, ziyaretçi, kamera, hasta) |
| Veri kategorileri | Hangi alanlar tek tek? (kimlik, iletişim, konum, işlem, görsel, sağlık, biyometrik…) |
| Amaçlar | Her veri kategorisi hangi amaçla? Pazarlama, profil çıkarma var mı? |
| Hukuki sebep | Her amaç için dayanılan şart (sözleşme, hukuki yükümlülük, meşru menfaat, açık rıza)? |
| Alıcılar | Kimlere aktarılıyor? (grup şirketi, kargo, ödeme kuruluşu, bulut, kamu kurumu) — yurt dışı var mı? |
| Toplama kanalı | Web formu, mobil uygulama, çağrı merkezi, kamera, matbu form? |
| Saklama | Ne kadar saklanıyor? Saklama-imha politikası var mı? |
| VERBİS | Kayıt yükümlüsü mü, kayıtlı mı? |
| Başvuru kanalı | İlgili kişi başvurusu nasıl alınacak? (yazılı, KEP, kayıtlı e-posta) |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "3" | "5" | "6" | "10" | "11"
legal_list_statute_articles law_no: "24454" include_content: true # Aydınlatma Tebliği
legal_get_statute_article law_no: "6563" article_no: "6" law_type: "Kanun"
legal_search_official_gazette query: "Kişisel Verileri Koruma Kurulunun" search_in: "title" sort_by: "date_desc"
legal_get_official_gazette_document url: "<2026/347 aydınlatma–açık rıza; 2025/1072 SMS doğrulama kodu>"
legal_search_admin_guidance sorgu: "Kişisel Verileri Koruma Kurulunun kararı aydınlatma yükümlülüğü <sektör>" kurum: "Kişisel Verileri Koruma Kurulu" tarih_baslangic: "<son 3 yıl>"
legal_search_statute_semantic sorgu: "<sektörel kanunda öngörülen işleme — ör. 5549, 1219, 5651>"
```

---

## Çıktı iskeleti — aydınlatma metni (dışa giden metin)

```markdown
[VERİ SORUMLUSU UNVANI] — [SÜREÇ ADI] KİŞİSEL VERİLERİN İŞLENMESİNE İLİŞKİN AYDINLATMA METNİ

1. Veri sorumlusu: [unvan, adres, MERSİS, iletişim; varsa temsilci]
2. İşlenen kişisel veriler ve amaçları:
   | Veri kategorisi | Veriler | Amaç | Hukuki sebep (6698 m.5/2-… ya da m.6/3-…) |
3. Toplama yöntemi: [kanal; otomatik / kısmen otomatik / otomatik olmayan]
4. Aktarım: | Alıcı grubu | Amaç | Hukuki sebep | Yurt dışı mı, dayanağı |
5. Saklama süresi: [süre ya da ölçüt]
6. Haklarınız (6698 m.11): [m.11'deki bentler]
7. Başvuru: [yöntem ve adres — Veri Sorumlusuna Başvuru Tebliğine uygun]

Bu metni okudum ve anladım. [yalnız okuma kaydı; onay/rıza değil]
```

## Çıktı iskeleti — açık rıza metni (ayrı)

```markdown
[VERİ SORUMLUSU] — [BELİRLİ KONU] İÇİN AÇIK RIZA BEYANI

[Aydınlatma metnine bağlantı]
[Rızanın konusu: hangi veri, hangi amaç, hangi alıcı — tek bir konu]
☐ Kabul ediyorum ☐ Kabul etmiyorum
[Rızayı geri alma yolu; rıza verilmemesinin hizmete etkisi yoksa bunu yaz]
```

## Çıktı iskeleti — mevcut metin denetimi

| # | Metindeki ifade | Sorun | Önem | Dayanak | Önerilen düzeltme (en küçük değişiklik) |
|---|---|---|---|---|---|

---

## Sık hatalar
- Aydınlatma metnine "okudum, onaylıyorum / açık rıza veriyorum" eklemek.
- Her şeyi açık rızaya dayandırmak (sözleşme ya da hukuki yükümlülük varken).
- Açık rızayı hizmet şartı yapmak; tüm amaçlara tek kutu.
- Hukuki sebebi toplu yazmak ("Kanun'un 5 ve 6. maddeleri").
- Özel nitelikli veride 7499 öncesi m.6 kurgusunu kullanmak.
- SMS doğrulama kodunu ticari ileti onayı saymak.
- Aydınlatma metnini VERBİS kaydıyla çelişkili bırakmak.
