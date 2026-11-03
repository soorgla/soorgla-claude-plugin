# Vekâlet ücreti ve masraf bilgilendirmesi

Upstream'de doğrudan karşılığı yok (ABD'de ücret "engagement letter" ile ayrı yürür; `litigation-legal/oc-status` yalnız bütçe sorusunu içerir). Bu dosya Türk hukukuna göre yazılmıştır: Avukatlık Kanunu, Avukatlık Asgari Ücret Tarifesi (AAÜT), Harçlar Kanunu tarifesi ve HMK Gider Avansı Tarifesi.

**Bu dosya ücreti belirlemez.** Ücreti avukat belirler; bu dosya müvekkile **anlaşılır ve eksiksiz** anlatılmasını sağlar ve tarifenin altında ücret yazılmasına karşı uyarır.

---

## 1. Ne zaman kullanılır

- İş kabulünden önce ya da avukatlık sözleşmesiyle birlikte: "Bu dava bana kaça mal olur?"
- Dava sırasında yeni masraf: bilirkişi ücreti, keşif, ek gider avansı, kanun yolu harcı.
- Karardan sonra: kararda hükmedilen yargılama gideri ve karşı vekâlet ücreti; kimin ne ödeyeceği.
- Dönem sonu / iş sonu masraf dökümü ve hesap verme (TBK m.508 `[soorgla]`).

---

## 2. Kurallar `[soorgla]`

| Kural | Dayanak | Mektuba etkisi |
|---|---|---|
| Avukatlık sözleşmesi belli bir hukuki yardımı ve tutarı kapsamalıdır; yazılı olmayan anlaşma genel hükümlere göre ispatlanır | Av.K. m.163 | Ücret mektubunda yazılı sözleşme önerilir; sözlü anlaşmanın teyidi istenir |
| Dava değerinin en fazla %25'i ücret olarak kararlaştırılabilir; **AAÜT altında ücret kararlaştırılamaz**; ücretsiz dava baroya bildirilir | Av.K. m.164 | Tarifenin altında tutar yazılmaz; yazılırsa 🔴 |
| Kararla karşı tarafa yüklenen vekâlet ücreti **avukata aittir** | Av.K. m.164 son fıkra | Müvekkile "karşı taraftan alınacak vekâlet ücreti size değil avukata aittir" açıkça söylenir (sözleşmede aksi kararlaştırılabilirse avukat notunda `[incele]`) |
| AAÜT altında ücret kararlaştırılamaz; tarife altındaki akdi ücret tarife uyarınca kararlaştırılmış sayılır | AAÜT (42687) m.1/3 | Aynı |
| Tarife altında ücret belirlemek/tahsil etmek, iş temin etmek için yargılama ya da icra giderlerini üstlenmek kınama sebebidir | Av.K. m.135/2-n (7571) | "Masrafları biz karşılarız" teklifi yazılmaz; 🔴 |
| Masraf alıp dava açmamak ya da alınan masrafı iade etmemek kınama sebebidir | Av.K. m.135/2-r (7571) | Masraf avansı alındıysa harcama dökümü ve iade kaydı tutulur |
| Vekil, istem üzerine işin hesabını vermek ve vekâletle aldıklarını teslim etmekle yükümlüdür; gecikilen paranın faizini öder | TBK m.508 | Tahsil edilen paranın teslim tarihi mektupta yazılır |
| Yargılama giderleri aleyhine hüküm verilen tarafa yüklenir; kısmi haklılıkta oranlanır | HMK m.326 | "Kaybederseniz" senaryosu mektupta zorunlu |
| Davacı harç ve gider avansını dava açarken yatırır; yetersizse iki haftalık kesin süre verilir | HMK m.120 | Ek avans istemi geldiğinde süre ilk paragrafta |
| AAÜT'te sulh, kabul, feragat ve konusuz kalmada ücret; arabuluculuk aşamasında ücret | AAÜT m.6, m.16 | Sulh teklifinde "ücretiniz nasıl etkilenir" bilgisi |
| Ücret takdirinde hukuki yardımın tamamlandığı ya da hükmün verildiği tarihteki tarife esas alınır | AAÜT m.21 | Uzun davada tarifenin değişebileceği söylenir |

Av.K. m.164/4'teki "%10-20" takdir aralığı yalnız ücret kararlaştırılmamışsa ya da sözleşme geçersizse uygulanır; mektupta bu aralığı "ücretiniz" gibi sunma.

---

## 3. MCP adımları

1. **Güncel AAÜT'ü bul.** `legal_search_official_gazette` (`query: "Avukatlık Asgari Ücret Tarifesi"`, `search_in: "title"`, `sort_by: "date_desc"`), ardından aynı sorguyu `"Avukatlık Asgari Ücret Tarifesinde Değişiklik"` ile tekrarla. En yeni "Genel Hükümler" kaydının yürürlükte olup olmadığını ve sonrasında değişiklik yayımlanıp yayımlanmadığını yaz. Yeni tarife genellikle sonbaharda yayımlanır `[model bilgisi — doğrulayın]`; Ekim-Aralık arasında mektup yazılıyorsa bu kontrolü atlama.
2. **Genel hükmü çek.** `legal_list_statute_articles` (`law_no: "42687"`, `include_content: true`, gerekirse `article_no`) ya da `legal_get_statute_article`. `legal_resolve_statute` bu tarife için **eski yılları** döndürür; kullanma (bkz. SKILL.md "Bilinen eksikler").
3. **Tutar cetveli:** karşı vekâlet ücreti için `legal_calculate_attorney_fee` (`hukum_tarihi` olarak beklenen hüküm tarihi, yargı yeri, dava türü, kabul ve reddedilen miktar; kaybetme senaryosunda `reddedilen` = talep). Araç tarifenin asgarisini verir, hâkimin üç katına kadar artırabileceğini (m.3/1) `takdir_ust_siniri` alanıyla gösterir; mektupta "en az" diye yaz. Araç yanıt vermezse, hata dönerse ya da "yüklü değil" derse tutarı avukattan iste; `[kullanıcı verdi]`. Vermezse `[___ TL — güncel AAÜT ikinci kısım / üçüncü kısım]` yer tutucusu. Eski tarife tablosundan (semantik aramanın `yalniz_tablolar` sonuçları) tutar **alınmaz**.
4. **Harçlar:** `legal_calculate_court_fee` (`harc_turu`: `basvurma_asliye`, `basvurma_sulh`, `pesin_harc` + `deger`, `karar_ilam_nispi` + `deger`, …) ve `legal_get_social_parameters` (`harc_istinaf_bam`, `harc_temyiz_yargitay`, `harc_kesif`, `harc_arabuluculuk_karar`, `harc_basvurma_aym` …). İdari yargı harçları araçta yok → `[doğrula]`.
5. **Gider avansı ve tanık ücreti:** `legal_search_statute_semantic` (`sorgu: "gider avansı tarifesi"`, `mevzuat_tur: "teblig"`) → HMK Gider Avansı Tarifesi; tanık ücreti için HMK Tanık Ücret Tarifesi. Yıl kontrolü: dönen tarifenin yürürlük yılını RG aramasıyla teyit et. Bilirkişi ücreti tarifesi aranmadı `[doğrula]`.
6. **Faiz (alacak davası mektubunda):** `legal_get_legal_interest_rates` (`yasal_faiz`, `ticari_temerut`); hangi faizin uygulanacağı alan becerisinin değerlendirmesidir.
7. **Kesinlik ve kanun yolu sınırı:** `legal_get_social_parameters` (`istinaf_kesinlik_siniri`, `temyiz_siniri`) — "itiraz edebilir miyiz" sorusunda tutar sınırını müvekkile sade dille söylemek için.

---

## 4. Masraf bilgilendirme iskeleti (müvekkile)

Avukat notunda her tutarın kaynağı ve tarihi yazılır; müvekkil metninde etiket bulunmaz.

```
Konu: [Dava / iş] için tahmini masraf ve ücret bilgisi

Sayın [Ad Soyad],

[Dava / iş] için ödemeniz gerekebilecek tutarları aşağıda bir arada
görebilirsiniz. Tutarlar bugünkü tarifelere göredir; dava sürerken tarifeler
değişebilir ve mahkeme ek masraf (ör. bilirkişi ücreti) isteyebilir.

**1. Avukatlık ücreti**
[Avukatlık sözleşmemize göre: tutar / ödeme planı / başarıya bağlı kısım
(varsa ve en fazla dava değerinin dörtte biri olacak şekilde)]

**2. Dava açarken mahkemeye yatırılacaklar**
- Başvurma harcı: [tutar] TL
- Peşin harç: [tutar] TL [dava değeri üzerinden]
- Gider avansı (tebligat ve posta giderleri): [tutar] TL
- Toplam: yaklaşık [tutar] TL

**3. Dava sırasında çıkabilecek masraflar**
- Bilirkişi ücreti: mahkeme ister; tutarı mahkeme belirler.
- Keşif: [gerekirse] [tutar] TL harç + bilirkişi ve yol giderleri
- Tanık ücretleri: [gerekirse]
Bu masraflar için mahkeme süre verir; süresinde yatırılmazsa ilgili delil
dinlenmeyebilir. Bu nedenle böyle bir istem geldiğinde size hemen yazacağım.

**4. Dava sonunda**
- Davayı kazanırsanız: yatırdığınız harç ve masraflar karşı tarafa
  yükletilir; ancak tahsili ayrı bir aşamadır. Mahkemenin karşı tarafa
  yüklediği vekâlet ücreti kanun gereği avukata aittir.
- Davayı kaybederseniz: karşı tarafın masrafları ve avukatı için mahkemenin
  belirleyeceği vekâlet ücreti size yükletilebilir. Bugünkü tarifeye göre bu
  tutar en az [___] TL olabilir.
- Kısmen kazanırsanız: masraflar kazanılan ve kaybedilen orana göre
  paylaştırılır; reddedilen kısım için karşı tarafa vekâlet ücreti ödenebilir.

**5. Üst mahkemeye başvuru (istinaf/temyiz) gerekirse**
- Başvurma harcı ve karar harcı: [tutar] TL
- [Ek avukatlık ücreti — sözleşmemize göre]

Masraflar için yatırdığınız avansın dökümünü her [ay / aşama] sonunda size
göndereceğim; kullanılmayan kısmı iş bitince iade edilir.

Saygılarımla,
Av. [Ad Soyad]
```

**Avukat notunda zorunlu kontroller:**
- [ ] Yazılan avukatlık ücreti güncel AAÜT'ün altında mı? (`legal_calculate_attorney_fee` canlıysa onunla karşılaştır; değilse avukat teyidi) Altındaysa 🔴 Av.K. m.164/4 ve m.135/2-n.
- [ ] Başarı ücreti dava değerinin %25'ini aşıyor mu? Aşıyorsa 🔴 Av.K. m.164/2.
- [ ] "Masrafları biz karşılarız" ya da benzeri bir ifade var mı? Varsa 🔴 m.135/2-n.
- [ ] Kaybetme senaryosu (karşı vekâlet ücreti + yargılama gideri) yazıldı mı?
- [ ] Harç ve avans tutarları bu konuşmada araçtan mı geldi, tarihli mi?
- [ ] Müvekkil tüketici ya da işçi ise ve adli yardım / harçtan muafiyet / arabuluculukta ücret kuralı söz konusuysa alan becerisine bakıldı mı `[incele]`?

---

## 5. Masraf dökümü ve hesap verme

Müvekkil masraf avansı verdiyse iş sonunda ya da istendiğinde (TBK m.508) döküm:

| Tarih | Kalem | Tutar | Belge (makbuz/dekont) | Not |
|---|---|---|---|---|
| | Avans alındı | | | |
| | Başvurma + peşin harç | | UYAP makbuzu | |
| | Gider avansı | | | |
| | … | | | |
| | **Kalan / iade edilecek** | | | |

Döküm müvekkil verisidir; dosya klasörü etkinse `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/masraf-dokumu.md` altında tutulur (gizlilik notu SKILL.md). Muhasebe kaydının yerine geçmez; serbest meslek makbuzu ve vergi yönü `[doğrula]`, mali müşavire.

---

## 6. Sık hatalar

- Eski yılın tarife tablosundan tutar almak (semantik tablo araması eski tarifeleri getiriyor).
- "Karşı taraftan alınacak vekâlet ücreti size ödenecek" yazmak.
- Kaybetme senaryosunu yazmamak; müvekkil en çok bunu sonradan sorar.
- Harç tutarını yıl ve dönem belirtmeden yazmak.
- Ücreti "yaklaşık" bırakıp yazılı sözleşme önermemek.
