# soorgla araç rehberi ve atıf biçimi

Bu rehber, alan becerisi olmayan konularda araştırma yaparken araçların nasıl davrandığını anlatır. Satırların hepsi 2026-10-31'de gerçek çağrılarla denendi. Deneme konusu hasta hakları ve aydınlatılmış onamdı; bu alanın kendi becerisi yok.

Araç adları çıplak yazılır. Bağlayıcıya göre önek alabilirler (ör. `mcp__…__legal_search_cases`).

---

## 1. Mevzuat

**Kaydı çözme ve numara çakışması.** Mevzuat numarası tekil değildir. 1960 sonrası yönetmelik ve kurum mevzuatı numaraları kanun numaralarıyla çakışır.

- `legal_resolve_statute` (`query: "Hasta Hakları Yönetmeliği"`) tek aday döndürdü: `statute_id 43984`, `law_no 4847`. 
- Aynı numarayla `legal_get_statute_article_history` (`law_no: "4847"`, `article_no: "25"`) `ambiguous: true` döndürdü. Adaylar 4847 sayılı Avrupa Birliği Uyum Komisyonu Kanunu ve Hasta Hakları Yönetmeliğiydi. 
- `legal_get_statute_article` (`law_no: "4847"`, `article_no: "25"`, `law_type` verilmeden) Kanunu seçti, `count: 0` döndü ve yönetmeliği `other_candidates` içinde (`statute_id 43984`) gösterdi. Doğru kayıt için `legal_get_statute_article_by_id` (`statute_id`, `article_no`) kullan. 

**Kural:** Önce `legal_resolve_statute` çağır. Sonraki her çağrıda `statute_id` ver (madde için `legal_get_statute_article_by_id`); aracın `statute_id` almadığı yerde `law_type` ver ve yanıttaki `other_candidates`'a bak. Dönen `title` alanını her seferinde beklenen mevzuatla karşılaştır. Aynı madde iki kez dönerse tekilleştir.

**Madde metni.** `legal_get_statute_article` kanunda düzgün çalışıyor. Ör. `law_no: "1219"`, `article_no: "70"`, `law_type: "Kanun"` çağrısı maddeyi "(Değişik: 23/1/2008-5728/38 md.)" ve "(Ek cümleler: 21/7/2025-7557/3 md.)" notlarıyla birlikte döndürdü.  Harfli maddeler (ör. Hasta Hakları Yönetmeliği m.42/A) yapı taslağında görünür. `legal_get_statute_article_by_id` (`statute_id: 43984`, `article_no: "42/A"`) harfli maddeyi tam metinle döndürdü; boş dönerse `legal_list_statute_articles` (`article_no`, `include_content: true`) kullan. 

**Yapı.** `legal_get_statute_outline` (`statute_id`) bölüm başlıklarını ve madde aralıklarını verir. Başta "article_no 0 / section" diye boş bir kayıt gelebilir; yok say. 

**Konuya göre arama.** `legal_search_statute_semantic` kavram sorgusunda iyi sonuç verir: "hastanın tedaviyi reddetme hakkı ve aydınlatılmış onam" sorgusunda ilk dört sonuç Hasta Hakları Yönetmeliği m.25, 11, 12 ve 24'tü. Yanıttaki `ilgili_mevzuatlar` listesi hangi mevzuatların ağırlıklı olduğunu gösterir; liste yalnızca numara verir, numarayı `legal_resolve_statute` ile çöz. Beşinci sonuç `ustveri_eksik: true` işaretli ilgisiz bir RG kaydıydı; **bu tür sonuç atıf olarak kullanılmaz.** 

**Sözcük araması.** `legal_search_statute` ("aydınlatılmış onam") üniversite yönetmelikleri ve Bitki Karantinası Yönetmeliği gibi ilgisiz sonuçlar döndürdü. Bu aracı yalnızca `law_no` ile daraltılmış birebir ifade araması için kullan. 

**Güncellik ve tarihçe.**
- `legal_list_statute_versions` hem Hasta Hakları Yönetmeliği (`statute_id 43984`) hem 1219 sayılı Kanun için **0 sürüm** döndürdü. Oysa yönetmelik 2014, 2016 ve 2019'da değişmiş, 1219 m.70 ise 2025'te 7557 ile değişmiştir. 
- Geçici yol: Madde metnindeki "(Değişik/Ek/Mülga: tarih-kanun/madde)" notlarına bak. Ayrıca `legal_search_official_gazette` (`query: "<ad> Değişiklik"`, `search_in: "title"`, `sort_by: "date_desc"`) ile ara. Bu arama yönetmelik için üç değişiklik yönetmeliği buldu (16.01.2019, 23.12.2016, 08.05.2014). 
- Sürüm kaydı olmadığı için `legal_compare_statute_versions` bu konuda denenemedi. Sürüm kaydı olan kanunlarda (ör. 4857) diğer becerilerde kullanılıyor.
- **Mülga madde:** Mülga madde "(Mülga: tarih-kanun/madde)" metniyle, `status: "mulga_veya_iptal"` ve `warnings` uyarısıyla döner; `status` alanını her zaman oku. Çok yeni bir değişiklik (son birkaç hafta) henüz işlenmemiş olabilir; sonuç kritikse RG'den teyit et. 

---

## 2. Kararlar

**Arama.** `legal_search_cases` olay cümlesiyle iyi çalışır.
- "hastanın aydınlatılmış onamı alınmadan yapılan ameliyat nedeniyle hekimin sorumluluğu" (`mahkeme: "yargitay"`, `tarih_baslangic: "2023-01-01"`) sorgusu 3. HD ve 11. HD kararlarını döndürdü. 
- `daire: "Hukuk Genel Kurulu"` filtresi çalışıyor; HGK 2018/849 E., 2020/592 E. ve 2017/680 E. döndü. 
- Danıştay araması (`mahkeme: "danistay"`) 10. Daire ve İDDK kararlarını döndürdü. 

**Tam metin.** `legal_get_case_document` (`belge_id`) kararın tamamını verir. Metin `azami_karakter` sınırında kesilirse yanıtta `kesildi: true` gelir. Gerekçenin ve hüküm fıkrasının tamamı gerekiyorsa sınırı yükselt. Hüküm fıkrası metnin sonundadır; kesik metinden sonuç yazma. 

**Numara ile bulma.**
- `legal_get_case_by_number` esas ve karar numarasını **birlikte** ister. `daire` parametresi almaz. Dönen dairenin beklenen daire olduğunu kontrol et. 
- Yalnızca esas numarası varsa `legal_list_cases_by_number` kullan. "2024/1848" sorgusu Yargıtay ve Danıştay'ın farklı dairelerinden **29 karar** döndürdü; `daire` ve `mahkeme` ile daralt. 
- Boş sonuç, kararın var olmadığını göstermez; bazı kayıtlarda numara alanları boştur.

**Anayasa Mahkemesi.** `mahkeme: "anayasa"` ile bireysel başvuru kararları geliyor. Aynı karar iki kayıtla dönebiliyor: `aym_bb:…` ve `anayasa-bireysel-basvuru-…`. Künye aynıysa birini kullan. Bazı kayıtlarda atıf yalnızca "Anayasa Mahkemesi İkinci Bölüm, 23.02.2022" biçimindedir, başvuru numarası eksiktir; numarayı diğer kayıttan ya da metinden tamamla. 

**AİHM.**
- `mahkeme: "aihm"` ile çalışıyor, ama `atif` alanı çoğu zaman yalnızca "AİHM Kararı" ya da "E. 9389/19, K. 001-245086, 03.06.2025" oluyor. Bazı kayıtlarda `karar_tarihi` boş.
- Başvuru adını `baslik` alanından al ("CASE OF UYGUN v. TÜRKİYE").
- Türkçe sorgu da sonuç veriyor. `…-turkishtranslation` kimlikli kayıtlar Türkçe çeviridir. Çeviriler Adalet Bakanlığı ya da AYM kaynaklıdır ve **gayriresmîdir**; bunu belirt `[model bilgisi — doğrulayın]`.
- İngilizce sorguda başka devletler aleyhine verilmiş ilke kararları da gelir. Bunlar Türkiye'yi doğrudan bağlamaz, Sözleşme yorumunu gösterir. 

**Dağılım.** `legal_case_facets` sorgu sözcüklerinden **herhangi biriyle** eşleşen bütün kararları sayar. "aydınlatılmış onam hekim sorumluluğu tazminat" sorgusunda ilk daireler 2. HD, 9. HD ve 4. HD çıktı; bu sonuç anlamsızdır. Daire tespiti için kullanma. 

**Toplam sayılar.** `legal_search_cases` yanıtındaki `toplam_karar` (ör. 640.541) yaklaşık ve geniş eşleşmeye dayalıdır. "Bu konuda yüzlerce karar var" ya da "yerleşik içtihat" demek için bu sayıyı kullanma.

---

## 3. İçtihadı birleştirme kararları

- `legal_search_cases` (`daire: "İçtihatları Birleştirme Büyük Genel Kurulu"`) **0 sonuç** döndürdü. Filtresiz aramada ise İBK'lar yalnızca başka kararların içinde anılıyordu. 
- Geçici yol: `legal_search_official_gazette` (`query: "İçtihadı Birleştirme"`, `search_in: "title"`, `sort_by: "date_desc"`). Bu arama 36 sonuç verdi; ilki Yargıtay İBBGK 08.05.2026, E.2021/8, K.2026/1 (RG 30.06.2026) idi. Konuya göre daraltmak için sorguya konu sözcüğü ekle ya da `search_in: "all"` ile ara. 
- RG'deki İBK metni çoğunlukla PDF'tir (`.pdf` adres). `legal_get_official_gazette_document` ile oku. OCR hataları olabilir.

---

## 4. Resmî Gazete

- `search_in: "title"` belirli bir yönetmelik ya da kararı bulmada isabetlidir. Sonuçta `id` gelmeyebilir ve `number` boş olabilir. Tam metni `legal_get_official_gazette_document` aracına **`url`** vererek al; yanıt `id`'yi ve RG sayısını metin içinde verir (ör. "Sayı : 30657"). 
- Uzun metin 50.000 karakterde kesilir. `offset` ile parça parça oku.
- Torba kanunlar başlık aramasında kaçabilir. Değişiklik arıyorsan `search_in: "all"` ile de dene.

---

## 5. İdari görüş ve kurul kararları

- `legal_search_admin_guidance` aracında `kurum` filtresi tam adla çalışır. Ör. `kurum: "Kişisel Verileri Koruma Kurulu"` ile "hasta verilerinin işlenmesi ve hastanelerde kişisel veri ihlali" sorgusu 791 parça arasından hastane veri ihlali karar özetlerini döndürdü (2021/407, 2020/63, 2022/923). 
- Çalışan kurum adları: Rekabet Kurulu, Gelir İdaresi Başkanlığı (özelgeler çoğunlukla "<il> Vergi Dairesi Başkanlığı" ya da "<il> Defterdarlığı" adıyla), Reklam Kurulu, Bankacılık Düzenleme ve Denetleme Kurulu, Kişisel Verileri Koruma Kurulu.
- Kapsamda olmayanlar: SGK genelgeleri, KİK ilke kararları, Tüketici Hakem Heyeti, imar ve personel görüşleri, Sağlık Bakanlığı genelgeleri. Bulunamazsa §5 "sessiz tamamlama yok" kuralını uygula.
- Yanıtta `not: "İdari belgelerdir; mahkeme içtihadı yerine geçmez."` gelir. Notta da ağırlığı ayrı belirt.

---

## 6. Türk atıf biçimi

**Öncelik:** Araç hazır atıf döndürüyorsa (`kaynak.markdown`, `kaynak.atif`, `markdown_citation`) **onu aynen kullan** (ORTAK-KURALLAR.md §4). Aşağıdaki kalıplar, aracın atfı eksik olduğunda (AİHM, bazı AYM kayıtları) ya da kullanıcı dilekçe içi biçim istediğinde kullanılır. Kalıplar `[model bilgisi — doğrulayın]` niteliğinde bir yazım önerisidir; resmî bir atıf standardı değildir.

| Kaynak | Kalıp |
|---|---|
| Kanun maddesi | `[No] s. [Kısa ad] m.[madde]/[fıkra]` → 6098 s. TBK m.506/2 |
| Yönetmelik | `[Ad] m.[madde]` (RG [gg.aa.yyyy], S. [sayı]) |
| Yargıtay / BAM | `Yargıtay [Daire], E. [yyyy/n], K. [yyyy/n], T. [gg.aa.yyyy]` → Yargıtay 3. HD, E. 2024/1848, K. 2025/836, T. 13.02.2025 |
| Yargıtay kurulu | `Yargıtay HGK, E. …, K. …, T. …` |
| İçtihadı birleştirme | `Yargıtay İBBGK, E. …, K. …, T. … (RG gg.aa.yyyy, S. …)` |
| Danıştay | `Danıştay [n]. D., E. …, K. …, T. …` / `Danıştay İDDK, E. …, K. …, T. …` |
| AYM bireysel başvuru | `AYM, [Başvurucu adı], B. No: [yyyy/n], T. [gg.aa.yyyy]` |
| AYM norm denetimi | `AYM, E. …, K. …, T. … (RG gg.aa.yyyy, S. …)` |
| AİHM | `AİHM, [Başvurucu] / Türkiye, B. No: [n/yy], T. [gg.aa.yyyy]` |
| Kurul kararı | `[Kurul], [tarih] t., [no] s. Karar (Özeti)` |
| Resmî Gazete | `RG [gg.aa.yyyy], S. [sayı]` (mükerrerse "Mük.") |

Kişisel veri: Karar metinlerinde taraf adları çoğunlukla "..." ile anonimleştirilmiştir; notta da ad yazma. AYM ve AİHM başvurucu adları kararın resmî adıdır ve yazılabilir.
