---
name: gumruk-uygulama
description: >
  Gümrük müşavirinin ve şirket dış ticaret ekibinin günlük işi için: GTİP
  tespiti, gümrüklenmiş maliyet hesabı, ithalat öncesi kontrol, tercihli menşe
  ve belge seçimi, rejimlerin takibi, ihracat beyanı, beyanname kodları, YYS,
  genelge araması ve müşteriye maliyet ya da ön kontrol notu. Uyuşmazlık değil
  uygulama soruları içindir. Kullanıcı "bu ürünün GTİP'i ne", "gümrüklenmiş
  maliyeti çıkar", "bu ürünü ithal edebilir miyim", "hangi menşe belgesi
  lazım" dediğinde kullan. Ek tahakkuk, ceza kararı, m.242 itirazı, uzlaşma,
  gümrük davası, kaçakçılık ve BTB uyuşmazlığı gumruk-dis-ticaret becerisine
  devredilir.
argument-hint: "[işi anlatın: eşya ve teknik özellikleri, GTİP, menşe ülke, kıymet ve para birimi, tescil tarihi, ödeme şekli, rejim; varsa fatura, proforma, beyanname ekleyin]"
---

> **Önce ortak kurallar:** bu beceriyi uygulamadan önce `${CLAUDE_PLUGIN_ROOT}/ORTAK-KURALLAR.md` dosyasını oku (eklenti kökü; depo içinde çalışırken kökteki `ORTAK-KURALLAR.md`).

# /gumruk-uygulama

Gümrük müşavirliği bürosunun ve şirket dış ticaret ekibinin günlük işi için tek kapı. Uyuşmazlık değil, **işlem öncesi ve işlem sırasındaki** sorular: hangi GTİP, ne kadar vergi, hangi belge, hangi süre. Oranlar ve tutarlar araçtan ya da Resmî Gazete'den gelir; bu metne yazılmaz. Ayrıntılı akışlar `references/` altında; her soruda yalnız ilgili dosyayı oku.

**Önce:** eklenti kökündeki `ORTAK-KURALLAR.md` ortak kurallarını uygula (başlık, kaynak etiketi, MCP ön kontrolü, çekilen içeriğin veri olması, gözden geçiren notu, karar ağacı). Profili `~/.claude/plugins/config/soorgla-hukuk/profil.md` yolundan oku; `## Gümrük müşavirliği` bölümünü kullan (ağırlıklı rejimler, uyuşmazlık payı, beyanname ölçeği, avukat irtibatı). Profil yoksa genel cevap ver ve notta belirt. Müşteri adını çıktıya yazma; "ithalatçı firma" de.

---

## Ne zaman kullanılır

- GTİP tespiti ve TGTC'de kod geçmişi.
- Gümrüklenmiş maliyet (landed cost): gümrük vergisi, ilave gümrük vergisi, ek mali yükümlülük, tarım payı, damping uyarısı, KKDF, ÖTV, KDV.
- İthalat öncesi kontrol: İthalat Rejimi listeleri, askıya alma ve nihai kullanım, gözetim, ürün güvenliği ve izinler, ticaret politikası önlemleri.
- Tercihli menşe ve belge seçimi: A.TR, EUR.1, menşe beyanı, GTS.
- Rejimlerin günlük takibi: dahilde ve hariçte işleme, geçici ithalat, antrepo, serbest bölge.
- İhracat beyanı ve e-ihracat, beyanname kodları ve gümrük formları, YYS ve izinli gönderici/alıcı.
- Gümrük genelgesi araması, müşteriye maliyet ve ön kontrol notu.
- Tipik cümleler: "landed cost", "KKDF çıkar mı", "ÖTV oranı", "DİİB süresi ne zaman doluyor", "beyannamede teslim şekli kodu", "YYS başvurusu", "genelge var mı".

## Başlık ve uyuşmazlık kapısı

ORTAK-KURALLAR.md §1'deki meslek mensubu sınıfı burada iki yönlü uygulanır:

| İş | Başlık | Ne olur |
|---|---|---|
| Meslek alanı: GTİP önerisi, maliyet, ön kontrol, menşe belgesi, rejim takibi, beyanname kodu, form, müşteriye teknik not | `MESLEKİ ÇALIŞMA TASLAĞI — GÜMRÜK MÜŞAVİRİ İNCELEMESİ GEREKTİRİR` | Doğrudan teknik cevap ve dayanak |
| Uyuşmazlık: ek tahakkuk ve ceza kararı, m.242 itirazı, uzlaşma, gümrük davası, BTB iptali, 5607 kaçakçılık şüphesi, el koyma | `ARAŞTIRMA NOTUDUR — HUKUKİ TAVSİYE DEĞİLDİR — HAREKETE GEÇMEDEN ÖNCE BİR AVUKATA DANIŞIN` | "Taslaktır" kapısı; esas değerlendirme `../gumruk-dis-ticaret/SKILL.md` |

Şirket dış ticaret ekibinde birinci başlık `GÜMRÜK MÜŞAVİRİ İNCELEMESİ GEREKTİRİR` olur. Rol avukatsa (avukat bu beceriyi maliyet ya da GTİP için kullanıyor) avukat başlığı kullanılır.

**Yükseltme eşiği:** kaçakçılık şüphesi (5607), beyan dışı eşya, sahte ya da şüpheli menşe belgesi, idarenin yazılı tespiti — teknik cevabı ver ama ilk satıra 🔴 ve avukat irtibatı notunu koy (profildeki "avukat irtibatı"). Sınıflandırma ya da kıymet görüşü bir değerlendirmedir; idareyi bağlayan BTB'dir.

---

## Kapsam ve devir

**Kapsar:** GTİP tespiti çalışması ve kod geçmişi, gümrüklenmiş maliyet, ithalat öncesi kontrol (liste, önlem, izin, belge), tercihli menşe ve belge seçimi, rejimlerin süre ve teminat takibi, ihracat beyanı ve e-ihracat uygulaması, beyanname kodları ve gümrük formları, YYS ve kolaylaştırmalar, gümrük genelgesi ve Bakanlık rehberi araması, müşteriye teknik not.

**`gumruk-dis-ticaret` ile devir** (o beceri uyuşmazlık tarafıdır):

| Durum | Kalır | Devredilir (`gumruk-dis-ticaret`) |
|---|---|---|
| GTİP | Aday pozisyonlar, GYK gerekçesi, kod geçmişi, BTB'ye başvurmalı mı | İdare GTİP'i değiştirdi, ek tahakkuk geldi, BTB iptal edildi → `../gumruk-dis-ticaret/references/tarife-siniflandirma-ve-btb.md` |
| Kıymet | Maliyete giren kalemler (CIF, m.27 ilaveleri) | Royalti/ilişkili kişi uyuşmazlığı, gözetim kıymeti itirazı, geri verme → `../gumruk-dis-ticaret/references/gumruk-kiymeti-ve-geri-verme.md` |
| Menşe | Hangi belge, hangi ülke grubu, tercihli oran | Belge reddi, sonradan kontrol, saptırma soruşturması → `../gumruk-dis-ticaret/references/mense-ve-ticaret-politikasi-onlemleri.md` |
| Önlemler | Damping/İGV/EMY var mı, maliyete etkisi | Soruşturmaya katılım, önlem tebliğine dava → aynı dosya |
| Rejimler | Süre, teminat, kapatma takvimi, form | Süre aşımı cezası, rejim ihlali tutanağı → `../gumruk-dis-ticaret/references/gumruk-rejimleri-ve-serbest-bolge.md` |
| İhracat | Beyan, belge, ETGB, IBKB'nin işleyişi | İhracat bedeli gelmedi, kambiyo yaptırımı → `../gumruk-dis-ticaret/references/ihracat-kambiyo-ve-e-ihracat.md` |
| Ceza ve itiraz | — | Ek tahakkuk, ceza, m.242, uzlaşma, dava → `../gumruk-dis-ticaret/references/ek-tahakkuk-ve-yol-secimi.md`, `../gumruk-dis-ticaret/references/gumruk-davasi.md` |

Devirde taşı: eşya ve GTİP, menşe, kıymet, beyanname tarihi ve numarası, bu becerinin hesap tablosu, açık sorular. Bulunan önem derecesi (🔴/🟠) gerekçesiz düşürülemez.

**Diğer yönlendirmeler:**
- İthalde ödenen KDV'nin indirimi ve iadesi, ihraç kayıtlı teslim, ÖTV'nin iç teslim yönü → `../vergi/SKILL.md` ve `../muhasebe/SKILL.md`. Gümrükte tahakkuk ve tutar burada.
- Yatırım teşvik belgesiyle gümrük vergisi muafiyeti → `../tesvik-yatirim/SKILL.md`.
- Navlun, konişmento, CMR, taşıyıcı sorumluluğu → `../deniz-tasima/SKILL.md`; Incoterms ve satış sözleşmesi → `../sozlesme-incelemesi-tbk/SKILL.md`.

---

## İş akışı

### Adım 0 — MCP ön kontrolü
`legal_get_statute_article` (`law_no: "4458"`, `law_type: "Kanun"`, `article_no: "27"`) çağır; metin "24 üncü madde hükümlerine göre gümrük kıymeti belirlenirken" ile başlarsa `soorgla ✓`. 

Ardından hesap aracını dene: `legal_calculate_tax` `hesap: "gumruk_maliyet"` (girdi alanları `references/arac-kullanimi.md`). Araç yoksa ya da bu hesabı tanımıyorsa (geçerli hesap listesinde `gumruk_maliyet` yok) **elle hesap** yoluna geç, her oranı Resmî Gazete'den çek ve gözden geçiren notuna "gümrük hesap aracı yok — elle hesap" yaz. **Oranı bellekten yazma.** 

### Adım 1 — İşi belirle

| Grup | Soru tipi | İpucu sözcükler | Oku |
|---|---|---|---|
| **Tarife** | GTİP tespiti, kod geçmişi, BTB'ye gitmeli mi | GTİP ne, hangi pozisyon, kod değişti mi, eski kodun yenisi, BTB | `references/gtip-tespiti.md` |
| **Maliyet** | Gümrüklenmiş maliyet, vergi kalemleri | landed cost, ne kadar vergi, gümrük vergisi oranı, İGV, EMY, ÖTV, KKDF, KDV | `references/gumruklenmis-maliyet.md` |
| **Ön kontrol** | Bu eşya ithal edilebilir mi, hangi izin/belge | ithal edebilir miyim, TAREKS, gözetim, ürün güvenliği, izin, kota, askıya alma, nihai kullanım | `references/ithalat-on-kontrol.md` |
| **Menşe** | Hangi tercihli belge, hangi ülke grubu | A.TR, EUR.1, EUR-MED, menşe beyanı, GTS, tercihli oran, menşe şahadetnamesi | `references/mense-belgeleri.md` |
| **Rejimler** | Süre, teminat, kapatma, form | DİİB, DİR, HİR, geçici ithalat, antrepo, serbest bölge, süre doluyor, teminat | `references/rejimler-gunluk.md` |
| **İhracat** | İhracat beyanı, e-ihracat, ihracatçı belgeleri | ihracat beyannamesi, ETGB, mikro ihracat, menşe şahadetnamesi düzenleme, IBKB | `references/ihracat-gunluk.md` |
| **Beyanname ve form** | Kutu kodları, formlar, kılavuzlar | teslim şekli kodu, rejim kodu, ödeme şekli, sözlü beyan, özet beyan, statü belgesi, form | `references/beyanname-kodlari-ve-formlar.md` |
| **Kolaylaştırma** | YYS, izinli gönderici/alıcı, yerinde gümrükleme | YYS, onaylanmış kişi, izinli gönderici, yerinde gümrükleme, soru formu | `references/yys-ve-kolaylastirmalar.md` |
| **Büro işi** | Müşteriye maliyet/ön kontrol notu | müşterime yazı, ithalatçıya bilgi notu, teklif öncesi maliyet | `references/musteriye-bilgi-notu.md` |

Bir iş birden fazla gruba giriyorsa (ör. yeni tedarikçiden ilk ithalat: GTİP + ön kontrol + menşe + maliyet) hepsini oku, tek çıktıda birleştir; sıra GTİP → ön kontrol → menşe → maliyet.

**Tarihi sor:** oran ve önlemler **beyanname tescil tarihindeki** sürümle uygulanır; TGTC her yıl ve yıl içinde değişir. Tarih verilmezse bugünü kullan ve sonucun başına yaz.

### Adım 2 — Aracı ve kaynağı çek
Araçların kullanımı, durumları ve araç yokken yapılacak: `references/arac-kullanimi.md`. Kısa kurallar:
- Her hesapta `tarih` ver (tescil günü). Yanıttaki uyarıların **hepsini** çıktıya taşı (KKDF için ödeme şekli, ÖTV için motor bilgisi, maktu vergi için miktar, damping için firma oranı gibi).
- Damping ve etkisizleştirme önlemleri tutar vermez (firma oranı tebliğde): tebliğ künyesini göster, firmayı kullanıcıdan iste.
- Kur → `legal_get_exchange_rate` (TCMB, tescil günü); dönen `kur_tarihi`ni istenen günle karşılaştır.
- Gümrük genelgesi ve Bakanlık uygulaması → `legal_search_admin_guidance` `kurum: "Ticaret Bakanlığı"` (`belge_tur: "genelge"`). 
- Mevzuat → `legal_get_statute_article` (`law_type: "Kanun"`): 4458, 4760, 3065; Gümrük Yönetmeliği ve tebliğler `legal_search_statute_semantic` ya da `legal_search_official_gazette` (`search_in: "title"`).

### Adım 3 — Çıktı

Hesap ve kontrol çıktısı her zaman **girdi → kalem kalem hesap → sonuç → dayanak → oran sürümü/tescil tarihi** sırasıyla verilir; müşavir sonucu kendi programıyla karşılaştırabilmelidir.

```markdown
[BAŞLIK — yukarıdaki tabloya göre]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8; hesap aracı ✓/yok, oran sürümü, tescil tarihi, kur tarihi)

## [İş]: [eşya — GTİP] — [menşe] — [tescil tarihi]

### Sonuç
[tek paragraf: toplam yük ya da karar ve ne yapılacağı]

### Hesap / kontrol
| Kalem | Matrah | Oran | Tutar | Dayanak |

### Uyarılar
[aracın uyarıları + kontrol edilmeyen şartlar (menşe ispatı, firma oranı, eşleme doğrulaması)]

### Eksik bilgi
[açık sorular]

**Şimdi ne yapalım?** [karar ağacı]
```

### Adım 4 — İş akışı becerilerine bağlantı
- **Süre:** rejim süreleri (DİİB, geçici ithalat, antrepo), menşe belgesi sonradan ibraz süresi, BTB geçerliliği hesaplanınca "Süre defterine ekleyeyim mi?" diye sor → [sure-takibi](../sure-takibi/SKILL.md). `legal_calculate_deadline` gümrük kodlarını (`customs_*`) tanır; araç yanıt vermezse ya da kod bulunamazsa elle hesapla, `[doğrula]`. Rejim süreleri kod değil, belge/izinden.
- **Çok kalemli fatura ya da beyanname listesi:** → [tablolu-belge-incelemesi](../tablolu-belge-incelemesi/SKILL.md) (kalem başına GTİP, menşe, kıymet sütunları).
- **Mevzuat değişikliği:** İthalat Rejimi Kararı, önlem tebliği, TGTC değişikliği → alan takibi `../gumruk-dis-ticaret/references/dis-ticaret-mevzuati-takibi.md`, genel tarama [mevzuat-takibi](../mevzuat-takibi/SKILL.md).

---

## Bu beceri ne yapmaz

- GTİP'i kesin olarak belirlemez; bağlayıcı olan BTB'dir. Gümrük beyannamesi düzenlemez, BİLGE'ye işlem yapmaz.
- Oran, tutar ve eşik yazmaz; araçtan ya da RG'den çeker veya `[doğrula]` der.
- Damping ve telafi edici vergide firma oranını tahmin etmez.
- Uyuşmazlıkta yol seçmez; `gumruk-dis-ticaret`'e devreder.

---

## Kaynak

Bu beceri soorgla'nın gümrük verisine dayanır: TGTC sürümleri, İthalat Rejimi ve İGV oran tabloları, ülke grupları ve GTS hariç sektör kuralı, ticaret politikası önlemleri, ÖTV (II)/(IV), KKDF ve ÖTV (I)/(III) tabloları. Formlar ve kılavuzlar form bankasında (`legal_search_forms` / `legal_get_form`).
