# Kötü haber verme ve "sonuç vaadi yok" kuralı

Uyarlama: Anthropic `legal-clinic/client-letter` ve `legal-clinic/status` "bu beceri kötü haberi şablonla vermez, gözetmene işaretler" kuralı ve `commercial-legal/stakeholder-summary` "sorun bulunduysa" bölümü (Apache 2.0). Upstream kötü haberi tamamen kapsam dışı bırakır; burada avukatın kararını devralmadan **taslak ve görüşme planı** hazırlanır.

---

## 1. Sonuç vaadi yasağı

### Dayanak `[soorgla]`

- **Av.K. m.34:** avukat görevini "özen, doğruluk ve onur içinde" yerine getirmek ve TBB meslek kurallarına uymakla yükümlüdür.
- **Av.K. m.55:** iş elde etmek için reklam sayılabilecek her türlü teşebbüs yasaktır.
- **TBB Reklam Yasağı Yönetmeliği m.4:** müvekkille ve müvekkil adayıyla görüşmenin içeriği reklam yasağını ihlal etmeyecek nitelikte olmalıdır.
- **Av.K. m.135 (7571 ile değişik):** reklam yasağını ihlal etmek kınama sebebidir; ayrıca mesleğiyle ilgili bir işten dolayı ısrarlı biçimde (çevrim içi mecralar dahil) kişilerle iletişim kurmaya çalışmak da kınama sebebi sayılmıştır.

TBB Meslek Kuralları'nın müvekkile güvence vermeye ilişkin hükümleri MCP katalogunda bulunamadı `[model bilgisi — doğrulayın]`; atıf gerekiyorsa yukarıdaki kanun ve yönetmelik maddeleri kullanılır.

Ayrıca: avukatın yükümlülüğü sonucu değil **özeni** borçlanmaktır; Yargıtay HGK avukatın özen borcunun genel vekâletten "çok daha ağır ve kapsamlı" olduğunu, özen borcuna aykırılığın haklı azil, ücret kaybı ve tazminat sonucu doğurabileceğini belirtir `[soorgla]`: [Yargıtay Hukuk Genel Kurulu, E. 2022/109, K. 2023/439, 10.05.2023](https://soorgla.com/karar/yargitay-hukuk-genel-kurulu-2023-439-karari) (gerekçe §20-25). Bu karar mektupta değil, avukat notunda gerekçe olarak kullanılır.

### Yasaklı ifadeler (taslakta bulunursa değiştir ve avukat notuna yaz)

| Yazma | Yerine |
|---|---|
| "Davayı kesin kazanırız / garanti" | "Elimizdeki belgeler iddianızı destekliyor; sonucu mahkeme verecek." |
| "%80 ihtimalle", "büyük ihtimalle kazanırız" | Olasılık yüzdesi yazılmaz. Güçlü ve zayıf yanlar ayrı ayrı yazılır (görüşmede). |
| "En geç 6 ayda biter" | "Bu tür davalar çoğu zaman [aşamalar]dan geçer; kesin süre söylemek mümkün değil." Süre aralığı yalnız avukat verirse ve "tahmin" diye. |
| "Paranızı alacağız" | "Karar lehinize çıkarsa tahsil için [icra] aşaması gerekir; karşı tarafın ödeme gücü sonucu etkiler." |
| "Hâkimi tanıyorum / bu mahkeme bizden yana" | Hiçbir biçimde yazılmaz. Taslakta kullanıcı istese bile yazılmaz; avukat notuna "meslek kuralı" işareti. |
| "Diğer avukat hata yapmış" | Önceki avukat hakkında değerlendirme yazılmaz; olgu yazılır ("[tarih]'te süre dolmuş görünüyor `[incele]`"). Av.K. m.135/1-f meslektaşı küçük düşürücü ifadeyi uyarma sebebi sayar `[soorgla]`. |
| "Hiç masrafınız olmaz" | Masraf kalemleri ve kaybetme halinde karşı vekâlet ücreti riski yazılır (`ucret-ve-masraf-bilgilendirmesi.md`). |
| "Merak etmeyin" | "Bir sonraki adım şu; size [tarih]'te yazacağım." |

İlk görüşme, teklif ve sosyal medya metinleri (müvekkil adayına) bu listeyle ayrıca taranır: "başarı oranımız", "X dava kazandık", "en iyi" ifadeleri reklam yasağı riski taşır `[incele]`.

---

## 2. Kötü haber: önce konuşma, sonra yazı

**Kural:** aleyhe karar, ret, süre kaçırma, büyük masraf çıkması, dosyayı bırakma gibi haberler **ilk kez yazıyla verilmez.** Önce telefon ya da yüz yüze görüşme; ardından aynı gün ya da ertesi gün yazılı teyit. Taslak iki parça üretir:

1. **Görüşme planı** (avukat için, müvekkile gitmez)
2. **Görüşme sonrası yazılı teyit** (müvekkile)

Müvekkile ulaşılamıyorsa ve süre işliyorsa yazı beklemez: yazılı bildirim + "sizi aradım, ulaşamadım" cümlesi + süre ilk paragrafta.

### 2.1 Görüşme planı (avukat notu)

```markdown
### Görüşme planı — [konu] — [tarih]

1. **Haberin özü (ilk 30 saniye):** [tek cümle — ör. "Mahkeme davayı reddetti."]
2. **Neden (kısa, suçlamasız):** [mahkemenin gerekçesi, iki cümle; gerekçeli karar
   yoksa "gerekçeyi henüz görmedik"]
3. **Şimdi ne olabilir (seçenekler):** [istinaf / temyiz / yeni dava / sulh /
   hiçbir şey yapmamak — her biri için süre, masraf, olası sonuç aralığı;
   ALAN BECERİSİNDEN gelir; yoksa `[incele]`]
4. **Müvekkilin vermesi gereken karar ve son günü:** [___]
5. **Masraf ve risk:** [karşı vekâlet ücreti ve yargılama gideri yüklenmiş mi;
   tutar karardan; kanun yolu harcı `legal_get_social_parameters`]
6. **Sorulabilecek zor sorular ve dürüst cevaplar:**
   - "Hata sizde mi?" → [olgu; savunma ya da itiraf değil; büro sorumluluk
     sigortası/ortağa yükseltme gerekiyorsa `[incele]`]
   - "Kazanma ihtimalimiz ne?" → yüzde verme; güçlü ve zayıf yanlar
   - "Ücreti geri alabilir miyim?" → avukatlık sözleşmesine bak; ortağa yükselt
7. **Görüşmeden sonra:** yazılı teyit (aşağıda) + günlük kaydı (F kipi)
```

### 2.2 Yazılı teyit iskeleti

```
Konu: [Mahkeme] [Esas no] — bugünkü görüşmemizin özeti ve karar vermeniz gereken konu

Sayın [Ad Soyad],

Bugün telefonda konuştuğumuz gibi, [mahkeme] [tarih] tarihinde [kararın sade
özeti — ör. "davanızı reddetti"]. Bu sonucun sizin için ne kadar üzücü
olduğunu biliyorum.

**Karar vermeniz gereken konu ve son gün**
[Karara itiraz (istinaf) etmek isterseniz, başvurunun en geç
**[gün ay yıl, gün adı]** günü yapılması gerekiyor. Bu tarihten sonra itiraz
hakkı kaybedilir.]
Kararınızı bana en geç **[gün ay yıl — son günden birkaç iş günü önce]** bildirmenizi rica ederim.

**Seçenekler**
1. [Seçenek] — [ne demek] — [yaklaşık masraf] — [olası sonuç, vaatsiz]
2. [Seçenek] — …
3. Bir şey yapmamak — [karar kesinleşir; şu sonuçları olur: …]

**Masraf durumu**
[Kararda size yüklenen yargılama gideri ve karşı taraf vekâlet ücreti: [tutar,
karardan]. Bunun ödenmesi gerekip gerekmediğini ve ne zaman gerektiğini
[ayrıca konuşalım / şöyle].]

Hangi yolu seçerseniz seçin, kararınızı birlikte vermek isterim. Sorularınız
için [iletişim].

Saygılarımla,
Av. [Ad Soyad]
```

---

## 3. Özel durumlar

### 3.1 Süre kaçırıldı (büro hatası olabilir)

- Taslak **hata kabulü ya da inkâr içermez**; olguyu yazar. Bu durum avukatın mesleki sorumluluğunu ilgilendirir (Av.K. m.135/2-m: özen yükümlülüğünü ihlal ederek hak kaybına sebebiyet verme kınama sebebidir `[soorgla]`).
- Avukat notunun en üstüne 🔴 ve "**Ortağa / sorumlu avukata yükselt; mesleki sorumluluk sigortasına bildirim gerekip gerekmediğini kontrol edin `[incele]`.**" Eski hâle getirme gibi kurtarma yolu varsa ilgili dilekçe becerisine işaret et (`hukuk-yargilamasi-dilekce`), ama mektuba "kurtarırız" yazma.
- Müvekkile yazılı metin avukat bunu açıkça onaylamadan hazırlanmaz; yalnız görüşme planı üretilir.

### 3.2 Dosyayı bırakma / istifa

- Av.K. m.135/2-f işin reddi zorunluluğunu ya da işi sonuna kadar takip yükümlülüğünü ihlali kınama sebebi sayar `[soorgla]`. İstifanın süresi, bildirimi ve ücrete etkisi `[model bilgisi — doğrulayın: Av.K. m.41 ve m.174]`.
- Mektup: istifanın tarihi, işleyen süreler (yeni avukata kadar müvekkilin kendisinin izlemesi gereken), evrak teslimi (Av.K. m.39 evrak saklama `[soorgla]`), yeni avukata devir bilgisi. Neden kısmı kısa ve suçlamasız.

### 3.3 Beklenenden düşük tutar / kısmi kabul

Kısmi kabulde yargılama giderleri haklılık oranına göre paylaştırılır (HMK m.326/2 `[soorgla]`). Mektup "kısmen kazandık" demez; **kabul edilen ve reddedilen** kısmı ve reddedilen kısım için karşı tarafa ödenecek vekâlet ücretini ayrı yazar.

### 3.4 Ceza dosyası

Tutuklama, mahkûmiyet, HAGB gibi haberlerde müvekkil çoğu zaman tutukludur ya da yakını aracılığıyla bilgi alır. Yakınına bilgi vermek için müvekkilin açık izni gerekir (Av.K. m.36 `[soorgla]`); izin yoksa yakına yalnız "avukat olarak görüştüm, kendisi size bilgi verecek" düzeyinde yaz. Esas değerlendirmesi `ceza-hukuku-suclar`.

---

## 4. Sık hatalar

- Kötü haberi ilk kez e-postayla vermek.
- Seçenekleri sunmadan "itiraz edelim mi?" diye sormak; müvekkil neyi seçtiğini bilmez.
- Karar için son günü kanun yolu süresinin son günü olarak vermek; müvekkile dilekçeyi hazırlayacak zaman bırakan daha erken bir tarih ver.
- Teselli cümlelerini çoğaltıp kararı ve son günü geri plana itmek.
- "Hâkim hatalı" gibi kişisel yorum; yerine gerekçedeki somut sorunu yaz.
