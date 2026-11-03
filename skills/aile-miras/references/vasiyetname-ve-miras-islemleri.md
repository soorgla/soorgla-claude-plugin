# Vasiyetname, mirasçılık belgesi, mirasın reddi ve tereke işlemleri

**Ne zaman kullanılır:** vasiyetname hazırlanması ya da mevcut bir vasiyetnamenin geçerliliği; vasiyetnamenin iptali; mirasçılık belgesi (veraset ilamı) alınması ya da iptali; borçlu ölen kişinin mirasının reddi; tereke tespiti. Saklı payı zedeleyen vasiyet → tenkis için `mirascilik-sakli-pay-ve-tenkis.md`.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| **Mirasın reddi: 3 ay.** Yasal mirasçı için mirasbırakanın ölümünü öğrenmeden (mirasçı olduğunu sonradan öğrendiğini ispat ederse o tarihten); atanmış mirasçı için tasarrufun resmen bildiriminden | TMK 606 | Hak düşürücü. Süre geçmişse 🔴; önemli sebeple sulh hâkiminden süre uzatımı ya da yeni süre (TMK 615) `[incele]` |
| Ölüm tarihinde mirasbırakanın **ödemeden aczi açıkça belli ya da resmen tespit edilmişse** miras reddedilmiş sayılır (hükmen ret) | TMK 605/2 | Süreye bağlı değildir `[doğrula]`; dava yoluyla tespit istenir |
| Vasiyetnamenin (ölüme bağlı tasarrufun) iptali: iptal sebebini ve hak sahibi olduğunu **öğrenmeden 1 yıl**; her hâlde vasiyetnamede açılma tarihinden **iyiniyetli davalıya 10 yıl, kötüniyetliye 20 yıl** | TMK 559/1 | Hükümsüzlük **def'i** her zaman ileri sürülebilir |
| Ölüme bağlı tasarrufa itiraz (mirasçılık belgesi bakımından): bildirimden **1 ay** | TMK 598/2 | İtiraz yoksa atanmış mirasçıya belge verilir; iptal dava hakkı saklıdır |
| Mirasçılık belgesinin geçersizliği **her zaman** ileri sürülebilir | TMK 598/3 | Belgenin iptali davası süreye bağlı değildir |

`legal_calculate_deadline` bu süreleri tanımaz ("tmk_mirasin_reddi" → Kural bulunamadı). Elle hesapla, `legal_check_holiday` ile kontrol et, `[doğrula]` yaz.

---

## Kontrol listesi

### 1. Vasiyetname şekli (TMK 531 vd.)
Üç şekil vardır: **resmî**, **el yazılı**, **sözlü**.

| Şekil | Zorunlu unsurlar | Dayanak |
|---|---|---|
| Resmî | **İki tanığın** katılımıyla resmî memur (sulh hâkimi, noter ya da kanunla yetkili görevli) düzenler; okuma, imza ve tanık beyanı aşamaları | TMK 532 |
| El yazılı | Yapıldığı **yıl, ay ve gün** gösterilerek **başından sonuna kadar** mirasbırakanın el yazısıyla yazılıp **imzalanması**; notere, sulh hâkimine ya da yetkili memura saklanmak üzere bırakılabilir | TMK 538 |
| Sözlü | Yalnız **olağanüstü durumlarda** (yakın ölüm tehlikesi, ulaşımın kesilmesi, hastalık, savaş) resmî ya da el yazılı vasiyet yapılamıyorsa; son arzular **iki tanığa** anlatılır; resmî vasiyetnamedeki tanık yasakları (okur-yazarlık dışında) burada da geçerli | TMK 539 Tanıklardan biri arzuları hemen yazıp ikisi birlikte vakit geçirmeden sulh ya da asliye mahkemesine verir (m.540); başka şekilde vasiyet yapma olanağı doğduktan **1 ay** sonra sözlü vasiyet hükümden düşer (m.541). |

- Bilgisayar çıktısı, kısmen el yazısı ya da tarihsiz el yazılı vasiyetname: şekil eksikliği 🔴 (iptal sebebi, TMK 557/4). Tarihteki küçük eksikliklerin sonucu `[incele]`.
- Vasiyetname hazırlatmak isteyen kullanıcıya: saklı payları hesapla (aşan kısım tenkise açıktır); en güvenli yolun resmî vasiyetname olduğunu söyle; el yazılı seçilirse metni kendisinin elle yazacağını, tarih atıp imzalayacağını açıkla.
- Miras sözleşmesi resmî vasiyetname şeklinde yapılır; taraflar arzularını memura aynı anda bildirir, memur ve iki tanık önünde imzalar.

### 2. Vasiyetnamenin iptali (TMK 557)
İptal sebepleri:
1. tasarruf ehliyetinin yokluğu (ayırt etme gücü; sağlık raporu, Adli Tıp);
2. yanılma, aldatma, korkutma ya da zorlama;
3. içeriğin, koşulların ya da yüklemelerin hukuka veya ahlaka aykırılığı;
4. şekle aykırılık.

- Süreleri 559'a göre hesapla (öğrenme 1 yıl; 10/20 yıl).
- Temyiz: miras hukuku dairesi (2026'da 7. HD) `[doğrula]`.

### 3. Vasiyetnamenin açılması
- Ölümden sonra vasiyetnameyi bulan ya da saklayan kişi, geçerli olup olmadığına bakmadan, ölümü öğrenir öğrenmez sulh hâkimine teslim etmelidir (yoksa zarardan sorumlu); hâkim teslimden itibaren **1 ay** içinde açar, ilgililere okur (TMK 595-596).

### 4. Mirasçılık belgesi (veraset ilamı)
- **Yasal mirasçılar** için belge **sulh mahkemesince ya da noterlikçe** verilir.
- **Atanmış mirasçı ya da vasiyet alacaklısı** için belgeyi yalnız **sulh mahkemesi** verir; bildirimden itibaren 1 ay içinde itiraz edilmemiş olmalıdır.
- Noterin belge **veremediği** durumlar: nüfus kayıtlarının yetersiz olması, talebin yabancıdan gelmesi, bilirkişi incelemesi ya da tanık dinlenmesi gerekmesi, talebin yabancılık unsuru taşıması gibi yargılama gerektiren hâller. Noter yalnız nüfus kayıtlarına göre **yasal** mirasçılığı tespit eder; atanmış mirasçı/vasiyet alacaklısı için yol sulh mahkemesidir (TMK 598/2). Noterin verdiği belgeye karşı yetkili sulh hukuk mahkemesine itiraz edilebilir. Yetkinin kaynağı 1512 m.71/A. Yönetmelik 2011 tarihli; sonraki değişiklikleri `legal_search_official_gazette` (`query: "Mirasçılık Belgesi"`, `search_in: "title"`) ile kontrol et.
- Mirasçılık belgesinin geçersizliği her zaman ileri sürülebilir (598/3). Belgede eksik ya da fazla mirasçı varsa iptal davası açılır.
- Belge nüfus kaydına dayanır: evlilik dışı çocuk, evlatlık, gaiplik kararı varsa kayıtları kontrol et.

### 5. Mirasın reddi
- **Yer ve şekil:** sulh mahkemesine sözlü ya da yazılı beyan; ret **kayıtsız ve şartsız** olmalıdır; süresinde yapılan ret mirasın açıldığı yerin sulh mahkemesince kütüğe yazılır. Ret noterde yapılamaz `[doğrula]`.
- **Süre:** 3 ay (TMK 606).
- **Reddi engelleyen davranışlar:** süre içinde terekeye ait işleri olağan yönetim dışında yürütmek, tereke mallarını gizlemek ya da kendine mal edinmek → mirasçı artık mirası reddedemez (TMK 610/2) 🟠. Zamanaşımını kesmek için dava açmak ya da takip yapmak ret hakkını kaldırmaz (610/3). Kullanıcıya "ret beyanına kadar tereke mallarını satmayın, araçları devretmeyin, hesaplardan para çekmeyin" uyarısı ver.
- **Hükmen ret (605/2):** ölüm tarihinde ödemeden aciz açıkça belli ise; tespit davası. Davalı tereke alacaklıları ya da diğer mirasçılar `[incele]`.
- Retten sonra reddedenin payı, miras açıldığında o sağ değilmiş gibi hak sahiplerine (kural olarak altsoyuna) geçer (m.611); altsoyun tamamı reddederse pay sağ kalan eşe geçer (m.613); en yakın yasal mirasçıların tamamı reddederse tereke sulh mahkemesince iflas hükümlerine göre tasfiye edilir (m.612). Altsoyun da ayrıca ret beyanında bulunması gerekip gerekmediğini kontrol et.
- Borçlu mirasbırakanın alacaklıları icra takibine geçtiyse → `icra-iflas` (`../../icra-iflas/SKILL.md`). Vatandaşın kendi verebileceği basit itiraz → [../../vatandas-basvurulari/references/icra-itirazi.md](../../vatandas-basvurulari/references/icra-itirazi.md).
- Alternatif yollar: resmî defter tutulması (TMK 619 vd.; ret usulüyle **1 ay** içinde sulh hâkiminden istenir, bir mirasçının istemi diğerleri için de etkilidir), resmî tasfiye. Defterin ret süresine etkisi `[incele]`.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4721" article_no: "531" | "532" | "533" | "538" | "539" | "545" | "557" | "559" | "595" | "596" | "598" | "605" | "606" | "609" | "610" | "615" | "619"
legal_search_statute_semantic sorgu: "noterlikçe mirasçılık belgesi düzenlenmesi" mevzuat_no: "1512"
legal_search_statute_semantic sorgu: "mirasçılık belgesi yönetmelik noter" mevzuat_tur: "cb_yonetmeligi"
legal_search_cases mahkeme: "yargitay" daire: "7. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. el yazılı vasiyetnamede tarihin eksik olması şekil eksikliği iptal>"
legal_search_cases mahkeme: "yargitay" sorgu: "<mirasın hükmen reddi ödemeden aciz tespit>"
legal_get_case_document belge_id: "<seçilen karar>"
legal_check_holiday tarih: "<3 aylık sürenin son günü>"
```
Ek kaynak: `mevzuat_no: 1512` (Noterlik Kanunu, vasiyetname şekilleri) → yukarıdaki semantik arama.

---

## Görüşme soruları

1. Mirasbırakanın ölüm tarihi ve ölümü öğrenme tarihi?
2. Son yerleşim yeri (yetkili sulh mahkemesi)?
3. Vasiyetname var mı? Türü, tarihi, kimde, açıldı mı, size ne zaman bildirildi?
4. Mirasbırakanın sağlık durumu (vasiyetname tarihinde ayırt etme gücü)?
5. Mirasbırakanın borçları biliniyor mu? İcra takibi, banka kredisi, kefalet?
6. Ölümden sonra tereke mallarıyla ilgili bir işlem yaptınız mı (araç satışı, hesap kullanımı)?
7. Mirasçılık belgesi alındı mı, hangi makamdan?
8. Diğer mirasçılar kimler, reddetmeyi düşünüyorlar mı?

## Çıktı iskeleti

```markdown
## Miras işlemi değerlendirmesi: [mirasbırakan] — [tarih]
### Sonuç
### Kritik süreler
| İşlem | Başlangıç | Son gün | Dayanak | Durum |
### Vasiyetname şekil kontrolü (varsa)
| Unsur | Var/Yok | Not |
### Mirasın reddi taslağı (gerekirse — TASLAK)
- Merci: [mirasın açıldığı yer] Sulh Hukuk Mahkemesi
- Beyan: kayıtsız ve şartsız ret
- Ekler: ölüm belgesi, nüfus kaydı, [___]
### Mirasçılık belgesi yolu (noter / sulh)
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Mirasın reddini notere yaptırmaya çalışmak (merci sulh mahkemesi).
- 3 aylık sürenin başlangıcını ölüm tarihi sanmak (öğrenme tarihinden işler).
- Ret süresi içinde tereke malını kullanıp reddi geçersiz kılmak.
- Bilgisayarla yazılmış ve imzalanmış metni el yazılı vasiyetname saymak.
- Vasiyetnameyle atanmış mirasçı için noterden mirasçılık belgesi istemek.
- İptal davasının 1 yıllık süresini vasiyetnamenin açılmasından saymak (öğrenmeden işler).

---
