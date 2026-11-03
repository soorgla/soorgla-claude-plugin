# Zamanaşımı, dava şartları ve görevli mahkeme

## Ne zaman kullanılır
Her tazminat sorusunda, esasa girmeden önce: "Talep zamanaşımına uğradı mı, ne zamana kadar dava açılmalı, dava açmadan önce yapılması zorunlu bir başvuru var mı, hangi mahkeme görevli?" Tazminat dosyalarında en sık hak kaybı burada olur.

`legal_calculate_deadline` bu sürelerin hiçbirini tanımıyor (yalnız `hmk_appeal`, `hmk_cassation`, `cmk_appeal`, `iik_complaint`). Hepsini **madde metninden elle** hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]` işaretle.

---

## Zamanaşımı tablosu

| Talep | Süre | Dayanak | Not |
|---|---|---|---|
| Genel haksız fiil | Zararı ve tazminat yükümlüsünü **öğrenmeden 2 yıl**, her hâlde **fiilden 10 yıl** | TBK m.72/1 | İki süre birlikte işler; hangisi önce dolarsa. |
| Fiil aynı zamanda **suç** ise | Ceza kanunlarındaki **daha uzun dava zamanaşımı** | TBK m.72/1 ikinci cümle; KTK m.109/2 | Ceza davası açılmış olması ya da mahkûmiyet şart değil; fiilin suç oluşturması yeterli. |
| Ceza dava zamanaşımı süreleri | Ağırlaştırılmış müebbet 30, müebbet 25, 20 yıldan az olmayan hapis 20, 5-20 yıl arası hapis 15, 5 yıla kadar hapis ya da adli para cezası **8 yıl**; suçun kanundaki cezasının **üst sınırı** esas, nitelikli hâller gözetilir | TCK m.66/1, 3, 4 | Taksirle yaralama/öldürmenin üst sınırını `legal_get_statute_article 5237 m.85, m.89` ile çek. |
| Motorlu araç kazası — maddi zarar | Öğrenmeden 2 yıl, her hâlde kazadan 10 yıl; uzamış ceza zamanaşımı **maddi tazminat için de** | KTK m.109/1-2 | Yükümlüye karşı kesilen zamanaşımı sigortacıya karşı da kesilir ve tersi (m.109/3). |
| Motorlu araç kazası — rücu (yükümlüler arası) | Tam ifa ve rücu edileceği kişiyi öğrenmeden 2 yıl | KTK m.109/4 | |
| Ürün sorumluluğu (7223) | Öğrenmeden **3 yıl**, her hâlde **zararın doğduğu tarihten 10 yıl** | 7223 m.6/6 | Diğer kanunlardaki sorumluluk hükümleri saklı (m.6/7). |
| Özel hekim / özel hastane (vekâlet ilişkisi) | **5 yıl** (vekâlet sözleşmesinden doğan alacak) | TBK m.147/5 | 3. HD bu ilişkiyi vekâlet sayıyor ve 5 yıllık süreyi uyguluyor. Zarar gören haksız fiile de dayanabilir (TBK m.60); hangisinin lehe olduğunu olay ve öğrenme tarihine göre hesapla `[incele]`. |
| Estetik ameliyat, diş protezi (eser ilişkisi) | **5 yıl**; yüklenicinin **ağır kusuruyla** hiç ya da gereği gibi ifa etmemesi hâlinde genel süre | TBK m.147/6 | Temyiz 6. HD. |
| İşverene karşı iş kazası tazminatı (TBK m.417/3 sözleşmeye aykırılık) | → `../../sosyal-guvenlik-sgk/references/is-kazasi-ve-rucu.md` | | |
| İdari eylemden doğan zarar (kamu hastanesi, yol kusuru) | Önce idareye başvuru: eylemi öğrenmeden **1 yıl**, her hâlde eylemden **5 yıl**; ret ya da **30 gün** cevapsızlıktan sonra **60 gün** içinde dava | İYUK m.13/1, m.7/1 | Görevsiz adli yargıda açılıp görev yönünden reddedilen davada ön başvuru aranmaz (m.13/2). |
| Yetersiz/fahiş trafik tazminatı anlaşmasının iptali | Anlaşmadan **2 yıl** | KTK m.111/2 | |
| Zamanaşımına uğramış haksız fiil alacağına dayanarak ifadan kaçınma | Her zaman | TBK m.72/2 | |

**Zamanaşımının kesilmesi ve durması:** borçlunun borcu ikrarı (faiz ödemesi, kısmi ifa, rehin, kefil), dava ya da def'i yoluyla **mahkemeye veya hakeme** başvuru (Sigorta Tahkim dâhil `[incele]`), icra takibi ve iflas masasına başvuru zamanaşımını keser (TBK m.154). Arabuluculuk başvurusundan son tutanağa kadar zamanaşımı durur (6325 m.18/A-15; ayrıntı `../../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md`). Durma sebepleri (TBK m.153). Sigortacının ödemesi işletene karşı da ikrar sayılabilir `[incele]`.

**Kısmi dava ve zamanaşımı:** 31.07.2026'dan sonra açılan davalarda belirsiz alacak davası yok; kısmi davada bir defalık artırımda zamanaşımı artırılan kısım için de dava tarihinde kesilmiş sayılır (HMK m.109/4). Ayrı bir ek dava açılacaksa kalan kısmın zamanaşımı ayrıca hesaplanmalı `[incele]`.

---

## Dava öncesi zorunlu adımlar (dava şartları)

| Uyuşmazlık | Zorunlu adım | Dayanak | Not |
|---|---|---|---|
| ZMSS sigortacısına karşı talep | **Yazılı başvuru**; 15 gün içinde cevap yoksa ya da cevap karşılamazsa dava/tahkim | KTK m.97 | Tamamlanabilir dava şartı; işleten için aranmaz. |
| ZMSS sigortacısına karşı dava | **Zorunlu arabuluculuk yok** | 4. HD uygulaması | |
| Sigorta Tahkim Komisyonu | Sigortacıya başvuru + red ya da 15 iş günü cevapsızlık | 5684 m.30/13 | |
| Tüketici mahkemesinde görülecek dava (özel hastane-hasta, ayıplı ürün) | **Zorunlu arabuluculuk** (tüketici hakem heyetinin görev alanındakiler ve bazı istisnalar hariç) | 6502 m.73/A | Özel hastane malpraktis davası tüketici işlemi sayılıyorsa bu şart gündeme gelir `[incele]`. |
| Ticari dava niteliğindeki para alacağı/tazminat (iki tacir arasında ticari işletmeye ilişkin hasar; kasko/ihtiyari sigorta) | **Zorunlu arabuluculuk** | TTK m.5/A | ZMSS istisnası dışında `[incele]`; ayrıntı `../../hukuk-yargilamasi-dilekce/references/arabuluculuk-basvurusu.md`. |
| İdari eylemden doğan zarar | İdareye ön başvuru | İYUK m.13 | |
| İş kazası tazminatı | **Arabuluculuk yok** | 7036 m.3/3 | → `sosyal-guvenlik-sgk`. |
| Genel haksız fiil (tacir olmayanlar arasında) | Zorunlu adım yok | | İhtiyari arabuluculuk ve ihtarname mümkün. |

---

## Görevli mahkeme ve temyiz dairesi

| Uyuşmazlık | İlk derece | Temyiz (BGK 2026/1) |
|---|---|---|
| Genel haksız fiil, kişilik hakkı | Asliye hukuk | 4. HD |
| Kusursuz sorumluluk (TBK 65-71, TMK 369) | Asliye hukuk | 3. HD |
| Trafik kazası — yalnız sürücü/işleten (tacir değil) | Asliye hukuk `[incele]` | 4. HD |
| Trafik kazası — sigortacıya karşı | Asliye ticaret (mutlak ticari dava) `[incele]` | 4. HD |
| Destekten yoksun kalma — yolcu taşıma kazası (taşıyıcı + sigorta) | Asliye ticaret (4. HD uyuşmazlık giderme) | 4. HD |
| Özel hastane / hekim (tüketici işlemi) | Tüketici mahkemesi | 3. HD |
| Estetik, diş protezi | Tüketici mahkemesi / asliye hukuk (tarafa göre) `[incele]` | 6. HD |
| Ürün sorumluluğu (imalatçı) | Tüketici mahkemesi (tüketici ise) / asliye ticaret (tacirler) `[incele]` | 3. HD (imalatçının sorumluluğu) `[incele]` |
| Kamu hastanesi, idari eylem | İdare mahkemesi (tam yargı) | Danıştay (10. D) `[doğrula]` |
| Sigorta Tahkim itiraz hakem heyeti kararı | — | Yargıtay (temyiz; 4. HD) `[incele]` |

Kesinlik ve temyiz sınırları her yıl değişir: `legal_get_social_parameters` (`istinaf_kesinlik_siniri`, `temyiz_siniri`), **dava tarihindeki** değer.

---

## Görüşme soruları
1. Olay (fiil) tarihi; zararı ve sorumluyu ilk ne zaman öğrendiniz?
2. Zarar sonradan mı ortaya çıktı (ör. ilerleyen maluliyet, geç teşhis)?
3. Fiil suç mu; ceza soruşturması/kovuşturması var mı, hangi madde?
4. Daha önce dava, icra takibi, arabuluculuk, sigortaya başvuru, tahkim, idareye başvuru yapıldı mı; tarihleri?
5. Karşı taraf ödeme yaptı ya da borcu kabul eden yazı verdi mi?
6. Karşı tarafla aranızda sözleşme var mı (hasta-hastane, yolcu-taşıyıcı, alıcı-satıcı)?
7. Taraflar tacir mi; zarar ticari işletmeyle mi ilgili?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6098" article_no: "72" | "146" | "147"
legal_get_statute_article law_no: "2918" article_no: "97" | "109" | "111"
legal_get_statute_article law_no: "5237" article_no: "66" | "85" | "89"
legal_list_statute_articles law_no: "7223" article_query: "zamanaşımı" include_content: true
legal_get_statute_article law_no: "2577" article_no: "13" | "7"
legal_list_statute_articles law_no: "6502" law_type: "Kanun" article_no: "73" include_content: true
legal_check_holiday tarih: "<son gün>"
legal_search_cases mahkeme: "yargitay" sorgu: "<ör. uzamış ceza zamanaşımı taksirle yaralama trafik kazası maddi tazminat>"
legal_search_official_gazette query: "Büyük Genel Kurulu" search_in: "title" # güncel daire iş bölümü
```

## Çıktı iskeleti
```markdown
### Süreler ve dava şartları
| Süre / şart | Başlangıç | Son gün | Dayanak | Durum (✅ / 🟠 / 🔴) |
### Hangi sürenin uygulanacağı (genel / ceza / sözleşme / 7223) — gerekçe [incele]
### Görevli mahkeme ve temyiz dairesi
```

## Sık hatalar
- Yalnız 2 yıllık süreye bakıp uzamış ceza zamanaşımını atlamak (ya da tersine, suç oluşturmayan fiile ceza süresini uygulamak).
- Özel hastane malpraktisinde 10 yıllık genel süreyi varsaymak; 3. HD vekâlet ilişkisinde 5 yıl uyguluyor.
- 7223 ürün sorumluluğunda 2 yıllık TBK süresini uygulamak (özel süre 3 yıl).
- Kamu hastanesi olayında doğrudan dava açmak; İYUK m.13 ön başvurusu ve 1 yıl/5 yıl süresi kaçar.
- ZMSS davasında zorunlu arabuluculuk aramak; KTK m.97 başvurusunu ise atlamak.
- 31.07.2026 sonrası davayı belirsiz alacak davası olarak açmak.
