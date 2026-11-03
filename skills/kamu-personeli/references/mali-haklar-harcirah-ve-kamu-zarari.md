# Mali haklar, harcırah, yersiz ödeme ve kişi borcu

## Ne zaman kullanılır
- Memur aylığı, ek gösterge, zam ve tazminat, ek ödeme, ek ders, nöbet ücreti eksik ödendi (memur tarafı) ya da doğru mu hesaplanıyor (mutemet / strateji birimi).
- Geçici ya da sürekli görev yolluğu (harcırah) hakkı ve tutarı.
- İdare geçmişe dönük "yersiz ödeme" diye kişi borcu çıkardı; geri ödeme, faiz, taksit ve dava yolu.
- Sayıştay sorgusu ya da ilamı (personel ve harcırah ödemeleri).

**Kural:** katsayı, gösterge, gündelik, vergi dilimi ve oran **beceri metnine yazılmaz**. Eski YAML'daki "%15, %20, %27" gelir vergisi dilimleri ve "güncel memur maaş katsayısı doğru mu?" sorusu bu nedenle alınmadı. Değerler bordrodan, ilgili yıl bütçe kanunu cetvellerinden ya da kullanıcıdan alınır; `[doğrula]`. `legal_get_social_parameters` memur maaş katsayılarını döndürmüyor.

---

## Kurallar ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| Memuriyet mahalli içinde görev | Resmî görevle memuriyet mahalli içinde bir yere gönderilene **gündelik verilmez** (madde içindeki istisnalar saklı) | 6245 m.39 |
| Geçici görev gündeliği | Yurt içinde ilk **90 gün tam**, takip eden **90 gün 2/3**; yurt dışında ilk 180 gün tam, sonrası 2/3 | 6245 m.42 |
| Memuriyet mahallinin tanımı | Belediye sınırları ölçütü; büyükşehirlerde özel durum | 6245 m.3/g (6552/89 ile değişik) |
| Gündelik tutarları, konaklama sınırları | Her yıl merkezi yönetim bütçe kanunu cetvelleri | Kullanıcıdan / bütçe kanunu; `[doğrula]` |
| Kademe ilerlemesinin geriye dönük iptali | Müstahak olmadığı sonradan anlaşılanın ilerlemesi ilerlemiş sayıldığı tarihten iptal edilir | 657 m.64 son fıkra → yersiz ödeme doğar |
| Kamu zararı ölçütleri | Fazla ödeme, iş/hizmet yaptırılmadan ödeme, transfer niteliğindeki giderlerde fazla veya yersiz ödeme vb. | 5018 m.71/2 — Sayıştay 5. Daire K.48968 (08.11.2023) kararında aktarılan metin `[soorgla]` |
| Sayıştay emsal (belediye maktu fazla çalışma) | Maktu fazla çalışma ücreti yalnız zabıta ve itfaiyede fiilen çalışana ödenebilir | Sayıştay 4. Daire K.52311 (27.03.2024) `[soorgla]` `[çekildi ama desteği doğrulayın]` |
| Sayıştay emsal (harcırah) | Mevzuata aykırı geçici görev yolluğu ödemesinden kamu zararı | Sayıştay 5. Daire K.44049 (22.05.2019) `[soorgla]` — eski; daha güncel karar ara |
| İdari hata kaynaklı yersiz ödemenin geri alınması | İki yaklaşım var: (1) Danıştay İçtihatları Birleştirme Kurulu 22.12.1973 t. E.1968/8 K.1973/14 — yokluk, açık hata, memurun gerçek dışı beyanı veya hilesi hâlinde süre aranmaksızın, bunların dışında (memurun iyiniyetli olduğu hâllerde) yalnız **dava açma süresi içinde** geri alınabilir; (2) Danıştay 12. Daire 2024'te, rızaen iade istemini ve aksi hâlde Kamu Zararlarının Tahsiline İlişkin Usul ve Esaslar Hakkında Yönetmeliğe göre tahsil edileceğini bildiren yazıyı **kesin ve yürütülmesi gereken işlem saymadı** (davanın incelenmeksizin reddi); ödenmezse idare adli yargıya başvurabilir. Hangisinin uygulanacağı işlemin türüne (borç bildirimi mi, maaştan kesinti/geri alma işlemi mi) göre değişir; güncel kararı ara `[incele]` | |

**Sayıştay kapsamı:** soorgla'da Sayıştay daire kararları 2011-2024 arası mevcut; personel ve harcırah kararlarına `legal_search_cases` (`mahkeme: "sayistay"`) ile ulaşılıyor. Temyiz Kurulu ve Daireler Kurulu kararlarının kapsamı bu turda ölçülmedi.

---

## Kontrol listesi — memur / avukat tarafı

**Eksik ödeme talebi:**
1. Hangi kalem (aylık, ek gösterge, tazminat, ek ödeme, ek ders, nöbet, yolluk)? Dayanağı (657 m.146 ve sonrası, 375 KHK, özel kanun, ilgili CBK)?
2. Hak doğuran olgu ve tarihi (göreve başlama, öğrenim değişikliği, unvan, kademe hak kazanma tarihi).
3. Önce idareye **yazılı başvuru** (İYUK m.10); 30 gün cevapsızlık ret sayılır → 60 gün içinde **tam yargı** (ya da iptal + tam yargı) davası → `personel-davasi-usul-ve-sureler.md`.
4. Geriye dönük alacak: her ay doğan (süregelen) parasal haklarda Danıştay, ancak dava süresi içinde kalan ilk uygulamadan itibaren doğan alacağa hükmediyor — süresinde başvurup süresinde dava açılmışsa başvurudan geriye doğru dava süresi içindeki ilk uygulama, süreler kaçırılmışsa dava tarihinden geriye doğru dava süresi içindeki ilk uygulama esas alınır; daha eski aylar süre aşımından reddedilir 🔴. Faiz başlangıcı: idareye başvuru varsa başvuru tarihi, yoksa ya da başvuru reddinden sonra süresinde dava açılmadıysa dava tarihi (henüz doğmamış alacak için başvurudan faiz işlemez). Bu hesabı İYUK m.10-11'deki 7331 sonrası 30 günlük cevap süresiyle yeniden kur; 5 yıllık zamanaşımı ya da 6183 gibi bir süre beceride varsayılmaz `[doğrula]`.

**Kişi borcu / yersiz ödeme bildirimi geldi:**
1. Borç yazısının tarihi, tebliği, tutarı, dönemi, hesap tablosu var mı?
2. Ödemenin kaynağı: idarenin hatası mı, memurun yanıltıcı beyanı mı? İyiniyet. `[incele]`
3. Faiz istenmiş mi, hangi tarihten? Taksit imkânı?
4. Borç işlemine karşı **60 gün** içinde iptal davası; yürütmenin durdurulması (maaştan kesinti başladıysa).
5. Sayıştay ilamına dayalıysa: ilam memura tebliğ edildi mi, sorumlu kim (ita amiri, gerçekleştirme görevlisi, muhasebe yetkilisi), memur ilama taraf mı? → `../../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`.

## Kontrol listesi — idare tarafı (mutemet, strateji, gerçekleştirme görevlisi)

1. **Harcırah ödemesi öncesi:** geçici görev onayı var mı; görev yeri memuriyet mahalli dışında mı (m.39); süre 90/90 sınırı (m.42); belgeler (konaklama faturası, yol bileti) ve bütçe kanunu sınırları.
2. **Bordro kontrolü:** derece/kademe ve ek gösterge kadroya uygun mu; kademe ilerlemesi onayı (m.64); disiplin cezasının kademe ilerlemesine etkisi.
3. **Yersiz ödeme tespit edilince:** hesap tablosu (dönem, kalem, brüt/net, kesintiler), tebliğ, itiraz ve dava yolu gösterimi; faiz uygulanacaksa dayanağı `[incele]`.
4. Sayıştay sorgusu geldiyse savunma süresi ve sorumlular listesi → `../../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`.

---

## Hesap tablosu iskeleti (tutar uydurulmaz)

```markdown
| Dönem | Kalem | Ödenmesi gereken (formül) | Ödenen | Fark | Dayanak | Girdi kaynağı |
|---|---|---|---|---|---|---|
| [ay/yıl] | [ek gösterge / gündelik] | [gösterge × katsayı] — katsayı: [kullanıcıdan / bütçe kanunu] | [bordrodan] | [=] | [madde] | [belge] |
```

Her formül girdisinin kaynağı yazılı olmadan tablo "tamam" sayılmaz `[doğrula]`. Faiz hesabı için `legal_get_legal_interest_rates` 7589 sonrası yanlış oran verebilir; faizde kanun metnine dayan `[incele]`.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Kalem | Hangi ödeme, hangi dönem? Bordro örnekleri var mı? |
| Görevlendirme | Geçici görev onayı, görev yeri, süre? |
| Borç | Kişi borcu yazısı, tarih, tutar, hesap tablosu, tebliğ tarihi? |
| Kaynak | Fazla ödeme kimin işleminden doğdu? Beyanınız istenmiş miydi? |
| Sayıştay | Sorgu/ilam var mı? Sorumlu olarak gösterilen kim? |

---

## soorgla çağrıları

```
legal_search_statute_semantic mevzuat_no: "6245" sorgu: "<memuriyet mahalli | geçici görev gündeliği | sürekli görev yolluğu>"
legal_get_statute_article law_no: "657" law_type: "Kanun" article_no: "64" | "146" | "152"
legal_search_statute_semantic sorgu: "kamu zararı yersiz ödeme 5018 sayılı Kanun 71 inci madde"
legal_search_statute_semantic sorgu: "<yıl> merkezi yönetim bütçe kanunu harcırah gündelik cetveli" yalniz_tablolar: true
legal_search_cases sorgu: "<kalem> yersiz ödeme personel kamu zararı" mahkeme: "sayistay" tarih_baslangic: "<3 yıl önce>"
legal_search_cases sorgu: "idari hata sonucu yersiz ödeme iyiniyetli memur geri alınması faiz" mahkeme: "danistay"
```

---

## Sık hatalar
- Memuriyet mahalli içindeki göreve gündelik ödemek (Sayıştay'ın en sık bulgusu).
- 90 günü aşan geçici görevde tam gündeliğe devam etmek.
- Katsayı ya da vergi dilimini eski yıldan almak.
- Kişi borcu yazısına dava açmadan maaştan kesintiye razı olmak (60 gün süre).
- Sayıştay ilamını memura karşı doğrudan icra edilebilir sanmak — sorumlular ve tahsil usulü `[incele]`.
