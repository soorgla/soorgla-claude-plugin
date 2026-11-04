---
name: tanisma-ve-buro-profili
description: >
  İlk kurulum ve büro profili becerisi: kısa ya da tam tanışma görüşmesiyle
  kullanıcının rolünü, çoğunlukla hangi tarafta olduğunu, uzmanlık alanlarını,
  şehrini, dilekçe biçimini ve imza bloğunu öğrenip tek profil dosyasına
  yazar; profili gösterir ve günceller. Profil yokken ilk kullanımda da
  çalışır; dosya olmayan ortamlar için yapıştırılacak profil bloğu üretir.
  Kullanıcı "kurulum yap", "beni tanı", "profilimi göster", "imza bloğumu
  ekle" dediğinde kullan. Hukuki değerlendirme yapmaz; soru gelince ilgili
  alan becerisine devreder.
argument-hint: "[boş: kurulum | kısa | tam | güncelle <alan> | göster | bağlantı | blok (web/ChatGPT için)]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

<!--
Bu becerideki iş akışı anthropics/claude-for-legal (Apache 2.0, Copyright 2026 Anthropic PBC)
deposundaki cold-start-interview (commercial-legal, employment-legal, litigation-legal, legal-clinic,
law-student ve diğer paketler), customize becerileri ve references/company-profile-template.md
dosyasından Türk hukukuna ve soorgla-hukuk eklentisine uyarlanmış ve değiştirilmiştir. Upstream'deki
12 ayrı paket profili + ortak şirket profili yerine tek profil dosyası kullanılır. ABD'ye özgü unsurlar
(attorney work product, ABA Formal Opinion 512, Model Rules, state bar referral, ASC 450, CLM/HRIS
entegrasyonları) çıkarılmış ya da Türk karşılığıyla değiştirilmiştir. Ayrıntı: NOTICE.md.
-->

# /tanisma-ve-buro-profili

Eklentideki bütün becerilerin okuduğu **tek profil dosyasını** kurar, gösterir ve günceller. Hukuki soru cevaplamaz; profil hazır olunca kullanıcının asıl işini ilgili alan becerisine devreder.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula. Bu becerinin çıktısı bir hukuki analiz değil, kullanıcının kendi beyanlarından oluşan bir ayar dosyasıdır; taslak başlığı (§1) profil dosyasının içine konmaz, ama kurulum sırasında verilen her hukuki bilgi (eşik, süre, madde) §4 etiketlerine ve §6 doğrulama kuralına tabidir.

---

## Ne zaman kullanılır

- Kısa (5 soru) ya da tam görüşme.
- Rol: avukat, stajyer, şirket hukukçusu, kamu görevlisi, vatandaş, hukuk öğrencisi.
- Çoğunlukla hangi taraf (işçi/işveren, kiracı/kiraya veren, alacaklı/borçlu…), uzmanlık alanları, şehir ve adliye.
- Dilekçe biçimi ve imza bloğu, risk iştahı, sık kullanılan şablonlar, UYAP/KEP/UETS kullanımı, dil düzeyi, yükseltme kişisi.
- claude.ai web ve ChatGPT'de dosya yoksa proje talimatına yapıştırılacak profil bloğu.
- Tipik cümleler: "profil oluştur", "profili güncelle", "şu alanı değiştir", "tarafımı değiştir", "bağlantıyı kontrol et", "baştan kuralım".

## Profil nerede durur

| Ortam | Konum | Not |
|---|---|---|
| Claude Code, Claude Cowork (dosya sistemi var) | `~/.claude/plugins/config/soorgla-hukuk/profil.md` | Eklenti güncellemelerinden etkilenmez. Üst klasörleri oluştur. Windows'ta `~` kullanıcı klasörüdür (`C:\Users\<ad>\.claude\...`). |
| claude.ai web, Claude masaüstü sohbeti, ChatGPT (dosya sistemi yok) | Kullanıcının **proje talimatı / özel talimat** alanı ya da sohbetin ilk mesajı | Dosya yazılmaz; profil bloğu üretilir ve kullanıcı yapıştırır → `references/web-ve-chatgpt.md` |

Tek dosya, tek doğru kaynak. Alan becerilerine özgü bölümler (`## İş hukuku`, `## Sözleşme playbook'u` …) aynı dosyanın içinde alt bölümlerdir; ayrı dosya açılmaz. Müvekkil ya da dosya bilgisi profile **yazılmaz** (bkz. "Gizlilik").

---

## Komutlar ve akış seçimi

| Kullanıcı ne dedi / durum | Ne yap | Oku |
|---|---|---|
| Profil yok; "kurulum", "başlayalım", "beni tanı" ya da başka bir beceri profil yokluğunda kurulum önerdi ve kullanıcı kabul etti | Durum kontrolü → kısa mı tam mı sor | `references/kisa-gorusme.md`, `references/tam-gorusme.md` |
| "kısa" | 5 soruluk görüşme, gerisi `[VARSAYILAN]` | `references/kisa-gorusme.md` |
| "tam" ya da kısa profili genişletmek | Role göre dallanan tam görüşme | `references/tam-gorusme.md` |
| "profilimi göster" | Profili oku, bölüm bölüm tek satır özetle; dosya yolunu yaz | — |
| "şu alanı değiştir", "tarafım artık işveren", "imza bloğu ekle", "risk iştahını düşür" | Tek alan güncellemesi (upstream `customize`) | `references/profil-guncelleme.md` |
| "bağlantıyı kontrol et" | Yalnız soorgla MCP ve ortam kontrolü; `## Bağlantılar` bölümünü yeniler | Aşağıda Adım 2 |
| "baştan kuralım" | Tam görüşme; eski profille fark gösterilmeden üzerine yazılmaz | `references/tam-gorusme.md` |
| Dosya sistemi yok (web/ChatGPT) ya da "blok ver" | Profil bloğu üret, yapıştırma talimatı ver | `references/web-ve-chatgpt.md` |
| Kurulumun ortasında hukuki soru geldi | Soruyu not et, "önce kurulumu bitirelim mi, yoksa şimdi mi bakalım?" diye sor; bakılacaksa ilgili alan becerisine devret, kurulumu duraklat | — |

Profil şablonu ve alanların anlamı: `references/profil-sablonu.md`. Diğer becerilerin profili nasıl okuduğu, profil yoksa ne yaptığı: `references/profil-okuma-kurallari.md`. Gizlilik ve saklama: `references/gizlilik-ve-saklama.md`.

---

## İş akışı

### Adım 0 — Durum kontrolü

Profil dosyasını oku (dosya sistemi varsa):

- **Yok** → kurulum önerisine geç (Adım 1).
- **`` satırı var** → "Geçen sefer [bölüm] bölümünde durmuştuk; cevaplarınız kayıtlı. Kaldığımız yerden mi devam, baştan mı?" Cevaplanmış soruyu yeniden sorma.
- **`Rol:` satırı `[DOLDURULACAK]`** → şablon hiç doldurulmamış (ör. elle kopyalanmış); baştan başla.
- **Dolu** → kurulum zaten yapılmış. Kullanıcı açıkça "baştan" demediyse tam görüşme açma; "Profiliniz hazır: [rol], [taraf], [şehir]. Bir alanı mı değiştirelim, yoksa baştan mı kuralım (önce farkı gösteririm)?" de.

Kullanıcının kişisel geçmişinden, başka konuşmalardan, `~/CLAUDE.md` ya da bellek dosyalarından profil alanı **doldurma**. Bu konuşmada daha önce geçen bir bilgi (ör. "Ankara'da çalışıyorum" demişti) varsa önce sor: "Daha önce Ankara dediniz; profile yazayım mı?"

**Kurulum kapsamı kontrolü (Claude Code).** Çalışma klasörü kullanıcının ana klasörü değil de bir proje klasörüyse bir kez söyle: "Eklenti proje kapsamında kurulmuş olabilir; bu durumda yalnız [klasör] içindeki dosyaları okuyabilirim. İndirilenler ya da Belgeler'deki dosyaları da okutacaksanız kullanıcı kapsamında kurun. Profil dosyası yine `~/.claude/plugins/config/soorgla-hukuk/` altında durur." Devam için onay al.

### Adım 1 — Açılış ve çatal (kısa mı, tam mı)

3-4 satırı geçme:

> **soorgla-hukuk**, Türk hukukunda değerlendirme ve dilekçe taslağı hazırlayan becerilerden oluşur; mevzuat, karar, süre, harç ve faiz soorgla'dan kaynağıyla çekilir. Bordro, vergi, gümrük ve aktüerya hesapları da soorgla araçlarıyla yapılır; araç yanıt vermezse dayanak, adımlar ve süre verilir, tutar hesaplanmaz.
>
> **Kısa kurulum (yaklaşık 2 dakika, 5 soru):** rolünüz, çoğunlukla hangi tarafta olduğunuz, uzmanlık alanlarınız, şehriniz ve yazı diliniz. Gerisi varsayılan kalır.
> **Tam kurulum (10-15 dakika):** bunlara ek olarak dilekçe biçimi ve imza bloğu, risk iştahı, yükseltme kişisi, şablonlarınız, UYAP/KEP kullanımı ve alan bazlı ayarlar.
>
> Hangisi? İstediğiniz an "dur" diyebilirsiniz; cevaplar kaydedilir, sonra kaldığımız yerden devam ederiz.

Seçim gelmeden başka soru sorma. Kullanıcı "hiç kurulum istemiyorum" derse kabul et: profil yazma, genel cevap moduna geç (`references/profil-okuma-kurallari.md` §2) ve bunu bir cümleyle söyle.

### Adım 2 — Bağlantı kontrolü (her iki yolda, ilk sorudan önce)

Upstream kuralı: **tanımlı olmak bağlı olmak değildir.** `.mcp.json`'da soorgla'nın yazılı olması yetmez.

1. `legal_get_social_parameters` (`tur: "asgari_ucret_brut"`) çağır. Sonuç gelirse soorgla **✓ (denendi)**. 
2. Hata ya da araç yoksa **✗**: "soorgla bağlı değil. Claude Code'da `/mcp` → `soorgla` → tarayıcıda giriş; claude.ai'de Ayarlar → Bağlayıcılar → 'Soorgla — Türk Hukuku'. Bağlanmadan da çalışırım ama bütün atıflar `[model bilgisi — doğrulayın]` etiketi alır."
3. Araç listede var ama çağıramıyorsan **⚪ tanımlı ama denenmedi**; nasıl doğrulanacağını tek satırla yaz.
4. Ortam: dosya yazabiliyor musun (Claude Code/Cowork) yoksa web/ChatGPT mi? Word çıktısı için ortamda docx becerisi var mı (varsa ✓, yoksa "Word istenirse markdown verilir")?

**UYAP, KEP ve UETS bağlayıcı değildir.** Eklenti bu sistemlere bağlanmaz, dosya yüklemez, tebligat göndermez (ORTAK-KURALLAR.md §13/7). Profilde bunlar yalnız kullanıcının **çalışma alışkanlığı** olarak tutulur.

Sonucu `## Bağlantılar` bölümüne yaz (bkz. şablon); ✓ yalnız gerçekten dönen çağrı için.

### Adım 3 — Görüşme

- Kısa yol → `references/kisa-gorusme.md`.
- Tam yol → `references/tam-gorusme.md` (role göre dallanır: avukat/büro, stajyer, şirket hukukçusu, kamu görevlisi, vatandaş, öğrenci).

Ortak görüşme kuralları (upstream "interview pacing"):

- **Bir turda en fazla 2-3 cevaplanabilir soru**, alt soruları da sayarak. Ekranı kaydırmadan cevaplanabilmeli. Mümkünse seçenekli sor (1/2/3).
- **Yazılı bir yerde duruyorsa iste.** Dilekçe örneği, imza bloğu, büro yazım kılavuzu, sözleşme şablonu: "Yapıştırın ya da dosya yolunu verin; yoksa kısaca anlatın." Kullanıcıya zaten yazdığı şeyi yeniden yazdırma.
- **Yazılı cevap gereken soruda bekle.** "Bu soru yazılı cevap istiyor; bekliyorum." Cevap gelmeden sonraki soruya geçme.
- **"Atla" geçerlidir.** Atlanan alan `[ATLANDI]` olarak yazılır; sessizce varsayılan atanmaz.
- **Kutuya sığmayan iş.** Kullanıcının işi seçeneklere uymuyorsa (ör. tahkim, deniz ticareti, uluslararası kurumlarda çalışma, akademisyen bilirkişi) "Kendi cümlelerinizle anlatın, profili ona göre kurayım" de; zorla bir kutuya koyma ve hangi alanların uyarlandığını profilde not et.
- **Söylenen hukuki olguyu doğrula (ORTAK-KURALLAR.md §6).** Kullanıcı kurulumda bir eşik, süre ya da madde söylerse profile yazmadan önce soorgla'dan kontrol et. Ör. "30 işçinin altındayız ama iş güvencesi var" → `legal_get_statute_article` (`law_no: "4857"`, `article_no: "18"`) ile eşiği çek, çelişki varsa `[öncül işaretlendi — doğrulayın]` ile sor. Profile yanlış yazılan bir olgu bütün gelecekteki çıktılara sızar; burası en yüksek kaldıraçlı kontrol noktasıdır. 
- **Sayısal değer profile yazılmaz.** Kıdem tavanı, asgari ücret, harç, faiz, parasal sınır profile kopyalanmaz; beceriler her seferinde araçtan çeker (ORTAK-KURALLAR.md §5). Profil yalnız kullanıcının **kendi** eşiklerini tutar (ör. "50.000 TL üstü ihtarnameleri ortak görsün").

### Adım 4 — Yazmadan önce: boşluklar ve çelişkiler

Bütün cevapları baştan oku ve tek mesajda göster, **cevap bekle**:

> Yazmadan önce: [N] alan boş kaldı: [liste]. İkisi önemli: [en önemli boşluk ve neden — ör. "rolünüz belli değil; her çıktının başlığı buna göre seçiliyor"]. Şimdi doldurmak ister misiniz, yoksa boş mu kalsın?

Çelişki varsa (ör. "risk iştahı: atak" ama "her dilekçeyi ortak görsün"; "ağırlıklı taraf: işçi" ama "işveren şirketin iç hukukçusuyum") ikisini yan yana yaz, hangisinin geçerli olduğunu sor. Sessiz boşluk ya da sessiz seçim yok.

### Adım 5 — Yaz

- Yazmadan önce paylaşılan bilgisayar sorusunu sor (`references/gizlilik-ve-saklama.md` §5).
- Dosya sistemi varsa `~/.claude/plugins/config/soorgla-hukuk/profil.md` dosyasını `references/profil-sablonu.md` yapısıyla yaz (UTF-8). Kullanıcının kendi sözcüklerini koru. Bu bir ayar dosyası değil, kullanıcının düz metinle düzeltebileceği bir belgedir: YAML ya da JSON yazma.
- **Var olan profilin üzerine yazarken** önce değişen satırları göster ("şu 4 satır değişecek"), onay al. Var olan alan bölümlerini (`## İş hukuku`, `## Sözleşme playbook'u`) görüşme kapsamı dışındaysa olduğu gibi koru.
- Duraklatma: kullanıcı "dur" derse o ana kadarki cevapları yaz, en üste `` koy, cevaplanmayanları `[BEKLİYOR]` işaretle.
- Dosya yazılamazsa (izin, yol) sessiz kalma: ORTAK-KURALLAR.md §11 kalıbıyla söyle, profil bloğunu sohbete ver ve web akışına geç.

### Adım 6 — Kapanış

1. **Ne duyduğumu özetle**, 5-8 satır: "Şunu anladım: … Yanlış olan ne?"
2. **Nerede tutulduğunu ve gizliliği söyle** (bir kez): dosya yolu, düz metin olduğu, müvekkil bilgisi içermediği → `references/gizlilik-ve-saklama.md` §1'deki kısa metin.
3. **Değiştirmenin yolu:** "Dosyayı doğrudan düzenleyebilirsiniz; ya da 'profili güncelle: …' deyin. En sık değişenler: ağırlıklı taraf, uzmanlık alanları ve imza bloğu."
4. **Ne yapabileceğimi göster** — profile göre seçilmiş 3-5 örnek, genel liste değil. Ör. işçi tarafında çalışan avukata: "işe iade değerlendirmesi ve arabuluculuk başvurusu (`is-hukuku` → `hukuk-yargilamasi-dilekce`)", "kıdem/ihbar hesabı", "istinaf dilekçesi (`kanun-yollari-dilekce`)". Vatandaşa: "işten çıkarıldım, haklarım ne?", "ev sahibim çık diyor", "ödeme emri geldi". Kurulumda kullanıcı somut bir iş söylediyse listeyi atla, o işe geç.
   Meslek mensubuna örnekler kendi alanından seçilir. Mali müşavire: inceleme sonrası uzlaşma mı dava mı, cezada indirim yolları, özelge ve tebliğ araması, brütten nete bordro ve işveren maliyeti, gecikme ve pişmanlık zammı, SGK gecikme, damga, amortisman ve yılsonu (`muhasebe`: vergi uyum, bordro, yılsonu, büro işleri; uyuşmazlıkta `vergi`, `sosyal-guvenlik-sgk`). Gümrük müşavirine: ek tahakkuk ve m.242 itirazı, BTB (`gumruk-dis-ticaret`). Bilirkişiye: rapor öz denetimi ve dayanak kontrolü (`tazminat-haksiz-fiil`; hesap tablosu, aktüerya aracı gelince).
5. **Profil öğrenir:** "Bir çıktı size uymadığında genellikle bir profil ayarıdır; çıktı hangisi olduğunu söyler. 'Bundan sonra imza bloğuna baro sicil numaramı ekle' gibi cümlelerle değiştirebilirsiniz."

Kapanışı tek mesajda ver; kullanıcıyı uzun metinle yorma.

---

## Rol, başlık ve kapı eşlemesi (özet)

Ayrıntı `references/profil-sablonu.md` §1'de. Bu beceri ORTAK-KURALLAR.md §1'deki üç başlık sınıfını **değiştirmez**, yalnız kullanıcı türünden türetir:

| Kullanıcı türü | `Rol:` satırı (başlık sınıfı) | Ek davranış |
|---|---|---|
| Avukat (serbest, ortak, büro çalışanı) | Avukat/hukukçu | — |
| Stajyer avukat | Avukat/hukukçu | Profilde staj avukatı adı; dilekçe ve dışarı giden metinde "staj avukatı onayı" hatırlatması `[model bilgisi — doğrulayın: stajyerin yetki sınırları Av.K. ve TBB Yönetmeliği]` |
| Şirket hukukçusu / şirket avukatı | Avukat/hukukçu | Yükseltme zinciri (hukuk müdürü, genel müdür) sorulur |
| Kamu görevlisi — hukukçu (hukuk müşaviri, kamu avukatı) | Avukat/hukukçu | Kurum içi onay zinciri |
| Kamu görevlisi — hukukçu değil (ihale, personel, mali birim) | Avukat olmayan, avukata erişimi var | Kurum hukuk müşavirliği "avukat irtibatı" olarak yazılır |
| Bilirkişi | Hukukçu bilirkişi → avukat/hukukçu; diğerleri → meslek mensubu | Taraf sorulmaz; hesap tablosu ve rapor öz denetimi; kusur/maluliyet oranını beceri yazmaz |
| Sigorta eksperi / hasar ve rücu birimi | Avukat olmayan, avukata erişimi var (şirket hukuk birimi) | Karşı taraf bakışı (ispat yükü, limit, rücu) |
| Mali müşavir (SM/SMMM/YMM), şirket finans ekibi, gümrük müşaviri | Meslek mensubu (finans ekibinde başlık "MALİ MÜŞAVİR İNCELEMESİ GEREKTİRİR") | Alanında teknik cevap; uyuşmazlığa dönen işte avukat irtibatına yönlendirme |
| Vatandaş / şirket sahibi / İK | Avukat olmayan (erişimi var ya da yok) | ORTAK-KURALLAR.md §1 "Taslaktır" kapısı; erişimi yoksa baro adli yardım bürosu hatırlatması |
| Hukuk öğrencisi | Avukat olmayan, avukata erişimi yok | "Gerçek dosya" kontrolü; çıktılar çalışma notu çerçevesinde |

Avukat olmayan kullanıcıya kurulumda **bir kez** (her çıktıda değil) şunu söyle:

> Her özelliği kullanabilirsiniz. İki şey değişir: (1) Çıktıları "şunu yapın" diye değil, "şunu buldum, avukata şunları sorun" diye veririm; emin olamadığınız bir yeşil ışıktan daha kullanışlıdır. (2) Hukuki sonucu olan adımlardan önce (dilekçe vermek, ihtarname göndermek, ibraname ya da sulh imzalamak, itiraz süresini kullanmak) durup "bunu bir avukatla gözden geçirdiniz mi?" diye sorarım ve avukata götüreceğiniz kısa bir özet hazırlarım. Bu bir sorumluluk reddi değil; aracın neyi iyi yaptığını bilmesi.

Avukata erişimi olmayana ek: "Bulunduğunuz ildeki **baro adli yardım bürosu** ücretsiz avukat desteği için ilk adres; iş, tüketici, kira ve ticari uyuşmazlıklarda **adliyedeki arabuluculuk bürosu** da bilgi verir." `[model bilgisi — doğrulayın: adli yardımın şartları Av.K. ve baro yönetmeliğine göre değişir]`

---

## Gizlilik (özet)

Ayrıntı `references/gizlilik-ve-saklama.md`.

- Profil **büro düzeyindedir**: müvekkil adı, T.C. kimlik no, dosya numarası, olay ayrıntısı profile yazılmaz. Kullanıcı yazdırmak isterse uyar ve dosya çalışma alanını öner (ORTAK-KURALLAR.md "Büro profili" son paragrafı).
- Avukatın sır saklama yükümlülüğü Av.K. m.36'dan doğar [soorgla]; profil dosyası düz metindir, şifrelenmez, bilgisayara erişen herkes okuyabilir. KVKK m.12 veri güvenliği yükümlülüğü [soorgla] büroya da uygulanır; özel nitelikli veriler (sağlık, ceza mahkûmiyeti, sendika üyeliği…) m.6 kapsamındadır [soorgla]. 
- İmza bloğunda baro sicil no, T.C. kimlik no ya da cep telefonu tutulup tutulmayacağını kullanıcı seçer; varsayılan `[___]` yer tutucudur.
- Web/ChatGPT'de profil bloğu sağlayıcının sunucusunda (proje talimatı) durur; bu kullanıcıya söylenir.

---

## Korkuluklar (değiştirilemez)

Kullanıcı profil üzerinden şunları kapatmak isterse ne koruduklarını açıkla, onay alsan bile **kapatma**; profile "kullanıcı istedi, korkuluk yerinde kaldı" notu düş:

- Taslak başlığı (ORTAK-KURALLAR.md §1) ve avukat olmayan için "Taslaktır" kapısı.
- Kaynak etiketleri (`[soorgla]`, `[model bilgisi — doğrulayın]`), `[doğrula]` ve `[incele]` işaretleri (§4).
- Sayısal değerlerin araçtan çekilmesi (§5), önem derecesinin gerekçesiz düşürülmemesi (§8).

Risk iştahı ve dil düzeyi **üslubu** değiştirir; bu korkulukları değiştirmez (bkz. `references/profil-sablonu.md` §6).

---

## Bu beceri ne yapmaz

- Hukuki soru cevaplamaz, dilekçe yazmaz; işi alan ve dilekçe becerilerine devreder.
- Kullanıcı adına rol, taraf ya da risk iştahı seçmez; varsayılanlar başlangıç noktasıdır, `[VARSAYILAN]` diye görünür.
- Müvekkil dosyası tutmaz (dosya klasörü ayrı iştir).
- UYAP, KEP, UETS ya da e-Devlet'e bağlanmaz.
- Kişisel geçmişten, başka sohbetlerden ya da bellekten profil doldurmaz.
- Boş alanı uydurmaz: `[ATLANDI]` / `[VARSAYILAN]` / `[BEKLİYOR]` dürüst işaretlerdir.
