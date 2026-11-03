# Dosyayı kapatma (`kapat`)

Kaynak: upstream `litigation-legal/matter-close` ve `matter-workspace close`. Türk hukukuna uyarlandı: sonuç türleri HMK/CMK/İİK karşılıklarıyla yazıldı; kesinleşme kapısı, vekaletten istifa (HMK m.82), evrak saklama ve hapis hakkı (Av.K. m.39) ve KVKK m.7 silme hatırlatması eklendi; "reserve accuracy" yalnız şirket içi kullanıcıda isteğe bağlı.

Amaç: sonucu yapılandırılmış biçimde kaydetmek (gelecekteki risk değerlendirmeleri için en değerli veri budur) ve dosyayı silmeden etkin portföyden çıkarmak.

---

## 0. Kapı

- `_liste.yaml`'da kısa ad yoksa: "`<kisa-ad>` dizinde yok; kapatılacak bir şey bulamadım. Kısa adı kontrol edelim."
- Kullanıcı avukat değilse ORTAK-KURALLAR.md §1 kapısı: "Kapatmak takibi bitirir; açık bir kanun yolu, icra ya da masraf alacağı varsa kaçabilir. Bunu bir avukatla gözden geçirdiniz mi?" Hayırsa avukata götürülecek bir sayfalık özet (sonuç, kesinleşme durumu, açık süreler, bağlı dosyalar, sorulacaklar) ver; kapanış alanlarını yazma.

## 1. Kesinleşme kapısı

Bir karar sonucu kapanıyorsa önce **kesinleşmiş mi** sor:

- UYAP'ta kesinleşme şerhi var mı? Varsa tarihini al `[kullanıcı verdi]`.
- Yoksa kanun yolu süresini `legal_calculate_deadline` ile hesapla (`hmk_appeal`, `hmk_cassation`, `cmk_appeal`); tebliğ tarihi her taraf için ayrıdır, karşı tarafın tebliğini bilmiyorsan süre "bilinmiyor" kalır. İdari yargı, icra itirazı gibi araç kodu olmayan yollarda madde metninden elle hesapla `[doğrula]`.
- Süre açıksa ya da karşı tarafın kanun yoluna gidip gitmediği bilinmiyorsa kapatma; durumu `beklemede` yap ve kesinleşme kontrolü için `sureler`'e bir satır ekle. Kullanıcı yine de kapatmak isterse gerekçeyi günlüğe yaz.
- Karar kesinleşti ama **icra** gerekiyorsa (alacak, vekalet ücreti, yargılama gideri): kapatmak yerine yeni bir icra dosyası açmayı öner (`ac`, `icra-iflas` alan becerisi); iki dosyayı "İlgili dosyalar"da birbirine bağla.

## 2. Vekaletin sona ermesi (azil, istifa)

- **İstifa:** istifa eden vekilin görevi, istifanın müvekkile tebliğinden itibaren HMK m.82'deki süre boyunca devam eder; istifa dilekçesiyle birlikte müvekkile ihtar yapılır `[soorgla]`. Süreyi madde metninden yaz, son günü karta ekle; o güne kadar dosya kapanmaz, `durum: beklemede`.
- **Azil:** azlin mahkemeye bildirilmesi ve yeni vekil atanana kadar yükümlülükler `[model bilgisi — doğrulayın]` (HMK m.81). Dosyayı kapatmadan önce açık sürelerin müvekkile ya da yeni vekile yazılı bildirildiğini kaydet.
- Her iki hâlde de dosyanın devri için kısa bir **devir notu** öner (açık süreler, son duruşma, belgelerin yeri); metni `muvekkil-iletisimi` (yüklüyse) kurar.

## 3. Sonuç bilgileri

**Sonuç türü** (birini seç, gerekirse açıkla):

| Hukuk / idari | Ceza | İcra / diğer |
|---|---|---|
| kabul · kısmen kabul · ret · sulh · feragat · davanın kabulü (karşı taraf) · konusuz kalma · açılmamış sayılma / işlemden kaldırma · görevsizlik-yetkisizlik ile gönderme · birleştirme (hangi dosyaya) · arabuluculukta anlaşma · arabuluculukta anlaşamama (dava açılmadı) | beraat · mahkûmiyet · HAGB · düşme · KYOK · uzlaşma · durma | tahsil · aciz belgesi · takipten vazgeçme · danışmanlık tamamlandı · vekaletten istifa/azil |

- **Sonuç tarihi:** karar, sulh tutanağı ya da kesinleşme tarihi (hangisi olduğunu yaz).
- **Parasal sonuç:** hüküm altına alınan / ödenen / tahsil edilen tutar, yargılama gideri ve vekalet ücreti — kullanıcının verdiği gibi `[kullanıcı verdi]`; beceri hesaplamaz.
- **Açılıştaki tahminle kıyas:** açılıştaki risk ve tez ne demişti, ne oldu?
- (Şirket içi, isteğe bağlı) ayrılan karşılık ile gerçekleşen tutar.
- **Dersler:** iki üç cümle, dürüst. "Bilirkişi raporuna itirazı geç hazırladık" türü bir cümle, "olumlu sonuçlandı"dan değerlidir. Kullanıcı ders yazmazsa alan boş kalır; beceri ders uydurmaz.
- **İlgili belge:** karar, sulh tutanağı, kesinleşme şerhi (B-no ya da yol).

## 4. Saklama, iade ve kişisel veri

1. **Evrak saklama süresi:** `legal_get_statute_article` (`law_no: "1136"`, `article_no: "39"`) çağır; süreyi metinden al ve `saklama_bitis` alanına vekaletin sona erdiği tarihten hesaplanmış günü yaz. Madde, evrakın geri alınmasının müvekkile yazıyla bildirildiği hâlde daha kısa bir sürenin işlediğini ve ücret ile gider ödenmedikçe avukatın evrakı geri vermekle yükümlü olmadığını (hapis hakkı) da düzenler `[soorgla]`. Hangi sürenin işlediği (yazılı bildirim yapıldı mı) `[incele]`.
2. **Asıl belgelerin iadesi:** müvekkile ait asıl belgeler varsa iade edilip edilmediğini sor; "Yapılacaklar"a madde olarak ekle.
3. **KVKK:** işlenmesini gerektiren sebep ortadan kalkınca kişisel veriler silinir, yok edilir ya da anonim hâle getirilir; diğer kanunlardaki saklama hükümleri saklıdır (KVKK m.7) `[soorgla]`. Yani Av.K. m.39 süresi ve büronun kendi saklama politikası dolunca bu klasörün de silinmesi ya da anonimleştirilmesi gündeme gelir. Beceri bunu **hatırlatır**, kendiliğinden silmez (§5).
4. Hapis hakkı ya da masraf alacağı varsa kapanış özetine 🟠 ile yaz.

## 5. Yazma ve taşıma

Önce bütün kapanış girişini ve dizin farkını göster; açık onaydan sonra:

1. `_gunluk.md` en üstüne:

```markdown
## [AAAA-AA-GG] — Dosya kapandı: [sonuç türü]

**Sonuç:** [anlatı: ne oldu, hangi koşullarla]
**Kesinleşme:** [tarih ve dayanak | beklemede değil]
**Parasal sonuç:** [tutarlar `[kullanıcı verdi]`]
**Açılıştaki tahminle kıyas:** [___]
**Dersler:** [kullanıcının yazdığı | boş]
**Saklama:** Av.K. m.39'a göre [AAAA-AA-GG]'ye kadar · iade: [yapıldı | bekliyor]
**İlgili belge:** [___]
```

2. `dosya.md` sonundaki "Kapanış" bölümüne tek paragraflık özet ve günlük girişine işaret (önceki bölümlere dokunma; açılış kaydı tarihtir).
3. `_liste.yaml` satırında: `durum: kapali`, `kapanis`, `sonuc`, `saklama_bitis`, `son_guncelleme`. **Satırı silme.**
4. Klasörü `dosyalar/<kisa-ad>/` → `dosyalar/_kapali/<kisa-ad>/` taşı; dizindeki `yol`'u güncelle.
5. Kapanan dosya etkin dosyaysa profilde `Etkin dosya: yok — genel bağlam`.

**Silme ve anonimleştirme** ayrı ve açık bir talimatla yapılır ("`<kisa-ad>` klasörünü sil" / "anonimleştir"). O zaman: saklama süresi dolmuş mu, iade yapılmış mı, bağlı açık dosya var mı kontrol et; silinecekleri listele; tekrar onay al; dizin satırını `durum: silindi`, tarih ve "kim talimat verdi" bilgisiyle bırak (ad yerine kod). Yerel yedekler ve bulut eşitlemesi beceri tarafından silinemez; bunu kullanıcıya söyle.

## 6. Yeniden açma

Kapanmış bir dosya geri gelirse (yargılamanın iadesi, yeni bir icra, bağlantılı dava) eski dosyayı açma; yeni bir dosya aç ve "İlgili dosyalar"a eskisini yaz. Eski dosyanın içeriğini okumak dosyalar arası bağlam kuralına tabidir (`gizlilik-ve-istemciler.md` §1); aynı müvekkilin önceki dosyası olması tek başına izin değildir, kullanıcı açıkça isterse okunur.

## Bu adım ne yapmaz

- Dosyayı silmez; kapatma arşivlemedir.
- Kesinleşmeyi varsaymaz.
- Ders ya da sonuç uydurmaz.
