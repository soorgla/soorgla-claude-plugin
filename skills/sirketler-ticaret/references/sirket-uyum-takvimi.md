# Şirket uyum takvimi ve sağlık taraması

## Ne zaman kullanılır
- "Şirketimizin yıllık yükümlülükleri neler?", "olağan genel kurul ne zaman", "defter tasdiki", "internet sitesi zorunlu mu", "şirket sağlık taraması", "grup şirketlerinin takvimi".
- Bir şirket satın alınmadan önce hedef şirketin uyum durumunun kontrolü (→ `sirket-satin-alma-ve-inceleme.md` ile birlikte).

Upstream `entity-compliance` uyarlamasıdır: her şirket için **türüne göre** ayrı takvim kurulur (A.Ş. ile Ltd. yükümlülüklerini karıştırma; upstream'deki "Delaware şirketi tek kova değildir" uyarısının Türk karşılığı budur).

**Kaynak uyarısı:** aşağıdaki süreler kanun metninden çekildi; vergi beyannameleri, e-defter beratları, SGK bildirgeleri ve oda aidatları bu tablonun **dışındadır** — mali müşavirin takvimi o konularda esastır. Tracker, mali müşavirin ya da şirket sekreterinin verisini düzenlemek içindir, onun yerine geçmez.

---

## 1. Yıllık takvim (A.Ş. — Ltd. farkları ayrıca)

| Yükümlülük | Süre | Dayanak | A.Ş. | Ltd. |
|---|---|---|---|---|
| Olağan genel kurul | Faaliyet dönemi sonundan itibaren **3 ay** | TTK m.409/1  | ✓ | ✓ (m.617/1)  |
| Belgelerin pay sahiplerine açılması | Genel kuruldan **en az 15 gün önce** | TTK m.437/1  | ✓ | Ltd. → m.614 `[doğrula]` |
| Genel kurul çağrısı | En az **2 hafta önce** (ilan ve toplantı günü hariç), TTSG + internet sitesi + taahhütlü mektup | TTK m.414  | ✓ | Ltd. → m.617 `[doğrula]` |
| Fiziki yevmiye, kebir, envanter defteri açılış onayı (izleyen dönem) | Kullanılacak faaliyet döneminin ilk ayından önceki ayın sonuna kadar (noter) | TTK m.64/3 | ✓ | ✓ |
| Yevmiye defteri kapanış onayı | İzleyen faaliyet döneminin **6. ayı sonuna** kadar | TTK m.64/3 | ✓ | ✓ |
| Yönetim kurulu karar defteri kapanış onayı | İzleyen faaliyet döneminin **1. ayı sonuna** kadar | TTK m.64/3 | ✓ | Müdürler kurulu karar defteri `[doğrula]` |
| Pay defteri, genel kurul toplantı ve müzakere defteri | Yeterli yaprak varsa izleyen dönemlerde açılış onayı gerekmez | TTK m.64/3 | ✓ | ✓ |
| Elektronik defterler | Açılış ve (yevmiye/YK karar defteri) kapanış onayı aranmaz. Bakanlık m.64/4 yetkisini kullandı: **1/1/2026'dan itibaren kuruluşu tescil edilen şirketler** ve izne tabi A.Ş.'ler (2012 tarihli asgari sermaye/izin tebliğinin m.5/1 listesi) **pay defteri ile genel kurul toplantı ve müzakere defterini** elektronik ortamda (Bakanlık sistemi) tutmak zorunda; diğerleri ihtiyari olarak geçebilir, geçen geri dönemez. YK karar defteri 20.09.2025 değişikliğiyle zorunluluk kapsamından çıkarıldı | TTK m.64/3-4 (7262 ile); İşletmenin Muhasebesiyle İlgili Olmayan Ticari Defterlerin Elektronik Ortamda Tutulması Hakkında Tebliğ (RG 14.02.2025, 32813; değişik RG 20.09.2025, 33023) | ✓ | ✓ |
| Tescil sırasında defter onayı | A.Ş. ve Ltd. kuruluş tescilinde açılış onayı ticaret sicili müdürlüğünce | TTK m.64/3 (7099 ile) | ✓ | ✓ |

 

## 2. Olay bağlı süreler

| Olay | Süre | Dayanak |
|---|---|---|
| Kuruluş tescili (denetime tabi şirket) → internet sitesi | **3 ay**; içerik ilgili olaydan itibaren **en geç 5 gün** içinde; en az **6 ay** yayında | TTK m.1524/1, 5  |
| İnternet sitesi yükümlülüğüne uymamak | İlgili kararların **iptal sebebi**, yönetici sorumluluğu, cezai hükümler saklı | TTK m.1524/2 |
| Ltd. pay devrinin tescil başvurusu | **30 gün** | TTK m.598 (`idari-ve-kurum-basvurulari`'nda çekildi) |
| Sermaye artırımının tescili | Karardan **3 ay** | TTK m.456/3  |
| Hamiline pay devri | MKK'ya bildirim (bildirimden önce haklar kullanılamaz) | TTK m.489  |
| Sermaye kaybı (m.376) | Genel kurul "hemen/derhâl" | TTK m.376  |
| Asgari sermaye | **31/12/2027** (bir kez uzatıldı, RG 17.10.2026; ikinci uzatma olabilir) | TTK geçici m.15  |
| Sicile tescili gereken değişiklikler (temsil, adres, müdür, YK) | Kanunda aksine hüküm yoksa **15 gün**; sicil müdürlüğü yetki çevresi dışında oturanlar için 1 ay | TTK m.30; Ticaret Sicili Yönetmeliği  |
| Gerçek faydalanıcı bildirimi, MERSİS güncellemesi | İdari düzenleme | `[doğrula]` — araçta görülmedi |

## 3. Sağlık taraması (upstream `--audit` modunun karşılığı)

Her şirket için tek tek:
1. **Sicil:** unvan, merkez adresi, sermaye, temsil yetkilileri ve süreleri (YK üyelerinin görev süresi dolmuş mu?), şubeler — sicil gazetesi ile şirket kayıtları uyumlu mu?
2. **Sermaye:** asgari tutarın altında mı (geçici m.15)? Ödenmemiş sermaye var mı (A.Ş. 24 ay)?
3. **Genel kurul:** son üç yılın olağan genel kurulları yapılmış ve tescil/ilan edilmiş mi? Aralıksız beş yıl yapılmaması geçici m.7 resen terkin kapsamındaydı — risk göstergesi `[incele]`.
4. **Defterler:** açılış/kapanış onayları; e-defter geçişi.
5. **İnternet sitesi** (denetime tabiyse): açık mı, zorunlu içerik var mı?
6. **Sermaye kaybı:** son yıllık bilançoda m.376 eşikleri?
7. **Pay defteri:** devirler işlenmiş mi; hamiline paylar MKK'ya bildirilmiş mi?
8. **Bağımsız denetim** kapsamında mı (ölçütler CB kararıyla; `[doğrula]`)?
9. **Bekleyen davalar**, idari para cezaları, Rekabet Kurumu soruşturmaları.

Durum kodları: `güncel` / `yaklaşan (90 gün)` / `gecikmiş` / `bilinmiyor`. Bilinmeyen tarihi tahmin etme; "bilinmiyor — mali müşavir/sicilden teyit" yaz.

## 4. Takip dosyası (isteğe bağlı)

Kullanıcı isterse takvimi şu yapıda bir markdown tablosu olarak üret (dosyaya yazmak profil/dosya çalışma alanı kurallarına tabidir, ORTAK-KURALLAR.md "Büro profili"):

| Şirket | Tür | Sicil no | Yükümlülük | Son gün | Dayanak | Son yapılan | Durum | Sorumlu |

---

## Görüşme soruları
1. Şirket(ler)in türü, sicil müdürlüğü, faaliyet dönemi (takvim yılı mı, özel hesap dönemi mi)?
2. Bağımsız denetime tabi mi; internet sitesi var mı?
3. Defterler fiziki mi elektronik mi?
4. Son olağan genel kurul tarihi; YK/müdür görev süreleri?
5. Sicildeki sermaye tutarı?
6. Mali müşavirin takvimi elinizde mi (vergi/SGK süreleri için)?

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6102"  article_no: "64" | "397" | "409" | "414" | "437" | "456" | "617" | "1524"
legal_get_statute_article  law_no: "6102"  article_no: "geçici 15"
legal_search_official_gazette  query: "bağımsız denetime tabi şirketlerin belirlenmesine dair Cumhurbaşkanı Kararı"  sort_by: "date_desc"
legal_search_official_gazette  query: "ticari defterlere ilişkin tebliğ"  search_in: "title"  sort_by: "date_desc"
legal_search_statute_semantic  sorgu: "ticaret siciline tescili gereken hususların tescil süresi on beş gün"
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Kaynaklar satırına: "vergi/SGK süreleri kapsam dışı")

## Uyum takvimi — [şirket/grup], [faaliyet yılı]

### Önümüzdeki 30 / 60 / 90 gün
| Son gün | Şirket | Yükümlülük | Dayanak | Durum |

### Gecikmiş ve bilinmeyen kalemler
### Sağlık taraması bulguları (🔴/🟠/🟡)
```

## Sık hatalar
- Ltd. ve A.Ş. takvimini aynı sanmak (devir tescili, Bakanlık temsilcisi, karar defteri).
- Bağımsız denetime tabi olmayan şirkete internet sitesi zorunluluğu yazmak (m.1524/6).
- Yevmiye ve YK karar defteri kapanış sürelerini karıştırmak (6. ay / 1. ay).
- Bilinmeyen bir tarihi "muhtemelen" diye doldurmak.

