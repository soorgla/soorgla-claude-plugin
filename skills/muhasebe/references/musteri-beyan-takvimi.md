# Müşteri bazında beyan takvimi

Büronun müşteri listesinden (türüne göre) aylık, üç aylık ve yıllık beyan/ödeme son günleri tablosunu üretmek ve süre defterine aktarmak. Gün kuralları madde ve tebliğden çekilir; son gün tatil kontrolüyle kesinleşir. Müşteri adı ve VKN çıktıya, deftere ve profile **yazılmaz**.

## Ne zaman
- "Bu ay hangi müşteri ne verecek?", "Kasım takvimini çıkar."
- "Yeni müşteri aldım (limited, bilanço) — yıllık takvimini kur."
- "Son gün pazara denk geliyor mu?"

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Takvim dönemi (ay / yıl) | Hangi beyanlar düşer | Bu ay varsay, yaz |
| Müşteri kısa kodu (ad değil: `M-014`, `limited-03`) | Satır kimliği | Kullanıcıdan kod iste; ad verirse `[Müşteri-n]` kullan |
| Müşteri türü: kurum (bilanço) / gerçek kişi bilanço / işletme / serbest meslek / basit usul / yalnız GMSİ | Beyan seti | Sor |
| KDV mükellefi mi, tevkifat sorumlusu mu | KDV 1 / KDV 2 | Sor |
| İşçi sayısı ve muhtasarı üç aylık verme tercihi | MUHSGK aylık mı (GVK 98/3) | Sor |
| Özel hesap dönemi | KV ve geçici vergi günleri kayar | Sor |
| Damga, ÖTV, turizm payı vb. ek yükümlülük | Ek satırlar | Sor `[incele]` |

## Araç çağrıları

`legal_calculate_deadline` **vergi beyan kodu içermez** (kod listesinde yalnız vergi uyuşmazlığı süreleri var: `tax_penalty_reduction_376`, `tax_settlement_request`, `iyuk_tax_lawsuit`, `tax_payment_order_objection`). Bu yüzden:

1. Ham son günü aşağıdaki tablodan (madde/tebliğ) kur.
2. Her ham günü `legal_check_holiday` ile sına; tatilse VUK 18/4'e göre izleyen ilk iş günü, onu da sına.
3. Mali tatil (Temmuz) dönemine düşen günleri ayrıca işaretle `[doğrula]`.

```json
legal_check_holiday { "tarih": "2026-12-28" }
legal_check_holiday { "tarih": "2027-03-25" }
```
Araç `{tatil, aciklama, tatil_turu, yarim}` döndürür; arife (`yarim: true`) günü 13.00'ten sonra tatildir — son gün arifeye denk gelirse 🟠 not düş `[incele]` (e-beyanname saatine etkisi).

## Hukuki çerçeve — gün kuralları

| Beyan | Kanundaki gün | Dayanak | Not |
|---|---|---|---|
| KDV (KDV 1) | Vergilendirme dönemini izleyen ayın 24'ü; tevkifat sorumlusu (KDV 2) 21'i | 3065 m.41/1 | Uygulamadaki gün Bakanlık düzenlemesiyle farklı olabilir; güncel VUK GT / KDV GUT'tan oku `[doğrula]` |
| Muhtasar (MUHSGK) | Ertesi ayın 23'ü; maddedeki hizmet erbabı sayısını aşmayanlar bildirimle Ocak, Nisan, Temmuz, Ekim 23'ü | GVK m.98 | Muhtasar ve Prim Hizmet Beyannamesi GT (Sıra No: 1) ve sonraki düzenlemelerle güncel gün `[doğrula]` |
| Muhtasar ödemesi | Beyannamenin verildiği ayın 26'sı | 5520 m.21/4 | GV tarafı GVK'den `[doğrula]` |
| Geçici vergi (GV ve KV) | Üç aylık dönemi izleyen ikinci ayın 14'ü beyan, 17'si ödeme | GVK mük.120/3; 5520 m.32/2 | Son (4.) dönemde beyan verilip verilmediği `[doğrula]` |
| Kurumlar vergisi | Hesap döneminin kapandığı ayı izleyen 4. ayın 1-25'i; ödeme aynı ayın sonu | 5520 m.14/3, m.21/1 | Özel hesap döneminde kayar |
| Yıllık gelir vergisi | İzleyen yılın Mart 1-25'i | GVK m.92/1 | Ödeme taksitleri (GVK m.117) `[doğrula]` |
| Basit usul | Ayrı gün ve kazanç istisnası (GVK m.20/B) | — | Bu turda okunmadı `[doğrula]` |
| Damga vergisi beyannamesi, Ba-Bs, e-defter berat, ÖTV, KKDF | — | — | Tebliğden `[doğrula]`; okunmadan satır açma, `[HESAPLANACAK]` yaz |

- **Süre hesabı:** gün olarak belirtilen sürede başlangıç günü sayılmaz; "sonu belli bir gün" ile tayin edilen süre o günün tatil saatinde biter; resmi tatil süreye dahildir ama **son gün resmi tatile rastlarsa izleyen ilk iş gününün tatil saatinde biter.** [Vergi Usul Kanunu m. 18](https://soorgla.com/mevzuat/213-vergi-usul-kanunu/) [soorgla]
- **Mali tatil:** 5604 sayılı Kanun; m.2 SGK ve iş mevzuatı beyan, bildirim ve ödemelerinin m.1'deki süre kadar ertelendiğini söyler; vergi beyanlarına etkisi m.1'de; madde metninden doğrula `[doğrula]`.
- Pişmanlık, gecikme zammı ve geç beyan sonuçları → `beyan-takvimi-ve-odemeler.md`.

## Müşteri türüne göre beyan seti (iskelet)

| Tür | Aylık | Üç aylık | Yıllık |
|---|---|---|---|
| Kurum (bilanço) | KDV 1 (/2), MUHSGK, damga `[doğrula]` | Geçici KV | KV (4. ay), e-defter/berat `[doğrula]` |
| Gerçek kişi bilanço / işletme | KDV, MUHSGK (işçi varsa) | Geçici GV | Yıllık GV (Mart) |
| Serbest meslek | KDV, MUHSGK (stopaj/işçi) | Geçici GV | Yıllık GV (Mart) |
| Basit usul | — `[doğrula]` | — | GVK m.20/B ve beyan durumu `[doğrula]` |
| Yalnız GMSİ (kira) | — | — | Yıllık GV (Mart) → `kira_geliri` |

## Çıktı iskeleti

```markdown
MESLEKİ ÇALIŞMA TASLAĞI — SMMM/YMM İNCELEMESİ GEREKTİRİR
> ⚠️ Gözden geçiren notu: soorgla ✓ (tatil kontrolü) · gün kuralları madde metninden, tebliğ günü [doğrula] satırlarında · müşteri adı yok

## Beyan takvimi — [AA.YYYY]
| Son gün | Gün | Müşteri kodu | Beyan / ödeme | Dönem | Dayanak | Hesap | Durum |
|---|---|---|---|---|---|---|---|
| [GG.AA.YYYY] | [gün] | M-014 | KDV 1 | Ekim 2026 | 3065 m.41 + [tebliğ günü doğrula] | ham gün → legal_check_holiday → son gün | açık |
```
Satır sırası: son güne göre; aynı günde müşteri koduna göre.

## Süre defterine aktarma
"Bu satırları süre defterine ekleyeyim mi?" → onayla → [sure-takibi](../../sure-takibi/SKILL.md) `--ekle`, her satır için:
- `id`: `<müşteri kodu>-<beyan>-<YYYY-AA>`; `alan: muhasebe`; `tur: uyum` (beyanname türü; bkz. `../../sure-takibi/references/sure-turleri-ve-kaynak-haritasi.md` §1); `saat_sahibi: biz`.
- `dayanak`: madde + `[soorgla]`; tebliğ günü doğrulanmadıysa `[doğrula]`. `hesap: "elle [doğrula]"` (beyan kodu yok). `gerekce`: "dönem sonu → kural (madde) → ham gün → legal_check_holiday → son gün".
- `ic_hedef`: profildeki iç hedef payı; belge teslim günü müşteriye ayrıca bildirilecekse ayrı satır.
- Başlık ve notlarda **müşteri adı, VKN, ciro yok** (ORTAK-KURALLAR.md "Büro profili"; süre defteri gizlilik notu). Profile müşteri listesi yazılmaz; liste kullanıcının kendi dosyasında kalır.

## Kontrol listesi
- ✅ Her satırda dayanak ve tatil kontrolü var.
- 🔴 Tebliğle değişmiş günü kanundaki günle yazmak (KDV, MUHSGK) → doğrulanmadıysa satırı `[doğrula]`la, "kesin" deme.
- 🟠 Üç aylık muhtasar tercihi olan müşteride aylık satır açmak / tersi.
- 🟠 Özel hesap dönemli kurumda takvim yılı varsaymak.
- 🟡 Ödeme günü beyan gününden farklı (geçici vergi, KV, muhtasar) — iki satır.
- [incele] Mücbir sebep / süre uzatımı ilanı (VUK GT) — ilan edilmişse ilgili il ve müşteriler.

## Uyuşmazlığa dönüş
Kaçırılan beyan için ceza ihbarnamesi, izaha davet, uzlaşma ya da dava süresi → `../../vergi/SKILL.md`; bu süreler `legal_calculate_deadline` kodlarıyla (`tax_settlement_request`, `iyuk_tax_lawsuit` …) hesaplanır.
