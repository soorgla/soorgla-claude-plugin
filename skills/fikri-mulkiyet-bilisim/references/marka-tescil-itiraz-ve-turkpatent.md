# Marka tescili, ön araştırma ve TÜRKPATENT süreçleri

## Ne zaman kullanılır
- "Bu adı marka olarak alabilir miyiz?", "başvurumuz bültende yayımlandı, itiraz geldi", "bizim markamıza benzeyen bir başvuru yayımlandı", "markamız reddedildi", "YİDK kararına dava açalım mı", "rakibin markası yıllardır kullanılmıyor, iptal ettirebilir miyiz", "yenileme süresini kaçırdık".
- TÜRKPATENT önündeki bütün marka işlemleri: başvuru, mutlak ret incelemesi, üçüncü kişi görüşü, yayıma itiraz, karara itiraz, YİDK, yenileme, iptal talebi.

**Kapsam dışı:** Piyasadaki kullanım nedeniyle tecavüz ve mahkemede hükümsüzlük → `marka-tecavuz-ve-hukumsuzluk.md`. Tescilsiz işaretin haksız rekabetle korunması → `../../sirketler-ticaret/references/haksiz-rekabet.md`.

Upstream `clearance` becerisinin "ilk geçiş, görüş değil" kuralı ve benzer marka ailesi taraması uyarlandı. ABD'ye özgü çoklu faktör testleri (du Pont, Polaroid) aktarılmadı; Türk ölçütü SMK m.6/1 "ilişkilendirilme ihtimali de dâhil karıştırılma ihtimali"dir.

---

## Süre tablosu

| İşlem | Başlangıç | Süre | Dayanak | Not |
|---|---|---|---|---|
| Yayıma itiraz | Başvurunun Bülten'de yayımı | 2 ay | SMK m.18/1 | Gerekçe ve **ücret** aynı süre içinde; gerekçe süresinde verilmezse itiraz yapılmamış sayılır (m.18/2)  |
| Kurum kararına itiraz (YİDK'ye) | Kararın bildirimi | 2 ay | SMK m.20/2 | Süreden sonra gerekçe değiştirilemez, yeni gerekçe eklenemez  |
| YİDK nihai kararına karşı dava | Bildirim | 2 ay | SMK m.156/2 (görev ve yetki: Ankara FSHHM) | Süre SMK metninde bulunamadı; 2 ay Yargıtay 11. HD E.2024/5852 K.2025/3511 ile onanan ilk derece gerekçesinde; YİDK kararı olmadan dava açılamaz `[incele]`   |
| İptal talebine cevap (marka sahibi) | Talebin tebliği | 1 ay (+ talep üzerine 1 aya kadar ek süre) | SMK m.26/7 | Kurum dosya üzerinden karar verir  |
| Yenileme | Koruma süresinin bitiminden önceki 6 ay; ek ücretle bitimden sonraki 6 ay | — | SMK m.23/2 | Koruma başvuru tarihinden 10 yıl, 10'ar yıllık dönemler  |
| Yenilenmeyen markaya karşı başvuru | Koruma süresinin sona ermesi | 2 yıl içinde yapılan aynı/benzer başvuruya itiraz | SMK m.6/8 | Eski sahip bu 2 yılda markayı kullanmış olmalı  |

`legal_calculate_deadline` bu süreleri tanımıyor; elle hesapla, `legal_check_holiday` ile kontrol et, `[doğrula]`. Ücret tutarları için güncel TÜRKPATENT ücret tarifesi tebliği (RG).

---

## Kontrol listesi — ön araştırma ("bu adı alabilir miyiz?")

Bu bir **ilk geçiştir, tescil edilebilirlik görüşü değildir.** soorgla'da marka sicili yok; TÜRKPATENT araştırma çıktısını kullanıcıdan iste ya da web araması yap ve `[web araması — doğrulayın]` etiketle. Araştırma yapılmadıysa "benzer marka bulunamadı" yazma, "araştırma yapılmadı" yaz.

1. **Mutlak ret (SMK m.5):** ayırt edicilikten yoksun mu, mal/hizmetin türünü, kalitesini, coğrafi kaynağını tanımlayan (tasviri) bir işaret mi, ticarette ortak kullanılan bir ad mı, halkı yanıltıcı mı? Tasviri işaret kullanımla ayırt edicilik kazanmışsa tescil edilebilir `[incele]`. 
2. **Nispi ret (SMK m.6):** önceki tescil/başvuru ile aynılık-benzerlik + mal/hizmet aynılığı-benzerliği → karıştırılma ihtimali (m.6/1); ticari vekil (m.6/2); tescilsiz ama kullanımla hak kazanılmış işaret (m.6/3); Paris 6 mükerrer tanınmış marka (m.6/4); tanınmışlık nedeniyle haksız yarar, itibar zararı ya da ayırt ediciliğin zedelenmesi — mal/hizmet farklı olsa bile (m.6/5); başkasının adı, unvanı, fotoğrafı, telif hakkı (m.6/6); kötü niyetli başvuru (m.6/9).  Nispi nedenler **yalnız itiraz üzerine** uygulanır; Kurum resen bakmaz.
3. **Benzer marka ailesi taraması** (upstream `clearance`): aynı kök, fonetik ikizler (harf değişimi, okunuş), anlamsal eşdeğer ve çeviri, "+jenerik ek" varyantları, aynı ürün kategorisindeki yerleşik adlar. Tek isim aramasıyla yetinme.
4. **Sınıf seçimi:** Nis sınıflandırması güncel tebliğe göre (TÜRKPATENT 2026/2, RG 26.02.2026); alt grupların benzerliği sınıf numarasından değil emtia tebliğinden değerlendirilir `[incele]`. 
5. **Ticaret unvanı ve alan adı** çakışması (TTK m.50 vd.; haksız rekabet yönü `sirketler-ticaret`).
6. **Yurt dışı koruma:** Madrid Protokolü yolu (SMK m.14) `[incele]`.

Çıktı: risk düzeyi (🟢/🟡/🟠/🔴) ve "karıştırılmaz" değil "şu faktörler riski artırıyor/azaltıyor".

## Kontrol listesi — yayıma itiraz (itiraz eden)

- [ ] Yayım tarihi ve 2 aylık son gün; ücret ödendi ve dekontu sunuldu mu?
- [ ] Dayanak hak: tescilli marka, önceki başvuru, tanınmış marka, tescilsiz kullanım, unvan, telif. Her biri için delil (kullanım, tanınmışlık belgeleri).
- [ ] Dayanak marka itiraz edilen başvurunun tarihinde **5 yıldan eskiyse**, başvuru sahibi **kullanım ispatı** isteyebilir: önceki 5 yılda Türkiye'de ciddi kullanım ya da haklı sebep ispatlanmazsa itiraz reddedilir; kısmi kullanımda yalnız o mallar esas alınır (SMK m.19/2). Kullanım delilini itirazla birlikte hazırla. 
- [ ] Kısmi ret talebi: yalnız çakışan mal/hizmetler (m.19/3).
- [ ] Uzlaşma: Kurum tarafları uzlaşmaya teşvik edebilir; 6325 uygulanır (m.19/4). Birlikte var olma (coexistence) anlaşmasında rekabet riskini işaretle → `ihtarname-ve-uyusmazlik-stratejisi.md`.

## Kontrol listesi — itiraza cevap (başvuru sahibi)

- [ ] Dayanak marka 5 yılı doldurmuş mu → kullanım ispatı talep et (m.19/2).
- [ ] Mal/hizmet listesini daraltma (kısmi geri çekme) ile çakışmayı gidermek mümkün mü?
- [ ] Kötü niyet iddiasına karşı: işaretin seçilme gerekçesi, önceki kullanım, sektörde bilinirlik.
- [ ] Ret kararı gelirse 2 ay içinde YİDK'ye itiraz (m.20).

## Kontrol listesi — kullanmama nedeniyle iptal (10.01.2024'ten beri Kurumda)

SMK m.26 yayımdan 7 yıl sonra yürürlüğe girdi; iptal talebi **TÜRKPATENT'e** yapılır. O tarihte mahkemede görülmekte olan iptal davaları mahkemece sonuçlandırılır (geçici m.4/2).  Eski YAML'daki "iptal davası açılır" ifadesi 10.01.2024 sonrası için yanlış.

- [ ] İptal hâli: m.9/1 (tescilden itibaren 5 yıl kullanmama ya da 5 yıl kesinti, haklı sebep yok), yaygın ad hâline gelme, yanıltıcı kullanım, garanti/ortak marka şartnamesine aykırılık (m.26/1).
- [ ] **Talep öncesi 3 ay kuralı:** iptal talebinde bulunulacağı düşünülerek başlatılan kullanım, talepten önceki 3 ay içindeyse dikkate alınmaz (m.26/4). Karşı tarafa önceden ihtar göndermek bu yüzden riskli `[incele]`.
- [ ] 5 yılın dolması ile talep arasında ciddi kullanım başlamışsa talep reddedilir (m.26/4).
- [ ] Kısmi iptal: yalnız kullanılmayan mal/hizmetler (m.26/5).
- [ ] Talep, talep tarihinde sicilde kayıtlı sahibe karşı (m.26/3).
- [ ] Kullanım delili (marka sahibi): fatura, katalog, reklam, internet satışları; tescil kapsamındaki mallar için; devreden şirketin kullanımı da hesaba katılabilir (bkz. 11. HD E.2025/4074 — bilirkişi, devir öncesi stok ekstrelerini ve devir sonrası defterleri birlikte değerlendirdi).  `[incele]`
- [ ] İptalin etkisi: talep tarihinden; talep üzerine daha önceki tarih (m.27). 
- [ ] Kurum iptal kararına itiraz → YİDK (m.20), sonra Ankara FSHHM.

## YİDK kararına karşı dava

- Görevli ve yetkili: **Ankara Fikri ve Sınai Haklar Hukuk Mahkemesi**; Kurum davalı (m.156/2).  Bu adli yargı davasıdır (idare mahkemesi değil).
- Mahkeme, YİDK karar tarihindeki hukuki durumu esas alır; ancak itiraza dayanak marka sonradan hükümsüz kılınırsa (m.27/1) bu gözetilir.  `[çekildi ama desteği doğrulayın]`
- Aynı davada YİDK kararının iptali ile itiraz edilen markanın hükümsüzlüğü birlikte istenebilir (Ankara BAM 20. HD E.2023/225 K.2025/523 "Kurum kararının iptali, marka hükümsüzlüğü") `[incele]`. 
- İstinaf: Ankara BAM ilgili hukuk dairesi; temyiz: Yargıtay (daireyi BGK'den teyit et).

---

## İdare (TÜRKPATENT) tarafı

Kurum uzmanı ya da YİDK raportörü bakışı (eski YAML'larda bureaucrat dosyası yok; madde metninden kuruldu):
- Nispi ret nedenlerini **resen** uygulama (m.6 "itiraz üzerine").
- Kullanım ispatı talebinde 5 yıl hesabını başvuru/rüçhan tarihine göre yap (m.19/2).
- Süresinde sunulmayan gerekçeyi dikkate alma (m.18/2, m.20/2); bu, davada iptal sebebi yapılır.
- Kısmi ret/iptal kararında marka örneğini değiştirme (m.26/5).
- Gerekçe: karıştırılma ihtimali değerlendirmesinde görsel, işitsel, kavramsal benzerlik ve mal/hizmet ilişkisini ayrı ayrı yaz; davada en sık bozma nedeni gerekçe eksikliğidir `[incele]`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Başvuru/tescil numarası, sınıflar, başvuru ve rüçhan tarihi? Sicil çıktısı var mı? | Hak ve tarih sırası |
| Bülten yayım tarihi ya da kararın bildirim tarihi (e-bildirim mi)? | Süre |
| İşaret ne zamandan beri, hangi mallarda, nerede kullanılıyor? Fatura, katalog, internet kaydı? | Kullanım ispatı, m.6/3 |
| Karşı tarafla önceki ilişki (bayi, distribütör, eski ortak, eski çalışan)? | m.6/2, kötü niyet |
| Karşı tarafa ihtar gönderildi mi, ne zaman? | m.26/4 üç ay kuralı |
| Yurt dışında tescil var mı? | Tanınmışlık, Madrid |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6769"  law_type: "Kanun"  article_no: "5" | "6" | "9" | "18" | "19" | "20" | "21" | "23" | "26" | "27" | "156" | "geçici 4"
legal_search_official_gazette  query: "Türk Patent ve Marka Kurumunca Uygulanacak Ücret Tarifesi"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "Marka Tescil Başvurularına Ait Mal ve Hizmetlerin Sınıflandırılmasına İlişkin Tebliğ"  search_in: "title"  sort_by: "date_desc"
legal_search_statute_semantic  sorgu: "<konu> Sınai Mülkiyet Kanununun Uygulanmasına Dair Yönetmelik"  mevzuat_tur: "kurum_yonetmeligi"
legal_search_cases  mahkeme: "yargitay"  daire: "11. Hukuk Dairesi"  sorgu: "<YİDK kararının iptali / kullanmama iptali / kötü niyetli başvuru>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "bam"  sorgu: "Ankara Bölge Adliye Mahkemesi Kurum kararının iptali <konu>"
legal_search_admin_guidance  sorgu: "<konu>"  kurum: "Türk Patent ve Marka Kurumu"     # 0 döner; sonucu nota yaz
```

---

## Çıktı iskeleti

```markdown
## Marka [ön araştırma / itiraz / itiraza cevap / iptal talebi] — [işaret], sınıf [..]
| Önceki hak | Sahip | Tarih | Sınıf | Benzerlik (görsel/işitsel/kavramsal) | Mal/hizmet ilişkisi | Risk |
### Süre tablosu
### Faktörler (lehe / aleyhe)
### Öneri: [başvur / daralt / itiraz et / kullanım delili topla / iptal talep et] — [incele]

### İtiraz dilekçesi iskeleti (TÜRKPATENT)
TÜRK PATENT VE MARKA KURUMU — Marka Dairesi Başkanlığına
İtiraz eden: [___] (vekil: [___])  |  Başvuru no: [___]  |  Bülten no/tarih: [___]
Dayanak haklar: [tescil no, sınıf, tarih] …
Gerekçeler: 1) SMK m.6/1 … 2) m.6/5 … 3) m.6/9 …
Deliller: [kullanım, tanınmışlık]
Talep: Başvurunun [tüm / şu mal-hizmetler] bakımından reddi.  Ücret dekontu: ekte
```

---

## Sık hatalar

- 🔴 İtiraz gerekçesini ya da ücret dekontunu 2 ay içinde sunmamak (itiraz yapılmamış sayılır).
- 🔴 10.01.2024 sonrasında kullanmama iptali için mahkemede dava açmak (talep Kuruma).
- 🟠 5 yıldan eski dayanak markayla itirazda kullanım delilini hazırlamamak.
- 🟠 İptal talebinden önce karşı tarafa ihtar gönderip kullanımı "uyandırmak" (m.26/4 üç ay kuralı yalnız talepten önceki 3 ayı kapsar).
- 🟠 YİDK kararına karşı davayı idare mahkemesinde açmak.
- 🟡 "Araştırmada benzer marka çıkmadı" demek; soorgla'da sicil yok.

---

