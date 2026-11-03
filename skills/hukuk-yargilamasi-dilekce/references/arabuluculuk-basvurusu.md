# Zorunlu (dava şartı) arabuluculuk başvurusu

*Yeni akış — eski YAML'larda yoktu. İş hukuku becerisindeki işe iade/işçilik alacağı arabuluculuğu buradaki genel kurala bağlanır; iş hukukuna özgü süreler (4857 m.20 bir ay, iki hafta) `is-hukuku` becerisindedir.*

## Ne zaman kullanılır
Dava açılmadan önce arabulucuya başvurulmuş olmasının **dava şartı** olduğu uyuşmazlıklarda. Başvurulmadan dava açılırsa dava **hiçbir işlem yapılmadan usulden reddedilir**; son tutanak eklenmezse bir haftalık kesin süre verilir, sunulmazsa yine usulden ret.

---

## 1. Kapsam: hangi uyuşmazlık dava şartına tabi?

| Alan | Kapsam | Dayanak | Kapsam dışı / not |
|---|---|---|---|
| **İş** | Kanuna, bireysel ya da toplu iş sözleşmesine dayanan işçi veya işveren alacağı ve tazminatı; işe iade; bunlarla ilgili **itirazın iptali, menfi tespit, istirdat** (7445 ile 2023'te eklendi) | 7036 m.3/1 | İş kazası ve meslek hastalığından doğan maddi/manevi tazminat ile bunlarla ilgili tespit, itiraz ve rücu davaları **hariç** (m.3/3). Gazeteci (5953) ve gemiadamı (854) işçi sayılır (m.3/20). |
| **Ticari** | TTK m.4 ve diğer kanunlardaki ticari davalardan **konusu bir miktar para olan alacak, tazminat, itirazın iptali, menfi tespit ve istirdat** davaları | TTK m.5/A-1 | İtirazın iptali, menfi tespit, istirdat 7445 (RG 05.04.2023) ile eklendi. Önceki tarihli davalarda menfi tespitin kapsama girip girmediği tartışmalıydı: Yargıtay 11. HD çoğunluğu 2023 öncesi menfi tespit davasında arabuluculuk itirazını reddetti; karşı oy kapsamda saydı. **Dava tarihindeki metni** uygula. |
| **Tüketici** | **Tüketici mahkemelerinde görülen** uyuşmazlıklar | 6502 m.73/A-1 (7251, 2020) | Hariç: (a) **tüketici hakem heyetinin görev alanındaki** uyuşmazlıklar, (b) hakem heyeti kararlarına itirazlar, (c) m.73/6 davaları (Bakanlık/örgüt davaları), (ç) m.74 davaları, (d) taşınmazın aynından doğan tüketici uyuşmazlıkları. Sınırın altındaki uyuşmazlıklarda hakem heyetine başvuru **zorunlu**, üstündekilerde **yapılamaz**; kanundaki taban tutar her yıl yeniden değerleme oranıyla artar — yılın sınırını **her seferinde çek**, beceriye yazma. Yılın sınırı: `legal_get_social_parameters` `tur: "thh_parasal_sinir"` (dönem ve RG dayanağıyla döner). |
| **Kira** | Kira ilişkisinden kaynaklanan uyuşmazlıklar (taşınır ve taşınmaz kira) | 6325 m.18/B-1-a (7445, 2023) | **Hariç:** kiralanan taşınmazın İİK'ya göre **ilamsız icra yoluyla tahliyesi**. Tahliye davası, kira tespiti, kira alacağı arabuluculuğa tabidir. |
| **Ortaklığın giderilmesi** | Taşınır ve taşınmazların paylaştırılması ve ortaklığın giderilmesi | 6325 m.18/B-1-b | |
| **Kat mülkiyeti** | 634 sayılı KMK'dan kaynaklanan uyuşmazlıklar | 6325 m.18/B-1-c | |
| **Komşuluk** | Komşu hakkından kaynaklanan uyuşmazlıklar | 6325 m.18/B-1-ç | |

**Genel istisna:** Özel kanunda tahkim ya da başka alternatif çözüm zorunluluğu varsa ya da **tahkim sözleşmesi** bulunuyorsa dava şartı arabuluculuk hükümleri uygulanmaz.

Liste genişleyebilir (her yıl yeni alanlar eklendi). Şüphede `legal_search_statute_semantic` ile `sorgu: "dava açılmadan önce arabulucuya başvurulmuş olması dava şartıdır"` ara.

---

## 2. Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Başvurudan son tutanağa kadar **zamanaşımı durur, hak düşürücü süre işlemez** | Büroya başvuru | 6325 m.18/A-15; 7036 m.3/17 | Bu süreyi süre tablosunda ayrı satır olarak göster. |
| Arabulucunun sonuçlandırma süresi — **genel** (tüketici, kira, ortaklığın giderilmesi, KMK, komşuluk) | Arabulucunun görevlendirilmesi | 6325 m.18/A-9: **üç hafta**, zorunlu hâlde en çok **bir hafta** uzatma | |
| — **İş** | Görevlendirme | 7036 m.3/10: **üç hafta + en çok bir hafta** | |
| — **Ticari** | Görevlendirme | TTK m.5/A-2: **altı hafta + en çok iki hafta** | |
| Dava öncesi ihtiyati tedbir / ihtiyati haciz sonrası dava açma süresi | Büroya başvuru → son tutanak | 6325 m.18/A-16 | HMK m.397/1 ve İİK m.264/1 süreleri bu arada **işlemez**. Başvurudan sonra başvurana karşı icra takibi yapılırsa son tutanaktan itibaren **iki hafta** içinde menfi tespit davası açılıp istenirse İİK m.72/2 uygulanır. |
| Büronun yetkisine itiraz kabul edilirse yetkili büroya başvuru | Sulh hukuk kararının tebliği | 6325 m.18/A-8 / 7036 m.3/9: **bir hafta** | Bu sürede başvurulursa ilk başvuru tarihi esas alınır. |
| Son tutanaktan sonra dava | Son tutanak | **Genel bir süre yok**; maddi hukuk süresi kaldığı yerden işler. **İstisna — işe iade:** son tutanaktan itibaren **iki hafta** (4857 m.20/1) → `is-hukuku` | Her uyuşmazlıkta özel kanunda "son tutanaktan itibaren" süre var mı diye kontrol et `[incele]`. |

`legal_calculate_deadline` arabuluculuk sürelerini tanımıyor; elle hesapla, `[doğrula]`.

**Kira — erken başvuru tuzağı 🔴:** TBK m.350 ihtiyaç ve yeniden inşa tahliyesinde arabulucuya başvuru, dava açma hakkı **doğduktan sonra** (belirli süreli sözleşmede süre bittikten sonra) ve dava süresi içinde yapılmalıdır; erken başvuru dava şartını karşılamaz. m.351 için birlik kararı yok `[incele]`. Esas ve takvim → `../../kira-hukuku/references/usul-arabuluculuk-ve-gorev.md`.

---

## 3. Başvuru yeri ve usul

- **Genel (6325 m.18/A-4):** uyuşmazlığın konusuna göre **yetkili mahkemenin bulunduğu yer** arabuluculuk bürosu; büro yoksa görevlendirilen sulh hukuk yazı işleri müdürlüğü.
- **İş (7036 m.3/5):** karşı tarafın (birden çoksa birinin) **yerleşim yeri** ya da **işin yapıldığı yer** bürosu.
- Arabulucu listeden büroca belirlenir; taraflar listedeki bir arabulucuda anlaşırsa o görevlendirilir (6325 m.18/A-5).
- Başvuran kendisinin ve elindeyse karşı tarafın **her türlü iletişim bilgisini** verir; büro resmî kayıtlardan araştırabilir (m.18/A-6). Avukatı olsa bile asıl taraf da bilgilendirilir (m.18/A-7, 7445 ek cümle).
- Karşı taraf büronun yetkisine **en geç ilk toplantıda** itiraz edebilir (m.18/A-8).
- Görüşmeler aksi kararlaştırılmadıkça büronun bağlı olduğu adalet komisyonu alanında yapılır (m.18/A-17).
- İşte taraflar bizzat, kanuni temsilci ya da avukatla katılır; işverenin yazılı yetkilendirdiği çalışanı da temsil edebilir (7036 m.3/18).
- Başvuru usulü Adalet Bakanlığı yönetmeliğindedir (7036 m.3/22). Başvuru dilekçeyle, bürodaki form doldurularak ya da elektronik ortamda yapılır; başvuranın uyuşmazlık konusunu açıklaması istenir (Hukuk Uyuşmazlıklarında Arabuluculuk Kanunu Yönetmeliği m.23/3-4). Form içeriğini uydurma.

## 4. İlk toplantıya katılmama ve ücret
- Geçerli mazeret olmadan **ilk toplantıya katılmayan** taraf son tutanakta belirtilir; davada haklı çıksa bile karşı tarafın yargılama giderlerinin **yarısından** sorumlu tutulur ve lehine vekâlet ücretinin **yarısına** hükmedilir (7531 ile 2024 değişikliği). İki taraf da katılmazsa giderler kendi üzerlerinde kalır.
- **Tüketici lehine istisna:** bu yaptırım tüketici aleyhine uygulanmaz; tüketicinin ödeyeceği ücret (iki saatlik tutarı geçmemek üzere) Adalet Bakanlığı bütçesinden karşılanır.
- Ücret: anlaşmada tarifenin İkinci Kısmı, anlaşamamada iki saate kadar bütçeden; tutarları **tarifeden çek**, beceriye yazma. Tarife her yıl yenilenir: `legal_search_official_gazette` (`query: "Arabuluculuk Asgari Ücret Tarifesi"`, `search_in: "title"`, `sort_by: "date_desc"`) ile o yılın tarifesini bul.
- 7036 m.3/15 Anayasa Mahkemesince iptal edildi (03.06.2025, E.2024/157 K.2025/121).

## 5. Anlaşma olursa
- Anlaşılan hususlarda dava açılamaz (6325 m.18/5). Taraflar ve avukatları ile arabulucunun (ticari uyuşmazlıkta avukatlar ile arabulucunun) imzaladığı anlaşma belgesi, kanunda şerh zorunlu tutulan hâller dışında **ilam niteliğinde** belgedir (m.18/4).
- **18/B alanlarında (kira, ortaklığın giderilmesi, KMK, komşuluk) icra edilebilirlik şerhi zorunludur**; taşınmazla ilgili belgelerde taşınmazın bulunduğu yer sulh hukuk mahkemesinden alınır. Taşınmazın devrine/sınırlı ayni hakka ilişkin anlaşmada şerhten sonra tapu müdürlüğünden **resmî senet düzenlenmeksizin** tescil istenebilir (7531, 2024).
- İşe iadede anlaşma tutanağında işe başlatma tarihi, boşta geçen süre ücreti ve işe başlatmama tazminatı parasal olarak yazılmazsa anlaşma sağlanamamış sayılır → `../../is-hukuku/references/fesih-ve-ise-iade.md`.

---

## Görüşme soruları
1. Uyuşmazlığın türü (iş / ticari para alacağı / tüketici / kira / ortaklığın giderilmesi / KMK / komşuluk)? Dava şartı mı, ihtiyari mi?
2. Tahkim şartı ya da özel çözüm yolu var mı?
3. Tüketici uyuşmazlığında tutar hakem heyeti sınırının altında mı? (altındaysa arabuluculuk değil hakem heyeti)
4. Başvuran ve karşı taraf: ad/unvan, T.C./vergi no, adres, **telefon ve e-posta** (büro için)
5. Uyuşmazlığın kısa özeti ve talep edilen kalemler, yaklaşık tutar
6. Yetkili mahkeme yeri (genel) ya da karşı tarafın yerleşim yeri/işin yapıldığı yer (iş)
7. Dava öncesi ihtiyati tedbir/haciz kararı var mı? (süre işlemez)
8. Hak düşürücü süre ya da zamanaşımı yakın mı? (başvuru tarihini öne çek)
9. Vekil katılacak mı? İşveren tarafında yetkili çalışan belgesi?

## soorgla çağrıları
```
legal_list_statute_articles law_no: "6325" law_type: "Kanun" article_no: "18" include_content: true # 18, 18/A, 18/B
legal_get_statute_article law_no: "7036" article_no: "3"
legal_list_statute_articles law_no: "6102" law_type: "Kanun" article_no: "5" include_content: true # 5/A
legal_list_statute_articles law_no: "6502" law_type: "Kanun" article_no: "73" include_content: true # 73/A
legal_get_statute_article law_no: "6502" article_no: "68" # hakem heyeti görevi
legal_search_official_gazette query: "tüketici hakem heyeti parasal sınır" search_in: "title"
legal_search_cases sorgu: "<uyuşmazlık> arabulucuya başvurulmadan açılan dava usulden ret" mahkeme: "yargitay" tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar>
```
**MCP notu:** harfli maddeler (`18/A`, `5/A`, `73/A`) `legal_get_statute_article` ile boş döner; `legal_list_statute_articles` kullan.

## Başvuru metni iskeleti
Resmî başvuru büronun formuyla ya da UYAP üzerinden yapılır. Aşağıdaki metin forma girecek bilgilerin taslağıdır:
```markdown
[YER] ADLİYESİ ARABULUCULUK BÜROSU'NA

BAŞVURAN : [AD SOYAD / UNVAN] (T.C./Vergi No: [___]) — [ADRES] — Tel: [___] — E-posta: [___]
VEKİLİ : Av. [___]
KARŞI TARAF : [AD SOYAD / UNVAN] — [ADRES] — [bilinen tel/e-posta]
UYUŞMAZLIK TÜRÜ: [İş (7036 m.3) | Ticari (TTK m.5/A) | Tüketici (6502 m.73/A) | Kira / Ortaklığın giderilmesi / KMK / Komşuluk (6325 m.18/B)]
UYUŞMAZLIK KONUSU:
1. [kısa olay — tarih]
2. Talep edilen kalemler: [___] (yaklaşık [___] TL)
YETKİ : [yetkili mahkeme yeri / karşı tarafın yerleşim yeri / işin yapıldığı yer]
TALEP : Dava şartı arabuluculuk kapsamında arabulucu görevlendirilmesini talep ederim. [TARİH] [İmza]
```

## Sık hatalar
- 🔴 Dava şartı arabuluculuk atlandı; dava usulden reddedildi, bu arada hak düşürücü süre kaçtı.
- 🔴 Tüketici uyuşmazlığı hakem heyeti sınırının altında olduğu hâlde arabulucuya gidildi (ya da tersi).
- 🟠 Kira alacağında ilamsız icra tahliyesi ile tahliye davası karıştırıldı.
- 🟠 İlk toplantıya katılmama yaptırımı kullanıcıya söylenmedi.
- 🟠 18/B anlaşmasında icra edilebilirlik şerhi alınmadı.
- 🟡 Karşı tarafın iletişim bilgisi eksik; görüşme yapılamadı.

## Kaynak
Yeni akış; eski YAML'larda karşılığı yok. Ek talimat: "zorunlu arabuluculuk başvurusu (7036 m.3 iş, TTK 5/A ticari, 6502 m.73/A tüketici, kira vb.)".
