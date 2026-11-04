# Memur disiplin soruşturması, cezalar ve itiraz

## Ne zaman kullanılır
- Memura savunma istem yazısı geldi, ceza verildi ya da itiraz/dava yolu soruluyor (memur / avukat tarafı).
- Disiplin amiri bir olayı öğrendi; soruşturma açılacak, muhakkik atanacak, savunma istenecek, ceza tayin edilecek (idare tarafı).
- Aday memurun disiplin cezası nedeniyle ilişiğinin kesilmesi; cezanın özlük dosyasından silinmesi.

Statü kontrolü: 657'ye tabi memur ve Devlet Memurları Disiplin Yönetmeliği kapsamındaki personel. Sözleşmeli personelde disiplin karşılığı "sözleşme feshi"dir → `sozlesmeli-personel-ve-sendika.md`. Özel kanunlu personelde (emniyet 7068, akademisyen 2547, hâkim/savcı 2802) özel kanun hükmü önce gelir (657 m.125 son fıkralar "Özel kanunların disiplin suçları ve cezalarına ilişkin hükümleri saklıdır"). 

**Upstream uyarlaması:** `employment-legal/skills/internal-investigation`'daki "kaynak kapsama listesi" (hangi delil toplandı, hangisi eksik) ve "emsal karşılaştırması" fikirleri idare tarafı akışına alındı. ABD'ye özgü privilege, Garrity ve Weingarten kuralları alınmadı; yerine Anayasa m.129/2 savunma güvencesi ve 657 m.130 kondu.

---

## 2026 değişikliği — 7573 sayılı Kanun (RG 29.01.2026)

- **m.127/2 yeniden yazıldı:** iki yıllık ceza zamanaşımı korunuyor; ek olarak disiplin cezası **yargı kararıyla iptal edilirse**, kararın idareye ulaştığı tarihten itibaren kalan zamanaşımı süresi içinde, süre dolmuş ya da altı aydan az kalmışsa **en geç altı ay içinde** karar gerekçesi dikkate alınarak yeniden ceza verilebilir.  Usulden (savunma, yetki) iptal edilen ceza bu yolla yeniden tesis edilebilir; memur tarafında "iptal = dosya kapandı" beklentisini düzelt.
- **m.56 değişti, m.57 kaldırıldı:** aday memurun adaylık süresinde birden fazla uyarma ve/veya kınama ya da bir aylıktan kesme veya kademe ilerlemesinin durdurulması cezası alması ilişik kesme sebebidir; ilişiği kesilen (sağlık nedenleri hariç) üç yıl memurluğa alınmaz.  Ayrıntı → `atama-nakil-ve-ozluk.md`.
- Yürürlük: yayımı tarihinde (29.01.2026).  Geçiş hükmü yok; 29.01.2026 öncesi iptal edilen cezalara uygulanıp uygulanmayacağı yerleşik içtihatla henüz netleşmemiş olabilir — kesin bilgi gibi yazma. Her dosyada `legal_search_cases` (`mahkeme: "danistay"` ve `"bam"`, `tarih_baslangic: "2026-01-29"`, `sorgu: "iptal edilen disiplin cezasının 657 m.127 uyarınca yeniden verilmesi"`) ile ara; karar bulamazsan `[ARAŞTIRMA GEREKLİ: 7573 m.3'ün önceki iptallere uygulanması]` yaz ve iki ihtimali (uygulanır / uygulanmaz) ayrı ayrı göster. 

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Kimin süresi / sonucu |
|---|---|---|---|
| Soruşturmaya başlama: **1 ay** (uyarma, kınama, aylıktan kesme, kademe ilerlemesinin durdurulması) | Fiilin disiplin amirince öğrenilmesi | 657 m.127/1-a  | İdare. Kaçarsa ceza verme yetkisi zamanaşımına uğrar 🔴 |
| Soruşturmaya (kovuşturmaya) başlama: **6 ay** (memurluktan çıkarma) | Öğrenme | 657 m.127/1-b  | İdare |
| Ceza verme zamanaşımı: **2 yıl** | Fiilin işlendiği tarih | 657 m.127/2  | İdare. İptal sonrası yeniden tesiste kalan süre / en geç 6 ay (7573) |
| Savunma süresi: **en az 7 gün** | Savunma istem yazısının tebliği | 657 m.130/2; Disiplin Yönetmeliği m.30/3  | Memur. Süresinde savunma vermeyen savunma hakkından vazgeçmiş sayılır |
| Disiplin kurulu cezayı reddederse amirin başka ceza vermesi: **15 gün** | Ret kararı | 657 m.126/3  | İdare |
| İtiraz: **7 gün** | Cezanın ilgiliye tebliği | 657 m.135/2  | Memur. Süresinde itiraz edilmeyen ceza kesinleşir |
| İtiraz merciinin karar süresi: **30 gün** | Dilekçe ve eklerin mercie intikali | 657 m.135/3  | İtiraz mercii |
| İptal davası: **60 gün** | Cezanın (itiraz edildiyse itiraz kararının) yazılı bildirimi | 2577 m.7/1; 657 m.135/5 "idari yargı yoluna başvurulabilir"  | Memur. İtiraz ile dava süresi ilişkisi → `personel-davasi-usul-ve-sureler.md` `[incele]` |
| Cezanın özlük dosyasından silinmesi için başvuru: uyarma/kınama **5 yıl**, diğerleri **10 yıl** | Cezanın uygulanması | 657 m.133  | Memur; çıkarma cezası silinmez; kademe durdurmada disiplin kurulu mütalaası |

`legal_calculate_deadline` bu süreleri tanımıyor; elle hesapla, `legal_check_holiday`, `[doğrula]`.

---

## Cezalar, yetkili merci ve itiraz yolu

| Ceza (m.125) | İçeriği | Veren (m.126) | İtiraz mercii (m.135) |
|---|---|---|---|
| A. Uyarma | Yazıyla daha dikkatli olma bildirimi | Disiplin amiri | Disiplin kurulu |
| B. Kınama | Yazıyla kusurlu olduğunun bildirimi | Disiplin amiri | Disiplin kurulu |
| C. Aylıktan kesme | Brüt aylıktan 1/30–1/8 kesinti | Disiplin amiri | Disiplin kurulu |
| D. Kademe ilerlemesinin durdurulması | 1–3 yıl | Disiplin kurulu kararı alınarak atamaya yetkili amir (il disiplin kurulu kararına dayananlarda vali) | Yüksek disiplin kurulu |
| E. Devlet memurluğundan çıkarma | Bir daha memur olamamak üzere | Yüksek disiplin kurulu kararı | İtiraz yolu yok → doğrudan dava |

**Eski YAML düzeltmesi:** `disciplinary_investigation.yaml` "uyarma ve kınamaya karşı disiplin kuruluna, diğerlerine karşı yüksek disiplin kuruluna" diyordu. Doğrusu: **aylıktan kesme de disiplin kuruluna**, yalnız kademe ilerlemesinin durdurulması yüksek disiplin kuruluna gider; çıkarma cezasına itiraz yolu yoktur. 

**Yargı denetimi:** disiplin kararları yargı denetimi dışında bırakılamaz (Anayasa m.129/3, 2010 değişikliği); uyarma ve kınama dahil her cezaya dava açılabilir.  Uyarma cezasına karşı dava idare mahkemesinde **tek hâkimle** görülür (7589 ile 2576 m.7/1-d); tek hâkimle görülen davada istinaf sonrası temyiz yolu kapalıdır (2577 m.46/2-a). 

**Ceza tayininde dikkat:**
- **Tekerrür:** silinme süresi içinde aynı fiilin tekrarında bir derece ağır ceza; aynı derecede cezayı gerektiren ayrı fiillerde üçüncü uygulamada bir derece ağır ceza. 
- **Bir derece hafif ceza:** geçmiş hizmetleri olumlu olan ve **ödül veya başarı belgesi** almış memura bir derece hafif ceza "uygulanabilir" — takdir yetkisidir, zorunluluk değildir. Eski YAML bunu "Md. 125/E alt ceza" diye anıyordu; 125/E çıkarma cezasıdır, hüküm maddenin son fıkralarındadır. Uygulanmadıysa gerekçe yazılmış mı, eşitlik ilkesine uygun mu `[incele]`. 
- **Kıyas:** sayılan fiillere nitelik ve ağırlık bakımından benzer eylemlere aynı neviden ceza verilir; kıyasla ceza verilmişse benzerlik gerekçelendirilmiş mi `[incele]`. 
- **Son kademedeki memur:** kademe ilerlemesinin durdurulmasını gerektiren hâlde brüt aylığın 1/4–1/2'si kesilir, tekerrüründe görevine son verilir. 
- **Ceza yargılamasıyla ilişki:** disiplin kovuşturmasının yapılmış olması ceza kovuşturmasına engel değildir.  m.131'e göre ceza kovuşturmasının başlamış olması disiplin kovuşturmasını **geciktiremez**; memurun mahkûm olması ya da olmaması disiplin cezasının uygulanmasına **engel olmaz**. Beraat kararındaki maddi olgu tespitlerinin disiplin cezasına etkisi içtihatla belirlenir `[incele]`. 

---

## Kontrol listesi — memur / avukat tarafı (ceza verildi ya da savunma istendi)

1. **Statü ve mevzuat:** 657 mi, özel kanun mu? Hangi disiplin yönetmeliği?
2. **Zamanaşımı (m.127):** disiplin amiri olayı ne zaman öğrendi, soruşturma oluru hangi tarihte? 1 ay / 6 ay aşıldı mı? Fiil tarihinden ceza tarihine 2 yıl geçti mi? Öğrenme tarihi belgede yoksa idareden iste (dosya inceleme, 4982 bilgi edinme) 🔴.
3. **Soruşturma açıldı mı:** soruşturma yapılmadan ceza verilemez (Yönetmelik m.28). 
4. **Savunma (en sık iptal sebebi):**
   - Savunmayı **disiplin amiri** (ya da yetkili kurul) **soruşturmanın son aşamasında** mı istedi? Danıştay İDDK, muhakkikin aldığı "savunma"nın yeterli olmadığına, savunmanın soruşturma sürecinin son aşamasında yetkili disiplin amiri ya da kurulu tarafından istenmesi gerektiğine karar verdi (oyçokluğu; karşı oy muhakkikin de alabileceği görüşünde). — Danıştay İDDK E.2024/29 K.2024/57 (30.10.2024) `[soorgla]`  Bu bir **aykırılık giderme** kararıdır (2576 m.3/C); bölge idare mahkemelerini yönlendirir `[incele]`.
   - Yazıda iddialar, dayandığı deliller, fiilin hukuki nitelendirmesi ve m.125'in **hangi bent ve alt bendi** yazılı mı (Yönetmelik m.30/2)?
   - En az 7 gün süre verildi mi; "süresinde verilmezse vazgeçmiş sayılır" ihtarı var mı (m.30/4)?
   - Çıkarma cezasında YDK son savunmayı (sözlü ya da yazılı) ayrıca istedi mi (Yönetmelik m.30/6, 657 m.129)?  
5. **Yetki:** cezayı veren doğru disiplin amiri mi; kademe durdurmada disiplin kurulu kararı, çıkarmada YDK kararı var mı; kurul usulüne uygun toplandı mı (nisap, üyeler)?
6. **Sebep:** fiil sabit mi; delil var mı; tanık beyanları, belgeler? Fiil ile uygulanan bent örtüşüyor mu (ör. "kasten" unsuru gereken 125/D-n ile kusurlu davranış olan 125/B-a)?
7. **Ölçülülük ve eşitlik:** aynı olaydaki diğer personele hangi ceza verildi; bir derece hafif ceza değerlendirildi mi?
8. **İtiraz/dava süresi** — tablo; itiraz edildiyse itiraz merci kararının tarihi.
9. **Paralel ceza soruşturması:** 4483 sürecindeki durum → `gorevden-uzaklastirma-ve-4483.md`.
10. **Emsal:** son 3 yıldan en az bir Danıştay ya da BİM kararı, tam metin.

## Kontrol listesi — idare tarafı (disiplin amiri, muhakkik, personel birimi)

Amaç: iptale dayanıklı işlem. Upstream "kaynak kapsama listesi" burada uygulanır.

1. **Saat başlat:** öğrenme tarihi (ihbar, şikâyet, müfettiş raporu) ve fiil tarihi dosyanın ilk satırına; 1 ay / 6 ay / 2 yıl son günlerini yaz 🔴.
2. **Soruşturma oluru ve muhakkik görevlendirmesi:** muhakkik ilgiliden kıdemli ya da eşit mi, tarafsız mı? Muhakkik ifade alır, belge toplar ama **savunma istemez, ceza veremez** (Yönetmelik m.29). 
3. **Delil kapsama listesi:** ilgilinin ifadesi · şikâyetçi ifadesi · tanıklar · belgeler/yazışmalar · kamera ve sistem kayıtları (kişisel veri → `../../kvkk/SKILL.md`) · önceki cezalar ve sicil · aynı olaydaki diğer personel (eşitlik) · olay tarihinde yürürlükteki iç düzenleme. Her satır: toplandı / eksik / uygulanamaz.
4. **İfade alırken:** isnadı bildir; ceza soruşturması da varsa ifadenin ceza dosyasına girebileceğini söyle; zorlama ve yönlendirme yapma.
5. **Soruşturma raporu:** olay, deliller, ifade özetleri, değerlendirme, önerilen ceza ve bent; bir derece hafif ceza değerlendirmesi; tekerrür kontrolü (m.133 süreleri içinde önceki ceza).
6. **Savunma istemi:** disiplin amiri imzalı, son aşamada, m.30/2 unsurlarıyla, en az 7 gün, vazgeçme ihtarlı; tebliğ belgesini dosyaya koy. Muhakkik yazısıyla yetinme (İDDK 2024/57).
7. **Ceza kararı:** gerekçeli; bent ve alt bent; itiraz mercii ve süresi (7 gün) ile dava yolu ve süresi (60 gün) **karar metninde gösterilmeli** `[incele]` ; tebliğ.
8. **Kurul aşaması:** kademe durdurmada dosya disiplin kuruluna, çıkarmada kanaat yazısıyla YDK'ya; kurul cezayı kabul ya da reddeder, başka ceza tayin edemez; ret hâlinde amirin 15 günü var (m.126/3).
9. **Aday memur:** adaylık süresinde verilen ceza ilişik kesme sebebi olabilir (m.56, 7573) → ayrı işlem, ayrı tebliğ.
10. **İptal sonrası:** yargı kararı gelirse kalan zamanaşımı / en geç 6 ay içinde gerekçeye uygun yeni işlem (m.127/2, 7573).

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Statü | Kadronuz/unvanınız, kurumunuz, 657'ye mi özel kanuna mı tabisiniz? Aday mısınız? |
| Olay | Fiil ne, ne zaman oldu? Amir ne zaman öğrendi (ihbar/şikâyet tarihi)? |
| Belgeler | Soruşturma oluru, muhakkik görevlendirme yazısı, ifade tutanağı, savunma istem yazısı (kim imzaladı?), ceza kararı, tebliğ tarihleri |
| Savunma | Savunma verdiniz mi, ne zaman, kaç gün süre tanındı? |
| Geçmiş | Önceki disiplin cezası, ödül veya başarı belgesi var mı? |
| Paralel süreç | Aynı olay için savcılık soruşturması / 4483 ön incelemesi var mı? Görevden uzaklaştırıldınız mı? |
| İtiraz | İtiraz ettiniz mi, ne zaman, sonuç? |
| İdare tarafı | Öğrenme tarihi kesin mi? Muhakkik kim? Hangi deliller toplandı? Benzer olaylarda hangi cezalar verildi? |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "657"  law_type: "Kanun"  article_no: "125" | "126" | "127" | "130" | "133" | "135"
legal_get_statute_article  law_no: "657"  law_type: "Kanun"  article_no: "129" | "131" | "134"
legal_get_statute_article  law_no: "2709"  article_no: "129"
legal_search_statute_semantic  sorgu: "Devlet Memurları Disiplin Yönetmeliği <savunma | muhakkik | disiplin kurulu nisap>"
legal_search_official_gazette  query: "7573"  date_from: "2026-01-01"
legal_search_cases  sorgu: "<fiil> disiplin cezası savunma istem yazısı disiplin amiri iptal"  mahkeme: "danistay"  tarih_baslangic: "<3 yıl önce>"
legal_search_cases  sorgu: "<aynı>"  mahkeme: "bam"
legal_get_case_document  belge_id: "danistay:1127493100"   # İDDK E.2024/29 K.2024/57 — savunmayı disiplin amiri ister
```

Daire filtresi verme; sonuçlardaki daireyi oku (bkz. SKILL.md Adım 3).

---

## Çıktı iskeleti — değerlendirme

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Disiplin işlemi değerlendirmesi — [ceza, tarih, sayı] — [memur / idare tarafı]
### Sonuç
### Süre tablosu
| İşlem | Başlangıç | Son gün | Dayanak | Durum |
### Usul (zamanaşımı · soruşturma · savunma · yetki · kurul)
### Esas (fiil · bent · ölçülülük · eşitlik · bir derece hafif ceza)
### Emsal
### Önerilen yol
[itiraz → dava; ya da doğrudan dava; yürütmenin durdurulması gerekçesi]
```

## Çıktı iskeleti — disiplin kuruluna itiraz dilekçesi (memur)

```markdown
[TASLAK — gönderilmeden önce avukat incelemesi] (avukat değilse ORTAK-KURALLAR.md §1 kapısı)

[KURUM] DİSİPLİN KURULU BAŞKANLIĞINA  /  YÜKSEK DİSİPLİN KURULU BAŞKANLIĞINA
(… aracılığıyla)

İTİRAZ EDEN : [ad soyad, T.C. kimlik no, unvan, görev yeri]
İTİRAZ EDİLEN KARAR : [disiplin amiri], [tarih], [sayı] — [ceza], 657 m.125/[bent-alt bent]
TEBLİĞ TARİHİ : [___]

AÇIKLAMALAR:
1. Usul: [zamanaşımı / savunmanın disiplin amirince istenmemesi / m.30/2 unsurlarının eksikliği / yetki]
2. Esas: [fiilin sabit olmaması / bendin yanlışlığı / ölçülülük / bir derece hafif ceza / eşitlik]
DELİLLER: [ceza kararı, savunma istem yazısı, savunma, tanık, ödül belgeleri]
SONUÇ VE İSTEM: Cezanın kaldırılmasına, olmazsa hafifletilmesine karar verilmesini saygıyla arz ederim.
[tarih, imza]
```

## Çıktı iskeleti — savunma istem yazısı (idare)

İçerik: muhatap; soruşturma oluru tarih/sayı; **iddialar**; **dayandığı deliller**; **hukuki nitelendirme ve 657 m.125 bent/alt bent**; savunma için süre (en az 7 gün, son gün tarihiyle); "süresinde savunma verilmezse savunma hakkından vazgeçmiş sayılacağınız" ihtarı; disiplin amirinin imzası. Biçim → `../../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md`.

---

## Sık hatalar
- Savunmayı muhakkiğe istetip disiplin amirinin ayrıca istememesi (İDDK E.2024/29 K.2024/57).
- "Savunmanızı verin" deyip fiili, delili ve bendi yazmamak.
- Bir aylık soruşturma başlatma süresini müfettiş raporunun gelişinden değil olayın ilk öğrenildiği tarihten saymamak (öğrenme anının belirlenmesi `[incele]`).
- Aylıktan kesme cezasına itirazı yüksek disiplin kuruluna yapmak (merci disiplin kuruludur).
- Çıkarma cezasına "itiraz" etmeye çalışıp 60 günlük dava süresini kaçırmak.
- Usulden iptal edilen cezanın "bitti" sanılması (7573: kalan süre / en geç 6 ay içinde yeniden ceza).
- Bir derece hafif cezayı zorunlu sanmak; ya da hiç değerlendirmemek.
- Disiplin savunmasında ceza dosyasını etkileyecek kabullerde bulunmak.
- Danıştay dairesini eski YAML'dan "12. Daire" diye sabitlemek.

