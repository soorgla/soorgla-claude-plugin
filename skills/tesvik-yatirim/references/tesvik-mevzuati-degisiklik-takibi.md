# Teşvik mevzuatı değişiklik takibi: "bu yeni düzenleme bizi etkiler mi?"

## Ne zaman kullanılır
- "Yeni teşvik kararı/tebliğ çıktı, belgemizi etkiler mi?", "öncelikli ürün listesi güncellendi mi?", "Ar-Ge teşvikleri uzatıldı mı?"
- Bir uyuşmazlıkta **belge/müracaat tarihinde** hangi kararın ve kanun metninin geçerli olduğunu bulmak.
- Profilde izlenen belgeler için dönemsel tarama.

**Upstream uyarlaması** (`regulatory-legal/reg-feed-watcher`): kaynağı çek → önem süzgecinden geçir → yalnız önemli olanı göster → her değişiklik için "eski / yeni / yürürlük / geçiş / kimi etkiler / ne yapılmalı" satırı. Federal Register ve RSS yerine Resmî Gazete; süzgeç değerdir, süzgeçsiz liste gürültüdür.

---

## 1. Çekme

```
legal_search_official_gazette query: "Yatırımlarda Devlet Yardımları" search_in: "title" sort_by: "date_desc" date_from: "<son tarama>"
legal_search_official_gazette query: "9903 sayılı Cumhurbaşkanı Kararı" sort_by: "date_desc" date_from: "<son tarama>" # Karara atıf yapan tebliğ/yönetmelikler
legal_search_official_gazette query: "Öncelikli Ürün Listesi Tebliği" search_in: "title" sort_by: "date_desc"
legal_search_official_gazette query: "<5746 | 4691 | 5520 sayılı Kurumlar Vergisi Kanununun 32/A | 3065 sayılı Kanunun 13>" document_type: "kanun" date_from: "<…>"
legal_search_official_gazette query: "Teknoloji Geliştirme Bölgeleri | Ar-Ge veya Tasarım Merkezlerinde" search_in: "title" sort_by: "date_desc"
legal_search_official_gazette query: "KOSGEB | İstihdamı Koruma Destek Programı | Yeşil Dönüşüm Programı | Dijital Dönüşüm" search_in: "title" sort_by: "date_desc"
legal_get_official_gazette_document url: "<sonuç>" # uzun metinde offset/max_chars
```

**Uyarılar:**
- Torba kanunların başlığı teşvik içermez (7555 "Türk Parasının Kıymetini Koruma… ", 7566 "Vergi Kanunları…", 7582 "Bazı Kanunlarda…"): madde kalıbıyla (`"5746 sayılı … Kanunun 3 üncü maddesi"`) `search_in: "all"` ara.
- 9903 madde aracıyla çekilemez (katalogda bölütlenmemiş); Karar değişikliğini yalnız RG'den izle.
- Bakanlığın yıllık **tutar güncelleme ilanı** RG'de değil Bakanlık sitesinde olabilir (Tebliğ 2025/1 m.27) `[web araması — doğrulayın]`.
- CB kararlarının ekleri (ör. 10766) soorgla'da boş gelebilir.

## 2. Önem süzgeci

| Tier | Ölçüt | Gösterim |
|---|---|---|
| 🔴 Önemli | Belge iptali, vize, satış/devir, destek süresi, vergi indirimi dönemi, istisnanın sona ermesi; açık dosyayı etkiler | Hemen, eylem önerisiyle |
| 🟠 Orta | Yeni program/liste, şart değişikliği, belge format değişikliği; profildeki sektöre dokunur | Özet tabloda |
| 🟡 Bilgi | Başka sektör, usul ayrıntısı | Tek satır ya da hiç |

Profilde izlenen belge/sektör yoksa süzgeci sor ("hangi belgeler, hangi sektör, hangi teşvik rejimi?").

## 3. Son 2-3 yılın başlıca değişiklikleri (bu becerinin yazıldığı tarih: 31.10.2026)

| Düzenleme / RG | Ne değişti (seçme) | Etkilenen dosya | Doğrulama |
|---|---|---|---|
| 2012/3305'te değişiklik CB kararları 6923 (RG 10.03.2023), 7108 (RG 20.04.2023), 8860 (RG 29.08.2024); Tebliğ 2012/1 değişiklikleri 2023/1-2025/1 | Eski sistemin son değişiklikleri; eski belgelerde hâlâ uygulanır | `tesvik-sistemi-ve-uygunluk.md`, eski belge dosyaları | |
| **9903 sayılı CB Kararı (RG 30.05.2025)** | Yeni sistem: Türkiye Yüzyılı Kalkınma Hamlesi (3 program), Sektörel Teşvik (öncelikli/hedef), bölgesel teşvik (SGK); makine desteği; ekosistem planı; 2012/3305 ve Cazibe Merkezleri kaldırıldı; e-fatura ve toplam destek sınırı 1.1.2026'dan | Hepsi | |
| **Tebliğ 2025/1 (RG 21.06.2025)** | E-TUYS usulü, eksik tamamlama 30 gün, kapsam dışı harcamalar, ilerleme raporu Mart sonu, mücbir sebep, vize; Tebliğ 2012/1 kaldırıldı | `tesvik-belgesi-sureci-ve-yukumlulukler.md` | |
| **7555 (RG 24.07.2025)** | KVK 32/A yeniden: Sanayi ve Teknoloji Bakanlığı belgesi, en fazla on hesap dönemi, kullanılmayan katkı devretmez (24.07.2025 sonrası belgeler; 16.06.2025 öncesi reddedilmemiş başvurular hariç); 5746 ve 4691'de stopaj teşvikine tavan ve asgari ücret istisnası mahsubu, damga vergisine tavan (1.8.2025); OSB muafiyetinin BSMV'yi kapsamadığı | `destek-unsurlari-vergi-sgk-gumruk.md`, `ar-ge-tasarim-ve-teknopark.md` | |
| **7566 (RG 19.12.2025)** | 4447 geçici m.35: 2026 için imalat sanayiinde istihdamı koruma destek programına İşsizlik Sigortası Fonu kaynağı; 635 KHK ek m.1/ğ Bakanlığa destek verme yetkisi; KDV geçici m.37'ye dokunmadı — süre zaten CB Kararı 9770 (RG 01.05.2025) ile 31.12.2028'e uzatılmıştı | `kosgeb-ajans-ve-diger-destekler.md`, `destek-unsurlari…` | |
| CB Kararı 10766 (RG 25.12.2025) | Ar-Ge/tasarım merkezi ve TGB personelinin merkez/bölge dışı süreleri — **ek metni soorgla'da yok** | `ar-ge-tasarim-ve-teknopark.md` | |
| Öncelikli Ürün Listesi Tebliğinde değişiklik (RG 31.01.2026) | Amaç maddesi 9903 ve proje bazlı karara bağlandı; liste güncellendi | `tesvik-sistemi-ve-uygunluk.md` | |
| İstihdamı Koruma Destek Programı Uygulama Yönetmeliği (RG 03.03.2026; değişiklik RG 28.08.2026) | 9903 m.18/5 nakil belgeli işletmelere özel koşul | `kosgeb-ajans-ve-diger-destekler.md` | |
| Tebliğ 2026/1 (RG 09.04.2026) | YMM raporuyla tamamlama vizesi (EK-5 yeni format; eski belgelere de) | `tesvik-belgesi-sureci…` | |
| Yeşil Dönüşüm Programı Uygulama Usul ve Esasları Tebliğinde değişiklik (RG 08.05.2026) | Program 9903'e bağlandı | `tesvik-sistemi…` | |
| **7582 (RG 04.06.2026)** | 5746 m.3/15-16 (teknogirişim rozeti, dijital şirket aidat muafiyeti); KVK 32/8 üretim kazancına indirimli oran (2027 kazançları); KVK 10/1-i ve j; nitelikli hizmet merkezi (4875 ek m.1, GVK 23/20); 6183 m.48 tecil süresi ve teminat sınırı değişikliği | `ar-ge…`, `destek-unsurlari…`, `kosgeb…` | |
| 7589 / 7590 (RG 31.07.2026) | Teşvik mevzuatına (5746, 4691, 32/A, 9903) dokunan hüküm **bulunamadı**; yargı usulü (İYUK 45-46) değişiklikleri dava aşamasında `vergi`/`kanun-yollari-dilekce`'den | — | |
| Stratejik Öncelik ve Teknik Değerlendirme Tebliğinde değişiklik (RG 03.09.2026) | TSP Belgesi ve yeni Öncelikli Finansman Belgesi; finansman programı kredisine faiz desteği yok | `kosgeb…`, `destek-unsurlari…` | |

**Takvim uyarıları (yakın):**
- 9903 geçici m.3-4 (deprem bölgesi ve Cazibe Merkezi OSB'leri için 6. bölge desteği) son müracaat 31.12.2026 — uzatma çıktı mı? 01.11.2026 itibarıyla uzatma yok: 9903'ü değiştiren karar RG'de bulunamadı (yalnız uygulama tebliği değişikliği 2026/1, RG 09.04.2026 — EK-4/EK-5 YMM raporu). 31.12.2026'ya kadar her analizde `legal_search_official_gazette` (`query: "Yatırımlarda Devlet Yardımları Hakkında Kararda Değişiklik"`, `search_in: "title"`, `sort_by: "date_desc"`) ile yeniden ara.
- 9903 geçici m.5: eski belgelerde süresi biten 6. bölge SGK desteği 31.12.2028'e kadar uzatılmış (şartlı).
- 5746 ve 4691 istisnaları 31.12.2028'de sona eriyor.
- 4447 geçici m.35 kaynağı yalnız 2026 yılı için.

## 4. Her değişiklik için satır

| Alan | İçerik |
|---|---|
| Künye | RG tarih/sayı, düzenleme adı, madde |
| Eski metin → yeni metin | Kısa alıntı (RG'den) |
| Yürürlük ve geçiş | Hangi müracaat/belge tarihine uygulanır |
| Kimi etkiler | Profildeki belge(ler) |
| Ne yapılmalı | Takvim güncellemesi, revize, başvuru, model güncellemesi |
| Önem | 🔴/🟠/🟡 |

## 5. Sık hatalar
- 🔴 Yeni karar çıktı diye eski belgeye yeni kuralı uygulamak (geçici m.2) — ya da tersine, eski belgelere açıkça uzanan yeni hükümleri atlamak.
- 🟠 Yalnız başlık araması yapıp torba kanundaki teşvik değişikliğini kaçırmak.
- 🟠 soorgla mevzuat kaydındaki madde metnini son değişikliği yansıtıyor sanmak; son 6 ayda değişen maddeyi RG'den oku.

## Kaynak ve uyarlama

YAML karşılığı yok; upstream `regulatory-legal/reg-feed-watcher` iş akışından (Apache 2.0) ve 2023-2026 RG taramasından sıfırdan kuruldu.
