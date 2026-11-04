# Satış, trampa (mal değişimi) ve bağışlama

Mülkiyeti devir borcu doğuran sözleşmelerin incelemesi: taşınır ve taşınmaz satışı, taksitle satış, ticari satış, trampa, bağışlama.

## Ne zaman kullanılır
- Satış sözleşmesi, sipariş formu, tedarik sözleşmesi (tek seferlik mal), taşınmaz satış vaadi, araç satışı, taksitli satış.
- Mal karşılığı mal değişimi (takas).
- Bağış, hibe, "karşılıksız devir", koşullu bağış.

Önce her zaman: `genel-inceleme-ve-playbook.md`. Tüketici varsa: `genel-islem-kosullari-ve-tuketici.md`.

---

## 1. Satış

### Kontrol listesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ŞEKİL-TAŞINMAZ | Taşınmaz satışı **resmî şekilde** (tapu müdürlüğünde; Noterlik K. m.60/3 noterde taşınmaz satış sözleşmesi yapılmasına da yer veriyor) mi? Taşınmaz satış vaadi, alım ve geri alım sözleşmeleri de resmî şekil ister; önalım sözleşmesi yazılı şekil | TBK m.237; TMK m.706; 2644 m.26 | Adi yazılı taşınmaz satışı ve vaadi geçersiz → 🔴. Satış vaadi noterde **düzenleme şeklinde** yapılır `[incele]`  |
| TARAF-NİTELİĞİ | Alıcı tüketici mi tacir mi? Tüketiciyse 6502 (ayıp, cayma, haksız şart); tacirler arasıysa TTK m.23 | 6502 m.3; TTK m.23 | Bu ayrım uygulanacak rejimi kökten değiştirir |
| AYIP-TÜKETİCİ | Tüketicinin seçimlik hakları (dönme, indirim, onarım, ayıpsız misliyle değişim) kısıtlanmış mı? | 6502 m.11 | Kısıtlama haksız şart → KIRMIZI  |
| AYIP-KARİNESİ | Teslimden itibaren 6 ay içinde ortaya çıkan ayıp teslimde var sayılır; ispat satıcıda | 6502 m.10/1 | Malın ya da ayıbın niteliğiyle bağdaşmıyorsa karine işlemez |
| AYIP-İHBAR (genel) | Alıcı imkân bulur bulmaz gözden geçirip uygun sürede bildirmeli; gizli ayıp sonradan anlaşılırsa **hemen** | TBK m.223 | İhmal → satılan kabul edilmiş sayılır |
| AYIP-İHBAR (tacirler) | Açık ayıpta **2 gün**; açık değilse teslimden itibaren **8 gün** içinde inceleme/inceletme ve ihbar | TTK m.23/1-c | Tacir alıcıda sözleşmeye daha uzun süre yazdırmak lehedir |
| AYIP-ZAMANAŞIMI | Taşınırda devirden itibaren 2 yıl (satıcı ağır kusurluysa bu süreden yararlanamaz); yapı ayıbında mülkiyetin geçişinden 5 yıl, ağır kusurda 20 yıl; tüketicide teslimden 2 yıl, konut/tatil amaçlı taşınmazda 5 yıl, hile ya da ağır kusurla gizlenmişse süre uygulanmaz | TBK m.231, m.244/3; 6502 m.12 | Sözleşmede süreyi kısaltan kayıt → TBK 115 / 6502 süzgeci |
| AYIP-SORUMSUZLUK | Satıcının ayıptan sorumsuzluk kaydı; satıcı satılanı ayıplı devretmekte ağır kusurluysa sorumsuzluk kaydı kesin hükümsüz | TBK m.221 |  |
| TAKSİT-ŞEKİL | Taksitle satış (taşınır, bedel teslimden sonra kısım kısım) **yazılı** şekil; ticari satıcıda zorunlu içerik (peşin fiyat, toplam bedel, en az iki taksit, 7 gün geri alma hakkı, faiz üst sınırı vb.) | TBK m.253 | Tüketicide ayrıca 6502 m.17-19 |
| TAKSİT-CAYMA | Tüketici 7 gün içinde gerekçesiz ve cezasız cayabilir; bilgilendirme ispatı satıcıda | 6502 m.18 | |
| TAKSİT-MUACCELİYET | Kalan borcun tamamını isteme ancak: satıcı tüm edimlerini ifa etmiş + tüketici bedelin **en az onda birini** oluşturan **art arda iki taksidi** ya da **en az dörtte birini** oluşturan bir taksidi ödememiş + **en az 30 gün** süreli muacceliyet uyarısı | 6502 m.19 | Eski YAML "onda bir" ve "dörtte bir" eşiklerini atlıyordu |
| MÜLKİYETİ-SAKLI-TUTMA | Mülkiyeti saklı tutma kaydı **resmî şekilde** yapılıp alıcının yerleşim yeri **noterliğindeki özel sicile** kaydedilmiş mi? Hayvan satışında yapılamaz | TMK m.764 | Eski YAML bunu "TBK 253" diye gösteriyordu; TBK 253 taksitle satışın tanımı ve şeklidir. Sicil kaydı yoksa kayıt geçersiz → KIRMIZI (satıcı tarafı) |
| ZAPT | Üçüncü kişinin üstün hakkı (rehin, haciz, şerh) — tapu ve sicil kontrolü | TBK m.214-218 |  |
| DÖVİZ | Taşınmaz satışında Türkiye'de yerleşikler arasında döviz/dövize endeksli bedel **yasak**; taşıt dışı taşınır satışında serbest; taşıt satışında yasak | 2008-32/34 Tebliğ m.8/1, 8/9 | `odunc-ve-yabanci-para.md` §2 |
| YÜZÖLÇÜMÜ | Taşınmaz yazılı yüzölçümünü karşılamıyorsa tazminat; tapuya resmî ölçümle yazılmışsa satıcı özel olarak üstlenmedikçe sorumlu değil | TBK m.244/1-2 | |

### Kimin adına?
**Alıcı / tüketici koruyucusu:** sözleşme koşullarının süre içinde aleyhe değiştirilmemesi (6502 m.4/2), ayıp karinesi, ek bedel yasağı (6502 m.4/3), ayıp ihbar süresinin uzatılması, satıcının ağır kusurunda zamanaşımı korunması.

**Satıcı / ticari strateji:** tacir alıcıya karşı TTK 23 ihbar sürelerini sözleşmede teyit et; muayene yükümlülüğünü açık yaz; taksitte muacceliyet şartlarını 6502 m.19'a uydur; mülkiyeti saklı tutmayı **noterde resmî şekil + sicil** ile kur.

## 2. Trampa (mal değişimi)
| Kod | Kontrol | Dayanak |
|---|---|---|
| ÇİFT-STATÜ | Her taraf verdiği mal bakımından satıcı, aldığı mal bakımından alıcı; satış hükümleri uygulanır | TBK m.282-283  |
| ŞEKİL | Mallardan biri taşınmazsa resmî senet (tapu) | TBK m.237 kıyasen; TMK m.706 |
| ZAPT-AYIP | Karşılıklı zapt ve ayıp sorumluluğu | TBK m.284 |
| DENKLİK | Değer farkı varsa üste para (denkleştirme) yazılmış mı? Açık oransızlık ve zor durumdan yararlanma → aşırı yararlanma | TBK m.28 | Süre: öğrenmeden/zor durumun kalkmasından 1 yıl, her hâlde 5 yıl  |
| TİCARİ | Tacirler arası mal değişiminde TTK m.23 ihbar süreleri | TTK m.23/1 |

Tapu harcı ve vergi: her iki taşınmaz için ayrı harç doğabilir; beyan değerini emsalin altında gösterme riskini **işaretle**, oran yazma `[doğrula — mali müşavir]`.

## 3. Bağışlama

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ŞEKİL | Bağışlama **sözü** yazılı; taşınmaz ya da taşınmaz üzerindeki ayni hak için **resmî** şekil. Şekle aykırı söz yerine getirilirse elden bağışlama hükmünde; ama resmî şekil gerektirenlerde bu kural uygulanmaz | TBK m.288 | Elden bağışlama taşınırda teslimle (TBK m.289)  |
| EHLİYET | Bağışlayanın fiil ehliyeti; kısıtlının bağışlaması | TBK m.286 |  |
| AHLAKİ-ÖDEV | Ahlaki ödevin yerine getirilmesi bağışlama sayılmaz | TBK m.285 |  |
| YÜKLEME | Koşul/yükleme yerine getirilmezse geri alma | TBK m.295 | |
| GERİ-ALMA | Geri alma sebepleri (ağır suç, aile hukuku ödevlerinin önemli ihlali, yüklemenin yerine getirilmemesi) | TBK m.295 |  |
| GERİ-ALMA-SÜRESİ | Sebebin öğrenilmesinden itibaren **1 yıl**; bağışlayan süre içinde ölürse mirasçılara geçer; sağlığında öğrenemediyse mirasçılar ölümden itibaren 1 yıl | TBK m.297 | Hak düşürücü süre |
| DÖNEMSEL | Dönemsel edimli bağışlama, aksi kararlaştırılmadıkça bağışlayanın ölümüyle sona erer | TBK m.298 |  |
| SAKLI-PAY | Mirasçıların saklı payını ihlal riski, tenkis; tapuda bağışla yapılan devirde muris muvazaası iddiası | TMK m.560 vd., m.565 | → `../../aile-miras/SKILL.md` |
| VERGİ | Veraset ve intikal vergisi yükümlüsü | 7338 s. Kanun | Oran/tutar yazma `[doğrula]` |

Daire notu (2026/1 iş bölümü): tapuda bağış suretiyle yapılan devirlerde TBK m.290-295'e dayalı geri alma davaları gayrimenkul hukuku dairesine gider; güncel BGK kararıyla teyit et. 

## 4. Süreler (özet)

| Süre | Dayanak |
|---|---|
| Tacirler arası ayıp ihbarı: 2 gün (açık) / 8 gün (inceleme+ihbar) | TTK m.23/1-c |
| Taşınır ayıp zamanaşımı 2 yıl; yapı 5 yıl (ağır kusurda 20) | TBK m.231, m.244/3 |
| Tüketici: 2 yıl; konut/tatil taşınmazı 5 yıl; ikinci elde en az 1 / 3 yıl | 6502 m.12 |
| Ayıp karinesi 6 ay | 6502 m.10/1 |
| Taksitle satışta cayma 7 gün; muacceliyet uyarısı en az 30 gün | 6502 m.18-19; TBK m.253 |
| Bağışlamayı geri alma 1 yıl | TBK m.297 |
| Aşırı yararlanma 1 yıl / 5 yıl | TBK m.28/2 |

## 5. Görüşme soruları
1. Satılan taşınır mı, taşınmaz mı (yapı mı)? Tapu kaydı ve takyidatlar?
2. Alıcı tüketici mi tacir mi? Satıcı tacir mi?
3. Bedel peşin mi, taksitli mi? Döviz mi?
4. Teslim tarihi, muayene ve ayıp bildirimi nasıl ve ne zaman yapıldı?
5. Mülkiyeti saklı tutma isteniyor mu? Noter sicili?
6. (Bağışta) Bağışlayanın mirasçıları kimler; başka bağış var mı; koşul/yükleme?

## 6. MCP adımları
```
legal_get_statute_article  law_no: "6098"  article_no: "221" | "223" | "231" | "237" | "244" | "253" | "282" | "284" | "288" | "295" | "297"
legal_get_statute_article  law_no: "6102"  article_no: "23"
legal_get_statute_article  law_no: "4721"  article_no: "706" | "764"
legal_get_statute_article  law_no: "6502"  article_no: "10" | "11" | "12" | "18" | "19"
legal_get_statute_article  law_no: "11990"  article_no: "8"          # 32 s. Karar Tebliği, dövizli bedel
legal_search_cases  mahkeme: "yargitay"  daire: "<güncel iş bölümü: ticari satış 11. HD, adi satış 3. HD, satış vaadi 7. HD>"
    sorgu: "<ör. tacirler arası satışta ayıbın sekiz gün içinde ihbar edilmemesi nedeniyle malın kabul edilmiş sayılması>"
```

## 7. Çıktı iskeleti
`genel-inceleme-ve-playbook.md` §9 kalıbı + şu ek blok:
```markdown
### Satışa özgü kontrol
| Şekil | Ayıp ihbarı rejimi | Zamanaşımı | Taksit / cayma | Mülkiyeti saklı tutma | Dövizli bedel |
|---|---|---|---|---|---|
```

## 8. Sık hatalar
- Tacirler arası satışta TBK 223'ün "uygun süre"sini uygulamak; TTK 23'ün 2/8 günü atlamak.
- Mülkiyeti saklı tutmayı sözleşmeye yazmayı yeterli sanmak (TMK 764: resmî şekil + noter sicili).
- Taşınmaz satış vaadini adi yazılı ya da onaylama şeklinde kabul etmek.
- 6502 m.19 muacceliyet eşiklerini eksik yazmak.
- Bağışlamayı geri alma süresini zamanaşımı sanmak (hak düşürücü).

---

