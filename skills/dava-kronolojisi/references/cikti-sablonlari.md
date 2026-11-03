# Çıktı şablonları

Dört çıktı vardır. Varsayılan **çalışma kronolojisi**dir; diğerleri istek üzerine üretilir ve çalışma kronolojisinden türetilir (aynı olay numaraları korunur).

| Çıktı | Bayrak | Kime | İçerik |
|---|---|---|---|
| Çalışma kronolojisi | `--calisma` (varsayılan) | Avukat, büro içi | Bütün olaylar, işaretler, boşluklar, süre aktarım bloğu |
| Olay anlatımı | `--anlatim` | Dilekçe "açıklamalar" bölümü taslağı | Yalnız 🔴 ve ilgili 🟡; düzyazı, delil atıflı |
| Tanık kronolojisi | `--tanik <ad>` | Tanık hazırlığı, tanık beyanına karşı soru | Tanığın gönderen, alan, katılan ya da konu olduğu olaylar |
| CSV | `--csv` | Excel, büro programı | Çalışma kronolojisinin tablo kısmı |

---

## 1. Çalışma kronolojisi

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> **Gizlilik.** Bu kronoloji müvekkil dosyasındaki belgelerden türetilmiştir ve avukatın sır saklama yükümlülüğü (Av.K. m.36) kapsamındaki bilgileri, kişisel verileri ve özel nitelikli kişisel verileri içerebilir. "GİZLİDİR" başlığı bir etikettir, koruma değildir. Avukat-müvekkil ilişkisi dışındaki birine (karşı taraf, şirket içi birimler, sigorta, bilirkişi) göndermeden önce dış sürüm hazırlayın. Aşağıdaki `gizlilik_durusu` satırı, sonraki her gönderim kararının dayanağıdır.
> [Diske yazıldıysa:] Bu dosya bilgisayarınızda düz metin olarak `[tam yol]` yolunda durur.

> ⚠️ **Gözden geçiren notu** (ORTAK-KURALLAR.md §8)
> - **Kaynaklar:** soorgla ✓ | soorgla bağlı değil — hukuki etki atıfları model bilgisinden
> - **Okunan:** [N belgenin N'i; uzun belgelerde sayfa aralığı; OCR'la okunanlar]
> - **Takdirinize bırakılan:** [N `[incele]`; N çelişkili tarih; N sınırda önem]
> - **Güncellik:** [hukuki etki maddeleri AAAA-AA-GG'de çekildi]
> - **Güvenmeden önce:** [ör. 🔴 olayların kaynak alıntılarını belgeyle karşılaştırın; çelişkili tebliğ tarihini UETS kaydıyla doğrulayın]
> - **Profil:** [var | yok — genel cevap]

# Kronoloji — [dosya adı / taraflar]

> Önem işaretleri (🔴/🟡/⚪) ve gizlilik işaretleri (🔒) ilk okumadır; dışarı çıkan her belgede (dilekçe, müvekkil yazısı, arabuluculuk) kullanmadan önce `[incele]`.

**Dosya:** [dosya-kisa-adi | belge kipi — dosya açılmadı]
**Mahkeme / esas no:** [biliniyorsa; bilinmiyorsa [___]]
**Kip:** dosya | belge
**Kurulma:** [YYYY-AA-GG] · **Sürüm:** v[N]
**Kaynaklar:** [N] belge ([türlere göre sayı: dilekçe 4, tebligat 6, rapor 2, yazışma 23 …])
**Olaylar:** [N] ([N] 🔴 / [N] 🟡 / [N] ⚪) · **Çelişkili:** [N] · **Yaklaşık tarihli:** [N]
**Kilit olgu:** [tek cümle]
**Önem bakışı:** [davacı / davalı / sanık / katılan / idare]
**gizlilik_durusu:** A | B | C — [B/C ise gerekçe]
**Özel kısıt:** [yok | soruşturma gizliliği | kapalı duruşma | başka dosyadan belge | özel nitelikli veri]

[Süre geçmiş ya da 7 günden az kalmışsa burada: 🔴 **SÜRE:** S[n] — [olay] — ön hesap son gün [tarih]]

---

## Zaman çizelgesi

| No | Tarih | Kesinlik | Olay | Kaynak (belge + yer) | Alıntı | Önem | Hukuki etki | 🔒 |
|---|---|---|---|---|---|---|---|---|
| K-01 | 2025-03-12 | kesin | Davalı, davacıya fesih bildirimini elden verdi | Fesih bildirimi s.1; dava dilekçesi s.2 ¶3 (iddia); cevap s.3 ¶1 | "…12.03.2025 tarihi itibarıyla…" | 🔴 | süre başlatır — 4857 m.20/1 [soorgla] | açık |
| K-02 | 2025-03 (yaklaşık) | yaklaşık | … | … | … | 🟡 | — | 🔒 sır |
| K-03 | ⚠️ 2026-03-02 / 2026-03-07 | çelişkili | Gerekçeli karar davalı vekiline e-tebligatla … | UYAP ekranı; UETS alındısı | "…" / "…" | 🔴 | süre başlatır — HMK m.345 [soorgla] | açık |

## Kilit olaylar (yalnız 🔴)

### K-01 — [YYYY-AA-GG] — [başlık]
- **Ne oldu:** [tek satır]
- **Neden önemli:** [kilit olguya bağı — analiz, etiketli]
- **Kaynaklar:** [liste]

## Çelişen tarihler

| Olay | Tarih A (kaynak) | Tarih B (kaynak) | Sonucu değiştiriyor mu | Olası neden | Nasıl çözülür |
|---|---|---|---|---|---|
| K-03 | 2026-03-02 (UYAP ekranı) | 2026-03-07 (Tebligat K. m.7/a ile türetilmiş) | Evet — istinaf süresinin son günü değişir 🔴 | UYAP ekranı ulaşma tarihini gösteriyor olabilir | UETS delil kaydı / mahkemeden müzekkere `[incele]` |

## Boşluklar
**Olay olmayan aralıklar:** [aralıklar ve soru]
**Anılan ama dosyada olmayan belgeler:** [liste]
**Okunamayan kaynaklar:** [liste ve nedeni]

## Süre aktarım bloğu → sure-takibi
[hukuki-onem-ve-sure-aktarimi.md §3 biçiminde]

## İşaretler
- `[doğrula: …]` — olgu belgeyle henüz karşılaştırılmadı (OCR, el yazısı, saat dilimi, arife)
- `[KAYNAK GEREKLİ]` — olayın belge yeri bulunamadı
- `[incele: …]` — avukat takdiri (çelişki, sınırda önem, gizlilik niteliği, delilin hukuka uygunluğu)

## Sürüm
- v[N] — [YYYY-AA-GG] — [kaynak özeti]
- v[N-1] — [YYYY-AA-GG] (önceki)

**Kontrol listemde olmayan ama soracağım bir soru:** …

**Şimdi ne yapalım?** [SKILL.md "Sonraki adım"]
```

**Olay numarası (K-nn)** kalıcıdır: yeni sürümde mevcut olayların numarası değişmez, yeni olaylar sona eklenir (tablo yine tarih sırasıyla gösterilir). Unsur-delil tablosu, olay anlatımı ve süre aktarım bloğu bu numaralara atıf yapar.

---

## 2. Olay anlatımı (`--anlatim`)

Dilekçenin "AÇIKLAMALAR" bölümünün iskeletidir; dilekçenin kendisi değildir (dilekçe metni `ORTAK-KURALLAR.md` §14'teki dilekçe becerisinde kurulur).

- Yalnız 🔴 ve davaya bağlı 🟡 olaylar; tarih sırasıyla düzyazı. Her paragraf bir olay ya da sıkı bağlı bir olay kümesi.
- Her olgunun sonunda delil göstergesi: `(EK-3: fesih bildirimi)`, `(Bilirkişi raporu s.12)`, `(Tanık [ad])`. Ek numaraları kullanıcının delil listesiyle eşleşmiyorsa `[EK-__]` bırak.
- **İç anlatım yok:** "kronolojiyi çıkardım", önem gerekçeleri, `[incele]` işaretleri anlatıma girmez; kaynak etiketleri dipnotta toplanır (`ORTAK-KURALLAR.md` §8, §13/5).
- **Gizlilik filtresi:** `gizlilik_durusu: B` ise `🔒 sır` ve `🔒 incele` olaylar **varsayılan olarak dışarıda**. Kullanıcı yine de istiyorsa açık onay iste ve onayı çıktının başına kalıcı olarak yaz: `Not: 🔒 işaretli [N] olay avukatın [tarih] tarihli açık onayıyla eklendi.`
- **Çelişkili tarihler:** anlatımda tek bir tarih seçilmez; avukat seçene kadar `[tarih: K-03 çelişkili — seçiniz]` kalır.
- **Beyan ile olgu:** karşı tarafın iddiası olan olaylar olgu gibi anlatılmaz ("davalı … iddia etmektedir").
- Temsil edilen tarafın bakışı kullanılır; kullanıcı aksini söylemedikçe profildeki taraf.

---

## 3. Tanık kronolojisi (`--tanik <ad>`)

- Tanığın gönderen, alıcı, katılan, tutanakta imzacı ya da konu olduğu bütün olaylar.
- Ek sütun: **Tanık bunu nereden biliyor?** (bizzat gördü / duydu / başkasından duydu / belgeyi imzaladı).
- Ek bölüm: **Tanığın önceki beyanları** (ifade, tutanak, e-posta) ile kronoloji arasındaki çelişkiler — duruşmada sorulacak sorular için.
- Tanığın kişisel verileri (adres, T.C. kimlik no, sağlık) çıktıya gerekmedikçe yazılmaz.

---

## 4. CSV

Sütunlar: `no,tarih,kesinlik,olay,kaynak,alinti,onem,hukuki_etki,dayanak,gizlilik`. UTF-8. Hücre `=`, `+`, `-`, `@`, sekme ya da satır başıyla başlıyorsa başına `'` ekle (karşı taraf belgelerinden alınan alıntılar formül olarak çalışabilir); tırnak eklenen hücre sayısını gözden geçiren notuna yaz. Excel'de Türkçe karakter sorunu olursa kullanıcıya "Veri → Metinden" ile UTF-8 seçerek açmasını söyle.

---

## 5. Artımlı kurulum ve sürüm farkı

Önceki kronoloji varsa (dosya kipinde `kronoloji.md`; Claude Code dışı istemcide kullanıcının yapıştırdığı metin):
1. Önceki sürümü oku; olay numaralarını koru.
2. Yeni kaynaklardan olayları çıkar, tekilleştir.
3. Fark özeti:
   - **Yeni olaylar** (K-nn, tarih, tek satır)
   - **Kaynak eklenen olaylar** (yeni belge mevcut olayı doğruladı ya da çelişki çıkardı)
   - **Değişen önem ya da kesinlik** (gerekçesiyle; 🔴 → 🟡 düşürme gerekçesiz yapılmaz)
   - **Çıkarılan olaylar** (nadir; nedeni yazılır, numara boş bırakılır)
4. Sürüm numarasını artır; önceki sürümü dosya kipinde `kronoloji-v[N-1].md` olarak sakla (kullanıcı istemezse üzerine yazma).

---

## 6. Dosya konumu ve istemci farkları

| Ortam | Nereye | Not |
|---|---|---|
| Claude Code / Cowork, dosya kipi | `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/kronoloji.md` (+ `.csv`, eski sürümler) | Etkin dosyayı teyit et; başka dosyanın klasörüne yazma, başka dosyanın belgesini okuma |
| Claude Code, belge kipi | Sohbet | Kullanıcı isterse aynı yapıda yeni bir dosya klasörüne ya da kullanıcının gösterdiği yola; yolu açıkça yaz |
| claude.ai web, ChatGPT, dosya sistemi yok | Sohbet + sonda tek **kopyalanacak blok** (markdown tablo ya da CSV) | Sürüm farkı için önceki kronolojiyi yapıştırmasını iste; yüklenen belgelerin o hizmette saklandığını bir satırla hatırlat |

Diske yazılan her dosyanın başında gizlilik notu ve tam yol bulunur (bölüm 1).
