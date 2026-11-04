# Ara ve kesin hakediş denetimi, hakedişe itiraz

## Ne zaman kullanılır
- Yüklenici ya da idare bir **geçici (ara) hakediş** ya da **kesin hakediş / kesin hesap** dosyasını kontrol etmek istiyor: kapak, icmal, yeşil defter (metraj cetveli), ataşman ve röleveler, pursantaj (götürü bedel), ihzarat, kesintiler.
- Yüklenici hakedişteki bir kaleme itiraz edecek ya da "ihtirazi kayıt koymadan imzaladık, şimdi isteyebilir miyiz?" diye soruyor.
- İdare hakedişi düzeltti, kesinti yaptı ya da ödemeyi geciktirdi.
- Fiyat farkı hesabı → ayrıca `fiyat-farki.md`; sözleşmede olmayan kalem ya da miktar aşımı → `is-artisi-ve-yeni-birim-fiyat.md`.

---

## 1. Uygulanan metni belirle (önce)

| Soru | Neden önemli |
|---|---|
| İhale ilan tarihi 1.9.2025'ten önce mi sonra mı? | Genel Şartname m.39 (hakediş ve itiraz) ve Tip Sözleşme m.11 (ödeme süreleri) 1.9.2025'te değişti; eski sözleşmeye eski metin uygulanır.  |
| Sözleşme türü: anahtar teslimi götürü bedel / birim fiyat / karma? | Götürü bedelde ödeme iş programı ve **ilerleme yüzdesi (pursantaj)** üzerinden, birim fiyatta **metraj × birim fiyat** üzerinden yapılır. Uygulama projesi olan yapım işi götürü bedelle, ön/kesin projeli iş birim fiyatla ihale edilir.  |
| Fiyat farkı öngörülmüş mü? | Fiyat farkı ve ek kesin teminat kesintisi hakedişe girer → `fiyat-farki.md`. |
| Avans verilmiş mi? | Avans mahsubu ve (fiyat farklı işlerde) mahsup edilmemiş avansın güncellenmesi. |

---

## 2. Kontrol listesi — geçici hakediş

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| DÜZENLEME | Geçici hakediş yüklenicinin başvurusu üzerine her ayın **ilk beş işgünü** içinde düzenlenir; yüklenici başvurmazsa idare aynı ay içinde tek taraflı düzenler; yıla sari olmayan işlerde son hakediş bütçe yılının son ayının 20'sinde | Genel Şartname m.39/4-a (1.9.2025 sonrası metin) |  |
| POZ-FİYAT | Hakedişteki poz numaraları ve birim fiyatlar sözleşme birim fiyat cetveliyle birebir aynı mı? | Sözleşme; 4735 m.4 | Sözleşmede olmayan poz → YBF tutanağı var mı (`is-artisi-ve-yeni-birim-fiyat.md`) |
| METRAJ | İcmaldeki miktarların dayanağı yeşil defter (ölçü: en × boy × yükseklik) ve ataşman/röleve mi? Kapanan imalat (temel altı, sıva altı, yalıtım) için imzalı ve tarihli ataşman var mı? | Genel Şartname m.39/1-c ("Metrajlar, yeşil defter ve eklerinde gösterilir"; bitmiş iş kısımlarında kesin metraj esas), m.28 (ataşman ve defterler; imzalayan yüklenici içeriği kabul etmiş olur, itirazını yazılı bildirir)  | Ölçüye dayanmayan miktar → "dayanaksız imalat" 🟠 |
| PURSANTAJ | Götürü bedelde ilerleme yüzdesi sahadaki fiziki gerçekleşmeyle ve iş programıyla uyumlu mu? | Sözleşme, iş programı | İdare tarafının en sık Sayıştay bulgusu |
| KÜMÜLATİF | Hakediş birikimli düzenlenir: bu hakediş = toplam yapılan iş − önceki hakediş toplamı. "Önceki hakediş" satırı bir önceki hakedişin toplamıyla kuruşu kuruşuna aynı mı? | Genel Şartname m.39 `[model bilgisi — doğrulayın]` | Fark → "kümülatif hesap hatası", mükerrer ödeme riski 🔴 |
| MİKTAR-AŞIMI | Birim fiyatlı bir kalemde sözleşme miktarı aşıldı mı? Aşıldıysa iş artışı oluru ve sınır hesabı var mı? | 4735 m.24 | Olur yoksa aşan kısım için ödeme riski → `is-artisi-ve-yeni-birim-fiyat.md` |
| İHZARAT | Şantiyedeki henüz kullanılmamış malzeme bedeli ödeniyorsa: ihzarat tutanağı, fiziki stok, şartnameye uygunluk, ihzarat bedelinin pozun birim fiyatını aşmaması | Genel Şartname, sözleşme `[model bilgisi — doğrulayın]` | Birim fiyatlı işlerde ihzar edilen malzemenin fiyat farkı ihzarat ayına göre hesaplanır (Sayıştay 2. D. K.48286, 06.04.2022 arama özetinde) `[çekildi ama desteği doğrulayın]` |
| AVANS | Avans mahsubu sözleşmedeki oranla yapılmış mı? Fiyat farklı işte mahsup edilmemiş avansın defaten kesilmesi ya da iadesi gerekiyorsa Pn ile güncellenmiş mi (Pn < 1 ise güncelleme yok)? | Tip Sözleşme m.13.11 (1.9.2025 sonrası ilanlar) |  |
| TEMİNAT-KESİNTİSİ | Götürü bedelde **geçici kabul noksanları**, birim fiyatta **kesin hesap** için her hakedişte yapılan iş tutarının %3'ü kadar teminat mektubu ya da kesinti; fiyat farklı işte tutar Pn ile güncellenir; bu teminatlar haczedilemez | Tip Sözleşme m.30 dipnot (1.9.2025 sonrası ilanlar) |  |
| EK-TEMİNAT | Fiyat farkı ödenen işte sözleşme bedelindeki artış tutarının %6'sı ek kesin teminat; hakedişten kesilerek de alınabilir | 4735 m.12 |  |
| GECİKME-CEZASI | İş programına göre gecikme varsa ceza hakedişten kesilmiş mi; kısmi gecikme cezası öngörülmüş mü? | 4735 m.20/a; sözleşme | Ayrıntı → `sure-uzatimi-ve-gecikme-cezasi.md` |
| NEFASET | Kabulde kusurlu görülen ama kabule engel olmayan iş için bedel indirimi (nefaset kesintisi) | Muayene ve Kabul Yönetmeliği; Genel Şartname `[model bilgisi — doğrulayın]` | Gerekçe ve tutanak şart |
| VERGİ-SGK | KDV tevkifatı, damga vergisi, SGK borç sorgusu ve ilişiksizlik | → `../../vergi/SKILL.md`, `../../sosyal-guvenlik-sgk/SKILL.md` | Tutar uydurma |
| ÖDEME-SÜRESİ | 1.9.2025 sonrası ilanlarda: hakediş yüklenicinin imzalayıp verdiği tarihten itibaren en geç **30 gün** içinde onaylanır, onayı izleyen en geç **30 gün** içinde tahakkuka bağlanır, tahakkuktan itibaren en geç **15 gün** (sözleşmede farklı süre yazılabilir) içinde ödenir | Tip Sözleşme m.11.2 |  Önceki sözleşmelerde sözleşmenin kendi maddesine bak |

### Kesin hakediş ve kesin hesap
- Birim fiyatlı işte kesin hesaplar işin devamı sırasında peyderpey hazırlanır; kesin hakedişte geçici hakediş rakamlarına değil **kesin metraja** itibar edilir.  
- Kesin hesapta idarece yapılan değişikliklere yüklenici, değişikliklerin kendisine **tebliğinden itibaren en geç 15 gün** içinde itiraz eder (1.9.2025 sonrası metin). 
- Kesin hakediş tutarı iş deneyim belgesinin de dayanağıdır → iş deneyim belgesi uyuşmazlığı `../../kamu-ihale/SKILL.md`.

---

## 3. Hakedişe itiraz ve "ihtirazi kayıt" — en önemli tuzak

**Eski metin (1.9.2025 öncesi ilanlar):** yüklenici geçici hakedişe itirazını dilekçeyle açıklar ve hakedişi "idareye verilen … tarihli dilekçemde yazılı ihtirazi kayıtla" diye imzalar; imzadan sonra tahakkuka kadar yapılan düzeltmelere ödeme tarihinden itibaren **10 gün** içinde itiraz eder; aksi hâlde hakedişi olduğu gibi kabul etmiş sayılır.

**Bu hüküm Danıştay'da iptal edildi.** İdari Dava Daireleri Kurulu, kuralın kanuni dayanağı olmadığını, 4735 m.4'teki taraf eşitliğini bozduğunu ve hak arama özgürlüğünü kısıtladığını belirterek ret kararını bozdu; Daire uyarak m.39/4-e'yi iptal etti. Hizmet İşleri Genel Şartnamesindeki benzer hüküm (m.42/a) de iptal edildi.  4735 m.4 metni: taraflar sözleşme hükümlerinin uygulanmasında eşit hak ve yükümlülüklere sahiptir; ihale dokümanı ve sözleşmede bu prensibe aykırı maddeye yer verilemez. 

**Yeni metin (1.9.2025 sonrası ilanlar):** yüklenici geçici hakedişe ya da hakediş imzalandıktan sonra tahakkuka kadar yapılan düzeltmelere itirazlarını **en geç kesin hesapların idareye teslim edildiği tarihe kadar** dilekçeyle bildirmek zorundadır. 

**Ama adli yargı farklı bakabilir.** Yargıtay 6. HD çoğunluğu 2025'te, ihtirazi kayıt konmadan imzalanan geçici hakedişlerdeki fiyat farkının sonradan istenemeyeceğine dair ilk derece ve BAM kararını **onadı**; karşı oy Danıştay iptalini, HMK m.193/2'yi (ispat hakkını imkânsızlaştıran delil sözleşmesi geçersiz) ve 4735 m.4'ü dayanak gösterdi.  Aynı yönde 2025 tarihli bir başka 6. HD kararı `sozlesme-incelemesi-tbk` becerisinde de çekildi (`../../sozlesme-incelemesi-tbk/references/eser-ve-insaat.md`, HAKEDİŞ-İTİRAZ satırı).

**Pratik kural (her iki taraf için):**
- **Yüklenici:** hangi metin uygulanırsa uygulansın, itiraz edilecek her kalem için hakedişi **gerekçeli dilekçe + ihtirazi kayıtla** imzala, dilekçenin alındı tarihini sakla. Eski sözleşmede 10 günlük süreyi kaçırdıysan Danıştay iptalini ve karşı oy gerekçesini kullan ama sonucu `[incele]` ve 🟠 olarak işaretle — Yargıtay çoğunluğu aleyhe.
- **İdare:** iptal edilmiş hükme dayanarak "itiraz etmediniz" diye talebi reddetmek dava riski taşır; aynı zamanda Genel Şartname kontrol teşkilatına eski hakedişleri düzeltme yetkisi tanır `[model bilgisi — doğrulayın]`, bu yetki eşitlik tartışmasında idare aleyhine kullanılabilir.

---

## 4. Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Geçici hakedişin düzenlenmesi: ayın ilk 5 işgünü | Yüklenicinin başvurusu | Genel Şartname m.39/4-a (1.9.2025 sonrası) |  |
| Hakediş onayı 30 gün → tahakkuk 30 gün → ödeme 15 gün | Hakedişin yüklenici tarafından imzalanıp verilmesi | Tip Sözleşme m.11.2 (1.9.2025 sonrası) | Sözleşme farklı ödeme süresi yazabilir  |
| Geçici hakedişe ve düzeltmelere itiraz: kesin hesapların idareye teslimine kadar | — | Genel Şartname m.39/4-e (1.9.2025 sonrası) | Eski metin: ödeme tarihinden itibaren 10 gün (Danıştay'ca iptal; Yargıtay çoğunluğu uyguluyor) `[incele]` |
| Kesin hesaptaki değişikliklere itiraz: 15 gün | Değişikliğin yükleniciye tebliği | Genel Şartname m.40/9 (1.9.2025 sonrası) |  |
| Yüksek Fen Kuruluna itiraz | Kesin kabul aşaması tamamlanıncaya kadar, idareye yazılı | 4735 ek m.2 | → `uyusmazlik-ve-yargi-yolu.md`  |

---

## 5. Görüşme soruları (eski YAML `vector_store` bağımlılığından)

| Alan | Soru |
|---|---|
| Belgeler | Bu hakedişin kapak, icmal, yeşil defter ve ataşmanları; bir önceki hakediş; sözleşme birim fiyat cetveli (ya da götürü bedelde iş programı ve ilerleme yüzdeleri tablosu) elinizde mi? |
| Tarihler | İhale ilan tarihi, sözleşme tarihi, yer teslimi, bu hakedişin dönemi, imza ve ödeme tarihleri? |
| Tür | Sözleşme türü? Fiyat farkı ve avans öngörülmüş mü? |
| İtiraz | Hangi kaleme itiraz ediyorsunuz? Daha önceki hakedişlerde ihtirazi kayıt ya da dilekçe verdiniz mi, tarihleri? |
| Değişiklik | İş artışı oluru, YBF tutanağı, revize proje ya da süre uzatımı kararı var mı? |
| Taraf (idare) | Kontrol teşkilatı ve yapı denetim görevlisinin imzaları tamam mı? Harcama yetkilisi kim? |

---

## 6. MCP adımları

```
legal_get_statute_article  law_no: "4735"  law_type: "Kanun"  article_no: "4" | "6" | "12" | "13" | "20" | "24" | "36"
legal_search_official_gazette  query: "Yapım İşleri İhaleleri Uygulama Yönetmeliğinde Değişiklik"  search_in: "title"  sort_by: "date_desc"
legal_get_official_gazette_document  url: "<sözleşmenin ilan tarihine en yakın değişiklik>"
legal_search_cases  mahkeme: "yargitay"  daire: "6. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "kamu ihale yapım işi geçici hakedişe ihtirazi kayıt konulmadan imzalanması sonradan hakediş alacağı istenmesi"
legal_search_cases  mahkeme: "danistay"  sorgu: "Yapım İşleri Genel Şartnamesi 39. madde geçici hakedişlere itiraz iptal"
legal_search_cases  mahkeme: "sayistay"  sorgu: "<ör. mükerrer metraj ödemesi kümülatif hakediş kamu zararı>"
legal_get_case_document  belge_id: "<seçilen>"
```

---

## 7. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …
## Hakediş denetimi — [işin adı] — [hakediş no / dönem] — [yüklenici / idare]
### Sonuç
[Hakediş tutarı doğru / hatalı — net fark: … TL [doğrula]]
### Uygulanan metin
| İlan tarihi | Sözleşme türü | Genel Şartname sürümü | Fiyat farkı | Avans |
### Bulgular
| # | Poz / kalem | Tespit | Dayanak | Mali etki | İşaret |
|---|---|---|---|---|---|
| 1 | 15.xxx | Yeşil defter 100 m², icmal 120 m² | Genel Şartname m.40 | +20 m² × … TL | 🟠 |
### Kümülatif kontrol
| Önceki hakediş toplamı (bu hakedişte) | Önceki hakedişin kendi toplamı | Fark |
### Kesintiler
| Avans | Gecikme cezası | Teminat kesintisi (%3) | Ek kesin teminat (%6) | Vergi/SGK | Nefaset |
### İtiraz durumu
[itiraz edilecek kalemler, süre, ihtirazi kayıt metni önerisi]
### Aksiyon
[icmal revize edilmeli / tutanak eklenmeli / itiraz dilekçesi → idari-ve-kurum-basvurulari]
```

**İhtirazi kayıt metni önerisi (yüklenici için, hakediş imza bloğuna):**
> "İdareye verilen [tarih] tarihli ve [sayı] sayılı dilekçemde yazılı ihtirazi kayıtla."

Dilekçenin kendisi → `../../idari-ve-kurum-basvurulari/SKILL.md`.

---

## 8. Sık hatalar
- Hakedişi itirazsız imzalayıp alacağı kesin hesapta ya da davada istemek (Yargıtay çoğunluğu reddediyor).
- 1.9.2025 sonrası metni eski sözleşmeye (ya da tersini) uygulamak.
- Götürü bedelde metraj tartışmasına girmek; esas olan iş programı ve ilerleme yüzdesidir (proje dışı iş hariç).
- Kümülatif "önceki hakediş" satırını kontrol etmemek (mükerrer ödeme).
- İhzaratı fiziki stok tutanağı olmadan ödemek.
- Mahsup edilmemiş avansın fiyat farklı işte güncellenmesini atlamak.
- Kontrol teşkilatının eski hakedişlerde yaptığı düzeltmeleri hiç sorgulamamak.

