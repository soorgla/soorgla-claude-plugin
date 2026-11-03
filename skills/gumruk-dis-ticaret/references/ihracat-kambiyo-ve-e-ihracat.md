# İhracat: ihracat bedeli ve kambiyo, e-ihracat, ihracatta yaptırımlar

## Ne zaman kullanılır
- "İhracat bedeli süresinde gelmedi, banka vergi dairesine bildirdi / ceza geldi."
- İhracat bedeli kabul belgesi (IBKB), bedelin bankaya satışı, mahsup, iade (reklamasyon, kalite sorunu).
- E-ihracat: mikro ihracat, elektronik ticaret gümrük beyannamesi (ETGB), posta ve hızlı kargo.
- İhracatta beyan ile gerçek eşya farkı; sahte ihracat.
- İhracat teşvik ve destekleri → `../../tesvik-yatirim/SKILL.md`; ihracat istisnasının ve ihraç kayıtlı teslimin KDV yönü → `../../vergi/SKILL.md`.

---

## Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| İhracat bedelleri kambiyo mevzuatına tabi | İhracat bedellerinin yurda getirilmesi kambiyo mevzuatı hükümlerine tabidir | İhracat Yönetmeliği (10365) m.18/1 |
| Ödeme şekilleri ve beyan dövizi | Bedel beyan edilen Türk parası ya da döviz üzerinden yurda getirilir; yolcu beraberinde efektif getirilirse gümrüğe beyan zorunlu | 32 sayılı Karara İlişkin Tebliğ (İhracat Bedelleri) 2018-32/48 m.3 |
| Hesap kapatma, ihbar, ek süre | Süresi içinde gelen bedellerle ilgili hesaplar aracı bankalarca kapatılır, IBKB düzenlenir; süresinde kapatılmayan hesaplar bankalarca bildirilir; ek süre imkânı | Tebliğ 2018-32/48 m.8 Getirme süresi, ek süre şartları ve bedelin bankaya satılma oranı sık değişir ve soorgla'da madde madde okunamıyor: bunları **metne yazma**; `legal_search_official_gazette` (`query: "İhracat Bedelleri"`, `search_in: "title"`, `sort_by: "date_desc"`) ile son tebliğ değişikliğini ara, TCMB İhracat Genelgesi için kullanıcıdan güncel metni iste; bulunamazsa `[ARAŞTIRMA GEREKLİ: ihracat bedeli getirme süresi/satış oranı — Tebliğ 2018-32/48 + TCMB İhracat Genelgesi]`. |
| Kambiyo yaptırımı (2025) | 1567 m.3 yeniden düzenlendi: 1. maddedeki kıymetlerin izinsiz yurttan çıkarılması/sokulması 5607'ye göre suç ya da kabahat oluşturmuyorsa rayiç bedelin yarısından iki katına kadar idari para cezası (teşebbüste yarı indirim); 1567'deki fiiller "suç" yerine "kabahat"; tekerrürde artırım | 7555 m.2 (RG 24.07.2025) İhracat bedelini getirmemenin hangi fıkradaki yaptırıma bağlandığı `[doğrula]`. |
| İhracatta beyan farkı | Teşvik/iade amacıyla gerçekleşmemiş ihracatı gerçekleşmiş gibi gösterme ya da cins, miktar, evsaf, fiyatı farklı gösterme 5607 m.3/9 suçu; beyan ile gerçek eşya arasındaki fark **%10'u aşmıyorsa** yalnız 4458'e göre işlem | 5607 m.3/9 |
| İhracı yasak eşya | Kanunen ihracı yasak eşyayı ülkeden çıkarma suç | 5607 m.3/8 |
| İhracat vergisine tabi eşya | Gümrük işlemine tabi tutmadan ya da vergisi ödenmeden çıkarma → vergiler + iki katı idari para cezası | 4458 m.239/2 |

---

## E-ihracat

- **Posta ve hızlı kargo:** Posta ve Hızlı Kargo Yoluyla Taşınan Eşyanın Gümrük İşlemlerine İlişkin Tebliğ (Seri No: 1) (RG 22.04.2022); hızlı kargo şirketleri ve posta idaresi eşyanın gümrük işlemlerini **dolaylı temsil** yoluyla yürütür; basitleştirilmiş gümrük beyannamesi. Dolaylı temsilcinin sorumluluğu m.181/2 sınırındadır.
- **ETGB:** elektronik ticaret gümrük beyannamesiyle mal ihracatında gelir vergisi uygulaması GVK Genel Tebliği Seri No 314 m.9 vd.'de; ETGB'nin kapsamı (değer ve ağırlık sınırları) tebliğde — sınırları metne yazma. Posta ve hızlı kargo tarafında 4458 Uygulama Kararı m.126/1-b son olarak CB Kararı 8362 (RG 20.04.2024) ve 10813 (RG 07.01.2026, yayımdan 30 gün sonra yürürlük) ile değişti; ETGB'nin kendi değer/ağırlık sınırları için ilgili gümrük genel tebliğinin güncel metnini RG'de (`search_in: "title"`, `sort_by: "date_desc"`) ara, bulamazsan `[ARAŞTIRMA GEREKLİ: ETGB sınırları]`.
- E-ihracatta ihracat bedelinin tahsili (pazaryeri, ödeme kuruluşu) ve IBKB düzenlenmesi `[doğrula]`.

---

## GİB görüşleri (kesişim)

`legal_search_admin_guidance` ile ihracat bedelinin iadesi, KKDF, ihraç kayıtlı teslim özelgeleri bulunuyor (ör. "İhracat Bedeli İadesi hk." 10.06.2024; "İhracat Bedelinin İadesinde KKDF hk." 02.04.2024). Bu özelgeler idareyi yalnız talep sahibine karşı bağlar (→ `../../vergi/references/ozelge-ve-idari-gorus.md`).

---

## Kontrol listesi — ihracat bedeli gelmedi

1. Fiili ihraç tarihi, ödeme şekli (peşin, mal mukabili, vesaik mukabili, akreditif, kabul kredili), vade.
2. Getirilme süresi ve ek süre talep edildi mi `[doğrula]`?
3. Bedel neden gelmedi: alıcının iflası, kalite reklamasyonu, iade, mahsup? Belgelenebiliyor mu?
4. Banka bildirimi yapıldı mı; vergi dairesi/idare hangi yaptırımı uyguladı?
5. 1567 m.3 (7555 sonrası) ve 32 sayılı Karar m.8 hangi fıkra; idari para cezası mı?
6. Yaptırıma karşı yol: 1567 m.3 cezalarına karar vermeye **Cumhuriyet savcısı** yetkilidir (m.3 son fıkra); m.3'te ayrı başvuru yolu yok; genel kural Kabahatler Kanunu m.27 — tebliğ/tefhimden itibaren **15 gün** içinde sulh ceza (hâkimliği) başvurusu. Aynı işlemde idari yargıya giren bir karar da varsa m.27/8 uyarınca birlikte idari yargıda görülür `[incele]`.

## Kontrol listesi — e-ihracat

1. Gönderi ETGB sınırları içinde mi; değilse normal beyanname gerekir.
2. Satış belgesi ve platform kayıtları, bedel tahsili.
3. Kargo şirketiyle dolaylı temsil sözleşmesi; yanlış beyan sorumluluğu.
4. Vergi indirimi/istisnası (GVK GT 314) → vergi becerisi.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Hangi beyannameyle ihraç ettiniz, fiili ihraç tarihi? | Süre |
| Ödeme şekli ve vadesi? | Getirilme süresi |
| Bankadan bildirim ya da ihbar yazısı geldi mi? | Yaptırım süreci |
| Bedel kısmen geldi mi, iade/reklamasyon belgesi var mı? | Mahsup ve mazeret |
| Gönderi ETGB ile mi, kargo şirketi kim? | E-ihracat |

---

## soorgla çağrıları

```
legal_search_statute_semantic sorgu: "ihracat bedellerinin yurda getirilmesi" mevzuat_no: "24798" # tek TABLO kaydı döner
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/07/20250724-2.htm" # 7555
legal_get_statute_article law_no: "5607" law_type: "Kanun" article_no: "3"
legal_search_statute_semantic sorgu: "posta ve hızlı kargo basitleştirilmiş gümrük beyannamesi" mevzuat_tur: "teblig"
legal_search_admin_guidance sorgu: "ihracat bedeli <konu>" kurum: "Gelir İdaresi Başkanlığı" belge_tur: "ozelge"
legal_search_official_gazette query: "32 Sayılı Karara İlişkin Tebliğ" search_in: "title" sort_by: "date_desc"
```

---

## Çıktı iskeleti

```markdown
## İhracat bedeli değerlendirmesi — [beyanname]
| İhraç tarihi | Ödeme şekli | Getirilme süresi (kaynak) | Gelen/gelmeyen tutar | Mazeret belgesi | Yaptırım riski |
### Önerilen adım (ek süre, mahsup belgesi, itiraz)
```

---

## Sık hatalar

- 🔴 Getirilme süresini ve satış oranını model bilgisinden söylemek (sık değişir).
- 🟠 1567 fiillerini 7555 sonrası hâlâ "suç" diye nitelemek.
- 🟠 %10'u aşmayan beyan farkını kaçakçılık saymak (5607 m.3/9 son cümle).
- 🟡 ETGB sınırlarını eski tebliğden almak.

---

## İdare tarafı
- Banka bildiriminden sonra yükümlünün mazeret ve mahsup belgelerini değerlendirmeden yaptırım uygulama.

---
