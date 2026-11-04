# Yazılım lisansı, SaaS ve bakım-destek sözleşmeleri

Hazır yazılımın kullanım hakkı (lisans), bulut tabanlı abonelik (SaaS), ısmarlama yazılım geliştirme ve bakım-destek sözleşmeleri.

## Ne zaman kullanılır
- "Lisans sözleşmesi", "son kullanıcı lisansı (EULA)", "SaaS abonelik", "hizmet seviyesi (SLA)", "otomatik yenileme", "kaynak kod", "verilerimizi geri alabilir miyiz", "yapay zekâ eğitiminde verimizi kullanabilir mi".
- Yazılımın sıfırdan geliştirilmesi → eser yönü `eser-ve-insaat.md`, hak devri yönü bu dosya.
- Kişisel veri işleme eki (DPA), alt işleyenler, yurt dışı aktarım → `../../kvkk/SKILL.md` (bu dosya yalnız işaret koyar).

Eski YAML `software_license_agreement.yaml` **boş**; dosya sıfırdan, upstream `saas-msa-review` becerisinin SaaS katmanı Türk hukukuna uyarlanarak yazıldı.

---

## 1. Fikri mülkiyet temeli (FSEK)

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ŞEKİL | Mali haklara ilişkin sözleşme ve tasarruflar **yazılı** olmalı ve konu olan haklar **ayrı ayrı** gösterilmeli (işleme, çoğaltma, yayma, temsil, umuma iletim) | FSEK m.52 | "Tüm haklar devredilmiştir" genel ifadesi yetersizlik riski → SARI/KIRMIZI |
| DEVİR-RUHSAT | Mali haklar süre, yer ve içerik bakımından sınırlı/sınırsız devredilebilir ya da yalnız kullanma yetkisi (ruhsat/lisans) verilebilir; münhasır mı basit mi açık yazılmalı | FSEK m.48/1-2 | Lisansta münhasırlık ve alt lisans yetkisi ayrı yaz |
| GELECEK-ESER | Henüz meydana getirilmemiş ya da tamamlanacak esere ilişkin tasarruf işlemleri hakkında kanun kısıtı | FSEK m.48/3; m.50 | m.48/3: henüz meydana getirilmemiş ya da tamamlanacak esere ilişkin tasarruf bâtıl; m.50: tasarrufa ilişkin taahhüt geçerli, gelecekteki eserlerin bütününe ya da türüne ilişkin taahhüt bir yıl önceden ihbarla feshedilebilir; geliştirme sözleşmesinde hak devrini **teslim/tamamlanmayla** bağlayan yapı kur `[incele]`  |
| ÇALIŞAN-ESERİ | İşçi ve memurların işlerini görürken meydana getirdikleri eserlerde haklar, aksi kararlaştırılmadıkça işverence kullanılır | FSEK m.18/2 | **Bağımsız yüklenici/freelance geliştiricide bu kural yok** → hak devri sözleşmeyle ve m.52 şekliyle yapılmalı |
| MANEVİ-HAK | Umuma arz, adın belirtilmesi, eserde değişiklik; şeref ve itibarı zedeleyen yayım ya da değişikliği menetme yetkisinden sözleşmeyle vazgeçme hükümsüz (m.14/3, m.16/3); kullanılmama taahhüdü sınırları | FSEK m.14-17 | `[incele]`  |
| AÇIK-KAYNAK | Teslim edilen yazılımda açık kaynak bileşen ve lisans yükümlülükleri (copyleft) beyanı | Sözleşme | Garanti/beyan maddesi iste |

## 2. Sözleşme kontrol listesi (lisans + SaaS)

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| KAPSAM | Kullanıcı sayısı, cihaz, coğrafya, grup şirketleri, alt lisans, devredilebilirlik | FSEK m.48 | |
| BEDEL-DÖVİZ | Yurt dışında üretilen yazılımın satışı ve yurt dışında üretilen donanım/yazılımın lisans ve hizmet sözleşmelerinde dövizli bedel **serbest**; yurt içinde üretilen yazılım lisansında ve yerli SaaS'ta Türkiye'de yerleşikler arası dövizli bedel genel kurala (hizmet → yasak) tabi `[incele]` | 2008-32/34 Tebliğ m.8/11, 8/7 | → `odunc-ve-yabanci-para.md` §2 |
| OTOMATİK-YENİLEME | Yenileme süresi, iptal bildirim penceresi, bildirim yöntemi (e-posta / portal / yazılı), yenilemede fiyat (aynı / TÜFE sınırlı / güncel liste / sınırsız) — **yenileme tarihini ve iptal son gününü her durumda çıkar** | Sözleşme; tüketicide 6502 m.52/3 | Tüketici abonelik sözleşmesine "süre kadar kendiliğinden uzar" hükmü **konamaz**; uzatma tüketicinin talebi/onayıyla |
| TÜKETİCİ-FESİH | Tüketici belirsiz süreli ya da bir yıldan uzun belirli süreli aboneliği gerekçesiz ve cezasız istediği zaman feshedebilir; fesih yöntemi kuruluş yönteminden ağır olamaz; ödenen fazla ücret 15 gün içinde iade | 6502 m.52/4-5 | B2B SaaS'ta bu kural yok; playbook'a göre |
| FİYAT-ARTIŞI | Yıllık artış (sabit oran / TÜFE / sınırsız); aşım (overage) fiyatı; "ek hizmet" tanımının genişliği | Sözleşme; TBK m.24 (GİK tek yanlı değişiklik) | Tek yanlı fiyat/şart değişikliği GİK'te yazılmamış sayılır → `genel-islem-kosullari-ve-tuketici.md` |
| VERİ-ÇIKIŞ | Dışa aktarım biçimi (açık/standart), ne zaman (her zaman / talep üzerine / yalnız sona ermede), sona ermeden sonra erişim süresi, maliyeti, silme teyidi; sağlayıcının "anonimleştirilmiş/toplulaştırılmış" türev veriyi saklaması | Sözleşme; 6698 | İş birimi için en kritik madde çoğunlukla budur |
| SLA | Erişilebilirlik taahhüdü, ölçüm dönemi, hizmet kredisi (hesap, tavan, **tek çare** mi), planlı bakım istisnası; kredinin sorumluluk tavanıyla ilişkisi | Sözleşme; TBK m.115 | Hizmet kesintisi iş için kritik değilse bu bölümde pazarlık sermayesi harcama |
| ALT-İŞLEYEN | Alt işleyen listesi, değişiklik bildirimi, itiraz/fesih hakkı | 6698 | → `../../kvkk/SKILL.md` |
| HİZMET-DEĞİŞİKLİĞİ | Önemli olumsuz değişiklikte fesih hakkı; kullanılan özelliğin kaldırılması (deprecation) bildirim süresi | Sözleşme; TBK m.24 | |
| YAPAY-ZEKA | Aşağıdaki 7 soru | Sözleşme; 6698 | Sözleşme hepsinde sessizse bu da bir bulgudur |
| KAYNAK-KOD | Ismarlama yazılımda kaynak kod teslimi; hazır yazılımda **escrow** (iflas, destek sonu, şirket devri tetikleyicileri) | Sözleşme | |
| AYIP-GARANTİ | Yazılım hatası ve ayıp: geliştirmede eser hükümleri (TBK m.474-478); lisansta "olduğu gibi" kaydı ve TBK m.115 sınırı | TBK m.115, m.474-478 | |
| SORUMLULUK | Dört pozisyon (doğrudan/dolaylı, matrah, istisnalar: veri ihlali, gizlilik, fikri mülkiyet tazmini) | `genel-inceleme-ve-playbook.md` §1 | SaaS'ta tavanın üstündeki istisnalar çoğu zaman gerçek riskin tamamıdır |
| FM-TAZMİN | Üçüncü kişinin fikri mülkiyet ihlali iddiasında savunma ve tazmin; çare (değiştir / lisans al / iade) | Sözleşme | |
| ŞARTLARA-ATIF | "Sağlayıcının internet sitesindeki güncel şartlar ve gizlilik politikası sözleşmenin parçasıdır" — tek yanlı güncellemeye açık kapı | TBK m.21, m.24 | Atıfla dahil edilen metni oku ya da "okunmadı" diye ayrı etiketle |
| MESAFELİ | Tüketiciye mesafeli satışta ön bilgilendirme ve cayma (dijital içerikte istisnalar) | 6502 m.48; Mesafeli Sözleşmeler Yönetmeliği |  |

### Yapay zekâ ve makine öğrenmesi hakları — 7 soru (upstream "AI/ML data rights decision procedure")
1. **Açık izin:** Müşteri verisi, içeriği ya da kullanım verisi model eğitimi/iyileştirme için kullanılabilir mi?
2. **Politikayla örtülü izin:** "Güncel gizlilik politikamız" atfı, "hizmet iyileştirme" ya da "analitik" gibi geniş amaçlar tek yanlı güncellemeyle eğitim iznine dönüşebilir mi? (TBK 24 süzgeci)
3. **Anonimleştirme ölçütü:** "Anonim" tanımlanmış mı; geri döndürülebilir mi? (KVKK anlamında anonim veri ölçütü → kvkk)
4. **Rakip kirlenmesi:** Sağlayıcı rakiplerimize de hizmet veriyor mu; verimiz onların çıktısına sızabilir mi?
5. **Vazgeçme (opt-out):** Kapsamı, kalıcılığı, yenilemede ve şart güncellemesinde korunup korunmadığı; varsayılan açık mı?
6. **Çıktı sahipliği:** Yapay zekâ çıktıları kime ait; sağlayıcı çıktıları eğitim örneği yapabilir mi? Üçüncü taraf model sağlayıcısına veri gidiyor mu (alt işleyen listesi)?
7. **Düzenleyici zincir:** Sağlayıcının kullanımı bize KVKK veri sorumlusu yükümlülüğü, yurt dışı aktarım ya da sektör düzenlemesi (BDDK, SPK) riski doğuruyor mu?

## 3. Kimin adına?
- **Müşteri (satın alma tarafı):** veri çıkışı, eğitim yasağı, SLA'nın gerçek işe etkisi, fiyat artış tavanı, otomatik yenileme iptal penceresi, kaynak kod/escrow, FSEK 52'ye uygun hak devri (geliştirmede).
- **Sağlayıcı (satış tarafı):** sorumluluk tavanı ve istisnaların dar tutulması, kullanım sınırları, ödeme gecikmesinde askıya alma, toplulaştırılmış veri kullanım hakkı (açık ve KVKK'ya uygun), tüketiciye satışta 6502 m.52 uyumu.

**Neye savaşılmaz:** büyük SaaS sağlayıcıları metinlerini nadiren değiştirir; yıllık bedeli düşük ve alternatifi bol bir araçta hafif dokun, platform niteliğindeki ve geçiş maliyeti yüksek sözleşmede tam incele (upstream).

## 4. Yenileme takibi devri
Yenileme tarihi ve iptal penceresi bulunduysa şu kaydı çıkar (alan yoksa boş bırak ve söyle); takvime ya da sözleşme yönetim sistemine eklendiğini **doğrulamadan** "takibe aldım" yazma:
```yaml
karsi_taraf:
sozlesme:
imza_tarihi:
ilk_donem_sonu:
yenileme_mekanizmasi:      # ör. "yıllık otomatik"
iptal_bildirim_suresi_gun:
iptal_son_gunu:            # ilk_donem_sonu - bildirim süresi; legal_check_holiday ile kontrol
yenilemede_fiyat:
yillik_bedel:
is_birimi_sorumlusu:
```

## 5. Görüşme soruları
1. Hazır yazılım mı, bulut hizmeti mi, size özel geliştirme mi?
2. Kullanıcı sayısı, yıllık bedel, sözleşme süresi, para birimi; yazılım yurt dışında mı üretiliyor?
3. Hizmete kesinti ne kadar zarar verir (iş açısından kritik mi)?
4. Hangi veriler (kişisel veri, ticari sır) sisteme girecek?
5. Sözleşme bittiğinde verileri nasıl alacaksınız; ne kadar süre erişim lazım?
6. (Geliştirme) Geliştiriciler çalışan mı, bağımsız yüklenici mi? Kaynak kod size teslim edilecek mi?

## 6. MCP adımları
```
legal_get_statute_article  law_no: "5846"  article_no: "14" | "18" | "48" | "50" | "52"
legal_get_statute_article  law_no: "6502"  article_no: "48" | "52"
legal_get_statute_article  law_no: "11990"  article_no: "8"
legal_get_statute_article  law_no: "6098"  article_no: "21" | "24" | "115"
legal_search_cases  mahkeme: "yargitay"  daire: "11. Hukuk Dairesi"
    sorgu: "yazılım lisans sözleşmesi mali hakların ayrı ayrı gösterilmemesi FSEK 52 şekil şartı"
legal_check_holiday  # iptal son günü
```
Daire: yazılım geliştirme eser sözleşmesi olarak eser dairesine; FSEK ve SMK'dan kaynaklanan davalar, tarafların ve mahkemenin sıfatına bakılmaksızın 2026/1 iş bölümüne göre 11. HD'ye gider; iş bölümü her yıl değişir, yeniden kontrol et. 

## 7. Çıktı iskeleti
`genel-inceleme-ve-playbook.md` §9 + SaaS ek bölümü:
```markdown
### Sonuç
[İmzalanabilir / önce X için mücadele / vazgeç — tek cümle]
### Yapay zekâ ve veri hakları
### SaaS'a özgü bulgular
#### Otomatik yenileme — yenileme: [tarih] · iptal son günü: [tarih] · fiyat: [mekanizma]
#### Fiyat artışı
#### Veri çıkışı   ← iş biriminin okuması gereken bölüm
#### SLA [ya da "Atlandı — hizmet iş için kritik değil"]
#### Alt işleyenler → kvkk
#### Hizmet değişiklikleri
```
Her SaaS bulgusu iki ölçek taşır: hukuki risk ve iş sürtünmesi. Veri çıkışı, otomatik yenileme ve fiyat artışı çoğu zaman "hukuken 🟢, iş için 🔴"dir; iş sürtünmesi derecesinden raporla.

## 8. Sık hatalar
- "Tüm fikri haklar devredilmiştir" ibaresini FSEK 52'ye yeterli saymak.
- Freelance geliştiricinin kodunda FSEK 18'e güvenmek.
- Tüketici SaaS'ına otomatik uzama hükmü koymak (6502 m.52/3).
- Atıfla dahil edilen kullanım şartlarını okumadan "temiz" demek.
- Yerli yazılım lisansında dövizli bedeli serbest sanmak.
- Yapay zekâ eğitim izni konusunda sessiz sözleşmeyi "sorun yok" diye geçmek.

---

