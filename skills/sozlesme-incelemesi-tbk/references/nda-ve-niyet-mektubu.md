# Gizlilik sözleşmesi (NDA) ve niyet mektubu (MoU / LOI)

Ticari görüşmelerin başında imzalanan iki belge: gizlilik sözleşmesi ve niyet mektubu / mutabakat zaptı / ön protokol.

## Ne zaman kullanılır
- "NDA'yı imzalayabilir miyiz", "gizlilik sözleşmesi", "karşılıklı gizlilik", "tek taraflı NDA", "confidentiality agreement".
- "Niyet mektubu bağlayıcı mı", "MoU", "LOI", "term sheet", "ön protokol", "mutabakat zaptı".
- İş sözleşmesindeki gizlilik ve rekabet maddesi → `../../is-hukuku/references/ise-alim-ve-rekabet-yasagi.md`. Kişisel veri paylaşımı → `../../kvkk/SKILL.md`.

Eski YAML'lar (`nda_analysis.yaml`, `memorandum_of_understanding.yaml`) **boş**; dosya sıfırdan, upstream `nda-review` becerisinin hızlı ayıklama mantığı Türk hukukuna uyarlanarak yazıldı.

---

## 1. NDA — hızlı ayıklama

Amaç (upstream): NDA'ların çoğu sorunsuzdur; birkaçında mayın vardır. Bir dakikada ayıkla ki avukat yalnız gerekenleri okusun.

### 1.1 Kapsam kontrolü (her şeyden önce)
Başlığı "Gizlilik Sözleşmesi" olan metin gizlilikten fazlasını yapıyor olabilir: **münhasırlık, rekabet etmeme, çalışan ayartmama, lisans verme, fikri mülkiyet devri, önalım (ROFR), en çok kayrılan müşteri (MFN), standstill, geniş tahkim şartı**. Bunlardan biri varsa NDA analizinin sonucu ne olursa olsun **otomatik SARI**: "Bu belge NDA başlıklı ama [X] içeriyor; NDA'dan fazlası, avukat incelemesine."

### 1.2 Kovalar
- **YEŞİL — imzaya gönder:** yalnız avukatça onaylanmış NDA pozisyonları profilde varsa ve hepsi karşılanıyorsa. Playbook yoksa YEŞİL **verilmez**; en iyi sonuç SARI.
- **SARI — avukat şu maddelere baksın:** sapma var ama kırmızı çizgi değil ya da playbook sessiz.
- **KIRMIZI — önce hukuk birimi:** "asla" listesindeki madde ya da yapısal uyumsuzluk (ör. playbook karşılıklılık isterken tek taraflı NDA; süresiz yükümlülük; kabul edilmeyen yabancı hukuk).

Temiz NDA'da çıktı tek cümledir: "Kırmızı bayrak yok. Standart onay sürecinden imzaya." Uzun rapor yazma.

### 1.3 Kontrol listesi

| Kod | Kontrol | Türk hukuku notu |
|---|---|---|
| KARŞILIKLILIK | Karşılıklı mı, tek taraflı mı? Tek taraflıysa sor: yalnız biz mi bilgi veriyoruz; dar ve belirli bir paylaşım mı; birleşme-devralma, iş ilişkisi ya da yatırım mı (öyleyse bu akış değil, hukuk birimi)? | — |
| TANIM | Gizli bilgi: işaretlenmiş olanlar mı, paylaşılan her şey mi? Sözlü bilginin yazıyla teyit süresi? | Çok geniş tanım ispatı zorlaştırır; çok dar tanım koruma açığı bırakır |
| İSTİSNALAR | Beş klasik istisna: kamuya açık olan/olan; önceden bilinen; bağımsız geliştirilen; üçüncü kişiden kısıtsız alınan; kanun ya da mahkeme/merci kararıyla açıklanması zorunlu olan (mümkünse karşı tarafa bildirimle) | Zorunlu açıklama istisnasına SPK, BDDK, Rekabet Kurumu, KVKK taleplerini ekle |
| HAFIZA (residuals) | "Yardımsız hafızada kalan bilgiyi kullanabilir" kaydı | Playbook'a göre; yoksa SARI |
| SÜRE | Sözleşme süresi ve sona erdikten sonra gizlilik süresi; ticari sırlar için daha uzun koruma | Süresiz gizlilik yükümlülüğünün sürekli borç ilişkisi olarak sınırlanması tartışması `[incele]` |
| İADE-İMHA | Bilgilerin iadesi/imhası; yedekleme ve arşiv sistemleri istisnası; yasal saklama yükümlülükleri (VUK, TTK defter saklama) | Kanuni saklama süresi istisnası eklenmeli |
| ALICILAR | Çalışanlar, danışmanlar, grup şirketleri: "bilmesi gereken" ölçütü ve onların ihlalinden sorumluluk | Yardımcı kişi sorumluluğu (TBK m.116) `[doğrula]` |
| CEZAİ-ŞART | İhlalde cezai şart var mı, karşılıklı mı, tutarı; tacir taraf indirim isteyemez | TBK m.179-182; TTK m.22 → `cezai-sart-ifa-ve-sorumluluk.md`. NDA ihlalinde zararın ispatı güç olduğundan cezai şart pratikte ana yaptırımdır |
| TEDBİR | İhtiyati tedbir talep hakkının saklı tutulması | HMK m.389 vd. `[doğrula]` |
| KİŞİSEL-VERİ | Paylaşılacak bilgide kişisel veri var mı? Varsa NDA yetmez; veri işleme/aktarım hükümleri | → `../../kvkk/SKILL.md` |
| HAKSIZ-REKABET | NDA dışında da iş sırlarının hukuka aykırı ifşası ve iş ürününden yetkisiz yararlanma haksız rekabettir | TTK m.55/1-c, 55/1-d |
| REKABET-YASAĞI | NDA'ya gizlenmiş rekabet etmeme/ayartmama | Kapsam kontrolüne düşer; ticari tarafta 4054, işçide TBK 444-447 |
| HUKUK-YETKİ | Uygulanacak hukuk ve yetkili mahkeme/tahkim | Yetki şartı yalnız tacirler arasında (HMK m.17) |
| YABANCI-HUKUK | Yabancı hukuk ve yabancı mahkeme seçimi | ORTAK-KURALLAR.md §2; o hukuka göre emin cevap verme |

### 1.4 Karşı taraf bağlamı
- Büyük şirket NDA'sı: genellikle değişmez; KIRMIZI'nın gerçek bitiş hattı mı, "formumuzdan farklı" mı olduğunu ayır, kararı yükselt.
- Küçük karşı taraf: en hızlı yol çoğu zaman "bizim formumuzu kullanalım".

### 1.5 Kapanış eylemi
Profilde `nda_kapanis_eylemi` varsa her çıktının sonuna aynen ekle (ör. "NDA'yı ve bu analizi hukuk@… adresine iletin"); yoksa: "Nihai NDA'yı standart onay sürecinizden geçirin." (upstream "closing action").

## 2. Niyet mektubu (MoU / LOI / term sheet)

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| BAĞLAYICILIK | Belge bağlayıcı mı? Ana sözleşmenin esaslı noktaları (taraflar, konu, bedel) belirlenmiş ve bağlanma iradesi varsa önsözleşme ya da doğrudan sözleşme sayılabilir | TBK m.1-2 (kurulma), m.29 (önsözleşme) | Başlık "bağlayıcı değildir" dese de içerik belirler `[incele]` |
| ÖNSÖZLEŞME-ŞEKLİ | İleride kurulacak sözleşme bir şekle tabiyse önsözleşme de o şekle tabi (kanundaki istisnalar hariç) | TBK m.29/2 | Ör. taşınmaz satış vaadi resmî, kefalet vaadi el yazısı (TBK 583/2) |
| BAĞLAYICI-HÜKÜMLER | Bağlayıcı olmayan belgede bile bağlayıcı yapılması gerekenler: gizlilik, münhasır görüşme (exclusivity) süresi, masraflar, uygulanacak hukuk | Sözleşme | Ayrı ayrı "bu madde bağlayıcıdır" diye yaz |
| CULPA-IN-CONTRAHENDO | Görüşmelerin dürüstlüğe aykırı kesilmesinden sorumluluk (sözleşme öncesi güven sorumluluğu) | TMK m.2; Yargıtay HGK 22.03.2022, 2019/435 E., 2022/352 K. | Masraf ve güven zararı riski `[incele]` |
| MÜNHASIRLIK | Münhasır görüşme süresi ve ihlal yaptırımı; rekabet hukuku | 4054 | Uzun münhasırlık SARI |
| KAMU | Kamu kurumuyla "protokol" ya da "mutabakat" — ihale mevzuatı istisnası mı? | 4734 | → `../../kamu-ihale/SKILL.md` |

## 3. Görüşme soruları
1. Bilgiyi kim veriyor, kim alıyor; amaç ne (iş ortaklığı değerlendirmesi, tedarik, yatırım, birleşme)?
2. Paylaşılacak bilgi türü: teknik, ticari, kişisel veri, kaynak kod?
3. Gizlilik ne kadar sürmeli; ticari sır var mı?
4. (MoU) Taraflar bu belgeyle bağlanmak istiyor mu? Hangi maddeler bağlayıcı olmalı?
5. Karşı taraf yurt dışında mı; hangi hukuk?

## 4. MCP adımları
```
legal_get_statute_article law_no: "6098" article_no: "1" | "2" | "29" | "116" | "179" | "182"
legal_get_statute_article law_no: "6102" article_no: "22" | "55"
legal_get_statute_article law_no: "6100" article_no: "17" | "389"
legal_search_cases mahkeme: "yargitay" daire: "11. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "gizlilik sözleşmesinin ihlali nedeniyle cezai şart talebi ticari sır"
legal_search_cases mahkeme: "yargitay" sorgu: "niyet mektubu esaslı unsurları içerdiğinden önsözleşme niteliğinde bağlayıcıdır"
```

## 5. Çıktı iskeleti
```markdown
## NDA ayıklama: [karşı taraf]
**[YEŞİL — imzaya gönder | SARI — [onaylayan] baksın | KIRMIZI — önce hukuk birimi]**
**Kapsam kontrolü:** [yalnız gizlilik | NDA'dan fazlası: …]

### Yönetici özeti
- [tek satırlık mekanik düzeltme, ör. "Madde 6'daki çalışan ayartmama yasağını çıkarın"]
- [karmaşık olan: "Madde 4 — hukuk birimine yönlendirin"]

### İşaretli maddeler
**1. [Konu]** — Madde [X]
   Ne: … · Neden: [playbook pozisyonu / playbook sessiz]
   Hukuki risk: 🔴/🟠/🟡/🟢 · İş sürtünmesi: …
   Muhtemel çözüm: …

### Geçen kontroller
| Kontrol | Durum |

[kapanış eylemi]
```

## 6. Sık hatalar
- "NDA" başlığına güvenip içindeki münhasırlık ya da rekabet yasağını kaçırmak.
- Playbook yokken YEŞİL vermek.
- Kanuni saklama yükümlülüklerini imha maddesinden istisna etmemek.
- Kişisel veri paylaşımını NDA ile çözmeye çalışmak.
- "Bağlayıcı değildir" yazılı MoU'yu her durumda bağlayıcı değil saymak; ya da şekle tabi ana sözleşmenin önsözleşmesini şekilsiz yapmak.

---
