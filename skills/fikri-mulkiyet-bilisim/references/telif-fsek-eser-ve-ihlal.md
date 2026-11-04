# Telif hakkı (FSEK): eser, hak sahipliği, yazılım ve ihlal

## Ne zaman kullanılır
- "Yazılımımızı/kaynak kodumuzu kopyaladılar", "lisans sayısını aşmışlar", "korsan yazılım denetimi geldi", "fotoğrafımız izinsiz kullanılıyor", "kitabımı intihal etmişler", "çalışanın yazdığı kod kimin", "freelance geliştiriciden hakları aldık mı", "FSEK 68 üç kat ne demek", "yapay zekâ ile üretilen içerik eser mi".
- FSEK hukuk davaları (men, ref, tazminat) ve FSEK m.71 suçları.

**Bu bir triyajdır.** Eser niteliği ve benzerlik çoğu zaman teknik bilirkişiyle belirlenir; "eserdir/değildir" kesin yazma.

**Sınır:** Lisans, yayın, SaaS ve geliştirme sözleşmesinin madde madde incelemesi → `../../sozlesme-incelemesi-tbk/references/yazilim-lisans-ve-saas.md` ve `vekalet-simsarlik-komisyon-yayim.md` (FSEK m.48, 52 orada DOGRULANDI). İnternetten içerik kaldırma → `internet-icerik-kaldirma.md`. Açık kaynak lisansları → `acik-kaynak-lisans-uyumu.md`. Ceza usulü → `../../ceza-ve-infaz-dilekce/SKILL.md`.

---

## Süre ve usul tablosu

| Konu | Kural | Dayanak |
|---|---|---|
| Koruma süresi | Eser sahibinin hayatı + ölümünden itibaren 70 yıl; birden çok sahipte son ölenin ölümünden 70 yıl; ilk sahip tüzel kişiyse aleniyetten 70 yıl | FSEK m.27   |
| Zamanaşımı (tazminat) | FSEK'te özel süre yok; mali hak tecavüzünde tazminat haksız fiil hükümlerine bağlı (m.70/2) → TBK m.72 | FSEK m.70  |
| Görevli mahkeme | FSEK hukuk ve ceza davalarında SMK m.156/1'deki mahkemeler (FSHHM) | FSEK m.76/1 (6769 m.189 ile değişik)  |
| Yetki (ref ve men) | Eser sahibi ikametgâhında da dava açabilir | FSEK m.66/son  |
| Ticari dava | İşletmeyi ilgilendirmeyen fikir ve sanat eseri davaları ticari dava değil (TTK 5/A arabuluculuk da aranmaz); işletmeyle ilgiliyse ticari | TTK m.4/1 son cümle  `[incele]` |
| Ceza şikâyeti | m.71-72 suçları şikâyete bağlı; hak belgesi ve deliller **şikâyet süresi içinde** başsavcılığa verilmezse kovuşturmaya yer olmadığı | FSEK m.75  |
| Savcının faaliyet durdurma kararı | Çoğaltmayla sınırlı; 24 saat içinde hâkim onayına; onaylanmazsa hükümsüz | FSEK m.75/3 |
| İhtiyati tedbir | Dava öncesi veya sonrası; emre muhalefet İİK m.343 cezası; gümrükte 4458 m.57 | FSEK m.77  |

---

## Kontrol listesi

**1. Eser mi? (FSEK m.1/B, m.2-6)**
- [ ] Sahibinin hususiyetini taşıyor mu ve dört türden birine giriyor mu (ilim-edebiyat, musiki, güzel sanatlar, sinema)? 
- [ ] **Bilgisayar programları** ve program sonucu doğuracak hazırlık tasarımları ilim-edebiyat eseridir; **arayüze temel oluşturan düşünce ve ilkeler eser sayılmaz** (m.2/1).  Algoritma ve fikir korunmaz; ifade korunur.
- [ ] Teknik/bilimsel fotoğraf, harita, proje, endüstri tasarım projeleri m.2/3'te; bedii vasıflı fotoğraf güzel sanat eseri `[doğrula]`.
- [ ] İşleme ve derleme (m.6): çeviri, uyarlama, veritabanı niteliğindeki derleme; özgün eser üzerindeki haklar saklı.
- [ ] **Yapay zekâ çıktısı:** FSEK eser sahibini "eseri meydana getiren kişi" olarak tanımlıyor (m.1/B-b); insan katkısı olmayan çıktının eser sayılması tartışmalı `[incele]`. Model eğitiminde başkasının eserinin çoğaltılması ayrı risk `[incele]`. Yapay zekâ çıktısına özgü kanun değişikliği ya da Yargıtay kararı soorgla'da bulunamadı; çalışma anında RG ve güncel karar araması yap, bulamazsan `[ARAŞTIRMA GEREKLİ: yapay zekâ çıktısı ve FSEK]`. 

**2. Hak sahibi kim? (zincir)**
- [ ] Eser sahibi = meydana getiren gerçek kişi (m.1/B-b). Mali hakları kullanma yetkisi eser sahibine aittir (m.18/1).
- [ ] **İşçi, memur ve hizmetli eserleri:** aksi sözleşmeden ya da işin mahiyetinden anlaşılmadıkça haklar işverence/atayanca kullanılır; tüzel kişi organlarına da uygulanır (m.18/2).  **Bağımsız yüklenici ve freelance geliştiricide bu kural yok** → yazılı ve hakları ayrı ayrı gösteren devir (m.52) şart (`../../sozlesme-incelemesi-tbk/references/yazilim-lisans-ve-saas.md`).
- [ ] Yapımcı/yayımcı ancak eser sahibiyle sözleşmeye göre mali hakları kullanabilir (m.18/3).
- [ ] Devir zinciri: geliştirme sözleşmesinde "mali haklar kuruma aittir" maddesi hangi sözleşmede var; yalnız birinde varsa diğer dönemlerin kodu kimin? (11. HD E.2025/1871 — devir maddesi yalnız bir sözleşmede vardı; mahkeme o sözleşmeye konu modüller için davacıyı hak sahibi saydı). 
- [ ] Manevi haklar (adın belirtilmesi, değişiklik yasağı, umuma arz; m.14-17) gerçek kişi eser sahibine aittir ve devredilemez; **mali hakları devralmış tüzel kişi FSEK m.70 manevi tazminatı isteyemez** (aynı karar, ilk derece gerekçesi onandı).  

**3. İhlal fiili (mali haklar m.21-25)**
- [ ] İşleme, çoğaltma, yayma, temsil, umuma iletim. **Çoğaltma** programın yüklenmesi, görüntülenmesi, çalıştırılması, iletilmesi ve depolanmasını gerektirdiği ölçüde geçici çoğaltmayı da kapsar (m.22). 
- [ ] **Korsan kullanım / lisans aşımı:** bir kullanıcılık lisansın 100 kullanıcıya açılması, sanal makinede çoğaltma, süre bitiminden sonra kullanım.
- [ ] **İntihal/kaynak kod kopyası:** veri tabanı yapısı, tablolar, kaynak kod karşılaştırması bilirkişi raporuyla; dava öncesi FSHHM'de delil tespiti (aynı kararda "D.İş" tespit raporu belirleyici oldu).
- [ ] **İstisnalar:** kâr amacı gütmeyen şahsi kullanım için çoğaltma (hak sahibinin meşru menfaatine zarar vermemek kaydıyla); programı hukuken edinen kişinin amaca uygun kullanım için çoğaltması, hata düzeltmesi, bir yedek kopya (m.38) — sözleşmeyle önlenemeyen çekirdek haklar.  Alıntı, eğitim, haber istisnaları m.31-37 `[doğrula]`.

**4. Hukuki talepler**
- [ ] **Tecavüzün ref'i (m.66):** kusur şartı yok; işletme çalışanlarının fiilinde işletme sahibine de dava; mahkeme tedbirleri takdir eder. 
- [ ] **Tecavüzün men'i (m.69)** `[doğrula]`.
- [ ] **FSEK m.68 bedel:** yazılı izin alınmadan işleme, çoğaltma, yayma, temsil, umuma iletimde sözleşme yapılsaydı istenebilecek bedelin ya da rayiç bedelin **en çok üç katı**; kopyalar satışa çıkmamışsa imha ya da maliyet bedeline teslim veya üç kat.  "Üç kat" **üst sınırdır; mahkeme takdir eder** ve ortak kusurda indirim yapabilir (11. HD E.2025/1871: rayiç bedelin 2 katına hükmedilen karar onandı).  Eski YAML'daki "3 katına kadar tazminat hakkı doğar, altın vuruş" ifadesi bu takdir yetkisini gizliyor; düzeltildi.
- [ ] **FSEK m.70** maddi ve manevi tazminat (kusur şartı) `[doğrula]`.
- [ ] **İspat kolaylığı (m.76/2):** davacı kuvvetli kanaat oluşturacak delil sunarsa mahkeme davalıdan izin belgelerini ya da kullanılan eser listesini isteyebilir; sunulamaması haksız kullanım karinesidir.  Lisans denetimi davalarında kritik.

**5. Cezai yol (m.71-75)**
- [ ] m.71/1: izinsiz işleme, temsil, çoğaltma, değiştirme, dağıtma, umuma iletim, yayımlama, satışa arz, ticari amaçla satın alma, ithal/ihraç, şahsi kullanım dışında bulundurma — 1-5 yıl hapis **veya** adli para cezası. Kendi eseri olarak ad koyma (m.71/2), kaynak göstermeden iktibas (m.71/3) ayrı suçlar. 
- [ ] Ek m.4/1 bilgilerini yetkisiz kaldırma ile ihlale devam eden bilgi içerik sağlayıcı: 3 ay-2 yıl (m.71 son fıkralar).
- [ ] Satıcının kaynağını bildirip yakalanmayı sağlaması: indirim ya da cezadan vazgeçme (m.71 son fıkra).
- [ ] Şikâyet ve belge sunma şartı (m.75).
- [ ] Eski YAML'daki "Yargıtay 8. CD bilişim" daire bilgisi sabit yazılmaz.

---

## İdare tarafı

Kamu kurumu yazılım hak sahibi ya da kullanıcısı olabilir (11. HD E.2025/1871'de davacı üniversite, ihlal Sayıştay denetiminde fark edildi). Kurum içi kontrol:
- İhale ve destek hizmet sözleşmelerinde mali hak devri maddesi **her sözleşmede** var mı, hakları ayrı ayrı sayıyor mu (m.52)? Kaynak kod ve dokümantasyon teslimi devir yerine geçmez.
- Kurumdaki lisans envanteri; lisans aşımı kamu zararı ve FSEK m.76/2 karinesi riski → kamu zararı yönü `kamu-mali-denetim-sayistay` becerisi (3. dalga).

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Eseri kim, hangi ilişki içinde (işçi, memur, freelance, şirket ortağı) yarattı? | m.18, m.52 |
| Devir/lisans sözleşmeleri yazılı mı; hangi haklar ayrı ayrı sayılmış? | m.52 |
| İhlal edilen eserin oluşturulma tarihi ve kanıtı (git geçmişi, noter, depo kaydı)? | Önce gelme, sahiplik |
| Karşı tarafın ürününe erişim var mı; kod örneği, ekran görüntüsü? | Delil tespiti |
| Lisans bedeli ya da emsal fiyat listesi? | m.68 rayiç bedel |
| Eser yayımlandı mı, ne zaman? | Süre, aleniyet |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "5846"  law_type: "Kanun"  article_no: "2" | "6" | "14" | "18" | "21" | "22" | "27" | "38" | "48" | "52" | "66" | "68" | "69" | "70" | "71" | "75" | "76" | "77"
legal_list_statute_articles  statute_id: 69863  article_no: "1/B"  include_content: true
legal_search_cases  mahkeme: "yargitay"  sorgu: "<olay: lisanssız yazılım FSEK 68 / kaynak kod benzerliği / işçi eseri m.18>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "bam"  sorgu: "<olay> FSEK"
legal_get_case_document  belge_id: "<son 3 yıldan karar>"
legal_search_admin_guidance  kurum: "Gelir İdaresi Başkanlığı"  belge_tur: "ozelge"  sorgu: "telif ücreti stopaj <durum>"     # vergi yönü → vergi becerisi
```

---

## Çıktı iskeleti

```markdown
> Bu bir triyajdır; ihlal olduğu ya da olmadığı yönünde bir tespit değildir.
## FSEK triyajı — [eser]
### Eser niteliği (faktörler)
### Hak sahipliği zinciri
| Tarih | Belge | Kimden → kime | Hangi haklar (m.52) | Eksik |
### İhlal fiilleri ve istisnalar
### Talepler: ref / men / m.68 bedel / m.70 tazminat / tedbir / şikâyet
### Süreler
### Öneri — [incele]
```

---

## Sık hatalar

- 🔴 Freelance geliştiricinin kodunu m.18/2 kapsamında işverenin saymak.
- 🟠 "FSEK 68 → otomatik üç kat" demek (üst sınır, takdir ve indirim var).
- 🟠 Tüzel kişi adına manevi tazminat istemek.
- 🟠 Ceza şikâyetinde hak belgesini süre içinde sunmamak (m.75).
- 🟡 Fikir/algoritmanın kendisini eser saymak (m.2/1 arayüz düşünce ve ilkeleri).

---

