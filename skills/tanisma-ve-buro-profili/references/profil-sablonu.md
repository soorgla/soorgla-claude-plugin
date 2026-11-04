# Profil şablonu ve alanların anlamı

Upstream `company-profile-template.md` (paylaşılan şirket profili) ile paket başına "practice profile" dosyalarının tek dosyada birleşmiş hâli. Mevcut ORTAK-KURALLAR.md "Büro profili" şablonunun **genişletilmiş** sürümüdür: oradaki alan adları (`Rol`, `Avukat irtibatı`, `Çalışma biçimi`, `## İş hukuku`, `## Dosya (müvekkil) çalışma alanları`) aynen korunur, böylece mevcut beceriler okumaya devam eder.

## İşaretler

| İşaret | Anlamı | Becerinin davranışı |
|---|---|---|
| `[DOLDURULACAK]` | Şablon hiç doldurulmamış | Alan yok sayılır |
| `[VARSAYILAN]` | Kısa kurulumda sorulmadı, varsayılan kondu | Varsayılan kullanılır; çıktı "varsayılan kullanıldı, profil ayarı: X" diyebilir |
| `[ATLANDI]` | Kullanıcı bilerek atladı | Alan yok sayılır; gerekirse beceri o anda sorar |
| `[BEKLİYOR]` | Kurulum duraklatıldı, henüz sorulmadı | Alan yok sayılır; kurulum devamında sorulur |
| `[Kullanılmıyor]` | Kullanıcı alanı kapattı (bölüm silinmez) | Alan yok sayılır, beceri sormaz |

---

## 1. Şablon

````markdown
# soorgla-hukuk profili
*Oluşturma: [TARİH] · Son güncelleme: [TARİH] · Kurulum: [kısa | tam]*
*Bu dosyayı doğrudan düzenleyebilirsiniz. Eklentideki her beceri iş yapmadan önce okur. Müvekkil adı, dosya numarası ya da olay ayrıntısı YAZMAYIN.*

## Kim kullanıyor
- Rol: [Avukat/hukukçu | Meslek mensubu (SM/SMMM/YMM, gümrük müşaviri, bilirkişi) | Avukat olmayan, avukata erişimi var | Avukat olmayan, avukata erişimi yok]
- Kullanıcı türü: [Avukat | Stajyer avukat | Şirket hukukçusu | Kamu görevlisi (hukukçu) | Kamu görevlisi (hukukçu değil) | Vatandaş / işletme sahibi | İK / danışman | Mali müşavir (SM/SMMM/YMM) | Şirket finans/muhasebe ekibi | Gümrük müşaviri | Bilirkişi | Sigorta eksperi / hasar birimi | İhale danışmanı | Hukuk öğrencisi | Diğer: …]
- Avukat irtibatı: [avukat olmayan için kişi/büro/kurum hukuk müşavirliği; yoksa "yok"]
- Staj avukatı: [yalnız stajyer için; yoksa "—"]
- Çalışma biçimi: [Serbest avukat/küçük büro | Orta-büyük büro | Şirket içi hukuk | Kamu kurumu | Adli yardım/CMK | Bireysel kullanım | Öğrenim]
- Kurum/büro: [isteğe bağlı; yalnız kullanıcı isterse — ad yazılmadan da çalışır]

## Taraf
- Varsayılan taraf: [Genelde talep eden (davacı/alacaklı/başvurucu) | Genelde karşı taraf (davalı/borçlu/idare) | İkisi de, her dosyada sor]
- Alan bazında:
  | Alan | Ağırlıklı taraf |
  |---|---|
  | İş | [işçi | işveren | ikisi] |
  | Kira | [kiracı | kiraya veren | ikisi] |
  | İcra | [alacaklı | borçlu | ikisi] |
  | Tüketici | [tüketici | işletme] |
  | İdare / vergi | [ilgili kişi-mükellef | idare] |
  | Tazminat ve trafik | [zarar gören | sigorta / zarar veren | bilirkişi (tarafsız) | dosyaya göre] |
  | Kamu ihale | [idare | istekli firma | ihale danışmanı (birden çok istekli adına) | dosyaya göre] — ayrıntı "Kamu ihale" bölümünde |
  | Ceza | [müdafi | katılan vekili | ikisi] |
  | [diğer] | |

## Uzmanlık ve iş dağılımı
- Ana alanlar (öncelik sırasıyla): [ör. iş, sosyal güvenlik, icra]
- Ara sıra: [ ]
- Hiç bakmadığımız: [ör. ceza — bu alanda çıktı "uzman yönlendirmesi" notu taşır]
- Kutuya sığmayan iş tanımı: [kullanıcının kendi cümlesi, varsa]

## Yer
- Şehir: [ ]
- Sık çalışılan adliyeler / mahkemeler: [ör. İstanbul Anadolu Adliyesi, Kartal]
- Bölge adliye mahkemesi / bölge idare mahkemesi: [biliniyorsa; bilinmiyorsa beceri sorar]
- Sık muhatap kurumlar: [ör. SGK İl Müdürlüğü, vergi dairesi, belediye]

## Üslup
- Dil düzeyi: [Hukukçu dili | Sade (hukukçu olmayan okur) | Çok sade (vatandaş, kısa cümle)]
- Müvekkile/yönetime giden metin: [resmî | sıcak ama resmî | kısa madde işaretli]
- Dilekçe biçimi:
  - Merci başlığı: [ör. "İSTANBUL ANADOLU ( ). İŞ MAHKEMESİ'NE" — büyük harf, ortalı]
  - Bölüm başlıkları: [ör. DAVACI / VEKİLİ / DAVALI / KONU / AÇIKLAMALAR / HUKUKİ SEBEPLER / DELİLLER / SONUÇ VE İSTEM]
  - Açıklamalar: [numaralı paragraf | serbest]
  - Karar atıf biçimi: [ör. "Yargıtay 9. HD, 12.03.2024 T., 2023/1234 E., 2024/5678 K." | soorgla'nın hazır atfı]
  - Dipnot: [kullanılır | kullanılmaz]
- İmza bloğu:
  ```
  [___]
  Av. [Ad Soyad]
  [Baro] Barosu Sicil No: [___]   ← kullanıcı açıkça isterse doldurulur
  ```
- Hitap ve kapanış: [ör. "Saygılarımızla arz ederiz." | "Arz ve talep ederim."]
- Word çıktısı: [istenir | markdown yeterli]

## Risk iştahı
- Genel tutum: [Temkinli | Dengeli | Atak] [VARSAYILAN: Dengeli]
- Bizi en çok ne korkutur: [ör. süre kaçırmak, işe iadede ispat, harç hesabı]
- Kendi eşiklerimiz: [ör. "X TL üstü taleplerde ortak görsün" — yasal eşik değil, büroya özgü]

## Yükseltme ve onay
- Yükseltme kişisi: [ad/rol | "kendim karar veririm" | stajyer için staj avukatı | kurum hukuk müşavirliği]
- Otomatik yükseltme durumları: [ör. süresi 7 günden az kalan iş, ceza boyutu, basına yansıyan dosya, kamu zararı]
- Kanal: [yüz yüze | e-posta | büro yazışma grubu] — eklenti göndermez, yalnız özet hazırlar

## Şablonlar ve örnekler
- Sık kullanılan belgeler: [ör. işe iade arabuluculuk başvurusu, ihtarname, icra takip talebi, istinaf]
- Büronun kendi şablonları: [var — konum: … | yok]
- Örnek dilekçe/yazı alındı mı: [evet, N adet, kurulum tarihinde okundu | hayır]
- Öğrenilen biçim notları: [örneklerden çıkarılan kısa notlar; müvekkil bilgisi içermez]

## Elektronik işlemler
- UYAP: [Avukat Portal kullanılıyor | Vatandaş Portal | Kullanılmıyor]
- e-imza / mobil imza: [var | yok]
- UETS (elektronik tebligat adresi): [var | yok | bilmiyorum]
- KEP: [var | yok] — işveren ise işçiye KEP ile bildirim uygulaması: [ ]
- Not: eklenti bu sistemlere bağlanmaz; bu bilgi yalnız taslağın biçimini ve hatırlatmaları etkiler.

## Bağlantılar
| Bağlantı | Durum | Son kontrol | Yoksa |
|---|---|---|---|
| soorgla MCP | [✓ denendi | ⚪ tanımlı, denenmedi | ✗ yok] | [TARİH] | Atıflar `[model bilgisi — doğrulayın]` |
| Dosya sistemi | [✓ | ✗] | [TARİH] | Profil bloğu sohbete/proje talimatına |
| Word (docx) becerisi | [✓ | ✗] | [TARİH] | Markdown verilir |

## Öğrenci ayarları  ← yalnız hukuk öğrencisi
- Sınıf / hazırlık: [1-4. sınıf | HMGS | hâkimlik-savcılık | avukatlık stajı öncesi]
- Öğrenme biçimi: [Sorgula beni (Sokratik) | Önce anlat sonra sor]
- Güçlü / zayıf dersler: [ ]

## Çıktı tercihleri
- Yönlendirme onayı (yonlendirme_onayi): [evet — işe başlamadan "bunu X olarak inceleyeceğim, doğru mu?" diye sor | hayır]
- Uzunluk: [kısa | standart | ayrıntılı]

## İş hukuku
[ORTAK-KURALLAR.md "Büro profili" şablonundaki alanlar; tam kurulumda iş hukuku ana alansa sorulur, değilse bölüm "[Kullanılmıyor]"]

## Sözleşme playbook'u
[sozlesme-incelemesi-tbk/references/genel-inceleme-ve-playbook.md şablonu; bu beceri doldurmaz, o beceri kullanıcı onayıyla ekler]

## Kaza ve bedensel zarar  ← yalnız bilirkişi, sigorta tarafı ya da ana alanlarda "Tazminat ve trafik" varsa
- Rol: [zarar gören tarafı (avukat / kişi) | sigorta tarafı (şirket, eksper, rücu, sigorta avukatı) | bilirkişi]
- Bilirkişilik alanı (bilirkişi ise): [aktüerya | trafik kusuru | maluliyet (hekim) | araç hasarı ve değer kaybı | diğer]
- Sigorta tarafında ağırlıklı iş: [hasar ve değer kaybı tespiti | tazminat ödemesi | rücu | Sigorta Tahkim'de cevap]
- Dosya ölçeği: [tek tük | çok — süre defteri ve dosya klasörü]

## Kamu ihale  ← yalnız ana alanlarda "Kamu ihale ve hakediş" varsa
- İhale rolü: [İdare (ihale yetkilisi, komisyon, satın alma) | İstekli firma (kendi adına teklif veren) | İhale danışmanı (birden çok istekli adına doküman tarama, şikâyet ve itirazen şikâyet takibi) | Avukat (müvekkile göre)]
- Kurum türü (idare ise): [bakanlık | belediye | üniversite | KİT | diğer]
- Ağırlıklı aşama: [hazırlık ve doküman | teklif ve değerlendirme | şikâyet, itirazen şikâyet ve dava | sözleşme ve hakediş]
- Eşzamanlı ihale sayısı: [tek tük | çok — süre defteri ve dosya klasörü kurulsun]

## Mali müşavirlik  ← yalnız kullanıcı türü mali müşavirse
- Unvan: [SM | SMMM | YMM | şirket finans/muhasebe ekibi] — YMM'de defter tutma önerilmez, tasdik işi açılır (3568 m.2/B)
- Büro ili ve vergi dairesi: [ ] — SMMM asgari ücret tarifesi il grubuna göre değişir
- Müşteri ölçeği: [birkaç | onlarca | yüzlerce]; dağılım: [bilanço ~% | işletme ~% | serbest meslek ~%]
- Ağırlıklı işler: [bordro ve SGK | KDV ve muhtasar | gelir/kurumlar beyanı | yılsonu kapanış ve enflasyon düzeltmesi | e-belge | vergi incelemesi ve uzlaşma | KDV iadesi | tasdik (YMM) | şirket kuruluş/tasfiye]
- Muhasebe programı ve e-defter / e-fatura entegratörü: [ ] — yalnız alışkanlık; eklenti bunlara bağlanmaz
- Danışılan / yükseltme: [YMM | vergi avukatı | oda | kendim]
- Avukat irtibatı: [uyuşmazlıklarda çalışılan avukat ya da büro; yoksa "yok"]
- Müşteriye giden yazı biçimi: [resmî | sade | madde işaretli]; imza bloğu: [unvan, oda; sicil no yazılmaz → `[___]`]
- Sayısal değer (asgari ücret, had, oran) bu bölüme yazılmaz; beceriler araçtan ve tarifeden çeker.

## Gümrük müşavirliği  ← yalnız kullanıcı türü gümrük müşaviriyse
- Ağırlıklı rejim ve işler: [ithalat | ihracat | dahilde/hariçte işleme | antrepo ve geçici depolama | transit | serbest bölge]
- Uyuşmazlık payı: [ek tahakkuk ve m.242 itirazı | gümrük davası | tarife sınıflandırması ve BTB | kıymet | menşe ve önlemler | kaçakçılık–idari yaptırım]
- Beyanname ölçeği: [günde birkaç | onlarca | yüzlerce]; avukat irtibatı: [ ]

## Süre takibi
- Uyarı bantları (kalan gün): [VARSAYILAN — ⛔ geçti / 0–6 / 7–13 / 14–29 / 30–89]
- İç hedef payı (iş günü): [VARSAYILAN]
- Takvim hatırlatıcıları (gün önce): [VARSAYILAN — 14 / 7 / 3 / 1]

## Dosya (müvekkil) çalışma alanları
- Etkin: [✗ — şirket içi ve vatandaş kullanıcılar için kapalı]
- Etkin dosya: yok
- Dosyalar arası bağlam: kapalı
- Dosya klasörü yeri: [VARSAYILAN — ~/.claude/plugins/config/soorgla-hukuk/dosyalar/]
- Çıkar çatışması: [yer ve yöntem (büro kaydı, yazılım, elle); kontrol bitmeden paralel açılışa izin var mı] ← dosya-klasoru okur

## Notlar
- [kullanıcının profil üzerinden istediği ama korkuluk nedeniyle uygulanmayan ayarlar ve gerekçesi]
````

---

## 2. Alanlar hangi beceride neyi değiştirir

| Alan | Etkisi | Okuyan beceriler |
|---|---|---|
| Rol | Her çıktının ilk satırındaki başlık; "Taslaktır" kapısı | Hepsi (ORTAK-KURALLAR.md §1) |
| Kullanıcı türü | Görüşme dalı; stajyer/öğrenci/kamu ek davranışları | Hepsi |
| Avukat irtibatı | Avukat olmayan için "avukata götürülecek özet"in kime gideceği | Hepsi |
| Varsayılan taraf / alan bazında taraf | Kontrol listesindeki vurgu (hak kaçırma riski mi, ispat yükü mü); "tarafı sor" adımı atlanır | Bütün alan becerileri (`is-hukuku`'nda "Ağırlıklı taraf", `kira-hukuku`'nda kiracı/kiraya veren …) |
| Ana alanlar / hiç bakmadığımız | Yönlendirme önerisi; bakılmayan alanda "uzman yönlendirmesi" notu | Hepsi; `genel-hukuk-arastirmasi` (planlanan) |
| Şehir, adliyeler | Yetkili mahkeme ve merci başlığı önerisi; baro adli yardım ve arabuluculuk bürosu hatırlatmasının ili | Dilekçe becerileri, `vatandas-basvurulari` |
| Dil düzeyi | Cümle uzunluğu, terim açıklaması; avukat olmayan için §8 sade açıklama kuralı **her durumda** geçerlidir | Hepsi |
| Dilekçe biçimi, imza bloğu, atıf biçimi | Taslağın iskeleti; boşsa ORTAK-KURALLAR.md §13/5 iskeleti | Dilekçe becerileri |
| Risk iştahı | Öneri tonu ve "Şimdi ne yapalım?" sıralaması (bkz. §6) | Hepsi |
| Yükseltme kişisi, otomatik yükseltme | Karar ağacındaki "Yükselt" seçeneğinin muhatabı; otomatik durumda çıktının başına 🟠 "yükseltin" notu | Hepsi (ORTAK-KURALLAR.md §8 karar ağacı) |
| Sık kullanılan belgeler | Karar ağacında ilk seçenek olarak önerilen taslak | Dilekçe becerileri |
| UYAP/UETS/KEP | Taslakta "UYAP'tan e-imzayla sunulacaksa…" hatırlatması; e-tebligatta tebliğ anı hatırlatması | Dilekçe becerileri, `is-hukuku` (KEP ile fesih bildirimi) |
| Bağlantılar | "soorgla bağlı değil" satırı | Hepsi (ORTAK-KURALLAR.md §3) — ama her beceri yine kendi ön kontrolünü yapar; profil satırı tek başına ✓ sayılmaz |
| Kaza ve bedensel zarar: rol, bilirkişilik alanı | Zarar gören: hak ve süre kaçırma, eksik kalem; sigorta: ispat yükü, limit (ZMSS), Genel Şartlar formülü, rücu; **bilirkişi: hesap tablosu ara adımlarıyla ve dayanağıyla, rapor öz denetimi (itiraza açık nokta); kusur ve maluliyet oranını beceri yazmaz** | `tazminat-haksiz-fiil`, `hukuk-yargilamasi-dilekce` (bilirkişi itirazı), `vatandas-basvurulari` (Sigorta Tahkim), kaza ve tazminat hesap araçları |
| Kamu ihale: rol, aşama, eşzamanlı ihale | İhale becerilerinde rol sorusu atlanır; idare modu (hazırla, savun) ya da istekli modu (incele, itiraz et); danışmanda çok dosyalı süre tablosu, "şikâyete dayanak" tarama listesi ve emsal KİK kararında mahkeme etkisi kontrolü öne çıkar | `kamu-ihale` (giriş), `ihale-yapim`, `ihale-mal`, `ihale-hizmet`, `ihale-danismanlik`, `ihale-sikayet` (danışmanda `references/danisman-cok-dosya.md`), `ihale-belgeleri`, `hakedis`, `sure-takibi`, `dosya-klasoru` |
| Mali müşavirlik / gümrük müşavirliği bölümleri | Taraf varsayılanı mükellef/yükümlü; tutar ve oranda araç ve tebliğ önce (hesap değerlendirmesi müşavirin işi, beceri dayanağı ve süreyi verir); uyuşmazlık başlayınca avukat irtibatına yönlendirme notu; çok müşteride süre defteri | `vergi`, `sosyal-guvenlik-sgk`, `gumruk-dis-ticaret`, `sirketler-ticaret`, `tesvik-yatirim`, `sure-takibi`, muhasebe ve gümrük becerileri (planlanan) |
| yonlendirme_onayi | İşe başlamadan tür onayı | `sozlesme-incelemesi-tbk` ve isteyen diğerleri |

---

## 3. Kullanıcı türüne göre dallanma notları

- **Avukat (serbest / küçük büro, hiyerarşi yok):** yükseltme "onaya gönder" değil "**danış**"tır: "İkinci görüş için kimi ararsınız (meslektaş, baro komisyonu, akademisyen)?" Cevap "kimse" olabilir; doğrudur, yazılır.
- **Orta-büyük büro, şirket içi, kamu:** onay zinciri sorulur (ortak avukat, hukuk müdürü, hukuk müşaviri, genel müdür).
- **Stajyer avukat:** upstream `legal-clinic` gözetim modelinin karşılığı. Staj avukatının adı ve "dışarı gidecek her metin staj avukatı onayından geçer" kuralı yazılır; bu kural profil üzerinden kapatılamaz. Stajyerin duruşma ve dilekçe yetkisinin sınırları `[model bilgisi — doğrulayın: Av.K. staj hükümleri ve TBB Avukatlık Kanunu Yönetmeliği]`.
- **Şirket hukukçusu:** şirketin faaliyet alanı ve sektör tek cümle (ör. "lojistik, 400 çalışan, 3 ilde depo") — upstream "What does your company do?" sorusunun karşılığı. İnternet sitesi bağlantısı yeterli; ticari sır yazdırma.
- **Kamu görevlisi:** kurum türü (bakanlık, belediye, üniversite, KİT…) ve birim (ihale, personel, strateji, hukuk müşavirliği). Kamu tarafı becerileri (`kamu-ihale` idare tarafı, `kamu-personeli` idare tarafı, `kamu-mali-denetim-sayistay`) bu alanı okur.
- **İhale danışmanı / şikâyet takipçisi:** birden çok istekli adına ihale dokümanı tarayıp şikâyet ve itirazen şikâyet yürüten kullanıcı (hukuken istekli tarafı). Kurulumda süre defteri ve dosya klasörü önerilir (ihale başına bir klasör, İKN ile). Müvekkil firma adları profile yazılmaz, dosya klasörüne yazılır. Ürün metinlerinde "danışman" ya da "şikâyet ve itiraz takibi" denir; argo adlar kullanılmaz.
- **Bilirkişi (aktüer, trafik kusur, hekim):** mahkemenin görevlendirdiği uzman; taraf değildir, taraf sorulmaz. Başlık sınıfı: hukukçu bilirkişi → avukat/hukukçu; diğerleri → meslek mensubu (`MESLEKİ ÇALIŞMA TASLAĞI — BİLİRKİŞİ İNCELEMESİ GEREKTİRİR`). Beceri hesap tablosunu ara adımları, formülü ve dayanağıyla verir; raporun HMK ve Bilirkişilik Yönetmeliği'ne göre öz denetimini yapar (soru-cevap eşleşmesi, dayanılan belge, gerekçe, hukuki nitelendirme yasağı). **Kusur ve maluliyet oranını beceri belirlemez, rapora sonuç cümlesi yazmaz**; bilirkişinin kendi değerlendirmesi için soru ve kontrol listesi verir. Dosya kişisel ve sağlık verisi içerir: KVKK özel nitelikli veri uyarısı.
- **Sigorta eksperi / sigorta şirketi hasar ve rücu birimi:** hukuken zarar görenin karşı tarafı. Vurgu ispat yükü, ZMSS ve Genel Şartlar limitleri, değer kaybında Genel Şartlar formülü ile piyasa yönteminin karşılaştırılması, rücu şartları ve Sigorta Tahkim'de cevap. Uyuşmazlık dava ya da tahkime gidince şirket avukatına yönlendirme notu.
- **Mali müşavir (SM / SMMM / YMM) ve gümrük müşaviri:** kendi alanının uzmanı ama hukukçu değil; başlık sınıfı **meslek mensubu** (ORTAK-KURALLAR.md §1): kendi alanındaki işte `MESLEKİ ÇALIŞMA TASLAĞI`, uyuşmazlıkta avukat olmayan başlığı ve kapısı. 3568 m.2/A defter, bilanço ve beyanname düzenlemeyi, mali mevzuatta müşavirliği ve yazılı görüşü SMMM mesleğinin konusu sayar; bu işlerde "avukata danışın" denmez. Dil varsayılanı "meslek dili" (hukuk terimleri kısa açıklamalı). Mevzuat, özelge, tebliğ ve tarife sorularında doğrudan ve teknik cevap; vergi/gümrük **uyuşmazlığına** (dava, kaçakçılık, ceza) dönen işte avukat irtibatına yönlendirme notu. Müşteri (mükellef/firma) adları profile değil dosya klasörüne yazılır.
- **Vatandaş / işletme sahibi:** taraf genelde soruda belli olur; profil kısa tutulur. Dil düzeyi varsayılanı "çok sade".
- **Hukuk öğrencisi:** upstream `law-student`. Çıktı başlığı avukat olmayan sınıfıdır. **Gerçek dosya kontrolü:** öğrenci gerçek bir olayı (gerçek ad, tarih, dosya) anlatırsa dur: "Bu bir çalışma örneği değil, gerçek bir dosyaya benziyor. Stajda ya da bir büroda karşılaştıysanız oradaki avukatın onayıyla ve kişisel verileri çıkararak çalışın; kendi meselenizse çalışma aracı yerine bir avukata danışın. İsterseniz adları ve tarihleri değiştirip çalışma örneğine çevirelim." Fakültenin sınav ve ödev kurallarını hatırlat: not verilen işte kullanım kuralını öğretim elemanına sorun.

---

## 4. Upstream'den alınmayanlar

- Paket başına ayrı profil ve `company-profile.md`: tek dosya kullanıyoruz.
- CLM, HRIS, e-imza, Slack, Box entegrasyon tablosu: karşılığı yok; yalnız soorgla MCP, dosya sistemi ve docx.
- "PRIVILEGED & CONFIDENTIAL — ATTORNEY WORK PRODUCT": ORTAK-KURALLAR.md §1 başlıkları ve "Sır saklama notu" kullanılır.
- ABA Formal Opinion 512, Model Rules 1.1/1.4/1.6/5.3: karşılığı Av.K. m.36 [soorgla] ve meslek kuralları `[model bilgisi — doğrulayın: TBB Meslek Kuralları ve yapay zekâ kullanımına ilişkin baro ya da TBB rehberi var mı]`.
- ASC 450 karşılık ayırma, yönetim kurulu notu: yalnız şirket hukukçusu dalında "yönetime özet" olarak.
- Sözleşme playbook'u, iş hukuku eşikleri gibi alan ayrıntıları: ilgili alan becerisi kendi bölümünü ekler; bu beceri yalnız iskeleti ve iş hukuku bölümünü (ORTAK-KURALLAR.md'de zaten tanımlı) sorar.

---

## 5. Profil boyutu

Profil kısa kalmalı: hedef 150 satırın altı. Alan bölümleri uzarsa (ör. sözleşme playbook'u) bile genel bölümler ilk 60 satırda bitmeli; beceriler önce üst bölümü okur. Örneklerden çıkarılan biçim notları en fazla 10 madde; örnek metnin kendisi profile kopyalanmaz.

---

## 6. Risk iştahı neyi değiştirir, neyi değiştirmez

| | Temkinli | Dengeli | Atak |
|---|---|---|---|
| "Şimdi ne yapalım?" sıralaması | Önce "eksik olguları topla", "yükselt" | Avukat seçer, sıralama nötr | Önce "taslağı hazırla" |
| Öneri dili | En güvenli yol önce, diğerleri riskleriyle | Seçenekler eşit | Savunulabilir en güçlü talep önce, riskleri yanında |
| Talep kapsamı önerisi | Dar, sağlam kalemler | — | Geniş, zayıf kalemler `[incele]` ile ayrılmış |
| **Değişmez** | Önem dereceleri (🔴/🟠), `[incele]` ve `[doğrula]` işaretleri, süre uyarıları, taslak başlığı, "Taslaktır" kapısı | | |

Atak tutum hiçbir 🔴'yi 🟠'ye çevirmez; temkinli tutum hiçbir 🟢'yi 🔴 yapmaz. İştah sunuşu değiştirir, bulguyu değil.
