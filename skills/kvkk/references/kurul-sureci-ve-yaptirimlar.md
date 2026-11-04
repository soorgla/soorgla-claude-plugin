# Kurul incelemesi, idari para cezası, dava, ceza ve tazminat

## Ne zaman kullanılır
- Kişisel Verileri Koruma Kurumu bilgi-belge istedi, yerinde inceleme duyurdu ya da şikâyet üzerine savunma istedi.
- Kurul "hukuka aykırılığın giderilmesi" ya da idari para cezası kararı verdi; itiraz/dava yolu ve süresi soruluyor.
- Kişisel veri nedeniyle ceza (TCK 135-140) ya da tazminat yolu değerlendiriliyor.

**2024 değişikliği — yargı yolu:** Kurulca verilen idari para cezalarına karşı artık **idare mahkemesinde dava** açılır (m.18/3, 7499 ile eklendi, yürürlük 1/6/2024). Bu tarihten önce bu cezalar Kabahatler Kanunu genel kuralıyla **sulh ceza hâkimliğinde** itiraz konusuydu; 1/6/2024 itibarıyla sulh ceza hâkimliklerinde görülmekte olan başvurular orada görülmeye devam eder.  Eski emsallerdeki "sulh ceza hâkimliğine 15 gün içinde itiraz" bilgisi yeni cezalar için **bayattır**.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Kurulun istediği bilgi-belgeyi gönderme: **15 gün** | Talebin tebliği | 6698 m.15/3  | Devlet sırrı hariç; yerinde incelemeye imkân sağlama zorunlu. |
| Kurul kararının (aykırılığın giderilmesi) yerine getirilmesi: gecikmeksizin, **en geç 30 gün** | Kararın tebliği | 6698 m.15/5  | Yerine getirmemek ayrı İPC (m.18/1-c).  |
| İPC'ye karşı **idare mahkemesinde** iptal davası: **60 gün** | Yazılı bildirimi izleyen gün | 6698 m.18/3 + 2577 İYUK m.7/1  | İki hükmün birlikte okunmasıdır; özel süre bulunmadığı sonucu `[incele]`. Yetkili idare mahkemesi: 6698'de özel yetki kuralı yoksa genel kural İYUK m.32/1 — işlemi yapan idari merciin (KVK Kurulu) bulunduğu yer idare mahkemesi; özel bir yetki kuralı (İYUK m.33-38) uygulanıp uygulanmadığını ve Danıştay'ın KVKK İPC davalarındaki yetki kararını `legal_search_cases` (`mahkeme: "danistay"`, `sorgu: "Kişisel Verileri Koruma Kurulu idari para cezası yetkili idare mahkemesi"`) ile teyit et; bulamazsan `[ARAŞTIRMA GEREKLİ: KVKK İPC yetkili mahkeme]`.  |
| İPC'nin ödenmesi ve peşin ödeme indirimi | Tebliğ | 5326 m.17/6  | 6698 ödeme süresi düzenlemediğinden genel kural — uygulanabilirliği `[incele]`. |
| Kurulun kararına (İPC dışı: giderme kararı, aktarım durdurma) karşı dava | Tebliğ | 2577 m.7/1 — 60 gün `[incele]` | İdari işlem → idari yargı. |
| Şikâyete Kurul cevabı: 60 gün içinde yoksa ret sayılır | Şikâyet | 6698 m.15/4  | → `ilgili-kisi-basvurusu.md` |
| TCK 135-140 suçlarında şikâyet/soruşturma şartı ve zamanaşımı | — | TCK m.139: kişisel verilerin kaydedilmesi (m.135), verileri hukuka aykırı verme/ele geçirme (m.136) ve verileri yok etmeme (m.138) **dışındaki** bölüm suçları şikâyete bağlı; zamanaşımı genel hükümlerden | `[incele]`  |

`legal_calculate_deadline` İPC davası süresini hesaplar (`kvkk_ipc_lawsuit`); diğer süreleri elle hesapla, `legal_check_holiday`, `[doğrula]`. 7 günden az kaldıysa 🔴.

---

## İdari para cezaları (m.18)

| Bent | Fiil | Muhatap |
|---|---|---|
| (a) | Aydınlatma yükümlülüğünü (m.10) yerine getirmemek | Veri sorumlusu |
| (b) | Veri güvenliği yükümlülüklerini (m.12) yerine getirmemek | Veri sorumlusu |
| (c) | Kurul kararlarını (m.15) yerine getirmemek | Veri sorumlusu |
| (ç) | VERBİS kayıt ve bildirim yükümlülüğüne (m.16) aykırılık | Veri sorumlusu |
| (d) | Standart sözleşme bildirimi (m.9/5) yapmamak — **7499 ile eklendi** | Veri sorumlusu **veya veri işleyen** |

- Cezalar gerçek kişiler ve özel hukuk tüzel kişileri hakkında uygulanır; kamu kurumlarında disiplin hükümleri işletilir. 
- **Tutar:** m.18/1'deki alt-üst sınırlar kanun metnindeki taban tutarlardır; her takvim yılı başından geçerli olmak üzere VUK mükerrer m.298 yeniden değerleme oranında artırılarak uygulanır. Bu becerinin metnine tutar yazılmaz: m.18 metnini çek, ilgili yılın yeniden değerleme oranını kullanıcıdan ya da Kurum duyurusundan al, hesabı formülle göster, `[doğrula]`. 
- Cezanın belirlenmesinde haksızlık içeriği, kusur ve ekonomik durum gözetilir (alt-üst sınırlı cezalar). 

---

## Kontrol listesi — Kurul incelemesine cevap / savunma

1. Talep yazısının tebliğ tarihi, istenen belgeler, süre (15 gün) — tablo.
2. Talep şikâyete mi dayanıyor, re'sen mi? Şikâyet 3071 m.6 şartlarını taşıyor mu?  Şikâyetçi önce veri sorumlusuna başvurmuş mu (m.14/2)?
3. Olgular: hangi veri, hangi işlem, hangi tarih; hukuki sebep; aydınlatma kanıtı (ispat yükü veri sorumlusunda ); güvenlik tedbirleri; VERBİS kaydı.
4. Benzer olaylarda Kurul kararları ve ilke kararları (aşağıdaki çağrılar). İlke kararına aykırılık ağırlaştırıcıdır `[incele]`.
5. Kusuru azaltan unsurlar: derhâl düzeltme, ilgili kişiyle iletişim, tedbirlerin güncellenmesi, iç eğitim.
6. Yazı **dışa gider**: taslak başlığı ve iç notlar yazının içinde olmaz; iç değerlendirme ayrı belge.

## Kontrol listesi — İPC/Kurul kararına karşı dava değerlendirmesi

1. **Usul**: tebliğ tarihi ve şekli; karar 1/6/2024 öncesi mi sonrası mı (yargı yeri); dava süresi; yetkili mahkeme `[doğrula]`.
2. **Yetki ve şekil**: Kurul kararı mı, Başkanlık işlemi mi; gerekçe; savunma hakkı tanındı mı?
3. **Sebep**: fiil gerçekten oluştu mu? Doğru bent mi uygulandı (ör. aydınlatma eksikliği (a) ile güvenlik ihlali (b) karıştırılmış mı)?
4. **Konu/ölçülülük**: tutarın alt-üst sınır içinde ve m.17/2 ölçütlerine uygun belirlenmesi; yeniden değerleme yılı doğru mu?
5. **Muhatap**: (d) bendi dışındaki cezalar yalnız veri sorumlusuna; veri işleyene (a)-(ç) cezası verilmiş mi? 
6. **Emsal**: `legal_search_cases` (`mahkeme: "danistay"` ve `"bam"`), son 3 yıldan en az bir tam metin. 2024 öncesi sulh ceza kararları ancak esas yönünden fikir verir.
7. Dava dilekçesi: `../../idare-davalari-imar/references/idari-dava-dilekcesi.md` (İPC iptali iskeleti; aşağıdaki kısa iskelet yalnız o beceri yüklü değilse); istinaf/temyiz aşaması → `../../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`.

## Ceza ve tazminat yolları (işaret düzeyinde)

- **Suçlar**: kişisel verilere ilişkin suçlarda TCK m.135-140 uygulanır; m.7'ye aykırı olarak silmeyen/anonimleştirmeyen TCK m.138'e göre cezalandırılır.  Verileri hukuka aykırı verme, yayma, ele geçirme (TCK 136) iki yıldan dört yıla kadar hapis gerektirir.  Yargıtay'da hangi ceza dairesinin baktığını sabit yazma; güncel iş bölümünü çek. Suç duyurusu metni → `../../ceza-ve-infaz-dilekce/SKILL.md` (kapsamda değilse `[incele]`).
- **Tazminat**: kişilik hakları ihlal edilenlerin genel hükümlere göre tazminat hakkı saklıdır; m.11/1-(ğ) zararın giderilmesini talep hakkı. Dava esası → `../../tazminat-haksiz-fiil/SKILL.md`; dilekçe → `../../hukuk-yargilamasi-dilekce/SKILL.md`.  Örnek güncel karar: banka müşteri sırrı ve hesap hareketlerinin mahkeme müzekkeresini aşan biçimde ifşası nedeniyle manevi tazminat davası — Yargıtay 4. HD E.2022/3953 K.2025/2404 (13.02.2025) `[soorgla]`; kararın sonucu ve gerekçesi yalnız davanın kısmı okunarak aktarılmıştır `[çekildi ama desteği doğrulayın]`. 
- **AYM**: kişisel verilerin korunmasını isteme hakkı (Anayasa m.20/3) ihlali iddiası — olağan yollar tüketildikten sonra → `../../aym-aihm-basvuru/SKILL.md`.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Yazı/karar | Kurumdan gelen yazının/kararın tarihi, sayısı, tebliğ tarihi ve şekli (KEP, posta)? |
| Konu | Şikâyet mi re'sen mi; hangi fiil; hangi bent? |
| Tutar | Ceza tutarı ve hangi yıl için hesaplandığı? |
| Olgular | Olayın gelişimi, aydınlatma/rıza kanıtları, güvenlik tedbirleri, VERBİS kaydı? |
| Önceki | Daha önce Kurul kararı/İPC var mı? |
| Ödeme | Peşin ödemeyi düşünüyor musunuz (dava hakkını etkilemez)? |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6698"  article_no: "15" | "17" | "18"
legal_list_statute_articles  law_no: "6698"  article_kind: "gecici"  include_content: true
legal_get_statute_article  law_no: "5326"  article_no: "17"
legal_get_statute_article  law_no: "2577"  article_no: "7"
legal_get_statute_article  law_no: "5237"  article_no: "135" | "136" | "138" | "139" | "140"
legal_search_cases  sorgu: "Kişisel Verileri Koruma Kurulu idari para cezası iptali"  mahkeme: "danistay"  tarih_baslangic: "2024-06-01"
legal_search_cases  sorgu: "<aynı>"  mahkeme: "bam"
legal_case_facets  sorgu: "Kişisel Verileri Koruma Kurulu kararı iptal"  mahkeme: "danistay"
legal_search_admin_guidance  sorgu: "Kişisel Verileri Koruma Kurulunun kararı <fiil> idari para cezası"  kurum: "Kişisel Verileri Koruma Kurulu"  tarih_baslangic: "<son 3 yıl>"
legal_search_official_gazette  query: "Kişisel Verileri Koruma Kurulunun"  search_in: "title"  sort_by: "date_desc"
```

---

## Çıktı iskeleti — değerlendirme ve süre tablosu

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Kurul işlemi değerlendirmesi — [karar/yazı tarihi, sayısı]
### Sonuç
### Süre tablosu
| İşlem | Başlangıç | Son gün | Dayanak | Durum |
### Hukuka aykırılık iddiaları
| # | Usul/Esas | İddia | Dayanak | Güç (🟢/🟡/🟠) |
### Tutar kontrolü
[m.18 bent, taban aralık, yeniden değerleme yılı ve oranı (kullanıcıdan/Kurumdan), hesap — [doğrula]]
### Emsal
```

## Çıktı iskeleti — idare mahkemesi dava dilekçesi (yedek; asıl iskelet `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`)

```markdown
[TASLAK — yedek iskelettir; idare-davalari-imar yüklüyse onun idari-dava-dilekcesi.md iskeletini kullanın; usul avukat tarafından tamamlanmalıdır] `[incele]`

[… İDARE MAHKEMESİ BAŞKANLIĞINA]  [yetkili mahkeme — doğrula]

DAVACI        : [unvan, adres, vergi no]
VEKİLİ        : [varsa]
DAVALI        : Kişisel Verileri Koruma Kurumu Başkanlığı
DAVA KONUSU   : Kişisel Verileri Koruma Kurulunun [tarih] tarihli ve [sayı] sayılı kararı ile verilen [tutar] TL idari para cezasının iptali
TEBLİĞ TARİHİ : [tarih]

AÇIKLAMALAR: [usul — tebliğ, savunma hakkı, gerekçe] [esas — fiil, bent, ölçülülük]
HUKUKİ SEBEPLER: 6698 m.… ; 2577 ; 5326 m.17 [her biri soorgla atfıyla, dipnotta]
DELİLLER: [karar, tebligat, aydınlatma kanıtları, teknik raporlar]
SONUÇ VE İSTEM: [kararın/İPC'nin iptaline; yürütmenin durdurulmasına (gerekçesiyle); yargılama giderleri]
[tarih, imza]
```
Harç → `legal_calculate_court_fee` (idari yargı harcı türü tanınmazsa `legal_get_social_parameters`) `[doğrula]`.

---

## Sık hatalar
- 1/6/2024 sonrası cezaya sulh ceza hâkimliğine itiraz etmek (ya da tersine, derdest eski başvuruyu idare mahkemesine taşımaya çalışmak).
- Dava süresini Kabahatler K.'nın eski 15 günüyle karıştırmak; ya da 60 günü kesin saymak (özel süre kontrolü yapılmadan).
- Kurulun 15 günlük bilgi-belge süresini kaçırmak.
- m.18'deki taban tutarları güncel ceza sanmak.
- Veri işleyene (a)-(ç) bentlerinden ceza verilmesini sorgulamamak.
- Peşin ödemenin dava hakkını düşürdüğünü sanmak.

