# E-ticaret ve lansman uyumu, Bakanlık ve Reklam Kurulu yaptırımları

<!-- Upstream product-legal/launch-review (Apache 2.0, Anthropic PBC) iş akışından uyarlandı: önce "ne çıkıyor" sorusu, kategori kategori tarama, dürüst atlama, bulgu–aksiyon tablosu, "yayına çıkabilir" kapısı. ABD sektör rejimleri (FTC, CAN-SPAM, ROSCA vb.) alınmadı; karşılıkları 6502, 6563 ve ikincil düzenlemelerdir. -->

## Ne zaman kullanılır
- **İşletme tarafı lansman/uyum denetimi:** yeni e-ticaret sitesi, mobil uygulama, pazaryeri mağazası, abonelik modeli, kampanya ya da sadakat programı çıkıyor; "tüketici mevzuatı açısından eksik ne?".
- **Yaptırım geldi:** Ticaret Bakanlığı (il müdürlüğü) 6502 ya da 6563 idari para cezası, Reklam Kurulu durdurma/İPC kararı; savunma, uzlaşma, ödeme, dava seçenekleri.
- Reklam metninin iddia iddia incelemesi → `reklam-ve-haksiz-ticari-uygulama.md`. Kişisel veri, çerez, açık rıza → `../../kvkk/SKILL.md`. Pazaryeri ile satıcı arasındaki ticari ilişki (6563 ek m.1-4: ödeme süresi, tek taraflı fiyat müdahalesi) tüketici hukuku değil → `../../sirketler-ticaret/SKILL.md` `[incele]`. 

---

## A. Lansman denetimi (upstream launch-review uyarlaması)

### Adım 1 — Ne çıkıyor?
Düz Türkçeyle cevapla: ne satılıyor (mal/hizmet/dijital içerik/abonelik), kime (tüketici mi tacir mi), hangi kanaldan (kendi site, pazaryeri, sosyal medya, telefon), yeni olan ne (yeni ödeme modeli, otomatik yenileme, kişiye özel ürün, yapay zekâ, kampanya). Yapay zekâ ya da kişiselleştirme varsa KVKK ve reklam yönetmeliği m.18/8, m.25/A bayrağını kaldır.

### Adım 2 — Kategori taraması
Her kategori için: **Bakılan · Bulgu (Temiz / Düzeltme gerekli / Engelleyici / Atlandı) · Ayrıntı · Aksiyon (kim, ne zamana kadar)**. Uygulanmayan kategoriyi tek satır gerekçeyle atla; doldurma.

| # | Kategori | Temel soru | Dayanak |
|---|---|---|---|
| 1 | Satıcı kimliği ve bilgi verme | Unvan, iletişim, MERSİS/vergi, meslek odası bilgileri sitede kolay ve güncel mi? | 6563 m.3  |
| 2 | Sipariş akışı | Ödeme bilgisi girilmeden önce toplam bedel ve şartlar açıkça görünüyor mu; sipariş "gecikmeksizin" teyit ediliyor mu; veri giriş hatası düzeltme aracı var mı? | 6563 m.4  |
| 3 | Ön bilgilendirme ve mesafeli sözleşme | Yönetmelik m.5'teki zorunlu bilgiler (cayma, iade taşıyıcısı, şikâyet yolu: THH ve m.73/A arabuluculuk bilgisi dahil); "ödeme yükümlülüğü" uyarısı onaydan hemen önce | 6502 m.48/2; Mesafeli Söz. Yön. m.5 (RG 24.5.2025 ile değişik g ve k bentleri), m.8  |
| 4 | Teslimat | Taahhüt edilen süre; mal satışında 30 gün üst sınırı | 6502 m.48/3 |
| 5 | Cayma ve iade | Cayma formu ve site üzerinden cayma seçeneği, teyit; istisnalar doğru mu (iptal edilen bentlere dayanılmıyor mu); 14 gün iade; iade masrafı | Yön. m.11-15 → `cayma-hakki-ve-mesafeli-satis.md` |
| 6 | Fiyat ve indirim | Vergiler dahil fiyat, birim fiyat; indirimde önceki fiyat (1.8.2026'dan 10 gün kuralı, kanal bazında) | 6502 m.54; Reklam Yön. m.14 |
| 7 | Abonelik ve otomatik yenileme | Otomatik uzama hükmü yok mu; fesih, kuruluş kanalından ağır olmayan yöntemle mümkün mü? | 6502 m.52/3-4 |
| 8 | Ticari elektronik ileti | Tüketiciye SMS/e-posta/arama için **önceden onay**; içerik onaya uygun; ret imkânı ücretsiz ve kolay; ret talebinden sonra **3 iş günü** içinde gönderim durur. Esnaf ve tacirlere onaysız gönderilebilir | 6563 m.6-8  | İleti Yönetim Sistemi (İYS): Ticari İletişim ve Ticari Elektronik İletiler Hakkında Yönetmelik (`20914`) m.4/ö, m.10/A vd. Gönderen İYS'ye kaydolur ve İYS'de onayı olmayan alıcıya ileti gönderemez (m.5/2-3); İYS dışında alınan onay **üç iş günü** içinde İYS'ye kaydedilir, kaydedilmeyen onay **geçersiz** (m.7/11-12); İYS dışı onayın ispatı hizmet sağlayıcıda (m.7/10, m.13/1); ret bildirimi de üç iş günü içinde İYS'ye bildirilir (m.9/6). Onay metninde olumlu beyan önceden seçili olamaz, onay mal/hizmetin ön şartı yapılamaz (m.7/8-9)   |
| 9 | Promosyon, çekiliş, yarışma | Katılım şartları açık ve kolay ulaşılır; çekiliş izni | 6563 m.5/1-b; Reklam Yön. m.15 `[doğrula]` |
| 10 | Yorum ve puanlama | Yalnız satın alanlar; doğrulanamayan yorum yok; şikâyete 48 saat cevap süresi (şikâyet sitelerinde) | Reklam Yön. m.28/B, 28/C (1.8.2026'dan)  |
| 11 | Garanti, kılavuz, satış sonrası | Garanti belgesi, Türkçe kılavuz, yetkili servis bilgisi | 6502 m.55-58 |
| 12 | Kişisel veri | Aydınlatma, çerez, açık rıza, hedefli reklam | → kvkk; Reklam Yön. m.25/A |
| 13 | Pazaryeri olarak çalışıyorsak | Cayma/iade talep sistemi, kayıt (3 yıl), kampanya sorumluluğu, reklam–ön bilgi uyumu, hukuka aykırı içeriği kaldırma | 6502 m.48/5-6; Yön. m.12/A; 6563 m.9  |
| 14 | ETBİS ve lisans | ETBİS kaydı; işlem hacmi eşiğini aşan aracı hizmet sağlayıcıda lisans | 6563 ek m.4 (eşikler kanunda; çek) `[doğrula]`; ETBİS kaydı ve bildirimleri: Elektronik Ticaret Aracı Hizmet Sağlayıcı ve Elektronik Ticaret Hizmet Sağlayıcılar Hakkında Yönetmelik (`39927`) ve Elektronik Ticaret Bilgi Sistemi ve Bildirim Yükümlülükleri Hakkında Tebliğ (`23842`)  |

### Adım 3 — Ciddiyet
Her bulgu: 🔴 engelleyici (yayına çıkarsa her işlem için İPC ya da tüketiciye karşı geçersizlik: ör. ön bilgilendirme yok, cayma engelleniyor, onaysız SMS), 🟠 düzeltme gerekli, 🟡 iyileştirme, 🟢 bilgi. Profil yoksa yukarı yuvarla. Kalıba uymayan yeni bir durum: "Bu bilinen bir kalıba uymuyor — insan kararı gerekir" de.

### Adım 4 — Çıktı

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

# Lansman incelemesi: [ürün/kampanya] — [tarih]
**Yayın tarihi:** [..] · **Kanal:** [..]

## Sonuç
[Yayına çıkabilir mi; önce ne yapılmalı]
**Karar:** [Çıkabilir | Koşullarla çıkabilir | [X] tamamlanana kadar bekletilmeli | Yükselt]

## Kategori bulguları
### [N]. [Kategori]
**Bakılan:** … **Bulgu:** … **Ayrıntı:** … **Aksiyon:** …

## Aksiyon tablosu
| # | İş | Sorumlu | Son tarih | Engelleyici mi |

## Atlanan kategoriler (gerekçesiyle)
```

**"Çıkabilir" kapısı:** kullanıcı avukat değilse "Çıkabilir" ya da "Koşullarla çıkabilir" demeden önce sor: "Bunu bir avukatla gözden geçirdiniz mi?" Hayırsa bir sayfalık avukat özeti (ne çıkıyor, kategori bulguları, açık sorular, koşullardan sonra kalan risk, avukata sorulacak üç şey). "Bekletilmeli" ve "yükselt" kapı gerektirmez.

---

## B. Yaptırım geldi: Bakanlık ve Reklam Kurulu

### Süreler ve dayanakları

| Süre / kural | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Yetki: m.77/12-13 (reklam, haksız ticari uygulama) kararları **Reklam Kurulu**; diğerleri **Bakanlık** (taşrada il müdürlüğüne devredilebilir) | — | 6502 m.78/1 (7392/16)  | |
| **Uzlaşma talebi: 15 gün**, henüz dava açılmamış İPC için; talep dava açma süresini **durdurur**, uzlaşmazlıkta kaldığı yerden işler; ikinci uzlaşma talebi yok | İPC kararının **tebliği** | 6502 m.77/A-3  | İndirim en çok %50; uzlaşılan cezada 5326 m.17 peşin ödeme indirimi ayrıca uygulanmaz; tutanak kesin, dava açılamaz (m.77/A-4-5). 7529 ile m.77/A-2 mülga. Uzlaşma Yönetmeliği 2025'te iki kez değişti `[doğrula]`  |
| **İdare mahkemesinde iptal davası: 30 gün**; dava açmak yerine getirmeyi durdurmaz | İşlemin tebliğini izleyen gün | 6502 m.78/2  | İYUK'un genel 60 günü değil 🔴 |
| İPC'nin ödenmesi: **1 ay** | Tebliğ | 6502 m.78/3 | Peşin ödeme indirimi (5326 m.17/6) ve dava hakkı ilişkisi `[incele]` |
| 6563 cezaları | — | 6563 m.12; tutarlar her yıl tebliğle `[doğrula]`  | İtiraz/dava yolu madde metninden çek `[doğrula]` |

### Kontrol listesi

| Kod | Kontrol | Not |
|---|---|---|
| YP-TEBLİĞ | Tebliğ tarihi ve yöntemi; uzlaşma (15 gün) ve dava (30 gün) son günleri | İkisini birlikte takvime yaz |
| YP-DAYANAK | Hangi fıkra/bent uygulandı; "her bir işlem veya sözleşme için" çarpımı doğru mu; o yılın tebliğindeki tutar mı? | m.77; RG tebliği |
| YP-TAVAN | Bir takvim yılında toplam cezanın gayrisafi gelirin belirli oranıyla (bankalarda öz kaynakla) sınırlanması uygulandı mı? (m.77/19; 2., 4., 8., 9., 12., 13. fıkralar ve devre tatil hariç) |  Oranları madde metninden çek |
| YP-REKLAM-ÖLÇÜT | Reklam Kurulu cezasında haksızlık içeriği, menfaat/zarar, kusur, ekonomik durum değerlendirildi mi? | m.77/12-13 (7529 ile eklenen cümle) — gerekçesizlik iptal sebebi olabilir `[incele]` |
| YP-ERİŞİM | İnternette içerik çıkarma bildirimi yapıldı mı, 24 saat geçmeden erişim engeli mi verildi? | m.77/12 (7392, 7511) |
| YP-UZLAŞMA-MI | Uzlaşma şartları (mevzuata nüfuz edememe, yanlış yorum, yargı kararlarıyla görüş farkı) savunulabilir mi; uzlaşma sonrası dava hakkı kaybı kabul edilebilir mi? | Takdir `[incele]` |
| YP-MAHKEME | Bireysel işleme karşı idare mahkemesi; dayanak yönetmelik hükmü de dava ediliyorsa Danıştay ilk derece | Danıştay 10. D. E.2020/3621 K.2024/6305 — Reklam Kurulu kararı ile Yönetmelik m.28-29 ve ekinin iptali birlikte istenmiş, Danıştay ilk derece olarak bakmış  `[incele]` |
| YP-DİLEKÇE | İptal davası dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`; savunma/uzlaşma yazısı → `../../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md` biçimiyle | |

### Uzlaşma talebi iskeleti

```
T.C. TİCARET BAKANLIĞI
[___] Ticaret İl Müdürlüğü / Tüketicinin Korunması ve Piyasa Gözetimi Genel Müdürlüğü
(Uzlaşma Komisyonu'na sunulmak üzere)

TALEPTE BULUNAN : [unvan, MERSİS/vergi no, adres, KEP]
KONU            : [tarih] tarihli ve [sayı] sayılı idari para cezası kararı hakkında
                  6502 sayılı Kanun m.77/A uyarınca uzlaşma talebi
TEBLİĞ TARİHİ   : [___]   (15 günlük süre: son gün [___])

AÇIKLAMALAR :
1. Ceza kararının konusu ve dayanağı (m.77/[fıkra]).
2. Uzlaşma gerekçesi: [kanun hükmüne yeterince nüfuz edememe / yanlış yorum /
   yargı kararlarıyla idarenin görüş farkı — somut açıklama].
3. Aykırılığın giderildiğine ilişkin yapılanlar (Ek-…).
TALEP : İdari para cezası hakkında uzlaşma sağlanmasını arz ederiz.
EKLER : ceza kararı ve tebliğ belgesi, düzeltme kanıtları, yetki belgesi
[tarih, yetkili imza]
```
Başvuru yeri ve biçimi Uzlaşma Yönetmeliği'nden teyit edilmeli `[doğrula]`.

---

## Görüşme soruları
| Alan | Soru |
|---|---|
| Lansman | Ürün/hizmet, hedef kitle, kanallar, yayın tarihi, ödeme ve iade akışı ekran görüntüleri, sözleşme ve ön bilgi metinleri, ileti onay kayıtları |
| Yaptırım | Ceza kararı ve tebliğ belgesi, tutanaklar, denetim yazışmaları, önceki cezalar, bir önceki yıl gayrisafi geliri, aykırılığın giderilip giderilmediği |

## soorgla çağrıları
```
legal_get_statute_article  law_no: "6563"  law_type: "Kanun"  article_no: "3" | "4" | "5" | "6" | "7" | "8" | "9" | "12"
legal_list_statute_articles  law_no: "6563"  law_type: "Kanun"  article_kind: "ek"  include_content: true
legal_get_statute_article  law_no: "6502"  article_no: "48" | "52" | "54" | "55" | "56" | "58" | "77" | "78"
legal_list_statute_articles  law_no: "6502"  article_no: "77/A"  include_content: true
legal_list_statute_articles  law_no: "20237"  article_no: "5"  include_content: true
legal_search_official_gazette  query: "77 nci Maddesine Göre"  search_in: "title"  sort_by: "date_desc"         # yılın ceza tutarları
legal_search_official_gazette  query: "İdari Para Cezalarına İlişkin Uzlaşma Yönetmeliği"  search_in: "title"  sort_by: "date_desc"
legal_resolve_statute  query: "Ticari İletişim ve Ticari Elektronik İletiler Hakkında Yönetmelik"
legal_search_cases  mahkeme: "danistay"  sorgu: "<olay: 6502 mesafeli sözleşme ön bilgilendirme idari para cezası iptal>"  tarih_baslangic: "<son 3 yıl>"
```

## Sık hatalar
- İPC iptal davasında İYUK'un 60 gününe güvenmek (6502 m.78/2: 30 gün).
- Uzlaşma talep edip dava süresinin durduğunu hesaba katmamak ya da uzlaşma sonrası dava açmaya çalışmak.
- Ceza tutarını kanundaki taban rakamdan hesaplamak (o yılın tebliği).
- Tacir alıcıya yapılan B2B satışta 6502 yükümlülüklerini uygulamak; ya da tersine, onaysız ticari ileti için "müşterimiz zaten" savunmasına güvenmek.
- Lansman denetiminde uygulanmayan kategorileri gerekçesiz atlamak ya da doldurmak.

