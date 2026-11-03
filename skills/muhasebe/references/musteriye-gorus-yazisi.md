# Müşteriye yazılı teknik görüş

## Ne zaman
- "Müşterime bu konuda yazı hazırla", "görüşümüzü yazılı verelim", "yönetime bilgi notu".
- Bir hesap, özelge araştırması ya da uygulama sorusunun sonucu müşteriye **yazılı** gidecek.

Aylık durum, eksik belge listesi gibi sade yazışmalar → `../../muvekkil-iletisimi/SKILL.md` (kipleri meslek mensubuna uyarlanarak). Bu dosya **teknik görüş** içindir: dayanağı, varsayımı ve sınırı olan yazı.

---

## Mesleki dayanak

- SMMM'nin işi, defter ve beyanname düzenlemenin yanında, mali mevzuat ve uygulamasında müşavirlik yapmak ve **mali tablo ve beyannamelerle ilgili konularda yazılı görüş vermek**tir; YMM aynı (b) ve (c) işlerini yapar, defter tutamaz. [Serbest Muhasebeci Mali Müşavirlik Ve Yeminli Mali Müşavirlik Kanunu m. 2](https://soorgla.com/mevzuat/3568-serbest-muhasebeci-mali-musavirlik-ve-yeminli-mali-musavirlik-kanunu/) [soorgla]
- **Meslek sırrı:** meslek mensubu ve yanında çalışanlar işleri dolayısıyla öğrendikleri bilgi ve sırları ifşa edemez. [3568 m. 43](https://soorgla.com/mevzuat/3568-serbest-muhasebeci-mali-musavirlik-ve-yeminli-mali-musavirlik-kanunu/) [soorgla]; gizlilik ilkesinin ayrıntısı [Etik İlkeler Hakkında Yönetmelik m. 15](https://soorgla.com/mevzuat/11666-serbest-muhasebeci-mali-musavirler-ve-yeminli-mali-musavirlerin-mesleki-faaliyetlerinde-uyacaklari-etik-ilkeler/#madde-15) [soorgla].

Yazılı görüş meslek alanındadır; başlık `MESLEKİ ÇALIŞMA TASLAĞI — SMMM/YMM İNCELEMESİ GEREKTİRİR` (şirket finans ekibinde `MALİ MÜŞAVİR`). Konu uyuşmazlıksa aşağıdaki "Uyuşmazlık konusunda görüş" bölümü.

---

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Soru, müşterinin kendi cümlesiyle | Görüş neye cevap veriyor | Sor; yazının "Soru" bölümü boş kalamaz |
| Olgular ve dayandığı belgeler (sözleşme, fatura, mizan) | Görüş belgeye dayanır (m.2/A-c) | Varsayım olarak yaz, "Varsayımlar"a taşı |
| Dönem / işlem tarihi | Uygulanacak mevzuat ve oran | Sor |
| Hesap veya araştırma sonucu | Değerlendirmenin içeriği | Önce ilgili alt dosyayı çalıştır (Adım 1 tablosu) |
| Okuyucu (sahip, CFO, yönetim kurulu, banka, karşı taraf) | Gönderim yeri ve iki sürüm | Sor |
| Profil `## Mali müşavirlik` → yazı biçimi ve imza bloğu | Ton ve imza | Profil yoksa resmî biçim, imza `[___]` |

---

## Araç çağrıları

Görüş yazısı kendi başına araç çağırmaz; **içerdiği her sayı ve atıf** ilgili alt dosyanın akışından gelir:

```
legal_calculate_tax { "hesap": "<ilgili hesap>", "girdi": {…}, "tarih": "<işlem tarihi>" }
legal_get_statute_article law_no: "<kanun>" law_type: "Kanun" article_no: "<madde>"
legal_search_statute_semantic sorgu: "<konu>" mevzuat_tur: "teblig"
legal_search_admin_guidance sorgu: "<konu>" belge_tur: "ozelge" tarih_baslangic: "<son 3 yıl>"
```

Yazıya giren her tutarın `parametre` dönemi ve her atfın `markdown_citation` / `kaynak.markdown` bağlantısı iç sürümde saklanır.

---

## İki sürüm (ORTAK-KURALLAR.md §1 gönderim yeri kontrolü)

| | İç değerlendirme | Müşteriye giden sürüm |
|---|---|---|
| Başlık ve gözden geçiren notu | Var | **Yok** (yazının dışında, üstte kalır) |
| `[incele]`, `[doğrula]`, `[soorgla]` etiketleri | Satır içinde | Hiçbiri; açık noktalar "Varsayımlar ve sınırlar"a cümle olarak |
| Araç iç anlatımı ("X aracını çağırdım") | Olabilir | Yok |
| Risk ve alternatif yorumlar | Tam | Sonuca etkisi olanlar, sade |
| Müşteri unvanı / VKN | `[Müşteri]` | Meslek mensubu kendisi doldurur; taslakta `[Müşteri]` |

Okuyucu müşterinin dışındaysa (banka, karşı taraf, alıcı şirket, geniş dağıtım listesi): uyar, meslek sırrını hatırlat (3568 m.43) ve yalnız arındırılmış metni öner. Gönderim bu becerinin işi değildir; e-posta aracı varsa yalnız taslak oluşturulur.

---

## Kontrol listesi

- ✅ Soru tek cümle; görüş o soruya cevap veriyor.
- ✅ Her sayı araçtan ya da madde metninden; dönem yazıldı.
- ✅ Her atıf etiketli kaynaktan; müşteri sürümünde dipnot/kaynak listesinde.
- 🔴 Sonuç vaadi yok ("kesinlikle ceza çıkmaz", "inceleme olmaz" yazılmaz).
- 🔴 Başkasına verilmiş özelge "bizi korur" diye yazılmadı (`ozelge-emsali-ve-celiski.md`).
- 🟠 Varsayımlar ayrı başlıkta; olgu değişirse görüşün değişeceği yazıldı.
- 🟠 Görüş tarihi ve "bu tarihteki mevzuata göre" kaydı var.
- 🟡 Profil yazı biçimi (resmî / sade / madde işaretli) uygulandı.
- [incele] Alternatif yorum varsa hangisinin önerileceği.

## Sık hatalar

- 🔴 İç sürümdeki `[incele]` / `[doğrula]` etiketlerini ya da gözden geçiren notunu müşteri metnine sızdırmak.
- 🔴 Sicil numarasını, oda kaydını ya da müşterinin VKN'sini taslağa yazmak (her zaman `[___]` / `[Müşteri]`).
- 🟠 Tarihsiz görüş: oranlar ve hadler değişince yazı yanıltıcı olur.
- 🟠 Varsayımları gövdeye gömmek; okuyucu hangi olguya dayandığını göremez.
- 🟡 Uzun mevzuat alıntısı; müşteri sürümünde madde adı + bir cümle yeter.

## Uyuşmazlık konusunda görüş

Konu inceleme, izaha davet, ihbarname, uzlaşma, dava, ödeme emri ya da haciz ise:
- Başlık `ARAŞTIRMA NOTUDUR — HUKUKİ TAVSİYE DEĞİLDİR — HAREKETE GEÇMEDEN ÖNCE BİR AVUKATA DANIŞIN` olur; esas değerlendirme `../../vergi/SKILL.md`.
- Meslek mensubu tutarları ve teknik tespitleri yazabilir; **yol seçimi** (uzlaşma / dava / itiraz) önerisi yazılmaz.
- Müşteri sürümüne şu not girer: "Bu konu idare ile uyuşmazlık niteliği taşıdığından, izlenecek yol için bir avukatla görüşmenizi öneririz; [süre] tarihinde dolan süreye dikkat ediniz." Süre `legal_calculate_deadline` ile hesaplanır.
- Profilde "Avukat irtibatı" doluysa adını değil yalnız "çalıştığımız avukat" ifadesini öner; doldurmayı kullanıcıya bırak.

## Çıktı iskeleti

İç değerlendirme SKILL.md Adım 4 iskeletiyle verilir. Müşteri sürümü **ayrı bir kod bloğunda**, başlığın ve notun altında:

```markdown
[Büro antetli / profil yazı biçimi] Tarih: [GG.AA.YYYY]
Sayın [Müşteri yetkilisi],
Konu: [tek satır]

1. Olgular
[müşterinin bildirdiği ve incelediğimiz belgeler; belge listesi]

2. Soru
[tek cümle]

3. Dayanaklar
[kanun maddesi, tebliğ bölümü, varsa özelge — madde adı + kısa açıklama]

4. Değerlendirme
[hesap tablosu ya da gerekçe; sayılar ve dönemleri]

5. Sonuç
[ne yapılmalı, hangi tarihe kadar]

6. Varsayımlar ve sınırlar
[dayanılan olgular; olgu değişirse görüş değişir; [tarih] itibarıyla mevzuat;
 uyuşmazlık konusu ise avukata yönlendirme notu]

Saygılarımızla,
[Ad Soyad]
[Unvan — SM / SMMM / YMM], [Oda]
Oda sicil no: [___]
```

Sonra karar ağacı (ORTAK-KURALLAR.md §8): müşteri sürümünü düzelt · süreyi süre defterine ekle (`../../sure-takibi/SKILL.md`) · eksik olgu soru listesi · uyuşmazlıksa vergi becerisine devir.
