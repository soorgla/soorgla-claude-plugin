# Delil ve tanık listesi

## Ne zaman kullanılır
Mahkemenin verdiği kesin süre içinde (genelde ön inceleme ara kararıyla) tanık listesi, eldeki belgeler ve getirtilecek kayıtların bildirilmesi. Dava/cevap dilekçesinde delil gösterilmiş olsa bile tanıkların ad ve adresleri çoğu zaman bu listeyle verilir.

---

## Süre ve kural tablosu

| Kural | Dayanak | Not |
|---|---|---|
| Liste süresi | Mahkemenin ara kararı (kesin süre) | Süreyi ara kararın tebliğinden/tefhiminden say; kesin süre kaçarsa delile dayanma hakkı düşebilir. `[incele]` |
| **İkinci tanık listesi verilemez**; listede olmayan dinlenmez | HMK m.240/2 | Kullanıcıyı **bütün** tanıkları şimdi yazması için uyar. |
| Listede tanık dinletilecek **vakıa**, tanığın **adı, soyadı ve tebliğe elverişli adresi** | HMK m.240/2 | T.C. kimlik no kanunda sayılmaz ama tebligat için yararlıdır. |
| Adres yoksa ya da tanık bulunamazsa: işin niteliğine uygun **kesin süre**; yine gösterilmezse tanıktan vazgeçilmiş sayılır | HMK m.240/3 | |
| Somutlaştırma; hangi delil hangi vakıa için | HMK m.194/1-2 | |
| Başka yerden getirtilecek belge için bulunmasını sağlayacak açıklama | HMK m.121 (dava dilekçesi); m.195 (getirtilecek belge) | |
| **Senetle ispat zorunluluğu** | HMK m.200 + ek m.1 | Hukuki işlemin **yapıldığı tarihteki** sınırı aşan işlemler senetle ispat edilir; sınır her yıl yeniden değerleme oranıyla artar — tutarı beceriye yazma, işlem tarihine göre çek. Karşı tarafın açık muvafakatiyle tanık dinlenebilir (m.200/2). Delil başlangıcı ve senede karşı tanık için m.201-202. |

---

## Görüşme soruları (eski `data_schema`)
1. Mahkeme, esas no, delil sunan taraf ve vekil — `court_name`, `file_number`, `party_info`
2. Mahkemenin verdiği süre ve ara kararın tebliğ/tefhim tarihi?
3. Tanıklar: ad soyad, adres, (varsa T.C. no, telefon), **hangi vakıa** için — `witness_list`
4. Daha önce tanık listesi verildi mi? (verildiyse ikinci liste yasağı)
5. Elinizdeki belgeler (fotoğraf, sözleşme, yazışma, fatura) — `documents_attached`
6. Kurumlardan getirtilecek kayıtlar: kurum, dosya/sicil no, tarih aralığı (tapu, SGK hizmet dökümü, banka hesap hareketleri, HTS, UYAP dosyası, ticaret sicili) — `documents_to_subpoena`
7. İspat edilecek hukuki işlemin tarihi ve değeri (senetle ispat kontrolü)

## soorgla çağrıları
```
legal_get_statute_article law_no: "6100" article_no: "240" | "194" | "195" | "200" | "201" | "202"
legal_get_statute_article law_no: "6100" article_no: "ek 1"
legal_search_cases sorgu: "ikinci tanık listesi verilemez, listede gösterilmeyen tanığın dinlenmesi bozma sebebi" mahkeme: "yargitay" tarih_baslangic: <son 3 yıl>
legal_get_case_document belge_id: <seçilen karar>
```

## Dilekçe iskeleti (eski `ui_config`: başlık → esas no → taraf → konu → uyarı → A. tanıklar → B. celbedilecek belgeler → C. ekte sunulanlar → sonuç)
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
[DAVACI / DAVALI] : [___]
VEKİLİ : Av. [___]
KONU : Sayın Mahkemenin [tarih] tarihli ara kararı uyarınca tanık ve delil listemizin sunulmasıdır.

A. TANIK LİSTEMİZ (HMK m.240)
| # | Ad Soyad | Tebliğe elverişli adres | Dinletilecek vakıa |
|---|---|---|---|
| 1 | [___] | [___] | Açıklamalar m.[__]: [___] |

B. GETİRTİLMESİNİ TALEP ETTİĞİMİZ BELGELER
1. [Kurum] — [kayıt/dosya no, tarih aralığı] — İspat edilecek vakıa: [___]

C. EKTE SUNULAN BELGELER
1. [___] — İspat edilecek vakıa: [___]

SONUÇ VE İSTEM : Tanıkların davetiye ile çağrılarak dinlenmesine, (B) bölümündeki belgelerin ilgili yerlerden getirtilmesine karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```
İç uyarı (dilekçeye girmez): "Bu listeden sonra ikinci tanık listesi verilemez (HMK m.240/2)."

## Sık hatalar
- 🔴 Bazı tanıklar "sonra bildiririz" diye dışarıda bırakılmış (ikinci liste yasağı).
- 🔴 Senetle ispat gereken işlem için yalnız tanık gösterilmiş; muvafakat ya da delil başlangıcı aranmamış.
- 🟠 Tanığın hangi vakıa için dinleneceği yazılmamış.
- 🟠 Getirtilecek kayıt için kurum/sayı/tarih yok — müzekkere yazılamıyor.
