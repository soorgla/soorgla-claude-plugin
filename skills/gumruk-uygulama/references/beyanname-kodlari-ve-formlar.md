# Beyanname kodları, gümrük formları ve rehberler

## Ne zaman kullanılır
- "Beyannamede CIF'in teslim şekli kodu ne?", "rejim kodu 4000 ne demek?", "kabul kredili ödeme kodu?", "döviz/kap/ölçü birimi kodu".
- "Sözlü beyan formu", "özet beyan", "gümrük statü belgesi", "BTB başvuru formu", "nihai kullanım formu" — formun kendisi ve kullanma talimatı.

---

## Kod listeleri

Gümrük beyannamesi kutularındaki kodlar Ticaret Bakanlığının yayımladığı listelerdendir: rejim, işlemin niteliği, teslim şekli, taşıma şekli, döviz, kap, ölçü birimi, ödeme şekli, ülke, gümrük idaresi, liman, antrepo, muafiyet, vergi türü, istenen doküman, tamamlayıcı bilgi, 1 numaralı kutu alt kodları.

| Kaynak | Ne var | Not |
|---|---|---|
| Ticaret Bakanlığı "EDI/XML Referans Mesajları" kod sayfaları | Güncel kod listeleri (BİLGE ile aynı) | Esas kaynak; `[web — doğrulayın]` |
| "Bilgi Bankası" kod PDF'leri | Rejim, teslim şekli, döviz, kap, ÖTS, işlemin niteliği, 1 no'lu kutu, taşıma şekli | PDF'lerin bir kısmı eski olabilir; EDI listesiyle karşılaştır |
| Beyanname Kullanma Talimatı | Her kutunun nasıl doldurulacağı | Gümrük Yönetmeliği ekidir (form bankasında MEV kaydı) |

Kod listesi aracı yok; kodları kullanıcıya **kaynak sayfasıyla** ver, ezberden kod yazma.

---

## Formlar ve kılavuzlar (form bankası)

Form bankasında gümrük formları canlıda (mevzuat.gov.tr ekleri: Gümrük Yönetmeliği, Gümrük İşlemlerinin Kolaylaştırılması Yönetmeliği, transit, TIR, onaylanmış kişi, DİR/HİR, gözetim tebliğleri; ticaret.gov.tr: 59 ek belge). Arama `legal_search_forms`, getirme `legal_get_form`; araç yoksa aşağıdaki sayfalar.

| Belge | Form bankası / sayfa |
|---|---|
| Gümrük beyannamesi formları ve kullanma talimatı, sözlü beyan, özet beyan, emniyet ve güvenlik belgesi, gümrük statü belgesi, kontrol belgesi | Gümrük Yönetmeliği ekleri (MEV-13472-…); Ticaret Bakanlığı "Gümrük İdarelerinde Kullanılan Belgeler" |
| BTB formu ve başvuru formu, menşe şahadetnamesi | Aynı sayfa |
| Nihai kullanım izin başvurusu, izin belgesi, denetim formu, satış ve devir formu | Aynı sayfa |
| İşlenmiş tarım ürünleri beyan formu / analiz sonuç raporu | Aynı sayfa |
| Sektörel destekleme başvuru formu | Aynı sayfa (yalnız ticaret.gov.tr'de) |
| Özet beyan rehberi, FSH e-başvuru rehberi, yolcu rehberi | Bilgi Bankası |
| Gümrük laboratuvarlarının tahlil yapabildiği eşya listesi, tehlikeli eşya listesi, özel tertibat listesi | Bilgi Bankası |
| E-bilgilendirme broşürleri (11 konu; bağlayıcı değil) | E-Bilgilendirme Platformu |

Aynı formun mevzuat.gov.tr ve ticaret.gov.tr kopyası varsa form bankası onları eşdeğer bağla tek satırda gösterir; **güncel sürümü** kullan, eski sürümün tarihini çıktıda yaz.

---

## Sık hatalar
- 🟠 Kodları ezberden yazmak; liste değişir (özellikle rejim ve muafiyet kodları).
- 🟠 Eski "Bilgi Bankası" PDF'indeki kodu EDI listesiyle karşılaştırmadan kullanmak.
- 🟡 Bağlayıcı olmayan e-bilgilendirme broşürünü dayanak gibi göstermek.
