# Harcama öncesi kamu zararı ön kontrolü — idare / kamu görevlisi tarafı

## Ne zaman kullanılır
- Harcama yetkilisi, gerçekleştirme görevlisi, muhasebe yetkilisi, strateji geliştirme / mali hizmetler birimi ya da ödemeyi onaylayacak kurul üyesi, bir ödemeyi **yapmadan veya imzalamadan önce** "bu Sayıştay'a takılır mı, kamu zararı doğurur mu?" diye soruyor.
- Konu: temsil-ağırlama-tören, yolluk ve harcırah, personele ek ödeme/ikramiye/yardım, sosyal yardım ve bağış, kira ve taşınmaz tahsisi, avans ve kredi, doğrudan temin, hizmet alımı, dernek-vakıf-birliklere aktarım, belediye meclis kararına dayalı ödemeler.
- Yapım işi, hakediş, fiyat farkı, iş artışı ise → `../../hakedis/references/sayistay-denetim-riski.md` (bulgu kodları orada). İhale usulü seçimi → `../../kamu-ihale/SKILL.md`.

**Sınır:** bu dosya **ön kontrol** yapar. Sorgu gelmişse → `sayistay-denetim-sureci-ve-sorgu.md`; kamu zararı tespit edilmişse → `kamu-zarari-tahsili-ve-idari-tespit.md`.

---

## 1. Dakikalık triyaj (upstream `is-this-a-problem` uyarlaması)

Önce tek cümlelik karar, sonra gerekçe:

| Sonuç | Ne zaman | Ne yazılır |
|---|---|---|
| ✅ **İmzalanabilir** | Ödemenin açık bir kanun/CBK/yönetmelik dayanağı var, belge zinciri tam, tutar sözleşme/onay ile uyumlu, Sayıştay emsalinde aynı tip ödeme tazmine konu edilmemiş | "Dayanak: [madde]. Belge zinciri tam. İmzalanabilir." + `[incele]` notu: "araç kapsamı 2024'te bitiyor" |
| ⚠️ **Şu tamamlanmadan imzalama** | Dayanak var ama belge eksik (onay, tutanak, muayene-kabul, fatura, görevlendirme oluru), tutar hesabı doğrulanmamış ya da yetki devri belirsiz | Eksik belge listesi + kim tamamlayacak |
| 🛑 **Dur** | Mevzuatta öngörülmemiş ödeme, iş/mal/hizmet alınmadan ödeme, kişiye özel/görevle ilgisiz harcama, ödenek yokluğu ya da tasarruf tedbirine açık aykırılık; aynı tip ödemede tazmin hükmü emsali | Gerekçe + "hukuk müşavirliği / mali hizmetler görüşü alın" |

Emin değilsen yukarı yuvarla (ORTAK-KURALLAR.md §8): ⚠️ ile 🛑 arasında kalırsan 🛑.

### Tuzak soruları (görünüşte basit ama değil)

| Soru şöyle geliyor | Neden basit olmayabilir | Sor |
|---|---|---|
| "Meclis/encümen/yönetim kurulu karar aldı, öderiz" | Kurul kararı mevzuatta dayanağı olmayan ödemeyi hukuka uygun kılmaz; ayrıca kanun/CBK yetkisiyle kurul kararıyla yapılan harcamalarda harcama yetkisinden doğan sorumluluk kurula aittir (5018 m.31/3) | "Kararın dayandığı kanun maddesi hangisi? Kurul bu harcamaya kanunen yetkili mi?" |
| "Herkes böyle ödüyor, geçen yıl da ödedik" | Önceki yılların denetlenmemiş olması dayanak değildir; zamanaşımı 10 yıl (5018 m.74) | "Bu ödeme daha önce Sayıştay raporuna girdi mi? Sorgu geldi mi?" |
| "Fuar/tanıtım için gönderdik, şehir içi taksi de ödensin" | Harcırah Kanunu belirli nakil masraflarını sayar; şehir içi görev mahallindeki taksi ücreti sayılmamış → tazmin | "Görev mahallinde hangi masraf hangi madde ile ödeniyor?" |
| "Personel bilfiil çalıştı ama ataması sınavsızdı" | Mevzuata aykırı atama her durumda kamu zararı doğurmaz; görev fiilen yapılmışsa Temyiz Kurulu tazmini kaldırabilmiştir — ama bu takdire bağlı | "Görev fiilen yapıldı mı? Karşılığında ödenen kalem ne?" `[incele]` |
| "Tasarruf genelgesine aykırı ama ödenek var" | Ödenek varlığı yetmez; tasarruf tedbirlerine aykırılık 7521 ile disiplin sonucuna bağlandı (5018 ek m.9) ve harcamanın niteliğine göre kamu zararı da doğabilir | "Hangi genelge, hangi madde? İstisna onayı alındı mı?" |
| "Belediye başkanının temsil gideri" | Temsil giderleri "görev ile ilgili olma şartı" ile ve yönergeye göre yapılabilir | "Harcama kimin, hangi temsil faaliyeti için? Belge?" |

Dayanaklar:
- 5018 m.31/3: kanun/CBK yetkisine dayanarak kurul, komite, komisyon kararıyla yapılan harcamalarda harcama yetkisinden doğan sorumluluk kurula aittir. 
- 5018 m.74: kamu zararı ve para cezaları, fiilin işlendiği yılı izleyen mali yıl başından itibaren onuncu yılın sonunda zamanaşımına uğrar (kesen/durduran genel hükümler saklı). 
- Şehir içi taksi: Sayıştay Temyiz Kurulu, karar düzeltme aşamasında, yurt içi geçici görevde şehir içi taksi ücretlerinin belediye bütçesinden ödenmesinde tazmin hükmünü yerinde gördü. `[soorgla]` 
- Sınavsız atama: Temyiz Kurulu, görevin fiilen yapıldığı sınavsız şube müdürü atamasında tazmin hükmünü kaldırdı. `[soorgla]` `[çekildi ama desteği doğrulayın]` (gerekçenin "GEREĞİ GÖRÜŞÜLDÜ" kısmı metinde kesildi; hüküm fıkrası okundu) 
- Tasarruf tedbirleri: 7521 ile 5018'e eklenen ek m.9'a göre tasarruf tedbirlerine aykırı iş ve işlemleri tespit edilenlere disiplin hükümleri uygulanır ve sonuç Cumhurbaşkanlığına bildirilir.  Güncel genelge: Tasarruf Tedbirleri ile İlgili 2024/7 sayılı Cumhurbaşkanlığı Genelgesi (RG 17.05.2024, 32549).  2026/10 sayılı Cumhurbaşkanlığı Genelgesi (2027-2029 Kamu Yatırım Programı hazırlıkları, RG 12.09.2026) de dayanak olarak hâlâ 2024/7'yi anar. Çalışma anında yeni genelge çıkıp çıkmadığını kontrol et: `legal_search_official_gazette` `query: "Tasarruf"`, `search_in: "title"`, `date_from: 2024-05-18`, `sort_by: "date_desc"`; ayrıca `search_in: "all"` ile "tasarruf tedbirleri genelgesi" ara. 
- Temsil giderleri: belediye temsil-ağırlama yönergesinde "görev ile ilgili olma şartı". `[soorgla]` `[çekildi ama desteği doğrulayın]`  Yönerge, İçişleri Bakanlığının 25.04.1984 tarihli ve 27302 sayılı onayıyla yürürlüğe konuldu (Sayıştay kararındaki aktarım); RG'de yayımlanmadığından soorgla'da tam metni yok. Güncel metni idareden ya da İçişleri Bakanlığından temin et; Sayıştay'ın m.3'teki başkan takdirini "mahalli müşterek ihtiyaçlar ekseninde" sınırladığını gözet. 

---

## 2. Ön kontrol kontrol listesi

| # | Kontrol | Dayanak | İşaret |
|---|---|---|---|
| 1 | **Harcama talimatı** var mı; hizmet gerekçesi, işin konusu ve tutarı, süresi, kullanılabilir ödenek, gerçekleştirme usulü ve görevliler yazılı mı? | 5018 m.32/1  | |
| 2 | **Ödenek** var mı, doğru tertipten mi; yüklenmeye girişilen tutar saklı tutuldu mu? Bütçede yeterli ödenek olmayan iş için yüklenmeye girişilemez | 5018 m.26  | |
| 3 | **Dayanak mevzuat**: ödeme kanunda/CBK'da/yönetmelikte öngörülmüş mü? Öngörülmeyen ödeme başlı başına kamu zararı hâlidir | 5018 m.71/2-g | |
| 4 | **Gerçekleştirme**: iş/mal/hizmet usulüne uygun alındı mı, görevli kişi/komisyon onayladı mı, gerçekleştirme belgeleri düzenlendi mi? | 5018 m.33/1-2  | |
| 5 | **Tutar**: sözleşme, karar, onaydaki tutarı aşıyor mu; rayiç bedelin üstünde mi? | 5018 m.71/2-a, d | |
| 6 | **Ön mali kontrol**: mali hizmetler biriminin ön mali kontrolüne tabi işlemse görüş alındı mı? | 5018 m.58  | |
| 7 | **Muhasebe yetkilisi kontrolü**: yetkili imzalar, mevzuattaki belgelerin tamlığı, maddi hata, hak sahibinin kimliği | 5018 m.61/3  | |
| 8 | **Tasarruf tedbirleri**: güncel genelgenin kalemine giriyor mu, istisna onayı gerekli mi? | 5018 ek m.9; 2024/7 Genelge | |
| 9 | **Ödenek üstü / program dışı**: ayrıntılı harcama programı, serbest bırakma oranı ya da ödenek gönderme belgesi aşılıyor mu? (kamu zararı olmasa da para cezası) | 5018 m.70  | |
| 10 | **Yetki**: harcama yetkisi devredildiyse devir usulüne uygun mu (devir, devredenin idari sorumluluğunu kaldırmaz) | 5018 m.31/5  | |
| 11 | **Sayıştay emsali**: aynı tip ödeme için tazmin ya da beraat kararı var mı (idare türüyle)? | `legal_search_cases` `mahkeme: "sayistay"` | |
| 12 | **İBK**: konu Sayıştay İçtihadı Birleştirme Kararına bağlanmış mı? (bağlayıcı) | 6085 m.58/3 | |

**Muhasebe yetkilisi için not:** muhasebe yetkilisi ilgili mevzuatta düzenlenmiş belgeler dışında belge arayamaz; belgesi eksik/hatalı ödeme emri belgesini en geç bir iş günü içinde gerekçesiyle harcama yetkilisine yazılı olarak geri gönderir; sorumluluğu incelemesi gereken belgelerle sınırlıdır.  Bu nedenle "muhasebe yetkilisi de imzaladı, sorun yok" savunması harcama yetkilisini korumaz.

---

## 3. Görüşme soruları (eski `expenditure_check` persona ve filtrelerinden)

| Alan | Soru |
|---|---|
| İdare türü | Belediye ve bağlı idare mi, üniversite mi, genel/özel bütçeli mi, SGK mı, özel idare mi? (Sayıştay karar künyesi bu sınıflandırmayı kullanıyor; sorgu cümlesine kat) |
| Sıfat | Sizin işlemdeki sıfatınız: harcama yetkilisi, gerçekleştirme görevlisi, muhasebe yetkilisi, kurul üyesi, mutemet? |
| Harcama | Ne ödenecek, kime, ne kadar, hangi tertipten? Harcama talimatı var mı? |
| Dayanak | Hangi kanun/CBK/yönetmelik/kurul kararı? Kararın dayandığı yetki maddesi? |
| Belgeler | Fatura, tutanak, muayene-kabul, görevlendirme oluru, sözleşme, piyasa araştırması? |
| Geçmiş | Aynı ödeme önceki yıllarda yapıldı mı; Sayıştay raporunda bulgu ya da sorgu oldu mu? |
| Tasarruf | Genelge kapsamında mı, istisna onayı var mı? |

---

## 4. MCP adımları

```
legal_get_statute_article  law_no: "5018"  law_type: "Kanun"  article_no: "31" | "32" | "33" | "58" | "61" | "70" | "71"
legal_list_statute_articles  law_no: "5018"  law_type: "Kanun"  article_kind: "ek"  article_no: "9"  include_content: true
legal_get_statute_article  law_no: "<işlemin dayanağı: 6245 | 657 | 5393 | 2547 | 4734 …>"  article_no: "<madde>"
legal_search_official_gazette  search_in: "title"  query: "Tasarruf Tedbirleri"  sort_by: "date_desc"
legal_search_cases  mahkeme: "sayistay"  sorgu: "<idare türü + harcama + aykırılık; ör. belediye personelinin geçici görevde şehir içi taksi ücretinin bütçeden ödenmesi kamu zararı>"  tarih_baslangic: "2022-01-01"
legal_get_case_document  belge_id: "<seçilen; daire ilamı mı Temyiz Kurulu kararı mı ayır>"
legal_search_admin_guidance  kurum: "Sayıştay Genel Kurulu"  sorgu: "<konu>"     # yalnız 2006/2011/2013 İBK'ları
```

---

## 5. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Kaynaklar: "Sayıştay kararları araçta 2024 sonuna kadar")

## Ön kontrol — [harcama] — [idare türü] — [sıfat]

**Karar:** ✅ İmzalanabilir | ⚠️ Şu tamamlanmadan imzalama: […] | 🛑 Dur: […]
**Bir cümle neden:** […]

### Kontrol listesi
| # | Kontrol | Sonuç | Atıf |

### Emsal
[Sayıştay karar künyesi — daire ilamı / Temyiz Kurulu — tazmin / kaldırma — neyi destekliyor]

### Eksik belge ve sorumlusu
| Belge | Kim tamamlar | Ne zamana |

**Şimdi ne yapalım?** 1. Eksik belge yazısını hazırla 2. Hukuk müşavirliği görüş talebi 3. Mali hizmetler ön mali kontrol talebi 4. Bekle 5. Başka
```

---

## 6. Sık hatalar
- "Ödenek var" demeyi "dayanak var" sanmak.
- Kurul kararını kanuni dayanak yerine koymak.
- Muhasebe yetkilisinin imzasını harcama yetkilisi için güvence saymak.
- Araçtaki Sayıştay sonuçlarını güncel sanmak (2025+ yok) ve Başsavcılık mütalaasını karar gibi aktarmak.
- Tasarruf tedbirine aykırılığı yalnız "kamu zararı" olarak değerlendirip 7521 sonrası disiplin sonucunu atlamak.

