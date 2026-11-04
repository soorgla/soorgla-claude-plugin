# Genel sağlık sigortası (GSS)

**Ne zaman kullanılır:** GSS tescili ve prim borcu (özellikle 5510 m.60/1-g kapsamındaki "hiçbir yerden sağlık güvencesi olmayan" kişiler), gelir testi, sağlık hizmetinden yararlanma şartı ("provizyon çıkmıyor"), işten ayrılış sonrası sağlık hakkı, GSS borcunun emeklilik/aylık talebine etkisi.

**Kapsam dışı:** sağlık hizmet sunucularının (hastane, eczane) SGK ile sözleşme ve SUT uyuşmazlıkları; tıbbi malpraktis → `tazminat-haksiz-fiil` (`../../tazminat-haksiz-fiil/references/malpraktis-hekim-sorumlulugu.md`).

---

## Süre ve yol tablosu

| Konu | Kural | Dayanak |
|---|---|---|
| GSS tescili, prim tahakkuku, gelir testi sonucuna itiraz | Kuruma yazılı başvuru; 60 gün cevapsızlık = ret; sonra iş mahkemesi | 7036 m.4/1; 5510 m.101  |
| İşten ayrılan 4/1-a sigortalının sağlık hakkı | Zorunlu sigortalılığın sona ermesinden itibaren **10 gün**; son bir yılda 90 gün zorunlu sigortalılık varsa **90 gün** (bakmakla yükümlü olunanlar dahil) | 5510 m.67  |
| Mezun gençlerin sağlık hakkı | Lise mezunu 20, yükseköğrenim mezunu 25 yaşını geçmemek ve kendisi GSS'li olmamak kaydıyla mezuniyetten itibaren **2 yıl**, prim borcuna bakılmaksızın | 5510 m.67  |
| Ücretsiz izinde GSS | 4857 m.56 ve m.74 dışında bir takvim yılında toplam bir ayı aşmayan ve işverence belgelendirilen ücretsiz izinlerde GSS devam eder | 5510 m.67 son fıkra  |

---

## Kontrol listesi

### 1. Kişi hangi GSS kategorisinde?
- 5510 m.60'ı çek ve kişinin bendini belirle (çalışan 4/1-a, b, c; aylık alan; bakmakla yükümlü olunan kişi; (g) bendi — başka güvencesi olmayanlar; öğrenci ve uluslararası öğrenci; 7538 ile değişen 60/7).  
- Bakmakla yükümlü olunan kişi (eş, çocuk, ana-baba) olarak başka birinin üzerinden yararlanma imkânı var mı? Varsa (g) bendi tescili ve borç yersiz olabilir 🟠. 

### 2. Gelir testi ve prim tutarı
- (g) bendinde prim, aile içi kişi başı gelire göre belirlenir; gelir testi yaptırmamış olan en yüksek basamaktan tahakkuk görür. Gelir testine hiç başvurmayanlar ve geçmiş dönem için geçici maddeler (ör. geçici m.53) affedici düzenlemeler getirdi; somut kişinin dönemi için çek.  Basamak eşikleri ve oranları beceriye yazma; m.60 ve m.81/1-f'yi çek. 
- **1.1.2016 öncesine ait ödenmemiş (g) bendi GSS primleri ve fer'ileri silindi** (5510 geçici m.111, 7571 s. Kanun, RG 25.12.2025); ödenmiş olanlar iade edilmez. Kullanıcı eski dönem GSS borcundan söz ediyorsa önce bunu kontrol et. 🟠 

### 3. Sağlık hizmetinden yararlanma şartı (5510 m.67)
- 18 yaş altı, başkasının bakımına muhtaç, trafik kazası, acil hâl, iş kazası/meslek hastalığı, bildirimi zorunlu bulaşıcı hastalık, madde bağımlılığı tedavisi gibi hâllerde şart aranmaz. 
- Diğer hâllerde: başvurudan önceki son bir yılda toplam **30 gün** GSS prim ödeme günü; (g) bendi ve 4/1-b'de ayrıca **60 günden fazla prim borcu olmaması** (6183 m.48'e göre tecil-taksit devam edenler hariç).  Askerlik, hükümlülükle bitmeyen tutukluluk, geçici iş göremezlik ödeneği süresi ve grev-lokavt 30 gün hesabında dikkate alınmaz.
- Çözüm yolları: borcun ödenmesi ya da 6183 m.48'e göre taksitlendirme; bakmakla yükümlü olunan kişi statüsü; gelir testiyle primin Devletçe ödenmesi. `[incele]`

### 4. GSS borcunun diğer haklara etkisi
- 4/1-b sigortalıda **GSS dahil** prim borcu varken yaşlılık, malullük ve hak sahiplerine ölüm aylığı bağlanmaz.  → `emeklilik-ve-borclanma.md`.
- Borç zamanaşımı: prim alacağında 10 yıl (5510 m.93) → `sgk-uyum-ve-itiraz.md`.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "5510"  article_no: "60" | "67" | "81" | "82" | "93"
legal_get_statute_article  law_no: "5510"  article_no: "geçici 53" | "geçici 111"
legal_search_statute_semantic  sorgu: "genel sağlık sigortası gelir testi <konu>"  mevzuat_no: "5510"
legal_search_statute_semantic  sorgu: "gelir tespiti yönetmeliği genel sağlık sigortası"  mevzuat_tur: "kurum_yonetmeligi"
legal_search_official_gazette  query: "genel sağlık sigortası primi"  document_type: "kanun"  date_from: "<son 2 yıl>"
legal_get_statute_article  law_no: "6183"  article_no: "48"
legal_search_cases  mahkeme: "yargitay"  daire: "10. Hukuk Dairesi"
    sorgu: "<ör. genel sağlık sigortası tescilinin iptali bakmakla yükümlü olunan kişi>"
legal_get_social_parameters  tur: "asgari_ucret_brut"
```

---

## Görüşme soruları

1. Kişi şu anda çalışıyor mu, aylık alıyor mu, öğrenci mi?
2. Eşi, ana-babası ya da çocuğu üzerinden sağlık güvencesi olabilir mi?
3. GSS borcu hangi döneme ait, tutarı ve tebliğ tarihi?
4. Gelir testi yaptırıldı mı, sonucu?
5. Sağlık hizmeti neden alınamıyor (provizyon hatası, borç, 30 gün şartı)?
6. 4/1-b sigortalılığı var mı (emeklilik talebi gündemde mi)?

## Çıktı iskeleti

```markdown
## GSS değerlendirmesi: [kişi] — [tarih]
### Sonuç
### GSS kategorisi (5510 m.60 bendi) ve gerekçesi
### Borç durumu
| Dönem | Tutar | Silinme/af hükmü | Zamanaşımı | Durum |
### Sağlık hizmetinden yararlanma (m.67)
### Yol: Kuruma başvuru / taksit / gelir testi
### Eksik bilgi
```

## Sık hatalar

- 🔴 2016 öncesi (g) bendi GSS borcunun 7571 ile silindiğini atlamak.
- 🟠 Bakmakla yükümlü olunan kişi imkânını sormadan borcu kabul etmek.
- 🟠 4/1-b'de GSS borcunun emeklilik talebini engellediğini söylememek.
- 🟡 Acil hâl ve iş kazası istisnalarını unutmak.

---

