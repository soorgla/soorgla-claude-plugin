# Vergi incelemesi süreci ve idare (kamu görevlisi) tarafı

## Ne zaman kullanılır
- Mükellef nezdinde **vergi incelemesi** başladı ya da sürüyor: "müfettiş defterleri istedi", "inceleme tutanağını imzalayayım mı", "tarhiyat öncesi uzlaşma istesek mi", "inceleme bir yıldır bitmedi".
- Takdir komisyonuna sevk ve takdir kararı.
- **İdare / kamu görevlisi tarafı:** vergi dairesi müdürlüğü, gelir servisi, uzlaşma komisyonu üyesi, vergi müfettişi ya da rapor değerlendirme komisyonu bakışıyla "işlemimiz hukuka uygun mu, dava riskimiz ne?" (eski `bureaucrat/finance_revenue_social/tax_administration` akışı; ayrı beceri değil).

---

## Süreler ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| İncelemeye başlama bildirimi | İncelemeye tabi olana incelemenin **konusu ve başlandığı** yazıyla bildirilir; örneği birime ve vergi dairesine gönderilir | VUK m.140/1 (7338/18) |
| İnceleme süresi | Başlangıçtan itibaren tam incelemede en fazla **1 yıl**, sınırlı incelemede **6 ay**, KDV iade incelemesinde **3 ay** esas; ek süre tam/sınırlıda en çok **6 ay**, KDV iadesinde **2 ay**; ek sürenin nedenleri mükellefe yazılı bildirilir | VUK m.140/6 (7104/19) |
| Mesai dışı inceleme | İşyerinde muvafakat olmadan resmî çalışma saatleri dışında inceleme yapılamaz (tutanak ve emniyet tedbirleri hariç) | VUK m.140/3 |
| İnceleme bitince | İncelemenin yapıldığını gösteren vesika mükellefe verilir | VUK m.140/4 |
| Takdir komisyonu ve zamanaşımı | Komisyona başvuru tarh zamanaşımını durdurur; durma en çok **1 yıl** | VUK m.114/2 |
| Tarhiyat öncesi uzlaşma | Vergi incelemesine dayanılarak kesilecek **cezalarda** (7524 sonrası yalnız ceza); uzlaşılan husus için dava ve şikâyet yok; sağlanamazsa tarhiyat sonrası uzlaşma yok; usul Yönetmelikte | VUK ek m.11 |

**Süre aşımının sonucu:** m.140/6 "bitirmeleri **esastır**" der; sürenin aşılması tek başına tarhiyatı hukuka aykırı kılar mı tartışmalıdır `[incele]`. Çalışma anında `legal_search_cases` (`mahkeme: "danistay"`, `sorgu: "vergi incelemesinin 140 ıncı maddedeki sürede bitirilmemesi tarhiyatın iptali"`, son 3 yıl) ile ara ve en az bir tam metni oku; bulamazsan `[ARAŞTIRMA GEREKLİ: VUK m.140/6 süre aşımının tarhiyata etkisi]`.

---

## Kontrol listesi — mükellef tarafı (inceleme sürerken)

1. Başlama yazısı tebliğ edildi mi; incelemenin **konusu ve dönemi** ne? (m.140/1) Kapsam dışına taşan istemleri not et.
2. **Defter ve belge ibrazı**: ibraz etmemek re'sen takdir sebebi ve m.359 yönünden "gizleme" sayılabilir; ibraz tutanağa bağlansın. 🔴
3. **Tutanaklar**: imzalamadan önce oku; katılmadığın tespiti şerh düş. İmzadan kaçınmak tespiti ortadan kaldırmaz `[incele]`.
4. **Süre**: başlama tarihinden itibaren 1 yıl / 6 ay / 3 ay geçti mi; ek süre yazısı geldi mi?
5. **Pişmanlık penceresi kapandı mı?** İnceleme başladıktan sonra o vergi türü için pişmanlık yolu kapanır (m.371/2).
6. **Tarhiyat öncesi uzlaşma** isteyip istememe: sağlanamazsa tarhiyat sonrası uzlaşma kaybedilir; vergi aslı uzlaşma dışında. Karar `[incele]`.
7. **Rapor değerlendirme komisyonu**: vergi müfettişi raporları vergi dairesine gitmeden önce komisyonda mevzuata uygunluk yönünden değerlendirilir; komisyon özelgenin m.369 kapsamında olduğunu düşünürse özel komisyon karar verir. Elinde lehine özelge varsa incelemede sun.
8. **Genel tebliğe aykırı rapor**: incelemeye yetkililer Cumhurbaşkanı kararı, yönetmelik, genel tebliğ ve sirkülere aykırı rapor düzenleyemez. İdarenin kendi tebliğine aykırı tarhiyat 🟠 iddia.

## Kontrol listesi — idare tarafı (kamu görevlisi bakışı)

Amaç: işlemi hukuka uygun kurmak ve dava kaybını önlemek. Mükellefe yönelik savunma metni yazma; iç değerlendirmeyi ayrı tut (ORTAK-KURALLAR.md §1).

| Aşama | Kontrol | Risk |
|---|---|---|
| İnceleme | Başlama yazısı, kapsam, süre ve ek süre yazıları dosyada mı? | 🟠 süre/usul iddiası |
| Rapor | Somut tespitler (sahte belgede alıcı nezdinde mal/para hareketi) yazılı mı; yalnız düzenleyici hakkındaki VTR'ye atıf mı? | 🔴 iptal riski |
| Rapor | Tebliğ ve sirkülere uygunluk (m.140/5) ve rapor değerlendirme komisyonu kararı | 🟠 |
| Takdir | Takdir komisyonuna sevk ve dönüş tarihleri, zamanaşımı durması ≤1 yıl | 🔴 zamanaşımı |
| Tarhiyat | Ceza türü/katı ve artırımlar gerekçeli mi; m.359 fiili somut mu? | 🔴 |
| Tebliğ | Muhatap (tasfiyede VUK m.10/5), adres, e-tebligat iletim kaydı | 🔴 süre/kesinleşme |
| Uzlaşma komisyonu | 7524 sonrası yalnız ceza; geçiş dosyaları (geçici m.35) ayrı; eşik altı usulsüzlük uzlaşma dışı | 🟠 yetki aşımı |
| Tahsil | Kesinleşme, ödeme emri ihtarları, temsilciye gitme şartları | → `amme-alacagi-tahsili-6183.md` |

İdare tarafında da emsal ara: lehine ve aleyhine VDDK kararlarını birlikte göster; Sayıştay denetimi riski (vergi gelirlerinin terkin ve tahsilinde) ayrı bir konu olarak işaretle → `../../kamu-mali-denetim-sayistay/SKILL.md` (esas); savunma metni `../../idari-ve-kurum-basvurulari/references/sayistay-savunmasi.md`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| İncelemeye başlama yazısının tarihi, konusu, dönemi? | Süre, kapsam |
| Hangi defter ve belgeler istendi, ne ibraz edildi, tutanak var mı? | m.359 gizleme riski |
| İnceleme sahte belge (VTR) iddiasına mı dayanıyor? | Somut tespit savunması |
| Ek süre yazısı geldi mi? | m.140/6 |
| Lehinize özelge ya da önceki inceleme var mı? | m.369, tutarlılık |
| (İdare) Rapor değerlendirme komisyonu kararı ve tebliğ belgeleri dosyada mı? | Dava riski |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "213" law_type: "Kanun" article_no: "134" | "135" | "138" | "139" | "140" | "141" | "ek 11"
legal_resolve_statute query: "Vergi İncelemelerinde Uyulacak Usul ve Esaslar Hakkında Yönetmelik"
legal_resolve_statute query: "Tarhiyat Öncesi Uzlaşma Yönetmeliği"
legal_search_cases mahkeme: "danistay" sorgu: "<ör. vergi inceleme süresinin aşılması tarhiyatın iptali>" tarih_baslangic: "<son 3 yıl>"
```

---

## Çıktı iskeleti

```markdown
## Vergi incelemesi durum notu — [mükellef / dönem] — [taraf: mükellef | idare]
| Aşama | Tarih | Süre / sınır | Durum | İşaret |
### Riskler (🔴/🟠/🟡)
### Tarhiyat öncesi uzlaşma: öneri [incele]
### Yapılacaklar (belge, şerh, bildirim)
```

---

## Sık hatalar

- 🔴 Defterleri ibraz etmemeyi "savunma taktiği" sanmak (m.359 gizleme).
- 🟠 İnceleme başladıktan sonra pişmanlıkla beyan vermeye çalışmak.
- 🟠 Tarhiyat öncesi uzlaşmayı "risksiz" sanmak (sağlanamazsa sonrası yok).
- 🟡 İdare tarafında süre ve ek süre yazılarını dosyaya koymamak.

---
