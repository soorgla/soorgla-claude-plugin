# Faiz hesabı

Araç: `legal_get_legal_interest_rates` (parametresiz). Yalnız **o gün geçerli** oranları döndürür; geçmiş dönem sorgusu yoktur.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Anapara (TL) | Formülün tabanı | `[___]` |
| Faizin başlangıç tarihi (temerrüt, dava, takip, ödeme günü) | Gün sayısı ve oran dönemi | Sor; alan becerisi belirler `[incele]` |
| Bitiş tarihi (hesap tarihi, ödeme, takip tarihi) | Gün sayısı | Bugün varsay, açıkça yaz |
| Faiz türü: yasal / ticari temerrüt / sözleşmesel / gecikme zammı | Oran seçimi | Sor; işin ticari olup olmadığı alan becerisinin işi `[incele]` |
| Sözleşmede oran var mı | TBK m.88/120 sınırı | Sor |
| Kısmi ödeme var mı, tarihleri | Mahsup sırası | Sor; varsa 🟠 teyit eşiği |

## Aracın döndürdüğü oran tipleri

| `oran_tipi` | Ne işe yarar | Dayanak alanı (araç) |
|---|---|---|
| `yasal_faiz` | Adi işlerde kanuni faiz ve temerrüt faizi | 3095 m.1 / 7589 |
| `ticari_temerut` | Ticari işlerde temerrüt faizi (önceki yılın 31 Aralık avans oranı) | 3095 m.2 |
| `tcmb_avans` | Ticari temerrüt oranının kaynağı; yarıyıl kontrolü için | TCMB |
| `tcmb_reeskont` | Yasal faizin kaynağı (yüzde sekseni); yarıyıl kontrolü için | TCMB |
| `politika_faizi` | Bilgi; hiçbir kanuni faizin doğrudan kaynağı değildir | TCMB PPK |
| `gecikme_zammi_aylik` | 6183 amme alacağı, **aylık** oran | CBK |
| `kredi_karti_azami_aylik` | Kredi kartı azami akdi faiz, **aylık** | TCMB |

Tutarlılık kontrolü (her çağrıda yap, tutmuyorsa işaretle):
- `yasal_faiz` ≈ `tcmb_reeskont` × 0,80 (7589 sonrası dönem).
- `ticari_temerut` = önceki yılın 31 Aralık `tcmb_avans` oranı.
- `tcmb_avans` / `tcmb_reeskont` başlangıç tarihinden **sonra** yayımlanmış bir "Reeskont ve Avans İşlemlerinde Uygulanacak Faiz Oranlarının Tespiti" tebliği varsa araç bayattır (aşağıdaki geçici yol).

## Hukuki çerçeve (madde metinleri çekildi)

- **Kanuni faiz:** sözleşmede miktar yoksa yıllık oran, TCMB'nin önceki yılın 31 Aralık günü uyguladığı **reeskont** oranının yüzde sekseni. [Kanuni Faiz Ve Temerrüt Faizine İlişkin Kanun m. 1](https://soorgla.com/mevzuat/3095-kanuni-faiz-ve-temerrut-faizine-iliskin-kanun/) [soorgla]
- **Ticari temerrüt:** TCMB'nin önceki yılın 31 Aralık günü kısa vadeli **avanslar** için uyguladığı oran, kanuni faizden fazlaysa ticari işlerde sözleşme olmasa da istenebilir. [Kanuni Faiz Ve Temerrüt Faizine İlişkin Kanun m. 2](https://soorgla.com/mevzuat/3095-kanuni-faiz-ve-temerrut-faizine-iliskin-kanun/) [soorgla]
- **Akdi faiz sınırı (adi iş):** sözleşmeyle kararlaştırılan yıllık faiz, kanuni oranın yüzde elli fazlasını aşamaz. [Türk Borçlar Kanunu m. 88](https://soorgla.com/mevzuat/6098-turk-borclar-kanunu/) [soorgla]
- **Temerrüt faizi sınırı (adi iş):** sözleşmeyle kararlaştırılan temerrüt faizi kanuni oranın yüzde yüz fazlasını aşamaz; akdi faiz daha yüksekse temerrüt faizi akdi faizden az olamaz. [Türk Borçlar Kanunu m. 120](https://soorgla.com/mevzuat/6098-turk-borclar-kanunu/) [soorgla]
- **Ticari işlerde oran serbestisi** ve bileşik faiz yalnız cari hesap ile iki taraf için de ticari ödünçte, en az üç aylık dönemle. [Türk Ticaret Kanunu m. 8](https://soorgla.com/mevzuat/6102-turk-ticaret-kanunu/) [soorgla]
- **Mal ve hizmet tedarikinde geç ödeme:** ticari işletmeler arasında faiz oranını TCMB her yıl ocakta ilan eder; oran 3095'teki ticari gecikme faizinden en az sekiz puan fazladır. [Türk Ticaret Kanunu m. 1530](https://soorgla.com/mevzuat/6102-turk-ticaret-kanunu/) [soorgla] **Bu oran araçta yok** (aşağıda).
- **Gecikme zammı:** amme alacağında vadenin bitiminden itibaren her ay için ayrı ayrı; ay kesirleri günlük hesaplanır; Cumhurbaşkanı oranı değiştirebilir. [Amme Alacaklarının Tahsil Usulü Hakkında Kanun m. 51](https://soorgla.com/mevzuat/6183-amme-alacaklarinin-tahsil-usulu-hakkinda-kanun/) [soorgla]

**Numara çakışması:** `law_no: "3095"` aynı numaralı bir yönetmelikle çakışır. `law_type` verilmese de araç Kanunu seçiyor ve yönetmeliği `other_candidates`'ta gösteriyor; yine de `law_type: "Kanun"` ver, yanıttaki `statute.title`'ı kontrol et.

## Ticari iş mi, adi iş mi?

Bu ayrım **hukuki değerlendirmedir**; bu beceri karar vermez.
- Sor: alacak bir ticari işletmeyle ilgili mi, taraflar tacir mi, borçlu tüketici mi?
- İşin her iki taraf için ticari olup olmadığı, tek taraf için ticari işin diğer taraf için de ticari sayılıp sayılmayacağı (TTK m.3 ve m.19) `[model bilgisi — doğrulayın]` ve `[incele]`; ilgili alan becerisi (`sozlesme-incelemesi-tbk`, `sirketler-ticaret`, `icra-iflas`) belirler.
- Cevap gelmezse iki satır hesapla: "yasal faizle" ve "ticari temerrüt faiziyle", farkı göster, seçimi avukata bırak.

## Yarıyıl kuralı

3095 m.1 ve m.2'de oran **yılbaşında** önceki yılın 31 Aralık oranıyla belirlenir; 30 Haziran'daki oran 31 Aralık oranından **beş puan veya daha çok** farklıysa **yılın ikinci yarısında** 30 Haziran oranı (yasal faizde onun yüzde sekseni) geçerli olur.

Adımlar:
1. Hesap aralığındaki her takvim yılı için 31 Aralık (önceki yıl) ve 30 Haziran reeskont/avans oranlarını bul.
2. Fark ≥ 5 puansa yılı 01.01–30.06 ve 01.07–31.12 diye ikiye böl.
3. Yasal faizde ayrıca **kanun değişikliği** sınırı vardır: 7589 öncesi dönemde oran Cumhurbaşkanı kararıyla belirleniyordu `[model bilgisi — doğrulayın]`; araç bu dönemi ayrı kayıt olarak tutuyor ama dışarı vermiyor (aşağıda).

## Basit faiz — adım adım

```
Gün = bitiş tarihi − başlangıç tarihi (başlangıç günü sayılmaz)
Faiz = Anapara × (Yıllık oran / 100) × Gün / 365
Toplam = Anapara + Σ dönem faizleri
```

Örnek iskelet (sayılar yalnız biçim için; oranları araçtan yeniden çek):

| Dönem | Başlangıç | Bitiş | Gün | Oran (%) | Kaynak | Faiz (TL) |
|---|---|---|---|---|---|---|
| 1 | 15.03.2026 | 30.07.2026 | 137 | [eski dönem yasal faiz] | geçici yol `[doğrula]` | … |
| 2 | 31.07.2026 | 31.10.2026 | 93 | 31,00 (2026-07-31'den) | [soorgla] `legal_get_legal_interest_rates` | … |
| | | | | | **Toplam faiz** | … `[doğrula]` |

Kurallar:
- Oran değişim günü hangi döneme yazılır (değişiklik günü yeni orana mı)? Aracın `baslangic_tarihi` alanını yeni oranın ilk günü say; bunu tabloya not et.
- Kısmi ödemede mahsup sırası (önce masraf, faiz, sonra anapara — TBK m.100) `[model bilgisi — doğrulayın]`; kısmi ödeme varsa 🟠 teyit eşiği.
- Bileşik faiz yalnız TTK m.8/2 koşullarında; aksi hâlde basit faiz. Kullanıcı bileşik isterse koşulu sor.
- İcra takibinde takip tarihine kadar işlemiş faiz ayrı kalem, takip sonrası faiz oranı ayrı satır olarak yazılır (`icra-iflas`).

## Gecikme zammı (aylık)

```
Tam ay sayısı = vade bitiminden itibaren geçen tam aylar
Kesir gün = kalan günler
Gecikme zammı = Anapara × aylık oran/100 × tam ay + Anapara × aylık oran/100 × kesir gün / 30
```

- Oran aralık içinde değiştiyse (CBK ile) her dönemi ayrı hesapla. Eski CBK'leri bul: `legal_search_official_gazette` `query: "gecikme zammı"` + `date_from`/`date_to` (`search_in: "all"`). Başlık araması (`search_in: "title"`) güncel CBK'yi **kaçırdı**, yalnız 2005 kararını getirdi.
- Kesir günde 30 gün bölen `[model bilgisi — doğrulayın]`.
- Asgari tutar ve ceza nitelikli alacaklarda yarı oran kuralı madde metnindedir (6183 m.51/2-3); vergi ziyaı cezası, mahkeme kararıyla verilen ceza ve diğer cezalar farklıdır → `vergi` becerisi.
- **Gecikme faizi (VUK m.112) ve tecil faizi araçta ayrı tip değildir.** Gecikme faizinin gecikme zammı oranında uygulandığı `[model bilgisi — doğrulayın]`; tecil faizi bu araçta yok → tutar için `legal_calculate_tax` `hesap: "tecil_faizi"`; oranın dayanağı için `legal_search_official_gazette` `query: "tecil faizi"` `sort_by: "date_desc"`.

## Bilinen eksikler ve geçici yollar

| Eksik | Geçici yol |
|---|---|
| **Geçmiş oranlar araçtan alınamıyor** (parametre yok; yalnız güncel kayıt). | Reeskont/avans: `legal_search_official_gazette` `query: "Reeskont ve Avans İşlemlerinde Uygulanacak Faiz Oranlarının Tespiti"` `date_to: <31 Aralık ya da 30 Haziran>` `sort_by: "date_desc"`; o tarihte yürürlükte olan son tebliğin PDF'ini `legal_get_official_gazette_document` ile oku. Bulunan oran `[soorgla]`, hesap `[doğrula]`. Yasal faizin 7589 öncesi oranları için CBK/BKK'yi RG'de ara; bulunamazsa `[model bilgisi — doğrulayın]` |
| `ticari_temerut` başlangıcı 2026-01-01 ama politika faizi 2026-10-23'te değişti | Ticari temerrüt yıl içinde politika faiziyle değişmez; yalnız yarıyıl kuralı. Avans oranı 30.06'da 5 puan değişmiş mi RG'den kontrol et `[doğrula]` |
| TTK m.1530/7 geç ödeme faizi yok | Kullanıcıdan TCMB ilanını iste; `[doğrula — TCMB ocak ilanı]` |
| Mevduat faizi (kıdem tazminatında 1475 m.14 en yüksek mevduat faizi) yok | Kullanıcıdan bankaların ilan ettiği oranı iste `[doğrula]`; hesap `is-hukuku` |
| Tecil faizi yok | RG araması (yukarıda) |
| Kredi kartı oranları yalnız azami aylık; gecikme faizi yok | `[doğrula — TCMB]` |

## Teyit eşiği

Çok dönemli faiz, kısmi ödeme, bileşik faiz, döviz alacağı (TL'ye çevirme günü), ya da faizin dava değeri/takip tutarı olarak kullanılması → 🟠 bilirkişi / mali müşavir teyidi.

## Örnek çağrılar

```
legal_get_legal_interest_rates
legal_get_statute_article law_no: "3095" article_no: "1" law_type: "Kanun"
legal_get_statute_article law_no: "3095" article_no: "2" law_type: "Kanun"
legal_get_statute_article law_no: "6183" article_no: "51" law_type: "Kanun"
legal_search_official_gazette query: "Reeskont ve Avans İşlemlerinde Uygulanacak Faiz Oranlarının Tespiti" date_to: "2025-12-31" sort_by: "date_desc"
legal_search_official_gazette query: "gecikme zammı" date_from: "<AAAA-AA-GG>" date_to: "<AAAA-AA-GG>"
```
