# Şirket satın alma: hukuki inceleme (due diligence) ve kapanış listesi

## Ne zaman kullanılır
- "Bir şirketi (paylarını) satın alıyoruz", "veri odasındaki belgeleri incele", "due diligence raporu", "kontrol değişikliği maddeleri", "kapanışa ne kaldı", "pay alım sözleşmesindeki ön şartlar".
- Satıcı tarafı: veri odası hazırlığı, açıklama listesi (disclosure).

Upstream `diligence-issue-extraction` ve `closing-checklist` uyarlamasıdır. Pay alım sözleşmesinin (SPA) borçlar hukuku incelemesi (beyan ve tekeffüller, tazminat, cezai şart, hukuk seçimi) → `../../sozlesme-incelemesi-tbk/SKILL.md`; bu dosya şirket hukuku, rekabet ve kapanış mekaniğine bakar.

**Büyük işlem kapısı:** satın alma, SKILL.md Adım 6'daki "büyük işlem" sınıfındadır. Aynı gün imza/kapanış istenirse dur.

---

## 1. İnceleme kapsamı ve önemlilik eşiği

İşe başlamadan sor: hangi kategoriler, hangi önemlilik eşiği (ör. yalnız belli tutarın üstündeki sözleşmeler), hangi rapor biçimi (alıcının kendi bulgu şablonu varsa birebir onu kullan). Eşik yoksa öner, tutarı kullanıcı belirler.

**Envanter tablosu** (her kategori için):

| İnceleme kategorisi | Veri odası klasörü | Belge sayısı | Okunan | Durum |

Boş kategorileri "ek bilgi talebi" listesine yaz. **Okunan** satırını gözden geçiren notuna taşı (ORTAK-KURALLAR.md §10).

## 2. Kategori bazında çıkarılacaklar

**Şirket ve pay yapısı**
- Sicil kayıtları ile esas sözleşme ve pay defteri uyumlu mu; ödenmemiş sermaye; hamiline paylar MKK'ya bildirilmiş mi (TTK m.489)?
- Devir sınırları, önalım, onay şartı (A.Ş. m.493; Ltd. m.595 noter + genel kurul) — işlem için kimin onayı gerekiyor?
- Pay sahipleri sözleşmesi: sürükleme/birlikte satış, kilit süresi, veto hakları.
- Asgari sermaye uyumu (geçici m.15 — 31/12/2027'ye uzatıldı, RG 17.10.2026), sermaye kaybı (m.376) göstergeleri.
- Son genel kurulların usulü (çağrı, Bakanlık temsilcisi zorunlu toplantılar) — iptal/butlan riski taşıyan kararlar.
- Bağlı şirketler, şirketler topluluğu ilişkileri (TTK m.195 vd.) `[incele]`.

**Önemli sözleşmeler**
- Kontrol değişikliği (change of control) maddesi: bu işlem tetikliyor mu, karşı tarafın onayı ya da fesih hakkı var mı?
- Devir yasağı (pay devri sözleşme devri değildir; ama kontrol değişikliği maddesi ayrıca kontrol edilir).
- Münhasırlık, rekabet yasağı, en çok kayrılan müşteri şartı (alıcının iş alanını kısıtlıyor mu; 4054 m.4 riski).
- Olağan dışı tazminat ve sorumluluk.

**Fikri mülkiyet** — marka/patent sahipliği şirkette mi; çalışan ve yazılımcı eser devirleri; açık kaynak lisansları `[incele]` → `../../fikri-mulkiyet-bilisim/references/acik-kaynak-lisans-uyumu.md`, `../../fikri-mulkiyet-bilisim/references/telif-fsek-eser-ve-ihlal.md`.

**İş ve SGK** — kilit çalışan, toplu işçi çıkarma riski, kontrol değişikliğine bağlı tazminatlar, prim borçları → `../../is-hukuku/SKILL.md`, `../../sosyal-guvenlik-sgk/SKILL.md`.

**Uyuşmazlıklar ve idari süreçler** — devam eden davalar ve icra takipleri, Rekabet Kurumu soruşturmaları, KVKK Kurul süreçleri (`../../kvkk/SKILL.md`), vergi incelemeleri (`[incele — mali müşavirle]`).

**Kişisel veri** — veri odasında çalışan/müşteri kişisel verisi paylaşılıyorsa KVKK yönü → `../../kvkk/SKILL.md`.

## 3. Bulgu yazımı

Her bulgu:

```
Bulgu #N: [başlık]
Kategori: [şirket / sözleşme / FM / iş / uyuşmazlık / rekabet]
Önem: 🔴/🟠/🟡/🟢
Belge: [veri odası yolu + belge adı + sayfa]
Bulgu: [belge ne diyor, neden önemli]
Öneri: [fiyat ayarlaması / özel tazmin / kapanış öncesi onay / beyan ve tekeffül / işlemden çekilme]
```

- Her mevzuat ve karar atfı kaynak etiketi taşır (ORTAK-KURALLAR.md §4). Kullanıcının ya da satıcının andığı bir maddeye itiraz ediyorsan metni çek ve alıntıla; çekemiyorsan "metni görmeden ne dediğini söyleyemem" (upstream kuralı, ORTAK-KURALLAR.md §6).
- soorgla zayıf dönerse sessizce tamamlama: seçenekleri sun (ORTAK-KURALLAR.md §5).
- Kapanış öncesi işlem gerektiren her bulgu (onay, genel kurul kararı, Rekabet Kurulu izni, ibra, teminat çözümü) **kapanış listesine** aktarılır.

## 4. Rekabet Kurulu izni

- İşlem 4054 m.7 anlamında birleşme/devralma ise ve 2010/4 sayılı Tebliğ m.7'deki ciro eşikleri aşılıyorsa izin alınmadan **hukuki geçerlilik kazanmaz**; izinsiz işlemde idari para cezası (m.16/1-b) ve işlemin etkisi `[incele]`.
- Eşik tutarlarını beceri metnine yazma; Tebliğin güncel m.7'sinden çek. Ayrıntı → `rekabet-hukuku-4054.md`.
- Sektörel izinler (bankacılık, sigorta, enerji, medya, elektronik haberleşme) `[incele]`.

## 5. Kapanış listesi (upstream `closing-checklist` uyarlaması)

Pay alım sözleşmesinden (imzalanmış ya da son taslak) çıkar:
- **Ön şartlar (CP):** Rekabet Kurulu izni, sektörel izin, üçüncü kişi onayları, şirket organ kararları (Ltd.'de genel kurul onayı; A.Ş.'de bağlı payda YK onayı), önalım haklarından feragat.
- **Kapanış teslimleri (CD):** pay defteri kaydı / ciro edilmiş pay senetleri, Ltd.'de noter onaylı devir sözleşmesi ve sicil tescil başvurusu (30 gün), MKK bildirimi (hamiline), YK üyelerinin istifası ve yeni atama kararları, teminat çözüm belgeleri, ibraname.
- **Kapanış öncesi taahhütler** (olağan iş akışı, yasaklı işlemler).

Liste biçimi:

| No | Kalem | Tür (CP/CD/taahhüt) | Sorumlu | Son gün | Durum | Engelleyici mi | Kaynak (SPA maddesi / bulgu no) |

"Kapanışa ne kaldı?" sorusunda: engelleyici açık kalemler, kritik yol, kapanışa kalan gün. Yeni bulgular geldikçe listeye eklenir (upstream "kendini güncelleyen liste").

Ciddi olumsuz değişiklik (MAC/MAE) şartı sözleşmede nasıl tanımlanmış — tanımı sözleşmeden al, Türk hukukunda uygulanışı `[incele]`.

---

## Görüşme soruları
1. İşlemin yapısı: pay devri mi, malvarlığı/işletme devri mi (TBK m.202-203), birleşme mi?
2. Hedef şirket türü, pay yapısı, alınacak oran; kontrol değişiyor mu?
3. Tarafların (grup bazında) Türkiye ve dünya cirosu? Hedef teknoloji teşebbüsü mü?
4. İnceleme kategorileri ve önemlilik eşiği; rapor biçimi?
5. İmza ve kapanış ayrı mı; hedef kapanış tarihi?
6. Veri odası erişimi; belge sayısı?

## soorgla çağrıları

```
legal_get_statute_article law_no: "4054" article_no: "7" | "16" law_type: "Kanun"
legal_search_official_gazette query: "Rekabet Kurulundan İzin Alınması Gereken Birleşme ve Devralmalar Hakkında Tebliğ" search_in: "title" sort_by: "date_desc"
legal_get_official_gazette_document url: "<en son değişiklik tebliği>"
legal_get_statute_article law_no: "6102" article_no: "489" | "490" | "493" | "595" | "598" | "376" | "geçici 15"
legal_get_statute_article law_no: "6098" article_no: "202" | "203" law_type: "Kanun" # malvarlığı/işletme devri
legal_search_cases mahkeme: "yargitay" daire: "11. Hukuk Dairesi" sorgu: "<ör. pay devir sözleşmesinde beyan ve tekeffül ihlali nedeniyle tazminat>" tarih_baslangic: "<son 3 yıl>"
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Okunan: veri odasının hangi kısmı)

## Hukuki inceleme raporu — [proje kodu]

### Yönetici özeti (en önemli 5 bulgu)
### Envanter ve kapsam
### Bulgular (kategori bazında)
### Kapanış listesi
### Ek bilgi talepleri
```

## Sık hatalar
- Rekabet Kurulu iznini "bildirim" sanıp kapanışı izinden önce yapmak (hukuki geçerlilik yok).
- Ltd. pay devrinde genel kurul onayı ve noter şeklini kapanış listesine koymamak.
- Kısmi okumadan "veri odasında sorun yok" demek.
- Satıcının açıklama listesindeki madde atfını metni çekmeden doğru kabul etmek.

## Kaynak ve uyarlama

- Doğrudan karşılığı yok (eski sistemde şirket satın alma görevi yoktu). `consultant/corporate_registry/share_capital_structure.yaml`'daki pay devri ve yapı değişikliği filtreleri ile `lawyer/commercial_corporate/commercial_contracts_analysis.yaml`'daki rekabet notu kullanıldı.
- Upstream: corporate-legal `diligence-issue-extraction` (envanter, önemlilik filtresi, kategori bazında çıkarım, bulgu şablonu, kaynak etiketi ve "metni görmeden yorumlama" kuralı), `closing-checklist` (CP/CD ayrımı, bulgulardan otomatik besleme, engelleyici kalemler, MAC tanımını sözleşmeden alma).
