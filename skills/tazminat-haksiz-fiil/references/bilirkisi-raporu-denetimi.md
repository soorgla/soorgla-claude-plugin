# Bilirkişi raporu denetimi (maluliyet, aktüerya, kusur, araç hasarı, işçilik hesabı)

## Ne zaman kullanılır
Tebliğ edilen bir bilirkişi raporu yüklendi ya da yapıştırıldı: "rapora itiraz", "rapor doğru mu", "aktüer raporunu kontrol et", "kusur raporu hatalı", "maluliyet oranı yanlış". Sigorta Tahkim Komisyonu dosyasındaki rapor ve ceza dosyasından gelen kusur raporu da bu dosyayla denetlenir (ceza yargılamasındaki itiraz `ceza-ve-infaz-dilekce`'nin işidir).

Bu dosya raporu **denetler**, hesap kalemlerini hesap araçlarıyla **yeniden hesaplar**, farkları ve itiraz noktalarını tabloya döker ve itiraz dilekçesine devreder. Raporun yerine geçecek kusur oranı, maluliyet oranı ya da tutar **üretmez**.

**Kullanılmaz:** rapor henüz yokken "bilirkişi ne der" tahmini → kusurda `kaza-tutanagi-ve-kusur.md`, hesapta `bedensel-zarar-ve-destek-hesabi.md`.

Başka becerilerden bağlantı: işçilik alacağı raporu `is-hukuku`'ndan (§4.6), iş kazası kusur raporu `sosyal-guvenlik-sgk`'dan (§4.4) bu dosyaya gelir; ayrı kopya yoktur.

---

## 0. İlk iş: süre
- Rapora itiraz ve ek süre talebinin süresi ve son gün kuralı `../../hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md` "Süre tablosu"ndadır (HMK m.281/1). Tebliğ tarihini sor, son günü oradaki kurala göre hesapla, `legal_check_holiday` ile kontrol et. 7 günden az kaldıysa çıktının en üstüne 🔴 (ORTAK-KURALLAR.md §13/1).
- Bilirkişinin **reddi** için süre daha kısadır: sebebin öğrenilmesinden itibaren en geç bir hafta (HMK m.272). Ret sebebi görünüyorsa ayrı 🔴 satırı. 
- Süre geçmişse denetim yine yapılır; sonuç "itiraz" değil, mahkemenin ek rapor yetkisine (m.281/2-3) ve esasa beyana dayanak olarak çerçevelenir `[incele]`.
- Son gün hesaplanınca "süre defterine ekleyeyim mi?" diye sor → `../../sure-takibi/SKILL.md`.

---

## 1. Hesap araçlarının durumu (her çalıştırmada kontrol et)

Yeniden hesap aşağıdaki MCP araçlarına dayanır. Araç yanıt vermezse ya da hata dönerse:
- yeniden hesap **yapılmaz**, elle hesap ya da "yaklaşık" tutar **yazılmaz**;
- fark tablosunun "Yeniden hesap" sütununa `araç yok — yalnız yöntem denetimi` yazılır;
- yöntem ve girdi denetimi (§3-§4) tam yapılır, bulgular yine üretilir.

| Rapor türü | MCP aracı | Alt seçim |
|---|---|---|
| Maluliyet | `legal_calculate_actuarial_present_value` | `islem: maluliyet_birlestir` |
| Aktüerya | `legal_calculate_actuarial_present_value` | `islem: tazminat` |
| Aktüerya / işçilik (brüt-net girdi) | `legal_calculate_employment_claims` | `islem: brutten_nete` |
| İşçilik alacağı | `legal_calculate_employment_claims` | `islem: alacaklar` |
| Araç hasarı, değer kaybı, pert, mahrumiyet | `legal_calculate_vehicle_damage` | `tur: deger_kaybi \| pert_farki \| mahrumiyet` |
| Kusur raporunun fiziksel varsayımları | `legal_calculate_stopping_distance` | `mod: durma \| izden_hiz \| kritik_hiz \| yaya \| takip` |

Girdi kontrolü araçları: bakiye ömür `legal_get_life_expectancy` (tablo adını döndürmez, PMF-1931 yok), faiz `legal_get_legal_interest_rates`, asgari ücret ve kıdem tavanı `legal_get_social_parameters` (yalnız güncel dönem), TÜFE `legal_calculate_cpi_change`. Bunlarla raporun **tek tek girdileri** (ör. bakiye ömür, faiz oranı) kontrol edilir.

**Girdi uydurma yok.** Rapordan okunamayan girdi (doğum tarihi, gelir, PSD, rayiç) `[___]` kalır; o kalem yeniden hesaplanmaz ve bulgu "raporda girdi gösterilmemiş" olur (ORTAK-KURALLAR.md §5).

---

## 2. Rapor türünü tanı

Dosyada birden fazla rapor olabilir (kök, ek, ceza dosyası, tahkim, uzman görüşü). Her biri ayrı satırda tanınır ve ayrı denetlenir; aralarındaki çelişki ayrıca denetlenir (§4.7).

| Tür | Tanıma ipuçları | Tipik düzenleyen |
|---|---|---|
| **Maluliyet** | "% … oranında engelli/malul", yönetmelik adı, Balthazard, sistem/organ başlıkları, iyileşme süresi | Yetkili hastane sağlık kurulu, üniversite adli tıp ABD, ATK; iş kazasında SGK sağlık kurulu |
| **Aktüerya** | bilinen / işleyecek dönem, TRH-2010, PMF-1931, progresif rant, peşin sermaye değeri, aktif / pasif dönem | Aktüer bilirkişi |
| **Kusur — trafik** | asli / tali kusur, KTK m.84, "%… kusurlu", kroki değerlendirmesi | Trafik bilirkişisi, ATK Trafik İhtisas Dairesi, İTÜ, KGM Fen Heyeti |
| **Kusur — iş kazası** | 6331, İSG yönetmelikleri, "işveren … oranında kusurlu", müfettiş raporu | İSG uzmanı içeren heyet |
| **Araç hasarı** | parça + işçilik, değer kaybı, sovtaj, pert, rayiç, ikame araç, mahrumiyet | Otomotiv uzmanı / eksper bilirkişi |
| **İşçilik alacağı** | kıdem, ihbar, fazla çalışma, UBGT, çıplak / giydirilmiş ücret, hakkaniyet indirimi | Hesap bilirkişisi |

Tür belirsizse tek soru: "Bu rapor oran mı (maluliyet/kusur), yoksa tutar mı (tazminat/alacak/hasar) belirliyor?"

---

## 3. Usul denetimi (her türde, esastan önce)

Usul eksikliği tek başına **yeni bilirkişi** talebine dayanak olur; esas hatası **ek rapor** ya da **açıklama** talebine.

### 3.1 Bilirkişi konusu mu, sınırlar belli mi?
- [ ] Çözümü özel veya teknik bilgi gerektiren konu mu? Genel bilgi, tecrübe ya da hukuki bilgiyle çözülebilen konuda bilirkişiye gidilmez (HMK m.266; 6754 m.3/3). 
- [ ] UYAP ve entegre sistemlerden ulaşılabilen bilgi (ör. yasal faiz ya da asgari ücret dökümü) tek başına bilirkişi konusu değil (6754 m.3/8). 
- [ ] Görevlendirme kararındaki sorular raporda tek tek cevaplanmış mı; sorulmayan konuda görüş var mı (6754 m.3/6)? 

### 3.2 Hukuki nitelendirme yasağı
- [ ] Bilirkişi hâkimin yapacağı hukuki nitelendirme ve değerlendirmede bulunamaz (HMK m.279/4; 6754 m.3/2).  HGK bu yasağı uyguluyor (HGK E.2017/367 K.2019/350: rapor hukuki nitelendirme içeremez, yabancı hukuku hâkim kendiliğinden araştırır); HGK E.2017/230 K.2020/996 Bilirkişilik Yönetmeliği m.5/2-3 metnini aynen aktarıyor (§ 30).  
- Tipik ihlaller: zamanaşımı ya da hak düşürücü süre görüşü; "fesih haklıdır"; "davacı tazminata hak kazanmıştır"; gerekçesiz hakkaniyet indirimi oranı; kusur raporunda "bu nedenle sigortacı sorumludur". KTK kuralına aykırılık tespiti teknik, sorumluluk sonucu hukuki değerlendirmedir `[incele]`.
- Bulgu: 🟠 "Rapor hukuki değerlendirme içeriyor; bu kısım hükme esas alınamaz." Hesap bu değerlendirmeye bağlıysa (ör. zamanaşımı kabul edilip dönem dışlanmış) **seçenekli hesap** istenir.

### 3.3 Asgari içerik (HMK m.279/2)
Eksik her kalem itiraz dilekçesinde ayrı satır olur. 
- [ ] Tarafların ad ve soyadları
- [ ] Görevlendirildiği hususlar (mahkemenin soruları)
- [ ] İncelenen maddi vakıalar (hangi belge, muayene, keşif)
- [ ] **Gerekçe** ve sonuç — gerekçesiz sonuç "denetime elverişli değil" itirazının çekirdeği
- [ ] Kurulda görüş ayrılığı ve sebebi
- [ ] Düzenleme tarihi ve imzalar; tüzel kişi bünyesindeki bilirkişinin adı, soyadı, imzası (6754 m.10/2) 

### 3.4 Bilirkişinin kendisi
- [ ] **Liste:** bölge kurulu listesinden mi; liste dışıysa m.268/1-2 sırası gözetilmiş mi?  Sicil sorgusunu kullanıcı yapar; beceri sicil verisi uydurmaz `[doğrula]`.
- [ ] **Uzmanlık uyumu:** raporda yazan unvan ile görevlendirilen uzmanlık alanı aynı mı (6754 m.10/1-g, ğ)? Örnek: değer kaybı raporunu inşaat mühendisi yazmış. 
- [ ] **Kamu görevlisi:** davalı kamu kurumuysa bilirkişi o kurumun görevlisi mi (m.268/3 yasağı)?  Varsa 🔴 ve m.272 ret süresi en üstte.
- [ ] **Bizzat yapma:** "yardımcı"nın incelemesine dayanma (6754 m.3/4). 
- [ ] **Tek rapor ilkesi:** aynı konuda kural olarak bir rapor; eksiklik için ek rapor (6754 m.3/7).  Yeni bilirkişi talebi gerekçeli olmalı: usul eksikliği, uzmanlık uyumsuzluğu, giderilemeyen çelişki ya da ek rapora rağmen süren eksiklik.

### 3.5 Maluliyet raporunu kim verebilir
- [ ] Belirleme, sağlık kurulu raporu vermeye **yetkili** kuruluşta, kaza tarihindeki mevzuata göre ve yaralanmayla ilgili **uzman hekimleri içeren** heyetçe yapılmalı. 4. HD E.2024/7318 K.2025/14186 (15.10.2025): ortopedi ve adli tıp uzmanlarının raporu, epilepsi riski ve yüz skarı için yetersiz bulundu; nöroloji ve plastik cerrahi uzmanı içeren kuruldan rapor istendi. 
- **Denetim kuralı:** imza bloğundaki uzmanlık dalları, raporda değerlendirilen arızaların sistemleriyle tek tek eşleştirilir. Eşleşmeyen arıza → 🟠 "uzman hekim heyette yok".
- [ ] Kaza ile arıza arasında **illiyet bağı** yazılmış mı? Yazılmamışsa hükme esas alınamaz: 4. HD E.2024/6604 K.2025/13645 (tedavi belgeleri getirtilip kişi yeniden muayene edilerek, kaza tarihindeki yönetmeliğe göre ATK raporu alınması için bozma). 
- Sigorta Tahkim dosyasında bilirkişiler ayrı yönetmeliğe tabi (Sigorta Tahkim Komisyonu Bilirkişilik Yönetmeliği).   Seçim ve itiraz usulü için madde metnini çek; çekemezsen `[doğrula]`.

### 3.6 Hâkimin takdiri ve çelişkili raporlar
- Hâkim raporu diğer delillerle birlikte serbestçe değerlendirir (HMK m.282).  Bu, çelişen raporlar arasında **gerekçesiz** tercih yetkisi vermez: birine neden itibar edildiği gerekçelendirilmeli ya da çelişkiyi gideren üçüncü rapor alınmalı (4. HD E.2025/4748 K.2025/7648; E.2023/3943 K.2025/4851). 
- Küçük fark (ör. iki maluliyet raporunda %12,6 ile %13) çelişki sayılmayabiliyor (4. HD E.2023/4242 K.2025/1007) `[çekildi ama desteği doğrulayın]`. Sayısal eşik yok `[incele]`.

---

## 4. Türe göre kontrol listesi

Her madde bir bulgu üretir: durum (uygun / hatalı / eksik / belirsiz / denetlenemedi) ve önem (🔴/🟠/🟡/🟢, ORTAK-KURALLAR.md §8). Aşağıdaki kararların çoğu arama alıntısından çekildi; çıktıda kullanmadan önce **son 3 yıldan en az birinin tam metnini** `legal_get_case_document` ile oku (SKILL.md Adım 3), okunmayanlar `[çekildi ama desteği doğrulayın]` etiketi alır.

### 4.1 Maluliyet
- [ ] Yönetmelik **kaza tarihine** göre mi seçilmiş? Yürürlükte olmayan yönetmeliğe göre rapor hüküm kurmaya elverişli değil (4. HD E.2023/12820 K.2024/6818); çocuk/erişkin yönetmeliği karışıklığı (4. HD E.2025/10038 K.2025/15980). Dönem sınırları → `bedensel-zarar-ve-destek-hesabi.md` "Hesap yöntemi". 
- [ ] Birden fazla arıza **düz toplanmış** mı, yönetmeliğin birleştirme yöntemiyle mi birleştirilmiş?
- [ ] Kaza dışı (önceden var olan) arıza ayrılmış mı?
- [ ] Düzenleyen kurul yetkili mi, arızalara uygun uzman var mı, illiyet yazılmış mı (§3.5)?
- [ ] Geçici iş göremezlik (iyileşme) süresi ayrı yazılmış mı? Aktüerya hesabının girdisidir; yoksa aktüer raporu da eksik kalır.
- **Yeniden hesap:** `legal_calculate_actuarial_present_value` `islem: maluliyet_birlestir` → raporun **kendi** arıza oranlarıyla birleştirme ve yönetmelik seçimi. Arıza oranının tabloya uygunluğu yalnız **gösterilir**; uygun oran beceri tarafından seçilmez `[incele]`.

### 4.2 Aktüerya
Ana liste `bedensel-zarar-ve-destek-hesabi.md` → "Hesap denetim listesi (aktüer raporu geldiğinde)"; o liste uygulanır, burada tekrar yazılmaz. Denetime özgü ekler:
- [ ] **Yaşam tablosu ve yöntem:** 4. HD'nin yerleşik uygulaması TRH-2010 ve işleyecek dönem için progresif rant; teknik faiz ya da belirli süreli rant hatalı bulunuyor (4. HD E.2023/12710 K.2024/2198; E.2023/10098 K.2023/13975). PMF-1931'in istendiği hâller (taraf kabulü, aleyhe bozma yasağı) `[incele]`. 
- [ ] **SGK peşin sermaye değeri:** rücuya tabi gelirin ilk PSD'si düşülmüş mü; SGK'ya sorulmuş mu (4. HD E.2023/2759 K.2024/3241; HGK E.2024/250 K.2025/354)?
- [ ] **PSD tarihi:** rapor tarihine en yakın PSD mi kullanılmış (4. HD E.2023/10135 K.2025/9530)? SGK yazısının tarihi ile rapor tarihini karşılaştır.
- [ ] **Gelir:** belgeli mi; asgari ücretin katı ya da "gelir güncelleme oranı" nereden geliyor (aynı karar)? Asgari ücreti `legal_get_social_parameters` ile; geçmiş dönem araçta yoksa `[doğrula]`.
- [ ] **Bakiye ömür:** rapordaki değer `legal_get_life_expectancy` (cinsiyet, olay tarihindeki yaş) ile aynı mı?
- [ ] **Faiz:** başlangıç tarihi ve türü (yasal / avans) `legal_get_legal_interest_rates` ile dönem dönem kontrol edilir; 31.07.2026 sonrası dönem için SKILL.md Adım 3 uyarısı.
- [ ] **Güncel hesap:** bozma sonrası rapor yeni hesap yapmadan eski rapora atıfla mı yetinmiş (3. HD E.2024/2394 K.2025/2754)?
- [ ] Seçenekli hesap varsa hangi seçeneğin Daire uygulamasına uyduğu ve hükmün hangisine dayandığı.
- **Yeniden hesap:** `legal_calculate_actuarial_present_value` `islem: tazminat` raporun girdileriyle (doğum tarihi, cinsiyet, olay ve rapor tarihi, oran, kusur, gelir, PSD, ödemeler). Fark kalem kalem: geçici iş göremezlik, bilinen, işleyecek aktif ve pasif dönem, mahsuplar. Gelir brütse önce `legal_calculate_employment_claims` `islem: brutten_nete`. Ara tutarlar raporda yoksa yalnız sonuç karşılaştırılır ve 🟠 "ara tutarlar yok — denetime elverişli değil".

### 4.3 Kusur — trafik
Olay sırası ve KTK eşlemesi `kaza-tutanagi-ve-kusur.md`'de; burada **mevcut raporun** denetimi.
- [ ] **Tutanakla çelişki** giderilmiş mi (4. HD E.2022/9901 K.2024/6694; E.2025/11604 K.2025/17107)?
- [ ] **Ceza / savcılık dosyasındaki raporla çelişki** giderilmiş mi (4. HD E.2023/3943 K.2025/4851 tam metin; E.2022/9758 K.2024/5179; E.2024/10972 K.2025/8625)? Dosyadaki bütün kusur raporları tabloya: kaynak, tarih, düzenleyen, taraf başına oran.
- [ ] Ceza mahkemesinin **kesinleşmiş maddi vakıa** tespitine aykırı mı (TBK m.74; 4. HD E.2023/13290 K.2025/8068)? 
- [ ] Dosyadaki deliller (kamera, tanık, ekspertiz, hasar fotoğrafı, kroki ölçüsü) **tek tek** değerlendirilmiş mi; atlanan hangisi?
- [ ] Oranlar toplamı %100 mü; her taraf ayrı gerekçeli mi; "asli/tali" nitelemesi oranlarla tutarlı mı?
- [ ] Fiziksel varsayımlar (hız, reaksiyon süresi, durma ve görüş mesafesi) açık yazılmış mı? Yazılmışsa `legal_calculate_stopping_distance` ile **aynı girdilerle** tekrar üretilir; fark → 🟠 "raporun hesabı kendi varsayımlarıyla tutarsız". Araç kusur oranı üretmez.
- [ ] Hukuki sonuç cümlesi var mı (§3.2)?
- Çelişkiyi giderecek kurum önerisi: ATK Trafik İhtisas Dairesi, İTÜ, KGM Fen Heyeti ya da üç kişilik heyet (4. HD E.2025/4748; E.2022/13922 K.2024/11873); seçim `[incele]`.

### 4.4 Kusur — iş kazası
- [ ] Heyette olayın iş kolunda **İSG uzmanı** var mı; 6331 kapsamında değerlendirilmiş mi (10. HD E.2025/9022 K.2025/17991; E.2024/15777 K.2025/1813)?
- [ ] Kusur **oranlanmış** mı; bilirkişiler önceki rapora "katılmakla" mı yetinmiş (10. HD E.2023/4071 K.2024/9256; E.2024/11548 K.2024/12328)?
- [ ] Ceza dosyasında mahkûm olanların kusuru ayrıca değerlendirilmiş mi?
- [ ] Müfettiş raporundaki tespitler irdelenmiş mi, aynen mi alınmış?
- [ ] Rücu davasında kusur oranı, gerçek zarar ile ilk peşin sermaye değerli gelirden **düşük olana** uygulanmış mı? Gelir fiili ödemeye dönüştüyse fiili ödemeyle de karşılaştırılır.  
- Esas → `../../sosyal-guvenlik-sgk/references/is-kazasi-ve-rucu.md`.

### 4.5 Araç hasarı, değer kaybı, pert, mahrumiyet
- [ ] **Değer kaybı ölçütü:** hasarsız ikinci el rayiç ile onarılmış hâlin rayici arasındaki fark; model, yaş, kilometre, önceki hasar, hasarın niteliği gözetilmiş mi (HGK E.2017/2049 K.2021/771; 4. HD E.2023/4299 K.2025/2544)? Genel Şartlar formülüyle yetinen rapor işaretlenir → `trafik-kazasi-ve-zmss.md` "Zarar kalemleri".
- [ ] **Uzmanlık:** otomotiv alanında uzman bilirkişi mi (HGK E.2020/642 K.2022/1120)?
- [ ] **Hasar kalemleri:** parça ve işçilik ayrı ayrı mı; tek kalem "hasar bedeli" denetime elverişli değil.
- [ ] **Pert:** kaza tarihindeki piyasa değeri belirlenmiş mi; onarımın ekonomik olup olmadığı tartışılmış mı?
- [ ] **Mahrumiyet:** yeni araç temini ya da onarım için **makul süre** tespit edilmiş mi (4. HD E.2022/15682 K.2023/1865)? Mahrumiyet ZMSS teminatı dışında (KTK m.92/k); kimden istendiğini kontrol et → `arac-hasari-deger-kaybi-ve-pert.md`.
- **Yeniden hesap:** `legal_calculate_vehicle_damage` (`tur: deger_kaybi | pert_farki | mahrumiyet`). Rayiç ve sovtaj bilirkişi girdisidir; araç bunları değiştirmez, yalnız kaynaklar arası farkı ve formül karşılaştırmasını gösterir.

### 4.6 İşçilik alacağı hesabı
- [ ] Yöntem ve dönemler gösterilmiş mi (9. HD E.2025/1689 K.2025/3171)?
- [ ] Fazla çalışma **haftalık** mı hesaplanmış (9. HD E.2019/3772 K.2021/2540)?
- [ ] Tablodaki zam oranı ile hesapta uygulanan aynı mı (9. HD E.2025/2251 K.2025/4832)?
- [ ] Ara dinlenme düşülmüş mü (9. HD E.2024/5126 K.2024/6748)?
- [ ] Kayıt olmayan dönem tanık, e-posta, sistem kaydıyla mı kurulmuş?
- [ ] Kıdem tavanı dönemi doğru mu (`legal_get_social_parameters`; geçmiş dönem yoksa `[doğrula]`)?
- [ ] Zamanaşımı, ıslah ya da fesih niteliği hakkında hukuki değerlendirme (§3.2; 9. HD E.2022/8184 K.2022/8814)?
- **Yeniden hesap:** `legal_calculate_employment_claims` (`islem: alacaklar`, gerekiyorsa `brutten_nete`) tablodaki her satırı yeniden üretir; fark satır numarasıyla gösterilir. Esas → `../../is-hukuku/references/iscilik-alacaklari.md`.

### 4.7 Raporlar arası çelişki
- Aynı türden bütün raporlar tek tabloda: tarih, düzenleyen, sonuç, gerekçe özeti.
- Fark küçük değilse (§3.6) 🟠, talep "çelişkiyi giderecek yeni rapor".
- Hükme esas alınan raporu tercih gerekçesi yoksa bu, kanun yolunda da kullanılır → `kanun-yollari-dilekce`.
- Uzman görüşü (HMK m.293) ile bilirkişi raporu arasındaki çelişkinin aynı kurala tabi olup olmadığı `[incele]`.

---

## 5. Akış
1. Raporları oku. Her biri için: tür, tarih, düzenleyen, sorulan sorular, sonuç. **Okunan** satırı zorunlu; okunamayan sayfa `[okunamadı]` (ORTAK-KURALLAR.md §10).
2. Süre (§0); ret sebebi varsa bir haftalık süre ayrıca.
3. Usul denetimi (§3).
4. Türe göre denetim (§4).
5. Yeniden hesap: önce aracı raporun **kendi** girdileriyle çalıştır; sonra hatalı bulunan girdiyi düzelterek ikinci kez (ör. doğru PSD, doğru yönetmelik). Araç yoksa §1 kuralı.
6. Fark tablosu ve çelişki tablosu.
7. Talep türü (HMK m.281/1): ek rapor / açıklama / yeni bilirkişi (§3.4 tek rapor ilkesi) / bilirkişinin reddi.
8. Devir (§7).

---

## 6. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## Bilirkişi raporu denetimi — [dosya] — [rapor türü], [rapor tarihi]

Tebliğ: [tarih] · İtiraz son günü: [tarih] [🔴 kalan gün < 7] · Ret süresi (varsa): [tarih]
Okunan: [sayfa / okunan sayfa] · Kaynaklar: soorgla ✓ · Hesap araçları: [çalıştı / yok — yalnız yöntem denetimi]

### Özet
[2-4 cümle: en ağır bulgu, toplam fark, önerilen talep türü]

### Usul bulguları
| # | Konu | Bulgu | Önem | Dayanak |

### Fark tablosu
| # | Kalem | Raporun değeri | Yeniden hesap | Fark | Lehe / aleyhe | İtiraz cümlesi | Dayanak |
| | **Toplam** | | | | | | |

Yeniden hesap girdileri: [araç, alt seçim, girdi özeti — rapordakinden farklı olan girdi kalın]

### Raporlar arası çelişki (varsa)
| Rapor | Tarih | Düzenleyen | Sonuç | Not |

### Denetlenemeyenler
[girdi raporda yok / araç yok / tablo okunamadı — her biri ayrı satır]

### Önerilen talep (HMK m.281/1)
[ek rapor | açıklama | yeni bilirkişi (gerekçe) | bilirkişinin reddi (m.272, ayrı süre)]
Önerilen kurum (kusur / maluliyet): [ATK / İTÜ / KGM Fen Heyeti / üniversite ABD] [incele]

**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı]
```

- **Lehe hatalar da yazılır.** Karşı tarafın itirazını öngörmek için gerekir; dilekçede kullanıp kullanmamak avukatın takdiridir `[incele]`.
- Tutarlar araçtan geldiği gibi, iki hane TL; araç yoksa sütun boş kalır. Her tutar `[doğrula — bilirkişiyle teyit edin]` etiketi alır (SKILL.md "Hesaplarda kurallar").
- Lehe küçük bir hesap hatası raporun bütününü güvenilmez kılmaz; önem kalemin tutarına göre verilir.

---

## 7. Devir
- Bulgular, fark tablosu ve talep türü bu dosyanın; dilekçe metni ve süre doğrulaması `../../hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md`'nin işidir (ORTAK-KURALLAR.md §14).
- Devir özeti: dosya ve taraflar, rapor künyesi ve tebliğ tarihi, son gün, usul bulguları, fark tablosu (itiraz cümlesi sütunuyla), talep türü, atıflar (etiketleriyle), açık sorular.
- Dilekçe becerisi itiraz cümlelerini HMK m.281 ayrımına göre (eksik / belirsiz / çelişkili) gruplar; hesap hatası en başta ve somut tutarla.
- 🔴/🟠 bulgular dilekçede gerekçesiz düşürülemez (ORTAK-KURALLAR.md §8, §14).
- Hüküm verilmiş ve çelişki giderilmemişse aynı tablo istinaf/temyiz sebebi olarak `kanun-yollari-dilekce`'ye taşınır.
- Raporların ve tebliğlerin tarih sırası → `../../dava-kronolojisi/SKILL.md`.
- Maluliyet raporu sağlık verisidir (KVKK m.6); çıktıda tanı ayrıntısı yalnız denetim için gerektiği kadar yer alır.

## Sık hatalar
- Araç yanıt vermediğinde "yaklaşık" bir yeniden hesap yazmak. Yazılmaz; yöntem denetimiyle yetinilir.
- Raporun yerine kusur ya da maluliyet oranı önermek.
- Usul eksikliği varken yalnız "ek rapor" istemek; ya da tek rapor ilkesini gözetmeden gerekçesiz "yeni bilirkişi" istemek.
- Ret sebebini görüp bir haftalık süreyi itiraz süresiyle karıştırmak.
- Ceza dosyasındaki rapor ile hukuk raporunu karşılaştırmadan kusur itirazı yazmak.
- Yalnız arama alıntısıyla çekilen kararı "yerleşik içtihat" diye sunmak.

## Kaynak
Eski YAML karşılığı yok; `hukuk-yargilamasi-dilekce` bilirkişi itirazı dosyasının esas tarafı olarak yazıldı.
