# Vergi ve ceza ihbarnamesine karşı idari yollar: uzlaşma, cezada indirim, düzeltme-şikâyet

Mükellef ya da ceza muhatabı bir vergi/ceza ihbarnamesi aldığında dava dışında üç idari yol vardır. Bunlar **birbirini dışlayabilir** ve seçim süreyle bağlıdır; dilekçeden önce yol seçimini yap ve kullanıcıya göster.

| Yol | Ne sağlar | Dava ile ilişkisi |
|---|---|---|
| **Tarhiyat sonrası uzlaşma** (VUK ek m.1) | Vergi ve ceza miktarında idareyle anlaşma | Uzlaşma talep edilen vergi/ceza için dava ancak uzlaşma vaki olmazsa açılır; uzlaşma sağlanırsa dava yok |
| **Tarhiyat öncesi uzlaşma** (VUK ek m.11) | Vergi incelemesi sırasında, tarhiyattan önce | Uzlaşılan husus için dava açılamaz; uzlaşılamazsa tarhiyat sonrası uzlaşma istenemez |
| **Cezada indirim** (VUK m.376) | Vergi ve cezanın belirli kısmı süresinde ödenirse cezada indirim | Dava açılırsa indirimden yararlanılamaz |
| **Düzeltme ve şikâyet** (VUK m.116-124) | Vergi hatasının (hesap/vergilendirme hatası) düzeltilmesi | Dava süresi geçtikten sonra düzeltme reddedilirse Bakanlığa şikâyet |

Esas vergi hukuku değerlendirmesi (tarhiyat yerinde mi, sahte belge, KDV indirimi) bu dosyanın konusu değildir; burada amaç **doğru yolu süresinde, doğru makama, eksiksiz dilekçeyle** işletmektir. Vergi davası dilekçesi kapsam dışıdır.

---

## Süre tablosu

| İşlem | Süre ve başlangıç | Dayanak | Not |
|---|---|---|---|
| Tarhiyat sonrası uzlaşma talebi | İhbarnamenin **tebliğinden itibaren 30 gün** | VUK ek m.1/1  | Uzlaşma vaki olmazsa **yeniden uzlaşma istenemez**. Mükellef dava açma süresi sonuna kadar idarenin nihai teklifini yazılı kabul ederse uzlaşma sağlanmış sayılır. |
| Uzlaşma vaki olmazsa dava | Uzlaşmanın vaki olmadığına dair tutanağın tebliğinden itibaren; dava süresi bitmiş ya da **15 günden az** kalmışsa tutanağın tebliğinden itibaren **15 gün** | VUK ek m.7  | |
| Cezada indirim (m.376) | İhbarnamenin **tebliğinden itibaren 30 gün** içinde vergi dairesine başvuru; vergi + cezanın kalan kısmı vadede ya da teminatla vadeden itibaren 3 ay içinde ödenir | VUK m.376/1  | Ödeme yapılmaz ya da dava açılırsa indirim düşer. **İndirim oranını madde metninden al**; 7524 sayılı Kanunla (28.07.2024) ikinci bent yürürlükten kaldırıldı, eski "ilk / sonraki ceza" ayrımlı oranları kullanma. |
| Vergi mahkemesinde dava | Tebliği izleyen günden itibaren **30 gün** | 2577 m.7/1 ve 7/2-b  | Bu beceri dava dilekçesi yazmaz; süreyi hatırlatır. |
| Düzeltme talebi | VUK m.114'teki **tarh zamanaşımı** dolduktan sonra ortaya çıkan vergi hataları düzeltilemez; zamanaşımının son yılında tarh ve tebliğ edilen vergilerde (ve ilanla tebliğ hâllerinde) düzeltme süresi ilgili tarihten itibaren **bir yıldan aşağı olamaz** | VUK m.126    | Düzeltme yalnızca **vergi hatası** içindir (m.117 hesap, m.118 vergilendirme hatası); hukuki yorum farkı düzeltmeyle çözülmez `[incele]`.  |
| Düzeltme reddine karşı şikâyet | Dava açma süresi geçtikten sonra yapılan düzeltme talebi reddedilirse **Maliye (Hazine ve Maliye) Bakanlığına** şikâyet; il özel idaresi vergilerinde valilik, belediye vergilerinde belediye başkanlığı | VUK m.124  | Şikâyet başvurusu için süre m.124'te yazmıyor; "ret tebliğinden itibaren 30 gün" gibi bir süre bu beceride hiçbir hükme bağlanamadı, kesin süre olarak yazma. Başvurudan önce Gelir İdaresi'nin VUK genel tebliğleri/sirkülerlerinde şikâyet süresini `legal_search_statute_semantic` (`mevzuat_tur: "teblig"`, sorgu: "VUK 124 şikayet yoluyla müracaat süresi") ve `legal_search_admin_guidance` ile ara; bulamazsan `[ARAŞTIRMA GEREKLİ: VUK 124 şikâyet süresi]` yaz ve ret tebliğinden sonra **gecikmeden** başvur. Bakanlığın şikâyet üzerine verdiği ret işlemi idari davaya konu olabilir (Danıştay 4. D., E. 2016/19036, K. 2021/2183 — arama özeti; kullanmadan önce tam metni oku).  |

`legal_calculate_deadline` tarhiyat sonrası uzlaşma (`tax_settlement_request`), cezada indirim (`tax_penalty_reduction_376`) ve vergi davası (`iyuk_tax_lawsuit`) kodlarını tanır; diğer süreleri elle hesapla (tebliğ günü sayılmaz), son günü `legal_check_holiday` ile kontrol et, `[doğrula]`. Elektronik tebligatta tebliğ, iletildiği tarihi izleyen **beşinci günün sonunda** yapılmış sayılır; araca başlangıç olarak bu günü ver. 

---

## Yol seçimi — kontrol listesi

1. **Ceza türü:** vergi ziyaı cezası mı, usulsüzlük/özel usulsüzlük cezası mı? Usulsüzlük cezalarında uzlaşma yalnızca belirli tutarı aşan cezalarda mümkündür; eşik **yeniden değerlenen** tutardır ve kanun metninde parantez içinde güncel değeri gösterilir. **Tutarı bu dosyaya yazma, madde metninden oku.** 
2. **Kapsam dışı:** VUK m.359'daki fiillerle (kaçakçılık) vergi ziyaına sebebiyet verilmesi hâlinde kesilen ceza ve iştirak edenlere kesilen ceza uzlaşma kapsamı dışındadır. 
3. **Uzlaşma gerekçesi:** ek m.1 uzlaşmanın ileri sürülebileceği hâlleri sayar (kanuna yeterince nüfuz edememe, m.369 yanılma, vergi hataları ve maddi hata, yargı kararlarıyla idarenin görüş farklılığı). Dilekçede bu gerekçelerden en az birini somut olgularla ileri sür. 
4. **Tarhiyat öncesi uzlaşma** istendi ve sağlanamadıysa tarhiyat sonrası uzlaşma talep edilemez. 
5. **Uzlaşma ile dava aynı anda:** uzlaşma talebinden önce dava açılmışsa dava, uzlaşma sonuçlanana kadar incelenmez.  Eski YAML'daki "uzlaşma talep eden aynı anda dava açamaz" ifadesi bu ayrıntıyla değiştirildi.
6. **İndirim mi uzlaşma mı:** iki yolun parasal sonucunu kullanıcının vereceği tutarlarla karşılaştırmak avukatın takdiridir `[incele]`; uzlaşma komisyonlarının "güncel indirim oranları" diye bir yayımlanmış oran yoktur, eski YAML'daki bu ifade kaldırıldı.
7. **Makam:** uzlaşma başvurusu uzlaşma komisyonuna yetkili vergi dairesi/başkanlık üzerinden yapılır; komisyonların teşkili **Uzlaşma Yönetmeliği**nde (RG 03.02.1999, 23600; 2022 değişiklikli); komisyonların uzlaşabileceği en çok tutarlar Yönetmelik m.5 uyarınca **genel tebliğlerle** belirlenir — tutarı tebliğden çek. 

---

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `notice_details[].date` | İhbarnamenin **tebliğ** tarihi? (düzenleme tarihi değil) Elektronik tebligat mı? |
| `notice_details[].number` | İhbarname / takip numarası? |
| `notice_details[].tax_type` / `period` | Vergi türü ve dönem? Ceza türü (vergi ziyaı / usulsüzlük / özel usulsüzlük)? |
| `notice_details[].amount` | Vergi aslı ve ceza tutarı ayrı ayrı? |
| (yeni) | Tarhiyat bir vergi inceleme raporuna mı dayanıyor? Tarhiyat öncesi uzlaşma istendi mi? |
| (yeni) | Dava açıldı mı? |
| `application_type` | Hangi yol: uzlaşma, cezada indirim, düzeltme? (bilinmiyorsa yukarıdaki kontrol listesiyle öner) |
| `tax_office_presidency` | Bağlı olunan vergi dairesi / başkanlık? |
| `taxpayer_info.*` | Unvan/ad-soyad, VKN/TCKN, tebligat adresi, telefon? |
| `request_justification` | Talebin olgusal gerekçesi: hangi uzlaşma gerekçesi, hangi hata, ödeme niyeti? |
| `legal_reasons` | (Araştırma adımında doldurulur — kullanıcıya sorma.) |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "213"  article_no: "ek 1" | "ek 7" | "ek 11" | "376" | "369" | "124"
legal_get_statute_article  law_no: "213"  article_no: "116" | "117" | "118" | "126"     # düzeltme
legal_get_statute_article  law_no: "2577"  article_no: "7"
legal_get_statute_article_history  (213 m.376, ek m.1)         # 7524 (2024) değişiklikleri; tarihçe eksik olabilir
legal_search_official_gazette  query: "7524"  document_type: "kanun"   # değiştiren kanun metni
legal_resolve_statute  query: "Uzlaşma Yönetmeliği"
legal_search_cases  mahkeme: "danistay"  sorgu: "<ör. uzlaşma tutanağının tebliğinden sonra dava süresi>"  tarih_baslangic: "<son 3 yıl>"
legal_get_case_document  belge_id: "<seçilen karar>"
```

---

## Dilekçe iskeleti

```markdown
[… VERGİ DAİRESİ BAŞKANLIĞI (… UZLAŞMA KOMİSYONU BAŞKANLIĞINA) / … VERGİ DAİRESİ MÜDÜRLÜĞÜNE]

MÜKELLEF       : [unvan / ad-soyad]
VKN / TCKN     : [___]
VERGİ DAİRESİ  : [___]
ADRES / TEL    : [___]
VEKİLİ         : [varsa]

KONU: Aşağıda bilgileri yer alan ihbarname(ler) için [tarhiyat sonrası uzlaşma / VUK 376 uyarınca cezada
      indirim / VUK 116-124 uyarınca düzeltme] talebimizdir.

BAŞVURU KONUSU İHBARNAMELER:
| Tebliğ tarihi | İhbarname no | Vergi / ceza türü | Dönem | Vergi aslı | Ceza |
|---|---|---|---|---|---|
| [___] | [___] | [___] | [___] | [___] | [___] |

AÇIKLAMALAR:
1. [Olay ve tarhiyatın dayanağı]
2. [Uzlaşma gerekçesi / vergi hatasının açıklaması / ödeme taahhüdü]

HUKUKİ NEDENLER: 213 sayılı VUK [ek m.1 / m.376 / m.116-124] ve ilgili mevzuat.

SONUÇ VE İSTEM:
- (Uzlaşma) … ihbarnamelere konu vergi ve cezalar için uzlaşma görüşmesine çağrılmamızı,
- (İndirim) VUK m.376 uyarınca cezada indirim yapılarak kalan vergi ve cezanın süresinde ödeneceğini bildirir,
  [vade / teminat] …
- (Düzeltme) … tutarındaki [hesap / vergilendirme] hatasının düzeltilerek fazla tahakkukun terkinini / iadesini,
saygılarımla arz ve talep ederim.

[Tarih]                                                    MÜKELLEF / VEKİLİ
                                                           [ad-soyad / unvan, imza]
EKLER: [ihbarname sureti, vergi inceleme raporu, belgeler, vekâletname]
```
Uzlaşma ve indirim başvuruları uygulamada çoğunlukla Gelir İdaresi'nin elektronik sistemi üzerinden de yapılabilir `[doğrula]`; dilekçe yine kayıt ve gerekçe için yararlıdır.

---

## Sık hatalar

- 🔴 30 günü ihbarnamenin düzenleme tarihinden saymak; ölçüt **tebliğ**dir.
- 🔴 Hem cezada indirim isteyip hem dava açmak (indirim düşer).
- 🔴 Uzlaşma vaki olmadıktan sonra dava süresini kaçırmak (ek m.7'deki 15 günlük uzama yalnızca süre bitmiş ya da 15 günden az kalmışsa).
- 🟠 7524 öncesi indirim oranlarını ya da mülga hükümleri kullanmak; m.376 ve ek m.1'i her seferinde çekmek.
- 🟠 Yorum farkını "vergi hatası" gibi düzeltme yoluyla çözmeye çalışmak.
- 🟡 Usulsüzlük cezası eşiğini kanunun eski (parantez dışı) tutarından okumak.

---

