# Resmî yazı (üst yazı) ve makam oluru

Kamu idaresinin kurum içi ya da kurumlar arası yazışması ve bir işlem için yetkili makamdan alınan onay (olur). Biçim kuralları **Resmî Yazışmalarda Uygulanacak Usul ve Esaslar Hakkında Yönetmelik**tedir (RG 10.06.2020, s.31151; soorgla'da `law_no: "2646"`).  Eski YAML'lardaki "31151 Sayılı Yönetmelik" ifadesi Resmî Gazete sayısıdır, yönetmelik numarası değil.

Biçim kurallarını bu dosyadan değil, gerektiğinde maddeden çek: `legal_get_statute_article law_no: "2646" article_no: "<n>" law_type: "21"`. (`law_type` verilmezse araç aynı maddeyi 3-5 kez tekrarlıyor.)

Yönetmelikteki "Örnek 1-18" belge görselleri soorgla'da yoktur; düzen için madde metnine dayan.

---

## Ne zaman kullanılır

- **Resmî yazı:** bilgi verme, bilgi/belge isteme, talimat, görüş, iade, dağıtımlı duyuru.
- **Makam oluru:** görevlendirme, harcama, ihale onayı, soruşturma açılması, yetki devri gibi bir işlemin yapılması için üst makamdan onay. Olurun dayanağı olan maddi mevzuatı (657, 4734, 5018 vb.) kullanıcıdan al ve maddeyi çek.

Süreye bağlı değildir; ancak cevap süresi verilen yazılarda süreyi metinde açıkça yaz.

---

## Biçim kuralları (doğrulanan maddeler)

| Unsur | Kural | Dayanak |
|---|---|---|
| Başlık | Ortalı; 1. satır "T.C.", 2. satır idare adı **büyük harf**, 3. satır birim adı ilk harfleri büyük. Bağlı/ilgili idarede dört satır olabilir; il ve ilçe teşkilatında mülki idare adı. Başlık DETSİS kaydına göre yazılır. | m.10  |
| Sayı | Zorunlu. Sıra: "E" (elektronik) / "Z" (zorunlu hâl) / "O" (olağanüstü) – DETSİS numarası – standart dosya planı kodu – kayıt numarası; aralarda kısa çizgi (ör. `E-67915368-903.07.02-4752`). Başlığın son satırından iki satır aşağıda, solda. Kayıt numarası EBYS'den alınır. | m.11  |
| Tarih | Sayı ile aynı satırda, yazı alanının en sağında; `gg.aa.yyyy` (ör. 01.09.2019) ya da ay harfle (10 Ekim 2019). E-imzalı belgede **son yetkilinin e-imza zaman damgası** belge tarihidir. Tutanak ve raporlarda tarih metnin sonunda olabilir. | m.12  |
| Konu | "Sayı:"nın bir alt satırında; kelimelerin baş harfleri büyük, sonunda noktalama yok, yazı alanının dikey orta hizasını geçmez; kısa ve öz | m.13  |
| Muhatap | Konunun son satırından iki satır aşağıda, **ortalı**; idare/tüzel kişi adı **büyük harf** ve yönelme hâl eki ("… BAKANLIĞINA"); birim adı gerekirse alt satırda parantez içinde. Gerçek kişide "Sayın Ad SOYAD". Dağıtımlı belgede "DAĞITIM YERLERİNE". | m.14  |
| İlgi | Muhataptan iki satır aşağıda, solda; birden fazlaysa eskiden yeniye "a)", "b)" sırasıyla; "… tarihli ve … sayılı …" kalıbı, sonunda nokta; ilgi tutulan belgeyi gönderen idarenin adı yazılır (muhatabın kendi yazısıysa yazılmaz); gerçek kişiden gelen için "…'ın … tarihli başvurusu/dilekçesi." | m.15  |
| Metin | İlgiden bir satır, ilgi yoksa muhataptan iki satır sonra; paragraf girintisi 1,25 cm, iki yana yaslı, paragraflar arasında boşluk yok; dört ve üstü haneli sayılarda nokta (1.452), kesirde virgül; TDK Yazım Kılavuzu; kısaltma ilk geçtiği yerde açık yazılır; harfle maddelendirme "a)" biçiminde. | m.16/1-11  |
| **Bitiş ibaresi** | Alt makama "… rica ederim."; üst ve **aynı düzey** makama "… arz ederim."; üst/aynı düzey ve alt makamlara dağıtımlıda "… arz ve rica ederim." veya "… arz/rica ederim."; yetki devriyle imzada **yetkiyi devreden makamın** hiyerarşisine göre; gerçek kişiye "Saygılarımla.", "İyi dileklerimle." veya "Bilgilerinize sunulur." | m.16/12  |
| İmza | Metinden 2-4 satır sonra, yazı alanının en sağında ortalı; ad ilk harfi büyük, SOYAD büyük, altta unvan. Yetki devrinde 2. satıra "Vali a.", "Genel Müdür a." vb.; vekâlette "Genel Müdür V." vb. İki imzada üst unvan sağda; ikiden fazlada en üst unvan **en solda**. E-imzalı belgede ad-soyad üzerine "e-imzalıdır" benzeri ibare konmaz. | m.17  |
| Ek, dağıtım, paraf | **Ek:** imzadan sonra solda; tek ekse "Ek:" yanına, birden çoksa altına numaralı; çok ekte eklerin sağ üstüne "EK-1"; gönderilmeyen ek için "Ek konulmadı". **Dağıtım:** birden çok muhatapta, ekten (yoksa imzadan) sonra solda; "Gereği:" ve "Bilgi:" kısımları; uzunsa "DAĞITIM LİSTESİ". **Paraf:** tarih, unvan, ad-soyad kısaltmasız, ast-üst sırasıyla; e-imzalı belgede üstveride tutulur, muhataba gitmez. | m.18, m.19, m.21  |

## Makam oluru — ek kurallar (m.20)

- Olur belgesi ilgili birim yöneticisince **güvenli e-imza ile teklif edilir**, olur makamınca e-imzayla imzalanır; zorunlu/olağanüstü hâlde el yazısı imza. 
- İmza bölümünden sonra uygun boşluk bırakılarak yazı alanının **ortasına büyük harflerle "OLUR"**; altına ad (ilk harf büyük) SOYAD, bir alt satıra unvan, ortalı. E-imzalı olurda **olur makamının imza tarihi belge tarihidir**. 
- Teklif eden birim ile olur makamı arasında başka makamlar varsa olura katılabilir: teklif edenin imzası ile "OLUR" arasında, yazı alanının **solunda** "Uygun görüşle arz ederim." ve altında ad SOYAD, unvan. 
- Eski YAML'daki "makam hitabı 'MAKAMINA' şeklinde biter (ör. BAKANLIK MAKAMINA)" ifadesi m.20'de yoktur; muhatap satırı m.14'e göre yazılır. Uygulamada "… MAKAMINA" kullanımı yaygındır `[doğrula — Yönetmelik Örnek 17]`. Metnin "… olurlarınıza arz ederim." diye bitmesi m.16/12 arz kuralının uygulamasıdır.

---

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `institution_header` | Başlık: idare ve birim adı (DETSİS'teki gibi)? Taşra teşkilatı mı? |
| `document_number` | Sayı: DETSİS no ve standart dosya planı kodu? (kayıt numarası EBYS'den gelir; bilinmiyorsa `[___]`) |
| `document_date` | Tarih? (e-imzalı belgede imza tarihi) |
| `document_subject` | Konu? |
| `recipient` / `authority_title` | Muhatap kim? Hiyerarşide üst mü, aynı düzey mi, alt mı? Dağıtımlı mı? |
| `references` | İlgi yazılar (tarih ve sayı)? |
| `body_text` | Yazının amacı, dayanağı ve ne istendiği? (olurda: teklif edilen işlem, gerekçe, dayanak madde) |
| `closing_statement` | (Hiyerarşiden otomatik seçilir — m.16/12) |
| `signer_info` / `proposing_official` | İmzalayan / teklif eden: ad, soyad, unvan; yetki devri ya da vekâlet var mı? |
| `intermediate_approval` | (Olur) Uygun görüş verecek ara makamlar? |
| `approval_authority` | (Olur) Olur verecek makam: ad, soyad, unvan? |
| `attachments` / `distribution` | Ekler ve dağıtım (gereği / bilgi)? |

## soorgla çağrıları

```
legal_get_statute_article  law_no: "2646"  law_type: "21"  article_no: "10" | "11" | "12" | "13" | "14" | "15" | "16" | "17" | "18" | "19" | "20"
legal_get_statute_article  law_no: "<olurun dayanağı: 657 | 4734 | 5018 | …>"  article_no: "<ilgili madde>"
legal_search_official_gazette  query: "Resmî Yazışmalarda Uygulanacak Usul ve Esaslar Hakkında Yönetmelikte Değişiklik"  search_in: "title"  sort_by: "date_desc"
```

---

## Belge iskeleti — resmî yazı

```markdown
                                   T.C.
                         [İDARENİN ADI]
                         [Birimin Adı]

Sayı : E-[DETSİS]-[SDP kodu]-[kayıt no]                               [gg.aa.yyyy]
Konu : [___]

                              [MUHATAP İDARE ADINA]
                                  ([Birim Adı])

İlgi : a) [tarih] tarihli ve [sayı] sayılı yazı.

      [Metin — 1,25 cm girinti, iki yana yaslı; amaç, dayanak, istenen]

      Bilgilerinize [arz / rica / arz ve rica] ederim.

                                                              [Ad SOYAD]
                                                              [Unvan]
Ek : [___]
Dağıtım:
Gereği:              Bilgi:
[___]                [___]
```

## Belge iskeleti — makam oluru

```markdown
                                   T.C.
                         [İDARENİN ADI]
                         [Birimin Adı]

Sayı : E-[___]                                                        [gg.aa.yyyy]
Konu : [___]

                              [OLUR MAKAMININ ADI — ör. VALİLİK MAKAMINA]

      [Gerekçe ve dayanak: … sayılı Kanunun … maddesi uyarınca …]

      Makamlarınızca da uygun görülmesi hâlinde olurlarınıza arz ederim.

                                                              [Ad SOYAD]
                                                              [Teklif eden unvan]
Uygun görüşle arz ederim.
[Ad SOYAD]
[Ara makam unvanı]

                                   OLUR
                                [Ad SOYAD]
                                 [Unvan]
Ek: [___]
```

## Sık hatalar

- 🟠 Aynı düzey makama "rica ederim" yazmak (kural: üst ve **aynı düzey** → arz).
- 🟠 Yetki devriyle imzada imzalayanın kendi hiyerarşisine göre arz/rica seçmek (kural: yetkiyi devredenin).
- 🟡 Sayı alanını standart dosya planı kodu olmadan yazmak; kayıt numarası uydurmak.
- 🟡 İkiden fazla imzada sıralamayı ters yapmak.

---

