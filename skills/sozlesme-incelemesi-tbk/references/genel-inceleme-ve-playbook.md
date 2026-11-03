# Genel sözleşme incelemesi ve büro playbook'u

Her sözleşme incelemesinin tabanı. Türe özgü dosya (satış, eser, kefalet…) bunun üstüne eklenir.

## Ne zaman kullanılır
- "Bu sözleşmeyi inceler misin", "imzalayabilir miyiz", "riskli maddeler neler", "karşı tarafın taslağına revizyon hazırla".
- Karşı tarafın kâğıdı (biz müşteri / alıcıyız) ya da bizim kâğıdımızın karşı taraftan dönen revizyonu.
- Türü ne olursa olsun; tür belirsizse önce `sozlesme-turleri-tablosu.md`.

İş akışı Anthropic `commercial-legal` deposundaki `review` ve `vendor-agreement-review` becerilerinden uyarlanmıştır; ABD'ye özgü unsurlar (work product, eyalet otomatik yenileme kanunları, UCC) çıkarılmış, yerine TBK/TTK kuralları konmuştur.

---

## 1. Playbook: standart / kabul edilebilir / kırmızı çizgi

Upstream'in ana fikri: **inceleme piyasa standardına değil, bu büronun ya da şirketin kendi pozisyonuna göre yapılır.** Profilde `## Sözleşme playbook'u` bölümü yoksa:

1. Kullanıcıya iki seçenek sun: (a) 5 soruluk kısa playbook kurulumu, (b) **geçici mod** — genel varsayılanlarla incele, her bulguyu `[GEÇİCİ — playbook yok]` etiketle.
2. Geçici modda **YEŞİL "imzaya gönderilebilir"** sonucu verilmez; en iyi sonuç "SARI — avukat onayıyla imzalanabilir"dir.
3. İnceleme sırasında playbook'ta karşılığı olmayan bir maddeyle karşılaşırsan sor: "Playbook'unuz [konu] hakkında sessiz. Hangi durumda YEŞİL/SARI/KIRMIZI sayalım? Profile ekleyeyim mi?" — kullanıcı onay verirse profile yaz.

Profil şablonu (kullanıcı onayıyla `~/.claude/plugins/config/soorgla-hukuk/profil.md` dosyasına eklenir):

```markdown
## Sözleşme playbook'u
- Etkin taraf: [DOLDURULACAK — satış (biz tedarikçiyiz) | satın alma (biz müşteriyiz) | ikisi de]
- yonlendirme_onayi: [evet | hayır]

### Satın alma tarafı (karşı tarafın kâğıdı)
#### Sorumluluk sınırı
- Doğrudan zarar tavanı: [DOLDURULACAK — ör. "son 12 ayda ödenen bedel"]
- Dolaylı zarar / kâr kaybı: [hariç | tavanlı | tavansız]
- Tavanın dışında kalması gerekenler: [ör. kast ve ağır kusur (TBK 115 zaten), gizlilik ihlali, fikri mülkiyet, kişisel veri ihlali]
- Tavan matrahı tanımı: [hangi bedel tanımını kabul ederiz]
- Kabul edilebilir geri çekilme: [ ]
- Asla kabul etmeyiz: [ ]
#### Tazmin (rücu, üçüncü kişi talepleri)
#### Cezai şart
- Bize yüklenen cezai şart: [kabul ediyoruz / üst sınırla / asla]
- Tacir olduğumuz için indirim isteyemeyeceğimizi (TTK 22) biliyoruz: [evet]
#### Süre, yenileme, fesih
#### Uygulanacak hukuk, yetki, tahkim
- Tercih: [ör. Türk hukuku, İstanbul (Çağlayan) mahkemeleri] · Kabul edilebilir: [ ] · Yükselt: [ ] · Asla: [ ]
#### Ödeme ve para birimi (dövizli bedel — 32 sayılı Karar kontrolü)
#### Kişisel veri (→ kvkk)
#### Bitiş hattı (tek madde — her incelemede ilk kontrol)

### Satış tarafı (bizim kâğıdımız)
[aynı başlıklar]

### Yükseltme
- Tutar eşiği ve onaylayan: [DOLDURULACAK]
- Otomatik yükseltme: [ör. tavansız sorumluluk, fikri mülkiyet devri, münhasırlık, rekabet yasağı, yabancı hukuk seçimi]
```

**Sorumluluk sınırı dört pozisyondur, tutar en önemsizidir** (upstream "liability cap decision procedure"). Her incelemede ayrı ayrı yaz:
1. Tavan doğrudan zararı mı, her türlü sorumluluğu mu kapsıyor; dolaylı zarar ve kâr kaybı nasıl?
2. **Tavan matrahını aynen alıntıla** ("son 12 ayda ödenen" ile "sözleşme süresince ödenecek" arasında kat kat fark vardır); belirsizse işaretle.
3. Tavanın üstünde kalanlar (istisnalar) ile altında kalanları say; tavanın gerçekten anlamlı bir alanı kapsayıp kapsamadığını söyle.
4. **Türk hukuku süzgeci:** borçlunun ağır kusurundan sorumsuzluk anlaşması kesin hükümsüzdür; hizmet sözleşmesinden doğan her türlü sorumsuzluk anlaşması ve izinle yürütülen meslek/sanat için hafif kusurdan sorumsuzluk da kesin hükümsüzdür (TBK m.115). Bu nedenle "hiçbir durumda sorumlu değildir" ibaresi ağır kusur bakımından zaten işlemez; bunu tavan analizine yaz.

## 2. Yönlendirme tablosu (ilk okuma, hızlı)

| Soru | Cevap |
|---|---|
| Sözleşmenin türü ve ekleri | [ana başlık; Ek-1 …, Ek-2 …] |
| Biz kimiz / kimin kâğıdı | |
| Karşı taraf | [büyük kurum (pazarlık etmez) / küçük şirket (bizim kâğıdımızı alır)] |
| Bedel ve para birimi | [TL / döviz / dövize endeksli → `odunc-ve-yabanci-para.md` §2] |
| Süre, yenileme | [otomatik yenileme ve itiraz süresi] |
| Taraflar tacir mi, tüketici var mı | [→ `genel-islem-kosullari-ve-tuketici.md`] |
| Kişisel veri işleniyor mu, DPA eki var mı | [var / atıfla / yok → `../../kvkk/SKILL.md`] |
| Uygulanacak hukuk, yetki, tahkim | |
| İmza yetkisi | [imza sirküleri, müşterek/münferit] |

**Bedel sözleşmede değil siparişte ise** (çerçeve sözleşme + sipariş formu): yükseltme eşiğini tahminle uygulama; kullanıcıdan bedeli iste ya da "eşik üstü varsayıldı" diye yaz (upstream kuralı).

**Ek atıfla dahil edilmişse** ("…internet sitesindeki genel şartlar", "…KVKK eki"): okunmamış ek ile hiç olmayan ek farklı boşluklardır; ayrı etiketle. Okumadan eksiksiz analiz yapılmış gibi davranma. Ayrıca atıfla dahil edilen genel şartlar TBK m.21 bilgilendirme şartı bakımından ayrı risk taşır.

## 3. Kontrol listesi (her sözleşmede)

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TÜR | Nitelendirme doğru mu; karma sözleşmede hangi hükümler uygulanır? | TBK genel; `sozlesme-turleri-tablosu.md` | Başlık bağlamaz, içerik belirler `[incele]` |
| ŞEKİL | Türün geçerlilik şekli (yazılı, el yazısı, resmî, miras sözleşmesi şekli) karşılanmış mı? Sonradan yapılan değişiklik de aynı şekle tabi mi? | TBK m.12-13; türe özgü madde | Şekil eksikse 🔴 |
| TARAF-SIFATI | Taraflar tacir mi, tüketici mi? Tüketici varsa 6502 ve haksız şart denetimi. | TTK m.12, m.18-22; 6502 m.3 | |
| İMZA-YETKİSİ | İmzalayanın temsil yetkisi (imza sirküleri, müşterek imza)? Yetkisiz temsil hâlinde sözleşme onaya kadar bağlamaz. | TBK m.46-47; TTK (şirket temsili) | Eski YAML "askıda hükümsüz" diyordu; sonuç doğru, madde atfı eksikti |
| GİK | Tek taraflı hazırlanmış, çok sayıda sözleşmede kullanılan matbu hükümler var mı? Bilgilendirme yapılmış mı, şaşırtıcı hüküm var mı? | TBK m.20-25 | Ayrıntı: `genel-islem-kosullari-ve-tuketici.md` |
| CEZAİ-ŞART | Türü (seçimlik / ifaya eklenen / dönme cezası), karşılıklı mı, aşırı mı; borçlu tacir mi? | TBK m.179-182; TTK m.22 | Ayrıntı: `cezai-sart-ifa-ve-sorumluluk.md` |
| SORUMLULUK | Sorumluluk sınırı, dolaylı zarar, ağır kusur istisnası | TBK m.115 | §1'deki dört pozisyon |
| FAİZ | Akdî faiz ve temerrüt faizi üst sınırları; bileşik faiz | TBK m.88, m.120; TBK m.388/3; 6502 m.4/7 | Oran araçtan; tüketici işleminde bileşik faiz uygulanmaz |
| DÖVİZ | Bedel döviz cinsinden ya da dövize endeksli mi; taraflar Türkiye'de yerleşik mi; istisna var mı? | 32 sayılı Karar m.4/g; 2008-32/34 Tebliğ m.8 | Ayrıntı: `odunc-ve-yabanci-para.md` §2 |
| SÜRE-FESİH | Belirli/belirsiz süre, otomatik yenileme, fesih bildirimi süresi ve şekli, haklı nedenle fesih | TBK genel; tacirler arasında TTK m.18/3 şekli | |
| MÜCBİR-UYARLAMA | Mücbir sebep tanımı, bildirim yükümlülüğü; aşırı ifa güçlüğünde uyarlama/fesih | TBK m.136-138 | TBK m.138 yabancı para borçlarına da uygulanır |
| DEVİR | Sözleşmenin/alacağın devri ve kontrol değişikliği | TBK m.183 vd., m.205 | |
| GİZLİLİK | Gizlilik süresi, ticari sır, çalışanlara yayılma | TBK genel; TTK haksız rekabet m.55 | Ayrı NDA varsa `nda-ve-niyet-mektubu.md` |
| KVKK | Kişisel veri aktarımı, veri işleyen rolü, yurt dışı aktarım | 6698 | → `../../kvkk/SKILL.md`; burada yalnız işaret |
| YETKİ | Yetki şartı yalnız tacirler veya kamu tüzel kişileri arasında geçerli; tüketiciye karşı yetki şartı tüketicinin yerleşim yeri yetkisini kaldırmaz | HMK m.17; 6502 m.73/5 | |
| TAHKİM | Tahkim şartı açık mı (kurum, yer, dil, hakem sayısı); tüketici ve iş uyuşmazlığında sınırlar | HMK m.407 vd.; MTK 4686 | |
| ARABULUCULUK | Ticari parasal alacaklarda dava şartı arabuluculuk; tüketici mahkemesi uyuşmazlıklarında da (THH görevi hariç) | TTK m.5/A; 6502 m.73/A | Sözleşmeye "önce arabuluculuk" yazmak dava şartının yerine geçmez |
| UYGULANACAK-HUKUK | Yabancı unsur varsa hukuk seçimi | MÖHUK 5718 m.24 | Yabancı hukuk seçilmişse ORTAK-KURALLAR.md §2 |
| İSPAT | Delil sözleşmesi, e-posta/elektronik kayıtların delil sayılması | HMK m.193 | |
| DAMGA | Nüsha sayısı ve damga vergisi yükü kimde | 488 s. Kanun | Oran yazma; mali müşavir `[doğrula]` |

Tablo tabandır; sözleşmede başka bir sorun görürsen ekle.

## 4. Ayıklama: YEŞİL / SARI / KIRMIZI

| Kova | Ölçüt | Sonraki adım |
|---|---|---|
| **YEŞİL** | Avukatça onaylanmış playbook pozisyonunun içinde; emredici hükme aykırılık yok | Not et, pazarlık sermayesi harcama |
| **SARI** | Standarttan sapma ama kırmızı çizgi değil, ya da playbook sessiz | Avukat bakmalı; ilk turda iste, son açık madde ise bırakılabilir |
| **KIRMIZI** | "Asla kabul etmeyiz" listesinde; emredici hükme aykırı; şekil eksik; bitiş hattı | İmzalamadan önce düzelt; düzelmezse yükselt ya da vazgeç |

Kalibrasyon: her şey KIRMIZI değildir. Belirsizse bir üst kovaya yuvarla (ORTAK-KURALLAR.md §8), ama gerekçesini yaz.

**Karşı taraf bağlamı:** büyük kurumlar matbu metinlerini nadiren değiştirir; KIRMIZI'nın gerçekten bitiş hattı mı, yoksa "bizim formumuzdan farklı" mı olduğunu ayır ve kararı yükseltme kişisine bırak. Küçük karşı tarafta en hızlı yol çoğu zaman "bizim formumuzu kullanalım"dır.

**Kendi lehimize** maddeleri ayrıca listele: başka bir maddede geri adım atarken takas malzemesidir.

## 5. Revizyon (redline) dili
- En küçük değişiklik: kelime → ibare → cümle → bent → madde. Bütün maddeyi ancak kaçınılmazsa yeniden yaz ve karşı tarafa söyle.
- Her revizyon yapıştırılmaya hazır Türkçe metin olur; "gözden geçirilmeli" gibi muğlak öneri yok.
- Karmaşık yeniden yazım gerektiren madde avukat olmayan kullanıcı için "Madde X — hukuk birimine yönlendirin" diye bırakılır (upstream "complexity filter").
- Word izlenen değişiklik istenirse ortamdaki docx becerisini kullan (ORTAK-KURALLAR.md §13/6); yoksa markdown tabloda "eski / yeni" ver.

## 6. Süreler (sözleşme incelemesinde sık çıkanlar)

| Süre | Dayanak | Not |
|---|---|---|
| Aşırı yararlanmada iptal: öğrenme/zor durumun kalkmasından 1 yıl, her hâlde kuruluştan 5 yıl | TBK m.28/2 | Hak düşürücü |
| Genel zamanaşımı 10 yıl; dönemsel edimler, vekâlet, komisyon, acentelik, eser (ağır kusur hariç) 5 yıl | TBK m.146-147 | |
| Tacirler arası satışta ayıp ihbarı: açık ayıpta 2 gün, açık olmayanda teslimden 8 gün içinde inceleme ve ihbar | TTK m.23/1-c | Bkz. `satis-trampa-bagislama.md` |
| Acentelikte belirsiz süreli sözleşmenin feshi 3 ay önceden; denkleştirme istemi sona ermeden itibaren 1 yıl | TTK m.121/1, m.122/4 | |
| Ticari arabuluculuk süresi: görevlendirmeden 6 hafta, zorunlu hâlde en çok 2 hafta uzatma | TTK m.5/A/2 | |

Otomatik yenilemeli sözleşmelerde **yenileme tarihini ve itiraz son gününü** her durumda tabloya yaz (upstream renewal-tracker devri); son günü `legal_check_holiday` ile kontrol et.

## 7. Görüşme soruları
1. Kimin adına? Biz hangi taraftayız; kâğıt kimin?
2. Sözleşmenin tamamı ve tüm ekleri (şartname, sipariş formu, genel şartlar, KVKK eki) elinizde mi?
3. Toplam bedel ve süre? Bedel döviz mi, taraflardan biri yurt dışında yerleşik mi?
4. Taraflar tacir mi; karşı tarafta tüketici var mı?
5. Bu karşı tarafla daha önce imzalanmış sözleşme var mı (verilmiş tavizler)?
6. İş birimi için olmazsa olmaz ticari şartlar neler; en çok neye bakmamı istersiniz?
7. İmza tarihi ve imza süreci (ıslak, e-imza, noter)?

## 8. MCP adımları
```
legal_get_statute_article law_no: "6098" article_no: "20" | "21" | "25" | "28" | "88" | "115" | "120" | "138" | "146" | "147"
legal_get_statute_article law_no: "6102" article_no: "18" | "22" | "23"
legal_list_statute_articles law_no: "6102" article_no: "5" include_content: true # 5/A
legal_list_statute_articles law_no: "6502" article_no: "73" include_content: true # 73/A
legal_get_statute_article law_no: "6100" article_no: "17"
legal_search_official_gazette query: "Büyük Genel Kurulu" search_in: "title" sort_by: "date_desc" # güncel daire iş bölümü
legal_search_cases mahkeme: "yargitay" daire: "<iş bölümüne göre>" tarih_baslangic: "<son 3 yıl>"
    sorgu: "<ör. matbu sözleşmedeki tek taraflı fesih yetkisi genel işlem koşulu olarak yazılmamış sayılır>"
legal_get_case_document belge_id: "<seçilen karar>"
legal_get_legal_interest_rates # faiz maddesi varsa
```

## 9. Çıktı iskeleti
SKILL.md Adım 6'daki kalıp. Kısa sorularda (tek madde) yalnız ilgili bulgu bloğunu ver. 10'dan fazla bulgu varsa önce KIRMIZI'ları ver, SARI ve YEŞİL'i tabloya indir.

Kanal özeti (iş birimi "sorun var mı?" diye sorduysa): `[Karşı taraf] [tür] — DEĞİŞİKLİK GEREKİYOR. 1 KIRMIZI (sorumluluk tavansız, m.12), 2 SARI. Onay: [kişi].`

## 10. Sık hatalar
- Piyasa standardını büro playbook'u sanmak; playbook yokken YEŞİL vermek.
- Sorumluluk sınırını tek satırda geçmek; tavan matrahını alıntılamamak.
- TBK m.115'i unutmak: ağır kusur muafiyeti zaten hükümsüzdür, "kabul edilebilir" sayılamaz.
- Tacir borçlunun cezai şartta indirim isteyemeyeceğini (TTK 22) atlamak ya da tersine "hiçbir koşulda indirilmez" demek (ekonomik mahvolma istisnası: `cezai-sart-ifa-ve-sorumluluk.md`).
- Yetki şartını tüketici ya da tacir olmayan tarafa karşı geçerli saymak.
- Sözleşmedeki "önce arabulucuya gidilir" maddesini dava şartı arabuluculuğun yerine geçirmek ya da tersine dava şartını unutmak.
- Dövizli bedeli 32 sayılı Karar istisnalarını kontrol etmeden kabul etmek.
- Atıfla dahil edilmiş genel şartları okumadan "temiz" demek.
- Daire iş bölümünü eski bir yılın kararından yazmak (eski YAML'lar "2025 iş bölümü"nü sabit yazıyordu).

---
