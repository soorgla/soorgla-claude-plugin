---
name: hesaplamalar
description: >
  soorgla hesap araçlarının ne zaman ve nasıl kullanılacağını gösteren ve
  hesap tablosunu kuran iş akışı becerisi: faiz, süre ve son gün, harç, TÜFE
  değişimi ve ortalaması, asgari ücret ve kıdem tavanı, kesinlik ve temyiz
  sınırı, döviz kuru, bakiye ömür. Kullanıcı "faiz hesapla", "son gün ne
  zaman", "harç ne kadar", "TÜFE ne kadar arttı", "kur kaç" dediğinde kullan.
  Kıdem-ihbar, kira artışı, destekten yoksun kalma, fiyat farkı gibi alan
  hesaplarının hukuki değerlendirmesi ilgili alan becerisinde (is-hukuku,
  kira-hukuku, tazminat-haksiz-fiil, hakedis, icra-iflas, vergi) kalır.
argument-hint: "[ne hesaplanacak: tutar, başlangıç ve bitiş tarihi, tebliğ tarihi, dava değeri, para birimi, yaş ve cinsiyet]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /hesaplamalar

soorgla MCP'nin sekiz hesap aracını doğru kullanmak için kısa yönlendirme becerisi. Araçların her birinin girdisi, çıktısı, tuzakları ve çalışmayan yerleri `references/` altındadır; her soruda yalnız ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (taslak başlığı §1, MCP ön kontrolü §3, kaynak etiketi §4, sessiz tamamlama yok §5, kullanıcının söylediği olguyu doğrula §6, gözden geçiren notu §8). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; yoksa genel cevap ver ve notta "Profil: yok — genel cevap" yaz.

---

## Ne zaman kullanılır

- Faiz: yasal faiz, ticari temerrüt faizi, avans ve reeskont oranı, yarıyıl kuralı, basit faiz, gecikme zammı.
- Süre hesabı ve son gün: istinaf, temyiz, icra şikâyeti, adli tatil, resmî tatil, arife.
- Harç: başvurma, peşin, karar ve ilam, icra tahsil harcı.
- TÜFE değişimi ve on iki aylık ortalama, asgari ücret, kıdem tazminatı tavanı, kesinlik ve temyiz sınırı.
- Döviz kuru (TCMB), bakiye ömür ve yaşam tablosu.
- Tipik cümleler: "kaç gün faiz işler", "asgari ücret ne kadar", "tavan ne", "bakiye ömür".

## Kapsam

**Kapsar:** hesap aracını seçmek ve çağırmak, aracın döndürdüğü değerin dönemini ve dayanağını kontrol etmek, araç tanımadığında elle hesabın yolunu göstermek, her hesabı **girdi → formül → ara sonuç → sonuç → kaynak** tablosuyla vermek, bilirkişi/mali müşavir teyidi eşiğini işaretlemek.

**Kapsamaz (alan becerisine devreder):**

| Alan hesabı | Esas ve hukuki değerlendirme | Bu becerinin katkısı |
|---|---|---|
| Kıdem, ihbar, fazla mesai, yıllık izin, UBGT | `is-hukuku` (`references/iscilik-alacaklari.md`) | Tavan, asgari ücret, faiz türü ve faiz başlangıcı tablosu |
| Kira artışı, kira tespiti | `kira-hukuku` (`references/kira-bedeli-artis-ve-tespit.md`) | TÜFE on iki aylık ortalamanın araçla yaklaşık hesabı (`references/tufe-ve-endeks.md`) |
| Destekten yoksun kalma, bedensel zarar, iş göremezlik | `tazminat-haksiz-fiil` (`references/bedensel-zarar-ve-destek-hesabi.md`), iş kazası `sosyal-guvenlik-sgk` | Bakiye ömür değeri ve sınırları (`references/yasam-tablosu.md`) |
| Fiyat farkı, gecikme cezası | `hakedis` | Yalnız TÜFE/kur; Yİ-ÜFE alt endeksleri araçta yok |
| Takip tutarı, faiz işletme, harç ve masraf | `icra-iflas` | Faiz ve harç araç kullanımı |
| Vergi gecikme faizi, gecikme zammı, tecil faizi | `vergi` (`references/amme-alacagi-tahsili-6183.md`) | Gecikme zammı oranı ve günlük kesir hesabı |
| Bordro, KDV ve stopaj kırılımı, damga, pişmanlık zammı, vergi cezası tutarı, SGK gecikme, amortisman ve yılsonu | `muhasebe` (`legal_calculate_tax`, `references/arac-kullanimi.md`) | Yalnız kur, TÜFE ve faiz araçları |
| Nafaka artışı (TÜFE) | `aile-miras` | TÜFE değişimi |
| Ecrimisil | `gayrimenkul-insaat` | TÜFE; ÜFE araçta yok |
| Dilekçede harç ve süre tablosu | Dilekçe becerileri (ORTAK-KURALLAR.md §13) | Süre ve harç araç kullanımı |

Alan becerisi çalışırken kendi hesap adımında bu becerinin ilgili referans dosyasına bakabilir; bu beceri alan hesabını yeniden yapmaz, tabloyu ve araç notlarını verir.

---

## İş akışı

### Adım 0 — MCP ön kontrolü
`legal_get_social_parameters` (parametresiz) ya da istenen hesabın aracını çağır. Yanıt gelirse **Kaynaklar** satırına `soorgla ✓`. Gelmezse hiçbir oran, tutar, kur ya da son gün **model bilgisinden kesin değer gibi** verilmez: formülü kur, sayıların yerine `[___ — soorgla bağlı değil, birincil kaynaktan girin]` koy.

### Adım 1 — Hesap türünü sınıfla

| Hesap | İpucu sözcükler | Araç | Oku |
|---|---|---|---|
| A. Faiz | faiz, temerrüt, yasal faiz, ticari faiz, avans faizi, reeskont, işlemiş faiz, gecikme zammı | `legal_get_legal_interest_rates` | `references/faiz.md` |
| B. Süre / son gün | son gün, kaç gün kaldı, tebliğ, istinaf, temyiz, şikâyet, adli tatil, bayram | `legal_calculate_deadline`, `legal_check_holiday` | `references/sure.md` |
| C. Harç | harç, peşin harç, başvurma harcı, karar ve ilam harcı, tahsil harcı, dava masrafı | `legal_calculate_court_fee`, `legal_get_social_parameters` | `references/harc.md` |
| D. TÜFE ve endeks | TÜFE, enflasyon, güncelleme, kira artış oranı, on iki aylık ortalama | `legal_calculate_cpi_change` | `references/tufe-ve-endeks.md` |
| E. Sosyal parametre ve döviz | asgari ücret, kıdem tavanı, kesinlik sınırı, temyiz sınırı, THH sınırı, kur, dolar, euro | `legal_get_social_parameters`, `legal_get_exchange_rate` | `references/parametre-ve-kur.md` |
| F. Bakiye ömür | yaşam beklentisi, bakiye ömür, yaşam tablosu, TRH, PMF | `legal_get_life_expectancy` | `references/yasam-tablosu.md` |

Hangi kodun tanındığı, hangisinin "Kural bulunamadı" ya da sessizce 0 döndürdüğü: `references/arac-durumu.md` (sınama tarihli tablo).

Bir soru birden fazla hesaba giriyorsa (ör. "100 bin TL alacağa dava açacağım, harç ve işlemiş faiz ne olur") hepsini oku, tek tabloda birleştir.

### Adım 2 — Girdileri topla, uydurma
Her hesap için zorunlu girdiler ilgili referans dosyasının başındadır. Eksik girdi `[___]` olarak kalır; tarih, tutar, yaş ya da para birimi tahmin edilmez. Kullanıcının verdiği oran veya süre araçla çelişiyorsa ilk cümlede söyle (ORTAK-KURALLAR.md §6).

### Adım 3 — Aracı çağır ve dönemi kontrol et
Her araç sonucunda **üç şeyi** kontrol et ve tabloya yaz:
1. **Dönem:** dönen değerin `baslangic_tarihi` / `donem_basi` / `kur_tarihi` alanı, hesabın ait olduğu tarihi kapsıyor mu? Kapsamıyorsa söyle; araçların çoğu yalnız **güncel** değeri verir.
2. **Dayanak:** aracın `dayanak` / `kanun_maddesi` alanı. Hukuki dayanağı ayrıca `legal_get_statute_article` ile çekmek gerekiyorsa çek (araç atıf vermez; `usage_hint` bunu söyler).
3. **Sessiz hata:** sonuç `null`, boş liste, `0` ya da "Bilinmeyen harç türü" ise bunu **sonuç gibi kullanma**; `references/arac-durumu.md`'deki geçici yola geç.

### Adım 4 — Hesap tablosu
Her hesap aynı iskeletle verilir:

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8; Güncellik satırına her aracın döndürdüğü dönem/kur tarihi)

## [Hesap adı] — [hesap tarihi]

### Girdiler
| Girdi | Değer | Kaynak |
|---|---|---|
| Anapara / dava değeri / tebliğ tarihi … | … | [kullanıcı verdi] |
| Oran / tavan / harç oranı … | … (dönem: …) | [soorgla] `legal_…` |

### Formül
[tek satır; ör. Faiz = Anapara × (Yıllık oran / 100) × Gün / 365]

### Ara sonuçlar
| Dönem / adım | Gün | Oran | Tutar |
|---|---|---|---|

### Sonuç
**[tutar / son gün]** `[doğrula]` — [tek cümle: neyi kapsamıyor]

### Teyit eşiği
[bilirkişi / mali müşavir / bordro uzmanı teyidi gerekiyor mu — aşağıdaki kurala göre]
```

Kuruşa kadar yuvarlama yalnız son satırda yapılır; ara sonuçlar en az dört ondalıkla taşınır. Araçların döndürdüğü uzun ondalıklar (`6831.000000000000000000`) çıktıda iki ondalığa indirilir.

### Adım 5 — Teyit eşiği
Şu durumlardan biri varsa sonucun üstüne 🟠 ve "**bilirkişi / mali müşavir teyidi gerekir**" yaz:
- Hesap birden fazla oran dönemini, kısmi ödemeyi ya da mahsubu içeriyor.
- Brütten nete geçiş, vergi veya SGK kesintisi gerekiyor (bu beceri vergi ve prim kesintisi hesaplamaz).
- Aktüerya (bakiye ömür + iskonto/progresif rant), maluliyet oranı ya da kusur oranı var.
- Araç değeri hesabın ait olduğu dönemi kapsamıyor ve geçici yol kullanıldı.
- Sonuç bir dilekçede **dava değeri, harç ya da talep tutarı** olarak kullanılacak.
- Sonuç kesinlik, temyiz ya da tüketici hakem heyeti sınırının ±%10 yakınında.

Bunların hiçbiri yoksa yine `[doğrula]` etiketi kalır; "kesin tutar" ibaresi kullanılmaz.

### Adım 6 — Sonraki adım
ORTAK-KURALLAR.md §8 karar ağacı. Hesap bir alan değerlendirmesinin parçasıysa devri yaz: "Bu tablo `is-hukuku` değerlendirmesine girdi olarak taşınabilir."

---

## Ortak hesap kuralları

- **Sayı beceri metninden alınmaz.** Bu beceride ve referanslarında geçen sayılar yalnız sınama örneğidir; her hesapta araçtan yeniden çek.
- **Gün sayımı:** faizde başlangıç günü sayılmaz, bitiş günü sayılır; yıl 365 gün kabul edilir `[model bilgisi — doğrulayın]`; artık yıl farkını ayrıca belirt. Usul sürelerinin sayımı ayrıdır (`references/sure.md`).
- **Dönem bölme:** oran, tavan ya da harç tarifesi hesap aralığında değiştiyse aralığı dönemlere böl, her dönemi ayrı satırda hesapla.
- **Tarih biçimi:** araçlara `YYYY-AA-GG`; çıktıda `GG.AA.YYYY`. Araç tarihleri Europe/Istanbul takvimine göredir.
- **Kaynak etiketi:** araç sonucu `[soorgla]` alır ama aracın dayanak alanı bir madde atfı değildir; maddeyi ayrıca çekmediysen madde atfı `[model bilgisi — doğrulayın]` kalır.
- **Araç-model çelişkisi:** araç X, sen Y biliyorsan ikisini de yaz ve işaretle (ORTAK-KURALLAR.md §7).

---

## Veri ve gizlilik

Bu beceri dosyaya bir şey **yazmaz**; hesap tablosu sohbette verilir.
- Kullanıcı tabloyu kaydetmek isterse ve profilde dosya çalışma alanları etkinse yalnız `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/hesaplar.md` yoluna, yazmadan önce yolu söyleyerek yaz. Müvekkil adı, T.C. kimlik no ve dosya numarası yerine dosya kısa adı kullanılır. Bu dosyalar avukatın sır saklama yükümlülüğü (Av.K. m.36 `[model bilgisi — doğrulayın]`) ve KVKK kapsamındaki kişisel veridir; bilgisayarda şifresiz durur, yedekleme ve paylaşım kullanıcının sorumluluğundadır.
- **claude.ai web, ChatGPT ve dosya sistemi olmayan istemciler:** hiçbir dosyaya yazma. Tabloyu sohbette ver, altına "Kopyalayıp dosyanıza ekleyin" notuyla tek bir markdown bloğu koy. Hesapta kişi adı geçiyorsa blokta baş harfe indir.
- Araçlara yalnız tarih, tutar, yaş ve kod gider; müvekkil adı ya da olay anlatımı araç parametresine yazılmaz.

---

## Bu beceri ne yapmaz

- Hukuki niteleme yapmaz (iş ticari mi, alacak muaccel mi, fesih haklı mı, hangi faiz türü istenebilir): bunu sorar ya da `[incele]` ile alan becerisine bırakır.
- Vergi, SGK primi, damga vergisi, gelir vergisi dilimi hesaplamaz.
- Aktüerya raporu, bilirkişi raporu ya da mali müşavir hesabının yerine geçmez.
- Aracın tanımadığı bir süreyi "araç hesapladı" diye sunmaz.
