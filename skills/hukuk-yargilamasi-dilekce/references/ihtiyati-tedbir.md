# İhtiyati tedbir talebi (ve tedbire itiraz)

## Ne zaman kullanılır
Dava konusu mal ya da hakkın dava sonuna kadar devredilmesini, değiştirilmesini önlemek ya da gecikmeden doğacak ciddi zararı engellemek. Para alacağının güvencesi için **ihtiyati haciz** (İİK m.257 vd.) ayrı yoldur → esası `icra-iflas` (`../../icra-iflas/references/menfi-tespit-istirdat-ve-ihtiyati-haciz.md`). 

---

## Şartlar ve süre tablosu

| Kural | Dayanak | Not |
|---|---|---|
| Tedbir sebebi: mevcut durumdaki değişme nedeniyle hakkın elde edilmesinin önemli ölçüde zorlaşması / imkânsızlaşması **ya da** gecikme nedeniyle sakınca veya ciddi zarar | HMK m.389/1 | Tehlikeyi somut belgeyle anlat (satış ilanı, devir girişimi).  |
| Dava öncesi: **esas hakkında görevli ve yetkili mahkemeden**; dava açıldıktan sonra **yalnız asıl davanın mahkemesinden** | HMK m.390/1 | Eski YAML "dava açılmamışsa görevli ve yetkili mahkeme" diyordu — doğru.  |
| Dilekçede tedbir **sebebi ve türü açıkça**; esas yönünden haklılığın **yaklaşık ispatı** | HMK m.390/3 |  |
| Karşı taraf dinlenmeden tedbir | HMK m.390/2 | Derhâl koruma zorunluluğu gerekçelendirilir. |
| **Teminat** | HMK m.392/1 | Kural teminattır; talep **resmî belgeye / kesin delile** dayanıyorsa ya da durum gerektiriyorsa mahkeme **gerekçesini açıkça belirterek** teminatsız tedbir verebilir; adli yardımdan yararlanan teminat göstermez. **Kanunda oran yok:** eski YAML'daki "genelde %10-15" kanuni değildir, uygulama tahminidir — dilekçeye yazma, `[incele]`.  |
| Dava öncesi tedbirden sonra **iki hafta içinde dava** ve evrakı memura ibraz | HMK m.397/1 | Süre, kararın **uygulanmasını talep ettiği** tarihten başlar; kaçarsa tedbir kendiliğinden kalkar. Dava şartı arabuluculukta, büroya başvurudan son tutanağa kadar bu süre işlemez.  |
| Karşı tarafın itirazı: **bir hafta** | HMK m.394/2 | Hazır ise uygulamadan, değilse uygulama tutanağının tebliğinden. İtiraz konusu: tedbirin şartları, yetki, teminat. Dava açıldıktan sonra itirazı davaya bakan mahkeme karara bağlar (7251/42 ek cümle). Üçüncü kişi öğrenmeden itibaren bir hafta (m.394/3). İtiraz dilekçeyle ve tüm delillerle (m.394/4).  |
| Teminat karşılığı tedbirin değiştirilmesi/kaldırılması | HMK m.395 |  |
| Teminat iadesi | HMK m.392/2 | Hükmün kesinleşmesinden ya da tedbirin kalkmasından itibaren bir ay içinde tazminat davası açılmazsa. |
| Adli tatil | HMK m.103/1-a | Tedbir talepleri ve itirazları adli tatilde de görülür.  |

**Uyuşmazlık konusu sınırı:** HMK m.389/1'e göre ihtiyati tedbir yalnız **uyuşmazlık konusu hakkında** verilebilir. Para alacağı davasında davalının dava konusu olmayan taşınır-taşınmazlarına ve banka hesaplarına tedbir konulamaz; para alacağının güvencesi **ihtiyati haciz**tir (İİK m.257 vd.) (İstanbul BAM 43. HD, E. 2025/135, K. 2025/144, 11.02.2025). Eski YAML'daki "küçük alacak için fabrikaya tedbir istenmez" örneği bu kuralın sonucudur; ayrıca bir ölçülülük denetimi için güncel Yargıtay kararı okunmadı — gerekiyorsa `legal_search_cases` ile ara. 

---

## Görüşme soruları (eski `data_schema`)
1. Dava açıldı mı? Açıldıysa mahkeme ve esas no; açılmadıysa görevli/yetkili mahkeme ("dava öncesi değişik iş") — `court_name`, `file_number`
2. Tedbir isteyen ve karşı taraf bilgileri — `requesting_party`, `opposing_party`
3. Tedbir konusu mal/hak: tapu (il, ilçe, ada, parsel), araç plakası, banka, şirket payı — `measure_subject`
4. İstenen tedbir türü: devir yasağı şerhi, kullanım yasağı, yediemin, işlem durdurma
5. Gecikmede sakınca: somut olay ve belge (satış ilanı, devir başvurusu, tarih) — `urgency_reason`
6. Yaklaşık ispat delilleri: sözleşme, senet, tapu kaydı, yazışma — `approximate_proof_evidence`
7. Teminat: ne kadar ve hangi türde verilebilir; teminatsız isteniyorsa resmî belge/kesin delil var mı; adli yardım? — `guarantee_status`
8. Karşı taraf dinlenmeden mi isteniyor? Neden?
9. Dava şartı arabuluculuk var mı? (varsa dava açma süresi için 6325 m.18/A-16)

## soorgla çağrıları
```
legal_get_statute_article  law_no: "6100"  article_no: "389" | "390" | "391" | "392" | "394" | "395" | "397"
legal_list_statute_articles  law_no: "6325"  law_type: "Kanun"  article_no: "18"  include_content: true
legal_search_cases  sorgu: "<tedbir türü> ihtiyati tedbir yaklaşık ispat teminatsız tedbir şartları"  mahkeme: "bam"  tarih_baslangic: <son 3 yıl>
legal_search_cases  sorgu: "<aynı>"  mahkeme: "yargitay"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
legal_calculate_court_fee  harc_turu: "basvurma_asliye"
```
Not: tedbir kararlarına karşı itiraz sonucu verilen kararlar kanun yoluna gidip "kesin" karara bağlandığından içtihat çoğunlukla **BAM** kararlarındadır (m.394/5); önce `mahkeme: "bam"` ile ara. 

## Dilekçe iskeleti (eski `ui_config`: başlık → taraflar → konu → gecikmede sakınca → yaklaşık ispat → teminat → sonuç)
```markdown
[YER] NÖBETÇİ [MAHKEME] MAHKEMESİ'NE
[Dava öncesi: "İHTİYATİ TEDBİR TALEBİ (DAVA ÖNCESİ)" | Dava içinde: "DOSYA NO: [___] E."]

TEDBİR İSTEYEN : [___] — VEKİLİ: Av. [___]
KARŞI TARAF    : [___]
KONU           : [Mal/hak] üzerine [tedbir türü] ihtiyati tedbiri konulması talebidir.

TEDBİR KONUSU  : [tapu: il/ilçe/ada/parsel | plaka | ___]

GECİKMESİNDE SAKINCA BULUNAN HÂL (HMK m.389)
1. [somut olay — tarih] (Delil: [___])

HAKLILIĞIMIZ VE YAKLAŞIK İSPAT (HMK m.390/3)
1. [___] (Delil: [___])

TEMİNAT (HMK m.392)
[Mahkemece takdir edilecek teminatı yatırmaya hazırız | Talebimiz resmî belgeye / kesin delile dayandığından teminatsız tedbir talep ederiz: ___]

SONUÇ VE İSTEM : [Teminatlı / teminatsız olarak] [karşı taraf dinlenmeden] [mal/hak] üzerine [tedbir türü] ihtiyati tedbir konulmasına karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```

## Sık hatalar
- 🔴 Dava öncesi tedbirden sonra iki haftada dava açılmamış ya da evrak memura ibraz edilmemiş.
- 🔴 Dava açıldıktan sonra başka mahkemeden tedbir istenmiş.
- 🟠 Tedbir sebebi ve türü açıkça yazılmamış; tehlike soyut.
- 🟠 Teminat oranı "kanunen %15" diye yazılmış.
- 🟡 Para alacağı için ihtiyati haciz yerine tedbir istenmiş.

