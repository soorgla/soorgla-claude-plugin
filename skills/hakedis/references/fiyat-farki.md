# Fiyat farkı ve ek fiyat farkı

## Ne zaman kullanılır
- Hakedişteki fiyat farkı hesabı (Pn katsayısı, temel ve güncel endeks, ağırlık katsayıları, B katsayısı) kontrol edilecek.
- Yüklenici fiyat farkının eksik ödendiğini, idare fazla ödendiğini düşünüyor; Sayıştay sorgusu fiyat farkına ilişkin.
- Süre uzatımı, cezalı çalışma ya da yeni birim fiyat nedeniyle hangi ayın endeksinin kullanılacağı tartışmalı.
- Olağanüstü fiyat artışları için kanunla getirilen **ek fiyat farkı** (4735 geçici maddeleri) uygulanabilir mi?

**Önce sor:** ihale ilan tarihi, son teklif tarihi, sözleşme türü, idari şartnamedeki fiyat farkı maddesi (formül ve katsayılar), avans, iş programı ve revize iş programları, süre uzatımı kararları.

---

## 1. Hukuki çerçeve

- Fiyat farkının esas ve usullerini Kamu İhale Kurumunun teklifi üzerine **Cumhurbaşkanı** belirler; sözleşmedeki fiyat farkı esaslarında **sözleşme imzalandıktan sonra değişiklik yapılamaz**.
- Yapım işlerinde uygulanan metin 2013/5217 sayılı BKK eki "4734 Sayılı Kamu İhale Kanununa Göre İhale Edilen Yapım İşlerinde Uygulanacak Fiyat Farkına İlişkin Esaslar"dır. Esasların konsolide madde metni **araçta yok**; karar sayfası ve değişiklik kararları (özellikle CB Kararı 5202, RG 24.02.2022 ve 10132, RG 30.07.2025) RG'den okunur.
- Son değişiklik: Cumhurbaşkanı Kararı 10132 (RG 30.07.2025), yürürlük **1.9.2025**; ilan/duyurusu bu tarihten önce yapılmış ihalelerde ilan tarihindeki Esaslar uygulanır (Esaslar geçici m.3).
- Fiyat farkı ödenen işlerde, fiyat farkı nedeniyle sözleşme bedelinde oluşan artışın %6'sı oranında **ek kesin teminat** alınır; hakedişten kesilebilir.
- Hizmet ve mal alımlarının ayrı Esasları vardır (2013/5215 hizmet, 2013/5216 mal); bu dosya yapım işlerine odaklanır. Mal Esasları araçta "mülga" etiketiyle görünüyor ama 2025'te değiştirildi → etiket hatalı olabilir `[incele]`.

---

## 2. Kontrol listesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ÖNGÖRÜLMÜŞ-MÜ | İdari şartname ve sözleşmede fiyat farkı hesaplanacağı yazıyor mu? Yazmıyorsa kural olarak fiyat farkı ödenmez (kanuni ek fiyat farkı hariç) | 4735 m.8; idari şartname | Sözleşme süresi uzun yapım işlerinde ihale dokümanında fiyat farkı öngörülmesinin zorunlu olduğu KİK kararında aktarılıyor — dayanak Esaslar m.6/1: "sözleşme süresi 365 takvim gününü aşan yapım işlerinde fiyat farkı hesaplanacağına ilişkin düzenlemeye yer verilmesi zorunludur" (5202 ile eklendi; hizmette aynı kural hizmet Esasları m.7/1). |
| ŞARTNAME-SÖZLEŞME | İdari şartnamedeki fiyat farkı maddesi ile sözleşmedeki madde aynı mı? Çelişkide ihale dokümanı esastır | 4735 m.4 | `sozlesme-tasarisi-denetimi.md` |
| FORMÜL | Formüldeki sabit katsayı (a) ve ağırlık katsayılarının (b1, b2, c, d, e, f, g) toplamı 1,00 mi? Hakedişte kullanılan katsayılar şartnamedekiyle birebir aynı mı? | Esaslar m.5/6 | İdare sabit katsayıları toplamı 1,00 olacak şekilde belirleyip her biri için endeksi dokümanda göstermek zorunda; farklı aşamalar için toplamı 1,00 olan farklı katsayı setleri belirlenebilir (m.5/7) |
| TEMEL-ENDEKS | Temel endeks (Io, Ço …) hangi aya ait? | Esaslar m.4/1-ı | Temel endeks **ihale tarihinin içinde bulunduğu aya** ait Endeks Tablosu sayısıdır (çerçeve anlaşmada davet tarihinin ayı; akaryakıtta ihale tarihindeki EPDK satış fiyatı). Eski YAML'daki "bir önceki ay" **yanlıştı**; "bir önceki ay" yaklaşık maliyet güncellemesinin (YİİUY m.11) kuralıdır, karıştırma. |
| GÜNCEL-ENDEKS | Güncel endeks (In) uygulama ayına (imalatın yapıldığı ay) ait mi? Bir ayda birden fazla hakediş düzenlenmiş ve endeks henüz yayımlanmamışsa önceki ayın endeksi kullanılır, yayımlanınca sonraki hakedişte düzeltilir | Esaslar m.6/2 (10132 ile eklenen cümle) | |
| ENDEKS-SERİSİ | Hangi TÜİK serisi (Yİ-ÜFE genel, alt endeksler, CPA 2008 seçilmiş sınıflar tablosu, ana metaller, akaryakıt)? 10132 ile "seçilmiş sınıflar tablosu" eklendi | Esaslar m.4/1-k, m.5/4 | Yİ-ÜFE genel ve alt endekslerini `legal_calculate_tender` fiyat farkı hesapları kendisi okur; seçilmiş sınıflar ve akaryakıt değerlerini kullanıcıdan TÜİK/EPDK tablosuyla iste; `legal_calculate_cpi_change` yalnız TÜFE verir. **İşçilik bileşeni** (Io, In) Esaslarda TÜFE 2003=100 "Genel" sütunudur (m.5/4-a, 5202); bu seri **Ocak 2026'da kesiliyor**, yeni seri 2025=100 — 2026 ve sonrası uygulama aylarında hangi serinin, hangi zincirleme/bağlama ile kullanılacağını Esaslar değişikliği ya da KİK duyurusundan kontrol et `[incele]` |
| B-KATSAYISI | Formüldeki B katsayısı sözleşmede ne yazıyor (0,90 / 1,00)? Hakedişte farklı katsayı kullanılmış mı? | Esaslar m.5/1 (F = An × B × (Pn − 1)); sözleşme | |
| GECİKME-CEZALI | Yüklenici kusuruyla gecikilen kısımlarda hangi endeks? Sözleşme süresi bitmiş ve idarenin izniyle cezalı çalışılan işlerde fiyat farkı Esasların m.7/2 hükmüne göre hesaplanır | Esaslar m.6/10 (10132 ile değişik), m.7/2 | 5202 ile m.6/10'daki karşılaştırma "işin bitmesi gereken tarihin içinde bulunduğu aya ait endeks ile işin fiilen gerçekleştirildiği aya ait endeks" biçimine getirilmişti (2022 metni). |
| SÜRE-UZATIMI | Mücbir sebep ya da idareden kaynaklı gecikme nedeniyle süre uzatımı verildiyse **revize iş programı** düzenlenir; uzatıma sebep olan durumdan önceki döneme ait aylık ödenek dağılımı değiştirilemez; fiyat farkı revize programa göre gerçekleştirilmesi gereken aya göre hesaplanır; revize programa yüklenici kusuruyla uyulmazsa m.7/2 uygulanır | Esaslar m.7/4 (10132 ile değişik, 1.9.2025) | |
| YBF | Sözleşmede birim fiyatı bulunmayan kalem için Genel Şartname m.22'ye göre yeni birim fiyat yapıldıysa: fiyat farkı öngörülen işte ihale ayına; öngörülmeyende proje değişikliği onay ayına (iş bitim tarihinden sonraki değişiklikte iş bitim ayına indirgenmiş) birim fiyat esas | Esaslar m.6/8 (10132 ile değişik) | → `is-artisi-ve-yeni-birim-fiyat.md` |
| AVANS | Avans verilen işte fiyat farkı hesabında avans mahsubu; mahsup edilmemiş avansın Pn ile güncellenmesi | Esaslar; Tip Sözleşme m.13.11 | |
| İHZARAT | Birim fiyatlı işte iş programına uygun ihzar edilen malzemede ihzarat ayı uygulama ayı sayılır | Esaslar | Sayıştay 2. D. K.48286 (06.04.2022) arama özetinde Esaslar m.? alıntısı `[çekildi ama desteği doğrulayın]` |
| ESKİ-KARARNAME | Hesap yürürlükten kalkmış bir kararnameye (ör. 2002/5039) göre mi yapılmış? | Esaslar | Sayıştay'ın kamu zararı saydığı tipik hata |
| ÖDENEK | İdare, revize iş programında ödenek konmayan aylar için fiyat farkını ödenek dilimine göre mi hesapladı? | Esaslar m.7/4; iş programı | Yargıtay 6. HD E.2024/466 K.2025/832 olayında yüklenici bu nedenle eksik ödeme iddia etti; çoğunluk ihtirazi kayıt yokluğundan reddetti (`hakedis-denetimi.md` §3) |

---

## 3. Kanuni ek fiyat farkı (geçici maddeler)

4735'e olağanüstü fiyat hareketleri için geçici maddeler eklenmiştir (geçici m.2-7). Her biri **belirli tarihlerde ihale edilmiş ve belirli dönemde gerçekleştirilen** kısımlara uygulanır; süresi geçmiş olabilir. Olaydaki işin kapsama girip girmediğini madde metninden kontrol et.

- **Geçici m.7 (7491, 27.12.2023):** 1.3.2023'ten önce ihalesi yapılan ve maddenin yürürlüğü itibarıyla geçici kabulü onaylanmamış TL sözleşmeli yapım işlerinde, **1.1.2024–31.12.2024** arasında gerçekleştirilen kısımlar için: fiyat farkı öngörülmüş sözleşmelerde B katsayısı 1,00'e (2985 kapsamı konutta 1,15'e) kadar artırılarak; fiyat farkı öngörülmemiş sözleşmelerde Yİ-ÜFE genel endeksindeki değişimin %15'ine kadar fiyat farkı hesaplanabilir; ayrıca altı ayı geçmemek üzere süre uzatımı verilebilir. Üçüncü ve dördüncü fıkralardaki yetki ibareleri **Anayasa Mahkemesince iptal edildi** (E.2024/54, K.2025/163, 22.07.2025; RG 09.12.2025). İptalin yürürlük tarihi ve iki fıkranın kalan kısımlarının akıbeti `[incele]`.
- **Geçici m.5 ve m.6:** önceki ek fiyat farkı ve devir/fesih imkânları; AYM 2022/32 K.2025/67 geçici m.5/4 ile ilgili karar verdi.
- Ek fiyat farkı "verilebilir" diye düzenlendiyse idarenin takdiri ve uygulama esasları belirleyicidir; yükleniciye otomatik hak doğurmaz `[incele]`.

---

## 4. Hesap kalıbı (girdileri kullanıcıdan al)

```
F = An × B × (Pn − 1) [formül sözleşmeden alınır]
Pn = a × (In/Io) + b1 × (Çn/Ço) + b2 × (Dn/Do) + c × (Yn/Yo) + d × (Kn/Ko) + e × (Mn/Mo) + …
An = uygulama ayında gerçekleştirilen iş tutarı (sözleşme fiyatlarıyla; avans etkisi ayrıca)
```
Sembolleri ve katsayıları **sözleşmedeki fiyat farkı maddesinden** aynen al; yukarıdaki kalıp yalnız yön gösterir `[model bilgisi — doğrulayın]`. Her satıra endeks ayını ve TÜİK tablo adını yaz. Sonuç `[doğrula]`. `legal_calculate_tender` (`fiyat_farki_yapim`; ek fiyat farkı süre uzatımı için `sure_uzatimi_gecici7`) ile hesaplanır; Yİ-ÜFE endekslerini araç okur, şartnamedeki alt endeksi `seriler` ile ver. Araç yanıt vermezse ya da hata dönerse hesap elle yapılır.

---

## 5. Süreler

| Süre | Dayanak | Not |
|---|---|---|
| Fiyat farkına itiraz | Hakedişe itiraz süresiyle aynı (`hakedis-denetimi.md` §3-4) | En sık hak kaybı noktası |
| Endeks yayımlanmadan düzenlenen hakediş | Endeks yayımlanınca sonraki hakedişte düzeltme | Esaslar m.6/2 |
| Geçici m.7 dönemi | 1.1.2024–31.12.2024 arasında gerçekleştirilen kısımlar | 4735 geçici m.7 |

---

## 6. Taraflara göre vurgu

**Yüklenici:** idare kaynaklı gecikmede (yer teslimi, proje onayı, ödenek) süre uzatımının ve revize iş programının fiyat farkına yansıtılması; TÜİK geriye dönük endeks düzeltmesi; her hakedişte ihtirazi kayıt.

**İdare / Sayıştay perspektifi:** eski kararnameyle hesap, yanlış temel endeks, ağırlık katsayılarının şartnameden farklı alınması, cezalı çalışmada yüksek endeks kullanılması, avans etkisinin atlanması, ek kesin teminatın kesilmemesi. Bunlar kişisel kamu zararı sorumluluğuna dönüşebilir → `sayistay-denetim-riski.md`.

---

## 7. Görüşme soruları

| Alan | Soru |
|---|---|
| İhale | İlan tarihi ve son teklif tarihi? İdari şartnamenin fiyat farkı maddesi (formül, katsayılar, B) nedir? |
| Sözleşme | Tür, süre, avans, iş programı ve revize iş programları? |
| Hakediş | Hangi hakedişlerde fiyat farkı ödendi; hangi endeks aylarıyla? İhtirazi kayıt konuldu mu? |
| Gecikme | Süre uzatımı kararları (gerekçe: mücbir sebep / idare kaynaklı)? Cezalı çalışılan dönem var mı? |
| Ek fiyat farkı | İş geçici m.7 (ya da önceki geçici maddeler) kapsamında mı; idare bu yönde karar aldı mı? |

---

## 8. MCP adımları

```
legal_get_statute_article law_no: "4735" law_type: "Kanun" article_no: "8" | "12"
legal_get_statute_article law_no: "4735" law_type: "Kanun" article_kind: "gecici" article_no: "5" | "6" | "7"
legal_search_official_gazette query: "Yapım İşlerinde Uygulanacak Fiyat Farkına İlişkin Esaslar" search_in: "title" sort_by: "date_desc"
legal_get_official_gazette_document url: "<ilan tarihinde yürürlükteki son değişiklik>"
legal_search_cases mahkeme: "yargitay" daire: "6. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "kamu ihale yapım işi süre uzatımı verilmesine rağmen fiyat farkının revize iş programına göre eksik hesaplanması"
legal_search_cases mahkeme: "sayistay" sorgu: "fiyat farkı yanlış temel endeks fazla ödeme kamu zararı yapım işi"
legal_search_cases mahkeme: "anayasa" sorgu: "4735 sayılı Kanun geçici madde ek fiyat farkı"
legal_calculate_cpi_change baslangic: "<…>" bitis: "<…>" # yalnız TÜFE; işçilik bileşeni ya da kaba kontrol
```

---

## 9. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …
## Fiyat farkı denetimi — [işin adı] — [yüklenici / idare]
### Sonuç
[Hesap doğru / hatalı — fark … TL [doğrula]; kaynak hata: …]
### Uygulanan esaslar
| İlan tarihi | Esaslar sürümü (2013/5217 + değişiklikler) | Formül | B | Ağırlıklar toplamı |
### Endeks tablosu
| Bileşen | Temel endeks (ay, değer) | Güncel endeks (ay, değer) | Oran | Kaynak tablo |
### Hesap
| Hakediş | An | Pn | F (sözleşme) | F (hakediş) | Fark |
### Bulgular
[her satır: işaret + dayanak + mali etki]
### Ek fiyat farkı
[kapsamda mı; dönem; idare kararı; AYM iptali notu]
```

---

## 10. Sık hatalar
- Fiyat farkı katsayısını TÜFE ile hesaplamak (`legal_calculate_cpi_change` sonucu Pn değildir).
- Sözleşme imzalandıktan sonra esasları "güncel" metne göre değiştirmek (4735 m.8/2 yasaklar).
- İlan tarihindeki Esaslar yerine hakediş tarihindeki Esasları uygulamak.
- Süre uzatımında revize iş programı yapmadan eski programın aylarına göre hesaplamak.
- Geçici m.7'yi 2024 dışındaki imalata ya da 1.3.2023 sonrası ihalelere uygulamak.
- Ek kesin teminatı (%6) kesmeyi unutmak.

## Eski YAML'dan düzeltilenler
- YAML "Esaslar m.8 — fiyat farkı verilmeyecek denmişse bile mücbir sebep/idare kaynaklı süre uzatımında fiyat farkı ödenmesi zorunludur" diyordu; bu kural araçta doğrulanamadı. Güncel Esaslar m.7/4 yalnız **fiyat farkı hesaplanan** işlerde revize iş programını düzenliyor → iddia `[model bilgisi — doğrulayın]` olarak kaldı.
- YAML temel endeks, B katsayısı ve katsayı toplamı kurallarını madde numarasıyla kesin yazıyordu. 2026-11-02'de CB Kararı 5202 metninden düzeltildi: katsayı toplamı m.5/6 (YAML "m.5"), temel endeks **ihale tarihinin içinde bulunduğu ay** (YAML "bir önceki ay" diyordu, yanlış). B değeri sözleşmeden alınır.
- YAML'da 2025 değişiklikleri (10132) ve 7491 geçici m.7 ile AYM iptali yoktu; eklendi.
- YAML "Research Agent ile TÜİK/TCMB verisi çek" diyordu; ayrı endeks aracı yok: Yİ-ÜFE genel ve alt endeksleri `tcmb_fiyat_endeksleri`'nde, katsayı → seri eşlemesi `ihale_fiyat_farki_endeks_esleme`'de; `fiyat_farki_yapim` `ihale_ayi`/`uygulama_ayi` ile okur. EPDK akaryakıt ve dört basamaklı seçilmiş sınıflar kullanıcıdan.
