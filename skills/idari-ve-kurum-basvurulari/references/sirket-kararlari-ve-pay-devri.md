# Şirket kararları (karar defteri) ve limited şirket pay devri

Anonim ve limited şirketlerde yönetim organı ya da genel kurul kararının karar defterine işlenecek metni; limited şirkette esas sermaye payı devri sözleşmesi ve onay kararı. Süreye bağlı bir itiraz değildir; risk **yanlış organ, yanlış nisap ve eksik şekil**dir. Sicil tescili ve noter işlemleri kullanıcıya bırakılır.

Esas şirketler hukuku analizi (pay devri vergisi, değerleme, ortaklar arası sözleşme, birleşme) bu dosyanın konusu değildir; esas analiz `../../sirketler-ticaret/SKILL.md` becerisindedir (pay devri şekil şartları: `../../sirketler-ticaret/references/pay-devri-ve-sermaye.md`; genel kurul ve yönetim kurulu kararları: `../../sirketler-ticaret/references/organlar-genel-kurul-ve-kararlar.md`).

---

## 1. Doğru organı seç

| Karar | Anonim şirket | Limited şirket |
|---|---|---|
| Günlük yönetim, şube açma, imza yetkisi, temsil | Yönetim kurulu (TTK m.390)  | Müdür / müdürler kurulu: birden fazla müdürde **çoğunlukla** karar, eşitlikte **başkanın oyu üstün**; şirket sözleşmesi farklı düzenleyebilir (TTK m.624/3)  |
| Şirket sözleşmesi değişikliği (adres → merkez değişikliği dâhil) | Genel kurul; sermayenin en az yarısı temsil edilmeli, mevcut oyların çoğunluğuyla karar (ikinci toplantıda üçte bir); merkezin yurt dışına taşınması oybirliği, işletme konusunun tamamen değişmesi ve imtiyazlı pay %75 (TTK m.421)  | Genel kurul (TTK m.616/1-a)  |
| Müdür atama/görevden alma | — | Genel kurul (TTK m.616/1-b)  |
| **Esas sermaye payı devrinin onayı** | — | **Genel kurul** — devredilemez yetki (TTK m.616/1-g)  |

Eski `draft_corporate_resolution` tanımı "Hisse Devri (Ltd.)" kararını müdürler kurulu/yönetim kurulu kararı seçenekleri arasında sunuyordu; limited şirkette pay devrinin onayı **genel kurulun devredilemez yetkisidir**, müdürler kurulu kararıyla verilemez.

**Adres değişikliği:** aynı il/ilçe içinde adres değişikliği ile **şirket merkezinin** değişmesi ayrı şeylerdir. Merkez değişikliği şirket sözleşmesi değişikliğidir ve limited şirkette ağırlaştırılmış nisaba tabidir (TTK m.621/1-f).  Hangisi olduğunu sor `[incele]`. Eski YAML'daki "MAKS uyumlu adres" ibaresi bir sicil uygulamasıdır `[doğrula]`.

## 2. Nisabı kontrol et

| Organ | Toplantı / karar nisabı | Dayanak |
|---|---|---|
| AŞ yönetim kurulu | Üye tam sayısının çoğunluğuyla toplanır, hazır bulunanların çoğunluğuyla karar alır; esas sözleşme ağırlaştırabilir. Eşitlikte konu sonraki toplantıya kalır, ikinci eşitlikte öneri reddedilmiş sayılır. Vekâletle katılım ve oy yok. | TTK m.390/1-3  |
| AŞ yönetim kurulu — **toplantısız (elden dolaştırma)** | Hiçbir üye toplantı istemezse, karar şeklinde yazılmış öneriye **üye tam sayısının çoğunluğunun yazılı onayı**; öneri tüm üyelere yapılmış olmalı; imzalı kâğıtlar karar defterine yapıştırılır ya da karara dönüştürülür | TTK m.390/4  |
| AŞ yönetim kurulu — geçerlilik | Kararların geçerliliği **yazılıp imzalanmış olmalarına** bağlıdır | TTK m.390/5  |
| Ltd. genel kurul — olağan | Kanun/sözleşmede aksi yoksa **toplantıda temsil edilen oyların salt çoğunluğu** | TTK m.620  |
| Ltd. genel kurul — önemli kararlar | Temsil edilen oyların **en az üçte ikisi** ve oy hakkı bulunan esas sermayenin **tamamının salt çoğunluğu** birlikte: işletme konusu değişikliği, oyda imtiyaz, pay devrinin **sınırlandırılması/yasaklanması/kolaylaştırılması**, sermaye artırımı, rüçhan hakkı, **merkez değişikliği**, fesih vb. | TTK m.621/1  |
| Tek ortaklı Ltd. | Tek ortak genel kurulun tüm yetkilerine sahiptir; kararları **yazılı** olmalıdır | TTK m.616/3  |

Pay devrinin **onayı** m.621'de sayılmaz; olağan nisaba (m.620) tabidir, ancak şirket sözleşmesi farklı düzenleyebilir — **şirket sözleşmesini iste.**

## 3. Limited şirket pay devri

- **Şekil:** devir ve devir borcunu doğuran işlemler **yazılı** yapılır ve **imzalar noterce onanır**. Ek ödeme, yan edim, ağırlaştırılmış rekabet yasağı, önerilmeye muhatap olma, önalım, geri alım, alım hakları ve sözleşme cezası koşulları varsa devir sözleşmesinde belirtilir. 
- **Onay:** sözleşmede aksi yoksa genel kurul onayı şarttır; **devir bu onayla geçerli olur**. Genel kurul sebep göstermeden reddedebilir; sözleşme devri yasaklayabilir; ret/yasakta haklı sebeple çıkma hakkı saklıdır. 
- **Zımni onay:** başvurudan itibaren **üç ay** içinde genel kurul reddetmezse onay verilmiş sayılır. 
- **Tescil:** pay geçişinin tescili için başvuruyu **şirket müdürleri** yapar; **30 gün** içinde yapılmazsa ayrılan ortak, adının silinmesi için sicile başvurabilir. 
- **Pay defteri:** şirket pay defteri tutar; ortaklar, payları ve payların devir ve geçişleri bu deftere yazılır (TTK m.594). 
- Vergi (damga vergisi, değer artış kazancı) ve SGK borç sorumluluğu yönü `[incele — mali müşavirle]`; tutar yazma.

---

## Görüşme soruları (eski `data_schema` alanlarından)

**Şirket kararı:**
| Alan | Soru |
|---|---|
| `company_name` | Tam ticaret unvanı (sicildeki gibi)? |
| `company_type` | Anonim mi limited mi? Tek ortaklı mı? |
| `organ_type` | Kararı hangi organ alıyor? (yukarıdaki tabloyla kontrol et; yanlışsa söyle) |
| `meeting_details.decision_no` / `decision_date` | Karar numarası ve tarihi? (defterdeki sıradaki numara) |
| `meeting_details.attendees` | Toplantıya katılanlar? Üye tam sayısı kaç? Toplantılı mı, elden dolaştırma mı? |
| `meeting_details.subject` | Kararın konusu? |
| `resolution_items` | Alınacak kararlar madde madde? (yetkide: kişi, süre, kapsam, münferit/müşterek; adreste: eski ve yeni şekil) |
| `voting_result` | Oy birliği mi çokluğu mu? Karşı oy var mı? |
| `signatories` | İmza atacaklar? |
| (yeni) | Şirket sözleşmesinde konuya ilişkin ağırlaştırıcı ya da özel hüküm var mı? (sözleşmeyi isteyin) |

**Pay devri:**
| Alan | Soru |
|---|---|
| `transferor_info` / `transferee_info` | Devreden ve devralanın ad-soyad/unvan, TCKN/VKN, adres? Devralan mevcut ortak mı, üçüncü kişi mi? |
| `share_details.count` / `nominal_value` / `total_value` | Devredilen pay adedi, bir payın itibari değeri, toplam itibari değer? Şirketin toplam sermayesi ve devir sonrası pay dağılımı? |
| `transfer_price` | Devir bedeli ve ödeme şekli (peşin, vadeli, ödendi mi)? |
| `meeting_date` / `decision_number` | Onay genel kurulunun tarihi ve karar no? |
| (yeni) | Şirket sözleşmesinde devri sınırlayan hüküm (önalım, onay şartı, yasak), ek ödeme veya yan edim yükümlülüğü var mı? |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6102"  article_no: "390" | "408" | "418" | "421"     # AŞ yönetim kurulu, genel kurul yetki ve nisaplar
legal_get_statute_article  law_no: "6102"  article_no: "595" | "598" | "599" | "616" | "620" | "621" | "623" | "624"   # Ltd.
legal_search_statute_semantic  sorgu: "ticaret sicili tescil başvurusu karar noter onayı"  mevzuat_tur: "kurum_yonetmeligi"   # Ticaret Sicili Yönetmeliği
legal_search_cases  mahkeme: "yargitay"  daire: "11. Hukuk Dairesi"  sorgu: "<ör. limited şirket pay devrinin genel kurul onayı olmadan geçersizliği>"  tarih_baslangic: "<son 3 yıl>"
```
Daire görevlendirmesi: 1.7.2026'dan itibaren uygulanan Yargıtay BGK 2026/1 (RG 30.06.2026) iş bölümünde "Ticaret Hukuku, Sigorta Hukuku, Bankalar Hukuku" temel görevli bölüm TTK'daki şirketler (anonim, limited, kollektif, komandit), ticaret sicili ve unvan uyuşmazlıklarını kapsıyor; RG metni OCR'lı olduğundan bölüm başlığı okunamıyor, ancak aynı karardaki hatırlatmalar TTK m.4 ticari davaları, ticari alım-satım ve finansal kiralamayı açıkça "11. Hukuk Dairesine" veriyor ve 2026'nın ilk yarısındaki genel kurul iptali / pay devri kararları 11. HD'den (ör. E. 2025/4085, K. 2026/1023, 23.02.2026). Yeni bir uyuşmazlıkta `daire` filtresini kullanmadan önce `legal_case_facets(mahkeme: "yargitay")` ile son kararların dairesini kontrol et. 

---

## Belge iskeleti — karar defteri sureti

```markdown
[ŞİRKET UNVANI]
[YÖNETİM KURULU / MÜDÜRLER KURULU / GENEL KURUL] KARARI

KARAR TARİHİ           : [___]
KARAR NO               : [___]
TOPLANTIYA KATILANLAR  : [ad-soyad, sıfat]   (üye tam sayısı: [___])
KARARIN KONUSU         : [___]

Şirket [yönetim kurulu / müdürler kurulu / ortaklar genel kurulu], yukarıda belirtilen tarihte şirket merkezinde
toplanarak [gündemi görüşmüş ve] aşağıdaki kararları almıştır:

1. [Karar maddesi — kişi, kapsam, süre, eski şekil / yeni şekil]
2. [___]

İşbu kararlar [oy birliği / … oya karşı … oy çokluğu] ile kabul edilmiştir. [Karşı oy gerekçesi: ___]

İMZALAR
[ad-soyad — sıfat — imza]   [ad-soyad — sıfat — imza]
```

## Belge iskeleti — pay devri seti (Ltd.)

```markdown
BÖLÜM 1 — ESAS SERMAYE PAYI DEVİR SÖZLEŞMESİ  (imzalar noterce onaylanacaktır)

DEVREDEN : [ad-soyad/unvan, TCKN/VKN, adres]
DEVRALAN : [ad-soyad/unvan, TCKN/VKN, adres]
ŞİRKET   : [unvan, sicil no, MERSİS no]

1. Devreden, şirketteki [adet] adet ve beheri [___] TL itibari değerli, toplam [___] TL itibari değerli esas
   sermaye payını, [___] TL bedel karşılığında, bütün hak ve yükümlülükleriyle devralana devretmiştir.
2. Bedel [ödeme şekli] ödenmiştir / ödenecektir.
3. [Varsa ek ödeme, yan edim, önalım vb. koşullar — TTK m.595/1]
4. Devralan şirket sözleşmesini okuduğunu ve kabul ettiğini beyan eder.
5. Devir, ortaklar genel kurulunun onayı ile geçerli olur (TTK m.595/2).

[Tarih]                     DEVREDEN [imza]                     DEVRALAN [imza]

BÖLÜM 2 — ORTAKLAR GENEL KURULU KARARI (onay)

KARAR TARİHİ : [___]   KARAR NO : [___]   KONU : Esas sermaye payı devrinin onayı
Şirket ortakları şirket merkezinde toplanarak; [devreden]'in şirketteki [adet] adet payının [devralan]'a devrine
ilişkin [noter, tarih, yevmiye no] onaylı devir sözleşmesinin onaylanmasına, devrin pay defterine işlenmesine ve
ticaret siciline tescil ve ilanı için müdürlerin başvurmasına [oy birliği / oy çokluğu] ile karar vermişlerdir.
Devir sonrası ortaklık yapısı: [tablo]

İMZALAR: [ortaklar]
```

## Sık hatalar

- 🔴 Limited şirkette pay devri onayını müdürler kurulu kararıyla vermek (TTK m.616/1-g).
- 🔴 Devir sözleşmesini noter onayı olmadan imzalatmak (TTK m.595/1).
- 🟠 Merkez değişikliğini basit adres değişikliği gibi olağan nisapla almak (TTK m.621/1-f).
- 🟠 Elden dolaştırma kararında önerinin tüm üyelere yapılmaması (TTK m.390/4).
- 🟡 Şirket sözleşmesini görmeden nisap yazmak.

---

