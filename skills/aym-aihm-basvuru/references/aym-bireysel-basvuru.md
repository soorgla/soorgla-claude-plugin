# Anayasa Mahkemesi bireysel başvurusu

## Ne zaman kullanılır

Kamu gücünün bir işlemi, eylemi ya da ihmali nedeniyle Anayasa'da güvence altına alınmış ve aynı zamanda AİHS ve Türkiye'nin taraf olduğu ek protokoller kapsamındaki bir hakkın ihlal edildiği iddiası varsa ve kanunda öngörülen idari ve yargısal başvuru yollarının tamamı tüketildiyse kullanılır.

Kullanılmaz:
- Kanun, CBK ve düzenleyici idari işlem aleyhine doğrudan; AYM kararları ve Anayasa'nın yargı denetimi dışında bıraktığı işlemler aleyhine.
- Kamu tüzel kişileri; özel hukuk tüzel kişileri yalnız tüzel kişiliğe ait hakları için başvurabilir; yalnız Türk vatandaşlarına tanınan haklarda yabancılar başvuramaz.
- Başvurucunun **güncel ve kişisel** bir hakkı **doğrudan** etkilenmemişse.

---

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| **30 gün** | Başvuru yollarının tüketildiği tarih; başvuru yolu öngörülmemişse ihlalin öğrenildiği tarih | 6216 m.47/5; AYM İçtüzüğü m.64/1 | `legal_calculate_deadline` hesaplamaz → elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` |
| Mazeret: **15 gün** | Mazeretin kalktığı tarih | 6216 m.47/5; İçtüzük m.64/2 | Mazereti belgeleyen delillerle birlikte; önce mazeret incelenir |
| Eksiklik tamamlama: **en çok 15 gün** | Yazı işlerinin bildirimi | 6216 m.47/6 | Tamamlanmazsa ret uyarısı |

**Başlangıç tarihi tuzağı 🔴.** Eski YAML "nihai kararın tebliğinden/öğrenilmesinden" diyordu; kanun "tüketildiği tarih" der, AYM uygulamada **öğrenme** tarihini esas alır ve tebliğden önce UYAP/e-Devlet üzerinden kararın açılıp okunduğu tarihi öğrenme sayar; ceza infaz kurumundaki başvurucu adına, onun rızasıyla üçüncü kişilerin UYAP'tan okuması da öğrenme sayılabilir. Kararın tebliğ edilmesi öngörülmüyorsa içeriğin kesin olarak öğrenilebileceği tarih esas alınır. Bu yüzden görüşmede **"kararı UYAP'tan ilk ne zaman gördünüz, siz ya da avukatınız?"** sorusunu mutlaka sor; emin değilse UYAP evrak işlem kütüğünü kontrol ettir ve **en erken** tarihi baz al.

**Makul süre iddiası:** yargılamanın uzunluğu şikâyeti doğrudan AYM'ye değil, önce 6384 sayılı Kanun kapsamında Tazminat Komisyonuna götürülür; aksi hâlde bu kısım tüketilmemiş sayılır Komisyona başvuru süresi ve usulü için 6384'ü ayrıca çek: makul süre iddiasında m.5/A (7499/28), diğer müracaatlarda m.5.

---

## Kabul edilebilirlik kontrol listesi

| # | Ölçüt | Dayanak | Kontrol |
|---|---|---|---|
| 1 | Süre (30 gün / mazeret) | 6216 m.47/5 | Yukarıdaki tablo; öğrenme tarihi kanıtı |
| 2 | Başvuru yollarının tüketilmesi | 6216 m.45/2 | Olağan kanun yollarının hepsi kullanıldı mı (istinaf, temyiz, itiraz)? Şikâyet kanun yolu aşamasında **özüyle** ileri sürüldü mü? İlk kez AYM'de ileri sürülen şikâyet tüketilmemiş sayılabilir `[incele]` |
| 3 | Kişi bakımından | 6216 m.46 | Başvurucu doğrudan, kişisel ve güncel olarak etkilenmiş mi; tüzel kişi ise hak tüzel kişiye mi ait? |
| 4 | Konu bakımından | 6216 m.45/1 | Hak hem Anayasa'da hem AİHS/ek protokollerde (Türkiye'nin taraf olduğu) korunuyor mu? Ortak koruma alanı dışındaki hak ihlali iddiası konu bakımından yetkisizlikle kabul edilemez. Kararlardaki örnekler: çalışma hakkı; yerleşme ve seyahat hürriyeti (Türkiye 4 No.lu Protokol'e taraf değil); yabancıların ülkeye girişi, sınır dışı edilme ve vatandaşlığa kabul gibi egemenlik alanındaki uyuşmazlıklarda adil yargılanma şikâyeti (AİHS m.6 kapsamı dışında). Ortak alana giren bir hakla (ör. özel ve aile hayatı) esaslı bağ somut verilerle gösterilirse şikâyet o hak yönünden incelenebilir `[incele]` |
| 5 | Zaman bakımından | 6216 geçici m.1/8 | AYM yalnız 23.09.2012'den sonra kesinleşen nihai işlem ve kararlar aleyhine başvuruları inceler |
| 6 | Anayasal ve kişisel önem; önemli zarar | 6216 m.48/2 | Anayasanın uygulanması ve yorumu ya da temel hakların kapsamı bakımından önem taşımayan **ve** başvurucunun önemli zarara uğramadığı başvurular kabul edilemez sayılabilir |
| 7 | Açıkça dayanaktan yoksunluk | 6216 m.48/2 | Şikâyet "kanun yolu şikâyeti" (dördüncü derece) mi? Bkz. SKILL.md "Sık hata" |
| 8 | Kötüye kullanma | 6216 m.51 | Yanıltıcı bilgi, hakaret içeren dil, olguları gizleme → disiplin para cezası riski |

İnceleme: kabul edilebilirlik komisyonlarda (oy birliği yoksa bölümde), esas bölümlerde yapılır; kabul edilemezlik kararları kesindir. Kabul edilebilirliğe karar verilirse başvuru Adalet Bakanlığına gönderilir, Bakanlık görüş bildirebilir; başvurucu bu görüşe karşı beyanda bulunabilir.

---

## Zorunlu unsurlar (resmî form)

Başvuru, İçtüzük ekindeki (EK-1) ve Mahkemenin internet sitesindeki **resmî başvuru formu** kullanılarak resmî dilde yapılır. Eski YAML "olaylar ve hukuki açıklamalar EK-1 olarak sunulur" diyordu; bu yanlış ve yanıltıcıdır: **EK-1 formun kendisidir.** Ayrıntılı açıklama ek metinle desteklenebilir; ancak formun zorunlu alanları boş bırakılıp "ekte" denmemeli `[incele]`.

**Formda yer alması gerekenler** (İçtüzük m.59/2 özet):
- (a)-(c) Başvurucu kimlik/iletişim bilgileri (tüzel kişide MERSİS/vergi no ve temsilci), avukat ya da kanuni temsilci bilgileri.
- (ç) Kamu gücünün işlem/eylem/ihmaline dair olayların **tarih sırasıyla** özeti.
- (d) Hangi güncel ve kişisel hakkın hangi nedenle ihlal edildiği, gerekçeler ve delillere ilişkin özlü açıklama.
- (e) Her hak ve ona ilişkin açıklamanın **ayrı ayrı** ve birbiriyle ilişkilendirilerek yazılması.
- (f) Başvuru yollarının tüketilmesine ilişkin aşamalar, tarih sırasıyla.
- (g) Yolların tüketildiği ya da ihlalin öğrenildiği tarih. (ğ) Varsa mazeret açıklaması.
- (h) Talepler. (ı) Mahkemede derdest başka başvuru numarası.
- (i) Kimliğin gizli tutulması talebi ve gerekçesi. (j) SMS/e-posta bilgilendirme tercihi.
- (k) İmza. (l) Varsa İçtüzük m.73 tedbir talebi ve gerekçesi.

Kanun düzeyinde de: kimlik ve adres, ihlal edilen hak ve dayanılan Anayasa hükümleri, ihlal gerekçeleri, tüketme aşamaları, tüketme/öğrenme tarihi, varsa zarar.

**Biçim:** form okunaklı ve özlü olmalı; ekler hariç **10 sayfayı** aşarsa ayrıca olayların özeti eklenir; ekler tarih sırasıyla numaralandırılıp dizi pusulasına bağlanır.

**Zorunlu ekler** (İçtüzük m.59/3): vekâletname/temsil belgesi · harç makbuzu (ya da adli yardım talebi ve mali durum belgeleri) · bizzat başvuruda kimlik örneği · tüzel kişide temsil yetkisi belgesi · **nihai kararı öğrenme tarihini gösteren belge** · ihlal iddiasını temellendiren belgelerin onaylı örnekleri · tazminat isteniyorsa zarar belgeleri · **olağan ve olağanüstü kanun yolu dilekçelerinin onaylı örnekleri** · varsa mazeret belgeleri. Sunulamayan belge için gerekçe yazılır (m.59/4). Avukatla başvuruda vekâletname şarttır.

**Başvuru yeri:** doğrudan ya da mahkemeler veya yurt dışı temsilcilikler vasıtasıyla. Elektronik başvuru (UYAP) imkânı `[model bilgisi — doğrulayın]`.

**Harç:** başvuru harca tabidir (6216 m.47/2). Tutarı yazma; `legal_calculate_court_fee` bu türü tanımıyor → AYM sitesinden/492 tarifesinden teyit, `[doğrula]`.

**Tedbir:** yaşam ya da maddi-manevi varlığa yönelik ciddi tehlike varsa formda (m.59/2-l) tedbir talep edilir; tedbir kararı verilirse esas hakkında en geç altı ay içinde karar verilir. Tedbir talebi olağan dışıdır; mülkiyet, para, ihale gibi konularda istenmesini önerme `[incele]`.

**Talep ve sonuç:** ihlal tespiti; ihlal mahkeme kararından kaynaklanıyorsa yeniden yargılama için dosyanın ilgili mahkemeye gönderilmesi; hukuki yarar yoksa tazminat ya da genel mahkemelerde dava yolu. Tazminat isteniyorsa kalemleri ve belgeleri ayrı yaz.

---

## Görüşme soruları (eski `data_schema` alanlarından)

1. **Başvurucu** (`applicant_info`): gerçek kişi mi tüzel kişi mi; vekil avukat kim; adli yardım gerekiyor mu?
2. **Nihai karar** (`final_decision_info`): hangi merci (Yargıtay/Danıştay/BAM/ilk derece kesin karar), tarih, esas/karar no, **tebliğ tarihi**, **UYAP'tan ilk görüldüğü tarih** (siz, avukatınız ya da başkası)?
3. Hangi kanun yollarına başvuruldu; dilekçelerin örnekleri elinizde mi? Şikâyet ettiğiniz hususu bu dilekçelerde ileri sürdünüz mü?
4. **İhlal edilen hak(lar)** (`violated_rights`): kullanıcının sözcükleriyle ne oldu; hangi hakka bağlanıyor (aday listeyi sen öner, seçimi avukata bırak `[incele]`)?
5. **Kronoloji** (`chronology_of_events`): olaydan nihai karara kadar tarihli adımlar.
6. **Zarar ve talep** (`conclusion_request`): yeniden yargılama mı, tazminat mı; tazminat kalemleri ve belgeleri?
7. Tedbir gerektiren ciddi tehlike var mı?
8. Kimliğin gizli tutulması isteniyor mu (çocuk, sağlık, cinsel hayat vb.)?
9. Aynı konuda AYM'de derdest başka başvuru ya da AİHM başvurusu var mı?
10. Yargılamanın uzunluğundan da şikâyet var mı? (→ Tazminat Komisyonu yolu)

Eski `legal_arguments` ve `relevant_precedents` alanları kullanıcıdan istenmez; beceri bunları MCP'den kurar.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6216" article_no: "45" | "46" | "47" | "48" | "49" | "50" | "51"
legal_get_statute_article law_no: "1" law_type: "17" article_no: "59" | "60" | "64" | "73" # AYM İçtüzüğü
legal_get_statute_article law_no: "2709" article_no: "148" # ve ihlal edilen hakkın maddesi
legal_search_statute_semantic sorgu: "<makul süre / Tazminat Komisyonu>" mevzuat_no: "6384"
legal_check_holiday tarih: "<hesaplanan son gün>"
legal_search_cases mahkeme: "anayasa" tarih_baslangic: "<bugün - 3 yıl>"
    sorgu: "<ör. gerekçeli karar hakkı esaslı iddianın karşılanmaması ihlal>"
legal_search_cases mahkeme: "anayasa" daire: "Genel Kurul" sorgu: "<ilke kararı>"
legal_search_cases mahkeme: "anayasa" sorgu: "<olay> süre aşımı kabul edilemez" # süre riskini sına
legal_get_case_document belge_id: "<seçilen güncel karar>" # en az bir tam metin
legal_search_cases mahkeme: "aihm" sorgu: "<aynı hak> Türkiye" # AYM metnine destek
```

---

## Dilekçe iskeleti (formun ek açıklama metni)

Eski `ui_config.blocks` sırası korunmuştur. Bu metin **resmî formun yerine geçmez**; formun (ç)-(h) alanlarını ayrıntılandıran ektir.

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

> ⚠️ Gözden geçiren notu …

### Kısa değerlendirme
[başvuru yapılabilir mi; en büyük kabul edilebilirlik riski]

### Süre tablosu
| Süre | Başlangıç | Son gün | Dayanak | Durum |
|---|---|---|---|---|
| Bireysel başvuru (30 gün) | [öğrenme tarihi] | [___] [doğrula] | 6216 m.47/5; İçtüzük m.64/1 [soorgla] | 🔴/🟠/✅ |

### Kabul edilebilirlik kontrolü
[8 maddelik liste, işaretli]

---

ANAYASA MAHKEMESİ BAŞKANLIĞINA
(Bireysel Başvuru Formu Ekidir)

BAŞVURUCU : [___]
VEKİLİ : [___]
NİHAİ KARAR : [merci], [tarih], E. [___] K. [___]; öğrenme tarihi [___]
KONU : [hak(lar)] ihlal edildiği iddiasıyla bireysel başvuru açıklamalarıdır.

A. OLAYLARIN ÖZETİ (Form ç)
1. [tarih] — [olay]
…

B. BAŞVURU YOLLARININ TÜKETİLMESİ (Form f-g)
1. [tarih] — [kanun yolu] — [sonuç]; ileri sürülen şikâyet: [___]
Son karar [tarih]te [nasıl] öğrenilmiştir; başvuru süresindedir.

C. İHLAL İDDİALARI (Form d-e) — her hak ayrı başlık
C.1. [Hak] (Anayasa m.[__]; AİHS m.[__])
  a) İlgili ilkeler — [AYM ilke kararı, soorgla atfı]
  b) Somut olay — [hakkın hangi güvencesi, nasıl ihlal edildi]
  c) Sonuç
C.2. …

D. EMSAL KARARLAR
- [AYM kararı — künye — neyi destekliyor] [soorgla]
- [AİHM Türkiye kararı — künye] [soorgla]

E. ZARAR (varsa)
[kalemler, belgeler]

F. SONUÇ VE İSTEM (Form h)
1. Başvurunun kabul edilebilir olduğuna,
2. [Hak]kın ihlal edildiğine,
3. İhlalin ve sonuçlarının ortadan kaldırılması için yeniden yargılama yapılmak üzere kararın bir örneğinin [mahkeme]ye gönderilmesine,
4. [Varsa] [___] TL manevi / [___] TL maddi tazminata,
5. Yargılama giderleri ve vekâlet ücretinin başvurucuya ödenmesine
karar verilmesini saygıyla arz ve talep ederim.

[tarih] [Başvurucu / Vekili — imza]

EKLER (dizi pusulası, tarih sırasıyla): 1. Vekâletname 2. Harç makbuzu 3. Nihai karar ve öğrenme tarihini gösteren belge 4. Kanun yolu dilekçeleri 5. …
```

---

## Sık hatalar

- 🔴 Süreyi tebliğden başlatmak; UYAP'tan daha önce okunmuşsa süre çoktan başlamış olabilir.
- 🔴 Kanun yolu dilekçesinde hiç ileri sürülmemiş şikâyeti ilk kez AYM'de ileri sürmek (tüketilmeme).
- 🟠 Delil değerlendirmesi ve yorum şikâyetini hak ihlali gibi sunmak (açıkça dayanaktan yoksunluk).
- 🟠 Bütün hakları tek paragrafta karıştırmak; m.59/2-e her hakkı ayrı ister.
- 🟠 Formu boş bırakıp "ekteki dilekçede" demek; formu 10 sayfadan uzun yazıp özet eklememek.
- 🟠 Kanun yolu dilekçelerinin ve öğrenme tarihini gösteren belgenin eklenmemesi.
- 🟡 Yargılamanın uzunluğunu Tazminat Komisyonuna gitmeden AYM'ye taşımak.
- 🟡 Eski YAML'daki "karar düzeltme" yolunu tüketilmesi gereken yol saymak; HMK ve CMK'da bugün bu yol yoktur, idari yargıda İYUK m.54 6545 ile mülga, yalnız geçiş hükmüne tabi eski dosyalarda kalmış olabilir `[incele]`.

---
