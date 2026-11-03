# Taşınmaz edinimi öncesi tapu incelemesi, satış vaadi ve Hazinenin sorumluluğu

## Ne zaman kullanılır
- "Bu evi alacağım, tapusunu kontrol eder misin?", "takyidatta ipotek ve haciz var, ne yapmalıyım?", "satış vaadi sözleşmesi imzaladık, tapuya şerh ettirelim mi?", "kat irtifaklı daire alıyorum".
- Tapu müdürlüğünün hatası ya da mahkeme kararıyla tapunun iptali yüzünden zarar (TMK 1007).
- Arabuluculuk anlaşma belgesiyle tapuda tescil.
- **Yönlendirmeler:** satış, satış vaadi, bağışlama, trampa **sözleşme metni** incelemesi → `../../sozlesme-incelemesi-tbk/references/satis-trampa-bagislama.md`; konut alımında tüketici hakları ve ön ödemeli konut → `../../tuketici/SKILL.md`; imar durumu, ruhsat ve iskân → `../../idare-davalari-imar/references/imar-plani-ruhsat-ve-donusum.md`; yabancı alıcı → `yabancilar-vatandaslik` (aynı dalgada); tapu harcı ve vergi → `../../vergi/SKILL.md`; ipotek/haciz takibi → `../../icra-iflas/SKILL.md`.

Bu dosyadaki kategori bazlı inceleme, upstream `corporate-legal/diligence-issue-extraction` becerisindeki "kategoriye göre çıkar, önem süzgecinden geçir, bulguyu tek satırda yaz" akışından uyarlandı.

---

## Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| Şekil | Mülkiyeti devir amaçlı sözleşme resmî şekil; resmî senedi tapu sicil müdürlüğü düzenler | TMK m.706; 2644 m.26 |
| Satış vaadi | Noterde düzenleme şeklinde; istemle tapuya şerh edilir, şerh sonraki malikleri bağlar; şerhten itibaren beş yıl içinde satış yapılmazsa resen terkin | 2644 m.26; TBK m.237 | |
| Uzaktan resmî senet | Taraflar farklı tapu müdürlüklerinde ya da yurt dışı teşkilatında ise iradeler ayrı ayrı alınabilir (7181) | 2644 m.26 | |
| Değerleme raporu | SPK/BDDK yetkili değerleme kuruluşlarının konut finansmanı ve sermaye piyasası raporları TKGM'ye elektronik gönderilir (7579) | 2644 ek m.4 | |
| Sicilin açıklığı | Kimse tapu sicilindeki bir kaydı bilmediğini ileri süremez | TMK m.1020 | |
| Aile konutu şerhi | Malik olmayan eş şerh isteyebilir; şerh olmasa da açık rıza aranır | TMK m.194 | |
| Arabuluculukla tescil | 18/B kapsamında taşınmaz devri ya da sınırlı aynî hak kuran anlaşma belgesine icra edilebilirlik şerhi alındıktan sonra taraflardan biri tapudan tescil isteyebilir; tapu müdürlüğü mevzuat incelemesini yapar, resmî senet düzenlenmeden tescil eder | 6325 m.18/B-3, 18/B-5 (7531/26) | |
| Kooperatif | Etaplar hâlinde inşaat yapan yapı kooperatifi tüm inşaatlar bitmeden tahsis ettiği konutun tapusunu devredemez (7579) | 1163 ek m.6 | |
| Devletin sorumluluğu | Tapu sicilinin tutulmasından doğan bütün zararlardan Devlet sorumlu; kusurlu görevliye rücu; dava sicilin bulunduğu yer mahkemesinde | TMK m.1007 | |

### TMK 1007 tazminatı — notlar
- Sorumluluk kusursuzdur; şartlar: sicilin tutulmasına ilişkin işlem/eylem, zarar, illiyet; zarar görenin illiyeti kesen kusuru sorumluluğu kaldırır. Beyanlar hanesindeki şerhi (ör. orman tahdidi) görerek alan kişide çoğunluk illiyetin kesildiğini kabul etti; karşı oy kusursuz sorumluluğu öne çıkarıyor `[incele]`.
- Davalı Hazine; görevli mahkeme ve temyiz dairesi (2026/1'e göre 5. HD) `[doğrula]`.
- **Zamanaşımı:** madde metninde özel süre yok; 5. HD, mülkiyet kaybının (tapu iptal kararının) kesinleştiği tarihten itibaren TBK m.146'daki 10 yıllık genel zamanaşımını uyguluyor. 18.11.2009 tarihli HGK kararından (2009/4-383 E., 2009/517 K.) önce süresi dolmuş olanlar için ise makul süre içinde dava açılması aranıyor (AYM Yaşar Çoban, 2014/6673). Somut dosyada kesinleşme tarihini ve zamanaşımı definin süresinde ileri sürülüp sürülmediğini kontrol et `[incele]`.

---

## Kontrol listesi — alım öncesi inceleme

Her kategoride bulguyu tek satır yaz: **ne var → neden önemli → ne yapılmalı → önem**.

| Kategori | Kontrol | Önem kuralı |
|---|---|---|
| Malik ve pay | Satıcı tek malik mi, paylı mı, elbirliği (mirasçılar) mı? Veraset ilamı ve intikal yapıldı mı? Kısıtlılık, vekâletle satış (vekâletname tarihi, özel yetki) | Elbirliğinde tüm mirasçılar; vekâlette noterden doğrulama 🟠 |
| Rehin | İpotek (derece, lehtar, tutar), terkin taahhüdü ve bedelin bankaya ödenmesi sırası | Terkinsiz devir 🔴 |
| Şerhler | Haciz, ihtiyati haciz, ihtiyati tedbir, satış vaadi şerhi, kira şerhi, önalım/geri alım şerhi, aile konutu şerhi, kat karşılığı sözleşme şerhi | Tedbir ve haciz 🔴; satış vaadi ve aile konutu 🔴 |
| Beyanlar | Riskli yapı, yapı kayıt belgesi (imar barışı), orman/mera/kıyı tahdidi, kültür varlığı tescili, yönetim planı | Riskli yapı ve tahdit 🔴; yapı kayıt belgesi 🟠 |
| İrtifaklar | Geçit, mecra, intifa, oturma hakkı, üst hakkı | İntifa/oturma 🟠 |
| Nitelik | Ana taşınmaz/bağımsız bölüm; arsa, kat irtifakı, kat mülkiyeti; tapudaki nitelik ile fiilî kullanım (mesken/işyeri) | Kat irtifakında iskân yok 🟠; meskende işyeri → KMK m.24 |
| Paylı mülkiyette | Diğer paydaşların önalım hakkı (TMK 732-734) | Payın üçüncü kişiye satışında önalım riski 🟠 → `onalim-hakki.md` |
| İmar ve yapı | İmar durumu, ruhsat, iskân, kaçak kat, 6306 süreci | → idare-davalari-imar |
| Kira | Kiracı var mı; yeni malikin ihtiyaç ve süre kuralları | → kira-hukuku |
| Aidat ve borç | Yönetimden borç yazısı; KMK m.22 kanuni ipotek riski (mahkemece tespit edilen gider borcu için bağımsız bölüme diğer malikler lehine tescil; alacak öncelikli) | 🟡 |
| Bedel | Tapuda gösterilen bedel ile gerçek bedel; düşük beyanın vergi ve önalım sonucu | Önalımda 7571 sonrası rayiç bedel esas → risk azaldı ama vergi riski `[incele]` |
| Yabancı alıcı | 2644 m.35 kısıtları, askeri yasak bölge | → yabancilar-vatandaslik |

**Satış vaadi ve kat karşılığı alıcısı için:** sözleşme noterde düzenleme şeklinde mi; tapuya şerh edildi mi (beş yıllık şerh süresi); yüklenicinin edimi ne aşamada (→ `kat-karsiligi-insaat-uyusmazliklari.md`).

---

## Süre tablosu

| İşlem | Başlangıç | Süre | Dayanak |
|---|---|---|---|
| Satış vaadi şerhinin kendiliğinden düşmesi | Şerh tarihi | Beş yıl | 2644 m.26 |
| Önalım hakkının düşmesi (alıcı açısından) | Noter bildirimi / satış | Üç ay / bir yıl | TMK m.733 (7571) → `onalim-hakki.md` |
| TMK 1007 davası | Zararın kesinleşmesi `[incele]` | Tartışmalı | Yukarıdaki not |

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Tapu kaydı ve takyidat belgesi (güncel, tarihli) paylaşılabilir mi? | İncelemenin tabanı |
| Satıcı kim; vekâletle mi satıyor; mirasçılar arasında intikal yapıldı mı? | Yetki |
| Bedel nasıl ödenecek (kredi, nakit, takas); ipotek terkini kimin üstünde? | Sıra ve risk |
| Taşınmazda oturan var mı (kiracı, eş, paydaş)? | Teslim, aile konutu |
| İskân/yapı kayıt belgesi; imar durumu; riskli yapı beyanı? | Kullanım ve değer |
| Alıcı yabancı mı, şirket mi? | 2644 m.35 |

---

## İdare tarafı (tapu müdürlüğü)

- Resmî senet öncesi: kimlik ve vekâlet doğrulaması (noter sorgusu), kısıtlılık, aile konutu şerhi, haciz/tedbir ve şerh kontrolü; eksiklik varsa işlemi durdurup yazılı gerekçe.
- Arabuluculuk anlaşma belgesiyle tescilde (6325 m.18/B-5): şerhin taşınmazın bulunduğu yer sulh hukuk mahkemesinden alınmış olması, taşınmaza ilişkin kanuni sınırlamaların (tarım arazisi bölünmezliği, yabancı edinimi, imar) uygulanması.
- Hata hâlinde: TMK 1007 sorumluluğu kusursuz; personel rücuu kusura bağlı. İç değerlendirme ile ilgiliye verilecek cevabı ayır (ORTAK-KURALLAR.md §1).

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4721" law_type: "Kanun" article_no: "194" | "706" | "1007" | "1009" | "1020"
legal_get_statute_article law_no: "2644" law_type: "Kanun" article_no: "26" | "35"
legal_list_statute_articles law_no: "2644" law_type: "Kanun" article_kind: "ek" include_content: true # ek m.4 (7579)
legal_list_statute_articles statute_id: 69230 article_query: "ortaklığın giderilmesi" include_content: true # 6325 m.18/B
legal_get_statute_article law_no: "6098" law_type: "Kanun" article_no: "237"
legal_search_cases mahkeme: "yargitay" daire: "5. Hukuk Dairesi" sorgu: "<tapu sicilinin tutulmasından doğan zarar TMK 1007 tazminat>" tarih_baslangic: "<son 3 yıl>"
legal_search_cases mahkeme: "yargitay" daire: "7. Hukuk Dairesi" sorgu: "<taşınmaz satış vaadi sözleşmesine dayalı tapu iptali tescil>"
legal_search_admin_guidance sorgu: "<tapu harcı / KDV konusu>" kurum: "Gelir İdaresi Başkanlığı" belge_tur: "ozelge"
```

---

## Çıktı iskeleti

```markdown
## Taşınmaz inceleme raporu — [il/ilçe/ada/parsel/bb] — [alıcı adına]
### Sonuç: alınabilir / şartlı / alınmamalı (tek paragraf)
### Bulgular
| Kategori | Ne var | Neden önemli | Ne yapılmalı | Önem |
### Kapanış listesi (işlem günü)
- [ ] İpotek terkin yazısı - [ ] Haciz/tedbir kaldırma - [ ] Aile konutu rızası - [ ] Önalım riski notu - [ ] Vergi/harç hesabı (mali müşavir)
### Eksik belgeler
```

---

## Sık hatalar

- 🔴 Takyidatı satış gününden önce yeniden almamak (arada konan haciz/tedbir).
- 🔴 Noter satış vaadini tapuya şerh ettirmemek; ya da beş yıllık şerh süresini izlememek.
- 🟠 Paylı taşınmazda payın üçüncü kişiye satışında önalım riskini anlatmamak.
- 🟠 Beyanlar hanesindeki şerhi (orman, riskli yapı) görmeyip sonra 1007 tazminatına güvenmek.
- 🟡 Tapuda bedelin düşük gösterilmesini "önalımdan korur" diye önermek (7571 sonrası rayiç bedel; vergi riski).

---

## Kaynak ve uyarlama

- `analysis/ownership_transfer/sales_contract.yaml` — guardrail `FORMAL-VALIDITY-REAL-ESTATE` (resmî şekil, satış vaadinin noterde düzenleme şekli) ve `offense` stratejisindeki mülkiyetin saklı tutulması notu; tüketici ve ayıp kısmı tuketici ve sozlesme-incelemesi-tbk'da.
- `analysis/ownership_transfer/donation_contract.yaml` — `FORMAL-VALIDITY-CHECK` (taşınmaz bağışında resmî şekil), `TIME-LIMIT-REVOCATION` (geri alma süresi; dava → `tapu-iptali-ve-tescil.md`).
- `analysis/ownership_transfer/exchange_contract.yaml` — `FORMAL-OFFICIAL-DEED` (trampada resmî senet), `LIABILITY-DEFECT-EVICTION` ve "zapt riski: tapuda rehin, haciz, şerh kontrolü" → yukarıdaki kategori tablosu.
- **Düzeltilen:** trampa YAML'ındaki "sadece noterde yapılan trampa sözleşmeleri taşınmaz mülkiyetini devretmez" doğru; ancak noterde düzenleme şeklindeki satış vaadi geçerli bir borç sözleşmesidir ve şerhle üçüncü kişilere karşı korunur (2644 m.26). YAML'larda 1007, aile konutu şerhi, arabuluculuk belgesiyle tescil (7531) ve 7579 değişiklikleri yoktu; eklendi.
- Upstream: `corporate-legal/diligence-issue-extraction` (kategori ve önem süzgeci).
