# SGK gecikme cezası, gecikme zammı ve bildirge düzeltmesi

Araç: `legal_calculate_tax` `hesap: "sgk_gecikme"` (5510 m.89/2). Gecikme cezası oranı ve DİBS serisi tablodan gelir; bu dosyaya oran yazılmaz. **6183 m.51 gecikme zammı (`gecikme_zammi`) SGK alacağına uygulanmaz** (5510 m.88 aşağıda). İdari para cezasına itiraz, tutarın yerindeliği ve borç uyuşmazlığı `../../sosyal-guvenlik-sgk/SKILL.md`'dedir; burada yalnız tutar ve bildirge yolu.

## Ne zaman

- "Mart primini geç ödedik, ne kadar gecikme çıkar?", "İPC'yi geç ödersek?", "APHB'yi/MUHSGK'yı geç verdik ya da düzelteceğiz."
- e-Bildirge borç dökümünü sağlamak; yapılandırma öncesi kaba tutar.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Borcun türü: prim / İPC / noksan tahakkuk farkı / diğer Kurum alacağı | Vade kuralı farklı | Sor 🔴 |
| Prim için: belgenin ait olduğu ay ve ücret dönemi (ayın 1-30'u mu, 15'i-14'ü mü) | Asıl son gün | Sor |
| İPC için: tebliğ tarihi (e-Tebligat'ta tebliğ sayılan gün) | 15 gün | Sor 🔴 |
| Asıl tutar (prim aslı ya da ceza aslı) | Hesabın tabanı | Sor |
| Ödeme tarihi | Son dönem gün hesabı | Bugün varsay, yaz |
| Kısmi ödeme, mahsup (KDV iadesi dahil) | Bakiye ve süre | Sor 🟠 |

## Vadeyi belirle (`vade` alanına **asıl** son günü yaz)

| Alacak | Asıl son gün | Dayanak |
|---|---|---|
| 4/a primi, ücret dönemi ayın 1'i-sonu | Belgenin ilişkin olduğu ayı izleyen ayın son günü | SSİY m.108/4-a |
| 4/a primi, ücret dönemi 15'i-ertesi 14'ü | Dönemi izleyen takvim ayının 14'ü | SSİY m.108/4-b |
| TİS, YHK, işe iade, arabuluculuk, geriye dönük ücret farkı | Olay tarihini izleyen ay/dönem sonu | SSİY m.108/5 |
| Kurumca sonradan tespit edilen noksan tahakkuk (kusursuz) | Tebliğden itibaren; borç aslı tebliğden itibaren yedi gün içinde ödenmezse gecikme tebliğ tarihinden işler | 5510 m.88 son fıkralar, SSİY m.108/16 |
| İdari para cezası | Tebliğ tarihinden itibaren 15 gün | 5510 m.102 |
| Sona eren sözleşmeye bağlı ücret dışı ödeme (karar kesinleşmesi) | Kesinleşmeyi izleyen ay sonu; süresinde ödenirse gecikme ve m.102 yok | 5510 m.80/1-d |

Son gün tatile rastlarsa ödeme süresi tatil olmayan ilk güne uzar; **o gün de ödenmezse** gecikme cezası ve zammı yine **asıl vadeyi izleyen günden** işler. Bu yüzden `vade`'ye uzamış günü değil, asıl son günü yaz. Tatil kontrolü: `legal_check_holiday`.

## Araç çağrıları

```json
{ "hesap": "sgk_gecikme", "girdi": { "tutar": 0, "vade": "2026-03-31", "odeme": "2026-07-10" }, "tarih": "2026-07-10" }
```
```
legal_check_holiday tarih: "<asıl son gün>"
legal_get_statute_article law_no: "5510" article_no: "89" law_type: "Kanun"
legal_search_admin_guidance sorgu: "gecikme cezası gecikme zammı hesaplanması" kurum: "Sosyal Güvenlik Kurumu"
```
Yanıt: `sonuc.gecikme_cezasi`, `gecikme_zammi`, `toplam_ek`, `toplam_borc`; `ara_degerler.donemler[]` her dönem için başlangıç, ceza oranı, DİBS ayı ve oranı, son dönemde gün sayısı. `parametre.dibs_ilk` / `dibs_son` seri kapsamını gösterir; ödeme tarihi `dibs_son`'dan sonraki bir aya düşüyorsa sonuç yoktur, tahmin etme.

## Hukuki çerçeve

- **Prim ödeme yükümlülüğü:** işveren işçi payını keser, kendi payını ekler, Kurumca belirlenen günün sonuna kadar öder; hak edilip ödenmemiş ücretin primi de aynı. [5510 m. 88](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **6183'ün uygulanması:** süresinde ödenmeyen prim ve diğer alacakların tahsilinde 6183 uygulanır, **m.51, 102 ve 106 hariç**. [5510 m. 88](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Fiilen ödenmeyen prim** GV/KV'de gider yazılamaz. [5510 m. 88](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Gecikme cezası ve zammı:** ödenmeyen kısım sürenin bittiği tarihten itibaren ilk üç aylık sürede her ay gecikme cezasıyla artırılır; ayrıca her ay için bir önceki aya ait DİBS aylık ortalama faizi bileşik uygulanır; ödeme ayında zam günlük. Dava ve takip açılmış olsa da işler. CB ceza oranını değiştirebilir. [5510 m. 89/2](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]
- **Yöntem ve tatil:** gecikme yasal son günü takip eden günden başlar; son gün tatile denk gelirse tatil olmayan ilk gün yasal süredir, bu sürede ödenmezse ceza ve zam vadenin bittiği günden işler. [SGK Genelge 2020/20](https://kms.kaysis.gov.tr/Home/Goster/163634) [soorgla] Kuruşa yuvarlama ve gün/3000 formülü genelgenin hesap örneklerinden; §5 metninden doğrula `[doğrula]`.
- **Ödeme süreleri:** SSİY m.108/4 (ay sonu / 14'ü), m.108/5 (geriye dönük ödemelerde özel başlangıçlar), m.108/15 (KVK iadesinden mahsupta ek süre ve kısmi mahsupta gecikme), m.108/16 (noksan tahakkuk farkı yedi gün). [Sosyal Sigorta İşlemleri Yönetmeliği m. 108](https://soorgla.com/mevzuat/13973-sosyal-sigorta-islemleri-yonetmeligi/) [soorgla]
- **APHB/MUHSGK'nın geç verilmesi:** yasal son günü izleyen günden itibaren üçüncü ayın sonuna kadar verilen asıl/ek belge, şüphe yoksa ve işe giriş bildirgesi süresinde verilmişse incelemesiz işleme alınır; belge türü ya da kanun numarası hatalı seçilmiş belgenin düzeltilmesi (sigortalı, gün, PEK aynıysa) incelemesiz işlenir ve **İPC uygulanmaz**. [SSİY m. 103](https://soorgla.com/mevzuat/13973-sosyal-sigorta-islemleri-yonetmeligi/) [soorgla]
- **İPC:** belge/beyanname eksik ya da geç verilirse m.102/1-c (belge) ve 1-m (MUHSGK) kapsamında ceza; kendiliğinden 30 gün içinde verilir ve ceza tebliğden itibaren 15 gün içinde ödenirse (a), (b), (g), (h), (j) bentlerinde indirimli uygulama — **(c) ve (m) bu listede yok**; tebliğden 15 gün içinde ödeme ya da itiraz; peşin ödemede indirim; ödenmeyen İPC'ye m.89 gecikmesi. [5510 m. 102](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla] İndirim oranları ve tutarlar madde metninden; burada yazılmadı.
- **Eksik gün:** nedeni APHB/MUHSGK'da bildirilir; belgeler istenip verilmezse Kurum re'sen düzenler. [5510 m. 86](https://soorgla.com/mevzuat/5510-sosyal-sigortalar-ve-genel-saglik-sigortasi-kanunu/) [soorgla]

## Kontrol listesi

- 🔴 `vade` asıl son gün mü (uzamış gün değil)?
- 🟠 Nisan 2025'te başlayan dönem: 2025-03 DİBS oranı SGK tablosunda yok; o ay iskontolu ihraç olmadığı için SGK uygulamasına göre önceki ayın oranı kullanıldı (türetilmiş). Araç uyarı verir; e-Bildirge borç dökümüyle karşılaştır `[doğrula]`.
- 🔴 SGK alacağına `gecikme_zammi` (6183 m.51) kullanıldı mı? Kullanılmaz.
- 🟠 İPC'de tebliğ tarihi e-Tebligat kuralına göre mi alındı (5510 m.88 elektronik tebliğ fıkrası)?
- 🟠 KDV iadesinden mahsup talebi var mı? Süre ve kısmi mahsup kuralı SSİY m.108/15.
- 🟠 Geç ödeme o ay Hazine indirimi ve teşvikleri düşürür → `sgk-prim-ve-tesvikler.md`.
- 🟡 Kısmi ödeme: her ödemede bakiye ayrı hesaplanmalı; araç tek tutar ve tek ödeme tarihi alır.
- 🟡 Araç sonucunu e-Bildirge borç dökümüyle karşılaştır; kuruş farkı yuvarlamadan olabilir.
- [incele] İPC'nin hangi bentten verildiği, indirim şartları, itiraz yolu → uyuşmazlık.

## Sık hatalar

- 6183 gecikme zammı oranını SGK borcuna uygulamak.
- Tatil uzamasını vadeye işlemek (gecikmeyi bir-iki gün geç başlatmak).
- İlk üç ay gecikme cezasını tüm dönemlere uygulamak.
- Düzeltme amaçlı (kanun no hatalı) belgeye İPC beklemek; ya da yeni sigortalı/gün ekleyen belgeyi "düzeltme" sanmak.
- APHB'yi geç verip primi süresinde ödemek: İPC ayrı, gecikme yok — ikisini karıştırmak.

## Bilinen araç sınırları (çıktıya taşı)

- DİBS serisi SGK sayfasından; 2025-03 türetilmiş (önceki ay); seri sonundan sonraki ödeme hesaplanmaz.
- Son dönemde gün sayısı başlangıç ve ödeme günü dahil sayılır (1–10 Nisan = 10 gün; 19.01–02.02 = 15 gün); zam B × oran × gün / 3000, her adım kuruşa yuvarlanır.
- Kısmi ödeme, mahsup, yapılandırma ve tecil faizi yok.
- Tatil uzaması hesaplanmaz; araç yalnız uyarır.

## Uyuşmazlığa dönüş

İPC'ye itiraz, re'sen tahakkuka itiraz (5510 m.86/7 — bir ay), ödeme emri, haciz, kanuni temsilci sorumluluğu (5510 m.88) → başlığı değiştir, `../../sosyal-guvenlik-sgk/SKILL.md` (`references/sgk-uyum-ve-itiraz.md`). Taşı: tebliğ tarihleri, vade tablosu, hesap dökümü, araç uyarıları. İtiraz süresini "Süre defterine ekleyeyim mi?" diye sor (`sure-takibi`).

## Çıktı

SKILL.md Adım 4. Hesap tablosu `donemler[]`'den: Dönem | Başlangıç | Gün | Ceza oranı | Gecikme cezası | DİBS ayı | DİBS oranı | Zam | Borç. Üstte vade tablosundaki satır ve dayanağı; altta `formul`, `parametre` ve tüm `uyarilar`.
