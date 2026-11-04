# KDV, gelir ve kurumlar vergisi: temel uygulama ve planlama soruları

## Ne zaman kullanılır
- KDV indirimi, iadesi, tevkifatı (sorumlu sıfatıyla beyan), belgesiz mal, sahte / yanıltıcı fatura iddiası.
- Kurumlar / gelir vergisinde KKEG, örtülü sermaye, transfer fiyatlandırması yoluyla örtülü kazanç dağıtımı, enflasyon düzeltmesi, yurt içi asgari kurumlar vergisi.
- "Bu işlem planlaması inceleme riski doğurur mu?" türü ön değerlendirme.

**Sınır:** bu dosya hukuki çerçeveyi ve riskleri verir; beyanname, hesap ya da YMM raporu düzenlemez. **Oranlar, tevkifat oranları, iade alt sınırları, istisna tutarları metne yazılmaz** — kanun, Cumhurbaşkanı kararı ve genel tebliğden o tarih için çekilir, `[doğrula]`. Genel tebliğ (KDV Genel Uygulama Tebliği, KV Genel Tebliği, TF tebliği) atfı yapılacaksa RG'den ya da `legal_search_statute_semantic` (`mevzuat_tur: "teblig"`) ile bul; bulunamazsa `[model bilgisi — doğrulayın]`.

---

## 1. KDV

### İndirim (3065 m.29)
- İndirilebilecekler: kendisine yapılan teslim ve hizmetler için düzenlenen faturada gösterilen KDV, ithalde ödenen KDV, götürü/telafi ediciden gerçek usule geçişte envanterdeki malların KDV'si ve (7491 ile) sorumlu sıfatıyla beyan edilip ödenen KDV. 
- **İndirim süresi:** vergiyi doğuran olayın vuku bulduğu takvim yılını izleyen takvim yılı aşılmamak şartıyla, belgenin kanuni defterlere kaydedildiği dönemde. Süre dışı indirim 🔴 tarhiyat sebebi. 
- Devreden KDV kural olarak iade edilmez; indirimli orana tabi işlemlerde belirli sınırı aşan kısım için mahsuben / nakden iade m.29/2'de; sınırı Cumhurbaşkanı belirler.  Sınırı metne yazma.

### Tevkifat ve sorumluluk (3065 m.9)
- Bakanlık, vergi alacağının emniyeti için işleme taraf olanları sorumlu tutabilir (tevkifatın dayanağı); yurt dışından KDV mükellefi olmayan gerçek kişilere sunulan elektronik hizmetlerde KDV'yi hizmeti sunan beyan eder. 
- Tevkifat oranları ve kapsamı **genel tebliğdedir** ve sık değişir; işlem tarihindeki tebliğ metnini çek `[doğrula]`. Eski YAML'daki "%50, %70, %90" gibi örnek oranları kullanma.
- **Belgesiz mal / hizmet:** tespit hâlinde alış belgeleri için **10 gün** süre verilir; ibraz edilemezse emsal bedel üzerinden KDV re'sen tarh edilir ve vergi ziyaı cezası uygulanır; satıcıya inceleme raporuna dayanılarak tarhiyat yapıldıysa alıcıdan ayrıca aranmaz. 

### İade (3065 m.32 ve tebliğ)
- İhracat, istisna, indirimli oran ve tevkifat kaynaklı iadede belge seti ve yol (YMM raporu, teminat, vergi inceleme raporu) **tebliğe** bağlıdır; tutar sınırlarını tebliğden çek.  Çalışma anında iade türünün belge setini KDV Genel Uygulama Tebliği'nin iade bölümünden (`legal_search_statute_semantic`, `sorgu: "KDV Genel Uygulama Tebliği iade belgeleri YMM raporu teminat <iade türü>"`) ya da GİB özelgelerinden (`legal_search_admin_guidance`, `kurum: "Gelir İdaresi Başkanlığı"`) çek; bulamazsan `[ARAŞTIRMA GEREKLİ: KDV GUT iade belge seti — <iade türü>]`. 
- İade incelemesi süresi 3 ay (+2 ay ek süre) esas. 
- İadenin, belgelerin tamamlandığı tarihi izleyen 3 ay içinde yapılmaması hâlinde tecil faizi oranında faiz ödenir. 

### Sahte / muhteviyatı itibarıyla yanıltıcı belge
- Tanımlar VUK m.359'da: **sahte belge** gerçek bir muamele olmadığı hâlde varmış gibi düzenlenen; **yanıltıcı belge** gerçek bir muameleyi mahiyet veya miktar itibarıyla gerçeğe aykırı yansıtan. 
- Alıcı (kullanan) savunmasında kontrol: (1) tarhiyat yalnız **düzenleyici hakkındaki vergi tekniği raporuna** mı dayanıyor, alıcı nezdinde somut tespit (mal girişi, stok, sevk irsaliyesi, taşıma, ödemenin bankadan yapılıp dönmediği) var mı? (2) mal/hizmetin gerçekten alındığına dair belge; (3) Ba-Bs uyumu; (4) iyi niyet ve basiret. Danıştay içtihadı bu noktada **dairelere ve döneme göre değişkendir**; somut olaya en yakın son 3 yıl VDDK kararını tam metinle oku `[incele]`.  
- Sahte belge iddiası üç kat vergi ziyaı (VUK m.344/2) ve suç duyurusu (m.359) getirir → `vergi-cezalari-ve-pismanlik.md`.

---

## 2. Kurumlar ve gelir vergisi

### KKEG (kanunen kabul edilmeyen giderler)
- Liste 5520 m.11 (kurumlar) ve 193 m.41 (gelir); para cezaları, vergi cezaları, gecikme zammı/faizi, örtülü sermaye faizi, örtülü kazanç gibi kalemler. Somut kalemi madde metninden doğrula. 

### Örtülü sermaye (5520 m.12)
- Ortaklardan ya da ortakla ilişkili kişilerden temin edilen borçların hesap dönemi içinde herhangi bir tarihte **öz sermayenin üç katını** aşan kısmı örtülü sermayedir; ilişkili banka kredileri %50 dikkate alınır; öz sermaye **hesap dönemi başındaki** VUK öz sermayesidir. 
- Örtülü sermaye üzerinden faiz ve benzeri ödemeler (kur farkı hariç) dağıtılmış kâr payı sayılır; karşı tarafta düzeltme için tarhiyatın kesinleşip ödenmiş olması şarttır. 

### Transfer fiyatlandırması (5520 m.13)
- İlişkili kişilerle emsallere aykırı bedel → kazanç örtülü dağıtılmış sayılır; ilişkili kişi tanımı ve %10 oranı m.13/2'de; yöntemler m.13/4; peşin fiyatlandırma anlaşması m.13/5. 
- **Yurt içi** ilişkili işlemlerde örtülü kazanç kabulü **Hazine zararı** şartına bağlıdır. 🟠 savunma noktası. 
- Belgelendirme yükümlülüğü tam ve zamanında yerine getirildiyse vergi ziyaı cezası (m.359 hâli hariç) **%50 indirimli** uygulanır. 

### Enflasyon düzeltmesi (VUK mük.298, geçici m.33)
- 2022 ve 2023 geçici dönemlerinde şartlara bakılmaksızın düzeltme yapılmadı; **31.12.2023 tarihli** mali tablolar şart aranmaksızın düzeltmeye tabi tutuldu, farkı geçmiş yıllar kâr/zararına; belirli finans sektörü şirketleri için 2024-2025 düzeltme farkı kazançta dikkate alınmaz (7491, 7529).  **Yeni erteleme:** VUK geçici m.37 (7571/34, RG 25.12.2025) — 2025 hesap dönemi ile geçici vergi dönemleri dahil 2026 ve 2027 hesap dönemlerinde (özel hesap döneminde 2026-2028'de biten dönemler) şartlar oluşsa bile **enflasyon düzeltmesi yapılmaz**; Cumhurbaşkanı üç hesap dönemine kadar uzatabilir; bu dönemler mük.298/Ç bakımından şartların gerçekleşmediği dönem sayılır; işlenmiş altın/gümüş mükelleflerine (mük.298/A-9) birinci ve ikinci fıkra uygulanmaz. Uzatma kararını RG'de ara. 7566 ve 7590'da enflasyon düzeltmesine dokunan hüküm yok. 

### Yurt içi asgari kurumlar vergisi (5520 m.32/C) ve küresel asgari vergi
- 7524 ile eklendi: hesaplanan kurumlar vergisi, indirim ve istisnalar düşülmeden önceki kurum kazancı üzerinden hesaplanan asgari vergiden az olamaz; ayrıca çok uluslu gruplar için küresel asgari tamamlayıcı vergi (ek m.6 vd.). Oranları ve istisnaları madde metninden çek.  Yürürlük ve ilk uygulanacağı dönem `[doğrula]`.

### Gelir vergisi — son değişiklik örneği
- Konut kira gelirlerinde (GVK m.74/1-4) zarar mahsubu sınırlaması: 7566 ile "Konutlar hariç olmak üzere kiraya verilen mal ve haklar" ifadesi getirildi; 1.1.2025'ten başlayan dönem gelirlerine ilişkin beyannamelere uygulanır.  Hükmün etkisini (konut kira zararının mahsup edilememesi mi) madde metniyle birlikte yorumla `[incele]`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Hangi vergi, hangi dönem, hangi işlem? | Uygulanacak metin ve tebliğ |
| İşlemin tarafları ilişkili mi (ortak, %10, yakın akraba)? | m.12-13 |
| Fatura, sözleşme, sevk, ödeme belgeleri var mı? Ödeme bankadan mı? | Sahte belge savunması |
| TF belgelendirmesi (form, rapor) süresinde hazırlandı mı? | %50 indirim |
| İade yolu: YMM raporu, teminat, inceleme? | Süre ve faiz |
| Daha önce bu konuda özelge alındı mı? | m.369 koruması → `ozelge-ve-idari-gorus.md` |

---

## İdare tarafı

- Sahte belge tarhiyatında alıcı nezdinde somut tespitleri rapora yaz; yalnız düzenleyici VTR'sine atıf dava riskidir.
- Yurt içi TF tarhiyatında Hazine zararını hesapla ve rapora koy (m.13/7).
- İade taleplerinde 3 aylık süre ve tecil faizi riskini izle (VUK m.112/5).

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "3065"  law_type: "Kanun"  article_no: "9" | "29" | "30" | "32"
legal_get_statute_article  law_no: "5520"  law_type: "Kanun"  article_no: "11" | "12" | "13"
legal_search_statute_semantic  sorgu: "yurt içi asgari kurumlar vergisi"  mevzuat_no: "5520"     # harfli madde 32/C
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "geçici 33" | "359"
legal_search_statute_semantic  sorgu: "<ör. KDV tevkifatı yapım işi oranı>"  mevzuat_tur: "teblig"
legal_search_official_gazette  query: "Katma Değer Vergisi Genel Uygulama Tebliğinde Değişiklik"  search_in: "title"  sort_by: "date_desc"
legal_search_cases  mahkeme: "danistay"  sorgu: "<olay>"  tarih_baslangic: "<son 3 yıl>"
legal_calculate_cpi_change  # endeks gerektiren hesaplarda; ÜFE/TÜFE ayrımı [doğrula]
legal_get_exchange_rate     # dövizli işlemler
```

---

## Çıktı iskeleti

```markdown
## [KDV / KV / GV] değerlendirmesi — [işlem / dönem]
### Kısa cevap
### Dayanak (madde + tebliğ, etiketli)
### Risk tablosu
| Risk | Olasılık | Sonuç (vergi / ceza / suç) | Önlem |
### Belge ve süre listesi
### Özelge gerekli mi? → ozelge-ve-idari-gorus.md
```

---

## Sık hatalar

- 🔴 Tevkifat ya da KDV oranını ezberden yazmak.
- 🔴 KDV indirimini izleyen takvim yılı sonrasına taşımak.
- 🟠 Yurt içi TF'de Hazine zararı şartını atlamak.
- 🟠 Örtülü sermayede dönem sonu öz sermayesini kullanmak (dönem başı esas).
- 🟡 Enflasyon düzeltmesinde 2022-2023 erteleme ve 31.12.2023 özel kuralını karıştırmak.

---

