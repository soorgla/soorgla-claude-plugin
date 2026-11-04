# Tarife sınıflandırması (GTİP), BTB ve gümrüklenmiş maliyet

## Ne zaman kullanılır
- "Bu ürünün GTİP'i ne olmalı?", "idare GTİP'i değiştirip ek tahakkuk yaptı".
- Bağlayıcı tarife bilgisi (BTB) istemeli mi, elimizdeki BTB bizi korur mu?
- İthal edilecek eşyanın vergi yükünü (gümrük vergisi, ilave gümrük vergisi, damping, EMY, KDV, ÖTV) önceden görmek (gümrüklenmiş maliyet).

---

## Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| BTB ve BMB | Yazılı talep üzerine Bakanlık ya da yetkilendirdiği gümrük idaresi verir | 4458 m.9/1  |
| Bağlayıcılık | Gümrük idarelerini **yalnız hak sahibine karşı**, yalnız tarife pozisyonu (ya da menşe) konusunda ve yalnız bilginin verildiği tarihten sonra tamamlanacak işlemler için bağlar | m.9/2  |
| İspat yükü | Bilgi alan kişi, beyan ettiği eşya ile bilgide tanımlanan eşya arasında her bakımdan uygunluğu kanıtlamak zorunda | m.9/3  |
| Geçerlilik | BTB veriliş tarihinden itibaren **altı yıl**, BMB **üç yıl**; yanlış/eksik bilgiye dayanan bilgi iptal edilir | m.9/4   |
| Geçersizlik | Tarife cetveli değişikliği, Dünya Gümrük Örgütü izahname/karar değişikliği (RG yayım tarihinden) ya da iptal/değişikliğin tebliği | m.9/5  |
| Kazanılmış hak süresi | Geçersizlikten önce bağlayıcı alım-satım sözleşmesi yapılmışsa altı ay kullanılabilir (lisans/izin belgesinde onun süresi) | m.9/7  |
| Yanlış BTB bilgisinin cezası | m.6 ve 7'ye göre verilen kararlara dayanak belge ve bilgilerin yanlış verilmesi → usulsüzlük cezasının iki katı | m.241/3-a  (Madde numarası kanun metnindeki eski atıf; BTB bugün m.9'da `[doğrula]`.) |
| Tarife unsurlarında aykırılık cezası | Beyan ile muayene sonucu arasında tarife unsurlarında aykırılık ve vergi farkı **%5'i aşarsa** farkın üç katı | m.234/1-a  |

**Vergi oranları:** gümrük vergisi ve ilave gümrük vergisi oranları İthalat Rejimi Kararı ve eklerinde; karar 2026'da birden çok kez değişti. Oranı beceri metninden değil, **beyanname tescil tarihindeki** karar sürümünden al. 

---

## Sınıflandırma adımları (eski YAML akışı, korunarak)

1. **Teknik tanım:** malzeme, işlev, kullanım yeri, monte/demonte, set hâlinde mi, ambalaj. Kullanıcıdan teknik föy, katalog, fotoğraf iste.
2. **Genel Yorum Kuralları (GYK) sırası:** 1 (pozisyon metni ve bölüm/fasıl notları) → 2/a (eksik, monte edilmemiş) ve 2/b (karışım) → 3/a (en belirgin tanım), 3/b (esas nitelik), 3/c (en son pozisyon) → 4 (en çok benzeyen) → 5 (kaplar) → 6 (alt pozisyon) `[model bilgisi — doğrulayın]`. GYK metni Türk Gümrük Tarife Cetvelinde; soorgla'da ne mevzuat ne RG tam metni olarak bulunuyor. Sınıflandırma görüşünde kural numarası ve sırasını kullanıcının ya da Ticaret Bakanlığının güncel TGTC metninden teyit ettir; teyit yoksa çıktıya `[ARAŞTIRMA GEREKLİ: TGTC Genel Yorum Kuralları metni]` yaz. 
3. **İzahname ve sınıflandırma görüşleri:** Armonize Sistem izahnamesi ve Dünya Gümrük Örgütü kararları; soorgla'da yok → kullanıcıdan iste ya da web `[web araması — doğrulayın]`.
4. **BTB taraması:** benzer eşya için BTB var mı? soorgla'da BTB veritabanı **yok** (eski YAML'daki `karar_btb` indeksi hayalîdir); Ticaret Bakanlığı BTB sorgusu → web. 
5. **Danıştay emsali:** `legal_search_cases mahkeme: "danistay"` "<eşya> <pozisyon> tarife uyuşmazlığı".
6. **Önlem kontrolü:** seçilen GTİP'te ilave gümrük vergisi, damping vergisi, EMY, gözetim, kota var mı → `mense-ve-ticaret-politikasi-onlemleri.md`.
7. **Yasak, izin, TAREKS/ürün güvenliği denetimi** → aynı dosya.

---

## Gümrüklenmiş maliyet tablosu (iskelet; oranlar araçtan)

Hesap akışı ve araç (`legal_calculate_tax` `hesap: "gumruk_maliyet"`): `../../gumruk-uygulama/references/gumruklenmis-maliyet.md`. Bu tablo uyuşmazlıkta idarenin tahakkukuyla karşılaştırma iskeletidir.

| Kalem | Matrah | Oran / tutar | Kaynak (RG künyesi, tescil tarihi sürümü) |
|---|---|---|---|
| Gümrük kıymeti (CIF; m.27 ilaveleri) | → `gumruk-kiymeti-ve-geri-verme.md` | | |
| Gümrük vergisi | kıymet | İthalat Rejimi Kararı Ek | |
| İlave gümrük vergisi | kıymet | İthalat Rejimi Kararı | |
| Dampinge karşı vergi / EMY | birim ya da kıymet | ilgili tebliğ/karar | |
| ÖTV | | 4760 listeleri | |
| KDV | kıymet + vergiler + giderler | 3065 | |
| Kur | | `legal_get_exchange_rate` (tescil günü TCMB) | |

KDV/ÖTV matrahı ve indirimi vergi becerisinin konusudur (→ `../../vergi/references/kdv-gvk-kvk-temel-sorular.md`); burada yalnız gümrükte tahakkuk.

---

## Kontrol listesi — "idare GTİP'i değiştirdi"

1. İdarenin dayandığı pozisyon ve gerekçe yazılı mı; laboratuvar raporu var mı (m.243 ikinci tahlil, 15 gün)?
2. Beyan edilen ve idarenin tespit ettiği pozisyonlar için vergi farkı %5'i aşıyor mu (m.234/1-a ceza eşiği)?
3. Elinizde BTB var mı; eşya her bakımdan BTB'deki tanıma uygun mu (ispat sizde, m.9/3); BTB tarihten sonra ve süresi içinde mi?
4. BTB tarife cetveli değişikliğiyle geçersizleşti mi; bağlayıcı sözleşme varsa 6 aylık süre (m.9/7)?
5. Önceki beyannamelerde aynı GTİP idarece kabul edilmiş mi (güven ilkesi argümanı `[incele]`)?
6. Ek tahakkukta hangi kalemler var; ilave vergi ve damping ayrı tartışılmalı.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Ürünün teknik föyü, kullanım amacı, bileşimi? | GYK |
| BTB aldınız mı, tarihi ve numarası? Ürün aynen o mu? | m.9 |
| Daha önceki ithalatlarda hangi GTİP'le beyan ettiniz, sorun çıktı mı? | Güven, seri tahakkuk |
| Menşe ülke ve tedarik rotası? | Önlemler |
| Laboratuvar tahlili yapıldı mı? | m.243 |

---

## soorgla çağrıları

```
legal_list_statute_articles  statute_id: 54479  article_query: "bağlayıcı tarife bilgisi"  include_content: true
legal_get_statute_article  law_no: "4458"  law_type: "Kanun"  article_no: "234" | "241" | "243"
legal_search_official_gazette  query: "İthalat Rejimi Kararı"  search_in: "title"  sort_by: "date_desc"
legal_search_cases  mahkeme: "danistay"  sorgu: "<eşya> tarife pozisyonu sınıflandırma ek tahakkuk"
legal_get_exchange_rate  para_birimi: "USD" | "EUR"  tarih: "<tescil tarihi>"
```

---

## Çıktı iskeleti

```markdown
## Tarife değerlendirmesi — [eşya]
| Aday pozisyon | GYK gerekçesi | Destek (BTB/emsal/izahname) | Vergi ve önlem sonucu | Etiket |
### Öneri: [pozisyon] — güven düzeyi ve riskler
### BTB önerisi (başvuru metni → idari-ve-kurum-basvurulari)
### Gümrüklenmiş maliyet tablosu (oranlar RG'den, tescil tarihi sürümü)
```

---

## Sık hatalar

- 🔴 Başkasına verilmiş BTB'yi bağlayıcı saymak (yalnız hak sahibine karşı, m.9/2).
- 🟠 Vergi oranını eski İthalat Rejimi Kararından vermek.
- 🟠 GTİP önerisini kesin hüküm gibi sunmak; bağlayıcı olan BTB'dir.
- 🟡 İlave gümrük vergisini ve dampingi maliyete katmayı unutmak.

---

## İdare tarafı
- Pozisyon değişikliğinde gerekçeyi GYK sırasıyla yaz, laboratuvar raporunu ve izahname notunu karara ekle.
- Yükümlünün geçerli BTB'si varsa bağlayıcılığını (m.9/2) ve uygunluk ispatını değerlendir.

---

