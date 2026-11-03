# İflas ve konkordato

**Ne zaman kullanılır:**
- Borçlu şirket (ya da tacir) borçlarını ödeyemiyor: konkordato mu, iflas mı, borca batıklık bildirimi mi?
- Alacaklı: iflas yoluyla takip, doğrudan iflas, konkordatoya itiraz, oylama, tasdike karşı kanun yolu.
- İflas tasfiyesinde alacak kaydı, kayıt kabul/terkin davası, sıra cetveli.

Bu beceri mali analizi yapmaz: borca batıklık bilançosu, konkordato ön projesinin finansal fizibilitesi ve bağımsız denetim raporu uzman işidir. Beceri hukuki şartları, belge listesini ve süreleri kontrol eder.

**Önemli eskime:** eski YAML "iflas erteleme yerine geçen konkordato" diyordu. İflasın ertelenmesi 7101 sayılı Kanunla (kabul 28.2.2018) kaldırıldı; yürürlük tarihinde görülmekte olan iflasın ertelenmesi ve konkordato taleplerine talep tarihindeki hükümler uygulanmaya devam eder (İİK geçici m.14). 7101'in RG tarihi bu taramada doğrulanamadı; tarih kritikse `legal_search_official_gazette` ile 7101'i ara, bulamazsan `[ARAŞTIRMA GEREKLİ: 7101 RG/yürürlük tarihi]` yaz. İİK m.179 artık sermaye şirketleri ve kooperatiflerin **borca batıklık** hâlinde doğrudan iflasını düzenler.

---

## Süre tablosu

| Süre | Başlangıç | Dayanak |
|---|---|---|
| İflas yoluyla takipte ödeme emrine itiraz ve ödeme: **7 gün** | Ödeme emrinin tebliği | İİK m.155 |
| İflas isteme hakkı: **1 yıl** | Ödeme emrinin tebliği | İİK m.156 son fıkra |
| Borçlunun kendi iflas talebine alacaklı itirazı: **15 gün** | Talebin ilanı | İİK m.178/2 |
| Geçici mühlete alacaklı itirazı: **7 gün kesin süre** | Geçici mühlet kararının ilanı | İİK m.288/2 |
| Geçici mühlet **3 ay**, uzatma en fazla **2 ay** (toplam 5 ay) | Karar | İİK m.287/4 |
| Kesin mühlet **1 yıl**, güçlük hâlinde **6 aya kadar** uzatma | Kesin mühlet kararı (geçici mühlet içinde verilir) | İİK m.289/1, 3, 5 |
| Kesin mühlette karar verilemezse mühlet hükümlerinin devamı: en fazla **6 ay** | — | İİK m.304/2 |
| Tasdik duruşmasına itiraz sebeplerini bildirme: duruşmadan en az **3 gün** önce | Duruşma günü | İİK m.304/1 |
| Alacaklılar toplantısından sonra iltihak: **7 gün**; komiser raporu: iltihak süresinden itibaren **7 gün** | Toplantı | İİK m.302 son fıkralar |
| Çekişmeli alacak davası: **1 ay** | Tasdik kararının ilanı | İİK m.308/b |
| İflasta sıra cetveline itiraz davası: **15 gün** (yalnız sıraya ise icra mahkemesine şikâyet) | Cetvelin ilanı | İİK m.235 |
| Konkordato hakkındaki karara istinaf **2 hafta**; BAM kararına temyiz **2 hafta** | Borçlu ve konkordato talep eden alacaklı için kararın tebliği; itiraz eden diğer alacaklılar için tasdik kararının ilanı | İİK m.308/a |

---

## İflas kontrol listesi

1. **İflasa tabi mi?** TTK'ya göre tacir sayılanlar ya da tacir hükümlerine tabi olanlar ve özel kanunla iflasa tabi kılınanlar; alacaklı bunlara haciz yoluyla da gidebilir ve seçtiği yolu bir kez harçsız değiştirebilir (m.43).
2. **Yol:**
   - **Takipli iflas** (m.155-156): ödeme emrine 7 gün içinde itiraz yoksa alacaklı ticaret mahkemesinden iflas ister; itiraz varsa itirazın kaldırılmasıyla birlikte iflas ister. Depo emri: itiraz yoksa ya da itiraz yerinde görülmezse mahkeme borçluya **7 gün** içinde borcu faiz ve masraflarla ödemesini ya da mahkeme veznesine depo etmesini emreder; ödemezse ilk oturumda iflas kararı verilir. Diğer alacaklılar iflas talebinin ilanından itibaren 15 gün içinde davaya katılıp itiraz edebilir (m.158).
   - **Doğrudan iflas, alacaklının talebiyle** (m.177): belirli yerleşim yeri yok, kaçma, hileli işlem, mal saklama; ödemelerin tatili; m.308 hâli; ilamlı alacağın icra emrine rağmen ödenmemesi.
   - **Borçlunun kendi talebi** (m.178): aciz bildirimi ve aktif-pasif mal beyanı şart; yarı mevcudunu haczettiren takip sonrası iflas isteme mecburiyeti.
   - **Borca batıklık** (m.179): sermaye şirketi ve kooperatifte muhtemel satış fiyatlarıyla ara bilanço; yönetim organı, tasfiye memuru ya da alacaklı beyanı; TTK m.376-377 ve 634 saklı. TTK m.376/3: borca batıklık şüphesinde yönetim kurulu işletmenin devamlılığına ve muhtemel satış fiyatlarına göre ara bilanço çıkarır; aktifler yetmiyorsa asliye ticaret mahkemesine bildirip iflas ister (alacaklıların sıra sonrasına geçme beyanı istisnası saklı). Sorumluluk sonuçları `[incele]`.
3. **Görevli mahkeme:** asliye ticaret. Harç: `legal_get_social_parameters` (`tur: "harc_iflas_konkordato"`).
4. **İflas masasına kayıt, alacaklılar toplantıları, sıra cetveli** (m.206 imtiyaz sırası, m.235 kayıt kabul ve terkin davası masaya ya da alacaklıya karşı).
5. **Suç işareti:** hileli ve taksirli iflas (TCK m.161-162) → yalnız işaret.

## Konkordato kontrol listesi

### Talep (borçlu ya da alacaklı)
1. **Şart:** borçlarını vadesinde ödeyemeyen **ya da ödeyememe tehlikesi altında** bulunan herhangi bir borçlu (iflasa tabi olmayan da). İflas talep edebilecek her alacaklı da borçlu hakkında konkordato işlemlerinin başlatılmasını isteyebilir.
2. **Yetkili ve görevli mahkeme:** iflasa tabi borçluda m.154'teki yer, değilse yerleşim yeri **asliye ticaret** mahkemesi; konkordato gider avansı tarifeden.
3. **Ek belgeler (m.286):** ön proje; malvarlığı belgeleri (son bilanço, gelir ve nakit akım tabloları, hem işletmenin devamlılığı esasına göre hem muhtemel satış fiyatlarıyla ara bilançolar, defter tasdikleri, e-defter beratları, duran varlık listeleri, alacak-borç listesi); alacaklı listesi ve imtiyaz durumu; **iflas karşılaştırma tablosu**; KGK yetkili bağımsız denetim kuruluşunun **makul güvence raporu**. Eksik belgeyle geçici mühlet verilmez.

### Mühlet ve sonuçları
4. **Geçici mühlet** derhâl, belgeler eksiksizse; geçici komiser (gerekirse üç, biri bağımsız denetçi); bu kararlara kanun yolu kapalı. Geçici mühlet kesin mühletin sonuçlarını doğurur.
5. **Mühletin alacaklılara etkisi (m.294):** 6183 takipleri dahil yeni takip yapılamaz, başlamış takipler durur, ihtiyati tedbir ve haciz uygulanmaz, takip işlemiyle kesilebilen zamanaşımı ve hak düşürücü süreler işlemez. m.206 birinci sıradaki imtiyazlı alacaklar için haciz yoluyla takip yapılabilir. Proje aksini öngörmedikçe kesin mühletten itibaren **rehinsiz alacaklara faiz durur**. Takas m.200-201'e tabi (geçici mühlet ilanı esas). Mühletten önce yapılan, mühletten sonra doğan müstakbel alacak temliki hükümsüz. Rehinli alacaklı mühlette rehnin paraya çevrilmesi takibini başlatabilir ya da sürdürebilir ama muhafaza tedbiri alınamaz, satış yapılamaz (istisna: projede kullanılmayacak, değeri düşecek ya da muhafazası masraflı rehinli mal için mahkeme izniyle satış) (m.295). İşletme için önemli sözleşmeler konkordato talebi gerekçesiyle feshedilemez (m.296). Borçlu komiser nezaretinde işine devam eder; mahkeme izni olmadan rehin kuramaz, kefil olamaz, ivazsız tasarruf yapamaz, taşınmazını ve önemli taşınırlarını devredemez, aksi işlemler hükümsüzdür (m.297).
6. **Alacaklılar kurulu:** en fazla 7, tek sayılı, ücretsiz; zorunlu hâller yönetmelikte.

### Oylama ve tasdik
7. **Kabul çoğunluğu (m.302):** (a) kaydedilmiş alacaklıların **ve** alacakların yarısını, **ya da** (b) alacaklıların dörtte birini **ve** alacakların üçte ikisini **aşan** çoğunluk. Yalnız projeden etkilenen alacaklılar oy kullanır; m.206 birinci sıra imtiyazlılar ile borçlunun eşi, çocuğu, kendisinin ve eşinin ana, baba ve kardeşleri hesaba katılmaz; rehinli alacak teminatsız kalan kısmıyla katılır. "Yarısı" eşitlik değil, **aşma** ister: 4 alacaklıdan 2'si yetmez.
8. **Tasdik şartları (m.305):** (a) iflas karşılaştırması — teklif, iflasta eline geçecek muhtemel miktardan fazla; (b) teklif borçlunun kaynaklarıyla orantılı; (c) m.302 çoğunluğu; (d) birinci sıra imtiyazlılar ve mühlet içinde komiser izniyle doğan borçlar için yeterli teminat; (e) yargılama giderleri ve harcın tasdikten önce depo edilmesi. Mahkeme projeyi yetersiz bulursa düzeltme isteyebilir.
9. **Tasdik kararının içeriği:** alacaklıların hangi ölçüde vazgeçtiği ve ödeme takvimi hüküm fıkrasında açıkça yazılmalı; yazılmazsa karar infaza elverişsiz ve bozma sebebi.
10. **Vekilin kanun yolundan feragati** özel yetki ister; vekâletnamede yoksa feragat nedeniyle ret hatalı.
11. **Tasdik edilmezse:** talep reddedilir, ilan edilir; borçlu iflasa tabi ve doğrudan iflas sebebi varsa **re'sen iflas**; tasfiye basit ya da adi usulle, gerekirse komiserlerce.
12. **Görevli daire:** konkordato, iflas, iflas sıra cetveli ve kayıt kabul/terkin → **Yargıtay 6. HD**; sermaye şirketlerinin uzlaşma yoluyla yeniden yapılandırılması da 6. HD. İflas yoluyla takipte icra mahkemesi şikâyetleri 12. HD.

---

## Görüşme soruları

### Borçlu tarafı
1. Şirket türü, sermaye, faaliyet, çalışan sayısı?
2. Toplam borç ve dağılımı: rehinli, imtiyazlı (işçi, kamu), adi; en büyük 10 alacaklı?
3. Vadesi geçmiş borçlar ve başlamış takipler (6183 dahil)?
4. Son bilanço ve ara bilançolar hazır mı? Bağımsız denetim kuruluşuyla çalışıldı mı?
5. Teklif: tenzilat oranı, vade, ödeme kaynağı (faaliyet nakdi, varlık satışı, sermaye artırımı)?
6. Borca batık mı? (TTK m.376 bildirim yükümlülüğü)
7. Grup şirketleri ya da kefil ortaklar için ayrı konkordato gerekir mi?

### Alacaklı tarafı
1. Alacak türü ve teminatı (rehin, kefalet, çek/senet)?
2. Geçici mühlet ilanı ne zaman yapıldı? (7 günlük itiraz)
3. Komiser alacak kaydında alacağı tam yazdı mı? Çekişmeli mi?
4. Oylama tarihi; kabul ya da ret kararı?
5. Projede faiz, tenzilat ve vade alacaklıyı iflastan daha kötü duruma sokuyor mu?

## soorgla çağrıları

```
legal_get_statute_article law_no: "2004" article_no: "155" | "156" | "158" | "177" | "178" | "179" | "206" | "235"
legal_get_statute_article law_no: "2004" article_no: "285" | "286" | "287" | "288" | "289" | "294" | "295" | "296" | "297" | "302" | "304" | "305" | "306" | "308" | "308/b" | "308/c"
legal_get_statute_article law_no: "6102" article_no: "376" | "377"
legal_get_social_parameters tur: "harc_iflas_konkordato"
legal_search_cases mahkeme: "yargitay" daire: "6. Hukuk Dairesi" tarih_baslangic: <son 3 yıl>
    sorgu: "<ör. konkordato tasdikinde iflas karşılaştırma tablosu ve teklifin kaynaklarla orantılı olması>"
legal_search_cases mahkeme: "bam" sorgu: "<ör. geçici mühlete alacaklı itirazı, eksik belge>"
legal_search_official_gazette query: "konkordato" document_type: "yönetmelik" # Konkordato Komiserliği Yönetmeliği değişiklikleri
```

## Çıktı iskeleti

```markdown
## [İflas / Konkordato] değerlendirmesi: [borçlu] — [mahkeme, esas no, tarih]
### Sonuç (hangi yol, tek cümle neden)
### Süreler ve aşama
| Aşama | Tarih | Süre/son gün | Dayanak | Durum |
### Şartlar (m.285-286 / m.177-179 / m.302 / m.305 — ✅/🔴/[incele])
### Alacaklı haritası (rehinli, imtiyazlı, adi; oy hesabı)
### Mühletin etkisi (takipler, faiz, takas, rehin)
### Mali analize bırakılanlar (bağımsız denetçi / bilirkişi)
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- "İflasın ertelenmesi" istemek (2018'de kaldırıldı).
- Konkordato talebini m.286 belgeleri ve bağımsız denetim raporu tamamlanmadan vermek → geçici mühlet verilmez.
- Oy hesabında "yarısı" eşiğini aşma yerine eşitlikle sağlamak; borçlunun yakınlarını ve birinci sıra imtiyazlıları hesaba katmak.
- Mühlet içinde rehinsiz alacağa faiz işletmeye devam etmek.
- Tasdik kararında vazgeçme oranı ve ödeme takvimini yazmamak.
- İflas sıra cetveli davasını 15 gün yerine 7 gün sanmak (7 gün icra sıra cetvelidir, m.142).
