# Aile içi şiddet ve 6284 sayılı Kanun kapsamında tedbirler

**Ne zaman kullanılır:** anlatımda eş, eski eş, birlikte yaşanan kişi ya da aile bireyinden şiddet, tehdit, ısrarlı takip, ekonomik şiddet var; koruma ve uzaklaştırma kararı isteniyor; tedbir kararına itiraz ediliyor; tedbir kararına aykırılık var. **Bu dosya, diğer bütün aile dosyalarının önüne geçer** (SKILL.md Adım 0).

Bu referans eski YAML'larda yalnız birer satırla ("6284 — uzaklaştırma kararları için") anılıyordu; kontrol listesi sıfırdan yazıldı. Upstream `legal-clinic/client-intake` becerisindeki güvenlik sorusu ve "acil" triyaj sınıfı uyarlandı.

---

## Önce: acil durum ve gizlilik

- Hayati tehlike varsa: 112'yi aramasını ve en yakın kolluğa gitmesini söyle. Kolluk amiri gecikmesinde sakınca bulunan hâllerde uzaklaştırma ve yaklaşmama tedbirlerini **kendisi** alabilir; hâkim 24 saat içinde onaylamazsa tedbir kalkar. 
- Barınma ve geçici koruma: mülki amir (kaymakam/vali) koruyucu tedbir verir; gecikmesinde sakınca varsa barınma ve geçici korumayı kolluk amiri alır ve mülki amir 48 saat içinde onaylar. 
- Tedbir **en çabuk ve en kolay ulaşılabilecek** yer hâkiminden, mülki amirden ya da kolluktan istenebilir. Başvuran kişinin kendisi, Aile ve Sosyal Hizmetler Bakanlığı, kolluk ya da Cumhuriyet savcısı isteyebilir. 
- **Avukat beklenmez:** 6284 başvurusu için "önce avukata danışın" kapısı uygulanmaz (SKILL.md Adım 6). Ama avukata erişim için baro adli yardım bürosunu hatırlat (ORTAK-KURALLAR.md §1).
- **Gizlilik:** korunan kişinin ve aile bireylerinin kimlik ve adres bilgileri resmî kayıtlarda gizli tutulabilir. Bunu talep listesine koy. Çıktıda adres yazma; karşı tarafa gidecek metinde yer verme. 
- Upstream'deki "yüksek gizlilik" uyarısı: şiddet dosyalarında konuşmaya gereğinden fazla tanımlayıcı bilgi girilmesini önerme; kullanıcı yalnız gerekli olguları vermeli.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| Tedbir kararı ilk defasında **en çok 6 ay** | 6284 m.8/2  | Şiddet tehlikesi sürüyorsa süre uzatılabilir, şekil değiştirilebilir. Bitiş tarihini takvime koy; uzatma talebini bitişten önce ver |
| Kolluk kararıyla alınan önleyici tedbir: hâkim onayı **24 saat** | 6284 m.5/2 | Onaylanmazsa kalkar |
| Kolluk kararıyla alınan koruyucu tedbir: mülki amir onayı **48 saat** | 6284 m.3/2 | |
| Tedbir kararlarına itiraz: tefhim ya da tebliğden **2 hafta**; itiraz mercii **1 hafta** içinde karar verir; karar kesindir | 6284 m.9  | İtiraz istinaf değildir; ret kararı yalnız korunan kişiye tebliğ edilir (m.8/4) |
| Tedbire aykırılık: zorlama hapsi **3-10 gün**; her tekrarda **15-30 gün**; toplam **6 ayı** geçemez | 6284 m.13  | Fiil ayrıca suç oluşturuyorsa ceza yargılaması da yapılır |

`legal_calculate_deadline` bu süreleri hesaplamaz; elle hesapla ve `[doğrula]` yaz.

---

## Kontrol listesi

### 1. Kapsam
- Korunan kişi: şiddete uğrayan ya da uğrama tehlikesi olan kadın, çocuk, aile bireyi ve tek taraflı ısrarlı takip mağduru. Evlilik koşulu yoktur; ev içi şiddet tanımı aynı haneyi paylaşmayan aile bireylerini de kapsar (m.2/1-b). 
- Şiddet türleri: fiziksel, cinsel, psikolojik, ekonomik; tehdit ve baskı da dahil `[doğrula]`.

### 2. Tedbir türleri
**Hâkim tarafından verilen önleyici tedbirler (m.5/1):** 
- (a) tehdit, hakaret, aşağılama içeren söz ve davranışta bulunmama;
- (b) ortak konuttan uzaklaştırma ve konutun korunan kişiye tahsisi;
- (c) korunan kişinin konutuna, okuluna, işyerine yaklaşmama;
- (ç) kişisel ilişkinin refakatçi eşliğinde yapılması, sınırlanması ya da kaldırılması;
- (d) yakınlarına, tanıklarına ve çocuklarına yaklaşmama;
- (e) eşyalara zarar vermeme;
- (f) iletişim araçlarıyla rahatsız etmeme;
- (g-ğ) silah teslimi;
- (h-ı) alkol veya madde kullanmama, tedavi.

**Yanında verilebilecekler:**
- 5395 koruyucu ve destekleyici tedbirler; TMK'ya göre velayet, kayyım, nafaka ve kişisel ilişki kararları (m.5/3).
- Talep olmasa bile **tedbir nafakası** (m.5/4).

**Mülki amir tarafından verilen koruyucu tedbirler (m.3/1):** barınma, geçici maddi yardım, danışmanlık, geçici koruma, kreş desteği. 

### 3. Delil
- Koruyucu tedbir kararı için şiddetin uygulandığına dair **delil ya da belge aranmaz**; önleyici tedbir geciktirilmeksizin verilir.  Kullanıcıya "delil yok diye başvurudan vazgeçmeyin" de.
- Yine de ileriki boşanma ve velayet davası için delilleri koru: darp raporu, mesaj, ses kaydı, tanık, kolluk tutanağı. Hukuka uygunluk `[incele]`.

### 4. Boşanma ve velayetle bağlantı
- 6284 kararları boşanma dosyasında kusur delili olarak kullanılabilir; kararın kendisi kusuru ispat etmez `[incele]`.
- Aile içi şiddet iddiası olan uyuşmazlık **arabuluculuğa elverişli değildir**. 
- Kişisel ilişki düzenlemesi şiddet nedeniyle sınırlanabilir (m.5/1-ç).
- Temyizde görevli daire: 2. HD.  Ama tedbir kararlarına itiraz m.9'a göre kesin karara bağlanır; Yargıtay'a giden 6284 işlerinin kapsamı `[incele]`.

### 5. Tedbir kararına karşı (şiddet uygulayan taraf adına)
- İtiraz süresi 2 hafta, merci aile mahkemesinin bir sonraki dairesi ya da asliye hukuk (m.9/2).
- İtirazda ileri sürülecekler: kararın süresi ve kapsamının orantısızlığı, kişisel ilişkinin tamamen kaldırılması, konutun tahsisi. Şiddet olgusunu inkâr etmek tek başına yeterli değildir (delil aranmaz kuralı) `[incele]`.
- Tedbire uyulması gerektiğini mutlaka yaz: aykırılık zorlama hapsi doğurur (m.13).

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6284"  article_no: "1" | "2" | "3" | "4" | "5" | "8" | "9" | "13"
legal_search_statute_semantic  sorgu: "6284 uygulama yönetmeliği tedbir kararı başvuru"  mevzuat_tur: "cb_yonetmeligi"
legal_search_cases  mahkeme: "yargitay"  daire: "2. Hukuk Dairesi"  sorgu: "<6284 tedbir kararı itiraz>"
legal_search_cases  mahkeme: "anayasa"  sorgu: "<6284 uzaklaştırma kararı bireysel başvuru>"
legal_search_official_gazette  query: "6284 sayılı"  date_from: "<son 2 yıl>"
```

---

## Görüşme soruları

1. Şu anda güvende misiniz? Şiddet uygulayan kişi aynı evde mi?
2. Son olay ne zaman oldu? Daha önceki olaylar?
3. Çocuklar var mı, onlar da şiddete maruz kaldı mı?
4. Silah var mı?
5. Daha önce tedbir kararı verildi mi? Bitiş tarihi? İhlal edildi mi?
6. Hangi tedbirleri istiyorsunuz: uzaklaştırma, yaklaşmama, iletişim yasağı, konutun size tahsisi, nafaka, adres gizliliği?
7. Barınma ya da maddi destek ihtiyacı var mı?
8. (Karşı taraf adına) Karar ne zaman tebliğ edildi, hangi tedbirler var?

## Çıktı iskeleti

```markdown
## 🔴 Güvenlik — ilk yapılacaklar
1. [acil hat / kolluk / en yakın aile mahkemesi]
2. [adres gizliliği talebi]
## 6284 başvuru taslağı (TASLAK)
- Başvuran: [___]  (adres yazılmaz — gizlilik talebi)
- Şiddet uygulayan: [___]
- Olaylar (tarih sırasıyla, kısa): …
- İstenen tedbirler: [m.5/1 bentleri] + [m.5/3 velayet/nafaka/kişisel ilişki] + [m.8/6 gizlilik]
- Süre: [en çok 6 ay — uzatma notu]
## Süreler
| İşlem | Tarih | Son gün | Dayanak |
## Boşanma / velayet dosyasıyla bağlantı
## Eksik bilgi
```

## Sık hatalar

- Delil yok diye başvuruyu ertelemek (koruyucu tedbirde delil aranmaz).
- 6 aylık sürenin bitişini takip etmemek.
- Tedbir kararına itirazı istinaf dilekçesi gibi yazmak.
- Korunan kişinin adresini çıktıya ya da karşı tarafa gidecek metne yazmak.
- Şiddet dosyasında arabuluculuk önermek.

---

