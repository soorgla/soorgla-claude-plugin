# Çıktı: markdown, CSV, Excel

Upstream `excel-output.md` ve `gsheets-output.md` uyarlamasıdır. İşlem ekiplerinin gerçekten açtığı dosya genellikle Excel'dir; doğru kur.

## 1. Hangi biçim?

| Biçim | Ne zaman | Not |
|---|---|---|
| **Markdown tablo** | Her zaman, sohbet içinde | Uzun tabloda yalnız ilk 20 satır + işaretli satırlar; tamamı dosyada |
| **CSV** (`<ad>.csv` + `<ad>_kaynaklar.csv`) | Dosya sistemi varsa her zaman | Değerler bir dosyada, alıntı ve yerler eşlik dosyasında; ana dosya temiz kalır |
| **Excel** (`.xlsx`) | Kullanıcı isterse ya da ekip Excel'de çalışıyorsa | Sor, tahmin etme |
| **Google Sheets** | Kullanıcı açıkça isterse ve yazma yetkili bir bağlayıcı varsa | Yetkiyi önce sına; yoksa CSV + içe aktarma talimatı |

Excel yolu: ortamda bir xlsx becerisi ya da aracı varsa (ör. `anthropic-skills:xlsx`) onu kullan; yoksa Python `openpyxl` (`python -c "import openpyxl"` ile sına; yoksa kurmayı öner ya da CSV'de kal). Hiçbiri yoksa CSV ver ve bunu söyle.

## 2. Formül enjeksiyonu koruması (zorunlu)

Karşı taraftan gelen metin (sözleşme alıntısı, unvan, adres, sistem dökümü) saldırgan denetimindedir. Excel, Sheets ya da LibreOffice bir hücreyi formül sanarsa makro tetiklenebilir ya da veri dışarı sızdırılabilir.

- Belgeden, araç sonucundan ya da kullanıcı yapıştırmasından gelen **her metin hücresinde**, ilk karakter `=`, `+`, `-`, `@`, sekme (`\t`), satır başı (`\r`) ya da satır sonu (`\n`) ise başına **tek tırnak** (`'`) ekle: `=TOPLA(A1:A10)` → `'=TOPLA(A1:A10)`. Baştaki boşluklar atlanıp ilk anlamlı karaktere bakılır.
- Türk sözleşmelerinde sık görülen tuzak: madde metni "- Taraflar …" ya da "+%10 KDV" diye başlar; kaçışsız açılırsa formül hatası ya da formül olur.
- Sizin ürettiğiniz sütun başlıkları ve hesapladığınız sayılar güvenlidir; sayı sütununa metin yazılmaz.
- **CSV'de ayrıca** RFC 4180 tırnaklaması: virgül, çift tırnak ya da satır sonu içeren alan çift tırnak içine alınır, içteki `"` → `""`. Türkçe Excel CSV'yi noktalı virgülle bekleyebilir; ayırıcıyı kullanıcıya sor ya da `.xlsx` öner. Dosyayı **UTF-8 (BOM'lu)** yaz ki Excel Türkçe karakterleri bozmasın.
- Python'da yazılıyorsa satır sonunu açıkça ver (`newline=""` ile `csv` modülü); Windows'ta düz `open(..., "w")` CRLF ekler.

Bu adım isteğe bağlı değildir: kullanıcının açtığı tablonun bir makroyu tetiklemesi, kullanıcıya yönelik bir tedarik zinciri saldırısıdır.

## 3. Excel çalışma kitabı yapısı

**Sayfa 1: `Inceleme`** (ana tablo)
- Satır 1: taslak başlığı (ORTAK-KURALLAR.md §1, role göre) — birleştirilmiş tek hücre.
- Satır 2: dağıtım notu (aşağıda §5).
- Satır 3: sütun etiketleri; satır 4+: her belge (ya da madde) bir satır.
- A sütunu: belge adı / yolu (Sheets'te belgeye bağlantı).
- Sonra şema sırasıyla her veri sütunu; her veri sütununun hemen ardından gizli `_kaynak` sütunu (`[alıntı] | [yer]`) ve görünür hücreye **açıklama (comment)** olarak aynı alıntı + yer (gizli sütun kapalıyken de üzerine gelince görünür).
- Hücre dolgusu duruma göre: dolgusuz = `cevaplandi`; açık sarı `#FFF2CC` = `belirsiz` ya da `incelenmeli`; açık gri `#EFEFEF` = `yok`.
- Her [veri + _kaynak] grubundan sonra boş bir `Dogrulandi` sütunu: açılır liste `✓`, `✗`, `?`. Gözden geçiren doldurur; ekibin neyi bir insanın gerçekten kontrol ettiğini görmesini sağlar.
- Veri bölgesinde hücre birleştirme yok (avukatlar sıralar ve süzer). Alıntılar kesilmez; hücre metni kaydırılır ya da tam alıntı açıklamada durur.

**Sayfa 2: `Isaretler`** — `belirsiz` / `incelenmeli` her hücre bir satır: Belge | Sütun | Durum | Değer | Alıntı | Yer | Not. Doğrulama iş kuyruğudur; benzer kararlar birlikte verilsin diye sütuna göre sıralı.

**Sayfa 3: `Onemli_bulgular`** — önem eşiğini aşan ya da 🔴/🟠 işaretli satırlar: Belge | Konu | Önem | Alıntı | Yer | Devredilecek beceri.

**Sayfa 4: `_sema`** — şema dosyasındaki sütun tanımları: id, etiket, tür, seçenekler, soru. Altı ay sonra dosyayı açan ortak neyin sorulduğunu görür.

**Sayfa 5: `_ozet`** — belge sayısı, sütun sayısı, koşu tarihi; sütun başına `cevaplandi` / `yok` / `belirsiz` / `incelenmeli` sayıları; normalleştirmede işaretlenen sütunlar; okunamayan belgeler; döviz çevirisi yapıldıysa kullanılan `kur_tarihi`; doğrulama hatırlatması.

`_sema` ve `_ozet` olmadan çalışma kitabı teslim edilmez; kendi kendini belgelemesi dosyayı güvenilir kılar. **Güven yüzdesi sütunu yazılmaz**; durum ve alıntı zaten sinyaldir.

## 4. Google Sheets (istenirse)

- Aynı sayfa yapısı. Alıntılar hücre **notu** olarak (yorum değil); not yazdırmada görünmez, bu yüzden `Isaretler` sayfası da alıntıları taşır.
- Belgeler Drive'daysa A sütununda dosyaya bağlantı ver.
- Paylaşım **yalnız sahibi**; "bağlantıya sahip herkes" açılmaz; kullanıcıya bilinçli paylaşmasını söyle.
- Yazma yetkisini sınamadan varsayma; yetki yoksa CSV + `bicim-talimati.md` (renk ve açılır liste nasıl uygulanır) ver.

## 5. Başlık ve dağıtım notu

Her dosyanın ilk satırı taslak başlığıdır. Altına:

> Bu tablo, gizli ve avukatlık sır saklama yükümlülüğü (Av.K. m.36) kapsamındaki belgelerden türetilmiştir ve onların gizlilik niteliğini taşır. Belgelerde kişisel veri varsa tablo da kişisel veri içerir (KVKK). Dağıtımı avukat-müvekkil çevresiyle sınırlı tutun; dosyayı ilgili müvekkil dosyasıyla birlikte saklayın. Her hücre doğrulanması gereken bir ipucudur, bulgu değildir.

Karşı tarafa, veri odası yöneticisine ya da işlem dışındaki birimlere gidecekse `Isaretler`, `_kaynak` sütunları, iç notlar ve önem işaretleri çıkarılmış **ayrı bir sürüm** hazırlanır (ORTAK-KURALLAR.md §1 gönderim yeri kontrolü).

## 6. Dosya adı ve yeri

- Ad: `<kisa-ad>_tablolu-inceleme_<YYYY-AA-GG>.xlsx` / `.csv` / `_kaynaklar.csv`, şema `.inceleme-semasi.yaml`. Dosya adına müvekkil ya da karşı taraf adı yazma; kısa kod kullan.
- Yer: kullanıcının gösterdiği klasör ya da profilde dosya çalışma alanı etkinse `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/tablolu-inceleme/`. Yazmadan önce yolu söyle; yedekleme/senkron klasörüyse uyar.
- Dosya sistemi yoksa (claude.ai web dosya üretemiyorsa, ChatGPT): markdown tablo + kullanıcının kopyalayıp `.csv` olarak kaydedeceği bir CSV kod bloğu (formül kaçışı uygulanmış) + şema bloğu. "Dosya oluşturamadım; aşağıdaki bloğu kopyalayın" diye açıkça söyle.

## 7. Özet ekranı (sohbette)

```markdown
[TASLAK BAŞLIĞI]

> ⚠️ Gözden geçiren notu — Kaynaklar: [soorgla ✓ | bağlı değil] · Okunan: [N/M belge tamamı; okunamayan: …] · Takdirinize bırakılan: [N `incelenmeli` hücre] · Profil: [var/yok]

## Tablolu inceleme — [kısa ad] — [tarih]

**Belge:** N · **Sütun:** K · **Tamamlanan satır:** N
**Doğrulama iş yükü:**
| Sütun | yok | belirsiz | incelenmeli | Not |
**Normalleştirmede işaretlenen sütunlar:** [%10 üstü olanlar; alıntı uyuşmazlıkları]
**Önemli bulgular:** [🔴/🟠 satırlar, en fazla 10; tamamı `Onemli_bulgular` sayfasında]
**Dosyalar:** [yol]

Her hücre bir ipucudur; beyan, açıklama eki ya da mütalaaya girmeden önce doğrulanmalıdır.

**Şimdi ne yapalım?** [SKILL.md Adım 8]
```
