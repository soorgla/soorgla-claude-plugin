# Veri işleme sözleşmesi (veri sorumlusu – veri işleyen)

## Ne zaman kullanılır
- Müşteri kendi veri işleme sözleşmesini (DPA, "veri işleyen taahhütnamesi", "KVKK eki") gönderdi; ya da siz tedarikçinize (bulut, bordro, çağrı merkezi, kargo, yazılım) DPA gönderiyorsunuz.
- Hizmet sözleşmesinin içindeki kişisel veri maddeleri inceleniyor. Sözleşmenin geri kalanı (ücret, sorumluluk sınırı, fesih, yetki) → `../../sozlesme-incelemesi-tbk/SKILL.md`.

KVKK'da GDPR m.28 gibi ayrıntılı bir "veri işleyen sözleşmesi" maddesi **yoktur**. Dayanak, veri sorumlusunun veri işleyenle birlikte güvenlik tedbirlerinden **müştereken sorumlu** olması ve veri işleyenin sır saklama/amaç dışı kullanmama yükümlülüğüdür. Sözleşme bu sorumluluğu iç ilişkide düzenler; ilgili kişiye ve Kurula karşı sorumluluğu ortadan kaldırmaz.

---

## Önce: yön hangisi?

- **Siz veri işleyensiniz** (müşterinin DPA'sı): operasyonel esnekliğinizi korursunuz — savunma incelemesi.
- **Siz veri sorumlususunuz** (tedarikçinin DPA'sı ya da sizin şablonunuz): veriyi ve ilgili kişiyi korursunuz — koruma incelemesi.
- Belirsizse sor; rol yanlışsa her öneri tersine döner. Rol tanımları için m.3/1-(ğ) "veri işleyen" ve (ı) "veri sorumlusu" metnini çek; taraf amaç ve vasıtaları kendisi belirliyorsa sözleşmede "veri işleyen" yazsa da veri sorumlusudur `[incele]`.

**Önceki işler:** aynı karşı taraf ya da faaliyet için daha önce ön inceleme (`on-inceleme-ve-etki-degerlendirmesi.md`) ya da DPA incelemesi yapıldıysa önce onu oku; önem derecesi taban olarak taşınır, gerekçesiz düşürülmez (ORTAK-KURALLAR.md §8). Yoksa "önceki inceleme yok" yaz.

---

## Süreler ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| İhlalin Kurula ve ilgilisine bildirimi | "En kısa sürede" — sözleşmede veri işleyenin veri sorumlusuna bildirim süresi bundan **kısa** olmalı | 6698 m.12/5; Kurul 24.01.2019 t. 2019/10 s. kararı: Kurula öğrenmeden itibaren **72 saat** |
| İlgili kişi başvurusu | Veri sorumlusu 30 günde cevaplar; veri işleyenin iletme ve destek süresi bunun içinde kalmalı | 6698 m.13/2 |
| Kurulun bilgi-belge talebi | 15 gün — veri işleyenin destek yükümlülüğü sözleşmede olmalı | 6698 m.15/3 |
| Yurt dışı standart sözleşme bildirimi | İmzaların tamamlanmasından itibaren 5 iş günü | 6698 m.9/5; Yönetmelik m.14/5 → `yurt-disi-aktarim.md` |

---

## Kontrol listesi — her DPA'da

| Madde | Aranan | Sık kavga |
|---|---|---|
| **Roller** | Veri sorumlusu/işleyen açıkça ve gerçeğe uygun belirlenmiş | Karşı tarafın kendini "bağımsız veri sorumlusu" yazıp veriyi kendi amaçlarına kullanması |
| **Kapsam ve talimat** | Veri kategorileri, ilgili kişi grupları, amaç, süre; yalnız yazılı talimatla işleme | "ve ilgili diğer amaçlar" gibi genişletici ifadeler |
| **Amaç dışı kullanım yasağı** | Ürün geliştirme, yapay zekâ eğitimi, istatistik için kullanım yasak ya da açıkça sınırlı | "Hizmetin iyileştirilmesi" adı altında eğitim verisi |
| **Gizlilik** | Personelin gizlilik yükümlülüğü; görev sona erince de sürer | — |
| **Güvenlik tedbirleri** | Somut teknik ve idari tedbirler eki (erişim yetkisi, loglama, şifreleme, yedek) | "Uygun tedbirler alınır" deyip ek koymamak = boş taahhüt |
| **Alt işleyen** | Güncel liste, değişiklikte önceden bildirim ve itiraz/fesih; aynı yükümlülüklerin alt işleyene aktarılması | Toptan onay / her değişiklikte veto |
| **İhlal bildirimi** | Tetikleyici ("öğrenme" mi "teyit" mi), süre, içerik, iş birliği | "Gecikmeksizin" gibi ölçüsüz ifade |
| **Denetim** | Bağımsız denetim raporu / yerinde denetim, bildirim süresi, maliyet | Kısa ihbarla yerinde denetim (işleyen için ağır) |
| **İlgili kişi başvurularına destek** | Başvuru işleyene gelirse süre içinde iletme | İşleyenin doğrudan cevap vermesi |
| **Yurt dışı aktarım** | Veri ya da alt işleyen yurt dışındaysa m.9 dayanağı (yeterlilik kararı / standart sözleşme / BCR…) | Dayanak hiç yok → 🔴 → `yurt-disi-aktarim.md` |
| **Sona erme** | İade ya da silme/yok etme, süre, imha tutanağı, yedekler için açık istisna | "Makul sürede silinir" |
| **Sorumluluk** | Veri ihlali sorumluluğunun genel sınırın içinde mi dışında mı olduğu; rücu | Sınırsız veri sorumluluğu (işleyen için varlık riski) |
| **Kurul işlemleri** | Kurul incelemesinde belge ve bilgi desteği; m.18 cezasının iç ilişkide paylaşımı `[incele]` | — |

### Veri işleyen olduğunuzda (savunma)
Müşterinin istediği, profildeki standart pozisyonun dışındaysa standart pozisyonu öner, kabul edilebilir yedek pozisyona hazır ol. Profilde DPA oyun kitabı yoksa: "profil yok — genel öneriler" yaz ve kullanıcıya standart/yedek/asla pozisyonlarını sor.

### Veri sorumlusu olduğunuzda (koruma)
Tedarikçinin taslağında alt işleyen listesi, güvenlik eki, ihlal süresi, denetim hakkı, amaç dışı kullanım yasağı, yurt dışı dayanağı ve silme taahhüdü yoksa her birini talep et.

### Aydınlatma metniyle tutarlılık (upstream dpa-review'dan)
DPA'daki amaçlar ve alıcılar aydınlatma metninde ve VERBİS kaydında var mı? Aydınlatma "yurt dışına aktarım yoktur" diyor ama tedarikçi yurt dışındaysa → aydınlatma ya da tedarikçi değişmeli. → `aydinlatma-ve-acik-riza.md`.

### İşaretleme ölçüsü
**En küçük değişiklikle** düzelt: önce kelime, sonra ifade, sonra alt bent, en son madde. Bir maddeyi baştan yazıyorsan bunu gönderim notunda açıkça söyle.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Yön | Bu sözleşmede siz veri sorumlusu musunuz, veri işleyen mi? |
| Hizmet | Hizmet nedir; işleyen veriye nasıl erişiyor (barındırma, uzaktan erişim, işleme)? |
| Veri | Hangi kategoriler? Özel nitelikli veri (sağlık, biyometrik, ceza mahkûmiyeti) var mı? |
| Yer | Veri ve yedekler hangi ülkede? Alt işleyenler kim ve nerede? |
| Ana sözleşme | DPA ana sözleşmenin eki mi? Sorumluluk sınırı ana sözleşmede mi? |
| Profil | Standart / yedek / asla kabul etmeyeceğiniz pozisyonlar (denetim, ihlal süresi, alt işleyen, yer, silme, sorumluluk)? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "3" | "8" | "9" | "12" | "13" | "15"
legal_get_statute_article law_no: "40863" article_no: "<veri işleyenin yurt dışına aktarımı — 6. madde ve devamı>"
legal_search_admin_guidance sorgu: "Kişisel Verileri Koruma Kurulunun kararı veri işleyen veri sorumlusu müşterek sorumluluk teknik idari tedbir" kurum: "Kişisel Verileri Koruma Kurulu" tarih_baslangic: "<son 3 yıl>"
legal_search_statute_semantic sorgu: "veri işleyen alt işleyen sözleşme kişisel veri güvenliği"
```

---

## Çıktı iskeleti — DPA inceleme notu

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

# Veri İşleme Sözleşmesi İncelemesi: [Karşı taraf]
**Yön:** [veri işleyeniz / veri sorumlusuyuz] **Ana sözleşme:** [ek / bağımsız] **Önceki inceleme:** [var — tarih / yok]

## Sonuç
[İki cümle: imzalanabilir mi, ne değişmeli?] Bulgular: [N]🟢 [N]🟡 [N]🟠 [N]🔴

## Madde madde
### [Madde adı]
- Karşı tarafın metni: …
- Pozisyonumuz (profil / genel öneri): …
- Açık ve risk: …
- Önerilen değişiklik: [en küçük düzeltme]

## Aydınlatma metni ve VERBİS tutarlılığı
[🟢 tutarlı | 🟡 farklar]

## Toplu düzeltme listesi (karşı tarafa gidecek)
## Karşı taraf kabul etmezse
[yedek pozisyon ya da yükseltme]
```

**İmza kapısı:** DPA'yı imzalamak, karşı imza vermek ya da platformda otomatik kabul etmek bağlayıcı işlemdir; avukat olmayan kullanıcıda ORTAK-KURALLAR.md §1 kapısı.

## Çıktı iskeleti — sıfırdan DPA (veri sorumlusu şablonu)

Bölümler: taraflar ve roller · tanımlar (6698 m.3'e atıf) · konu, kapsam, süre (veri kategorileri ve ilgili kişi grupları eki) · talimatla işleme · gizlilik · teknik ve idari tedbirler (Ek-1) · alt işleyenler (Ek-2 liste, değişiklik usulü) · ihlal bildirimi · ilgili kişi başvurularına destek · Kurul işlemlerine destek · yurt dışı aktarım (dayanak; standart sözleşme gerekiyorsa ayrıca) · denetim · sona ermede iade/imha · sorumluluk ve rücu · uygulanacak hukuk ve yetki. Her tutar ve süre kullanıcıdan alınır; `[___]` olarak bırakılır.

---

## Sık hatalar
- Rolü sözleşmedeki etikete göre belirlemek (gerçek ilişkiye bakmamak).
- "Veri işleyen sorumlu değildir" diyerek veri sorumlusunun m.12/2 müşterek sorumluluğunu ortadan kalktı sanmak.
- Güvenlik eki olmadan "uygun tedbir" taahhüdü.
- Alt işleyen ve yedekleme konumunu sormamak (gizli yurt dışı aktarım).
- Silme taahhüdünde yedekleri ve kanuni saklama sürelerini düzenlememek.
- DPA'yı aydınlatma metniyle ve VERBİS kaydıyla karşılaştırmamak.
