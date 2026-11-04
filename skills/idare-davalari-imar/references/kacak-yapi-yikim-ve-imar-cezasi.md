# Kaçak yapı: yapı tatil tutanağı, mühürleme, yıkım, imar para cezası ve imar barışı

## Ne zaman kullanılır
- Belediye ya da valilik ruhsatsız/ruhsata aykırı yapı tespit etti: yapı tatil tutanağı, mühürleme, encümen (il idare kurulu) yıkım kararı, 3194 m.42 imar para cezası (İPC).
- Yapı için 2018 imar barışında **yapı kayıt belgesi** alınmış; yıkım/ceza karşısında etkisi soruluyor.
- İdare tarafı (imar müdürlüğü, encümen, denetim): tutanağın ve kararın usulüne uygun kurulması, savunma, yıkımın icrası.

---

## Yargı yolu — İPC sulh cezada değil idari yargıda

- 3194 m.42 imar para cezası, imara aykırı yapılanmanın tespiti, önlenmesi ya da giderilmesine yönelik idari işlemin devamıdır; 5326 m.27/8 gereğince **idari yargıda** dava edilir. Sulh ceza hâkimliğine "15 gün itiraz" yolu yanlıştır; İYUK m.7 genel süresi (60 gün) uygulanır `[incele]`. 
- Yıkım ve İPC çoğunlukla **aynı encümen kararında**dır; tek dilekçeyle iptal istenir (İYUK m.5 bağlılık). 
- Yetki: taşınmazın bulunduğu yer idare mahkemesi (İYUK m.34/1 — "imar ... yıkım ... ruhsat"). 
- Ceza yönü: imar kirliliği suçu (TCK m.184) idari süreçten bağımsızdır; yapı plana ve ruhsata uygun hâle getirilirse kamu davası açılmaz/düşer (m.184/5); m.184'ten mahkûm olana, aynı fiil için tahsil edilen İPC faizsiz iade edilir (3194 m.42). → ceza ayrıntısı `../../ceza-ve-infaz-dilekce/SKILL.md`. 

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Yapı tatil zaptının **yapıya asılması = yapı sahibine tebliğ**; bir nüsha muhtara, bir nüsha İl Müdürlüğüne | Asılma tarihi | 3194 m.32/2 (7221 ile değişik cümle) | Tebligat Kanunu'na göre ayrıca tebliğ şartı kanunda yok; usulüne uygun asılma yeterli `[incele]`.  |
| Aykırılığın tapu beyanlar hanesine bildirimi: en geç **yedi gün** | Tespit | 3194 m.32/1 (7221) | İdare yükümlülüğü. |
| Yapı sahibinin yapıyı ruhsata uygun hâle getirmesi / ruhsat alması: **en çok bir ay** | Asılma (tebliğ) | 3194 m.32/3 | Süre içinde uygun hâle getirilirse mühür kaldırılır; aksi hâlde ruhsat iptali ve encümen yıkım kararı (m.32/5). |
| **İstisna — bir ay beklenmez:** idare yapının ruhsata bağlanamayacağını ya da aykırılığın giderilemeyeceğini tespit ederse ruhsat beklemeden iptal ve yıkım | Tespit | 3194 m.32 son fıkra (7153, 2018)  | Eski YAML'daki "30 gün dolmadan encümen yıkım kararı alamaz" kuralı **mutlak değil**. |
| Bir ay sonunda uygun hâle getirilmeyen yapıda iki ay içinde yıkım kararı alınmaz ya da kararlı yapı altı ay içinde yıkılmazsa Bakanlık yıkar/yıktırır, maliyet **%100 fazlasıyla idareden** | Tutanak tarihi | 3194 m.32/5 (7221) | İdare tarafı için risk. Eski YAML'daki "%20 ek yıkım masrafı" 2960 Boğaziçi K. m.13'e özgüdür, 3194'e değil.  |
| Encümen İPC kararı: tespitten itibaren **on iş günü** içinde | Aykırılığın tespiti | 3194 m.42/1  | Sürenin aşılmasının işlemi sakatlayıp sakatlamadığı `[incele]` (düzenleyici süre mi?). |
| m.42/2-ç ilave ceza (emlak vergisi birim değeri × alan): tebliğden itibaren **bir ay** içinde aykırılık giderilirse tahsil edilmez | İPC tebliği | 3194 m.42/2-ç (7226) | |
| İPC ve yıkıma karşı iptal davası: **60 gün** | Encümen kararının tebliği | İYUK m.7 | YD istemi şart değil ama yıkımın icrasından önce gerekli. |

`legal_calculate_deadline` bu süreleri tanımıyor; elle hesapla (İYUK m.8), `[doğrula]`.

---

## Kontrol listesi — ilgili / yapı sahibi tarafı ("usul süzgeci")

1. **Yapı tatil tutanağı**
   - Tarih, düzenleyenler, yetkili idare (belediye/valilik; Boğaziçi'nde 2960 özel usul).
   - **Yapıya asıldı mı?** Muhtara nüsha bırakıldı mı? Asılma tarihi ile zaptın tarihi tutarlı mı?
   - Yapının o andaki durumu (kat, alan, ölçü, kroki, fotoğraf) **açık ve tereddütsüz** mü? Danıştay: tamamen ruhsatsız yapıda alan ölçüsündeki eksiklik **yıkım** yönünden tutanağı sakatlamaz; ama **İPC** için aykırılığa konu alan, mülkiyet durumu, alanın özelliği gibi hesaba esas tespitlerin tutanakta yer alması **zorunlu**. Bu ayrım dilekçede ayrı başlık olmalı. 
2. **Bir aylık süre** verildi mi; yoksa m.32 son fıkra istisnası (ruhsata bağlanamaz tespiti) gerekçelendirildi mi?
3. **Encümen kararı**: toplantı ve karar yeter sayısı, gerekçe, yetki (belediye encümeni/il idare kurulu; büyükşehir/ilçe yetki ayrımı `[incele]`).
4. **İPC hesabı** (m.42/2): yapı sınıfı ve grubu (Bakanlık sınıflandırması), aykırılıktan etkilenen alan (m²), birim tutar × o yılın yeniden değerleme oranı, artırım oranları (c bendi — hisseli parsel, kamuya ait parsel, ruhsatsız, tamamlanmış ve kullanılıyor vb.) **ayrı ayrı** hesaplanmış mı, mükerrer artırım var mı? Tutarları beceriye yazma; m.42 metnini çek, hesabı göster, `[doğrula]`.
5. **Muhatap**: ceza yapı sahibine, yapı müteahhidine ve aykırılığı altı iş günü içinde bildirmeyen fenni mesule **ayrı ayrı** (m.42/2); doğru kişiye mi kesildi? Yapı sahibi kim (malik mi, fiilen yapan mı)? `[incele]`
6. **Tekerrür** (m.42: fiilin tekrarında bir kat artırım) doğru uygulandı mı? Aynı fiil için mükerrer ceza var mı?
7. **İmar barışı** (3194 geçici m.16): yapı kayıt belgesi var mı, 31.12.2017 öncesi yapı mı, başvuru ve ödeme süresinde mi? Varsa **bu Kanun uyarınca alınmış yıkım kararları ile tahsil edilemeyen İPC'ler iptal edilir** (tahsil edilmiş İPC iade edilmez). Üçüncü kişilere ait özel mülkiyet, Hazine'nin sosyal donatı tahsisli arazileri, Boğaziçi sahil şeridi/öngörünüm, tarihi yarımada ve Gelibolu tarihi alanı kapsam dışı. Bu kapsam dışı yapılara belge düzenlendiği sonradan tespit edilirse belge **iptal edilir**, sağladığı haklar geri alınır ve yatırılan bedel iade edilmez; yalan beyanda bulunan hakkında TCK m.206'dan suç duyurusu yapılır — dayanak Kanun değil **Yapı Kayıt Belgesi Verilmesine İlişkin Usul ve Esaslar m.8/2** (Danıştay 6. D. iptal istemini reddetti; bedelin iade edilmemesi kısmına karşı oy var, İDDK aşamasını kontrol et). Belge yapının yenilenmesine ya da kentsel dönüşüme kadar geçerli. AYM bu maddede iki iptal kararı verdi: E.2019/21 K.2020/51 ("yıkım kararları ile tahsil edilemeyen idari para cezaları iptal edilir" cümlesindeki bir ibare) ve E.2023/74 K.2024/141 (onuncu fıkranın üçüncü cümlesi: "Yapının depreme dayanıklılığı hususu malikin sorumluluğundadır." — RG 03.12.2024/32741; idarenin denetim yükümlülüğü belge sonrasında da sürer, depremden doğan zarar için tam yargı yolu açık). Güncel metni çek.  
8. **Kazanılmış hak / eski yapı**: yapı 3194 öncesi mi, ruhsatlı ama sonradan değişiklik mi, köy yerleşik alanı (m.27) mı?
9. YD: yıkım uygulanmakla etkisi tükenecek işlemdir → savunma alınmadan YD istemi (İYUK m.27/2) ayrı başlık. 
10. Emsal: son 3 yıldan en az bir Danıştay tam metni (ör. yukarıdaki 4. D. 2025 kararı).

## Kontrol listesi — idare tarafı (belediye / encümen)

1. Tutanak: yerinde ölçüm; kat kat ölçü ve kroki; fotoğraf; yapı sınıfı/grubu; aykırılık türü (ruhsatsız / ruhsata aykırı / cephe-malzeme); mülkiyet durumu ve alanın özelliği (artırım bentleri için); fenni mesul bildirimi.
2. Asılma ve muhtar nüshası tutanağı; İl Müdürlüğüne gönderim; tapuya yedi gün içinde beyan bildirimi.
3. Bir ay süre verildi mi, ya da ruhsata bağlanamazlık tespiti ayrı ve gerekçeli mi?
4. Encümen kararı on iş günü içinde; İPC hesap tablosu karar ekinde; her sorumlu için ayrı ceza; dava yolu-süre-merci bildirimi.
5. Yıkım kararını iki ayda alma, altı ayda yıkma (aksi hâlde Bakanlık yıkar, %100 fazlası idareden).
6. YD kararı gelirse yıkımı durdur (İYUK m.28/1).
7. Yapı kayıt belgesi sorgusu (e-Devlet/Bakanlık kaydı) karar öncesi.
8. Belge ve yazılar: tutanak ve encümen kararı metni → `../../idari-ve-kurum-basvurulari/SKILL.md` (`tutanak.md`, `resmi-yazi-ve-olur.md`).

## Görüşme soruları

| Alan | Soru |
|---|---|
| Yapı | Ne zaman yapıldı; ruhsat/iskân var mı; ne kadar aykırılık (kat, m²)? |
| Tutanak | Tarih; yapıya asıldı mı; elinizde fotoğrafı/kopyası var mı? |
| Encümen | Karar tarihi, sayısı; yıkım mı, ceza mı, ikisi mi; tebliğ tarihi? |
| Ceza | Tutar, hesap tablosu; kime kesildi? |
| İmar barışı | Yapı kayıt belgesi no ve tarihi; başvurudaki beyanlar |
| Ceza davası | TCK 184 soruşturması/kovuşturması var mı? |

## soorgla çağrıları

```
legal_get_statute_article  law_no: "3194"  law_type: "Kanun"  article_no: "32" | "42" | "27"
legal_get_statute_article  law_no: "3194"  law_type: "Kanun"  article_no: "geçici 16"
legal_get_statute_article  law_no: "5326"  article_no: "27"  law_type: "Kanun"
legal_get_statute_article  law_no: "5237"  article_no: "184"  law_type: "Kanun"
legal_get_statute_article  law_no: "2577"  article_no: "27" | "34"
legal_search_cases  sorgu: "yapı tatil tutanağında aykırılığa konu alan tespit edilmeden verilen imar para cezası"  mahkeme: "danistay"  tarih_baslangic: "<3 yıl önce>"
legal_search_cases  sorgu: "yapı kayıt belgesi bulunan yapı hakkında yıkım kararı"  mahkeme: "danistay"
legal_case_facets  sorgu: "yapı tatil tutanağı yıkım imar para cezası"  mahkeme: "danistay"  tarih_baslangic: "<3 yıl önce>"
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Kaçak yapı işlemleri değerlendirmesi — [taşınmaz, encümen kararı]
### Sonuç
### Kronoloji (tespit → asılma → bir ay → encümen → tebliğ → dava son günü)
### Yıkım yönünden
| # | Usul/esas | Bulgu | Dayanak | Güç |
### İPC yönünden
| Kalem | İdarenin hesabı | Kontrol | Not |
### İmar barışı
### YD (uygulanmakla etkisi tükenecek)
### TCK 184 bağlantısı (işaret)
### Emsal
```

## Sık hatalar
- İmar İPC'sine sulh ceza hâkimliğine 15 günde itiraz etmek (idari yargı, 60 gün).
- "Bir ay dolmadan yıkım kararı alınamaz"ı mutlak sanmak (m.32 son fıkra, 2018).
- Yıkım ve ceza yönlerini tek değerlendirmede birleştirmek; tutanaktaki ölçü eksikliğinin cezayı sakatlayıp yıkımı sakatlamayabileceğini görmemek.
- Yapı kayıt belgesinin tahsil edilmiş cezayı da geri getireceğini sanmak; üçüncü kişi taşınmazındaki yapıya belge alınabileceğini düşünmek.
- "%20 fazlası yıkım masrafı"nı 3194'e uygulamak (2960 Boğaziçi).
- Tutar ve oranları ezberden yazmak; yılın yeniden değerleme oranını atlamak.

