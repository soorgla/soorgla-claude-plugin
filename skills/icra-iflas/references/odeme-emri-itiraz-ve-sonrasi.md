# Ödeme emrine itiraz ve sonrası (itirazın kaldırılması, itirazın iptali)

**Ne zaman kullanılır:**
- Borçlu vekili ödeme emri aldı: itiraz edilmeli mi, nasıl, hangi riskle?
- Alacaklı vekiline itiraz tebliğ edildi: itirazın kaldırılması mı, itirazın iptali davası mı?
- İnkâr tazminatı ve dava şartı arabuluculuk soruluyor.

Avukatsız vatandaşın basit Örnek 7 itirazı bu dosyanın işi değildir → `../../vatandas-basvurulari/references/icra-itirazi.md`. Kambiyo takibinde itiraz icra mahkemesine yapılır; usulü bu dosyada, şikâyet tarafı `sikayet-tebligat-ve-icra-mahkemesi.md`'de.

---

## Triyaj: ödeme emri geldiğinde (borçlu tarafı)

Upstream "demand-received" akışından uyarlandı: ödeme emri bir taleptir; hepsine aynı tepki verilmez. Önce alanları çıkar, sonra seçenekleri tartıp **birini öner**, kararı avukata bırak.

**1. Ödeme emrinden çıkar:** icra dairesi ve dosya no; örnek no (7 / 10 / 13 / 14 / iflas yolu); tebliğ şekli ve tarihi (posta, e-tebligat, m.21, m.35); alacaklı ve vekili; asıl alacak, faiz (oran, başlangıç), masraf; dayanak belge; varsa rehin.

**2. Tebliğ tarihini kesinleştir:** e-tebligat muhatabın elektronik adresine ulaştığı tarihi izleyen 5. günün sonunda yapılmış sayılır; usulsüz tebliğde süre öğrenme tarihinden başlar → `sikayet-tebligat-ve-icra-mahkemesi.md`. 

**3. Esas değerlendirmesi (görüş değil, yönlendirme için yapılandırılmış okuma):** borç var mı, ne kadarı var, ödendi mi, zamanaşımı, imza borçluya ait mi, yetki doğru mu, faiz doğru mu. Sonuç: **güçlü itiraz / kısmi itiraz / zayıf itiraz / itiraz anlamsız** `[incele]`.

**4. Seçenekler** (birini öner, iki cümle gerekçe):

| Seçenek | Ne zaman | Bedeli |
|---|---|---|
| A. Tam itiraz | Borç yok, belge alacaklıyı desteklemiyor | Alacaklı itirazın kaldırılması/iptalini kazanırsa **en az %20 inkâr tazminatı** (m.67/2, m.68 son fıkra) |
| B. Kısmi itiraz | Borcun bir kısmı tartışmasız | İtiraz edilen kısmın **cihet ve miktarı açıkça** yazılmazsa itiraz edilmemiş sayılır (m.62) |
| C. İtiraz etmeden ödeme/taksit + menfi tespit ya da istirdat | Borç tartışmalı ama haciz riski yüksek | İstirdat süresi ödemeden itibaren 1 yıl; teminat şartları → `menfi-tespit-istirdat-ve-ihtiyati-haciz.md` |
| D. İtiraz etmeme | Borç açık; itiraz yalnız zaman kazandırır | Takip kesinleşir, haciz başlar; ama tazminat riski yok |

**5. İmza:** senede dayalı takipte imza borçluya ait değilse bunu **ayrıca ve açıkça** yaz; kambiyoda 5 gün içinde icra mahkemesine; haksız imza inkârında kambiyoda alacağın %10'u para cezası. 

---

## Süre tablosu

| Süre | Başlangıç | Merci | Dayanak |
|---|---|---|---|
| Genel haciz ödeme emrine itiraz: **7 gün** | Ödeme emrinin tebliği | İcra dairesi | İİK m.62/1 |
| Kambiyo: borca, imzaya, yetkiye itiraz ve "kambiyo senedi değil" şikâyeti: **5 gün** | Ödeme emrinin tebliği | **İcra mahkemesi** | İİK m.168/3-5  |
| Kira takibinde itiraz: **7 gün** (TBK'daki 6 günlük mühlet hâlinde **3 gün**) | Tahliye ihtarlı ödeme emrinin tebliği | İcra dairesi | İİK m.269  |
| İflas yoluyla takipte itiraz: **7 gün** | Ödeme emrinin tebliği | İcra dairesi | İİK m.155  |
| Gecikmiş itiraz: **3 gün** | Engelin kalktığı gün | İcra mahkemesi | İİK m.65 (vatandas-basvurulari aynı tur) |
| İtirazın kaldırılması: **6 ay** | İtirazın alacaklıya tebliği | İcra mahkemesi | İİK m.68/1  |
| İtirazın iptali davası: **1 yıl** | İtirazın alacaklıya tebliği | Genel mahkeme (asliye hukuk / ticaret / iş / tüketici) | İİK m.67/1  |
| İhtiyati haciz varsa itirazın kaldırılması ya da dava: **7 gün** | İtirazın alacaklıya tebliği | İcra mahkemesi / mahkeme | İİK m.264/2  |

İtirazın iptali süresi geçerse alacaklı genel hükümlerle dava açabilir ama takip düşer ve inkâr tazminatı istenemez `[incele]`. 

---

## Alacaklı tarafı: itirazın kaldırılması mı, itirazın iptali mi?

| Ölçüt | İtirazın kaldırılması (m.68) | İtirazın iptali (m.67) |
|---|---|---|
| Belge | İmzası ikrar edilmiş ya da noterce onaylı borç ikrarı içeren senet; resmî daire/yetkili makam belgesi | Her türlü delil |
| Merci | İcra mahkemesi, belgeyle sınırlı inceleme | Genel mahkeme, tam yargılama |
| Süre | 6 ay | 1 yıl |
| Arabuluculuk | Dava şartı değil `[doğrula]` | Ticari, işçilik, kira ve tüketici alacaklarında **dava şartı olabilir** (aşağıda) |
| Kesin hüküm | Maddi anlamda kesin hüküm oluşturmaz: borçlu icra mahkemesinde ileri sürüp ispat edemediği itiraz ve def'ileri menfi tespit davasında yeniden ileri sürebilir | Kesin hüküm |
| Tazminat | Esasa ilişkin nedenle kabulde borçlu, aynı nedenle redde alacaklı en az %20 | Borçlunun itirazı haksızsa borçlu; takip haksız ve kötü niyetliyse alacaklı en az %20 |

**Kural:** belge m.68'deki niteliği taşımıyorsa itirazın kaldırılması **istenemez**; doğru yol itirazın iptali davasıdır (eski YAML bu ayrımı doğru vurguluyordu). Borçlu itirazını m.68'deki nitelikte bir belgeyle desteklerse talep reddolunur. Borçlunun gösterdiği belgedeki imzayı alacaklı inkâr eder ve imza ona ait çıkarsa alacaklı belgedeki miktarın %10'u para cezasına mahkûm edilir.  İmza incelemesinin usulü İİK m.68/a'da: adi senette imza itirazda reddedilmişse alacaklı itirazın tebliğinden itibaren **6 ay** içinde itirazın geçici kaldırılmasını ister; borçlu duruşmaya mazeretsiz gelmezse ya da imza ona ait çıkarsa para cezası; talebin kabulü ya da reddi hâlinde karşı tarafa tazminat (oranlar madde metninden). 

### Dava şartı arabuluculuk (itirazın iptali, menfi tespit, istirdat)

- **Ticari:** TTK m.5/A'nın kapsamı 7445 ile "konusu bir miktar para olan alacak, tazminat, **itirazın iptali, menfi tespit ve istirdat** davaları"nı içerecek şekilde genişletildi; menfi tespit ve istirdat için **1.9.2023 ve sonrasında açılan** davalara uygulanır. 
- **İşçilik alacağı:** 7036 m.3/1'e "Bu alacak ve tazminatla ilgili itirazın iptali, menfi tespit ve istirdat davaları hakkında birinci cümle hükmü uygulanır" cümlesi eklendi; aynı geçiş tarihi.  Esas için `../../is-hukuku/SKILL.md`.
- **Kira:** kira ilişkisinden kaynaklanan uyuşmazlıklarda (İİK'ya göre ilamsız icra yoluyla tahliye hükümleri hariç) dava şartı arabuluculuk, 1.9.2023'ten itibaren.  Ayrıntı `../../kira-hukuku/SKILL.md`.
- **Tüketici:** 6502 m.73/A tüketici mahkemesinde görülen **tüm** uyuşmazlıklarda dava şartı arabuluculuk getirir; istisnalar: tüketici hakem heyetinin görevine giren uyuşmazlıklar, hakem heyeti kararına itiraz, m.73/6 ve m.74 davaları, taşınmazın aynından doğanlar. Hakem heyeti sınırı altındaki alacakta itirazın iptalinin hangi yolda görüleceği `[incele]`. 
- **Süre etkisi:** arabulucuya başvurudan son tutanağa kadar geçen süre zamanaşımı ve hak düşürücü süreyi durdurur; itirazın iptalinin 1 yıllık süresinin hesabında bunu göster. 
- **Arabuluculuğa başvuran borçlu aleyhine takip:** başvurudan sonra başvuran aleyhine aynı uyuşmazlıkla ilgili takip yapılırsa başvuran, son tutanaktan itibaren **iki hafta** içinde menfi tespit açıp İİK m.72/2'deki tedbiri isteyebilir. 

---

## Kontrol listesi

### Borçlu vekili
1. Tebliğ tarihi ve usulü (e-tebligat 5. gün, m.21/2, m.35) 🔴
2. Takip yolu doğru mu? Kambiyo vasfı, örnek no, yetki.
3. İtiraz merci doğru mu (icra dairesi / icra mahkemesi)?
4. Kısmi itirazda miktar ve cihet açık mı?
5. İmza itirazı ayrı ve açık mı?
6. Faiz ve fer'ilere itiraz yazıldı mı?
7. Yetki itirazı yetkili daireyi göstererek esasla birlikte yapıldı mı? `[doğrula]`
8. İnkâr tazminatı riski müvekkile yazılı anlatıldı mı? 🟠
9. Yurt içi adres bildirildi mi?
10. İtiraz belgesi alındı mı?

### Alacaklı vekili
1. İtirazın tebliğ tarihi → 6 ay / 1 yıl / ihtiyati haciz varsa 7 gün 🔴
2. Belge m.68 niteliğinde mi? Değilse doğrudan itirazın iptali.
3. Uyuşmazlık ticari, işçilik, kira ya da tüketici mi? → önce arabuluculuk 🔴
4. Görevli mahkeme (ticaret / asliye hukuk / iş / tüketici / sulh) ve yetki.
5. İnkâr tazminatı için alacağın **likit** olduğu gösterilebiliyor mu? Ölçüt: alacağın miktarı belli ve sabit ya da borçlu tarafından bütün unsurları bilinen/bilinmesi gereken, borçlunun yalnız başına hesaplayabileceği bir alacak olması. Yalnızca bilirkişi incelemesi yapılmış olması alacağı likit olmaktan çıkarmaz (ör. ticari kayıt ve faturalardan hesaplanabilen alacak). Hak tartışmalıysa tazminata hükmedilmez `[incele]`. 
6. Haciz isteme süresi itirazla durdu; dava kesinleşince yeniden işler (m.78/2).

---

## Görüşme soruları

1. Ödeme emrinin örnek numarası, tebliğ tarihi ve şekli?
2. Dayanak belge ve alacağın kaynağı? Belgedeki imza müvekkile mi ait?
3. Borcun ne kadarını kabul ediyorsunuz? Ödeme belgesi var mı?
4. Taraflar tacir mi? İşçi-işveren ilişkisi mi? Kira mı? Tüketici işlemi mi? (arabuluculuk ve görevli mahkeme)
5. İtiraz alacaklıya hangi tarihte tebliğ edildi? (alacaklı tarafı)
6. Takipten önce ya da sonra ihtiyati haciz konuldu mu?
7. Arabuluculuk başvurusu yapıldı mı, son tutanak tarihi?

## soorgla çağrıları

```
legal_get_statute_article  law_no: "2004"  article_no: "62" | "65" | "66" | "67" | "68" | "68/a" | "168" | "170" | "264"
legal_get_statute_article  law_no: "7201"  article_no: "7/a" | "21" | "32" | "35"
legal_get_statute_article  law_no: "7036"  article_no: "3"
legal_list_statute_articles  law_no: "6102"  article_query: "arabulucuya başvurulmuş olması dava şartıdır"   # TTK 5/A
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2023/04/20230405-3.htm"     # 7445 (5/A, 18/B yedek kaynak)
legal_search_cases  mahkeme: "yargitay"  daire: "11. Hukuk Dairesi"  tarih_baslangic: <son 3 yıl>
    sorgu: "<ör. ticari itirazın iptali davasında dava şartı arabuluculuk ve inkâr tazminatı için alacağın likit olması>"
legal_search_cases  mahkeme: "yargitay"  daire: "12. Hukuk Dairesi"
    sorgu: "<ör. itirazın kaldırılmasında belgenin İİK 68 niteliği taşımaması>"
legal_get_social_parameters  tur: "harc_basvurma_sulh"        # icra mahkemesi başvurma harcı
legal_calculate_court_fee  harc_turu: "pesin_harc"  deger: <dava değeri>   # itirazın iptali DAVASI peşin harcı
```

## Çıktı iskeleti

```markdown
## Ödeme emri / itiraz değerlendirmesi: [taraf] — [icra dairesi, dosya no]
### Sonuç ve önerilen seçenek (A/B/C/D ya da kaldırma/iptal)
### Süre tablosu
| İşlem | Başlangıç | Son gün | Merci | Dayanak | Durum |
### Esas okuması (yönlendirme için, görüş değil) [incele]
### Tazminat ve masraf riski
### Arabuluculuk ve görevli mahkeme
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Belge m.68 niteliğinde değilken itirazın kaldırılması istemek; 6 ayı harcayıp sonra iptal davasına geçmek.
- Ticari ya da işçilik itirazın iptali davasını arabuluculuğa gitmeden açmak → dava şartı yokluğundan usulden ret.
- 1 yıllık süreyi arabuluculukta geçen süreyi hesaba katmadan ya da tersine katarak hesaplamak.
- Kambiyo takibinde itirazı icra dairesine yapmak.
- İnkâr tazminatını "otomatik %20" sanmak: tazminat talebe bağlıdır ve alt sınırdır.

