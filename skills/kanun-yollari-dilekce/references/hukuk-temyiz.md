# Hukuk temyizi (HMK m.361-373)

Bölge adliye mahkemesi (BAM) hukuk dairesinin temyize açık nihai kararına ve hakem kararlarının iptali talebi üzerine verilen karara karşı Yargıtay'a başvuru; ayrıca temyize cevap ve katılma yoluyla temyiz.

## Ne zaman kullanılır
- BAM hukuk dairelerinin **temyizi kabil nihai kararları** ile hakem kararlarının iptali talebi üzerine verilen kararlar.
- Davada haklı çıkan taraf da hukuki yararı varsa temyiz edebilir (m.361/2).
- **Kullanılmaz (HMK m.362/1):**
  - miktar veya değeri **temyiz sınırını** geçmeyen davalar → `legal_get_social_parameters` → `temyiz_siniri` (dava tarihine göre; ek m.1/2);
  - sulh hukukun görevindeki davalar (kira alacağı vb. istisnalarla), görev/yetki ve yargı yeri belirleme kararları, çekişmesiz yargı, nüfus kaydı düzeltme (soybağı hariç), nakil kararları, geçici hukuki korumalar, m.353/1-a kapsamında verilen kaldırma kararları;
  - **m.362/3 (7589 ile, 2026):** BAM istinafı kabul edip esas hakkında yeniden karar verdiyse, kabul ya da ret edilen kısım istinaf kesinlik sınırını aşıyorsa temyiz edilebilir; ancak ilk derece kararıyla fark istinaf sınırını geçmiyorsa ya da yalnız yargılama gideri/vekâlet ücretine ilişkinse temyiz yolu kapalıdır. Bu fıkranın yürürlük ve geçiş kuralını kontrol et.
  - özel kanunla BAM kararı kesin olan işler (ör. işe iade — 4857 m.20/3).
- Kısmi davada sınır alacağın tamamına göre; tam davada reddedilen kısma göre; karşı taraf temyiz ederse sınırın altında kalan taraf cevap dilekçesiyle temyiz edebilir (m.362/2).

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | MCP |
|---|---|---|---|
| Temyiz: **iki hafta** | BAM kararının tebliği | HMK m.361/1 | `legal_calculate_deadline` `hmk_cassation` |
| Temyize cevap: **iki hafta** | Temyiz dilekçesinin tebliği | HMK m.366 → m.347/2 kıyasen | elle |
| Katılma yoluyla temyiz | Cevap dilekçesiyle | m.366 → m.348 kıyasen | — |
| Harç/gider tamamlama: **bir hafta (kesin)** | Bildirim | m.366 → m.344 | elle |
| Duruşma gününe en az **iki hafta** | Davetiyenin tebliği | HMK m.369/2 | — |

Eski YAML "HMK 361 — kararın tebliğinden itibaren 2 hafta" diyordu: **teyit edildi.**

## Temyiz sebepleri (HMK m.371)

a) hukukun veya taraflar arasındaki sözleşmenin yanlış uygulanması · b) dava şartlarına aykırılık · c) delillerin kanuni bir sebep olmaksızın kabul edilmemesi · ç) karara etki eden yargılama hatası veya eksiklikleri.
- Yargıtay sebeplerle bağlı değildir; kanunun açık hükmüne aykırılığı da inceleyebilir (m.369/1). Yine de her sebebi ayrı yaz.
- Temyiz bir olay incelemesi değildir: BAM'ın delil takdirine itiraz ediyorsan bunu (c) ya da (ç) bendine, yani bir **hukuk kuralının** ihlaline bağla.
- Eski YAML "temyiz ancak hükmün hukuka aykırı olması nedenine dayanabilir (HMK 371 / CMK 288)" diyordu: bu cümle CMK m.288'in metnidir; hukukta m.371'deki dört bent yazılır.

## Duruşmalı inceleme (HMK m.369/2)
- Dosya üzerinde inceleme asıldır. Tüzel kişiliğin feshi, genel kurul kararlarının iptali, evlenmenin butlanı/iptali, boşanma/ayrılık, velayet, soybağı, kısıtlama davalarında ve **duruşma sınırını** aşan alacak ve ayın davalarında taraflardan biri temyiz veya cevap dilekçesinde isterse duruşma yapılır.
- Duruşma sınırı ek m.1 ile her yıl artar ve dava tarihindeki miktar esas alınır; `legal_get_social_parameters` bu kalemi **döndürmüyor** → madde metnindeki tutarı yeniden değerleme oranlarıyla elle güncelleme, kullanıcıdan güncel sınırı teyit etmesini iste `[doğrula]`.
- Tebligat gideri verilmemişse duruşma talebi dikkate alınmaz (m.369/2). Talep varsa gideri hatırlat.

## Görüşme soruları (data_schema → sorular)
1. BAM dairesi, esas ve karar numarası, karar tarihi? İlk derece mahkemesi ve dosya numarası? (`court_name`, `file_number`)
2. BAM kararı size hangi tarihte tebliğ edildi? (`decision_summary`)
3. BAM ne karar verdi: istinafın esastan reddi, kaldırıp yeniden esas hakkında karar, kaldırıp geri gönderme (m.353/1-a — temyiz kapalı)?
4. Dava tarihi ve değeri; kısmi/tam/(31.07.2026 öncesi açıldıysa) belirsiz alacak? (temyiz sınırı)
5. Temyiz eden ve karşı taraf, vekiller, adresler? (`party_info`, `opposing_party`)
6. Hukuka aykırılıklar: hangi kural, hangi gerekçe pasajı? (`cassation_grounds`)
7. Duruşma isteniyor mu, dava türü/değer bunu mümkün kılıyor mu? (`hearing_request`)
8. Aynı konuda Yargıtay ilgili dairesinin ya da HGK'nın aksi yönde kararı var mı (içtihat aykırılığı)?

## soorgla çağrıları
```
legal_get_social_parameters tur: "temyiz_siniri"
legal_get_statute_article law_no: "6100" article_no: "361" | "362" | "366" | "369" | "371" | "ek 1"
legal_calculate_deadline kural_kodu: "hmk_cassation" baslangic_tarihi: <tebliğ>
legal_get_social_parameters tur: "harc_temyiz_yargitay"
legal_search_cases mahkeme: "yargitay" daire: "<ilgili hukuk dairesi>" sorgu: "<hukuka aykırılık cümlesi>" tarih_baslangic: <son 3 yıl>
legal_search_cases mahkeme: "yargitay" daire: "Hukuk Genel Kurulu" sorgu: "<ilke>"
legal_case_facets mahkeme: "yargitay" sorgu: "<konu>" # hangi daire bakıyor
legal_get_case_document belge_id: <seçilen güncel karar>
```
Daire iş bölümü her yıl değişebilir; dilekçeye "Yargıtay İlgili Hukuk Dairesine" yaz, daire numarasını sabitleme.

## Dilekçe iskeleti (eski `ui_config` blok sırası korunarak)
```markdown
YARGITAY İLGİLİ HUKUK DAİRESİNE
Gönderilmek üzere
[___] BÖLGE ADLİYE MAHKEMESİ [___]. HUKUK DAİRESİNE

BAM DOSYA NO : [___] Esas — [___] Karar
İLK DERECE DOSYA NO : [___] [___] Mahkemesi [___] E. — [___] K.

TEMYİZ EDEN : [___], T.C. [___], [adres] ([davacı/davalı])
VEKİLİ : Av. [___]
KARŞI TARAF : [___], T.C. [___], [adres]
VEKİLİ : [___]

BAM KARAR TARİHİ : [___]
TEBLİĞ TARİHİ : [___]

KONU : [___] Bölge Adliye Mahkemesi [___]. Hukuk Dairesinin [___] tarihli
                        ve [___] sayılı kararının hukuka aykırı olması nedeniyle temyizen
                        incelenerek BOZULMASI [ve duruşmalı inceleme yapılması] talebidir.

[DURUŞMA TALEBİ — yalnız m.369/2 şartları varsa:
 Dosyanın niteliği / değeri HMK m.369/2 kapsamında olduğundan temyiz incelemesinin
 duruşmalı yapılmasını talep ederiz. Tebligat gideri yatırılmıştır.]

TEMYİZ SEBEPLERİ VE HUKUKA AYKIRILIKLAR :
  1. [HMK m.371/1-(a/b/c/ç)] — [BAM gerekçesindeki pasaj] — [ihlal edilen kural] — [etkisi]
  2. …
YARGITAY İÇTİHATLARI : [soorgla'dan çekilmiş, tam metni okunmuş en az bir güncel karar]
HUKUKİ NEDENLER : HMK m.361 vd., m.371; [maddi hukuk]
SONUÇ VE İSTEM : Açıklanan nedenlerle BAM kararının BOZULMASINA, [duruşma yapılmasına],
                        yargılama giderleri ve vekâlet ücretinin karşı tarafa yükletilmesine
                        karar verilmesini saygıyla arz ve talep ederim.
                                         [tarih] — Temyiz eden vekili Av. [___] (e-imza)
```

## Sık hatalar
- 🔴 BAM'ın m.353/1-a kapsamındaki geri gönderme kararını temyiz etmek (m.362/1-g: temyiz yolu kapalı).
- 🔴 Temyiz sınırını bugünkü yıla göre almak; dava tarihindeki sınır esastır.
- 🟠 Temyiz dilekçesini istinaf dilekçesinin kopyası gibi yazmak: olay ve delil tartışması yerine m.371 bentlerine bağlı hukuki gerekçe gerekir.
- 🟠 Duruşma talebini temyiz dilekçesine yazmayıp sonra istemek; ya da tebligat giderini yatırmamak.
- 🟡 Daire numarasını ezberden yazmak.
