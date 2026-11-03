# SGK işlemleri: uyum, teşvik, İPC ve prim itirazı

**Ne zaman kullanılır:** işverene kesilen idari para cezası (İPC), re'sen prim tahakkuku, yersiz teşvik geri alımı ya da müfettiş/denetim raporuna karşı itiraz; işyerinin bildirim ve teşvik uyumunun denetimi. Emeklilik, statü ve borçlanma soruları → `emeklilik-ve-borclanma.md`.

Üç iş:
1. **Uyum denetimi** — işyerinin bildirimleri ve prim teşvikleri mevzuata ve SGK genelgelerine uygun mu?
2. **İtiraz** — İPC, re'sen prim tahakkuku, teşvik iptali ya da denetim raporuna karşı itiraz.
3. **Borç yönetimi** — tecil-taksit (6183 m.48), yapılandırma kanunları, zamanaşımı.

Genelgeler bu alanda kanunun uygulanmasını belirler ama mahkeme kararı değildir ve yargıyı bağlamaz. Genelgeye dayanırken bunu açıkça yaz. soorgla'nın idari görüş derleminde SGK genelgeleri bulunmuyor (SKILL.md Adım 3); genelge metnini kullanıcıdan iste.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| İPC'ye Kuruma itiraz: tebliğden itibaren **15 gün** | 5510 m.102 | Süre geçerse kesinleşir. 🔴 15 gün içinde peşin ödemede dörtte üçü tahsil edilir ve yargı yolu hakkı korunur; kendiliğinden 30 gün içinde verilen bildirgede bazı bentlerde ceza dörtte bir uygulanır. |
| İPC itirazının reddinden sonra: **30 gün** içinde **idare mahkemesi** | 5510 m.102 | Eski `circular_compliance` tanımındaki "SGK işlemleri adli yargıdadır" ifadesi ve eski `social_security_sgk` tanımındaki "karar_danistay kapalı" ayarı İPC için **yanlış**. Yargı yeri işlem türüne göre ayrılır: İPC → idare mahkemesi; re'sen prim tahakkuku → iş mahkemesi. |
| Re'sen tahakkuk eden prim borcuna Kurum ünitesine itiraz: tebliğden itibaren **1 ay**; ret hâlinde ret kararının tebliğinden **1 ay** içinde **iş mahkemesi** | 5510 m.86/7 (eski tanımdaki "m.88/89" yanlış; onlar tahsil ve gecikme hükümleri) | Kuruma itiraz takibi durdurur; mahkemeye başvuru takip ve tahsili durdurmaz. |
| Prim alacağında zamanaşımı: **10 yıl** | 5510 m.93/2 | Başlangıç: ödeme süresinin dolduğu tarihi izleyen takvim yılı başı; mahkeme kararı, müfettiş raporu ya da başka kurumdan gelen bilgiye dayanan alacaklarda kesinleşme/rapor/intikal tarihi. Eski `social_security_sgk` tanımındaki "dönemine göre 5 veya 10 yıl" ifadesini kullanma. Kesen sebepler `[incele]`. |
| İPC'de zamanaşımı: **10 yıl**, fiilin işlendiği tarihten | 5510 m.102; hüküm bulunmayan hâllerde 5326 | |
| İşe giriş bildirgesi: sigortalılık başlangıcından **önce**; istisnalar: inşaat, balıkçılık, tarımda en geç çalışmaya başlatılan gün; ilk kez işyeri bildirgesi verilen işyerinde ilk ay içinde başlayanlar için bir aylık sürenin sonuna kadar | 5510 m.8/1 | Süre aşımı = m.102 uyarınca İPC (m.8 son fıkrası). Sigortalının kendisini bildirmemesi aleyhine delil değildir (m.8/2). |
| Aylık prim ve hizmet belgesi (MUHSGK) | 5510 m.86/1; verilme süresi yönetmelikte | Süreyi yönetmelikten çek (`legal_search_statute_semantic`). |

`legal_calculate_deadline` İPC sürelerini hesaplar (`sgk_ipc_objection`, `sgk_ipc_lawsuit`); sonucu 5510 m.102 metniyle karşılaştır. Diğer süreleri elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]`.

---

## Kontrol listesi — uyum denetimi

1. **Güncel genelge uyumu:** yapılan işlem (sigortalı statüsü, prim günü, hizmet alım ihalesi, alt işveren) en son SGK genelgesine uygun mu? → `legal_search_admin_guidance` (`kurum: "Sosyal Güvenlik Kurumu"`, `belge_tur: "genelge"`), bulunamazsa `legal_search_official_gazette`. Temel genelgeler: **İşveren İşlemleri Genelgesi 2020/20** ve **İdari Para Cezası Genelgesi 2020/8**; ikisinin de değişiklikleri işlenmiş güncel hâli ayrı kayıt olarak gelir, en yenisini kullan. Genelgenin numarası ve tarihi yalnızca araç sonucundan ya da kullanıcı belgesinden aktarılır; tahmini numara yazma.
2. **Prim teşvikleri (kısa):** işyeri şartları taşıdığı hâlde bir teşviki kullanmamış mı, ya da şartı olmadan kullanmış mı? Teşvik kodlarını (ör. eski tanımdaki 06486, 17103) ve şartlarını yalnızca araçtan ya da kullanıcı belgesinden aktar. Teşvikler sık değişir ve süreli; her biri için yürürlük süresini çek:
   - **Genel işveren hissesi indirimi (5510 m.81/1-ı):** eski metin "beş puan" diyordu; 7538 s. Kanunla 01.02.2025'ten itibaren "dört" yapıldı, imalat sektörü için geçici m.108 ile beş puan korundu; **7566 s. Kanunla (RG 19.12.2025) 2026 Ocak ayı başından itibaren "iki"** yapıldı, geçici m.108'deki atıf da "iki" olarak güncellendi (imalatta "iki" ibaresi "beş" uygulanır). Oranı her seferinde araçtan çek.
   - **Eski "uzun vadeli sigorta prim oranı":** güncel m.81/a metni MYÖ primini %21 (işveren %12) gösteriyor; eski kaynaklardaki %20/%11 oranlarını kullanma; değişiklik 7566 s. Kanunla 2026 Ocak ayı başından itibaren geçerli, öncesindeki dönemler için eski oran uygulanır.
   - **Devlet katkısı fıkrası** 7590 s. Kanunla yürürlükten kalktı; madde başlığı "Prim oranları" oldu.
   - **4447 geçici m.10 (ilave istihdam):** uygulama süresi 7495 ile 31.12.2025'e uzatıldı, Cumhurbaşkanına 31.12.2026'ya kadar uzatma yetkisi verildi; bu yetki kullanıldı, süre **31.12.2026'ya** uzatıldı (Cumhurbaşkanı Kararı 10769, RG 25.12.2025). 2027 için yeni uzatma yetkisi kanunla verilmedikçe süre bu tarihte biter; yeni kanun çıkıp çıkmadığını RG'den kontrol et.
   - **EYT emeklisinin aynı işyerinde yeniden çalıştırılması:** SGDP işveren hissesinin 5 puanı Hazinece karşılanır (5510 geçici m.95/2). soorgla madde kaydı (`legal_get_statute_article 5510 geçici 95`) yalnız birinci fıkrayı döndürüyor; ikinci fıkrayı 7438 RG metninden oku.
   - 2025-2026 asgari ücret desteği (7539, 7573) ve sektörel destekler (7590 m.36 turizm) yıl yıl çıkar; `legal_search_official_gazette` (`query: "asgari ücret desteği"`, `date_from`) ile bul. `[doğrula]`
3. **Yersiz teşvik riski:** teşvik şartı sonradan kaybedilmiş mi (borç, kayıt dışı istihdam tespiti, fiilen çalışmayan sigortalı bildirimi)? Bu tespitte işveren bir yıl teşvikten yararlanamaz ve yararlanılan tutar gecikme cezası ve zammıyla geri alınır. 🟠 Yeniden yapılandırılmış ya da 6183 m.48'e göre taksitlendirilmiş borç teşvike engel değildir (m.81/ı ve 4447 geçici m.10).
4. **İPC riski:** zorunlu bildirimler zamanında mı? Eksik/geç bildirim listesi çıkar. Geçmişte terkin/af hükmü var mı kontrol et (ör. 7538 ile eklenen geçici m.107, 4/1-b-4 tarımsal faaliyet bildirimleri için İPC terkin etti).
5. **Denetim raporu:** fiili çalışmanın reddi, sahte sigortalılık, yersiz teşvik tespiti var mı? İtiraz yolu ve süresi (aşağıda).

## Kontrol listesi — itiraz

**Usul yönünden:**
- Tebligat usulüne uygun mu (7201 Tebligat K.)? Tebliğ tarihi doğru mu? Elektronik tebligat, muhatabın elektronik adresine ulaştığı tarihi izleyen **beşinci günün sonunda** yapılmış sayılır (7201 m.7/a); tüm özel hukuk tüzel kişileri için e-tebligat zorunlu.
- Süre içinde mi? İşlem İPC mi (15 gün / idare mahkemesi) prim tahakkuku mu (1 ay / iş mahkemesi)?
- Zamanaşımı var mı (5510 m.93, m.102)?
- İşlemi yapan birim yetkili mi?

**Esas yönünden:**
- Fiil oluşmuş mu? (Ör. sigortasız işçi iddiasının somut delili var mı?)
- Ceza tutarı doğru hesaplanmış mı? İPC'ler fiil türüne göre asgari ücretin katları ya da kesirleri üzerinden belirlenir; kat oranını m.102'nin ilgili bendinden çek, Esas alınacak asgari ücret **fiil tarihinde geçerli** (16 yaşından büyükler için) aylık brüt asgari ücrettir; `legal_get_social_parameters tur: "asgari_ucret_brut"` yalnız güncel dönemi verir, fiil başka döneme düşüyorsa o dönemin tutarını SGK'nın yıllık "prime esas kazançların alt ve üst sınırları" genelgesinden (`legal_search_admin_guidance`) ya da kullanıcıdan al, `[doğrula]`.
- Lehe genelge hükmü ya da Yargıtay/Danıştay kararı var mı?
- Mücbir sebep, sehven hata, düzeltme beyannamesi?
- Terkin ya da af hükmü kapsamında mı?

## Borç yönetimi

- **Tecil ve taksit:** 6183 m.48. Taksitlendirme ve yapılandırma devam ettiği sürece teşviklerden yararlanma ve GSS'den yararlanma şartlarına engel olmaz (5510 m.67/1-b).
- **Yapılandırma kanunları:** son genel SGK yapılandırması 7440 s. Kanun (RG 12.03.2023). Yeni bir yapılandırma çıkıp çıkmadığını `legal_search_official_gazette` (`query: "alacakların yeniden yapılandırılması"`, `document_type: "kanun"`, `date_from`) ile ara.
- Gecikme cezası ve zammı 5510 m.89 (oranları araçtan / RG'den çek).

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "5510" article_no: "8" | "86" | "88" | "89" | "93" | "102"
legal_list_statute_articles law_no: "5510" article_no: "81" include_content: true # oranlar 2025-2026'da değişti; tarihçe aracı 2015'te kalıyor
legal_get_statute_article law_no: "5510" article_no: "geçici 108" # imalat indirimi (7538)
legal_get_statute_article law_no: "4447" article_no: "geçici 10"
legal_get_statute_article law_no: "6183" article_no: "48" # tecil-taksit
legal_search_official_gazette query: "5510 sayılı" document_type: "kanun" date_from: "<son 2 yıl>" sort_by: "date_desc"
legal_search_official_gazette query: "Sosyal Sigorta İşlemleri Yönetmeliği değişiklik"
legal_search_statute_semantic sorgu: "sigorta primleri genel tebliği" mevzuat_tur: "teblig" # eski profilde PRIM_TEB
legal_search_admin_guidance sorgu: "<konu>" belge_tur: "genelge" # SGK genelgesi derlemde yok; kontrol amaçlı
legal_search_cases mahkeme: "yargitay" daire: "10. Hukuk Dairesi"
    sorgu: "<ör. yersiz teşvik geri alınması prim borcu itiraz>"
legal_search_cases mahkeme: "yargitay" daire: "21. Hukuk Dairesi" tarih_bitis: "2020-09-02" # kapatılan daire, eski emsal
legal_search_cases mahkeme: "danistay" sorgu: "<İPC iptali>" # İPC'nin idari yargı aşaması
legal_get_social_parameters tur: "asgari_ucret_brut"
legal_get_social_parameters tur: "asgari_ucret_isveren_maliyeti_tam"
```
Ek kaynak: takma filtreler (`SGK_GENELGE`, `PRIM_TEB`) gerçek mevzuat numarası değildir; karşılıkları `legal_search_admin_guidance` ve `legal_search_statute_semantic` çağrılarıdır. Kapsam zayıf dönerse ORTAK-KURALLAR.md §5.

---

## Görüşme soruları — itiraz dilekçesi (eski `data_schema` alanlarından)

| Alan (eski şema) | Soru |
|---|---|
| `sgk_unit_name` | Tebligatı gönderen SGK birimi hangisi? (ör. "… Sosyal Güvenlik İl Müdürlüğü … Sosyal Güvenlik Merkezi") |
| `applicant_info.title` | İşyeri unvanı ya da ad-soyad? |
| `applicant_info.registry_no` | İşyeri sicil numarası? (SGK belgelerinde 23 haneli işyeri sicil numarası geçer; alt işverende buna 3 haneli alt işveren numarası eklenir — tebligattaki numarayı aynen al, hane sayısını sen tamamlama) |
| `applicant_info.address` | Tebligat adresi? |
| `notification_details.date` | Tebliğ tarihi? (süre hesabı için kritik; e-tebligat mı?) |
| `notification_details.number` | Tebligat / ceza ihbarnamesi sayısı? |
| `notification_details.subject` | Konu: İPC, prim borcu, rücu, teşvik iptali, denetim raporu? |
| `notification_details.amount` | Ceza/borç tutarı? |
| `objection_summary` | Bir cümlelik konu özeti. |
| `factual_grounds` | Olayın gelişimi; fiilin işlenmediği, sehven hata, mücbir sebep? Elde hangi belgeler var? |
| `legal_grounds` | (Araştırma adımında doldurulur — kullanıcıya sorma.) |
| `conclusion_request` | Talep: cezanın/borcun iptali, kaldırılması, düzeltilmesi? |

Eski tanımda bir `research_agent` bağımlılığı vardı (`consultant.social_security_labor.circular_compliance`): dilekçeyi yazmadan önce dayanak madde, genelge ve kararlar araştırılıyordu. Bu beceride karşılığı: önce yukarıdaki **uyum denetimi** ve **soorgla çağrıları**, sonra dilekçe.

## Çıktı iskeleti — SGK itiraz dilekçesi
**Dilekçe metni katmanı:** analiz burada biter; itiraz dilekçesinin metni `idari-ve-kurum-basvurulari` becerisinde (`../../idari-ve-kurum-basvurulari/references/sgk-itiraz-dilekcesi.md`) bu iskelet temel alınarak kurulur. O beceri yüklü değilse aşağıdaki iskeleti kullan.

```markdown
[TASLAK BAŞLIĞI — dışarı gidecek metinde iç notlar ayrı mesajda]

[SGK BİRİMİ — ortalı, büyük harf]

İTİRAZ EDEN : [unvan / ad-soyad]
SİCİL NO : [işyeri sicil no]
ADRES : [tebligat adresi]
VEKİLİ : [varsa]

TEBLİĞ TARİHİ : [tarih]
SAYI / KONU : [sayı — İPC / prim borcu / rücu]
TUTAR : [tutar]

KONU : [… tarih ve … sayılı … tebligatına karşı itirazlarımızdır.]

AÇIKLAMALAR VE İTİRAZ GEREKÇELERİMİZ:
1. [Usul — tebliğ, süre, zamanaşımı]
2. [Esas — fiil, tutar hesabı, lehe hükümler]
…

HUKUKİ VE YASAL DAYANAKLAR: [5510 m.…, yönetmelik, genelge — her biri soorgla atfıyla; dipnotta kaynak etiketleri]

SONUÇ VE İSTEM: [… iptaline / kaldırılmasına karar verilmesini saygılarımızla arz ve talep ederiz.]

[Tarih] İTİRAZ EDEN / VEKİLİ
                                                            [ad-soyad, imza]
EKLER: [tebligat sureti, belgeler]
```
Hazır `.docx` şablonu yoktur (eski `ui_config` `templates/consultant/sgk_itiraz_v1.docx` dosyasına atıf yapıyordu; dosya mevcut değil).

## Sık hatalar

- 🔴 İPC ile prim borcunun yolunu ve yargı yerini karıştırmak (15 gün + idare mahkemesi / 1 ay + iş mahkemesi).
- 🔴 15 günlük peşin ödeme indirimini kullanıcıya söylememek.
- 🟠 Teşvik oranını eski kaynaktan ("5 puan") yazmak.
- 🟠 Genelge numarasını tahmin etmek.
- 🟡 Yapılandırma ya da terkin hükmü olup olmadığını aramamak.

---
