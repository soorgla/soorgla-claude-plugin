# Fesih öncesi kontrol (işveren tarafı): risk bayrakları, ibra ve ikale

Bu dosya, karar henüz kesinleşmemişken "bu işçiyi çıkarabilir miyiz?" sorusunu yanıtlar. Davadan sonra savunma kurmak için değil, davayı önlemek için kullanılır. Dava açılmışsa ya da fesih yapılmışsa `fesih-ve-ise-iade.md` dosyasına geç.

Fesihlerin çoğu sorunsuzdur; birkaçı dava olarak geri döner. Bu akış o birkaçını karar kesinleşmeden yakalamak içindir. **Beceri kuralı söylemez, araçtan çeker:** her süre, eşik ve oran o anda `legal_get_statute_article` ile okunur ve atıfla verilir.

Upstream karşılığı: `employment-legal/skills/termination-review` (Adım 2 yüksek risk bayrakları, Adım 4 ayrılık ödemesi ve feragat, Adım 5 belge izi). ABD'ye özgü parçalar (FMLA, OWBPA, WARN) Türk hukukundaki karşılıklarıyla değiştirildi.

---

## Sonuç doğuran işlem kapısı

Bayraklardan biri 🔴 ise çıktının en üstüne şunu yaz ve kullanıcı açıkça onaylamadan fesih bildirimi taslağı üretme:

> 🔴 **Dur.** Aşağıdaki bayrak(lar) fesih yapılmadan önce avukat görüşü gerektiriyor: [bayraklar]. Fesih bildirimi bu yüzden henüz hazırlanmadı. Bayraklar giderildiğinde ya da sorumlu avukat onay verdiğinde devam edelim.

Kullanıcı avukat değilse ORTAK-KURALLAR.md §1'deki "taslaktır" kapısını da uygula.

---

## Adım 1 — Temel olgular

1. İşçinin görevi, işe giriş tarihi, planlanan fesih tarihi.
2. Sözleşme belirsiz süreli mi? İşveren vekili mi?
3. İşyerindeki ve aynı işkolundaki toplam işçi sayısı (iş güvencesi eşiği için; eşiği `legal_get_statute_article 4857/18` ile çek).
4. Fesih nedeni: performans (verim), davranış, işletme gereği, haklı neden (m.25).
5. Aynı dönemde başka işçi çıkarılacak mı, kaç kişi? (toplu işçi çıkarma eşiği → `4857/29`)
6. Bildirim nasıl yapılacak: elden imzalı, KEP, noter? (`4857/109`)
7. Toplu iş sözleşmesi, personel yönetmeliği ya da disiplin yönetmeliği var mı? Fesihten önce izlenmesi gereken bir iç usul öngörüyor mu?

## Adım 2 — Yüksek risk bayrakları (en önemli adım)

Her satırı tek tek kontrol et. Biri bile işaretliyse kapıyı uygula.

| Bayrak | Neden riskli | Kontrol | Çekilecek dayanak |
|---|---|---|---|
| **Yakın tarihli şikâyet ya da başvuru** | Misilleme iddiası; geçerli neden sayılmaz | İşçi son dönemde işverene karşı idari/adli makama başvurdu mu, ALO 170, iş müfettişi, dava? | `4857/18` (üçüncü fıkra c bendi) |
| **Sendikal faaliyet** | Sendikal tazminat ve işe iade; ispat yükü kayar | Üyelik, temsilcilik, örgütlenme dönemi, yetki tespiti süreci? | `4857/18`, `6356/25` |
| **Gebelik, doğum, analık izni** | Ayrımcılık; yasak süreler | Gebelik bildirimi, doğum izni, süt izni, kısmi süreli çalışma talebi? İzin süreleri 2026'da değişti; süreyi her seferinde çek | `4857/74`, `4857/18`, `4857/5` |
| **Rapor ve hastalık** | Bekleme süresinde fesih geçerli neden değil | İşçi raporlu mu, rapor süresi ne zaman başladı? Bekleme süresini ihbar süresine göre hesapla | `4857/25` (I-b), `4857/18` (f bendi) |
| **Korunan özellik + zamanlama** | Ayrımcılık tazminatı | Din, siyasi görüş, engellilik, yaş, medeni hal açıklaması yakın tarihli mi? | `4857/5`, `6701` |
| **İhbar ve etik bildirim** | Misilleme | İşçi işyerinde usulsüzlük, İSG riski, taciz bildirdi mi? | `4857/18`; İSG bildirimi için 6331'deki ilgili madde → `legal_search_statute_semantic` |
| **Zayıf belge izi** | "Neden şimdi?" sorusu | Performans feshinde yazılı uyarı, hedef, değerlendirme, iyileştirme süresi var mı? | `legal_search_cases` 9. HD performans feshi |
| **Karşılaştırma sorunu** | Eşit davranma | Aynı şeyi yapan başka işçi çıkarılmıyor mu? | `4857/5` |
| **İç usul taahhüdü** | Usul aykırılığı | Personel/disiplin yönetmeliği ya da TİS fesihten önce kurul kararı, ihtar sayısı vb. öngörüyor mu? | Sözleşme ve yönetmelik metni |
| **Haklı neden süresi** | Süre kaçarsa haklı fesih düşer, haksız fesih sonuçları doğar | Olay ne zaman öğrenildi? | `4857/26` |
| **Fazla mesai ya da ücret açığı** | Fesihle birlikte alacak davası gelir | Ödenmemiş fazla çalışma, UBGT, izin var mı? | `iscilik-alacaklari.md` |

Tarafı işçi olan kullanıcıda aynı tablo "fesih bu nedenle geçersiz sayılabilir mi?" sorusuyla okunur.

## Adım 3 — Usul

- **Yazılı ve gerekçeli bildirim:** neden açık ve kesin yazılacak mı? (`4857/19` birinci fıkra)
- **Savunma:** neden davranış ya da verimse savunma alınacak mı, makul süre verilecek mi? İşletme gereğinde savunma şartı yoktur. (`4857/19` ikinci fıkra)
- **Bildirim yolu:** fesih sonucu doğuran bildirim her hâlde yazılıdır; KEP için işçinin yazılı kabulü gerekir. İşçi imzadan kaçınırsa tutanak. (`4857/109`)
- **Bildirim süresi ya da peşin ödeme:** kıdeme göre süre (`4857/17`). Süre tablosunu araçtan doldur, sabit yazma.
- **İşletme gereği:** işletme kararı yazılı mı, tutarlı uygulanıyor mu, başka pozisyon önerildi mi, seçim ölçütü objektif mi? `[incele]`
- **Toplu işçi çıkarma:** eşik aşılıyorsa önceden bildirim yükümlülükleri ve bekleme süresi. (`4857/29`)

## Adım 4 — Belge izi

- Yazılı uyarılar, tutanaklar, performans kayıtları, savunma istem yazısı ve savunma metni.
- Belgeler tutarlı bir hikâye anlatıyor mu?
- Fesih nedeniyle çelişen belge var mı (yakın tarihli terfi, prim, olumlu değerlendirme)? 🟠
- "Neden şimdi?" sorusunun yazılı cevabı var mı?

## Adım 5 — Ayrılık ödemesi, ibra, ikale ve arabuluculuk anlaşması

**İbraname** (`6098/420` ikinci-dördüncü fıkralar):
- Yazılı mı?
- İbra tarihinde sözleşmenin sona ermesinden itibaren en az bir ay geçti mi? Fesih günü imzalatılan ibraname kesin hükümsüzdür.
- Alacağın türü ve miktarı açıkça yazılı mı?
- Ödeme noksansız ve banka aracılığıyla mı yapıldı?
- Gerçek tutarı içermeyen ibra yalnız makbuz hükmündedir; yine de banka ödemesi şarttır.

**İkale (karşılıklı anlaşmayla sona erdirme):**
- Teklif kimden geldi? İşveren teklif ettiyse işçiye "makul yarar" sağlanmış mı (kıdem ve ihbara ek ödeme)? Bu ölçüt içtihattan gelir → `legal_search_cases` 9. HD ve HGK, sorgu: "ikale sözleşmesi makul yarar işveren teklifi".
- İkale ile işe iade yolu kapanır; işsizlik ödeneği hakkı etkilenebilir `[incele]`.
- İrade sakatlığı iddiasına açık mı (baskı, süre verilmemesi)?

**Arabuluculuk anlaşması:**
- Anlaşma son tutanağı ilam niteliğindedir; ibranamenin bir ay bekleme şartına takılmayan güvenli yol olarak sık kullanılır `[incele]`.
- İşe iade konusunda anlaşılıyorsa işe başlatma tarihi ile tutarlar tutanakta parasal olarak yazılmalıdır, yoksa anlaşma sağlanamamış sayılır (`4857/21`).
- Arabuluculuk ücreti kuralı (`7036/3` on üçüncü fıkra).

## Adım 6 — Maliyet senaryosu

Bu adımda hesap yapma; `iscilik-alacaklari.md` hesap iskeletine yönlendir. Senaryoları yan yana koy:

| Senaryo | Kalemler | Kaynak |
|---|---|---|
| Geçerli nedenle fesih, dava yok | kıdem + ihbar + izin + varsa alacaklar | `iscilik-alacaklari.md` |
| Fesih geçersiz bulunursa | + işe başlatmama tazminatı aralığı + boşta geçen süre | `4857/21` |
| İkale / arabuluculuk anlaşması | yukarıdakiler + ek ödeme | kullanıcı girdisi |

Her tutar `[doğrula — bordro uzmanı / bilirkişi]`.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4857"  article_no: "5" | "17" | "18" | "19" | "21" | "25" | "26" | "29" | "74" | "109"
legal_get_statute_article  law_no: "6098"  article_no: "420"
legal_get_statute_article  law_no: "7036"  article_no: "3"
legal_get_statute_article  law_no: "6356"  article_no: "25"        # sendikal bayrak varsa
legal_search_cases  mahkeme: "yargitay"  daire: "9. Hukuk Dairesi"
    sorgu: "<ör. işveren teklifiyle yapılan ikale sözleşmesinde makul yarar şartı>"
    tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "bam"  sorgu: "<olay>"                # işe iadede son merci BAM
legal_search_official_gazette  query: "İş Kanunu"  document_type: "kanun"  date_from: <son 2 yıl>  sort_by: "date_desc"
                                                                    # yakın tarihli değişiklik var mı
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

## Fesih öncesi kontrol: [görev/rol] — [tarih]
**Neden:** [performans / davranış / işletme gereği / haklı neden] · **Planlanan tarih:** … · **İş güvencesi:** [var / yok — neden]

### Sonuç
[Devam edilebilir / Önce X düzeltilmeli / DUR — tek cümle neden]

### Yüksek risk bayrakları
| Bayrak | Durum (🔴/🟠/✅) | Not | Dayanak [soorgla] |

### Usul kontrolü
| Adım | Yapıldı mı | Eksik | Dayanak |

### Belge izi
### Ayrılık ödemesi / ibra / ikale / arabuluculuk seçenekleri
### Maliyet senaryoları [doğrula]
### Eksik bilgi

**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** [karar ağacı — ORTAK-KURALLAR.md]
```

---

## Kaynak
- Upstream: `claude-for-legal-upstream/employment-legal/skills/termination-review/SKILL.md` (Apache-2.0), Türk hukukuna uyarlandı.
- Eski YAML karşılığı yok: `lawyer/labor_social_security/termination_reemployment.yaml` ve `consultant/social_security_labor/labor_law_disputes.yaml` yalnız dava sonrasına odaklıydı.
