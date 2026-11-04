# İlgili kişi başvurusu ve Kurula şikâyet

## Ne zaman kullanılır
- **Veri sorumlusu tarafı:** bir kişi "verilerimi silin", "hakkımda hangi veriler var", "kime aktardınız" diye başvurdu; cevap taslağı ve süreç gerekiyor.
- **İlgili kişi tarafı:** kullanıcı bir şirkete ya da kuruma KVKK başvurusu yapmak, cevap gelmediyse Kurula şikâyette bulunmak istiyor.
- Başvuru bir dava, işten çıkarma ya da basın konusu ile bağlantılıysa (kişi davacı, avukat ya da gazeteci) önce **yükselt** (aşağıda).

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Veri sorumlusunun cevabı: en kısa sürede, **en geç 30 gün** | Başvurunun veri sorumlusuna ulaşması `[incele]` | 6698 m.13/2  | Kural ücretsiz; işlem ayrıca maliyet gerektiriyorsa Kurul tarifesindeki ücret. Kimlik doğrulaması süreyi kendiliğinden durdurmaz; eksik bilgiyi hemen iste. `[incele]` |
| Silme/yok etme talebinin sonuçlandırılması: **en geç 30 gün** | Talep | Silme Yönetmeliği (talep üzerine silme hükmü)  | Veri üçüncü kişiye aktarılmışsa onlara da bildirim (m.11/1-f). |
| İlgili kişinin Kurula şikâyeti: cevabı öğrendiği tarihten **30 gün**, her hâlde başvuru tarihinden **60 gün** | Cevabın öğrenilmesi / başvuru tarihi | 6698 m.14/1  | Ret, yetersiz cevap ya da süresinde cevapsızlık hâllerinde. |
| Başvuru yolu tüketilmeden şikâyet olmaz | — | 6698 m.14/2  | Kurul ihlal iddiasını re'sen de inceleyebilir (m.15/1). |
| Kurulun şikâyete cevabı: 60 gün içinde cevap yoksa talep **reddedilmiş sayılır** | Şikâyet tarihi | 6698 m.15/4  | Zımni ret → idari yargı yolu `[incele]`. |

`legal_calculate_deadline` cevap ve şikâyet sürelerini hesaplar (`kvkk_controller_response`, `kvkk_board_complaint`, `kvkk_board_complaint_max`); sonucu m.13-14 metniyle karşılaştır. Kodu olmayan süreleri elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]`.

---

## Kontrol listesi — veri sorumlusu cevabı (upstream dsar-response'tan uyarlandı)

1. **Talebi sınıfla** (m.11): öğrenme, bilgi talebi, amaç ve amaca uygun kullanım, aktarılan üçüncü kişiler (yurt içi/dışı), düzeltme, silme/yok etme, düzeltme-silmenin alıcılara bildirilmesi, münhasıran otomatik analiz sonucuna itiraz, zararın giderilmesi. Bileşik talepleri (ör. "önce verilerimi gönderin sonra silin") bağlı iki talep olarak ele al.  Not: KVKK'da GDPR'daki gibi ayrı bir "taşınabilirlik" hakkı yoktur. `[model bilgisi — doğrulayın]`
2. **Başvuru şekli**: yazılı ya da Kurulun belirlediği yöntemlerle — KEP, güvenli elektronik imza, mobil imza, ilgili kişinin daha önce bildirdiği ve veri sorumlusunun sisteminde kayıtlı e-posta ya da başvuruya yönelik yazılım/uygulama (Tebliğ m.5/1). Zorunlu içerik: ad-soyad (yazılıysa imza), T.C. kimlik no (yabancıda uyruk ve pasaport/kimlik no), tebligata esas adres, varsa e-posta/telefon, talep konusu (m.5/2). Başvuru tarihi: yazılıda tebliğ tarihi, diğerlerinde ulaştığı tarih (m.5/4-5). Şekle uymayan başvuruyu sessizce yok sayma; eksikliği bildir.  
3. **Kimlik doğrulama**: riskle orantılı. Aşırı doğrulama başvuruyu engellemeye dönüşür; yetersiz doğrulama başkasının verisini sahtekâra verir. Doğrulama eksikse günler içinde iste, son güne bırakma.
4. **Sistemleri tek tek tara** (profilde sistem listesi yoksa sor): ana veritabanı, CRM, çağrı merkezi kayıtları, e-posta, destek kayıtları, log, analitik, yedekler, kamera, kâğıt arşiv, veri işleyenler. Tablo: sistem | sorgulandı mı | veri var mı | ne.
5. **Rol kontrolü**: siz veri işleyen misiniz? Öyleyse başvuruyu sözleşmeye göre veri sorumlusuna iletin; doğrudan cevap vermeyin. → `veri-isleme-sozlesmesi.md`.
6. **Ret / kısıt gerekçeleri** (öneridir, avukat daraltır):
   - Başka mevzuatta saklama yükümlülüğü (vergi, ticari defter, iş, sağlık kayıtları) → silme talebini kısmen reddet; dayanağı yaz. 
   - Bir hakkın tesisi/kullanılması/korunması için zorunluluk (derdest dava, dava hazırlığı). 
   - m.28 istisnaları (yargı mercileri, suç soruşturması, kamu denetimi vb.); m.28/2 hâllerinde m.11 hakları (zararın giderilmesi hariç) uygulanmaz. 
   - Üçüncü kişilerin verisi → karartarak ver.
   - Her ret **gerekçeli** olmalı. 
   Her önerilen ret gerekçesine yaz: "öneridir — gönderilmeden önce avukat incelemeli". Belirsiz bir istisnayı sessizce düşürme; geri alınabilir hatayı seç (ORTAK-KURALLAR.md §8).
7. **Yükseltme tetikleyicileri** (profildeki kişiye): başvuran davacı/karşı taraf avukatı/gazeteci olabilir; kapsam olağan dışı ("hakkımdaki tüm iç yazışmalar"); hakkında dava ya da delil saklama ihtiyacı varken silme talebi; Kurul ya da başka kamu kurumu bilgiye eklenmiş; önceki cevaba itiraz.
8. **Kayıt tut**: alınış, doğrulama, cevap tarihleri, verilen/silinen, ret gerekçeleri, işlemi yapan. Kurul incelemesinde ilk istenecek belgedir.

## Kontrol listesi — ilgili kişi (başvuran) tarafı

1. Veri sorumlusunun doğru unvanı ve başvuru adresi (aydınlatma metni, VERBİS, MERSİS) bulundu mu?
2. Talepler m.11 bentleriyle eşleşiyor mu? Somut mu? (hangi veri, hangi tarih aralığı)
3. Başvuru şekli ispatlanabilir mi? (KEP, iadeli taahhütlü posta, noter; kayıtlı e-posta)
4. Başvuru tarihi kaydedildi mi? (30 gün ve 60 gün hesapları buna bağlı)
5. Tazminat isteniyorsa: KVKK m.14/3 genel hükümlere yollar; Kurula şikâyet tazminat vermez → `../../tazminat-haksiz-fiil/SKILL.md` ve `../../hukuk-yargilamasi-dilekce/SKILL.md`. 
6. Suç şüphesi (verinin hukuka aykırı verilmesi/yayılması — TCK 136) varsa ayrı yol; Kurula şikâyet savcılığa başvurunun yerine geçmez. 

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Rol | Başvuruyu siz mi aldınız (veri sorumlusu/işleyen), siz mi yapacaksınız (ilgili kişi)? |
| Başvuru tarihi ve kanalı | Ne zaman, hangi yolla ulaştı/gönderilecek? |
| Talep | Tam metin (kişisel verileri karartarak yapıştırın) — hangi haklar isteniyor? |
| Kimlik | Başvuran kim olduğunu nasıl kanıtladı? Vekil mi başvurdu, vekâletname var mı? |
| Sistemler | Kişinin verisi hangi sistemlerde? Veri işleyen ve yurt dışı alıcı var mı? |
| Saklama yükümlülüğü | Hangi kayıtları kanunen saklamak zorundasınız? |
| Uyuşmazlık | Kişiyle derdest dava, iş uyuşmazlığı, şikâyet var mı? |
| Önceki başvuru | Daha önce başvurmuş mu, cevap verilmiş mi? |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6698"  article_no: "7" | "11" | "13" | "14" | "15" | "28"
legal_get_statute_article  law_no: "24455"  law_type: "Tebliğ"  article_no: "5" | "6"            # Veri Sorumlusuna Başvuru Tebliği
legal_search_statute_semantic  sorgu: "ilgili kişinin silme talebi otuz gün içinde sonuçlandırır"
legal_search_admin_guidance  sorgu: "Kişisel Verileri Koruma Kurulunun kararı ilgili kişi başvurusuna cevap verilmemesi"  kurum: "Kişisel Verileri Koruma Kurulu"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  sorgu: "6698 sayılı Kanun 11. madde başvuru cevap verilmemesi tazminat"  tarih_baslangic: "<son 3 yıl>"
legal_check_holiday  tarih: "<30. gün>"
```

---

## Çıktı iskeleti — (a) alındı/ön cevap ve (b) esas cevap (iki ayrı mektup)

Upstream'deki "iki mektup kuralı": alındı yazısı birkaç gün içinde, esas cevap 30 gün içinde. Tek bir mektubu 30. güne bırakmak süreç hatasıdır. Bu mektuplar **dışa gider**: taslak başlığı ve iç notlar mektubun içinde olmaz; iç değerlendirme ayrı belgede başlıklı kalır.

```markdown
(a) Konu: KVKK kapsamındaki başvurunuz hk. — alındı

Sayın [Ad Soyad],
[tarih] tarihinde [kanal] ile ilettiğiniz başvuru tarafımıza ulaşmıştır.
Başvurunuzu şöyle anlıyoruz: [tek cümle].
Cevabımızı en geç [tarih — 30. gün; tatil kontrolü] tarihine kadar ileteceğiz.
[Kimlik doğrulaması eksikse:] Başvurunun size ait olduğunu doğrulayabilmemiz için [somut adım] rica ederiz.
[Veri sorumlusu, iletişim]
```

```markdown
(b) Konu: KVKK kapsamındaki başvurunuza cevabımız

1. Talepleriniz: [m.11 bentleriyle]
2. İşlenen verileriniz: | Kategori | Kaynak | Amaç | Hukuki sebep | Saklama |
3. Aktarımlar: | Alıcı grubu | Yurt içi/dışı | Amaç |
4. Yapılan işlem: [düzeltildi / silindi / anonimleştirildi — tarih; alıcılara bildirim]
5. Karşılanamayan talepler ve gerekçesi: [dayanak madde]
6. Kurula şikâyet hakkınız: 6698 m.14 uyarınca [30/60 gün].
[Veri sorumlusu, tarih]
```

## Çıktı iskeleti — Kurula şikâyet (ilgili kişi)

```markdown
KİŞİSEL VERİLERİ KORUMA KURUMU BAŞKANLIĞINA

ŞİKÂYET EDEN : [ad soyad, T.C. kimlik no, adres, iletişim]
ŞİKÂYET EDİLEN (VERİ SORUMLUSU): [unvan, adres]
KONU : 6698 sayılı Kanun m.14 uyarınca şikâyet

AÇIKLAMALAR:
1. [tarih] tarihinde veri sorumlusuna [kanal] ile başvurdum (Ek-1).
2. [Cevap vermedi / reddetti / yetersiz cevap verdi — tarih] (Ek-2).
3. [İhlal iddiası: hangi veri, hangi işlem, hangi madde]
SONUÇ VE İSTEM: [hukuka aykırılığın tespiti ve giderilmesi, m.15 uyarınca işlem]
EKLER: başvuru ve gönderim kanıtı, cevap (varsa), diğer belgeler
[tarih, imza]
```
Kurul başvuru kanalı ve biçimi (e-Devlet/KVKK şikâyet modülü, posta) `[doğrula]`; 3071 m.6 şartlarını (ad, adres, imza) taşımayan şikâyet incelemeye alınmaz. 

---

## Sık hatalar
- Başvuruyu 30. güne kadar bekletip tek mektup göndermek.
- Kimlik doğrulama istemeyi süre durdurucu saymak.
- Silme talebini, kanuni saklama yükümlülüğünü ayırmadan tümden kabul ya da tümden ret.
- Veri işleyen olarak ilgili kişiye doğrudan esas cevap vermek.
- İlgili kişinin, veri sorumlusuna başvurmadan doğrudan Kurula gitmesi (m.14/2).
- Kurul şikâyetinin tazminat sağlayacağını sanmak.
- Ret cevabında gerekçe yazmamak (m.13/3).

