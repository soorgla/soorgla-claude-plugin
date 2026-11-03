# Şikâyet, tebligat ve icra mahkemesi

**Ne zaman kullanılır:** icra ya da iflas dairesinin bir işlemi kanuna aykırı ya da olaya uygun değil (İİK m.16); ödeme emri ya da icra emri usulsüz tebliğ edildi; ilamlı takipte icranın geri bırakılması isteniyor; icra mahkemesi kararına istinaf/temyiz düşünülüyor. Haciz, satış ve ihale şikâyetlerinin ayrıntısı → `haciz-satis-istihkak-ve-sira-cetveli.md`.

Temel ilke: icra mahkemesi dar yetkili, belgeye dayalı, hızlı bir mercidir. Esas hakkında kesin hüküm vermez; şikâyetle ileri sürülemeyecek bir iddia (borcun varlığı, ödeme belgesi olmayan itfa) genel mahkemeye gider. Kanunun "mahkemeye bıraktığı" hususlar şikâyete konu olmaz.

---

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Şikâyet: **7 gün** | İşlemin **öğrenildiği** tarih | İİK m.16/1 | `legal_calculate_deadline` `iik_complaint` hesaplar. |
| Süresiz şikâyet | — | İİK m.16/2 | Kanundaki süresiz hâle ek olarak, kamu düzenine aykırı işlemlere karşı süresiz şikâyet doktrinde ve Yargıtay uygulamasında kabul edilen istisnadır (ör. 12. HD'nin derdest/mükerrer takibi kamu düzenine ilişkin sayıp süresiz şikâyetle iptal ettiği uygulama). **Dikkat:** meskeniyet (m.82/1-12) gibi haczedilmezlik şikâyetleri 12. HD'ye göre 7 günlük süreye tabidir, süresiz sayma. Somut işlemin süresiz şikâyete konu olup olmadığını `legal_search_cases` (`daire: "12. Hukuk Dairesi"`) ile o işlem türü için ara ve tam metni oku `[incele]`. |
| İcranın geri bırakılması (ilamlı): **7 gün** | İcra emrinin tebliği | İİK m.33/1 | Yalnız zamanaşımı, itfa, imhal; itfa/imhal resmî ya da onaylı belgeyle. İcra emrinin tebliğinden **sonra** doğan itfa, imhal ya da zamanaşımı **her zaman** ileri sürülebilir (m.33/2). |
| Takibin kesinleşmesinden sonra itfa/mühlet | Her zaman | İİK m.71 | Zamanaşımında m.33/a kıyasen. |
| İcra mahkemesi kararına **istinaf: iki hafta** | Kararın tebliği | İİK m.363/1 | Değer/miktar parasal sınırı aşmalı; bazı karar türleri istinafa kapalı (aşağıda). |
| BAM kararına **temyiz: iki hafta** | Kararın tebliği | İİK m.364/2 (7499/3) | Parasal sınır m.364/1. |

**Kanun yolu ve icra:** istinaf ve temyiz satıştan başka icra işlemlerini durdurmaz. Kötüniyetli kanun yolu başvurusunda HMK m.422'deki yaptırım.

---

## Kesinlik ve kanun yolu sınırı

- İstinaf için değer ya da miktarın kanundaki tabanın yeniden değerlenmiş tutarını **geçmesi** gerekir (m.363/1); temyiz için BAM kararında ayrı sınır (m.364/1). İki sınır da her takvim yılı başında yeniden değerleme oranıyla artar ve **şikâyet başvurusunun yapıldığı ya da davanın açıldığı tarihteki** miktar esas alınır.
  - Eski metin "hükmün verildiği" tarihi esas alıyordu; 7550 (RG 04.06.2025) "davanın açıldığı veya şikâyet başvurusunun yapıldığı" tarihe çevirdi, 7571 ikinci fıkrayı yeniden yazdı. 7550 yayımı tarihinde (**04.06.2025**) yürürlüğe girdi ve ek m.1'in üçüncü fıkrasını da kaldırdı; 7571 m.3 **25.12.2025**'te yürürlüğe girdi. İkisi de İİK'ya geçiş hükmü eklemedi. 04.06.2025'ten önce verilmiş kararlarda hangi metnin (hüküm tarihi mi, dava/şikâyet tarihi mi) uygulanacağı açık sorudur: çalışma anında `legal_search_cases` (`mahkeme: "yargitay"`, `tarih_baslangic: "2025-06-04"`, sorgu "ek 1 parasal sınır davanın açıldığı tarih 7550 geçiş") ile ara; bulamazsan iki sonucu da göster ve `[ARAŞTIRMA GEREKLİ: ek m.1 geçiş]` yaz.
- **Güncel tutar:** `legal_get_social_parameters`'ta icra mahkemesi sınırı kalemi **yok**. HMK sınırlarını (`istinaf_kesinlik_siniri`, `temyiz_siniri`) buraya uygulama. Tutarı bilmiyorsan `[doğrula — güncel İİK m.363/364 sınırı]` yaz ve kullanıcıdan iste.
- **Değere bakılmaksızın istinafa kapalı kararlar** (m.363/1'de sayılanlar): m.85'in uygulanma biçimi, vekâlet ücreti, m.103 davetiyesi, yediemin ücreti ve değiştirilmesi, muhafaza şekli, kıymet takdirine şikâyet, ihale teminatı, satışın durdurulması, satış ilanının iptali, süresinde satış istenmemesi nedeniyle düşme, m.263, iflas idaresi oluşumu ve işlemleri, iflas idare memuru ücreti, m.36 icranın geri bırakılması. Kıymet takdirine şikâyette verilen karar ayrıca kesindir (m.128/a son fıkra).

İstinaf/temyiz dilekçesinin metni → `kanun-yollari-dilekce`; bu dosyadaki süre ve sınır bilgisini oraya taşı.

---

## Tebligat kontrol listesi

1. **E-tebligat zorunluları** (kamu idareleri, tüm özel hukuk tüzel kişileri, noterler, avukatlar, sicile kayıtlı arabulucu ve bilirkişiler vb.) için tebligat elektronik yapılır; talep eden gerçek kişiye de adres verilir. Tebliğ, adrese ulaştığı tarihi izleyen **5. günün sonunda** yapılmış sayılır.
2. **E-tebligat adresinin kendisinden habersiz açılması:** 12. HD, vakıf adına üst kurumca açılıp kendisine usulünce bildirilmeyen e-tebligat adresine yapılan tebliği usulsüz saydı; usulsüz tebliğde gecikmiş itiraz şartları oluşmaz, öğrenme tarihi tebliğ tarihi olarak belirlenir.
3. **Tebligat K. m.32:** usulsüz tebliğ, muhatap tebliğe muttali olmuşsa geçerlidir; muhatabın beyan ettiği öğrenme tarihi tebliğ tarihidir. Dilekçede "gecikmiş itiraz" denmiş olsa da hâkim bunu m.32 şikâyeti olarak nitelendirir.
4. **m.21/1 (adreste bulunmama ya da imtina: evrak muhtara, ihbarname kapıya, komşuya haber)**, **m.21/2 (adres kayıt sistemindeki adres: muhatap orada hiç oturmamış olsa bile muhtara teslim, kapıya yapıştırma)** ve **m.35 (daha önce usulüne uygun tebligat yapılmış adresten ayrılıp yenisini bildirmeyen ve adres kayıt sisteminde de adresi bulunmayan kişiye eski adrese kapıya asma)** şartları. Yapıştırma tarihi tebliğ tarihidir. Mazbatadaki şerh eksikse usulsüzlük.
5. **Tebliğ hiç yapılmamışsa** (yalnız UYAP'tan öğrenme) usulsüz tebliğ şikâyetinin konusu yoktur; m.32 uygulanamaz.
6. Tebliğ tarihi düzeltilince itiraz süresi o tarihten işler: şikâyetle birlikte **itirazı da** yap.

---

## Şikâyet kontrol listesi

1. İşlem nedir, kim yaptı (icra müdürü, iflas idaresi, satış memuru)? Hangi tarihte öğrenildi? 🔴
2. Şikâyet konusu kanuna aykırılık mı, hadiseye uygunsuzluk mu, hakkın yerine getirilmemesi mi (süresiz)?
3. Kanunun mahkemeye bıraktığı bir husus mu (borcun varlığı, istihkak, sıra cetvelinde alacağın esası)? Öyleyse şikâyet değil dava.
4. Şikâyet ehliyeti ve hukuki yarar.
5. Yetkili icra mahkemesi: işlemi yapan icra dairesinin bulunduğu yer.
6. Harç ve gider avansı: `legal_get_social_parameters` (`tur: "harc_basvurma_sulh"`).
7. Tedbir: şikâyet kendiliğinden icrayı durdurmaz; icra mahkemesinden tedbir (takibin/satışın durdurulması) iste `[incele]` — m.17-18'de açık tedbir hükmü yok, dayanağı ayrıca araştır. İcra mahkemesi işleri ivedidir, basit yargılama usulü uygulanır; duruşmasız işlerde 10 gün içinde karar verilir (m.18). Şikâyet kabul edilirse işlem bozulur ya da düzeltilir (m.17).
8. Kanun yolu sınırı ve kapalı karar türleri (yukarıda).

---

## Görüşme soruları

1. Şikâyet edilen işlem ve tarihi? İşlemi nasıl öğrendiniz (tebligat, UYAP, haciz sırasında)?
2. Ödeme emri / icra emri nasıl tebliğ edildi? Mazbata ya da e-tebligat kaydı elinizde mi?
3. İlamlı takipte: ilamdan sonra ödeme, mühlet ya da zamanaşımı var mı? Belgesi resmî ya da onaylı mı?
4. Takip değeri (kanun yolu sınırı için)?
5. Hangi tedbir gerekli (satışın durdurulması, haczin kaldırılması)?

## soorgla çağrıları

```
legal_get_statute_article law_no: "2004" article_no: "16" | "17" | "18" | "33" | "71" | "363" | "364" | "ek 1"
legal_get_statute_article law_no: "7201" article_no: "7/a" | "21" | "32" | "35"
legal_calculate_deadline kural_kodu: "iik_complaint" baslangic_tarihi: <öğrenme tarihi>
legal_check_holiday tarih: <son gün>
legal_search_cases mahkeme: "yargitay" daire: "12. Hukuk Dairesi" tarih_baslangic: <son 3 yıl>
    sorgu: "<ör. e-tebligat adresi borçlunun bilgisi dışında açılmışsa ödeme emri tebliği usulsüzdür>"
legal_search_cases mahkeme: "bam" sorgu: "<olay>" # icra mahkemesi kararlarının çoğu BAM'da kesinleşir
legal_get_social_parameters tur: "harc_basvurma_sulh"
```

## Çıktı iskeleti

```markdown
## Şikâyet değerlendirmesi: [şikâyetçi] — [icra dairesi, dosya no]
### Sonuç
### Süre
| İşlem | Öğrenme/tebliğ | Son gün | Dayanak | Durum |
### Şikâyet sebebi ve dayanağı (madde metninden)
### Tebligat incelemesi (mazbata/e-tebligat kaydı)
### Tedbir talebi
### Kanun yolu (değer, sınır [doğrula], kapalı karar türü mü)
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Usulsüz tebliğde "gecikmiş itiraz" yoluna gitmek; doğrusu m.32 şikâyeti ve öğrenme tarihinin tespiti.
- Borcun varlığına ilişkin iddiayı şikâyetle ileri sürmek.
- İcra mahkemesi kararına HMK sınırını uygulamak; ya da 7571 öncesi "hüküm tarihi" kuralıyla sınırı hesaplamak.
- İstinafın satışı durdurduğunu varsayıp başka işlemler için tedbir istememek.
- Eski YAML'daki "Usulsüz tebligat → hacizler düşer" genellemesi: usulsüzlük tebliğ tarihini düzeltir; sonraki işlemlerin akıbeti ayrıca değerlendirilir `[incele]`.
