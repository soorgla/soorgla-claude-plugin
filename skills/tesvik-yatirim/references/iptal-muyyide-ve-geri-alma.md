# Belge iptali, kısmi müeyyide, desteklerin geri alınması ve dava yolu

## Ne zaman kullanılır
- "Teşvik belgemiz iptal edildi", "kısmi müeyyide yazısı geldi", "faiz desteğini gecikme zammıyla geri istiyorlar", "belge iptal edilince vergi dairesi KDV tarh etti".
- Bakanlık ya da vergi dairesi görevlisinin "bu belgeyi iptal etmeli miyiz, kısmi müeyyide mi uygulanmalı, geri alma nasıl yapılır?" sorusu (idare tarafı, §6).

**Upstream uyarlaması** (`litigation-legal/demand-received`): gelen yazıyı önce **alan alan ayrıştır** (kim, hangi belge, hangi hüküm, hangi destek, ne kadar, ne zamana kadar, hangi yol gösterilmiş), sonra seçenekleri yan yana koy; yazının söylediğini doğrulamadan kabul etme.

Vergi tarhiyatına karşı yol (uzlaşma, dava, ödeme emri) → `../../vergi/SKILL.md`. Dava dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`.

---

## 1. Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| İptal sebepleri | Karar/mevzuata aykırılık, belgedeki kayıt ve koşulları yerine getirmeme, tahrifat, sahte/yanıltıcı belge, yanlış bilgi, belge kapsamı makineyi (icra/iflas yoluyla dahil) süresinden önce satma ya da sattırma, yatırımı ve ekosistem planını öngörülen sürede tamamlamama, asgari yatırım tutarına uymama | 9903 m.32/1  |
| Kısmi müeyyide | Yükümlülük kısmen yerine getirilmiş ve iptal gerekmiyorsa desteklerin ilgili kısmı geri alınır | 9903 m.32/2  |
| Geri alma usulü | İptal ya da kısmi müeyyidede destekler **6183 hükümlerine göre** geri alınır; finansal kiralama makinesine isabet eden kısım kiralama şirketine de uygulanabilir | 9903 m.32/3-4  |
| Faiz/makine desteği | Fazla ödenen tutara her ödeme tarihinden itibaren 6183 m.51 gecikme zammı; önceki karar belgelerine de uygulanır | 9903 m.15/8, m.17/5  |
| Vize aşamasında eksiklik | Destekler (müracaat tarihindeki mevzuata uygun olmak şartıyla) revize edilir; fazlası 6183 ile geri alınır | 9903 m.29/8  |
| Vize müracaatı yapılmaması | Bildirimden iki ay sonra iptal | 9903 m.29/5  |
| Vergisel sonuç (KDV) | Yatırım belgede öngörüldüğü gibi gerçekleşmezse alıcıdan vergi ziyaı cezalı KDV + gecikme faizi; zamanaşımı gerektiren durumu izleyen takvim yılı başından | 3065 m.13/d  |
| Ar-Ge teşvikleri | Şart ihlali/amaç dışı kullanımda vergi ziyaı doğmuş sayılır; vergi dışı destekler 6183 ve gecikme zammıyla | 5746 m.4/4  |
| SGK desteği | Yersiz yararlanma gecikme cezası ve zammıyla; fiilen çalışmayan bildiriminde bir yıl yoksunluk | 5510 ek m.2  |
| Mücbir sebep | Sebep sürdükçe süre işlemez; kullanılamaz hale gelen harcamanın destekleri geri alınmaz, durdurulur | Tebliğ 2025/1 m.25/3-4  |

**Orantılılık:** m.32/2 kısmi müeyyideyi açıkça öngörür. Eksikliğin belge iptalini değil kısmi geri almayı gerektirdiğini savunmak çoğu dosyada ana argümandır `[incele]`.

**İptalin geri alınması:** Bakanlık iptali sonradan geri alıp vize yaparsa iptale dayalı vergi tarhiyatının dayanağı kalmaz.  Bu nedenle iki işlem (Bakanlık iptali ve vergi tarhiyatı) **ayrı ayrı ve süresinde** dava edilmeli; iptal davası sonucu tarhiyat davasını etkiler (bekletici mesele / dayanağın kalkması) `[incele]`. 

---

## 2. Gelen yazının ayrıştırılması (triyaj)

| Alan | Yazıda ne var | Kontrol |
|---|---|---|
| Gönderen | Teşvik Uygulama GM / vergi dairesi / gümrük / SGK | İşlemi yapmaya yetkili mi? |
| Belge | No, tarih, dayandığı karar | 2012/3305 belgesine 9903 maddesi mi uygulanmış? |
| İşlem türü | İptal / kısmi müeyyide / revize / geri alma talebi / tarhiyat | Kesin ve yürütülmesi gereken işlem mi, hazırlık yazısı mı? |
| Dayanılan hüküm | Karar m.?, Tebliğ m.? | Madde metniyle örtüşüyor mu? |
| Olgu | Satış, eksik makine, süre aşımı, istihdam eksiği, vize başvurusu yok… | Kanıt ve ekspertiz raporu dosyada mı? |
| Bildirim | m.29/5 bildirimi yapıldı mı, tarihi | İki ay geçti mi? |
| Tutar ve faiz | Geri alınacak destek, gecikme zammı başlangıcı | Her ödeme tarihinden mi hesaplanmış? |
| Gösterilen yol ve süre | Dava, mahkeme, süre | İYUK m.11 başvurusu/ dava süresi |
| Tebliğ tarihi | KEP/e-tebligat/posta | Süre başlangıcı |

---

## 3. Kontrol listesi

1. **Dayanak karar doğru mu?** Eski belgeye dayandığı karar uygulanır; 9903'ün önceki belgelere açıkça uzanan hükümleri (m.15/8, m.29/5-7, m.33 son cümle) dışında 9903 maddesiyle işlem kurulmuşsa 🟠. 
2. **Usul:** iptalden önce yatırımcıya bilgi/belge istendi mi, ekspertiz yapıldı mı, vize için m.29/5 bildirimi yapıldı mı? Bildirimsiz iptal 🔴 (idare aleyhine).
3. **Olgu-hüküm uyumu:** sayılan iptal sebebi gerçekten var mı (ör. "satış" iddia edilen makine aslında mücbir sebeple kullanılamaz hale gelmiş olabilir; yer değişikliği izni alınmış olabilir)?
4. **Orantılılık:** eksik iptal mi gerektiriyor, kısmi müeyyide mi (m.32/2)?
5. **Mücbir sebep:** resmî yazı ile tevsik edildi mi; süre işlemez kuralı uygulandı mı (Tebliğ m.25)?
6. **Geri alma hesabı:** hangi destek, hangi tarihten, hangi oranla; 6183 m.51 gecikme zammı ödeme tarihinden; vergisel destekler (KDV, vergi indirimi) vergi dairesince VUK'a göre ayrıca tarh edilir → `vergi`.
7. **Zamanaşımı:** KDV 13/d'de zamanaşımı gerektiren durumun meydana geldiği yılı izleyen yıl başından; vergi dışı destekte 6183 tahsil zamanaşımı → `../../vergi/references/amme-alacagi-tahsili-6183.md`. 
8. **Finansal kiralama şirketi** müeyyideye ortak edildi mi (m.32/4)?
9. **Ceza boyutu:** sahte/yanıltıcı belge iddiası varsa ceza soruşturması riski `[incele]` → `ceza-hukuku-suclar` (3. dalga; yoksa işaret).
10. **Teminat/ödeme:** dava tahsili durdurmaz; yürütmenin durdurulması iste `[incele]`.

---

## 4. Süreler ve dayanakları

| İşlem | Süre | Başlangıç | Dayanak |
|---|---|---|---|
| Bakanlık iptal/müeyyide işlemine iptal davası (idare mahkemesi) | 60 gün | Yazılı bildirimi izleyen gün | 2577 m.7  |
| Teşvik ihlaline dayalı vergi tarhiyatına dava (vergi mahkemesi) | 30 gün | Tebliği izleyen gün (e-tebligatta iletimi izleyen 5. gün sonu) | 2577 m.7; esas → `vergi` |
| Vize müracaatı (iptalden kaçınmak için) | Bildirimden 2 ay | Bakanlık bildirimi | 9903 m.29/5 |
| Geri alınan faiz desteği | Gecikme zammı her ödeme tarihinden | — | 9903 m.15/8 |

Yetkili idare mahkemesi (işlemi yapan merkez teşkilatı / yatırım yeri) için İYUK m.32-33 ve güncel uygulamayı `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`'den kontrol et `[doğrula]`. Daireyi ve mahkemeyi sabit yazma. Genel kural: özel hüküm yoksa yetkili mahkeme işlemi yapan idari merciin bulunduğu yer idare mahkemesidir (İYUK m.32/1); m.33 yalnız kamu görevlileri davalarına ilişkindir. Bakanlık merkez işlemlerinde bu kural Ankara'yı gösterir; il müdürlüğü/ajans işleminde işlemi yapan birimin yeri.  

---

## 5. soorgla çağrıları

```
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2025/05/20250530-2.pdf"  offset: 50000  max_chars: 12000   # m.29-34, geçici maddeler
legal_get_statute_article  law_no: "2577"  law_type: "Kanun"  article_no: "7" | "11" | "27" | "32" | "33"
legal_get_statute_article  law_no: "3065"  law_type: "Kanun"  article_no: "13"
legal_search_cases  mahkeme: "danistay"  sorgu: "yatırım teşvik belgesinin iptali işleminin iptali tamamlama vizesi"  tarih_baslangic: "2023-01-01"
legal_search_cases  mahkeme: "danistay"  sorgu: "yatırım teşvik belgesi iptal edildiğinden katma değer vergisi tarhiyatı vergi ziyaı"  tarih_baslangic: "2023-01-01"
legal_get_case_document  belge_id: "<seçilen karar>"
legal_search_official_gazette  query: "gecikme zammı oranı"  sort_by: "date_desc"
legal_search_admin_guidance  sorgu: "yatırım teşvik belgesi iptal KDV istisnası geri alınması"  tarih_baslangic: "2024-01-01"
```

Danıştay'da bulunan örnekler (son 3 yıl): 3. D. E.2023/5837 K.2024/6305 (iptal geri alınınca tarhiyat dayanaksız; tam metin okundu), 7. D. E.2022/4602 K.2024/4356 (teminatla ithalatta belge ibrazı; tam metin okundu), 3. D. E.2021/2393 K.2023/1621, E.2021/2392 K.2023/1620 (belge iptali sonrası kurumlar vergisi; yalnız özet görüldü `[çekildi ama desteği doğrulayın]`). 

---

## 6. İdare tarafı

**Teşvik Uygulama GM / ekspertiz görevlisi:**
- İptal yerine kısmi müeyyide yeterli mi (m.32/2)? Gerekçede neden iptal seçildiğini yaz.
- Vize müracaatı yapılmayan belgede bildirimi tebliğ et, iki aylık süreyi bekle; bildirim yoksa iptal etme.
- Mücbir sebep başvurusunu Tebliğ m.25 listesine göre değerlendir, resmî yazıyı iste.
- Geri alma yazısında her destek için ödeme tarihini, tutarı ve gecikme zammı başlangıcını ayrı göster; vergi dairesine/SGK'ya/gümrüğe bildirim yap.

**Vergi dairesi:** iptalin kesinleşip kesinleşmediğini ve geri alınıp alınmadığını sor; iptal davası açılmışsa tarhiyatın akıbetinin ona bağlı olduğunu dosyaya not et.

İç değerlendirme ile yatırımcıya gidecek yazıyı ayır (ORTAK-KURALLAR.md §1 gönderim yeri).

---

## 7. Çıktı iskeleti

```markdown
## Teşvik belgesi iptal/müeyyide değerlendirmesi — [belge] — [tarih]
### Sonuç: [dava / yeniden başvuru-vize / kısmi ödeme / bekle] — son gün: [ ]
### Yazının ayrıştırılması (tablo §2)
### Süre tablosu
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |
### Hukuka aykırılık iddiaları (her biri işaretli, dayanaklı)
### Geri alma hesabının kontrolü (kullanıcı rakamıyla)
### Vergi/SGK/gümrük yansımaları → ilgili beceri
### Seçenekler
| Yol | Sonuç | Risk | Maliyet | Not |
```

---

## 8. Sık hatalar

- 🔴 Yalnız vergi tarhiyatına dava açıp Bakanlığın iptal işlemini süresinde dava etmemek (tarhiyatın dayanağı kesinleşir).
- 🔴 Vize bildirimini almışken iki ayı kaçırmak.
- 🟠 Eski karar belgesinde 9903 maddesine dayanan işlemi sorgulamamak.
- 🟠 Kısmi müeyyide imkânını (m.32/2) hiç tartışmamak.
- 🟠 Gecikme zammının başlangıcını tebliğ tarihi sanmak (her ödeme tarihinden).
- 🟡 Mücbir sebebi resmî yazısız ileri sürmek.

---

