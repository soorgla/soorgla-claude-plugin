# Eski hâle getirme

## Ne zaman kullanılır
Kanunda belirtilen ya da hâkimin **kesin** olarak belirlediği süre **elde olmayan sebeplerle** kaçırıldı (ağır hastalık, doğal afet, usulsüz tebligatla öğrenememe vb.) ve ulaşılmak istenen sonuca başka bir hukuki yoldan ulaşılamıyor. 

Önce kontrol et: başka yol var mı? (ör. usulsüz tebligatta tebliğin öğrenme tarihine göre yeniden hesaplanması; mahkemeden yeni kesin süre). Varsa eski hâle getirme istenemez (m.95/2) `[incele]`.

---

## Süre tablosu

| Kural | Dayanak | Not |
|---|---|---|
| Talep süresi: **engelin ortadan kalkmasından itibaren iki hafta** | HMK m.96/1 | Engelin kalktığı tarihi belgeyle göster (taburcu tarihi, rapor bitişi).  |
| Son sınır: ilk derece ve istinafta **en geç nihai karar verilinceye kadar** | HMK m.96/2 | İstisna: nihai karar bir tarafın yokluğunda verilmişse, tahkikatta kaçırılan süreler için karardan sonra da istenebilir.  |
| Dilekçeyle; sebepler ve **delil veya emareleri** gösterilir | HMK m.97 |  |
| **Kaçırılan işlem de aynı iki haftalık süre içinde yapılır** | HMK m.97 | Cevap dilekçesi, istinaf dilekçesi vb. ekte değil, aynı süre içinde ve tam olarak sunulur. Eksik olursa talep reddedilir. 🔴 |
| Merci | HMK m.98 | İşlem hangi mahkemede incelenecek idiyse o mahkeme; istinaf hakkı düştüyse **bölge adliye mahkemesi**, temyiz hakkı düştüyse **Yargıtay**.  |

`legal_calculate_deadline` bu süre için kod tanımıyor; elle hesapla, `[doğrula]`.

**Emsal (tam metin okundu):** Gerekçeli karar yalnız davacı vekiline tebliğ edilmiş, vekil istinaf süresinin son gününü kapsayan tarihlerde hastanede yatmış (epikriz), taburcu olduktan sonra iki hafta içinde eski hâle getirme istemli istinaf dilekçesi vermiştir. BAM, yetki belgeli başka avukatlar bulunduğu gerekçesiyle süreden reddetmiş; Yargıtay 9. HD, kararın o avukatlara tebliğ edilmediğini, vekilin elinde olmayan sebeple süreyi kaçırdığını ve talebin m.96/1 süresinde olduğunu belirterek BAM kararını yerinde görmedi. Dilekçede **epikriz/rapor tarihleri ile tebliğin kime yapıldığını** mutlaka göster.  

Eski YAML "Covid-19, ani ameliyat" mazeretlerinin kabul edildiği kararları öneriyordu; bu turda bu konuda karar çekilmedi. Mazeretin "elde olmayan" sayılıp sayılmayacağı takdire bağlıdır `[incele]`.

---

## Görüşme soruları (eski `data_schema`)
1. Kaçırılan işlemi yapacak mahkeme ve esas no — `court_name`, `file_number`
2. Talep eden ve karşı taraf — `requesting_party`, `opposing_party`
3. Kaçırılan işlem ne? (cevap, istinaf, bilirkişi itirazı, kesin süreli işlem) — `missed_action`
4. Süre ne zaman başladı, ne zaman bitti?
5. Engel neydi, ne zaman başladı, **ne zaman kalktı**? Belge? — `excuse_details`, `evidence_list`
6. Vekil var mıydı? Engel vekilde mi, asılda mı? (vekil varsa başka avukat görevlendirebilir miydi — takdir `[incele]`)
7. Kaçırılan işlemin metni hazır mı? (aynı süre içinde sunulmalı)
8. Başka bir hukuki yol var mı (tebligat usulsüzlüğü vb.)?

## soorgla çağrıları
```
legal_get_statute_article  law_no: "6100"  article_no: "95" | "96" | "97" | "98" | "99"
legal_search_cases  sorgu: "<mazeret türü> nedeniyle süre kaçırılması eski hâle getirme talebinin kabulü"  mahkeme: "yargitay"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
legal_check_holiday  tarih: <son gün>
```

## Dilekçe iskeleti (eski `ui_config`: başlık → taraflar → konu → yasal uyarı → açıklamalar ve mazeret → yapılmak istenen işlem → hukuki sebepler/deliller → sonuç)
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
TALEP EDEN  : [___] — VEKİLİ: Av. [___]
KARŞI TARAF : [___]
KONU        : Elde olmayan sebeple süresinde yapılamayan [işlem]'in HMK m.95 vd. uyarınca eski hâle getirilmesi ve [işlem]'imizin kabulü talebidir.

AÇIKLAMALAR VE MAZERETİMİZ
1. [Süre: başlangıç ___, bitiş ___]
2. [Engel: ne, başlangıç ___] (Delil: [rapor/tutanak])
3. [Engelin kalktığı tarih: ___] — talebimiz bu tarihten itibaren iki hafta içindedir.
4. Ulaşılmak istenen sonuca başka bir hukuki yoldan ulaşılamamaktadır (HMK m.95/2).

YAPILMAK İSTENEN İŞLEM
[Kaçırılan işlemin tam metni bu dilekçeyle birlikte / ekte sunulmaktadır (HMK m.97).]

HUKUKİ SEBEPLER : HMK m.95-97, [___]
DELİLLER        : [hastane raporu, taburcu belgesi, afet tutanağı …]
SONUÇ VE İSTEM  : Eski hâle getirme talebimizin kabulüne, süresinde yapılamayan [işlem]'in süresinde yapılmış sayılmasına karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
EKLER: 1. [Kaçırılan işlemin metni] 2. [Mazeret belgeleri]
```

## Sık hatalar
- 🔴 Kaçırılan işlem aynı süre içinde yapılmamış ("sonra sunacağız").
- 🔴 İki hafta engelin kalkmasından değil başka bir tarihten sayılmış.
- 🟠 Mazeret belgesiz ya da engelin kalktığı tarih belirsiz.
- 🟠 Başka hukuki yol varken eski hâle getirme istenmiş (m.95/2).

