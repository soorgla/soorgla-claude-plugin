# Trafik kazası sonrası ilk adımlar ve sigortaya başvuru

Trafik kazası geçiren vatandaşın kaza yerinde ve sonraki günlerde yapacakları: tutanak, fotoğraf ve delil, karşı tarafın trafik sigortasına (ZMSS) yazılı başvuru, cevap gelmezse ya da düşük ödeme teklif edilirse Sigorta Tahkim Komisyonu. Bu dosya **yol gösterir ve başvuru yazısının taslağını** verir; hukuki değerlendirme (kim sorumlu, ne istenebilir, ne kadar) `tazminat-haksiz-fiil` becerisindedir.

## Ne zaman kullanılır
- "Kaza yaptım ne yapmalıyım", "tutanak nasıl doldurulur", "karşı tarafın sigortasına nasıl başvururum", "sigorta cevap vermiyor", "sigorta çok az para teklif etti", "değer kaybı başvurusu".
- Kullanıcı avukat değil. Avukatsa doğrudan `tazminat-haksiz-fiil`'e geç.

**Bu dosyaya girmeyenler:**
- Ölüm, ağır yaralanma, maluliyet → 🔴 avukat eşiği (aşağıda); hesap ve hak sahipliği `tazminat-haksiz-fiil`.
- Kaza aynı zamanda iş kazasıysa (servis, görev sırasında) → `sosyal-guvenlik-sgk`.
- Taksirle yaralama şikâyeti ve ceza dosyası → `../../ceza-ve-infaz-dilekce/references/davaya-katilma.md`.
- Dava dilekçesi → `hukuk-yargilamasi-dilekce` (avukat önerilir).

---

## Süre tablosu

| Ne | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Sigortanın yazılı başvuruya cevap süresi | Başvurunun sigortaya ulaşması | KTK m.97: **15 gün** | Bu süre dolmadan ya da cevap beklenmeden dava açılmaz.  |
| Sigorta Tahkim'e gitmeden bekleme | Sigortaya başvuru | 5684 m.30/13: **15 iş günü** | KTK'daki 15 **takvim** günü ile karıştırma; tahkim için iş günü sayılır.  |
| Hakem kararına itiraz | Kararın bildirimi | 5684 m.30/12: **10 gün** | 🔴 hak düşürücü; parasal eşik altındaki kararlar kesin olabilir, eşiği madde metninden çek `[doğrula]`. |
| Yetersiz anlaşmanın iptali | Anlaşma tarihi | KTK m.111: **2 yıl** | Açıkça yetersiz tutarda imzalanan ibra ve anlaşma için.  |
| Tazminat zamanaşımı | Zararı ve sorumluyu öğrenme / kaza | KTK m.109 | Ayrıntı ve hesap `../../tazminat-haksiz-fiil/references/zamanasimi-ve-dava-sartlari.md`; 30 günden az kaldıysa 🔴. |

`legal_calculate_deadline` bu süreleri tanımaz: olay tarihinin **ertesi gününden** say, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle ve "son güne bırakmayın" de. İş günü hesabında hafta sonu ve resmî tatiller atlanır.

---

## 1. Kaza yerinde (kullanıcıya adım adım anlat)

Kazaya karışanların kanuni yükümlülükleri (KTK m.81): 
1. **Durun, güvenliği sağlayın.** Aracı ek tehlike yaratmayacak şekilde durdurun; reflektör, dörtlü flaşör.
2. **Yaralı varsa 112'yi arayın.** Yaralıyı uzman değilseniz yerinden oynatmayın.
3. **Kaza yerini değiştirmeyin** — trafik ve can güvenliğini etkilemiyorsa. İz ve kanıtlar sorumluluğun belirlenmesi için önemlidir.
4. **Kimlik, ehliyet, ruhsat ve sigorta poliçesi bilgilerini** karşılıklı gösterin ve not alın (poliçe tarihi ve numarası dahil).
5. **Kazayı polise / jandarmaya bildirin** ve gelene kadar ya da izin almadan ayrılmayın. Yalnız maddi hasar varsa ve **herkes anlaşırsa** kendi aranızda tutanak tutup ayrılabilirsiniz (aşağıda §2).
6. **Ölümlü ya da yaralanmalı kazada zabıtanın izni olmadan zaruret dışında olay yerinden ayrılmak suçtur** (hapis cezası ve ehliyetin geri alınması); maddi hasarlı kazada da anlaşma yoksa idari para cezası var. Ceza tutarını beceriye yazma; gerekiyorsa m.81'i çek.
7. Park hâlindeki araca ya da sahibi olmayan bir mala zarar verdiyseniz sahibini bulun; bulamazsanız üzerine yazılı not bırakın ve polise bildirin (m.81/e).

**Fotoğraf ve delil (yerinde, araçlar kaldırılmadan):**
- Genel görünüm: iki aracın konumu, yol, şeritler, levhalar, ışıklar (4-5 farklı açıdan).
- Hasar: her araçta yakından ve uzaktan; plaka okunacak şekilde.
- Fren izi, cam kırıkları, yol üzerindeki parçalar; mümkünse ölçü (adım sayısı bile yazılabilir).
- Tanıkların adı ve telefonu.
- Yakındaki kameralar (işyeri, MOBESE, araç içi kamera): kayıtlar birkaç gün içinde silinebilir; sahibinden **hemen** saklamasını isteyin. Gerekirse delil tespiti → `../../tazminat-haksiz-fiil/references/talep-yazisi-ve-delil-koruma.md` (avukat önerilir).

---

## 2. Anlaşmalı tutanak (yalnız maddi hasar)

- Yalnız maddi hasar varsa ve bütün sürücüler polise gerek görmüyorsa "Maddi Hasarlı Trafik Kazası Tespit Tutanağı" birlikte doldurulur. Bu yolla ayrılırsanız **sonradan polisten tutanak isteyemezsiniz.** 
- Şu hâllerde **polis / jandarma çağırın**, anlaşmalı tutanak tutmayın: yaralı ya da ölü var; karşı sürücünün ehliyeti yok; karşı aracın trafik sigortası yok; alkol ya da uyuşturucu şüphesi; kamu aracı ya da kamu malına zarar; tek taraflı kaza; anlaşamıyorsunuz. 
- **İmzalamadan önce:**
  - Krokiyi birlikte çizin; araçların yönü, şeridi ve çarpışma noktası doğru mu?
  - "Kazanın oluş şekli" kutucuklarını **kendiniz** okuyun; size söylenen değil, olan işaretlensin.
  - Karşı tarafın el yazısıyla **sizin** bölümünüzü doldurmasına izin vermeyin.
  - Fotoğraf çekin (anlaşmalı tutanakta da önerilir).
  - Bir nüsha sizde kalsın; fotoğrafını çekin.
- Tutanak **kusur oranı belirlemez**; oranı sigorta ya da bilirkişi belirler. "Kusur oranım ne olur?" sorusuna oran verme: "Kusur oranını bilirkişi belirler" de ve `../../tazminat-haksiz-fiil/references/kaza-tutanagi-ve-kusur.md` ile bilirkişiye sorulacakları çıkar.

---

## 3. Sonraki günler

1. **Hastaneye gidin** — kazada yaralandıysanız ya da sonradan ağrı başladıysa hemen. Kaza günü alınan rapor, sonraki talepler için en önemli belgedir. Tedavi giderlerini kural olarak SGK karşılar (KTK m.98). 
2. **Kendi kasko şirketinize** (varsa) haber verin; poliçenizdeki bildirim süresine bakın.
3. **Karşı aracın trafik sigortasını öğrenin:** tutanaktaki poliçe bilgisi; yoksa SBM sorgusu (e-Devlet / sigorta şirketi) `[doğrula]`.
4. **Ekspertiz ve onarım:** hasar tespiti yapılmadan aracı onarıma vermeyin; parça ve işçilik ayrı yazılı fatura isteyin; onarım öncesi ve sonrası fotoğraf çekin.
5. **Belge dosyası:** tutanak, fotoğraflar, ehliyet-ruhsat fotokopisi, ekspertiz, fatura, hastane belgeleri, kira faturası (ikame araç kiraladıysanız), yazışmalar.

---

## 4. Karşı tarafın trafik sigortasına yazılı başvuru (KTK m.97)

- Trafik sigortasından istenecek tutar için **dava ya da tahkimden önce sigortaya yazılı başvuru zorunludur.** Sigorta 15 gün içinde cevap vermez ya da cevap talebi karşılamazsa dava açılabilir ya da Sigorta Tahkim'e gidilebilir. 
- Başvuru yolu: sigorta şirketinin genel müdürlüğüne iadeli taahhütlü posta, KEP ya da şirketin yazılı başvuru kanalı. **Telefon görüşmesi başvuru sayılmaz**; ulaştığını gösteren belge saklanır.
- **Trafik sigortasından istenemeyenler** (kullanıcıya baştan söyle):
  - **Manevi tazminat** (KTK m.92/f) → yalnız sürücü ve araç sahibinden.
  - **İkame araç, kazanç kaybı, aracın çalışamaması** gibi dolaylı zararlar (KTK m.92/k) → sürücü ve araç sahibinden.
  - Kendi kusurunuza düşen kısım.
  
- **Değer kaybı** trafik sigortasından istenebilir (araç trafikten çekilmediyse / hurdaya ayrılmadıysa). Sigortanın formülle hesapladığı tutar mahkemenin kabul ettiği yöntemle aynı olmayabilir → `../../tazminat-haksiz-fiil/references/arac-hasari-deger-kaybi-ve-pert.md`.
- Teminat limitleri **kaza ya da poliçe tarihine** göre değişir; tutarı beceriye yazma, `legal_get_social_parameters` (`tur: "zmss_maddi_arac_basi"`) ile çek; dönmüyorsa `[doğrula]`.

---

## 5. Sigorta cevap vermedi, reddetti ya da az ödedi

| Durum | Yol |
|---|---|
| 15 iş günü içinde cevap yok ya da kısmi / tam ret | **Sigorta Tahkim Komisyonu** başvurusu (sigorta şirketi sisteme üye olmasa bile trafik sigortasında başvurulabilir) ya da dava.  |
| Sigorta ödeme teklif etti, "ibraname" imzalatmak istiyor | **İmzalamadan önce bekleyin.** "Tüm haklarımdan feragat ederek ibra ederim" yazan belge ileride ek talebi zorlaştırır. Tutar açıkça yetersizse anlaşma 2 yıl içinde iptal edilebilir (KTK m.111), ama bu dava gerektirir. Kabul ediyorsanız "**ihtirazi kayıtla**, kısmi ödeme olarak aldım" yazmayı düşünün `[incele]` → `../../tazminat-haksiz-fiil/references/talep-yazisi-ve-delil-koruma.md` §C. 🔴 |
| Daha önce mahkemeye ya da tüketici hakem heyetine başvurdunuz | Aynı uyuşmazlık için Sigorta Tahkim'e başvurulamaz (5684 m.30/14).  |

- **Sigorta Tahkim başvurusu:** başvuru ücreti, parasal eşikler ve formlar Komisyonun güncel duyurusundan alınır; beceriye yazılmaz `[doğrula]` (araçta yok). Hakemler kural olarak dört ay içinde karar verir (5684 m.30/16). Hakem heyeti kararına itiraz süresi **10 gün** (m.30/12) 🔴.
- **Karşı aracın sigortası yok ya da araç kaçtı:** bedensel zararlar için Güvence Hesabı'na başvuru; **araç hasarı kural olarak Güvence Hesabı'ndan alınamaz** (5684 m.14).  Araç hasarı için sürücü ve araç sahibine başvuru.
- **Tüketici hakem heyeti bu iş için değildir** (trafik sigortası uyuşmazlığı); kullanıcı THH diyorsa Sigorta Tahkim'e yönlendir `[incele]`.

---

## 6. "Hasar danışmanı" ve aracılar

Kazadan sonra size ulaşan, "değer kaybınızı biz alırız", "yüzde şu kadar komisyonla" diyen kişi ya da şirketler olabilir. Kullanıcıya sakin ve genel bir uyarı ver; belirli bir firmayı itham etme:
- Mahkeme ve hakem önünde başkasının hakkını dava etmek ve takip etmek, bunlara ait evrakı düzenlemek **baroya kayıtlı avukatlara** aittir; kişi kendi işini kendisi takip edebilir (Avukatlık Kanunu m.35).  Karşınızdakinin avukat olup olmadığını baro sicilinden kontrol edebilirsiniz.
- **İmzalamadan önce okuyun:** vekâletname, "alacak temliki" (hakkınızı başkasına devretme) ya da "hizmet sözleşmesi". Alacağınızı devrederseniz sigortadan çıkacak paranın tamamı size gelmeyebilir ve sonradan geri dönmek zor olabilir `[incele]`.
- Ücret, komisyon ve masrafın yazılı olmasını isteyin; "peşin masraf" talebine dikkat.
- Trafik sigortasına başvuruyu (§4) ve çoğu durumda Sigorta Tahkim başvurusunu kendiniz yapabilirsiniz; ama zarar büyükse ya da bedensel zarar varsa bir avukatla görüşmeniz önerilir. **"Avukata gerek yok" deme.**

---

## 🔴 Avukat eşikleri
- Ölüm, ağır yaralanma, kalıcı sakatlık (maluliyet) iddiası.
- Sigorta ödeme karşılığında ibraname / feragat belgesi imzalatmak istiyor.
- Kusur oranına itiraz edilecek; ya da sigorta "kaza kurgudur / hasar kazayla uyumsuz" diyor.
- Karşı aracın sigortası yok, araç kaçtı ya da çalıntı.
- Hakem heyeti kararı geldi ve itiraz düşünülüyor (10 günlük süre).
- Zamanaşımına 30 günden az kaldı.
- Kaza aynı zamanda iş kazası.

Bu durumlarda taslağı yine verebilirsin; en üste "Bu durumda tek başınıza ilerlemeniz risklidir" uyarısını ve nedenini koy, baro **adli yardım bürosunu** hatırlat.

## Görüşme soruları
1. Kaza ne zaman, nerede oldu? Yaralanan var mı?
2. Polis geldi mi, yoksa aranızda tutanak mı tuttunuz? Tutanakta ne yazıyor?
3. Fotoğraf, kamera kaydı, tanık var mı?
4. Karşı aracın plakası ve trafik sigortası şirketi (poliçe no) belli mi?
5. Aracınızın kaskosu var mı? Araç onarıldı mı, pert mi?
6. Sigortaya yazılı başvuru yaptınız mı; tarihi, cevabı?
7. Sigorta bir ödeme teklif etti mi; bir belge imzaladınız mı?
8. Aracınız kaç gün kullanılamadı; araç kiraladınız mı?

## soorgla çağrıları
```
legal_get_statute_article  law_no: "2918"  article_no: "81" | "92" | "97" | "98" | "109" | "111"
legal_get_statute_article  law_no: "5684"  article_no: "30" | "14"
legal_get_statute_article  law_no: "1136"  article_no: "35"
legal_get_social_parameters  tur: "zmss_maddi_arac_basi"
legal_check_holiday   # son gün ve iş günü sayımı
```

## İskelet — trafik sigortasına KTK m.97 başvurusu (vatandaş)

İçerik ve asgari unsurlar `../../tazminat-haksiz-fiil/references/talep-yazisi-ve-delil-koruma.md` "KTK m.97 başvurusunun asgari içeriği" ile aynıdır; burada sade dille:

```
[Sigorta şirketinin unvanı]
Genel Müdürlüğü / Hasar Birimi
[adres / KEP adresi: ___]

KONU: Karayolları Trafik Kanunu m.97 uyarınca yazılı başvuru —
      kaza tarihi [___], karşı araç plakası [___], poliçe no [___]

Başvuran: [ad soyad], T.C. kimlik no [___], adres [___], telefon [___], e-posta [___]
Araç: [plaka], ruhsat sahibi [___]

[Tarih]'te [yer]'de, şirketinizce trafik sigortası yapılan [plaka] plakalı aracın karıştığı
kazada aracımda hasar oluşmuştur. Kaza [polis tutanağı / anlaşmalı tutanak] ile tespit
edilmiştir.

Talep ettiğim kalemler:
1. Araç hasarı (onarım bedeli): [___] TL — ekspertiz / fatura ektedir
2. Değer kaybı: [___] TL [ya da: tespitini talep ediyorum]
3. [Diğer: çekici, otopark, ekspertiz ücreti — belgeli]: [___] TL

Ödemenin aşağıdaki hesaba yapılmasını talep ederim:
IBAN: [___] — Hesap sahibi: [___]

Ekler: tutanak, fotoğraflar, ruhsat ve ehliyet fotokopisi, ekspertiz raporu,
       fatura, kimlik fotokopisi, [___]

[Tarih] — [Ad soyad, imza]
```
- Tutarları kullanıcı verir; bilinmiyorsa "tespitini talep ediyorum" yazılır, **tutar uydurulmaz**.
- Bedensel zarar başvurusu (maluliyet, iş göremezlik) bu iskeletle yapılmaz → 🔴 avukat eşiği.
- Gönderim yolunu ve tarihini kayda geçir; "Bu süreleri süre defterine ekleyeyim mi?" → `../../sure-takibi/SKILL.md`.

## Sık hatalar
- Anlaşmalı tutanağı okumadan, karşı tarafın doldurduğu hâliyle imzalamak.
- Yaralanmalı kazada "aramızda hallederiz" deyip polis çağırmamak ya da olay yerinden ayrılmak.
- Sigortaya telefonla başvurmuş olmayı yazılı başvuru sanmak.
- Manevi tazminatı ya da ikame araç bedelini trafik sigortasından istemek.
- İbranameyi hemen imzalamak.
- Sigorta Tahkim için 15 takvim günü saymak (iş günüdür).
- "Kusur oranım %X" diye kesin konuşmak.

## Kaynak
Yeni dosya (2026-11-01). Eski YAML karşılığı yok. Hukuki ayrıntılar `tazminat-haksiz-fiil` becerisinin referanslarından (trafik-kazasi-ve-zmss, kaza-tutanagi-ve-kusur, arac-hasari-deger-kaybi-ve-pert, talep-yazisi-ve-delil-koruma) özetlendi; madde atıfları orada doğrulandı.
