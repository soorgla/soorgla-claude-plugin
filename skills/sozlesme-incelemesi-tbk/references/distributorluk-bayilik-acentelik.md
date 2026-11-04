# Bayilik, distribütörlük (tek satıcılık), franchise ve acentelik

Dikey dağıtım ilişkileri: üretici/tedarikçi ile bayi, distribütör, franchise alan ya da acente arasındaki sürekli sözleşmeler.

## Ne zaman kullanılır
- "Bayilik sözleşmesi", "distribütörlük", "tek yetkili satıcı", "münhasır bölge", "franchise", "acente", "portföy (denkleştirme) tazminatı", "bayiliğimiz feshedildi", "rekabet etmeme süresi".
- Akaryakıt, otomotiv gibi sektörlere özgü dikey kurallar varsa ayrıca işaretle `[incele]` (motorlu taşıtlar için ayrı grup muafiyeti tebliği var).

Eski YAML `distributorship_agreement.yaml` **boş**; içerik `lawyer/commercial_corporate/commercial_contracts_analysis.yaml` ve sıfırdan yazımdır.

---

## 1. Nitelendirme

| Tür | Özellik | Uygulanacak hükümler |
|---|---|---|
| **Acentelik** | Bağımsız tacir yardımcısı (işletmeye bağlı hukuki konumu yok); sürekli olarak, belli yer/bölgede sözleşmelere aracılık ya da bunları **müvekkil tacir adına** yapma | TTK m.102-123  |
| **Tek satıcılık / distribütörlük** | Distribütör malı **kendi adına ve hesabına** alıp satar; bölgede münhasırlık | Kanunda düzenlenmemiş (atipik); TTK m.122/5 kıyasen; TBK genel; 4054 |
| **Bayilik** | Kendi adına ve hesabına satış; münhasırlık olmayabilir | Atipik; TBK genel; 4054 |
| **Franchise** | Marka, know-how, sistem kullanımı + ücret; bayilik + lisans karması | Atipik; FSEK/SMK lisans, 4054 |

Tek satıcılık ve bayilik kanunda düzenlenmeyen atipik sözleşmelerdir; tek satıcılık bayiliğin bir alt türü olarak görülür. `[çekildi ama desteği doğrulayın]` 

## 2. Kontrol listesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| FESİH-SÜRESİ | Acentelikte belirsiz süreli sözleşme **üç ay önceden** ihbarla feshedilir; belirli süreli sözleşme süre bitiminde uygulanmaya devam ederse belirsiz süreliye dönüşür; haklı sebeple her zaman fesih; ihbar süresine uymayan, başlanmış işlerin tamamlanmamasından doğan zararı öder | TTK m.121/1, 2, 4 | Distribütörlükte kanuni süre yok; makul süre ve ilişkinin yoğunluğu `[incele]`. Eski YAML "genelde 3 ay (TTK 121)" diyordu; bu yalnız acentelik için kanuni süredir |
| DENKLEŞTİRME-KOŞUL | Sona ermeden sonra: (a) müvekkil acentenin bulduğu müşterilerden önemli menfaat sağlamaya devam ediyor, (b) acente bu müşterilerden doğacak ücreti kaybediyor, (c) hakkaniyete uygun | TTK m.122/1 | |
| DENKLEŞTİRME-TAVAN | Son beş yıllık faaliyetten aldığı yıllık komisyon/ödemelerin **ortalamasını aşamaz**; daha kısa süreli ilişkide faaliyet süresi ortalaması | TTK m.122/2 | Tutar değil formül yaz |
| DENKLEŞTİRME-KAYIP | Acente haklı sebep olmadan feshederse ya da kusuru nedeniyle haklı sebeple feshedilirse istem yok | TTK m.122/3 | |
| DENKLEŞTİRME-FERAGAT | **Önceden vazgeçilemez**; sona ermeden itibaren **bir yıl içinde** ileri sürülmeli | TTK m.122/4 | Sözleşmedeki "denkleştirme talep edilmeyecektir" kaydı → KIRMIZI (hükümsüz) |
| DENKLEŞTİRME-KIYASEN | Hakkaniyete aykırı düşmedikçe **tek satıcılık** ve benzeri tekel hakkı veren sürekli ilişkilerde de uygulanır | TTK m.122/5 | Münhasırlık yoksa uygulanması tartışmalı `[incele]` |
| MÜNHASIRLIK | Bölge/müşteri münhasırlığı; pasif satış yasağı; internet satışları | 4054 m.4; 2002/2 Tebliğ m.4 | Pasif satışı yasaklayan kayıt muafiyeti düşürebilir `[incele]`  |
| YENİDEN-SATIŞ-FİYATI | Sağlayıcının bayinin satış fiyatını belirlemesi (asgari ya da sabit fiyat) | 4054 m.4; 2002/2 Tebliğ m.4 | Azami ya da tavsiye fiyat dışında **KIRMIZI** |
| REKABET-ETMEME-SÜRE | Alıcıya getirilen **belirsiz süreli ya da beş yılı aşan** rekabet etmeme yükümlülüğü grup muafiyetinden **yararlanamaz**; beş yılı aşacak şekilde zımnen yenilenebilen yükümlülük belirsiz süreli sayılır; sağlayıcıya ait tesiste istisna | 2002/2 Tebliğ m.5/a | Eski YAML "5 yılı aşan yasaklar geçersizdir" diyordu; doğrusu: muafiyet dışında kalır, bireysel muafiyet (4054 m.5) değerlendirilmeden geçersiz denemez `[incele]` |
| SÖZLEŞME-SONRASI-REKABET | Sona ermeden sonra rekabet etmeme: kural olarak muafiyet dışı; istisna — rakip mallarla sınırlı, anlaşma süresince kullanılan tesis/arazi ile sınırlı, know-how'ı korumak için zorunlu ve **bir yılı aşmayan** | 2002/2 Tebliğ m.5/b | Kamuya mal olmamış know-how için süresiz kullanım/açıklama yasağı saklı |
| SEÇİCİ-DAĞITIM | Seçici dağıtım üyelerine belirli rakip markaları satmama yükümlülüğü muafiyet dışı | 2002/2 Tebliğ m.5/c | |
| PAZAR-PAYI | Grup muafiyetinin pazar payı eşiği ve tek alıcıya sağlama eşiği | 2002/2 Tebliğ m.2; 2021/4 Değişiklik Tebliği | Oranı tebliğden çek; ezberden yazma. 2021/4 ile eşik değişti ve uyum için geçiş süresi tanındı  |
| STOK-İADESİ | Sona ermede stok geri alımı, fiyatı, iade süresi | Sözleşme | Yoksa SARI (distribütör tarafı) |
| ASGARİ-ALIM | Asgari alım/satış hedefi ve tutturulamamasının sonucu (fesih, münhasırlığın kalkması) | Sözleşme | Hedefe bağlı fesih "haklı sebep" sayılır mı `[incele]` |
| TEMİNAT | Teminat mektubu, ipotek, kefalet (gerçek kişi kefil → el yazısı ve eş rızası) | TBK m.583-584 | → `kefalet-ve-saklama.md` |
| CEZAİ-ŞART | Rekabet ihlali ya da erken fesih cezası; taraflar tacir → TTK 22, ekonomik mahv istisnası | TBK m.179-182; TTK m.22 | → `cezai-sart-ifa-ve-sorumluluk.md` |
| BİLDİRİM-ŞEKLİ | Tacirler arası fesih bildirimi noter, taahhütlü mektup, telgraf ya da güvenli e-imzalı KEP | TTK m.18/3 | |
| MARKA-LİSANS | Franchise ve bayilikte marka kullanım izni, sona erince kullanımın bitmesi | 6769 SMK m.24 |  |
| KVKK | Müşteri verilerinin aidiyeti ve sona ermede devri | 6698 | → `../../kvkk/SKILL.md` |
| ZAMANAŞIMI | Acentelikten doğan alacaklar 5 yıl | TBK m.147/5 | Distribütörlükte genel süre `[incele]` |

**Emsal (son 3 yıl):** tek satıcılıkta TTK m.122/5 yoluyla denkleştirme ve m.122/1-a,b,c koşulları — [Yargıtay 11. HD E.2024/3335 K.2025/3436, 15.05.2025]; [11. HD E.2024/4540 K.2025/4358, 19.06.2025]. Tam metnin yalnız olay kısmı okundu (uzun dosya, birleşen davalar; davacı fesih ihbar süresinin ilişkinin yoğunluğu nedeniyle 3 aydan uzun olması gerektiğini ileri sürüyor); gerekçe paragrafı okunmadığından `[çekildi ama desteği doğrulayın]`. 

## 3. Kimin adına?
- **Sağlayıcı (üretici):** asgari hedef ve performansa bağlı fesih, makul fesih bildirimi, denkleştirmenin hakkaniyet unsurlarını belgeleyen kayıtlar (müşteri portföyünün kimin emeği olduğu), rekabet etmeme süresinin tebliğe uyumu, fiyat belirleme yasağı.
- **Bayi / distribütör / acente:** münhasırlığın açık tanımı, sağlayıcının bölgeye doğrudan satış yasağı, denkleştirmeden feragat kaydının hükümsüzlüğü, uzun ihbar süresi ve yatırımların karşılanması, stok iadesi.

## 4. Görüşme soruları
1. Bayi malı kendi adına ve hesabına mı satıyor, yoksa sağlayıcı adına mı aracılık ediyor?
2. Münhasır bölge ya da müşteri grubu var mı? Sağlayıcı bölgeye doğrudan satış yapıyor mu?
3. Sözleşme süresi, kaç kez yenilendi, ilişki kaç yıldır sürüyor?
4. Son beş yılın komisyon/kâr verileri?
5. Rekabet etmeme yükümlülüğü: sözleşme süresince ve sonrasında kapsam ve süre?
6. Fesih nasıl ve kim tarafından yapıldı; gerekçe; bildirim şekli?
7. Taraflardan birinin pazar payı hakkında bilgi var mı?

## 5. MCP adımları
```
legal_get_statute_article  law_no: "6102"  article_no: "102" | "121" | "122" | "18" | "22"
legal_get_statute_article  law_no: "39031"  article_no: "2" | "4" | "5"     # Dikey Anlaşmalar Grup Muafiyeti Tebliği 2002/2
legal_get_statute_article  law_no: "4054"  article_no: "4" | "5"
legal_search_official_gazette  query: "Dikey Anlaşmalara İlişkin Grup Muafiyeti Tebliği"  search_in: "title"  sort_by: "date_desc"
legal_search_admin_guidance  kurum: "Rekabet Kurumu"  sorgu: "<ör. bayilik sözleşmesinde beş yılı aşan rekabet yasağı bireysel muafiyet>"
legal_search_cases  mahkeme: "yargitay"  daire: "11. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "tek satıcılık sözleşmesinin haksız feshi denkleştirme tazminatı ve makul fesih süresi"
legal_search_cases  mahkeme: "danistay"  daire: "13. Daire"  sorgu: "<Rekabet Kurulu dikey anlaşma kararının iptali>"
```
**Motorlu taşıt bayiliği:** sözleşme motorlu taşıt satışı, yedek parça ya da servis içeriyorsa genel 2002/2 yerine ayrıca Motorlu Taşıtlar Sektöründeki Dikey Anlaşmalara İlişkin Grup Muafiyeti Tebliği'ne (2017/3, katalog no `23360`) bak: `legal_list_statute_articles law_no: "23360"`. Tebliğin hâlâ yürürlükte olup olmadığını ve 2002/2'nin yerine yeni bir dikey tebliğ çıkıp çıkmadığını her incelemede `legal_search_official_gazette` (`query: "Grup Muafiyeti Tebliği"`, `search_in: "title"`, `sort_by: "date_desc"`) ile kontrol et; bulamazsan `[ARAŞTIRMA GEREKLİ: dikey grup muafiyeti tebliğlerinin güncel durumu]` yaz.

## 6. Çıktı iskeleti
`genel-inceleme-ve-playbook.md` §9 + ek:
```markdown
### Dağıtım ilişkisine özgü kontrol
- **Nitelendirme:** acentelik / tek satıcılık / bayilik / franchise — gerekçe
- **Münhasırlık:** …
- **Rekabet hukuku süzgeci:** fiyat belirleme [yok/var 🔴] · rekabet etmeme süresi [≤5 yıl / aşıyor → muafiyet dışı] · sözleşme sonrası yasak [≤1 yıl ve koşullar / aşıyor]
- **Fesih:** süre [ ] — kanuni/makul süre karşılaştırması
- **Denkleştirme:** koşullar (a)(b)(c) · tavan formülü · 1 yıllık süre: [son gün]
```

## 7. Sık hatalar
- Distribütörlüğü acentelik sayıp TTK'yı doğrudan uygulamak; ya da tersine TTK 122/5'i hiç görmemek.
- Denkleştirmeden önceden feragati geçerli saymak.
- Beş yılı aşan rekabet yasağını "kesin geçersiz" diye raporlamak (doğrusu: grup muafiyeti dışında, bireysel değerlendirme).
- Pazar payı eşiğini ezberden yazmak; 2021/4 değişikliğini atlamak.
- Rekabet Kurulu kararlarını mahkeme kararı ağırlığında sunmak.

---

