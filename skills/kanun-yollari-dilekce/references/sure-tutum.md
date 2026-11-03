# "Süre tutum" (müddeti muhafaza) dilekçesi — eleştirel değerlendirme

Kullanıcı "süre tutum dilekçesi yaz", "gerekçeli karar gelmedi, kısa istinaf verelim", "tefhim edildi, süre kaçmasın" dediğinde önce bu dosyayı oku, sonra ilgili yolun dosyasına (`hukuk-istinaf.md`, `hukuk-temyiz.md`, `ceza-istinaf-temyiz.md`, `idari-istinaf-temyiz.md`) geç.

## Bu bir kanun yolu kurumu mu?

**Hayır.** HMK, CMK, İYUK ve 7036'da "süre tutum" adlı bir başvuru türü, süreyi durduran ya da uzatan bir hüküm yoktur. Bu, **gerekçe göstermeden yapılmış kısa bir kanun yolu başvurusu** için uygulamada kullanılan addır. Hukuki etkisi yalnızca şudur: dilekçe süresinde verilmişse kanun yoluna başvurulmuş sayılır; sonraki "ayrıntılı dilekçe" ise **ancak kanun yolu süresi içinde** verilirse dikkate alınır.

Eski YAML'ın dayandığı varsayım ("süre tefhimle başlar, gerekçeli kararı beklemeden süre tutum verilmelidir") bugün **çoğu yargı kolunda geçersizdir**:

| Yargı kolu | Süre ne zaman başlar | Süre tutum gerekli mi? | Dayanak |
|---|---|---|---|
| Hukuk (HMK) | İlamın **tebliği** | Hayır. Tefhimle başlayan süre yok. | HMK m.345 |
| İş mahkemesi (7036) | İlamın **tebliği** | Hayır. YAML'daki "İş mahkemelerinde 7036 özel hükümleriyle süre tefhimle başlayabilir" iddiası **yanlış**. | 7036 m.7/4 |
| İcra mahkemesi (İİK) | Kararın **tebliği** (güncel metin) | Hayır (güncel metin). Eski metinde "tefhim veya tebliğden on gün" vardı. Değişiklik 7499 sayılı Kanunla yapıldı, 1.6.2024'te yürürlüğe girdi ve yalnız **1.6.2024 ve sonrasında verilen** kararlara uygulanır; daha önce verilen kararlarda eski metin (tefhim veya tebliğden on gün) geçerlidir. | İİK m.363/1 |
| Ceza (CMK) — **1.6.2024 ve sonrası** kararlar | Hükmün **gerekçesiyle birlikte tebliği** | Hayır. | CMK m.273/1, m.291/1, geçici m.6/1-c |
| Ceza (CMK) — **1.6.2024 öncesi** kararlar | Eski metin: hükmün **açıklanması** (yokluğunda verilmişse tebliğ) | **Evet, gerçek ihtiyaç buydu.** Kısa başvuru tefhimden itibaren süresinde verilmeliydi. Bu dosyalar artık çoğunlukla kanun yolundadır. | CMK m.273 (2014 sürümü) |
| İdari yargı (İYUK) | Kararın **tebliği** | Hayır. | İYUK m.45/1, m.46 |

Eski kaynaklardaki "ceza istinaf süresi 7 gün" bilgisi **eskidir**; güncel süre iki hafta ve gerekçeli tebliğden işler.

## İçtihat — gerekçesiz erken dilekçe ne olur?

1. **Tebliğden önce verilen kısa dilekçe istinaf iradesi sayılabilir**, ama BAM yalnız **kamu düzeni** yönünden inceler (HMK m.355). Ayrıntılı dilekçe tebliğden itibaren iki haftayı geçerse dikkate alınmaz.
2. **Karşı görüş riski:** 2. HD kararındaki karşı oy, tebliğden önce hak doğmadığını (HMK m.349/1 kıyası) ve erken dilekçenin hiçbir hukuki sonuç doğurmadığını savunuyor. Daireler arası uygulama birlik değildir `[incele]`.
3. **Süre içinde kısa dilekçe + süre dışında ayrıntılı dilekçe:** inceleme kısa dilekçeye göre yapılır; "karar usul ve yasaya aykırıdır" gibi genel ifade sebep sayılmaz; sonuç çoğunlukla esastan rettir.
4. **e-Tebligat tuzağı:** UYAP/e-Tebligatta tebliğ, iletimi izleyen beşinci gün yapılmış sayılır; süre bu tarihten işler. Gerekçeli kararın geldiğini fark etmemek en sık süre kaybı nedenidir.

## Becerinin davranışı

1. Yargı kolunu ve karar tarihini öğren. Yukarıdaki tabloya göre **süre başlamış mı** söyle.
2. Süre henüz başlamadıysa (gerekçeli karar tebliğ edilmediyse):
   - Kullanıcıya "Süre tutum dilekçesi zorunlu değildir; süre gerekçeli kararın tebliğiyle başlar" de ve **tebliği takip** önerisi ver (UYAP/e-Tebligat kontrolü, takvime işleme).
   - Kullanıcı yine de kısa dilekçe vermek isterse (ör. ihtiyati tedbirin kalkmaması, icranın durdurulması gibi pratik bir neden) aşağıdaki iskeleti üret; ama **gerekçeli dilekçenin tebliğden itibaren süre içinde ayrıca verilmesi gerektiğini** iki kez yaz ve son günü hesapla. Kısa dilekçeye bile bilinen sebepleri ekle.
3. Süre başladıysa ve az kaldıysa (🔴): "süre tutum" değil, **elden gelen en iyi gerekçeli dilekçeyi** süre içinde ver. Sonradan ek dilekçe, süre dolmadan verilirse dikkate alınır.
4. 1.6.2024 öncesi bir ceza hükmü söz konusuysa eski metni çek; tefhimden işleyen süre ihtimalini 🔴 işaretle.
5. Harç ve gideri kısa dilekçeyle birlikte yatır; aksi hâlde kesin süreli muhtıra gelir (HMK m.344).

## Görüşme soruları (data_schema → sorular)
1. Kararı veren mahkeme ve dosya esas no? (`court_name`, `file_number`)
2. Kısa karar hangi tarihte tefhim edildi? (`decision_date`)
3. Gerekçeli karar tebliğ edildi mi, ne zaman (e-Tebligat iletim tarihi)?
4. Hukuk mu, iş mi, icra mı, ceza mı, idari mi? Ceza ise hüküm 1.6.2024'ten önce mi verildi?
5. Başvuru türü: istinaf mı temyiz mi? (`appeal_type`)
6. Başvuran sıfatı ve vekili? (`party_info`)
7. Bilinen itiraz sebepleri (kısa da olsa)?

## Kısa (gerekçesiz) başvuru iskeleti — yalnız 2. maddedeki durumda
```markdown
[___] BÖLGE ADLİYE MAHKEMESİ İLGİLİ [HUKUK/CEZA] DAİRESİNE (temyizde: YARGITAY İLGİLİ … DAİRESİNE)
Gönderilmek üzere
[___] [___]. [___] MAHKEMESİNE

DOSYA NO : [___] Esas
BAŞVURAN : [___] ([davacı/davalı/sanık]) — Vekili Av. [___]
KARŞI TARAF : [___]
KONU : [__.__.____] tarihinde tefhim edilen kısa karara karşı [İSTİNAF/TEMYİZ] başvurumuzun
               sunulması ve gerekçeli kararın tebliğinden sonra kanuni süre içinde gerekçeli
               dilekçemizi sunacağımızın bildirilmesidir.

AÇIKLAMALAR : 1. Mahkemenizin yukarıda numarası yazılı dosyasında [__.__.____] tarihinde verilen
                  karara karşı [istinaf/temyiz] yoluna başvuruyoruz.
               2. Şimdiden bildirdiğimiz başlıca sebepler: [bilinen sebepler — boş bırakma; en az
                  bir somut sebep yaz, ör. görev/dava şartı, delil toplanmaması, hesap hatası].
               3. Ayrıntılı sebeplerimizi gerekçeli kararın tebliğinden itibaren kanuni süre içinde
                  sunacağız.
SONUÇ VE İSTEM: [İstinaf/temyiz] başvurumuzun kabulü ile gerekçeli kararın tebliğini, gerekçeli
               dilekçemizin süresi içinde sunulmasından sonra kararın [kaldırılmasına/bozulmasına]
               karar verilmesini saygıyla arz ve talep ederiz.
                                         [tarih] — Av. [___] (e-imza)
```
Eski YAML'daki "süre tutum talebimizin kabulü" ifadesi **atıldı**: kanunda kabul edilecek bir "süre tutum talebi" yoktur; talep kanun yolu başvurusunun kendisidir.

## Sık hatalar
- 🔴 Kısa dilekçeyi verip gerekçeli dilekçenin süresini tefhimden ya da "ek süre verilecek" beklentisiyle hesaplamak. Ek süre verilmez.
- 🔴 Ayrıntılı dilekçeyi tebliğden itibaren iki haftadan (idari yargıda otuz günden) sonra vermek.
- 🟠 Kısa dilekçede hiç sebep yazmamak: m.355 nedeniyle inceleme kamu düzeniyle sınırlı kalabilir.
- 🟡 Harç ve gideri yatırmamak.
