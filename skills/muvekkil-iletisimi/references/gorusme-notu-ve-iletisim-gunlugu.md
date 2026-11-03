# Görüşme notu ve müvekkil iletişim günlüğü

Uyarlama: Anthropic `legal-clinic/client-comms-log` (yalnız ekleme yapılan kayıt, `--add/--read/--summary/--patterns` kipleri, gözetim taraması) (Apache 2.0). Klinik dönem devri (semester-handoff) ve öğrenci gözetimi yerine büro içi devir ve sorumlu avukat incelemesi kondu.

---

## 1. Neden tutulur

1. **Özen ve ispat.** Müvekkil "bana kimse söylemedi" dediğinde tarihli kayıt cevaptır. Davanın safhaları hakkında müvekkile bilgi vermemek, kanunun tanıdığı bir hakkın kullanımını engelliyorsa kınama sebebidir (Av.K. m.135/2-l, 7571 ile değişik) `[soorgla]`; avukatın özen borcu ağırdır (Yargıtay HGK E.2022/109 K.2023/439) `[soorgla]`.
2. **Devir.** Dosya başka avukata ya da stajyere geçtiğinde müvekkile aynı sorular yeniden sorulmaz.
3. **Görünürlük.** Cevapsız aramalar, kaçan geri dönüşler, uzun sessizlikler kayıtta görünür.
4. **Dosya tutma yükümlülüğü.** Dosya tutmamak ya da saklama yükümlülüğünü ihlal etmek uyarma sebebidir (Av.K. m.135/1-l) `[soorgla]`; evrak saklama süresi Av.K. m.39 `[soorgla]`.

Günlük **iletişim kaydıdır, hukuki analiz deposu değildir.** Strateji, sulh sınırı ve değerlendirme iç notta tutulur.

---

## 2. Nerede tutulur — gizlilik

| Ortam | Yer | Not |
|---|---|---|
| Claude Code, dosya klasörü etkin | `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/iletisim-gunlugu.md` | Dosya klasörü becerisiyle aynı klasör yapısı |
| Claude Code, dosya klasörü kapalı | Aynı yol; ilk yazımdan önce kullanıcı onayı ve yol gösterimi | Klasör yoksa oluştur |
| claude.ai web, ChatGPT, mobil | Dosya yazılmaz | Kayıt sohbette kopyalanacak blok olarak verilir; kullanıcı büro programına / UYAP not alanına / kendi dosyasına yapıştırır |

İlk kayıtta bir kez söylenecek uyarı:

> Bu günlük müvekkil sırrı niteliğinde bilgi (Av.K. m.36) ve kişisel veri içerir. Bilgisayarınızda `[yol]` altında şifrelenmemiş düz metin olarak durur; yedekleme, disk şifrelemesi ve erişim yetkisi büronuzun sorumluluğundadır. Özel nitelikli kişisel veriyi (sağlık, ceza mahkûmiyeti vb.) yalnız gerekiyorsa ve en az ölçüde yazın `[model bilgisi — doğrulayın: KVKK m.6]`.

Kurallar:
- `<dosya-kisa-adi>` müvekkil adı ya da T.C. kimlik numarası içermez (ör. `2026-014-kira-tahliye`).
- Bir dosyanın günlüğüne başka dosyanın bilgisi yazılmaz; bir dosyada çalışırken başka dosyanın günlüğü okunmaz (ORTAK-KURALLAR.md "Büro profili").
- Günlükte kart, IBAN, parola, e-Devlet şifresi gibi bilgiler tutulmaz; müvekkil gönderdiyse "IBAN alındı (kayıtta tutulmadı)" yazılır.

---

## 3. Kipler

Bağımsız değişken: `[dosya-kisa-adi] [--ekle (varsayılan) | --oku | --ozet | --tarama]`. Dosya kısa adı verilmediyse sor; dosya klasörü etkinse etkin dosyayı öner.

### 3.1 `--ekle` — yeni kayıt

Alanlar:
- **Tarih ve saat** (varsayılan: şimdi; Europe/Istanbul)
- **Yön:** `gelen` (müvekkil → büro) | `giden` (büro → müvekkil)
- **Kanal:** telefon | e-posta | KEP | mektup | yüz yüze | görüntülü | WhatsApp/SMS | sesli mesaj bırakıldı | sesli mesaj alındı
- **Büro tarafı:** ad
- **Karşı taraf:** müvekkil ya da "üçüncü kişi: [nitelik — eşi, şirket muhasebecisi, karşı taraf avukatı]". Üçüncü kişiyle müvekkil hakkında konuşulduysa müvekkilin izni var mı? (Av.K. m.36) — yoksa `[incele]`.
- **Süre / uzunluk:** "10 dk telefon", "3 paragraf e-posta"
- **Özet:** 2-4 cümle; ne konuşuldu, ne söylendi. Özellikle **müvekkile söylenen süre, masraf ve risk** açıkça yazılır.
- **Yapılacaklar:**
  - Büronun müvekkile borcu (ne, ne zamana kadar)
  - Müvekkilin büroya borcu (belge, karar, ödeme — ne zamana kadar)
- **Takip tarihi**
- **Notlar:** dil, iletişim güçlüğü, müvekkilin tutumu (yargılayıcı değil, olgusal)

**Yazmadan önce:** biçimlendirilmiş kaydı kullanıcıya göster ve onay iste. Onaysız yazılmaz.

Günlük dosyası yoksa başlıkla oluştur:

```markdown
# İletişim günlüğü — [dosya kısa adı]

**Dosya:** [dosya-kisa-adi]
**Müvekkil:** [ad — ya da baş harfler, profil tercihine göre]
**Açılış:** [AAAA-AA-GG]

Yalnız ekleme yapılır. En yeni kayıt en üstte.
Gizlilik: Av.K. m.36 kapsamında müvekkil sırrı; kişisel veri.

---
```

Kayıt biçimi (en yeni üstte):

```markdown
### [AAAA-AA-GG SS:DD] — [giden/gelen] — [kanal] — [büro tarafı] ↔ [karşı taraf]
**Süre:** [___]
**Özet:** [2-4 cümle]
**Söylenen süre / masraf / risk:** [varsa açıkça; yoksa "yok"]
**Büro yapacak:** [iş — son tarih] | yok
**Müvekkil yapacak:** [iş — son tarih] | yok
**Takip:** [tarih] | yok
**Not:** [___]
```

### 3.2 `--oku`

Son N kaydı göster (varsayılan 5). Müvekkili aramadan önce ya da dosyayı devralırken kullanılır.

### 3.3 `--ozet`

Tek paragraf: son temas (tarih, kanal), toplam kayıt sayısı, en sık kanal, büronun açık işleri, cevaplanmamış gelen iletişim, müvekkilden beklenenler. Devir notuna ve iç durum notuna (`sade-dil-ve-durum-mektubu.md` §5) girer.

### 3.4 `--tarama` — gözetim taraması

Sorumlu avukat / ortak için; şunları işaretle:

| Bulgu | Ölçüt | Önem |
|---|---|---|
| Cevapsız gelen iletişim | Gelen kayıttan sonra giden kayıt yok | Süre işleyen dosyada 🔴, diğerinde 🟠 |
| Kaçan takip | Takip tarihi geçmiş, sonrasında kapatan kayıt yok | 🟠 |
| Süre bildirimi eksik | Alan becerisi / dosya notu bir süre gösteriyor ama günlükte müvekkile bildirildiğine dair kayıt yok | 🔴 (Av.K. m.135/2-l riski `[incele]`) |
| Yalnız sözlü bildirim | Süre ya da masraf bilgisi yalnız telefonla verilmiş, yazılı teyit kaydı yok | 🟠 |
| Dil / erişim | Müvekkilin dili Türkçe değil ya da okuma güçlüğü notu var; giden yazılar buna uygun mu | 🟡 |
| Tutum değişimi | Ardışık kayıtlarda artan kızgınlık/endişe notu | 🟡 → ortakla görüşme önerisi |
| Uzun sessizlik | Etkin dosyada uzun süre hiç temas yok (eşik profilden; yoksa sor) | 🟡 |

Tarama sonuçları tahmin değil kayıt temellidir: "kayıtta görünmüyor" yaz, "yapılmamış" yazma; kayıt tutulmamış olabilir.

---

## 4. Görüşme notu (ilk görüşme ya da önemli görüşme)

Uzun görüşmeler günlüğe tek kayıtla, ayrıntısı ayrı notla girer: `.../dosyalar/<dosya-kisa-adi>/gorusme-notlari/<AAAA-AA-GG>-<konu>.md`.

```markdown
[ORTAK-KURALLAR.md §1 avukat başlığı]

# Görüşme notu — [dosya kısa adı] — [tarih]

**Katılanlar:** [büro] / [müvekkil ve varsa yanındakiler — sıfatları]
**Kanal ve süre:** [___]

## Müvekkilin anlattığı olaylar
[Kronolojik, müvekkilin ifadesiyle; "müvekkile göre" diye. Olgu-değerlendirme ayrımı:
değerlendirme bu bölüme girmez.]

## Müvekkilin istediği
[Ne sonuç bekliyor — kendi sözleriyle]

## Müvekkile söylenenler
- Süreler: [her biri, dayanağıyla — dayanak alan becerisinden ya da `[incele]`]
- Masraf ve ücret: [___]
- Riskler: [___]
- **Sonuç vaadi verilmedi** (kontrol: `kotu-haber-ve-sonuc-vaadi.md` §1) — [✓ / dikkat: …]

## Alınan / istenen belgeler
| Belge | Alındı / istendi | Son tarih |

## Açık sorular
- [___]

## Sonraki adım
- [ ] [iş — kim — son tarih]
```

Görüşme notu müvekkilin anlatımını **değerlendirmeden** kaydeder; esas değerlendirmesi ilgili alan becerisine devredilir (devirde bu not "olay özeti" olarak taşınır, ORTAK-KURALLAR.md §14).

---

## 5. Bağlantılar

- Durum mektubu, kötü haber teyidi ya da ücret mektubu gönderildikten sonra → `--ekle` öner.
- İç durum notu hazırlanırken → `--ozet` oku.
- Bir kayıt müvekkile süre doğuruyorsa (ör. "Cuma'ya kadar belge getirecek") → süre takibi becerisi (yüklüyse); yoksa avukat notunda tablo.
- Dosya devri → `--ozet` + son 5 kayıt.

## 6. Bu kip ne yapmaz

- **Geçmiş kaydı düzeltmez.** Yalnız ekleme: yanlış kayıt, yeni bir kayıtla "[tarih] tarihli kayıt düzeltmesi: …" diye düzeltilir.
- **Dış sistemlerden otomatik kayıt çekmez** (e-posta, santral, UYAP). Ortamda e-posta arama aracı varsa kullanıcı isterse belirli bir yazışmanın özetlenip günlüğe eklenmesi önerilebilir; kendiliğinden taranmaz.
- **Kayıt disiplinini sağlayamaz.** Kaydedilmeyen görüşmeyi bilemez.
- **Strateji tutmaz.**
