# Bulgu ayıklama, önemli sözleşmeler listesi ve ekip özeti

Upstream `diligence-issue-extraction`, `material-contract-schedule` ve `deal-team-summary` uyarlamasıdır. Bu dosya **iş akışını** verir (envanter, eşik, bulgu biçimi, liste, özet katmanları); şirket satın almanın hukuki çerçevesi (pay devri şekli, onaylar, Rekabet Kurulu, kapanış) `../../sirketler-ticaret/references/sirket-satin-alma-ve-inceleme.md` dosyasındadır ve bulguların değerlendirmesi oradan ve ilgili alan becerilerinden yapılır.

Kaynak belgeler gizlidir; bu dosyadaki her çıktı onların gizlilik niteliğini taşır (SKILL.md "Gizlilik ve dosyaların yeri").

---

## 1. Envanter ve boşluklar

Veri odası (sanal veri odası, paylaşılan klasör, e-posta ekleri) dizinini çıkar ve bilgi talep listesinin kategorileriyle eşle:

| Talep kategorisi | Veri odası klasörü | Belge | Okunan | Durum |
|---|---|---|---|---|
| Şirket ve pay yapısı | /01-Sirket | 45 | 45 | Tamam |
| Önemli sözleşmeler | /02-Sozlesmeler | 312 | 120 | Sürüyor |
| Fikri mülkiyet | /03-FM | 89 | 0 | Başlanmadı |

**Boşluklar:** karşılığı olmayan talep kalemleri ve belgelerde atıf yapılıp veri odasında bulunmayan belgeler → **ek bilgi talebi listesi**. Okunan sütunu gözden geçiren notundaki **Okunan** satırına taşınır.

## 2. Önem eşiği ve okuma sırası

- Eşik kullanıcıdan (ya da pay alım sözleşmesindeki tanımdan) alınır; beceri tutar önermez.
- Sözleşmeleri belirtilen bedele (dosya adı ya da üst veride varsa) ya da karşı tarafın önemine göre sırala; eşiğe ya da kategori sonuna kadar yukarıdan aşağı oku.
- Büyük kategorilerde (yüzlerce sözleşme) partiler hâlinde ilerle; her partiden sonra bulgu listesini güncelle ve 🔴 bulguyu **hemen** bildir, kategori bitmesini bekleme.
- Toplu madde çıkarımı için önce tablolu incelemeyi koştur (`tablolu-inceleme-akisi.md`); bu dosya yargı katmanıdır: yan protokoller, değişiklikler, aracın zorlandığı belgeler.

**Kategori başına standart çıkarım** (ayrıntı ve hukuki çerçeve `sirket-satin-alma-ve-inceleme.md` §2):
- **Önemli sözleşmeler:** kontrol değişikliği (bu işlem tetikliyor mu), devir yasağı, münhasırlık/rekabet yasağı, en iyi koşul şartı, işlem nedeniyle karşı tarafın fesih hakkı, olağan dışı tazmin ve sorumluluk.
- **Şirket:** pay defteri ve sicil uyumu, devir kısıtları ve önalım, işlem için gereken organ kararları, pay sahipleri sözleşmesi (sürükleme, birlikte satış, veto).
- **Fikri mülkiyet:** sahiplik zinciri (çalışan ve yazılımcı devirleri), açık kaynak, lisanslı mı sahipli mi, bekleyen uyuşmazlık.
- **İş:** kontrol değişikliğine bağlı ödemeler, kilit çalışan, bekleyen davalar, işçi statüsü riski (serbest çalışan görünümlü işçi).
- **Uyuşmazlıklar:** bekleyen dava ve icra takipleri, karşılıklar, ihtarlar, idari soruşturmalar (Rekabet, KVKK, vergi incelemesi).
- **Halef sorumluluğu:** malvarlığı/işletme devrinde devralanın borçlardan sorumluluğu ve önceki borçlunun iki yıllık müteselsil sorumluluğu — TBK m.202 `[soorgla]`; devralınan/devralınmayan borçlar ekinin bilinen riskleri kapsayıp kapsamadığı `[incele]`.

## 3. Bulgu biçimi

Kullanıcının (ya da müvekkilin) kendi bulgu şablonu varsa **birebir onu** kullan. Yoksa:

```
Bulgu #N: [başlık]
Kategori: [talep listesi kategorisi]
Önem: 🔴 / 🟠 / 🟡 / 🟢
Belge: [veri odası yolu + belge adı + madde no / sayfa]
Alıntı: "[birebir]"
Bulgu: [belge ne diyor, işlem için neden önemli]
Öneri: [fiyat ayarlaması / özel tazmin / kapanış öncesi onay / beyan ve tekeffül / işlemden çekilme] [incele]
Devir: [ilgili alan becerisi]
```

- **Önem ölçeği** (ORTAK-KURALLAR.md §8): 🔴 işlem değerini ya da yapısını etkiler (kilit müşteride onaya bağlı kontrol değişikliği, açıklanmamış önemli dava, fikri mülkiyet sahiplik boşluğu); 🟠 yüksek, çözülebilir ama zaman alır; 🟡 dikkat gerektirir (onay gerekli ama büyük olasılıkla alınır, giderilebilir açık kaynak sorunu); 🟢 dosya için not. Sınırda olanı yukarı yuvarla; eşik altı/üstü sınır kararını avukat verir.
- Her mevzuat ve karar atfı kaynak etiketi taşır (ORTAK-KURALLAR.md §4). Belge içindeki atıf `[kullanıcı verdi]`.
- **Atfa itiraz:** satıcının ya da karşı tarafın andığı bir maddenin başka bir şey dediğini düşünüyorsan metni `legal_get_statute_article` ile çek ve alıntıla; çekemiyorsan "metni görmeden ne dediğini söyleyemem `[madde çekilemedi — doğrulayın]`" (ORTAK-KURALLAR.md §6).
- **Arama zayıf dönerse sessiz tamamlama yok** (ORTAK-KURALLAR.md §5): kaç sonuç döndüğünü söyle, seçenekleri sun.

Kategori çıktısı:

```markdown
[TASLAK BAŞLIĞI]
> [dağıtım notu — cikti-excel-csv.md §5]
> ⚠️ Gözden geçiren notu …

# Durum tespiti bulguları: [işlem kısa kodu] — [kategori]
**Okunan belge:** N / M · **Kapsam:** [tamamı | eşik üstü | ilk N] · **Bulgular:** N🔴 N🟠 N🟡 N🟢

### Sonuç
[🔴 N engelleyici · 🟠 N yüksek] — [işlem ekibinin bilmesi gereken tek şey]

[bulgular, önem sırasıyla]

## Boşluklar
- [yanıtsız talep kalemi]
- [atıf var, veri odasında yok]
```

**Kapanış öncesi işlemlere devir:** bulgu kapanıştan önce bir iş gerektiriyorsa (karşı taraf onayı, organ kararı, Rekabet Kurulu ya da sektör kurulu izni, ipotek/rehin fekki, borç kapatma yazısı, çalışanla ibra) **kapanış listesine** aktarılmak üzere işaretle → `sirket-satin-alma-ve-inceleme.md` kapanış listesi. Gri bölgedekileri de işaretle; liste aşamasında düşürülebilir. Eksik aktarım tek yönlü kapıdır.

10'dan fazla bulgu çıktıysa ya da kullanıcı isterse: önem ve kategoriye göre sayılar ve sıralanabilir bulgu tablosu içeren bir pano (Artifact) öner.

## 4. Önemli sözleşmeler listesi (açıklama eki) ve onay takibi

Pay alım sözleşmesinde "Ek [X]'te tüm Önemli Sözleşmeler listelenmiştir" türünden bir beyan varsa ek bu adımla hazırlanır.

1. **Tanımı al:** "Önemli Sözleşme" tanımını pay alım sözleşmesi taslağından **birebir** çek. Sözleşmedeki tanım belirleyicidir; profildeki önem eşiği farklıysa sözleşmeninki uygulanır. Tipik ölçütler (tanımın yerine geçmez): yıllık/toplam bedel eşiği, süre, kontrol değişikliği ya da devir yasağı içermesi, münhasırlık/rekabet yasağı, en büyük N müşteri/tedarikçi, taşınmaz kiraları, fikri mülkiyet lisansları, ilişkili taraf sözleşmeleri, kamu sözleşmeleri, olağan iş akışı dışındaki sözleşmeler. Lisanslı sektörlerde sözleşme dışı izin şartları da (SKILL.md Adım 6 sektörel izin araması) ayrıca kontrol edilir.
2. **Tanımı tabloya mekanik uygula:** her sözleşme için `Karşıladığı ölçüt(ler)` ve `Listeye girer mi`. Tablolu incelemenin çıktısı doğrudan girdi olarak kullanılır.
3. **Sınır durumları avukata bırak** `[incele]`: eşiğin hemen altında ama iş için önemli; ölçütü karşılıyor ama zaten feshediliyor; sözlü anlaşma ya da yan mektup.
4. **Liste verisi:** karşı taraf, sözleşme adı/türü, tarih, süre/bitiş, bedel, karşıladığı ölçüt, işlem için onay gerekiyor mu, veri odası yeri. Eksik alan uydurulmaz, `[___]` kalır.
5. **Biçim:** taslaktaki diğer eklerin biçimine uy (numaralı liste ya da tablo; sözleşme türüne göre alt bölümler).

```markdown
## Ek [X] — Önemli Sözleşmeler
İşbu Sözleşme tarihi itibarıyla Önemli Sözleşmeler şunlardır:
### (a) Müşteri sözleşmeleri
1. [Sözleşme adı], [tarih], [Şirket] ile [Karşı taraf] arasında. [Veri odası: yol]
### (b) Tedarikçi sözleşmeleri
…
```

6. **Onay takibi (iç belge, ekin parçası değil):**

| Ek no | Karşı taraf | Onay gerekli mi (madde) | Durum | Sorumlu | Tarih |

Ek, imzalanan sözleşmenin parçası olarak karşı tarafa teslim edilince bir işlem belgesidir; teslimden önce iç notlar (onay takibi, işaretler) ayıklanır.

**Teslim öncesi çapraz kontrol:** ölçütü karşılayan her sözleşme listede mi (eksiksizlik); ölçütü karşılamayan sözleşme listede mi (beyan bir veri dökümü değildir); liste diğer eklerle tutarlı mı (rehin doğuran sözleşme teminatlar ekinde de var mı); her satırın veri odası yeri var mı.

Bu adım tanımı belirlemez (sözleşmededir), onay almaz (izler), beyanı yazmaz (beyanın atıf yaptığı eki doldurur). Beyan ve tekeffül metni → `../../sozlesme-incelemesi-tbk/SKILL.md`.

## 5. İşlem ekibine ve yönetime özet

Okuyucuya göre katman seç; belli değilse sor.

| Okuyucu | Alır | Almaz |
|---|---|---|
| **Yönetim kurulu / üst yönetim** | En önemli 3-5 bulgu, fiyat/yapı etkisi, karar bekleyenler | Kategori ayrıntısı, 🟢 bulgular, süreç |
| **İşlem sorumlusu** | Bütün 🔴 ve 🟠/🟡, ilerleme, karar bekleyenler, sonraki adımlar | 🟢 ayrıntısı |
| **Çalışma ekibi** | Her şey: tam bulgular, kategori durumu, boşluklar | — |

**Yönetim katmanı iskeleti:**

```markdown
[TASLAK BAŞLIĞI]
> Bu özet gizli durum tespiti bulgularını bir araya getirir ve onların gizlilik niteliğini taşır. Avukat-müvekkil çevresi dışına (geniş iş birimleri dahil) dağıtmadan önce dağıtım listesini kontrol edin.

# [İşlem kodu] — Durum tespiti özeti — [tarih]
**Durum:** [Planlandığı gibi / Sorunlar var / Önemli bulgular]
**Kapsam:** veri odasının %[X]'i incelendi

## Önemli bulgular
[3-5; her biri tek paragraf: ne, işleme etkisi, ne yapıyoruz]

## Karar bekleyenler
- [ ] [fiyat ayarlaması / özel tazmin / çekilme eşiği] — [kim karar verir] — [ne zamana]

## Son özetten bu yana
[yeni bulgular, çözülenler, kapsam ilerlemesi]
```

**İşlem sorumlusu katmanı** buna ek olarak: kategori bazında açık bulgular (🔴, 🟠, 🟡 tek satır), ilerleme tablosu (`Kategori | Okunan | Kapsam % | 🔴 | 🟡 | Durum`), boşluklar ve yönetime sorular, önümüzdeki 72 saat. **Çalışma ekibi katmanı** her bulgunun tam bloğunu içerir.

**Farklar önce:** düzenli bir özetse önce değişeni yaz: yeni bulgular, önemi artan/azalan bulgular (gerekçesiyle; ORTAK-KURALLAR.md §8 önem düşürme kuralı), çözülenler (onay alındı, belirsizlik giderildi), kapsam ilerlemesi. "Hâlâ 12 sarı" yerine "2 yeni sarı, 3 çözüldü".

Bu adım önem kararını vermez (çıkarım anında verilen kararları raporlar), bulguyla ne yapılacağına karar vermez (kararı görünür kılar) ve özeti dağıtmaz (taslağı hazırlar, insan gönderir). Müvekkile sade dilde mektup gerekiyorsa ilgili iş akışı becerisine (müvekkil iletişimi) devredilir.

Avukat olmayan kullanıcıda (ör. şirket içi iş geliştirme) özetin başına ORTAK-KURALLAR.md §1 "araştırma notudur" başlığı konur ve her işaretin yanına tek satırlık sade açıklama eklenir.
