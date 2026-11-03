# Araştırma notu (memo): OSKUS düzeni

> Uyarlama: anthropics/claude-for-legal `legal-clinic/skills/memo` (Apache 2.0), değiştirilmiştir. ABD'deki IRAC (Issue-Rule-Application-Conclusion) yerine Türk hukuk eğitimi ve uygulamasında alışılmış **Olay / Sorun / Kural / Uygulama / Sonuç** düzeni kullanılır. "Work product" başlığı yerine ORTAK-KURALLAR.md §1'deki taslak başlığı gelir.

## Ne zaman

Araştırma planı uygulanmış ve kaynaklar toplanmış olmalıdır (`arastirma-plani.md`). Kullanıcı yalnızca plan istediyse not yazma. Kısa doktrin sorusunda da memo yazma (ORTAK-KURALLAR.md §9).

## Kip (SKILL.md Adım 0)

- **`taslak`:** Kural ve uygulama bölümleri doldurulur. Sonuç "öneri" olarak yazılır ve takdir gerektiren her satır `[incele]` alır.
- **`iskelet`:** Kural bölümünde yalnızca `[ARAŞTIRMA GEREKLİ: …]` blokları ve (varsa) `[ÇERÇEVE — doğrulanmadı]` başlangıç notu bulunur. Uygulama bölümünde önemli olgular ve sorular yer alır, sonuç bölümü boş kalır. Çıktının başına şunu yaz:
  > **Kip: iskelet.** Bu notun yapısını ve araştırma boşluklarını ben çıkardım. Kuralı kaynaktan siz yazacaksınız, uygulamayı ve sonucu da siz kuracaksınız. Bir bölümde takılırsanız o bölüm için örnek bir paragraf isteyebilirsiniz; önce sizin denemenizi görmek isterim.

## Yazım kuralları

1. **Sorun soru cümlesidir.** Her sorun ayrı bir blok olur.
2. **Kural yalnızca çekilmiş kaynaktan yazılır.**
   - Madde metnini çektiysen ilgili cümleyi alıntıla ve `markdown_citation`/`kaynak.markdown` ile `[soorgla]` etiketle.
   - Çekemediysen kuralı uydurma. `[ARAŞTIRMA GEREKLİ]` bloğu yaz.
   - Genel bir çerçeveyi bildiğinden eminsen (ör. "sözleşmeye aykırılıkta kusur karine olarak var sayılır") bunu **`[ÇERÇEVE — doğrulanmadı]`** diye ayrı bir satırda ver ve `[model bilgisi — doğrulayın]` ekle. Çerçeve satırı kuralın yerine geçmez.
3. **Kuralın kaynağını hiyerarşi içinde göster.** Önce kanun, sonra yönetmelik, sonra içtihat, sonra idari görüş. Alt norm üst normla çelişiyorsa bunu işaretle (ör. yönetmelik kanunun öngörmediği bir şekil şartı koyuyorsa) `[incele]`.
4. **İçtihat için alıntı-önerme kontrolü** (ORTAK-KURALLAR.md §7) yapılır. Önerme kararın **gerekçesinden** alınır. Şunlardan alınmaz: taraf iddiası, bozulan ilk derece gerekçesi, karşı oy, bilirkişi görüşü. Tam metnini okumadığın karar `[çekildi ama desteği doğrulayın]` etiketi alır.
5. **Uygulama, olguyu kurala bağlar.** Her önemli olgu için "bu olgu kuralın hangi unsurunu karşılıyor ya da karşılamıyor" sorusu cevaplanır. Eksik olgu `[OLGU GEREKLİ: …]` diye işaretlenir.
6. **Sonuç bir olasılık yargısıdır, kesinlik değildir.** "Güçlü / makul / zayıf" gibi bir derece ve gerekçesi yazılır. Takdir gerektiren her eşik `[incele]` alır.
7. **Çelişen içtihat** varsa kural bölümünde iki çizgiyi de göster ve `celisen-ictihat-ve-bosluklar.md` tablosunu ekle. Sessizce birini seçme.
8. **Alanlar arası soruda** her alt soruyu ilgili alan becerisinin kontrol listesiyle yürüt. Bölüm başlığına hangi beceri referansını kullandığını yaz (yalnızca gözden geçiren notunda; müvekkile gidecek sürümde bu yazılmaz).

## Şablon

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

> **⚠️ Gözden geçiren notu**
> - **Kaynaklar:** soorgla ✓ | soorgla bağlı değil — …
> - **Okunan:** [N madde; M kararın tam metni (künyeler); K kararın yalnızca özeti]
> - **Takdirinize bırakılan:** [N satır `[incele]`]
> - **Güncellik:** [madde tarihçesi: …; RG'de son değişiklik: …; İBK taraması: …]
> - **Güvenmeden önce:** [1-2 iş]
> - **Profil:** [var | yok — genel cevap] · **Kip:** [taslak | iskelet]

# Araştırma notu: [konu]

**Tarih:** [gg.aa.yyyy] · **Hazırlayan:** [profilden ya da boş] · **İçin:** [avukat / dosya kısa adı] · **Yargı yolu (tahmini):** [ ] `[incele]`

## Kısa cevap
[2-4 cümle: her sorunun kısa cevabı ve güven derecesi. İskelet kipinde: "Sonuç sizindir; aşağıdaki boşluklar kapanınca yazılacak."]

## Olay
[Notun dayandığı olgular, tarih sırasıyla. Kaynağı belirt: [kullanıcı verdi] / belge adı. Varsayımlar ayrı satırda: "Varsayım: … `[incele]`"]

## Sorunlar
1. [Soru cümlesi]
2. …

---

## Sorun 1: [soru]

### Kural
**Mevzuat**
- [markdown_citation] [soorgla]: "…ilgili cümle…"
- …

**İçtihat**
- [kaynak.markdown] [soorgla] — [kararın bu soruda dediği, tek cümle; tam metin okundu / yalnızca özet]
- …

**İdari görüş / kurul kararı** (varsa; bağlayıcılığı mahkeme kararından farklıdır)
- …

[ÇERÇEVE — doğrulanmadı] … [model bilgisi — doğrulayın]

[ARAŞTIRMA GEREKLİ: … — denenen: `araç(parametreler)` → sonuç yok / ilgisiz]

### Uygulama
| Olgu | Kural unsuru | Değerlendirme |
|---|---|---|
| … | … | lehe / aleyhe / belirsiz `[incele]` |

[İskelet kipinde tablo yerine:]
[UYGULAMA — siz yazın. Ele alınması gereken olgular:
 - …
 - Şu soruyu cevaplayın: …]

### Sonuç
[Taslak kipinde: öneri + derece + gerekçe, `[incele]`.]
[İskelet kipinde: SONUÇ — siz yazın: "Yukarıdaki kural ve uygulamaya göre olası sonuç ne? En zayıf halka hangisi?"]

---

[her sorun için tekrarla]

## Güçlü yanlar (olgulardan görünen; test edilmeli)
- …

## Zayıf yanlar
- …
- [BELİRSİZ: [X] gerçekten zayıflık mı? [Y] kuralına bağlı]

## Açık sorular
**Olgusal:** [müvekkile ya da karşı tarafa sorulacaklar]
**Hukuki:** [araştırılacaklar; aşağıdaki listeye de girer]
**Stratejik:** [avukatın karar vereceği konular: yol seçimi, zamanlama, maliyet]

## Çelişen içtihat
[varsa tablo (`celisen-ictihat-ve-bosluklar.md`), yoksa "Taramada çelişki görülmedi (taranan: …)"]

## Araştırma boşlukları (toplu liste)
1. [ARAŞTIRMA GEREKLİ: …] — önerilen araç ve sorgu
2. …

## Kaynakça
[Notta kullanılan bütün atıflar, etiketleriyle]

---
**Atıf doğrulaması gereklidir.** [soorgla] etiketi atfın bu oturumda araçtan döndüğünü gösterir; kararın neyi desteklediğini ve hâlâ geçerli olup olmadığını (sonraki İBK, kanun değişikliği, AYM iptali) okuyucu doğrular. [model bilgisi — doğrulayın] etiketli her atıf, kullanılmadan önce birincil kaynaktan kontrol edilmelidir.
```

Notun ardından "Kontrol listemde olmayan ama soracağım bir soru" satırı ve SKILL.md Adım 5'teki karar ağacı gelir.

## Müvekkile ya da karşı tarafa gidecek sürüm

Kullanıcı notu dışarı göndermek isterse ORTAK-KURALLAR.md §1'deki gönderim yeri kontrolünü uygula ve iki sürüm öner:

- **(a) İç not:** bu şablon.
- **(b) Dış metin:** iç anlatım, kip notu, "zayıf yanlar" ve "stratejik sorular" bölümleri çıkarılır; kaynak etiketleri dipnota alınır.

Sade dilde müvekkil mektubu istenirse `muvekkil-iletisimi` becerisine devret (yüklüyse).

## Bu not ne değildir

- Hukuki mütalaa değildir. Mütalaa avukatın imzasıyla verilir.
- Tamamlanmış bir araştırma değildir. `[ARAŞTIRMA GEREKLİ]` blokları kapanmadan nottaki sonuç geçici sayılır.
- İskelet kipinde boş bırakılan uygulama ve sonuç bölümleri silinecek yer tutucular değildir. Notun asıl değeri o bölümlerdedir.
