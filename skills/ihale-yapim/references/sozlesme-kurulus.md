# Aşama 4–5 — Kesinleşen karar, bekleme, sözleşmeye davet, kesin teminat ve imza (yapım)

Onaydan imzaya kadar süre zinciri kısadır ve her halkası hak kaybı doğurur. **İdare:** süreler, bekleme yasağı,
yasaklılık teyidi, belge kontrolü. **İstekli:** davet tebliğinden itibaren 10 gün, kesin teminat tutarı, sunulacak
belgeler, imzalamamanın sonuçları. Sonuca şikâyet ve bekleme süresinin şikâyetle uzaması → `ihale-sikayet`. İmzadan
sonrası → `../../hakedis/SKILL.md` (imza öncesi sözleşme tasarısı denetimi: `hakedis/references/sozlesme-tasarisi-denetimi.md`).

---

## 1. Süre zinciri

| Adım | Süre | Dayanak | Kod (canlı) |
|---|---|---|---|
| Onay | karar tarihini izleyen en geç 5 iş günü | 4734 m.40 | `kik_tender_approval` |
| Kesinleşen karar bildirimi | onayı izleyen en geç 3 gün; elenme gerekçeleri dahil | 4734 m.41 | `kik_result_notice` |
| Bekleme (imza yasağı) | bütün isteklilere bildirimden itibaren 10 gün (21/b-c 5) | 4734 m.41 | `kik_standstill` |
| Davet | bekleme bitimini (ön mali kontrol varsa tamamlanmasını) izleyen günden itibaren 3 gün | 4734 m.42 | `kik_contract_invitation` |
| Kesin teminat + imza | davetin tebliğini izleyen 10 gün; yabancıya +12 gün | 4734 m.42 | `kik_contract_signing`, `_foreign` |
| İkinci teklif sahibine davet | 10 günlük sürenin bitimini izleyen 3 gün | 4734 m.44 | — |
| İdare imzalamazsa istekli | sürelerin bitiminden en geç 5 gün içinde 10 gün süreli noter ihbarı | şartname m.40; 4734 m.45 | `kik_contract_withdrawal_notice` (5), `kik_contract_withdrawal_period` (10) |

- [ ] Bu kodlar canlı: `legal_calculate_deadline` ile hesapla, `kural_adi`'yi satırla karşılaştır; araç yanıt vermezse
  elle say (olay günü sayılmaz), `legal_check_holiday` ile son günü kontrol et, `[incele]`. 
  Şikâyet varsa idarenin kararının son
  bildiriminden (karar alınmadıysa karar süresinin bitiminden) itibaren 10 gün geçmeden ve itirazen şikâyet sorgulaması
  yapılmadan, itirazen şikâyet varsa Kurum nihai kararı vermeden sözleşme imzalanamaz (4734 m.55 son fıkra; m.56/1).
  Ayrıntı `ihale-sikayet`. 
- [ ] Bildirim ve davet EKAP üzerinden; elektronik ortamda yapılan bildirimde **bildirim tarihi tebliğ tarihidir**,
  EKAP işlemlerinde teyit aranmaz; Kanunda hüküm yoksa Tebligat Kanunu (4734 m.65; şartname m.6).
  

## 2. Kesin teminat

- [ ] Kural 4734 m.43: ihale bedelinin **%6'sı**. Kurum, teklifi sınır değerin altındaki istekli için YM'nin %6–%15'i
  aralığında oran belirleyebilir (m.43/3). 
- [ ] Yapımda: teklif **SD'ye eşit/üzerinde → teklif fiyatının %6'sı; SD'nin altında → YM'nin %9'u** (Yapım Yön.
  m.56/2; şartname m.37.1). 
- [ ] Kısmi teklifte kısım bazında; ortak girişimde ortaklardan biri karşılayabilir — ama yurt dışı iş bitirme belgesi
  kullanan ortak hissesi oranında teminat verir (4734 m.10; şartname m.37.2).
- [ ] Teminat türü (4734 m.34 değerleri: nakit, mektup, DİBS) ve mektubun EKAP üzerinden düzenlenmesi (şartname
  m.27). EKAP dışı alınan mektubun kapsam ve şekli **e-forma uygun** olmalı, değilse geçersiz (Yapım Yön. m.56/4);
  kesin teminat mektubunun süresini idare işin bitiş tarihine göre belirler (m.56/6); teyit banka/sigorta genel
  müdürlüğü ya da şubesinden (m.56/9). 
- [ ] **İstekli:** SD altında kazandıysan %9'u **YM** üzerinden hesapla (YM ilk oturumda açıklandı); bütçeni buna göre
  ayarla.

## 3. İmza öncesi belgeler ve kontroller

**İstekli sunar** (davetin tebliğinden 10 gün içinde, kesin teminatla): ihale tarihinde odaya kayıtlı olduğunu ve
4734 m.10/4 (a), (b), (e), (g) durumlarında olmadığını gösteren belgeler; ortak girişimde her ortak ayrı; yabancıda
dengi belgeler (şartname m.38.2-4). İş ortaklığında **noter onaylı ortaklık sözleşmesi** (m.16.4). Taahhüt edilen
durumu tevsik eden belge verilmezse ihale dışı bırakılır, geçici teminat gelir kaydedilir (4734 m.10 son fıkra).

**İdare kontrol eder:**
- [ ] İmza tarihinde ihale sonuç bilgileri Kuruma gönderilerek **yasaklılık teyidi** zorunlu (4734 m.42).
- [ ] Fiziki istenen belgelerin yüklenenle aynı olması; farklı belge → değerlendirme dışı + 4734 m.17 (şartname
  m.29.12-13, m.38.5).
- [ ] Ön mali kontrol gerekiyorsa tamamlanması (5018 m.58); davet süresi ön mali kontrolün tamamlandığı tarihten işler
  (4734 m.42). Hangi tutardan sonra ön mali kontrol gerektiği idarenin iç düzenlemesine ve Bakanlık usul ve esaslarına
  bağlı `[doğrula: idarenin ön mali kontrol yönergesi]`. 
- [ ] Sözleşme bedeli KİK payı eşiğini aşıyorsa **bedelin onbinde beşi** yükleniciden; idare ve noter, yatırıldığını
  imza aşamasında aramak zorunda (4734 m.53/j-1; şartname m.41.1). Kanun metnindeki eşik eski TL tabanıdır, kullanma:
  eşik tutarı `legal_get_social_parameters` `ihale_kik_payi_sozlesme_esigi` (ilan dönemi).
  
- [ ] Sözleşme dokümandaki tasarıya uygun; damga vergisi ve giderler yükleniciye (şartname m.41.3-5).

## 4. İmzalamama ve ikinci teklif

- [ ] Kesin teminatı verip imzalamayan istekli: protesto ve hüküm gerekmeksizin **geçici teminat gelir kaydedilir**
  (4734 m.44); mücbir sebep dışında 4734 m.58 yasaklama hükümleri uygulanır (şartname m.38.6) — ama m.10 kapsamında
  taahhüt edilen duruma aykırı belgede teminat gelir kaydedilir, yasaklama verilmez. 🔴 Avukat olmayan kullanıcıda
  "imzalamayacağım" kararından önce ORTAK-KURALLAR.md §1 kapısı. Yasaklama ayrıntısı → `kamu-ihale`.
- [ ] İdare EAAT ikinci teklif fiyatını ihale yetkilisi uygun görürse ikinciyle imzalayabilir; o da imzalamazsa onun
  teminatı da gelir kaydedilir ve ihale iptal edilir (4734 m.44). 
- [ ] İkinci teklif sahibinin geçici teminatı imzadan hemen sonra iade (şartname m.28.3).

---

> **Çalışılmış örnek — İKN 2026/1776751**
> Şartname m.35–41 kanundaki zinciri birebir tekrarlıyor: bildirim 3 gün, bekleme 10 gün (m.35.3), davet 3 gün,
> imza 10 gün (+12 yabancı), kesin teminat %6 / SD altında YM'nin %9'u (m.37.1), KİK payı onbinde beş (m.41.1),
> yasaklılık teyidi (m.41.2). Teklif geçerliliği 120 gün (m.24): kesinleşme ve imza bu süre içinde tamamlanmazsa
> idare uzatma ister; istekli reddederse teminatı iade edilir.
