# Hukuk istinafı (HMK m.341-360)

İlk derece hukuk mahkemesinin (asliye hukuk, asliye ticaret, iş, tüketici, aile, sulh hukuk, icra mahkemesi hariç) kararına karşı bölge adliye mahkemesi (BAM) hukuk dairesine başvuru. Ayrıca: karşı tarafın istinafına **cevap** ve **katılma yoluyla istinaf**.

## Ne zaman kullanılır
- İlk derece mahkemesinin **nihai kararı** ya da ihtiyati tedbir/ihtiyati haciz kararlarının HMK m.341/1-b'de sayılanları.
- Ara kararlar kural olarak tek başına istinaf edilmez: m.341/1 istinafa açık kararları nihai kararlar ve sayılan ihtiyati tedbir/ihtiyati haciz kararlarıyla sınırlar; ara karara ilişkin şikâyet nihai kararın istinafında sebep olarak ileri sürülür (bunu ayrıca söyleyen bir HMK hükmü yok, kural m.341/1'den ve BAM içtihadından çıkar). Ara karara karşı ayrı istinaf dilekçesi verilirse HMK m.341 ve 352 uyarınca reddedilir. **İstisna:** kanunun ayrıca kanun yolu tanıdığı ara kararlar; ör. esas hüküm istinafa açık işlerde hâkimin reddi talebi hakkındaki merci kararına karşı **tebliğden itibaren iki hafta** içinde ayrı istinaf (m.43/2; BAM kararı kesin).
- **Kullanılmaz:** miktar veya değeri kesinlik sınırını geçmeyen malvarlığı davaları (manevi tazminat hariç) — sınırı `legal_get_social_parameters` → `istinaf_kesinlik_siniri`, dava tarihine göre. Kısmi davada sınır alacağın tamamına göre, tam davada reddedilen kısma göre belirlenir (m.341/3-4).
- Özel kanunla istinafı kesin olan işler: ör. işe iade davasında BAM kararı kesindir (4857 m.20/3) → temyiz yolu yoktur.

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | MCP |
|---|---|---|---|
| İstinaf: **iki hafta** | İlamın usulen taraflardan **her birine** tebliği | HMK m.345 | `legal_calculate_deadline` `hmk_appeal` |
| İstinafa cevap: **iki hafta** | İstinaf dilekçesinin karşı tarafa tebliği | HMK m.347/2 | araç tanımıyor → elle + `legal_check_holiday` |
| Katılma yoluyla istinaf | Cevap dilekçesiyle birlikte (başvuru süresi geçmiş olsa bile) | HMK m.348/1 | — |
| Katılma yoluyla başvuruya cevap: **iki hafta** | Katılma dilekçesinin tebliği | HMK m.348/1 | elle |
| Harç/gider eksikliğini tamamlama: **bir hafta (kesin)** | Mahkemenin yazılı bildirimi | HMK m.344 | elle |

- "Özel kanun hükümleri saklıdır": özel kanunda farklı süre varsa (ör. icra mahkemesi kararları İİK m.363) onu çek. Eski içtihatta İİK için "on gün" geçer; güncel metin **iki hafta** diyor.
- Ara karar ya da hüküm **tefhim** edilmiş olsa bile hukukta süre **tebliğden** işler; tefhimle başlayan bir hukuk istinaf süresi yoktur (bkz. `sure-tutum.md`).

## Zorunlu unsurlar (HMK m.342/2)

a) başvuran ile karşı tarafın davadaki sıfatları, adı, soyadı, T.C. kimlik numarası, adresleri · b) varsa kanuni temsilci ve vekillerin adı, soyadı, adresleri · c) kararı veren mahkeme, karar tarihi ve sayısı · ç) kararın başvurana **tebliğ tarihi** · d) kararın özeti · e) **başvuru sebepleri ve gerekçesi** · f) talep sonucu · g) imza.
- Karşı taraf sayısı kadar örnek eklenir (m.342/1).
- Kimlik, imza ve kararı belli eden kayıtlar varsa diğer eksikler dilekçeyi reddettirmez (m.342/3) — ama **sebep gösterilmezse BAM yalnız kamu düzeni yönünden inceler** (m.355). Bu nedenle (e) bendi fiilen zorunludur.
- Dilekçe kararı veren mahkemeye ya da başka bir yer mahkemesine verilebilir; dosya dilekçede gösterilen daireyle bağlı kalınmadan ilgili BAM'a gönderilir. Hitap: "… Bölge Adliye Mahkemesi İlgili Hukuk Dairesine gönderilmek üzere … Mahkemesine".

## İstinaf sebepleri — nasıl gruplanır
BAM'ın verebileceği kararlar HMK m.353'tedir; sebepleri buna göre grupla, talep sonucunu da buna bağla:
1. **Kaldırıp geri gönderme sebepleri (m.353/1-a):** davaya bakması yasak hâkim, haklı ret talebine rağmen reddedilen hâkim, görev/yetki hatası, diğer dava şartlarına aykırılık, usule aykırı açılmamış sayma/birleştirme/ayırma, **önemli delillerin toplanmaması veya değerlendirilmemesi**, talebin önemli bir kısmı hakkında karar verilmemesi.
2. **Esasa ilişkin sebepler (m.353/1-b; duruşmalı inceleme m.356-357):** delillerin yanlış değerlendirilmesi, bilirkişi raporundaki çelişki, hukukun yanlış uygulanması, hesap hatası, gerekçe hatası.
- Eski YAML "usule ilişkin sebepler (HMK 353 / CMK 289)" diyordu: HMK m.353 BAM'ın karar türlerini düzenler, sebep listesi değildir; CMK m.289 ceza temyizine aittir. Dilekçede sebepleri m.353'e **göre gruplayarak** yaz, m.353'ü "sebep maddesi" diye gösterme.
- **Yeni iddia ve delil yasağı (m.357):** BAM'da karşı dava, müdahale, ıslah yoktur; resen gözetilecekler dışında ilk derecede ileri sürülmeyen iddia ve savunma dinlenmez, yeni delile dayanılamaz. İstisna: ilk derecede usulüne uygun gösterilip incelenmeden reddedilen ya da mücbir sebeple gösterilemeyen deliller (m.357/3) — bunu dilekçede ayrı başlıkta belirt.

## Görüşme soruları (data_schema → sorular)
1. Kararı veren mahkeme, esas ve karar numarası, karar tarihi? (`court_name`, `file_number`)
2. Gerekçeli karar size hangi tarihte tebliğ edildi (UYAP/e-Tebligat/fiziki)? Karşı tarafa ne zaman tebliğ edildi? (`decision_summary` → tebliğ)
3. Dava hangi tarihte açıldı, dava değeri ne, kısmi mi, (31.07.2026 öncesi açıldıysa) belirsiz alacak mı, tam mı? (kesinlik)
4. Kim istinaf ediyor (davacı/davalı/fer'i müdahil), vekil kim? Karşı taraf(lar) kim, adresleri? (`party_info`, `opposing_party`)
5. Kararın hüküm fıkrası: neler kabul, neler ret edildi? Hangi kısmı istinaf ediyorsunuz?
6. Usule ilişkin itirazlarınız (görev, yetki, dava şartı, delil toplanmaması, hâkimin reddi)? (`procedural_errors`)
7. Esasa ilişkin itirazlarınız (delil değerlendirmesi, bilirkişi raporu, hukuk kuralının yanlış uygulanması)? (`substantive_errors`)
8. Karar gerekçesinin itiraz ettiğiniz pasajları (sayfa/paragraf)?
9. İlk derecede ileri sürülüp değerlendirilmeyen delil ya da talep var mı?
10. Duruşma talebi, ihtiyati tedbir veya icranın geri bırakılması talebi gerekiyor mu? `[incele]`
11. Karşı taraf da istinaf etti mi (cevap ve katılma yoluyla istinaf için)?

## soorgla çağrıları
```
legal_get_social_parameters tur: "istinaf_kesinlik_siniri" # dava tarihi yılına dikkat
legal_get_statute_article law_no: "6100" article_no: "341" | "342" | "343" | "344" | "345" | "347" | "348" | "353" | "355" | "ek 1"
legal_calculate_deadline kural_kodu: "hmk_appeal" baslangic_tarihi: <tebliğ>
legal_check_holiday tarih: <elle hesaplanan son gün>
legal_get_social_parameters tur: "harc_istinaf_bam"
legal_search_cases mahkeme: "bam" sorgu: "<olay + hata türü, ör. bilirkişi raporundaki çelişki giderilmeden hüküm kurulması>" tarih_baslangic: <son 3 yıl>
legal_search_cases mahkeme: "yargitay" daire: "Hukuk Genel Kurulu" sorgu: "<ilke>"
legal_get_case_document belge_id: <seçilen güncel karar>
```

## Dilekçe iskeleti (eski `ui_config` blok sırası korunarak)
```markdown
[BÖLGE ADLİYE MAHKEMESİ] İLGİLİ HUKUK DAİRESİNE
Gönderilmek üzere
[___] [___]. [ASLİYE HUKUK / İŞ / …] MAHKEMESİNE

DOSYA NO : [___] Esas — [___] Karar

İSTİNAF EDEN : [ad soyad / unvan], T.C. [___], [adres] ([davacı/davalı])
VEKİLİ : Av. [___], [adres]
KARŞI TARAF : [___], T.C. [___], [adres] ([davacı/davalı])
VEKİLİ : [___]

KARAR TARİHİ : [___]
TEBLİĞ TARİHİ : [___]

KONU : Yukarıda numarası yazılı dosyada verilen [__.__.____] tarihli kararın
                  usul ve esas yönünden hukuka aykırı olması nedeniyle istinaf yoluyla
                  incelenerek KALDIRILMASI talebidir.

KARARIN ÖZETİ : [hüküm fıkrası özeti]

AÇIKLAMALAR :
A. Usule ilişkin istinaf sebepleri
  1. [sebep — karar gerekçesindeki pasaj — neden hatalı — dayanak madde]
B. Esasa ilişkin istinaf sebepleri
  1. [sebep — …]
C. Emsal kararlar
  [soorgla'dan çekilmiş, tam metni okunmuş en az bir güncel karar; neyi desteklediği]

HUKUKİ NEDENLER : HMK m.341 vd., [ilgili maddi hukuk maddeleri]
DELİLLER : Dosya kapsamı, [___]

SONUÇ VE İSTEM : Açıklanan nedenlerle; [___] tarihli kararın KALDIRILMASINA,
                  [HMK m.353/1-a hâlinde: dosyanın yeniden görülmek üzere ilk derece
                  mahkemesine gönderilmesine | m.353/1-b hâlinde: davanın esası
                  hakkında yeniden hüküm kurularak davanın KABULÜNE/REDDİNE],
                  yargılama giderleri ve vekâlet ücretinin karşı tarafa yükletilmesine
                  karar verilmesini saygıyla arz ve talep ederim.

                                         [tarih]
                                         İstinaf eden vekili
                                         Av. [___] (e-imza)
EKLER: Vekâletname örneği, [___]
```
Eski YAML'daki "Süre uyarısı" kutusu dilekçeye girmez; değerlendirme bölümündeki süre tablosuna taşındı.

### İstinafa cevap / katılma yoluyla istinaf iskeleti
Başlık aynı; "İSTİNAF EDEN" yerine "CEVAP VEREN (İSTİNAF EDİLEN)". Konu: "… istinaf dilekçesine karşı cevaplarımızın sunulması [ve HMK m.348 uyarınca katılma yoluyla istinaf] talebidir." Katılma yoluyla istinaf ediliyorsa sebepler ayrı başlıkta ve harcı yatırılarak. Asıl başvuru feragat ya da esasa girilmeden ret ile düşerse katılma başvurusu da reddedilir (m.348/2) — kullanıcıya söyle.

## Sık hatalar
- 🔴 Süreyi tefhimden ya da kısa karardan saymak, ya da tersine "gerekçeli karar gelince bakarız" diyip tebliği kaçırmak (e-Tebligatta tebliğ, iletimi izleyen beşinci gün yapılmış sayılır).
- 🔴 Kesin karara başvurmak; dava tarihindeki sınır yerine bugünkü sınırı kullanmak.
- 🟠 Sebep yazmadan "karar usul ve yasaya aykırıdır" demek (m.355 riski).
- 🟠 Ayrıntılı dilekçeyi süre geçtikten sonra vermek: sonradan verilen ek dilekçe dikkate alınmayabilir (bkz. `sure-tutum.md`).
- 🟡 Harç ve gider avansını eksik yatırmak (m.344).
- 🟡 Talep sonucunu "bozulması" diye yazmak; hukuk istinafında doğru ifade "kaldırılması"dır.
