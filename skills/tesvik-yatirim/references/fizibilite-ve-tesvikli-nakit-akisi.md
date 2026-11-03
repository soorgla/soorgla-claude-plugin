# Fizibilite ve teşvikli nakit akışı (IRR, NPV, geri ödeme, hassasiyet)

## Ne zaman kullanılır
- "Bu yatırımın IRR/NPV'si ne olur?", "teşvikle ve teşviksiz karşılaştır", "geri ödeme süresi", "hammadde %10 artarsa?"
- Teşvik belgesi müracaatı, Stratejik Hamle fizibilitesi, banka kredisi ya da Bakanlık finansman programı için hazırlanan raporun **finansal model ve teşvik bölümü**.

**Rapor metni** (yönetici özeti, pazar, teknik analiz, SWOT, sonuç) → `../../idari-ve-kurum-basvurulari/references/yatirim-fizibilite-raporu.md`. Bu dosya o rapora girecek hesap tablosunu ve teşvik etkisini üretir.

**Temel sınır:** finansal projeksiyon **uydurulmaz**. Gelir, gider, yatırım tutarı, iskonto oranı, vergi oranı, kredi koşulları kullanıcıdan gelir `[kullanıcı verdi]`; yoksa tablo `[___]` kalır ve eksik veri listesi verilir. Teşvik oranları ve tavanları Karardan çekilir; beceri metninde sayı yoktur.

---

## 1. Kontrol listesi

1. **Amaç ve muhatap:** Bakanlık (teşvik/Stratejik Hamle), kalkınma ve yatırım bankası, ticari banka, iç karar? Stratejik Hamle'de fizibiliteyi Bakanlıkla protokollü kalkınma ve yatırım bankası hazırlar; büyük yatırımlarda müracaatta proje bazlı formatta fizibilite istenebilir.
2. **Yatırım tutarı ayrımı:** arazi-arsa, bina-inşaat, yerli makine, ithal makine (döviz cinsiyle), diğer harcamalar (etüt-proje, nakliye-montaj, aktifleştirilen kur farkı/faiz, maddi olmayan varlık), işletme sermayesi ayrı. Sabit yatırım tutarı faiz/makine desteği düşülmeden, **vergi indirimine esas** tutar ise bu destekler düşülerek hesaplanır.
3. **Teşvik kalemleri nakit akışına nasıl girer:**
   - Gümrük muafiyeti ve KDV istisnası → yatırım anındaki çıkışı azaltır (KDV istisnası ayrıca KDV iadesi/devri finansman yükünü ortadan kaldırır).
   - Vergi indirimi → işletme yıllarında vergi çıkışını azaltır; **7555 sonrası belgelerde en fazla on hesap dönemi** ve kazanç varken kullanılmayan katkı devretmez — modelde dönem sınırı ve kazanç profilini birlikte uygula.
   - Faiz/kâr payı ya da makine desteği → Hamle'de ilerleme raporuna bağlı, harcama yılını izleyen yıl ödenir (zamanlama gecikmesi); ikisi birlikte olmaz.
   - SGK işveren hissesi desteği → vize sonrası başlar; süresi bölge/programa göre (Karar m.18 tablosu).
   - Toplam destekler gerçekleşen sabit yatırımı geçemez (yeniden değerlenmiş).
4. **Göstergeler:** NPV (kullanıcının iskonto oranıyla), IRR, basit ve iskontolu geri ödeme süresi; teşvikli ve teşviksiz iki senaryo; kullanıcı veri verirse hassasiyet (girdi maliyeti ↑, satış fiyatı ↓, kur, faiz) ve başabaş.
5. **Enflasyon ve kur:** nominal/reel tutarlılık; TL nakit akışını nominal iskonto oranıyla, reel akışı reel oranla iskontola. Kur için `legal_get_exchange_rate`, TÜFE değişimi için `legal_calculate_cpi_change` (yalnız TÜFE; yeniden değerleme oranı ÜFE bazlıdır) `[doğrula]`.
6. **Tutarlılık testleri:** yıllar toplamı, kapasite × fiyat = gelir, amortisman ile sabit yatırımın uyumu, işletme sermayesi geri dönüşü, kredi geri ödeme planı ile faiz desteği süresi.
7. **Hukuki risk ayarlaması:** belge iptali/kısmi müeyyide senaryosu (destekler gecikme zammıyla geri alınırsa NPV ne olur?) `[incele]` → `iptal-muyyide-ve-geri-alma.md`.

---

## 2. Formüller (açık yaz, kullanıcının kontrol etmesi için)

```
NPV = Σ_{t=0..n} NA_t / (1 + r)^t
IRR : Σ_{t=0..n} NA_t / (1 + IRR)^t = 0 (sayısal çözüm; birden fazla işaret değişiminde birden çok IRR olabilir — uyar)
Geri ödeme : kümülatif NA'nın sıfırı geçtiği yıl (+ kesir); iskontolu sürümde NA_t/(1+r)^t
NA_t (teşvikli) = NA_t (teşviksiz) + gümrük/KDV etkisi_t + vergi indirimi etkisi_t + faiz/makine desteği_t + SGK desteği_t
```

Hesap gerekiyorsa bir hesap tablosu ya da kod ile yap, sonucu tabloya koy; ara adımları göster. `[incele]` — IRR/NPV hukuki görüş değildir; mali müşavir/finans uzmanı onayı gerekir.

---

## 3. Görüşme soruları (eski `financial_feasibility` ve `draft_investment_feasibility` alanları)

| Soru | Neden |
|---|---|
| Yatırım kalemleri ve yıllara dağılımı; ithal makine döviz cinsi? | Yatırım çıkışı, kur |
| Kapasite, kullanım oranı, satış fiyatı ve miktar projeksiyonu (5 yıl ve sonrası)? | Gelir |
| Hammadde, enerji, personel, genel gider varsayımları? | Gider |
| Finansman: özkaynak/kredi, vade, faiz, para birimi; finansal kiralama? | Faiz desteği, nakit akışı |
| İskonto oranı (sermaye maliyeti) ve proje ömrü/kalıntı değer? | NPV |
| Vergi oranı varsayımı ve kazanç beklenen ilk yıl? | Vergi indirimi zamanlaması |
| Hangi teşvik unsurları belgede/beklenen? | Teşvikli senaryo |
| Rapor kime sunulacak, format şartı var mı? | Biçim |

---

## 4. soorgla çağrıları

```
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/05/20250530-2.pdf" offset: 25000 max_chars: 30000 # m.15-20 oran ve tavanlar
legal_search_statute_semantic sorgu: "yatırıma katkı tutarı indirimli kurumlar vergisi" mevzuat_no: "5520"
legal_get_exchange_rate para_birimi: "<USD|EUR>" tarih: "<tarih>"
legal_calculate_cpi_change baslangic: "<ay>" bitis: "<ay>"
legal_get_legal_interest_rates # politika faizi; faiz desteği puanı TCMB bir hafta vadeli repo oranına bağlı — politika_faizi satırının baslangic_tarihi ile dönemi kontrol et
```

---

## 5. Çıktı iskeleti

```markdown
## Teşvikli fizibilite — finansal model — [proje] — [tarih]
### Varsayımlar (hepsi kullanıcı verisi; eksikler [___])
### Yatırım tutarı
| Kalem | Tutar | Döviz | Yıl |
### Nakit akışı (teşviksiz / teşvikli)
| Yıl | Gelir | Gider | Vergi | Yatırım | Teşvik etkisi | Net akış |
### Göstergeler
| Gösterge | Teşviksiz | Teşvikli |
| NPV (r = …) | | |
| IRR | | |
| Geri ödeme | | |
### Hassasiyet (kullanıcının seçtiği değişkenler)
### Teşvik varsayımlarının dayanağı (Karar m. — [doğrula])
### Uyarılar: vergi indirimi dönem sınırı, ödeme gecikmeleri, iptal senaryosu
```

---

## 6. Sık hatalar

- 🔴 Modelin ürettiği gelir/gider tahminini kullanıcı verisi gibi sunmak.
- 🟠 Vergi indirimini kazanç profilinden bağımsız, dönemsiz ve devredilebilir saymak (7555 sonrası belgede yanlış).
- 🟠 Faiz desteği ile makine desteğini birlikte modele koymak.
- 🟠 Destek ödemelerini harcama yılında saymak (Hamle'de izleyen yıl).
- 🟡 Sabit yatırım tutarını vergi indirimine esas tutarla karıştırmak.
- 🟡 Nominal akışı reel oranla iskontolamak.

---
