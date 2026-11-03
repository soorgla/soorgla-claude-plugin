# Yabancılık unsuru: uygulanacak hukuk, tanıma ve tenfiz

**Ne zaman kullanılır:** eşlerden biri yabancı ya da çifte vatandaş; boşanma yurt dışında gerçekleşti ve Türkiye'de nüfusa işlenmesi gerekiyor; yabancı nafaka, velayet ya da tazminat kararının Türkiye'de icrası; Türkiye'de açılacak boşanmada hangi hukukun uygulanacağı. Çocuğun yurt dışına götürülmesi → `velayet-cocuk-ve-soybagi.md` §6.

**Kapsam sınırı (ORTAK-KURALLAR.md §2):** bu dosya yalnız kısa bir MÖHUK çerçevesi verir. Yabancı hukukun içeriği hakkında emin cevap verme: "Bu analiz Türk hukukuna göredir; olayda [ülke] unsuru var, o ülke hukuku farklı sonuç verebilir" de ve uzman yönlendirmesi öner.

---

## Yol seçimi

| Amaç | Yol | Dayanak |
|---|---|---|
| Yabancı **boşanma** (ya da butlan/iptal) kararını nüfusa işletmek | Önce **idari tanıma**: nüfus müdürlüğü ya da dış temsilcilik. Koşullar: tarafların birlikte başvurması (biri ölmüş ya da yabancıysa Türk vatandaşı tek başına); yetkili makamca verilmiş ve kesinleşmiş olması; Türk kamu düzenine açıkça aykırı olmaması | 5490 m.27/A |
| İdari tanıma reddedildi ya da koşullar yok (ör. birlikte başvuru yok) | **Tanıma davası** — aile mahkemesi | 5490 m.27/A-3; 5718 m.58; 4787 m.4/2 |
| Nafaka, tazminat, velayet, yargılama gideri gibi **icra** gerektiren hükümler | **Tenfiz davası** | 5718 m.50 vd., m.54 |
| Türkiye'de boşanma davası açmak | TMK 168 ve MÖHUK yetki kuralları; uygulanacak hukuk m.14 | 5718 m.14 |

Eski YAML yalnız tanıma ve tenfiz davasını sayıyordu; 2017'den beri var olan **idari tanıma** yolu eksikti. Bu yol çoğu basit dosyada davadan hızlıdır.

---

## Kontrol listesi

### 1. Tanıma mı, tenfiz mi?
- Tanımada m.54/1-a'daki **karşılıklılık** şartı aranmaz; diğer tenfiz şartları aranır.
- Tenfiz şartları (m.54): (a) karşılıklılık; (b) Türk mahkemelerinin münhasır yetkisine girmeyen konu, ya da davalının itirazı hâlinde dava veya taraflarla gerçek ilişkisi olmayan aşırı yetki bulunmaması; (c) kamu düzenine açık aykırılık olmaması; (ç) usulüne uygun çağrı ve temsil, savunma hakkı.
- Eski YAML'daki "boşanma kararları çok eşlilik vb. değilse genelde kamu düzenine aykırı değildir" ifadesi bir eğilimdir, kural değildir `[incele]`.

### 2. Belgeler
- Kararın aslı ya da onaylı örneği, **kesinleşme şerhi** ya da kesinleştiğini gösteren yazı, onaylı Türkçe çeviri. Kanun "o ülke makamlarınca usulen onanmış" der; bu onay pratikte apostil (Lahey 1961 Sözleşmesine taraf ülke) ya da konsolosluk onayıdır `[doğrula]`. Eksik belge davanın reddine yol açabilir 🟠.

### 3. Uygulanacak hukuk (Türkiye'de açılan dava)
- Boşanma ve ayrılık sebepleri ile hükümleri: eşlerin **ortak millî hukuku**; ayrı vatandaşlıkta **ortak mutad mesken hukuku**; o da yoksa **Türk hukuku** (m.14/1).
- Boşanmış eşler arası nafaka ve boşanmada velayet de m.14/1'e tabidir (m.14/2-3).
- **Geçici tedbirlere** her durumda Türk hukuku uygulanır (m.14/4).
- Mal rejimi için ayrı bağlama kuralı vardır (m.15): eşler evlenme anındaki mutad mesken ya da millî hukuklarından birini açıkça seçebilir; seçim yoksa sırasıyla ortak millî hukuk, ortak mutad mesken hukuku, Türk hukuku; tasfiyede taşınmazlara bulundukları ülke hukuku uygulanır.
- Mirasa uygulanacak hukuk: ölenin millî hukuku (m.20/1); Türkiye'deki taşınmazlara Türk hukuku → `mirascilik-sakli-pay-ve-tenkis.md`.

### 4. Görev ve iş bölümü
- Aile hukukuna ilişkin yabancı kararların tanınması ve tenfizi: aile mahkemesi (4787 m.4/2). 4787 metni hâlâ eski MÖHUK'a (2675) atıf yapıyor; uygulamada 5718 anlaşılır `[doğrula]`.
- Temyizde: esas davaya ait hükmü incelemekle görevli daire. Aile kararlarında 2. HD.

### 5. Yabancı para nafaka
- Döviz cinsinden nafakanın TL karşılığı → `legal_get_exchange_rate` (karar tarihi ve ödeme tarihi ayrı) `[incele]`.

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "5718" article_no: "14" | "15" | "20" | "50" | "51" | "53" | "54" | "58"
legal_search_statute law_no: "5490" query: "yabancı ülke boşanma kararları nüfus kütüğüne tescil" # m.27/A harfli madde
legal_get_statute_article law_no: "4787" article_no: "4"
legal_search_cases mahkeme: "yargitay" daire: "2. Hukuk Dairesi" sorgu: "<yabancı boşanma kararının tanınması kesinleşme şerhi savunma hakkı>"
legal_search_statute_semantic sorgu: "yabancı boşanma kararlarının nüfusa tescili yönetmelik"
legal_get_exchange_rate
```
Ek kaynak: "uluslararası antlaşma (Lahey 1980)" → antlaşma metni katalogda olmayabilir; `legal_search_statute_semantic` ile dene, yoksa `[model bilgisi — doğrulayın]`.

---

## Görüşme soruları

1. Tarafların vatandaşlıkları (çifte vatandaşlık dahil) ve mutad meskenleri?
2. Karar hangi ülkede, hangi makamca (mahkeme, belediye, noter), hangi tarihte verildi? Kesinleşti mi?
3. Karar neyi kapsıyor: yalnız boşanma mı, nafaka/velayet/mal da var mı?
4. Karşı taraf davaya katıldı mı, tebligat usulüne uygun yapıldı mı?
5. Karşı taraf idari tanıma için birlikte başvurmaya razı mı?
6. Belgeler: apostil, çeviri, kesinleşme yazısı?

## Çıktı iskeleti

```markdown
## Yabancılık unsuru değerlendirmesi: [müvekkil] — [tarih]
### Sonuç (önerilen yol: idari tanıma / tanıma davası / tenfiz davası / Türkiye'de dava)
### Şart kontrolü
| Şart | Var/Yok | Belge | Not |
### Uygulanacak hukuk (Türkiye'de dava ise)
### Belgeler listesi
### Yabancı hukuk uyarısı
### Eksik bilgi
```

## Sık hatalar

- İdari tanıma yolunu (5490 m.27/A) atlayıp doğrudan dava önermek.
- Tanımada karşılıklılık aramak.
- Nafaka ve velayet hükmünü "tanıma" ile icra edilebilir sanmak (tenfiz gerekir).
- Yabancı hukukun içeriği hakkında emin cevap vermek.

---
