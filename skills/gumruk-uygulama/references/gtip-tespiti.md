# GTİP tespiti ve kod geçmişi

## Ne zaman kullanılır
- "Bu ürünün GTİP'i ne?", "proformadaki HS kodu bizde neye karşılık gelir?", "eski beyannamedeki kod bu yıl var mı?".
- İlk ithalattan önce sınıflandırma çalışması; BTB'ye başvurmaya değer mi kararı.
- İdare GTİP'i **değiştirdiyse** ya da ek tahakkuk geldiyse bu dosya değil → `../../gumruk-dis-ticaret/references/tarife-siniflandirma-ve-btb.md`.

---

## Kodun yapısı

| Hane | Düzey | Kaynak |
|---|---|---|
| 2 | Fasıl | Armonize Sistem (Dünya Gümrük Örgütü) |
| 4 | Pozisyon | Armonize Sistem |
| 6 | Alt pozisyon | Armonize Sistem — uluslararası ortak; yabancı tedarikçinin "HS code"u çoğunlukla bu |
| 8 | Kombine Nomanklatür | AB ile ortak (Gümrük Birliği) |
| 10–12 | Ulusal kırılım | Türk Gümrük Tarife Cetveli (TGTC); beyannamede 12 hane yazılır |

TGTC her yıl Cumhurbaşkanı kararıyla yeniden yayımlanır, yıl içinde değişiklik kararları da çıkar (ör. 2026 cetveli Karar 10781, RG 30.12.2025 Mükerrer; yıl içi değişiklik Karar 11507, RG 11.07.2026). Vergi ve önlem **12 haneli** kodla uygulanır; 6 haneli yabancı kodla oran bulunmaz. Son değişikliği bul: `legal_search_official_gazette` `query: "Türk Gümrük Tarife Cetvel"` `search_in: "title"` `sort_by: "date_desc"`.

---

## Akış

1. **Eşyayı tanımla:** malzeme, işlev, kullanım yeri, bileşim (yüzde), monte/demonte, set mi, ambalaj, perakendeye hazır mı. Teknik föy, katalog, fotoğraf iste. Tedarikçinin HS kodunu **başlangıç adayı** say, sonuç sayma.
2. **Aday pozisyonları bul:**
   - GTİP arama aracı varsa: önce kod önekiyle (`8471`, `8471.30`), sonra serbest metinle; `tarih` = planlanan tescil günü. Metin araması cetvelin resmî diliyle eşleşir; sık gündelik adlar ("dizüstü bilgisayar", "ekran kartı") küçük bir eşanlam tablosuyla cetvel önekine yönlendirilir ve sonuçta `eslesme` diye işaretlenir — bu yönlendirme sınıflandırma görüşü değildir. Tabloda olmayan gündelik adı cetvel terimine çevirerek ara ("taşınabilir otomatik bilgi işlem makinesi").
   - Araç yoksa: Ticaret Bakanlığının yayımladığı yılın TGTC dosyası `[web — doğrulayın]`; RG'deki karar eki.
   - TGTC'de satırların çoğu "- - Diğerleri"dir; tanımı **üst satırlarla birlikte** oku (fasıl → pozisyon → alt pozisyon).
3. **Genel Yorum Kuralları sırasıyla ele:** 1 (pozisyon metni ve bölüm/fasıl notları) → 2 → 3 → 4 → 5 → 6 `[model bilgisi — doğrulayın]`. Kural metni TGTC'nin başındadır; soorgla'da tam metin yok. Gerekçede kural numarasını yaz, metni kullanıcının TGTC'sinden teyit ettir.
4. **Fasıl ve bölüm notlarını oku:** hariç tutma notları en sık hata kaynağıdır ("bu fasıl … kapsamaz").
5. **Destek ara:**
   - İzahname ve Dünya Gümrük Örgütü sınıflandırma görüşleri → kullanıcıdan ya da web `[web araması — doğrulayın]`.
   - Gümrük genelgesi → `legal_search_admin_guidance` `kurum: "Ticaret Bakanlığı"` `sorgu: "<eşya> tarife"`.
   - Danıştay emsali (aynı eşya için uyuşmazlık) → `legal_search_cases` `mahkeme: "danistay"`; yalnız tartışmalı eşyada.
6. **Kod geçmişine bak** (eski beyanname, eski BTB, eski sözleşme varsa): aynı tanım bugün hangi kodda; kod bölündü mü, kapandı mı. Arama aracında yıl sürümü; yoksa önceki yılın TGTC'si. Kod değişikliği BTB'yi geçersiz kılar (4458 m.9/5).
7. **Sonucu ver:** öneri + güven düzeyi + alternatif aday + farkın vergi etkisi (iki aday arasında oran farkı varsa maliyet tablosu ikisi için de).

---

## BTB'ye başvurmalı mı

| Durum | Öneri |
|---|---|
| İki aday arasında vergi ya da önlem farkı büyük; düzenli ithalat | BTB öner (yalnız hak sahibini bağlar, 4458 m.9/2) |
| Tek seferlik, oran farkı yok | Gerekçeli sınıflandırma notu yeterli |
| Eşya yeni teknoloji, izahnamede açık örnek yok | BTB öner; ilk ithalatı BTB'den sonraya almayı konuş |
| Başkasına verilmiş BTB var | Emsal değer taşır, bağlamaz 🔴 |

BTB başvuru formu form bankasında (`legal_search_forms` "bağlayıcı tarife bilgisi başvuru formu"; araç yoksa Ticaret Bakanlığı "Gümrük İdarelerinde Kullanılan Belgeler" sayfası). Başvuru yazısı → `../../idari-ve-kurum-basvurulari/SKILL.md`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Ürünün ne işe yaradığı, neyden yapıldığı (yüzde bileşim)? | GYK 1 ve 3/b |
| Tedarikçinin yazdığı HS kodu ve ülkesi? | İlk 6 hane adayı |
| Daha önce aynı ürünü hangi GTİP'le beyan ettiniz? | Tutarlılık, seri tahakkuk riski |
| Set ya da parça hâlinde mi geliyor? | GYK 2/a, 3/b |
| BTB'niz var mı, tarihi? | m.9 geçerlilik |

---

## Çıktı iskeleti

```markdown
## GTİP önerisi — [eşya]
| Aday | Tanım (üst satırlarla) | GYK gerekçesi | Destek | Gümrük vergisi / önlem farkı |
### Öneri: [12 haneli kod] — güven: yüksek / orta / düşük
### Kod geçmişi (eski kod → yeni kod) — gerekiyorsa
### BTB önerisi: evet / hayır — neden
```

## Sık hatalar
- 🔴 Tedarikçinin 6 haneli HS kodunu 12 haneye "0000" ekleyerek tamamlamak.
- 🟠 "Diğerleri" satırını üst tanımı okumadan seçmek.
- 🟠 Eski yılın kodunu bu yılın oranıyla eşlemek (kod bölünmüş olabilir).
- 🟡 Önlem kontrolünü atlamak: aynı pozisyonda damping ya da İGV olabilir → `ithalat-on-kontrol.md`.
