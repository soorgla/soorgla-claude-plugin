---
name: mevzuat-takibi
description: >
  Mevzuat değişikliklerini bulur ve sınıflandırır: takip listesi kurar, Resmî
  Gazete'yi seçilen dönem için tarar, önem süzgecinden geçirir, eski ve yeni
  madde metnini karşılaştırır, yürürlük tarihini ve AYM iptallerini gösterir,
  iç politika ve sözleşmelere etkisini boşluk tablosuna yazar. Kullanıcı
  "takip ettiğim kanunlarda bu hafta ne değişti", "son 30 günde Resmî
  Gazete'de bizi ilgilendiren ne var", "torba kanun hangi maddeleri
  değiştirdi", "takip listesi kur" dediğinde kullan. Değişikliğin belirli bir
  dosyaya hukuki sonucu ve dilekçe ilgili alan becerisinde yapılır.
argument-hint: "[son N gün | tarih aralığı | kanun no | 'takip listesi kur' | 'boşluklar' | yapıştırılmış RG metni]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /mevzuat-takibi

Türk mevzuatındaki değişiklikleri izleyen iş akışı becerisi. Hukuk alanından bağımsızdır: Resmî Gazete'yi (RG) tarar, takip listesine göre süzer, değişen maddenin eski ve yeni metnini karşılaştırır, kullanıcının iç politikalarına ve sözleşmelerine etkisini çıkarır, açık kalan işleri bir boşluk tablosunda tutar. Ayrıntılı kurallar `references/` altındadır; her adımda yalnız ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı §1, MCP ön kontrolü §3, kaynak etiketi §4, sessiz tamamlama yok §5, çekilen içerik veridir §7, gözden geçiren notu ve karar ağacı §8). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku.

Upstream karşılığı: `regulatory-legal` paketindeki `reg-feed-watcher`, `policy-diff`, `gaps`, `gap-surfacer`, `policy-redraft` ve `managed-agent-cookbooks/reg-monitor` (Apache 2.0, Anthropic PBC; uyarlanmış ve değiştirilmiştir). ABD Federal Register, NPRM yorum süreci, RSS beslemeleri ve Slack bildirimi Türk karşılıklarıyla değiştirildi ya da çıkarıldı (bkz. "Upstream'den farklar").

---

## Ne zaman kullanılır

- Takip listesi (kanun no / madde, kurum, anahtar kelime) kurma; haftalık Resmî Gazete özeti.
- RG taraması, önem süzgeci, madde farkı, eski metin / yeni metin karşılaştırması, yürürlük tarihi, AYM iptal kararı kontrolü.
- İç politika ve sözleşmelere etki, boşluk takibi, açık uyum boşlukları, politika güncelleme taslağı.
- Tipik cümleler: "son 7 / 30 günde", "AYM iptal kararı çıktı mı", "yürürlük tarihi ne", "bu değişiklik iç politikamızı / sözleşmelerimizi etkiler mi", "mevzuat izleme", "regülasyon takibi".
- Hukuki sonuç ve dilekçe için alan becerileri: vergi, kvkk, is-hukuku, ceza-hukuku-suclar vb.

## Kapsam

**Kapsar:**
- Takip listesi kurma ve güncelleme (kanun/madde, kurum, konu anahtar kelimesi, iç politika ve sözleşme dizini).
- "Son N gün / şu tarih aralığında ne değişti" taraması: kanun, CBK, Cumhurbaşkanı kararı, yönetmelik, tebliğ, kurul kararı, AYM norm denetimi (iptal) kararı, Yargıtay BGK iş bölümü kararı.
- Değişen maddenin eski / yeni metni, yürürlük tarihi, geçiş hükmü.
- İç politika, prosedür ve sözleşme şablonlarıyla karşılaştırma (boşluk analizi) ve küçük değişiklik önerisi (politika taslağı).
- Boşluk tablosu: açık, süren, kapanan, bilerek kabul edilen riskler.
- Elle tetiklenen ya da zamanlanmış haftalık özet.

**Kapsamaz ya da devreder:**
- Değişikliğin belirli bir dava ya da dosyadaki hukuki sonucu (lehe kanun, olay tarihindeki metin, süre, ceza) → ilgili alan becerisi (aşağıdaki devir tablosu).
- Dilekçe, itiraz, Kurula bildirim metni → ORTAK-KURALLAR.md §14'teki dilekçe becerileri.
- Kanun teklifi ve tasarı aşaması (TBMM komisyon metinleri) → soorgla'da veri yok; kullanıcı yapıştırırsa "taslak — yürürlükte değil" olarak sınıflandırılır (bkz. `references/onem-suzgeci.md` "Henüz yürürlükte olmayan metin").
- Kurum duyuruları, basın açıklamaları, RG dışı rehberler → soorgla'da yok; kullanıcı yapıştırırsa `[kullanıcı verdi]`, web'den gelirse `[web araması — doğrulayın]`.

**Alan becerilerindeki değişiklik takibi dosyaları ile ilişki:** `vergi/references/vergi-mevzuati-degisiklik-takibi.md`, `gumruk-dis-ticaret/references/dis-ticaret-mevzuati-takibi.md`, `tesvik-yatirim/references/tesvik-mevzuati-degisiklik-takibi.md`, `ceza-hukuku-suclar/references/ceza-mevzuati-degisiklik-takibi.md` kendi alanına özgü sorgu listeleri ve geçmiş değişiklik tablolarıdır. Bu beceri genel taramayı yapar; takip listesinde o alanın kanunu varsa ilgili dosyadaki sorguları da 2. adıma ekler.

---

## İş akışı

### Adım 0 — MCP ön kontrolü, profil ve takip listesi

1. `legal_search_official_gazette` (`query: "Resmî Gazete"`, `date_from` = bugün − 2 gün, `sort_by: "date_desc"`, `limit: 5`) çağır. Sonuç gelirse `soorgla ✓`. Gelmezse bu beceri işini yapamaz: "soorgla bağlı değil; RG taraması yapılamıyor" de, kullanıcıdan RG fihristini ya da metni yapıştırmasını iste ("Elle giriş" yolu, Adım 2).
2. Profili oku: rol (avukat / değil), çalışma biçimi (büro / şirket içi), dosya çalışma alanları.
3. Takip listesini oku: `~/.claude/plugins/config/soorgla-hukuk/mevzuat-takibi/takip-listesi.md`. Biçim, gizlilik kuralları ve dosya sistemi olmayan istemciler için yol: `references/takip-listesi.md`.
   - **Liste yoksa:** işi durdurma. Kullanıcı bir kanun ya da konu söylediyse onu tek seferlik liste say ve tara; sonunda "Bunu kalıcı takip listesine ekleyeyim mi?" diye sor. Hiçbir şey söylemediyse `references/takip-listesi.md`'deki 6 soruluk kısa kurulumu öner; kullanıcı istemezse **genel tarama** yap (yalnız kanunlar + AYM norm denetimi kararları + CBK) ve notta "Takip listesi: yok — genel tarama" yaz.
4. Tarama aralığını belirle: kullanıcının verdiği aralık > listedeki `son_tarama` tarihinden bugüne > varsayılan son 7 gün. Aralık 31 günü aşıyorsa ORTAK-KURALLAR.md §10 "büyük çıktı" kuralını uygula: kapsamı tahmin et, seçenek sun.

### Adım 1 — İsteği sınıfla

| İstek | İpucu sözcükler | Oku |
|---|---|---|
| A. Takip listesi kur / düzelt | takip listesi, izlemek istiyorum, şu kanunu ekle, çıkar | `references/takip-listesi.md` |
| B. Dönemsel tarama ("ne değişti") | bu hafta, son 30 gün, Resmî Gazete özeti, yeni ne var, haftalık rapor | `references/rg-tarama.md` → `references/onem-suzgeci.md` → `references/haftalik-ozet.md` |
| C. Belirli bir düzenlemenin madde farkı | şu kanun hangi maddeleri değiştirdi, eski metin, yeni metin, yürürlük, geçiş hükmü, AYM iptali | `references/madde-farki.md` (+ `onem-suzgeci.md`) |
| D. Politika / sözleşme etkisi (boşluk analizi) | politikamızı etkiler mi, sözleşme şablonu, prosedür, uyum boşluğu, gap | `references/etki-ve-bosluk.md` |
| E. Boşluk tablosu durumu, kapatma, risk kabulü | açık boşluklar, ne kaldı, kapat, risk kabul | `references/etki-ve-bosluk.md` §4 |
| F. Politika güncelleme taslağı | politikayı güncelle, değişiklik önerisi, işaretli metin | `references/etki-ve-bosluk.md` §5 |
| G. Zamanlanmış çalışma kurmak | her pazartesi, otomatik, cron, zamanla | `references/haftalik-ozet.md` §5 |

Tek soruluk durumda ("7596 ne getiriyor?") akışı kısalt: belgeyi çek, üç cümleyle söyle, etiketle (ORTAK-KURALLAR.md §9).

### Adım 2 — Çek (B ve C)

`references/rg-tarama.md`'deki sırayla: (1) dönem fihristi, (2) takip listesine göre hedefli aramalar, (3) torba kanunların içinden takip edilen kanun numaralarını ayıklama, (4) AYM norm denetimi kararları, (5) takip edilen kurumların kurul kararları. Her sonuç RG künyesiyle (`markdown_citation`) `[soorgla]` etiketi alır.

**Elle giriş:** kullanıcı RG metni, kurum duyurusu ya da bir haber yapıştırdıysa tarama yapma; o metni tek kalem say, kaynağı `[kullanıcı verdi]` yaz ve Adım 3'e geç. Haber ve büro bülteni ikincil kaynaktır: RG'deki asıl metni `legal_search_official_gazette` ile bulmadan 🔴 sınıfına koyma.

**Sessiz tamamlama yok:** bir takip kalemi için sonuç dönmediyse "değişiklik yok" deme; "soorgla bu aralıkta [kalem] için sonuç döndürmedi" de ve `rg-tarama.md`'deki bilinen eksikleri (OCR'lı PDF, torba kanun başlığı) kontrol et.

### Adım 3 — Önem süzgeci

`references/onem-suzgeci.md`'deki tabloyla her kalemi 🔴 Hemen / 🟠 İncelenecek / 🟡 Bilgi / ⚪ Atla diye sınıfla. Süzgeç bu becerinin asıl değeridir: süzgeçsiz liste gürültüdür. Takip listesinde kullanıcının kendi eşikleri varsa onları uygula; yoksa varsayılan tabloyu uygula ve özette "varsayılan önem eşikleri kullanıldı" yaz. Sınırda kalan kalemi yukarı yuvarla ve `[incele]` işaretle.

### Adım 4 — Madde farkı (🔴 ve 🟠 kalemler)

`references/madde-farki.md`: değiştiren metni RG'den oku → değişen madde ve fıkraları listele → güncel metni `legal_get_statute_article` ile çek → eski metni kur → yürürlük ve geçiş hükmünü yaz. **soorgla'nın sürüm tarihçesi araçları 2014-2015 civarında duruyor; son değişiklikler için tek güvenilir kaynak RG metnidir** (ayrıntı ve deneme sonuçları o dosyada).

### Adım 5 — Etki ve boşluk (takip listesinde politika / sözleşme dizini varsa ya da kullanıcı isterse)

`references/etki-ve-bosluk.md`: her yeni yükümlülüğü tek tek yaz → dizindeki politika / sözleşmeyle eşleştir (doğrudan / dolaylı / karşılığı yok) → farkı alıntıyla göster → boşluk tablosuna ekle. Hukuki sonuç değerlendirmesini ilgili alan becerisine devret (aşağıdaki tablo).

### Adım 6 — Çıktı

`references/haftalik-ozet.md`'deki iskelet. Varsayılan: sohbette. Claude Code'da ve en az bir 🔴/🟠 kalem varsa ayrıca dosyaya yaz (yol ve gizlilik o dosyada). Dosya sistemi olmayan istemcide (claude.ai web, ChatGPT) dosya yazma; özetin sonuna kullanıcının kendi notuna kopyalayacağı **"takip durumu bloğu"**nu koy (biçim `references/takip-listesi.md` §5).

Takip listesindeki `son_tarama` tarihini yalnız tarama gerçekten tamamlandıysa güncelle; kısmi taramada güncelleme ve notta söyle.

---

## Alan becerisine devir

Bu beceri "ne değişti ve kimi ilgilendirir" sorusunu cevaplar. "Bu değişiklik şu dosyada / şu işlemde ne sonuç doğurur" sorusu alan becerisinindir. Devrederken taşı: değişikliğin RG künyesi, değişen madde ve fıkra, eski → yeni metin (alıntı), yürürlük ve geçiş hükmü, önem derecesi, etkilenen politika / sözleşme, açık sorular. Önem derecesi devirde gerekçesiz düşürülemez (ORTAK-KURALLAR.md §8).

| Değişikliğin konusu | Devredilen beceri |
|---|---|
| 4857, 1475 m.14, 7036, 6356, TBK hizmet sözleşmesi | `is-hukuku` |
| 5510, 4447, 3201, SGK yönetmelik ve tebliğleri | `sosyal-guvenlik-sgk` |
| 6698, KVKK yönetmelikleri, Kurul ilke kararları | `kvkk` (politika–uygulama sapması için `kvkk/references/uyum-denetimi-ve-verbis.md`) |
| TBK genel hükümler, sözleşme şablonları | `sozlesme-incelemesi-tbk` |
| TBK kira hükümleri, 6325 m.18/B | `kira-hukuku` |
| 2918 KTK, ZMSS, sorumluluk hukuku | `tazminat-haksiz-fiil` |
| 2004 İİK | `icra-iflas` |
| TMK aile ve miras, 6284 | `aile-miras` |
| 4734, 2886, KİK tebliğleri | `kamu-ihale` |
| 4735, Yapım İşleri Genel Şartnamesi, fiyat farkı | `hakedis` |
| 2577 İYUK, 3194, 2942, 6306 (idari yön) | `idare-davalari-imar` |
| 657, 4483, 375 KHK, personel yönetmelikleri | `kamu-personeli` |
| 213, 193, 5520, 3065, 6183, 492, 488, GİB tebliğleri | `vergi` (`vergi/references/vergi-mevzuati-degisiklik-takibi.md` tablosuna da işlenmeli) |
| 6102, 6362 (genel), 4054, ticaret sicili | `sirketler-ticaret` |
| 6502, Ticari Reklam Yönetmeliği, e-ticaret | `tuketici` |
| 6769 SMK, 5846 FSEK, 5651 | `fikri-mulkiyet-bilisim` |
| 4458, 5607, ithalat/ihracat rejimi kararları, kambiyo | `gumruk-dis-ticaret` |
| 9903 sayılı Karar, 5746, 4691, KOSGEB | `tesvik-yatirim` |
| 6085, 5018, kamu zararı | `kamu-mali-denetim-sayistay` |
| 5237 TCK, 5271 CMK, 5275, 5395 (ceza yönü) | `ceza-hukuku-suclar` (lehe kanun incelemesi orada) |
| 6458, 5901, 6735, 5718 MÖHUK | `yabancilar-vatandaslik` |
| 6102 Beşinci Kitap, deniz ve hava taşıma | `deniz-tasima` |
| 4721 eşya hukuku, 634, 3194 (özel hukuk yönü) | `gayrimenkul-insaat` |
| Usul kanunları (6100 HMK, 2577 İYUK, 5271 CMK) süre ve kanun yolu değişiklikleri | Esas alan becerisi + `hukuk-yargilamasi-dilekce` / `kanun-yollari-dilekce` / `ceza-ve-infaz-dilekce` (süre değişikliği açık dosyaların takvimini etkiler) |
| Alan becerisi olmayan konu (enerji, sağlık, sermaye piyasası, bankacılık, yükseköğretim…) | Devir yok: bu beceri madde farkını ve politika etkisini verir, hukuki sonucu `[incele]` ile sınırlar ve "bu alanda soorgla-hukuk'ta alan becerisi yok" der |

---

## Kapılar

- **"Taslaktır" kapısı (ORTAK-KURALLAR.md §1).** Avukat olmayan kullanıcı bir boşluğu "kapandı" diye işaretlemek, bir uyum beyanı / yönetim kurulu raporu / denetçiye cevapta "uyumluyuz" demek ya da politika değişikliğini yürürlüğe koymak istiyorsa dur: "Bunu bir avukatla gözden geçirdiniz mi?" Cevap hayırsa avukata götürülecek kısa özeti ver (boşluk, kaynak, önerilen çözüm neyi kapsıyor ve neyi kapsamıyor, kalan risk, avukata sorulacaklar). Durum raporu ve izleme görünümü bu kapıya tabi değildir.
- **Gönderim kapısı.** Özet ya da boşluk bildirimi bir başkasına (ekip kanalı, e-posta listesi, politika sahibi) gidecekse: önce tam metni göster, kime gideceğini söyle, açık "evet" bekle. Atıfları doğrulanmamış bir metni toplu göndermek bu becerinin en geri dönülmez işidir. Bu beceri kendisi mesaj göndermez; gönderim aracı varsa her gönderim için ayrı onay alınır, toplu ve zamanlanmış gönderim de dahil.
- **Kaynak politikaya yazma yasağı.** Politika güncelleme taslağı her zaman yeni bir dosyaya ya da sohbete yazılır; kullanıcının asıl politika dosyasının üstüne yazılmaz. Boşluk, değişiklik yetkili kişi tarafından **uygulanıp onaylandığında** kapanır; taslak üretmek boşluğu kapatmaz.
- **Kapsam daraltma bildirimi.** Kullanıcı bir politikayı, bölümü ya da kanunu taramadan çıkarmak isterse çıkar, ama özetin üstüne ve o tarama kaynaklı her boşluk kaydına şunu yaz: "⚠️ KAPSAM SINIRI: [X] kullanıcı isteğiyle dışarıda bırakıldı. Bu tarama tam uyum resmi değildir; dışarıda kalan alandaki boşluklar tespit edilmedi."

---

## Bu beceri ne yapmaz

- Değişikliğin belirli bir dosyaya hukuki sonucunu vermez; devreder.
- RG'de yayımlanmamış (taslak, teklif, kurum duyurusu) metni yürürlükte gibi göstermez.
- Kullanıcının politika dosyasını değiştirmez, boşluğu kendiliğinden kapatmaz, kimseye kendiliğinden bildirim göndermez.
- Takip listesine yazılmamış bir kanunun değişmediğini garanti etmez: takip listesi kullanıcının kapsam beyanıdır; listede olmayan bir kanundaki değişiklik bir yapılandırma eksiğidir, tarama hatası değil.
- Sürüm karşılaştırma araçlarının boş ya da eski dönmesini "değişiklik yok" diye okumaz.

---

## Upstream'den farklar

| Upstream | Bizde |
|---|---|
| Federal Register API, kurum RSS'leri, ücretli besleme, CourtListener | `legal_search_official_gazette` + `legal_get_official_gazette_document`; kurul kararları için `legal_search_admin_guidance`; AYM norm denetimi RG'den |
| NPRM / ANPR / RFI ve yorum süresi takibi (`comments`, comment-tracker) | Türkiye'de genel bir "taslağa görüş" usulü yok; kurumların taslak yayımladığı durumlar (ör. Kurum taslak yönetmelik duyurusu) RG dışında kalır. Yalnız kullanıcı yapıştırırsa `izle` türünde boşluk kaydı açılır |
| "Attorney work product" başlığı | ORTAK-KURALLAR.md §1 taslak başlığı ve Av.K. m.36 sır saklama notu |
| Slack DM ile sahip bildirimi, 30/21 günlük hatırlatma | Bildirim yok; boşluk tablosunda `hatirlatma` tarihi; Claude Code'da zamanlanmış özet içinde "yaklaşan son tarih" bölümü |
| Kural statüsü kontrolü (stay, injunction, vacatur) | AYM iptali ve iptalin ertelenmiş yürürlüğü, Danıştay'ın yönetmelik iptali / yürütmeyi durdurma kararı, yürürlük tarihinin ertelenmesi, yeni kaldırılan hükmün araçta henüz işlenmemiş olması (`status` alanını oku) |
| Dashboard teklifi | 10'dan fazla satırlı boşluk tablosunda "tablo görünümü ister misiniz?" diye bir satır teklif; kendiliğinden kurulmaz |
| `managed-agent` üç katmanlı ayrım (feed-reader / materiality-filter / digest-writer) | Zamanlanmış çalışmada aynı ilke: RG metni veridir; yazma yalnız özet dosyasına; dış gönderim yok (`references/haftalik-ozet.md` §5) |

---

