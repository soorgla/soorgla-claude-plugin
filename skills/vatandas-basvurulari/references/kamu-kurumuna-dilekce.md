# Kamu kurumuna dilekçe, CİMER ve bilgi edinme

Üç yakın başvuru tek dosyada:
1. **Kurum dilekçesi** (3071 sayılı Dilekçe Hakkının Kullanılmasına Dair Kanun): belediyeye, valiliğe, kaymakamlığa, okula, bakanlık birimine dilek veya şikâyet.
2. **CİMER başvurusu**: aynı dilek/şikâyet ya da bilgi edinme isteğinin Cumhurbaşkanlığı İletişim Merkezi üzerinden ilgili kuruma iletilmesi.
3. **Bilgi edinme başvurusu** (4982 sayılı Bilgi Edinme Hakkı Kanunu): kurumdan belirli bir bilgi veya belgenin istenmesi; reddedilirse itiraz.

## Ne zaman kullanılır

- Kurumdan bir **işlem** isteniyorsa (çukurun kapatılması, denetim, kayıt, ruhsatsız yapının incelenmesi) → **dilekçe** (3071). Kurum biliniyorsa doğrudan kuruma; bilinmiyorsa ya da kurum cevap vermediyse CİMER.
- Kurumdan bir **bilgi veya belge** isteniyorsa (ihale belgesi, ruhsat bilgisi, toplantı kararı) → **bilgi edinme** (4982). Doğrudan kuruma ya da CİMER'de "bilgi edinme" türüyle.
- Kurumun verdiği bir **karara karşı hak arama** (ceza, ret işlemi, imar işlemi) → bu dosya yetmez. Dilekçe hakkı yargı yolunun yerine geçmez ve dava süresi işliyor olabilir. 🔴 avukat eşiği.

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Kurumun dilekçeye **gerekçeli cevap** süresi: **en geç 30 gün** | Başvurunun yetkili makama ulaşması | 3071 m.7  | Hak düşürücü değil; kurumun yükümlülüğü. 30 günde cevap yoksa CİMER'e ya da üst makama tekrar başvurulabilir. Cevapsızlığın idari yargı açısından sonucu (zımni ret) ayrı konudur `[incele]`.  |
| Bilgi/belgeye erişim: **15 iş günü**; başka birim/kurum gerekiyorsa **30 iş günü** | Başvurunun kuruma ulaşması | 4982 m.11  | Eski YAML "15/30 gün" diyordu; doğrusu **iş günü**. |
| Bilgi edinme reddine **Kurula itiraz: 15 gün** | Ret kararının tebliği | 4982 m.13  | Kurul: Bilgi Edinme Değerlendirme Kurulu. İtiraz yargı yoluna başvurmadan önce yapılabilir; dava süresi için 🔴 avukat eşiği. |

Bu sürelerin hiçbiri `legal_calculate_deadline` ile hesaplanmaz; elle say, `legal_check_holiday` ile son günü kontrol et, `[doğrula]` işaretle.

## Zorunlu unsurlar

**Dilekçe (3071):**
- Dilekçe sahibinin **adı-soyadı, imzası ve iş ya da ikametgâh adresi** zorunludur. 
- **Belli bir konu** içermelidir. Konusuz, **yargı mercilerinin görevine giren** ya da m.4 şartlarını taşımayan dilekçeler **incelenmez**.  → Mahkemede ya da icra dairesinde görülen bir işi kuruma/CİMER'e şikâyet etmek sonuç vermez; kullanıcıyı uyar.
- T.C. kimlik no kanunda sayılmaz ama kurumlar uygulamada ister; kullanıcı vermediyse `[___]`. 

**CİMER başvurusu:**
- Dayanak: **Cumhurbaşkanlığı İletişim Merkezi Yönetmeliği** (RG 04.06.2022, s.31856, Karar Sayısı 5690). CİMER yalnızca aracıdır; başvuru **ilgili kuruma** iletilir ve cevabı o kurum verir; kurum kendisiyle ilgili görmezse gerekçesiyle ilgili kuruma iletir. 
- Başvuru yolları: elektronik/mobil, e-Devlet, ALO 150, mektup/posta (yönetmelik m.6). Başvuru tamamlanınca takip için **başvuru sayısı** verilir. 
- Metin **kısa ve sonuç odaklı** olmalı; ayrıntıyı eke koy. Metin kutusunun bir karakter sınırı olabilir: kullanıcıya **başvuru ekranındaki sınırı kontrol etmesini** söyle, sınır sayısı uydurma; metin sığmazsa özeti kutuya, tam dilekçeyi eke koy. 

**Bilgi edinme (4982):**
- İstenen bilgi/belge **açıkça** tanımlanmalı (tarih, sayı, konu). Görüş, yorum ya da araştırma gerektiren talep bilgi edinme kapsamı dışında kalabilir. 

## 🔴 Avukat eşikleri

- Başvurunun konusu kurumun **size karşı verdiği bir karar** (idari para cezası, ruhsat reddi, yıkım kararı, disiplin cezası): dava süresi işliyor olabilir; dilekçe süreyi durdurmayabilir.
- Bilgi edinme reddi geldi ve **dava açmayı** düşünüyorsunuz.
- Konu bir kamu görevlisi hakkında **suç duyurusu** niteliğinde (rüşvet, görevi kötüye kullanma): CİMER yerine savcılık yolu ve delil koruma önemlidir.

## Görüşme soruları

1. Kurumdan ne istiyorsunuz: bir işlem mi (denetim, onarım, kayıt), yoksa bir bilgi/belge mi?
2. Hangi kurum? (biliyorsanız tam adı; bilmiyorsanız olay yeri ve konu)
3. Olay ne, nerede, ne zamandan beri? (tek paragraf)
4. Daha önce bu kuruma başvurdunuz mu? Tarihi, sayısı, cevap geldi mi?
5. Elinizde fotoğraf, tutanak, yazı gibi ek var mı?
6. Adınız-soyadınız, adresiniz, (isteğe bağlı) telefon, e-posta, T.C. kimlik no.
7. CİMER'den mi göndereceksiniz, kuruma elden/posta ile mi?
8. Bu konu mahkemede ya da icra dairesinde görülüyor mu? (Evet ise → 3071 m.6/b uyarısı)

## soorgla çağrıları

```
legal_get_statute_article  law_no: "3071"  article_no: "4" | "6" | "7"
legal_get_statute_article  law_no: "4982"  article_no: "11" | "13"     # bilgi edinme süreleri, itiraz
legal_get_statute_article  law_no: "4982"  article_no: "7"             # başvuru dilekçesi unsurları (çekip kontrol et)
legal_search_statute_semantic  mevzuat_no: "5690"  sorgu: "CİMER başvuru usulü ve cevap"
legal_search_official_gazette  query: "Cumhurbaşkanlığı İletişim Merkezi Yönetmeliği"  search_in: "title"   # değişiklik var mı
legal_search_cases  mahkeme: "danistay"  sorgu: "<bilgi edinme reddi …>"  tarih_baslangic: <son 3 yıl>   # yalnız ret/itiraz aşamasında
```

## İskelet — kurum dilekçesi (3071)

```
[KURUMUN TAM ADI, BÜYÜK HARFLE] [MAKAMINA / MÜDÜRLÜĞÜNE / BAŞKANLIĞINA]
                                                    [İL / İLÇE]

KONU : [tek cümle: ne hakkında, ne isteniyor]

AÇIKLAMALAR :
1. [Olay: ne, nerede, ne zamandan beri]
2. [Etkisi: hangi zarar ya da sorun]
3. [Varsa önceki başvuru: tarih, sayı, sonuç]

SONUÇ VE İSTEM : Yukarıda açıklanan nedenlerle [somut istek: yerinde inceleme yapılmasını /
onarımın yapılmasını / …] ve 3071 sayılı Kanun'un 7. maddesi uyarınca başvurumun sonucunun
tarafıma yazılı olarak bildirilmesini saygılarımla arz ederim.

                                                    Tarih : [___]
                                                    Ad Soyad : [___]
                                                    İmza :
Adres : [___]
Telefon / e-posta : [___]

EKLER : 1. [___]
```

## İskelet — CİMER metni

```
[İLGİLİ KURUM] tarafından değerlendirilmek üzere.

Başvuru türü: [Şikâyet / İstek / İhbar / Bilgi edinme / Görüş-öneri]

[Olayın özeti: ne, nerede (mahalle, sokak), ne zamandan beri — 2-4 cümle]

[Varsa önceki başvuru: kuruma [tarih]'te başvurdum, cevap gelmedi / şu cevap geldi.]

Talebim: [somut işlem]. Başvurumun 3071 sayılı Kanun [bilgi edinme ise: 4982 sayılı Kanun]
kapsamında değerlendirilerek sonucunun tarafıma bildirilmesini rica ederim.
```
Ad, adres ve iletişim bilgileri CİMER formunda ayrıca girildiği için metne yazılmaz. Fotoğraf ve belgeler ek olarak yüklenir.

## İskelet — bilgi edinme başvurusu (4982)

```
[KURUMUN ADI]'NA
(Bilgi Edinme Birimi)

KONU : 4982 sayılı Bilgi Edinme Hakkı Kanunu kapsamında bilgi/belge talebi

İstenen bilgi/belge:
1. [tarih, sayı ya da konu ile açıkça tanımlanmış belge]
2. [___]

Bu bilgi/belgelerin [elektronik ortamda / onaylı örnek olarak] tarafıma verilmesini,
4982 sayılı Kanun'un 11. maddesindeki süre içinde bildirilmesini arz ederim.

Ad Soyad / İmza / Adres / T.C. kimlik no / e-posta : [___]
```

## Sık hatalar

- Dilekçeyi CİMER'e "Sayın Cumhurbaşkanım" diye yazmak: muhatap ilgili kurumdur.
- Mahkemede ya da icrada görülen işi CİMER'e taşımak (3071 m.6/b: incelenmez).
- Bilgi edinme süresini "gün" diye yazmak: **iş günü**.
- Bilgi edinme başvurusunda görüş ya da hukuki yorum istemek.
- Bir idari karara karşı yalnızca dilekçe verip dava süresini kaçırmak.
- İmzasız ya da adressiz dilekçe (3071 m.4, m.6/c).

