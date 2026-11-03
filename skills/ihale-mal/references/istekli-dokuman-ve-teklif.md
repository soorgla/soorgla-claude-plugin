# İstekli: doküman incelemesi, rekabeti daraltan şartlar, teklif ve belgeler

İstekli dokümanı EKAP'tan indirdi; iki soru: **"Teklif verirsem elenir miyim, fiyata neyi katmalıyım?"** (uyum) ve
**"Doküman hukuka aykırı mı, şikâyet edeyim mi?"** (itiraz). İdarenin hazırlık listesi aynı kuralları içerir
(`idare-hazirlik-teknik-sartname.md`); bu dosya isteklinin yapacağı işlere odaklanır.

---

## 0. Önce süre
- Dokümana şikâyet: doküman indirme tarihinden **10 gün** (21/b-c'de 5) ve **her durumda ihale tarihinden 3 iş günü
  öncesine kadar**; erken olan son gündür. **İlana yansıyan hususlarda** (benzer iş, iş deneyimi oranı, yeterlik
  kriterleri, kısmi teklif) süre **ilk ilan tarihinden** işler — ilk ilan tarihini EKAP'tan al ya da kullanıcıya
  **mutlaka sor**; ilan eskiyse süre doküman indirilmeden dolmuş olabilir 🔴. `kik_complaint_before_tender` canlı
  (10 gün); 3 iş günü sınırını araç hesaplamaz, `legal_check_holiday` ile elle say, `[incele]`.

- Açıklama talebi: ihale tarihinden **20 gün** öncesine kadar; idare cevabı en az 10 gün önce herkese (4734 m.29;
  tip idari şartname m.13). Belirsizlikler çoğu zaman açıklama talebiyle çözülür, **ama açıklama talebi şikâyet
  süresini durdurmaz ve uzatmaz**; idarenin cevabı şikâyet süresi dolduktan sonra gelebilir. Aykırılık şüphesi varsa
  şikâyeti süresinde ver, açıklama talebini paralel yap; iki son günü birlikte göster (§5 çıktı iskeleti).

- Zeyilname ihaleden en az 10 gün önce; ihale bir defa en fazla 20 gün ertelenebilir; zeyilnameden önce verilen teklif
  geri çekilip yeniden verilebilir (Mal Yön. m.24/1-2).
- Süre 7 günden azsa 🔴; şikâyet kararı verilirse `../../ihale-sikayet/SKILL.md`'ye iddia listesiyle devret.

## 1. Rekabeti daraltan şartlar (itiraz modu)

| # | Kontrol | Dayanak | Önem |
|---|---|---|---|
| 1 | Marka/model/menşei belirtilmiş, "veya dengi" yok; ya da tek ürün kataloğundan kopya ölçüler | Mal Yön. m.14/3; 4734 m.12 | 🔴 |
| 2 | "Tanınmış/tescilli markalardan", "1. kalite" gibi ölçütsüz şart | m.14/1, 14/8 | 🟠 `[incele]` |
| 3 | Yerli malı teklifini engelleyen düzenleme | m.14/1 son cümle | 🟠 |
| 4 | İhaleden önce numune teslimi ya da numune ön elemesi | m.43/2-a | 🔴 |
| 5 | Mevzuatın izin vermediği yeterlik belgesi (taahhütname, personel belgesi, bünyede laboratuvar, özel imalat dışında ISO) | m.27/1-ğ, g, ı; m.42/1 | 🔴 |
| 6 | İş deneyimi oranı %10-40 dışında; ya da YM 13/b(2) üst limitin altında olduğu halde iş deneyimi isteniyor | m.37/3; m.27/1-b | 🔴 |
| 7 | Eşik altı ihalede bilanço / ciro isteniyor | m.27/1-c | 🔴 |
| 8 | Benzer iş tanımı dar (yalnız kamuya satış, yalnız belli marka) | m.3/1-b; 4734 m.5 | 🟠 |
| 9 | Yetkili satıcılık şartında imalatçı/serbest bölge seçenekleri eksik | m.38/1 | 🟠 |
| 10 | Kısmi teklif yok ama kalemler birbirinden bağımsız ve tek tedarikçiyi kayırıyor | 4734 m.5; m.61/4 | `[incele]` (idarenin takdiri) |
| 11 | Zorunlu yerli malı avantajı (listedeki ürün) uygulanmamış | 4734 m.63/c; m.61/6 | 🟠 |

- **Benzer iş emsalinin uygulanabilirliği.** "Benzer iş dar tanımlandı" gerekçeli KİK iptal kararları yalnız tanım
  **ihale konusu alımdan dar** olduğunda (ihale konusunun ana kalemlerinden yalnız birini kapsıyor, yalnız kamuya
  satışı ya da belli markayı sayıyor) emsal olur. Tanım ihale konusuyla **aynı ya da daha genişse** (ör. "her türlü gıda
  satışı") bu emsaller uygulanmaz; asıl soru belgenin tanıma girip girmediği ve tevsik şartıdır. Emsal göstermeden önce
  emsaldeki tanım–ihale konusu ilişkisini kendi dosyanınkiyle yan yana yaz `[incele]`
  (`../../ihale-sikayet/references/kik-emsal-arama.md` §emsal uygulanabilirlik).

Somut kanıt olmadan "adrese teslim" iddiası yazma; katalog karşılaştırması, rakip ürün listesi iste. Emsal için
`legal_search_cases` `mahkeme: "kik"` (UM kodlu kararlar), MK etkisini kontrol et, kararın **gerekçesi** mi yoksa
usulden ret mi olduğunu oku.

## 2. Teklif öz kontrolü (uyum modu) — idari şartname madde sırasıyla

| İdari Ş. | Kontrol | Not |
|---|---|---|
| 7.1(a)-(b) | teklif mektubu, imza yetkisi (ortaklar/yöneticiler), vekâlet | EKAP'ta e-imza |
| 7.1(c), 26 | geçici teminat ≥ teklif bedelinin %3'ü; mektup süresi şartnamedeki tarihten önce değil | 4734 m.33 |
| 7.1(d), 16 | iş ortaklığı beyannamesi; pilot ortak en çok hisseli | Mal Yön. m.30 |
| 7.1(f), 33.3 | yerli malı belgesi — **avantaj ancak 33.3'te oran yazılıysa** | m.61/3 |
| 7.3.1 | iş deneyimi: tek sözleşme, son 5 yıl kesin kabul, oran, benzer iş | §3 |
| 7.3.1.2 | belge %50+ hisseli ortağa aitse ortaklık tespit belgesi (ilk ilandan sonra düzenlenmiş, son 1 yıl kesintisiz) | m.37/7 |
| 7.3.2 | sicil, izin, ruhsat (gıdada işletme kayıt/onay) — kimin adına? | m.27/1-f |
| 7.7 | EKAP'ta teyit edilemeyen belgede asıl ya da noter onaylı suret; fatura örneği asıl sayılır | tip şartname |
| 10 | 4734 m.10/4 dışlama halleri; kesinleşmiş vergi/SGK borcu sınırı → `usul_kontrol` (`vergi_sgk_borcu_siniri`, ilan tarihine göre) | 15.11.2026 sonrası ilanlarda sınır değişti `[doğrula]` |
| 19-21 | birim fiyat; kısmi ve alternatif teklif var mı | aritmetik hatada teklif elenir (m.55/7) |
| 24 | teklif geçerlilik süresi | uzatma talebi reddedilebilir, teminat iade |
| 25 | fiyata dahil giderler: vergi (KDV hariç), sözleşme damga vergisi, karar pulu, nakliye, ambalaj, **analiz/test giderleri**, teminat masrafı, KİK payı | teknik şartnamedeki her yükümlülüğü fiyatlandır |

## 3. İş deneyimi ve güncelleme (Mal Yön. m.37, 46-48)
- [ ] **Tek sözleşme**; birden çok belge toplanamaz (m.47/2). Tutar fiyat farkı ve KDV hariç (m.47/3); benzer iş dışı
  kısımlar düşülür (m.47/4).
- [ ] **Özel sektöre satış:** sözleşme + VUK'a göre fatura örnekleri (ya da noter/YMM/SMMM/vergi dairesi onaylı suret) +
  sözleşme damga vergisinin **ilk ilan tarihi itibarıyla ödendiğini** (ya da istisna/muafiyeti) gösteren belge
  (m.46/1-a, 9/4/2026 değişikliği). İş bitirme belgesi düzenlenmiş olsa bile dikkate alınmaz. 🔴 damga vergisi en sık eleme sebebi.
- [ ] Sözleşmede kabul tarihi yoksa **en son fatura tarihi** kabul tarihidir (m.46/1-c).
- [ ] Toplam tutarı olmayan birim fiyatlı sözleşmede süre içindeki faturaların toplamı (m.46/1-e; m.47/6).
- [ ] Gerçek kişilere satışta %10 iş artışı sınırı (m.46/1-ç).
- [ ] Kamu işi: iş bitirme belgesi / teknolojik ürün deneyim belgesi (teklif edilen mal belgedeki mal olmalı, m.47/12).
- [ ] **Güncelleme** (m.48): 4734 kapsamındaki işte belgeye konu işin **ihale tarihinden önceki ay** endeksi; diğer
  işlerde **sözleşme tarihinden önceki ay** endeksi → ilk ilan ayından önceki ay endeksi. Yabancı parada önce o tarihteki
  TCMB alış kuru (m.48/2). → `tutar_guncelle` (`belge: is_deneyim_4734` / `is_deneyim_diger`); araç yoksa Yİ-ÜFE
  oranıyla elle, `[incele]`.
- [ ] Ciro: toplam ciro gelirin elde edildiği yılın **Haziran** endeksiyle; mal satış cirosu **fatura ayından önceki ay**
  endeksiyle (m.35) → `tutar_guncelle` (`belge: toplam_ciro` / `fatura`).
- [ ] Bilanço / iş hacmi istenmişse `bilanco_kontrol`, `is_hacmi_kontrol`; araç yoksa m.33/3 ve m.34/6'dan elle.
- [ ] Kamu görevlisine ait belge görevi sürerken kullanılamaz (m.47/11); unvan/tür değişikliğinde değişiklik belgesi (m.47/10).

**Örnek (İKN 2026/1824919):** %20 oran, benzer iş "her türlü gıda satışı". Özel sektöre gıda satışında belge seti
sözleşme + faturalar + damga vergisi belgesi; sözleşme yoksa yalnız faturalarla iş deneyimi **tevsik edilemez**
`[incele]`. Eşitlikte belge tutarı belirleyici (idari Ş. 33.2.1) — en yüksek tutarlı belgeyi kullan.

## 4. Yerli malı belgesi
- [ ] Avantaj ilanda ve idari şartnamede oranıyla yazılı mı? (m.61/3) Yazılı değilse belge sunmak sıralamayı değiştirmez.
- [ ] Belge, Bakanlığın usul ve esaslarına göre düzenlenmiş, teklif edilen mala ait ve geçerli mi? (m.61/7; Yerli Malı
  Tebliği SGM-2024/10, son değişiklik SGM-2026/3 RG 07.02.2026 — güncel metni RG'den çek). Başvuru ve sorgulama:
  Sanayi ve Teknoloji Bakanlığı yerli malı sayfası / sanayi sicil sistemi `[web araması — doğrulayın]`.
- [ ] Çok kalemli ihalede avantaj kalem bazında: yerli malı teklif etmeyenin o kalemdeki bedeline kendi bedeli × oran
  eklenir (m.61/4); sıralamayı `yerli_mali` hesabıyla ya da elle kontrol et.

## 5. Çıktı iskeleti
```markdown
### Doküman incelemesi — İKN [___] — [uyum / itiraz]
**Dokümana şikâyet son günü:** [tarih] ([başlangıç: ilk ilan / indirme] + 10 gün; ihaleden 3 iş günü önce sınırı: [tarih]; erken olan) · **Açıklama talebi son günü:** [tarih] (ihaleden 20 gün önce; şikâyet süresini durdurmaz)
| # | Belge / madde | Tespit (birebir alıntı) | Dayanak | Önem | Öneri (açıklama talebi / şikâyet iddiası / fiyata yansıt) |
### Teklif öz kontrol tablosu (idari şartname madde sırasıyla)
### Fiyata yansıtılacak maliyetler
### Şikâyet edilebilecek iddialar — numaralı (ihale-sikayet'e aynen devredilir)
```

## Sık hatalar
- 🔴 Doküman şikâyetini ihale sonrasına bırakmak (3 iş günü sınırı).
- 🔴 Açıklama talebinin cevabını bekleyip şikâyet süresini kaçırmak; ilana yansıyan hususta süreyi indirmeden saymak (ilk ilandan işler).
- 🔴 Özel sektör iş deneyiminde damga vergisi belgesini unutmak; birden fazla faturayı farklı sözleşmelerden toplamak.
- 🟠 Teknik şartnamedeki analiz, numune, 48 saatte değişim gibi yükümlülükleri fiyata katmamak.
- 🟠 Yerli malı avantajı yazılı değilken belgeye güvenmek.
