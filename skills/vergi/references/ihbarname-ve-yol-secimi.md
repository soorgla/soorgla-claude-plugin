# İhbarname geldi: triyaj, süre ve yol seçimi

## Ne zaman kullanılır
- Mükellef, kanuni temsilci ya da vekili bir **vergi/ceza ihbarnamesi** (ikmalen, re'sen ya da idarece tarhiyat; yalnız ceza ihbarnamesi) aldı ve "ne yapmalıyım?" diye soruyor.
- "Uzlaşmaya mı gideyim, dava mı açayım, indirimden mi yararlanayım?" sorusu.
- Tebligatın usulüne uygunluğu ya da zamanaşımı şüphesi.

Bu dosya **yolu seçer ve süreyi hesaplar**. Seçilen yolun dilekçesi: uzlaşma, indirim, düzeltme → `../../idari-ve-kurum-basvurulari/references/vergi-uzlasma-indirim-duzeltme.md`; dava → `vergi-davasi.md`.

**Upstream'den uyarlanan triyaj fikri** (`litigation-legal/demand-received`): gelen belgeyi önce alan alan ayrıştır, dosya geçmişiyle (önceki inceleme, önceki uzlaşma, aynı dönem için başka ihbarname) karşılaştır, sonra seçenekleri gerekçeli öneriyle sun; seçimi avukat/mali müşavir yapar.

---

## 1. Belgeyi ayrıştır (ilk iş)

| Alan | Neden önemli |
|---|---|
| İhbarname türü (vergi + ceza / yalnız ceza / ödeme emri mi?) | Ödeme emri ise bu dosya değil → `amme-alacagi-tahsili-6183.md` (süre 15 gün) |
| Tebliğ şekli ve tarihi (elden, posta, e-tebligat iletim tarihi, ilan) | Bütün süreler buradan başlar |
| Vergi türü ve dönemi | Tarh zamanaşımı, daire, ceza kesme zamanaşımı |
| Tarh türü (ikmalen / re'sen / idarece) ve dayanak rapor (vergi inceleme raporu, vergi tekniği raporu, takdir komisyonu kararı) | Uzlaşma kapsamı, rapor tebliğ edildi mi, somut tespit var mı |
| Ceza türü ve katı (vergi ziyaı 1 kat / 3 kat / %50 artırımlı; usulsüzlük; özel usulsüzlük) | Uzlaşma ve indirim imkânı → `vergi-cezalari-ve-pismanlik.md` |
| VUK m.359 atfı var mı (sahte / yanıltıcı belge) | Uzlaşma kapsam dışı; ayrıca suç duyurusu riski |
| Tarhiyat öncesi uzlaşma istendi mi, sonucu? | İstendi ve sağlanamadıysa tarhiyat sonrası uzlaşma yok |
| Aynı dönem için açılmış dava var mı? | Uzlaşma / dava ilişkisi |

---

## 2. Süre tablosu

| İşlem | Süre ve başlangıç | Dayanak | Not |
|---|---|---|---|
| Vergi mahkemesinde dava | Tebliği izleyen günden itibaren **30 gün** | 2577 m.7/1 ve 7/2-b  | Hak düşürücü. |
| Tarhiyat sonrası uzlaşma talebi | İhbarnamenin tebliğinden itibaren **30 gün** | VUK ek m.1/1  | Uzlaşma vaki olmazsa **yeniden istenemez**; idarenin nihai teklifi dava açma süresi sonuna kadar yazılı kabul edilirse uzlaşma sağlanmış sayılır. |
| Uzlaşma vaki olmazsa cezaya dava | Uzlaşmanın vaki olmadığına dair tutanağın tebliğinden itibaren genel hükümlere göre; dava süresi bitmiş ya da **15 günden az** kalmışsa tutanağın tebliğinden itibaren **15 gün** | VUK ek m.7 (dördüncü fıkra)  | Uzlaşma talebinden önce açılan dava, uzlaşma sonuçlanana kadar incelenmez (ek m.7/2). Uzlaşma yalnız cezayı kapsadığından **vergi aslına karşı dava süresi uzlaşma sürecinden bağımsız işler** `[incele]`. |
| Cezada indirim (m.376) | İhbarnamenin tebliğinden itibaren **30 gün** içinde vergi dairesine başvuru; vergi aslı ve cezanın kalan yarısı vadede ya da teminatla vadeden itibaren 3 ay içinde ödenir | VUK m.376/1  | Ödeme yapılmaz ya da **dava açılırsa** indirim düşer. |
| Tarh zamanaşımı | Vergi alacağının doğduğu takvim yılını izleyen yılın başından itibaren **5 yıl** içinde tarh **ve tebliğ** | VUK m.114/1  | Takdir komisyonuna başvuru zamanaşımını durdurur; duran süre her hâlde **1 yılı** aşamaz (m.114/2). Şarta bağlı istisnada süre şartın ihlal edildiği yılı izleyen yıl başından başlar (m.114/3). |
| Ceza kesme zamanaşımı | Vergi ziyaı ve m.353 / mük.355 usulsüzlüklerinde 5 yıl; diğer usulsüzlüklerde **2 yıl** | VUK m.374  | |
| Düzeltme talebi | Tarh zamanaşımı içinde; dava süresi geçtikten sonra reddedilirse şikâyet | VUK m.116-126 | Yalnız **vergi hatası** için; ayrıntı dilekçe becerisinde. |

`legal_calculate_deadline` dava (`iyuk_tax_lawsuit`, 30 gün), tarhiyat sonrası uzlaşma (`tax_settlement_request`) ve cezada indirim (`tax_penalty_reduction_376`) kodlarını tanır; diğerlerini elle hesapla, son günü `legal_check_holiday` ile kontrol et. Araç e-tebligatta 5. gün kuralını bilmez: başlangıç olarak **tebliğ sayılan günü** ver. 

**E-tebligat:** tebliğ, iletildiği tarihi izleyen **beşinci günün sonunda** yapılmış sayılır; 30 gün bu tarihi izleyen günden başlar.  7587 ile e-tebligat zorunluları kanunda sayıldı (kurumlar vergisi mükellefleri, gerçek usulde ticari/zirai/mesleki kazanç mükellefleri, kollektif ve adi komandit şirketler, ÖTV II sayılı liste araçlarının ilk iktisabında adına tescil yapılanlar) ve sistemden çıkış kuralları yazıldı (ör. 65 yaşını dolduranlar talep ederek çıkabilir).   Uygulama: VUK GT Sıra No 596 (RG 11.10.2026, 33397) — sistem Dijital Vergi Dairesi'nde (m.4); zorunlular m.5, muafiyetler (ör. %90 ve üzeri engelli, 18 yaş altı) m.6; mevcut zorunlular yayımı izleyen ayın sonuna kadar, yeni mükellefler işe başlamayı izleyen 15 gün içinde katılır (m.7); evrak sisteme ulaştığı tarihi izleyen 5. günün sonunda tebliğ edilmiş sayılır, SMS/e-posta bilgilendirmesinin yapılmaması süreyi etkilemez (m.9/3, m.10/2); çıkış: sicil terkini, ölüm, zorunlu gerçek kişide mükellefiyet bitiminden itibaren 5. takvim yılı sonundan sonra başvuru, 65 yaş başvurusu (m.11/1); tasfiye/iflas hâlindeki şirkete e-tebligat yapılmaz (m.11/3); 1.7.2026 öncesi kayıtlılar yeniden başvurmaz (geçici m.1); VUK GT 456 yürürlükten kalktı (m.15).  Mükellefiyeti sona eren gerçek kişiye eski düzende e-tebligat yapılabileceğini Danıştay kabul etmişti (9. D. E.2023/6289 K.2024/4445, oyçokluğu); yeni metindeki çıkış kurallarıyla birlikte değerlendir `[incele]`.

---

## 3. Yol seçimi — 7524 sonrası tablo

**En önemli değişiklik:** 7524 sayılı Kanunla (RG 02.08.2024) uzlaşmanın konusundan **vergi aslı çıkarıldı**; tarhiyat öncesi ve sonrası uzlaşma artık yalnız **cezaların** (vergi ziyaı cezası ile eşik üstü usulsüzlük ve özel usulsüzlük cezaları) tahakkuk edecek miktarı hakkındadır. Vergi aslı tartışmalıysa tek yol **dava** (ya da vergi hatasıysa düzeltme).  Geçiş: yürürlükten önce uzlaşma talep edilmiş, günü verilmemiş/ertelenmiş ya da talep süresi geçmemiş vergi ve cezalarda eski hükümler uygulanır (VUK geçici m.35).  Eski YAML'daki "tarhiyat (vergi aslı) ihtilaflıysa uzlaşma en uygun yoldur" ifadesi bu nedenle **yanlış**tır.

| Yol | Ne sağlar | Ne kaybettirir | Ne zaman düşün |
|---|---|---|---|
| **Dava** (2577) | Vergi aslı ve cezanın tamamının hukuka uygunluk denetimi; dava konusu kısmın tahsili durur (m.27/4) | İndirim hakkı (m.376) | Usul hatası (tebliğ, zamanaşımı, rapor), somut tespit eksikliği, hukuki yorum farkı, vergi aslı tartışmalı |
| **Tarhiyat sonrası uzlaşma** (ek m.1) | Ceza tutarında pazarlık; uzlaşılan cezaya başkaca indirim yok (ek m.9) | Uzlaşılan cezaya dava yok; uzlaşma vaki olmazsa tekrar istenemez | Vergi aslını kabul edip ceza yükünü düşürmek; ek m.1'deki gerekçelerden biri somut olarak ileri sürülebiliyor |
| **Cezada indirim** (m.376) | Vergi aslı + cezanın yarısı ödenirse cezanın yarısı silinir | Dava hakkı (dava açılırsa indirim düşer) | Vergi aslı tartışmasız, ceza da makul; hızlı kapanış |
| **Düzeltme ve şikâyet** (m.116-124) | Açık vergi hatasının (hesap / vergilendirme hatası) süre geçse de düzeltilmesi | — | Hata yorum gerektirmeden ilk bakışta anlaşılıyorsa; yorum gerekiyorsa yol kapalı |

Uzlaşılan cezalarda başkaca indirim uygulanmaz; eski metindeki "376/2 hariç indirim yok" ibaresi 7524 ile "başkaca bir indirim uygulanmaz" olarak değişti.  Uzlaşma ile indirim arasındaki parasal karşılaştırma ve "vergi aslına dava + cezaya indirim" gibi kısmi kurgular avukatın takdiridir `[incele]`.

**Düzeltme yolunun sınırı:** düzeltme-şikâyet ancak **hukuki yorum gerektirmeyen, ilk bakışta anlaşılabilen** vergi hataları içindir; yorum gerektiren uyuşmazlık ancak süresinde açılan davada incelenebilir.  30 gün kaçtıysa düzeltmeyi "kurtarıcı" diye önerme; hatanın niteliğini `[incele]` ile işaretle.

---

## 4. Kontrol listesi

1. **Tebliğ usulü** (VUK m.93 ve devamı, m.107/A): muhatap doğru mu (tüzel kişide kanuni temsilci, tasfiye hâlinde tasfiye memuru), adres doğru mu, ilanen tebliğ şartları var mı? Usulsüz tebliğde süre öğrenme tarihinden başlatılır mı `[incele]`. 
2. **Tarh zamanaşımı**: vergi alacağının doğduğu yılı belirle; takdir komisyonuna sevk ve dönüş tarihlerini iste (durma en çok 1 yıl). 🔴 dolmuşsa en güçlü iddia.
3. **Ceza zamanaşımı** ayrı hesaplanır (m.374); usulsüzlükte 2 yıl.
4. **Dayanak rapor tebliğ edildi mi?** Takdir komisyonu kararına dayanan tarhiyatta kararın ve re'sen takdiri gerektiren inceleme raporunun sureti ihbarnameye eklenir (VUK m.35 son fıkra). Diğer hâllerde (ör. dayanılan vergi tekniği raporu) tebliğ zorunluluğu içtihada dayanır `[incele]`. 
5. **Somut tespit**: sahte belge iddiasında yalnız düzenleyici hakkındaki rapora dayanılmış mı, alıcı nezdinde somut tespit (mal hareketi, ödeme, sevk) yapılmış mı? → `kdv-gvk-kvk-temel-sorular.md` §sahte belge.
6. **Ceza türü ve katı doğru mu?** (bkz. `vergi-cezalari-ve-pismanlik.md`)
7. **Uzlaşma kapsamı**: m.359 fiilleri, m.370/b ön tespit yazısı tebliğ edilenlere kesilen ceza ve eşik altı usulsüzlük cezaları uzlaşma dışı. 
8. **Eşik altı usulsüzlük cezası**: uzlaşma yerine m.376 indirimi %50 artırımlı uygulanır; eşik tutarını madde metnindeki parantezden oku. 
9. **Tarhiyat öncesi uzlaşma** yapıldıysa: uzlaşılan husus için dava yok; sağlanamadıysa tarhiyat sonrası uzlaşma yok. 
10. **Ödeme ve faiz**: dava açılırsa kaybedilen kısım için gecikme faizi işler `[doğrula]`; oran araçta yok, RG'den.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| İhbarnameyi nasıl ve hangi tarihte aldınız? E-tebligatsa sisteme düştüğü gün? | Süre başlangıcı |
| Hangi vergi, hangi dönem; vergi aslı ve ceza ayrı ayrı ne kadar? | Zamanaşımı, yol karşılaştırması |
| İhbarnamenin ekinde vergi inceleme raporu / vergi tekniği raporu var mı? Okuyabilir miyim? | Somut tespit denetimi |
| İnceleme sırasında tarhiyat öncesi uzlaşma istediniz mi? | Uzlaşma imkânı |
| Aynı dönem için başka ihbarname, dava ya da uzlaşma var mı? | Dosya geçmişi (upstream triyaj) |
| Rapor sahte / yanıltıcı belge diyor mu? Savcılığa bildirim yapıldı mı? | m.359, ceza yargılaması bağlantısı |
| Ödeme gücünüz var mı; tecil ya da teminat düşünür müsünüz? | İndirim / tecil seçeneği |
| Şirket tasfiye hâlinde ya da sicilden silinmiş mi? | Muhatap ve kanuni temsilci sorumluluğu (VUK m.10) |

---

## İdare tarafı (vergi dairesi, uzlaşma komisyonu)

- Tarhiyatı yapan birim için kontrol: tebliğ zinciri belgelenmiş mi, zamanaşımı hesabı dosyada mı, rapor ihbarnameye eklenmiş mi, ceza katı ve m.344 son fıkra artırımı doğru mu?
- Uzlaşma komisyonu üyesi için: 7524 sonrası komisyon vergi aslını müzakere edemez; tutanak yalnız ceza miktarlarını içerir. Geçiş kapsamındaki eski dosyaları (geçici m.35) ayrı listele.
- İdarenin dava riskini çıkarırken mükellef lehine Danıştay/VDDK kararlarını da göster; tek taraflı rapor yazma.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "213"  law_type: "Kanun"  article_no: "114" | "374" | "376" | "ek 1" | "ek 7" | "ek 9" | "ek 11"
legal_get_statute_article  law_no: "2577"  article_no: "7" | "27"
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2024/08/20240802-2.htm"  offset: 14000   # 7524 m.14-16
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2026/07/20260701-1.htm"  offset: 6000    # 7587 m.9 (107/A)
legal_search_cases  mahkeme: "danistay"  sorgu: "<olay: ör. e-tebligatla tebliğ edilen ihbarnamede dava süresi>"  tarih_baslangic: "<son 3 yıl>"
legal_get_case_document  belge_id: "<seçilen karar>"
legal_check_holiday  tarih: "<son gün>"
```

---

## Çıktı iskeleti

```markdown
## İhbarname değerlendirmesi — [vergi türü / dönem] — tebliğ [tarih]

### Sonuç
[Önerilen yol + son gün + tek cümle neden]

### Süre tablosu
| İşlem | Başlangıç | Süre | Son gün | Dayanak | Durum |
| Dava | | 30 gün | | 2577 m.7 | |
| Uzlaşma talebi (yalnız ceza) | | 30 gün | | VUK ek m.1 | |
| m.376 indirim | | 30 gün | | VUK m.376 | |

### Seçenekler
| Yol | Vergi aslı | Ceza | Dava hakkı | Not |

### Bulgular (tebliğ, zamanaşımı, rapor, ceza)
### Eksik bilgi
```

---

## Sık hatalar

- 🔴 7524 sonrası dosyada vergi aslı için uzlaşma önermek.
- 🔴 E-tebligatta süreyi iletim gününden başlatmak (beşinci günün sonu esas).
- 🔴 m.376 başvurusu yapıp sonra dava açmak.
- 🟠 Yorum farkını düzeltme-şikâyet yoluyla çözmeye çalışmak (VDDK 2024/883).
- 🟠 Ceza zamanaşımını vergiyle aynı sanmak (usulsüzlükte 2 yıl).
- 🟡 Takdir komisyonu durmasını 1 yıldan uzun hesaplamak.

---

