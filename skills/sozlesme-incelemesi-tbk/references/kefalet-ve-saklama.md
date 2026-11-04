# Kefalet, garanti ve saklama sözleşmeleri

Kişisel güvence sözleşmeleri (kefalet, gerçek kişinin verdiği garanti) ve saklama (vedia) sözleşmeleri.

## Ne zaman kullanılır
- Kredi, kira, bayilik ya da tedarik sözleşmesine eklenen kefalet; "müteselsil kefil", "garantör", "şahsi teminat", "eşimin rızası gerekir mi", "kefaletim ne zaman biter".
- Emanet, depo, ardiye, otel ya da otopark sorumluluğu.
- Kira sözleşmesindeki kefalet: şekil denetimi burada, kira ilişkisi `../../kira-hukuku/SKILL.md`'de.

---

## 1. Kefalet — önce şekil (geçerlilik)

Kefalet en sık **şekil eksikliğinden** geçersiz olan sözleşmedir. Her incelemede ilk iş:

| Kod | Kontrol | Dayanak | Sonuç |
|---|---|---|---|
| YAZILI | Sözleşme yazılı mı? | TBK m.583/1 | Değilse geçersiz 🔴 |
| AZAMİ-MİKTAR | Kefilin sorumlu olacağı **azami miktar** belirtilmiş mi ve **kefilin kendi el yazısıyla** mı? | TBK m.583/1 | Eksikse geçersiz 🔴 |
| TARİH | **Kefalet tarihi** kefilin el yazısıyla mı? | TBK m.583/1 | Eksikse geçersiz 🔴 |
| MÜTESELSİL | Müteselsil kefalet isteniyorsa "müteselsil kefil" ya da aynı anlama gelen ifade **kefilin el yazısıyla** mı? | TBK m.583/1 | Yoksa en fazla **adi kefalet** |
| YETKİ-VAAT | Kefil olmak için özel yetki verilmesi ve kefil olma vaadi de aynı şekle tabi | TBK m.583/2 | |
| SONRADAN-ARTIŞ | Sorumluluğu artıran sonraki değişiklikler aynı şekle uyulmadıkça hüküm doğurmaz | TBK m.583/3 | Ek protokolde kefil yeniden el yazısıyla imzalamalı |
| EŞ-RIZASI | Kefil evliyse (mahkemece ayrılık kararı ya da yasal ayrı yaşama hakkı yoksa) **eşin yazılı rızası**, sözleşmeden önce ya da en geç kuruluş anında | TBK m.584/1 | Eksikse geçersiz 🔴 |
| EŞ-RIZASI-İSTİSNA | Rıza aranmaz: ticaret siciline kayıtlı işletme sahibinin ya da ticaret şirketinin ortak/yöneticisinin **işletme veya şirketle ilgili** kefaleti; esnaf ve sanatkârın mesleki kefaleti; 5570 s. Kanun kredileri; tarım kredi ve benzeri kooperatif kredileri | TBK m.584/3 (Ek: 6455/77) | İstisna dar yorumlanır; şirket ortağının şirket dışı borca kefaleti istisna dışında `[incele]` |
| EŞ-RIZASI-DEĞİŞİKLİK | Miktarı artırmayan, adi kefaleti müteselsile çevirmeyen, güvenceleri önemli ölçüde azaltmayan değişikliklerde rıza gerekmez | TBK m.584/2 | |
| KİŞİSEL-GÜVENCE | Gerçek kişinin "garanti", "taahhütname", "aval dışı şahsi teminat" adıyla verdiği güvence de kefalet şekline, ehliyetine ve eş rızasına tabi | TBK m.603 | Adı "garanti sözleşmesi" diye kurtulmaz |
| TÜKETİCİ | Tüketicinin edimine karşılık alınan şahsi teminat, adı ne olursa olsun **adi kefalet** sayılır | 6502 m.4/6 | Müteselsil ibaresi tüketici aleyhine işlemez |

**Emsal (son 3 yıl, özet):** el yazısı şartının geçerlilik şartı olduğu ve azami miktar ile tarihin el yazısıyla yazılmadığı kira kefaletinin geçersiz olduğu — [Yargıtay 3. HD E.2025/1363 K.2025/5066, 22.10.2025]; ifadelerin hepsinin aynı kişi (kefil olmayan biri) tarafından yazılmasının şekli karşılamadığı — [Yargıtay 11. HD E.2023/4008 K.2024/7223, 08.10.2024]. `[çekildi ama desteği doğrulayın]` — yalnız arama özetleri okundu; dilekçede kullanmadan önce tam metin `legal_get_case_document` ile okunmalı. 

## 2. Kefalet — içerik

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TÜR | Adi kefalette alacaklı önce borçluya başvurur; doğrudan kefile ancak: kesin aciz belgesi, Türkiye'de takibin imkânsızlığı/önemli güçlüğü, borçlunun iflası, konkordato mehli | TBK m.585/1 | Rehin varsa adi kefil önce rehne gidilmesini isteyebilir (iflas/konkordato hariç) |
| MÜTESELSİL-TAKİP | Müteselsil kefilde alacaklı borçluyu ya da taşınmaz rehnini takip etmeden kefile gidebilir; **ama** borçlunun ifada gecikmesi **ve ihtarın sonuçsuz kalması** ya da açık ödeme güçsüzlüğü şart; teslime bağlı taşınır rehni ya da alacak rehni varsa önce rehin paraya çevrilir (istisnalar: hâkim tespiti, iflas, konkordato mehli) | TBK m.586 | Eski YAML "borçlu gecikmişse doğrudan kefile" diyordu; ihtar şartını atlıyordu |
| AZAMİ-SINIR | Kefil her durumda belirtilen azami miktarla sınırlı sorumlu; faiz ve takip giderleri bu sınırı aşamaz | TBK m.589 |  |
| GÜVENCE-AZALTMA | Alacaklının diğer güvenceleri kefil zararına azaltması | TBK m.592 |  |
| BİLDİRİMSİZ-ÖDEME | Kefilin borçluya bildirmeden ödemesi ve rücu kaybı | TBK m.597 |  |
| ON-YIL | Gerçek kişinin verdiği her türlü kefalet kuruluştan itibaren **10 yıl geçmekle kendiliğinden** sona erer; daha uzun süreli verilmiş olsa da kefil ancak 10 yıl dolana kadar takip edilebilir; uzatma, en erken sona ermeden 1 yıl önce, kefalet şekline uygun yazılı açıklamayla, azami 10 yıllık yeni dönem için | TBK m.598/3-5 | Zamanaşımı değil, sona erme. Uzun vadeli kredi ve kira sözleşmelerinde takvime yaz |
| ASIL-BORÇ | Asıl borç hangi sebeple olursa olsun sona erince kefil de kurtulur | TBK m.598/1 | |
| DAMGA | Kefalet bedeli üzerinden damga vergisi | 488 s. Kanun | Oran yazma `[doğrula]` |

### Garanti sözleşmesi ile ayrım
Garanti (TBK m.128) borçlunun borcuna bağlı değildir, bağımsız bir edim üstlenilir; kefalet ise asıl borca fer'idir. Tüzel kişinin verdiği bağımsız garanti şekle tabi değildir; **gerçek kişi** veriyorsa TBK m.603 nedeniyle kefalet şekli uygulanır. Nitelendirme tartışmalıysa `[incele]`. 

## 3. Saklama (vedia)

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| GERİ-İSTEME | Süre belirlenmiş olsa bile saklatan **her zaman** geri isteyebilir; saklayanın süreye göre yaptığı masraflar ödenir | TBK m.564 | Geri istemeyi engelleyen ya da cezaya bağlayan kayıt riskli |
| KULLANMA | Saklayan izinsiz kullanamaz; izinsiz kullanımda beklenmedik hâlden de sorumluluk | TBK m.563 |  |
| GİDER | Saklatanın zorunlu giderleri ve kusursuz saklayanın zararlarını karşılaması | TBK m.562 |  |
| MİSLİ-ŞEY | Paranın aynen değil mislen geri verilmesi (açıkça ya da örtülü; mühürsüz ve açık bırakılan para) kararlaştırılmışsa yarar ve hasar saklayana geçer; diğer misli eşya ve kıymetli evrakta tasarruf için açık yetki gerekir | TBK m.570 |  → `odunc-ve-yabanci-para.md` |
| OTEL | Otel, motel, pansiyon, tatil köyü işletenlerinin konaklayanın eşyasından sorumluluğu; kurtuluş beyyinesi; kusur yüklenmedikçe kişi başına **günlük konaklama ücretinin üç katı** sınırı | TBK m.576 | |
| OTOPARK | Garaj, otopark işletenlerinin sorumluluğu; kusur yüklenmedikçe **günlük saklama ücretinin on katı** sınırı; "sorumluluk kabul edilmez" ilanı sorumluluğu kaldırmaz | TBK m.579 | Tabelada sorumsuzluk ibaresi → KIRMIZI |
| TİCARİ | Ticari saklama, ardiye (TTK); ticari saklama davaları güncel iş bölümünde ticaret dairesinde | TTK m.4; BGK 2026/1 |  |

## 4. Kimin adına?
- **Kefil:** el yazısı ve eş rızası eksikliği, azami miktarın aşılması, 10 yıllık sona erme, alacaklının güvenceleri azaltması, adi kefalette önce borçluya başvurma.
- **Alacaklı:** el yazısıyla azami miktar, tarih ve "müteselsil kefil" ibaresi; eş rızasının **kuruluştan önce ya da en geç kuruluşta** yazılı alınması; 10 yıllık süreyi izleme; teslime bağlı rehin varsa sırayı bilme.
- **Saklayan:** gider ve zararların karşılanması, hapis hakkı, sorumluluğun kusurla sınırlanması.
- **Saklatan:** her zaman geri isteme hakkı, izinsiz kullanım yasağı, üçüncü kişi haczinde bildirim yükümlülüğü.

## 5. Görüşme soruları
1. Kefil gerçek kişi mi şirket mi? Evli mi; eşinin yazılı rızası ne zaman alındı?
2. Kefalet metninde azami miktar, tarih ve müteselsillik **kefilin el yazısıyla** mı? (Metnin fotoğrafını isteyin.)
3. Kefil tacir mi, şirket ortağı/yöneticisi mi; kefalet şirketle ilgili mi?
4. Kefalet ne zaman verildi (10 yıl)? Sonradan değişiklik/ek protokol var mı?
5. Asıl borç için rehin var mı; türü (taşınmaz, teslime bağlı taşınır, alacak)?
6. Asıl borçluya ihtar çekildi mi?

## 6. MCP adımları
```
legal_get_statute_article  law_no: "6098"  article_no: "128" | "583" | "584" | "585" | "586" | "589" | "592" | "597" | "598" | "603"
legal_get_statute_article  law_no: "6098"  article_no: "562" | "563" | "564" | "570" | "576" | "579"
legal_get_statute_article  law_no: "6502"  article_no: "4"
legal_search_cases  mahkeme: "yargitay"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "kefalet sözleşmesinde eşin yazılı rızası sözleşmeden sonra alındığı için kefalet geçersizdir"
legal_get_case_document  belge_id: "<seçilen>"
```
Daire: kefalet tek başına genel sözleşme dairesinde; ticari kredi, bankacılık ve kira kefaletleri asıl ilişkinin dairesine gidebilir — güncel BGK kararından teyit et.

## 7. Çıktı iskeleti
```markdown
### Kefalet şekil kontrolü
| Şart | Var mı | El yazısı mı | Dayanak | Sonuç |
|---|---|---|---|---|
| Yazılı şekil | | — | TBK 583/1 | |
| Azami miktar | | | TBK 583/1 | |
| Kefalet tarihi | | | TBK 583/1 | |
| Müteselsillik ibaresi | | | TBK 583/1, 586 | |
| Eş rızası (tarih) | | — | TBK 584 | |
**Kefaletin türü:** adi / müteselsil · **Sona erme tarihi (10 yıl):** [tarih] · **Sonuç:** geçerli / geçersiz / tartışmalı `[incele]`
```

## 8. Sık hatalar
- Matbu kefalet formunda daktilo ile yazılmış azami miktarı yeterli saymak.
- Eş rızasını sözleşmeden sonra almak.
- Şirket ortağının her türlü kefaletini eş rızasından muaf saymak (yalnız şirketle ilgili olanlar).
- Gerçek kişinin "garanti" adıyla verdiği güvenceyi şekilden muaf saymak (TBK 603).
- Müteselsil kefile ihtarsız başvurmak; taşınır rehni varken önce kefile gitmek.
- 10 yıllık süreyi zamanaşımı sanıp kesme/durma hükümlerini uygulamak.
- Otel veya otoparkın "sorumluluk kabul edilmez" ilanını geçerli saymak.

---

