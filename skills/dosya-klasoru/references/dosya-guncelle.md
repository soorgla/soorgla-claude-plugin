# Dosyayı güncelleme (`guncelle`)

Kaynak: upstream `litigation-legal/matter-update`. Türk usulüne uyarlandı: olay türleri (tebligat, ara karar, bilirkişi raporu, ıslah, sulh teklifi) yeniden yazıldı; "settlement acceptance" kapısı HMK m.74 özel yetki kontrolü ve ORTAK-KURALLAR.md §1 "taslaktır" kapısıyla birleştirildi; "materiality" tetikleyicisi yalnız şirket içi kullanıcı için isteğe bağlı bırakıldı.

Amaç: güncellemeyi ucuz tutmak. İki dakikalık yapılandırılmış kayıt; serbest anlatıya kayma yok.

---

## 0. Kapı

- `_liste.yaml`'da kısa ad yoksa **reddet ve yönlendir**: "`<kisa-ad>` dizinde yok. Önce `ac` ile açalım; çıkar çatışması kontrolü açılışta yapılıyor ve günlük o zaman oluşuyor. Açılmamış bir dosyaya günlük eklemem."
- Kısa ad verilmediyse etkin dosyayı öner; o da yoksa son güncellenen birkaç dosyayı yalnız dizinden listele.
- Satırda `cikar_catismasi.durum` `bekliyor` ya da `yapilmadi` ise ya da `atlama` doluysa her güncellemede ilk satırda hatırlat.

## 1. Olay türü

| Tür | Örnekler | Genelde etkilediği alanlar |
|---|---|---|
| Tebligat | dava dilekçesi, cevap, gerekçeli karar, ödeme emri, bilirkişi raporu, ihtarname tebliği | `sureler`, `durum` |
| Usul | duruşma yapıldı / ertelendi, ara karar, kesin süre verildi, birleştirme, görevsizlik, dosya işlemden kaldırıldı | `sonraki_durusma`, `sureler`, `durum` |
| Delil | tanık dinlendi, keşif, bilirkişi raporu geldi, belge celbi | Belgeler tablosu, `sureler` (rapora itiraz) |
| Esasa ilişkin | yeni olgu, kilit belge bulundu, ıslah, karşı dava | Olay özeti (yalnız ek not), risk |
| Strateji | sulh / arabuluculuk teklifi geldi ya da yapıldı, feragat, kabul düşünülüyor | risk, `durum` (bkz. §3) |
| Karar | ilk derece / BAM / Yargıtay kararı | `durum`, merci tablosu, `sureler` (kanun yolu) |
| Risk yeniden değerlendirme | olasılık ya da etki değişti | `risk` |
| Paydaş | karşı taraf vekili değişti, ekibe biri girdi, vekaletten azil/istifa | Taraflar, `sorumlu` (istifa/azil → `dosya-kapat.md` §2) |
| İdari | ücret sözleşmesi imzalandı, vekaletname yenilendi, masraf avansı yatırıldı | Vekaletname bölümü |

Uymuyorsa serbest tür.

## 2. Tarih, özet, alanlar

- Tarih: varsayılan bugün; kullanıcı geçmiş bir olayı giriyorsa o tarih. Tebligatta **tebliğ tarihi** ile öğrenme tarihini ayır; süre tebliğden işler.
- Özet: tek paragraf, kullanıcının anlattığı. Yorum eklenecekse `[incele]`.
- Yalnız olay türünün etkilediği alanları sor (yukarıdaki tablo). Usul güncellemesi genelde yalnız `sonraki_durusma` ve `sureler`'e dokunur; her alanı tek tek sorma.

## 3. Sulh, feragat, kabul, ibra kapısı

Olay **kabul edilecek** bir sulh, feragat, davayı kabul, ibra ya da arabuluculukta anlaşma ise (teklifin gelmesi ya da yapılması değil, kabulü):

1. **Yetki:** kartın vekaletname bölümüne bak. HMK m.74 bu işlemleri açık yetkiye bağlar `[soorgla]`. Yetki "yok" ya da "kontrol edilmedi" ise 🟠 işaretle: "Vekaletnamede özel yetki görünmüyor; müvekkilin kendi imzası ya da yeni vekaletname gerekebilir `[incele]`."
2. **Rol:** kullanıcı avukat değilse ORTAK-KURALLAR.md §1 kapısı: "Bunu bir avukatla gözden geçirdiniz mi?" Hayırsa avukata götürülecek bir sayfalık özet (dosya, önerilen koşullar, karşılığında vazgeçilen talepler, masraf ve vekalet ücreti, gizlilik ve ibra kapsamı, sonrası için sorulacaklar) ver; kabulü günlüğe **yazma**. Teklif kaydı kapı gerektirmez.
3. **Esas:** sulh metninin değerlendirmesi alan becerisinin işidir (ör. ibra geçerliliği → `is-hukuku`); burada yalnız kayıt tutulur.

## 4. Süre değişince

Yeni bir süre doğduysa (tebligat, kesin süre, ara karar, karar):

1. `sure-takibi` yüklüyse ona devret: olay, olay tarihi, dosyanın türü (hukuk / ceza / idari / icra), adli tatile tabi olup olmadığı.
2. Yüklü değilse geçici yol:
   - Kanun yolu ve İİK şikâyeti: `legal_calculate_deadline` (`hmk_appeal`, `hmk_cassation`, `cmk_appeal`, `iik_complaint`). Araç tebliğ gününü saymaz, son günün tatil olup olmadığını ve adli tatil etkisini ayrıca bildirir.
   - Araç 01.11.2026'dan beri İYUK dava süresi (`iyuk_lawsuit`), ödeme emrine itiraz (`iik_objection_payment_order`) gibi ~70 kodu tanır; bilinmeyen kodda geçerli kod listesini döndürür. Cevap, bilirkişi raporuna itiraz ve kesin süre için kod **yok**. Süreyi madde metninden çek (`legal_get_statute_article`), elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle.
   - **Adli tatil:** `legal_check_holiday` adli tatil günlerini `tatil: true` olarak döndürüyor (ör. 2027-07-20 → "Adli Tatil 2027 / Mali Tatil 2027"). Adli tatil günü iş günüdür; süre ertelenmez, yalnız adli tatile tabi işlerde son gün tatile rastlarsa HMK m.104'e göre uzar. Bu yüzden `tatil: true` ile birlikte `tatil_turu` `adli`/`mali_tatil` gelirse son günü kaydırma; HMK m.102-104'ü çek ve dosyanın adli tatile tabi olup olmadığını `[incele]` ile sor.
3. Yeni süreyi **hem** kartın "Kritik süreler" tablosuna **hem** `_liste.yaml`'daki `sureler` listesine yaz; yapılan ya da kaçan süreyi `durum` alanında işaretle (silme).
4. Son güne 7 günden az kaldıysa ya da geçtiyse onay mesajının ilk satırında 🔴.

## 5. Risk ve yeniden değerlendirme tetikleyicisi

Şu olay türlerinde **her zaman** sor ve cevabı açıkça kaydet ("değişmedi" de bir cevaptır, sessizlik değildir):

| Olay | Soru |
|---|---|
| Esasa ilişkin yeni olgu, bilirkişi raporu | "Risk şu an [🟡]. Bu gelişme değiştiriyor mu?" |
| Karar | "Kanun yoluna gidilecek mi? Risk ve durum ne olsun?" |
| Sulh / arabuluculuk teklifi | "Teklif riski ya da durumu değiştiriyor mu?" |
| (Şirket içi) dava karşılığı ayrılmış dosyada esaslı gelişme | "Finans birimine bildirilecek bir değişiklik var mı? `[incele]`" |

Günlük girişine ekle:

```markdown
**Risk kontrolü:** [değişmedi | X → Y]
**Gerekçe:** [tek cümle]
```

Önem derecesi gerekçe yazılmadan düşürülmez (ORTAK-KURALLAR.md §8).

## 6. Belge

Olay bir belgeye dayanıyorsa (ara karar, bilirkişi raporu, tebligat mazbatası) belge tablosuna yeni satır öner (B-no, tarih, kaynak, konum). Belgenin metnini karta kopyalama. Uzun belgeyse ve kullanıcı içeriğin incelenmesini istiyorsa ilgili alan becerisine ya da `tablolu-belge-incelemesi` becerisine (yüklüyse) yönlendir.

## 7. Yazma ve onay

Günlük girişini (`sablonlar.md` §2 biçimi, en üste) ve `dosya.md` / `_liste.yaml` farkını göster:

> "Şunu ekleyeceğim ve şunları güncelleyeceğim; onaylıyor musunuz?"

Onaydan sonra: girişi ekle, kartta değişen alanları güncelle, dizinde `son_guncelleme`'yi bugüne çek. Geçmiş girişleri değiştirme; düzeltme yeni bir giriştir ("[AAAA-AA-GG] tarihli girişteki tebliğ tarihi yanlış yazılmıştı; doğrusu …").

## Bu adım ne yapmaz

- Gelişmenin hukuki sonucunu değerlendirmez (alan becerisi).
- Alanları kullanıcıya göstermeden değiştirmez.
- Sulh ya da feragati "kabul edildi" diye yetki ve rol kapısından geçmeden kaydetmez.
