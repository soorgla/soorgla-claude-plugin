# Mal rejimi tasfiyesi: katılma alacağı, değer artış payı, katkı payı

**Ne zaman kullanılır:** boşanma ya da ölümle sona eren evlilikte malların paylaşımı; konut, araç, birikim, kredi, şirket payı gibi malların kişisel mal mı yoksa edinilmiş mal mı olduğunun belirlenmesi; 1.1.2002 öncesi edinilen mallar; mal kaçırma (eklenecek değerler); mal rejimi sözleşmesi. Ölümde eşin miras payı ayrı bir hesaptır → önce tasfiye, sonra miras (`mirascilik-sakli-pay-ve-tenkis.md`).

Temel ilke: edinilmiş mallara katılma rejimi bir **alacak hakkı** doğurur; diğer eşin malları üzerinde ortak mülkiyet doğurmaz. Eski YAML'daki "çalışarak alınan her şey ortaktır" ifadesi yanıltıcıdır; doğrusu: "tasfiyede diğer eşin artık değerinin yarısı kadar alacak hakkı vardır".

---

## Süre tablosu

| Süre / tarih | Dayanak | Not |
|---|---|---|
| Rejimin sona erme anı: boşanma ya da iptalde **dava tarihi**; ölümde ölüm tarihi | TMK 225 | Malların kapsamı bu tarihe göre; değerleri karar tarihine en yakın tarihe göre `[doğrula]` |
| **1.1.2002** — 743 sayılı eski MK dönemi (yasal rejim mal ayrılığı) ile TMK dönemi (edinilmiş mallara katılma) ayrımı | 4722 m.10 | Her mal için edinme ve ödeme tarihlerini ayır |
| Zamanaşımı: boşanma kararının **kesinleşmesinden 10 yıl** (TBK genel zamanaşımı) | 2. HD yerleşik uygulaması | **TMK 178'deki 1 yıl uygulanmaz.** Kısmi davada artırılan kısım için zamanaşımı ayrıca değerlendirilir `[incele]` |
| Eklenecek değerler: rejimin sona ermesinden önceki **1 yıl** içindeki rızasız karşılıksız kazandırmalar | TMK 229/1-1 | Katılma alacağını azaltma **kastıyla** yapılan devirlerde süre sınırı yok (229/1-2) |
| Boşanma davası sırasında mal kaçırma riski | İhtiyati tedbir | Tedbir → `hukuk-yargilamasi-dilekce` |

---

## Kontrol listesi

### 1. Hangi rejim, hangi dönem?
- Evlilik tarihi 1.1.2002 öncesi mi? Öyleyse 1.1.2002'ye kadar **mal ayrılığı**: o dönem için yalnız katkı payı alacağı, ispat yükü katkıyı iddia edende. 1.1.2002'den sonrası için edinilmiş mallara katılma.
- Mal rejimi sözleşmesi var mı (mal ayrılığı, paylaşmalı mal ayrılığı, mal ortaklığı)? Şekli ve tarihi `[incele]`.
- Yabancılık unsuru varsa uygulanacak hukuk MÖHUK'a göre belirlenir → `yabancilik-unsuru-ve-tanima.md`.

### 2. Mal grubu (TMK 219-220)
- **Edinilmiş mal:** çalışma karşılığı edinimler, sosyal güvenlik ve yardım kurumlarının ödemeleri, çalışma gücünün kaybı nedeniyle ödenen tazminatlar, kişisel malların gelirleri, edinilmiş malların yerine geçen değerler.
- **Kişisel mal:** kişisel kullanım eşyası; rejimin başında var olan ya da sonradan miras veya karşılıksız kazanma yoluyla edinilen mallar; manevi tazminat alacakları; kişisel malların yerine geçen değerler.
- Bir malın hangi grupta olduğunun belirlenmesi zorunlu ilk adımdır; davalı "kişisel maldır" diyorsa ispat yükü ona düşer; bir eşin bütün malları aksi ispat edilinceye kadar edinilmiş mal sayılır, kime ait olduğu ispatlanamayan mal paylı mülkiyette sayılır (TMK 222).
- Karma mallar: kredi ile alınan konut (evlilik öncesi peşinat + evlilik içinde kredi taksitleri + boşanma davasından sonra ödenen taksitler) → her dönem ayrı hesaplanır.

### 3. Hesap adımları
1. Her eşin edinilmiş mallarını sona erme tarihindeki kapsamıyla listele.
2. Eklenecek değerler (TMK 229) ve denkleştirme (TMK 230) ekle.
3. Edinilmiş mallara ilişkin borçları düş → **artık değer** (TMK 231). Artık değer negatifse sıfır sayılır (m.231/2: "Değer eksilmesi göz önüne alınmaz").
4. Değer artış payı (TMK 227): bir eşin diğerine ait malın edinilmesine, iyileştirilmesine ya da korunmasına karşılıksız katkısı oranında, maldaki değer artışından pay alır.
5. **Katılma alacağı:** her eş, diğer eşin artık değerinin yarısına hak kazanır; alacaklar **takas** edilir (TMK 236/1). Eski YAML'daki "Katılma Alacağı = Artık Değer / 2" formülü takası göstermediği için eksiktir.
6. **Zina ya da hayata kast** nedeniyle boşanmada hâkim, kusurlu eşin artık değerdeki payını hakkaniyete göre azaltabilir ya da kaldırabilir (TMK 236/2).
- Değerleme bilirkişiyle yapılır. Her tutar `[doğrula — bilirkişi]`. Faiz → `legal_get_legal_interest_rates`; başlangıcı (karar tarihi ya da dava tarihi) `[incele]`.

### 4. Mal kaçırma (TMK 229)
- Sona ermeden önceki 1 yıl içinde rızasız ve olağan hediye dışında karşılıksız kazandırmalar.
- Rejim sürerken katılma alacağını azaltma kastıyla yapılan devirler (süre sınırı yok).
- Karar, davanın kendisine **ihbar edilmesi** koşuluyla kazandırmadan yararlanan üçüncü kişiye karşı da ileri sürülebilir. Üçüncü kişiye dava ihbarını atlama 🟠.
- Eklenecek değer iddiasına ilişkin güncel uygulama →

### 5. Usul
- Görevli mahkeme: aile mahkemesi; temyizde 2. HD. Eski YAML'daki "kapatılan 8. HD" ifadesi yanlıştır; 8. HD kurulu, ama mal rejimi davalarına bakmıyor. Eski 8. HD kararlarını yalnız eski emsal olarak kullan. Geçiş: Yargıtay Birinci Başkanlık Kurulunun 02.07.2021 t. 211 s. iş bölümü kararı (RG 09.07.2021, 31536) ile mal rejimi temyizleri 2. HD'ye geçti; 8. HD Eylül 2021'den itibaren bu dosyaları 2. HD'ye gönderdi.
- Mal rejiminin sona ermesi tasfiye davalarının **görülebilirlik ön koşuludur**. Boşanma davasıyla birlikte açılırsa tefrik edilir; mal rejimini sona erdirecek boşanma davası derdestse usul ekonomisi gereği (HMK 30, 165/1) bekletici mesele yapılır. Boşanma davası reddedilip kesinleşmiş ve derdest başka boşanma davası yoksa tasfiye davası ön koşul yokluğundan usulden reddedilir; ancak hüküm anında eksiklik giderilmişse (yeni boşanma davası açılmışsa) HMK 115/3 gereği usulden ret yapılamaz, yeni dava bekletilir.
- Değer ve harç → `legal_calculate_court_fee`. **Belirsiz alacak davası (HMK 107) 7589 ile yürürlükten kaldırıldı** (RG 31.07.2026); bu tarihten sonra açılacak davada kısmi dava ve ıslah seçeneklerini, zamanaşımına etkisini ve görülmekte olan davalara geçişi `[incele]`.
- Tapu iptali ve tescil talebi: katılma alacağı alacak hakkıdır; aynî talep için ayrı hukuki dayanak gerekir (ör. paylı mülkiyetteki malın üstün yarar ispatı ve diğer payın ödenmesiyle bölünmeden verilmesi, TMK 226/2) `[incele]`.
- Ölümle sona ermede: sağ kalan eş önce katılma alacağını alır; sonra miras payı terekeden hesaplanır. Sağ kalan eş, ölen eşe ait birlikte yaşadıkları konut üzerinde katılma alacağına mahsuben (yetmezse bedel ekleyerek) **intifa veya oturma hakkı**, ev eşyası üzerinde mülkiyet isteyebilir; haklı sebep varsa konutta da mülkiyet tanınabilir (TMK 240).

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4721" article_no: "202" | "219" | "220" | "222" | "225" | "227" | "229" | "230" | "231" | "235" | "236" | "240"
legal_get_statute_article law_no: "4722" article_no: "10"
legal_search_cases mahkeme: "yargitay" daire: "2. Hukuk Dairesi" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. evlilikten önce alınan peşinat ve evlilik içinde ödenen konut kredisi taksitleri katılma alacağı hesabı>"
legal_search_cases mahkeme: "yargitay" daire: "Hukuk Genel Kurulu" sorgu: "<mal grubu, ispat yükü>"
legal_search_cases mahkeme: "yargitay" daire: "8. Hukuk Dairesi" tarih_bitis: "<geçiş tarihi>" # eski emsal
legal_get_case_document belge_id: "<seçilen karar>"
legal_get_legal_interest_rates
legal_calculate_court_fee
```
Ek kaynak: `mevzuat_turu: içtihadı birleştirme kararı` → sorguya "içtihadı birleştirme" ekle. `6098 TBK` (kefalet ve borçlar) → yalnız borçların düşülmesinde gerekirse.

---

## Görüşme soruları

1. Evlilik tarihi? Boşanma davası tarihi ve boşanmanın kesinleşme tarihi?
2. Mal rejimi sözleşmesi yapıldı mı?
3. Her mal için: kimin adına, ne zaman edinildi, nasıl ödendi (peşin, kredi, miras parası, evlilik öncesi birikim, eşin ailesinden yardım)? Belgeler (tapu, kredi sözleşmesi, banka dökümü)?
4. Kredi borcu ne zaman başladı, boşanma davasından sonra kim ödedi?
5. Boşanma davasından önceki 1 yıl içinde bağış ya da devir oldu mu? Kime?
6. Eşin şirket payı, işletmesi, banka hesabı, kıymetli maden, araç?
7. Boşanma sebebi zina ya da hayata kast mı?
8. Taraflardan biri yabancı mı ya da mal yurt dışında mı?

## Çıktı iskeleti

```markdown
## Mal rejimi tasfiyesi: [müvekkil] — [tarih]
### Sonuç
### Tarihler
| Evlilik | 01.01.2002 | Dava (sona erme) | Kesinleşme | Zamanaşımı sonu |
### Mal tablosu
| Mal | Malik | Edinme tarihi | Kaynak (kişisel/edinilmiş) | Dönem (öncesi/sonrası 2002) | Değer [doğrula] | Not |
### Hesap iskeleti
[artık değer formülü + girdiler; takas; 236/2 indirimi — her tutar [doğrula — bilirkişi]]
### Eklenecek değerler ve üçüncü kişiler
### Usul ve harç
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Katılma alacağına TMK 178'deki 1 yıllık süreyi uygulamak (doğrusu 10 yıl, kesinleşmeden).
- Rejimin sona erme anını boşanma kararının kesinleşmesi sanmak (doğrusu dava tarihi).
- 2002 öncesi ve sonrası ödemeleri tek kalemde hesaplamak.
- Edinilmiş mal üzerinde ortak mülkiyet varmış gibi tapu iptali istemek.
- Mal kaçırmada üçüncü kişiye davayı ihbar etmemek.
- Mal rejimi emsalinde "kapatılan 8. HD" demek.

---
