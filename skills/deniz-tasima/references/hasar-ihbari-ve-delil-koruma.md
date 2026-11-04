# Olay sonrası ilk adımlar: hasar ihbarı, delil koruma, gelen talebin triyajı

## Ne zaman kullanılır
- Yük hasarlı/eksik teslim edildi ya da hiç gelmedi; **saatler ve günler** içinde ne yapılmalı?
- Deniz kazası (çatma, karaya oturma, yangın, kurtarma) oldu; hangi kayıt korunmalı, hangi tespit istenmeli?
- Karşı taraftan (yük ilgilisi, sigortacı, P&I, kurtaran, acente) **talep mektubu / hasar ihbarı / süre uzatma talebi** geldi; nasıl ayrıştırılıp cevap seçeneği belirlenir?

Bu dosya Anthropic upstream `litigation-legal/legal-hold` (saklama yükümlülüğünün kapsamı, saklayıcılar, tetikleyici an, dört aşama), `demand-received` (gelen talebin alan alan çıkarılması, değerlendirme, seçenekler, süre triyajı) ve `chronology` (kaynaklı olay zaman çizelgesi, önem etiketleri) becerilerinden Türk deniz ve taşıma hukukuna uyarlanmıştır (Apache 2.0). ABD'ye özgü "litigation hold" ve "FRE 408" kavramları alınmadı; Türk hukukunda karşılıkları aşağıda.

Esas değerlendirme → `yuk-hasari-ve-tasiyan-sorumlulugu.md`, `catma-kurtarma-ve-musterek-avarya.md`. Dava öncesi delil tespiti dilekçesi → `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`; ihtarname → `../../hukuk-yargilamasi-dilekce/references/ihtarname.md`. Genel delil koruma → `../../tazminat-haksiz-fiil/references/talep-yazisi-ve-delil-koruma.md`.

---

## A. Yük ilgilisi: teslimde ve hemen sonra (süre tablosu)

| Ne | Ne zaman | Dayanak | Kaçarsa |
|---|---|---|---|
| Açık hasarı teslim belgesine yaz, yazılı bildir | **Teslim sırasında** (deniz ve kara) | 6102 m.1185/1; m.889/1  | Düzgün teslim karinesi |
| Gizli hasar bildirimi — deniz | Teslimden **aralıksız 3 gün** | 6102 m.1185/1 | Karine |
| Gizli hasar bildirimi — kara (TTK) | Teslimden **7 gün** | 6102 m.889/2  | Karine |
| Gecikme bildirimi — deniz / kara | **60 gün** / **21 gün** | 6102 m.1185/5; m.889/3 | **Hak düşer** |
| Hava bagaj / yük hasarı, gecikme | 7 gün / 14 gün / 21 gün | 2920 m.128  | `[doğrula]` |
| Deniz yolcusu bagajı (gizli) | 15 gün | 6102 m.1269  | Karine |
| Resmî ortak inceleme | Taraflar katılarak mahkeme, yetkili makam ya da resmen atanmış uzmanca yapılırsa bildirime gerek yok | 6102 m.1185/2  | — |
| Bildirimin muhatabı | Fiilî taşıyana yapılan bildirim taşıyana da yapılmış sayılır; kaptana/sorumlu zabite yapılan da | 6102 m.1185/6  | — |
| Kara taşımasında bildirim şekli | Teslimden sonra yazılı; telekomünikasyonla olur; imza şart değil; **zamanında gönderilmesi yeterli** | 6102 m.889/4  | — |
| Hak düşürücü süre | Teslimden **bir yıl** (deniz) — takvime hemen işle | 6102 m.1188 | Dava hakkı düşer |

`legal_calculate_deadline` bunları tanımıyor; elle hesapla, `legal_check_holiday`, `[doğrula]`. Bildirim süresi 3 günse ve bugün ikinci günse çıktının en üstüne 🔴.

**Bildirim içeriği (asgari):** taşıma belgesi no, gemi/araç, konteyner ve mühür no, teslim tarihi-saati, zıya/hasarın **genel olarak neden ibaret olduğu** (m.1185/1 son cümle), ortak sörvey daveti, hakların saklı tutulduğu. Gönderim: KEP/e-posta + teslim belgesine şerh; acente üzerinden ise acentenin yetkisi (TTK m.105/1: acente ihbar ve protestoyu müvekkili adına kabule yetkili). 

---

## B. Delil koruma (upstream "legal hold" uyarlaması)

**Tetikleyici an:** hasar görüldüğü, kaza olduğu ya da talep mektubu geldiği an. Türk hukukunda ABD'deki gibi genel bir "saklama emri" kurumu yoktur; ancak ispat yükü (TTK m.1185/4 karinesi, m.1178 hâkimiyet dönemi, m.1180 teknik yönetim) ve ticari defter/belge saklama yükümlülükleri delilin korunmasını fiilen zorunlu kılar `[incele]`.

| Kim saklar | Ne | Not |
|---|---|---|
| Yük ilgilisi | Konişmento/CMR/AWB asılları, teslim belgeleri ve şerhler, fotoğraf/video (zaman damgalı), sörvey raporu, ambalaj ve numune, sıcaklık kaydedici (reefer data logger), gümrük belgeleri, satış faturası ve paketleme listesi, sigorta poliçesi | Hasarlı malı **imha/satış öncesi** taşıyana ve sigortacıya bildir, tespit fırsatı ver |
| Taşıyan / donatan | Seyir ve makine jurnali, **VDR**, AIS/ECDIS kayıtları, istif planı, yükleme ve tahliye tally kayıtları, reefer monitör kayıtları, kaptan raporu, sörvey/class raporları, yazışmalar | VDR üzerine kayıt yapılmadan veri alınmalı `[incele]`; jurnal tutma yükümlülüğü m.1096-1097 `[doğrula]` |
| Liman / terminal | CCTV, gate-in/out, ekipman kayıtları | Kısa saklama süreleri — yazılı talep |
| Forwarder | Booking, talimat, alt taşıyıcı sözleşmeleri, yazışmalar | Sıfat tartışması için kritik |

**Resmî tespit araçları:**
1. **Deniz raporu** — kaptan ya da ilgisini ispat eden herkes, varma/barınma limanında ya da ilk elverişli yerde, vakit kaybetmeden; Türkiye'de mahkemece. 
2. **Çatma delil tespiti** — çatma yerindeki deniz ticareti mahkemesi; tespit raporu kusur oranı içermez. 
3. **HMK delil tespiti** (genel) → `../../hukuk-yargilamasi-dilekce/references/delil-tespiti.md`.
4. **Resmî ortak inceleme** (m.1185/2) — bildirimin yerine geçer.
5. Taşıyanın inceleme yükümlülüğü ve karşılıklı kolaylık: m.1184, m.1185/3. 

**Dört aşama (upstream'den):** (1) **başlat** — kapsam, saklayıcılar, tarih aralığı, sistemler; (2) **yenile** — yeni olgu ya da taraf çıktıkça kapsamı genişlet; (3) **sonlandır** — dava/sulh/hak düşürücü süre dolunca; (4) **izle** — kimin neyi ne zaman teslim ettiği. Avukat olmayan kullanıcı için saklama talimatını göndermeden önce ORTAK-KURALLAR.md §1 kapısı.

---

## C. Gelen talebin triyajı (upstream "demand-received" uyarlaması)

**1. Alan alan çıkar:** gönderen (yük ilgilisi, sigortacı halef, P&I, kurtaran, liman), muhatap (doğru tüzel kişi mi: taşıyan / acente / forwarder / donatan), gönderim şekli ve **tebliğ tarihi**, talep türü (tazminat, navlun/demuraj, kurtarma ücreti, garame teminatı, **süre uzatma**), tutar ve para birimi, dayanılan belge ve madde, verilen süre, tehdit (dava, gemi haczi), sulh teklifi var mı.

**2. Hukuki süreleri ayır:** karşı tarafın verdiği süre bağlamaz; asıl süreler: hak düşürücü süre (m.1188), zamanaşımı (m.855, m.1297, m.1319, m.1285), rücu süreleri (m.1188/3: 90 gün), gemi alacaklısı hakkının düşmesi (m.1326). Kendi iç karar tarihini bunlardan geriye say.

**3. Esas değerlendirmesi (görüş değil, triyaj):** olgular uyuyor mu; dayanılan madde/rejim doğru mu (çoğu talep yanlış rejime dayanır: CMR yerine TTK, deniz yerine kara); sınır ve sorumsuzluk savunmaları; talep edilen tutar ile olası hüküm arasındaki fark. Derece: **güçlü / tartışmalı / zayıf / dayanaksız** — `[incele]`.

**4. Seçenekler (birini öner, gerekçesiyle):**

| Seçenek | Ne zaman | Risk |
|---|---|---|
| A. Esasa cevap | Talep güçlü ya da tartışmalı; kayıt oluşturmak gerekiyor | Yazılı pozisyon bağlar |
| B. Bekletme yazısı + süre uzatma anlaşması | İnceleme gerekiyor; hak düşürücü süre yaklaşıyor | **m.1188/4 uzatması yalnız dava sebebinden sonra ve anlaşmayla**; tek taraflı "haklarımız saklı" yetmez 🔴 |
| C. Sulh görüşmesi | Erken çözüm ucuz | Türk hukukunda FRE 408 karşılığı genel bir "sulh yazışması delil olamaz" kuralı yok; arabuluculukta ileri sürülen öneri, görüş, kabul ve yalnız arabuluculuk için hazırlanan belgeler sonraki dava ya da tahkimde delil olarak ileri sürülemez, sunulsa da hükme esas alınamaz (6325 m.5; gizlilik m.4, ihlalin cezası m.33); "ikrar sayılmaz" kaydı ekle `[incele]` |
| D. Cevap vermeme + delil koruma | Talep dayanaksız | Ticari ilişkide sessizlik (TTK m.21/2 fatura karinesi gibi) aleyhe sonuç doğurabilir `[incele]` |
| E. Rücu bildirimi | Kendi alt taşıyıcına/forwarder'ına | Kara taşımasında üç ay içinde bildirim şartı (m.855/3); deniz rücuunda 90 gün (m.1188/3) |

**5. Zaman çizelgesi (upstream "chronology"):** her olay için tarih-saat, kaynak (belge adı/kayıt), önem (🔴 süre başlatan / hak düşüren / sorumluluk unsuru; 🟡 destekleyici; ⚪ arka plan), boşluklar. Taraf perspektifini başa yaz (yük ilgilisi mi, taşıyan mı).

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Teslim ne zaman, kime, hangi belgeyle yapıldı? Belgeye bir şey yazıldı mı? | Bildirim ve süre başlangıcı |
| Hasar fotoğrafı/videosu, mühür no, sıcaklık kaydı var mı? | Delil |
| Sörvey kim tarafından, taşıyan davet edildi mi? | m.1185/2 ve delil gücü |
| Hasarlı mal hâlâ elde mi; imha/satış planı var mı? | Delil kaybı |
| Talep mektubu ne zaman, kime, nasıl geldi? | Triyaj ve iç süre |
| Sigortacıya bildirim yapıldı mı (poliçedeki ihbar süresi)? | Sigorta teminatı (→ sirketler-ticaret) |
| Alt taşıyıcı/forwarder zincirinde kimler var? | Rücu bildirimleri |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6102"  law_type: "Kanun"  article_no: "1184" | "1185" | "1188" | "889" | "855" | "1098" | "1292" | "105"
legal_search_statute_semantic  sorgu: "hasar ihbarı süre"  mevzuat_no: "2920"
legal_list_statute_articles  statute_id: 69230  article_no: "33"  include_content: true      # 6325 gizlilik (doğrulanacak)
legal_search_cases  mahkeme: "yargitay"  sorgu: "hasar ihbarı süresinde yapılmadı karine taşıyan sorumluluk konişmento"  tarih_baslangic: "<son 3 yıl>"
legal_check_holiday  tarih: "<son gün>"
```

---

## Çıktı iskeleti

```markdown
## İlk 72 saat planı — [olay, konteyner/gemi, teslim tarihi]
### 🔴 En yakın süre: [bildirim / hak düşürücü] — son gün [__]
### Hemen yapılacaklar (sıralı)
1. [ ] Teslim belgesine şerh / yazılı bildirim (m.1185 / m.889) — muhatap: [taşıyan + fiilî taşıyan + acente]
2. [ ] Ortak sörvey daveti / resmî tespit (m.1185/2, m.1292, HMK)
3. [ ] Delil saklama talimatları (saklayıcı listesi)
4. [ ] Sigortacıya ihbar
5. [ ] Takvim: hak düşürücü süre, arabuluculuk, rücu bildirimleri
### Gelen talep triyajı (varsa): alanlar | değerlendirme derecesi | seçenek A-E ve öneri
### Zaman çizelgesi
| Tarih-saat | Olay | Kaynak | Önem |
```

---

## Sık hatalar

- 🔴 Teslim belgesini çekincesiz imzalamak ve gizli hasar için 3 günü (deniz) beklemek.
- 🔴 "Haklarımız saklıdır" yazısıyla bir yıllık hak düşürücü sürenin uzadığını sanmak; uzatma karşı tarafın **anlaşmasıyla** olur (m.1188/4) ya da arabuluculuk başvurusu süreyi işletmez (6325 m.18/A/15).
- 🟠 Hasarlı malı karşı tarafa tespit fırsatı vermeden imha etmek.
- 🟠 Bildirimi yalnız acenteye ya da yalnız fiilî taşıyana yapıp kimin taşıyan olduğunu belirlememek (m.1185/6 kolaylık sağlar ama sıfat tartışması sürer).
- 🟡 Upstream'deki ABD kavramlarını ("attorney work product", "FRE 408") Türk dosyasına taşımak (ORTAK-KURALLAR.md §1).

---

