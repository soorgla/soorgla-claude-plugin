# Kısa kurulum (5 soru)

Upstream "quick start path" uyarlaması: yalnız çıktının biçimini en çok değiştiren beş alan sorulur, gerisi `[VARSAYILAN]` yazılır. Hedef 2 dakika. Sorular iki tura bölünür (bir turda en fazla 3 soru).

## Tur 1

**1. Kimsiniz?** (Her çıktının ilk satırındaki başlık buna göre seçilir.)

> 1. Avukatım (serbest, büro ortağı ya da büro çalışanı)
> 2. Stajyer avukatım
> 3. Şirket hukukçusuyum / şirket avukatıyım
> 4. Kamu görevlisiyim — 4a) hukuk müşaviri / kamu avukatı, 4b) hukukçu değilim (ihale, personel, mali birim…)
> 5. Avukat değilim; işim ya da kendi meselem için kullanıyorum — 5a) danışabileceğim bir avukat var, 5b) yok
> 6. Hukuk öğrencisiyim
> 7. Meslek mensubu ya da uzmanım — 7a) mali müşavir (SM / SMMM / YMM) ya da şirket finans/muhasebe ekibi, 7b) gümrük müşaviri, 7c) bilirkişi (aktüer, trafik kusur, hekim…), 7d) sigorta eksperi ya da sigorta şirketi hasar / rücu birimi
> 8. Hiçbiri — kendi cümlemle anlatayım

**2. Çoğunlukla hangi taraftasınız?** (Kontrol listelerinin vurgusu değişir: talep eden tarafta hak ve süre kaçırma, karşı tarafta ispat yükü ve usul hatası öne çıkar.)

> 1. Genelde talep eden (işçi, kiracı, alacaklı, tüketici, davacı, başvurucu)
> 2. Genelde karşı taraf (işveren, kiraya veren, borçlu, işletme, davalı, idare)
> 3. İkisi de / dosyaya göre değişir — her seferinde sorun
> 4. Alan alan farklı — (kısaca yazın: "işte işveren, kirada kiracı" gibi)

**3. En çok hangi alanlarda çalışıyorsunuz?** (Birden çok seçin; sıralama öncelik sayılır.)

> İş · Sosyal güvenlik · Kira · Sözleşme/borçlar · Tazminat ve trafik · İcra-iflas · Aile ve miras · Ticaret ve şirketler · Tüketici · KVKK · Fikri mülkiyet ve bilişim · Ceza · İdare, imar, kamulaştırma · Vergi · Kamu ihale ve hakediş · Kamu personeli · Sayıştay ve kamu zararı · Gümrük ve dış ticaret · Teşvik · Yabancılar ve vatandaşlık · Deniz ve taşıma · Gayrimenkul ve inşaat · Diğer: …

Rol 7a (mali müşavir, finans ekibi) ise 3. soru yerine muhasebe alan listesi: Bordro ve SGK · KDV ve muhtasar · Gelir/kurumlar beyanı · Yılsonu kapanış ve enflasyon düzeltmesi · e-Belge · Vergi incelemesi ve uzlaşma · KDV iadesi · Tasdik (YMM) · Şirket kuruluş/tasfiye işlemleri. 4. soru yerine: "Hangi ilde, hangi vergi dairesiyle çalışıyorsunuz?" (SMMM ücret tarifesi il grubuna göre değişir).

Rol 6 (öğrenci) ise 2. ve 3. soru yerine: "Hangi sınıftasınız ya da hangi sınava hazırlanıyorsunuz (HMGS, hâkimlik-savcılık)? Önce anlatayım mı, yoksa soru sorarak mı ilerleyelim?"

## Tur 2

**4. Hangi şehirde, hangi adliyede çalışıyorsunuz?** (Yetkili mahkeme ve merci başlığı önerisi; avukatı olmayan kullanıcı için baro adli yardım bürosu ve arabuluculuk bürosu hatırlatmasının ili.) Vatandaş için yalnız şehir yeterli.

**5. Çıktılar nasıl bir dille yazılsın?**

> 1. Hukukçu dili (terimler açıklanmadan)
> 2. Sade — hukukçu olmayan biri okuyacak
> 3. Çok sade — kısa cümle, her terimin yanında açıklama

Varsayılan: rol 1-4a → 1; rol 7 → 2 (meslek dili: kendi alanının terimleri açıklamasız, hukuk terimleri kısa açıklamalı); rol 4b, 5, 6 → 3. Avukat olmayan kullanıcıda ORTAK-KURALLAR.md §8 "sade açıklama" kuralı seçimden bağımsız olarak uygulanır.

## Cevapların işlenmesi

- Rol 8 (kutuya sığmayan) → serbest anlatımı al, en yakın başlık sınıfını (avukat/hukukçu ya da avukat olmayan) **kullanıcıya sorarak** belirle; kendin seçme.
- Rol 5b → kurulum sonunda SKILL.md "Rol, başlık ve kapı eşlemesi"ndeki avukat olmayan metnini ve baro adli yardım hatırlatmasını bir kez ver.
- Rol 4b → "Kurumunuzun hukuk müşavirliği avukat irtibatı olarak yazılsın mı?" (tek soru, isteğe bağlı).
- Rol 7c (bilirkişi) → taraf sorulmaz (bilirkişi tarafsızdır). Tek soru: "Hangi alanda rapor yazıyorsunuz: aktüerya, trafik kusuru, maluliyet, araç hasarı, diğer?" Profilin "Kaza ve bedensel zarar" bölümüne yaz. Dil varsayılanı 1.
- Rol 7d (sigorta) → taraf varsayılanı sigorta / zarar veren tarafı. Tek soru: "Ağırlıklı iş: hasar ve değer kaybı tespiti, tazminat ödemesi, rücu, Sigorta Tahkim'de cevap?" Dil varsayılanı 2.
- Rol 7a ve 7b → taraf sorusu yerine (varsayılan: mükellef / yükümlü tarafı, karşısında idare) iki kısa soru:
  > a) Müşterilerinizin uyuşmazlıklarında birlikte çalıştığınız bir avukat var mı? (ad isteğe bağlı) b) Aynı anda kaç müşteri ya da dosya takip ediyorsunuz: birkaç / onlarca / yüzlerce?
  Onlarca ve üstüyse süre defteri ve dosya klasörü önerilir (`sure-takibi`, `dosya-klasoru`). 7a → ana alanlara vergi ve sosyal güvenlik önerilir; 7b → gümrük ve dış ticaret. Profilin "Mali müşavirlik" ya da "Gümrük müşavirliği" bölümüne yaz. Müşteri adları profile yazılmaz.
- Taraf 4 → alan bazında tabloya yaz; söylenmeyen alanlar "her dosyada sor".
- Alanlarda "Tazminat ve trafik" varsa ve rol 1-3 ise (avukat, stajyer, şirket hukukçusu) tek ek soru: "Kaza dosyalarında çoğunlukla zarar gören tarafında mısınız, sigorta / zarar veren tarafında mı, dosyaya göre mi?" Alan bazında taraf tablosuna yaz.
- Alanlarda "Kamu ihale ve hakediş" varsa tek ek soru (taraf sorusunun yerine geçer):
  > İhalelerde hangi taraftasınız? 1) İdare (ihale yetkilisi, komisyon, satın alma) 2) Kendi firmam adına teklif veriyorum 3) Birden çok firma adına ihale danışmanlığı yapıyorum (doküman tarama, şikâyet, itirazen şikâyet) 4) Avukatım, müvekkile göre değişir
  Cevap 3 ise: "Aynı anda çok ihale takip ediyorsanız her ihale için bir dosya klasörü ve ortak süre defteri kurayım mı?" (`dosya-klasoru`, `sure-takibi`). Profilin "Kamu ihale" bölümüne yaz.
- Kullanıcı bir eşik ya da süre söylerse (ör. "30 işçinin altıyız ama iş güvencesi var sanıyorum") SKILL.md Adım 3 doğrulama kuralını uygula.
- Bağlantı kontrolü (SKILL.md Adım 2) kısa yolda da yapılır.

## Yazılan profil

`profil-sablonu.md` §1 yapısı; doldurulmayan bütün alanlar `[VARSAYILAN]` değeriyle:

| Alan | Varsayılan |
|---|---|
| Risk iştahı | Dengeli |
| Yükseltme kişisi | Avukat: "kendim karar veririm" · avukat olmayan: Avukat irtibatı satırı · stajyer: "staj avukatı — adı sorulacak" |
| Dilekçe biçimi, imza bloğu | ORTAK-KURALLAR.md §13/5 genel iskeleti; imza `[___]` |
| Sık kullanılan belgeler | Boş — karar ağacı genel sırayla önerir |
| UYAP/UETS/KEP | Bilinmiyor — dilekçe becerisi gerekirse sorar |
| yonlendirme_onayi | evet |
| İş hukuku bölümü | İş ana alansa iskelet `[VARSAYILAN]`; ayrıntı `is-hukuku` ilk kullanımında sorulur |
| Dosya çalışma alanları | kapalı |

## Kapanış cümlesi

> Tamam, profiliniz hazır: [rol] · [taraf] · [alanlar] · [şehir] · [dil]. Gerisini varsayılanla doldurdum: risk iştahı dengeli, dilekçeler genel iskeletle, imza bloğu boş. Bir çıktı size uymadığında genellikle bu varsayılanlardan biridir; çıktı hangisi olduğunu söyler. "Tam kurulum" deyince imza bloğu, dilekçe biçimi, yükseltme ve şablonları da ekleriz. Profil: `~/.claude/plugins/config/soorgla-hukuk/profil.md` (müvekkil bilgisi içermez).

Ardından SKILL.md Adım 6/4'teki kişiye özel 3-5 örnek iş.
