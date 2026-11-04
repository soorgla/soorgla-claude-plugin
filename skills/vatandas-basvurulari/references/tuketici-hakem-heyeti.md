# Tüketici hakem heyeti başvurusu

Ayıplı mal (bozuk telefon, beyaz eşya, araç parçası) ya da ayıplı hizmet (kötü yapılan tadilat, eksik verilen hizmet) nedeniyle satıcı veya sağlayıcıyla anlaşamayan tüketicinin **tüketici hakem heyetine** (THH) başvurusu. Haksız fatura, abonelik ücreti, iade edilmeyen bedel gibi uyuşmazlıklar da aynı yoldan gider.

## Ne zaman kullanılır — önce tutarı kontrol et

1. Uyuşmazlığın **değerini** belirle (genelde fatura tutarı ya da istenen iade/tazminat tutarı).
2. `legal_get_social_parameters  tur: "thh_parasal_sinir"` ile **başvuru tarihindeki yılın** sınırını çek. Dönem alanı başvuru yılını kapsamıyorsa `legal_search_official_gazette  query: "Tüketici Hakem Heyetleri Yönetmeliğinin 6 ncı Maddelerinde Yer Alan Parasal Sınırların Artırılmasına İlişkin Tebliğ"  sort_by: "date_desc"` ile o yılın tebliğini bul.
3. Değer sınırın **altındaysa** THH'ye başvuru **zorunludur**; **üstündeyse** THH'ye başvurulamaz → tüketici mahkemesi (önce zorunlu arabuluculuk). 
4. Tek uyuşmazlıkta tutar sınırı aşıyorsa **aşan kısımdan feragat ederek** THH'ye başvurulabilir; başvuru tarihindeki sınır esas alınır.  Feragat edilen kısım bir daha istenemeyebilir → `[incele]`, kullanıcıya açıkça söyle.

Tutarı beceri metnine yazma; her seferinde çek. Eski YAML'daki sabit tutar (2025 yılı için) bayattır.

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Ayıplı maldan sorumluluk zamanaşımı: **2 yıl** (konut/tatil amaçlı taşınmazda **5 yıl**) | Malın **teslimi** (ayıp sonra çıksa bile) | 6502 m.12/1  | Sözleşme ya da kanunla daha uzun süre olabilir (garanti belgesi ayrı konu). |
| İspat kolaylığı (karine): **6 ay** | Teslim | 6502 m.10/1  | Eski YAML "ilk 6 ay (bazı durumlarda 1 yıl)" diyordu; madde metninde 1 yıl yok. |
| Ücretsiz onarım / ayıpsız misliyle değişim: **en çok 30 iş günü** (konut/tatil taşınmazında 60 iş günü) | Talebin satıcı/üretici/ithalatçıya yöneltilmesi | 6502 m.11/4  | Hizmette: yeniden görme/onarım **30 iş günü** (m.15/4).  |
| THH kararına **itiraz: 2 hafta** | Kararın **tebliği** | 6502 m.70/3  | Hak düşürücü niteliktedir `[doğrula]`. 🔴 avukat eşiği. |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]` işaretle.

## Zorunlu unsurlar

- **Başvuru yeri:** tüketicinin **yerleşim yerindeki** ya da **tüketici işleminin yapıldığı yerdeki** THH. THH olmayan yerde başvuru **ilçe kaymakamlığına** yapılır, kaymakamlık yetkili heyete iletir.  Eski YAML "İkametgâhın bulunduğu yer Kaymakamlığı/Valiliği Hakem Heyeti" diyordu; işlemin yapıldığı yer seçeneği eksikti.
- **Başvuru yolu:** e-Devlet kapısı üzerinden Tüketici Bilgi Sistemi (TÜBİS) ile elektronik başvuru ya da tüketici hakem heyetine elden veya posta yoluyla dilekçe; şahsen ya da avukat aracılığıyla. 
- **Seçimlik hak açıkça seçilmeli.** Ayıplı malda: (a) sözleşmeden dönme (bedel iadesi), (b) ayıp oranında bedel indirimi, (c) ücretsiz onarım, (ç) ayıpsız misliyle değişim; satıcı tüketicinin seçtiğini yerine getirmekle yükümlüdür. Onarım/değişim satıcı için orantısız güçlük doğuruyorsa tüketici dönme ya da indirime yönelir. Seçimlik hakla birlikte TBK'ya göre **tazminat** da istenebilir.  Ücretsiz onarım ve değişim üretici veya ithalatçıya karşı da kullanılabilir; satıcı, üretici ve ithalatçı müteselsilen sorumludur. 
- Ayıplı hizmette seçimlik haklar: hizmetin yeniden görülmesi, eserin ücretsiz onarımı, bedelden indirim, sözleşmeden dönme. 
- Tüketici sözleşme kurulurken ayıbı biliyorsa ya da bilmesi bekleniyorsa sözleşmeye aykırılık yoktur.  Kullanıcıya "Satın alırken bu kusuru biliyor muydunuz?" diye sor.
- Zorunlu unsurlar: başvuranın adı-soyadı, T.C. kimlik no, adresi (vekil varsa onun adı, vergi kimlik no ve adresi), uyuşmazlık konusu, talep, **TL cinsinden** uyuşmazlık değeri, şikâyet edilene ilişkin bilgiler. Ayrıca olay, istenen seçimlik hak, deliller (fatura, servis fişi, yazışma), imza. Eksik zorunlu bilgide heyet yedi gün süre verir. 

## Karar ve sonrası (kullanıcıya anlat)

- THH kararı **tarafları bağlar**; ilam gibi icra yoluyla yerine getirilir. THH vekâlet ücretine hükmetmez. 
- Tüketici aleyhine karar çıkarsa tebligat ve bilirkişi ücretlerini Bakanlık karşılar. 
- Tüketici lehine karara firma itiraz edip karar iptal edilirse tüketici aleyhine vekâlet ücretine hükmedilebilir; ancak THH'ye sunulmayan bir belge mahkemede sunulduğu için iptal olursa tüketici aleyhine gider ve vekâlet ücreti yüklenemez.  → Kullanıcıya "elinizdeki **bütün** belgeleri THH'ye şimdi verin" de.

## 🔴 Avukat eşikleri

- Tutar sınırın üstünde (tüketici mahkemesi + zorunlu arabuluculuk; arabuluculuk THH görevindeki uyuşmazlıklarda uygulanmaz). 
- THH kararına itiraz edilecek ya da firma itiraz etti (tüketici mahkemesi kararı kesin; tek şans).
- Konut, araç gibi yüksek değerli mal; sağlık zararı, yaralanma (tazminat ve ürün sorumluluğu).
- Aynı uyuşmazlık için zaten dava açılmış ya da başka bir heyete başvurulmuş (derdestlik). 
- Satıcı tüketici değil de "ticari satış" savunması yapıyor (alıcının tüketici sayılıp sayılmadığı tartışmalı).

## Görüşme soruları

1. Ne satın aldınız ya da hangi hizmeti aldınız? **Teslim tarihi** ve fatura tutarı?
2. Kusur ne zaman ortaya çıktı? Satın alırken biliyor muydunuz?
3. Satıcıya/servise başvurdunuz mu? Tarihleri ve cevapları? Servis fişi var mı?
4. Ne istiyorsunuz: **para iadesi**, **indirim**, **ücretsiz onarım**, **yenisiyle değişim** (hizmette: yeniden yapılması)? Ek bir zararınız var mı?
5. Satıcı/firmanın tam unvanı ve adresi (faturada yazar); vergi no/MERSİS biliniyorsa.
6. Yerleşim yeriniz ve satın alma yeri (hangi THH'ye başvurulacağı için).
7. Elinizdeki belgeler: fatura, garanti belgesi, servis formu, e-posta/SMS yazışmaları, fotoğraf.
8. Adınız-soyadınız, T.C. kimlik no, adres, telefon, e-posta.

## soorgla çağrıları

```
legal_get_social_parameters  tur: "thh_parasal_sinir"                    # ÖNCE BU
legal_search_official_gazette  query: "Tüketici Hakem Heyetleri Yönetmeliğinin 6 ncı Maddelerinde Yer Alan Parasal Sınırların Artırılmasına İlişkin Tebliğ"  sort_by: "date_desc"
legal_get_statute_article  law_no: "6502"  article_no: "10" | "11" | "12" | "15" | "68" | "70"
legal_search_statute_semantic  mevzuat_no: "6502"  sorgu: "tüketici mahkemesinde dava şartı arabuluculuk"   # m.73/A
legal_search_cases  mahkeme: "yargitay"  daire: "3. Hukuk Dairesi"
    sorgu: "<olay, ör. teslimden itibaren altı ay içinde ortaya çıkan ayıp, ispat yükü satıcıda>"
    tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```
Yargıtay 3. HD tüketici uyuşmazlıklarında güncel karar veriyor (ör. Yargıtay 3. HD E.2024/425 K.2025/1083, 24.02.2025 — gerekçesinde 6502 m.10 karinesini açıklıyor: teslimden itibaren altı ay içinde bildirilen/dava edilen ayıpta ayıpsızlığın ispatı satıcıda, sonrasında ayıbın ispatı alıcıda; ayrıca ayıp hile ile gizlenmişse satıcı zamanaşımından yararlanamaz). Bu karar daire görev dağılımını göstermez: dosyanın hangi daireye gideceğini sabit varsayma, `legal_search_cases`'i daire filtresiz çalıştırıp güncel kararların dairesine bak. 

## İskelet — THH başvuru dilekçesi

```
[___] TÜKETİCİ HAKEM HEYETİ BAŞKANLIĞI'NA
(Heyet yoksa: [___] KAYMAKAMLIĞI'NA — yetkili tüketici hakem heyetine iletilmek üzere)

BAŞVURAN (TÜKETİCİ) : [Ad Soyad], T.C. No: [___]
Adres / Tel / e-posta : [___]

KARŞI TARAF         : [Firma unvanı]
Adres               : [___]   Vergi No / MERSİS: [___ bilinmiyorsa boş]

UYUŞMAZLIK DEĞERİ   : [___] TL

KONU : [tarih]'de satın aldığım [mal/hizmet] ayıplı olduğundan 6502 sayılı Kanun
       m.[11 / 15] uyarınca [seçilen hak] talebimdir.

AÇIKLAMALAR :
1. [Tarih]'de karşı taraftan [mal/hizmet]'i [tutar] TL'ye satın aldım (Ek-1 fatura).
   Mal tarafıma [teslim tarihi]'de teslim edildi.
2. [Tarih]'de [kusur] ortaya çıktı. [Teslimden itibaren altı ay içinde ise:] Ayıp teslimden
   itibaren altı ay içinde ortaya çıktığından teslim tarihinde var olduğu kabul edilir
   (6502 m.10/1).
3. [Tarih]'de satıcıya/servise başvurdum (Ek-2). [Sonuç: onarılmadı / 30 iş günü geçti /
   talebim reddedildi].
4. Satın alırken bu ayıptan haberdar değildim.

HUKUKİ NEDENLER : 6502 sayılı Tüketicinin Korunması Hakkında Kanun m.[10, 11 / 15, 68]
[ve ilgili diğer maddeler — yalnız MCP'den çekilenler]

DELİLLER : Fatura, garanti belgesi, servis formları, yazışmalar, fotoğraflar, gerektiğinde
bilirkişi incelemesi.

SONUÇ VE İSTEM : Başvurumun kabulü ile [seçilen hak: ödediğim [___] TL'nin iadesine /
malın ayıpsız misliyle değiştirilmesine / ücretsiz onarımına / [___] TL indirime]
karar verilmesini arz ederim.

                                                    Tarih : [___]
                                                    Ad Soyad / İmza
EKLER :
1. Fatura
2. [___]
```
"Bedel iadesi / misliyle değişim" gibi **iki hakkı birden** istem olarak yazma; eski YAML'daki "iadesine / ürünün yenisi ile değiştirilmesine" kalıbı seçimin belirsiz kalmasına yol açıyordu. Kullanıcı kararsızsa farkı sade dille anlat, seçmesini iste.

## Sık hatalar

- Sınırın üstündeki uyuşmazlıkla THH'ye gitmek ya da eski yılın sınırını kullanmak.
- Seçimlik hakkı belirtmemek ya da iki hakkı birlikte istemek.
- Teslim tarihini yazmamak (6 ay karinesi ve 2 yıl zamanaşımı buna bağlı).
- Belgeleri THH'ye vermeyip mahkemeye saklamak (m.70/6 sonucu).
- THH kararına itirazın 2 haftalık süresini kaçırmak.
- Garanti süresi ile ayıptan sorumluluk süresini (zamanaşımı) karıştırmak `[incele]`.

