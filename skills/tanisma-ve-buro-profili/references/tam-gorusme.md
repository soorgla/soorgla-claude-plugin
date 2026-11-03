# Tam kurulum

Upstream `cold-start-interview` (commercial, employment, litigation, legal-clinic, law-student) uyarlaması. Hedef 10-15 dakika. Kısa kurulumdaki 5 soru (bkz. `kisa-gorusme.md`) **Bölüm 0**'dır; profil zaten kısa kurulumla yazılmışsa Bölüm 0 tekrar sorulmaz, yalnız tek satırla teyit edilir: "Avukatsınız, işçi tarafında, İstanbul Anadolu'da çalışıyorsunuz; doğru mu?"

Bölümler role göre dallanır. Her bölümün başında önce **belge iste**: "Elinizde [örnek dilekçe / imza bloğu / büro yazım kuralları] varsa yapıştırın ya da dosya yolunu verin; okuyup yalnız eksikleri sorarım. Yoksa 'yok' deyin, tek tek soralım."

## Dallanma tablosu

| Kullanıcı türü | Bölümler |
|---|---|
| Avukat (serbest / küçük büro) | 0 → 1 → 2 → 3 → 4 → 5 → 6 → (7 alan bölümleri) |
| Avukat (orta-büyük büro) | 0 → 1 (onay zinciriyle) → 2 → 3 → 4 → 5 → 6 → 7 |
| Stajyer avukat | 0 → 1S (gözetim) → 2 → 3 → 5 → 6 |
| Şirket hukukçusu | 0 → 1Ş (şirket ve onay zinciri) → 2 → 3 → 4 → 5 → 6 → 7 |
| Kamu görevlisi | 0 → 1K (kurum ve birim) → 2 → 3 → 4 → 6 |
| Vatandaş / işletme sahibi / İK | 0 → 1V → 2 (yalnız dil ve uzunluk) → 6 |
| Mali müşavir / gümrük müşaviri | 0 → 1M (meslek) → 2M (yazı biçimi) → 3 (yalnız şablonlar) → 6 |
| Bilirkişi / sigorta tarafı | 0 → 1B (uzmanlık) → 2 → 3 (yalnız şablonlar) → 6 |
| Hukuk öğrencisi | 0 → 1Ö → 6 |

Bölüm sırası önerilir; kullanıcı "şunu atla" derse `[ATLANDI]` yaz ve geç.

---

## Bölüm 1 — Çalışma biçimi ve yükseltme

**Avukat (1):**
- Büro yapısı: tek başına mı, ortaklı mı, kaç avukat ve stajyer?
- Ne kadar iş: ayda kabaca kaç yeni dosya, en sık hangi işler? (yalnız ölçek; müvekkil adı değil)
- **Yükseltme / danışma.** "Bir değerlendirme sizin yetkinizi ya da rahatlığınızı aşınca — süre çok dar, ceza boyutu çıktı, tutar büyük — kime gider? Bir ad ya da rol söyleyin ya da 'kendim karar veririm'." Küçük büroda bu "kime danışırsınız" sorusudur (meslektaş, akademisyen, baro komisyonu); "kimse" de geçerli cevaptır.
- Otomatik yükseltme durumları: "Tutardan bağımsız olarak her zaman başkasının görmesini istediğiniz durumlar?" Örnek öner: süresi 7 günden az kalmış iş, hamile ya da sendika temsilcisi işçinin feshi, ceza soruşturması ihtimali, basına yansıyan dosya, kamu zararı.

**Stajyer (1S):** upstream `legal-clinic` gözetim modeli.
- Staj avukatının adı ya da rolü (profilde "Staj avukatı" satırı).
- Gözetim biçimi: (a) her taslak dışarı çıkmadan staj avukatına gider, (b) yalnız mahkemeye ve karşı tarafa gidenler, (c) haftalık toplantıda toplu. Hangisi seçilirse seçilsin dilekçe, ihtarname ve müvekkile giden metin "staj avukatı onayı bekliyor" işaretini taşır; bu işaret profil üzerinden kaldırılamaz.

**Şirket hukukçusu (1Ş):** upstream "What does your company do?" + paylaşılan şirket profili.
- Şirket ne iş yapar, kime, nasıl? İnternet sitesi bağlantısı yeterli. Sektör ve kabaca çalışan sayısı (iş hukuku eşikleri için; eşiğin kendisini beceri araçtan çeker).
- Faaliyet gösterilen iller / ülkeler; yabancı unsur var mı (yabancı ortak, yurt dışı satış)?
- Düzenleyici kurumlar: hangileri sizi denetliyor (ör. BDDK, Rekabet Kurumu, KVKK Kurumu, EPDK, SPK)? Açık soruşturma var mı (yalnız "var/yok", ayrıntı yazdırma)?
- Onay zinciri: hukuk müdürü → genel müdür → yönetim kurulu; tutar eşikleri büroya özgüyse yazılır.
- Dış avukatlar: hangi işler dışarı verilir? (Büro adı isteğe bağlı.)
- Yönetime giden özet: kim okur, ne uzunlukta?

**Kamu görevlisi (1K):**
- Kurum türü (bakanlık, belediye, il özel idaresi, üniversite, KİT, düzenleyici kurum, SGK…) ve birim (hukuk müşavirliği, ihale, personel, strateji, mali hizmetler, teftiş).
- Sıfat (harcama yetkilisi, gerçekleştirme görevlisi, ihale komisyonu üyesi, muhakkik…) — `kamu-mali-denetim-sayistay` ve `kamu-ihale` idare tarafı bunu okur.
- Kurum içi onay: hukuk müşavirliği görüşü ne zaman alınır? Hukukçu olmayan kamu görevlisinde hukuk müşavirliği "Avukat irtibatı"dır.

**Bilirkişi / sigorta tarafı (1B):**
- Bilirkişi: alan (aktüerya, trafik kusuru, maluliyet, araç hasarı), bilirkişilik bölgesi (il), ayda kaç rapor (ölçek). Rapor biçimi tercihleri (başlık, bölüm sırası) 3. bölüme şablon olarak.
- Sigorta tarafı: şirket mi eksper mi, branş (trafik/ZMSS, kasko, sağlık), ağırlıklı iş (hasar tespiti, ödeme, rücu, Tahkim), onay zinciri (hasar müdürü, hukuk birimi).
- İkisinde de ölçek çoksa süre defteri ve dosya klasörü.

**Mali müşavir / gümrük müşaviri (1M):**
- Unvan (SMMM, YMM, gümrük müşaviri) ve müşteri ya da beyanname ölçeği (birkaç / onlarca / yüzlerce).
- Ağırlıklı işler (profil şablonundaki listeden) ve uyuşmazlıklarda çalışılan avukat (ad isteğe bağlı).
- Sık hazırlanan metinler: uzlaşma talebi, itiraz dilekçesi, KDV iade dilekçesi, m.242 itirazı, BTB başvurusu… (3. bölüm şablon listesine).
- Ölçek onlarca ve üstüyse süre defteri ve dosya klasörü kurulumunu öner.
- Mali müşavirde ek: büro ili ve vergi dairesi, müşteri dağılımı (bilanço / işletme / serbest meslek), muhasebe programı ve entegratör (yalnız alışkanlık), beyanname takvimini nasıl izlediği, emin olmadığında kime danıştığı (YMM, vergi avukatı, oda).

**Meslek mensubu yazı biçimi (2M):** dilekçe biçimi yerine müşteriye giden yazının ve raporun biçimi (resmî ya da sade, madde işaretli, Word/PDF); imza bloğunda unvan ve oda adı (sicil numarası profilde tutulmaz, `[___]`). Elektronik işlemlerde UYAP yerine GİB İnternet Vergi Dairesi / e-Beyanname, SGK e-Bildirge, BİLGE kullanımı yalnız alışkanlık olarak sorulur; eklenti bunlara bağlanmaz.

**Vatandaş / işletme sahibi / İK (1V):**
- Bir avukatla çalışıyor musunuz? (Ad isteğe bağlı.) Yoksa ildeki baro adli yardım bürosu hatırlatılır.
- İK ise: kaç işyeri, hangi işkolları (yalnız ölçek).

**Hukuk öğrencisi (1Ö):** upstream `law-student`.
- Sınıf ya da hazırlık (HMGS, hâkimlik-savcılık, avukatlık stajı öncesi).
- Öğrenme biçimi: (a) **Sorgula beni** — soru sorarım, cevabı vermem, buldurtur, itiraz ederim; (b) **Önce anlat** — açıklarım, sonra sorarak kontrol ederim. Varsayılan seçilen; her oturumda değiştirilebilir.
- Kolay gelen, zor gelen ve "hep ertelediğim" ders.
- Kurallar (bir kez söyle): fakültenizin not verilen işlerde yapay zekâ kuralını öğretim elemanına sorun; gerçek dosya ayrıntısı yazmayın (bkz. `profil-sablonu.md` §3).

---

## Bölüm 2 — Üslup ve dilekçe biçimi

Önce: "Beğendiğiniz bir dilekçeniz var mı? Müvekkil adlarını ve dosya numaralarını silip yapıştırın; biçimi oradan çıkarırım." Örnek gelirse **kişisel veriyi profile taşımadan** şunları çıkar ve kullanıcıya göster:
- Merci başlığı yazımı, taraf bloğu sırası, bölüm başlıkları
- Açıklamalar numaralı mı, paragraflar ne uzunlukta
- Karar ve madde atıf biçimi (ör. "Yargıtay 9. HD, 2023/1234 E., 2024/5678 K., 12.03.2024 T.")
- Ton: sert, ölçülü, teknik
- Kapanış ve imza bloğu düzeni

Örnek yoksa sor (2-3 soruluk iki tur):
- Bölüm başlıkları ve sırası (öner: ORTAK-KURALLAR.md §13/5 sırası; "aynen mi, değişiklik var mı?")
- Karar atıf biçimi (öner: soorgla'nın döndürdüğü hazır atıf)
- İmza bloğu: "Ad soyad ve baro adı yazılsın mı? Baro sicil numarası, T.C. kimlik no ya da telefon **profilde tutulmasın** önerim; taslakta `[___]` kalır, siz son aşamada doldurursunuz. Yine de yazayım mı?"
- Müvekkile/yönetime giden yazı: resmî mi, sıcak mı, madde işaretli mi?
- Word mü, markdown mı?

Örnek ya da yazım kılavuzu gelmediyse sonunda öner: "İsterseniz bu biçim kurallarını ayrı bir 'büro yazım kılavuzu' metni olarak da yazayım; stajyerinize ya da ekibe verebilirsiniz."

## Bölüm 3 — Taraf, alanlar ve yer (Bölüm 0'ın derinleştirilmesi)

- Alan bazında taraf tablosu (Bölüm 0'da "ikisi de" dendiyse her ana alan için ayrı sor).
- "Hiç bakmadığınız alanlar?" — o alanda gelen soruya çıktı "uzman yönlendirmesi" notu ekler.
- Sık çalışılan adliyeler ve bölge adliye / bölge idare mahkemesi. Bilmiyorsa yazma; beceri gerektiğinde sorar.
- Sık muhatap kurumlar (SGK il müdürlüğü, vergi dairesi, belediye, icra dairesi).

## Bölüm 4 — Risk iştahı

> Genel tutumunuz hangisine yakın? (Bu, önerilerin sırasını ve tonunu değiştirir; bulguların önem derecesini **değiştirmez**.)
> 1. **Temkinli** — en güvenli yol önce; dar ama sağlam talepler
> 2. **Dengeli** — seçenekleri eşit gösterin, ben seçerim
> 3. **Atak** — savunulabilir en güçlü talebi önce yazın, riskleri yanında
- "Sizi en çok ne korkutur?" (ör. süre kaçırmak, harç eksikliği, ispat) — upstream "what keeps us up at night".
- Büroya/şirkete özgü eşikler (yasal eşik değil): "X TL üstü işler ortağa gider" gibi.

Tutarlılık kontrolü: "atak" + "her dilekçe ortağa gider" çelişki değildir (onay ayrı iş) ama "atak" + "hep en dar talep" çelişkidir; sor.

## Bölüm 5 — Şablonlar ve sık işler

- En sık hazırladığınız 3-5 belge? (ör. işe iade arabuluculuk başvurusu, ihtarname, icra takip talebi, cevap dilekçesi, istinaf.) Bunlar "Şimdi ne yapalım?" karar ağacında ilk seçenek olarak önerilir.
- Kendi şablonlarınız var mı, nerede? (Konumu yaz; içeriği profile kopyalama. Şablon içinde müvekkil bilgisi varsa kullanıcıyı uyar.)
- Upstream'deki "seed documents" (10-20 belge) beklentisi burada yoktur; 1-3 temizlenmiş örnek yeterlidir. Örnek alınmadıysa profilde "Örnek dilekçe/yazı alındı mı: hayır" yazar; dilekçe becerileri genel iskeletle çalışır.

## Bölüm 6 — Elektronik işlemler ve bağlantılar

- UYAP: Avukat Portal / Vatandaş Portal / kullanılmıyor; e-imza ya da mobil imza var mı?
- UETS elektronik tebligat adresi var mı? Baro levhasına yazılı avukatlar ve özel hukuk tüzel kişileri için elektronik tebligat zorunludur (Tebligat K. m.7/a) [soorgla]; tebliğ, adrese ulaştığı tarihi izleyen beşinci günün sonunda yapılmış sayılır [soorgla]. Bu bilgi süre hatırlatmalarında kullanılır; profile yalnız "var/yok" yazılır.
- UYAP'tan elektronik işlemde süre gün sonunda biter (HMK m.445/4) [soorgla] — dilekçe becerileri bu hatırlatmayı UYAP kullanıcısına ekler.
- KEP: var mı? İşveren tarafında işçiye KEP ile bildirim uygulaması (ORTAK-KURALLAR.md iş hukuku bölümündeki alan) burada sorulur.
- Bağlantı kontrolü sonucu (SKILL.md Adım 2) bu bölümde gösterilir ve tabloya yazılır.

## Bölüm 7 — Alan bölümleri (isteğe bağlı)

"Ana alanlarınızdan biri için ayrıntılı ayar yapmak ister misiniz? Ör. iş hukukunda işçi sayısı, TİS, KEP ile bildirim, fesih öncesi inceleme kuralı. 3-4 dakika sürer; atlarsanız beceri ilk kullanımda sorar."

- **İş hukuku** ana alansa → ORTAK-KURALLAR.md "Büro profili" şablonundaki `## İş hukuku` alanları (ağırlıklı taraf, işçi sayısı ve aynı işkolundaki işyerleri, sektör, TİS ve sendika, KEP ile bildirim, alt işveren, disiplin yönetmeliği, fesih öncesi inceleme kuralı, otomatik yükseltme bayrakları). İşçi sayısı eşiği söylenirse 4857 m.18'den kontrol et [soorgla].
- **Sözleşme** ana alansa → "Sözleşme playbook'unu şimdi kuralım mı?" Evetse `sozlesme-incelemesi-tbk/references/genel-inceleme-ve-playbook.md` §1'deki 5 soruluk kurulumu oradan yürüt; şablon o dosyadadır, buraya kopyalanmaz.
- Diğer alanlar için bölüm açma; alan becerisi ihtiyaç duyduğunda kendi alanını profile önerir (kullanıcı onayıyla).

---

## Yazmadan önce: yeniden okuma

Upstream "before writing — re-read" kuralı. Bütün cevapları sırayla yeniden oku:
1. **Çelişki:** iki cevap birbirini tutmuyor mu? İkisini göster, hangisinin geçerli olduğunu sor.
2. **Kayan ayrıntı:** bir ad, şehir, eşik bölümler arasında değişti mi? Son değeri teyit et.
3. **Önemli boşluk:** özellikle rol, avukat irtibatı (avukat olmayan için), staj avukatı (stajyer için), yükseltme kişisi. Eksikse adıyla söyle.

Sonra SKILL.md Adım 4 (boşluk listesi, cevap bekle) → Adım 5 (yaz) → Adım 6 (kapanış).

## Ton

Meraklı ve sıcak; form doldurtan biri değil, ilk gününde doğru soruları soran yeni bir ekip arkadaşı. "Lütfen belirtiniz" yerine "Nasıl çalışıyorsunuz?" Kısa cevaba bir kez takip sorusu sorulabilir ("'temkinli' — süre ve usulde mi, talep tutarında mı?"); üstelemeyin, gerisi gerçek bir işte sorulur.
