# Teknik ve mali değerlendirme, yerli istekli avantajı, toplam puan

Kısa listedeki isteklilerin teklifleri iki aşamada değerlendirilir: önce teknik teklif (puan + asgari eşik), sonra yalnız eşiği geçenlerin mali teklifi; puanlar ağırlık katsayılarıyla birleşir, en yüksek toplam puanlı istekliyle görüşülür. Kontrol listesi örnek idari şartnamenin (İKN 2026/1765031) m.29-36 yapısını izler.

- **İdare:** "Kriterler somut ve anlaşılabilir mi, üye puanları gerekçeli mi, hesap doğru mu?"
- **İstekli:** "Puanım neden kırıldı, hesap doğru mu, rakip eşiği gerçekten geçti mi?"

---

## 1. Teklifin yapısı ve ilk oturum (İ.Ş. m.21, 29)

- [ ] Mali teklif = teklif mektubu + geçici teminat (ayrı zarf, "Mali Tekliftir"); teknik teklif = diğer bütün belgeler (ayrı zarf); ikisi bir dış zarfta. 
- [ ] İhale saatinde yalnız **teknik zarflar** açılır, belgeler tutanakla tespit edilir; mali zarflar açılmadan paketlenip mühürlenir; bu aşamada ret/kabul yok, belge düzeltilemez ve tamamlanamaz. 
- [ ] Belge eksik ya da şartlara aykırı → değerlendirme dışı; belge eksikliği tamamlatılamaz; **bilgi eksikliği** en az 2 iş günü süreyle tamamlatılır, tamamlamayanın teklifi dışarıda ve **geçici teminatı gelir kaydedilir**. 

## 2. Teknik değerlendirme kriterleri (İ.Ş. m.31)

- [ ] Kriterler kanunda sayılı: benzer nitelik ve ölçekteki sözleşmeleri yerine getirme deneyimi, önerilen yöntem, organizasyon yapısı, yönetici kadrosu ve teknik personelin eğitim ve mesleki nitelikleri. 
- [ ] Tam puanlar Yönetmelik eki **Tablo 1**'deki aralıklarda belirlenir; hangi kritere/alt kritere **nasıl** puan verileceği dokümanda **somut ve anlaşılabilir** yazılır.  Tablo 1 (araçta m.75 tablosu): A benzer nitelik ve ölçekteki işlerde deneyim **10-20**; B iş için önerilen yöntem, çalışma planı ve organizasyon yapısının iş tanımına uygunluğu **30-50** (örnekteki A 20, B 40 aralıkta ✅).  C (yönetici kadrosu ve teknik personel) satırının aralığı araç alıntısında görünmedi `[doğrula — Tablo 1 C satırı]`.
- [ ] Örnek dağılım: A benzer iş deneyimi 20; B yöntem/iş programı/organizasyon/kalite kontrol 40 (10+10+10+10); C yönetici kadrosu ve teknik personel 40 (genel nitelik 10, iş için uygunluk 15, yerel deneyim ve Türkçe 5, istihdam durumu 10). C kalemleri dört teknik personelin ayrı puanlarının **aritmetik ortalaması**; istihdam durumunda "tamamı bünyede 10, tamamı taahhüt 0, ara değer doğrusal" (İ.Ş. 31.1 tablo).
- [ ] **Yumuşak kalemler (B grubu)**: "işin nasıl yapılacağı", "organizasyon yapısının iş tanımına uygunluğu" gibi alt kriterlerde puan kırma ölçütü dokümanda yazılı mı? Yazılı değilse idare için 🟠 (doküman öz denetimi), istekli için doküman aşamasında itiraz konusuydu; sonuç aşamasında "puan dokümanda olmayan ölçüte göre kırıldı" iddiasına döner `[incele]`.
- [ ] **Asgari teknik puan** idari şartnamede (örnekte 70); altında kalan elenir, mali zarfı açılmadan iade edilir.  m.64/1-a asgari puanı idari şartnameye bırakır; madde metninde alt/üst sınır yok.  Tip idari şartname dipnotunda sınır olup olmadığı araçta yok `[doğrula — tip idari şartname dipnotu]`.

## 3. Teknik puanlama usulü (Yön. m.64)

- [ ] Her üye her istekliyi **gerekçeli** ve ayrı ayrı puanlar → Teknik Teklif Üye Değerlendirme Formu (imzalı) → Komisyon Değerlendirme Formu → üye puanlarının ortalaması = isteklinin ham teknik puanı (PT). 
- [ ] Eşiği geçemeyenlere ve geçenlere bildirim aynı tarihte; yeterli bulunmayanlara bildirim formunun ekinde üye ve komisyon formları gönderilir.  **Bu bildirim istekli için bir şikâyet anıdır** (10 gün) `[incele]`.
- [ ] Mali teklif açılış oturumunda önce teknik puanlar açıklanır, elenenlerin mali zarfları iade edilir, sonra **yaklaşık maliyet açıklanır**, mali zarflar açılır. 
- [ ] Mali zarfta teklif mektubu ya da geçici teminat yok/uygunsuz → dışarıda; birim fiyat teklif cetvelinde **aritmetik hata** → dışarıda.  Geçici teminat teklif bedelinin en az %3'ü (İ.Ş. 25.1).
- [ ] Teknik ya da mali değerlendirme sonunda 3'ten az istekli kalırsa ihale yapılmaz. 

## 4. Formüller (elle hesap yolu — `danismanlik_puan` / `yerli_mali` yanıt vermezse ya da hata dönerse)

| Adım | Formül | Dayanak |
|---|---|---|
| İtibari teknik puan | **PTİ = 100 × PT / PTmax** (PTmax: eşiği geçenler arasında en yüksek ham puan) | 12911 m.64/1-b |
| Mali puan | **PM = 100 × Mmin / M** (Mmin: geçerli mali teklifler arasında en düşük fiyat) | 12911 m.65/6 |
| Yerli avantajı | yabancı isteklinin bedeline, dokümanda yazılı oran (en fazla %15) eklenir: **M' = M × (1 + oran)**; PM bu tutarla hesaplanır. Ortakları arasında yabancı bulunan ortak girişim yararlanamaz | 4734 m.63/b, f; 12911 m.5, m.65/8-9 |
| Ağırlıklar | **P = PTİ × KT + PM × KM**, KT > KM, KT + KM = 1 | 4734 m.52/3; 12911 m.66/1; İ.Ş. 34.1 |
| KT'nin belirlenmesi | 7 parametre × 0-5 puan (toplam 0-35): **>29 → %78-80; 23-29 → %74-77; 0-22 → %70-73** | 12911 m.62/2-3 |

**Yorum noktaları `[incele]`:**
- m.64'teki "asgari puanın üzerindeki ham teknik puan" ifadesi uygulamada eşiği geçen isteklinin **ham puanı** olarak okunur (eşiği aşan fark değil); örnek şartname de "ortalama teknik puan" diyor (İ.Ş. 32.1).
- Yerli avantajında Mmin, avantaj eklenmiş tutarlar arasından seçilir; avantaj yalnız puanlamaya yöneliktir, sözleşme bedeli isteklinin kendi teklifidir.
- Örnekte KT 0,80 / KM 0,20 (İ.Ş. 29.2.9): KT %80 ancak m.62 puanı 29'un üstündeyse mümkün → idare işlem dosyasında 7 parametrenin puanlamasını göstermeli; istekli bunu doküman aşamasında sorgulayabilirdi.

**Örnek hesap (varsayımsal, birimsiz tutarlar; KT 0,8, KM 0,2, yerli avantajı %15):**

| İstekli | PT | PTİ | Teklif M | Avantajlı M' | PM | P |
|---|---|---|---|---|---|---|
| A (yerli) | 85 | 94,44 | 100 | 100 | 95,00 | 94,56 |
| B (yerli) | 78 | 86,67 | 95 | 95 | 100,00 | 89,33 |
| C (yabancı) | 90 | 100,00 | 85 | 97,75 | 97,19 | 99,44 |

Mmin = 95 (avantaj eklendikten sonra). Avantajsız hesapta Mmin 85 olurdu ve A'nın P'si 92,56'ya düşerdi. Hesabı her zaman bu tablo biçiminde göster; ara değerleri iki ondalıkla yuvarla, yuvarlama farkı sıralamayı değiştiriyorsa `[incele]`.

## 5. Sonuçlandırma (İ.Ş. m.34-36)

- [ ] En yüksek toplam puanlı istekli **görüşmeye** davet edilir: iş tanımı, sözleşme şartları, personel, mali teklif. Görüşme dokümandaki şartları önemli ölçüde değiştiremez; personel ücretleri ve teklif edilen harcamalar pazarlık konusu edilemez; mali görüşme yalnız ödeme koşulu/planının, tutar değişmeden idare lehine düzenlenmesine yönelik olabilir. 
- [ ] Önerilen anahtar teknik ve teknik personel zorunlu olmadıkça değiştirilemez; değişirse yeni personel **dengi veya daha nitelikli** olmalı. 
- [ ] Anlaşma sağlanamazsa da dokümandaki koşullarla en yüksek puanlı istekliye ihale yapılır. 
- [ ] **Eşitlik:** toplam puan eşitse mali puanı yüksek olan; o da eşitse Hizmet Alımı İhaleleri Uygulama Yönetmeliği m.63 (1-b, 5 ve 6. fıkralar hariç) uygulanır.  Hizmet Yönetmeliği m.63'ün yürürlükteki metnini `law_no: "12918"` ile çek.
- [ ] **Aşırı düşük teklif:** Danışmanlık Yönetmeliğinde aşırı düşük teklife ilişkin hüküm yok; sınır değer ve sorgulama kriteri belirlenmemiş. Ancak 4734 m.38 genel hükümdür (komisyon "belirlediği süre içinde" açıklama ister) ve 09.04.2026'dan beri ek m.3, hüküm bulunmayan hallerde diğer uygulama yönetmeliklerini niteliğine uygun düştüğü ölçüde uygulatır. Sorgulamanın tamamen dışlandığı söylenemez; sorgulama yapılırsa süreyi komisyon belirler `[incele]`. 

## 6. İtiraz ve savunma ekseni

| Konu | İstekli iddiası | İdare savunması | Not |
|---|---|---|---|
| Puan gerekçesiz | m.64/1-a üye bazında gerekçe yok | üye formları ve gerekçeler | 🟠 usul aykırılığı güçlü |
| Puan dokümanda olmayan ölçüte göre kırıldı | m.63/2 "somut ve anlaşılabilir" | kırma ölçütü dokümandaki alt kriterin içinde | `[incele]` |
| Rakibe fazla puan | eşit muamele (4734 m.5) | aynı ölçüt herkese | belgeyle karşılaştır |
| Hesap hatası (PTİ, PM, ağırlık, yerli avantajı) | formül | — | 🟢 aritmetik |
| "Doğru puan budur" | — | KİK idarenin yerine geçip puanlama yapmaz | aşağıdaki karar |

KİK 2025/UD.I-1022 (30.04.2025, kontrollük ve danışmanlık): Kurul, teknik puanlamaya yönelik itirazen şikâyeti reddederken Yönetmelik m.63-64'ü aktararak Kurumun ihale komisyonunun yerine geçip ihale işlemlerini baştan yapma yetkisi bulunmadığı sonucuna varmıştır. Tam metin okundu; kararın başlığında MK etkisi satırı görülmedi `[doğrula — MK etkisi]`.  Sonuç: istekli "takdir hatası"ndan çok **usul, ölçüt ve eşit muamele** iddiası kurmalı.

Diğer güncel konu örnekleri (okunmadı): KİK 2025/UD.II-904, 2025/UD.II-1331, 2025/UD.I-1017, 2025/UD.IV-883, 2024/UD.I-1274 (ağırlık katsayısı).

## MCP adımları

```
legal_get_statute_article  law_no: "12911"  law_type: "Yönetmelik"  article_no: "5" | "61" | "62" | "63" | "64" | "65" | "66" | "67"
legal_get_statute_article  law_no: "12918"  law_type: "Yönetmelik"  article_no: "63"      # eşitlik
legal_get_statute_article  law_no: "4734"  law_type: "Kanun"  article_no: "52" | "63"
legal_calculate_tender  hesap: "danismanlik_puan"   # hata dönerse §4 elle
legal_calculate_tender  hesap: "yerli_mali"          # hata dönerse §4 elle
legal_search_cases  mahkeme: "kik"  sorgu: "danışmanlık teknik puan gerekçe üye değerlendirme formu"  tarih_baslangic: "<son 3 yıl>"
```
