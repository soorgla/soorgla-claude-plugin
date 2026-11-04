---
name: kamu-personeli
description: >
  657 sayılı Kanun'a tabi memurlar ve sözleşmeli kamu personeli için disiplin,
  soruşturma izni, görevden uzaklaştırma, atama ve tayin, sözleşme feshi ve
  yersiz ödeme sorunlarını ele alır; memur ya da avukat tarafı ile idare
  (disiplin amiri, muhakkik, personel birimi) tarafı için ayrı akış sunar.
  İşçi statüsündeki kamu çalışanı için değil (is-hukuku), memur statüsü için.
  Kullanıcı "disiplin cezası aldım", "savunma istendi", "soruşturmacı
  atandım", "tayinim çıktı" dediğinde kullan.
argument-hint: "[olayı anlatın ya da belgeyi ekleyin: savunma istem yazısı, ceza kararı, atama onayı, görevden uzaklaştırma oluru, soruşturma izni kararı, kişi borcu yazısı]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu becerideki iş akışı fikirleri anthropics/claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC)
deposundaki employment-legal eklentisinin internal-investigation (kaynak kapsama listesi, kamu işvereninde
ifade alma güvencesi, emsal karşılaştırması) ve termination-review (sonuç doğuran işlem öncesi kontrol)
becerilerinden Türk kamu personeli hukukuna (657 DMK, 4483, 2577 İYUK) uyarlanmış ve değiştirilmiştir.
ABD'ye özgü privilege, Garrity ve Weingarten kuralları alınmamıştır. Ayrıntı: NOTICE.md.
-->

# /kamu-personeli

657 sayılı Devlet Memurları Kanunu (DMK) ve bağlantılı mevzuat (4483, 4688, 6245, 7315, 375 KHK, 7075) için birleşik beceri. Ayrıntılı kontrol listeleri `references/` altındadır; her soru tipinde yalnızca ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta belirt.

---

## Ne zaman kullanılır

- 657 Devlet Memurları Kanunu: disiplin soruşturması, savunma istem yazısı
- Disiplin cezaları: uyarma, kınama, aylıktan kesme, kademe ilerlemesinin durdurulması, devlet memurluğundan çıkarma
- Disiplin zamanaşımı (m.127), disiplin kuruluna itiraz, görevden uzaklaştırma
- 4483 soruşturma izni ve ön inceleme
- Aday memur, asalet, kademe ve derece ilerlemesi
- Naklen atama, muvafakat, aile birliği, il dışı tayin
- 4/B ve 4/C sözleşmeli personel fesih, 4688 sendika güvencesi
- Harcırah, yersiz ödeme ve kişi borcu, OHAL Komisyonu ve KHK ihraç
- Tipik cümleler: "görevden uzaklaştırıldım", "soruşturma izni verildi", "muvafakat vermiyorlar", "sözleşmem feshedildi"
- Devir: işçi statüsündeki kamu çalışanı → is-hukuku; dava dilekçesi → idare-davalari-imar

## Kapsam

**Kapsar:** memur disiplin hukuku (soruşturma, savunma, ceza, itiraz, zamanaşımı, sicilden silme), görevden uzaklaştırma, memur yargılaması (4483 ön inceleme ve soruşturma izni), atama ve özlük (adaylık, asalet, kademe/derece, naklen atama, muvafakat, aile birliği ve sağlık mazereti, güvenlik soruşturması, izinler), sözleşmeli personel (657 m.4/B, 4/C) ve fesih, kamu görevlileri sendika güvencesi (4688 m.18), mali haklar ve harcırah, yersiz ödeme ve kişi borcu, OHAL Komisyonu ve KHK ihraç kalıntıları, personel işlemlerine karşı dava yolu ve süreler.

**İki taraf, iki akış.** Her referans dosyası iki yönü ayrı yazar:
- **Memur / avukat tarafı:** işlem hukuka uygun mu, hangi süre işliyor, itiraz mı dava mı.
- **İdare / kamu görevlisi tarafı** (disiplin amiri, muhakkik, personel daire başkanlığı, mutemet): işlemi iptale dayanıklı nasıl kurarım, hangi süreyi kaçırmamalıyım, hangi yazıyı nasıl yazarım. Eski sistemdeki `bureaucrat/personnel_hr/*` görevleri bu akışa çevrildi; persona ayrı beceri değildir.

**Kapsamaz ya da yönlendirir:**
- Kamu kurumunda **işçi** statüsünde çalışan (4857, kadrolu işçi, eski taşeron geçişi) → `../is-hukuku/SKILL.md`. Statü belirsizse önce bunu çöz: atama işlemi ve kadro mı, iş sözleşmesi mi? `[incele]`.
- İdari dava dilekçesinin metni (iptal ve tam yargı, yürütmenin durdurulması talebi) → `../idare-davalari-imar/SKILL.md` ve `../idare-davalari-imar/references/idari-dava-dilekcesi.md`. Bu beceri esas değerlendirmesini ve süre tablosunu yapar, dilekçeyi devreder (ORTAK-KURALLAR.md §14).
- İdare mahkemesi kararına istinaf ve temyiz → `../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`.
- Disiplin amirinin "olur" yazısı, savunma istem yazısı ve soruşturma raporunun resmî yazı biçimi → `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` (içerik ve kontrol listesi bu beceride).
- Sayıştay sorgusu ve ilamına karşı savunma ve temyiz metni → `../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`; yersiz ödeme, kamu zararı, harcama yetkilisi sorumluluğunun esası → `../kamu-mali-denetim-sayistay/SKILL.md`.
- Memurun suç isnadıyla yargılanması (zimmet, irtikâp, görevi kötüye kullanma) ve soruşturma iznine itiraz dışındaki ceza muhakemesi → esas `../ceza-hukuku-suclar/SKILL.md`, dilekçe `../ceza-ve-infaz-dilekce/SKILL.md`.
- Emeklilik, hizmet birleştirme, 5434/5510 aylık bağlanması → `../sosyal-guvenlik-sgk/SKILL.md`.
- Memurun kişisel verisi (özlük dosyası erişimi, kamera ve e-posta denetimi) → `../kvkk/SKILL.md`.
- Avukatsız memurun bilgi edinme ya da CİMER başvurusu → `../vatandas-basvurulari/SKILL.md`.
- Olağan yollar tükendikten sonra AYM bireysel başvuru → `../aym-aihm-basvuru/SKILL.md`.
- Özel personel rejimleri: hâkim ve savcılar (2802, HSK), TSK mensupları, öğretim üyeleri (2547), emniyet (3201, 7068 Genel Kolluk Disiplin) — çerçeve bu beceriden, özel kanun hükmü ayrıca çekilir ve `[incele]` işaretlenir. 657 m.125 ve m.126 "özel kanun hükümleri saklıdır" der. 

---

## İş akışı

### Adım 0 — MCP ön kontrolü ve profil
`legal_get_statute_article` (`law_no: "657"`, `article_no: "127"`, `law_type: "Kanun"`) çağır. Yanıt gelirse `soorgla ✓`. Bu çağrı 7573 sonrası metnin geldiğini de gösterir ("Değişik fıkra: 23/1/2026 - 7573/3 md." notunu gör). 

**Aynı numaralı kanunlar:** `law_no: "657"` 1925 tarihli Harita Genel Müdürlüğü kanunuyla, `law_no: "4483"` 1943 tarihli İzmir Tramvay kanunuyla numara paylaşıyor. `legal_get_statute_article` (`law_type: "Kanun"`) varsayılan olarak yeni kaydı (DMK `statute_id 40344`, 4483 `statute_id 39868`) doğru başlık ve bağlantıyla döndürür; diğer kayıt `other_candidates`'ta gelir, gerekirse `legal_get_statute_article_by_id` ile alınır. `legal_list_statute_articles` yalnız `law_no` ile "ambiguous" döner; `statute_id` ver. 

Profili oku: rol (avukat / değil), taraf (memur / idare), kurum türü (bakanlık, belediye, üniversite, emniyet).

### Adım 1 — Soru tipini ve tarafı belirle

| Soru tipi | İpucu sözcükler | Oku |
|---|---|---|
| A. Disiplin soruşturması ve cezası (savunma, ceza, itiraz, zamanaşımı, sicilden silme) | disiplin cezası, savunma istendi, soruşturmacı atandım, muhakkik, kınama, aylıktan kesme, kademe durdurma, ihraç, disiplin kurulu, itiraz | `references/disiplin-sorusturmasi-ve-cezalar.md` |
| B. Görevden uzaklaştırma ve memur yargılaması | görevden uzaklaştırıldım, açığa alındım, soruşturma izni, ön inceleme, 4483, işleme koymama, suç duyurusu | `references/gorevden-uzaklastirma-ve-4483.md` |
| C. Atama, nakil ve özlük | tayin, il dışı atama, naklen atama, muvafakat, aile birliği, sağlık mazereti, aday memur, asalet, kademe, derece, güvenlik soruşturması, izin, görevde yükselme | `references/atama-nakil-ve-ozluk.md` |
| D. Sözleşmeli personel ve sendika | 4/B, 4/C, sözleşmeli, sözleşme feshi, yenilenmedi, sendika temsilcisi, yer değişikliği | `references/sozlesmeli-personel-ve-sendika.md` |
| E. Mali haklar, harcırah, yersiz ödeme | maaş farkı, ek gösterge, harcırah, yolluk, geçici görev, kişi borcu, yersiz ödeme, geri istendi, Sayıştay | `references/mali-haklar-harcirah-ve-kamu-zarari.md` |
| F. OHAL / KHK ihraç kalıntıları | KHK ile ihraç, OHAL Komisyonu, göreve iade, pasaport | `references/ohal-khk-ve-iade.md` |
| G. Dava yolu, süreler, yürütmenin durdurulması (her tipte son adım) | dava açmak istiyorum, süre kaçtı mı, idare mahkemesi, istinaf | `references/personel-davasi-usul-ve-sureler.md` |

Bir olay birden fazla tipe giriyorsa hepsini oku (ör. görevden uzaklaştırma sonrası ihraç: B + A + G; disiplin cezası nedeniyle kademe ilerlemesi yapılmadı: A + C).

**Tarafı sor** (profilde yoksa): "Siz işlemin muhatabı memur musunuz (ya da onun avukatı), yoksa işlemi yapan idare adına mı çalışıyorsunuz (disiplin amiri, muhakkik, personel birimi)?" Taraf yanlış belirlenirse tavsiye tersine döner.

**Statüyü kontrol et:** memur (657 m.4/A), sözleşmeli (4/B), geçici personel (4/C — KHK-696 ile mülga, eski kayıtlar için geçiş hükümlerini çek), işçi (4/D → is-hukuku), özel kanuna tabi (hâkim, asker, polis, akademisyen).  Statü yanlışsa süreler ve yargı yolu tümden değişir.

**Ad-hoc doktrin sorusu** (ör. "uyarma cezasına dava açılır mı?") geldiyse görüşme akışını atla: maddeyi çek, kısa cevap ver, etiketle.

### Adım 2 — Süreleri en başta çek

Kamu personeli işlerinde en sık kayıp **süre** kaynaklıdır: disiplin amirinin bir aylık soruşturma başlatma süresi, memurun yedi günlük itiraz süresi, 60 günlük dava süresi, 4483'te on günlük itiraz. Her referans dosyasında süre tablosu vardır; her satırın dayanağını çek.

- `legal_calculate_deadline` İYUK sürelerini hesaplar: `iyuk_lawsuit` (dava açma), `iyuk_implicit_rejection_application` / `iyuk_implicit_rejection_waiting` (m.10 zımni ret), `iyuk_appeal`, `iyuk_cassation`, `aym_individual_application`. 657 süreleri (7 gün itiraz, 127 zamanaşımı) ve 4483'ün 10 günlük itirazı için kod yok: elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]`. 
- Süre geçmişse ya da 7 günden az kaldıysa çıktının en üstüne 🔴.
- **İdare tarafında** zamanaşımı süreleri idarenin yetkisini düşürür (657 m.127): olayı öğrenme tarihini ve fiil tarihini ilk satıra yaz.

### Adım 3 — soorgla'dan kaynak çek

Eski `search_profile` tanımlarının karşılığı aşağıdaki çağrılardır. Her referans dosyasında konuya özel çağrılar ayrıca yazılıdır.

**Mevzuat:**
- 657 → `legal_get_statute_article` (`law_no: "657"`, `law_type: "Kanun"`); aynı numaralı kayıt için Adım 0 notu.
- 4483 → `legal_get_statute_article` (`law_no: "4483"`, `law_type: "Kanun"`); konu araması için `legal_search_statute_semantic` (`mevzuat_no: "4483"`).
- 2577 İYUK → `legal_get_statute_article` (`law_no: "2577"`). Madde tarihçesi 2015'te kalıyor; **m.10 ve m.11'deki otuz günlük süreler 7331 ile (RG 14.07.2021) altmış günden indirildi**, tarihçe aracı bunu göstermiyor. 
- Devlet Memurları Disiplin Yönetmeliği → soorgla numarası `3935`; maddeler başlıkla bölütlenmiş (`m.Savunma`), numarayla değil. `legal_search_statute_semantic` (`sorgu: "Devlet Memurları Disiplin Yönetmeliği <konu>"`) ile çek. 
- Bağlantılı: 2709 Anayasa m.129, 4688, 6245 Harcırah, 7315 Güvenlik Soruşturması, 375 KHK, 5018 m.71, 7075 OHAL Komisyonu, Sözleşmeli Personel Çalıştırılmasına İlişkin Esaslar (`715754`).

**Kararlar** — `legal_search_cases`:
- Personel davaları → `mahkeme: "danistay"` ve `mahkeme: "bam"`. **Daireyi sabitleme.** Eski YAML'lar "disiplin = 12. Daire, polis/öğretmen = 2. Daire" diyordu; 2023-2025 tarihli 657 disiplin ve atama kararlarının büyük bölümü **2. Daire**'den, sözleşmeli personel fesih kararları **12. Daire**'den ve İDDK'dan geliyor. Güncel iş bölümünü kararın künyesinden ve `legal_search_cases` sonuçlarından oku; `legal_case_facets` bu alanda işe yaramıyor (sorgudaki herhangi bir sözcükle eşleşen bütün kararları sayıyor).  **2026 iş bölümü (Danıştay Başkanlık Kurulu 2026/6, RG 25.02.2026):** disiplin cezaları, görevden uzaklaştırma, adaylık işlemleri, kamu görevlilerinin göreve alınması, kademe/derece/intibak ve parasal hakları, sözleşme yenilememe/feshi (2. ve 5. Daire görevleri dışında kalanlar), 4/C ve 4/D, kamu görevlileri emekliliği, izin, harcırah ve kamu konutları **12. Daire**'de; kamu görevlileri mevzuatından doğan ve 5. ile 12. Dairenin görevleri dışında kalan işler ile öğretime ilişkin işlemler ve aile hekimliği önceki sayfada başlayan bir dairede (OCR'da başlık ve ilk sayfa eksik; bağlamdan 2. Daire). Bu nedenle 2023-2025 kararlarındaki "disiplin = 2. Daire" dağılımı 2026 sonrası dosyalara taşınmaz; dava tarihine göre daireyi kararın künyesinden doğrula. 
- **Veri kapsamı:** araçta 2026 tarihli Danıştay kararı çok az (bu alandaki sorguda 17); en güncel emsal genellikle 2024-2025'tir. Bunu **Okunan** satırına yaz. 
- Sayıştay (yersiz ödeme, harcırah) → `mahkeme: "sayistay"`; 2023-2024 kararları var. 
- AYM (savunma hakkı, özel hayat, ifade özgürlüğü nedeniyle disiplin) → `mahkeme: "anayasa"`.
- **Zorunlu adım:** her analizde son 3 yıldan en az bir kararın tam metnini `legal_get_case_document` ile oku ve alıntı-önerme kontrolünü yap (ORTAK-KURALLAR.md §7). Karşı oy ile çoğunluk gerekçesini karıştırma.

**İdari görüşler:** `legal_search_admin_guidance` (`kurum: "Devlet Personel Başkanlığı"`, `belge_tur: "gorus"`) — DPB görüşleri (~750, **2018 öncesi arşiv**) artık derlemde. Görüşler 2018 öncesi mevzuata göredir (7573 gibi sonraki değişiklikler yok); her görüşü güncel madde metniyle karşılaştır ve "2018 öncesi görüş" diye etiketle. Cumhurbaşkanlığı İnsan Kaynakları Ofisi görüşleri yok; gerekiyorsa kullanıcıdan iste ya da `[web araması — doğrulayın]`. 

**Sayısal parametreler** — beceri metnine hiçbir tutar, katsayı, gösterge, gündelik ya da parasal sınır yazılmaz:
- Memur maaş katsayıları, gündelik tutarları, ek gösterge tabloları → kullanıcıdan (bordro, bütçe kanunu cetveli) ya da `legal_search_statute_semantic` (`yalniz_tablolar: true`); `[doğrula]`. `legal_get_social_parameters` memur katsayılarını döndürmüyor. 
- İdare mahkemesinde tek hâkimle görülen davaların parasal sınırı ve istinaf/temyiz sınırları → 2576 m.7 ve 2577 m.45-46 metninden çek (7589 ile değişti). 
- Kişi borcunda faiz → 6183 ya da 5018 m.71 metninden; `legal_get_legal_interest_rates` 7589 sonrası yanlış oran verebilir `[incele]`.

### Adım 4 — Analiz
İlgili referans dosyasındaki kontrol listesini sırayla yürüt. Her maddeyi ✅ / 🔴 / 🟠 / 🟡 / `[incele]` ile işaretle. Liste tabandır.

İdari işlem denetiminde beş unsur (yetki, şekil, sebep, konu, maksat) iskeleti kullanılır; her bulguyu bir unsura bağla. Eski `lawyer/administrative_tax/annulment_research.yaml`'daki bu çerçeve `idare-davalari-imar`'ın da ortak dilidir.

**Emsal karşılaştırması (upstream internal-investigation'dan):** aynı kurumda benzer fiile verilen cezalar (eşitlik ve ölçülülük) idare tarafında ceza tayininden önce, memur tarafında dava gerekçesinde sorulur.

**Orantılılık:** "Uyarma cezasına itiraz süresi kaç gün?" üç cümle ister; tam disiplin dosyası incelemesi değil.

### Adım 5 — Çıktı

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

## [Konu]: [memur / idare tarafı] — [tarih]

### Sonuç (tek paragraf)
[İşlem hukuka uygun görünüyor / şu noktada sakat / süre kaçmış — tek cümle neden]

### Kritik süreler
| Süre | Başlangıç | Son gün | Dayanak | Durum |

### Bulgular (yetki · şekil · sebep · konu · maksat)
[her madde: işaret + kısa açıklama + atıf etiketi]

### Emsal
[en az bir son 3 yıl kararı, tam metin okundu; alıntı-önerme kontrolü]

### Eksik bilgi
[açık sorular]

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 6 — "Taslaktır" kapısı
Avukat olmayan kullanıcı şunları yapmadan önce ORTAK-KURALLAR.md §1 kapısını uygula: disiplin kuruluna itiraz dilekçesi vermek, savunmayı göndermek, dava açmak, 4483 kararına itiraz etmek, sözleşme feshine karşı yazı göndermek, kişi borcunu kabul eden taahhüt imzalamak.

**İdare tarafında** kapı: ceza vermek, görevden uzaklaştırmak, ilişik kesmek, kişi borcu çıkarmak. Bu işlemler iptal ve tam yargı (ve amir hakkında 657 m.139 sorumluluğu) riski taşır; avukat ya da hukuk müşaviri onayı olmadan "uygulanabilir" deme.

**Memur tarafında savunma metni** dışa gider: taslak başlığı ve iç notlar savunma metninin içinde olmaz; iç değerlendirme ayrı belgede kalır. Savunma metninde suç teşkil edebilecek bir kabul varsa (ceza soruşturması paralel yürüyorsa) 🔴 ve `[incele]` — disiplin savunmasındaki beyan ceza dosyasına girebilir. Anayasa m.38 kimsenin kendini suçlamaya zorlanamayacağını söyler; savunma vermemek disiplin hukukunda yalnız "savunma hakkından vazgeçme" sonucunu doğurur (657 m.130).  

### Adım 7 — Dilekçe ve dış metin devri

| İstenen belge | Beceri |
|---|---|
| Disiplin kuruluna / yüksek disiplin kuruluna itiraz dilekçesi, savunma metni | Bu beceride iskelet (`references/disiplin-sorusturmasi-ve-cezalar.md`); avukatsız memur için sade üslup `../vatandas-basvurulari/SKILL.md` kurallarıyla |
| Savunma istem yazısı, soruşturmacı görevlendirme oluru, soruşturma raporu, görevden uzaklaştırma oluru (idare tarafı) | İçerik bu beceride; resmî yazı biçimi `../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` |
| 4483 soruşturma izni kararına itiraz dilekçesi | Bu beceride iskelet (`references/gorevden-uzaklastirma-ve-4483.md`) — idari dava değil, kesin karar verilen özel itiraz |
| İdare mahkemesinde iptal ve tam yargı davası (disiplin cezası, atama, fesih, kişi borcu, görevden uzaklaştırma) | `../idare-davalari-imar/references/idari-dava-dilekcesi.md` |
| İdare mahkemesi kararına istinaf/temyiz | `../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md` |
| Sayıştay sorgusuna cevap, ilama karşı temyiz | `../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md` |
| İdareye İYUK m.10 başvurusu (özlük hakkı talebi) | Bu beceride kısa iskelet (`references/personel-davasi-usul-ve-sureler.md`); resmî yazı biçimi `../idari-ve-kurum-basvurulari/SKILL.md` |
| AYM bireysel başvuru | `../aym-aihm-basvuru/SKILL.md` |

Devrederken taşı: statü ve kurum, taraf, işlem tarihi ve tebliğ tarihi, süre tablosu, çekilmiş madde ve karar künyeleri (etiketleriyle), beş unsur bulguları, yürütmenin durdurulması gerekçesi (telafisi güç zarar + açık hukuka aykırılık), istem önerisi, açık sorular.

---

## İş akışı becerilerine bağlantı

Esas değerlendirme bu beceride kalır; aşağıdakiler kaydeder, düzenler ya da hesaplar (ORTAK-KURALLAR.md §14 sonundaki tablo ve §15).

- **Süreyi kaydet:** savunma, itiraz ve dava süreleri hesaplanınca "Bu süreleri süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md).

## Bu beceri ne yapmaz

- Bir disiplin cezasının "kesin iptal edilir" olduğunu söylemez; güçlü ve zayıf iddiaları ayırır.
- Memur maaşını, harcırahı ya da kişi borcunu katsayı ve gündelik tutarı uydurarak hesaplamaz; formülü ve kullanıcıdan alınacak girdileri gösterir.
- Danıştay daire iş bölümünü metinden söylemez; karardan ve güncel iş bölümü kararından çeker.
- İdare adına ceza vermez, soruşturma izni kararı imzalamaz, UYAP'a dosya yüklemez.

---

