# Başvuru ve dava iskeletleri — EKAP e-form alanları ve ivedi dava unsurları

Bu dosya **kurgu yazmaz**. İddiaların seçimi, süre, ehliyet, bedel, iade ve dava stratejisi `../../ihale-sikayet/SKILL.md`'dedir (yazılmadıysa `../../kamu-ihale/references/sikayet-kik-ve-dava.md`). Dilekçenin **tam metin iskeleti** `../../idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md`'dedir. Buradaki iş: o metni EKAP'taki **resmî e-formun alanlarına** eşlemek, zorunlu alanı ve eki eksik bırakmamak.

Sıra (ORTAK-KURALLAR.md §13): tür ve süre → eksik bilgi → (bedel / harç) → atıflar MCP'den → çıktı → sunma kapısı.

---

## 1. Süre (önce)

| Başvuru | Süre | `legal_calculate_deadline` | Dayanak |
|---|---|---|---|
| İdareye e-şikâyet | farkına varmayı izleyen 10 gün (21/b-c 5 gün); sözleşmeden önce | `kik_complaint`; 21/b-c `kik_complaint_21bc` (ikisi de canlı) | 4734 m.55/1 |
| İlan/doküman şikâyeti | ilana yansıyan hususta (benzer iş, iş deneyimi oranı, yeterlik) **ilk ilandan**, diğerlerinde doküman indirmeden 10 gün + ihale tarihinden en geç 3 iş günü önce; hangisi önceyse | `kik_complaint_before_tender` (canlı, 10 gün); 3 iş günü sınırını araç hesaplamaz → `legal_check_holiday` ile elle `[incele]` | 4734 m.55/1-2 |
| Açıklama talebi (şikâyet değildir) | ihaleden 20 gün öncesine kadar yazılı; **şikâyet süresini durdurmaz** — iki son gün birlikte gösterilir | kod yok, elle | 4734 m.29 |
| Kuruma e-itirazen şikâyet | idare kararının bildirimini izleyen 10 gün; karar yoksa 10 günlük karar süresinin bitiminden 10 gün; iptal kararına karşı 5 gün | `kik_objection`, `kik_objection_no_decision`, `kik_objection_cancellation` (canlı) | 4734 m.55/4, m.56/1 |
| Kurul kararına dava | tebliğden 30 gün (ivedi yargılama) | `kik_lawsuit` (canlı) | 4734 m.57; İYUK m.20/A |

Kod yoksa madde metninden elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[incele]` işaretle. Süre geçmiş / 7 günden az → 🔴. Başvuru tarihi kayda giriş tarihidir (12766 m.9/4-5) `[soorgla]`; e-başvuruda EKAP gönderim zamanı esas `[doğrula]`.

## 2. E-şikâyet başvuru dilekçesi — KİK112

E-form KİK112 (V1, 18.07.2024 2024/DK.D-133) `[KİK e-form listesi 2026-10-31 — doğrula]`; form bankası kimliği `KIK-KIK112-<TÜR>`. Dayanak: 4734 m.54/3-5; İhalelere Yönelik Başvurular Hakkında Yönetmelik (`12766`) m.8/2 (dilekçe unsurları), m.8/3 (farkına varma tarihi), m.8/4 (yetki belgeleri), m.8/11 (faaliyet belgesi) `[soorgla]`.

| # | Form alanı | Doldurma kuralı | Eksikse |
|---|---|---|---|
| 1 | Tarih | gönderim günü | — |
| 2 | İhaleyi yapan idarenin adı ve adresi | ilandaki gibi | 🟠 |
| 3 | Başvuru sahibi ve MERSİS no | ad-soyad / ticaret unvanı | 🔴 (m.54/4-a) |
| 4 | TCKN (gerçek kişi) / VKN (tüzel kişi) | — | 🟠 |
| 5 | Vekili / temsilcisi | avukat değilse vekâletnamenin noterlik adı, tarihi, yevmiye no | 🟠 |
| 6 | İKN ve ihalenin adı | — | 🔴 (m.54/4-b) |
| 7 | Şikâyet konusu işlemin **farkına varıldığı / tebliğ edildiği tarih** | belgesiyle (KİK025 tebliği, EKAP indirme, ilan) | 🔴 (m.54/4-c) — süre denetimi buna dayanır |
| 8 | Şikâyet konusu işlem ve **nedenleri** | işlemin hangi yönden mevzuata aykırı olduğu ve kanıtları — **iddialar numaralı, her biri tek husus** (itirazen şikâyette yeni iddia eklenemez) | 🔴 (m.54/4-d) |
| 9 | Talep cümlesi | formdaki kalıp + istenen sonuç (düzeltici işlem / iptal) | 🟡 |
| 10 | Ad SOYADI / unvan, **e-imza** | — | 🔴 imzasız başvuru |

**Ekler (KİK112 dipnotu):** I- temsile yetki belgeleri — gerçek kişi bizzat: belge yok; avukatsız temsilci: vekâletname aslı/onaylı sureti + vekilin imza beyannamesi (noterlik bilgisi yazılırsa belge gerekmez); avukat: baro pulu yapıştırılmış vekâletname aslı ya da avukat/noter onaylı sureti; tüzel kişi bizzat: ticaret sicil tasdiknamesi ya da TTSG (MERSİS yazılırsa gerekmez) + imzalayanın noter tasdikli imza beyannamesi. II- şikâyetle ilgili diğer belgeler.

**Notlar (KİK112):** teklif zarfında idareye zaten verilmiş belgeler eklenmez; aynı kişinin birden fazla ihaleye, birden fazla kişinin aynı ihaleye tek dilekçeyle başvurusu yasak; **ilan ve doküman şikâyetinde ihale konusu alanda faaliyet gösterildiğine dair belge eklenmesi zorunlu**.

## 3. E-itirazen şikâyet başvuru dilekçesi — KİK114

E-form KİK114 (V1, 2024/DK.D-133) `[KİK e-form listesi 2026-10-31 — doğrula]`; form bankası kimliği `KIK-KIK114-<TÜR>`. Muhatap: "KAMU İHALE KURUMUNA — ANKARA". Dayanak: 4734 m.54, m.56; Yönetmelik `12766` m.8/5 (ekler), m.8/10 (iddia sınırı), m.8/12 (iddia ayrımı; Ek: RG-9/4/2026-33219) `[soorgla]`; Başvurular Tebliğindeki karşılık madde `[model bilgisi — doğrulayın]` (ayrıntı `idari-ve-kurum-basvurulari`).

| # | Form alanı (KİK114 sırası) | Kural |
|---|---|---|
| 1 | Tarih | — |
| 2 | Başvuru sahibi, MERSİS; TCKN/VKN | KİK112 ile aynı kişi |
| 3 | Vekil / temsilci | KİK112 ile aynı kural |
| 4 | İhaleyi yapan idare ve adresi; İKN; ihalenin adı | — |
| 5 | **Dokümanın EKAP hesabına girilerek indirildiği tarih** | doküman şikâyetinde sürenin başlangıcı |
| 6 | İdareye şikâyet edilen işlemin farkına varıldığı / tebliğ tarihi | şikâyet dilekçesindekiyle aynı |
| 7 | İdareye **şikâyet başvurusu tarihi** (m.55) | — |
| 8 | İdarenin şikâyet kararının **bildirim tarihi** — karar yoksa bu durum yazılır ve 10 günlük karar süresinin bitimini izleyen günden itibaren süre içinde başvurulur | 🔴 tarih tutarsızlığı süre reddine yol açar |
| 9 | İtirazen şikâyet konusu işlemler ve nedenleri — **yalnız şikâyette ileri sürülen iddialar** ve idare kararında belirlenen hususlar; numaralı, Tebliğ'deki ayrı/tek iddia ayrımıyla | — |
| 10 | Talep cümlesi ("Kurumunuzun nihai kararı üzerine yargıya başvuru hakkımız saklı olmak kaydıyla…") + istenen sonuç | — |
| 11 | Ad SOYADI / unvan, e-imza | — |

**Ekler (KİK114):** I- temsil belgeleri (KİK112'deki kurallar + **ortak girişimde** ortak girişim beyannamesi/sözleşmesi, pilot dışı ortak başvuruyorsa temsil yetki belgesi); II- idareye verilen şikâyet dilekçesinin bir örneği; III- idarenin şikâyet kararının bir örneği; IV- **başvuru bedeli dekontu** (Kurumun kurumsal hesabının bulunduğu bankalardan birine — form T.C. Ziraat, Vakıflar ve Halk Bankasını sayıyor); V- başvuru teminatı dekontu (teminat alınacak hâllerde; yürürlükte CB kararı var mı `[doğrula]`); VI- diğer belgeler.

**Başvuru bedeli:** tutar yaklaşık maliyete göre dilimli; **dilekçeye ya da bu dosyaya tutar yazılmaz** → `legal_get_social_parameters` (`ihale_itirazen_sikayet_dilim*`) ya da `legal_calculate_tender` `usul_kontrol`; başvuru tarihinin dönemi. Haklılık oranına göre iade iddia sayımına bağlıdır → `ihale-sikayet`.

## 4. İvedi dava dilekçesi — ihaleye özgü unsurlar

Tam iskelet: `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`. Esas ve strateji `ihale-sikayet`. Bu bölüm, ortak iskelete **eklenecek** ihaleye özgü unsurları sayar.

| Unsur | İhale davasında |
|---|---|
| Görevli/yetkili mahkeme | Kurul kararına karşı Ankara idare mahkemeleri: özel hüküm yoksa işlemi yapan merciin bulunduğu yer (İYUK m.32/1), Kurumun merkezi Ankara (4734 m.53/a) `[soorgla]`; başlık "ANKARA NÖBETÇİ İDARE MAHKEMESİ BAŞKANLIĞINA" kalıbı `[incele]` |
| Davalı | Kamu İhale Kurumu; ihaleyi yapan idare davaya katılabilir (müdahil; İYUK m.31/1 → HMK) `[soorgla]` |
| Dava konusu işlem | Kurul kararının tarihi ve sayısı (ör. `[2026/UH.__-____]`), tebliğ tarihi; MK kararıysa etkilediği önceki karar |
| Süre ve usul cümlesi | "İvedi yargılama usulüne tabi olup dava açma süresi 30 gündür (2577 m.20/A)"; 2577 m.11 başvurusu uygulanmaz |
| Yürütmenin durdurulması | YD istemi yazılabilir; ivedi usulde YD kararına itiraz yok (İYUK m.20/A-2) — istemi tek seferde güçlü kur |
| Açıklamalar | itirazen şikâyetteki **numaralı iddialar**la birebir; Kurulun her iddiaya verdiği gerekçe → neden hukuka aykırı; yeni iddia sınırı `[incele]` |
| Emsal | son 3 yıldan en az bir Danıştay kararının tam metni (`legal_get_case_document`); KİK kararı emsal gösteriliyorsa **MK etkisi** kontrolü (karar başlığındaki "Mahkeme etkisi" satırı) |
| Harç | `legal_calculate_court_fee`; 0 TL dönerse "harç yok" sayma (`../../hesaplamalar/references/harc.md`) |
| Deliller | ihale işlem dosyası, şikâyet ve itirazen şikâyet dilekçeleri, idare kararı, Kurul kararı ve tebliğ belgesi |
| Kanun yolu bilgisi (çıktının sonunda, metin dışında) | istinaf yok; nihai karara tebliğden 15 gün içinde doğrudan Danıştay'a temyiz → `kanun-yollari-dilekce` |

**Yasaklama kararı** ivedi usule tabi değildir (genel 60 gün, istinaf/temyiz genel hükümler) → `kamu-ihale/references/yasak-fiil-ve-yasaklama.md`.

## 5. Çıktı ve kapı

Çıktı sırası ORTAK-KURALLAR.md §13/5: taslak başlığı → gözden geçiren notu → süre tablosu → **form alanları tablosu** (alan → içerik → kaynak) → serbest metin bölümü (iddialar ve gerekçe). EKAP'ta form doldurulurken metin alanına yapıştırılacak blok ayrıca verilir. Hiçbir başvuru avukat onayı olmadan "gönderilebilir" işaretlenmez; bu beceri EKAP'a başvuru yapmaz, bedel yatırmaz (ORTAK-KURALLAR.md §13/7).

## Sık hatalar

- 🔴 Farkına varma tarihini belgesiz yazmak; KİK114'te şikâyet ve bildirim tarihlerini dilekçeyle tutarsız girmek.
- 🔴 KİK114'e şikâyette olmayan iddia eklemek.
- 🔴 Doküman şikâyetinde "ihale konusu alanda faaliyet" belgesini eklememek (KİK112 not 3).
- 🟠 Avukatsız temsilde noterlik/yevmiye bilgisi ya da imza beyannamesi eksik.
- 🟠 Bedeli kanundaki taban tutardan yatırmak.
