# Şablonlar: dosya.md, _gunluk.md, notlar.md, _liste.yaml

Kaynak: upstream `matter-workspace` (`matter.md`, `history.md` şablonları) ve `matter-intake` (`_log.yaml` şeması); Türk usulüne göre alanlar değiştirildi (UYAP birimi, esas no, vekaletname ve HMK m.74 yetkileri, karşı taraf vekili, arabuluculuk büro no; ABD'ye özgü "legal hold", "reserve", "outside counsel budget" alanları çıkarıldı ya da isteğe bağlı yapıldı).

Boş bırakılan alan `[___]` kalır; uydurulmaz. Her alanın kaynağı gerekiyorsa satır sonunda etiketlenir (`[kullanıcı verdi]`, `[soorgla]`, `[doğrula]`).

---

## 1. `dosya.md` (dosya kartı)

```markdown
GİZLİDİR — MESLEK SIRRI (Av.K. m.36) — KİŞİSEL VERİ İÇERİR (KVKK) — YALNIZ BU DOSYANIN EKİBİ

# Dosya: [Müvekkil ya da kod] — [kısa konu]

**Kısa ad:** [kisa-ad]
**Açılış:** [AAAA-AA-GG]
**Durum:** [on-hazirlik | arabuluculuk | dava | istinaf | temyiz | icra | sulh-muzakeresi | beklemede | kapali]
**Gizlilik sınıfı:** [standart | yüksek | çok yüksek] — [gerekçe tek satır]
**Alan becerisi:** [ör. is-hukuku] · **Rolümüz:** [davacı | davalı | alacaklı | borçlu | şüpheli/sanık müdafii | katılan vekili | başvurucu | danışmanlık]
**Sorumlu avukat:** [___] · **Ekip:** [___]
**Risk:** [🔴 | 🟠 | 🟡 | 🟢] — [avukatın tek cümlelik gerekçesi] `[incele]`

---

## Taraflar

| Sıfat | Ad / unvan | Not |
|---|---|---|
| Müvekkil | [___] | [iletişim kişisi, tercih edilen iletişim yolu] |
| Karşı taraf | [___] | |
| Karşı taraf vekili | [Av. ___, ___ Barosu] | [iletişim; UYAP'ta kayıtlı mı] |
| Diğer | [fer'i müdahil, ihbar olunan, sigorta şirketi, SGK, Hazine] | |

## Merci ve dosya numaraları

| Aşama | Merci / birim | Esas / dosya no | Karar no ve tarihi | Not |
|---|---|---|---|---|
| Arabuluculuk | [___ Arabuluculuk Bürosu] | [büro no] | [son tutanak tarihi] | |
| Soruşturma | [___ Cumhuriyet Başsavcılığı] | [soruşturma no] | | |
| İlk derece | [___ Mahkemesi] | [E. ____/____] | [K. ____/____, tarih] | UYAP birimi: [___] |
| İstinaf | [___ BAM ___ HD] | | | |
| Temyiz | [Yargıtay / Danıştay ___ Daire] | | | |
| İcra | [___ İcra Dairesi] | [E. ____/____] | | |

## Vekaletname ve ücret

- Vekaletname: [noter, tarih, yevmiye no] · Kapsam: [genel dava | özel] `[kullanıcı verdi]`
- HMK m.74 özel yetkileri (sulh, feragat, kabul, ibra, ıslahın tamamı, tahkim, ADR'ye başvuru, tevkil): [var olanları yaz | kontrol edilmedi]
- Ücret sözleşmesi: [yazılı var | yok | ___] — tutar ve koşullar buraya yazılmaz, yalnız varlığı ve yeri.

## Çıkar çatışması kontrolü

- **Durum:** [temiz | bekliyor | yapılmadı | uygulanmaz | sorunlu]
- **Yöntem:** [büro sistemi | büro kaydı/elle | avukatın kendi değerlendirmesi | uygulanmaz — kendi işi]
- **Kontrol eden / tarih:** [___] / [AAAA-AA-GG]
- **Kontrol edilen adlar:** [karşı taraf, bağlı şirketler, karşı taraf vekili, temel tanıklar]
- **Not / atlama gerekçesi:** [varsa — kalıcı kayıt]

## Olay özeti

[2–5 cümle: ne oldu, ne isteniyor, ne tehlikede.] `[kullanıcı verdi]`

**İlk tez (çalışma hipotezi):** [bizim anlatımız · karşı tarafın anlatımı · dönüm olgusu] `[incele]`

## Kritik süreler

Kaynak tablo budur; `sure-takibi` ve portföy özeti `_liste.yaml`'daki kopyasını okur. Değişince ikisi birlikte güncellenir.

| Süre | Başlangıç (olay) | Son gün | Dayanak | Hesaplayan | Durum |
|---|---|---|---|---|---|
| [ör. istinaf] | [gerekçeli kararın tebliği AAAA-AA-GG] | [AAAA-AA-GG] | [HMK m.345 `[soorgla]`] | [legal_calculate_deadline / elle `[doğrula]`] | [açık | yapıldı | kaçtı] |

## Duruşmalar ve ara kararlar

| Tarih | Ne | Verilen süre / iş | Sonuç |
|---|---|---|---|

## Belgeler

Belgenin kendisi buraya kopyalanmaz; yalnız künyesi ve yeri.

| No | Belge | Tarih | Kaynak | Konum | Gizlilik | Not |
|---|---|---|---|---|---|---|
| B1 | [dava dilekçesi] | | [müvekkil | UYAP | karşı taraf | mahkeme] | [yol ya da "büro arşivi"] | [standart | özel nitelikli veri] | |

## Yapılacaklar

- [ ] [iş] — [sorumlu] — [son tarih] — [bağlı süre satırı]

## Dosyaya özgü kurallar

*Profili yalnız bu dosya için geçersiz kılan kurallar.*
- [ör. "Müvekkil yazılı onay olmadan sulh görüşmesi istemiyor."]
- [ör. "Müvekkile yalnız e-posta, telefonla bilgi verilmez."]

## İlgili dosyalar

- [kisa-ad — tek satır neden] *(yalnız ad; o dosyanın içeriği buradan okunmaz)*

## Açık sorular

- [___]

## Kapanış

*(kapatılınca `dosya-kapat.md` §4 bloğu buraya eklenir; yukarıdaki bölümler değiştirilmez)*
```

---

## 2. `_gunluk.md` (olay günlüğü)

```markdown
GİZLİDİR — MESLEK SIRRI (Av.K. m.36) — YALNIZ EKLEME YAPILIR, EN YENİSİ ÜSTTE

# Günlük: [Müvekkil ya da kod] — [kısa konu]

---

## [AAAA-AA-GG] — Dosya açıldı

Kaynak: [müvekkil başvurusu | tebligat | ihtarname | arabuluculuk daveti | ödeme emri | ___].
Çıkar çatışması: [durum]. Alan becerisi: [___]. İlk süre: [___ — son gün ___].
```

Giriş biçimi (her `guncelle` için):

```markdown
## [AAAA-AA-GG] — [Olay türü]: [kısa başlık]

[Bir paragraf: ne oldu, ne anlama geliyor, hemen ne gerekiyor.]

**Değişen alanlar:**
- [alan]: [eski → yeni]

**Süre etkisi:** [yeni süre / süre yok]
**İlgili belge:** [B-no ya da yol]
**Kaydeden:** [ad] · **Kaynak:** [kullanıcı verdi | UYAP | tebligat]
```

---

## 3. `notlar.md`

Boş açılır; yalnız ilk satırda gizlilik başlığı bulunur. Serbest çalışma notu, tez denemesi, görüşme notu. İçindeki bilgi kart ya da günlükle çelişirse geçerli olan kart ve günlüktür.

---

## 4. `_liste.yaml` (portföy dizini)

Dosya başına bir satır. **Yalnız portföy ve süre özeti için gereken en az bilgi** tutulur; olay özeti, tez, belge içeriği buraya yazılmaz. Gizlilik sınıfı "yüksek" ya da "çok yüksek" ise `baslik` alanında müvekkil adı yerine kod kullanılır; `taraflar_cc` (çıkar çatışması için ad listesi) yine tutulur, çünkü kontrol adsız yapılamaz.

```yaml
- kisa_ad: yilmaz-ise-iade-2026
  baslik: "Yılmaz — işe iade"
  alan: is-hukuku
  rolumuz: davaci
  durum: dava # on-hazirlik | arabuluculuk | dava | istinaf | temyiz | icra | sulh-muzakeresi | beklemede | kapali
  merci: "İstanbul ___ İş Mahkemesi"
  esas_no: "2026/___"
  gizlilik: standart # standart | yuksek | cok-yuksek
  risk: orta # dusuk | orta | yuksek | engelleyici (🟢 🟡 🟠 🔴)
  sorumlu: "Av. ___"
  cikar_catismasi:
    durum: temiz # temiz | bekliyor | yapilmadi | uygulanmaz | sorunlu
    yontem: buro-kaydi
    kontrol_eden: "___"
    tarih: 2026-10-31
    atlama: # yalnız gerekçeli atlamada dolar; beceri silmez
      kim: null
      tarih: null
      gerekce: null
  taraflar_cc: ["___ A.Ş.", "Av. ___"]
  sureler:
    - ne: "istinaf"
      son_gun: 2026-11-16
      dayanak: "HMK m.345 [soorgla]"
      hesap: "legal_calculate_deadline" # ya da "elle [doğrula]"
      durum: acik # acik | yapildi | kacti | durdu | kapatildi
      # sure-takibi ek alanları (isteğe bağlı): id, tur, saat_sahibi, baslangic, gerekce,
      # ic_hedef, sorumlu, bagli_sureler, takvim_uid — şema: ../../sure-takibi/references/sure-defteri-ve-takvim.md
  sonraki_durusma: null
  acilis: 2026-10-31
  son_guncelleme: 2026-10-31
  kapanis: null
  sonuc: null
  saklama_bitis: null # kapanışta Av.K. m.39'dan hesaplanır
  yol: dosyalar/yilmaz-ise-iade-2026/
```

**Zorunlu alanlar** (portföy özeti eksikse uyarır): `kisa_ad`, `alan`, `durum`, `gizlilik`, `cikar_catismasi.durum`, `acilis`, `son_guncelleme`.

---

## 5. Profildeki satırlar

ORTAK-KURALLAR.md "Büro profili" şablonundaki bölüm; bu beceri yalnız bu üç satırı değiştirir (önce göstererek):

```markdown
## Dosya (müvekkil) çalışma alanları
- Etkin: [✓ | ✗ — şirket içi kullanıcılar için kapalı]
- Etkin dosya: [kisa-ad | yok — genel bağlam]
- Dosyalar arası bağlam: [kapalı | açık — yalnız açık istekte]
- Çıkar çatışması: [kontrol yeri ve yöntemi; "paralel açılışa izin: evet/hayır"]
- Dosya klasörü yeri: [~/.claude/plugins/config/soorgla-hukuk/dosyalar/ | proje içi ./dosyalar/]
```

Son iki satır profilde yoksa ilk kullanımda sorulur ve eklenmesi önerilir.
