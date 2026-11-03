# Kira takvimi ve ihtarlar

**Ne zaman kullanılır:** "ne zamana kadar bildirmeliyim", "ihtarnameyi ne zaman çekeyim", "süre kaçtı mı", "kiracıya kaç gün süre vermeliyim" sorularında; bir sözleşme incelemesinin ya da tahliye değerlendirmesinin sonunda **takvim** çıkarırken.

Upstream `commercial-legal/skills/renewal-tracker` uyarlaması: kira hukukunda da asıl risk, sözleşmeden bir kez çıkarılan tarihin unutulmasıdır. Bu dosya sözleşmeden **yıllık takvim** üretir ve her bildirim için yalnız "son gün"ü değil, **"gönderme son günü"**nü (tebliğ süresi payı düşülmüş tarih) gösterir.

İhtarname metni bu becerinin işi değildir → `../../hukuk-yargilamasi-dilekce/references/ihtarname.md`. Vatandaşın gayriresmî uyarı yazısı → `../../vatandas-basvurulari/references/komsu-ev-sahibi-uyari.md`.

---

## Takvim nasıl çıkarılır

1. **Kira yılı:** sözleşmenin başlangıç günü (ör. 15.03.2021 → her yıl 15 Mart - 14 Mart). Takvim yılı değildir.
2. **İlk süre sonu** ve sonraki **uzama yılları** (m.347/1).
3. **On yıllık uzama sonu:** ilk süre + 10 uzama yılı. Ondan sonraki her uzama yılının bitiminden **3 ay önce** kiraya verenin sebepsiz fesih bildirimi penceresi.
4. **Beş yıl eşiği** (m.344/3 rayiç tespit) ve her beş yıl.
5. Her kira yılı için **m.345 tespit penceresi**: yeni dönemden en az 30 gün önce dava ya da yazılı artırım bildirimi.
6. Her kira yılı sonu için **m.350 ihtiyaç davası penceresi** (yıl sonundan itibaren 1 ay) ve bu pencerenin ilk günlerinde **arabuluculuk başvurusu**.
7. Yeni malik için: tapu edinme + 1 ay (bildirim), edinme + 6 ay (dava hakkı) ya da süre sonu + 1 ay.
8. Kiracı için: süre bitiminden en az **15 gün önce** sona erdirme bildirimi (konut/çatılı işyeri, belirli süreli).

Hesaplanan her son günü `legal_check_holiday` ile kontrol et. TBK süreleri `legal_calculate_deadline`'da tanımlı değil; elle hesapla ve `[doğrula]` işaretle. Bir sürenin son günü kanunen tatil olan güne denk gelirse kendiliğinden izleyen ilk iş gününe geçer; aksine anlaşma geçerlidir (TBK m.93). Sözleşmede aksine hüküm var mı kontrol et.

### Gönderme payı (upstream "send_by" mantığı)
Bildirim ve ihtarlar **kiracıya ulaştığı (tebliğ edildiği)** tarihte hüküm doğurur; "son gün" tebliğ için son gündür. Noter ihtarnamesinde tebliğ birkaç gün sürebilir, adres yanlışsa haftalar. Takvimde her bildirim için:
- `son_gun` — kanundaki son gün (tebliğ için)
- `gonderme_son_gunu` — `son_gun` eksi tebliğ payı (noter/PTT için varsayılan birkaç iş günü; KEP için daha kısa) `[incele]`
- Uyarılar `gonderme_son_gunu`'na göre verilir: 🔴 0-13 gün, 🟠 14-44 gün, 🟡 45-89 gün (yarı açık aralıklar; her tarih tek banda düşer).

---

## İhtar ve bildirim tablosu

| Bildirim | Kim → kime | İçerik ve süre | Şekil | Dayanak |
|---|---|---|---|---|
| Temerrüt ihtarı | Kiraya veren → kiracı | Muaccel kira/yan gider; **en az 30 gün** süre (konut/çatılı işyeri; diğerlerinde en az 10 gün); ödenmezse fesih ihtarı. Süre tebliği izleyen günden işler | Yazılı | TBK m.315 |
| İki haklı ihtar | Kiraya veren → kiracı | Aynı kira yılında kira bedeli için ayrı ayrı iki ihtar; ihtar tarihinde borç muaccel olmalı | Yazılı | TBK m.352/2 |
| Özen borcuna aykırılık ihtarı | Kiraya veren → kiracı | Aykırılığın giderilmesi için en az 30 gün; aksi hâlde fesih | Yazılı | TBK m.316 |
| Artırım bildirimi | Kiraya veren → kiracı | Yeni dönemden en geç 30 gün önce; tespit kararının yeni dönemden itibaren etkisi için | Yazılı | TBK m.345/2 |
| Yeni malik ihtiyaç bildirimi | Yeni malik → kiracı | Edinmeden itibaren 1 ay içinde | Yazılı | TBK m.351/1 |
| Dava açacağını bildirme (süre uzatma) | Kiraya veren → kiracı | m.350-352 dava süresi içinde; süre bir kira yılı uzar | Yazılı | TBK m.353 |
| On yıl sonrası sebepsiz fesih | Kiraya veren → kiracı | Uzama yılının bitiminden en az 3 ay önce | Yazılı | TBK m.347/1, m.348 |
| Kiracının sona erdirme bildirimi | Kiracı → kiraya veren | Belirli süreli: süre bitiminden en az 15 gün önce. Aile konutunda eşin açık rızası | Yazılı | TBK m.347/1, m.348, m.349 |
| Ayıp bildirimi | Kiracı → kiraya veren | Gecikmeksizin; giderilmesi için uygun süre | Yazılı önerilir | TBK m.318, m.306 |
| Aile konutu bildirimi | Kiracı olmayan eş → kiraya veren | Bildirimle sözleşmenin tarafı olur; sonrasında ihtarlar iki eşe ayrı ayrı | — | TBK m.349/3 |

- Konut ve çatılı işyerinde **fesih bildirimi yazılı değilse geçersizdir**; WhatsApp mesajı, e-posta ya da sözlü bildirim ispat ve geçerlilik riski taşır. Noter ihtarnamesi ya da kiracının yazılı kabulüyle KEP `[incele]`. 🟠 E-posta ya da KEP ile yapılan bildirimin m.348'deki yazılı şekli karşılayıp karşılamadığına dair 3. HD kararı bu turda bulunamadı: kullanıcıya "geçerlidir" deme; noter ihtarnamesini öner. Uyuşmazlık çıkmışsa `legal_search_cases` (`daire: "3. Hukuk Dairesi"`, sorgu "kira fesih bildirimi e-posta KEP yazılı şekil 348 güvenli elektronik imza") ile ara ve tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: elektronik bildirim ve yazılı şekil]` yaz.

---

## Kontrol listesi
1. Sözleşme başlangıcı, ilk süre, kira yılı doğru çıkarıldı mı?
2. Bildirimin türü ve kanuni süresi madde metninden çekildi mi?
3. Bildirim kimden kime; aile konutunda iki eşe mi?
4. Şekil: yazılı mı, tebliğ ispatlanabilir mi?
5. Son gün ve gönderme son günü; resmî tatil kontrolü.
6. Bildirimden sonra hangi süre başlıyor (dava, arabuluculuk)? Takvime eklendi mi?

## Görüşme soruları
1. Sözleşme başlangıç tarihi ve süresi?
2. Bugüne kadar yapılan bildirimler: tarih, yol (noter, KEP, e-posta, elden), tebliğ tarihi?
3. Hangi sonucu istiyorsunuz (ödeme, tahliye, artış, çıkış)?
4. Kiracı evli mi, eşi kiraya verene bildirimde bulundu mu?
5. Kiracının güncel adresi kesin mi (tebliğ riski)?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6098" article_no: "315" | "316" | "345" | "347" | "348" | "349" | "351" | "352" | "353"
legal_check_holiday <her son gün>
legal_search_cases mahkeme: "yargitay" daire: "3. Hukuk Dairesi" sorgu: "<ör. ödeme günü gelmeden çekilen ihtar haklı ihtar sayılmaz>" tarih_baslangic: <son 3 yıl>
```

## Çıktı iskeleti — yıllık kira takvimi

```markdown
## Kira takvimi: [kiralanan] — başlangıç [gg.aa.yyyy], kira yılı [gg.aa]
| Tarih (son gün) | Gönderme son günü | İşlem | Kim | Dayanak | Durum |
|---|---|---|---|---|---|
| | | Kiracının sona erdirme bildirimi (süre bitiminden 15 gün önce) | Kiracı | TBK m.347/1 | 🟡 |
| | | Artırım bildirimi / tespit davası (yeni dönemden 30 gün önce) | Kiraya veren | TBK m.345 | |
| | — | İhtiyaç davası penceresi açılır (yıl sonu) → arabuluculuk başvurusu bu tarihten sonra | Kiraya veren | TBK m.350; 3. HD 2025/1495 | |
| | — | İhtiyaç davası son günü (yıl sonu + 1 ay; arabuluculuk süresi eklenir) | Kiraya veren | TBK m.350; 6325 m.18/A-15 | |
| | | On yıl sonrası fesih bildirimi (uzama yılı bitiminden 3 ay önce) | Kiraya veren | TBK m.347/1 | |
| | | Beş yıl eşiği — rayiç tespit mümkün | Kiraya veren | TBK m.344/3 | |

Hesaplama: [elle; legal_check_holiday ile kontrol edildi] [doğrula]
```

Kullanıcı takvimi sürekli izlemek isterse: bu becerinin işi değil; ileride eklenecek süre takibi becerisine (TODO: "Süre takibi") devredilecek. Şimdilik takvimi tablo olarak ver.

## Sık hatalar
- 🔴 Bildirimi son gün göndermek; tebliğ ertesi güne kalır, süre kaçar.
- 🔴 Kira yılını takvim yılı sanıp ihtiyaç davasını Ocak'ta açmak.
- 🟠 Temerrüt ihtarında 30 günden kısa süre vermek ya da fesih ihtarını yazmamak.
- 🟠 Aile konutunda ihtarı yalnız kiracı eşe göndermek.
- 🟡 Fesih bildirimini mesajla yapmak.
