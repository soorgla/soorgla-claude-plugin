# Abonelik iptali (fesih bildirimi)

İnternet, GSM hattı, dijital yayın platformu, gazete/dergi, spor salonu üyeliği gibi **abonelik sözleşmesini** sona erdirmek isteyen tüketicinin hizmet sağlayıcıya göndereceği fesih bildirimi. Firma iptali yapmıyor, fatura kesmeye devam ediyor ya da yüksek "cayma bedeli" istiyorsa da bu dosya kullanılır; uyuşmazlık sürerse `tuketici-hakem-heyeti.md`'ye geç.

## Ne zaman kullanılır

- **Belirsiz süreli** ya da **uzun süreli** abonelik: tüketici **gerekçe göstermeden ve cezai şart ödemeden** istediği zaman feshedebilir.
  - Dikkat: **Kanun** "bir yıldan daha uzun", **Yönetmelik** "bir yıl ve daha uzun" diyor. Tam 1 yıllık sözleşmede ikisi ayrışıyor; kanun üst normdur, ama yönetmelik tüketici lehine. `[incele]`
- **Bir yıldan kısa** belirli süreli abonelik: sağlayıcı sözleşme koşullarını değiştirirse fesih hakkı doğar (Kanun m.52/4); Yönetmelik buna "hizmetten yararlanmaya engel geçerli bir sebep" hâlini de ekler (ör. taşınma `[incele]`).
- **Taahhütlü abonelik** (indirim, cihaz ya da başka bir fayda karşılığında belirli süre abone kalma sözü) süresinden önce sona erdiriliyorsa: sağlayıcının isteyebileceği bedel, o tarihe kadar sağlanan **indirim, cihaz veya diğer faydaların tahsil edilmemiş kısmının toplamı ile sınırlıdır**. Faturadaki "cayma bedeli"ni bu sınırla karşılaştır.
- Elektronik haberleşme (GSM, internet) için ayrıca **Elektronik Haberleşme Sektörüne İlişkin Tüketici Hakları Yönetmeliği** (BTK; soorgla no `24039`) uygulanır. m.12: taahhüde aykırılıkta işletmecinin isteyebileceği bedel, o döneme kadar sağlanan indirim, cihaz ve diğer faydaların tahsil edilmemiş kısmıyla sınırlıdır; taahhüt bitimine kadar tahakkuk edecek bedeller daha düşükse düşük olan esas alınır (m.12/5). Mobil dışı aboneliklerde taşınma ve hizmetin yeni adreste aynı nitelikte sunulamaması belgelenirse cayma bedelsiz fesih (m.12/6); internet hızı Kurum ölçüm kriterlerini sağlamıyorsa cihaz kalan bedeli dışında cayma bedelsiz fesih (m.12/11); belirsiz durumda abone lehine yorum (m.12/12). Güncel metni `legal_list_statute_articles` (`law_no: "24039"`, `article_no: "12"`, `include_content: true`) ile çek.

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Sağlayıcının fesih talebini yerine getirme süresi: **en geç 7 gün** | Bildirimin **sağlayıcıya ulaştığı** tarih | Abonelik Sözleşmeleri Yönetmeliği **m.24/1** | Eski YAML bunu "Md. 25" diye gösteriyordu; doğrusu **m.24**. |
| Süreli yayınlarda: günlük **15 gün**, haftalık **1 ay**, aylık **3 ay** | Bildirim | Yönetmelik m.24/2 | Daha uzun aralıklı yayında bildirimden sonraki ilk yayından sonra hüküm doğurur. |
| Süre içinde feshedilmezse: süre bitiminden sonra **hiçbir bedel istenemez** (hizmetten yararlanılmış olsa bile) | 7 günlük sürenin bitimi | 6502 m.52/5; Yönetmelik m.25/2 | |
| Peşin ödenen bedelin kalanı ve **güvence/depozito** iadesi: **15 gün**, kesintisiz, depozito **güncel tutarıyla** | Fesih bildiriminin **hüküm ifade etmesi** | 6502 m.52/5; Yönetmelik m.25/3 | Eski YAML'daki "25/3 — 15 gün" doğru; "güncel tutar" eksikti. |
| Son dönem ödeme bildirimi (son fatura): **10 gün**; elektronik haberleşmede **4 aya kadar** uzayabilir | Fesih bildiriminin hüküm ifade etmesi | Yönetmelik m.25/4 | Mahsuplaşma yapılabilir (m.25/5). |

Bu süreler sağlayıcının yükümlülüğüdür; tüketici için hak düşürücü süre yoktur. Yine de bildirimin **ulaştığı tarihi ispatlayabilmek** önemlidir.

## Zorunlu unsurlar ve şekil

- Fesih bildiriminin **kâğıt üzerinde** ya da **kalıcı veri saklayıcısı** (e-posta, KEP, SMS gibi tekrar açılabilen kayıt) ile sağlayıcıya yöneltilmesi **yeterlidir**. Sağlayıcı kayıtlı telefonla fesih imkânı da sunabilir. Eski YAML şekli "Md. 24" diye gösteriyordu; doğrusu **Yönetmelik m.23** (ve Kanun m.52/4).
- Sağlayıcı, fesih için sözleşmenin kurulduğu yöntemden **daha ağır** ya da feshi **zorlaştıran** bir yöntem koyamaz (ör. internetten abone olunan hizmet için "şubeye gelin" şartı).
- Gerekçe yazmak zorunlu değildir (uzun/belirsiz süreli abonelikte). Kısa süreli abonelikte fesih sebebi (koşul değişikliği, taşınma) yazılmalıdır.
- Bildirimde: abone adı-soyadı, **abone/hizmet/sözleşme numarası** (en kritik bilgi), hizmetin adresi, fesih talebi, depozito iadesi için IBAN (varsa), iletişim, tarih, imza (kâğıtsa).
- Sağlayıcı, feshi yazılı ya da kalıcı veri saklayıcısıyla **bildirmekle** yükümlüdür. Teyit gelmezse ekran görüntüsü, e-posta, KEP alındısı saklanmalı.

## 🔴 Avukat eşikleri

Abonelik iptali çoğu zaman avukatsız yapılabilir. Şu durumlarda danışın:
- Firma ödenmeyen bedel için **icra takibi** başlattı → `icra-itirazi.md` (süre işliyor).
- İstenen cayma bedeli/borç yüksek ve THH sınırının üstünde (tüketici mahkemesi + arabuluculuk).
- Sözleşme bir işletme adına (tüketici sıfatı yok); 6502 uygulanmayabilir.

## Görüşme soruları

1. Hangi firma, hangi hizmet? Firmanın tam unvanı (fatura üstünde).
2. Abone / hizmet / sözleşme numaranız.
3. Sözleşme süresiz mi, belirli süreli mi? Belirli süreliyse kaç ay?
4. **Taahhüt** var mı (indirimli kampanya, cihaz, modem)? Taahhüt bitiş tarihi?
5. Neden iptal ediyorsunuz? (Kısa süreli/taahhütlü abonelikte önemli: fiyat/koşul değişikliği, taşınma, hizmetin hiç ya da gereği gibi verilmemesi)
6. Depozito/güvence bedeli ödediniz mi? İade için IBAN.
7. Bildirimi nasıl göndereceksiniz? (e-posta, KEP, iadeli taahhütlü posta, firmanın uygulaması)
8. Daha önce iptal istediniz mi? Ne zaman, nasıl, sonuç?
9. Adınız-soyadınız, T.C. kimlik no (firma isteyebilir), telefon, e-posta.

## soorgla çağrıları

```
legal_get_statute_article law_no: "6502" article_no: "52"
legal_get_statute_article law_no: "20480" article_no: "22" | "23" | "24" | "25" | "16" # Abonelik Sözleşmeleri Yönetmeliği
legal_search_statute_semantic sorgu: "elektronik haberleşme taahhütlü abonelik fesih cayma bedeli" # BTK düzenlemesi
legal_search_official_gazette query: "Abonelik Sözleşmeleri Yönetmeliğinde Değişiklik" search_in: "title" sort_by: "date_desc" # değişiklik var mı
```
`legal_get_statute_article` Yönetmelik için `law_no: "20480"` ile çalışıyor (soorgla iç numarası; Resmî Gazete sayısı değil).

## İskelet — fesih bildirimi

```
[FİRMA UNVANI]
[Müşteri Hizmetleri / Abonelik Birimi]
[Adres / e-posta / KEP adresi]

ABONE ADI SOYADI : [___]
T.C. KİMLİK NO : [___]
ABONE / HİZMET NO : [___]
HİZMET ADRESİ : [___]
İLETİŞİM : [telefon / e-posta]

KONU : Abonelik sözleşmesinin feshi

Şirketinizdeki yukarıda numarası yazılı aboneliğimi 6502 sayılı Tüketicinin Korunması
Hakkında Kanun'un 52. maddesi ve Abonelik Sözleşmeleri Yönetmeliği'nin 22. ve 23. maddeleri
uyarınca feshediyorum. [Kısa süreli/taahhütlü ise sebep: …]

Yönetmeliğin 24. maddesi uyarınca fesih talebimin bu bildirimin tarafınıza ulaştığı tarihten
itibaren en geç yedi gün içinde yerine getirilmesini, bu süreden sonrası için tarafıma bedel
tahakkuk ettirilmemesini (Kanun m.52/5), feshin tarafıma yazılı olarak ya da kalıcı veri
saklayıcısı ile bildirilmesini (Yönetmelik m.25/1) talep ederim.

[Depozito varsa:] Peşin ödediğim bedelin kalanının ve güvence/depozito bedelinin güncel
tutarıyla, Yönetmeliğin 25/3. maddesi uyarınca on beş gün içinde aşağıdaki hesaba kesintisiz
iadesini talep ederim. IBAN: [___]

[Taahhütlü ise:] Süresinden önce fesih nedeniyle talep edilecek bedelin, Yönetmeliğin
16. maddesi uyarınca tarafıma sağlanan indirim, cihaz veya diğer faydaların tahsil edilmemiş
kısmıyla sınırlı olarak ve kalem kalem gösterilerek bildirilmesini talep ederim.

Tarih : [___]
Ad Soyad / İmza : [___]
```

## Sık hatalar

- Telefonla iptal edip kayıt tutmamak; bildirimin ulaştığını ispatlayamamak.
- Eski YAML'daki madde numaralarını kullanmak (şekil m.23, 7 gün m.24, iade m.25/3).
- Taahhütlü abonelikte "hiç bedel ödemem" demek: bedel m.16 sınırında istenebilir. Ama sınırı aşan "cayma bedeli"ne itiraz edilmelidir.
- Fesihten sonra kesilen faturayı ödememek yerine itiraz etmemek; sonra icra takibiyle karşılaşmak.
- Firma şubeye gelme şartı koyunca vazgeçmek (m.23/3: zorlaştırıcı yöntem konamaz).
