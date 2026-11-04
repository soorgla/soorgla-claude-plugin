# Hizmet tespiti ve sigortalılık başlangıcı

**Ne zaman kullanılır:** sigortasız (kayıt dışı) ya da eksik gün/düşük ücretle bildirilen çalışmanın tespiti; sigorta başlangıç tarihinin tespiti; prim günü eksikliğinin emeklilik tarihine etkisi. Aynı olaydan işçilik alacağı da isteniyorsa `is-hukuku` becerisini ayrıca çalıştır (farklı zamanaşımı ve arabuluculuk kuralları).

Temel ilke: fiili çalışma esastır; hizmet tespiti davaları kamu düzenine ilişkindir, vazgeçilmez sosyal güvenlik hakkı söz konusu olduğundan davadan feragat sonuç doğurmaz.  Hâkim taraf delilleriyle yetinmez, kendiliğinden araştırma ilkesiyle delil toplar (bordro ve komşu işyeri tanıkları, tapu kayıtları, muhtar/aza beyanı, gerekirse keşif); gerçek işverenin kim olduğu kuşkuluysa doğru işveren davaya dahil edilir. 

İki ayrı dava türünü karıştırma:
- **Hizmet akdine dayalı zorunlu sigortalılık tespiti** (işverene karşı): Kuruma önceden başvuru şartı **yoktur**. 
- **Sigorta başlangıç tarihinin tespiti / Kurum kaydının düzeltilmesi** (Kuruma karşı): 7036 m.4 uyarınca önce Kuruma başvuru zorunludur. 

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| Hizmetin geçtiği yılın sonundan itibaren **5 yıl** içinde dava | 5510 m.86/9  | Hak düşürücü; dava şartıdır, mahkeme her aşamada re'sen gözetir. 🔴 2008 öncesi dönemde 506 m.79/10 uygulanır (süre 1987-1994 arasında 10 yıl, 07.06.1994'ten sonra yeniden 5 yıl).  |
| Sürenin işlemediği hâller | **Kanun metninde yok, 10. HD içtihadı** | Yönetmelikte sayılan belgeler (işe giriş bildirgesi, dönem bordrosu) Kuruma verilmişse ya da çalışma Kurumca tespit edilmişse, Kurumca öğrenilen ve **kesintisiz devam eden** çalışmalar için hak düşürücü süre geçmiş sayılmaz. Bildirimden önceki kayıt dışı dönem bildirim sonrasına kesintisiz bağlanıyorsa ("blok çalışma") süre, kesintisiz çalışmanın sona erdiği yılın sonundan başlar.  |
| Kuruma başvuru (yalnız Kuruma karşı tespit davalarında) | 7036 m.4/1 | 60 gün içinde cevap yoksa ret sayılır; başvuruda geçen süre hak düşürücü süreye sayılmaz.  |

`legal_calculate_deadline` bu süreyi hesaplamaz; yıl sonu + 5 yılı elle hesapla, `[doğrula]` işaretle.

---

## Kontrol listesi

### 1. Hak düşürücü süre 🔴
- Talep edilen her dönem için: hizmet yılının sonu + 5 yıl dava tarihinden önce mi doluyor?
- Süreyi durduran belge var mı (Kurum tespiti, işe giriş bildirgesi, imzalı bordro, müfettiş raporu)? Varsa bildirim ile kayıt dışı dönem **kesintisiz** mi? Arada kopma varsa blok çalışma ilkesi uygulanmaz.
- Örnek tuzak: işten ayrılış bildirgesinden sonra yıllarca beklenmişse süre, kesintisiz çalışmanın bittiği yılın sonundan işlemeye başlamış ve dolmuş olabilir (10. HD E.2025/1724 olayı: bildirimler 1995'te bitti, dava 2016 → ret). 🔴

### 2. Delil
- **Bordro tanığı:** o dönemde aynı işyerinde kayıtlı çalışan kişiler (SGK kaydından çıkarılır).
- **Komşu işyeri tanığı:** çevredeki işyeri sahipleri ve kayıtlı çalışanları.
- Davacının yalnızca kendi getirdiği, kaydı olmayan tanıklar yetersiz kalabilir. 🟠
- **Yazılı belge:** banka dekontları (ücret ödemesi), işyeri iç yazışmaları, kargo/teslim tutanakları, imzalı iş belgeleri, fotoğraf, HTS kayıtları, vergi kayıtları; sporcu, sanatçı gibi meslek gruplarında federasyon/birlik kayıtları.
- İşyerinin o tarihte SGK'ya kayıtlı olup olmadığı, işyeri dosyası, dönem bordroları (mahkemeden istenir).

### 3. Taraflar
- Dava işverene karşı açılır; dava Kuruma re'sen ihbar edilir, **SGK davalı yanında fer'i müdahildir** ve yanında katıldığı taraf başvurmasa da kanun yoluna gidebilir.  Kuruma ihbar yapılmadan karar verilmesinin sonucunu (bozma sebebi olup olmadığını) kesin bilgi gibi yazma: güncel 10. HD kararını `legal_search_cases` (`daire: "10. Hukuk Dairesi"`, `sorgu: "hizmet tespiti davası Kuruma ihbar edilmeden hüküm kurulması"`) ile ara, tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: ihbarsız hükmün sonucu]` yaz. 
- İşveren ölmüşse mirasçılar; şirket tasfiye edildiyse durum `[incele]`.

### 4. Zorunlu arabuluculuk
- 7036 m.3/1 dava şartını işçi/işveren alacağı, tazminatı ve işe iade davaları için koyar; hizmet tespiti bu sayımda yer almaz. Hizmet tespitini arabuluculuk listesine koyma. Aynı dilekçede işçilik alacağı da isteniyorsa o kalemler 7036 m.3/1 kapsamındadır, son tutanak dilekçeye eklenmelidir.  Arabuluculuk yapılmadan birlikte açılan davada alacak kalemlerinin akıbetini (tefrik, kısmi usulden ret) kesin bilgi gibi yazma; güncel kararı `legal_search_cases` (`sorgu: "hizmet tespiti ile birlikte işçilik alacağı arabuluculuk dava şartı"`) ile ara, bulamazsan `[ARAŞTIRMA GEREKLİ: birlikte açılan davada arabuluculuk]` yaz. 
- **Yargı çevresi:** hizmet tespiti ve onunla birlikte açılan işçilik alacakları temyizde 10. HD'dedir. 

### 5. Sonuçları
- Prim günü, sigorta başlangıç tarihi ve emeklilik tarihine etkisi → `emeklilik-ve-borclanma.md`. Tespit edilen ilk giriş 08.09.1999 öncesine düşüyorsa EYT (5510 geçici m.95) açısından sonuç doğurabilir. 🟠
- Kurum, kesinleşen kararı uygulamakla yükümlüdür (7036 m.4/2). İşveren yönünden tespit edilen dönem için prim, gecikme zammı ve İPC riski doğar → `sgk-uyum-ve-itiraz.md`.
- Aynı olaydan işçilik alacakları → `is-hukuku` becerisi, `../../is-hukuku/references/iscilik-alacaklari.md`.

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "5510"  article_no: "86"
legal_get_statute_article  law_no: "7036"  article_no: "4" | "3"
legal_get_statute_article  law_no: "506"  article_no: "79"        # 2008 öncesi dönemler (mülga; metin çekilemezse sürüm araması)
legal_search_statute_versions  law_no: "506"  query: "hizmetlerin geçtiği yılın sonundan başlayarak"
legal_search_cases  mahkeme: "yargitay"  daire: "10. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. bordro tanığı ve komşu işyeri tanığı ile fiili çalışmanın ispatı hizmet tespiti>"
legal_search_cases  mahkeme: "yargitay"  daire: "10. Hukuk Dairesi"
    sorgu: "hak düşürücü süre işe giriş bildirgesi blok çalışma kesintisiz"
legal_search_cases  mahkeme: "yargitay"  daire: "21. Hukuk Dairesi"  tarih_bitis: "2020-09-02"   # kapatılan daire, eski emsal
legal_search_cases  mahkeme: "yargitay"  daire: "Hukuk Genel Kurulu"
legal_search_cases  mahkeme: "bam"  sorgu: "<olay>"                   # tanık değerlendirmesi
legal_get_case_document  belge_id: "<seçilen karar>"                  # en az bir güncel kararın tam metni
```
Eski profildeki `mevzuat_turu: içtihadı birleştirme kararı` → sorguya "içtihadı birleştirme" ekle.

---

## Görüşme soruları

1. Çalışılan işyeri (unvan, adres, iş kolu) ve işveren?
2. Sigortasız ya da eksik bildirilen dönem (başlangıç–bitiş, yaklaşık)? Arada kopma var mı?
3. Görev, çalışma düzeni, ücretin nasıl ödendiği (elden / banka)?
4. O dönemde birlikte çalışılan ve sigortalı olan kişiler (bordro tanığı)?
5. Komşu işyerleri ve sahipleri?
6. Elde yazılı belge (dekont, yazışma, fotoğraf, iş kartı, federasyon kaydı)?
7. Daha önce SGK'ya şikâyet ya da müfettiş incelemesi oldu mu?
8. İşveren hâlâ faal mi?
9. Hizmet dökümü (e-Devlet) elde mi? İlk sigorta giriş tarihi ne görünüyor?
10. Amaç: emeklilik tarihini öne çekmek mi, prim günü tamamlamak mı, işçilik alacağı mı?

## Çıktı iskeleti

```markdown
## Hizmet tespiti değerlendirmesi: [kişi] — [tarih]
### Sonuç
### Dava türü ve yol (işverene karşı tespit / Kuruma karşı başlangıç tespiti — 7036 m.4)
### Dönemler ve hak düşürücü süre
| Dönem | Yıl sonu | 5 yıl dolumu | Süreyi durduran belge | Kesintisiz mi | Durum |
### Delil durumu
| Delil | Var/Yok | Güç | Not |
### Taraflar ve usul
### Emeklilik tarihine olası etkisi [doğrula — SGK hizmet dökümü ile]
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- 🔴 Bildirimden önceki kayıt dışı dönemi "işe giriş bildirgesi var, süre işlemez" diye kabul edip kesintisizliği kontrol etmemek.
- 🔴 Hizmet tespiti için arabuluculuk tutanağı istemek ya da Kuruma başvuru şartı aramak (işverene karşı davada yok).
- 🟠 Kuruma karşı sigorta başlangıç tespiti davasında 7036 m.4 başvurusunu atlamak.
- 🟠 Tanık olarak yalnız kayıtsız kişileri göstermek.
- 🟡 Tespit sonucunun EYT ve emeklilik tarihine etkisini konuşmamak.

---

