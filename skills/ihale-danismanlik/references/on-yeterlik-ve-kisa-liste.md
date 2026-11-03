# Ön yeterlik ve kısa liste

Danışmanlık ihalesinin ilk yarısı: ön yeterlik ilanı ve şartnamesi, başvuruların açılması, genel uygunluk, asgari kriterler, puanlama ve kısa liste. Kontrol listesi örnek ön yeterlik şartnamesinin (İKN 2026/1765031) madde yapısını izler; madde numaraları tip ön yeterlik şartnamesinde de aynıdır `[doğrula — başka idarenin şartnamesinde numarayı kontrol et]`.

- **İdare:** "Şartname tip şartnameye ve yönetmelik aralıklarına uygun mu, puanlama savunulur mu?"
- **Aday:** "Neden kısa listeye giremedim, puanım doğru mu, şikâyet edebilir miyim?"

---

## 1. Usul ve kısa liste kuralı

- [ ] Danışmanlık hizmetleri **yalnız belli istekliler arasında ihale** usulüyle ihale edilir; yaklaşık maliyeti m.13/b-2'deki hizmet üst limitinin dört katının altında kalanlar hizmet alımı ihalesiyle yapılabilir (tutarı `usul_kontrol` / `legal_get_social_parameters`'tan çek).
- [ ] Ön yeterlik ilanında kriterler ve **kısa listeye alınacak aday sayısı veya aralığı** yazılı; kısa liste en az 3, en fazla 10 aday. Örnekte 10 aday (Ö.Y.Ş. 21.1).
- [ ] İlan ve doküman hazırlanmadan ilan yapılamaz; ilanda dokümanda olmayan husus yer alamaz.
- [ ] İlan süresi: eşik üstü son başvurudan en az 14 gün önce; eşik altı en az 7 gün. İlan günü sayılır, son başvuru günü sayılmaz.
- [ ] Şartname **tip ön yeterlik şartnamesi** esas alınarak hazırlanır; boş/dipnotlu hususlar mevzuata aykırı olmayacak şekilde doldurulur, ek hükümler "Diğer Hususlar"a.

## 2. Başvuru belgeleri (Ö.Y.Ş. m.7) ve genel uygunluk

- [ ] Başvuru mektubu, oda kayıt belgesi (ilan/son başvuru yılında alınmış), imza beyannamesi/sirküleri, vekâletname, iş ortaklığı beyannamesi, %50+ hisseli ortağın deneyimini kullanana ortaklık tespit belgesi, yurt dışı deneyim için şirketler topluluğu belgesi.
- [ ] Konsorsiyuma izin verilmiş mi? Örnekte verilmemiş (Ö.Y.Ş. 7.3, 17).
- [ ] **Belge eksikliği tamamlatılamaz**; belgede **bilgi eksikliği** başvurunun esasını değiştirmiyorsa en az 2 iş günü süre verilerek tamamlatılır; sonradan düzenlenen belge son başvuru tarihi itibarıyla durumu göstermeli. Bu ayrım uyuşmazlıkların çoğunun kaynağı `[incele]`.
- [ ] Genel uygunluğu taşıyan aday sayısı 3'ten azsa ihale iptal.
- [ ] m.10/4 halleri (iflas, kesinleşmiş vergi/SGK borcu vb.) son başvuru tarihinde aranır (Ö.Y.Ş. 11.1). Borç sınırını `usul_kontrol`'den, ilan tarihine göre al.

## 3. Asgari ön yeterlik kriterleri (Ö.Y.Ş. m.8.1-8.4)

| Kriter | Kural | Dayanak |
|---|---|---|
| Bilanço | cari oran ≥ 0,75; öz kaynak oranı ≥ 0,15; KV banka borcu / öz kaynak < 0,50 — üçü birlikte; tutmazsa son iki yıl ortalaması; ortak girişimde her ortak ayrı ayrı | 12911 m.34/3-4, 10 |
| Bilanço — ilk dört ay | son başvuru tarihi yılın ilk dört ayındaysa **iki önceki yıl**; tutmazsa iki ve üç önceki yıl ortalaması | 12911 m.34/5 (RG 9/4/2026) |
| Serbest meslek erbabı | gelir/gider ≥ 1,25 | 12911 m.34/9 |
| İş hacmi | toplam ciro YM'nin %25-35'i **veya** danışmanlık cirosu YM'nin %15-25'i aralığında idarece belirlenen tutar; biri yeter; iki yıl ortalaması; ilk dört ayda iki önceki yıl; iş ortaklığında hisse oranında | 12911 m.35/6-8, 11 |
| İş deneyimi | tek sözleşme; YM'nin %25-50'si aralığında idarece belirlenen tutardan az olmamak üzere | 12911 m.38/4 |
| İş deneyiminin süresi | danışmanlıkta son 5 yıl, **yapımla ilgili danışmanlıkta son 15 yıl** içinde kabulü tamamlanan; devam eden işte ilk sözleşme bedeli tamam + %80 gerçekleşme | 12911 m.38/1-2, m.48/5 |
| İş ortaklığı | pilot ≥ %70, diğer her ortak ≥ %10, diğerlerinin toplamı ≥ %30; aynı ortaklık yapısıyla önceki iş ortaklığının belgesinde oran şartı aranmaz | 12911 m.38/5 |
| Anahtar teknik personel | eşik altı en fazla 2, eşik ve üstü en fazla 4 kişi; toplam deneyim en fazla 10, benzer deneyim en fazla 5 yıl istenebilir | 12911 m.39/2-3 |

- [ ] **İdare:** asgari tutarlar YM'ye göre aralıkta mı? YM gizli olduğundan aday denetleyemez; idare işlem dosyasında hesabı tutmalı `[incele]`. Örnekte iş hacminde idare "toplam ciro **veya** danışmanlık cirosu" kuralını doğru yazmış (Ö.Y.Ş. 8.1.3).
- [ ] **Belge tutarları:** iş bitirme/iş durum tam; denetim ve yönetim belgeleri beşte bir; yapım işi kontrollüğü ve yapı denetimi ihalelerinde gerçek kişilerin yapım işlerinden aldığı denetim/yönetim belgeleri **1/50**. Kontrollük ihalesinde bu oran çoğu zaman gözden kaçar 🟠.
- [ ] Benzer iş tanımı dokümanda ve ilanda açık mı? Örnekte "Yapım İşlerinde Benzer İş Grupları Listesi B/II ve B/III grubu işlerin danışmanlık (kontrollük) işi" (Ö.Y.Ş. 8.3). Dar tanım → rekabet (4734 m.5) iddiası; geniş tanım → idare için risk az `[incele]`. **Emsal ölçütü:** "dar benzer iş" iptal emsalleri yalnız tanım ihale konusundan **dar** olduğunda işler; tanım ihale konusuyla aynı ya da daha genişse uygulanmaz (`../../ihale-sikayet/references/kik-emsal-arama.md`). Benzer iş ilanda da yer aldığından şikâyet süresi **ilk ilan tarihinden** işler (4734 m.55/1).
- [ ] Kalite belgesi (ISO 9001) istendiyse TÜRKAK teyidi ve iş ortaklığında bir ortağın sunması yeterliliği (Ö.Y.Ş. 8.2.4).
- [ ] Şartnamenin m.7-8 dışında sayılan belge ve kriterler değerlendirmede dikkate alınmaz (Ö.Y.Ş. 8.2.6) — aday için "istenmeyen belgeden elenemem" savunması.

## 4. Puanlama (Ö.Y.Ş. m.8.5-8.6) — yalnız asgari şartları sağlayan aday sayısı kısa liste sayısını aşarsa

- [ ] Asgari şartları sağlayan sayı kısa liste sayısına eşit ya da azsa puanlama **yapılmaz**, hepsi kısa listeye alınır.
- [ ] Puan aralıkları: **mali kapasite 10-30, teknik yetenek 70-90** (genel hizmet deneyimi, özel hizmet deneyimi, personel, ekipman, AR-GE/standart/kalite); toplam 100. Örnek: mali 20; teknik 80 = genel 10 + özel 35 + personel 30 + ekipman 0 + kalite 5 ✅.
- [ ] Teknik yetenek her üye tarafından ayrı ayrı puanlanır, üye sayısına bölünür (üye ve komisyon formları); mali kapasite komisyon formuna. Üye formları yoksa ya da gerekçesizse 🟠 (istekli iddiası).
- [ ] Örnek puanlama mantığı (dokümandan): ciro ortalaması "asgari kritere eşit → alt puan, tam puan tutarına eşit/fazla → tam puan, ara değer doğrusal"; özel hizmet deneyiminde **tek sözleşme**, birden fazla iş toplanmaz, iş ortaklığında pilot ortağın deneyimi; genel hizmet deneyimi faaliyet süresi bantları, iş ortaklığında pilot ortak; personelde asgari kriteri sağlayana asgari puan, tam puan için gereken yıla doğrusal; iş ortaklığında bütün ortakların personeli birlikte (Ö.Y.Ş. 8.5.1, 8.6.1-8.6.3).
- [ ] **Doğrusal orantı** elle: `puan = alt + (tam − alt) × (değer − asgari) / (tam_tutar − asgari)`; değer ≥ tam tutar ise tam puan. İş ortaklığında mali kapasite: her ortağın tutarı ortaklık oranına bölünerek puanlanır, puanlar ortaklık oranıyla ağırlıklandırılıp toplanır (Ö.Y.Ş. 8.5.1 son paragraf) `[incele — şartname bu yöntemi yazmamışsa]`.
- [ ] **Eşitlik:** eşit puanlıların kısa liste sayısını aşması halinde tek sözleşmeye ilişkin iş deneyim tutarı fazla olan öne; iş ortaklığında pilot ortağın tutarı.
- [ ] Kısa liste **alfabetik** sıralanır.

## 5. Sonuç, bildirim ve davet (Ö.Y.Ş. m.21-22)

- [ ] Ön Yeterlik Değerlendirme Sonucu Tutanağı, kararı izleyen **3 iş günü** içinde kısa listeye giremeyenlere "Yeterli Bulunmayan Adaylara Sonucun Bildirilmesine İlişkin Form" ekinde gönderilir.
- [ ] Kısa listedekilere listenin oluşturulmasından 3 iş günü içinde davet mektubu + ihale dokümanı + sonuç tutanağı. Eşik üstünde ihale gününden en az 40 gün önce. Davet sayısı 3'ten azsa davet gönderilmez, ihale yapılmaz.
- [ ] Bildirim EKAP üzerinden; tebliğ tarihi bildirim kutusuna ulaşma tarihi, mesai dışında gönderilen ertesi iş günü (Ö.Y.Ş. 6.2). Şikâyet süresi buradan sayılır.

---

## İstekli için itiraz ekseni (şikâyet metni `ihale-sikayet`'te)

| İddia | Neye dayanır | Risk |
|---|---|---|
| Belge eksikliği değil bilgi eksikliğiydi, tamamlatılmalıydı | 12911 m.54/3-4 | 🟠 belgeye bağlı `[incele]` |
| Puan dokümandaki yöntemle hesaplanmamış (doğrusal orantı, tek sözleşme, pilot ortak) | Ö.Y.Ş. 8.5-8.6; m.54/9 | 🟢 aritmetik, kanıtı kolay |
| Üye formları yok / gerekçesiz | 12911 m.54/10 | 🟡 |
| Rakip asgari şartı sağlamıyor (ör. 1/50 oranı, 15 yıl sınırı, %70 pilot) | m.48/5-8, m.38/5 | 🟠 eşit muamele |
| Şartname yönetmelik aralığı dışında (puan, personel sayısı, deneyim yılı) | m.39/2-3, m.54/9 | doküman şikâyeti süresi geçtiyse 🔴 |

Şikâyet süresi: sonuç bildirimini (farkına varma) izleyen günden 10 gün (`kik_complaint`). Doküman hükmüne itiraz son başvurudan önce ve ≥3 iş günü kala yapılmalıydı; sonuç aşamasında doküman hükmüne itiraz kural olarak dinlenmez `[incele]`.

## İdare için öz denetim

- Her puan kalemi için "hangi belge, hangi şartname maddesi, hangi hesap" üçlüsünü üye formuna yaz.
- YM'ye göre asgari tutarların aralık hesabını işlem dosyasında tut (m.35/6, m.38/4).
- Eşit puan ve sıralama tablosunu tutanağa ekle; bildirim tarihini EKAP kaydından sakla.

## MCP adımları

- `legal_get_statute_article` — `law_no: "12911"`, `law_type: "Yönetmelik"`; maddeler: 14, 21, 34, 35, 38, 39, 48, 54, 55 (her biri ayrı çağrı)
- `legal_get_statute_article` — `law_no: "4734"`, `law_type: "Kanun"`; maddeler: 13, 49, 50
- `legal_search_cases` — `mahkeme: "kik"`, `sorgu: "ön yeterlik değerlendirmesi kısa listeye alınmama teknik personel puanlama"`, `tarih_baslangic: "<son 3 yıl>"`
Görülen güncel örnekler (konu taraması için; okumadan emsal gösterme, MK etkisini kontrol et): KİK 2025/UD.II-2327 (30.10.2025), 2025/UD.II-1227 (29.05.2025), 2024/UD.II-160 (25.01.2024, birden çok ihalede aynı anahtar personel).
