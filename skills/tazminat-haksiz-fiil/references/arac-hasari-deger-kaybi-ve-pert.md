# Araç hasarı: değer kaybı, pert (tam hasar) ve araç mahrumiyeti

## Ne zaman kullanılır
Trafik kazasında **araçtaki maddi zarar**: değer kaybı talebi, aracın pert sayılması ve sigortacının eksik ödemesi (pert farkı), araç serviste ya da pert iken kullanılamamasından doğan zarar (ikame araç, kazanç kaybı). Sorumlular, KTK m.97 başvurusu, Sigorta Tahkim ve süreler `trafik-kazasi-ve-zmss.md`'dedir; bu dosya yalnız bu üç kalemin **yöntemini, kimden isteneceğini ve delilini** verir. Bilirkişi raporu geldiyse denetim → `bilirkisi-raporu-denetimi.md` §4.5.

---

## 1. Hesap aracı durumu

`legal_calculate_vehicle_damage` (`tur: deger_kaybi | pert_farki | mahrumiyet`). Girdiler: değer kaybında `emsal_hasarsiz[]`, `emsal_onarilmis[]` ya da `bilirkisi_deger_kaybi`, karşılaştırma için `rayic`, `hasar_tutari`, `km`; pertte `iliski`, `rayic_kaynaklari[]`, `onarim_bedeli`, `sovtaj`/`satis_bedeli`, `sovtaj_secimi`; mahrumiyette `kalem`, `sure{gun, kaynak}`, `emsal_kira_gunluk` ya da `hasilat_gunluk[]` ve giderler. Kusur `karsi_kusur` (0-1). Araç listede yoksa ya da yanıt vermiyorsa:
- tutar **elle hesaplanmaz**, "yaklaşık" değer yazılmaz; çıktı yöntem, girdi listesi ve kimden istenecek tablosuyla sınırlı kalır;
- Genel Şartlar formülünün katsayıları, rayiç bantları ve oransal üst sınırları beceriye **yazılmaz**; araç bunları parametre tablosundan okur (`hesap.gs_deger_kaybi_katsayi`). Araç yokken formül karşılaştırması gerekiyorsa `legal_search_official_gazette` (`query: "Zorunlu Mali Sorumluluk Sigortası Genel Şartları"`, `search_in: "title"`) ile ilgili RG metnini çek, katsayıyı oradan göster `[doğrula]`;
- ZMSS araç başı maddi teminat limiti `legal_get_social_parameters` (`tur: "zmss_maddi_arac_basi"`) ile alınır; satır yoksa `trafik-kazasi-ve-zmss.md`'deki RG yolu.

Rayiç, onarılmış değer, sovtaj ve makul süre **ekspertiz ya da bilirkişi girdisidir**; araç olsa da bunları üretmez. Sabit uyarı: "Rayiç, sovtaj ve makul süre ekspertiz ya da bilirkişi tespitine bağlıdır; hesap girdi değerlerle yapılmıştır."

---

## 2. Değer kaybı

### 2.1 Yöntem: piyasa farkı, formül değil
- **Ölçüt (4. HD):** aracın kaza tarihindeki **hasarsız ikinci el piyasa değeri** ile **onarılmış hâldeki ikinci el piyasa değeri** arasındaki fark. Bu ölçüte uymayan rapora dayanılması bozma sebebi.
- **Gözetilecekler:** marka, model, yaş, kilometre, donanım, hasar miktarı, hasarlı parçaların niteliği, onarım türü (değişen / onarılıp boyanan), **önceki kazalar ve etkileri**. Önceki hasar değer kaybını ortadan kaldırmaz, hesapta gözetilir.
- **Genel Şartlar formülü bağlayıcı değil.** KTK m.90'daki Genel Şartlara yollama AYM E.2019/40 ve E.2021/82 ile iptal edildi; bilirkişi iki hesap yapmış ve formül seçilmişse bu bozma sebebi. Ayrıntı `trafik-kazasi-ve-zmss.md` "Mevzuatın güncel durumu". Formül sigortacının dava öncesi ödemesinde ve tahkim pratiğinde hâlâ kullanılır; bu yüzden **karşılaştırma** olarak gösterilir, sonuç olarak değil.
- Formülün sürümü **poliçe tarihine** göre seçilir (2015 ve 2020 sürümleri; Genel Şartlar geçici m.1).
- Genel Şartlardaki **teminat dışı hâller** (ör. mini onarım, vidalı parça, mülkiyeti değişen araç, belirli ticari araçlar, yabancı plaka) ve oransal üst sınırların mahkemede ayrıca uygulanıp uygulanmadığı açık `[incele]`.

### 2.2 ZMSS kapsamı
- Değer kaybı ZMSS maddi teminatı içinde; **trafikten çekilen ya da hurdaya ayrılan** aracın değer kaybı dışında (KTK m.92/l).
- **Pert araçta ayrıca değer kaybı istenmez**; rayiç zaten tam değeri karşılar `[incele]`.
- Değer kaybı ve araç mahrumiyeti özel ve teknik bilgi gerektirir; davacının dava öncesi tutarı kesin belirlemesi beklenemez (4. HD E.2025/8637). 31.07.2026'dan sonra açılan davada belirsiz alacak davası yok → kısmi dava ve HMK m.109/4 (`zamanasimi-ve-dava-sartlari.md`).

### 2.3 Delil
Ekspertiz raporu · onarım faturası (parça ve işçilik ayrı) · onarım öncesi ve sonrası fotoğraflar · TRAMER / SBM hasar kaydı (önceki hasarlar) · tarihli emsal ilan ekran görüntüleri (aynı marka, model, yıl, km bandı).

---

## 3. Pert (tam hasar) ve pert farkı

### 3.1 Önce ilişkiyi ayır
Görüşme sorusu: **"Hasarı kendi kaskonuz mu, karşı tarafın trafik sigortası mı ödüyor?"**

| | Kasko (sözleşme) | ZMSS / haksız fiil |
|---|---|---|
| Borçlu | Kendi kasko sigortacısı | Karşı aracın ZMSS sigortacısı, sürücü, işleten |
| Kusur | Aranmaz (teminat dışı hâller hariç) | Karşı tarafın kusur oranıyla sınırlı |
| Sovtaj (hurda) | **Sigortalı seçer:** hurdayı sigortacıya bırakırsa rayicin tamamı; kendinde tutarsa rayiç − sovtaj | Kural olarak zarar görende kalır → rayiç − sovtaj |
| Üst sınır | Poliçe | ZMSS araç başı maddi limit; aşan kısım sürücü ve işletenden |
| Esas | Kasko Genel Şartları ve poliçe klozu | KTK, TBK haksız fiil |

İkinci görüşme sorusu: **"Hurda araç sizde mi kalsın, sigortaya mı devredilsin?"**

### 3.2 Tam hasar ne zaman?
- **Kasko Genel Şartları:** güncel metinde (m.3.3.2.2) onarım masrafı aracın riziko tarihindeki değerini **aşması ve aynı zamanda** eksper raporuyla onarım kabul etmez hâle geldiğinin tespiti hâlinde tam hasar; iki koşul birlikte aranır. Eski metin (B.3.3.1.2.1) "**ya da**" diyordu; poliçe tarihindeki metni kontrol et `[incele]`.
- **Ekonomiklik (HGK E.2017/1102 K.2020/905):** onarım ekonomikse onarım bedeli; değilse kaza tarihindeki ikinci el rayiçten sovtaj düşülerek gerçek zarar `[çekildi ama desteği doğrulayın]`. Uygulamadaki ölçüt: onarım bedeli, rayiç ile sovtaj farkını aşıyorsa onarım ekonomik değil.
- İki ölçüt farklı sonuç verebilir (onarım rayici aşmıyor ama rayiç − sovtaj farkından yüksek). 4. HD E.2023/11811 K.2025/10223 böyle bir dosyada rayiç, onarım ve sovtajın yeniden belirlenmesi için bozdu; Daire onarım rayici aşmadığı için "pert total uygulamasına tabi tutulması mümkün değildir" dedi ama üç değerin ayrı ayrı belirlenmesi için bozdu; ekonomiklik ölçütünü açıkça tartışmadı `[incele]`.
- Sigortacıların "hasar rayicin belirli bir yüzdesini aşınca pert" uygulaması **yargısal ölçüt değildir**.

### 3.3 Rayiç ve sovtaj
- **Rayiç:** kaza (riziko) tarihindeki **ikinci el piyasa** değeri; hüküm tarihine güncellenmez, zaman farkı faizle karşılanır `[incele]`. Kaynağını etiketle: ekspertiz / bilirkişi / kasko değer listesi / emsal ilan; kaynaklar arasındaki farkı göster.
- Kasko poliçesinde "kasko değer listesi bedelini geçemez" klozu: 4. HD E.2022/14373 K.2025/10772 piyasa rayicine dayanan hakem kararını onadı; kısa onama, genel ilke sayma `[incele]`.
- Vergiler: ikinci el piyasa değeri vergiler dahil fiyattır; ÖTV muafiyetiyle alınmış ya da KDV indirebilen ticari araçta farklı uygulama var `[incele]`.
- **Sovtaj (ZMSS):** hasarlı araç zarar görende kaldıysa zarar (rayiç − sovtaj) × kusur. Araç satıldıysa gerçek satış bedelinin sovtaj yerine geçtiği `[incele]`. Onarılıp satılan araçta "satış bedeli ile onarım birlikte değerlendirilir, zarar yok" görüşüne dayanma: 4. HD E.2022/16746 K.2025/164 (kasko) bu görüşle verilen kararı kaldıran ve onarım farkına hükmeden İtiraz Hakem Heyeti kararını onadı.

### 3.4 Hesabın kuruluşu (tutarlar araçtan)
```
gerçek zarar = rayiç − sovtaj (ZMSS; kaskoda hurda sigortalıda)
               | rayiç (kaskoda hurda sigortacıya)
talep = gerçek zarar × karşı tarafın kusur oranı (yalnız ZMSS / haksız fiil)
sigortacı borcu = min(talep, ZMSS araç başı maddi limit) − sigortacının ödediği
aşan kısım → sürücü ve işleten
pert farkı = max(0, olması gereken − sigortacının ödediği)
```
Kusur oranı yoksa ya da tartışmalıysa → `kaza-tutanagi-ve-kusur.md`; oran uydurulmaz. ZMSS limitinin **poliçe mi kaza tarihine** göre alınacağı açık `[doğrula]`.

Ayrıca istenen kalemler: çekici, otopark, ekspertiz ücreti (belgeli; ZMSS'de maddi teminat içinde), araç mahrumiyeti (§4), faiz (`legal_get_legal_interest_rates`; kaskoda temerrütten, ZMSS'de başvuru ve KTK m.99 süresine göre `[incele]`).

---

## 4. Araç mahrumiyeti (ikame araç, kazanç kaybı)

### 4.1 Kimden istenir

| | Özel araç (kullanım yoksunluğu) | Ticari araç (kazanç kaybı) | Kiralama şirketi |
|---|---|---|---|
| Zarar | Emsal ikame araç kirası − kullanılmadığı için yapılmayan giderler | Günlük **net** kazanç × süre | Muadil aracın kira bedeli × süre |
| Fiilen kiralamış olmak gerekir mi | **Hayır**; sırf kullanımdan mahrum kalmak da zarardır | — | Muadil aracın verildiği ve faturası |
| Sürücü ve işleten (TBK m.49; KTK m.85) | ✔ | ✔ | ✔ |
| **ZMSS sigortacısı** | ✘ dolaylı zarar | ✘ | ✘ |
| Kasko (kendi aracı) | Poliçede ikame araç teminatı varsa, teminat ölçüsünde | Poliçeye göre | Poliçeye göre |
| İMM (karşı aracın ihtiyari sorumluluk sigortası) | Poliçe şartlarına göre `[incele]` | | |

- **7327 sonrası kazalar:** KTK m.92/k dolaylı zararları açıkça teminat dışında sayar.
- **7327 öncesi kazalar:** Yargıtay aynı sonuca "dolaylı zarar" nitelemesiyle ulaşıyor (4. HD E.2021/26464 K.2022/11237; 17. HD E.2014/17381). AYM E.2019/40 iptalinden sonra bu nitelemenin dayanağı tartışmaya açık `[incele]`.
- **Kasko:** belirleyici olan poliçe klozu (4. HD E.2022/6957 K.2024/2653: poliçe gereği teminattaki ikame araç bedeli kabul).

### 4.2 Süre: hataların çoğu burada
- **Onarılan araç:** aracın hasar durumuna göre **makul onarım süresi**; teknik konu, bilirkişiye bırakılır (4. HD E.2020/1587 K.2020/4597).
- **Zarar verene yüklenmeyen süreler:** zarar görenin geç onarıma vermesi, servis yoğunluğu, aracın kiracıya geç teslimi (4. HD E.2020/1587); kasko şirketinin ya da anlaşmalı servisin eksiğinden doğan gecikme (17. HD E.2019/2260 K.2020/5521: servise giriş-çıkış süresini doğrudan makul süre sayan rapor bozuldu).
- **Tek başına yetmeyen kaynaklar:** kooperatifin "çalışmadı" bildirimi, eksper raporundaki iş günü, davacının iddia ettiği süre, işletme defterindeki gün sayısı `[çekildi ama desteği doğrulayın]`.
- **Pert araç:** süre onarım süresi değil, **aynı vasıfta bir aracın satın alınması için gereken makul süre**dir; kazadan sigorta ödemesine kadar geçen süre kendiliğinden esas alınmaz (17. HD E.2015/14277, 29.02.2016).
- Yurt dışından parça bekleme ve ayıplı / geç onarım sürelerinin makul süreye girip girmediği açık `[incele]`.

### 4.3 Günlük bedel
- **Özel araç:** aynı vasıftaki aracın kiralama bedeli (emsal, aynı sınıf ve segment); zarar görenin aracını kullansaydı yapacağı zorunlu giderler (ör. yakıt) düşülür. Delil yoksa mahkeme TBK m.50/2 ile hakkaniyete uygun bedel tayin eder; beceri ve araç bu hâlde **tutar üretmez**, "takdir gerekli" yazar (4. HD E.2021/26464 K.2022/11237). Yalnız teklif belgesiyle emsal araştırması aynı şey değildir.
- **Ticari araç:** net kazanç = hasılat − yakıt, bakım, amortisman. Delil: esnaf odası, kooperatif ya da durak yazısı, **vergi dairesi gelir kayıtları**. Gerekçesiz yüksek günlük kazanç kabul edilmiyor. Malik kendi aracının şoförüyse, araç için hesaplanan kazanç kaybından ayrı şoför kazanç kaybı hesaplanmaz. Onarım süresi fatura tarihinden değil makine mühendisi bilirkişiden belirlenir.
- **Kiralama şirketi:** muadil aracın kira bedeli × makul onarım süresi; uzun süreli kiralamada işleten sıfatı ayrı sorun `[incele]`.
- Talep = zarar × karşı tarafın kusur oranı; TBK m.52 indirimleri ayrıca `[incele]`. Ticari araçta avans / yasal faiz ayrımı `[incele]`.

### 4.4 Delil
Servis giriş-çıkış belgesi · eksper raporu · kira faturası ya da emsal kira teklifleri · oda / durak / kooperatif yazısı · vergi dairesi gelir kayıtları · TRAMER kaydı · pert ise sigorta ödeme tarihi ve yeni araç alım belgesi.

---

## 5. Görüşme soruları
1. Kasko mu, karşı tarafın ZMSS'si mi; ikisi birden mi? Poliçe tarihleri?
2. Araç onarıldı mı, pert mi? Pert ise hurda kimde kalacak; sigortacı ne ödedi, neye dayanarak?
3. Aracın yaşı, kilometresi, önceki hasarları (TRAMER)?
4. Ekspertiz yapıldı mı; parça ve işçilik ayrı mı; onarım faturası var mı?
5. Araç ticari mi (taksi, minibüs, kamyon), özel mi, kiralama şirketinin mi?
6. Araç serviste kaç gün kaldı; gecikmenin sebebi parça, servis yoğunluğu ya da sigorta onayı mıydı?
7. Bu sürede araç kiralandı mı; fatura var mı? Kaskoda ikame araç teminatı var mı?
8. Ticari araçsa oda / kooperatif yazısı ve vergi kaydı alınabilir mi?

## soorgla çağrıları
```
legal_get_statute_article law_no: "2918" article_no: "90" | "92" | "97" | "99"
legal_search_cases mahkeme: "yargitay" daire: "4. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. değer kaybı hasarsız ikinci el piyasa değeri onarılmış hali arasındaki fark>"
    sorgu: "<ör. araç mahrumiyeti makul onarım süresi aynı vasıftaki aracın kira bedeli>"
    sorgu: "<ör. pert araç rayiç değerden sovtaj bedelinin mahsubu>"
legal_search_cases daire: "17. Hukuk Dairesi" # eski emsal (mahrumiyet süresi)
legal_get_social_parameters tur: "zmss_maddi_arac_basi"
legal_search_official_gazette query: "Zorunlu Mali Sorumluluk Sigortası Genel Şartları" search_in: "title"
legal_get_legal_interest_rates
legal_calculate_vehicle_damage tur: "deger_kaybi" | "pert_farki" | "mahrumiyet"
```

## Çıktı iskeleti
```markdown
## Araç hasarı değerlendirmesi — [plaka/araç] — [kaza tarihi]
### Sonuç
### İlişki ve borçlular
| Kalem | Kasko | ZMSS | Sürücü / işleten | Dayanak |
### Değer kaybı
- Yöntem: piyasa farkı (hasarsız rayiç − onarılmış rayiç); formül yalnız karşılaştırma
- Girdiler: [rayiç kaynağı, km, önceki hasar, onarım türü] · Tutar: [araçtan / araç yok] [doğrula]
### Pert ve pert farkı
- Tam hasar testleri: [Genel Şartlar / ekonomiklik — sonuçlar ayrı]
- Rayiç [kaynak] · Sovtaj [kim tutuyor] · Kusur [oran, kaynak] · Limit [araçtan]
### Araç mahrumiyeti
- Tür: [özel / ticari / kiralama] · Süre: [makul onarım / makul temin, kaynak] · Günlük bedel: [emsal / net kazanç]
- ZMSS: ✘ dolaylı zarar → talep sürücü ve işletene
### Delil listesi ve eksikler
### Süreler (trafik-kazasi-ve-zmss.md tablosundan)
**Şimdi ne yapalım?** [karar ağacı]
```

## Sık hatalar
- Değer kaybını Genel Şartlar formülüyle sonuçlandırmak; ya da formülü "mahkeme de böyle hesaplar" diye sunmak.
- Önceki hasarı "değer kaybı yok" gerekçesine çevirmek.
- Pert araçta ayrıca değer kaybı istemek.
- Kaskoda sovtaj seçimini sormadan rayiçten sovtaj düşmek.
- Araç mahrumiyetini ZMSS sigortacısından istemek.
- Servis giriş-çıkış süresini ya da sigorta ödeme tarihini doğrudan makul süre saymak.
- Ticari araçta brüt hasılatı kazanç kaybı saymak; şoför için ayrıca kazanç kaybı eklemek.
