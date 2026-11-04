# Teşvik sistemi ve uygunluk taraması: "hangi teşvikten yararlanırız?"

## Ne zaman kullanılır
- "Bu yatırıma teşvik belgesi alabilir miyiz?", "hangi bölgedeyiz?", "öncelikli yatırım mı, hedef yatırım mı?", "Teknoloji Hamlesi'ne başvurabilir miyiz?"
- Yatırım fikri aşamasında destek yol haritası (eski `incentive_discovery.yaml` görevi).
- Eski bir teşvik raporunda ya da danışman sunumunda geçen "1-6. bölge, öncelikli konuya 5. bölge desteği" anlatımının bugün geçerli olup olmadığı.

Belge alındıktan sonraki süreç → `tesvik-belgesi-sureci-ve-yukumlulukler.md`; destek unsurlarının ayrıntısı → `destek-unsurlari-vergi-sgk-gumruk.md`; Ar-Ge/teknopark → `ar-ge-tasarim-ve-teknopark.md`; KOSGEB/ajans → `kosgeb-ajans-ve-diger-destekler.md`.

---

## 1. Sistemin iskeleti (9903 sayılı Karar)

9903 sayılı Cumhurbaşkanı Kararı (RG 30.05.2025) 2012/3305 sayılı BKK'yı ve Cazibe Merkezleri Programını kaldırdı. Sistem üç katmandır: 

| Katman | Bileşen | Kim değerlendirir | Dayanak |
|---|---|---|---|
| Türkiye Yüzyılı Kalkınma Hamlesi | Teknoloji Hamlesi Programı (öncelikli ürün listesindeki ürün/teknoloji) | Program Değerlendirme Komitesi, proje bazında | 9903 m.6 |
| | Yerel Kalkınma Hamlesi Programı (ile özgü yerel yatırım konuları listesi) | Komite; Kalkınma Ajansları GM yürütür | 9903 m.7 |
| | Stratejik Hamle Programı (stratejik hamle yatırım konuları; ön değerlendirme kriterleri, kalkınma ve yatırım bankası fizibilitesi) | Genel Müdürlük ön değerlendirmesi + Komite | 9903 m.8; Tebliğ 2025/1 m.12 |
| Sektörel Teşvik Sistemi | Öncelikli Yatırımlar Teşvik Sistemi (Karar'da sayılan konular) | Genel Müdürlük | 9903 m.9 |
| | Hedef Yatırımlar Teşvik Sistemi (EK-3'teki konular ve şartlar) | Genel Müdürlük | 9903 m.10 |
| Bölgesel teşvikler | Yatırım bölgesine göre sigorta primi işveren hissesi desteği; 6. bölgede ayrıca sigorta primi (işçi hissesi) desteği | — | 9903 m.4/4, m.18, m.19 |

**Önemli fark (eski sisteme göre):** 9903'te bölge, KDV istisnası, gümrük muafiyeti ve vergi indirimi gibi unsurları değil, esas olarak **SGK primi desteğinin** süresini ve kapsamını belirler. Vergi indirimi ve faiz desteğinin oranı/tavanı **sisteme ve programa** göre değişir (m.15, m.20). Eski YAML'daki "öncelikli konulara 5. Bölge destekleri uygulanır" kuralı 2012/3305'e aittir ve 9903'te yoktur; öncelikli yatırımlar artık ayrı bir sistemdir. 

Ayrıca Dijital Dönüşüm Programı (m.11) ve Yeşil Dönüşüm Programı (m.12) yatırımları Stratejik Hamle ya da Öncelikli Yatırımlar kapsamında değerlendirilebilir; uygulama usul ve esasları ayrı tebliğlerdedir (ör. Yeşil Dönüşüm Programı Uygulama Usul ve Esasları Tebliği, son değişiklik RG 08.05.2026). 

**Bölgeler:** iller sosyo-ekonomik gelişmişliğe göre altı bölgeye ayrılır (EK-2). İlin hangi bölgede olduğunu **Karar EK-2'den oku**, beceri metninden ya da eski listeden yazma. OSB/endüstri bölgesi ya da EK-5'teki ilçeler bir alt bölge desteğinden yararlanır (yalnız SGK işveren hissesi desteği bakımından). 

**Geçiş:** 6 Şubat 2023 depremlerinden etkilenen ve 2018/11201 sayılı Kararın EK-2'sindeki ilçelerde ve Cazibe Merkezleri illerindeki OSB'lerde (imalat sanayii), belirli bir tarihe kadar yapılacak müracaatlarda 6. bölge destekleri uygulanır; son müracaat tarihini Karar geçici m.3-4'ten oku ve uzatılıp uzatılmadığını RG'de ara.  

**Son müracaat tarihi:** 9903 kapsamında müracaatlar Karar'da belirtilen tarihe kadar değerlendirilir (m.5/5'te 31.12.2030). 

---

## 2. Uygunluk kontrol listesi

1. **Belgeden önce harcama yapıldı mı?** Müracaat tarihinden önceki harcama kapsama alınmaz; makine siparişi verilmiş, avans ödenmiş, inşaat başlamışsa 🔴 ve ayrıştır. 
2. **Yatırım konusu desteklenebilir mi?** NACE Rev.2.1 kodu EK-3'te mi, kodun karşısında şart ya da hariç tutma var mı (ör. kapasite, alan, entegrasyon şartı; İstanbul'da desteklenmeyen konular)? Türkiye Yüzyılı Kalkınma Hamlesi, Dijital/Yeşil Dönüşüm ve m.9/1-v (deprem/yangın riski) yatırımlarında EK-3 şartı aranmaz. 
3. **Asgari sabit yatırım tutarı** sağlanıyor mu? Genel tutar bölge grubuna göre, programlarda ayrı tutarlar var; **tutarı Karardan ve güncel ilandan çek**, yazma `[doğrula]`. 
4. **Hangi sistem?** Önce Türkiye Yüzyılı Kalkınma Hamlesi (ürün öncelikli ürün listesinde mi; ilin yerel yatırım konularından biri mi; stratejik hamle listesinde mi ve ön değerlendirme kriterlerinden yeterli sayıda sağlanıyor mu), sonra Öncelikli Yatırımlar (m.9 bentleri), sonra Hedef Yatırımlar (EK-3). Hamle programına başvuru sürerken Sektörel Sistemden belge alınıp sonra revize edilebilir. 
5. **Konu bazlı kısıtlar:** elektrik üretimi, dağıtım, depolama, ana şebeke gaz dağıtımı ve İstanbul'daki hedef yatırımlar vergi indirimi alamaz; hedef yatırımlarda faiz desteği yalnız belirli bölgelerde; bazı öncelikli konularda faiz desteği yok. Konuya göre m.9/2-3 ve m.10/2-3'ü oku. 
6. **Yatırım cinsi:** komple yeni, tevsi, modernizasyon, ürün çeşitlendirme, entegrasyon, nakil. Komple yeni/tevsi/modernizasyon/ürün çeşitlendirme aynı il sınırında olmalı; bazı konular yalnız modernizasyon cinsinde belgelendirilir ve aktiften düşülecek makinenin firmada bulunma süresi ile alıcı-satıcı ortaklık şartı aranır. 
7. **Kim başvurabilir:** gerçek kişiler, adi ortaklıklar, sermaye şirketleri, kooperatifler, birlikler, iş ortaklıkları, kamu kurumları, dernek ve vakıflar, yabancı şirketlerin Türkiye şubeleri; kuruluşu tamamlanmamış tüzel kişi adına müracaat değerlendirilmez. 
8. **Ön şart belgeler:** SGK borcu yok yazısı (ya da yapılandırma), ÇED kararı/yazısı, gerekirse işyeri ruhsatı, sektörel izinler, büyük yatırımda proje bazlı formatta fizibilite. Teşvik belgesi izin ve ruhsatın yerine geçmez. 
9. **Kapsam dışı harcamalar:** hammadde, yedek parça, kullanılmış **yerli** makine, karayolu taşıtları (istisnalar hariç), tamir-bakım; turizm, sağlık, eğitim yatırımlarında makine listesine girebilecek ekipman sınırlı; inşaat malzemesi listeye girmez. 
10. **Maddi olmayan duran varlık** (marka, lisans, know-how) sabit yatırımın Karar'daki oranını aşamaz (Dijital Dönüşüm hariç) — oranı Karardan oku. 
11. **Ekosistem geliştirme planı:** KOBİ olmayan yatırımcı ya da Yerel Kalkınma Hamlesi yatırımcısı (vergi indirimi öngörülen yatırımlarda), Bakanlıkça onaylı bir ekosistem geliştirme planını tamamlama vizesine kadar gerçekleştirmekle yükümlüdür; asgari harcama sabit yatırıma oranla belirlenir. Plan tamamlanmazsa belge iptal sebebidir. 
12. **Diğer kamu desteği:** başka kurumdan destek alındı mı / alınacak mı? Birleşme yasağı → `destek-unsurlari-vergi-sgk-gumruk.md` §4. 

---

## 3. Süreler ve dayanakları

| İşlem | Süre / tarih | Dayanak |
|---|---|---|
| Harcamaya başlamadan önce müracaat | Müracaat tarihi = yatırımın başlangıcı | 9903 m.5/6, m.29/1  |
| Eksik belge tamamlama | Bildirimde süre yazmıyorsa 30 gün; süresinde tamamlanırsa ilk müracaat tarihindeki mevzuat uygulanır | Tebliğ 2025/1 m.8/3  |
| Eksik/çelişkili müracaatın yeniden yapılması | Yeni müracaat tarihindeki mevzuat uygulanır | Tebliğ 2025/1 m.8/2  |
| 9903 kapsamında son müracaat | Karar'daki tarih | 9903 m.5/5 |
| Deprem/Cazibe Merkezi geçiş desteği | Karar'daki tarihe kadar müracaat | 9903 geçici m.3-4 |
| Öncelikli ürün, yerel yatırım konuları, stratejik hamle listeleri | Her yıl ocak ayında güncellenebilir | 9903 m.6/4, m.7/5, m.8/9  |

---

## 4. Görüşme soruları (eski `incentive_discovery` profil alanlarından genişletildi)

| Soru | Neden |
|---|---|
| Yatırım nerede: il, ilçe, OSB/endüstri bölgesi/serbest bölge mi? | Bölge, alt bölge, İstanbul kısıtları |
| Ürün/hizmet ve NACE Rev.2.1 kodu? Kapasite? | EK-3 şartları, öncelikli ürün listesi, teknoloji sınıfı (EK-1) |
| Yatırım cinsi: komple yeni, tevsi, modernizasyon, nakil…? | Destek ve istihdam hesabı |
| Sabit yatırım kalemleri (arazi, bina, yerli/ithal makine, diğer, maddi olmayan varlık) ve toplamı? | Asgari tutar, maddi olmayan oran sınırı |
| Harcamaya başlandı mı, makine siparişi/avansı var mı? | m.5/6 |
| Firma KOBİ mi? Tescil tarihi (yeni kurulmuş mu)? | Ekosistem planı; yeni firmalara ek faiz/makine desteği seçeneği (m.20/4) |
| Mevcut istihdam ve planlanan ilave istihdam? | SGK desteği |
| Kredi kullanılacak mı (TL/döviz), finansal kiralama var mı? | Faiz/kâr payı desteği, kiralama şirketi sorumluluğu |
| Başka bir kamu kurumundan destek alındı mı/alınacak mı (KOSGEB, ajans, TÜBİTAK, proje bazlı)? | m.33 birleşme yasağı |
| Daha önce teşvik belgesi var mı, hangi karara dayanıyor, vizesi yapıldı mı? | Geçiş, devir, makine devri yasağı (geçici m.2/2) |

---

## 5. soorgla çağrıları

```
legal_search_official_gazette  query: "Yatırımlarda Devlet Yardımları Hakkında Karar"  search_in: "title"  sort_by: "date_desc"
legal_get_official_gazette_document  url: "https://www.resmigazete.gov.tr/eskiler/2025/05/20250530-2.pdf"  offset: 0  max_chars: 30000      # m.1-15
legal_get_official_gazette_document  url: "…20250530-2.pdf"  offset: 25000  max_chars: 30000                                              # m.15-29
legal_get_official_gazette_document  url: "…20250530-2.pdf"  offset: 50000  max_chars: 30000                                              # m.29-36, geçici, EK-1, EK-2, EK-3 başı
legal_get_official_gazette_document  url: "…20250530-2.pdf"  offset: 80000  max_chars: 25000                                              # EK-3 devamı, EK-4, EK-5
legal_search_official_gazette  query: "Öncelikli Ürün Listesi Tebliği"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "9903 sayılı Cumhurbaşkanı Kararı"  date_from: "<son 12 ay>"  sort_by: "date_desc"    # yerel yatırım konuları, stratejik hamle listesi, program usul esasları
legal_search_admin_guidance  sorgu: "<konu> yatırım teşvik belgesi"  tarih_baslangic: "2024-01-01"  belge_tur: "ozelge"   # GİB'in teşvik özelgeleri
```

9903 PDF'i OCR'lıdır (ı/ş/ğ bozuk, tablolar dağınık): **EK-2 il listesini ve EK-3 tablosunu satır satır okuyup kullanıcıya göstererek teyit ettir**; OCR karışıklığında `[doğrula — Bakanlık sitesindeki Karar metniyle]`. "Yerel Yatırım Konuları Listesi Tebliği" RG 09.07.2025'te yayımlandı, değişikliği RG 31.01.2026 (`query: "Yatırım Konuları"`, `search_in: "title"`). Stratejik hamle yatırım konuları listesi için ayrı başlıklı tebliğ bulunamadı: tanım 9903 m.2'de (Bakanlıkça belirlenen liste), program usulü Uygulama Tebliği 2025/1 m.12'de (RG 21.06.2025) — güncel listeyi Bakanlıktan/kullanıcıdan teyit et `[ARAŞTIRMA GEREKLİ: stratejik hamle yatırım konuları listesi]`.  

---

## 6. İdare tarafı (Genel Müdürlük uzmanı, ajans/il müdürlüğü görevlisi)

- Müracaatı Karar şartlarına ve "makroekonomik program, arz-talep dengesi, sektörel, mali ve teknik" değerlendirmeye göre ret/kabul ederken gerekçeyi yaz; ret işlemi idari dava konusudur (2577 m.7: 60 gün). 
- Eksiklik bildiriminde süreyi açıkça yaz; yazmazsan 30 gün işler.
- Müracaat tarihindeki mevzuatı esas al; eksik tamamlama süresinde tamamlanan müracaatta ilk tarih korunur.

---

## 7. Çıktı iskeleti

```markdown
## Teşvik uygunluk ön değerlendirmesi — [proje] — [tarih]
| Kriter | Durum | Not | Dayanak (Karar m./EK) |
| Belge öncesi harcama | | | m.5/6 |
| NACE ve EK-3 şartı | | | EK-3 |
| Asgari sabit yatırım | [doğrula — güncel tutar] | | m.5/2 |
| Uygun sistem/program | | | m.6-10 |
| Bölge / alt bölge | | | EK-2, m.22 |
| Konu bazlı kısıt | | | m.9/2-3, m.10/2-3 |
| Ekosistem planı | | | m.5/9 |
| Diğer kamu desteği | | | m.33 |
### Olası destek unsurları (oranlar Karar metninden, [doğrula])
### Yol haritası (sıra: önce müracaat, sonra harcama)
```

---

## 8. Sık hatalar

- 🔴 Belge alınmadan makine almak/inşaata başlamak ve "sonra kapsama alırız" demek.
- 🔴 2012/3305'e göre "6 bölge × destek oranı" tablosu kurmak; 9903'te oranlar sisteme ve programa göre.
- 🟠 Bölge listesini eski kararlardan ya da hafızadan yazmak (EK-2 değişebilir).
- 🟠 Öncelikli yatırıma "5. bölge desteği" atfetmek (2012/3305 kuralı).
- 🟠 OCR'lı Karar metnindeki tutar ve kodları doğrulamadan aktarmak.
- 🟡 Hamle programına başvuru sürerken Sektörel Sistemden belge alma seçeneğini atlamak.

---

