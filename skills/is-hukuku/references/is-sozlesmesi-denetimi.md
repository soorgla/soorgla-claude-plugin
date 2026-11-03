# İş sözleşmesi ve hizmet sözleşmesi denetimi

Bir iş sözleşmesini (ya da pazarlamacılık sözleşmesini) emredici hükümlere aykırılık, geçersizlik riski ve taraf dengesi açısından inceler.

**Tereddütte işçi lehine yorum:** iş hukukunun işçiyi koruyan emredici hükümleri önceliklidir. Sözleşmede işçi aleyhine emredici hükümden sapma kural olarak geçersizdir. İşçi lehine yorum yalnız **açık olmayan** iş mevzuatı kurallarında başvurulan bir yöntemdir; açık hüküm işçi lehine de olsa yorumla değiştirilemez. Bir TBK hükmünün işçi aleyhine değiştirilip değiştirilemeyeceğini ezberden yazma; ilgili maddeyi `legal_get_statute_article` ile çek ve metindeki "aleyhine değiştirilemez" ibaresine bak.

Her tespiti ilgili madde metniyle destekle: maddeyi `legal_get_statute_article` ile çek ve kısa alıntıla.

---

## Strateji: kimin adına?

Kontrol listesi aynıdır; rapordaki vurgu tarafa göre değişir.

**İşçi tarafı (savunucu)** — işçi aleyhine şartları ve ücret kesintilerini bul:
- Kişiliğin korunması ve psikolojik/cinsel tacizin önlenmesi yükümlülüğü (TBK m.417) sözleşmede/işyeri politikasında var mı?
- İbra şartı: sözleşme sürerken ya da sona ermeden 1 ay geçmeden alınan ibra geçersiz (TBK m.420).
- Yıllık izin süreleri kanuni alt sınırın altında mı (4857 m.53)?
- Ücretten kesme ve cezalar (4857 m.38) — yalnız TİS ya da iş sözleşmesinde gösterilen sebeplerle, sebebiyle derhâl bildirilerek ve kanundaki aylık üst sınır içinde.

**İşveren tarafı (strateji)** — sadakat, sır ve rekabet üzerinden işvereni koru:
- Sadakat ve sır saklama borcu; sözleşme bittikten sonra da devam eden sır saklama (TBK m.396).
- İşçinin kusuruyla verdiği zarardan sorumluluğu (TBK m.400).
- Haklı nedenle fesih hallerinin (4857 m.25/II) işyerine özgü örneklerle açıkça yazılması.

---

## Kontrol listesi (eski "yasal korkuluklar")

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| ŞEKİL-SÜRE | Süresi 1 yıl ve daha fazla olan sözleşmeler yazılı mı? Yazılı değilse işveren çalışma koşullarını gösteren belgeyi vermiş mi? | 4857 m.8; TBK m.394 | Yazılılık ispat şartı mı geçerlilik şartı mı — ayrımı yap `[incele]`. |
| DENEME | Deneme süresi en çok **2 ay**; toplu iş sözleşmesiyle **4 aya** kadar uzatılabilir. Aşan kısım risk. | 4857 m.15; TBK m.433 | |
| FAZLA-ÇALIŞMA | Fazla çalışma ücreti %50 zamlı mı? Ücrete "fazla mesai dahildir" maddesi var mı? Yıllık 270 saati aşan kısım için geçersizlik riski. | 4857 m.41; TBK m.402 | |
| REKABET-YASAĞI | Fiil ehliyetli işçi yazılı olarak mı üstlendi? Hizmet ilişkisi işçiye müşteri çevresi, üretim sırları ya da işverenin işleri hakkında bilgi edinme imkânı veriyor ve bunların kullanılması işverene önemli zarar verebilecek nitelikte mi? İşverenin haklı menfaati var mı? Yer, zaman ve iş türü bakımından işçinin ekonomik geleceğini tehlikeye atıyor mu? Süre özel haller dışında 2 yılı aşmamalı. Karşılık (ivaz) var mı? | TBK m.444-447 | Tek taraflı (yalnız işçi aleyhine) cezai şart riski `[incele]`. |
| BİLDİRİM-SÜRESİ | Fesih bildirim süreleri kanundaki kıdeme bağlı sürelerin (2, 4, 6, 8 hafta) altında mı? Altındaysa aykırı. | 4857 m.17; TBK m.432 | Süreler artırılabilir, azaltılamaz. TBK m.432'deki süreler 4857'dekinden farklıdır (iş kanunu kapsamı dışındaki işçi için ayrıca çek); TBK'da süreler iki taraf için eşit olmalı. |
| PAZARLAMACI-ÜCRET | Pazarlamacıya kural olarak sabit ücret ya da sabit ücret + komisyon ödenir. Ücretin tamamı ya da önemli kısmı komisyon olacaksa **yazılı anlaşma** gerekir ve komisyon pazarlamacının faaliyetinin **uygun karşılığı** olmalı; değilse kayıt geçersiz. | TBK m.448, m.454 | |
| PAZARLAMACI-KOMİSYON | Belirli bölge/müşteri çevresi için münhasır yetki varsa, bizzat yapmadığı ama bu çevrede gerçekleşen işlemler için komisyon hakkı. | TBK m.455 | |
| BELİRLİ-SÜRE | Belirli süreli sözleşme objektif nedene dayanıyor mu? Zincirleme yenileme belirsiz süreliye dönüşüm riski. | 4857 m.11 | |
| CEZAİ-ŞART | Yalnız işçi aleyhine konulan cezai şart geçersizdir (eğitim gideri, erken ayrılma). | TBK m.420/1 (özel hüküm); genel hükümler TBK m.179-182 | İstisna: **rekabet yasağına** bağlı cezai şart, işveren karşı edim üstlenmemiş olsa da geçerlidir; m.420/1 bu hâlde uygulanmaz. Ayrıntı: `ise-alim-ve-rekabet-yasagi.md`. |
| YETKİ | İş sözleşmesinde yetki şartı. | 7036 m.6/5 — maddeye aykırı yetki sözleşmesi geçersiz | |

Tablo tabandır; sözleşmede başka bir sorun görürsen ekle (KVKK aydınlatma, gizlilik, uzaktan çalışma, ücret ödeme günü, prim/ikramiye koşulları).

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4857" article_no: "8" | "11" | "15" | "17" | "25" | "38" | "41" | "53"
legal_get_statute_article law_no: "6098" article_no: "394" | "396" | "400" | "402" | "417" | "420" | "432" | "433" | "444" | "445" | "446" | "448" | "454" | "455"
legal_get_statute_article law_no: "7036" article_no: "6"
legal_list_statute_articles (6098, hizmet sözleşmesi bölümü) # madde numaralarını teyit için
legal_search_cases mahkeme: "yargitay" daire: "9. Hukuk Dairesi"
    sorgu: "<ör. rekabet yasağı süresi ve yer bakımından sınırlanması iş sözleşmesi>"
```
Rekabet yasağına ilişkin bazı uyuşmazlıklar ticaret davası sayılıp başka dairelere gidebilir: iş sözleşmesi sona erdikten sonraki rekabet yasağı ve cezai şart davalarında görevli mahkemenin iş mahkemesi mi asliye ticaret mi olduğu bölge adliye mahkemeleri arasında tartışmalıdır; Yargıtay'da 9. HD'nin yanında 11. HD ve 3. HD kararları da var. Daireyi sabitleme; `legal_search_cases` ile görev konusundaki en güncel kararı bul ve tam metnini oku.

---

## Görüşme soruları
1. Kimin adına? (işçi / işveren)
2. Sözleşme türü: belirsiz süreli / belirli süreli / pazarlamacılık / kısmi süreli / uzaktan?
3. Sözleşmenin tamamı ve ekleri (görev tanımı, yan protokoller, işyeri yönetmeliği) mevcut mu?
4. Toplu iş sözleşmesi uygulanıyor mu?
5. Özellikle bakılmasını istediğiniz madde?

## Çıktı iskeleti

```markdown
## İş sözleşmesi denetimi: [taraflar] — [tarih]
**Taraf:** [işçi/işveren] · **Sözleşme türü:** … · **Okunan:** [tüm metin / sayfa aralığı]

### Sonuç
[imzalanabilir / şu maddeler düzeltilmeli / ciddi geçersizlik riski]

### Bulgular
| # | Madde (sözleşme) | Sorun | Önem | Dayanak | Öneri metni |
|---|---|---|---|---|---|

### Taraf dengesi notu
[ücret ve izin · özen ve sadakat · fesih ve tazminat]

### Eksik bilgi
```
10'dan fazla bulgu varsa ORTAK-KURALLAR.md'deki pano önerisini yap.

---
