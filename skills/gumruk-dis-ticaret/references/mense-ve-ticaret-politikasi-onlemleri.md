# Menşe, tercihli tarife ve ticaret politikası önlemleri (İGV, damping, EMY, gözetim, TAREKS)

## Ne zaman kullanılır
- Menşe belgesi (EUR.1, menşe şahadetnamesi) ya da A.TR dolaşım belgesi sonradan kontrolde geçersiz çıktı; ek tahakkuk geldi.
- "Çin malı Malezya üzerinden geldi" — önlemlerin etkisiz kılınması (saptırma) riski.
- İlave gümrük vergisi, dampinge karşı vergi, ek mali yükümlülük, gözetim, kota.
- Yerli üretici olarak dampinge karşı şikâyet; ihracatçı/ithalatçı olarak soruşturmaya katılım; önlem tebliğine karşı dava.
- İthali yasak ya da izne tabi eşya, ürün güvenliği denetimi (TAREKS).

---

## Hukuki çerçeve

| Konu | Kural | Dayanak |
|---|---|---|
| Tam elde edilme | Tümüyle bir ülkede elde edilen veya üretilen eşya o ülke menşelidir; sayılan ürün grupları | 4458 m.18  |
| Tercihli menşe | Serbest ticaret ve tercihli ticaret anlaşmalarına göre ayrı yönetmeliklerle belirlenir (ör. Türkiye-Maldivler Tercihli Ticaret Anlaşması menşe yönetmeliği, RG 24.08.2026) | 4458 m.17-22; ilgili yönetmelik  |
| BMB | Bağlayıcı menşe bilgisi 3 yıl geçerli, yalnız hak sahibine karşı | m.9/4  |
| İyi niyet koruması | Tercihli tarife karşı ülkeyle idari işbirliğine dayanıyorsa, dolaşım belgesinin karşı ülke idaresince yanlışlıkla onaylandığı tespit edildiğinde, yükümlü tüm özeni gösterdiğini ispat ederse tahakkuk ettirilmeyen vergiler sonradan istenmez; belge ihracatçının yanlış verilerine dayanıyorsa ya da RG'de şüphe duyurusu varsa korunma yok (karşı ülke idaresinin bildiği/bilmesi gerektiği hâl hariç) | m.198/4  |
| Korumanın sınırı | m.198/4 yalnız **tercihli tarife nedeniyle** tahakkuk ettirilmeyen vergileri korur; dampinge karşı vergi ve ek mali yükümlülük bu nitelikte değildir | Danıştay 7. D. E.2022/466 K.2024/1975  |
| Damping vergisinin tahsili | 4458'in tahsil, takip ve teminata ilişkin usul hükümleri dampinge karşı vergiye de uygulanır; 3577'ye aykırı Gümrük Kanunu hükümleri uygulanmaz | 3577 m.15/1, m.16/2 (Danıştay 7. D. K.2024/1975'te aktarıldığı şekliyle)  |
| Ek mali yükümlülük | 2976 sayılı Kanun: ithalat/ihracat üzerine vergi dışı ek mali yükümlülükler Cumhurbaşkanı (eski BKK) kararıyla | 2976 m.1-3 (aynı kararda aktarıldığı şekliyle)  |
| Yasak eşya cezası | Genel düzenleyici işlemle ithali yasak eşya → fark vergiler + gümrüklenmiş değerin dört katı idari para cezası; lisans, izin, uygunluk belgesine tabi eşyada ayrı ceza | 4458 m.235/1-a, c (7190)  Tutarlar ve katlar `[doğrula]`. |

---

## Antidamping: soruşturma ve önlem

- **Önlemler RG'de tebliğle yayımlanır** ("İthalatta Haksız Rekabetin Önlenmesine İlişkin Tebliğ (No: 2026/xx)"); yalnız 2025 ortasından bu yana 70 tebliğ var, en yenisi 2026/31 (RG 14.10.2026).  Ürün ve menşe ülke için güncel tebliği her seferinde ara; önlem oranını metne yazma.
- **Soruşturma aşamaları** (başvuru, açılış, soru formu, yerinde doğrulama, nihai bildirim, kesin önlem, nihai gözden geçirme, önlemlerin etkisiz kılınması soruşturması) İthalatta Haksız Rekabetin Önlenmesi Hakkında Karar ve Yönetmelik'te. Yönetmelik soorgla'da `law_no: "4125"` (statute_id 43960, RG 30.10.1999/23861); şikâyet ve içeriği m.19 (üretim dalı adına başvuru, delil şartı, eksik şikâyetin bildirilmesi). Temsil oranı ve cevap sürelerini `legal_list_statute_articles` (statute_id 43960) ile m.20 vd.'den oku; okuyamazsan `[doğrula]`. 
- **Önlem tebliğine karşı dava:** düzenleyici işlem; Danıştay 7. D. 2020-2023'te ilk derece olarak inceledi (ör. E.2019/124 K.2023/2763; K.2021/2425-2426'da ABD menşeli önlem).  Süre İYUK m.7/4 (ilandan) → `gumruk-davasi.md`.
- **Saptırma (önlemlerin etkisiz kılınması):** üçüncü ülke üzerinden sevk, hafif işçilik, montaj → önlemin genişletilmesi ve menşe belgesinin sonradan kontrolü; yurt dışı doğrulama sonucu belge geçersizse damping vergisi ve EMY m.198/4 korumasına girmez. 🔴 risk.

---

## Kontrol listesi — menşe belgesi reddi

1. Belge türü: tercihli menşe (EUR.1, EUR-MED, menşe beyanı) mı, A.TR dolaşım belgesi mi, tercihsiz menşe şahadetnamesi mi? `[incele]`
2. Ret sebebi: belgenin karşı ülke makamlarınca düzenlenmediği mi, yanlış onay mı, ihracatçının yanlış beyanı mı?
3. Yurt dışı doğrulama yazısı dosyada mı; idare "yeterli ve açık" tespit yapmış mı (ilk derece mahkemesi K.2024/1975 olayında bunu aradı)?
4. m.198/4: karşı ülke idaresinin yanlış onayı + yükümlünün tüm özeni → hangi kalemler korunur (yalnız tercihli tarifeden doğan vergi), hangileri korunmaz (damping, EMY)?
5. RG'de o ülkeye ilişkin şüphe duyurusu var mı?
6. Ceza: m.234 (tarife unsurlarında aykırılık) mı, başka madde mi?
7. Eşya önleme tabi mi; saptırma soruşturması var mı?

## Kontrol listesi — ithalat öncesi uyum (eski YAML "güvenli ticaret filtresi")

1. GTİP ve menşe kesin mi (BTB/BMB önerisi)?
2. İGV, damping, EMY, gözetim, kota var mı — güncel RG?
3. Menşe ispat belgesi usulüne uygun mu?
4. Eşya ithali yasak ya da ön izne/uygunluk belgesine tabi mi (ürün güvenliği tebliğleri, TAREKS kaydı)? 2026 serisi "Ürün Güvenliği ve Denetimi: 2026/x" numarasıyla yayımlandı ve yıl içinde değiştirildi (ör. Oyuncaklar 2026/10 — RG 31.12.2025 4. mükerrer; Tüketici Ürünleri 2026/12, Anne ve Bebek 2026/17, Makinalar 2026/32, Tarım ve Orman Bakanlığı kontrolündeki ürünler 2026/5; Helal Uygunluk 2026/35 yeni). Ürünün tebliğini ve son değişikliğini `legal_search_official_gazette` (`query: "Ürün Güvenliği ve Denetimi"`, `search_in: "title"`, `sort_by: "date_desc"`) ile ara. 
5. Rota riski (aktarma ülkesi) ve tedarikçi menşe beyanının güvenilirliği.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Eşya hangi ülkede üretildi, hangi ülkeden sevk edildi? | Menşe, saptırma |
| Hangi belgeyle tercih talep ettiniz; onaylayan makam? | m.198/4 |
| Tedarikçiden menşe beyanı ve üretim belgeleri alabilir misiniz? | Özen ispatı |
| Ürününüz hakkında bir damping soruşturmasına katıldınız mı? | Bireysel oran, dava hakkı |
| (Yerli üretici) Toplam üretimdeki payınız? | Şikâyet ehliyeti `[doğrula]` |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4458"  law_type: "Kanun"  article_no: "18" | "198" | "235"
legal_resolve_statute  law_no: "3577"     # statute_id 39945
legal_resolve_statute  law_no: "2976"
legal_search_official_gazette  query: "İthalatta Haksız Rekabetin Önlenmesine İlişkin Tebliğ"  search_in: "title"  sort_by: "date_desc"
legal_search_official_gazette  query: "<ürün> <ülke> dampinge karşı"  date_from: "<son 2 yıl>"
legal_search_official_gazette  query: "Tercihli Menşeinin Tespiti Hakkında Yönetmelik"  search_in: "title"
legal_search_cases  mahkeme: "danistay"  sorgu: "EUR.1 dolaşım belgesi sonradan kontrol tercihli tarife ek tahakkuk"  tarih_baslangic: "2023-01-01"
```

---

## Çıktı iskeleti

```markdown
## Menşe / önlem değerlendirmesi — [eşya, ülke]
| Kalem | Tahakkuk nedeni | m.198/4 koruması | Görüş | Etiket |
### Saptırma riski ve belge zinciri
### Önerilen yol (itiraz/uzlaşma/dava; soruşturmaya katılım)
```

---

## Sık hatalar

- 🔴 m.198/4'ü damping vergisi ve EMY için de koruma sanmak.
- 🟠 Eski önlem tebliğindeki oranı uygulamak; nihai gözden geçirmeyle önlem uzamış ya da kalkmış olabilir.
- 🟠 A.TR'yi menşe belgesi saymak (dolaşım belgesidir) `[incele]`.
- 🟡 Önlem tebliğine karşı dava süresini (ilandan) kaçırmak.

---

## İdare tarafı
- Sonradan kontrolde karşı ülke yazısını ve ihracatçının yanlış beyanına ilişkin tespiti karara ekle; m.198/4 değerlendirmesini kalem bazında yaz.

---

