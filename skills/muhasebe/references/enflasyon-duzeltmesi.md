# Enflasyon düzeltmesi (VUK mük.298/A, geçici m.33 ve m.37)

> **Kapsam:** düzeltmenin **vergi etkisi** (yapılacak mı, VUK mük.298 düzeltmesinin vergi sonucu ne). Mizan düzeyinde tam düzeltme tablosu bu dosyanın kapsamında değil. `legal_calculate_tax` içinde `enflasyon_duzeltmesi` hesabı henüz **yok**. Şimdilik: yapılıp yapılmayacağını madde ve tebliğden belirle; yapılacaksa katsayıları kullanıcının verdiği endeksle **elle** kur ve her sayıyı `[doğrula]` işaretle.

## Ne zaman
- "Bu yıl (ya da bu geçici dönemde) enflasyon düzeltmesi yapacak mıyız?"
- "2023 sonu düzeltmesinden çıkan geçmiş yıl kârı/zararı ne olacak?"
- Altın/gümüş işi yapan müşteri (mük.298/A-9) — her dönem düzeltme yükümlülüğü.
- Düzeltme katsayısı / taşıma katsayısı nasıl hesaplanır.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Hesap dönemi ve geçici dönem | Geçici m.37 / m.33 dönemleri | Sor |
| Mükellef niteliği: bilanço esası mı, A-9 (münhasıran işlenmiş altın/gümüş) mı, geçici 33/4 finans sektörü mü, tasfiye/iflas | Erteleme kimlere uygulanmaz | Sor |
| Özel hesap dönemi | Erteleme yılları farklı | Sor |
| Düzeltmeye esas tarih ve kalem (parasal olmayan kıymet) | Katsayının paydası (mük.298/A-3) | Mizan ve kayıt tarihleri |
| Yİ-ÜFE endeks değerleri (ilgili aylar) | Katsayı | **Kullanıcıdan iste** (TÜİK / EVDS); aşağıdaki araç bunu vermiyor |

## Araç çağrıları

Hesap aracı yok. Kullanılabilecekler ve sınırları:

```json
{ "hesap": "enflasyon_duzeltmesi", "girdi": {} }
```
→ araç bu hesabın henüz olmadığını söyler; çıktıya "hesap aracı yok — elle hesap" yaz.

```json
legal_calculate_cpi_change { "baslangic": "2024-12-31", "bitis": "2025-12-31" }
```
→ **TÜFE** değişim yüzdesi döndürür (aracın açıklaması "TÜFE"; yanıt yalnız `degisim_yuzdesi`, endeks değeri yok). mük.298/A-2-f fiyat endeksi olarak **ÜFE**'yi, VUK GT 555 katsayılarda **Yİ-ÜFE**'yi kullanır. TÜFE ile katsayı kurma; bu araç düzeltmede **kullanılmaz**. Yİ-ÜFE endeksini kullanıcıdan iste.

## Hukuki çerçeve

- **Şart:** bilanço esasındaki GV/KV mükellefleri, fiyat endeksindeki artış maddedeki iki eşiği (son üç dönem ve içinde bulunulan dönem) birlikte aştığında mali tablolarını düzeltir; geçici vergi dönemlerinde de; Cumhurbaşkanı eşikleri değiştirebilir. Eşikleri madde metninden oku. [Vergi Usul Kanunu m. mükerrer 298](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Tanımlar:** parasal / parasal olmayan kıymet, düzeltme katsayısı (mali tablonun ait olduğu ayın endeksi ÷ düzeltmeye esas tarihi içeren ayın endeksi), taşıma katsayısı, enflasyon düzeltme hesabı; fiyat endeksi "Üretici Fiyatları Genel Endeksi". [Vergi Usul Kanunu m. mükerrer 298](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Düzeltmeye esas tarihler** (A-3), reel olmayan finansman maliyeti (A-4), fark hesapları ve öz sermaye farkları (A-5), amortismanların düzeltilmiş değerden hesabı (A-6), aradan sonra yeniden başlama (A-7), A-9 altın/gümüş, A-10 yatırımlar hesabındaki farkların özel fonu (7529/11).
- **Uygulama tebliği:** VUK GT 555 (RG 30.12.2023, 32415 2. mük.) — 2023 sonu bilançosu (Üçüncü Bölüm) ve 2024 ve sonrası (Dördüncü Bölüm); taşıma katsayısı m.35, düzeltme katsayısı m.36, Yİ-ÜFE ile. [VUK GT 555](https://soorgla.com/mevzuat/40611-vergi-usul-kanunu-genel-tebligi-sira-no-555/) [soorgla]

### Hangi dönemde yapılır / yapılmaz

| Dönem | Durum | Dayanak |
|---|---|---|
| 2022 ve 2023 geçici dönemleri | Yapılmadı; (Ç) bakımından şart oluşmamış sayılır | geçici m.33/1-2 |
| 31.12.2023 bilançosu | Şarta bakılmaksızın düzeltildi; fark geçmiş yıllar kâr/zararında, vergilendirilmez / zarar sayılmaz | geçici m.33/3 |
| 2024 geçici dönemleri | VUK GT 560 ve 563 ile yapılmayabildi | VUK GT 582 m.3/4 atfı |
| 2024 hesap dönemi sonu | Kapsamdaki tüm mükelleflerce yapıldı | VUK GT 582 m.3/4 |
| 2025 1-3. geçici dönemler | Yapılmaz (Bakanlık yetkisi, A-8-b) | VUK GT 582 m.3/1 |
| 2025/4. geçici dönem | Yapılmaz | VUK GT 587 (RG 24.12.2025) `[doğrula]` |
| 2025, 2026, 2027 hesap dönemleri (özel dönemde 2026-2028'de bitenler) | Şart oluşsa bile **yapılmaz**; (Ç) için şart oluşmamış sayılır; Cumhurbaşkanı üç döneme kadar uzatabilir | geçici m.37 |
| Finans sektörü (geçici 33/4) 2024-2025 | Düzeltme yapılır ama fark kazançta dikkate alınmaz; geçici 37 bunlara da uygulanır | geçici m.33/4, m.37/3 |
| mük.298/A-9 (münhasıran işlenmiş altın/gümüş) | Şarta bakılmaksızın **her dönem** yapar; geçici 33 ve 37 uygulanmaz | A-9; geçici m.33 (1-3. fıkralar A-9'a uygulanmaz); m.37/4 |

Uzatma kararı (2028 ve sonrası) için RG'yi ara: `legal_search_official_gazette` `query: "enflasyon düzeltmesi"` `document_type: "cumhurbaşkanı kararı"` `sort_by: "date_desc"` `[doğrula]`.

## Elle hesap iskeleti (yalnız A-9 ya da ileride yeniden başlarsa)

```
Düzeltme katsayısı = Yİ-ÜFE(mali tablo ayı) / Yİ-ÜFE(düzeltmeye esas tarih ayı) [VUK GT 555 m.36]
Taşıma katsayısı = Yİ-ÜFE(mali tablo ayı) / Yİ-ÜFE(önceki dönem sonu) [VUK GT 555 m.35]
Düzeltilmiş tutar = kayıtlı tutar × katsayı; fark → ilgili fark hesabı / enflasyon düzeltme hesabı
```
Her endeks değeri `[kullanıcı verdi]`, her katsayı ve fark `[doğrula]`.

## Kontrol listesi
- ✅ Dönem tabloda bulundu ve dayanağı çekildi.
- 🔴 2025-2027'de "şart oluştu, düzeltelim" demek geçici m.37'ye aykırı (A-9 hariç).
- 🔴 TÜFE (ya da `legal_calculate_cpi_change` yüzdesi) ile katsayı kurmak.
- 🟠 A-9 mükellefi gözden kaçmasın: erteleme ona uygulanmaz.
- 🟠 Düzeltme yapılmayan dönemde yeniden değerleme seçeneği → `yeniden-degerleme.md`.
- 🟡 2023 sonu farkı: geçmiş yıl kârı vergilenmez, zararı zarar sayılmaz; öz sermaye fark hesaplarının sonraki kullanımı (A-5) vergilendirme doğurabilir.
- [incele] TTK / TFRS kapsamındaki ticari finansal tablolar ayrı rejim (KGK tebliği, 40844) — vergi tablosundan ayır.

## Sık hatalar
- Vergi düzeltmesiyle TMS 29 ticari düzeltmesini karıştırmak.
- Geçici 37'yi yalnız yıllık dönem sanıp geçici vergi dönemlerinde düzeltme yapmak.
- Parasal kıymeti (yabancı para dahil) düzeltmeye sokmak.

## Yevmiye kaydı önerisi
Düzeltme yapılan (A-9) mükellefte: ilgili kıymet fark hesabı (borç) / 698 Enflasyon Düzeltme Hesabı (alacak); pasif kalemde ters yön; 698 bakiyesi gelir tablosuna aktarılarak kapatılır (A-2-m). Hesap kodları (698, 648/658) MSUGT ve VUK GT 555 örneklerinden okunmadı `[doğrula]`.

## Uyuşmazlığa dönüş
Düzeltme yapılmadığı / yanlış yapıldığı gerekçesiyle tarhiyat → `../../vergi/SKILL.md`.

## Çıktı
SKILL.md Adım 4; gözden geçiren notuna "hesap aracı yok — elle hesap; endeks kullanıcıdan" yaz.
