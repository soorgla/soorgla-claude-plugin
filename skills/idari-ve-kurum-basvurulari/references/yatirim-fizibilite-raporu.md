# Yatırım fizibilite raporu

Yatırım teşvik belgesi başvurusu ya da banka kredisi için yatırımın teknik, mali ve ekonomik yapılabilirliğini anlatan rapor. Hukuki bir dilekçe değildir; bu beceride yer alması eski görev grubundan gelir. Hukuki kısmı yalnızca **teşvik mevzuatına uygunluk** bölümüdür.

**Sınır:** finansal projeksiyon (gelir-gider, iç verim oranı, geri dönüş süresi) **üretme**. Kullanıcının verdiği rakamları tabloya dök, iç tutarlılığını kontrol et (toplamlar, yıllar), eksikleri işaretle. Rakam yoksa tabloyu `[___]` ile bırak. Teşvik oranlarını, bölge numaralarını, asgari yatırım tutarlarını **ezberden yazma**.

---

## Süre ve dayanak

Süreye bağlı bir başvuru değildir; ancak teşvik belgesinin kapsamı **belge tarihinden önce yapılan harcamaları** genellikle kapsamaz `[doğrula]`. Kullanıcıya yatırım harcamasına başlamadan başvuruyu sor.

Dayanak: yürürlükteki **Yatırımlarda Devlet Yardımları Hakkında Karar** (Cumhurbaşkanı kararı) ve uygulama tebliği. Karar sık değişir ve yeni karar sistemi gelebilir; adını, tarihini ve sayısını her seferinde Resmî Gazete'den çek. Güncel sistem: 9903 sayılı Yatırımlarda Devlet Yardımları Hakkında Karar (RG 30.05.2025) ve Uygulama Tebliği No 2025/1 (RG 21.06.2025); ayrıntı → `../../tesvik-yatirim/references/tesvik-sistemi-ve-uygunluk.md`.

## Zorunlu unsurlar (eski şablondan)

1. Yatırımın künyesi: yatırımcı, yer (il/ilçe/OSB), cinsi (komple yeni, tevsi, modernizasyon, entegrasyon vb.), sektör (NACE kodu), kapasite.
2. Yatırım tutarı: arazi-bina, yerli makine, ithal makine (döviz cinsiyle), diğer; toplam sabit yatırım; işletme sermayesi ayrı.
3. Finansman yapısı: özkaynak / kredi.
4. Pazar analizi, teknik analiz (teknoloji, makine parkı, yer seçimi, istihdam).
5. Finansal analiz: yatırım maliyeti tablosu, 5 yıllık gelir-gider, kârlılık göstergeleri — **kullanıcı verisiyle**.
6. Teşvik ve destekler: yatırımın konusu ve yerine göre yararlanılabilecek destek unsurları — **mevzuattan çekilerek**, her biri `[doğrula — Sanayi ve Teknoloji Bakanlığı / yatırım danışmanıyla]`.
7. SWOT.

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `project_name` | Projenin adı? |
| `investor_info` | Yatırımcı firma: unvan, VKN, faaliyet konusu, mevcut kapasite? |
| `investment_location` | Yatırım yeri: il, ilçe, OSB/serbest bölge mi? |
| `investment_type` | Komple yeni mi, tevsi mi, modernizasyon mu …? |
| (yeni) | Sektör / NACE kodu ve üretilecek ürün/hizmet? Kapasite? |
| `investment_amount.*` | Arazi-bina, yerli makine, ithal makine (döviz), diğer giderler, toplam? Makine listesi var mı? |
| `financing_structure.*` | Özkaynak ve kredi tutarı? |
| `market_analysis` | Pazar, hedef müşteri, rakipler hakkında elinizdeki veri? |
| `financial_projections` | 5 yıllık gelir-gider tahmini var mı? (yoksa tablo boş kalır) |
| `incentives_applied` | Hangi desteklere başvurulacak? Rapor kime sunulacak: Bakanlık mı, banka mı? |
| (yeni) | Yatırım harcamasına başlandı mı? |

## soorgla çağrıları

```
legal_search_official_gazette query: "Yatırımlarda Devlet Yardımları Hakkında Karar" search_in: "title" sort_by: "date_desc"
legal_search_official_gazette query: "Yatırımlarda Devlet Yardımları Hakkında Kararın Uygulanmasına İlişkin Tebliğ" search_in: "title" sort_by: "date_desc"
legal_search_statute_semantic sorgu: "<sektör> yatırımı teşvik bölgesi destek unsurları" mevzuat_tur: "cb_kararnamesi"
legal_get_exchange_rate # ithal makine tutarını TL'ye çevirmek gerekiyorsa
```
Kapsam zayıf dönerse ORTAK-KURALLAR.md §5; teşvik oranını ve bölgeyi "model bilgisi" ile yazma, `[doğrula]` bırak.

## Rapor iskeleti

```markdown
YATIRIM FİZİBİLİTE RAPORU — [Proje adı]
[Yatırımcı] · [Tarih] · TASLAK

1. YÖNETİCİ ÖZETİ
İşbu rapor, [yatırımcı] tarafından [yer]'de gerçekleştirilmesi planlanan [proje] projesinin teknik, ekonomik ve
mali yapılabilirliğini ortaya koymak amacıyla hazırlanmıştır. [3-5 cümle: ne, nerede, ne kadar, ne zaman, istihdam]

2. PROJE KÜNYESİ
| Yatırımcı | Yatırım yeri | Yatırım cinsi | Sektör (NACE) | Kapasite | İstihdam |

3. YATIRIM TUTARI VE FİNANSMAN
| Kalem | Tutar (TL) | Döviz |
| Arazi-bina inşaat | | |
| Makine-teçhizat (yerli) | | |
| Makine-teçhizat (ithal) | | |
| Diğer | | |
| **Toplam sabit yatırım** | | |
| İşletme sermayesi | | |
Finansman: özkaynak [___] / kredi [___]

4. PAZAR ANALİZİ
5. TEKNİK ANALİZ (teknoloji, makine parkı, yer seçimi, istihdam)
6. FİNANSAL ANALİZ (5 yıllık projeksiyon — kullanıcı verisi; kârlılık göstergeleri yalnız veri varsa)
7. YARARLANILACAK TEŞVİK VE DESTEKLER (her biri mevzuat atfıyla, [doğrula])
8. SWOT ANALİZİ
| Güçlü yönler | Zayıf yönler |
| Fırsatlar | Tehditler |
9. SONUÇ
```

## Sık hatalar

- 🟠 Teşvik bölgesi ve destek oranını eski karar sistemine göre yazmak.
- 🟠 Modelin ürettiği finansal tahmini kullanıcı verisi gibi sunmak.
- 🟡 Sabit yatırım ile işletme sermayesini karıştırmak; ithal makineyi döviz cinsi belirtmeden yazmak.

---
