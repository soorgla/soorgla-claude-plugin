# Unsur-delil tablosu (isteğe bağlı)

Kronoloji zaman çizelgesidir; unsur-delil tablosu **ispat haritasıdır**. Bir dava ya da savunmanın her unsuru bir satırdır; her satıra o unsuru destekleyen ve çürüten delil, kaynağıyla birlikte yazılır. Asıl çıktı **boş satırlardır**: delili olmayan unsur, davacı için kapatılması gereken açık, davalı için savunma hedefidir.

> **Tablo bir taslaktır; sonuç değildir.** Her hücre avukatın kaynağından doğrulaması gereken bir ipucudur. Unsur listesi aşağıda bir **taban** olarak verilir; bağlayıcı olan kanun metni ve yerleşik içtihattır ve unsurların nihai listesi ilgili **alan becerisinden** alınır. "Boş satır" davanın bittiği anlamına gelmez; nereye bakılması gerektiğini gösterir.

Eksik işaretlemek tek yönlü kapıdır (delilsiz unsurla dava açılır, savunma eksik verilir); fazla işaretlemeyi avukat incelemede kapatır. Kararsızsan `kısmi` ya da `çekişmeli` yaz, `destekli` yazma.

---

## 1. Akış

1. **Dava ya da savunma türünü ve tarafı belirle.** Birden çok talep varsa (maddi + manevi tazminat; işe iade + işçilik alacağı) her biri ayrı tablo.
2. **Gerçekten ileri sürülen talebi esas al.** Dilekçede olmayan bir talebi "olgular elveriyor" diye tabloya ekleme; o ayrı bir değerlendirmedir (alan becerisi).
3. **Unsur listesini yükle:**
   - (a) Aşağıdaki taban şablonlardan biri — **önce alan becerisindeki güncel listeyle karşılaştır**.
   - (b) Kullanıcının verdiği liste ya da yapıştırdığı madde metni → numaralı unsurlara böl.
   - (c) Savunma unsurları: zamanaşımı, hak düşürücü süre, ibra, sulh, feragat, müterafik kusur, illiyet bağının kesilmesi (mücbir sebep, zarar görenin ya da üçüncü kişinin ağır kusuru), takas, ödeme. İspat yükünün kimde olduğunu yaz.
   - Unsur listesini kullanıcıya göster ve onay al, sonra eşle.
4. **Dayanak maddeyi çek.** Tablonun başına unsurların dayanağını soorgla'dan çekilmiş metinle koy (`legal_get_statute_article`); çekilemiyorsa `[model bilgisi — doğrulayın]`.
5. **Eşle.** Kronoloji olayları ve belgeler hücrelere taşınır (aşağıdaki sütunlar).
6. **Boş satır listesi** ve **aşamaya göre okuma** (bölüm 4).

---

## 2. Tablo sütunları

| # | Unsur | Destekleyen delil (kaynak + alıntı) | Çürüten delil (kaynak + alıntı) | Güç | Durum | İspat yükü | Doğrulandı |
|---|---|---|---|---|---|---|---|
| 1 | … | `Bilirkişi raporu s.12: "…"` · kronoloji K-07 | `Cevap dilekçesi s.4 ¶2: "…"` | güçlü / orta / zayıf / yok | destekli / kısmi / çekişmeli / boş / delil toplanmalı | davacı / davalı | ☐ |

- **Kaynak biçimi** (Bates yerine): `[belge adı] s.[sayfa] ¶[paragraf]`, `Tanık [ad] beyanı, [duruşma tarihi] tutanağı s.[x]`, `Bilirkişi raporu s.[x]`, `Keşif tutanağı`, `UYAP evrak no [x]`, `E-posta [tarih saat]`. Kronoloji satırına atıf: `K-[no]`.
- **Birebir alıntı**: belge ya da beyan delilinde kısa birebir alıntı; özet değil. Alıntı üretilemiyorsa hücre `boş` ya da `delil toplanmalı`.
- **Güç**: basit tut; asıl önemli olan `zayıf` ve `yok`.
- **Delilin hukuka uygunluğu**: hukuka aykırı elde edilmiş delil (izinsiz ses kaydı, gizli kamera, başkasının e-postası) varsa satıra `[incele: delilin hukuka uygunluğu]` ekle (HMK m.189/2 `[model bilgisi — doğrulayın]`). Ceza dosyasında bu sütun zorunludur (`ceza-hukuku-suclar` unsur tablosu).

---

## 3. Taban şablonlar (alan becerisiyle karşılaştır)

### 3.1 Genel haksız fiil — TBK m.49
Dayanak: "Kusurlu ve hukuka aykırı bir fiille başkasına zarar veren, bu zararı gidermekle yükümlüdür." [soorgla: Türk Borçlar Kanunu m.49]. Ayrıntı ve özel sorumluluk hâlleri: `tazminat-haksiz-fiil/references/genel-haksiz-fiil-ve-kusursuz-sorumluluk.md`.

| # | Unsur | Tipik delil | İspat yükü |
|---|---|---|---|
| 1 | Fiil (davranış: yapma ya da yapmama) | Tutanak, kamera, tanık, kaza tespit tutanağı | Zarar gören |
| 2 | Hukuka aykırılık (ya da m.49/2: ahlaka aykırı kasıtlı fiil) | İhlal edilen kural, mevzuat, idari karar | Zarar gören |
| 3 | Kusur (kast / ihmal) | Kusur bilirkişi raporu, ceza dosyası | Zarar gören (kusursuz sorumlulukta aranmaz → alan becerisi) |
| 4 | Zarar (maddi / manevi) | Fatura, rapor, aktüer hesabı, maluliyet raporu | Zarar gören |
| 5 | İlliyet bağı (uygun nedensellik) | Adli tıp, bilirkişi, olay sırası (kronoloji) | Zarar gören |
| S1 | Savunma: illiyet bağının kesilmesi | Mücbir sebep, zarar görenin/üçüncü kişinin ağır kusuru | Zarar veren `[model bilgisi — doğrulayın]` |
| S2 | Savunma: zamanaşımı | Öğrenme tarihi ve fiil tarihi (TBK m.72 [soorgla]); kesme sebepleri (TBK m.154 [soorgla]) — kronolojiden | Def'i ileri süren |
| S3 | Savunma: indirim sebepleri (müterafik kusur vb.) | Kronoloji, bilirkişi | Zarar veren; TBK m.52 `[model bilgisi — doğrulayın]` |

### 3.2 İşe iade — 4857 m.18-21
Dayanak: feshin geçerli sebebe dayandığını ispat yükü işverendedir; işçi başka bir sebep iddia ederse onu ispatlar [soorgla: İş Kanunu m.20/2]. Ön şartlar ve kontrol listesi: `is-hukuku/references/fesih-ve-ise-iade.md` (sayısal eşikler — işçi sayısı, kıdem — oradan ve madde metninden çekilir; burada yazılmaz).

| # | Unsur | Tipik delil | İspat yükü |
|---|---|---|---|
| 1 | İş güvencesi ön şartları (işyerindeki işçi sayısı, kıdem, belirsiz süreli sözleşme, işveren vekili olmama) | SGK kayıtları, sözleşme, görev tanımı | İşçi `[incele: ön şartlarda ispat dağılımı]` |
| 2 | Fesih bildirimi: yazılı ve sebebi açık | Fesih bildirimi, tebliğ belgesi | İşveren |
| 3 | Davranış/yetersizlik feshinde savunma alınması | Savunma istem yazısı, savunma, tutanak | İşveren |
| 4 | Geçerli sebep (işçinin yeterliliği, davranışı ya da işletme gereği) | Performans kayıtları, tutanak, işletme kararı, kadro planı | İşveren (m.20/2 [soorgla]) |
| 5 | Feshin son çare olması (işletme gereklerinde) | Başka pozisyon, eğitim, çalışma süresi düzenlemesi kayıtları | İşveren `[model bilgisi — doğrulayın: içtihat]` |
| 6 | Süreler: arabuluculuk başvurusu ve dava | Fesih tebliği → arabulucu başvurusu → son tutanak → dava (4857 m.20/1 [soorgla]; süreleri madde metninden çek) — kronolojiden | İşçi |
| S1 | İşçinin iddia ettiği başka sebep (sendikal, yasak fesih nedeni, kötüniyet) | Yazışma, tanık, zamanlama (kronolojide fesih öncesi olaylar) | İşçi (m.20/2 [soorgla]) |

### 3.3 Sözleşmeye aykırılıktan tazminat — TBK m.112
Dayanak: "Borç hiç veya gereği gibi ifa edilmezse borçlu, kendisine hiçbir kusurun yüklenemeyeceğini ispat etmedikçe, alacaklının bundan doğan zararını gidermekle yükümlüdür." [soorgla: Türk Borçlar Kanunu m.112]. Ayrıntı: `sozlesme-incelemesi-tbk`.

| # | Unsur | Tipik delil | İspat yükü |
|---|---|---|---|
| 1 | Geçerli bir sözleşme ve borç | Sözleşme, ekler, yazışma | Alacaklı |
| 2 | Borca aykırılık (hiç ya da gereği gibi ifa etmeme) | İhtarname, teslim tutanağı, ayıp ihbarı, bilirkişi | Alacaklı |
| 3 | Zarar | Fatura, hesap, bilirkişi | Alacaklı |
| 4 | İlliyet bağı | Olay sırası (kronoloji), bilirkişi | Alacaklı |
| 5 | Kusur (karine) | — borçlu kusursuzluğunu ispatlamadıkça | Borçlu kusursuzluğu ispatlar [soorgla: TBK m.112] |
| S1 | Temerrüt şartları (ihtar ya da kesin vade) | İhtarname ve tebliği — kronolojiden | Alacaklı |

### 3.4 Diğer dava türleri
Bu dosyada şablonu olmayan her dava ve savunmada unsur listesini ilgili alan becerisinin referansından al (ör. boşanmada kusur ve affetme → `aile-miras`; kira tahliyesinde temerrüt ihtarı → `kira-hukuku`; suç unsurları → `ceza-hukuku-suclar` unsur tablosu; idari işlemde yetki-şekil-sebep-konu-amaç → `idare-davalari-imar`). Kullanıcı kendi listesini verirse onu kullan.

---

## 4. Aşamaya göre okuma (HMK yargılaması)

Aynı tablo, davanın aşamasına göre farklı okunur. Usul kuralları için ilgili dilekçe ve alan becerisine bak; aşağıdaki usul atıfları `[model bilgisi — doğrulayın]`.

- **Dava öncesi.** Boş satırlar: dava açmadan önce toplanacak deliller. Delil kaybolma riski varsa delil tespiti (`hukuk-yargilamasi-dilekce/references/delil-tespiti.md`), ihtarname, kayıtların korunması. Dava şartı arabuluculukta tutanağa geçecek olgular.
- **Dilekçeler aşaması.** Her unsur için dilekçede vakıa ve delil gösterilmiş mi? Gösterilmeyen delil sonradan sunulamayabilir (iddianın genişletilmesi yasağı, delil listesi) → `[incele]`; `delil-ve-tanik-listesi.md`.
- **Ön inceleme.** Çekişmeli satırlar uyuşmazlık noktalarının listesidir; çekişmesiz (karşı tarafın kabul ettiği) satırlar tahkikata girmez.
- **Tahkikat.** `delil toplanmalı` satırları: tanık, bilirkişi, keşif, müzekkere (banka, SGK, PTT/UETS delil kaydı) talepleri.
- **Bilirkişi raporu sonrası.** Raporun her unsura ne dediği satırlara işlenir; rapora itiraz bu tablodan kurulur (`hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md`).
- **Kanun yolu.** Karşı tarafın ya da mahkemenin dayandığı delil gerçekten o unsuru kanıtlıyor mu? Zayıf satırlar istinaf/temyiz sebebidir (`kanun-yollari-dilekce`).

---

## 5. Boş satır listesi (öncelikli çıktı)

```markdown
### Delili zayıf ya da olmayan unsurlar
- [#] [unsur] — durum: [boş / delil toplanmalı / kısmi] — eksik olan: [ne] — nasıl kapanır: [belge / tanık / bilirkişi / müzekkere]
```

Okuma notu: davacıysanız bunlar dava açmadan ya da tahkikat bitmeden kapatılması gereken açıklardır; davalıysanız savunmanın hedefleridir; dava öncesindeyseniz delil toplama öncelikleridir. **Bu beceri sonuç bildirmez:** "destekli" unsurlar, "boş" unsurlar ve "çekişmeli" unsurlar listelenir; hükmü avukat verir.

---

## 6. CSV ve tablo güvenliği

CSV ya da Excel çıktısında, hücre `=`, `+`, `-`, `@`, sekme ya da satır başı karakteriyle başlıyorsa başına tek tırnak (`'`) ekle. Karşı taraf dilekçesi, e-posta ve mesaj alıntıları formül olarak çalıştırılabilecek metin içerebilir. Tırnak eklenen hücreleri gözden geçiren notunda say.
