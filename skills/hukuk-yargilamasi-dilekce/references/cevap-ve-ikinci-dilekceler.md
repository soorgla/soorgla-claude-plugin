# Cevap dilekçesi, cevaba cevap (replik), ikinci cevap (düplik)

## Ne zaman kullanılır
- **Cevap:** davalı, dava dilekçesinin tebliğinden sonra savunmasını sunar.
- **Cevaba cevap:** davacı, cevap dilekçesine karşı.
- **İkinci cevap:** davalı, cevaba cevaba karşı.
Bu üç dilekçe **dilekçeler aşamasını** oluşturur. İddia ve savunmayı serbestçe genişletme/değiştirme imkânı **cevaba cevap ve ikinci cevapla biter**; ondan sonra genişletme ancak ıslah ya da karşı tarafın açık muvafakatiyle olur.

---

## Süre tablosu

| İşlem | Başlangıç | Süre ve dayanak | Not |
|---|---|---|---|
| Cevap dilekçesi | Dava dilekçesinin davalıya tebliği | **İki hafta** — HMK m.127 | |
| Ek cevap süresi talebi | Aynı iki hafta **içinde** başvurulmalı | Cevap süresinin bitiminden itibaren, **bir defaya mahsus, bir ayı geçmemek üzere** — HMK m.127 | Süre içinde istenmezse verilmez. Karar taraflara derhâl bildirilir. Hâkim takdiri `[incele]`. |
| Cevaba cevap | Cevap dilekçesinin davacıya tebliği | **İki hafta** — HMK m.136/1 | |
| İkinci cevap | Cevaba cevabın davalıya tebliği | **İki hafta** — HMK m.136/1 | |
| Adli tatil | — | HMK m.104 | Adli tatile tabi işlerde süre tatilde biterse tatil bitiminden itibaren bir hafta uzar. |

`legal_calculate_deadline` bu süreler için kod tanımıyor (`hmk_answer` → "Kural bulunamadı"); elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]`.

**Basit yargılama usulüne tabi işlerde** (ör. tüketici mahkemesi davaları, HMK Altıncı Kısım) dilekçeler aşaması farklıdır: cevap süresi yine **iki hafta**, ama ek süre **en çok iki hafta** (bir ay değil) ve **cevaba cevap ile ikinci cevap verilemez**.

---

## Cevap dilekçesinin zorunlu unsurları (HMK m.129/1)

a) Mahkemenin adı · b) Davacı ve davalının adı, soyadı, adresleri (davalı yurt dışındaysa yurt içi tebligat adresi) · c) Davalının T.C. kimlik no · ç) Varsa kanuni temsilci ve vekil bilgileri · d) Savunma vakıalarının **sıra numarası altında** özetleri · e) Her vakıanın hangi delille ispat edileceği · f) Hukuki sebepler · g) Açık talep sonucu · ğ) İmza. Belgeler m.121 uyarınca eklenir.

Esas numarası kanunda ayrı bent olarak sayılmaz ama uygulamada zorunludur; dilekçenin doğru dosyaya girmesi için başlığa yaz.

## İlk itirazlar ve dava şartları (eski YAML'daki hata düzeltildi)
- **İlk itirazlar yalnız ikidir:** (a) kesin yetki kuralı bulunmayan hâllerde **yetki itirazı**, (b) **tahkim itirazı**. Eski (c) bendi 7251 ile mülga.
- İlk itirazların **hepsi cevap dilekçesinde** ileri sürülmek zorundadır; sonra dinlenmez.
- **Görev, kesin yetki, derdestlik, kesin hüküm, hukuki yarar, dava şartı arabuluculuk** ilk itiraz değil **dava şartıdır**; re'sen gözetilir, her aşamada ileri sürülebilir. Yine de cevapta "usule ilişkin itirazlar" başlığında say.
- **Zamanaşımı** usul itirazı değil maddi hukuk def'idir; hâkim re'sen gözetmez, cevapta açıkça ileri sür. Hak düşürücü süre ise re'sen gözetilir. Zamanaşımı HMK m.116'daki ilk itirazlardan olmadığından cevapta ileri sürülme zorunluluğu kanundan değil **savunmanın genişletilmesi yasağından** doğar: cevap dilekçesinde ileri sürülmeyen ya da süresinden sonra verilen cevapla ileri sürülen zamanaşımı def'i, davacının **açık muvafakati** olmadıkça dikkate alınmaz (Yargıtay 4. HD, E. 2023/985, K. 2023/3219, 09.03.2023). Süresinde cevap verilmişse def'i cevabın **ıslahı** yoluyla da ileri sürülebilir; süresinde cevap hiç verilmemişse ıslahla getirilmesi tartışmalıdır — HGK E. 2022/710, K. 2024/488 bu konuyu (HUMK dönemi davada) inceledi, sonucunu kullanmadan önce tam metnini oku. Pratik kural: **def'iyi süresinde verilen cevap dilekçesine yaz** `[incele]`.

## Cevaba cevap / ikinci cevap stratejisi
- Bu dilekçeler, dava ve cevap dilekçelerine ilişkin hükümlere niteliğine aykırı düşmedikçe kıyasen tabidir (HMK m.136/2) — yani vakıa-delil eşleşmesi burada da gerekir.
- Eksik kalan **her** vakıa, talep ve delil şimdi eklenir; sonrası genişletme yasağıdır (m.141/1).
- Davacı: davalının usul itirazlarını ve esas savunmalarını tek tek karşıla. Davalı: yeni iddiaları cevapla; ilk cevabı tekrar etme, güçlendir.
- İspat yükü genel kuralı: kanunda aksine hüküm yoksa her taraf hakkını dayandırdığı olguları ispatla yükümlüdür (TMK m.6). Özel ispat kuralı (ör. 4857 m.20/2) varsa onu çek.

---

## Görüşme soruları
1. Mahkeme adı ve esas no? — `court_name`, `file_number`
2. Dava dilekçesinin (ya da cevabın / cevaba cevabın) **tebliğ tarihi** ve tebliğ şekli (UYAP, e-tebligat, fiziki)?
3. Kimin adına? (davalı / davacı) Taraf ve vekil bilgileri — `defendant_info`, `plaintiff_info`, `legal_representatives`
4. Yetki itirazı ya da tahkim şartı var mı? Sözleşmede yetki/tahkim maddesi?
5. Dava şartı eksikliği var mı (görev, arabuluculuk, derdestlik, hukuki yarar)? — `preliminary_objections`
6. Zamanaşımı ileri sürülecek mi? Olay ve dava tarihleri?
7. Karşı tarafın her iddiasına karşı savunma ve delil — `defense_narrative`, `counter_arguments`, `evidence_list`
8. Karşı dava açılacak mı? (harç ve süre ayrı — `[incele]`)
9. Ek süre gerekecek mi? Gerekiyorsa gerekçesi?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6100" article_no: "127" | "129" | "116" | "117" | "114" | "136" | "141"
legal_get_statute_article law_no: "6100" article_no: "317" # basit yargılama
legal_search_cases sorgu: "<savunma önermesi, ör. kesin yetki bulunmayan hâlde yetki itirazının cevap dilekçesinde yapılmaması>" mahkeme: "yargitay" tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar>
legal_check_holiday tarih: <hesaplanan son gün>
```

## Dilekçe iskeleti (eski `ui_config`: başlık → esas no → taraflar → konu → usule ilişkin → esasa ilişkin → içtihat → hukuki sebepler / deliller → sonuç)
```markdown
[YER] [__]. [MAHKEME TÜRÜ] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
[CEVAP DİLEKÇESİ | CEVABA CEVAP DİLEKÇESİ | İKİNCİ CEVAP DİLEKÇESİ]

DAVALI (veya DAVACI) : [___] (T.C. Kimlik No: [___]) — [ADRES]
VEKİLİ : Av. [___]
DAVACI (veya DAVALI) : [___]
KONU : [Davacının [tarih] tarihli dilekçesine karşı cevaplarımız / beyanlarımız]
TEBLİĞ TARİHİ : [___]

A. USULE İLİŞKİN İTİRAZLAR VE DEF'İLER
1. Yetki itirazı (HMK m.116/1-a): [yetkili mahkeme: ___]
2. Dava şartı eksikliği: [___]
3. Zamanaşımı def'i: [___]

B. ESASA İLİŞKİN CEVAPLAR
1. Davacının [__] numaralı iddiasına karşı: [___] (Delil: [___])
2. …

HUKUKİ SEBEPLER : [yalnız çekilmiş maddeler]
DELİLLER : [her delil — hangi vakıa]
SONUÇ VE İSTEM : [usulden ret / esastan ret]; yargılama giderleri ve vekâlet ücretinin davacıya yükletilmesine karar verilmesini saygıyla arz ve talep ederim. [TARİH]
                                        [İmza]
```

## Sık hatalar
- 🔴 Cevap süresi kaçmış ya da ek süre süre bittikten sonra istenmiş.
- 🔴 Yetki itirazında yetkili mahkeme gösterilmemiş; ilk itiraz sonraki dilekçeye bırakılmış.
- 🟠 Derdestlik/görev "ilk itiraz" olarak yazılmış (eski YAML hatası) — dava şartı olarak yaz.
- 🟠 Yeni vakıa ve delil ikinci dilekçeden sonraya bırakılmış.
- 🟡 Basit yargılama usulündeki davada cevaba cevap yazılmış.
